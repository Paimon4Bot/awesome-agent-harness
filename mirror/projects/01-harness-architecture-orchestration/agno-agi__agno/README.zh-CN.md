<div align="center" id="top">
  <a href="https://agno.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://agno-public.s3.us-east-1.amazonaws.com/assets/logo-dark.svg">
      <source media="(prefers-color-scheme: light)" srcset="https://agno-public.s3.us-east-1.amazonaws.com/assets/logo-light.svg">
      <img src="https://agno-public.s3.us-east-1.amazonaws.com/assets/logo-light.svg" alt="Agno">
    </picture>
  </a>
</div>

<p align="center">
  大规模构建、运行和管理代理式软件。
</p>

<div align="center">
  <a href="https://docs.agno.com">文档</a>
  <span>&nbsp;•&nbsp;</span>
  <a href="https://github.com/agno-agi/agno/tree/main/cookbook">Cookbook</a>
  <span>&nbsp;•&nbsp;</span>
  <a href="https://docs.agno.com/first-agent">快速开始</a>
  <span>&nbsp;•&nbsp;</span>
  <a href="https://www.agno.com/discord">Discord</a>
</div>

## 什么是 Agno

Agno 是代理式软件的运行时。构建代理、团队和工作流。将它们作为可扩展的服务运行。在生产环境中监控和管理它们。

| 层级 | 功能 |
|-------|--------------|
| **框架** | 构建带有记忆、知识、安全护栏和 100+ 集成的代理、团队和工作流。 |
| **运行时** | 使用无状态、会话作用域的 FastAPI 后端在生产环境中提供服务。 |
| **控制平面** | 使用 [AgentOS UI](https://os.agno.com) 测试、监控和管理你的系统。 |

## 快速开始

用大约 20 行代码构建一个有状态、可使用工具的代理，并将其作为生产 API 提供。

```python
from agno.agent import Agent
from agno.db.sqlite import SqliteDb
from agno.models.anthropic import Claude
from agno.os import AgentOS
from agno.tools.mcp import MCPTools

agno_assist = Agent(
    name="Agno Assist",
    model=Claude(id="claude-sonnet-4-6"),
    db=SqliteDb(db_file="agno.db"),
    tools=[MCPTools(url="https://docs.agno.com/mcp")],
    add_history_to_context=True,
    num_history_runs=3,
    markdown=True,
)

agent_os = AgentOS(agents=[agno_assist], tracing=True)
app = agent_os.get_app()
```

运行：

```bash
export ANTHROPIC_API_KEY="***"

uvx --python 3.12 \
  --with "agno[os]" \
  --with anthropic \
  --with mcp \
  fastapi dev agno_assist.py
```

大约 20 行代码，你就能获得：
- 一个带有流式响应的有状态代理
- 按用户、按会话的隔离
- 一个生产级 API，地址为 http://localhost:8000
- 原生追踪

连接到 [AgentOS UI](https://os.agno.com) 来监控、管理和测试你的代理。

1. 打开 [os.agno.com](https://os.agno.com) 并登录。
2. 点击顶部导航中的 **"Add new OS"**。
3. 选择 **"Local"** 以连接本地 AgentOS。
4. 输入你的端点 URL（默认：`http://localhost:8000`）。
5. 命名为 "Local AgentOS"。
6. 点击 **"Connect"**。

https://github.com/user-attachments/assets/75258047-2471-4920-8874-30d68c492683

打开 Chat，选择你的代理，然后提问：

> What is Agno?

代理会从 Agno MCP 服务器检索上下文，并给出有依据的答案。

https://github.com/user-attachments/assets/24c28d28-1d17-492c-815d-810e992ea8d2

你可以使用完全相同的架构在生产环境中运行多代理系统。

## 为什么选择 Agno？

代理式软件带来了三个根本性的转变。

### 全新的交互模型

传统软件接收请求并返回响应。代理则实时流式传输推理过程、工具调用和结果。它们可以在执行中途暂停，等待批准，然后稍后恢复。

Agno 将流式传输和长时间运行的执行视为一等公民能力。

### 全新的治理模型

传统系统执行预先编写的预定义决策逻辑。代理则动态选择行动。有些行动风险较低，有些需要用户批准，有些则需要管理员权限。

Agno 让你在代理定义中指定谁来决定什么，支持：

- 审批工作流
- 人在回路
- 审计日志
- 运行时强制执行

### 全新的信任模型

传统系统被设计为可预测的。每条执行路径都是预先定义的。代理则将概率推理引入执行路径。

Agno 将信任构建到引擎本身：

- 安全护栏作为执行的一部分运行
- 评估集成到代理循环中
- 追踪和审计日志是一等公民能力

## 为生产而构建

Agno 运行在你的基础设施上，而不是我们的。

- 无状态、可水平扩展的运行时。
- 50+ 个 API 和后台执行。
- 按用户和按会话的隔离。
- 运行时审批强制执行。
- 原生追踪和完整可审计性。
- 会话、记忆、知识和追踪存储在你的数据库中。

你拥有系统。你拥有数据。你定义规则。

## 你可以构建什么

Agno 驱动真实的代理式系统，它们都基于上述相同的基本组件构建。

- [**Pal →**](https://github.com/agno-agi/pal) 一个学习你偏好的个人代理。
- [**Dash →**](https://github.com/agno-agi/dash) 一个基于六层上下文的自学习数据代理。
- [**Scout →**](https://github.com/agno-agi/scout) 一个管理企业上下文知识的自学习上下文代理。
- [**Gcode →**](https://github.com/agno-agi/gcode) 一个会随着时间推移不断改进的后 IDE 时代编程代理。
- [**Investment Team →**](https://github.com/agno-agi/investment-team) 一个通过辩论并分配资本的多代理投资委员会。

单个代理。协调的团队。结构化的工作流。全部基于同一架构构建。

## 开始使用

1. [阅读文档](https://docs.agno.com)
2. [构建你的第一个代理](https://docs.agno.com/first-agent)
3. 探索 [cookbook](https://github.com/agno-agi/agno/tree/main/cookbook)

## IDE 集成

将 Agno 文档作为来源添加到你的编程工具中：

**Cursor：** Settings → Indexing & Docs → 添加 `https://docs.agno.com/llms-full.txt`

同样适用于 VSCode、Windsurf 和类似工具。

## 贡献

参见[贡献指南](https://github.com/agno-agi/agno/blob/main/CONTRIBUTING.md)。

## 遥测

Agno 会记录使用的模型提供商信息，以便优先安排更新。可通过 `AGNO_TELEMETRY=false` 禁用。

<p align="right"><a href="#top">↑ 回到顶部</a></p>
