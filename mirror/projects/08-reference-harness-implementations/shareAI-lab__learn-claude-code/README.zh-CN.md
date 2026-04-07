[English](./README.md) | [中文](./README.zh-CN.md) | [日本語](./README-ja.md)
# Learn Claude Code -- 面向真正代理的 Harness 工程

## 模型即代理

在讨论代码之前，我们先明确一件事。

**代理是一个模型。不是框架，不是提示词链，不是拖拽式工作流。**

### 代理是什么

代理是一个神经网络——Transformer、RNN、一个学习到的函数——通过在动作序列数据上经过数十亿次梯度更新训练而成，能够感知环境、推理目标并采取行动以实现这些目标。AI 中"代理"一词一直都是这个意思。一直都是。

人类是代理。一个生物神经网络，经过数百万年进化训练塑造，通过感官感知世界，通过大脑推理，通过身体行动。当 DeepMind、OpenAI 或 Anthropic 说"代理"时，他们的意思自该领域创立以来从未改变：**一个学会了行动的模型。**

证据写在历史中：

- **2013 -- DeepMind DQN 玩 Atari。** 一个单一的神经网络，仅接收原始像素和游戏分数，学会了玩 7 款 Atari 2600 游戏——超越了所有先前的算法，并在其中 3 款上击败了人类专家。到 2015 年，同一架构扩展到[49 款游戏并达到了专业人类测试者的水平](https://www.nature.com/articles/nature14236)，发表在 *Nature* 上。没有针对特定游戏的规则，没有决策树。一个模型，从经验中学习。那个模型就是代理。

- **2019 -- OpenAI Five 征服 Dota 2。** 五个神经网络，在 10 个月内与自己对弈了[45,000 年的 Dota 2](https://openai.com/index/openai-five-defeats-dota-2-world-champions/)，在旧金山的直播中以 2-0 击败了**OG**——当时的 TI8 世界冠军。在随后的公开竞技场中，AI 在 42,729 场比赛中赢得了 99.4%。没有脚本策略，没有元编程的团队协调。模型完全通过自我对弈学会了团队合作、战术和实时适应。

- **2019 -- DeepMind AlphaStar 掌握星际争霸 II。** AlphaStar 在闭门比赛中[以 10-1 击败职业选手](https://deepmind.google/blog/alphastar-mastering-the-real-time-strategy-game-starcraft-ii/)，后来在欧洲服务器上达到了[宗师段位](https://www.nature.com/articles/d41586-019-03298-6)——在 90,000 名玩家中排名前 0.15%。这是一个包含不完全信息、实时决策的游戏，其组合动作空间远超国际象棋和围棋。代理是什么？一个模型。经过训练的，不是脚本化的。

- **2019 -- 腾讯绝悟称霸王者荣耀。** 腾讯 AI Lab 的“绝悟”在世界冠军杯的一场完整 5v5 对局中[击败了 KPL 职业选手](https://www.jiemian.com/article/3371171.html)。在 1v1 模式中，职业选手在 15 场比赛中仅[赢得 1 场，且从未存活超过 8 分钟](https://developer.aliyun.com/article/851058)。训练强度：一天等于 440 个人类年。到 2021 年，绝悟在全英雄池上超越了 KPL 职业选手。没有手工制作的对抗表，没有脚本化的阵容。一个模型，通过自我对弈从零开始学会了整个游戏。

- **2024-2025 -- LLM 代理重塑软件工程。** Claude、GPT、Gemini——在全部人类代码和推理数据上训练的大语言模型——被部署为编码代理。它们阅读代码库、编写实现、调试故障、在团队中协调。其架构与之前的每一个代理完全相同：一个经过训练的模型，被放置在环境中，获得感知和行动的工具。唯一的区别是它们所学到的规模和所解决问题的通用性。

这些里程碑中的每一个都证明了同一个事实：**"代理"从来不是周围的代码。代理始终是模型。**

### 代理不是什么

"代理"这个词已经被整个提示词管道的作坊产业劫持了。

拖拽式工作流构建器。无代码"AI 代理"平台。提示词链编排库。它们都有同一个错觉：用 if-else 分支、节点图和硬编码的路由逻辑把 LLM API 调用连接起来就是"构建代理"。

不是的。它们构建的是鲁布·戈德堡机械——一个过度工程化、脆弱的过程式规则管道，中间塞了一个 LLM 作为花哨的文本补全节点。那不是代理，那是一个自命不凡的 shell 脚本。

**提示词管道"代理"是不训练模型的程序员的幻想。** 他们试图通过堆叠过程式逻辑来暴力实现智能——庞大的规则树、节点图、提示词链瀑布——并祈祷足够多的胶水代码能以某种方式涌现出自主行为。不会的。你无法通过工程手段达到自主性。自主性是学习来的，不是编程出来的。

那些系统从一开始就是死的：脆弱、不可扩展、从根本上无法泛化。它们是 GOFAI（老式人工智能）的现代复活——该领域几十年前就抛弃的符号规则系统，现在喷上了一层 LLM 的漆。包装不同，死路一条。

### 思维转变：从"开发代理"到开发 Harness

当有人说"我在开发代理"时，他们只能是以下两种情况之一：

**1. 训练模型。** 通过强化学习、微调、RLHF 或其他基于梯度的方法调整权重。收集任务过程数据——在真实领域中感知、推理和行动的实际序列——并用它来塑造模型的行为。这就是 DeepMind、OpenAI、腾讯 AI Lab 和 Anthropic 所做的事情。这是真正意义上的代理开发。

**2. 构建 harness。** 编写代码，为模型提供一个可操作的环境。这是大多数人在做的事，也是本仓库的重点。

harness 是代理在特定领域中运行所需的一切：

```
Harness = 工具 + 知识 + 观测 + 动作接口 + 权限

    工具：         文件 I/O、shell、网络、数据库、浏览器
    知识：         产品文档、领域参考、API 规范、风格指南
    观测：         git diff、错误日志、浏览器状态、传感器数据
    动作：         CLI 命令、API 调用、UI 交互
    权限：         沙箱、审批工作流、信任边界
```

模型做决策。harness 做执行。模型做推理。harness 提供上下文。模型是驾驶员。harness 是车辆。

**编码代理的 harness 是其 IDE、终端和文件系统访问。** 农业代理的 harness 是其传感器阵列、灌溉控制和天气数据源。酒店代理的 harness 是其预订系统、住客沟通渠道和设施管理 API。代理——智能体、决策者——始终是模型。harness 因领域而异。代理在领域间泛化。

本仓库教你构建车辆。用于编码的车辆。但这些设计模式适用于任何领域：农业管理、酒店运营、制造业、物流、医疗、教育、科学研究。任何需要被感知、推理和行动的任务——代理都需要一个 harness。

### Harness 工程师真正在做什么

如果你正在阅读这个仓库，你可能是一名 harness 工程师——这是一件很有力量的事情。以下是你真正的工作：

- **实现工具。** 给代理双手。文件读写、shell 执行、API 调用、浏览器控制、数据库查询。每个工具都是代理在其环境中可以采取的一个行动。将它们设计为原子的、可组合的、描述良好的。

- **整理知识。** 给代理领域专业知识。产品文档、架构决策记录、风格指南、法规要求。按需加载（s05），而非预先加载。代理应该知道有什么可用，并在需要时自行拉取。

- **管理上下文。** 给代理干净的内存。子代理隔离（s04）防止噪声泄漏。上下文压缩（s06）防止历史记录溢出。任务系统（s07）将目标持久化到单次对话之外。

- **控制权限。** 给代理边界。沙箱化文件访问。对破坏性操作要求审批。在代理和外部系统之间强制执行信任边界。这是安全工程与 harness 工程交汇的地方。

- **收集任务过程数据。** 代理在你的 harness 中执行的每个动作序列都是训练信号。来自真实部署的感知-推理-行动轨迹是微调下一代代理模型的原始材料。你的 harness 不仅服务于代理——它可以帮助改进代理。

你不是在编写智能。你是在构建智能所栖居的世界。那个世界的质量——代理能多清晰地感知、能多精确地行动、可用知识有多丰富——直接决定了智能能多有效地表达自己。

**构建优秀的 harness。代理会完成其余的工作。**

### 为什么选择 Claude Code——Harness 工程的典范课程

为什么本仓库专门解析 Claude Code？

因为 Claude Code 是我们见过的最优雅、最完整的代理 harness。不是因为某个巧妙的技巧，而是因为它*没有*做的事情：它不试图成为代理。它不强加死板的工作流。它不用复杂的决策树来质疑模型。它为模型提供工具、知识、上下文管理和权限边界——然后退居一旁。

看看 Claude Code 的本质，剥到最核心：

```
Claude Code = 一个代理循环
            + 工具（bash、read、write、edit、glob、grep、browser...）
            + 按需技能加载
            + 上下文压缩
            + 生成子代理
            + 带依赖图的任务系统
            + 带异步邮箱的团队协调
            + 用于并行执行的 worktree 隔离
            + 权限治理
```

就是这样。这就是整个架构。每个组件都是一个 harness 机制——为代理栖居而构建的世界的一部分。代理本身？它是 Claude。一个由 Anthropic 在全部人类推理和代码上训练的模型。harness 没有让 Claude 变聪明。Claude 本来就聪明。harness 给了 Claude 双手、眼睛和工作空间。

这就是为什么 Claude Code 是理想的教学对象：**它展示了当你信任模型并将工程精力集中在 harness 上时会发生什么。** 本仓库中的每个会话（s01-s12）都逆向工程了 Claude Code 架构中的一个 harness 机制。到最后，你不仅理解 Claude Code 如何工作，还理解适用于任何领域中任何代理的 harness 工程的通用原则。

教训不是"复制 Claude Code"。教训是：**最好的代理产品是由理解自己工作是 harness 而非智能的工程师构建的。**

---

## 愿景：让真正的代理充满宇宙

这不仅仅是关于编码代理。

人类执行复杂的、多步骤的、需要判断力的工作的每一个领域，都是代理可以运作的领域——只要有合适的 harness。本仓库中的模式是通用的：

```
物业管理代理    = 模型 + 物业传感器 + 维护工具 + 租户通讯
农业代理        = 模型 + 土壤/天气数据 + 灌溉控制 + 作物知识
酒店运营代理    = 模型 + 预订系统 + 客户渠道 + 设施 API
医学研究代理    = 模型 + 文献搜索 + 实验室仪器 + 方案文档
制造业代理      = 模型 + 生产线传感器 + 质量控制 + 物流
教育代理        = 模型 + 课程知识 + 学生进度 + 评估工具
```

循环始终相同。工具变了。知识变了。权限变了。代理——模型——泛化了。

每一位阅读本仓库的 harness 工程师都在学习远超软件工程的适用模式。你正在学习为智能、自动化的未来构建基础设施。每一个部署在真实领域中的精心设计的 harness，都是代理可以感知、推理和行动的又一个地方。

先填满车间。然后是农场、医院、工厂。然后是城市。然后是整个星球。

**Bash 就是你需要的一切。真正的代理是宇宙所需要的一切。**

---

```
                    代理模式
                    =================

    用户 --> messages[] --> LLM --> 响应
                                      |
                            stop_reason == "tool_use"?
                           /                          \
                         是                           否
                          |                             |
                    执行工具                       返回文本
                    追加结果
                    循环回去 -----------------> messages[]

    这就是最小循环。每个 AI 代理都需要这个循环。
    模型决定何时调用工具，何时停止。
    代码只执行模型的请求。
    本仓库教你构建围绕这个循环的一切——
    让代理在特定领域中有效的 harness。
```

**12 个渐进式会话，从简单循环到隔离自主执行。**
**每个会话添加一个 harness 机制。每个机制有一个座右铭。**

> **s01** &nbsp; *"一个循环 & Bash 就是你需要的全部"* &mdash; 一个工具 + 一个循环 = 一个代理
>
> **s02** &nbsp; *"添加工具意味着添加一个处理器"* &mdash; 循环不变；新工具注册到分发映射
>
> **s03** &nbsp; *"没有计划的代理会漂移"* &mdash; 先列出步骤，再执行；完成率翻倍
>
> **s04** &nbsp; *"分解大任务；每个子任务获得干净的上下文"* &mdash; 子代理使用独立的 messages[]，保持主对话清洁
>
> **s05** &nbsp; *"按需加载知识，而非预先加载"* &mdash; 通过 tool_result 注入，而非系统提示词
>
> **s06** &nbsp; *"上下文会填满；你需要腾出空间的方法"* &mdash; 三层压缩策略实现无限会话
>
> **s07** &nbsp; *"将大目标分解为小任务，排序并持久化到磁盘"* &mdash; 基于文件的任务图带依赖关系，为多代理协作奠定基础
>
> **s08** &nbsp; *"在后台运行慢操作；代理继续思考"* &mdash; 守护线程运行命令，完成时注入通知
>
> **s09** &nbsp; *"当任务太大无法独自完成时，委派给队友"* &mdash; 持久队友 + 异步邮箱
>
> **s10** &nbsp; *"队友需要共享的通信规则"* &mdash; 一个请求-响应模式驱动所有协商
>
> **s11** &nbsp; *"队友自己扫描看板并认领任务"* &mdash; 无需主管逐一分配
>
> **s12** &nbsp; *"各自在自己的目录中工作，互不干扰"* &mdash; 任务管理目标，worktree 管理目录，通过 ID 绑定

---

## 核心模式

```python
def agent_loop(messages):
    while True:
        response = client.messages.create(
            model=MODEL, system=SYSTEM,
            messages=messages, tools=TOOLS,
        )
        messages.append({"role": "assistant",
                         "content": response.content})

        if response.stop_reason != "tool_use":
            return

        results = []
        for block in response.content:
            if block.type == "tool_use":
                output = TOOL_HANDLERS[block.name](**block.input)
                results.append({
                    "type": "tool_result",
                    "tool_use_id": block.id,
                    "content": output,
                })
        messages.append({"role": "user", "content": results})
```

每个会话在这个循环之上叠加一个 harness 机制——而不改变循环本身。循环属于代理。机制属于 harness。

## 范围（重要）

本仓库是一个 0->1 的 harness 工程学习项目——构建围绕代理模型的环境。
它有意简化或省略了几个生产机制：

- 完整的事件/hook 总线（例如 PreToolUse、SessionStart/End、ConfigChange）。
  s12 仅包含一个用于教学的最小追加式生命周期事件流。
- 基于规则的权限治理和信任工作流
- 会话生命周期控制（resume/fork）和高级 worktree 生命周期控制
- 完整的 MCP 运行时细节（传输/OAuth/资源订阅/轮询）

请将本仓库中的团队 JSONL 邮箱协议视为教学实现，而非对任何特定生产内部机制的主张。

## 快速开始

```sh
git clone https://github.com/shareAI-lab/learn-claude-code
cd learn-claude-code
pip install -r requirements.txt
cp .env.example .env   # 在 .env 中填入你的 ANTHROPIC_API_KEY

python agents/s01_agent_loop.py       # 从这里开始
python agents/s12_worktree_task_isolation.py  # 完整进阶终点
python agents/s_full.py               # 毕业项目：所有机制组合
```

### Web 平台

交互式可视化、步骤图、源码查看器和文档。

```sh
cd web && npm install && npm run dev   # http://localhost:3000
```

## 学习路径

```
阶段 1: 循环                          阶段 2: 规划与知识
==================                   ==============================
s01  代理循环                [1]     s03  TodoWrite               [5]
     while + stop_reason                  TodoManager + 提醒
     |                                    |
     +-> s02  工具调用            [4]     s04  子代理              [5]
              分发映射: name->handler     每个子代理独立的 messages[]
                                              |
                                         s05  技能               [5]
                                              SKILL.md 通过 tool_result
                                              |
                                         s06  上下文压缩          [5]
                                              三层压缩策略

阶段 3: 持久化                        阶段 4: 团队
==================                   =====================
s07  任务                    [8]     s09  代理团队             [9]
     基于文件的 CRUD + 依赖图            队友 + JSONL 邮箱
     |                                    |
s08  后台任务                [6]     s10  团队协议             [12]
     守护线程 + 通知队列                  关闭 + 计划审批 FSM
                                          |
                                     s11  自主代理            [14]
                                          空闲循环 + 自动认领
                                     |
                                     s12  Worktree 隔离       [16]
                                          任务协调 + 可选隔离执行通道

                                     [N] = 工具数量
```

## 架构

```
learn-claude-code/
|
|-- agents/                        # Python 参考实现 (s01-s12 + s_full 毕业项目)
|-- docs/{en,zh,ja}/               # 以心智模型为先的文档（3 种语言）
|-- web/                           # 交互式学习平台 (Next.js)
|-- skills/                        # s05 的技能文件
+-- .github/workflows/ci.yml      # CI: 类型检查 + 构建
```

## 文档

以心智模型为先：问题、解决方案、ASCII 图、最简代码。
提供[英文](./docs/en/) | [中文](./docs/zh/) | [日本語](./docs/ja/)。

| 会话 | 主题 | 座右铭 |
|---------|-------|-------|
| [s01](./docs/zh/s01-the-agent-loop.md) | 代理循环 | *一个循环 & Bash 就是你需要的全部* |
| [s02](./docs/zh/s02-tool-use.md) | 工具调用 | *添加工具意味着添加一个处理器* |
| [s03](./docs/zh/s03-todo-write.md) | TodoWrite | *没有计划的代理会漂移* |
| [s04](./docs/zh/s04-subagent.md) | 子代理 | *分解大任务；每个子任务获得干净的上下文* |
| [s05](./docs/zh/s05-skill-loading.md) | 技能 | *按需加载知识，而非预先加载* |
| [s06](./docs/zh/s06-context-compact.md) | 上下文压缩 | *上下文会填满；你需要腾出空间的方法* |
| [s07](./docs/zh/s07-task-system.md) | 任务 | *将大目标分解为小任务，排序并持久化到磁盘* |
| [s08](./docs/zh/s08-background-tasks.md) | 后台任务 | *在后台运行慢操作；代理继续思考* |
| [s09](./docs/zh/s09-agent-teams.md) | 代理团队 | *当任务太大无法独自完成时，委派给队友* |
| [s10](./docs/zh/s10-team-protocols.md) | 团队协议 | *队友需要共享的通信规则* |
| [s11](./docs/zh/s11-autonomous-agents.md) | 自主代理 | *队友自己扫描看板并认领任务* |
| [s12](./docs/zh/s12-worktree-task-isolation.md) | Worktree + 任务隔离 | *各自在自己的目录中工作，互不干扰* |

## 接下来——从理解到交付

完成 12 个会话后，你将从里到外理解 harness 工程。有两种方式将知识付诸实践：

### Kode Agent CLI -- 开源编码代理 CLI

> `npm i -g @shareai-lab/kode`

技能 & LSP 支持、Windows 兼容、可插拔 GLM / MiniMax / DeepSeek 等开放模型。安装即用。

GitHub: **[shareAI-lab/Kode-cli](https://github.com/shareAI-lab/Kode-cli)**

### Kode Agent SDK -- 在你的应用中嵌入代理能力

官方 Claude Code Agent SDK 在底层与完整的 CLI 进程通信——每个并发用户意味着一个独立的终端进程。Kode SDK 是一个独立库，没有每用户进程开销，可嵌入后端、浏览器扩展、嵌入式设备或任何运行时。

GitHub: **[shareAI-lab/Kode-agent-sdk](https://github.com/shareAI-lab/Kode-agent-sdk)**

---

## 姊妹仓库：从*按需会话*到*始终在线助手*

本仓库教授的 harness 是**用完即弃**的——打开终端，给代理一个任务，完成后关闭，下次会话从零开始。这就是 Claude Code 的模式。

[OpenClaw](https://github.com/openclaw/openclaw) 证明了另一种可能性：在相同的代理核心之上，两个 harness 机制将代理从"戳一下才动"变成"每 30 秒醒来一次找活干"：

- **心跳** -- 每 30 秒 harness 给代理发一条消息检查是否有事可做。没事？继续睡。有事？立即行动。
- **定时任务** -- 代理可以调度自己的未来任务，到期自动执行。

加上多通道 IM 路由（WhatsApp / Telegram / Slack / Discord，13+ 平台）、持久上下文记忆和 Soul 人格系统，代理从一次性工具变成了始终在线的个人 AI 助手。

**[claw0](https://github.com/shareAI-lab/claw0)** 是我们的配套教学仓库，从头拆解这些 harness 机制：

```
claw 代理 = 代理核心 + 心跳 + 定时任务 + IM 聊天 + 记忆 + 灵魂
```

```
learn-claude-code                   claw0
(代理 harness 核心:                (主动式始终在线 harness:
 循环、工具、规划、                  心跳、定时任务、IM 通道、
 团队、worktree 隔离)               记忆、soul 人格)
```

## 关于
<img width="260" src="assets/001-fe8b852b-97da-4061-a467-9694906b5edf-b13d098bf6.jpg" /><br>

微信扫码关注我们，
或在 X 上关注: [shareAI-Lab](https://x.com/baicai003)

## 许可证

MIT

---

**模型是代理。代码是 harness。构建优秀的 harness。代理会完成其余的工作。**

**Bash 就是你需要的一切。真正的代理是宇宙所需要的一切。**
