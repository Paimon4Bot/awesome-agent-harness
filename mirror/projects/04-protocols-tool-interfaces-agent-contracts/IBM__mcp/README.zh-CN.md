# IBM MCP

IBM 提供的一系列模型上下文协议（MCP）服务器、MCP 客户端和开发者工具。将您的 IBM 产品连接到任何 AI 代理或 AI 应用程序。

## 什么是 MCP？

MCP 是一种开源协议，旨在使 AI 模型能够通过标准化服务器实现安全地与本地和远程资源进行交互。这些 IBM MCP 服务集合涵盖了生产就绪和实验性的 MCP 服务器，通过提供文件访问、数据库连接、API 集成和额外的上下文服务来增强 AI 能力。

## 可用的 MCP 服务器

#### ⚙️ 自动化

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [IBM MQ Server](https://github.com/ibm-messaging/mq-mcp-server) | 提供对 IBM MQ 队列管理器健康检查的访问，并针对特定队列管理器运行任何 MQSC 命令。 | *参见链接中的说明* |
| [K* Planner](https://github.com/IBM/kstar/tree/main/mcp) | K* MCP 服务器提供了 KStar 仓库中 Top-K 和 Top-Q 规划器的容器化部署，作为模型检查问题 (MCP) 工具。 | *参见链接中的说明* |

#### 💼 业务自动化

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [IBM Business Automation Workflow MCP Server](https://github.com/ibmbpm/ibm-baw-mcp-server) | IBM® 业务自动化工作流 MCP 服务器是一个本地模型控制协议 (MCP) 服务器，支持 AI 代理通过模型上下文协议与 IBM® 业务自动化工作流集成。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22ibm-baw-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22--from%22%2C%22git%2Bhttps%3A%2F%2Fgithub.com%2Fibmbpm%2Fibm-baw-mcp-server%22%2C%22ibm-baw-mcp-server%22%5D%2C%22env%22%3A%7B%22ENDPOINT%22%3A%22YOUR_WORKFLOW_ENDPOINT%22%2C%22USERID%22%3A%22YOUR_WORKFLOW_USERNAME%22%2C%22PASSWORD%22%3A%22YOUR_WORKFLOW_PASWORD%22%7D%7D) |
| [IBM Core Content Services MCP Server](https://github.com/ibm-ecm/ibm-content-services-mcp-server) | 提供与 IBM FileNet Content Manager (FNCM) 存储库交互的工具，支持文档管理、文件夹操作、搜索功能等。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](vscode:mcp/install?%7B%22name%22%3A%22core-cs-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22--from%22%2C%22git%2Bhttps%3A%2F%2Fgithub.com%2Fibm-ecm%2Fibm-content-services-mcp-server%22%2C%22core-cs-mcp-server%22%5D%2C%22env%22%3A%7B%22SERVER_URL%22%3A%22https%3A%2F%2Fyour-graphql-server%2Fcontent-services-graphql%2Fgraphql%22%2C%22OBJECT_STORE%22%3A%22your_object_store%22%2C%22USERNAME%22%3A%22username%22%2C%22PASSWORD%22%3A%22password%22%7D%7D) |
| [IBM Decision Intelligence MCP Server](https://github.com/DecisionsDev/decision-intelligence-mcp-server) | 此 MCP 服务器提供调用由 [IBM Decision Intelligence](https://www.ibm.com/products/decision-intelligence) 或 [IBM Automation Decision Services](https://www.ibm.com/products/automation-decision-services) 部署的决策服务的工具。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22ibm-decision-intelligence-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22di-mcp-server%22%5D%2C%22env%22%3A%7B%22APIKEY%22%3A%22%3CAPIKEY%3E%22%2C%22URL%22%3A%22https%3A%2F%2F%3CTENANT_NAME%3E.decision-prod-us-south.decision.saas.ibm.com%2Fads%2Fruntime%2Fapi%2Fv1%22%7D%7D) |
| [IBM ODM MCP Server](https://github.com/DecisionsDev/ibm-odm-decision-mcp-server) | 支持与 IBM Decision Server Runtime 集成的 MCP 服务器，用于检索和调用决策服务。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22ibm-odm-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22--from%22%2C%22git%2Bhttps%3A%2F%2Fgithub.com%2FDecisionsDev%2Fdecision-mcp-server%22%2C%22decision-mcp-server%22%5D%7D) |
| [IBM Process Mining](https://www.ibm.com/docs/en/process-mining/2.1.0?topic=menu-generating-mcp-rest-api-tokens) | 提供对流程和数据分析功能的访问。 | *参见链接中的说明* |

#### 🧠 数据与分析

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [IBM OpenPages MCP Server](https://github.com/IBM/ibm-openpages-local-mcp-server) | 实验性本地模型上下文协议 (MCP) 服务器，使 AI 代理能够通过标准化接口安全地与 IBM OpenPages GRC 平台交互。 | *参见链接中的说明* |
| [DataStax Astra DB](https://github.com/datastax/astra-db-mcp) | 用于 Astra DB 工作负载的 MCP 服务器。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22astra-db-mcp%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40datastax%2Fastra-db-mcp-server%22%5D%2C%22env%22%3A%7B%22ASTRA_DB_APPLICATION_TOKEN%22%3A%22your_astra_db_token%22%2C%22ASTRA_DB_API_ENDPOINT%22%3A%22your_astra_db_endpoint%22%7D%7D) |
| [Docling MCP Server](https://github.com/docling-project/docling-mcp) | 使用 Docling 将非结构化数据转换为结构化数据，提供文档转换、处理和生成工具。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22docling-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22uvx%22%2C%22args%22%3A%5B%22--from%3Ddocling-mcp%22%2C%22docling-mcp-server%22%5D%7D) |
| [IBM watsonx.data MCP Server](https://github.com/IBM/ibm-watsonxdata-mcp-server) | 使 AI 助手能够使用自然语言与 IBM watsonx.data 湖仓交互。提供使用 SQL 查询湖仓数据、探索数据目录和元数据、检查表结构以及监控引擎的工具。 | *参见链接中的说明* |
| [IBM watsonx.data Document Library Retrieval MCP Server](https://github.com/IBM/ibm-watsonxdata-dl-retrieval-mcp-server) | 使用对话语言从 watsonx.data 查询文档库，并通过本地 MCP 服务器接收人类可读的响应。 | *参见链接中的说明* |
| [IBM watsonx.data Document Library Retrieval MCP Server (Remote)](https://www.ibm.com/docs/en/watsonxdata/saas?topic=service-watsonxdata-remote-model-context-protocol-mcp-server) | 使用对话语言从 watsonx.data 查询文档库，并通过 IBM 基础设施托管的远程 MCP 服务器接收人类可读的响应。 | *参见链接中的说明* |
| [IBM watsonx.data intelligence MCP Server](https://github.com/IBM/data-intelligence-mcp-server) | 用于与 watsonx.data intelligence 本地或 SaaS 环境交互的 MCP 服务器。 | *参见链接中的说明* |
| [IBM MDM MCP Server](https://github.com/IBM/mdm-mcp-server) | 此 MCP 服务器使 Claude 等 AI 助手能够与 IBM MDM 服务（前身为 IBM Match 360）交互，允许用户通过自然语言对话搜索记录、检索数据模型和管理主数据。该服务器充当 AI 助手和 IBM MDM 之间的桥梁，通过模型上下文协议暴露企业数据管理能力。 | *参见链接中的说明* |

#### 👩🏻‍💻 开发者生产力

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [Carbon MCP](https://github.com/carbon-design-system/carbon-mcp) | 提供探索 Carbon 设计系统组件、令牌和图标的工具，回答文档问题，并生成一致的 UI 代码。 | *云服务器访问[说明](https://carbondesignsystem.com/developing/carbon-mcp/overview/)* |
| [IBM Developer for z/OS on VS Code MCP Server](https://www.ibm.com/docs/en/developer-for-zos/17.0.x?topic=overview-agent-mode) | 作为 IBM z/OS 企业应用开发编辑器一部分运行的 MCP 服务器，支持 COBOL、PL/I、REXX、JCL 和汇编语言。通过 VS Code 中的 AI 聊天功能访问本地工作区和远程 z/OS 开发环境。与 z/OS 交互，包括检索或更新数据集、提交作业并获取作业信息和假脱机文件、从 z/OS UNIX 主目录检索文件并在编辑器中打开、构建应用程序并通过指导分析问题及修复方案等。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:extension/IBM.zopeneditor) |

#### 🏗️ 基础设施与部署

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [IBM Cloud MCP Server](https://ibm-cloud.github.io/mcp/) | 通过 IBM Cloud 的工具增强您的 LLM。 | *参见链接中的说明* |
| [Terraform IBM Modules (TIM) MCP Server](https://github.com/terraform-ibm-modules/tim-mcp) | TIM-MCP 服务器提供对 Terraform IBM Modules (TIM) 生态系统的结构化访问，支持智能地以代码形式配置 IBM Cloud 基础设施资源。 | *参见链接中的说明* |
| [IBM Cloud Code Engine MCP Server](https://github.com/greyhoundforty/code-engine-mcp) | 此 MCP 服务器提供列出和检查 Code Engine 项目、应用程序、修订版本、域名映射和密钥的工具。 | *参见链接中的说明* |
| [IBM Cloud VPC MCP Server](https://github.com/greyhoundforty/ibmcloud-vpc-mcp) | 提供对 IBM Cloud VPC 资源和安全分析能力的访问，使 AI 代理能够与云基础设施、备份和安全策略交互。 | *参见链接中的说明* |
| [IBM i MCP Server](https://github.com/IBM/ibmi-mcp-server) | 用于 IBM i 系统的 MCP 服务器，使 AI 代理能够通过基于 SQL 的工具安全地与 IBM i 交互。它提供了一个灵活的框架，用于构建自定义的代理工具，支持性能监控、安全审计、存储分析、数据库管理等任务。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=flat-square&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22ibmi-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40ibm%2Fibmi-mcp-server%40latest%22%5D%7D) |
| [IBM Power Virtual Server MCP Server](https://github.com/IBM/powervs-mcp-server) | 为 AI 代理带来对注册到 IBM Power Virtual Server 的虚拟机的无缝可观测性和诊断能力。 | *参见链接中的说明* |
| [Terraform MCP Server](https://github.com/hashicorp/terraform-mcp-server) | 提供与 Terraform 生态系统的无缝集成，支持基础设施即代码 (IaC) 开发的高级自动化和交互能力。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22terraform-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22docker%22%2C%22args%22%3A%5B%22run%22%2C%22-i%22%2C%22--rm%22%2C%22hashicorp%2Fterraform-mcp-server%22%5D%7D) |

#### 📊 可观测性与监控

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [IBM Instana MCP Server](https://github.com/instana/mcp-instana) | 此 MCP 服务器提供列出和检查 IBM Instana 资源（包括应用程序、基础设施资源等）的工具。 | *参见链接中的说明* |
| [IBM Storage Insights MCP Server](https://github.com/IBM/ibm-storageinsights-mcpserver) | 通过 MCP 接口利用 IBM Storage Insights 的关键监控能力。 | *参见链接中的说明* |

#### 📡 网络

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [Consul MCP Server](https://hub.docker.com/r/hashicorp/consul-mcp-server) | 此 MCP 服务器充当桥梁，使 AI 模型能够通过 API 执行 Consul 操作。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](vscode:mcp/install?%7B%22name%22%3A%22consul%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22docker%22%2C%22args%22%3A%5B%22run%22%2C%22-i%22%2C%22--rm%22%2C%22-e%22%2C%22CONSUL_HTTP_ADDR%3Dhttp%3A%2F%2Fhost.docker.internal%3A8500%22%2C%22-e%22%2C%22CONSUL_HTTP_TOKEN%3D%24%7BCONSUL_DC1_TOKEN%7D%22%2C%22hashicorp%2Fconsul-mcp-server%22%5D%7D) |

#### 🔬 研究

| 服务器名称                                                                                  | 描述                                                                                                                                                                                                                                                                                                                                                                                              | 用法 |
|----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|
| [MAMMAL-MCP](https://github.com/BiomedSciAI/biomed-multi-alignment/tree/main/mammal_mcp) | MAMMAL (ibm/biomed.omics.bl.sm.ma-ted-458m) 是一个由 IBM 训练的"生物医学基础模型" (BMFM)，详情请参见 https://github.com/BiomedSciAI/biomed-multi-alignment。此 MCP 服务器可用于使 AI 代理系统使用 MAMMAL 模型的部分任务，例如："蛋白质-蛋白质相互作用预测"、"蛋白质溶解性预测"和"药物-蛋白质相互作用预测"。 | *参见链接中的说明* |

#### 🔐 安全

| 服务器名称 | 描述 | 用法 |
|---|---|---|
| [Guardium Data Protection MCP Server](https://github.com/IBM/gdp-mcp-server) | 通过 4 个智能 MCP 工具访问 621 个 IBM Guardium Data Protection REST API 端点——搜索 API、列出类别、获取 API 详情以及执行任何 GDP 端点。 | *[参见链接中的说明](https://github.com/IBM/gdp-mcp-server)* |
| [QRadar SIEM MCP Server](https://github.com/IBM/qradar-mcp-server) | 通过 4 个智能 MCP 工具访问 728+ 个 IBM QRadar REST API 端点——搜索违规事件、运行 AQL 查询、管理参考集以及调查安全事件。 | *[参见链接中的说明](https://github.com/IBM/qradar-mcp-server)* |
| [Guardium Cryptography Manager MCP Server](https://github.com/IBM/gcm-mcp-server) | 通过 3 个智能 MCP 工具访问 292 个 IBM Guardium Cryptography Manager API 端点——管理加密密钥、运行发现扫描、执行加密策略以及监控合规性。 | *[参见链接中的说明](https://github.com/IBM/gcm-mcp-server)* |
| [IBM Security Verify MCP Server](https://github.com/IBM/verify-mcp-server) | 通过 4 个智能 MCP 工具访问 210 个 IBM Security Verify REST API 端点——发现 API、管理用户、配置 SSO 以及编排身份工作流。 | *[参见链接中的说明](https://github.com/IBM/verify-mcp-server)* |
| [Vault MCP Server](https://developer.hashicorp.com/hcp/docs/vault-radar/mcp-server/overview) | 此 MCP 服务器充当桥梁，使 AI 模型能够通过 API 在 Vault 中执行 kv、pki 和挂载操作。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](vscode:mcp/install?%7B%22name%22%3A%22vault-mcp-server%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22docker%22%2C%22args%22%3A%5B%22run%22%2C%22--rm%22%2C%22-i%22%2C%22-e%22%2C%22VAULT_ADDR%3D%3CVault%20Address%3E%22%2C%22-e%22%2C%22VAULT_TOKEN%3D%3CVault%20Token%3E%22%2C%22-e%22%2C%22VAULT_NAMESPACE%3D%3CVault%20Namespace%3E%22%2C%22hashicorp%2Fvault-mcp-server%22%5D%7D) |
| [Vault Radar MCP Server](https://developer.hashicorp.com/hcp/docs/vault-radar/mcp-server/overview) | 提供对 HCP Vault Radar 数据源、秘密风险和事件的访问，使 LLM 能够使用自然语言查询和分析安全信息。 | [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?style=plastic&logo=visualstudiocode&logoColor=ffffff)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22vault-radar%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22docker%22%2C%22args%22%3A%5B%22run%22%2C%22--rm%22%2C%22-i%22%2C%22-e%22%2C%22HCP_PROJECT_ID%3D%3CHCP%20Project%20ID%3E%22%2C%22-e%22%2C%22HCP_CLIENT_ID%3D%3CHCP%20Service%20Principal%20Client%20ID%3E%22%2C%22-e%22%2C%22HCP_CLIENT_SECRET%3D%3CHCP%20Service%20Principal%20Client%20Secret%3E%22%2C%22hashicorp%2Fvault-radar-mcp-server%3A%3Ctag%3E%22%5D%7D) |

#### 🛠️ 开发者工具

- [BeeAI Framework](https://framework.beeai.dev/integrations/mcp) - BeeAI Framework 是一个用于构建生产级多代理系统的开源框架，同时支持 Python 和 TypeScript。它作为 MCP 客户端与模型上下文协议 (MCP) 集成，由 Linux 基金会在开放治理下托管。
- [ContextForge MCP Gateway](https://github.com/IBM/mcp-context-forge) - MCP 服务器、功能丰富的网关和代理，可联合 MCP 和 REST 服务——通过单一端点提供统一发现、认证、速率限制、可观测性、多传输协议以及可选的 HTMX 驱动管理 UI。
- [IBM API Connect for GraphQL](https://www.ibm.com/docs/en/api-connect-graphql/saas?topic=directives-directive-tool) - 将任何 GraphQL 模式转换为 MCP 服务器，包括认证功能。
- [Langflow](https://github.com/langflow-ai/langflow) - Langflow 是一个开源可视化构建器，允许开发者快速原型化和构建 AI 应用程序，它同时作为 MCP 服务器和 MCP 客户端与模型上下文协议 (MCP) 集成。
- [MCP Composer](https://pypi.org/project/mcp-composer/) - 基于 FastMCP 的库，用于管理多个 MCP 服务器和工具，支持动态注册、认证和统一接口。支持多种工具类型，如 OpenAPI (REST)、GraphQL、基于 CLI 的工具、客户端 SDK 和嵌套 MCP 服务器。
- [WxMCPServer](https://github.com/IBM/WxMCPServer) - 基于 IBM webMethods 混合集成 (IWHI) 的 MCP 服务器，使现有 API 能够用作 MCP 工具。
- [z/OS Connect](https://www.ibm.com/docs/en/zos-connect/3.0.0?topic=connect-what-is-mcp) - 基于 z/OS Connect 的 MCP 服务器，使现有 API 能够用作 MCP 工具。
- [IBM API Connect MCP Server](https://github.com/ibm-apiconnect/apic-mcp-server) - IBM APIC MCP 服务器向您的 MCP 客户端和 AI 代理工作流暴露 API Connect 的功能。

## MCP 客户端

我们推荐使用 [Langflow](https://github.com/langflow-ai/langflow) 或您选择的 IDE 作为 MCP 客户端。

## 💬 社区

参与 [Discord 社区](https://discord.com/invite/NzCQQWm7Xs)。

## 🤝 贡献

欢迎大家为此仓库做贡献，请参阅 [CONTRIBUTING.md](./CONTRIBUTING.md) 了解详情。

感谢我们所有了不起的贡献者！

<a href="https://github.com/ibm/mcp/graphs/contributors">
  <img src="assets/001-image-736e393bc9.svg" />
</a>

## ⭐ 支持

如果您觉得这些 IBM MCP 服务器有用，请考虑给仓库加星并贡献新的服务器、示例或改进！
