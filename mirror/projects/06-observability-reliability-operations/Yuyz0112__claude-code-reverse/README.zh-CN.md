# Claude Code 逆向工程：新版（2025年7月）

[English](./README.md)

**🚀 快速体验**：通过我们的交互式可视化工具体验逆向工程分析结果：[https://yuyz0112.github.io/claude-code-reverse/visualize.html](https://yuyz0112.github.io/claude-code-reverse/visualize.html)

当 Anthropic 发布 Claude Code（2025年2月）时，由于注册因高负载暂停，我无法直接试用。因此，我实现了一种利用 LLM 对静态代码进行逆向工程的方案，这成为了本仓库的第一个版本。初始版本的代码目前归档在 [v1](./v1) 目录中。

> 当时也有另一个版本，是其他人直接基于 sourcemaps 还原源代码实现的。不过该仓库后来被下架，说明 Anthropic 官方并不支持此类逆向工程行为。

实际上，v1 的实现与其说是逆向工程 Claude Code，不如说是一次探索"利用 LLM 分析大型混淆 JS 代码"极限的实验。

当我们能够实际运行 Claude Code 后，发现有许多更简单高效的方式来理解它的工作原理。不过，我最近注意到一个新仓库引用了 v1 的方法（提到参考了我的 v1 方案）。但深入一看就会发现，这种方法对于分析整体架构和设计并不有效。

因此，我花了一个晚上探索了一种基于**运行时行为和 API 数据**的逆向工程方法（以下简称 v2），并创建了一个日志可视化工具，帮助对 Claude Code 感兴趣的研究人员分析他们关注的部分。

- 如果你对 v2 的实现思路感兴趣，请按顺序阅读以下章节。
- 如果只关心 v2 逆向工程的分析结果，可以直接跳到"分析结果"部分。

## Monkey Patching API 请求代码

作为代理，Claude Code 最终需要与 LLM API 交互。因此，v2 的核心思路是忽略 Claude Code 复杂的内部处理，仅关注它在不同任务场景下与 LLM API 之间最终交换的请求和响应。

如果你想开发一个像 Claude Code 一样强大的代理，理论上只需在相同任务场景下实现自己的代码来构造类似的 API 请求即可。这类代码通常是应用层代码，有多种不同的实现方式和风格。因此，我认为从头自行实现是最合理的做法。

然而，Claude Code 真正值得学习的是它与 LLM API 交互的内容，因为这反映了它对 LLM 和代理的理解。

获取 API 数据的方法有很多，但我目前的方法是修改 Claude Code 的安装文件。

首先，找到 `cli.js` 文件：

```shell
which claude
$PATH_TO_CLAUDE
ls -l $PATH_TO_CLAUDE
$PATH_TO_CLAUDE -> $REAL_PATH/cli.js
```

接下来，使用 `js-beautify` 格式化 `cli.js`：

```shell
mv cli.js cli.bak
js-beautify cli.bak > cli.js
```

查看格式化后的 `cli.js`，并参考 Anthropic 的 [TS SDK](https://github.com/anthropics/anthropic-sdk-typescript)，你会发现 Claude Code 使用此 SDK 发起所有请求，具体是 `beta.messages.create` 方法。

我们只需在 `cli.js` 中找到打包的 TS SDK 代码，对 `beta.messages.create` 方法进行 monkey patch 即可。TS SDK 在 Promise 和 Stream 封装方面有一些细节，这里不再赘述；具体请参考 [cli.js.patch](./cli.js.patch) 中的实际补丁代码。

此补丁实现了以下逻辑：

1. 每次启动 Claude Code 时创建一个 `messages.log` 文件。
2. 每当发送 API 请求和接收响应时记录相应的日志。

完成修改后，使用 Claude Code 即可生成这些日志。基于此，我们可以让 Claude Code 执行各种任务并分析日志来理解其工作原理。

## 日志可视化

由于每次对话请求都包含冗长的公共提示词和工具定义，原始日志难以阅读。

为提高逆向工程分析的效率，v2 提供了日志解析工具 **[parser.js](./parser.js)** 和可视化工具 **[visualize.html](./visualize.html)**。

打开可视化工具后，可以选择一个已记录的日志文件来查看整个对话。该工具会根据提示词出现的频率和在对话中的位置，尝试自动识别哪些是公共提示词（由程序注入的）。

## 分析结果

> 本节分析结果将随着更多任务场景的探索而持续更新。

已被逆向工程的 Claude Code 内部流程包括：

- 配额检查
- 话题检测
- 核心 Agent 工作流
- 上下文压缩
- IDE 集成
- Todo 短期记忆管理
- Task/Sub Agent 工作流
- 总结历史对话

已分析的提示词记录在 [prompts 目录](./results/prompts/) 中，已分析的工具定义记录在 [tools 目录](./results/tools/) 中。

提示词和工具设计都包含许多亮点和值得研究的细节，可以闲暇时慢慢阅读。

### 配额检查

Claude Code 每次启动时都会执行一次轻量级对话，输入文本 `quota`。这很可能用于检查配额是否充足；请求成功则表示配额足够。

使用 Haiku 3.5 模型。

### 话题检测

每当用户输入内容时，LLM 使用 [check-new-topic 提示词](./results/prompts/check-new-topic.prompt.md) 来判断是否为新话题。

使用 Haiku 3.5 模型。

需要注意的是，话题检测仅考虑当前对话内容，不包含任何上下文。这使其成为一个非常粗粒度的检查。目前看来，它仅用于更新终端标题。

### 核心 Agent 工作流

当上下文充足时，消息会持续追加到当前上下文中。

定义 Agent 工作流的核心流程是 [system workflow 提示词](./results/prompts/system-workflow.prompt.md)。它包含丰富的细节，建议直接阅读。

在基于上下文的对话中，第一条用户消息的前后，Claude Code 还会分别插入 [system reminder start 提示词](./results/prompts/system-reminder-start.prompt.md) 和 [system reminder end 提示词](./results/prompts/system-reminder-end.prompt.md)。前者根据当前环境动态加载信息，后者检查是否需要加载由 Todo 工具管理的短期记忆。

目前看来，所有工具都在核心 Agent 工作流中一致加载。

使用 Sonnet 4 模型。

### 上下文压缩

在手动触发或上下文不足时触发，此过程将当前上下文压缩为一段文本，作为下一次对话的初始信息。这有效节省了上下文空间。

压缩时，系统提示词加载 [system compact 提示词](./results/prompts/system-compact.prompt.md)，并在当前上下文末尾追加 [compact 提示词](./results/prompts/compact.prompt.md)，指示 LLM 按特定格式完成压缩。

使用 Sonnet 4 模型。

### IDE 集成

当 Claude Code 在 IDE 环境中使用时，它会读取当前打开文件的路径，为对话提供更多上下文。

这些文件路径随后被整合到 [IDE open file 提示词](./results/prompts/ide-opened-file.prompt.md) 中。

在 IDE 集成状态下，Claude Code 还会通过 MCP 注册一些 IDE 专用工具，例如获取 IDE 中的错误信息、执行代码等。

你可以在 [ide-integration.log](./logs/ide-integration.log) 中看到我们如何引导 Claude Code 使用 IDE 工具修复文件中的 lint 错误。

### Todo 短期记忆管理

在 [system workflow 提示词](./results/prompts/system-workflow.prompt.md) 的"任务管理"部分，定义了一种基于 `TodoWrite` 工具的任务管理方法。

当 `TodoWrite` 执行时，它实际上会在 `~/.claude/todos/` 目录下创建一个 JSON 文件，记录当前对话的 Todos，作为短期记忆。当 Todo 完成时，模型也会使用此工具更新 JSON 文件。

如核心 Agent 工作流部分所述，system reminder end 提示词会动态加载最新的 Todo 列表，使模型能够追踪之前的进度。

### Task/Sub Agent 工作流

Claude Code 设计了一个 Sub Agent 系统，通过加载 [Task Tool](./results/tools/Task.tool.yaml) 实现，使用提示词引导模型在需要执行特定独立任务时通过调用此工具启动 Sub Agent。

Claude Code 的 Sub Agent 作为 Multi Agent 的一种特定形式，具有特殊设计：

1. 始终存在 Main Agent（用户最初交互的对象）的概念。
2. 启动 Sub Agent 时，从主上下文中提取待处理任务，将其作为子上下文的初始提示词。
3. Sub Agent 完成任务后，将最终结果作为工具结果返回给主上下文。

这种设计使 Sub Agent 成为优化主上下文空间的有效方式。在某些独立任务（如"从代码库中查找特定函数实现"）中，多轮 Agent 工具调用/结果交互会产生大量与最终所需结果无关的上下文（例如搜索了被 LLM 阅读后排除的不相关文件）。Sub Agent 可以将这些"脏上下文"隔离在子上下文中，Sub Agent 任务完成后即消失，而主上下文仅保留那一小部分所需结果。

### 总结历史对话

启动 Claude Code 时，它会总结之前的对话。

对应 [Summarize 提示词](./results/prompts/summarize-previous-conversation.prompt.md)。

使用 Haiku 3.5 模型。
