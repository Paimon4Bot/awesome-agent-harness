# 🌟 Microsoft Learn MCP 服务器
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Microsoft_Learn_MCP-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=microsoft-learn&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D)
[![Install in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-Install_Microsoft_Learn_MCP-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=microsoft-learn&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D&quality=insiders)

> **停止 AI 幻觉。** 让您的 AI 助手（Claude、Cursor、Copilot、Codex 等）直接访问最新的 Microsoft 官方文档。
>
> **✨ 免费。一键安装。无需密钥。**

## 🎯 为什么要安装它？

不要再依赖过时的训练数据或有风险的网页搜索。Learn MCP 服务器可安全、直接地访问 Microsoft 官方文档。

* 🧠 **消除幻觉。**
  防止 AI 凭空编造并不存在的 Azure SDK 方法或虚构的库包。获得真正能够编译的代码。

* 🔌 **即插即用（无需身份验证）。**
  无需 API 密钥、无需登录、无需注册。只需一键安装，即可立刻开始编码。

* 🛡️ **100% 可信且安全。**
  保护您的供应链。与可能抓取不安全博客或恶意站点的通用网页搜索不同，此工具**仅**访问 Microsoft 官方第一方文档。

* 💸 **完全免费。**
  提供高搜索容量，专为流畅、高强度的编码会话而设计。

### ✨ 示例提示词

> "给我用于创建带托管标识的 Azure Container App 的 Azure CLI 命令。"

> "gpt-5.4 在 Azure 欧洲区域可用吗？"

> "你确定这是在 .NET 8 minimal API 中实现 `IHttpClientFactory` 的正确方式吗？"

> "给我展示可运行的 Python 代码，使用 Azure AI Foundry evaluation SDK 执行 harms eval。"

## 🌐 Microsoft Learn MCP Server 端点

任何支持 Model Context Protocol（MCP，模型上下文协议）的 IDE、代理或工具，都可以访问 Microsoft Learn MCP Server。任何兼容客户端都可以连接到以下**远程 MCP 端点**：

```
https://learn.microsoft.com/api/mcp
```

> **注意：** 此 URL 旨在通过 Streamable HTTP **在兼容的 MCP 客户端内部**使用，例如我们在[安装与入门](#-安装与入门)部分中推荐的客户端。它不支持从 Web 浏览器直接访问；如果手动访问，可能会返回 `405 Method Not Allowed` 错误。对于需要自行构建解决方案的开发者，请遵循[构建自定义客户端](#%EF%B8%8F-构建自定义客户端)部分中的强制性指南，以确保实现具有弹性并受到支持。

**标准配置**适用于大多数客户端：

```json
{
  "servers": {
    "microsoft-learn": {
      "type": "http",
      "url": "https://learn.microsoft.com/api/mcp"
    }
  }
}
```

实验性功能请参见下方的[实验性功能](#-实验性功能)部分。

## 🧪 实验性功能

Microsoft Learn MCP Server 提供一些仍在积极开发中的实验性功能。这些功能可能会根据用户反馈和使用模式发生变化或进一步优化。

### OpenAI 兼容端点

对于需要兼容 OpenAI Deep Research 模型的应用程序，可以使用以下 OpenAI 兼容端点：

```
https://learn.microsoft.com/api/mcp/openai-compatible
```

此端点[支持 OpenAI Deep Research 模型](https://platform.openai.com/docs/mcp)，并遵循 OpenAI MCP 规范。

### Token 预算控制

为了管理 token 使用量并控制成本，您可以在 MCP 端点 URL 上附加 `maxTokenBudget` 查询参数。该参数会通过截断内容来限制搜索工具响应中的 token 数量，以满足您指定的预算。

```
https://learn.microsoft.com/api/mcp?maxTokenBudget=2000
```

> **注意：** 这些实验性功能可能会发生变化。欢迎通过我们的 [GitHub Discussions](https://github.com/MicrosoftDocs/mcp/discussions) 提供反馈。

## 🛠️ 当前支持的工具

| Tool Name | Description | Input Parameters |
|-----------|-------------|------------------|
| `microsoft_docs_search` | 对 Microsoft 官方技术文档执行语义搜索 | `query` (string): 用于检索的搜索查询 |
| `microsoft_docs_fetch` | 获取 Microsoft 文档页面并将其转换为 markdown 格式 | `url` (string): 要读取的文档页面 URL |
| `microsoft_code_sample_search` | 搜索 Microsoft/Azure 官方代码片段和示例 | `query` (string): Microsoft/Azure 代码片段的搜索查询<br/>`language` (string, optional): 编程语言筛选器。|

## 💻 Microsoft Learn CLI `preview`

[![npm version](https://img.shields.io/npm/v/@microsoft/learn-cli?style=flat-square&logo=npm&label=npm)](https://www.npmjs.com/package/@microsoft/learn-cli)

[`@microsoft/learn-cli`](https://www.npmjs.com/package/@microsoft/learn-cli) 包让您无需 MCP 客户端，也能在终端中访问同样的工具，包括搜索文档、抓取页面和查找代码示例。

```sh
# 立即运行（无需安装）
npx @microsoft/learn-cli search "azure functions timeout"

# 或全局安装
npm install -g @microsoft/learn-cli
# 然后使用 `mslearn`
mslearn search "azure functions timeout"
```

传入 `--json` 可获得结构化 JSON 输出，便于程序化处理：

```sh
mslearn search "azure openai" --json | jq '.results[].title'
```

完整命令参考请参见 [`cli/README.md`](cli/README.md)。

## 🤖 Agent Skills

[Agent Skills](https://agentskills.io/) 是可移植的指令包，可帮助 AI 代理更高效地使用工具。我们提供了三种技能，用于指导代理何时以及如何使用 Microsoft Learn MCP 工具：

| Skill | Purpose | Best For |
|-------|---------|----------|
| [`microsoft-docs`](skills/microsoft-docs/SKILL.md) | 理解概念、教程、架构、限制 | “X 是如何工作的？”，学习，配置指南 |
| [`microsoft-code-reference`](skills/microsoft-code-reference/SKILL.md) | API 查询、代码示例、验证、错误修复 | 编写代码、查找正确方法、故障排查 |
| [`microsoft-skill-creator`](skills/microsoft-skill-creator/SKILL.md) | 为任意 Microsoft 技术生成自定义代理技能的元技能 | 创建一个技能，以便教会代理了解新的 Azure 库、.NET 功能或其他 Microsoft 技术 |

### 快速设置

这些代理技能与 Learn MCP Server 本身一起打包在 `microsoft-docs` 插件中。如果您使用 Claude Code，请运行以下命令并重启 Claude Code：

```
/plugin install microsoft-docs@claude-plugins-official
```

如果您使用 GitHub Copilot CLI，请运行以下命令：

```
/plugin install microsoftdocs/mcp
```

否则：

1. **先安装 MCP Server**，参见下方的[安装](#-安装与入门)部分
2. **将技能文件夹复制**到项目的 `.github/skills/` 或 `.claude/skills/` 目录：
   - [`microsoft-docs`](skills/microsoft-docs/)：用于概念、教程和事实查询
   - [`microsoft-code-reference`](skills/microsoft-code-reference/)：用于 API 查询、代码示例和故障排查
   - [`microsoft-skill-creator`](skills/microsoft-skill-creator/)：用于生成关于 Microsoft 技术的自定义技能的元技能

### 支持的代理

Agent Skills 可在多种 AI 代理中工作：

- **VS Code**（Insiders）: 启用 `chat.useAgentSkills` 设置
- **GitHub Copilot CLI** 和 **Copilot coding agent**
- **Claude Code**、**Cursor**、**OpenAI Codex** 以及[更多](https://agentskills.io/)

### 我需要哪个技能？

| If you want to... | Install |
|-------------------|---------|
| 覆盖所有 Microsoft 文档使用场景 | 三个技能都安装 |
| 专注编码（API、示例、错误） | 仅安装 `microsoft-code-reference` |
| 专注事实与概念（限制、配置、教程） | 仅安装 `microsoft-docs` |
| 为特定 Microsoft 技术生成自定义技能 | 仅安装 `microsoft-skill-creator` |

## 🔌 安装与入门

Microsoft Learn MCP Server 支持在多个开发环境中快速安装。请选择您偏好的客户端以获得简化的设置流程：

| Client | One-click Installation | MCP Guide |
|--------|----------------------|-------------------|
| **VS Code** | [![Install in VS Code](https://img.shields.io/badge/Install_in-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=microsoft-learn&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D) <br/> 或在扩展中搜索“@mcp learn”以显示“Microsoft Learn”MCP | [VS Code MCP Official Guide](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) |
| **GitHub Copilot CLI** | `/plugin install microsoftdocs/mcp` | |
| **Claude Desktop** | 按照官方指南中的 “Add custom connector” 说明进行操作。 | [Claude Desktop Remote MCP Guide](https://modelcontextprotocol.io/docs/develop/connect-remote-servers) |
| **Claude Code** | `/plugin install microsoft-docs@claude-plugins-official`（包含 MCP server + skills） | [Claude Code Remote MCP Guide](https://code.claude.com/docs/en/mcp) |
| **Visual Studio** | 升级到最新的 VS 2022 或 2026，“Microsoft Learn” MCP 已内置 | [Visual Studio MCP Official Guide](https://learn.microsoft.com/en-us/visualstudio/ide/mcp-servers?view=vs-2022) |
| **Cursor IDE** | [![Install in Cursor](https://img.shields.io/badge/Install_in-Cursor-000000?style=flat-square&logoColor=white)](https://cursor.com/en/install-mcp?name=microsoft-learn&config=eyJuYW1lIjoibWljcm9zb2Z0LWxlYXJuIiwidHlwZSI6Imh0dHAiLCJ1cmwiOiJodHRwczovL2xlYXJuLm1pY3Jvc29mdC5jb20vYXBpL21jcCJ9) | [Cursor MCP Official Guide](https://docs.cursor.com/context/model-context-protocol) |
| **Codex** | `codex mcp add "microsoft-learn" --url "https://learn.microsoft.com/api/mcp"`| [Codex MCP documentation](https://github.com/openai/codex/blob/main/codex-rs/config.md#mcp_servers) |
| **Roo Code** | 打开 [Roo Code Marketplace](https://docs.roocode.com/features/marketplace)，搜索 `Microsoft Learn`，然后点击 `Install` | [Roo Code MCP Official Guide](https://docs.roocode.com/features/mcp/using-mcp-in-roo) |
| **Cline** | 需要手动配置<br/>使用 `"type": "streamableHttp"` | [Cline MCP Official Guide](https://docs.cline.bot/mcp/connecting-to-a-remote-server) |
| **Gemini CLI** | 需要手动配置<br/> <details><summary>View Config</summary>**Note**: Add an `mcpServer` object to `.gemini/settings.json` file<br/><pre>{<br/>  "Microsoft Learn MCP Server": {<br/>     "httpUrl": "https://learn.microsoft.com/api/mcp" <br/>   }<br/>}</pre></details>  | [How to set up your MCP server](https://github.com/google-gemini/gemini-cli/blob/main/docs/tools/mcp-server.md#how-to-set-up-your-mcp-server)|
| **Qwen Code** | 需要手动配置<br/> <details><summary>View Config</summary>**Note**: Add an `mcpServer` object to `.qwen/settings.json` file<br/><pre>{<br/>  "Microsoft Learn MCP Server": {<br/>     "httpUrl": "https://learn.microsoft.com/api/mcp" <br/>   }<br/>}</pre></details>  | [Configure the MCP server in settings.json](https://qwenlm.github.io/qwen-code-docs/en/cli/tutorials/#configure-the-mcp-server-in-settingsjson)|
| **GitHub** | 需要手动配置<br/> <details><summary>View Config</summary>**Note**: Navigate to Settings → Coding agent<br/><pre>{<br/>  "mslearn": {<br/>    "type": "http",<br/>    "url": "https://learn.microsoft.com/api/mcp",<br/>    "tools": [<br/>      "*"<br/>    ]<br/>  }<br/>}</pre></details> |
| **ChatGPT** | 需要手动配置<br/> <details><summary>View Instructions</summary>1. Open ChatGPT in the browser<br/>2. Go to **Settings → Connectors → Advanced settings → Turn Developer mode on**<br/>3. Go back to connectors and click **create**<br/>4. Give the connector a **name**, enter **URL** `https://learn.microsoft.com/api/mcp`, set **authentication** to `No authentication` and **trust** the application<br/>5. Click **create**<br/> </details> | [ChatGPT Official Guide](https://platform.openai.com/docs/guides/developer-mode)|
| **Windsurf** | 需要手动配置<br/> <details><summary>View Config</summary><pre>{<br/>  "mcpServers": {<br/>    "microsoft-learn": {<br/>      "serverUrl": "https://learn.microsoft.com/api/mcp"<br/>    }<br/>  }<br/>}</pre></details>| [Windsurf MCP Guide](https://docs.windsurf.com/windsurf/cascade/mcp) |
| **Kiro** | <details><summary>View Config</summary><pre>{<br/>  "microsoft-learn": {<br/>    "url": "https://learn.microsoft.com/api/mcp"<br/>    }<br/>}</pre> </details>| [Kiro MCP Guide](https://kiro.dev/docs/mcp/index) |

> ### ⚠️ 构建自定义客户端
>
> 如果您的使用场景需要直接的编程式集成，那么必须理解 MCP 是一种**动态协议，而不是静态 API**。可用工具及其架构会持续演进。
>
> 要构建一个在服务更新后仍然不会失效的弹性客户端，您应遵循以下原则：
>
> 1.  **动态发现工具：** 客户端应在运行时从服务器获取当前工具定义（例如，通过 `tools/list`）。**不要硬编码工具名称或参数。**
> 2.  **失败时刷新：** 客户端应处理 `tool/invoke` 调用过程中的错误。如果某个工具调用失败，并出现表明其缺失或架构已更改的错误（例如 HTTP 404 或 400 错误），则客户端应假设缓存已过期，并自动通过调用 `tools/list` 触发刷新。
> 3.  **处理实时更新：** 客户端应监听服务器通知（例如 `listChanged`），并相应刷新其工具缓存。

## ❓ 故障排查

### 💻 系统提示词

即使像 Claude Sonnet 4 这样对工具友好的模型，有时也不会默认调用 MCP 工具；请使用系统提示词来鼓励其使用。

下面是一个 Cursor 规则（系统提示词）示例，它会让 LLM 更频繁地使用 `microsoft-learn`：

```md
## Querying Microsoft Documentation

You have access to MCP tools called `microsoft_docs_search`, `microsoft_docs_fetch`, and `microsoft_code_sample_search` - these tools allow you to search through and fetch Microsoft's latest official documentation and code samples, and that information might be more detailed or newer than what's in your training data set.

When handling questions around how to work with native Microsoft technologies, such as C#, F#, ASP.NET Core, Microsoft.Extensions, NuGet, Entity Framework, the `dotnet` runtime - please use these tools for research purposes when dealing with specific / narrowly defined questions that may occur.
```

### ⚠️ 常见问题

| Issue | Possible Solution |
|-------|-------------------|
| 连接错误 | 检查网络连接，并确认服务器 URL 输入正确 |
| 未返回结果 | 尝试使用更具体的技术术语重新表述查询 |
| 工具未出现在 VS Code 中 | 重启 VS Code，或检查 MCP 扩展是否已正确安装 |
| HTTP status 405 | 当浏览器尝试连接该端点时，会出现方法不允许错误。请改为通过 VS Code GitHub Copilot 或 [MCP Inspector](https://modelcontextprotocol.io/docs/tools/inspector) 使用 MCP Server。 |

### 🆘 获取支持

- [提问并分享想法](https://github.com/MicrosoftDocs/mcp/discussions)
- [创建 issue](https://github.com/MicrosoftDocs/mcp/issues)

## 📚 其他资源

- [Microsoft Learn MCP Server 产品文档](https://learn.microsoft.com/training/support/mcp)
- [Microsoft MCP Servers](https://github.com/microsoft/mcp)
- [Microsoft Learn](https://learn.microsoft.com)
- [Model Context Protocol 规范](https://modelcontextprotocol.io)
