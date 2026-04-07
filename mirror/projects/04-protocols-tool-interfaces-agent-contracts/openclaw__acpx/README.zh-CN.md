<p align="center">
  <img src="assets/001-acpx-banner-a7f01bc059.svg" alt="acpx banner" width="100%" />
</p>

# acpx

[![npm version](https://img.shields.io/npm/v/acpx.svg)](https://www.npmjs.com/package/acpx)
[![npm downloads](https://img.shields.io/npm/dm/acpx.svg)](https://www.npmjs.com/package/acpx)
[![CI](https://github.com/openclaw/acpx/actions/workflows/ci.yml/badge.svg)](https://github.com/openclaw/acpx/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/node/v/acpx.svg)](https://nodejs.org)

> ⚠️ `acpx` 目前处于 alpha 阶段，CLI/运行时接口可能会发生变化。在此工具稳定之前，基于它构建的下游项目可能会出现兼容性问题。

> ACP 覆盖状态：参见 [ACP 规范覆盖路线图](docs/2026-02-19-acp-coverage-roadmap.md)。

你的代理喜欢 acpx！它们讨厌从 PTY 会话中抓取字符 😤

`acpx` 是 [Agent Client Protocol (ACP)](https://agentclientprotocol.com) 的无头 CLI 客户端，因此 AI 代理和编排器可以通过结构化协议与编码代理通信，而无需 PTY 抓取。

一个命令界面即可对接 Pi、OpenClaw ACP、Codex、Claude 以及其他兼容 ACP 的代理。专为命令行上的代理间通信而构建。

- **持久会话**：跨调用存续的多轮对话，按仓库作用域隔离
- **命名会话**：在同一仓库中运行并行工作流（`-s backend`、`-s frontend`）
- **提示词排队**：在一个提示词运行时提交新的提示词，按顺序执行
- **协作式取消命令**：`cancel` 通过队列 IPC 发送 ACP `session/cancel`，不会销毁会话状态
- **软关闭生命周期**：关闭会话但不删除磁盘上的历史记录
- **队列所有者 TTL**：短暂保持队列所有者存活以便后续提示词（`--ttl`）
- **即发即忘**：`--no-wait` 将提示词加入队列后立即返回
- **优雅取消**：`Ctrl+C` 在强制终止前发送 ACP `session/cancel`
- **会话控制**：`set-mode` 和 `set <key> <value>` 对应 `session/set_mode` 和 `session/set_config_option`
- **崩溃重连**：自动检测已终止的代理进程并重新加载会话
- **从文件/标准输入读取提示词**：`--file <path>` 或管道标准输入作为提示词内容
- **配置文件**：全局 + 项目级 JSON 配置，通过 `acpx config show|init` 管理
- **会话检查/历史**：`sessions show` 和 `sessions history --limit <n>`
- **本地状态检查**：`status` 报告运行中/已终止/无会话状态、PID、运行时间、最近提示词
- **客户端方法**：稳定的 `fs/*` 和 `terminal/*` 处理器，支持权限控制和 cwd 沙箱
- **认证握手**：通过环境变量/配置凭据支持稳定的 `authenticate`
- **结构化输出**：类型化的 ACP 消息（思考、工具调用、差异）而非 ANSI 抓取
- **任意 ACP 代理**：内置注册表 + `--agent` 逃生通道用于自定义服务器
- **单次执行模式**：`exec` 用于无状态即发即忘任务
- **实验性流程**：`flow run <file>` 用于跨多个提示词的 TypeScript 工作流模块
- **运行时拥有的流程动作**：shell 支持的动作步骤可以在代理轮次之外准备工作区和其他确定性机制
- **流程工作区隔离**：`acp` 节点可以针对每个步骤指定显式 cwd，使流程能将代理工作限制在一次性 worktree 中

```bash
$ acpx codex sessions new
$ acpx codex "find the flaky test and fix it"

[thinking] Investigating test suite for flaky failures

[tool] Run npm test -- --reporter=verbose (running)
[tool] Run npm test -- --reporter=verbose (completed)
  output:
    ✓ auth.login (0.8s)
    ✗ checkout.submit (timed out after 5000ms)
    ✓ cart.add (0.3s)

[thinking] Found it — checkout.submit has a race condition in the async setup

[tool] Edit src/checkout.test.ts (completed)
  output:
    Success. Updated 1 file.

[tool] Run npm test -- checkout.submit (completed)
  output:
    ✓ checkout.submit (0.4s)

Fixed: added `await` to the setup hook in checkout.submit. The test was
reading stale state from the previous run.

[done] end_turn
```

## 快速设置 -- 告诉你的代理关于 acpx

将下面的代码块复制并粘贴到你的 Pi、OpenClaw、Claude Code 或类似的 agent harness 中。它会安装 acpx，读取技能参考，并了解如何将 ACP 用于所有未来的编码代理任务。

```text
I want you to use acpx to run coding agents over the Agent Client Protocol
(ACP) instead of scraping PTY sessions. Please do the following:

1. Install acpx globally (recommended) or use npx:
   npm install -g acpx@latest

   Or without installing:
   npx acpx@latest

2. Install the acpx skill so you have the full reference available:
   npx acpx@latest --skill install acpx

3. Read the acpx skill reference so you know every command, flag, and
   workflow pattern:
   https://raw.githubusercontent.com/openclaw/acpx/main/skills/acpx/SKILL.md

4. If you need the full CLI reference with all options and examples:
   https://raw.githubusercontent.com/openclaw/acpx/main/docs/CLI.md

From now on, when you need to delegate work to a coding agent, use acpx
instead of spawning raw terminal sessions. For example:
  npx acpx@latest codex "fix the failing tests"
  npx acpx@latest claude "refactor the auth module"
  npx acpx@latest codex exec "one-shot: summarize this repo"
```

## 安装

```bash
npm install -g acpx@latest
```

或在不安装的情况下运行：

```bash
npx acpx@latest codex "fix the tests"
```

无论哪种方式，会话状态都存储在 `~/.acpx/` 中。全局安装会稍快一些，但 `npx acpx@latest` 也能正常工作。

## 代理前提条件

`acpx` 在首次使用时通过 `npx` 自动下载 ACP 适配器。你无需手动安装适配器包。

唯一的前提是你想要使用的底层编码代理：

- `acpx pi` -> Pi Coding Agent: https://github.com/mariozechner/pi
- `acpx openclaw` -> OpenClaw ACP 桥接: https://github.com/openclaw/openclaw
- `acpx codex` -> Codex CLI: https://codex.openai.com
- `acpx claude` -> Claude Code: https://claude.ai/code

其他内置代理文档请参见 [agents/README.md](agents/README.md)。

## 使用示例

```bash
acpx codex sessions new                        # 为当前项目目录创建会话（显式）
acpx codex 'fix the tests'                     # 隐式提示词（通过目录遍历路由）
acpx codex prompt 'fix the tests'              # 显式提示词子命令
echo 'fix flaky tests' | acpx codex            # 从标准输入读取提示词
acpx codex --file prompt.md                    # 从文件读取提示词
acpx codex --file - "extra context"            # 显式标准输入 + 追加参数
acpx codex --no-wait 'draft test migration plan' # 如果会话忙碌则排队不等待
acpx codex cancel                               # 协作式取消正在进行的提示词
acpx codex set-mode auto                        # session/set_mode（适配器定义的模式 ID）
acpx codex set thought_level high               # codex 兼容别名 -> reasoning_effort
acpx exec 'summarize this repo'                # 默认代理快捷方式（codex）
acpx codex exec 'what does this repo do?'      # 单次执行，不保存会话

acpx codex sessions new --name api              # 创建命名会话
acpx codex -s api 'implement token pagination'  # 在命名会话中发送提示词
acpx codex sessions new --name docs             # 创建另一个命名会话
acpx codex -s docs 'rewrite API docs'           # 在另一个命名会话中并行工作

acpx codex sessions              # 列出 codex 命令的会话
acpx codex sessions list         # 显式列表
acpx codex sessions show         # 检查 cwd 会话元数据
acpx codex sessions history      # 显示最近的轮次历史
acpx codex sessions new          # 创建新的 cwd 作用域默认会话
acpx codex sessions new --name api # 创建新的命名会话
acpx codex sessions ensure       # 返回现有作用域会话或创建新会话
acpx codex sessions ensure --name api # 确保命名作用域会话存在
acpx codex sessions close        # 关闭 cwd 作用域默认会话
acpx codex sessions close api    # 关闭 cwd 作用域命名会话
acpx codex status                # 当前会话的本地进程状态

acpx config show                 # 显示已解析的配置（全局 + 项目）
acpx config init                 # 创建 ~/.acpx/config.json 模板
```

主要 harness 示例：

```bash
acpx pi 'review recent changes'
acpx openclaw exec 'summarize active session state' # 内置 OpenClaw ACP 桥接
acpx codex 'fix the failing typecheck'
acpx claude 'refactor auth middleware' # 内置 claude 代理
```

其他受支持的 harness 及其特定说明记录在 [agents/README.md](agents/README.md) 中。

```bash
acpx my-agent 'review this patch'                      # 未知名称 -> 原始命令
acpx --agent './bin/dev-acp --profile ci' 'run checks' # --agent 逃生通道
```

## 实际场景

```bash
# 在专用会话中审查 PR 并自动批准权限
acpx --cwd ~/repos/shop --approve-all codex -s pr-842 \
  'Review PR #842 for regressions and propose a minimal fix'

# 在同一仓库中保持并行工作流
acpx codex -s bugfix 'isolate flaky checkout test'
acpx codex -s release 'draft release notes from recent commits'
```

## 全局选项实践

```bash
acpx --approve-all codex 'apply the patch and run tests'
acpx --approve-reads codex 'inspect repo structure and suggest plan' # 默认模式
acpx --deny-all codex 'explain what you can do without tool access'
acpx --non-interactive-permissions fail codex 'fail instead of deny in non-TTY'

acpx --cwd ~/repos/backend codex 'review recent auth changes'
acpx --format text codex 'summarize your findings'
acpx --format json codex exec 'review changed files'
acpx --format json --json-strict codex exec 'machine-safe JSON only'
acpx flow run ./my-flow.ts --input-file ./flow-input.json
acpx --timeout 1800 flow run ./my-flow.ts
acpx --format quiet codex 'final recommendation only'
acpx --suppress-reads codex exec 'show tool activity without dumping file bodies'

acpx --timeout 90 codex 'investigate intermittent test timeout'
acpx --ttl 30 codex 'keep queue owner alive for quick follow-ups'
acpx --verbose codex 'debug why adapter startup is failing'
```

## Flows

`acpx flow run <file>` 通过 `acpx/flows` 运行时执行 TypeScript 流程模块，并将运行状态持久化到 `~/.acpx/flows/runs/`。

流程用于一次提示词不够的多步骤 ACP 工作：

- `acp` 步骤在 ACP 中保持模型形态的工作
- `action` 步骤处理确定性机制，如 shell 命令或 GitHub 调用
- `compute` 步骤进行本地路由或整形
- `checkpoint` 步骤暂停等待运行时之外的事件

源代码树在 [examples/flows/README.md](examples/flows/README.md) 下包含流程示例：

- 小型示例，如 `echo`、`branch`、`shell`、`workdir` 和 `two-turn`
- 较大的 PR 分诊示例在 [examples/flows/pr-triage/README.md](examples/flows/pr-triage/README.md)
- 回放查看器在 [examples/flows/replay-viewer/README.md](examples/flows/replay-viewer/README.md)，用于在浏览器中检查保存的运行包

示例运行：

```bash
acpx flow run ./my-flow.ts --input-file ./flow-input.json

acpx flow run examples/flows/branch.flow.ts \
  --input-json '{"task":"FIX: add a regression test for the reconnect bug"}'

acpx flow run examples/flows/pr-triage/pr-triage.flow.ts \
  --input-json '{"repo":"openclaw/acpx","prNumber":150}'
```

PR 分诊示例仅是一个示例工作流。如果你对真实仓库运行它，它可能会评论或关闭真实的 GitHub PR。

## 配置文件

`acpx` 按以下顺序读取配置（后者优先）：

1. 全局：`~/.acpx/config.json`
2. 项目：`<cwd>/.acpxrc.json`

CLI 标志始终优先于配置值。

支持的键：

```json
{
  "defaultAgent": "codex",
  "defaultPermissions": "approve-all",
  "nonInteractivePermissions": "deny",
  "authPolicy": "skip",
  "ttl": 300,
  "timeout": null,
  "format": "text",
  "agents": {
    "my-custom": { "command": "./bin/my-acp-server" }
  },
  "auth": {
    "my_auth_method_id": "credential-value"
  }
}
```

使用 `acpx config show` 检查已解析的结果，使用 `acpx config init` 创建全局模板。

## 输出格式

```bash
# text（默认）：带工具更新的人类可读流
acpx codex 'review this PR'

# json：NDJSON 事件，适用于自动化
acpx --format json codex exec 'review this PR' \
  | jq -r 'select(.type=="tool_call") | [.status, .title] | @tsv'

# json-strict：抑制非 JSON 的 stderr 输出（需要 --format json）
acpx --format json --json-strict codex exec 'review this PR'

# quiet：仅输出最终助手文本
acpx --format quiet codex 'give me a 3-line summary'

# 在保持所选输出格式的同时抑制读取内容
acpx --suppress-reads codex exec 'inspect the repo and report tool usage'
```

- `text`：带助手文本和工具更新的人类可读流
- `json`：用于自动化的原始 ACP NDJSON 流
- `quiet`：仅输出最终助手文本
- `--suppress-reads`：在 `text` 和 `json` 输出中将原始读取文件内容替换为 `[read output suppressed]`

JSON 事件包含用于关联的稳定封装：

```json
{
  "eventVersion": 1,
  "sessionId": "abc123",
  "requestId": "req-42",
  "seq": 7,
  "stream": "prompt",
  "type": "tool_call"
}
```

会话控制 JSON 负载（`sessions new|ensure`、`status`）在适配器暴露提供者原生会话 ID 时可能还包含 `runtimeSessionId`。

## 内置代理和自定义服务器

内置代理：

| 代理 | 适配器 | 封装 |
| ---------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `pi` | [pi-acp](https://github.com/svkozak/pi-acp) | [Pi Coding Agent](https://github.com/mariozechner/pi) |
| `openclaw` | 原生 (`openclaw acp`) | [OpenClaw ACP 桥接](https://github.com/openclaw/openclaw) |
| `codex` | [codex-acp](https://github.com/zed-industries/codex-acp) | [Codex CLI](https://codex.openai.com) |
| `claude` | [claude-agent-acp](https://github.com/agentclientprotocol/claude-agent-acp) | [Claude Code](https://claude.ai/code) |
| `gemini` | 原生 (`gemini --acp`) | [Gemini CLI](https://github.com/google/gemini-cli) |
| `cursor` | 原生 (`cursor-agent acp`) | [Cursor CLI](https://cursor.com/docs/cli/acp) |
| `copilot` | 原生 (`copilot --acp --stdio`) | [GitHub Copilot CLI](https://docs.github.com/copilot/how-tos/copilot-chat/use-copilot-chat-in-the-command-line) |
| `droid` | 原生 (`droid exec --output-format acp`) | [Factory Droid](https://www.factory.ai) |
| `iflow` | 原生 (`iflow --experimental-acp`) | [iFlow CLI](https://github.com/iflow-ai/iflow-cli) |
| `kilocode` | `npx -y @kilocode/cli acp` | [Kilocode](https://kilocode.ai) |
| `kimi` | 原生 (`kimi acp`) | [Kimi CLI](https://github.com/MoonshotAI/kimi-cli) |
| `kiro` | 原生 (`kiro-cli-chat acp`) | [Kiro CLI](https://kiro.dev) |
| `opencode` | `npx -y opencode-ai acp` | [OpenCode](https://opencode.ai) |
| `qoder` | 原生 (`qodercli --acp`) | [Qoder CLI](https://docs.qoder.com/cli/acp) |
| `qwen` | 原生 (`qwen --acp`) | [Qwen Code](https://github.com/QwenLM/qwen-code) |
| `trae` | 原生 (`traecli acp serve`) | [Trae CLI](https://docs.trae.cn/cli) |

`factory-droid` 和 `factorydroid` 也会解析到内置的 `droid` 适配器。

其他内置代理文档请参见 [agents/README.md](agents/README.md)。

使用 `--agent` 作为自定义 ACP 服务器的逃生通道：

```bash
acpx --agent ./my-custom-acp-server 'do something'
```

对于仓库本地的 OpenClaw 检出，可以在配置中覆盖内置命令，使 `acpx openclaw ...` 直接启动 ACP 桥接，而不会产生 `pnpm` 包装器的干扰：

```json
{
  "agents": {
    "openclaw": {
      "command": "env OPENCLAW_HIDE_BANNER=1 OPENCLAW_SUPPRESS_NOTES=1 node scripts/run-node.mjs acp --url ws://127.0.0.1:18789 --token-file ~/.openclaw/gateway.token --session agent:main:main"
    }
  }
}
```

## 会话行为

- 提示词命令需要已有的已保存会话记录（通过 `sessions new` 或 `sessions ensure` 创建）。
- 提示词通过从 `cwd`（或 `--cwd`）向上遍历到最近的 git 根目录（含）来路由，选择匹配 `(代理命令, 目录, 可选名称)` 的最近活跃会话。
- 如果未找到 git 根目录，提示词仅匹配精确的 `cwd` 会话（不进行父目录遍历）。
- `-s <name>` 在目录遍历期间选择一个并行命名会话。
- `sessions new [--name <name>]` 为该作用域创建新会话并软关闭前一个会话。
- `sessions ensure [--name <name>]` 是幂等的：返回现有作用域会话或在缺失时创建新会话。
- `sessions close [name]` 软关闭会话：队列所有者/进程被终止，记录以 `closed: true` 保留。
- cwd 作用域的自动恢复会跳过标记为已关闭的会话。
- 提示词提交按会话感知队列。如果提示词正在运行，新提示词将被排队并由正在运行的 `acpx` 进程处理。
- 队列所有者使用空闲 TTL（默认 300 秒）。`--ttl <seconds>` 覆盖此值；`--ttl 0` 使所有者无限期存活。
- `--no-wait` 将提示词提交到队列后立即返回。
- `cancel` 向正在运行的队列所有者进程发送协作式 `session/cancel`，在没有提示词运行时返回成功（`nothing to cancel`）。
- `set-mode` 和 `set` 在队列所有者活跃时通过队列所有者 IPC 路由，否则直接重连以应用 `session/set_mode` 和 `session/set_config_option`。
- `set-mode` 的 `<mode>` 值由适配器定义；不支持的值会被适配器拒绝（通常为 `Invalid params`）。
- `exec` 始终是单次执行，不复用已保存的会话。
- 会话元数据存储在 `~/.acpx/sessions/` 下。
- 每次成功的提示词会将轻量级轮次历史预览（`role`、`timestamp`、`textPreview`）追加到会话元数据中。
- 运行中轮次期间的 `Ctrl+C` 发送 ACP `session/cancel`，短暂等待 `stopReason=cancelled` 后在需要时强制终止。
- 如果已保存会话的 pid 在下次提示词时已终止，`acpx` 会重新启动代理，尝试 `session/load`，如果加载失败则透明地回退到 `session/new`。

## 完整 CLI 参考

参见 [docs/CLI.md](docs/CLI.md)。

## 许可证

MIT
