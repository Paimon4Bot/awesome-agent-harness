# 🌟 Microsoft MCP 服务器

## 📘 什么是 MCP？

**Model Context Protocol（MCP）** 是一种开放协议，用于标准化应用程序向大语言模型（LLM）提供上下文的方式。它使 AI 应用能够以一致的方式连接各种数据源和工具，从而增强其能力与灵活性。MCP 采用客户端-服务器架构：

- **MCP Hosts**：发起连接的应用程序，例如 AI 助手或 IDE。
- **MCP Clients**：宿主应用中的连接器，与服务器保持 1:1 连接。
- **MCP Servers**：通过标准化 MCP 提供上下文和能力的服务。

更多详情，请访问 [官方 MCP 网站](https://modelcontextprotocol.io)。

## 📁 此仓库构建了哪些 MCP 服务器？

此仓库包含面向 Microsoft MCP Server 贡献者的核心库、测试框架、工程系统、流水线与工具，用于统一工程投入，并减少重复建设与分叉：

| MCP Server           |  README              | Source Code             |    CHANGELOG          | Releases             | Documentation             | Troubleshooting             | Support             |
|:---------------------|:--------------------:|:-----------------------:|:---------------------:|:--------------------:|:-------------------------:|:---------------------------:|:-------------------:|
| Azure MCP            | [Azure MCP README]   | [Azure MCP Source Code] | [Azure MCP CHANGELOG] | [Azure MCP Releases] | [Azure MCP Documentation] | [Azure MCP Troubleshooting] | [Azure MCP Support] |
| Microsoft Fabric MCP | [Fabric MCP README]  | [Fabric MCP Source Code] | [Fabric MCP CHANGELOG] | [Fabric MCP Releases] | [Fabric Documentation] | [Fabric MCP Troubleshooting] | [Fabric MCP Support] |

[Azure MCP README]: assets/001-readme-1cc2c2aac8.md
[Azure MCP CHANGELOG]: assets/002-changelog-2a9a22bcbc.md
[Azure MCP Source Code]: https://github.com/microsoft/mcp/blob/main/servers/Azure.Mcp.Server
[Azure MCP Releases]: assets/003-releases-e4f8a3ba45.html
[Azure MCP Documentation]: assets/004-azure-mcp-server-b433adfd5c.html
[Azure MCP Troubleshooting]: assets/005-troubleshooting-630b7c0b09.md
[Azure MCP Support]: assets/006-support-d4c28ec82a.md

[Fabric MCP README]: assets/007-readme-b208a94ddd.md
[Fabric MCP CHANGELOG]: assets/008-changelog-3ed8679a7e.md
[Fabric MCP Source Code]: https://github.com/microsoft/mcp/blob/main/servers/Fabric.Mcp.Server
[Fabric MCP Releases]: assets/009-releases-a7851f8391.html
[Fabric Documentation]: assets/010-fabric-2043b0064a.html
[Fabric MCP Troubleshooting]: assets/011-troubleshooting-d342badf30.md
[Fabric MCP Support]: assets/012-support-908249ae14.md

## 📚 Microsoft 提供了哪些 MCP 服务器？

### <img height="18" width="18" src="https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/acom_social_icon_azure" alt="Microsoft Azure Logo" /> Azure
- **REPOSITORY**: [microsoft/mcp](https://github.com/microsoft/mcp/tree/main/servers/Azure.Mcp.Server#readme)
- **DESCRIPTION**: 单个服务器中提供所有 Azure MCP 工具。Azure MCP Server 实现了 MCP 规范，在 AI 智能体与 Azure 服务之间建立无缝连接。Azure MCP Server 可以单独使用，也可以与 VS Code 中的 GitHub Copilot for Azure 扩展配合使用。
- **CATEGORY**: `CLOUD AND INFRASTRUCTURE`
- **TYPE**: `Local`
- **INSTALL**: [![Install Azure MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode:extension/ms-azuretools.vscode-azure-mcp-server) [![Install Azure MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode-insiders:extension/ms-azuretools.vscode-azure-mcp-server) [![Install Azure MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=github-copilot-azure.GitHubCopilotForAzure2022) [![Install Azure MCP in IntelliJ](https://img.shields.io/badge/IntelliJ%20IDEA-1495b1?style=flat-square&logo=intellijidea&logoColor=white)](https://plugins.jetbrains.com/plugin/8053) [![Install Azure MCP in Eclipse](https://img.shields.io/badge/Eclipse-b6ae1d?style=flat-square&logo=eclipse&logoColor=white)](https://marketplace.eclipse.org/content/azure-toolkit-eclipse)

### ✨ Microsoft Foundry
- **DOCUMENTATION**: [Get started with Foundry MCP Server](https://learn.microsoft.com/azure/ai-foundry/mcp/get-started?view=foundry&tabs=user)
- **DESCRIPTION**: 面向 Microsoft Foundry 的 Model Context Protocol 服务器，提供一组统一的工具，覆盖模型、知识、评估等能力。
- **CATEGORY**: `CLOUD AND INFRASTRUCTURE`
- **TYPE**: `REMOTE` - `https://mcp.ai.azure.com`
- **INSTALL**: [![Install Microsoft Foundry MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22foundry-mcp-remote%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.ai.azure.com%22%7D) [![Install Microsoft Foundry in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://vscode.dev/redirect?url=vscode-insiders:mcp/install?%7B%22name%22%3A%22foundry-mcp-remote%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.ai.azure.com%22%7D)

### <img height="18" width="18" src="assets/013-1062064-products-1-a2b6210f39.2-24x24" alt="Microsoft Azure DevOps Logo" /> Azure DevOps
- **REPOSITORY**: [Azure DevOps MCP Server](https://github.com/microsoft/azure-devops-mcp)
- **DESCRIPTION**: 这个 TypeScript 项目提供了一个适用于 Azure DevOps 的本地 MCP 服务器，使你可以直接从代码编辑器执行各种 Azure DevOps 任务。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Azure DevOps in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=ado&type=stdio&command=npx&args=%5B%22-y%22%2C%22%40azure-devops%2Fmcp%22%2C%22%24%7Binput%3Aado_org%7D%22%5D&inputs=%5B%7B%22id%22%3A%22ado_org%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Azure%20DevOps%20organization%20name%20(e.g.%20contoso)%22%7D%5D) [![Install Azure DevOps in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=ado&quality=insiders&type=stdio&command=npx&args=%5B%22-y%22%2C%22%40azure-devops%2Fmcp%22%2C%22%24%7Binput%3Aado_org%7D%22%5D&inputs=%5B%7B%22id%22%3A%22ado_org%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Azure%20DevOps%20organization%20name%20(e.g.%20contoso)%22%7D%5D) [![Install Azure DevOps in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://github.com/microsoft/azure-devops-mcp/blob/main/docs/GETTINGSTARTED.md#%EF%B8%8F-visual-studio-2022--github-copilot)

### ☸️ Azure Kubernetes Service (AKS)
- **REPOSITORY**: [Azure/aks-mcp](https://github.com/Azure/aks-mcp)
- **DESCRIPTION**: 该 MCP 服务器使 AI 助手能够与 Azure Kubernetes Service（AKS）集群交互。它充当 AI 工具与 AKS 之间的桥梁，将自然语言请求转换为 AKS 操作，并以 AI 工具可理解的格式返回结果。
- **CATEGORY**: `CLOUD AND INFRASTRUCTURE`
- **TYPE**: `Local`
- **INSTALL**: [![Install AKS MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode:extension/ms-kubernetes-tools.vscode-aks-tools) [![Install AKS MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode-insiders:extension/ms-kubernetes-tools.vscode-aks-tools) [![Install AKS MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://github.com/Azure/aks-mcp)

### <img height="18" width="18" src="assets/014-github-mark-ea2971cee799-20edf7b4fc.png" alt="GitHub Logo" /> GitHub
- **REPOSITORY**: [github/github-mcp-server](https://github.com/github/github-mcp-server)
- **DESCRIPTION**: 通过安全的 API 集成访问 GitHub 仓库、议题和拉取请求。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `REMOTE` - `https://api.githubcopilot.com/mcp`
- **INSTALL**: [![Install GitHub MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=github&config=%7B%22type%22%3A%20%22http%22%2C%22url%22%3A%20%22https%3A%2F%2Fapi.githubcopilot.com%2Fmcp%2F%22%7D) [![Install GitHub MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=github&config=%7B%22type%22%3A%20%22http%22%2C%22url%22%3A%20%22https%3A%2F%2Fapi.githubcopilot.com%2Fmcp%2F%22%7D&quality=insiders) [![Install GitHub MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22github%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.githubcopilot.com%2Fmcp%2F%22%7D)

### <img height="18" width="18" src="assets/014-github-mark-ea2971cee799-20edf7b4fc.png" alt="GitHub Logo" /> GitHub Awesome-Copilot
- **REPOSITORY**: [github/awesome-copilot](https://github.com/github/awesome-copilot)
- **DESCRIPTION**: 由社区贡献的说明、提示词和配置，帮助你最大化发挥 GitHub Copilot 的价值。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Awesome Copilot MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://aka.ms/awesome-copilot/mcp/vscode) [![Install Awesome Copilot MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://aka.ms/awesome-copilot/mcp/vscode-insiders) [![Install in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/awesome-copilot/mcp/vs)

### 📝 Markitdown
- **REPOSITORY**: [microsoft/markitdown](https://github.com/microsoft/markitdown)
- **DESCRIPTION**: 一个专门用于 Markdown 处理和操作的 MCP 服务器。它使 AI 模型能够借助稳健的解析和格式化能力读取、编写并转换 Markdown 内容。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Markitdown MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22markitdown%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22markitdown-mcp%22%5D%7D) [![Install Markitdown MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://vscode.dev/redirect?url=vscode-insiders:mcp/install?%7B%22name%22%3A%22markitdown%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22markitdown-mcp%22%5D%7D) [![Install Markitdown MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22markitdown%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22markitdown-mcp%22%5D%7D)
  
### 💻 Microsoft 365 Agents Toolkit
- **REPOSITORY**: [OfficeDev/microsoft-365-agents-toolkit](https://github.com/OfficeDev/microsoft-365-agents-toolkit/)
- **DESCRIPTION**: Microsoft 365 Agents Toolkit MCP Server 是一个 Model Context Protocol（MCP）服务器，为 AI 智能体与开发者之间提供无缝连接，用于构建适用于 Microsoft 365 和 Microsoft 365 Copilot 的应用与智能体。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Microsoft 365 Agents Toolkit in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode:extension/TeamsDevApp.ms-teams-vscode-extension) [![Install Microsoft 365 Agents Toolkit in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode-insiders:extension/TeamsDevApp.ms-teams-vscode-extension)

### 📅 Microsoft 365 Calendar
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_CalendarTools)
- **DESCRIPTION**: 用于创建、更新、删除事件、管理邀请和检查可用性的日历工具。与 Microsoft Graph Calendar API 集成。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_CalendarTools`
- **INSTALL**: [![Install Microsoft 365 Calendar MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-calendartools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_CalendarTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft 365 Calendar MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-calendartools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_CalendarTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 💬 Microsoft 365 Copilot Chat
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_M365Copilot)
- **DESCRIPTION**: 可搜索 M365 内容，包括文档、邮件、站点、文件和聊天。提供用于发起和维护面向 Microsoft Graph 的丰富聊天会话的工具。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_M365Copilot`
- **INSTALL**: [![Install Microsoft 365 Copilot Chat MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-m365copilot&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_M365Copilot%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft 365 Copilot Chat MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-m365copilot&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_M365Copilot%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 📧 Microsoft 365 Mail
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_MailTools)
- **DESCRIPTION**: 用于创建、发送、回复、更新、删除和搜索邮件的邮件工具。与 Microsoft Graph Mail API 集成。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_MailTools`
- **INSTALL**: [![Install Microsoft 365 Mail MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-mailtools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_MailTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft 365 Mail MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-mailtools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_MailTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 👤 Microsoft 365 User
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_MeServer)
- **DESCRIPTION**: 用于从 Microsoft Graph 检索用户详情、经理、团队或直属下属的工具。它充当智能体的自我认知层和组织感知层。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_MeServer`
- **INSTALL**: [![Install Microsoft 365 User MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-meserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_MeServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft 365 User MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-meserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_MeServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### ⚙️ Microsoft Admin Center
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_AdminTools)
- **DESCRIPTION**: 包含与 Microsoft Admin Center 相关工具的 MCP Server。它与 Microsoft Admin Center API 集成，以提供管理操作能力。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_AdminTools`
- **INSTALL**: [![Install Microsoft Admin Center MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-admintools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_AdminTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft Admin Center MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-admintools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_AdminTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 📊 Microsoft Clarity
- **REPOSITORY**: [microsoft/clarity-mcp-server](https://github.com/microsoft/clarity-mcp-server)
- **DESCRIPTION**: 这是一个面向 Microsoft Clarity 数据导出 API 的 Model Context Protocol（MCP）服务器。它允许你通过 Claude for Desktop 或其他兼容 MCP 的客户端从 Clarity 获取分析数据。
- **CATEGORY**: `DATA AND ANALYTICS`
- **TYPE**: `Local`
- **INSTALL**: [microsoft/clarity-mcp-server](https://github.com/microsoft/clarity-mcp-server)

### 🗃️ Microsoft Dataverse
- **REPOSITORY**: [Microsoft Dataverse](https://go.microsoft.com/fwlink/?linkid=2320176)
- **DESCRIPTION**: 以自然语言方式围绕你的业务数据进行对话。可发现表、运行查询、检索数据、插入或更新记录，并执行基于业务知识和上下文的自定义提示。
- **CATEGORY**: `DATA AND ANALYTICS`
- **TYPE**: `Local`
- **INSTALL**: [Microsoft Dataverse](https://go.microsoft.com/fwlink/?linkid=2320176)

### 💻 Microsoft Dev Box
- **REPOSITORY**: [@microsoft/devbox-mcp](https://www.npmjs.com/package/@microsoft/devbox-mcp?activeTab=readme)
- **DESCRIPTION**: 面向 Microsoft Dev Box 的 MCP 服务器。支持通过自然语言执行面向开发者的操作，例如管理 Dev Box、配置环境以及处理池。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Dev Box MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=DevBox&config=%7B%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40microsoft%2Fdevbox-mcp%40latest%22%5D%7D) [![Install Dev Box MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=DevBox&config=%7B%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40microsoft%2Fdevbox-mcp%40latest%22%5D%7D&quality=insiders) [![Install Dev Box MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22DevBox%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40microsoft%2Fdevbox-mcp%40latest%22%5D%7D)

### <img height="18" width="18" src="https://learn.microsoft.com/fabric/media/fabric-icon.png" alt="Microsoft Fabric Logo" /> Microsoft Fabric (Public Preview)
- **REPOSITORY**: [microsoft/mcp](https://github.com/microsoft/mcp/tree/main/servers/Fabric.Mcp.Server#readme)
- **DESCRIPTION**: 一个本地优先的 MCP 服务器，为 AI 智能体提供对 Microsoft Fabric 公共 API、项定义和最佳实践的全面访问。无需连接到实时环境，即可为所有 Fabric 工作负载启用 AI 辅助开发。
- **CATEGORY**: `DATA AND ANALYTICS`
- **TYPE**: `Local`
- **INSTALL**: [microsoft/mcp](https://github.com/microsoft/mcp/tree/main/servers/Fabric.Mcp.Server#readme)

### 🛢️ Microsoft Fabric Real-Time Intelligence
- **REPOSITORY**: [RTI MCP Server](https://aka.ms/rti.mcp.repo)
- **DESCRIPTION**: 该服务器通过 MCP 接口提供工具，使 AI 智能体能够与 Fabric RTI 服务交互，从而实现无缝的数据查询与分析能力。
- **CATEGORY**: `DATA AND ANALYTICS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Fabric RTI MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=ms-fabric-rti&config=%7B%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22microsoft-fabric-rti-mcp%22%5D%7D) [![Install Fabric RTI MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=ms-fabric-rti&config=%7B%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22microsoft-fabric-rti-mcp%22%5D%7D&quality=insiders) [![Install Fabric RTI MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22ms-fabric-rti%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22microsoft-fabric-rti-mcp%22%5D%7D)

### 📚 Microsoft Learn
- **REPOSITORY**: [microsoftdocs/mcp](https://github.com/microsoftdocs/mcp)
- **DESCRIPTION**: 具备对 Microsoft 官方文档实时访问能力的 AI 助手。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://learn.microsoft.com/api/mcp`
- **INSTALL**: [![Install Microsoft Learn MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=microsoft.docs.mcp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D) [![Install Microsoft Learn MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=microsoft.docs.mcp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D&quality=insiders) [![Install Microsoft Learn MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22microsoft.docs.mcp%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D)

### 🛡️ Microsoft Sentinel Data Exploration
- **DOCUMENTATION**: [Explore Microsoft Sentinel data lake with data exploration collection](https://aka.ms/mcp/data-exploration)
- **DESCRIPTION**: Microsoft Sentinel Model Context Protocol（MCP）服务器中的数据探索工具集允许你使用自然语言搜索相关表并从 Microsoft Sentinel 数据湖中检索数据。了解更多：[aka.ms/mcp/data-exploration](https://aka.ms/mcp/data-exploration)。
- **CATEGORY**: `SECURITY`
- **TYPE**: `REMOTE` - `https://sentinel.microsoft.com/mcp/data-exploration`
- **INSTALL**: [![Install Microsoft Sentinel Data Exploration MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22microsoft-sentinel-data-exploration%22%2C%22url%22%3A%22https%3A%2F%2Fsentinel.microsoft.com%2Fmcp%2Fdata-exploration%22%7D) [![Install Microsoft Sentinel Data Exploration MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://vscode.dev/redirect?url=vscode-insiders:mcp/install?%7B%22name%22%3A%22microsoft-sentinel-data-exploration%22%2C%22url%22%3A%22https%3A%2F%2Fsentinel.microsoft.com%2Fmcp%2Fdata-exploration%22%7D)

### 🛢️ Microsoft SQL
- **REPOSITORY**: [MSSQL MCP Server](https://aka.ms/MssqlMcp)
- **DESCRIPTION**: 以自然语言和 AI 的全新智能体方式与你的业务数据对话。通过简单的连接字符串连接任意 SQL 数据库，从本地部署到 Azure 云再到 Microsoft Fabric。你可以通过对话式提示发现并定义表架构、管理表，以及执行 CRUD 操作。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [MSSQL MCP Server](https://aka.ms/MssqlMcp)

### 💬 Microsoft Teams
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_TeamsServer)
- **DESCRIPTION**: 通过 Graph API 管理 Microsoft Teams 聊天、频道、用户和消息。支持服务端筛选、分页和令牌优化。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_TeamsServer`
- **INSTALL**: [![Install Microsoft Teams MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-teamsserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_TeamsServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft Teams MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-teamsserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_TeamsServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 📄 Microsoft Word
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/CodeBased/mcp_WordServer)
- **DESCRIPTION**: 包含用于操作 Microsoft Word 文档的工具的 MCP Server。支持读取和理解文档、创建新文档，以及通过批注协作。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_WordServer`
- **INSTALL**: [![Install Microsoft Word MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-wordserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_WordServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install Microsoft Word MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-wordserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_WordServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 💻 NuGet MCP Server
- **REPOSITORY**: [NuGet/Home](https://github.com/NuGet/Home)
- **DESCRIPTION**: 这是一个面向 NuGet 的 Model Context Protocol（MCP）服务器，可为 NuGet 包管理启用高级工具和自动化场景。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [Nuget MCP Server](https://www.nuget.org/packages/NuGet.Mcp.Server)

### 📁 OneDrive and SharePoint
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/FileBased/mcp_ODSPRemoteServer)
- **DESCRIPTION**: OneDrive 和 SharePoint 远程 MCP Server。ODSP MCP 端点公开的所有支持 OneDrive 和 SharePoint 文件集成的工具都会被自动发现并可直接使用。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_ODSPRemoteServer`
- **INSTALL**: [![Install OneDrive and SharePoint MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-odspremoteserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_ODSPRemoteServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install OneDrive and SharePoint MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-odspremoteserver&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_ODSPRemoteServer%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 📋 SharePoint Lists
- **REPOSITORY**: [bap-microsoft/MCP-Platform](https://github.com/bap-microsoft/MCP-Platform/tree/main/src/Services/WebApi/MCPServers/FirstParty/FileBased/mcp_SharepointListsTools)
- **DESCRIPTION**: 为 Lists 提供 Microsoft Graph SharePoint 工具的 MCP 服务器。包括站点管理、文档库、列表和协作功能。
- **CATEGORY**: `PRODUCTIVITY`
- **TYPE**: `REMOTE` - `https://agent365.svc.cloud.microsoft/agents/tenants/{tenant_id}/servers/mcp_SharePointListsTools`
- **INSTALL**: [![Install SharePoint Lists MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=agent365-sharepointliststools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_SharePointListsTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D) [![Install SharePoint Lists MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agent365-sharepointliststools&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//agent365.svc.cloud.microsoft/agents/tenants/%24%7Binput%3Atenant_id%7D/servers/mcp_SharePointListsTools%22%7D&inputs=%5B%7B%22id%22%3A%22tenant_id%22%2C%22type%22%3A%22promptString%22%2C%22description%22%3A%22Microsoft%20Entra%20tenant%20ID%20(GUID)%22%7D%5D&quality=insiders)

### 🎭 Playwright
- **REPOSITORY**: [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp)
- **DESCRIPTION**: 此服务器使 LLM 能够通过结构化的无障碍快照与网页交互，从而绕过对截图或视觉调优模型的需求。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [![Install Playwright MCP in VS Code](https://img.shields.io/badge/VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522playwright%2522%252C%2522command%2522%253A%2522npx%2522%252C%2522args%2522%253A%255B%2522%2540playwright%252Fmcp%2540latest%2522%255D%257D) [![Install Playwright MCP in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-24bfa5?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect?url=vscode-insiders%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522playwright%2522%252C%2522command%2522%253A%2522npx%2522%252C%2522args%2522%253A%255B%2522%2540playwright%252Fmcp%2540latest%2522%255D%257D) [![Install Playwright MCP in Visual Studio](https://img.shields.io/badge/Visual_Studio-C16FDE?style=flat-square&logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22playwright%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22%40playwright%2Fmcp%40latest%22%5D%7D)

### 🧩 Wassette
- **REPOSITORY**: [microsoft/wassette](https://github.com/microsoft/wassette)
- **DESCRIPTION**: Wassette：一个以安全为导向的运行时，通过 MCP 运行 WebAssembly 组件。
- **CATEGORY**: `DEVELOPER TOOLS`
- **TYPE**: `Local`
- **INSTALL**: [microsoft/wassette](https://github.com/microsoft/wassette)

## 🔌 Azure 插件
开始使用 Azure 插件，它可以将 [GitHub Copilot CLI](https://github.com/github/copilot-cli) 或 Claude Code 连接到你的 Azure 账户。借助此集成，你可以使用 Azure MCP 服务器中的工具和扩展的 Azure 知识技能，直接在开发环境中管理资源、部署应用程序并监控服务。

要将 Azure 插件安装到 Copilot CLI 和 Claude Code 中：

1. 添加市场：`/plugin marketplace add microsoft/skills`
2. 安装插件：`/plugin install azure-skills@skills`
3. 更新插件：`/plugin update azure-skills@skills`

## 🏗️ 在寻找使用 MCP 的入门模板？
查看带有 MCP 标签的 [Azure Developer CLI (azd) templates](https://azure.github.io/awesome-azd/?tags=mcp)。

## 📎 相关资源
- [Microsoft MCP Resources](https://github.com/microsoft/mcp/tree/main/Resources)
- [MCP Pattern Overview](https://modelcontextprotocol.io/introduction)
- [MCP SDKs and Building Blocks](https://modelcontextprotocol.io/docs/sdk)
- [MCP Specification](https://modelcontextprotocol.io/specification/latest)

## Contributing

本项目欢迎贡献与建议。大多数贡献都要求你同意一份
Contributor License Agreement（CLA），声明你有权并且确实授予我们
使用你的贡献的相关权利。详情请访问 https://cla.opensource.microsoft.com。

当你提交拉取请求时，CLA 机器人会自动判断你是否需要提供
CLA，并对 PR 做出相应标记（例如状态检查、评论）。只需按照机器人
提供的说明进行操作即可。对于所有使用我们 CLA 的仓库，你只需要完成一次。

本项目已采用 [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)。
更多信息请参见 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)，或发送邮件至
[opencode@microsoft.com](mailto:opencode@microsoft.com) 咨询其他问题或提出意见。

## Trademarks

本项目可能包含项目、产品或服务的商标或标识。对 Microsoft
商标或标识的授权使用受以下规范约束，并且必须遵循
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general)。
在本项目的修改版本中使用 Microsoft 商标或标识时，不得造成混淆，也不得暗示 Microsoft 赞助。
任何第三方商标或标识的使用均受相关第三方政策约束。
