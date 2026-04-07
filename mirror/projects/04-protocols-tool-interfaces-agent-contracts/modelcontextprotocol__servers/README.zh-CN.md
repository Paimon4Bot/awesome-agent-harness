# Model Context Protocol 服务器

此仓库收集了 [Model Context Protocol](https://modelcontextprotocol.io/)（MCP）的*参考实现*，以及社区构建服务器的引用和其他补充资源。

> [!IMPORTANT]
> 如果你正在寻找 MCP 服务器列表，可以浏览发布在 [the MCP Registry](https://registry.modelcontextprotocol.io/) 上的服务器。此 README 所对应的仓库专门用于存放由 MCP steering group 维护的少量参考服务器。

> [!WARNING]
> 此仓库中的服务器旨在作为**参考实现**，用于演示 MCP 功能和 SDK 用法。它们的目的是作为构建自有 MCP 服务器的开发者教育示例，而不是可直接投入生产的解决方案。开发者应根据自身特定的威胁模型和使用场景评估安全需求，并实施适当的防护措施。

此仓库中的服务器展示了 MCP 的灵活性与可扩展性，演示了如何用它为 Large Language Models (LLMs) 提供对工具和数据源的安全、受控访问。
通常，每个 MCP 服务器都使用某种 MCP SDK 实现：

- [C# MCP SDK](https://github.com/modelcontextprotocol/csharp-sdk)
- [Go MCP SDK](https://github.com/modelcontextprotocol/go-sdk)
- [Java MCP SDK](https://github.com/modelcontextprotocol/java-sdk)
- [Kotlin MCP SDK](https://github.com/modelcontextprotocol/kotlin-sdk)
- [PHP MCP SDK](https://github.com/modelcontextprotocol/php-sdk)
- [Python MCP SDK](https://github.com/modelcontextprotocol/python-sdk)
- [Ruby MCP SDK](https://github.com/modelcontextprotocol/ruby-sdk)
- [Rust MCP SDK](https://github.com/modelcontextprotocol/rust-sdk)
- [Swift MCP SDK](https://github.com/modelcontextprotocol/swift-sdk)
- [TypeScript MCP SDK](https://github.com/modelcontextprotocol/typescript-sdk)

## 🌟 参考服务器

这些服务器旨在演示 MCP 功能和官方 SDK。

- **[Everything](src/everything)** - 带有 prompts、resources 和 tools 的参考 / 测试服务器。
- **[Fetch](src/fetch)** - 用于高效 LLM 使用的网页内容抓取与转换。
- **[Filesystem](src/filesystem)** - 具有可配置访问控制的安全文件操作。
- **[Git](src/git)** - 用于读取、搜索和操作 Git 仓库的工具。
- **[Memory](src/memory)** - 基于知识图谱的持久记忆系统。
- **[Sequential Thinking](src/sequentialthinking)** - 通过思维序列进行动态且可反思的问题求解。
- **[Time](src/time)** - 时间与时区转换能力。

### 已归档

以下参考服务器现已存档，可以在 [servers-archived](https://github.com/modelcontextprotocol/servers-archived) 中找到。

- **[AWS KB Retrieval](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/aws-kb-retrieval-server)** - 使用 Bedrock Agent Runtime 从 AWS 知识库检索。
- **[Brave Search](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/brave-search)** - 使用 Brave 的搜索 API 进行网络和本地搜索。  已被 [official server](https://github.com/brave/brave-search-mcp-server) 取代。
- **[EverArt](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/everart)** - 使用各种模型生成人工智能图像。
- **[GitHub](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/github)** - 存储库管理、文件操作和 GitHub API 集成。
- **[GitLab](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/gitlab)** - GitLab API，支持项目管理。
- **[Google Drive](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/gdrive)** - Google Drive 的文件访问和搜索功能。
- **[Google Maps](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/google-maps)** - 位置服务、方向和地点详细信息。
- **[PostgreSQL](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/postgres)** - 具有模式检查的只读数据库访问。
- **[Puppeteer](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/puppeteer)** - 浏览器自动化和网页抓取。
- **[Redis](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/redis)** - 与 Redis 键值存储交互。
- **[Sentry](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/sentry)** - 从 Sentry.io 检索和分析问题。
- **[Slack](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/slack)** - 渠道管理和消息传递功能。现在由 [Zencoder](https://github.com/zencoderai/slack-mcp-server) 维护
- **[SQLite](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/sqlite)** - 数据库交互和商业智能功能。

## 🤝 第三方服务器

> [!NOTE]
本 README 中的服务器列表已不再维护，未来将被移除。

### 🎖️ 官方集成

官方集成由为其平台构建可用于生产环境的 MCP 服务器的公司维护。

- <img height="12" width="12" src="https://www.21st.dev/favicon.ico" alt="21st.dev Logo" /> **[21st.dev Magic](https://github.com/21st-dev/magic-mcp)** - 受最优秀的 21st.dev 设计工程师的启发，创建精心制作的 UI 组件。
- <img height="12" width="12" src="assets/001-2slides-red-f485b72990.svg" alt="2slides Logo" /> **[2slides](https://github.com/2slides/2slides-mcp)** - MCP 服务器提供将内容转换为幻灯片/PPT/演示文稿或根据用户意图生成幻灯片/PPT/演示文稿的工具。
- <img height="12" width="12" src="assets/002-lpsk1tszweomrahomaj9gea96la-47f648f54b.svg" alt="Paragon Logo" /> **[ActionKit by Paragon](https://github.com/useparagon/paragon-mcp)** - 使用 Paragon 的 [ActionKit](https://www.useparagon.com/actionkit) API 连接到 130 多个 SaaS 集成（例如 Slack、Salesforce、Gmail）。
- <img height="12" width="12" src="https://invoxx-public-bucket.s3.eu-central-1.amazonaws.com/frontend-resources/adfin-logo-small.svg" alt="Adfin Logo" /> **[Adfin](https://github.com/Adfin-Engineering/mcp-server-adfin)** - 您需要获得付款的唯一平台 - 所有付款都集中在一个地方，使用 [Adfin](https://www.adfin.com/) 进行发票和会计对账。
- <img height="12" width="12" src="https://github.com/AgentOps-AI/agentops/blob/main/docs/favicon.png" alt="AgentOps Logo" /> **[AgentOps](https://github.com/AgentOps-AI/agentops-mcp)** - 使用 [AgentOps](https://www.agentops.ai/) API 为调试 AI 代理提供可观察性和跟踪。
- <img height="12" width="12" src="https://www.agentql.com/favicon/favicon.png" alt="AgentQL Logo" /> **[AgentQL](https://github.com/tinyfish-io/agentql-mcp)** - 使 AI 代理能够使用 [AgentQL](https://www.agentql.com/) 从非结构化 Web 获取结构化数据。
- <img height="12" width="12" src="https://agentrpc.com/favicon.ico" alt="AgentRPC Logo" /> **[AgentRPC](https://github.com/agentrpc/agentrpc)** - 使用 [AgentRPC](https://www.agentrpc.com/) 跨网络边界连接到任何功能、任何语言。
- **[Agentset](https://github.com/agentset-ai/mcp-server)** - 连接到 [Agentset](https://agentset.ai) 的知识库的 RAG。
- <img height="12" width="12" src="https://www.airwallex.com/favicon.ico" alt="Airwallex Logo" /> **[Airwallex Developer](https://www.npmjs.com/package/@airwallex/developer-mcp)** - 为 AI 编码代理提供所需的工具，帮助开发人员与 [Airwallex APIs](https://www.airwallex.com/docs/api/) 集成
- <img height="12" width="12" src="https://aiven.io/favicon.ico" alt="Aiven Logo" /> **[Aiven](https://github.com/Aiven-Open/mcp-aiven)** - 导航您的 [Aiven projects](https://go.aiven.io/mcp-server) 并与 PostgreSQL®、Apache Kafka®、ClickHouse® 和 OpenSearch® 服务交互
- <img height="12" width="12" src="https://www.alation.com/resource-center/download/7p3vnbbznfiw/34FMtBTex5ppvs2hNYa9Fc/c877c37e88e5339878658697c46d2d58/Alation-Logo-Bug-Primary.svg" alt="Alation Logo" /> **[Alation](https://github.com/Alation/alation-ai-agent-sdk)** - 利用 Alation MCP 服务器提供的工具释放企业数据目录的力量。
- <img height="12" width="12" src="https://i.postimg.cc/5NYw9qjS/alby-icon-head-yellow-500x500.png" alt="Alby Logo" /> **[Alby Bitcoin Payments](https://github.com/getAlby/mcp)** - 将任何比特币闪电钱包连接到您的代理，即可通过您的代理在全球范围内发送和接收即时付款。
- **[Algolia](https://github.com/algolia/mcp)** - 使用 AI 代理来配置、配置和查询您的 [Algolia](https://algolia.com) 搜索索引。
- <img height="12" width="12" src="assets/003-o1cn01epkxwh1wlaxkzfv6n-6000000002771-2-tps-200-200-1a6c0ab463.png" alt="Alibaba Cloud AnalyticDB for MySQL Logo" /> **[Alibaba Cloud AnalyticDB for MySQL](https://github.com/aliyun/alibabacloud-adb-mysql-mcp-server)** - 连接[AnalyticDB for MySQL](https://www.alibabacloud.com/en/product/analyticdb-for-mysql)集群，获取数据库或表元数据，查询和分析数据。后续将支持添加OpenAPI进行集群操作。
- <img height="12" width="12" src="assets/004-analyticdb-b04745af5b.png" alt="Alibaba Cloud AnalyticDB for PostgreSQL Logo" /> **[Alibaba Cloud AnalyticDB for PostgreSQL](https://github.com/aliyun/alibabacloud-adbpg-mcp-server)** - 用于连接 [AnalyticDB for PostgreSQL](https://github.com/aliyun/alibabacloud-adbpg-mcp-server) 实例、查询和分析数据的 MCP 服务器。
- <img height="12" width="12" src="assets/005-o1cn0101uwwf1uyn3rae3hu-6000000002530-2-tps-32-32-bde5f02d01.png" alt="DataWorks Logo" /> **[Alibaba Cloud DataWorks](https://github.com/aliyun/alibabacloud-dataworks-mcp-server)** - 模型上下文协议 (MCP) 服务器，为 AI 提供工具，允许其通过标准化接口与 [DataWorks](https://www.alibabacloud.com/help/en/dataworks/) Open API 进行交互。该实现基于阿里云开放API，使AI代理能够无缝地执行云资源操作。
- <img height="12" width="12" src="https://opensearch-shanghai.oss-cn-shanghai.aliyuncs.com/ouhuang/aliyun-icon.png" alt="Alibaba Cloud OpenSearch Logo" /> **[Alibaba Cloud OpenSearch](https://github.com/aliyun/alibabacloud-opensearch-mcp-server)** - 该MCP服务器为AI代理配备了通过标准化且可扩展的接口与[OpenSearch](https://help.aliyun.com/zh/open-search/?spm=5176.7946605.J_5253785160.6.28098651AaYZXC)进行交互的工具。
- <img height="12" width="12" src="assets/006-alibaba-cloud-8bd157edc3.png" alt="Alibaba Cloud OPS Logo" /> **[Alibaba Cloud OPS](https://github.com/aliyun/alibaba-cloud-ops-mcp-server)** - 使用 [CloudOps Orchestration Service](https://www.alibabacloud.com/en/product/oos) 和阿里云 OpenAPI 管理阿里云资源的生命周期。
- <img height="12" width="12" src="assets/007-alibabacloudrds-657346d2be.png" alt="Alibaba Cloud RDS MySQL Logo" /> **[Alibaba Cloud RDS](https://github.com/aliyun/alibabacloud-rds-openapi-mcp-server)** - MCP 服务器旨在与阿里云 RDS OpenAPI 交互，支持通过 LLM 对 RDS 资源进行编程管理。
- <img height="12" width="12" src="https://www.alipayplus.com/favicon.ico" alt="AlipayPlus Logo" /> **[AlipayPlus](https://github.com/alipay/global-alipayplus-mcp)** - 将您的 AI 代理连接到 AlipayPlus Checkout 付款。
- <img height="12" width="12" src="https://datalab.alkemi.ai/favicon.png" alt="Alkemi Logo" /> **[Alkemi](https://github.com/alkemi-ai/alkemi-mcp)** - 通过 Alkemi.ai 查询 Snowflake、Google BigQuery、DataBricks 数据产品。
- <img height="12" width="12" src="https://cdn.allvoicelab.com/resources/workbench/dist/icon-dark.ico" alt="AllVoiceLab Logo" /> **[AllVoiceLab](https://www.allvoicelab.com/mcp)** - 具有 TTS、语音克隆和视频翻译功能的 AI 语音工具包，现在可用作 MCP 服务器，以实现更智能的代理集成。
- <img height="12" width="12" src="https://files.alpaca.markets/webassets/favicon-32x32.png" alt="Alpaca Logo" /> **[Alpaca](https://github.com/alpacahq/alpaca-mcp-server)** – Alpaca 的 MCP 服务器可让您通过 [Alpaca's Trading API](https://alpaca.markets/) 交易股票和期权、分析市场数据并构建策略
- <img height="12" width="12" src="https://www.alphavantage.co/logo.png/" alt="AlphaVantage Logo" /> **[AlphaVantage](https://mcp.alphavantage.co/)** - 连接到 100 多个 API 以获取金融市场数据，包括股票价格、基本面等来自 [AlphaVantage](https://www.alphavantage.co) 的数据
- <img height="12" width="12" src="https://alttester.com/app/themes/alttester-sage-theme/public/images/logo-alttester.038ec8.png" alt="AltTester Logo" /> **[AltTester®](https://alttester.com/docs/desktop/latest/pages/ai-extension.html)** - 使用 AltTester® 功能连接并测试您的 Unity 或 Unreal 游戏。使用 [AltTester](https://alttester.com) 和 AltTester® MCP 服务器更快、更智能地编写游戏测试自动化。
- <img height="12" width="12" src="assets/008-amplitude-logo-cabe1b451a.svg" alt="Amplitude Logo" /> **[Amplitude](https://amplitude.com/docs/analytics/amplitude-mcp)** - Amplitude MCP 服务器可实现 AI 助手与您的产品数据之间的无缝集成，让您可以直接从 AI 界面搜索、分析和查询图表、仪表板、实验、功能标志和指标。
- <img height="12" width="12" src="https://www.antom.com/favicon.ico" alt="Antom Logo" /> **[Antom](https://github.com/alipay/global-antom-mcp)** - 将您的 AI 代理连接到 Antom Checkout Payment。
- <img height="12" width="12" src="https://developers.anytype.io/img/favicon.ico" alt="Anytype Logo" /> **[Anytype](https://github.com/anyproto/anytype-mcp)** - MCP 服务器使 AI 助手能够与 [Anytype](https://anytype.io)（本地协作 wiki）进行交互，以通过自然语言组织对象、列表等。
- <img height="12" width="12" src="https://doris.apache.org/images/favicon.ico" alt="Apache Doris Logo" /> **[Apache Doris](https://github.com/apache/doris-mcp-server)** - MCP Server For [Apache Doris](https://doris.apache.org/)，基于MPP的实时数据仓库。
- <img height="12" width="12" src="https://iotdb.apache.org/img/logo.svg" alt="Apache IoTDB Logo" /> **[Apache IoTDB](https://github.com/apache/iotdb-mcp-server)** - [Apache IoTDB](https://github.com/apache/iotdb) 数据库的 MCP 服务器及其工具
- **[Apache Pinot](https://github.com/startreedata/mcp-pinot)** – MCP server for running real - Apache Pinot 上的时间分析查询，这是一个开源 OLAP 数据库，专为高吞吐量、低延迟的实时应用程序而构建。
- <img height="12" width="12" src="https://apify.com/favicon.ico" alt="Apify Logo" /> **[Apify](https://github.com/apify/apify-mcp-server)** - 使用 6,000 多个预构建的云工具从网站、电子商务、社交媒体、搜索引擎、地图等中提取数据
- <img height="12" width="12" src="https://2052727.fs1.hubspotusercontent-na1.net/hubfs/2052727/cropped-cropped-apimaticio-favicon-1-32x32.png" alt="APIMatic Logo" /> **[APIMatic MCP](https://github.com/apimatic/apimatic-validator-mcp)** - APIMatic MCP 服务器用于使用 [APIMatic](https://www.apimatic.io/) 验证 OpenAPI 规范。服务器利用 APIMatic 的 API 处理 OpenAPI 文件并返回验证摘要。
- <img height="12" width="12" src="https://apollo-server-landing-page.cdn.apollographql.com/_latest/assets/favicon.png" alt="Apollo Graph Logo" /> **[Apollo MCP Server](https://github.com/apollographql/apollo-mcp-server/)** - 将 GraphQL API 连接到 AI 代理
- <img height="12" width="12" src="https://appium.io/docs/en/latest/assets/images/appium-logo-horiz.png" alt="Appium Logo" /> **[Appium MCP Server](https://github.com/appium/appium-mcp.git)** - 用于移动开发和自动化的 MCP 服务器 | iOS、Android、模拟器、模拟器和真实设备
- <img height="12" width="12" src="https://developer.aqara.com/favicon.ico" alt="Aqara Logo" /> **[Aqara MCP Server](https://github.com/aqara/aqara-mcp-server/)** - 使用自然语言控制 [Aqara](https://www.aqara.com/) 智能家居设备、查询状态、执行场景等。
- <img height="12" width="12" src="https://media.licdn.com/dms/image/v2/C4D0BAQEeD7Dxbpadkw/company-logo_200_200/company-logo_200_200/0/1644692667545/archbee_logo?e=2147483647&v=beta&t=lTi9GRIoqzG6jN3kJC26uZWh0q3uiQelsH6mGoq_Wfw" alt="Archbee Logo" /> **[Archbee](https://www.npmjs.com/package/@archbee/mcp)** - 编写和发布文档，成为人工智能即时答案的可信来源。停止修补工具并使用 [Archbee](https://www.archbee.com/) — 第一个完整的文档平台。
- <img height="12" width="12" src="https://phoenix.arize.com/wp-content/uploads/2023/04/cropped-Favicon-32x32.png" alt="Arize-Phoenix Logo" /> **[Arize Phoenix](https://github.com/Arize-ai/phoenix/tree/main/js/packages/phoenix-mcp)** - 使用开源 AI 和 LLM 可观测性工具 [Arize Phoenix](https://github.com/Arize-ai/phoenix) 检查跟踪、管理提示、整理数据集并运行实验。
- <img height="12" width="12" src="https://731523176-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaVUBXRZbpAgtjYf5HsvO%2Fuploads%2FaRRrVVocXCTr6GkepfCx%2Flogo_color.svg?alt=media&token=3ba24089-0ab2-421f-a9d9-41f2f94f954a" alt="Armor Logo" /> **[Armor Crypto MCP](https://github.com/armorwallet/armor-crypto-mcp)** - MCP 可与多个区块链、质押、DeFi、交换、桥接、钱包管理、DCA、限价订单、代币查找、跟踪等接口。
- <img height="12" width="12" src="https://console.asgardeo.io/app/libs/themes/wso2is/assets/images/branding/favicon.ico" alt="Asgardeo Logo" /> **[Asgardeo](https://github.com/asgardeo/asgardeo-mcp-server)** - MCP 服务器通过 LLM 工具与您的 [Asgardeo](https://wso2.com/asgardeo) 组织进行交互。
- <img height="12" width="12" src="https://www.datastax.com/favicon-32x32.png" alt="DataStax logo" /> **[Astra DB](https://github.com/datastax/astra-db-mcp)** - 用于管理 [DataStax Astra DB](https://www.datastax.com/products/datastax-astra) NoSQL 数据库中的集合和文档的综合工具，具有创建、更新、删除、查找和关联的批量操作等全方位操作。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/66598898fd13d51606c3215d/66ccbfef13bd8bc19d587578_favicon-32x32.png" alt="Atla Logo" /> **[Atla](https://github.com/atla-ai/atla-mcp-server)** - 使 AI 代理能够与 [Atla API](https://docs.atla-ai.com/) 交互，以进行最先进的 LLMJ 评估。
- <img height="12" width="12" src="https://assets.atlan.com/assets/atlan-a-logo-blue-background.png" alt="Atlan Logo" /> **[Atlan](https://github.com/atlanhq/agent-toolkit/tree/main/modelcontextprotocol)** - Atlan 模型上下文协议服务器允许您通过多种工具与 [Atlan](https://www.atlan.com/) 服务进行交互。
- <img height="12" width="12" src="https://www.atlassian.com/favicon.ico" alt="Atlassian Logo" /> **[Atlassian](https://www.atlassian.com/platform/remote-mcp-server)** - 与 Jira 工作项和 Confluence 页面安全交互，并在两者之间进行搜索。
- <img height="12" width="12" src="https://res.oafimg.cn/-/737b3b3ffed9b19e/logo.png" alt="AtomGit Logo" /> **[AtomGit](https://atomgit.com/atomgit-open-source-ecosystem/atomgit-mcp-server)** - 官方 AtomGit 服务器，用于与存储库管理、PR、问题、分支、标签等集成。
- <img height="12" width="12" src="https://atono.io/favicon.ico" alt="Atono Logo" /> **[Atono](https://docs.atono.io/docs/mcp-server-for-atono/)** - 现代产品团队将他们的人工智能助手连接到 Atano 来创建和更新故事、错误、作业和修复。
- <img height="12" width="12" src="https://resources.audiense.com/hubfs/favicon-1.png" alt="Audiense Logo" /> **[Audiense Insights](https://github.com/AudienseCo/mcp-audiense-insights)** - [Audiense](https://www.audiense.com/products/audiense-insights) 报告中的营销洞察和受众分析，涵盖人口统计、文化、影响者和内容参与度分析。
- <img height="12" width="12" src="https://cdn.auth0.com/website/website/favicons/auth0-favicon.svg" alt="Auth0 Logo" /> **[Auth0](https://github.com/auth0/auth0-mcp-server)** - MCP 服务器用于与 Auth0 租户交互，支持创建和修改操作、应用程序、表单、日志、资源服务器等。
- <img height="12" width="12" src="https://firstorder.ai/favicon_auth.ico" alt="Authenticator App Logo" /> **[Authenticator App · 2FA](https://github.com/firstorderai/authenticator_mcp)** - 安全的 MCP（模型上下文协议）服务器，使 AI 代理能够与身份验证器应用程序进行交互。
- <img height="12" width="12" src="https://a0.awsstatic.com/libra-css/images/site/fav/favicon.ico" alt="AWS Logo" /> **[AWS](https://github.com/awslabs/mcp)** - 专业的 MCP 服务器可将 AWS 最佳实践直接引入您的开发工作流程。
- <img height="12" width="12" src="https://axiom.co/favicon.ico" alt="Axiom Logo" /> **[Axiom](https://github.com/axiomhq/mcp-server-axiom)** - 以自然语言查询和分析您的 Axiom 日志、跟踪和所有其他事件数据
- <img height="12" width="12" src="https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/acom_social_icon_azure" alt="Microsoft Azure Logo" /> **[Azure](https://github.com/microsoft/mcp/tree/main/servers/Azure.Mcp.Server)** - Azure MCP 服务器使 MCP 客户端能够访问关键的 Azure 服务和工具，例如 Azure 存储、Cosmos DB、Azure CLI 等。
- <img height="12" width="12" src="assets/009-1062064-products-1-a2b6210f39.2-24x24" alt="Microsoft Azure DevOps Logo" /> **[Azure DevOps](https://github.com/microsoft/azure-devops-mcp)** - 与 Azure DevOps 服务交互，例如存储库、工作项、构建、发布、测试计划和代码搜索。
- <img height="12" width="12" src="https://application.backdocket.com/favicon.ico" alt="Backdocket Logo" /> **[Backdocket](https://ai.backdocket.com)** - 搜索、检索和更新您的 **[Backdocket](https://backdocket.com)** 数据。目前包括索赔、事项、联系人、任务和高级搜索。要轻松使用远程 Mcp 服务器，请使用以下 url：**[https://ai.backdocket.com/mcp]([https://backdocket.com](https://ai.backdocket.com/mcp))**
- <img height="12" width="12" src="https://mapopen-website-wiki.cdn.bcebos.com/LOGO/lbsyunlogo_icon.ico" alt="Baidu Map Logo" /> **[Baidu Map](https://github.com/baidu-maps/mcp)** - [Baidu Map MCP Server](https://lbsyun.baidu.com/faq/api?title=mcpserver/base)为AI代理提供与百度地图API交互的工具，从而实现基于位置的服务和地理空间数据分析。
- <img height="12" width="12" src="https://www.bankless.com/favicon.ico" alt="Bankless Logo" /> **[Bankless Onchain](https://github.com/bankless/onchain-mcp)** - 查询链上数据，如 ERC20 代币、交易历史、智能合约状态。
- <img height="12" width="12" src="https://baserow.io/img/logo_baserow_square_large.png" alt="Baserow Logo" /> **[Baserow](https://gitlab.com/baserow/baserow/-/tree/develop/backend/src/baserow/api/mcp)** - 使用 MCP 集成从 Baserow 自托管或 SaaS 数据库查询数据。
- <img height="12" width="12" src="assets/010-68582c01f6420d9777922095-xasset-114rt-2911cd2f8b.avif" alt="Bauplan Logo" /> **[Bauplan](https://github.com/BauplanLabs/bauplan-mcp-server)** - 管理 Bauplan Lakehouse：查询表、创建数据分支、运行管道、检索日志。
- <img height="12" width="12" src="https://bicscan.io/favicon.png" alt="BICScan Logo" /> **[BICScan](https://github.com/ahnlabio/bicscan-mcp)** - EVM 区块链地址（EOA、CA、ENS）甚至域名的风险评分/资产持有量。
- <img height="12" width="12" src="https://www.bitnovo.com/favicons/favicon-196x196.png" alt="Bitnovo Logo" /> **[Bitnovo Pay](https://github.com/bitnovo/mcp-bitnovo-pay)** - 加密货币支付集成使人工智能代理能够通过支持比特币、以太坊和其他加密货币的 Bitnovo Pay API 创建支付、管理二维码和处理交易。
- <img height="12" width="12" src="https://web-cdn.bitrise.io/favicon.ico" alt="Bitrise Logo" /> **[Bitrise](https://github.com/bitrise-io/bitrise-mcp)** - 与您的构建、CI 和 [more](https://bitrise.io/blog/post/chat-with-your-builds-ci-and-more-introducing-the-bitrise-mcp-server) 聊天。
- <img height="12" width="12" src="https://boikot.xyz/assets/favicon.svg" alt="boikot Logo" /> **[Boikot](https://github.com/boikot-xyz/boikot)** - 通过 [boikot.xyz](https://boikot.xyz/) 了解主要公司的道德和不道德行为。
- <img height="12" width="12" src="https://boldsign.com/favicon.ico" alt="BoldSign Logo" /> **[BoldSign](https://github.com/boldsign/boldsign-mcp)** - 使用 [BoldSign](https://boldsign.com/) 轻松搜索、请求和管理电子签名合同。
- <img height="12" width="12" src="https://boost.space/favicon.ico" alt="Boost.space Logo" /> **[Boost.space](https://github.com/boostspace/boostspace-mcp-server)** - 与 [Boost.space](https://boost.space) 集成的 MCP 服务器，可实现来自 2000 多个来源的集中、自动化业务数据。
- <img height="12" width="12" src="https://boostsecurity.io/hs-fs/hubfs/blue-logo.png" alt="BoostSecurity Logo" /> **[BoostSecurity](https://github.com/boost-community/boost-mcp)** - 在 [BoostSecurity](https://boostsecurity.io/) 的支持下，MCP 可以保护编码代理，防止引入与漏洞、恶意软件或拼写错误的依赖关系。
- <img height="12" width="12" src="https://www.box.com/favicon.ico" alt="Box Logo" /> **[Box](https://github.com/box-community/mcp-server-box)** - 通过Box AI与智能内容管理平台交互。
- <img height="12" width="12" src="https://www.brightdata.com/favicon.ico" alt="BrightData Logo" /> **[BrightData](https://github.com/luminati-io/brightdata-mcp)** - 发现、提取网络并与之交互 - 一个支持跨公共互联网自动访问的界面。
- <img height="12" width="12" src="https://browserbase.com/favicon.ico" alt="Browserbase Logo" /> **[Browserbase](https://github.com/browserbase/mcp-server-browserbase)** - 在云中自动执行浏览器交互（例如 Web 导航、数据提取、表单填写等）
- <img height="12" width="12" src="https://browserstack.wpenginepowered.com/wp-content/themes/browserstack/img/favicons/favicon.ico" alt="BrowserStack Logo" /> **[BrowserStack](https://github.com/browserstack/mcp-server)** - 访问 BrowserStack 的 [Test Platform](https://www.browserstack.com/test-platform) 来调试、编写和修复测试、进行可访问性测试等。
- <img height="12" width="12" src="assets/011-favico-8752def2d4.png" alt="Buildable Logo" />**[Buildable](https://github.com/chunkydotdev/bldbl-mcp)** (TypeScript) - 用于可构建 AI 驱动的开发平台的官方 MCP 服务器。使人工智能助手能够管理任务、跟踪进度、获取项目背景以及与人类就软件项目进行协作。
- <img height="12" width="12" src="https://www.google.com/s2/favicons?domain=buildkite.com&sz=24" alt="Buildkite Logo" /> **[Buildkite](https://github.com/buildkite/buildkite-mcp-server)** - 将 Buildkite 数据（管道、构建、作业、测试）公开给 AI 工具和编辑器。
- <img height="12" width="12" src="https://builtwith.com/favicon.ico" alt="BuiltWith Logo" /> **[BuiltWith](https://github.com/builtwith/mcp)** - 识别任何网站背后的技术堆栈。
- <img height="12" width="12" src="https://portswigger.net/favicon.ico" alt="PortSwigger Logo" /> **[Burp Suite](https://github.com/PortSwigger/mcp-server)** - MCP 服务器扩展允许 AI 客户端连接到 [Burp Suite](https://portswigger.net)
- <img src="https://app.cal.com/favicon.ico" alt="Cal.com" width="12" height="12"> **[Cal.com](https://www.npmjs.com/package/@calcom/cal-mcp?activeTab=readme)** - 连接到 Cal.com API 来安排和管理预订和约会。
- <img height="12" width="12" src="https://campertunity.com/assets/icon/favicon.ico" alt="Campertunity Logo" /> **[Campertunity](https://github.com/campertunity/mcp-server)** - 在 Campertunity 上搜索世界各地的露营地、检查供应情况并提供预订链接。
- <img height="12" width="12" src="https://static.canva.com/static/images/favicon.ico" alt="Canva logo" /> **[Canva](https://www.canva.dev/docs/apps/mcp-server/)** — Provide AI - 为 [Canva](https://canva.com) 应用程序和集成提供强大的开发帮助。
- <img height="12" width="12" src="https://carbonvoice.app/favicon.ico" alt="Carbon Voice Logo" /> **[Carbon Voice](https://github.com/PhononX/cv-mcp-server)** - 将 AI 代理连接到 [Carbon Voice](https://getcarbon.app) 的 MCP 服务器。在 [Carbon Voice](https://getcarbon.app) 中创建、管理语音消息、对话、私信、文件夹、语音备忘录、AI 操作等并与之交互。
- <img height="12" width="12" src="https://play.cartesia.ai/icon.png" alt="Cartesia logo" /> **[Cartesia](https://github.com/cartesia-ai/cartesia-mcp)** - 连接[Cartesia](https://cartesia.ai/)语音平台，进行文字转语音、语音克隆等操作。
- <img height="12" width="12" src="https://www.cashfree.com/favicon.ico" alt="Cashfree logo" /> **[Cashfree](https://github.com/cashfree/cashfree-mcp)** - [Cashfree Payments](https://www.cashfree.com/)官方MCP服务器。
- **[CB Insights](https://github.com/cbinsights/cbi-mcp-server)** - 使用 [CB Insights](https://www.cbinsights.com) MCP 服务器连接到 [ChatCBI](https://www.cbinsights.com/chatcbi/)
- <img height="12" width="12" src="https://chainaware.ai/assets/brand/chainawareai-logo.svg" alt="ChainAware.ai Logo" /> **[Behavioural Prediction](https://github.com/ChainAware/behavioral-prediction-mcp)** - 由 [ChainAware.ai](https://www.chainaware.ai) 提供支持的人工智能工具，用于分析钱包行为预测、欺诈检测和地毯拉动预测。
- <img height="12" width="12" src="https://www.chargebee.com/static/resources/brand/favicon.png" alt="Chargebee Logo" /> **[Chargebee](https://github.com/chargebee/agentkit/tree/main/modelcontextprotocol)** - 将 AI 代理连接到 [Chargebee platform](https://www.chargebee.com) 的 MCP 服务器。
- <img height="12" width="12" src="https://cheqd.io/wp-content/uploads/2023/03/logo_cheqd_favicon.png" alt="Cheqd Logo" /> **[Cheqd](https://github.com/cheqd/mcp-toolkit)** - 通过 [cheqd's](https://cheqd.io) 信任注册表和凭证，使 AI 代理得到信任、验证、防止欺诈、保护您的声誉等。
- <img height="12" width="12" src="https://cdn.chiki.studio/brand/logo.png" alt="Chiki StudIO Logo" /> **[Chiki StudIO](https://chiki.studio/galimybes/mcp/)** - 完全通过配置（无代码）创建您自己的可配置 MCP 服务器，并提供说明、提示和工具支持。
- <img height="12" width="12" src="https://trychroma.com/_next/static/media/chroma-logo.ae2d6e4b.svg" alt="Chroma Logo" /> **[Chroma](https://github.com/chroma-core/chroma-mcp)** - 使用开源 AI 应用数据库进行嵌入、矢量搜索、文档存储和全文搜索
- <img height="12" width="12" src="https://www.google.com/chrome/static/images/favicons/favicon-32x32.png" alt="Chrome" /> **[Chrome DevTools](https://github.com/ChromeDevTools/chrome-devtools-mcp)** - 使 AI 编码助手能够直接在 Chrome 中调试网页，提供运行时洞察和调试功能。
- <img height="12" width="12" src="https://www.chronulus.com/favicon/chronulus-logo-blue-on-alpha-square-128x128.ico" alt="Chronulus AI Logo" /> **[Chronulus AI](https://github.com/ChronulusAI/chronulus-mcp)** - 使用 Chronulus AI 预测和预测代理来预测任何事情。
- <img height="12" width="12" src="https://circleci.com/favicon.ico" alt="CircleCI Logo" /> **[CircleCI](https://github.com/CircleCI-Public/mcp-server-circleci)** - 启用 AI 代理来修复 CircleCI 的构建失败。
- <img height="12" width="12" src="https://assets.zilliz.com/Zilliz_Logo_Mark_White_20230223_041013_86057436cc.png" alt="Claude Context Logo" /> **[Claude Context](https://github.com/zilliztech/claude-context)** - 将您的代码库作为 Claude Code 的上下文
- <img height="12" width="12" src="https://cleanupcrew.ai/favicon-light.png" alt="Cleanup Crew logo" /> **[Cleanup Crew](https://cleanupcrew.ai/install)** - 使用人工智能编码工具为非技术创始人提供实时人工支持服务。当 AI 遇到困难时，直接从 IDE 请求即时人工帮助。
- <img height="12" width="12" src="https://clickhouse.com/favicon.ico" alt="ClickHouse Logo" /> **[ClickHouse](https://github.com/ClickHouse/mcp-clickhouse)** - 查询您的 [ClickHouse](https://clickhouse.com/) 数据库服务器。
- <img height="12" width="12" src="https://brand.clicksend.com/_ipx/s_794x608/img/clicksend_icon_only.svg" alt="ClickSend Logo" /> **[ClickSend](https://github.com/ClickSend/clicksend-mcp-server/)** - 这是由 ClickSend 团队开发的官方 ClickSend MCP 服务器。
- <img height="12" width="12" src="assets/012-206176626-54d68c6540.png" alt="Clix Logo" /> **[Clix MCP Server](https://github.com/clix-so/clix-mcp-server)** - Clix MCP 服务器使 AI 代理能够提供实时、可信的 Clix 文档和 SDK 代码示例，以实现无缝集成。
- <img height="12" width="12" src="https://7463-tcb-advanced-a656fc-1257967285.tcb.qcloud.la/mcp/cloudbase-logo.svg" alt="CloudBase Logo" /> **[CloudBase](https://github.com/TencentCloudBase/CloudBase-AI-ToolKit)** - [Tencent CloudBase](https://tcb.cloud.tencent.com/) 为微信小程序和全栈应用提供无服务器云功能和数据库的一站式后端服务
- <img height="12" width="12" src="https://www.cloudbees.com/favicon.ico" alt="CloudBees Logo" /> **[CloudBees CI](https://docs.cloudbees.com/docs/cloudbees-ci-mcp-router/latest/)** - 允许 AI 访问您的 [CloudBees CI](https://www.cloudbees.com/capabilities/continuous-integration) 集群（基于 Jenkins® 的企业级解决方案）。
- <img height="12" width="12" src="https://www.cloudbees.com/favicon.ico" alt="CloudBees Logo" /> **[CloudBees Unify](https://docs.cloudbees.com/docs/cloudbees-unify-mcp-server/latest/install/mcp-server)** - 启用 AI 对您的 [CloudBees Unify](https://www.cloudbees.com/unify) 环境的访问。
- <img height="12" width="12" src="https://www.cloudbet.com/favicon.ico" alt="Cloudbet Logo" /> **[Cloudbet](https://github.com/cloudbet/sports-mcp-server)** - 通过 Cloudbet API 构建结构化体育和电子竞技数据：赛程、实时赔率、投注限额和市场。
- <img src="http://www.google.com/s2/favicons?domain=www.cloudera.com" alt="Cloudera Iceberg" width="12" height="12"> **[Cloudera Iceberg](https://github.com/cloudera/iceberg-mcp-server)** - 在 [Open Data Lakehouse](https://www.cloudera.com/products/open-data-lakehouse.html) 上启用 AI。
- <img height="12" width="12" src="assets/013-cloudflare-6b92bc0436.svg" /> **[Cloudflare](https://github.com/cloudflare/mcp-server-cloudflare)** - 在 Cloudflare 开发者平台上部署、配置和查询您的资源（例如 Workers/KV/R2/D1）
- <img src="assets/014-67c0f1e272e51cf3c511c17c-gyph-ce81248e7d.svg" alt="Cloudinary" width="12" height="12"> **[Cloudinary](https://github.com/cloudinary/mcp-servers)** - 将 Cloudinary 的媒体上传、转换、AI 分析、管理、优化和交付作为 AI 代理可用的工具
- <img height="12" width="12" src="https://raw.githubusercontent.com/Cloudsway-AI/smartsearch/refs/heads/main/plugin_cloudsway.ico" alt="Cloudsway Logo" /> **[Cloudsway SmartSearch](https://github.com/Cloudsway-AI/smartsearch)** - 由 Cloudsway 提供支持的 Web 搜索 MCP 服务器，支持关键字搜索、语言和安全选项。返回结构化 JSON 结果。
- <img height="12" width="12" src="https://app.codacy.com/static/images/favicon-16x16.png" alt="Codacy Logo" /> **[Codacy](https://github.com/codacy/codacy-mcp-server/)** - 与 [Codacy](https://www.codacy.com) API 交互，查询代码质量问题、漏洞和有关代码的覆盖率见解。
- <img height="12" width="12" src="https://codelogic.com/wp-content/themes/codelogic/assets/img/favicon.png" alt="CodeLogic Logo" /> **[CodeLogic](https://github.com/CodeLogicIncEngineering/codelogic-mcp-server)** - 与 [CodeLogic](https://codelogic.com)（一个软件智能平台）交互，该平台可绘制复杂代码和数据架构依赖关系图，以提高 AI 准确性和洞察力。
- <img height="12" width="12" src="assets/015-day-1-693b644a32.svg" alt="Coinex Logo" /> **[Coinex](https://github.com/coinexcom/coinex_mcp_server)** - 官方[Coinex API](https://docs.coinex.com/api/v2)。 MCP服务器与CoinEx加密货币交易所对接，可检索市场数据、K线数据、订单深度、账户余额查询、下单等。
- <img height="12" width="12" src="https://www.coingecko.com/favicon.ico" alt="CoinGecko Logo" /> **[CoinGecko](https://github.com/coingecko/coingecko-typescript/tree/main/packages/mcp-server)** - 官方 [CoinGecko API](https://www.coingecko.com/en/api) MCP 服务器，用于加密货币价格和市场数据，涵盖 200 多个区块链网络和 800 万多个代币。
- <img height="12" width="12" src="https://coinstats.app/favicon.ico" alt="CoinStats Logo" /> **[CoinStats](https://github.com/CoinStatsHQ/coinstats-mcp)** - [CoinStats API](https://coinstats.app/api-docs/mcp/connecting) 的 MCP 服务器。提供对加密货币市场数据、投资组合跟踪和新闻的访问。
- <img height="12" width="12" src="https://www.comet.com/favicon.ico" alt="Comet Logo" /> **[Comet Opik](https://github.com/comet-ml/opik-mcp)** - 以自然语言查询和分析来自法学硕士的 [Opik](https://github.com/comet-ml/opik) 日志、跟踪、提示和所有其他遥测数据。
- <img height="12" width="12" src="https://www.commercelayer.io/favicon.ico" alt="Commerce Layer Logo" /> **[Commerce Layer](https://github.com/commercelayer/mcp-server-metrics)** - 与商业层指标 API 交互。
- <img height="12" width="12" src="https://platform.composio.dev/favicon.ico" alt="Composio Logo" /> **[Composio](https://docs.composio.dev/docs/mcp-overview#-getting-started)** – 使用 [Composio](https://composio.dev) 连接 100 多个工具。零设置。内置身份验证。为特工而生，为人类服务。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/6572bd8c27ee5db3eb91f4b3/6572bd8d27ee5db3eb91f55e_favicon-dashflow-webflow-template.svg" alt="OSS Conductor Logo" /> <img height="12" width="12" src="https://cdn.prod.website-files.com/68c3f472828bb14d0564ad4a/68c3f472828bb14d0564b0ab_Orkes%20Logo%20Symbol.svg" alt="Orkes Conductor Logo" />**[Conductor](https://github.com/conductor-oss/conductor-mcp)** - 与 Conductor（OSS 和 Orkes）REST API 交互。
- <img height="12" width="12" src="https://configcat.com/favicon.ico" alt="ConfigCat Logo" /> **[ConfigCat](https://github.com/configcat/mcp-server)** - 使 AI 工具能够与 [ConfigCat](https://configcat.com)（面向团队的功能标记服务）进行交互。支持管理 ConfigCat 功能标志、配置、环境、产品和组织。帮助集成 ConfigCat SDK、实现功能标志并删除僵尸（陈旧）标志。
- <img height="12" width="12" src="https://www.confluent.io/favicon.ico" alt="Confluent Logo" /> **[Confluent](https://github.com/confluentinc/mcp-confluent)** - 与 Confluence Kafka 和 Confluence Cloud REST API 交互。
- <img height="12" width="12" src="assets/016-mattjoyce-b0a62fe978.png" alt="Construe Logo" /> **[Construe](https://github.com/mattjoyce/mcp-construe)** - FastMCP 服务器用于智能 ObsidianVault 上下文管理，具有 frontmatter 过滤、自动分块和安全双向知识操作。
- <img height="12" width="12" src="https://ginylil.com/favicon.ico" alt="Ginylil Logo" /> **[Context Templates](https://github.com/ginylil/context-templates)** - 可重用上下文模板的开源集合，旨在帮助开发人员跨各种开发任务构建提示、配置和工作流程。鼓励社区贡献以扩展和完善可用模板。
- <img src="https://contrastsecurity.com/favicon.ico" alt="Contrast Security" width="12" height="12"> **[Contrast Security](https://github.com/Contrast-Security-OSS/mcp-contrast)** - 将 Contrast 的漏洞和 SCA 数据带入您的编码代理中，以快速修复漏洞。
- <img height="12" width="12" src="https://www.convex.dev/favicon.ico" alt="Convex Logo" /> **[Convex](https://stack.convex.dev/convex-mcp-server)** - 内省并查询部署到 Convex 的应用程序。
- <img height="12" width="12" src="https://www.cortex.io/favicon.ico" alt="Cortex Logo" /> **[Cortex](https://github.com/cortexapps/cortex-mcp)** - [Cortex](https://www.cortex.io) 的官方 MCP 服务器。
- <img height="12" width="12" src="assets/017-605755-fba2742d56.png" alt="Couchbase Logo" /> **[Couchbase](https://github.com/Couchbase-Ecosystem/mcp-server-couchbase)** - 与 Couchbase 集群中存储的数据进行交互。
- <img height="12" width="12" src="https://www.courier.com/favicon.ico" alt="Courier Logo" /> **[Courier](https://www.courier.com/docs/tools/mcp)** - 通过电子邮件、短信、推送、Slack 和 Microsoft Teams 构建、更新和发送多渠道通知。
- <img height="12" width="12" src="assets/018-b256f9fa-2020-4b37-9644-c77229ef182b-8ebe2829a8.jpg" alt="CRIC 克而瑞 LOGO"> **[CRIC Wuye AI](https://github.com/wuye-ai/mcp-server-wuye-ai)** - 与克而瑞五爷AI平台能力互动，专为物业管理行业打造的智能助手。
- <img height="12" width="12" src="https://www.crowdstrike.com/etc.clientlibs/crowdstrike/clientlibs/crowdstrike-common/resources/favicon.ico" alt="CrowdStrike Logo" /> **[CrowdStrike Falcon](https://github.com/CrowdStrike/falcon-mcp)** - 将 AI 代理与 CrowdStrike Falcon 平台连接起来，进行智能安全分析，提供对检测、事件、行为、威胁情报、主机、漏洞和身份保护功能的编程访问。
- <img height="12" width="12" src="assets/019-58433296-a82a41a4b8.png" alt="CTERA Edge Filer" /> **[CTERA Edge Filer](https://github.com/ctera/mcp-ctera-edge)** - CTERA Edge Filer 提供智能边缘缓存和多协议文件访问，支持跨核心和远程站点快速、安全地访问文件。
- <img height="12" width="12" src="assets/019-58433296-a82a41a4b8.png" alt="CTERA Portal" /> **[CTERA Portal](https://github.com/ctera/mcp-ctera-core)** - CTERA Portal 是一个多租户、多云平台，可提供全球命名空间和跨 PB 级分布式内容的统一管理。
- <img height="12" width="12" src="https://customer.io/favicon.ico" alt="Customer.io Logo" /> **[Customer.io](https://docs.customer.io/ai/mcp-server/)** - 让任何 LLM 直接使用您的 Customer.io 工作区来创建细分、检查用户配置文件、搜索客户和访问工作区数据。分析客户属性、管理受众定位并探索您的工作空间，而无需切换选项卡。
- <img height="12" width="12" src="https://app.cycode.com/img/favicon.ico" alt="Cycode Logo" /> **[Cycode](https://github.com/cycodehq/cycode-cli#mcp-command-experiment)** - 通过使用 [Cycode](https://cycode.com/) 进行 SAST、SCA、Secrets 和 IaC 扫描，提高开发生命周期的安全性。
- <img height="12" width="12" src="http://app.itsdart.com/static/img/favicon.png" alt="Dart Logo" /> **[Dart](https://github.com/its-dart/dart-mcp-server)** - 在 [Dart](https://itsdart.com)（一款 AI 原生项目管理工具）中与任务、文档和项目数据进行交互
- <img height="12" width="12" src="assets/020-databricks-symbol-color-fdacdd4615.svg" alt="Databricks Logo" /> **[Databricks](https://docs.databricks.com/aws/en/generative-ai/mcp/)** - 使用统包管理的 MCP 服务器连接到数据、AI 工具和代理以及 Databricks 平台的其余部分。或者，在 Databricks 安全和数据治理边界内托管您自己的自定义 MCP 服务器。
- <img height="12" width="12" src="assets/021-cropped-artboard-1-32x32-f7b2c38671.png" alt="DataHub Logo" /> **[DataHub](https://github.com/acryldata/mcp-server-datahub)** - 使用 [DataHub](https://datahub.com/) 元数据搜索数据资产、遍历数据沿袭、编写 SQL 查询等。
- <img height="12" width="12" src="https://www.datawrapper.de/favicon-32x32.png" alt="Datawrapper logo"> **[Datawrapper](https://github.com/palewire/datawrapper-mcp)** - 模型上下文协议 (MCP) 服务器，用于使用 AI 助手创建 [Datawrapper](https://datawrapper.de) 图表。
- <img height="12" width="12" src="https://www.daytona.io/brand/social-daytona-icon.png" alt="Daytona Logo" /> **[Daytona](https://github.com/daytonaio/daytona/tree/main/apps/cli/mcp)** - 使用 [Daytona](https://daytona.io) 沙箱快速安全地执行 AI 生成的代码
- <img height="12" width="12" src="https://debugg.ai/favicon.svg" alt="Debugg AI Logo" /> **[Debugg.AI](https://github.com/debugg-ai/debugg-ai-mcp)** - 通过 [Debugg.AI](https://debugg.ai) 远程浏览测试代理对任何代码生成平台进行零配置、完全 AI 管理的端到端测试。
- <img height="12" width="12" src="https://www.deepl.com/img/logo/deepl-logo-blue.svg" alt="DeepL Logo" /> **[DeepL](https://github.com/DeepLcom/deepl-mcp-server)** - 使用 [DeepL](https://deepl.com) 自己的 AI 模型翻译或重写文本
- <img height="12" width="12" src="https://web-st.oss-cn-shanghai.aliyuncs.com/www/static/icon/bitbug_favicon.ico" alt="DeepQ Logo"> **[DeepQ](https://github.com/shenqingtech/deepq-financial-toolkit-mcp-server)** - 深擎科技金融工具包MCP Server是一款中文金融AI工具包，为AI大语言模型提供全面的金融数据和分析工具支持。
- <img height="12" width="12" src="https://defang.io/_next/static/media/defang-icon-dark-colour.25f95b77.svg" alt="Defang Logo" /> **[Defang](https://github.com/DefangLabs/defang/blob/main/src/pkg/mcp/README.md)** - 使用 [Defang](https://www.defang.io) 平台将您的项目无缝部署到云端，而无需离开您的集成开发环境
- <img height="12" width="12" src="https://deployhq.com/assets/favicon-357ebe39b58f28869358da83948e76e7cadfb0791c97af34abfe346f5e3ef634.png" alt="DeployHQ Logo" /> **[DeployHQ](https://github.com/deployhq/deployhq-mcp-server)** – 用于 DeployHQ API 集成的 MCP 服务器，使 AI 助手能够管理部署、列出项目和监控部署状态。
- <img height="12" width="12" src="https://destinia.com/headers/ilusion/sunrise/dist/favicon/favicon-16x16.png?v=PCJysKzN" alt="Destinia Logo" /> **[Destinia](https://destinia.com/developers)** - 提供搜索 Destinia 酒店并获取列表详细信息的工具。
- <img height="12" width="12" src="https://detailer.ginylil.com/favicon.ico" alt="Detailer Logo" /> **[Detailer](https://detailer.ginylil.com/)** – 立即为您的 GitHub 存储库生成丰富的、由 AI 驱动的文档。专为人工智能代理而设计，可在采取行动之前获取深入的项目背景。
- <img height="12" width="12" src="https://devcycle.com/_next/image?url=%2Fassets%2Fbrand%2FColor-logo-mark.png&w=384&q=75" alt="DevCycle Logo" /> **[DevCycle](https://docs.devcycle.com/cli-mcp/mcp-getting-started)** - 在 AI 编码助手中使用自然语言创建和监控功能标志。
- <img height="12" width="12" src="https://www.devexpress.com/Content/Core/favicon.ico" alt="DevExpress Logo" /> **[DevExpress](https://docs.devexpress.com/GeneralInformation/405551/help-resources/dev-express-documentation-mcp-server-configure-an-ai-powered-assistant)** 文档 MCP 服务器 — 立即在 AI 驱动下访问 [DevExpress](https://www.devexpress.com) UI 组件 API 上的 300,000 多个帮助主题 — 就在您选择的 AI 编码助手/IDE 中。
- <img height="12" width="12" src="https://www.devhub.com/img/upload/favicon-196x196-dh.png" alt="DevHub Logo" /> **[DevHub](https://github.com/devhub/devhub-cms-mcp)** - 在[DevHub](https://www.devhub.com) CMS平台内管理和利用网站内容
- <img height="12" width="12" src="https://devrev.ai/favicon.ico" alt="DevRev Logo" /> **[DevRev](https://github.com/devrev/mcp-server)** - 与 DevRev API 集成的 MCP 服务器，用于搜索 DevRev 知识图，其中可以从 diff 导入对象。来源列出了 [here](https://devrev.ai/docs/import#available-sources)。
- <img height="12" width="12" src="https://dexpaprika.com/favicon.ico" alt="DexPaprika Logo" /> **[DexPaprika (CoinPaprika)](https://github.com/coinpaprika/dexpaprika-mcp)** - 使用 CoinPaprika 的 [DexPaprika](https://dexpaprika.com) 跨多个区块链网络访问实时 DEX 数据、流动性池、代币信息和交易分析。
- **[Diffusion](https://github.com/diffusiondata/diffusion-mcp-server)** - 连接到任何 Diffusion 服务器以探索主题、创建/更新主题、管理会话、配置主题视图和指标等功能以及监控服务器。
- <img height="12" width="12" src="assets/022-dolt-logo-3x-9fe5fc3459.svg" alt="Dolt Logo" /> **[Dolt](https://github.com/dolthub/dolt-mcp)** - 用于版本控制的 [Dolt](https://doltdb.com/) 数据库的官方 MCP 服务器。
- <img height="12" width="12" src="https://eu.getdot.ai/favicon.ico" alt="GetDot.ai Logo" /> **[Dot (GetDot.ai)](https://docs.getdot.ai/dot/integrations/mcp)** - 使用您的 AI 数据分析师 [Dot](https://getdot.ai) 从您喜爱的数据库或数据仓库（Snowflake、BigQuery、Redshift、Databricks、Clickhouse 等）获取、分析或可视化数据。此远程 MCP 服务器是为已设置 Dot 的用户提供的一键集成。
- <img height="12" width="12" src="assets/023-65421071-73fdb44b0b.png" alt="Drata Logo" /> **[Drata](https://drata.com/mcp)** - 亲身体验我们的实验性 MCP 服务器，将实时合规性智能引入您的 AI 工作流程。
- <img height="12" width="12" src="assets/024-204530939-0cea9b9256.png" alt="Dumpling AI Logo" /> **[Dumpling AI](https://github.com/Dumpling-AI/mcp-server-dumplingai)** - 通过 [Dumpling AI](https://www.dumplingai.com/) 访问数据、网页抓取和文档转换 API
- <img height="12" width="12" src="assets/025-58178984-5a7456eb42.png" alt="Dynatrace Logo" /> **[Dynatrace](https://github.com/dynatrace-oss/dynatrace-mcp)** - 管理 [Dynatrace Platform ](https://www.dynatrace.com/platform) 并与之交互，以实现实时观察和监控。
- <img height="12" width="12" src="https://e2b.dev/favicon.ico" alt="E2B Logo" /> **[E2B](https://github.com/e2b-dev/mcp-server)** - 在 [E2B](https://e2b.dev) 托管的安全沙箱中运行代码
- <img height="12" width="12" src="https://www.edgee.cloud/favicon.ico" alt="Edgee Logo" /> **[Edgee](https://github.com/edgee-cloud/mcp-server-edgee)** - 部署和管理 [Edgee](https://www.edgee.cloud) 组件和项目
- <img height="12" width="12" src="https://static.edubase.net/media/brand/favicon/favicon-32x32.png" alt="EduBase Logo" /> **[EduBase](https://github.com/EduBase/MCP)** - 与 [EduBase](https://www.edubase.net) 互动，这是一个具有高级测验、考试管理和内容组织功能的综合电子学习平台
- <img height="12" width="12" src="https://www.elastic.co/favicon.ico" alt="Elasticsearch Logo" /> **[Elasticsearch](https://github.com/elastic/mcp-server-elasticsearch)** - 查询您在[Elasticsearch](https://www.elastic.co/elasticsearch)中的数据
- <img height="12" width="12" src="https://www.elastic.co/favicon.ico" alt="Elasticsearch Memory Logo" /> **[Elasticsearch Memory](https://github.com/fredac100/elasticsearch-memory-mcp)** - 具有分层分类、语义搜索和智能自动检测功能的持久内存。通过 [PyPI](https://pypi.org/project/elasticsearch-memory-mcp/) 安装。
- <img height="12" width="12" src="https://elasticemail.com/favicon.ico" alt="Elastic Email Logo" /> **[Elastic Email](https://github.com/ElasticEmail/elasticemail-mcp-server)** - Elastic Email MCP Server 为下一代 AI 代理和 MCP 兼容环境提供全面的电子邮件功能。
- <img height="12" width="12" src="assets/026-ember-black-c3b2d8aa29.png" alt="Ember AI Logo" /> **[Ember AI](https://docs.emberai.xyz/)** - 统一的 MCP 服务器，使 AI 代理能够执行跨链 DeFi 策略。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/656eaf5c6da3527caf362363/656ecc07555afac40df4c40e_Facicon.png" alt="Endor Labs Logo" /> **[Endor Labs](https://docs.endorlabs.com/deployment/ide/mcp/)** - 查找并修复代码中的安全风险。集成 [Endor Labs](https://endorlabs.com) 来扫描并保护您的代码免受漏洞和秘密泄漏。
- <img height="12" width="12" src="https://esignatures.com/favicon.ico" alt="eSignatures Logo" /> **[eSignatures](https://github.com/esignaturescom/mcp-server-esignatures)** - 用于起草、审查和发送具有约束力的合同的合同和模板管理。
- <img height="12" width="12" src="https://rainmaker.espressif.com/favicon.ico" alt="ESP RainMaker Logo" /> **[ESP RainMaker](https://github.com/espressif/esp-rainmaker-mcp)** - 用于控制和管理 ESP RainMaker 设备的官方 Espressif MCP 服务器。
- <img height="12" width="12" src="https://exa.ai/images/favicon-32x32.png" alt="Exa Logo" /> **[Exa](https://github.com/exa-labs/exa-mcp-server)** - [Exa](https://exa.ai) 为 AI 制作的搜索引擎
- <img height="12" width="12" src="https://www.explorium.ai/wp-content/uploads/2025/04/Favicon-Purple-512x512-1-150x150.png" alt="Explorium Logo" /> **[Explorium](https://github.com/explorium-ai/mcp-explorium)** - AI SDR 和 GTM 代理的 B2B 数据和基础设施 [Explorium](https://www.explorium.ai)
- **[FalkorDB](https://github.com/FalkorDB/FalkorDB-MCPServer)** - FalkorDB图数据库服务器获取模式和读/写密码[FalkorDB](https://www.falkordb.com)
- <img height="12" width="12" src="https://fetchserp.com/icon.png" alt="fetchSERP Logo" /> **[fetchSERP](https://github.com/fetchSERP/fetchserp-mcp-server-node)** - 多合一 SEO 和 Web 智能工具包 API [fetchSERP](https://www.fetchserp.com/)
- <img height="12" width="12" src="https://fewsats.com/favicon.svg" alt="Fewsats Logo" /> **[Fewsats](https://github.com/Fewsats/fewsats-mcp)** - 使 AI 代理能够使用 [Fewsats](https://fewsats.com) 以安全的方式购买任何东西
- <img height="12" width="12" src="https://fibery.io/favicon.svg" alt="Fibery Logo" /> **[Fibery](https://github.com/Fibery-inc/fibery-mcp-server)** - 在 [Fibery](https://fibery.io) 工作区中执行查询和实体操作。
- <img height="12" width="12" src="https://static.figma.com/app/icon/2/favicon.ico" alt="Figma Logo" /> **[Figma](https://github.com/figma/mcp-server-guide)** - 通过为 AI 代理提供重要的设计信息和上下文，使用官方 [Figma](https://www.figma.com) MCP 服务器从设计文件生成代码，将 Figma 直接引入您的工作流程。
- <img height="12" width="12" src="https://financialdatasets.ai/favicon.ico" alt="Financial Datasets Logo" /> **[Financial Datasets](https://github.com/financial-datasets/mcp-server)** - 为人工智能代理打造的股票市场 API
- <img height="12" width="12" src="https://www.gstatic.com/devrel-devsite/prod/v7aeef7f1393bb1d75a4489145c511cdd5aeaa8e13ad0a83ec1b5b03612e66330/firebase/images/favicon.png" alt="Firebase Logo" /> **[Firebase](https://github.com/firebase/firebase-tools/blob/master/src/mcp)** - Firebase 的实验性 [MCP Server](https://firebase.google.com/docs/cli/mcp-server) 为您的 AI 工具提供支持
- <img height="12" width="12" src="https://firecrawl.dev/favicon.ico" alt="Firecrawl Logo" /> **[Firecrawl](https://github.com/firecrawl/firecrawl-mcp-server)** - 使用 [Firecrawl](https://firecrawl.dev) 提取网页数据
- <img height="12" width="12" src="assets/027-100200663-c5d8ff5a8c.png" alt="Firefly Logo" /> **[Firefly](https://github.com/gofireflyio/firefly-mcp)** - 使用 [Firefly](https://firefly.ai) 集成、发现、管理和编码云资源。
- <img height="12" width="12" src="https://fireproof.storage/favicon.ico" alt="Fireproof Logo" /> **[Fireproof](https://github.com/fireproof-storage/mcp-database-server)** - 具有实时同步功能的不可变账本数据库
- <img height="12" width="12" src="https://fixparser.dev/favicon.ico" alt="FIXParser Logo" /> **[FIXParser](https://gitlab.com/logotype/fixparser/-/tree/main/packages/fixparser-plugin-mcp)** - 用于人工智能驱动的交易代理的现代 FIX 协议引擎
- <img height="12" width="12" src="assets/028-52471808-87268512ae.png" alt="Fluid Attacks Logo" /> **[Fluid Attacks](https://github.com/fluidattacks/mcp)** - 与 [Fluid Attacks](https://fluidattacks.com/) API 交互，实现漏洞管理、组织洞察和 GraphQL 查询执行。
- <img height="12" width="12" src="https://flutterwave.com/favicon.ico" alt="Flutterwave Logo" /> **[Flutterwave](https://github.com/bajoski34/mcp-flutterwave/tree/main)** - 与 Flutterwave 支付解决方案 API 交互，以管理交易、支付链接等。
- <img height="12" width="12" src="https://forevervm.com/icon.png" alt="ForeverVM Logo" /> **[ForeverVM](https://github.com/jamsocket/forevervm/tree/main/javascript/mcp-server)** - 运行 Python in a code sandbox.
- <img height="12" width="12" src="https://gcore.com/assets/favicon/favicon-16x16.png" alt="Gcore Logo" /> **[Gcore](https://github.com/G-Core/gcore-mcp-server)** - 通过LLM助手与Gcore平台服务交互，提供对CDN、GPU云和AI推理、视频流、WAAP以及包括实例和网络在内的云资源的统一访问。
- <img height="12" width="12" src="https://app.gibsonai.com/favicon.ico" alt="GibsonAI Logo" /> **[GibsonAI](https://github.com/GibsonAI/mcp)** - AI 驱动的云数据库：使用 AI 构建、迁移和部署数据库实例
- <img height="12" width="12" src="https://gitea.com/assets/img/favicon.svg" alt="Gitea Logo" /> **[Gitea](https://gitea.com/gitea/gitea-mcp)** - 使用 MCP 与 Gitea 实例交互。
- <img height="12" width="12" src="https://gitee.com/favicon.ico" alt="Gitee Logo" /> **[Gitee](https://github.com/oschina/mcp-gitee)** - Gitee API 集成、存储库、问题和拉取请求管理等等。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/5ee25cbe47310017adf964da/6323888a9b9f4e22a7bc766b_GG%20Favicon.svg" alt="GitGuardian Logo" /> **[GitGuardian](https://github.com/GitGuardian/gg-mcp)** - GitGuardian 官方 MCP 服务器 - 使用 GitGuardian 行业领先的 API 扫描项目，该 API 具有 500 多个秘密检测器，可在凭证到达公共存储库之前防止凭证泄露。使用丰富的上下文数据直接解决安全事件，以实现快速、自动的修复。
- <img height="12" width="12" src="assets/029-github-mark-ea2971cee799-20edf7b4fc.png" alt="GitHub Logo" /> **[GitHub](https://github.com/github/github-mcp-server)** - GitHub 的官方 MCP 服务器。
- <img height="12" width="12" src="assets/030-android-chrome-144x144-1-d1a7df4e96.png" alt="GitKraken Logo" /> **[GitKraken](https://github.com/gitkraken/gk-cli?tab=readme-ov-file#mcp-server)** - 用于与 GitKraken API 交互的 CLI。包括通过 `gk mcp` 的 MCP 服务器，它不仅包装 GitKraken API，还包装 Jira、GitHub、GitLab 等。
- <img height="12" width="12" src="https://gitlab.com/favicon.ico" alt="GitLab Logo" /> **[GitLab](https://docs.gitlab.com/user/gitlab_duo/model_context_protocol/mcp_server/)** - GitLab 的官方 MCP 服务器使 AI 工具能够通过 OAuth 2.0 安全地访问 GitLab 项目数据、管理问题并执行存储库操作。
- <img height="12" width="12" src="https://app.glean.com/images/favicon3-196x196.png" alt="Glean Logo" /> **[Glean](https://github.com/gleanwork/mcp-server)** - 使用 Glean 的 API 进行企业搜索和聊天。
- <img height="12" width="12" src="assets/031-android-chrome-192x192-41419320ba.png" alt="Globalping Logo" /> **[Globalping](https://github.com/jsdelivr/globalping-mcp-server)** - 访问包含数千个探测器的网络，以运行 ping、traceroute、mtr、http 和 DNS 解析等网络命令。
- <img height="12" width="12" src="https://gnucleus.ai/favicon.ico" alt="gNucleus Logo" /> **[gNucleus Text-To-CAD](https://github.com/gNucleus/text-to-cad-mcp)** - 使用 gNucleus AI 模型从文本生成 CAD 零件和装配体。
- <img height="12" width="12" src="https://api.gologin.com/favicon.ico" alt="GoLogin Logo" /> **[GoLogin MCP server](https://github.com/gologinapp/gologin-mcp)** - 直接通过 AI 对话管理您的 GoLogin 浏览器配置文件和自动化！
- <img height="12" width="12" src="https://www.gstatic.com/cgc/favicon.ico" alt="Google Cloud Logo" /> **[Google Cloud Run](https://github.com/GoogleCloudPlatform/cloud-run-mcp)** - 部署 code to Google Cloud Run
- <img height="12" width="12" src="assets/032-3717923-3def3595ba.png" alt="Google Maps Platform Logo" /> **[Google Maps Platform Code Assist](https://github.com/googlemaps/platform-ai/tree/main/packages/code-assist)** - 地面代理使用最新的官方文档和代码示例，以获得最佳的地理相关指导和代码。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/6605a2979ff17b2cd1939cd4/6605a460de47e7596ed84f06_icon256.png" alt="gotoHuman Logo" /> **[gotoHuman](https://github.com/gotohuman/gotohuman-mcp-server)** - 人机交互平台 - 允许人工智能代理和自动化将批准请求发送到您的 [gotoHuman](https://www.gotohuman.com) 收件箱。
- <img height="12" width="12" src="https://grafana.com/favicon.ico" alt="Grafana Logo" /> **[Grafana](https://github.com/grafana/mcp-grafana)** - 在 Grafana 实例中搜索仪表板、调查事件和查询数据源
- <img height="12" width="12" src="https://grafbase.com/favicon.ico" alt="Grafbase Logo" /> **[Grafbase](https://github.com/grafbase/grafbase/tree/main/crates/mcp)** - 通过单个命令将您的 GraphQL API 转变为具有模式智​​能的高效 MCP 服务器。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/5f5e90c17e7c9eb95c7acb17/61d3457a519242f2c75c725c_favicon.png" alt="Grain Logo" /> **[Grain](https://grain.com/release-note/06-18-2025)** - 直接在 Claude 中访问您的 Grain 会议笔记和记录，并使用本地 Claude 提示生成报告。
- <img height="12" width="12" src="assets/033-kcowbylkundff1dr452y6efjiu-d457da05e9.png" alt="Graphlit Logo" /> **[Graphlit](https://github.com/graphlit/graphlit-mcp-server)** - 除了网络爬行之外，还将从 Slack 到 Gmail 到播客提要的任何内容提取到可搜索的 [Graphlit](https://www.graphlit.com) 项目中。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/64a5291e7847ac04fe1531ad/64a529af2f1fc7debc26f2a6_favicon-32x32.avif" alt="Gremlin favicon" /> **[Gremlin](https://github.com/gremlin/mcp)** - 官方 [Gremlin](https://www.gremlin.com) MCP 服务器。分析您的可靠性状况，查看最近的测试和混沌工程实验，并创建详细的报告。
- <img height="12" width="12" src="https://greptime.com/favicon.ico" alt="Greptime Logo" /> **[GreptimeDB](https://github.com/GreptimeTeam/greptimedb-mcp-server)** - 为人工智能助手提供安全、结构化的方式来探索和分析 [GreptimeDB](https://github.com/GreptimeTeam/greptimedb) 中的数据。
- <img height="12" width="12" src="https://growi.org/assets/images/favicon.ico" alt="GROWI Logo" /> **[GROWI](https://github.com/growilabs/growi-mcp-server)** - 官方 MCP 服务器与 GROWI API 集成。
- <img height="12" width="12" src="https://gyazo.com/favicon.ico" alt="Gyazo Logo" /> **[Gyazo](https://github.com/nota/gyazo-mcp-server)** - 搜索、获取、上传 Gyazo 图像并与之交互，包括元数据和 OCR 数据。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/6374050260446c42f94dc90f/63d828be3e13d32ee6973f35_favicon-32x32.png" alt="Harper Logo" /> **[Harper](https://github.com/HarperDB/mcp-server)** - MCP 服务器为 MCP 客户端提供访问 [Harper](https://www.harpersystems.dev/) 内数据的接口。
- <img height="12" width="12" src="https://www.herokucdn.com/favicons/favicon.ico" alt="Heroku Logo" /> **[Heroku](https://github.com/heroku/heroku-mcp-server)** - 通过 LLM 驱动的工具与 Heroku 平台交互，用于管理应用程序、附加组件、测功机、数据库等。
- <img height="12" width="12" src="https://heyoncall.com/favicon.ico" alt="HeyOnCall Logo" /> **[HeyOnCall](https://heyoncall.com/blog/mcp-server-for-paging-a-human)** - 寻呼人员，向免费的 [HeyOnCall](https://heyoncall.com/) iOS 或 Android 应用程序发送关键或非关键警报。
- <img height="12" width="12" src="https://hillnote.com/favicon.ico" alt="Hillnote Logo" /> **[Hillnote](https://github.com/Rajathbail/hillnote-mcp-server)** - 在 [Hillnote](https://hillnote.com) 工作区中搜索、编辑、保存和创建文档，[Hillnote](https://hillnote.com) 是一个在本地存储文件的 markdown-first 编辑器。
- <img height="12" width="12" src="https://hiveintelligence.xyz/favicon.ico" alt="Hive Intelligence Logo" /> **[Hive Intelligence](https://github.com/hive-intel/hive-crypto-mcp)** - 适用于 AI 助手的终极加密货币 MCP，可统一访问加密货币、DeFi 和 Web3 分析
- <img height="12" width="12" src="https://www.hiveflow.ai/favicon.ico" alt="Hiveflow Logo" /> **[Hiveflow](https://github.com/hiveflowai/hiveflow-mcp-server)** - 直接从您的助手创建、管理和执行代理 AI 工作流程。
- <img height="12" width="12" src="assets/034-o1cn01d9qrry1i6ltna2bra-6000000004364-2-tps-218-200-ebb6c22213.png" alt="Hologres Logo" /> **[Hologres](https://github.com/aliyun/alibabacloud-hologres-mcp-server)** - 连接[Hologres](https://www.alibabacloud.com/en/product/hologres)实例，获取表元数据，查询分析数据。
- <img height="12" width="12" src="https://brew.sh/assets/img/favicon.ico" alt="Homebrew Logo" /> **[Homebrew](https://docs.brew.sh/MCP-Server)** 允许 [Homebrew](https://brew.sh) 用户在本地运行 Homebrew 命令。
- <img height="12" width="12" src="https://www.honeycomb.io/favicon.ico" alt="Honeycomb Logo" /> **[Honeycomb](https://github.com/honeycombio/honeycomb-mcp)** 允许 [Honeycomb](https://www.honeycomb.io/) 企业客户查询和分析其数据、警报、仪表板等；以及与代码库交叉引用生产行为。
- <img height="12" width="12" src="https://hopx.ai/favicon.ico" alt="HOPX Logo" /> **[HOPX](https://github.com/hopx-ai/mcp)** - 在隔离的云容器中执行 Python、JavaScript、Bash 和 Go 代码，启动时间低于 150 毫秒。预装数据科学库（pandas、numpy、matplotlib），用于人工智能驱动的数据分析和代码测试。
- <img height="12" width="12" src="https://static.hsinfrastatic.net/StyleGuideUI/static-3.438/img/sprocket/favicon-32x32.png" alt="HubSpot Logo" /> **[HubSpot](https://developer.hubspot.com/mcp)** - 连接、管理 [HubSpot](https://www.hubspot.com/) CRM 数据并与之交互
- <img height="12" width="12" src="https://huggingface.co/datasets/huggingface/brand-assets/resolve/main/hf-logo.svg" alt="HuggingFace Logo" /> **[Hugging Face](https://huggingface.co/settings/mcp)** - 以编程方式连接到 Hugging Face Hub API：空间和论文的语义搜索、数据集和模型的探索以及访问所有兼容的 MCP Gradio 工具空间！
- <img height="12" width="12" src="https://hunter.io/favicon.ico" alt="Hunter Logo" /> **[Hunter](https://github.com/hunter-io/hunter-mcp)** - 与 [Hunter API](https://hunter.io) 交互，使用自然语言获取 B2B 数据。
- <img height="12" width="12" src="https://app.hyperbolic.xyz/hyperbolic-logo.svg" alt="Hyperbolic Labs Logo" /> **[Hyperbolic](https://github.com/HyperbolicLabs/hyperbolic-mcp)** - 与 Hyperbolic 的 GPU 云交互，使代理和法学硕士能够查看和租用可用的 GPU、通过 SSH 连接到它们，并为您运行 GPU 驱动的工作负载。
- <img height="12" width="12" src="https://hyperbrowser-assets-bucket.s3.us-east-1.amazonaws.com/Hyperbrowser-logo.png" alt="Hyperbrowsers23 Logo" /> **[Hyperbrowser](https://github.com/hyperbrowserai/mcp)** - [Hyperbrowser](https://www.hyperbrowser.ai/) 是下一代平台，支持 AI 代理并实现轻松、可扩展的浏览器自动化。
- **[IBM watsonx.data intelligence](https://github.com/IBM/data-intelligence-mcp-server)** - 在 watsonx.data 智能治理和目录、数据质量、数据沿袭和数据产品中心中查找、理解和使用您的数据
- **[IBM wxflows](https://github.com/IBM/wxflows/tree/main/examples/mcp/javascript)** - IBM 的工具平台，用于为任何数据源构建、测试和部署工具
- <img height="12" width="12" src="https://improvedigital.com/favicon.ico" alt="Improve Digital Icon" /> **[Improve Digital Publisher MCP](https://github.com/azerion/improvedigital-publisher-mcp-server)** - MCP 服务器使发布商能够将 [Improve Digital’s](https://improvedigital.com/) 库存管理系统与其 AI 工具或代理集成。
- <img height="12" width="12" src="https://www.getinboxzero.com/icon.png" alt="Inbox Zero Logo" /> **[Inbox Zero](https://github.com/elie222/inbox-zero/tree/main/apps/mcp-server)** - 电子邮件人工智能个人助理 [Inbox Zero](https://www.getinboxzero.com)
- <img height="12" width="12" src="https://www.inflectra.com/Favicon.ico" alt="Inflectra Logo" /> **[Inflectra Spira](https://github.com/Inflectra/mcp-server-spira)** - 通过 [Inflectra](https://www.inflectra.com) 连接到 SpiraTest、SpiraTeam 或 SpiraPlan 应用程序生命周期管理平台的实例
- <img height="12" width="12" src="assets/035-infobip-symbol-orange-56fd574fc0.png" alt="Infobip Logo" /> **[Infobip](https://github.com/infobip/mcp)** - 用于集成[Infobip](https://www.infobip.com/)全球云通信平台的MCP服务器。它为人工智能代理配备了通信超能力，使他们能够发送和接收 SMS 和 RCS 消息、与 WhatsApp 和 Viber 交互、自动化通信工作流程以及管理客户数据，所有这些都在生产就绪的环境中进行。
- <img height="12" width="12" src="https://inkeep.com/favicon.ico" alt="Inkeep Logo" /> **[Inkeep](https://github.com/inkeep/mcp-server-python)** - RAG 搜索由 [Inkeep](https://inkeep.com) 提供支持的内容
- <img height="12" width="12" src="https://integration.app/favicon.ico" alt="Integration App Icon" /> **[Integration App](https://github.com/integration-app/mcp-server)** - 代表您的客户与任何其他 SaaS 应用程序交互。
- <img height="12" width="12" src="https://www.ip2location.io/favicon.ico" alt="IP2Location.io Icon" /> **[IP2Location.io](https://github.com/ip2location/mcp-ip2location-io)** - 与 IP2Location.io API 交互以检索 IP 地址的地理位置信息。
- <img height="12" width="12" src="https://static.iplocate.io/custom/logo-square-rounded.png" alt="IPLocate Icon" /> **[IPLocate](https://github.com/iplocate/mcp-server-iplocate)** - 使用 [IPLocate.io](https://www.iplocate.io) 查找 IP 地址地理位置、网络信息、检测代理和 VPN 以及查找滥用联系方式
- <img height="12" width="12" src="https://jellyfish.co/favicon.ico" alt="Jellyfish Logo" /> **[Jellyfish](https://github.com/Jellyfish-AI/jellyfish-mcp)** – 通过 [Jellyfish](https://jellyfish.co) 平台为您的 AI 代理提供有关团队软件工程分配和工作流程的背景信息
- <img height="12" width="12" src="assets/036-jenkins-3fac0ca6d2.svg" alt="Jenkins Logo" /> **[Jenkins](https://plugins.jenkins.io/mcp-server/)** - 官方 Jenkins MCP 服务器插件使 AI 助手能够管理构建、检查作业状态、检索日志并通过标准化 MCP 接口与 CI/CD 管道集成。
- <img height="12" width="12" src="assets/037-jetbrains-0085917e46.svg" /> **[JetBrains](https://www.jetbrains.com/help/idea/mcp-server.html)** – 使用 JetBrains IDE 处理代码：IntelliJ IDEA、PhpStorm 等。
- <img height="12" width="12" src="assets/038-jfrog16-1-1b068b15c6.png" alt="JFrog Logo" /> **[JFrog](https://github.com/jfrog/mcp-jfrog)** - 用于 [JFrog](https://jfrog.com/) 平台 API 的模型上下文协议 (MCP) 服务器，支持存储库管理、构建跟踪、发布生命周期管理等。
- <img height="12" width="12" src="https://kagi.com/favicon.ico" alt="Kagi Logo" /> **[Kagi Search](https://github.com/kagisearch/kagimcp)** - 使用 Kagi 的搜索 API 搜索网络
- 📅 **[Kalendis](https://github.com/kalendis-dev/kalendis-mcp)** - 跨多个框架（Next.js、Express、Fastify、NestJS）为 Kalendis 调度 API 生成 TypeScript 客户端和 API 路由处理程序，从而简化可用性管理和预订功能的集成。
- <img height="12" width="12" src="assets/039-319096-79b791eb24.png" alt="Kaltura Logo" /> **[Kaltura](https://github.com/kaltura/mcp-events)** - 管理[Kaltura Event Platform](https://corp.kaltura.com/blog/best-virtual-event-platform/#what-is-a-virtual-event-platform-0)。提供用于创建、管理 Kaltura 虚拟活动并与之交互的工具和资源。
- <img height="12" width="12" src="https://kash.click/favicon.ico" alt="Kash Logo" /> **[Kash.click](https://github.com/paracetamol951/caisse-enregistreuse-mcp-server)** - 让 AI 能够访问您的销售、客户、订单、税务信息、付款以及有关您业务的所有见解
- <img height="12" width="12" src="https://connection.keboola.com/favicon.ico" alt="Keboola Logo" /> **[Keboola](https://github.com/keboola/keboola-mcp-server)** - 在单一直观平台上构建强大的数据工作流程、集成和分析。
- <img height="12" width="12" src="https://mcp.onkernel.com/favicon.svg" alt="Kernel Logo" /> **[Kernel](https://github.com/onkernel/kernel-mcp-server)** – 通过 MCP 访问内核的基于云的浏览器。
- <img height="12" width="12" src="https://keywordseverywhere.com/favicon.ico" alt="Keywords Everywhere Logo" /> **[Keywords Everywhere](https://api.keywordseverywhere.com/docs/#/mcp_integration)** – 通过官方 keywords Everywhere API MCP 服务器访问 SEO 数据。
- <img height="12" width="12" src="https://keywordspeopleuse.com/favicon.ico" alt="KeywordsPeopleUse Logo" /> **[KeywordsPeopleUse.com](https://github.com/data-skunks/kpu-mcp)** - 使用 [KeywordsPeopleUse](https://keywordspeopleuse.com) 查找人们在线提出的问题。
- <img height="12" width="12" src="https://kiln.tech/images/animated_logo.svg" alt="Kiln Logo" /> **[Kiln](https://github.com/Kiln-AI/Kiln)** - 一个免费的开源平台，用于构建生产就绪的人工智能系统。它支持 RAG 管道、AI 代理、MCP 工具调用、评估、合成数据生成和微调 - 所有这些都在 [Kiln-AI](https://kiln.tech/) 的统一框架中。
- <img height="12" width="12" src="assets/040-4815054-e3c9821d05.png" alt="Kintone Logo" /> **[Kintone](https://github.com/kintone/mcp-server)** - [Kintone](https://kintone.com) 的官方本地 MCP 服务器。
- <img height="12" width="12" src="https://kirokuforms.com/favicon.svg" alt="KirokuForms Logo" /> **[KirokuForms](https://www.kirokuforms.com/ai/mcp)** - [KirokuForms](https://www.kirokuforms.com) 是一个人工智能驱动的表单平台，将专业表单构建与人在环 (HITL) 功能相结合。通过 [MCP integration](https://kirokuforms.com/ai/mcp) 创建自定义表单、收集提交内容并将人工监督集成到 AI 工作流程中。
- <img height="12" width="12" src="assets/041-kiteworks-logo-small-461410cf9f.png" alt="Kiteworks Logo" /> **[Kiteworks](https://github.com/kiteworks/mcp)** - 与 [Kiteworks Private Data Network (PDN) platform](https://kiteworks.com) 交互的官方 MCP 服务器。
- <img height="12" width="12" src="assets/042-klavis-ai-b51f9599f6.png" alt="Klavis Logo" /> **[Klavis ReportGen](https://github.com/Klavis-AI/klavis/tree/main/mcp_servers/report_generation)** - 通过简单的用户查询创建专业报告。
- <img height="12" width="12" src="https://www.klaviyo.com/media/Favicon-16by16.png" alt="Klaviyo Logo" /> **[Klaviyo](https://developers.klaviyo.com/en/docs/klaviyo_mcp_server)** - 与您的 [Klaviyo](https://www.klaviyo.com/) 营销数据进行交互。
- <img height="12" width="12" src="https://platform.kluster.ai/logo-light.svg" alt="kluster.ai Logo" /> **[kluster.ai](https://docs.kluster.ai/get-started/mcp/overview/)** - kluster.ai 提供 MCP 服务器，将 AI 服务直接引入您的开发工作流程，包括幻觉检测等护栏。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/6347ea26001f0287c592ff91/649953ef7a9ffe1f3e492b5a_Knit%20Logo.svg" alt="Knit Logo" /> **[Knit MCP Server](https://developers.getknit.dev/docs/knit-mcp-server-getting-started)** - 生产就绪的远程 MCP 服务器使您能够连接 CRM、HRIS、薪资、会计、ERP、日历、费用管理和聊天类别的 10000 多种工具。
- <img height="12" width="12" src="https://knock.app/favicon/favicon-dark.svg" alt="Knock Logo" /> **[Knock MCP Server](https://github.com/knocklabs/agent-toolkit#model-context-protocol-mcp)** - 通过电子邮件、应用内、推送、短信、Slack、MS Teams 发送产品和客户消息。
- <img height="12" width="12" src="https://kumo-sdk-public.s3.us-west-2.amazonaws.com/rfm-colabs/kumo_ai_logo.jpeg" alt="Kumo Logo" /> **[Kumo](https://github.com/kumo-ai/kumo-rfm-mcp)** - MCP 服务器与 KumoRFM 交互，KumoRFM 是用于从关系数据生成预测的基础模型。
- <img height="12" width="12" src="https://www.kurrent.io/favicon.ico" alt="Kurrent Logo" /> **[KurrentDB](https://github.com/kurrent-io/mcp-server)** - 这是一个简单的 MCP 服务器，可帮助您在 KurrentDB 之上更快地探索数据和原型投影。
- <img height="12" width="12" src="https://kuzudb.com/favicon.ico" alt="Kuzu Logo" /> **[Kuzu](https://github.com/kuzudb/kuzu-mcp-server)** - 该服务器使 LLM 能够检查数据库模式并在提供的 Kuzu 图形数据库上执行查询。有关调试用例，请参阅 [blog](https://blog.kuzudb.com/post/2025-03-23-kuzu-mcp-server/)）。
- <img height="12" width="12" src="assets/043-187484914-219b362312.png" alt="KWDB Logo" /> **[KWDB](https://github.com/KWDB/kwdb-mcp-server)** - 读取、写入、查询、修改数据以及对 KWDB 数据库中的数据执行 DDL 操作。
- <img height="12" width="12" src="https://kweenkl.com/favicon.ico" alt="kweenkl Logo" /> **[kweenkl](https://github.com/antoinedelorme/kweenkl-mcp)** - 使用自然语言从 AI 助手发送推送通知。预启动演示可通过示例 Webhook 令牌获得。
- <img height="12" width="12" src="https://labelstud.io/favicon-16x16.png" alt="Label Studio Logo" /> **[Label Studio](https://github.com/HumanSignal/label-studio-mcp-server)** - 开源 data labeling platform.
- <img src="assets/044-188884511-9655f73a26.png" alt="Lambda Capture" width="12" height="12"> **[Lambda Capture](https://github.com/lambda-capture/mcp-server)** - 美联储、英格兰银行、欧洲央行的宏观经济预测和语义背景。
- <img src="https://www.lambdatest.com/resources/images/header/professional-service.svg" alt="LambdaTest MCP server" width="12" height="12"> **[LambdaTest](https://www.lambdatest.com/mcp)** - LambdaTest MCP 服务器包括 Accessibility、SmartUI、Automation 和 HyperExecute，允许您将 AI 助手与您的测试工作流程连接起来，简化设置、分析故障并生成修复程序，以加快测试速度并提高效率。
- <img height="12" width="12" src="https://langfuse.com/favicon.ico" alt="Langfuse Logo" /> **[Langfuse Prompt Management](https://github.com/langfuse/mcp-server-langfuse)** - 用于协作编辑、版本控制、评估和发布提示的开源工具。
- <img height="12" width="12" src="https://laratranslate.com/favicon.ico" alt="Lara Translate Logo" /> **[Lara Translate](https://github.com/translated/lara-mcp)** - 适用于 Lara Translate API 的 MCP 服务器，可实现强大的翻译功能，支持语言检测和上下文感知翻译。
- <img height="12" width="12" src="https://last9.io/favicon.png" alt="Last9 Logo" /> **[Last9](https://github.com/last9/last9-mcp-server)** - 将实时生产环境（日志、指标和跟踪）无缝引入本地环境，以更快地自动修复代码。
- <img height="12" width="12" src="https://www.launchdarkly.com/favicon.ico" alt="LaunchDarkly Logo" /> **[LaunchDarkly](https://github.com/launchdarkly/mcp-server)** - LaunchDarkly 是一个持续交付平台，它提供功能标记作为服务，并允许开发人员快速安全地进行迭代。
- <img height="12" width="12" src="https://www.line.me/favicon-32x32.png" alt="LINE Logo" /> **[LINE](https://github.com/line/line-bot-mcp-server)** - 集成 LINE Messaging API，将 AI Agent 连接到 LINE 官方帐户。
- <img height="12" width="12" src="https://linear.app/favicon.ico" alt="Linear Logo" /> **[Linear](https://linear.app/docs/mcp)** - 搜索、创建和更新线性问题、项目和评论。
- <img height="12" width="12" src="https://lingo.dev/favicon.ico" alt="Lingo.dev Logo" /> **[Lingo.dev](https://github.com/lingodotdev/lingo.dev/blob/main/mcp.md)** - 使用 [Lingo.dev](https://lingo.dev) 本地化引擎，让您的 AI 代理讲地球上的每种语言。
- <img height="12" width="12" src="https://ligo.ertiqah.com/favicon.avif" alt="LiGo Logo" /> **[LinkedIn MCP Runner](https://github.com/ertiqah/linkedin-mcp-runner)** - 直接从 ChatGPT 和 Claude 使用 [LiGo](https://ligo.ertiqah.com/) 编写、编辑和安排 LinkedIn 帖子。
- <img height="12" width="12" src="assets/045-175112039-5d2bdbefcb.png" alt="Linkup Logo" /> **[Linkup](https://github.com/LinkupPlatform/js-mcp-server)** - （JS版）MCP服务器，通过Linkup的高级搜索API提供网络搜索功能。该服务器使人工智能助手和开发工具能够使用自然语言查询执行智能网络搜索。
- <img height="12" width="12" src="assets/045-175112039-5d2bdbefcb.png" alt="Linkup Logo" /> **[Linkup](https://github.com/LinkupPlatform/python-mcp-server)** - （Python 版本）MCP 服务器，通过 Linkup 的高级搜索 API 提供网络搜索功能。该服务器使人工智能助手和开发工具能够使用自然语言查询执行智能网络搜索。
- <img src="assets/046-149083471-a6d0af14bf.png" alt="Lippia.io" width="12" height="12"> **[Lippia](https://github.com/Lippia-io/Lippia-MCP-Server/blob/main/getting-started.md)** - MCP 服务器使用 Lippia 框架加速测试自动化。
- <img src="https://gornschool.com/gorn.png" alt="Lisply" width="12" height="12"> **[Lisply](https://github.com/gornskew/lisply-mcp)** - 灵活的前端，用于兼容 Lisp 语言的后端。
- <img height="12" width="12" src="https://litmus.io/favicon.ico" alt="Litmus.io Logo" /> **[Litmus.io](https://github.com/litmusautomation/litmus-mcp-server)** - 用于配置 [Litmus](https://litmus.io) Edge 进行工业数据收集、边缘分析和工业 AI 的官方 MCP 服务器。
- <img height="12" width="12" src="https://liveblocks.io/favicon.ico" alt="Liveblocks Logo" /> **[Liveblocks](https://github.com/liveblocks/liveblocks-mcp-server)** - 用于人工智能和人类协作的现成功能——使用它可以更快地开发您的 [Liveblocks](https://liveblocks.io) 应用程序。
- <img height="12" width="12" src="https://logfire.pydantic.dev/favicon.ico" alt="Logfire Logo" /> **[Logfire](https://github.com/pydantic/logfire-mcp)** - 通过 Logfire 提供对 OpenTelemetry 跟踪和指标的访问。
- <img height="12" width="12" src="https://make.magicmealkits.com/favicon.ico" alt="Magic Meal Kits Logo" /> **[Magic Meal Kits](https://github.com/pureugong/mmk-mcp)** - [Magic Meal Kits](https://make.magicmealkits.com/) 释放 Make 的全部潜力
- <img height="12" width="12" src="https://www.mailgun.com/favicon.ico" alt="Mailgun Logo" /> **[Mailgun](https://github.com/mailgun/mailgun-mcp-server)** - 与 Mailgun API 交互。
- <img height="12" width="12" src="https://www.mailjet.com/favicon.ico" alt="Mailjet Logo" /> **[Mailjet](https://github.com/mailgun/mailjet-mcp-server)** - 官方 MCP 服务器允许 AI 代理与 [Sinch Mailjet](https://www.mailjet.com) 的联系人、活动、细分、统计、工作流程（等）API 进行交互。
- <img height="12" width="12" src="https://www.make.com/favicon.ico" alt="Make Logo" /> **[Make](https://github.com/integromat/make-mcp-server)** - 将您的 [Make](https://www.make.com/) 场景转变为 AI 助手的可调用工具。
- <img height="12" width="12" src="https://static-assets.mapbox.com/branding/favicon/v1/favicon.ico" alt="Mapbox Logo" /> **[Mapbox](https://github.com/mapbox/mcp-server)** - 通过 Mapbox API（例如地理编码、POI 搜索、方向、等时线等）解锁地理空间智能。
- <img height="12" width="12" src="https://www.mariadb.com/favicon.ico" alt="MariaDB Logo" /> **[MariaDB](https://github.com/mariadb/mcp)** - 用于管理和查询 MariaDB 数据库的标准接口，支持标准 SQL 操作和基于向量/嵌入的高级搜索。
- <img height="14" width="14" src="assets/047-mcp-discovery-logo-efe504516a.png" alt="mcp-discovery logo" /> **[MCP Discovery](https://github.com/rust-mcp-stack/mcp-discovery)** - 一个用 Rust 构建的轻量级 CLI 工具，用于发现 MCP 服务器功能。
- <img height="12" width="12" src="https://woocommerce.com/favicon.ico" alt="WooCommerce Logo" /> **[MCP for WooCommerce](https://github.com/iOSDevSK/mcp-for-woocommerce)** - 将您的 WooCommerce 商店连接到 AI 助手，对产品、类别、评论和 WordPress 内容具有只读访问权限。 [WordPress plugin](https://wordpress.org/plugins/mcp-for-woocommerce/)
- <img height="12" width="12" src="https://googleapis.github.io/genai-toolbox/favicons/favicon.ico" alt="MCP Toolbox for Databases Logo" /> **[MCP Toolbox for Databases](https://github.com/googleapis/genai-toolbox)** - 开源 MCP 服务器，专门提供简单、快速且安全的数据库工具。支持 AlloyDB、BigQuery、Bigtable、Cloud SQL、Dgraph、Looker、MySQL、Neo4j、Postgres、Spanner 等。
- <img height="12" width="12" src="https://www.meilisearch.com/favicon.ico" alt="Meilisearch Logo" /> **[Meilisearch](https://github.com/meilisearch/meilisearch-mcp)** - 与美丽搜索交互和查询（全文和语义搜索 API）
- <img height="12" width="12" src="assets/048-logo-ba0c5f170c.png" alt="Memalot Logo" /> **[Memalot](https://github.com/nfergu/memalot?tab=readme-ov-file#mcp-server)** - 查找 Python 程序中的内存泄漏。
- <img height="12" width="12" src="https://memgraph.com/favicon.png" alt="Memgraph Logo" /> **[Memgraph](https://github.com/memgraph/ai-toolkit/tree/main/integrations/mcp-memgraph)** - 查询 [Memgraph](https://memgraph.com/) 图数据库中的数据。
- <img height="12" width="12" src="https://www.mercadolibre.com.ar/favicon.ico" alt="MercadoLibre Logo" /> **[Mercado Libre](https://mcp.mercadolibre.com/)** - Mercado Libre 的官方 MCP 服务器。
- <img height="12" width="12" src="https://www.mercadopago.com/favicon.ico" alt="MercadoPago Logo" /> **[Mercado Pago](https://mcp.mercadopago.com/)** - Mercado Pago 的官方 MCP 服务器。
- <img height="12" width="12" src="https://metoro.io/static/images/logos/MetoroLogo.png" alt="Metoro Logo" /> **[Metoro](https://github.com/metoro-io/metoro-mcp-server)** - 查询Metoro监控的kubernetes环境并与之交互
- <img height="12" width="12" src="https://knowall.ai/favicon.ico" alt="Microsoft Business Central Logo" /> **[Microsoft Business Central](https://github.com/knowall-ai/mcp-business-central)** - 管理 Dynamics 365 Business Central 客户、联系人、销售机会、发票和供应商
- <img height="12" width="12" src="https://claritystatic.azureedge.net/images/logo.ico" alt="Microsoft Clarity Logo"/> **[Microsoft Clarity](https://github.com/microsoft/clarity-mcp-server)** - 官方 MCP 服务器可从 [Clarity](https://clarity.microsoft.com) 获取您的行为分析数据和见解
- <img height="12" width="12" src="https://conn-afd-prod-endpoint-bmc9bqahasf3grgk.b01.azurefd.net/releases/v1.0.1735/1.0.1735.4099/commondataserviceforapps/icon.png" alt="Microsoft Dataverse Logo" /> **[Microsoft Dataverse](https://go.microsoft.com/fwlink/?linkid=2320176)** - 使用 NL 讨论您的业务数据 - 发现表、运行查询、检索数据、插入或更新记录，以及执行基于业务知识和上下文的自定义提示。
- <img height="12" width="12" src="https://learn.microsoft.com/favicon.ico" alt="Microsoft Learn Logo" /> **[Microsoft Learn Docs](https://github.com/microsoftdocs/mcp)** - 提供对 Microsoft 官方文档的结构化访问的 MCP 服务器。检索准确、权威和上下文感知的技术内容，用于代码生成、问答和工作流基础。
- <img height="12" width="12" src="https://statics.teams.microsoft.com/hashedassets/favicon/prod/favicon-9f45b466.ico" alt="Microsoft Teams Logo" /> **[Microsoft Teams](https://devblogs.microsoft.com/microsoft365dev/announcing-the-updated-teams-ai-library-and-mcp-support/)** - 具有 MCP 支持的官方 Microsoft Teams AI 库，可实现高级代理编排、多代理协作以及与 Teams 消息传递和协作功能的无缝集成。
- <img height="12" width="12" src="https://milvus.io/favicon-32x32.png" /> **[Milvus](https://github.com/zilliztech/mcp-server-milvus)** - 搜索、查询 Milvus 矢量数据库中的数据并与之交互。
- <img src="assets/049-mimilabssquare-0c092e59c5.svg" alt="mimilabs" width="12" height="12"> **[mimilabs](https://www.mimilabs.ai/mcp)** - 美国医疗保健数据发现指南，涵盖 50 多个政府来源和数千个公开的美国医疗保健数据集，涉及政府资助的计划、政策、药品定价、临床试验等。
- <img height="12" width="12" src="https://cdn.mxpnl.com/marketing-site/static/favicons/favicon-32x32.png" alt="Mixpanel Logo" /> **[Mixpanel](https://docs.mixpanel.com/docs/features/mcp)** - 通过自然语言查询和分析您的产品分析数据。此 Mixpanel MCP 将 AI 助手连接到您的 Mixpanel 工作区，从而能够通过对话方式访问用户行为洞察、漏斗、保留分析和自定义报告。
- <img src="assets/050-94089762-56771f0423.jpg" alt="Mobb" width="12" height="12"> **[Mobb](https://github.com/mobb-dev/bugsy?tab=readme-ov-file#model-context-protocol-mcp-server)** - [Mobb Vibe Shield](https://vibe.mobb.ai/) MCP 服务器可识别并修复人类和人工智能编写的代码中的漏洞，确保您的应用程序保持安全，而不会减慢开发速度。
- <img height="12" width="12" src="https://console.gomomento.com/favicon.ico" /> **[Momento](https://github.com/momentohq/mcp-momento)** - Momento Cache 可让您快速提高性能、降低成本并处理任何规模的负载。
- <img height="12" width="12" src="https://www.monday.com/favicon.ico" alt="Monday.com Logo" /> **[Monday.com](https://github.com/mondaycom/mcp)** - 与 Monday.com 看板、项目、帐户和工作表进行交互。
- <img height="12" width="12" src="https://www.mongodb.com/favicon.ico" /> **[MongoDB](https://github.com/mongodb-js/mongodb-mcp-server)** - MongoDB 社区服务器和 MongoDB Atlas 均受支持。
- <img height="12" width="12" src="https://moorcheh.ai/Moorcheh-mcp.ico" alt="Moorcheh Logo" /> **[Moorcheh](https://github.com/moorcheh-ai/moorcheh-mcp)** - 提供与 Moorcheh 嵌入、矢量存储、搜索和 Gen AI Answer 服务的无缝集成。
- <img height="12" width="12" src="https://www.motherduck.com/favicon.ico" alt="MotherDuck Logo" /> **[MotherDuck](https://github.com/motherduckdb/mcp-server-motherduck)** - 使用MotherDuck和本地DuckDB查询和分析数据
- <img height="12" width="12" src="https://docs.mulesoft.com/_/img/favicon.ico" alt="Mulesoft Logo" /> **[Mulesoft](https://www.npmjs.com/package/@mulesoft/mcp-server)** - 直接在任何兼容的 IDE 中使用自然语言构建、部署和管理 MuleSoft 应用程序。
- <img height="12" width="12" src="https://www.multiplayer.app/favicon-32x32.png" alt="Multiplayer Logo" /> **[Multiplayer](https://www.multiplayer.app/docs/ai/mcp-server)** - 轻松分析您的全栈会话录音。使用 Multiplayer 记录错误，使用 LLM 分析并修复它
- <img height="12" width="12" src="assets/051-logo-light-mode-d653817591.svg" alt="Nango Logo" /> **[Nango](https://nango.dev/docs/guides/use-cases/ai-tool-calling)** - 将您的 AI 代理与 500 多个 API 集成：身份验证、自定义工具和可观察性。开源。
- <img height="12" width="12" src="assets/052-38020270-d59252d1c3.png" alt="NanoVMs Logo" /> **[NanoVMs](https://github.com/nanovms/ops-mcp)** - 轻松构建 unikernels 并将其部署到任何云。
- <img height="12" width="12" src="https://needle-ai.com/images/needle-logo-orange-2-rounded.png" alt="Needle AI Logo" /> **[Needle](https://github.com/needle-ai/needle-mcp)** - 生产就绪的 RAG 开箱即用，可从您自己的文档中搜索和检索数据。
- <img height="12" width="12" src="https://neo4j.com/favicon.ico" alt="Neo4j Logo" /> **[Neo4j](https://github.com/neo4j-contrib/mcp-neo4j/)** - Neo4j 图形数据库服务器（架构 + 读/写密码）和独立的图形数据库支持内存
- <img height="12" width="12" src="https://knowall.ai/favicon.ico" alt="Neo4j Agent Memory Logo" /> **[Neo4j Agent Memory](https://github.com/knowall-ai/mcp-neo4j-agent-memory)** - 使用 Neo4j 知识图进行 AI 代理的内存管理
- <img height="12" width="12" src="https://neo4j.com/favicon.ico" alt="Neo4j Logo" /> **[Neo4j GDS](https://github.com/neo4j-contrib/gds-agent)** - Neo4j 图形数据科学服务器具有全面的图形算法，可实现复杂的图形推理和问答。
- <img height="12" width="12" src="assets/053-183852044-2342cfcc6b.png" alt="Neon Logo" /> **[Neon](https://github.com/neondatabase/mcp-server-neon)** - 与 Neon 无服务器 Postgres 平台交互
- <img height="12" width="12" src="https://app.usenerve.com/favicon.ico" alt="Nerve Logo" /> **[Nerve](https://github.com/nerve-hq/nerve-mcp-server)** - 通过 [Nerve](https://www.usenerve.com/) 在所有 SaaS 应用程序中搜索所有公司数据并采取行动
- <img height="12" width="12" src="assets/054-370544-d20e7fa9c1.jpg" alt="NetApp Logo" /> **[NetApp](https://github.com/NetApp/mcp)** - 跨 NetApp 系统和服务查询指标、管理卷和搜索。
- <img height="12" width="12" src="https://www.netdata.cloud/favicon-32x32.png" alt="Netdata Logo" /> **[Netdata](https://github.com/netdata/netdata/blob/master/src/web/mcp/README.md)** - 使用所有可观测性数据（包括指标、日志、系统、容器、流程和网络连接）进行发现、探索、报告和根本原因分析
- <img height="12" width="12" src="https://www.netlify.com/favicon/icon.svg" alt="Netlify Logo" /> **[Netlify](https://docs.netlify.com/welcome/build-with-ai/netlify-mcp-server/)** - 使用 Netlify Web 平台创建、构建、部署和管理您的网站。
- <img height="12" width="12" src="https://www.thenile.dev/favicon.ico" alt="Nile Logo" /> **[Nile](https://github.com/niledatabase/nile-mcp-server)** - 与 Nile 通信的 MCP 服务器 - Postgres 为 B2B 应用程序重新设计。使用 LLM 管理和查询数据库、租户、用户、身份验证
- <img height="12" width="12" src="assets/055-208441832-0f364c5964.png" alt="Nodit Logo" /> **[Nodit](https://github.com/noditlabs/nodit-mcp-server)** - 官方 Nodit MCP 服务器支持访问多链 RPC 节点和区块链数据的数据 API。
- <img height="12" width="12" src="https://app.norman.finance/favicons/favicon-32x32.png" alt="Norman Logo" /> **[Norman Finance](https://github.com/norman-finance/norman-mcp-server)** - 用于通过 Norman Finance 管理会计和税务的 MCP 服务器。
- <img height="12" width="12" src="https://notifly.tech/favicon.ico" alt="Notifly Logo" /> **[Notifly](https://github.com/notifly-tech/notifly-mcp-server)** - Notifly MCP 服务器使 AI 代理能够提供实时、可信的 Notifly 文档和 SDK 代码示例，以实现无缝集成。
- <img height="12" width="12" src="assets/056-4792552-a0b0cf8967.png" alt="Notion Logo" /> **[Notion](https://github.com/makenotion/notion-mcp-server#readme)** - 该项目为 Notion API 实现了一个 MCP 服务器。
- <img height="12" width="12" src="https://www.nutrient.io/assets/images/logos/nutrient.svg" alt="Nutrient Logo" /> **[Nutrient](https://github.com/PSPDFKit/nutrient-dws-mcp-server)** - 使用自然语言创建、编辑、签名、提取文档
- <img height="12" width="12" src="https://nx.dev/favicon/favicon.svg" alt="Nx Logo" /> **[Nx](https://github.com/nrwl/nx-console/blob/master/apps/nx-mcp)** - 使 LLM 可以访问代码库的 [Nx's understanding](https://nx.dev/features/enhance-AI)，提供对代码库架构、项目关系和可运行任务的深入了解，从而使 AI 能够提出精确的代码建议。
- <img height="12" width="12" src="assets/057-82347605-6cc933e762.png" alt="OceanBase Logo" /> **[OceanBase](https://github.com/oceanbase/mcp-oceanbase)** - OceanBase数据库MCP服务器及其工具
- <img height="12" width="12" src="https://docs.octagonagents.com/logo.svg" alt="Octagon Logo" /> **[Octagon](https://github.com/OctagonAI/octagon-mcp-server)** - 利用广泛的私人和公开市场数据提供实时投资研究。
- <img height="12" width="12" src="https://octoeverywhere.com/img/logo.png" alt="OctoEverywhere Logo" /> **[OctoEverywhere](https://github.com/OctoEverywhere/mcp)** - 3D 打印 MCP 服务器，允许查询实时状态、网络摄像头快照和 3D 打印机控制。
- <img height="12" width="12" src="assets/058-logo-a0299f6fd9.svg" alt="Octopus Deploy" /> **[Octopus Deploy](https://github.com/OctopusDeploy/mcp-server)** - 用于查询、检查和管理您的 [Octopus Deploy](https://octopus.com/) 实例的官方 MCP 服务器。
- <img height="12" width="12" src="assets/059-211697972-1a074b7276.png" alt="Offorte Logo" /> **[Offorte](https://github.com/offorte/offorte-mcp-server#readme)** - Offorte Proposal Software 官方 MCP 服务器支持创建和发送商业提案。
- <img height="12" width="12" src="https://maps.olakrutrim.com/favicon.ico" alt="Ola Maps" /> **[OlaMaps](https://pypi.org/project/ola-maps-mcp-server)** - 官方 Ola 地图 MCP 服务器，提供地理编码、方向、地点详细信息等服务。
- <img height="12" width="12" src="https://www.olostep.com/favicon.ico" alt="Olostep" /> **[Olostep](https://github.com/olostep/olostep-mcp-server)** - 从网络上搜索、抓取和爬行内容。清晰的降价实时结果。
- **[OMOP MCP](https://github.com/OHNLP/omop_mcp)** - 使用法学硕士将临床术语映射到 OMOP 概念，实现医疗保健数据标准化。
- <img height="12" width="12" src="https://static.onlyoffice.com/images/favicon.ico" alt="ONLYOFFICE DocSpace" /> **[ONLYOFFICE DocSpace](https://github.com/ONLYOFFICE/docspace-mcp)** - 与 [ONLYOFFICE DocSpace](https://www.onlyoffice.com/docspace.aspx) API 交互以创建房间、管理文件和文件夹。
- <img height="12" width="12" src="https://op.gg/favicon.ico" alt="OP.GG Logo" /> **[OP.GG](https://github.com/opgginc/opgg-mcp)** - 访问《英雄联盟》、《云顶之弈》和《Valorant》等热门游戏的实时游戏数据，提供冠军分析、电子竞技赛程表、元构成和角色统计数据。
- <img height="12" width="12" src="https://open-metadata.org/favicon.ico" alt="OpenMetadata" /> **[OpenMetadata](https://open-metadata.org/mcp)** - 第一个用于元数据的企业级 MCP 服务器
- <img height="12" width="12" src="assets/060-opensearch-mark-default-fab38d91a1.svg" alt="OpenSearch Logo" /> **[OpenSearch](https://github.com/opensearch-project/opensearch-mcp-server-py)** - MCP 服务器使 AI 代理能够对 [OpenSearch](https://opensearch.org/) 中存储的数据执行搜索和分析用例。
- <img height="12" width="12" src="https://app.opslevel.com/favicon.ico" alt="OpsLevel" /> **[OpsLevel](https://github.com/opslevel/opslevel-mcp)** - [OpsLevel](https://www.opslevel.com) 的官方 MCP 服务器。
- <img height="12" width="12" src="https://optuna.org/assets/img/favicon.ico" alt="Optuna Logo" /> **[Optuna](https://github.com/optuna/optuna-mcp)** - 官方 MCP 服务器可使用 [Optuna](https://optuna.org/) 无缝编排超参数搜索和其他优化任务。
- <img height="12" width="12" src="assets/061-oracle-27c620aad8.svg" alt="Oracle Logo" /> **[Oracle](https://docs.oracle.com/en/database/oracle/sql-developer-command-line/25.2/sqcug/starting-and-managing-sqlcl-mcp-server.html#GUID-5F916B5D-8670-42BD-9F8B-D3D2424EC47E)** - 官方 [Oracle Database: SQLcl ](https://www.oracle.com/database/sqldeveloper/technologies/sqlcl/download/) MCP 服务器允许直接在 SQLcl 中通过本机 MCP 支持对任何 Oracle 数据库进行所有访问。
- <img height="12" width="12" src="https://orshot.com/brand/favicon.svg" alt="Orshot Logo" /> **[Orshot](https://github.com/rishimohan/orshot-mcp-server)** - 官方 [Orshot](https://orshot.com) MCP 服务器可从自定义设计模板动态生成图像。
- <img height="12" width="12" src="https://oxylabs.io/favicon.ico" alt="Oxylabs Logo" /> **[Oxylabs](https://github.com/oxylabs/oxylabs-mcp)** - 使用 Oxylabs Web API 抓取网站，支持动态渲染和解析以进行结构化数据提取。
- <img height="12" width="12" src="https://developer.paddle.com/favicon.svg" alt="Paddle Logo" /> **[Paddle](https://github.com/PaddleHQ/paddle-mcp-server)** - 与 Paddle API 交互。管理产品目录、计费和订阅以及报告。
- **[PaddleOCR](https://paddlepaddle.github.io/PaddleOCR/latest/en/version3.x/deployment/mcp_server.html)** - MCP 服务器为 AI 应用程序带来企业级 OCR 和文档解析功能。
- <img height="12" width="12" src="assets/062-p-greenrgb-41c445ee02.svg" alt="PagerDuty Logo" /> **[PagerDuty](https://github.com/PagerDuty/pagerduty-mcp-server)** - 与您的 PagerDuty 帐户交互，使您可以直接从支持 MCP 的客户端管理事件、服务、计划等。
- **[Pagos](https://github.com/pagos-ai/pagos-mcp)** - 与 Pagos API 交互。查询信用卡 BIN 数据以及更多信息。
- <img height="12" width="12" src="https://paiml.com/favicon.ico" alt="PAIML Logo" /> **[PAIML MCP Agent Toolkit](https://github.com/paiml/paiml-mcp-agent-toolkit)** - 专业项目脚手架工具包，具有零配置 AI 上下文生成、Rust/Deno/Python 项目模板生成以及混合神经符号代码分析。
- <img src="https://cdn.bfldr.com/7GK1OJLK/at/kq7cwt4vkw5m2x9s4gkvbf7g/android-chrome-512x512-favicon.png?auto=webp&format=png&width=12&height=12" width="12" height="12" alt="PandaDoc"> **[PandaDoc](https://developers.pandadoc.com/docs/use-pandadoc-mcp-server)** - 配置 AI 开发工具以连接到 PandaDoc 的模型上下文协议服务器并利用 AI 驱动的 PandaDoc 集成。
- <img height="12" width="12" src="https://app.paperinvest.io/favicon.svg" alt="Paper Logo" /> **[Paper](https://github.com/paperinvest/mcp-server)** - 真实的模拟交易平台，具有市场模拟、22 个经纪商模拟以及用于无风险交易实践的专业工具。第一个集成 MCP 的交易平台。
- <img height="12" width="12" src="https://parallel.ai/favicon.ico" alt="Parallel Logo" /> **[Parallel Task MCP](https://github.com/parallel-web/task-mcp)** - 启动深度研究和批量任务
- **[Patronus AI](https://github.com/patronus-ai/patronus-mcp-server)** - 测试、评估和优化 AI 代理和 RAG 应用程序
- <img height="12" width="12" src="assets/063-paubox-b6b0a55a99.png" alt="Paubox Logo" />**[Paubox](https://mcp.paubox.com)** - 官方 MCP 服务器允许 AI 代理与 Paubox Email API 进行交互。 HITRUST 认证。
- <img height="12" width="12" src="https://www.paypalobjects.com/webstatic/icon/favicon.ico" alt="PayPal Logo" /> **[PayPal](https://mcp.paypal.com)** - PayPal 的官方 MCP 服务器。
- <img height="12" width="12" src="https://www.foxit.com/favicon.ico" alt="Foxit Logo" /> **[PDFActionInspector](https://github.com/foxitsoftware/PDFActionInspector/tree/develop)** - 模型上下文协议服务器，用于从 PDF 文件中提取和分析 JavaScript 操作。提供全面的安全分析，通过AI辅助风险评估检测恶意PDF行为、隐藏脚本和潜在安全威胁。
- <img height="12" width="12" src="https://ww2-secure.pearl.com/static/pearl/pearl-logo.svg" alt="Pearl Logo" /> **[Pearl](https://github.com/Pearl-com/pearl_mcp_server)** - 官方 MCP 服务器与 Pearl API 交互。立即将您的 AI 代理与 12,000 多名认证专家联系起来。
- <img height="12" width="12" src="https://www.perplexity.ai/favicon.ico" alt="Perplexity Logo" /> **[Perplexity](https://github.com/ppl-ai/modelcontextprotocol)** - 连接到 Perplexity 的 Sonar API 的 MCP 服务器，支持对话式 AI 的实时网络范围研究。
- <img height="12" width="12" src="assets/016-mattjoyce-b0a62fe978.png" alt="Persona Sessions Logo" /> **[Persona Sessions](https://github.com/mattjoyce/mcp-persona-sessions)** - 使人工智能助理能够进行结构化、角色驱动的会话，包括面试准备、个人反思以及带有内置计时器和评估的辅导对话。
- <img height="12" width="12" src="https://www.pga.com/favicon.ico" alt="PGA Logo" /> **[PGA (Golf)](https://mcp.pga.com)** - PGA 的官方 MCP 服务器，用于处理所有与高尔夫相关的事情。寻找教练、打高尔夫球、提高球技等等。
- <img height="12" width="12" src="https://www.pgyer.com/favicon.ico" alt="PGYER Logo" /> **[PGYER](https://github.com/PGYER/pgyer-mcp-server)** - [PGYER](https://www.pgyer.com/)平台的MCP服务器，支持上传、查询应用程序等。
- <img height="12" width="12" src="assets/064-54333248-b8f87e9df4.png" /> **[Pinecone](https://github.com/pinecone-io/pinecone-mcp)** - [Pinecone](https://docs.pinecone.io/guides/operations/mcp-server)的开发人员MCP服务器帮助开发人员在其开发环境中搜索文档和管理数据。
- <img height="12" width="12" src="assets/064-54333248-b8f87e9df4.png" /> **[Pinecone Assistant](https://github.com/pinecone-io/assistant-mcp)** - 从您的 [Pinecone Assistant](https://docs.pinecone.io/guides/assistant/mcp-server) 知识库检索上下文。
- <img height="12" width="12" src="https://www.pinmeto.com/hubfs/PinMeTo-Favicon.png" alt="PinMeTo logo" /> **[PinMeTo](https://github.com/PinMeTo/pinmeto-location-mcp)** - MCP 服务器使具有授权凭据的用户能够解锁其位置数据。
- <img height="12" width="12" src="https://pipedream.com/favicon.ico" alt="Pipedream Logo" /> **[Pipedream](https://github.com/PipedreamHQ/pipedream/tree/master/modelcontextprotocol)** - 通过 8,000 多个预构建工具连接 2,500 个 API。
- <img height="12" width="12" src="https://storage.googleapis.com/plainly-static-data/plainly%20-%20logo.png" alt="PlainlyVideos Logo" /> **[Plainly Videos](https://github.com/plainly-videos/mcp-server)** - [Plainly Videos](https://plainlyvideos.com) 的官方 MCP 服务器，允许用户浏览设计和项目，以及使用各种 LLM 客户端渲染视频。
- <img height="12" width="12" src="https://playcanvas.com/static-assets/images/icons/favicon.png" alt="PlayCanvas Logo" /> **[PlayCanvas](https://github.com/playcanvas/editor-mcp-server)** - 使用 PlayCanvas 编辑器创建交互式 3D Web 应用程序。
- <img height="12" width="12" src="https://playwright.dev/img/playwright-logo.ico" alt="Playwright Logo" /> **[Playwright](https://github.com/microsoft/playwright-mcp)** — 浏览器自动化 MCP 服务器使用 Playwright 运行测试、导航页面、捕获屏幕截图、抓取内容并可靠地自动化 Web 交互。
- <img height="12" width="12" src="https://www.plugged.in/favicon.ico" alt="Plugged.in Logo" /> **[Plugged.in](https://github.com/VeriTeknik/pluggedin-mcp)** - 将多个 MCP 服务器组合成单个 MCP 的综合代理。它提供跨服务器的工具、提示、资源和模板的发现和管理，以及构建 MCP 服务器时进行调试的平台。
- <img height="12" width="12" src="https://p-link.io/favicon.ico" alt="P-Link.io Logo" /> **[P-Link.io](https://github.com/paracetamol951/P-Link-MCP)** - Solana 网络上的 HTTP 402 协议实现。为代理商发送和接收付款
- <img height="12" width="12" src="https://polymarket.com/favicon.ico" alt="Polymarket Logo" /> **[Polymarket](https://github.com/ozgureyilmaz/polymarket-mcp)** - 来自 Polymarket 的实时预测市场数据 - 搜索市场、分析价格、识别交易机会。
- <img height="12" width="12" src="https://plusai.com/622ffb3448f15ce7a33c6a2b/652d81ccc31a7d50861db0ef_plus_favicon.ico" alt="Plus AI Logo" /> **[Plus AI](https://plusai.com/features/mcp)** - 模型上下文协议 (MCP) 服务器，用于使用 [Plus AI](https://plusai.com/) 演示文稿 API 自动生成专业的 PowerPoint 和 Google Slides 演示文稿。
- <img height="12" width="12" src="assets/065-port-symbol-white-91b39213ab.svg" alt="Port Logo" /> **[Port IO](https://github.com/port-labs/port-mcp-server)** - 访问和管理您的软件目录以提高服务质量和合规性。
- **[PostHog](https://github.com/posthog/mcp)** - 通过官方 PostHog MCP 服务器与 PostHog 分析、功能标记、错误跟踪等进行交互。
- <img height="12" width="12" src="https://postidentity.com/favicon.ico" alt="PostIdentity Logo" /> **[PostIdentity](https://github.com/PostIdentity/mcp-server)** - 从任何人工智能助手生成人工智能驱动的社交媒体帖子。由 [PostIdentity](https://postidentity.com) 提供支持，管理身份、创建帖子、跟踪推荐和浏览市场模板。
- **[Postman API](https://github.com/postmanlabs/postman-api-mcp)** - 使用 [Postman API](https://www.postman.com/postman/postman-public-workspace/collection/i2uqzpp/postman-api) 管理您的 Postman 资源。
- <img height="12" width="12" src="https://powerdrill.ai/_next/static/media/powerdrill.0fa27d00.webp" alt="Powerdrill Logo" /> **[Powerdrill](https://github.com/powerdrillai/powerdrill-mcp)** - MCP 服务器提供与 Powerdrill 数据集交互的工具，从而实现智能 AI 数据分析和见解。
- <img height="12" width="12" src="https://www.pre.dev/predevlogowhitebackground.png" alt="pre.dev Logo" /> **[pre.dev Architect](https://docs.pre.dev/mcp-server)** - 通过 pre.dev 使您的编码代理保持在正轨上，将其提高 10 倍。
- <img height="12" width="12" src="https://devdocs.prestashop-project.org/images/favicon.png" alt="PrestaShop Logo" /> **[PrestaShop.com](https://docs.mcp.prestashop.com/)** - 使用官方 PrestaShop MCP 服务器，通过 AI Assistant 管理您的 PrestaShop 商店。
- <img height="12" width="12" src="https://www.prisma.io/images/favicon-32x32.png" alt="Prisma Logo" /> **[Prisma](https://www.prisma.io/docs/postgres/integrations/mcp-server)** - 创建和管理 Prisma Postgres 数据库
- <img height="12" width="12" src="https://probe.dev/favicon.ico" alt="Probe.dev Logo" /> **[Probe.dev](https://docs.probe.dev/guides/mcp-integration)** - 由 [Probe.dev](https://probe.dev) 提供支持的全面媒体分析和验证。具有 FFprobe、MediaInfo 和 Probe Report 分析功能的托管 MCP 服务器。
- <img height="12" width="12" src="assets/066-fgzpihs4mxmsjhygz6n7f2xj0-09bca02fc9.png" alt="Prode.ai Logo" /> **[ProdE](https://github.com/CuriousBox-AI/ProdE-mcp)** - 您的 24/7 生产工程师可以跨多个代码库保留上下文。
- <img height="12" width="12" src="https://programintegrity.org/wp-content/uploads/2024/07/PIA-Favicon.svg" alt="Program Integrity Alliance (PIA) Logo" /> **[Program Integrity Alliance (PIA)](https://github.com/Program-Integrity-Alliance/pia-mcp-local)** - 本地和托管 MCP 服务器提供对美国政府开放数据集的 AI 友好访问。也可在 [Docker MCP Catalog](https://hub.docker.com/mcp/explore?search=PIA) 上使用。更多详情请参见 [our website](https://programintegrity.org)。
- <img height="12" width="12" src="assets/067-prompthouse-logo-12x12-2aa085bfdf.png" alt="PromptHouse Logo" /> **[PromptHouse](https://github.com/newtype-01/prompthouse-mcp)** - 为 AI 客户端提供具有 MCP 集成的个人提示库。
- <img height="12" width="12" src="https://docs.speedscale.com/img/favicon.ico" alt="proxymock Logo" /> **[proxymock](https://docs.speedscale.com/proxymock/reference/mcp/)** - 一个 MCP 服务器，通过录制实时应用程序自动生成测试和模拟。
- <img src="https://www.pubnub.com/favicon/favicon-32x32.png" alt="PubNub" width="12" height="12"> **[PubNub](https://github.com/pubnub/pubnub-mcp-server)** - 检索使用 PubNub SDK 进行开发和调用 API 的上下文。
- <img height="12" width="12" src="https://www.pulumi.com/images/favicon.ico" alt="Pulumi Logo" /> **[Pulumi](https://github.com/pulumi/mcp-server)** - 使用 [Pulumi](https://pulumi.com) 部署和管理云基础设施。
- <img height="12" width="12" src="https://pure.md/favicon.png" alt="Pure.md Logo" /> **[Pure.md](https://github.com/puremd/puremd-mcp)** - 使用 [pure.md](https://pure.md)（内置机器人检测避免、代理旋转和无头 JS 渲染）可靠地访问 Markdown 格式的 Web 内容。
- <img height="12" width="12" src="https://put.io/images/favicon.ico" alt="Put.io Logo" /> **[Put.io](https://github.com/putdotio/putio-mcp-server)** - 与您的 Put.io 帐户交互以下载种子。
- <img height="12" width="12" src="https://qdrant.tech/img/brand-resources-logos/logomark.svg" /> **[Qdrant](https://github.com/qdrant/mcp-server-qdrant/)** - 在 Qdrant 向量搜索引擎之上实现语义记忆层
- <img src="assets/068-18053493-27329343f0.png" alt="Qonto" width="12" height="12"> **[Qonto](https://github.com/qonto/qonto-mcp-server)** - 使用 MCP 通过法学硕士访问您的 Qonto 帐户并与之交互。
- <img src="https://api.qoretechnologies.com/api/public/apps/Qorus/qorus-logo.svg" alt="Qorus" width="12" height="12"> **[Qorus](https://qoretechnologies.com/manual/qorus/current/qorus/sysarch.html#mcp_server)** - 连接到任何应用程序、系统或技术，并利用 AI 实现业务流程自动化，无需编码
- <img height="12" width="12" src="assets/069-3912814-c4bcee11b6.png" alt="QuantConnect Logo" /> **[QuantConnect](https://github.com/QuantConnect/mcp-server)** - 与您的 [QuantConnect](https://www.quantconnect.com/) 帐户进行交互，以更新项目、编写策略、运行回测并将策略部署到生产实时交易中。
- **[Quickchat AI](https://github.com/incentivai/quickchat-ai-mcp)** - 作为 MCP 启动您的会话式 [Quickchat AI](https://quickchat.ai) 代理，让 AI 应用程序实时访问其知识库和会话功能
- <img height="12" width="12" src="assets/070-165178062-3014da32d2.png" alt="Ragie Logo" /> **[Ragie](https://github.com/ragieai/ragie-mcp-server/)** - 从连接到 Google Drive、Notion、JIRA 等集成的 [Ragie](https://www.ragie.ai) (RAG) 知识库中检索上下文。
- <img height="12" width="12" src="https://www.ramp.com/favicon.ico" /> **[Ramp](https://github.com/ramp-public/ramp-mcp)** - 与 [Ramp](https://ramp.com) 的开发者 API 交互，对您的支出进行分析并利用法学硕士获得见解
- **[Raygun](https://github.com/MindscapeHQ/mcp-server-raygun)** - 与您的崩溃报告进行交互并实时使用 Raygun 帐户上的监控数据
- <img height="12" width="12" src="assets/071-cu1m0xfonul76zeaw0idkq0m-437106c8a1.png" alt="Razorpay Logo" /> **[Razorpay](https://github.com/razorpay/razorpay-mcp-server)** - Razorpay 的官方 MCP 服务器
- <img height="12" width="12" src="https://www.recraft.ai/favicons/icon.svg" alt="Recraft Logo" /> **[Recraft](https://github.com/recraft-ai/mcp-recraft-server)** - 使用 [Recraft](https://recraft.ai) 生成光栅和矢量 (SVG) 图像。您还可以编辑、升级图像、创建自己的样式以及矢量化光栅图像
- <img height="12" width="12" src="https://www.redhat.com/favicon.ico" alt="Red Hat Logo" /> **[Red Hat Insights](https://github.com/RedHatInsights/insights-mcp)** - 与 [Red Hat Insights](https://www.redhat.com/en/technologies/management/insights) 交互 - 构建映像、管理漏洞或查看有针对性的建议。
- <img height="12" width="12" src="assets/072-1529926-fcc4a9b52c.png" alt="Redis Logo" /> **[Redis](https://github.com/redis/mcp-redis/)** - Redis官方MCP Server提供了管理和搜索Redis中数据的接口。
- <img height="12" width="12" src="assets/072-1529926-fcc4a9b52c.png" alt="Redis Logo" /> **[Redis Cloud API](https://github.com/redis/mcp-redis-cloud/)** - Redis Cloud API MCP 服务器允许您使用自然语言管理 Redis Cloud 资源。
- <img src="assets/073-149024635-2570bfe06a.png" alt="Reexpress" width="12" height="12"> **[Reexpress](https://github.com/ReexpressAI/reexpress_mcp_server)** - 为您的搜索、软件和数据科学工作流程启用相似性-距离-幅度统计验证
- <img height="12" width="12" src="https://cdn.prod.website-files.com/68a872edf3df6064de547670/68b7f089c45a6083ce25acb1_reflag-favicon-32.png" alt="Reflag" /> **[Reflag](https://github.com/reflagcom/javascript/tree/main/packages/cli#model-context-protocol)** - 使用 [Reflag](https://reflag.com) 创建和管理功能标志
- <img height="12" width="12" src="https://www.reltio.com/wp-content/uploads/2024/03/cropped-cropped-Reltio_Light_Mode_Dark_Mode_Favicon-270x270.png" alt="Reltio Logo" /> **[Reltio](https://github.com/reltio-ai/reltio-mcp-server)** - 一个轻量级、基于插件的 MCP 服务器，旨在在 Reltio 环境中执行与语言模型的高级实体匹配。
- <img height="12" width="12" src="https://www.rember.com/favicon.ico" alt="Rember Logo" /> **[Rember](https://github.com/rember/rember-mcp)** - 在 [Rember](https://rember.com) 中创建间隔重复抽认卡，以记住您在聊天中学到的任何内容
- <img height="12" width="12" src="assets/074-114033652-6b6bb4ea99.png" alt="Render Logo" /> **[Render](https://render.com/docs/mcp-server)** - 官方 Render MCP 服务器：启动新服务，对数据库运行查询，并通过直接访问服务指标和日志来快速调试。
- <img height="12" width="12" src="https://reportportal.io/favicon.ico" alt="ReportPortal Logo" /> **[ReportPortal](https://github.com/reportportal/reportportal-mcp-server)** - 使用您最喜欢的法学硕士探索和分析 [ReportPortal](https://reportportal.io) 的自动化测试结果。
- <img height="12" width="12" src="http://nonica.io/Nonica-logo.ico" alt="Nonica Logo" /> **[Revit](https://github.com/NonicaTeam/AI-Connector-for-Revit)** - 实时与您的 Revit 模型连接并交互。
- <img height="12" width="12" src="https://ui.rilldata.com/favicon.png" alt="Rill Data Logo" /> **[Rill Data](https://docs.rilldata.com/explore/mcp)** - 与 Rill Data 交互以查询和分析您的数据。
- <img height="12" width="12" src="https://riza.io/favicon.ico" alt="Riza logo" /> **[Riza](https://github.com/riza-io/riza-mcp)** - [Riza](https://riza.io) 的 LLM 任意代码执行和工具使用平台
- <img height="12" width="12" src="https://cdn.foundation.roblox.com/current/RobloxStudio.ico" alt="Roblox Studio" /> **[Roblox Studio](https://github.com/Roblox/studio-rust-mcp-server)** - Roblox Studio MCP 服务器，在 Roblox Studio 中创建和操作场景、脚本
- <img src="https://hyper3d.ai/favicon.ico" alt="Rodin" width="12" height="12"> **[Rodin](https://github.com/DeemosTech/rodin-api-mcp)** - 使用 [Hyper3D Rodin](https://hyper3d.ai) 生成 3D 模型
- <img height="12" width="12" src="https://cdn.prod.website-files.com/66b7de6a233c04f4dac200a6/66bed52680d689629483c18b_faviconV2%20(2).png" alt="Root Signals Logo" /> **[Root Signals](https://github.com/root-signals/root-signals-mcp)** - 使用法学硕士作为法官进行评估，改进和质量控制您的输出
- **[Roundtable](https://github.com/askbudi/roundtable)** - 统一集成层，通过零配置自动发现和企业就绪架构桥接多个人工智能编码助手（Codex、Claude Code、Cursor、Gemini）。
- **[Routine](https://github.com/routineco/mcp-server)** - MCP服务器与[Routine](https://routine.co/)交互：日历、任务、笔记等。
- <img height="12" width="12" src="https://platform.composio.dev/favicon.ico" alt="Composio Logo"> **[Rube](https://github.com/ComposioHQ/Rube)** - Rube 是一个模型上下文协议 (MCP) 服务器，可将您的 AI 工具连接到 Gmail、Slack、GitHub 和 Notion 等 500 多个应用程序。只需将其安装在您的 AI 客户端中，使用您的应用程序进行一次身份验证，然后开始要求您的 AI 执行实际操作，例如“发送电子邮件”或“创建任务”。
- <img height="12" width="12" src="assets/075-1-4239d835f4.png" alt="SafeDep Logo" /> **[SafeDep](https://github.com/safedep/vet/blob/main/docs/mcp.md)** - SafeDep `vet-mcp` 有助于在开源包用于您的项目之前审查其安全风险（例如漏洞和恶意代码），尤其是人工智能生成的代码建议。
- <img height="12" width="12" src="https://waf-ce.chaitin.cn/favicon.ico" alt="SafeLine Logo" /> **[SafeLine](https://github.com/chaitin/SafeLine/tree/main/mcp_server)** - [SafeLine](https://safepoint.cloud/landing/safeline) 是一个自托管的 WAF（Web 应用程序防火墙），用于保护您的 Web 应用程序免受攻击和利用。
- <img height="12" width="12" src="https://scrapi.tech/favicon.ico" alt="ScrAPI Logo" /> **[ScrAPI](https://github.com/DevEnterpriseSoftware/scrapi-mcp)** - 使用 [ScrAPI](https://scrapi.tech) 进行网页抓取。提取由于机器人检测、验证码甚至地理位置限制而难以访问的网站内容。
- <img height="12" width="12" src="https://upnorthmedia.co/favicon.ico" alt="Up North Media Logo" /> **[ScreenshotMCP](https://github.com/upnorthmedia/ScreenshotMCP/)** - 模型上下文协议 MCP 服务器，用于捕获具有完整页面、元素和设备尺寸特征的网站屏幕截图。
- <img height="12" width="12" src="https://screenshotone.com/favicon.ico" alt="ScreenshotOne Logo" /> **[ScreenshotOne](https://github.com/screenshotone/mcp/)** - 使用[ScreenshotOne](https://screenshotone.com/)渲染网站截图
- <img height="12" width="12" src="assets/076-56912e614b35093426c515860f9f2234-58dfae704c.svg" alt="Search1API Logo" /> **[Search1API](https://github.com/fatwang2/search1api-mcp)** - 一个用于搜索、爬网和站点地图的 API
- <img height="12" width="12" src="https://www.searchunify.com/favicon.ico" alt="SearchUnify Logo" /> **[SearchUnify](https://github.com/searchunify/su-mcp/)** - SearchUnify MCP 服务器 (su-mcp) 可实现 SearchUnify 与 Claude Desktop 的无缝集成
- <img height="12" width="12" src="https://secureframe.com/favicon.ico" alt="Secureframe Logo" /> **[Secureframe](https://github.com/secureframe/secureframe-mcp-server)** - 从 [Secureframe](https://secureframe.com) 查询安全控制、监控合规性测试并访问 SOC 2、ISO 27001、CMMC、FedRAMP 和其他框架的审核数据。
- <img height="12" width="12" src="https://semgrep.dev/favicon.ico" alt="Semgrep Logo" /> **[Semgrep](https://github.com/semgrep/semgrep/blob/develop/cli/src/semgrep/mcp/README.md)** - 使 AI 代理能够使用 [Semgrep](https://semgrep.dev/) 保护代码。
- <img height="12" width="12" src="https://semilattice.ai/favicon.png" alt="Semilattice icon" /> **[Semilattice](https://github.com/semilattice-research/mcp)** - 通过准确的受众预测来测试内容、个性化功能以及 A/B 测试决策。
- <img height="12" width="12" src="assets/077-187640573-60f8d42d44.png" alt="Sequa Logo" /> **[Sequa.AI](https://github.com/sequa-ai/sequa-mcp)** - 停止缝合 Copilot 和 Cursor 的上下文。借助 [Sequa MCP](https://github.com/sequa-ai/sequa-mcp)，您的 AI 工具可以立即了解您的所有代码库和文档。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/6372338e5477e047032b37a5/64f85e6388a2a5c8c9525b4d_favLogo.png" alt="Shortcut Logo" /> **[Shortcut](https://github.com/useshortcut/mcp-server-shortcut)** - 从 [Shortcut](https://shortcut.com/) 访问并实施您的所有项目和任务（故事）。
- <img height="12" width="12" src="https://simplifier.io/favicon.ico" alt="Simplifier Logo" /> **[Simplifier](https://github.com/simplifier-ag/simplifier-mcp)** - 在 [Simplifier](https://simplifier.io/) 低代码平台中管理连接器、业务对象等。
- <img height="12" width="12" src="https://www.singlestore.com/favicon-32x32.png?v=277b9cbbe31e8bc416504cf3b902d430"/> **[SingleStore](https://github.com/singlestore-labs/mcp-server-singlestore)** - 与 SingleStore 数据库平台交互
- <img height="12" width="12" src="https://smartbear.com/smartbear/assets/img/favicon.png" alt="SmartBear Logo" /> **[SmartBear](https://github.com/SmartBear/smartbear-mcp)** - 提供对 SmartBear 的 API 中心、测试中心和 Insight 中心的多种功能的访问，全部通过 [dedicated tools and resources](https://developer.smartbear.com/smartbear-mcp/docs/mcp-server) 进行。
- <img src="https://smooth-operator.online/logo48.png" alt="Smooth Operator" width="12" height="12"> **[Smooth Operator](https://smooth-operator.online/agent-tools-api-docs/toolserverdocs)** - 通过 AI 视觉、鼠标、键盘、自动化树、Web 浏览器实现 Windows 自动化的工具
- <img height="12" width="12" src="https://app.snyk.io/bundle/favicon-faj49uD9.png" alt="Snyk Logo" /> **[Snyk](https://github.com/snyk/snyk-ls/blob/main/mcp_extension/README.md)** - 通过将 [Snyk](https://snyk.io/) 漏洞扫描直接嵌入到代理工作流程中来增强安全态势。
- <img height="12" width="12" src="https://www.sonarsource.com/favicon.ico" alt="SonarQube Logo" /> **[SonarQube](https://github.com/SonarSource/sonarqube-mcp-server)** - 实现与 [SonarQube](https://www.sonarsource.com/) 服务器或云的无缝集成，并允许在代理上下文中进行代码片段分析。
- <img src="https://sophtron.com/favicon.ico" alt="Sophtron" width="12" height="12"> **[Sophtron](https://github.com/sophtron/Sophtron-Integration/tree/main/modelcontextprotocol)** - 连接到您的银行、信用卡、公用事业账户，以检索 [Sophtron Bank Integration](https://sophtron.com) 的账户余额和交易。
- <img height="12" width="12" src="https://learn.microsoft.com/favicon.ico" alt="Microsoft Learn Logo" /> **[SQL Server](https://github.com/Azure-Samples/SQL-AI-samples/tree/main/MssqlMcp)** - 官方 Microsoft SQL Server MCP<sup>[1](https://devblogs.microsoft.com/azure-sql/introducing-mssql-mcp-server/)</sup>
- <img height="12" width="12" src="https://www.stackhawk.com/wp-content/uploads/2025/03/icon-512x512-2-150x150.png" alt="StackHawk Logo" /> **[StackHawk](https://github.com/stackhawk/stackhawk-mcp)** - 使用 [StackHawk](https://www.stackhawk.com/) 测试并修复代码或 vivi 编码应用程序中的安全问题。
- <img height="12" width="12" src="https://stackoverflow.com/Content/Sites/stackoverflow/Img/apple-touch-icon@2.png" alt="StackOverflow Logo" /> **[Stack Overflow](https://api.stackexchange.com/docs/mcp-server)** - 访问 Stack Overflow 值得信赖且经过验证的技术问题和解答。
- <img height="12" width="12" src="https://www.stardog.com/img/favicon.ico?_cchid=1cc28b39bd2e8a628edeed79ccd4f49c" alt="Stardog Logo" /> **[Stardog](https://github.com/stardog-union/stardog-cloud-mcp)** - 通过 [Stardog](https://www.stardog.com) 的语义 AI 平台，使用您的企业知识图谱为人类和代理提供可信的上下文答案。
- <img height="12" width="12" src="https://www.starrocks.io/favicon.ico" alt="StarRocks Logo" /> **[StarRocks](https://github.com/StarRocks/mcp-server-starrocks)** - 与[StarRocks](https://www.starrocks.io/)互动
- <img height="12" width="12" src="https://downloads.steadybit.com/logomark.svg" alt="Steadybit Logo" /> **[Steadybit](https://github.com/steadybit/mcp)** - 与[Steadybit](https://www.steadybit.com/)互动
- <img height="12" width="12" src="https://steuerboard.net/favicon.ico" alt="Steuerboard Logo" /> **[Steuerboard](https://github.com/steuerboard/steuerboard-mcp-typescript)** - 使用我们的官方 MCP 服务器与您企业中的会计数据进行交互
- <img height="12" width="12" src="assets/078-22632046-165fd33818.png" alt="Storybook Logo" /> **[Storybook](https://github.com/storybookjs/addon-mcp)** - 与 [Storybook](https://storybook.js.org/) 交互以自动化 UI 组件测试和文档记录
- <img height="12" width="12" src="assets/042-klavis-ai-b51f9599f6.png" alt="Strata Logo" /> **[Strata](https://www.klavis.ai/)** - 一台 MCP 服务器可逐步引导您的 AI 代理使用多个应用程序中的数千种工具。它消除了上下文过载并确保准确的工具选择，使代理能够轻松处理复杂的多应用程序工作流程。
- <img height="12" width="12" src="https://stripe.com/favicon.ico" alt="Stripe Logo" /> **[Stripe](https://github.com/stripe/agent-toolkit)** - 与 Stripe API 交互
- <img height="12" width="12" src="https://www.success.co/favicon.ico" alt="Success.co Logo" /> **[Success.co](https://www.success.co/docs/guides/ai-mcp-connector)** - 与您的 Success.co 帐户互动 - 增强您的 EOS® 之旅并深入了解您的团队和业务。
- <img height="12" width="12" src="assets/079-cdnsteve-73bb6fa386.png" alt="Sugar Logo" /> **[Sugar](https://github.com/cdnsteve/sugar)** - Claude Code 的自主 AI 开发平台，具有任务管理、专业代理和工作流程自动化功能。完整的 MCP 服务器将 Claude 与 Python CLI 连接起来，以实现丰富的任务上下文和自主执行。
- <img height="12" width="12" src="https://sunra.ai/favicon.ico" alt="Sunra AI Logo" /> **[Sunra AI](https://github.com/sunra-ai/sunra-clients/tree/main/mcp-server)** - 在[Sunra.ai](https://sunra.ai)上搜索并运行AI模型。发现模型，创建视频、图像和 3D 模型内容，跟踪其状态并管理生成的媒体。
- <img height="12" width="12" src="https://supabase.com/favicon/favicon.ico" alt="Supabase Logo" /> **[Supabase](https://github.com/supabase-community/supabase-mcp)** - 与 Supabase 交互：创建表、查询数据、部署边缘函数等。
- <img height="12" width="12" src="https://supadata.ai/favicon.ico" alt="Supadata Logo" /> **[Supadata](https://github.com/supadata-ai/mcp)** - [Supadata](https://supadata.ai) 的官方 MCP 服务器 - 面向创客的 YouTube、TikTok、X 和 Web 数据。
- <img height="12" width="12" src="https://d12w4pyrrczi5e.cloudfront.net/archive/50eb154ab859c63a8f1c850f9fe094e25d35e929/images/favicon.ico" alt="Tako Logo" /> **[Tako](https://github.com/TakoData/tako-mcp)** - 使用自然语言搜索 [Tako](https://trytako.com) 可视化的实时金融、体育、天气和公共数据
- <img height="12" width="12" src="https://tavily.com/favicon.ico" alt="Tavily Logo" /> **[Tavily](https://github.com/tavily-ai/tavily-mcp)** - 由 [Tavily](https://tavily.com/) 提供支持的 AI 代理搜索引擎（搜索 + 提取）
- <img height="12" width="12" src="assets/080-10522416-4e6b02ff4d.png" alt="Telnyx Logo" /> **[Telnyx](https://github.com/team-telnyx/telnyx-mcp-server)** - 用于构建人工智能驱动的通信应用程序的官方 MCP 服务器。创建语音助手、发送短信活动、管理电话号码，并将实时消息传递与企业级可靠性集成。包括远程 [streamable-http](https://api.telnyx.com/v2/mcp) 和 [sse](https://api.telnyx.com/mcp/sse) 服务器。
- <img height="12" width="12" src="assets/081-91520705-ceb290bd0c.png" alt="Tencent RTC Logo" /> **[Tencent RTC](https://github.com/Tencent-RTC/mcp)** - MCP Server 使 AI IDE 能够更有效地理解和使用 [Tencent's Real-Time Communication](https://trtc.io/) SDK 和 API，从而显着简化开发人员构建音频/视频通话应用程序的流程。
- <img height="12" width="12" src="assets/082-1615979-5fa4ca134c.png" alt="Teradata Logo" /> **[Teradata](https://github.com/Teradata/teradata-mcp-server)** - 该 MCP 服务器支持 [Teradata](https://teradata.com) 平台上的多任务数据分析工具和提示。
- <img height="12" width="12" src="assets/083-terraform-logomark-ondark-e580a5d366.svg" alt="Terraform Logo" /> **[Terraform](https://github.com/hashicorp/terraform-mcp-server)** - 与 Terraform 生态系统无缝集成，为 [Terraform](https://www.hashicorp.com/en/products/terraform) 提供支持的基础设施即代码 (IaC) 开发提供先进的自动化和交互功能
- <img height="12" width="12" src="https://textarttools.com/textarttoolslogo.png" alt="TextArtTools Logo" /> **[TextArtTools](https://github.com/humanjesse/textarttools-mcp)** - 使用 23 种 Unicode 样式转换文本，并使用 322 多种Figlet 字体创建风格化横幅。
- <img height="12" width="12" src="https://www.textin.com/favicon.png" alt="TextIn Logo" /> **[TextIn](https://github.com/intsig-textin/textin-mcp)** - [TextIn](https://www.textin.com/?from=github_mcp) API 的 MCP 服务器，是一个用于提取文本并对文档进行 OCR 的工具，它还支持将文档转换为 Markdown
- <img height="12" width="12" src="assets/084-106156665-c14baf5647.png" alt="Thena Logo" /> **[Thena](https://mcp.thena.ai)** - Thena 的 MCP 服务器，使用户和 AI 代理能够与 Thena 的服务交互并跨不同渠道（例如 Slack、电子邮件、Web、Discord 等）管理客户。
- <img height="12" width="12" src="assets/085-24291394-f19fe30db7.png" alt="ThingsBoard" /> **[ThingsBoard](https://github.com/thingsboard/thingsboard-mcp)** - ThingsBoard MCP 服务器为 LLM 和 AI 代理提供自然语言界面，以便与您的 ThingsBoard IoT 平台进行交互。
- <img height="12" width="12" src="https://www.lg.com/favicon.ico" alt="ThinQ Logo" /> **[ThinQ Connect](https://github.com/thinq-connect/thinqconnect-mcp)** - 通过 ThinQ Connect MCP 服务器与 LG ThinQ 智能家居设备和电器进行交互。
- <img height="12" width="12" src="https://thirdweb.com/favicon.ico" alt="Thirdweb Logo" /> **[Thirdweb](https://github.com/thirdweb-dev/ai/tree/main/python/thirdweb-mcp)** - 读取/写入超过 2k 条区块链，支持数据查询、合约分析/部署和交易执行，由 [Thirdweb](https://thirdweb.com/) 提供支持
- <img height="12" width="12" src="https://www.thoughtspot.com/favicon-16x16.png" alt="ThoughtSpot Logo" /> **[ThoughtSpot](https://github.com/thoughtspot/mcp-server)** - 人工智能是新的商业智能。为您团队中的每个人提供专门的数据分析师。将 [ThoughtSpot](https://thoughtspot.com) 的能力带入 Claude 或任何 MCP 主机。
- <img height="12" width="12" src="assets/086-dark-brand-ef831bf394.svg" alt="Tianji Logo" /> **[Tianji](https://github.com/msgbyte/tianji/tree/master/apps/mcp-server)** - 与天机平台交互，无论是自托管还是云平台，由 [Tianji](https://tianji.msgbyte.com/) 提供支持。
- <img height="12" width="12" src="https://www.pingcap.com/favicon.ico" alt="TiDB Logo" /> **[TiDB](https://github.com/pingcap/pytidb)** - MCP Server 与 TiDB 数据库平台交互。
- <img height="12" width="12" src="https://www.tinybird.co/favicon.ico" alt="Tinybird Logo" /> **[Tinybird](https://github.com/tinybirdco/mcp-tinybird)** - 与 Tinybird 无服务器 ClickHouse 平台交互
- <img height="12" width="12" src="https://b2729162.smushcdn.com/2729162/wp-content/uploads/2023/10/cropped-Favicon-1-192x192.png?lossy=1&strip=1&webp=1" alt="Tldv Logo" /> **[Tldv](https://gitlab.com/tldv/tldv-mcp-server)** - 通过 [tl;dv](https://tldv.io) 将您的 AI 代理连接到 Google-Meet、Zoom 和 Microsoft Teams
- <img height="12" width="12" src="https://www.todoist.com/static/favicon-32x32.png" alt="Todoist Logo" /> **[Todoist](https://github.com/doist/todoist-ai)** - 搜索、添加和更新 [Todoist](https://todoist.com) 任务、项目、部分、评论等。
- <img height="12" width="12" src="https://cdn.tokenmetrics.com/logo.svg" alt="Token Metrics Logo" /> **[Token Metrics](https://github.com/token-metrics/mcp)** - [Token Metrics](https://www.tokenmetrics.com/) 集成，用于获取实时加密货币市场数据、交易信号、价格预测和高级分析。
- <img height="12" width="12" src="assets/087-1920-6b7e7ec2-d897-4cd7-94f3-46a8301212c3-27e4b77b41.png" alt="TomTom Logo" /> **[TomTom-MCP](https://github.com/tomtom-international/tomtom-mcp)** - [TomTom](https://www.tomtom.com/) MCP 服务器通过提供对 TomTom 定位服务（包括搜索、路由、交通和静态地图数据）的无缝访问来简化地理空间开发。
- <img height="12" width="12" src="https://images.tradeit.app/trade_agent/logo.svg" alt="Trade It Logo" /> **[Trade It](https://github.com/trade-it-inc/trade-it-mcp)** - 通过 [Trade It](https://tradeit.app) 在您的经纪公司执行股票、加密货币和期权交易。支持 Robinhood、ETrade、Charles Schwab、Webull、Coinbase 和 Kraken。
- <img height="18" width="18" src="https://github.com/twelvedata/mcp/raw/develop/favicon.ico" alt="Twelvedata Logo" /> **[Twelve Data](https://github.com/twelvedata/mcp)** — 通过我们的官方 [Twelve Data](https://twelvedata.com) MCP 服务器将您的人工智能代理与实时和历史金融市场数据集成。
- <img height="12" width="12" src="https://www.twilio.com/content/dam/twilio-com/core-assets/social/favicon-16x16.png" alt="Twilio Logo" /> **[Twilio](https://github.com/twilio-labs/mcp)** - 与 [Twilio](https://www.twilio.com/en-us) API 交互以发送短信、管理电话号码、配置您的帐户等。
- <img height="12" width="12" src="https://miniprogram.tcsas-superapp.com/icon_512.png" alt="TCSAS Logo" /> **[TCSAS](https://github.com/TCMPP-Team/tcsas-devtools-mcp-server)** - 基于腾讯小程序技术框架构建，完全跟随开发，由[Tencent Cloud Super App as a Service](https://www.tencentcloud.com/products/tcsas?lang=en&pg=)提供支持。
- <img height="12" width="12" src="https://uberall.com/media/favicon.svg" alt="Uberall Logo" /> **[Uberall](https://github.com/uberall/uberall-mcp-server)** – Manage multi - 位置存在，包括列表、评论和社交发布，通过 [uberall](https://uberall.com)。
- <img height="12" width="12" src="assets/088-91906527-6cfa8cf7a1.png" alt="Unblocked Logo" /> **[Unblocked](https://docs.getunblocked.com/unblocked-mcp)** 通过 [Unblocked](https://getunblocked.com) 允许您的 AI 驱动的 IDE 访问 Slack、Confluence、Google Docs、JIRA 等上下文，帮助它们生成更快、更准确的代码。
- <img height="12" width="12" src="https://unifai.network/favicon.ico" alt="UnifAI Logo" /> **[UnifAI](https://github.com/unifai-network/unifai-mcp-server)** - 使用[UnifAI Network](https://unifai.network)动态搜索和调用工具
- <img height="12" width="12" src="assets/089-plcqevjroynyriugw90nfqbpoq-f4ec108d48.jpg" alt="Unstructured Logo" /> **[Unstructured](https://github.com/Unstructured-IO/UNS-MCP)** - 在 [Unstructured Platform](https://unstructured.io) 中设置非结构化数据处理工作流程并与之交互
- <img height="12" width="12" src="assets/090-uno-platform-symbol-rw-e1e623e04b.png" alt="Uno Platform Logo" /> **[Uno Platform](https://platform.uno/)** - 将代理和开发人员连接到 [Uno Platform's](https://aka.platform.uno/mcp) 知识库 - 文档、API 和最佳实践，允许构建跨平台 .NET 应用程序。
- <img height="12" width="12" src="https://upstash.com/icons/favicon-32x32.png" alt="Upstash Logo" /> **[Upstash](https://github.com/upstash/mcp-server)** - 在[Upstash](https://upstash.com/)上使用自然语言管理Redis数据库并运行Redis命令。
- <img height="12" width="12" src="https://raw.githubusercontent.com/e2e-test-quest/uuv/refs/heads/main/uuv.ico" alt="UUV Logo" /> **[UUV](https://github.com/e2e-test-quest/uuv/tree/main/packages/mcp-server)** - 使用 [UUV](https://e2e-test-quest.github.io/uuv/) 生成人类可读的端到端测试。
- <img height="12" width="12" src="http://vaadin.com/favicon.ico" alt="Vaadin Logo" /> **[Vaadin](https://github.com/marcushellberg/vaadin-documentation-services)** - 搜索 Vaadin 文档，获取完整文档并获取版本信息。专为人工智能代理而设计。
- <img src="https://www.vantage.sh/favicon.ico" alt="Vantage" width="12" height="12"> **[Vantage](https://github.com/vantage-sh/vantage-mcp-server)** - 与您组织的云成本支出进行交互。
- <img height="12" width="12" src="https://mcp.variflight.com/favicon.ico" alt="VariFlight Logo" /> **[VariFlight](https://github.com/variflight/variflight-mcp)** - 飞常准官方MCP服务器提供查询航班信息、天气数据、舒适度指标、最低票价以及其他民航相关数据的工具。
- <img height="12" width="12" src="https://docs.octagonagents.com/logo.svg" alt="Octagon Logo" /> **[VCAgents](https://github.com/OctagonAI/octagon-vc-agents)** - 与投资者代理人（例如 Wilson 或 Thiel）互动，不断更新市场情报。
- **[Vectorize](https://github.com/vectorize-io/vectorize-mcp-server/)** - [Vectorize](https://vectorize.io) MCP 服务器用于高级检索、私人深度研究、Anything-to-Markdown 文件提取和文本分块。
- <img height="12" width="12" src="https://static.verbwire.com/favicon-16x16.png" alt="Verbwire Logo" /> **[Verbwire](https://github.com/verbwire/verbwire-mcp-server)** - 通过 Verbwire API 部署智能合约、铸造 NFT、管理 IPFS 存储等
- <img height="12" width="12" src="http://vercel.com/favicon.ico" alt="Vercel Logo" /> **[Vercel](https://vercel.com/docs/mcp/vercel-mcp)** - 访问日志、搜索文档以及管理项目和部署。
- <img height="12" width="12" src="https://verodat.io/assets/favicon-16x16.png" alt="Verodat Logo" /> **[Verodat](https://github.com/Verodat/verodat-mcp-server)** - 与 Verodat AI Ready 数据平台交互
- <img height="12" width="12" src="https://www.veyrax.com/favicon.ico" alt="VeyraX Logo" /> **[VeyraX](https://github.com/VeyraX/veyrax-mcp)** - 单一工具即可控制所有 100 多个 API 集成和 UI 组件
- <img height="12" width="12" src="assets/091-174736222-9f014b19a0.jpg" alt="VictoriaLogs Logo" /> **[VictoriaLogs](https://github.com/VictoriaMetrics-Community/mcp-victorialogs)** - 与 [VictoriaLogs APIs](https://docs.victoriametrics.com/victorialogs/querying/#http-api) 和 [documentation](https://docs.victoriametrics.com/victorialogs/) 集成，用于处理与 VictoriaLogs 实例相关的日志和调试任务。
- <img height="12" width="12" src="assets/091-174736222-9f014b19a0.jpg" alt="VictoriaMetrics Logo" /> **[VictoriaMetrics](https://github.com/VictoriaMetrics-Community/mcp-victoriametrics)** - 与 [VictoriaMetrics APIs](https://docs.victoriametrics.com/victoriametrics/url-examples/) 和 [documentation](https://docs.victoriametrics.com/) 全面集成，用于与 VictoriaMetrics 实例相关的监控、可观察性和调试任务。
- <img height="12" width="12" src="assets/091-174736222-9f014b19a0.jpg" alt="VictoriaTraces Logo" /> **[VictoriaTraces](https://github.com/VictoriaMetrics-Community/mcp-victoriatraces)** - 与 [VictoriaTraces APIs](https://docs.victoriametrics.com/victoriatraces/querying/#http-api) 和 [documentation](https://docs.victoriametrics.com/victoriatraces/) 集成，用于处理与 VictoriaTraces 实例相关的分布式跟踪和调试任务。
- <img height="12" width="12" src="assets/092-ijlyg00locmd6zr1xlmxhbawzkm-4ceb8acdd3.png" alt="VideoDB Director" /> **[VideoDB Director](https://github.com/video-db/agent-toolkit/tree/main/modelcontextprotocol)** - 创建人工智能驱动的视频工作流程，包括自动编辑、内容审核、语音克隆、精彩片段生成和可搜索视频时刻，所有这些都可以通过简单的 API 和直观的基于聊天的界面进行访问。
- <img height="12" width="12" src="https://landing.ai/wp-content/uploads/2024/04/cropped-favicon-192x192.png" alt="LandingAI VisionAgent" /> **[VisionAgent MCP](https://github.com/landing-ai/vision-agent-mcp)** - 一个简单的 MCP 服务器，使您的法学硕士能够更好地推理图像、视频和文档。
- <img height="12" width="12" src="https://raw.githubusercontent.com/mckinsey/vizro/main/vizro-core/docs/assets/images/favicon.png" alt="Vizro Logo" /> **[Vizro](https://github.com/mckinsey/vizro/tree/main/vizro-mcp)** - 用于创建经过验证且可维护的数据图表和仪表板的工具和模板
- <img height="12" width="12" src="https://wavespeed.ai/logo.webp" alt="WaveSpeed Logo" /> **[WaveSpeed](https://github.com/WaveSpeedAI/mcp-server)** - WaveSpeed MCP 服务器为 AI 代理提供图像和视频生成功能。
- <img height="12" width="12" src="https://waystation.ai/images/logo.svg" alt="WayStation Logo" /> **[WayStation](https://github.com/waystation-ai/mcp)** - 通用 MCP 服务器可连接到流行的生产力工具，例如 Notion、Monday、AirTable 等
- <img height="12" width="12" src="https://www.webflow.com/favicon.ico" alt="Webflow Logo"> **[Webflow](https://github.com/webflow/mcp-server)** - 与 Webflow 站点、页面和集合交互
- <img height="12" width="12" src="https://webscraping.ai/favicon.ico" alt="WebScraping.AI Logo" /> **[WebScraping.AI](https://github.com/webscraping-ai/webscraping-ai-mcp-server)** - 与 **[WebScraping.AI](https://WebScraping.AI)** 交互以进行网络数据提取和抓取
- <img height="12" width="12" src="assets/093-ujty9i-jhs1-73b6c42d19.png" alt="WhatsApp Business Logo" /> **[WhatsApp Business](https://medium.com/@wassenger/introducing-whatsapp-mcp-ai-connector-3d393b52d1b0)** - WhatsApp Business MCP 连接器使 AI 代理能够发送消息、管理对话、访问模板以及与 WhatsApp Business API 集成以实现自动化客户通信。
- <img height="12" width="12" src="https://winston-app-production-public.s3.us-east-1.amazonaws.com/winston-ai-favicon-light.svg" alt="Winston.AI Logo" /> **[Winston AI](https://github.com/gowinston-ai/winston-ai-mcp-server)** - AI 检测器 MCP 服务器在检测文本和图像中 AI 的使用方面具有行业领先的准确率。 [Winston AI](https://gowinston.ai) MCP 服务器还提供强大的抄袭检查器来帮助保持完整性。
- <img height="12" width="12" src="https://woocommerce.com/wp-content/uploads/2024/12/cropped-logo-w-favicon.png" alt="WooCommerce.com Logo" /> **[WooCommerce.com](https://developer.woocommerce.com/docs/features/mcp/)** - 通过我们的 MCP 集成管理您的 WooCommerce.com 商店、产品和订单。
- <img height="12" width="12" src="https://developer.wordpress.com/wp-content/uploads/2025/03/cropped-favicon-64x64-from-figma.png" alt="WordPress.com Logo" /> **[WordPress.com](https://developer.wordpress.com/docs/mcp/)** - 将您的 AI 助手连接到 WordPress.com，让您可以直接查看网站的内容、分析和设置。
- <img height="12" width="12" src="https://www.xero.com/favicon.ico" alt="Xero Logo" /> **[Xero](https://github.com/XeroAPI/xero-mcp-server)** - 使用我们的官方 MCP 服务器与您企业中的会计数据进行交互
- <img height="12" width="12" src="https://storage.yandexcloud.net/ydb-www-prod-site-assets/favicon-202305/favicon.ico" alt="YDB Logo" /> **[YDB](https://github.com/ydb-platform/ydb-mcp)** - 查询[YDB](https://ydb.tech/)数据库
- <img height="12" width="12" src="https://fe-resource.yeelight.com/logo-black.jpeg" alt="Yeelight Logo" /> **[Yeelight MCP Server](https://github.com/Yeelight/yeelight-iot-mcp)** - 官方[Yeelight MCP Server](https://github.com/Yeelight/yeelight-iot-mcp)使用户能够使用自然语言控制和查询[Yeelight](https://en.yeelight.com/)智能设备，提供无缝、高效的人机交互体验。
- <img height="12" width="12" src="https://cdn.prod.website-files.com/632cd328ed2b485519c3f689/6334977a5d1a542102d4b9b5_favicon-32x32.png" alt="YepCode Logo" /> **[YepCode](https://github.com/yepcode/mcp-server-js)** - 在安全、可扩展的沙箱环境中运行代码，完全支持依赖项、机密、日志以及对 API 或数据库的访问。由 [YepCode](https://yepcode.io) 提供支持
- <img height="12" width="12" src="https://www.yugabyte.com/favicon-16x16.png" alt="YugabyteDB Logo" /> **[YugabyteDB](https://github.com/yugabyte/yugabytedb-mcp-server)** - MCP 服务器与您的 [YugabyteDB](https://www.yugabyte.com/) 数据库交互
- <img height="12" width="12" src="assets/094-14069894-b2214b8d3d.png" alt="Yunxin Logo" /> **[Yunxin](https://github.com/netease-im/yunxin-mcp-server)** - 连接云信IM/RTC/DATA Open-API的MCP服务器
- <img height="12" width="12" src="https://cdn.zapier.com/zapier/images/favicon.ico" alt="Zapier Logo" /> **[Zapier](https://zapier.com/mcp)** - 立即将您的 AI 代理连接到 8,000 个应用程序。
- <img height="12" width="12" src="assets/095-zenable-light-7293e67c9f.svg" alt="Zenable Logo" /> **[Zenable](https://docs.zenable.io/integrations/mcp/getting-started)** - 清理草率的 AI 代码并防止漏洞
- **[ZenML](https://github.com/zenml-io/mcp-zenml)** - 通过 [ZenML](https://www.zenml.io) MCP 服务器与 MLOps 和 LLMOps 管道交互
- **[ZettelkastenSpace](https://github.com/joshylchen/zettelkasten_space)** - 基于经过验证的 [Zettelkasten](https://www.zettelkasten.space/) 方法，并通过模型上下文协议通过 Claude Desktop 集成进行增强
- <img height="12" width="12" src="https://www.zine.ai/images/zine-logo.png" alt="Zine Logo" /> **[Zine](https://www.zine.ai)** - 人工智能所到之处，你的记忆无处不在。想想 iPhoto 的知识 - 上传和管理。与 ChatGPT 类似，但可移植 - 随身携带的上下文。
- <img height="12" width="12" src="https://zizai.work/images/logo.jpg" alt="ZIZAI Logo" /> **[ZIZAI Recruitment](https://github.com/zaiwork/mcp)** - 与由 [ZIZAI Recruitment](https://zizai.work) 提供支持的下一代智能招聘平台进行互动。

### 🌎 社区服务器

越来越多的社区开发和维护的服务器展示了 MCP 跨不同领域的各种应用。

> [!NOTE]
> 社区服务器**未经测试**，使用时应**您自担风险**。他们不隶属于 Anthropic，也不受 Anthropic 的认可。

- **[1mcpserver](https://github.com/particlefuture/1mcpserver)** - MCP 中的 MCP。在本地计算机上自动发现、配置和添加 MCP 服务器。
- **[1Panel](https://github.com/1Panel-dev/mcp-1panel)** - 提供1Panel交互的MCP服务器实现。
- **[A2A](https://github.com/GongRzhe/A2A-MCP-Server)** - MCP 服务器将模型上下文协议 (MCP) 与代理到代理 (A2A) 协议联系起来，使兼容 MCP 的 AI 助手（如 Claude）能够与 A2A 代理无缝交互。
- **[Ableton Live](https://github.com/Simon-Kansara/ableton-live-mcp-server)** - 用于控制 Ableton Live 的 MCP 服务器。
- **[Ableton Live](https://github.com/ahujasid/ableton-mcp)** (by ahujasid) - Ableton 集成允许提示启用音乐创作。
- **[ActivityPub MCP](https://github.com/cameronrye/activitypub-mcp)** - 一个全面的 MCP 服务器，使 LLM 能够通过 ActivityPub 协议探索 Fediverse 并与之交互，支持跨去中心化社交网络的参与者发现、时间线获取、实例探索和 WebFinger 解析。
- **[Actor Critic Thinking](https://github.com/aquarius-wing/actor-critic-thinking-mcp)** - 表演评价的演员批评家思维
- **[Adobe Commerce](https://github.com/rafaelstz/adobe-commerce-dev-mcp)** — MCP 与 Adob​​e Commerce GraphQL API 交互，包括订单、产品、客户等。
- **[ADR Analysis](https://github.com/tosin2013/mcp-adr-analysis-server)** - 由 AI 驱动的架构决策记录 (ADR) 分析服务器，可为软件开发项目提供架构洞察、技术堆栈检测、安全检查和 TDD 工作流程增强。
- **[Ads MCP](https://github.com/amekala/ads-mcp)** - 用于创建跨平台广告活动的远程 MCP 服务器（Google Ads Search 和 PMax、TikTok）。 OAuth 2.1 身份验证，支持长时间运行的操作的进度流。 [Website](https://www.adspirer.com/)
- **[Agent Interviews](https://github.com/thinkchainai/agentinterviews_mcp)** - 使用 [Agent Interviews](https://agentinterviews.com) 进行大规模人工智能驱动的定性研究访谈和调查。
- **[AgentBay](https://github.com/Michael98671/agentbay)** - MCP 服务器，用于为 AI 代理提供无服务器云基础设施。
- **[Agentic Framework](https://github.com/Piotr1215/mcp-agentic-framework)** - 多代理协作框架使 AI 代理能够注册、相互发现、通过 HTTP 传输交换异步消息，并通过持久消息历史记录共同处理复杂的任务。
- **[AgentMode](https://www.agentmode.app)** - 从单个 MCP 服务器连接到数十个数据库、数据仓库、Github 等。  在本地、云端或本地运行 Docker 映像。
- **[AI Agent Marketplace Index](https://github.com/AI-Agent-Hub/ai-agent-marketplace-index-mcp)** - MCP服务器用于从[AI Agent Marketplace Index](http://www.deepnlp.org/store/ai-agent)中搜索超过5000+各种类别的AI代理和工具并监控AI代理的流量。
- **[AI Endurance](https://github.com/ai-endurance/mcp)** - 面向跑步者、自行车手和铁人三项运动员的人工智能训练平台，拥有 20 多种锻炼管理、活动分析、表现预测和恢复跟踪工具。
- **[AI Tasks](https://github.com/jbrinkman/valkey-ai-tasks)** - 让人工智能通过集成的任务管理和跟踪工具来管理复杂的计划。支持 STDIO、SSE 和 Streamable HTTP 传输。
- **[ai-Bible](https://github.com/AdbC99/ai-bible)** - 可靠且可重复地搜索圣经 [ai-Bible Labs](https://ai-bible.com)
- **[Airbnb](https://github.com/openbnb-org/mcp-server-airbnb)** - 提供搜索 Airbnb 并获取房源详细信息的工具。
- **[Airflow](https://github.com/yangkyeongmo/mcp-server-apache-airflow)** - 使用官方 python 客户端连接到 [Apache Airflow](https://airflow.apache.org/) 的 MCP 服务器。
- **[Airtable](https://github.com/domdomegg/airtable-mcp-server)** - 通过架构检查对 [Airtable](https://airtable.com/) 数据库进行读写访问。
- **[Airtable](https://github.com/felores/airtable-mcp)** - Airtable 模型上下文协议服务器。
- **[Algorand](https://github.com/GoPlausible/algorand-mcp)** - 用于工具交互 (40+) 和资源可访问性 (60+) 的综合 MCP 服务器，以及与 Algorand 区块链交互的许多有用提示。
- **[Amadeus](https://github.com/donghyun-chae/mcp-amadeus)** (by donghyun-chae) - 用于访问、探索 Amadeus Flight Offers 搜索 API 并与之交互的 MCP 服务器，用于检索详细的航班选项，包括航空公司、时间、持续时间和定价数据。
- **[Amazon Ads](https://github.com/MarketplaceAdPros/amazon-ads-mcp-server)** - MCP服务器通过[MarketplaceAdPros](https://marketplaceadpros.com)/提供与亚马逊广告的交互能力
- **[AniList](https://github.com/yuna0x0/anilist-mcp)** (by yuna0x0) - 与 AniList API 交互的 MCP 服务器，允许您搜索动漫和漫画、检索用户数据并管理您的观看列表。
- **[Anki](https://github.com/scorzeth/anki-mcp-server)** - 用于与 [Anki](https://apps.ankiweb.net) 牌组和卡牌交互的 MCP 服务器。
- **[Anki](https://github.com/nietus/anki-mcp)** - MCP 服务器与 Anki 和 Ankiconnect 一起在本地运行。支持创建、更新、搜索和过滤卡牌和牌组。包括批量更新和其他高级工具。
- **[AntV Chart](https://github.com/antvis/mcp-server-chart)** - 模型上下文协议服务器，用于使用 [AntV](https://github.com/antvis) 生成 15 个以上可视化图表。
- **[Any Chat Completions](https://github.com/pyroprompts/any-chat-completions-mcp)** - 与任何 OpenAI SDK 兼容的聊天完成 API 进行交互，例如 OpenAI、Perplexity、Groq、xAI 等等。
- **[Apache Gravitino(incubating)](https://github.com/datastrato/mcp-server-gravitino)** - 允许法学硕士使用 Gravitino 探索结构化数据和非结构化数据的元数据，并执行包括标记/分类在内的数据治理任务。
- **[API Lab MCP](https://github.com/atototo/api-lab-mcp)** - 将 Claude 转变为人工智能驱动的 API 测试实验室。通过与身份验证支持、响应验证和性能指标的自然对话来测试、调试和记录 API。
- **[APIWeaver](https://github.com/GongRzhe/APIWeaver)** - 一个 MCP 服务器，可根据 Web API 配置动态创建 MCP 服务器。这使您可以轻松地将任何 REST API、GraphQL 端点或 Web 服务集成到 MCP 兼容工具中，供 Claude 等 AI 助手使用。
- **[Apollo IO MCP Server](https://github.com/AgentX-ai/apollo-io-mcp-server)** - apollo.io mcp 服务器。代理获取/丰富人员和组织的联系数据。
- **[Apple Books](https://github.com/vgnshiyer/apple-books-mcp)** - 在 Apple Books 上与您的图书馆互动、管理您的藏书、总结亮点、笔记等等。
- **[Apple Calendar](https://github.com/Omar-v2/mcp-ical)** - MCP 服务器允许您通过自然语言与 macOS 日历进行交互，包括事件创建、修改、日程列表、查找空闲时段等功能。
- **[Apple Docs](https://github.com/kimsungwhee/apple-docs-mcp)** - 功能强大的模型上下文协议 (MCP) 服务器，可通过自然语言查询无缝访问 Apple 开发人员文档。直接在 AI 支持的开发环境中搜索、探索并获取有关 Apple 框架、API、示例代码等的详细信息。
- **[Apple Script](https://github.com/peakmojo/applescript-mcp)** - MCP 服务器允许 LLM 运行 AppleScript 代码以完全控制 Mac 上的任何内容，无需设置。
- **[APT MCP](https://github.com/GdMacmillan/apt-mcp-server)** - MCP 服务器使用 ai 代理为您运行 debian 包管理器 (apt) 命令。
- **[Aranet4](https://github.com/diegobit/aranet4-mcp-server)** - MCP 服务器用于管理您的 Aranet4 CO2 传感器。获取数据并存储在本地 SQLite 中。询问有关历史数据的问题。
- **[ArangoDB](https://github.com/ravenwits/mcp-server-arangodb)** - MCP Server通过[ArangoDB](https://arangodb.com/)提供数据库交互能力。
- **[ArangoDB Graph](https://github.com/PCfVW/mcp-arangodb-async)** - 异步优先的Python架构，将官方[python-arango driver](https://github.com/arangodb/python-arango)包装为图形管理功能、内容转换实用程序（JSON、Markdown、YAML和Table）、备份/恢复功能和图形分析功能； 33 个 MCP 工具使用严格的 [Pydantic](https://github.com/pydantic/pydantic) 验证。
- **[Archestra.AI](https://github.com/archestra-ai/archestra)** - 开源企业级 MCP 网关、MCP 注册表、MCP 协调器、MCP 凭证管理、LLM 成本管理和聊天平台。
- **[Arduino](https://github.com/vishalmysore/choturobo)** - MCP 服务器使用 Claude AI 和 Arduino (ESP32) 实现人工智能驱动的机器人技术，实现现实世界的自动化以及与机器人的交互。
- **[arXiv API](https://github.com/prashalruchiranga/arxiv-mcp-server)** - 一个 MCP 服务器，支持使用自然语言与 arXiv API 进行交互。
- **[arxiv-latex-mcp](https://github.com/takashiishida/arxiv-latex-mcp)** - MCP 服务器获取并处理 arXiv LaTeX 源，以精确解释论文中的数学表达式。
- **[Arr Suite](https://github.com/shaktech786/arr-suite-mcp-server)** - 适用于 Plex 的智能 MCP 服务器和完整的 *arr 媒体自动化套件（Sonarr、Radarr、Prowlarr、Bazarr、Overseerr），具有自然语言处理功能，可实现统一媒体管理。
- **[Atlassian](https://github.com/sooperset/mcp-atlassian)** - 与 Atlassian Cloud 产品（Confluence 和 Jira）交互，包括搜索/读取 Confluence 空间/页面、访问 Jira 问题和项目元数据。
- **[Atlassian Server (by phuc-nt)](https://github.com/phuc-nt/mcp-atlassian-server)** - 一个 MCP 服务器，将 AI 代理（Cline、Claude Desktop、Cursor 等）连接到 Atlassian Jira 和 Confluence，通过模型上下文协议实现数据查询和操作。
- **[Attestable MCP](https://github.com/co-browser/attestable-mcp-server)** - 通过 Gramine 在可信执行环境 (TEE) 内运行的 MCP 服务器，展示使用 [RA-TLS](https://gramine.readthedocs.io/en/stable/attestation.html) 的远程证明。这允许 MCP 客户端在连接之前验证服务器。
- **[Audius](https://github.com/glassBead-tc/audius-mcp-atris)** - Audius + AI = Atris。在 Audius 上与粉丝互动、播放音乐、给您最喜欢的艺术家打赏等等：一切都通过 Claude 完成。
- **[AutoML](https://github.com/emircansoftware/MCP_Server_DataScience)** – 用于数据分析工作流程的 MCP 服务器，包括读取、预处理、特征工程、模型选择、可视化和超参数调整。
- **[Aviationstack](https://github.com/Pradumnasaraf/aviationstack-mcp)** – 使用 AviationStack API 获取实时航班数据的 MCP 服务器，包括航空公司航班、机场时刻表、未来航班和飞机类型。
- **[AWS](https://github.com/rishikavikondala/mcp-server-aws)** - 使用 LLM 对您的 AWS 资源执行操作。
- **[AWS Athena](https://github.com/lishenxydlgzs/aws-athena-mcp)** - 供 AWS Athena 在 Glue Catalog 上运行 SQL 查询的 MCP 服务器。
- **[AWS Cognito](https://github.com/gitCarrot/mcp-server-aws-cognito)** - 连接到 AWS Cognito 进行身份验证和用户管理的 MCP 服务器。
- **[AWS Cost Explorer](https://github.com/aarora79/aws-cost-explorer-mcp-server)** - 通过检查跨区域、服务、实例类型和基础模型 ([demo video](https://www.youtube.com/watch?v=WuVOmYLRFmI&feature=youtu.be)) 的支出，优化您使用此 MCP 服务器的 AWS 支出（包括 Amazon Bedrock 支出）。
- **[AWS Open Data](https://github.com/domdomegg/aws-open-data-mcp)** - 通过模糊匹配和详细的数据集信息搜索和探索 AWS Open Data Registry 中的数据集。
- **[AWS Resources Operations](https://github.com/baryhuang/mcp-server-aws-resources-python)** - 运行生成的 python 代码以安全地查询或修改 boto3 支持的任何 AWS 资源。
- **[AWS S3](https://github.com/aws-samples/sample-mcp-server-s3)** - 适用于 AWS S3 的示例 MCP 服务器，可灵活地从 S3 获取对象，例如 PDF 文档。
- **[AWS SES](https://github.com/aws-samples/sample-for-amazon-ses-mcp)** Sample MCP Server for Amazon SES (SESv2). See [AWS blog post](https://aws.amazon.com/blogs/messaging - and-targeting/use-ai-agents-and-the-model-context-protocol-with-amazon-ses/) 了解更多详细信息。
- **[AX-Platform](https://github.com/AX-MCP/PaxAI?tab=readme-ov-file#mcp-setup-guides)** - AI Agent协作平台。协作处理任务、共享上下文并协调工作流程。
- **[Azure ADX](https://github.com/pab1it0/adx-mcp-server)** - 查询和分析 Azure 数据资源管理器数据库。
- **[Azure DevOps](https://github.com/Vortiago/mcp-azure-devops)** - MCP 服务器提供通往 Azure DevOps 服务的桥梁，使 AI 助手能够查询和管理工作项目。
- **[Azure MCP Hub](https://github.com/Azure-Samples/mcp)** - **[Arun Sekhar](https://github.com/achandmsft)** 为 Azure 开发人员提供的所有 MCP 服务器和相关资源的精选列表
- **[Azure OpenAI DALL-E 3 MCP Server](https://github.com/jacwu/mcp-server-aoai-dalle3)** - 用于 Azure OpenAI DALL-E 3 服务的 MCP 服务器，用于从文本生成图像。
- **[Azure Wiki Search](https://github.com/coder-linping/azure-wiki-search-server)** - 一个 MCP，使 AI 能够查询 Azure Devops Wiki 上托管的 wiki。
- **[Baidu AI Search](https://github.com/baidubce/app-builder/tree/master/python/mcp_server/ai_search)** - 使用百度云的 AI 搜索进行网页搜索
- **[BambooHR MCP](https://github.com/encoreshao/bamboohr-mcp)** - 与 BambooHR API 接口的 MCP 服务器，提供对员工数据、时间跟踪和 HR 管理功能的访问。
- **[Base Free USDC Transfer](https://github.com/magnetai/mcp-free-usdc-transfer)** - 使用 Claude AI 免费在 [Base](https://base.org) 上发送 USDC！使用 [Coinbase CDP](https://docs.cdp.coinbase.com/mpc-wallet/docs/welcome) 构建。
- **[Basic Memory](https://github.com/basicmachines-co/basic-memory)** - 本地优先的知识管理系统，从 Markdown 文件构建语义图，实现与法学硕士对话的持久记忆。
- **[BGG MCP](https://github.com/kkjdaniel/bgg-mcp)** (by kkjdaniel) - MCP 可通过 AI 工具与 BoardGameGeek API 进行交互。
- **[Bible](https://github.com/trevato/bible-mcp)** - 将圣经背景添加到您的生成式人工智能应用程序中。
- **[BigQuery](https://github.com/LucasHild/mcp-server-bigquery)** (by LucasHild) - 该服务器使法学硕士能够检查数据库架构并在 BigQuery 上执行查询。
- **[BigQuery](https://github.com/ergut/mcp-bigquery-server)** (by ergut) - Google BigQuery 集成的服务器实现，支持直接 BigQuery 数据库访问和查询功能
- **[Bilibili](https://github.com/wangshunnn/bilibili-mcp-server)** - 该MCP服务器提供了获取Bilibili用户个人资料、视频元数据、搜索视频等的工具。
- **[Binance](https://github.com/ethancod1ng/binance-mcp-server)** - 通过 Binance API 集成进行加密货币交易和市场数据访问。
- **[Binance](https://github.com/AnalyticAce/binance-mcp-server)** (by dosseh shalom) - 币安模型上下文协议 (MCP) 的非官方工具和服务器实现。旨在支持开发人员构建加密货币交易人工智能代理。
- **[Bing Web Search API](https://github.com/leehanchung/bing-search-mcp)** (by hanchunglee) - Microsoft Bing Web 搜索 API 的服务器实现。
- **[BioMCP](https://github.com/genomoncology/biomcp)** (by imaurer) - 生物医学研究助理服务器，提供对 PubMed、ClinicalTrials.gov 和 MyVariant.info 的访问。
- **[bioRxiv](https://github.com/JackKuo666/bioRxiv-MCP-Server)** - 🔍 使 AI 助手能够通过简单的 MCP 界面搜索和访问 bioRxiv 论文。
- **[Bitable MCP](https://github.com/lloydzhou/bitable-mcp)** (by lloydzhou) - MCP 服务器通过模型上下文协议提供对 Lark Bitable 的访问。它允许用户使用预定义的工具与 Bitable 表进行交互。
- **[Blender](https://github.com/ahujasid/blender-mcp)** (by ahujasid) - Blender 集成允许快速启用 3D 场景创建、建模和操作。
- **[Blender MCP](https://github.com/pranav-deshmukh/blender-mcp)** - MCP 服务器使用自然语言在搅拌机上创建专业的 3D 场景。
- **[Blockbench MCP Plugin](https://github.com/jasonjgardner/blockbench-mcp-plugin)** (by jasonjgardner) - Blockbench 插件，用于将 AI 代理连接到 Blockbench 的 JavaScript API。允许在 Blockbench 中使用 AI 创建和编辑 3D 模型或像素艺术纹理。
- **[Blockchain MCP](https://github.com/tatumio/blockchain-mcp)** - 来自 **[Tatum](http://tatum.io/mcp)** 的区块链数据 MCP 服务器可立即解锁 AI 代理的区块链访问权限。该官方 Tatum MCP 服务器可在几秒钟内连接到任何 LLM。
- **[Bluesky](https://github.com/semioz/bluesky-mcp)** (by semioz) - Bluesky（一个去中心化社交网络）的 MCP 服务器。它支持与 AT 协议的自动交互，支持发帖、点赞、转发、时间线管理和个人资料操作等功能。
- **[Bluetooth MCP Server](https://github.com/Hypijump31/bluetooth-mcp-server)** - 通过自然语言命令控制蓝牙设备并管理连接，包括设备发现、配对和音频控制。
- **[BNBChain MCP](https://github.com/bnb-chain/bnbchain-mcp)** - 用于与 BSC、opBNB 和 Greenfield 区块链交互的 MCP 服务器。
- **[Braintree](https://github.com/QuentinCody/braintree-mcp-server)** - 非官方 PayPal Braintree 支付网关 MCP 服务器，供 AI 代理安全地处理支付、管理客户和处理交易。
- **[Brazilian Law](https://github.com/pdmtt/brlaw_mcp_server/)** (by pdmtt) - 使用官方资源对巴西法律进行代理驱动的研究。
- **[BreakoutRoom](https://github.com/agree-able/room-mcp)** - 代理在 p2p 房间中共同实现目标
- **[Browser MCP](https://github.com/bytedance/UI-TARS-desktop/tree/main/packages/agent-infra/mcp-servers/browser)** (by UI-TARS) - 一种快速、轻量级的 MCP 服务器，通过 Puppeteer 的结构化可访问性数据为法学硕士提供浏览器自动化功能，具有可选的视觉模式，可实现复杂的视觉理解和灵活的跨平台配置。
- **[browser-use](https://github.com/co-browser/browser-use-mcp-server)** (by co-browser) - 浏览器使用的 MCP 服务器，带有 dockerized playwright + chromium + vnc。支持 stdio 和可断点续传 http。
- **[BrowserLoop](https://github.com/mattiasw/browserloop)** - 用于使用 Playwright 截取网页屏幕截图的 MCP 服务器。支持具有可配置格式、视口大小、基于 cookie 的身份验证以及整页和特定于元素的屏幕截图的高质量捕获。
- **[Bsc-mcp](https://github.com/TermiX-official/bsc-mcp)** 第一个 MCP 服务器，作为 AI 和 BNB 链之间的桥梁，使 AI 代理能够通过与 BNB 链无缝集成来执行复杂的链上操作，包括转账、交换、启动、任何代币的安全检查等等。
- **[BugBug MCP Server](https://github.com/simplypixi/bugbug-mcp-server)** - BugBug API 的非官方 MCP 服务器。
- **[BVG MCP Server - （非官方）](https://github.com/svkaizoku/mcp-bvg)** - Berliner Verkehrsbetriebe Api 的非官方 MCP 服务器。
- **[Bybit](https://github.com/ethancod1ng/bybit-mcp-server)** - 模型上下文协议 (MCP) 服务器，用于将人工智能助手与 Bybit 加密货币交易 API 集成，从而实现自动交易、市场数据访问和账户管理。
- **[C64 Bridge](https://github.com/chrisgleissner/c64bridge)** - Commodore 64 硬件的 AI 命令桥。通过 REST API 控制 Ultimate 64 和 C64 Ultimate 设备，其中包括 BASIC 和汇编程序创建、实时内存检查、SID 音频合成以及通过本地 RAG 策划的复古计算知识。
- **[CAD-MCP](https://github.com/daobataotie/CAD-MCP#)** (by daobataotie) - 通过MCP服务器绘制CAD（线、圆、文本、注释...），支持主流CAD软件。
- **[Calculator](https://github.com/githejie/mcp-server-calculator)** - 该服务器使法学硕士能够使用计算器进行精确的数值计算。
- **[CalDAV MCP](https://github.com/dominik1001/caldav-mcp)** - CalDAV MCP 服务器将日历操作公开为 AI 助手的工具。
- **[Calendly-mcp-server](https://github.com/meAmitPatil/calendly-mcp-server)** - 开源calendly mcp服务器。
- **[Catalysis Hub](https://github.com/QuentinCody/catalysishub-mcp-server)** - 非官方 MCP 服务器，用于从催化中心数据库搜索和检索科学数据，提供对计算催化研究和表面反应数据的访问。
- **[CCTV VMS MCP](https://github.com/jyjune/mcp_vms)** - 模型上下文协议 (MCP) 服务器旨在连接到闭路电视录制程序 (VMS) 以检索录制的视频流和实时视频流。它还提供了控制 VMS 软件的工具，例如在指定时间显示特定通道的实时或播放对话框。
- **[CFBD API](https://github.com/lenwood/cfbd-mcp-server)** - [College Football Data API](https://collegefootballdata.com/) 的 MCP 服务器。
- **[ChatMCP](https://github.com/AI-QL/chat-mcp)** – 与 Linux、macOS 和 Windows 兼容的开源跨平台 GUI 桌面应用程序，通过 **[AIQL](https://github.com/AI-QL)** 实现跨动态可选择的 LLM 与 MCP 服务器的无缝交互
- **[ChatSum](https://github.com/mcpso/mcp-server-chatsum)** - 使用法学硕士查询并总结聊天消息。通过 [mcpso](https://mcp.so)
- **[Chess.com](https://github.com/pab1it0/chess-mcp)** - 通过标准化MCP接口访问Chess.com棋手数据、棋谱等公共信息，让AI助手能够搜索和分析棋谱信息。
- **[Chessagine-mcp](https://github.com/jalpp/chessagine-mcp)** - 集成了Stockfish引擎评估、位置主题分析、Lichess开放数据库和国际象棋知识库的国际象棋MCP服务器。
- **[ChessPal Chess Engine (stockfish)](https://github.com/wilson-urdaneta/chesspal-mcp-engine)** - 一个由 Stockfish 驱动的国际象棋引擎，作为 MCP 服务器公开。计算最佳移动并支持 HTTP/SSE 和 stdio 传输。
- **[Chroma](https://github.com/privetin/chroma)** - 用于语义文档搜索和元数据过滤的矢量数据库服务器，基于 Chroma 构建
- **[Chrome history](https://github.com/vincent-pli/chrome-history-mcp)** - 与 AI 谈论您的浏览器历史记录，玩得开心^_^
- **[cicada](https://github.com/wende/cicada)** - Elixir 项目的 AST 支持代码智能。提供功能搜索、调用站点跟踪、PR 归因、git 历史记录、语义搜索等 9 种工具，减少 AI 查询 token 82%。
- **[CIViC](https://github.com/QuentinCody/civic-mcp-server)** - 用于癌症变异临床解释 (CIViC) 数据库的 MCP 服务器，提供对癌症研究的临床变异解释和基因组证据的访问。
- **[Claude Thread Continuity](https://github.com/peless/claude-thread-continuity)** - 持久内存系统使 Claude Desktop 对话能够在会话之间恢复完整的上下文。维护对话历史记录、项目状态和用户首选项，以实现无缝的多会话工作流程。
- **[claude-faf-mcp](https://github.com/Wolfe-Jam/claude-faf-mcp)** - .faf 格式的 MCP 服务器。具有项目上下文管理的上下文评分引擎。
- **[ClaudePost](https://github.com/ZilongXue/claude-post)** - ClaudePost 为 Gmail 提供无缝电子邮件管理，提供电子邮件搜索、阅读和发送等安全功能。
- **[CLDGeminiPDF Analyzer](https://github.com/tfll37/CLDGeminiPDF-Analyzer)** - MCP 服务器工具可以通过 API 将大型 PDF 文件共享给 Google LLM，以便对 Claude Desktop 进行进一步/附加分析和响应检索。
- **[ClearML MCP](https://github.com/prassanna-ravishankar/clearml-mcp)** - 在 AI 对话中直接从 [ClearML](https://clear.ml) 获取全面的 ML 实验背景和分析。
- **[ClickUp](https://github.com/TaazKareem/clickup-mcp-server)** - 用于 ClickUp 任务管理的 MCP 服务器，支持任务创建、更新、批量操作和 Markdown 描述。
- **[Cloudinary](https://github.com/felores/cloudinary-mcp-server)** - Cloudinary 模型上下文协议服务器将媒体上传到 Cloudinary 并获取媒体链接和详细信息。
- **[CockroachDB](https://github.com/amineelkouhen/mcp-cockroachdb)** - MCP 服务器使 AI 代理和 LLM 能够使用自然语言管理、监控和查询 **[CockroachDB](https://www.cockroachlabs.com/)**。
- **[CockroachDB MCP Server](https://github.com/viragtripathi/cockroachdb-mcp-server)** – Full - 使用 FastAPI 和 CockroachDB 构建的特色 MCP 实现。支持模式引导、JSONB 存储、LLM 就绪 CLI 和可选的 `/debug` 端点。
- **[Code Screenshot Generator](https://github.com/MoussaabBadla/code-screenshot-mcp)** - 直接从 Claude 生成带有专业主题的漂亮的语法突出显示的代码屏幕截图。支持文件读取、行选择、git diff 可视化和批处理。
- **[code-assistant](https://github.com/stippi/code-assistant)** - 编码助理 MCP 服务器，允许探索代码库并对代码进行更改。只能与受信任的存储库一起使用（不足以防止提示注入）。
- **[code-context-provider-mcp](https://github.com/AB498/code-context-provider-mcp)** - MCP 服务器，为 AI 助手提供代码上下文和分析。使用 WebAssembly Tree-sitter 解析器提取目录结构和代码符号，无需本机依赖项。
- **[code-executor](https://github.com/bazinga012/mcp_code_executor)** - 允许 LLM 在指定 Conda 环境中执行 Python 代码的 MCP 服务器。
- **[code-sandbox-mcp](https://github.com/Automata-Labs-team/code-sandbox-mcp)** - MCP 服务器用于创建安全代码沙箱环境，以便在 Docker 容器中执行代码。
- **[cognee-mcp](https://github.com/topoteretes/cognee/tree/main/cognee-mcp)** - 具有可定制摄取、数据处理和搜索功能的 GraphRAG 内存服务器
- **[coin_api_mcp](https://github.com/longmans/coin_api_mcp)** - 提供对 [coinmarketcap](https://coinmarketcap.com/) 加密货币数据的访问。
- **[CoinMarketCap](https://github.com/shinzo-labs/coinmarketcap-mcp)** - 实现完整的 [CoinMarketCap](https://coinmarketcap.com/) API，用于访问加密货币市场数据、交易信息和其他区块链相关指标。
- **[commands](https://github.com/g0t4/mcp-server-commands)** - 运行命令和脚本。就像在终端中一样。
- **[Companies House MCP](https://github.com/stefanoamorelli/companies-house-mcp)** (by Stefano Amorelli) - MCP 服务器与 UK Companies House API 连接。
- **[computer-control-mcp](https://github.com/AB498/computer-control-mcp)** - MCP 服务器使用 PyAutoGUI、RapidOCR、ONNXRuntime 提供计算机控制功能，如鼠标、键盘、OCR 等，无需外部依赖。
- **[Computer-Use - 远程 MacOS 使用](https://github.com/baryhuang/mcp-remote-macos-use)** - OpenAI Operator 的开箱即用的开源替代方案，提供完整的桌面体验，并针对使用远程 macOS 计算机作为自主 AI 代理进行了优化。
- **[computer-use-mcp](https://github.com/domdomegg/computer-use-mcp)** - 通过屏幕捕获、鼠标和键盘功能控制您的计算机，以实现自动桌面交互和任务执行。
- **[Congress.gov API](https://github.com/AshwinSundar/congress_gov_mcp)** - 一个 MCP 服务器，用于与来自 Congress.gov API 的实时数据进行交互，该 API 是美国国会的官方 API。
- **[Console Automation](https://github.com/ooples/mcp-console-automation)** - 生产就绪的 MCP 服务器，用于 AI 驱动的控制台自动化和监控。 40 个用于会话管理、SSH、测试、监控和后台作业的工具。就像终端应用程序的 Playwright 一样。
- **[consul-mcp](https://github.com/kocierik/consul-mcp-server)** - 用于服务管理、健康检查和键值存储的 consul MCP 服务器
- **[consult7](https://github.com/szeider/consult7)** - 通过 OpenRouter、OpenAI 或 Google AI 使用高上下文模型分析大型代码库和文档集合——非常有用，例如使用 Claude Code
- **[Contentful-mcp](https://github.com/ivo-toby/contentful-mcp)** - 从此 MCP 服务器读取、更新、删除、发布您的 [Contentful](https://contentful.com) 空间中的内容。
- **[Context Crystallizer](https://github.com/hubertciebiada/context-crystallizer)** - AI 上下文工程工具，通过系统分析和优化，将大型存储库转化为具体的、AI 可使用的知识。
- **[Context Processor](https://github.com/mschultheiss83/context-processor)** - 具有可配置预处理策略（澄清、分析、搜索、获取）的智能上下文管理，用于增强内容清晰度、可搜索性和元数据提取。
- **[context-portal](https://github.com/GreatScottyMac/context-portal)** - Context Portal (ConPort) 是一个记忆库数据库系统，可以有效地构建特定于项目的知识图，捕获决策、进度和架构等实体及其关系。它作为检索增强生成（RAG）的强大后端，使人工智能助手能够访问精确的、最新的项目信息。
- **[cplusplus-mcp](https://github.com/kandrwmrtn/cplusplus_mcp)** - 使用 libclang 进行语义 C++ 代码分析。使 Claude 能够通过 AST 解析而不是文本搜索来理解 C++ 代码库 - 查找类、导航继承、跟踪函数调用和探索代码关系。
- **[CRASH](https://github.com/nikkoxgonzales/crash-mcp)** - MCP 服务器用于结构化、迭代推理和思考，具有灵活的验证、置信度跟踪、修订机制和分支支持。
- **[CreateveAI Nexus](https://github.com/spgoodman/createveai-nexus-server)** - AI 代理和企业系统之间的开源桥梁，具有简单的自定义 API 插件功能（包括与 ComfyUI 节点的紧密兼容性），支持 Copilot Studio 的 MCP 代理集成，支持安全环境中的 Azure 部署（机密存储在 Azure Key Vault 中），以及直接的本地部署。
- **[Creatify](https://github.com/TSavo/creatify-mcp)** - MCP 服务器公开了用于 AI 视频生成的 Creatify AI API 功能，包括头像视频、URL 到视频转换、文本到语音和 AI 驱动的编辑工具。
- **[Cronlytic](https://github.com/Cronlytic/cronlytic-mcp-server)** - 通过 [Cronlytic](https://cronlytic.com) MCP 服务器为无服务器 cron 作业创建 CRUD 操作
- **[crypto-feargreed-mcp](https://github.com/kukapay/crypto-feargreed-mcp)**  - 提供实时和历史加密货币恐惧和贪婪指数数据。
- **[crypto-indicators-mcp](https://github.com/kukapay/crypto-indicators-mcp)**  - 提供一系列加密货币技术分析指标和策略的MCP服务器。
- **[crypto-sentiment-mcp](https://github.com/kukapay/crypto-sentiment-mcp)**  - 向 AI 代理提供加密货币情绪分析的 MCP 服务器。
- **[cryptopanic-mcp-server](https://github.com/kukapay/cryptopanic-mcp-server)** - 由 CryptoPanic 提供支持，向 AI 代理提供最新的加密货币新闻。
- **[CSV Editor](https://github.com/santoshray02/csv-editor)** - 全面的 CSV 处理，具有 40 多个数据操作、分析和验证操作。具有自动保存、撤消/重做功能，并可处理 GB+ 文件。使用 FastMCP 和 Pandas 构建。
- **[Current Time UTC MCP Server](https://github.com/jairampatel/currenttimeutc-mcp)** - 轻量级 MCP 服务器，实时提供准确的 UTC 时间和时区转换。
- **[Cursor MCP Installer](https://github.com/matthewdcage/cursor-mcp-installer)** - 一种在 Cursor IDE 中轻松安装和配置其他 MCP 服务器的工具，支持 npm 包、本地目录和 Git 存储库。
- **[CV Forge](https://github.com/thechandanbhagat/cv-forge)** - 智能 MCP（模型上下文协议）服务器，可分析职位发布并制作完美匹配的简历（由 [Chandan Bhagat](https://me.chandanbhagat.com.np) 提供）。
- **[CVE Intelligence Server](https://github.com/gnlds/mcp-cve-intelligence-server-lite)** – Provides vulnerability intelligence via multi - 通过 MCP 获取 CVE 数据、基本漏洞发现和 EPSS 风险评分。对于安全研究、自动化和代理工作流程很有用。
- **[D365FO](https://github.com/mafzaal/d365fo-client)** - 适用于 Microsoft Dynamics 365 Finance & Operations (D365 F&O) 的综合 MCP 服务器，可轻松访问 OData 端点、元数据操作、标签管理和 AI 助手集成。
- **[Dagster](https://github.com/dagster-io/dagster/tree/master/python_modules/libraries/dagster-dg-cli)** - 使用 [Dagster](https://dagster.io/) 轻松构建数据管道的 MCP 服务器。
- **[Dappier](https://github.com/DappierAI/dappier-mcp)** - 将法学硕士连接到来自可信来源的实时、经过权限许可的专有数据。访问实时网络搜索、新闻、体育、金融数据、加密货币和优质出版商内容的专用模型。在 [marketplace.dappier.com](https://marketplace.dappier.com/marketplace) 探索数据模型。
- **[Data Exploration](https://github.com/reading-plus-ai/mcp-server-data-exploration)** - MCP 服务器用于对基于 .csv 的数据集进行自主数据探索，以最少的努力提供智能见解。注意：会在您的机器上执行任意Python代码，请谨慎使用！
- **[Data4library](https://github.com/isnow890/data4library-mcp)** (by isnow890) - 韩国图书馆信息 Naru API 的 MCP 服务器，提供对韩国各地公共图书馆数据、图书搜索、借阅状态、阅读统计和基于 GPS 的附近图书馆发现的全面访问。
- **[Databricks](https://github.com/JordiNeil/mcp-databricks-server)** - 允许法学硕士运行 SQL 查询、列出和获取 Databricks 帐户中作业执行的详细信息。
- **[Databricks Genie](https://github.com/yashshingvi/databricks-genie-MCP)** - 连接到 Databricks Genie 的服务器，允许法学硕士提出自然语言问题、运行 SQL 查询以及与 Databricks 会话代理交互。
- **[Databricks Smart SQL](https://github.com/RafaelCartenet/mcp-databricks-server)** - 利用 Databricks Unity Catalog 元数据，执行智能高效的 SQL 查询来解决临时查询并探索数据。
- **[DataCite](https://github.com/QuentinCody/datacite-mcp-server)** - DataCite 的非官方 MCP 服务器，通过 DataCite 的 REST API 和 GraphQL 接口提供对研究数据和出版物元数据的访问，以进行学术研究发现。
- **[Datadog](https://github.com/GeLi2001/datadog-mcp-server)** - Datadog MCP 服务器用于基于官方 datadog api 构建的应用程序跟踪、监控、仪表板、事件查询。
- **[Dataset Viewer](https://github.com/privetin/dataset-viewer)** - 使用搜索、过滤、统计和数据导出等功能浏览和分析 Hugging Face 数据集
- **[Dataverse DevTools MCP Server](https://github.com/vignaesh01/DataverseDevToolsMcpServer)** - MCP 服务器提供即用型 Dataverse/Dynamics 365 工具，用于用户和安全管理、数据操作、Web API 执行、元数据探索和故障排除。
- **[DataWorks](https://github.com/aliyun/alibabacloud-dataworks-mcp-server)** - 模型上下文协议 (MCP) 服务器，为 AI 提供工具，允许其通过标准化接口与 [DataWorks](https://www.alibabacloud.com/help/en/dataworks/) Open API 进行交互。该实现基于阿里云开放API，使AI代理能够无缝地执行云资源操作。
- **[DaVinci Resolve](https://github.com/samuelgursky/davinci-resolve-mcp)** - DaVinci Resolve 的 MCP 服务器集成为视频编辑、颜色分级、媒体管理和项目控制提供了强大的工具。
- **[DBHub](https://github.com/bytebase/dbhub/)** - 连接到 MySQL、MariaDB、PostgreSQL 和 SQL Server 的通用数据库 MCP 服务器。
- **[Deebo](https://github.com/snagasuri/deebo-prototype)** – 代理调试 MCP 服务器，帮助 AI 编码代理通过隔离的多代理假设测试委托和修复硬错误。
- **[Deep Research](https://github.com/reading-plus-ai/mcp-server-deep-research)** - 轻量级 MCP 服务器提供 Grok/OpenAI/Gemini/Perplexity 风格的自动化深度研究探索和结构化报告。
- **[DeepSeek MCP Server](https://github.com/DMontgomery40/deepseek-mcp-server)** - 除了 [other useful API endpoints](https://github.com/DMontgomery40/deepseek-mcp-server?tab=readme-ov-file#features) 之外，模型上下文协议服务器还集成了 DeepSeek 的高级语言模型
- **[deepseek-thinker-mcp](https://github.com/ruixingshi/deepseek-thinker-mcp)** - MCP（模型上下文协议）提供商 Deepseek 向支持 MCP 的 AI 客户端（例如 Claude Desktop）提供推理内容。支持从 Deepseek API 服务或本地 Ollama 服务器访问 Deepseek 的思维过程。
- **[Deepseek_R1](https://github.com/66julienmartin/MCP-server-Deepseek_R1)** - 连接 Claude Desktop 和 DeepSeek 语言模型 (R1/V3) 的模型上下文协议 (MCP) 服务器实现
- **[DeFi Rates](https://github.com/qingfeng/defi-rates-mcp)** - 查询超过 13 种协议（Aave、Morpho、Compound、Venus、Solend、Drift、Jupiter 等）的实时 DeFi 借贷利率。比较以太坊、Arbitrum、Base、BSC、Solana 和 HyperEVM 的费率、搜索最佳机会并计算循环策略。
- **[Defuddle Fetch](https://github.com/domdomegg/defuddle-fetch-mcp-server)** - 使用 Defuddle 增强提取功能来获取 Web 内容，将页面转换为干净的 Markdown，其结果比标准 HTML 到 Markdown 转换器更好。
- **[deploy-mcp](https://github.com/alexpota/deploy-mcp)** - 适用于 AI 助手的通用部署跟踪器，具有实时状态徽章和部署监控功能。
- **[Depyler](https://github.com/paiml/depyler/blob/main/docs/mcp-integration.md)** - 节能的 Python-to-Rust 转译器具有渐进式验证功能，使 AI 助手能够将 Python 代码转换为安全、高性能的 Rust，同时减少 75-85% 的能耗。
- **[Descope](https://github.com/descope-sample-apps/descope-mcp-server)** - 与 [Descope](https://descope.com) 集成的 MCP 服务器，用于搜索审核日志、管理用户等。
- **[DesktopCommander](https://github.com/wonderwhy-er/DesktopCommanderMCP)** - 让 AI 编辑和管理计算机上的文件、运行终端命令并通过 SSH 连接到远程服务器 - 所有这些均由最流行的本地 MCP 服务器之一提供支持。
- **[Devcontainer](https://github.com/AI-QL/mcp-devcontainers)** - 用于 devcontainer 的 MCP 服务器，用于直接从 devcontainer 配置文件生成和配置开发容器。
- **[DevDb](https://github.com/damms005/devdb-vscode?tab=readme-ov-file#mcp-configuration)** - 直接在 IDE 内部运行的 MCP 服务器，用于连接到 MySQL、Postgres、SQLite 和 MSSQL 数据库。
- **[DevOps AI Toolkit](https://github.com/vfarcic/dot-ai)** - 人工智能驱动的开发生产力平台，通过智能自动化和人工智能驱动的协助增强软件开发工作流程。
- **[DevOps-MCP](https://github.com/wangkanai/devops-mcp)** - 动态 Azure DevOps MCP 服务器，具有基于目录的身份验证切换，支持工作项、存储库、构建、管道以及使用本地配置文件的多项目管理。
- **[DGIdb](https://github.com/QuentinCody/dgidb-mcp-server)** - 用于药物基因相互作用数据库 (DGIdb) 的 MCP 服务器，提供对药物基因相互作用数据、可药物基因组信息和药物基因组学研究的访问。
- **[Dicom](https://github.com/ChristianHinge/dicom-mcp)** - 用于查询和检索医学图像以及解析和读取 dicom 封装文档（pdf 等）的 MCP 服务器。
- **[Dify](https://github.com/YanxingLiu/dify-mcp-server)** - 用于 dify 工作流程的 MCP 服务器的简单实现。
- **[Discogs](https://github.com/cswkim/discogs-mcp-server)** - 连接到 Discogs API 以便与您的音乐收藏进行交互的 MCP 服务器。
- **[Discord](https://github.com/v-3/discordmcp)** - 一个 MCP 服务器，用于通过机器人连接到 Discord 公会并在通道中读写消息
- **[Discord](https://github.com/SaseQ/discord-mcp)** - MCP 服务器，通过机器人连接到 Discord，并提供与 Discord 的全面集成。
- **[Discord](https://github.com/Klavis-AI/klavis/tree/main/mcp_servers/discord)** - 用于 Klavis AI 的 Discord API 集成
- **[Discourse](https://github.com/AshDevFr/discourse-mcp-server)** - 用于搜索 Discourse 论坛上的 Discourse 帖子的 MCP 服务器。
- **[Dispatch Agent](https://github.com/abhinav-mangla/dispatch-agent)** - 智能 MCP 服务器，通过 ReAct 子代理提供专门的文件系统操作。
- **[DocBase](https://help.docbase.io/posts/3925317)** - 用于 DocBase API 集成的官方 MCP 服务器，支持后期管理、用户协作、组管理等。
- **[Docker](https://github.com/ckreiling/mcp-server-docker)** - 与 Docker 集成以管理容器、映像、卷和网络。
- **[Docker](https://github.com/0xshariq/docker-mcp-server)** - Docker MCP Server 通过 CLI 和 MCP 工作流程提供高级、统一的 Docker 管理，支持容器、映像、卷、网络和编排。
- **[Docs](https://github.com/da1z/docsmcp)** - 启用 AI 代理的文档访问，支持 llms.txt 和其他远程或本地文件。
- **[documcp](https://github.com/tosin2013/documcp)** - 用于智能文档处理和管理的MCP服务器，支持多种格式和文档操作。
- **[Docy](https://github.com/oborchers/mcp-server-docy)** - Docy 让您的 AI 在需要时直接访问其所需的技术文档。不再有过时的信息、损坏的链接或速率限制 - 只需准确、实时的文档访问即可获得更精确的编码帮助。
- **[Dodo Payments](https://github.com/dodopayments/dodopayments-node/tree/main/packages/mcp-server)** - 使 AI 代理能够通过 [Dodo Payments](https://dodopayments.com) API 的轻量级、无服务器兼容接口安全地执行支付操作。
- **[Domain Tools](https://github.com/deshabhishek007/domain-tools-mcp-server)** - 用于全面域分析的模型上下文协议 (MCP) 服务器：WHOIS、DNS 记录和 DNS 运行状况检查。
- **[Downdetector](https://github.com/domdomegg/downdetector-mcp)** - 通过 DownDetector 检查服务状态和中断信息，实时监控各个平台和区域的服务可用性。
- **[DPLP](https://github.com/szeider/mcp-dblp)**  - 搜索 [DBLP](https://dblp.org) 计算机科学参考书目数据库。
- **[Druid MCP Server](https://github.com/iunera/druid-mcp-server)** - [iunera](https://www.iunera.com) 的 Apache Druid 的 STDIO/SEE MCP 服务器提供了广泛的工具、资源和提示来管理和分析 Druid 集群。
- **[Drupal](https://github.com/Omedia/mcp-server-drupal)** - 使用 STDIO 传输层与 [Drupal](https://www.drupal.org/project/mcp) 交互的服务器。
- **[dune-analytics-mcp](https://github.com/kukapay/dune-analytics-mcp)** - 将 Dune Analytics 数据桥接到 AI 代理的 mcp 服务器。
- **[DynamoDB-Toolbox](https://www.dynamodbtoolbox.com/docs/databases/actions/mcp-toolkit)** - 利用您的模式和访问模式使用自然语言与 [DynamoDB](https://aws.amazon.com/dynamodb) 数据库进行交互。
- **[eBook-mcp](https://github.com/onebirdrocks/ebook-mcp)** - 一个轻量级的 MCP 服务器，允许法学硕士阅读您的个人 PDF 和 EPUB 电子书并与之交互。非常适合构建人工智能阅读助手或基于聊天的电子书界面。
- **[ECharts MCP Server](https://github.com/hustcc/mcp-echarts)** - 使用 ECharts 和 AI MCP 动态生成可视化图表，用于图表生成和数据分析。
- **[EDA MCP Server](https://github.com/NellyW8/mcp-EDA)** - 用于电子设计自动化工具的综合模型上下文协议服务器，使 AI 助手能够使用 Yosys 综合 Verilog、使用 Icarus Verilog 进行设计仿真、使用 OpenLane 运行完整的 ASIC 流程以及使用 GTKWave 和 KLayout 查看结果。
- **[EdgeOne Pages MCP](https://github.com/TencentEdgeOne/edgeone-pages-mcp)** - 一种 MCP 服务，用于将 HTML 内容部署到 EdgeOne Pages 并获取可公开访问的 URL。
- **[Edwin](https://github.com/edwin-finance/edwin/tree/main/examples/mcp-server)** - 用于 edwin SDK 的 MCP 服务器 - 使 AI 代理能够与 EVM、Solana 和其他区块链上的 DeFi 协议进行交互。
- **[eechat](https://github.com/Lucassssss/eechat)** - 一款开源、跨平台桌面应用程序，可跨 Linux、macOS 和 Windows 与 MCP 服务器无缝连接。
- **[Elasticsearch](https://github.com/cr7258/elasticsearch-mcp-server)** - 提供 Elasticsearch 交互的 MCP 服务器实现。
- **[ElevenLabs](https://github.com/mamertofabian/elevenlabs-mcp-server)** - 与 ElevenLabs 文本转语音 API 集成的服务器，能够生成具有多种声音的完整画外音。
- **[Email](https://github.com/Shy2593666979/mcp-server-email)** - 该服务器使用户能够通过各种电子邮件提供商发送电子邮件，包括Gmail、Outlook、Yahoo、Sina、Sohu、126、163和QQ邮箱。它还支持从指定目录附加文件，从而可以轻松地随电子邮件内容一起上传附件。
- **[Email SMTP](https://github.com/egyptianego17/email-mcp-server)** - 一个简单的 MCP 服务器，可让您的 AI 代理通过 SMTP 发送电子邮件并附加文件。
- **[Enhance Prompt](https://github.com/FelixFoster/mcp-enhance-prompt)** - 用于增强您提示的 MCP 服务。
- **[Entrez](https://github.com/QuentinCody/entrez-mcp-server)** - NCBI Entrez 数据库的非官方 MCP 服务器，通过 NCBI 的电子实用程序 API 提供对 PubMed 文章、基因信息、蛋白质数据和其他生物医学研究资源的访问。
- **[Ergo Blockchain MCP](https://github.com/marctheshark3/ergo-mcp)** - 集成 Ergo 区块链节点和 Explorer API 的 MCP 服务器，用于检查地址余额、分析交易、查看交易历史记录、执行地址取证分析、搜索代币以及监控网络状态。
- **[ESP MCP Server](https://github.com/horw/esp-mcp)** - 集成 ESP IDF 命令的 MCP 服务器，例如使用 LLM 为 ESP 微控制器构建和刷新代码。
- **[Eunomia](https://github.com/whataboutyou-ai/eunomia-MCP-server)** - 连接 Eunomia 仪器与 MCP 服务器的 Eunomia 框架扩展
- **[Everything Search](https://github.com/mamertofabian/mcp-everything-search)** - 跨Windows（使用[Everything SDK](https://www.voidtools.com/support/everything/sdk/)）、macOS（使用mdfind命令）和Linux（使用locate/plocate命令）的快速文件搜索功能。
- **[EVM MCP Server](https://github.com/mcpdotdirect/evm-mcp-server)** - 为 30 多个 EVM 网络提供全面的区块链服务，支持原生代币、ERC20、NFT、智能合约、交易和 ENS 解析。
- **[Excel](https://github.com/haris-musa/excel-mcp-server)** - Excel 操作包括数据读取/写入、工作表管理、格式设置、图表和数据透视表。
- **[Excel to JSON MCP by WTSolutions](https://github.com/he-yang/excel-to-json-mcp)** - MCP 服务器提供标准化接口，用于将 (1) Excel 或 CSV 数据转换为 JSON 格式；(2) Excel(.xlsx) 文件转换为结构化 JSON。
- **[Extended Memory](https://github.com/ssmirnovpro/extended-memory-mcp)** - 通过多项目支持、自动重要性评分和基于标签的组织，对 Claude 对话进行持久记忆。经过 400 多项测试即可投入生产。
- **[F1](https://github.com/AbhiJ2706/f1-mcp/tree/main)** - 访问一级方程式数据，包括比赛结果、车手信息、单圈时间、遥测和赛道详细信息。
- **[Fabi](https://docs.fabi.ai/advanced_features_and_dev_tools/mcp_server)** - MCP 服务器公开 [Fabi](https://app.fabi.ai/) 分析代理，将自然语言提示转化为见解：导航连接的数据、生成安全的 SQL/Python、运行查询以及将结果保存到仪表板中。
- **[Fabric MCP](https://github.com/aci-labs/ms-fabric-mcp)** - Microsoft Fabric MCP 服务器可在您最喜爱的 LLM 模型的帮助下加速 Fabric 租户的工作。
- **[Fabric Real-Time Intelligence MCP](https://github.com/Microsoft/fabric-rti-mcp)** - 官方 Microsoft Fabric RTI 服务器可使用您最喜爱的 LLM 模型加速与 Eventhouse、Azure Data Explorer(Kusto)、Eventstreams 和其他 RTI 项目的配合。
- **[fabric-mcp-server](https://github.com/adapoet/fabric-mcp-server)** - Fabric-mcp-server 是一个 MCP 服务器，它将 [Fabric](https://github.com/danielmiessler/fabric) 模式与 [Cline](https://cline.bot/) 集成，将它们公开为 AI 驱动的任务执行工具并增强 Cline 的功能。
- **[Facebook Ads](https://github.com/gomarble-ai/facebook-ads-mcp-server)** - MCP 服务器充当 Facebook 广告的接口，支持以编程方式访问 Facebook 广告数据和管理功能。
- **[Facebook Ads 10xeR](https://github.com/fortytwode/10xer)** - 先进的 Facebook Ads MCP 服务器，具有增强的创意洞察、多维细分和全面的广告效果分析。
- **[Facebook Ads Library](https://github.com/trypeggy/facebook-ads-library-mcp)** - 从 Facebook 广告库获取任何答案，在几秒钟内进行深入研究，包括消息传递、创意测试和比较。
- **[Fal MCP Server](https://github.com/raveenb/fal-mcp-server)** - 直接在 Claude 中使用 Fal.ai 模型（FLUX、Stable Diffusion、MusicGen）生成 AI 图像、视频和音乐
- **[Fantasy PL](https://github.com/rishijatia/fantasy-pl-mcp)** - 让您的编码代理能够直接访问最新的梦幻英超联赛数据
- **[Fast Filesystem](https://github.com/efforthye/fast-filesystem-mcp)** - 具有大文件处理功能和 Claude 优化功能的高级文件系统操作。提供快速文件读/写、大文件顺序读取、目录操作、文件搜索以及带备份和恢复的流式写入。
- **[Fastmail MCP](https://github.com/MadLlama25/fastmail-mcp)** - 通过 JMAP 访问 Fastmail：列出/搜索电子邮件、发送和移动邮件、处理附件/线程以及联系人和日历工具。
- **[fastn.ai – Unified API MCP Server](https://github.com/fastnai/mcp-fastn)** - 具有统一 API 的远程动态 MCP 服务器，可连接到 1,000 多个工具、操作和工作流程，并具有内置身份验证和监控功能。
- **[FDIC BankFind MCP Server - （非官方）]（https://github.com/clafollett/fdic-bank-find-mcp-server)** - 这是一个 MCP 服务器，可将 FDIC BankFind API 的强大功能直接引入您的 AI 工具和工作流程。结构化的美国银行数据，以最大的震撼力交付。😎📊
- **[Federal Reserve Economic Data (FRED)](https://github.com/stefanoamorelli/fred-mcp-server)** (by Stefano Amorelli) - 社区开发了 MCP 服务器来与美联储经济数据交互。
- **[Fetch](https://github.com/zcaceres/fetch-mcp)** - 灵活获取 HTML、JSON、Markdown 或纯文本的服务器。
- **[Feyod](https://github.com/jeroenvdmeer/feyod-mcp)** - 一个回答有关足球比赛问题的服务器，专门针对费耶诺德足球俱乐部。
- **[FHIR](https://github.com/wso2/fhir-mcp-server)** - 模型上下文协议服务器，提供对来自任何兼容 FHIR 服务器的快速医疗保健互操作性资源 (FHIR) 数据的无缝、标准化访问。它专为与人工智能工具、开发人员工作流程和医疗保健应用程序轻松集成而设计，可实现临床数据的自然语言和编程搜索、检索和分析。
- **[Fibaro HC3](https://github.com/coding-sailor/mcp-server-hc3)** - 适用于 Fibaro Home Center 3 智能家居系统的 MCP 服务器。
- **[Figma](https://github.com/GLips/Figma-Context-MCP)** - 让您的编码代理直接访问 Figma 文件数据，帮助其一次性设计实施。
- **[Figma](https://github.com/paulvandermeijs/figma-mcp)** - 速度极快的 MCP 服务器，用于读取和导出 Figma 设计文件。
- **[Figma to Flutter](https://github.com/mhmzdev/figma-flutter-mcp)** - 从Figma设计令牌中写下干净、更好的Flutter代码，并用Flutter术语丰富节点数据。
- **[Files](https://github.com/flesler/mcp-files)** - 使代理能够以外科手术般的精确度快速查找和编辑代码库中的代码。查找符号，随处编辑它们。
- **[FileSystem Server](https://github.com/Oncorporation/filesystem_server)** - 适用于 Visual Studio 2022 的本地 MCP 服务器，通过为 AI 代理提供对项目文件夹和文件的选择性访问来提供代码工作区功能
- **[finmap.org](https://github.com/finmap-org/mcp-server)** MCP 服务器提供来自美国、英国、俄罗斯和土耳其证券交易所的全面历史数据。访问行业、股票行情、公司概况、市值、数量、价值和交易数量，以及树状图和直方图可视化。
- **[Firebase](https://github.com/gannonh/firebase-mcp)** - 用于与 Firebase 服务交互的服务器，包括 Firebase 身份验证、Firestore 和 Firebase 存储。
- **[Fish Audio](https://github.com/da-okazaki/mcp-fish-audio-server)** - 文本转语音与 Fish Audio 的 API 集成，支持多种语音、流媒体和实时播放
- **[FitBit MCP Server](https://github.com/NitayRabi/fitbit-mcp)** - 使用从 OAuth 流获取的令牌连接到 FitBit API 的 MCP 服务器。
- **[Fleet](https://github.com/SimplyMinimal/fleet-mcp)** - 用于设备管理、安全监控和合规性执行的完整队列集成。支持主机管理、实时查询执行、策略管理、软件清单、漏洞跟踪和 MDM 操作。支持只读和读写模式。
- **[FlightRadar24](https://github.com/sunsetcoder/flightradar24-mcp-server)** - Claude Desktop MCP 服务器可帮助您使用 Flightradar24 数据实时跟踪航班。
- **[Fluent-MCP](https://github.com/modesty/fluent-mcp)** - 适用于 Fluent (ServiceNow SDK) 的 MCP 服务器，提供对 ServiceNow SDK CLI、API 规范、代码片段等的访问。
- **[Flyworks Avatar](https://github.com/Flyworks-AI/flyworks-mcp)** - 快速且免费的 Zeroshot 口型同步 MCP 服务器。
- **[fmp-mcp-server](https://github.com/vipbat/fmp-mcp-server)** - 使您的代理能够进行并购分析和投资银行工作流程。使用 [财务建模准备 API] 访问公司概况、财务报表、比率并执行行业分析
- **[FoundationModels](https://github.com/phimage/mcp-foundation-models)** - 集成 Apple 的 [FoundationModels](https://developer.apple.com/documentation/foundationmodels) 用于文本生成的 MCP 服务器。
- **[Foursquare](https://github.com/foursquare/foursquare-places-mcp)** - 使您的代理能够使用 [Foursquare Places API](https://location.foursquare.com/products/places-api/) 推荐世界各地的地点
- **[FPE Demo MCP](https://github.com/Horizon-Digital-Engineering/fpe-demo-mcp)** - FF3 格式保留加密与身份验证模式，以实现 LLM 工作流程中的安全数据保护。
- **[FrankfurterMCP](https://github.com/anirbanbasu/frankfurtermcp)** - MCP 服务器充当 [Frankfurter API](https://frankfurter.dev/) 货币兑换数据的接口。
- **[freqtrade-mcp](https://github.com/kukapay/freqtrade-mcp)** - 与 Freqtrade 加密货币交易机器人集成的 MCP 服务器。
- **[GDAL](https://github.com/Wayfinder-Foundry/gdal-mcp)** - GDAL 风格的地理空间工作流程具有内置推理指导和参考资源，可为 AI 代理提供目录发现、元数据智能和栅格/矢量处理。
- **[GDB](https://github.com/pansila/mcp_server_gdb)** - 基于MCP协议的GDB/MI协议服务器，提供AI助手远程应用调试能力。
- **[Gemini Bridge](https://github.com/eLyiN/gemini-bridge)** - 轻量级 MCP 服务器，使 Claude 能够通过官方 CLI 与 Google 的 Gemini AI 交互，提供零 API 成本和无状态架构。
- **[Geolocation](https://github.com/jackyang25/geolocation-mcp-server)** - WalkScore API 集成用于步行、交通和自行车评分。
- **[ggRMCP](https://github.com/aalobaidi/ggRMCP)** - 一个 Go 网关，可将 gRPC 服务转换为 MCP 兼容工具，允许 Claude 等 AI 模型直接调用您的 gRPC 服务。
- **[Ghost](https://github.com/MFYDev/ghost-mcp)** - 模型上下文协议 (MCP) 服务器，用于通过 Claude 等 LLM 接口与 Ghost CMS 进行交互。
- **[Git](https://github.com/geropl/git-mcp-go)** - 允许 LLM 与本地 git 存储库交互，包括。可选的推送支持。
- **[Git Mob](https://github.com/Mubashwer/git-mob-mcp-server)** - MCP 服务器与 [git-mob](https://github.com/Mubashwer/git-mob) CLI 应用程序交互，用于在pair/mob 编程期间管理 git 提交中的共同作者。
- **[Github](https://github.com/0xshariq/github-mcp-server)** - 模型上下文协议 (MCP) 服务器，为 AI 助手和开发人员提供 29 个 Git 操作 + 11 个工作流组合。该服务器通过标准化接口公开全面的 Git 存储库管理，使 AI 模型和开发人员能够安全地管理复杂的版本控制工作流程。
- **[GitHub Actions](https://github.com/ko1ynnky/github-actions-mcp-server)** - 用于与 GitHub Actions 交互的模型上下文协议 (MCP) 服务器。
- **[GitHub Enterprise MCP](https://github.com/ddukbg/github-enterprise-mcp)** - 用于与 GitHub Enterprise 交互的模型上下文协议 (MCP) 服务器。
- **[GitHub GraphQL](https://github.com/QuentinCody/github-graphql-mcp-server)** - 非官方 GitHub MCP 服务器，提供对 GitHub GraphQL API 的访问，支持对存储库数据、问题、拉取请求和其他 GitHub 资源进行更强大、更灵活的查询。
- **[GitHub Projects](https://github.com/redducklabs/github-projects-mcp)** — 通过完整的 GraphQL API 访问权限（包括项目、字段和里程碑）管理 GitHub 项目。
- **[GitHub Repos Manager MCP Server](https://github.com/kurdin/github-repos-manager-mcp)** - 基于令牌的 GitHub 自动化管理。无需 Docker，配置灵活，80 多个工具可直接 API 集成。
- **[GitMCP](https://github.com/idosal/git-mcp)** - gitmcp.io 是一个通用的远程 MCP 服务器，可以轻松连接到任何 GitHub 存储库或项目文档
- **[Glean](https://github.com/longyi1207/glean-mcp-server)** - 使用 Glean API 进行搜索和聊天的服务器。
- **[Gmail](https://github.com/GongRzhe/Gmail-MCP-Server)** - 用于在 Claude Desktop 中集成 Gmail 的模型上下文协议 (MCP) 服务器，并支持自动身份验证。
- **[Gmail](https://github.com/Ayush-k-Shukla/gmail-mcp-server)** - 用于 Gmail 的简单 MCP 服务器，支持 oauth2.0 的所有基本操作。
- **[Gmail Headless](https://github.com/baryhuang/mcp-headless-gmail)** - 远程托管 MCP 服务器无需本地凭据或文件系统设置即可获取和发送 Gmail 邮件。
- **[Gmail MCP](https://github.com/gangradeamitesh/mcp-google-email)** - 使用 MCP（模型上下文协议）的 Gmail 服务实现，提供通过 Gmail 的 API 发送、接收和管理电子邮件的功能。
- **[Gnuradio](https://github.com/yoelbassin/gnuradioMCP)** - 用于 GNU Radio 的 MCP 服务器，使 LLM 能够自主创建和修改 RF .grc 流程图。
- **[Goal Story](https://github.com/hichana/goalstory-mcp)** - 用于个人和职业发展的目标跟踪器和可视化工具。
- **[GOAT](https://github.com/goat-sdk/goat/tree/main/typescript/examples/by-framework/model-context-protocol)** - 在任何区块链上运行超过 200 个链上操作，包括以太坊、Solana 和 Base。
- **[Godot](https://github.com/Coding-Solo/godot-mcp)** - MCP 服务器为项目编辑、调试和场景管理提供全面的 Godot 引擎集成。
- **[Golang Filesystem Server](https://github.com/mark3labs/mcp-filesystem-server)** - 通过使用 Go! 构建的可配置访问控制来保护文件操作。
- **[Goodnews](https://github.com/VectorInstitute/mcp-goodnews)** - 一个简单的 MCP 服务器，可提供精选的积极且令人振奋的新闻报道。
- **[Google Ads](https://github.com/gomarble-ai/google-ads-mcp-server)** - MCP 服务器充当 Google Ads 的接口，支持以编程方式访问 Facebook Ads 数据和管理功能。
- **[Google Analytics](https://github.com/surendranb/google-analytics-mcp)** - Google Analytics MCP 服务器可为法学硕士提供 200 多个维度和指标的数据进行分析。
- **[Google Analytics 4](https://github.com/gomakers-ai/mcp-google-analytics)** - 用于 Google Analytics 数据 API 和测量协议的 MCP 服务器，用于读取报告和发送事件。
- **[Google Calendar](https://github.com/v-3/google-calendar)** - 与 Google 日历集成以检查日程、查找时间以及添加/删除活动
- **[Google Calendar](https://github.com/nspady/google-calendar-mcp)** - 用于管理 Google 日历事件的 Google 日历 MCP 服务器。还支持按标题和位置等属性搜索事件。
- **[Google Custom Search](https://github.com/adenot/mcp-google-search)** - 通过 Google 自定义搜索 API 提供 Google 搜索结果
- **[Google Maps](https://github.com/Mastan1301/google_maps_mcp)** - 使用 Google Places API 提供位置结果。
- **[Google Sheets](https://github.com/xing5/mcp-google-sheets)** - 访问和编辑 Google 表格中的数据。
- **[Google Sheets](https://github.com/rohans2/mcp-google-sheets)** - 用 TypeScript 编写的 MCP 服务器，用于访问和编辑 Google 表格中的数据。
- **[Google Tasks](https://github.com/zcaceres/gtasks-mcp)** - Google Tasks API 模型上下文协议服务器。
- **[Google Vertex AI Search](https://github.com/ubie-oss/mcp-vertexai-search)** - 通过使用您自己的私人数据建立 Gemini 模型来提供 Google Vertex AI 搜索结果
- **[Google Workspace](https://github.com/taylorwilsdon/google_workspace_mcp)** - 全面的 Google Workspace MCP，完全支持使用 Streamable HTTP 或 SSE 传输的日历、云端硬盘、Gmail 和文档。
- **[Google-Scholar](https://github.com/JackKuo666/Google-Scholar-MCP-Server)** - 使 AI 助手能够通过简单的 MCP 界面搜索和访问 Google Scholar 论文。
- **[Google-Scholar](https://github.com/mochow13/google-scholar-mcp)** - 用 TypeScript 编写的 Google Scholar MCP 服务器，具有可流式 HTTP 传输，以及与服务器集成并与 `gemini-2.5-flash` 交互的 `client` 实现。
- **[Gopher MCP](https://github.com/cameronrye/gopher-mcp)** - 现代跨平台 MCP 服务器，使 AI 助手能够安全高效地浏览 Gopher 协议和 Gemini 协议资源并与之交互。
- **[Gralio SaaS Database](https://github.com/tymonTe/gralio-mcp)** - 使用 [Gralio MCP](https://gralio.ai/mcp) 服务器查找并比较 SaaS 产品，包括来自 G2 评论、Trustpilot、Crunchbase、Linkedin、定价、功能等的数据
- **[GraphQL](https://github.com/drestrepom/mcp_graphql)** - 全面的 GraphQL API 集成，可自动将每个 GraphQL 查询公开为单独的工具。
- **[GraphQL Schema](https://github.com/hannesj/mcp-graphql-schema)** - 允许法学硕士探索大型 GraphQL 模式，而不会导致上下文膨胀。
- **[Graylog](https://github.com/Pranavj17/mcp-server-graylog)** - 按绝对/相对时间戳搜索 Graylog 日志，按流过滤，并直接从 Claude Desktop 调试生产问题。
- **[Grok-MCP](https://github.com/merterbak/Grok-MCP)** - 用于 xAI API 的 MCP 服务器，具有最新的 Grok 模型、图像分析和生成以及网络搜索。
- **[gx-mcp-server](https://github.com/davidf9999/gx-mcp-server)** - 将远大期望数据验证和质量检查作为 AI 代理的 MCP 工具。
- **[HackMD](https://github.com/yuna0x0/hackmd-mcp)** (by yuna0x0) - HackMD 的 MCP 服务器，协作 Markdown 编辑器。它允许用户使用模型上下文协议在 HackMD 中创建、读取和更新文档。
- **[HAProxy](https://github.com/tuannvm/haproxy-mcp-server)** - 在 Go 中实现的 HAProxy 模型上下文协议 (MCP) 服务器，利用 HAProxy 运行时 API。
- **[Hashing MCP Server](https://github.com/kanad13/MCP-Server-for-Hashing)** - 具有加密散列函数的 MCP 服务器，例如SHA256、MD5等
- **[HDW LinkedIn](https://github.com/horizondatawave/hdw-mcp-server)** - 使用 [HorizonDataWave.ai](https://horizondatawave.ai/) 访问配置文件数据并管理用户帐户。
- **[HeatPump](https://github.com/jiweiqi/heatpump-mcp-server)** — Residential heat - **HeatPumpHQ** 提供的泵选型和成本估算工具。
- **[Helm Chart CLI](https://github.com/jeff-nasseri/helm-chart-cli-mcp)** - Helm MCP 为 AI 助手和 Kubernetes 的 Helm 包管理器之间提供了一座桥梁。它允许 AI 助手通过自然语言请求与 Helm 交互，执行安装图表、管理存储库等命令。
- **[Heurist Mesh Agent](https://github.com/heurist-network/heurist-mesh-mcp-server)** - 通过 [Heurist Mesh network](https://github.com/heurist-network/heurist-agent-framework/tree/main/mesh) 访问专门的 web3 AI 代理，以进行区块链分析、智能合约安全、代币指标和区块链交互。
- **[HLedger MCP](https://github.com/iiAtlas/hledger-mcp)** - 复式记账纯文本会计，就在您的法学硕士课程中！此 MCP 支持对本地 [HLedger](https://hledger.org/) 会计日记帐进行全面的读取和（可选）写入访问。
- **[Holaspirit](https://github.com/syucream/holaspirit-mcp-server)** - 与 [Holaspirit](https://www.holaspirit.com/) 互动。
- **[Home Assistant](https://github.com/tevonsb/homeassistant-mcp)** - 与 [Home Assistant](https://www.home-assistant.io/) 交互，包括查看和控制灯光、开关、传感器和所有其他家庭助理实体。
- **[Home Assistant](https://github.com/voska/hass-mcp)** - 适用于 Home Assistant 的 Docker 就绪 MCP 服务器，具有实体管理、域摘要、自动化支持和引导对话。包括预构建的容器映像，以便于安装。
- **[HTML to Markdown](https://github.com/levz0r/html-to-markdown-mcp)** - 获取网页并将 HTML 转换为干净、格式化的 Markdown。通过自动文件保存处理大页面以绕过令牌限制。
- **[html2md-mcp](https://github.com/sunshad0w/html2md-mcp)** - MCP 服务器，用于将 HTML 转换为 Markdown，并具有浏览器支持和身份验证。使用 trafilatura 和 BeautifulSoup4 将 HTML 大小减少 90-95%，并与 JavaScript 渲染内容的 Playwright 集成。
- **[HubSpot](https://github.com/buryhuang/mcp-hubspot)** - 用于管理联系人和公司的 HubSpot CRM 集成。直接通过 Claude 聊天创建和检索 CRM 数据。
- **[HuggingFace Spaces](https://github.com/evalstate/mcp-hfspace)** - 用于使用 HuggingFace Spaces 的服务器，支持开源图像、音频、文本模型等。 Claude 桌面模式，易于集成。
- **[Human-In-the-Loop](https://github.com/GongRzhe/Human-In-the-Loop-MCP-Server)** - 功能强大的 MCP 服务器，使 Claude 等 AI 助手能够通过直观的 GUI 对话框与人类交互。该服务器通过提供实时用户输入工具、选择、确认和反馈机制，弥合了自动化人工智能流程和人类决策之间的差距。
- **[Human-use](https://github.com/RapidataAI/human-use)** - 通过 MCP 进行即时人类反馈，让您的 AI 与世界各地的人类互动。由 [Rapidata](https://www.rapidata.ai/) 提供支持
- **[Hyperledger Fabric Agent Suite](https://github.com/padmarajkore/hlf-fabric-agent)** - 用于通过 MCP 工具管理 Fabric 测试网络和链码生命周期的模块化工具包。
- **[Hyperliquid](https://github.com/mektigboy/server-hyperliquid)** - 集成 Hyperliquid SDK 以交换数据的 MCP 服务器实现。
- **[Hypertool](https://github.com/toolprint/hypertool-mcp)** – MCP that let's you create hot - 来自多个 MCP 服务器的可交换“角色工具集”，以减少工具过载并提高工具执行。
- **[hyprmcp](https://github.com/stefanoamorelli/hyprmcp)** (by Stefano Amorelli) - `hyprland` 的轻量级 MCP 服务器。
- **[iFlytek SparkAgent Platform](https://github.com/iflytek/ifly-spark-agent-mcp)** - 这是一个使用MCP Server调用科大讯飞SparkAgent平台任务链的简单示例。
- **[iFlytek Workflow](https://github.com/iflytek/ifly-workflow-mcp-server)** - 通过MCP服务器连接科大讯飞工作流并运行您自己的Agent。
- **[IIIF](https://github.com/code4history/IIIF_MCP)** - 全面的 IIIF（国际图像互操作性框架）协议支持，用于搜索、导航和操作全球博物馆、图书馆和档案馆的数字馆藏。
- **[Image Generation](https://github.com/GongRzhe/Image-Generation-MCP-Server)** - 该 MCP 服务器使用 Replicate Flux 模型提供图像生成功能。
- **[ImageSorcery MCP](https://github.com/sunriseapps/imagesorcery-mcp)** - 基于 ComputerVision 的🪄 神奇的人工智能助手图像识别和编辑工具。
- **[IMAP MCP](https://github.com/dominik1001/imap-mcp)** - 📧 IMAP 模型上下文协议 (MCP) 服务器，将 IMAP 操作公开为 AI 助手的工具。
- **[iMCP](https://github.com/loopwork-ai/iMCP)** - 一款 macOS 应用，为您的 iMessage、提醒事项和其他 Apple 服务提供 MCP 服务器。
- **[InfluxDB](https://github.com/idoru/influxdb-mcp-server)** - 针对 InfluxDB OSS API v2 运行查询。
- **[Inner Monologue MCP](https://github.com/abhinav-mangla/inner-monologue-mcp)** - 一种认知推理工具，使法学硕士能够在生成答案之前进行私密的、结构化的自我反思和多步骤推理，从而提高答案质量和解决问题的能力。
- **[Inoyu](https://github.com/sergehuber/inoyu-mcp-unomi-server)** - 与 Apache Unomi CDP 客户数据平台交互以检索和更新客户资料
- **[Instagram DM](https://github.com/trypeggy/instagram_dm_mcp)** - 通过您的法学硕士在 Instagram 上发送私信
- **[Intelligent Image Generator](https://github.com/shinpr/mcp-image)** - 通过 AI 增强将随意提示转变成专业品质的图像
- **[interactive-mcp](https://github.com/ttommyth/interactive-mcp)** - 通过将本地用户提示和聊天功能直接添加到 MCP 循环中，启用交互式 LLM 工作流程。
- **[Intercom](https://github.com/raoulbia-ai/mcp-server-for-intercom)** - 符合 MCP 的服务器，用于从 Intercom 检索客户支持票证。该工具使 Claude Desktop 和 Cline 等人工智能助手能够访问和分析您的 Intercom 支持票证。
- **[iOS Simulator](https://github.com/InditexTech/mcp-server-simulator-ios-idb)** - 模型上下文协议 (MCP) 服务器，使 LLM 能够通过自然语言命令与 iOS 模拟器（iPhone、iPad 等）进行交互。
- **[ipybox](https://github.com/gradion-ai/ipybox)** - 基于IPython和Docker的Python代码执行沙箱。有状态代码执行、主机和容器之间的文件传输、可配置的网络访问。详情请参见[ipybox MCP server](https://gradion-ai.github.io/ipybox/mcp-server/)。
- **[it-tools-mcp](https://github.com/wrenchpilot/it-tools-mcp)** - 模型上下文协议服务器，为 AI 代理重新创建 [CorentinTh it-tools](https://github.com/CorentinTh/it-tools) 实用程序，支持通过 MCP 访问各种开发人员工具（编码、解码、转换等）。
- **[itemit MCP](https://github.com/umin-ai/itemit-mcp)** - itemit 是资产跟踪 MCP，可管理为超过 300 个组织提供支持的库存、监控和位置跟踪。
- **[iTerm MCP](https://github.com/ferrislucas/iterm-mcp)** - 与 macOS 的 iTerm2 终端模拟器集成，使 LLM 能够执行和监控终端命令。
- **[iTerm MCP Server](https://github.com/rishabkoul/iTerm-MCP-Server)** - 用于 iTerm2 终端集成的模型上下文协议 (MCP) 服务器实现。能够管理多个 iTerm 会话。
- **[Java Decompiler](https://github.com/idachev/mcp-javadc)** - 使用 CFR 反编译器将 Java 字节码从 .class 文件、包名称或 JAR 存档反编译为可读源代码
- **[JavaFX](https://github.com/quarkiverse/quarkus-mcp-servers/tree/main/jfx)** - 使用 JavaFX 画布绘制绘图
- **[JDBC](https://github.com/quarkiverse/quarkus-mcp-servers/tree/main/jdbc)** - 连接到任何兼容 JDBC 的数据库并进行查询、插入、更新、删除等操作。支持 MySQL、PostgreSQL、Oracle、SQL Server、SQLite 和 [more](https://github.com/quarkiverse/quarkus-mcp-servers/tree/main/jdbc#supported-jdbc-variants)。
- **[Jenkins](https://github.com/jasonkylelol/jenkins-mcp-server)** - 该 MCP 服务器允许您创建 Jenkins 任务。
- **[JMeter](https://github.com/QAInsights/jmeter-mcp-server)** - 通过 MCP 兼容工具使用 Apache JMeter 运行负载测试。
- **[Job Searcher](https://github.com/0xDAEF0F/job-searchoor)** - FastMCP 服务器提供用于根据时间段、关键字和远程工作偏好检索和过滤职位列表的工具。
- **[jobswithgpt](https://github.com/jobswithgpt/mcp)** - 使用 jobswithgpt 进行职位搜索 MCP，它索引了 500K+ 公共职位列表并持续刷新。
- **[joinly](https://github.com/joinly-ai/joinly)** - MCP 服务器用于与基于浏览器的会议平台（Zoom、Teams、Google Meet）进行交互。使 AI 代理能够将机器人发送到在线会议、收集实时记录、朗读文本以及在会议聊天中发送消息。
- **[JSON](https://github.com/GongRzhe/JSON-MCP-Server)** - JSON 处理和处理服务器具有使用 JSONPath 语法的高级查询功能，并支持数组、字符串、数字和日期操作。
- **[JSON](https://github.com/kehvinbehvin/json-mcp-filter)** - JSON 模式生成和过滤服务器，具有 TypeScript 类型创建功能，经过优化，可使用 Quicktype-core 检索相关上下文 JSON 数据，并支持基于形状的数据提取、嵌套对象过滤和数组处理操作。
- **[JSON to Excel by WTSolutions](https://github.com/he-yang/json-to-excel-mcp)** - 将 (1) JSON 数据、(2) 指向公开可用的 .json 文件的 URL 转换为 CSV 格式字符串。
- **[JSON2Video MCP](https://github.com/omergocmen/json2video-mcp-server)** - 模型上下文协议 (MCP) 服务器实现，用于使用 json2video API 以编程方式生成视频。该服务器提供强大的视频生成和状态检查工具，可与 LLM、代理或任何 MCP 兼容的客户端一起使用。
- **[jupiter-mcp](https://github.com/kukapay/jupiter-mcp)** - MCP 服务器，用于使用 Jupiter 的新 Ultra API 在 Solana 区块链上执行代币交换。
- **[Jupyter MCP Server](https://github.com/datalayer/jupyter-mcp-server)** – 与 Jupyter Notebook 实时交互，允许 AI 编辑、记录和执行代码以进行数据分析、可视化等。与任何 Jupyter 部署（本地、JupyterHub 等）兼容。
- **[Jupyter Notebook](https://github.com/jjsantos01/jupyter-notebook-mcp)** - 将 Jupyter Notebook 连接到 Claude AI，让 Claude 可以直接与 Jupyter Notebook 交互并控制。这种集成支持人工智能辅助代码执行、数据分析、可视化等。
- **[k8s-multicluster-mcp](https://github.com/razvanmacovei/k8s-multicluster-mcp)** - MCP 服务器用于使用多个 kubeconfig 文件同时与多个 Kubernetes 集群交互。
- **[Kafka](https://github.com/tuannvm/kafka-mcp-server)** - 在 Go 中实现的 Apache Kafka 模型上下文协议 (MCP) 服务器，利用 [franz-go](https://github.com/twmb/franz-go)。
- **[Kafka Schema Registry MCP](https://github.com/aywengo/kafka-schema-reg-mcp)** \ - 用于 Kafka Schema 注册表的综合 MCP 服务器，具有 48 个工具、多注册表支持、身份验证和生产安全功能。通过企业级功能（包括架构上下文、迁移工具和全面的导出功能）实现人工智能驱动的架构管理。
- **[kafka-mcp](https://github.com/shivamxtech/kafka-mcp)** - 用于 Kafka 集群的 MCP 服务器，通过消息、主题、偏移量、消费者和生产者分区工具以及与 MCP 客户端的无缝集成与 kafka 环境交互。
- **[Kaggle-mcp](https://github.com/Seif-Sameh/Kaggle-mcp.git)** - 提供与 Kaggle API 无缝集成的 MCP 服务器。通过 Claude Desktop 等兼容 MCP 的客户端与 Kaggle 竞赛、数据集、内核和模型进行交互。
- **[Keycloak](https://github.com/idoyudha/mcp-keycloak)** - Keycloak MCP 服务器专为代理应用程序而设计，可有效管理和搜索 Keycloak 中的数据。
- **[Keycloak MCP](https://github.com/ChristophEnglisch/keycloak-model-context-protocol)** - 该 MCP 服务器支持与 Keycloak 进行自然语言交互，以进行用户和领域管理，包括创建、删除和列出用户和领域。
- **[Keycloak MCP Server](https://github.com/sshaaf/keycloak-mcp-server)** - 旨在与 Keycloak 配合使用进行身份和访问管理，拥有约 40 多个工具，涵盖用户、领域、客户端、角色、组、IDP、身份验证。可用本机构建。
- **[Kibana MCP](https://github.com/TocharianOU/mcp-server-kibana.git)** (by TocharianOU) - 社区维护的 MCP 服务器实现，允许任何兼容 MCP 的客户端通过自然语言或编程请求访问和管理 Kibana 实例。
- **[Kibela](https://github.com/kiwamizamurai/mcp-kibela-server)** (by kiwamizamurai) - 与 Kibela API 交互。
- **[KiCad MCP](https://github.com/lamaalrajih/kicad-mcp)** - Mac、Windows 和 Linux 上适用于 KiCad 的 MCP 服务器。
- **[kill-process-mcp](https://github.com/misiektoja/kill-process-mcp)** - 通过自然语言查询列出和终止操作系统进程
- **[Kindred Offers & Discounts MCP](https://github.com/kindred-app/mcp-server-kindred-offers)** (by kindred.co) - 该 MCP 服务器允许您从世界各地的电子商务商家网站获取实时交易和优惠/优惠券。
- **[kintone](https://github.com/macrat/mcp-server-kintone)** - 通过LLM工具管理[kintone](https://kintone.com)中的记录和应用程序。
- **[KnowAir Weather MCP](https://github.com/shuowang-ai/Weather-MCP)** - 综合模型上下文协议 (MCP) 服务器，由彩云天气 API 提供支持，提供实时天气数据、空气质量监测、预报和天文信息。
- **[Kokoro TTS](https://github.com/mberg/kokoro-tts-mcp)** - 使用 Kokoro 文本转语音将文本转换为 MP3，并可选择自动上传到 S3。
- **[Kong Konnect](https://github.com/Kong/mcp-konnect)** - 用于与 Kong Konnect API 交互的模型上下文协议 (MCP) 服务器，允许 AI 助手查询和分析 Kong 网关配置、流量和分析。
- **[Korea Stock Analyzer](https://github.com/Mrbaeksang/korea-stock-analyzer-mcp)** - 通过巴菲特、林奇、格雷厄姆、格林布拉特、费舍尔和邓普顿等 6 种传奇投资策略分析韩国股票 (KOSPI/KOSDAQ)。
- **[KRS Poland](https://github.com/pkolawa/krs-poland-mcp-server)** - 访问波兰国家法院登记处 (KRS)——政府对所有企业、基金会和其他法律实体的权威登记处。
- **[Kubeflow Spark History MCP Server](https://github.com/kubeflow/mcp-apache-spark-history-server)** - 使 AI 代理能够分析 Spark 作业性能、识别瓶颈并提供智能见解。
- **[Kubernetes](https://github.com/Flux159/mcp-server-kubernetes)** - 连接到 Kubernetes 集群并管理 Pod、部署和服务。
- **[Kubernetes and OpenShift](https://github.com/manusa/kubernetes-mcp-server)** - 功能强大的 Kubernetes MCP 服务器，还提供对 OpenShift 的额外支持。除了为任何 Kubernetes 资源提供 CRUD 操作之外，该服务器还提供专门的工具来与集群交互。
- **[KubeSphere](https://github.com/kubesphere/ks-mcp-server)** - KubeSphere MCP 服务器是一个模型上下文协议 (MCP) 服务器，提供与 KubeSphere API 的集成，从而能够从 KubeSphere 获取资源。分为四个工具模块：工作区管理、集群管理、用户和角色、扩展中心。
- **[Kukapay MCP Servers](https://github.com/kukapay/kukapay-mcp-servers)** - 一套全面的模型上下文协议 (MCP) 服务器，专用于 Kukapay 的加密货币、区块链和 Web3 数据聚合、分析和服务。
- **[kwrds.ai](https://github.com/mkotsollaris/kwrds_ai_mcp)** - 关键词研究，人们还问，SERP 和 [kwrds.ai](https://www.kwrds.ai/) 的其他 SEO 工具
- **[KYC-mcp-server](https://github.com/vishnurudra-ai/KYC-mcp-server)** - 了解您的计算机 (KYC) - MCP 服务器与 Claude Desktop 兼容。针对 Windows、Mac OS 和 Linux 操作系统的全面系统诊断，并提供人工智能支持的建议。
- **[Langflow MCP Server](https://github.com/nobrainer-tech/langflow-mcp)** - 全面的 MCP 服务器为 Langflow 工作流自动化提供 90 种工具 - 管理流、执行工作流、处理构建以及与知识库交互。包括 Docker 支持和 Langflow 1.6.4 的完整 API 覆盖。
- **[Langflow-DOC-QA-SERVER](https://github.com/GongRzhe/Langflow-DOC-QA-SERVER)** - 由 Langflow 提供支持的用于文档问答的模型上下文协议服务器。它通过提供一个简单的接口来通过 Langflow 后端查询文档，从而演示了核心 MCP 概念。
- **[Language Server](https://github.com/isaacphi/mcp-language-server)** - MCP 语言服务器允许启用 MCP 的客户端访问语义工具（例如获取定义、引用、重命名和诊断），从而帮助他们更轻松地导航代码库。
- **[Large File MCP](https://github.com/willianpinho/large-file-mcp)** - 通过智能分块、导航和流媒体功能智能处理大文件。具有 LRU 缓存、正则表达式
搜索和全面的文件分析。
- **[Lark(Feishu)](https://github.com/kone-net/mcp_server_lark)** - 飞书表单、消息、文档等的模型上下文协议（MCP）服务器。
- **[Lazy Toggl MCP](https://github.com/movstox/lazy-toggl-mcp)** - 通过 Toggl API 跟踪时间的简单非官方 MCP 服务器
- **[lean-lsp-mcp](https://github.com/oOo0oOo/lean-lsp-mcp)** - 通过语言服务器协议与 [Lean theorem prover](https://lean-lang.org/) 交互。
- **[librenms-mcp](https://github.com/mhajder/librenms-mcp)** - 用于[LibreNMS](https://www.librenms.org/)管理的MCP服务器
- **[libvirt-mcp](https://github.com/MatiasVara/libvirt-mcp)** - 允许 LLM 与 libvirt 交互，从而能够创建、销毁或列出系统中的虚拟机。
- **[Lightdash](https://github.com/syucream/lightdash-mcp-server)** - 与 BI 工具 [Lightdash](https://www.lightdash.com/) 交互。
- **[LINE](https://github.com/amornpan/py-mcp-line)** (by amornpan) - 实现 LINE Bot 集成，使语言模型能够通过标准化接口读取和分析 LINE 对话。具有异步操作、全面的日志记录、Webhook 事件处理以及对各种消息类型的支持。
- **[Linear](https://github.com/tacticlaunch/mcp-linear)** - 与线性项目管理系统交互。
- **[Linear](https://github.com/jerhadf/linear-mcp-server)** - 允许 LLM 与 Linear 的 API 进行交互以进行项目管理，包括搜索、创建和更新问题。
- **[Linear (Go)](https://github.com/geropl/linear-mcp-go)** - 允许 LLM 通过单个静态二进制文件与 Linear 的 API 进行交互。
- **[Linear MCP](https://github.com/anoncam/linear-mcp)** - 全面实施 Linear SDK，支持项目、计划、问题、用户、团队和状态的全面线性管理。
- **[Linked API MCP](https://github.com/Linked-API/linkedapi-mcp)** - MCP 服务器可让 AI 助手控制 LinkedIn 帐户并检索实时数据。
- **[Listmonk MCP Server](https://github.com/rhnvrm/listmonk-mcp)** (by rhnvrm) - [Listmonk](https://github.com/knadh/listmonk) 电子邮件营销 FOSS 的完整 API 覆盖。
- **[LlamaCloud](https://github.com/run-llama/mcp-server-llamacloud)** (by marcusschiesser) - 集成存储在 [LlamaCloud](https://cloud.llamaindex.ai/) 上的托管索引中的数据
- **[lldb-mcp](https://github.com/stass/lldb-mcp)** - 用于 LLDB 的模型上下文协议服务器，提供 LLM 驱动的调试。
- **[llm-context](https://github.com/cyberchitta/llm-context.py)** - 提供带有可配置配置文件的存储库打包 MCP 工具，该配置文件指定文件包含/排除模式和可选提示。
- **[Local History](https://github.com/xxczaki/local-history-mcp)** – 用于访问 VS Code/光标的本地历史记录的 MCP 服务器。
- **[Local RAG](https://github.com/shinpr/mcp-local-rag)** - 只需最少的设置即可进行轻量级本地文档搜索。搜索 PDF、DOCX、TXT 和 Markdown 文件 - 无需 Docker，无需外部服务。
- **[Locust](https://github.com/QAInsights/locust-mcp-server)** - 允许使用 MCP 兼容客户端运行和分析 Locust 测试。
- **[Loki](https://github.com/scottlepp/loki-mcp)** - 基于 Golang 的 MCP 服务器从 [Grafana Loki](https://github.com/grafana/loki) 查询日志。
- **[Loki MCP Server](https://github.com/mo-silent/loki-mcp-server)** - 基于 Python 的 MCP 服务器，用于查询和分析来自 Grafana Loki 的日志，并提供高级过滤和身份验证支持。
- **[LottieFiles](https://github.com/junmer/mcp-server-lottiefiles)** - 从 [LottieFiles](https://lottiefiles.com/) 中搜索和检索 Lottie 动画
- **[lsp-mcp](https://github.com/Tritlo/lsp-mcp)** - 使用语言服务器协议与语言服务器交互，通过悬停、代码操作和完成来提供附加上下文信息。
- **[Lspace](https://github.com/Lspace-io/lspace-server)** - 将分散的 ChatGPT/Claude/Cursor 对话转化为持久的、可搜索的知识。
- **[lucene-mcp-server](https://github.com/VivekKumarNeu/MCP-Lucene-Server)** - spring boot 服务器使用 Lucene 进行快速文档搜索和管理。
- **[lucid-mcp-server](https://github.com/smartzan63/lucid-mcp-server)** – An MCP server for Lucidchart and Lucidspark: connect, search, and obtain text representations of your Lucid documents and diagrams via LLM - 驱动的人工智能视觉分析。 [npm](https://www.npmjs.com/package/lucid-mcp-server)
- **[LunarCrush Remote MCP](https://github.com/lunarcrush/mcp-server)** - 获取当前实时社交环境的最新社交指标和帖子以及 LLM 和令牌优化输出中的历史指标。自动交易/财务咨询的理想选择。
- **[mac-messages-mcp](https://github.com/carterlasalle/mac_messages_mcp)** - MCP 服务器通过模型上下文协议 (MCP) 与 iMessage 数据库安全连接，允许法学硕士查询和分析 iMessage 对话。它包括强大的电话号码验证、附件处理、联系人管理、群聊处理以及对发送和接收消息的全面支持。
- **[Maestro MCP](https://github.com/maestro-org/maestro-mcp)** - 用于通过 Maestro RPC API 与比特币交互的 MCP 服务器。
- **[Magg: The MCP Aggregator](https://github.com/sitbon/magg)** - 元 MCP 服务器充当通用中心，允许法学硕士自主发现、安装和编排多个 MCP 服务器，本质上使 AI 助手能够按需扩展自己的功能。包括 `mbro`，一个具有脚本功能的强大 CLI MCP 服务器浏览器。
- **[Mailchimp MCP](https://github.com/AgentX-ai/mailchimp-mcp)** - 允许 AI 代理与 Mailchimp API 交互（只读）
- **[MailNet](https://github.com/Astroa7m/MailNet-MCP-Server)** - 统一的 Gmail + Outlook MCP 服务器，具有代理编排、自动令牌刷新、新提供商的标准化基类以及用于音调、签名和线程感知回复的专用电子邮件设置端点。
- **[MalwareBazaar_MCP](https://github.com/mytechnotalent/MalwareBazaar_MCP)** (by Kevin Thomas) - 人工智能驱动的 MCP 服务器，可自主与 MalwareBazaar 交互，为授权网络安全研究工作流程提供实时威胁情报和样本元数据。
- **[man-mcp-server](https://github.com/guyru/man-mcp-server)** - MCP 用于搜索和访问本地计算机上的手册页。
- **[Mandoline](https://github.com/mandoline-ai/mandoline-mcp-server)** - 让人工智能助手能够利用 Mandoline 的评估框架来反思、批判并不断提高自己的表现。
- **[MariaDB](https://github.com/abel9851/mcp-server-mariadb)** - MariaDB 数据库与 Python 中的可配置访问控制集成。
- **[Markdown2doc](https://github.com/Klavis-AI/klavis/tree/main/mcp_servers/pandoc)** - 使用 Pandoc 在各种文件格式之间进行转换
- **[Markdownify](https://github.com/zcaceres/mcp-markdownify-server)** - MCP 可将几乎所有内容转换为 Markdown（PPTX、HTML、PDF、Youtube 脚本等）
- **[market-fiyati](https://github.com/mtcnbzks/market-fiyati-mcp-server)** - marketfiyati.org.tr 的 MCP 服务器，提供土耳其市场的杂货价格搜索和比较。）
- **[Markitdown](https://github.com/Klavis-AI/klavis/tree/main/mcp_servers/markitdown)** - 将文件转换为 Markdown
- **[Masquerade](https://github.com/postralai/masquerade)** - 在将 PDF 文档发送给 Claude 之前，先对其敏感信息进行编辑。 Masquerade 充当法学硕士的隐私防火墙。
- **[MasterGo](https://github.com/mastergo-design/mastergo-magic-mcp)** - 该服务器旨在将 MasterGo 设计工具与 AI 模型连接起来。它使 AI 模型能够直接从 MasterGo 设计文件中检索 DSL 数据。
- **[Matlab-MCP-Tools](https://github.com/neuromechanist/matlab-mcp-tools)** - 一个 MCP，用于编写和执行 MATLAB 脚本、维护 MCP 调用之间的工作区上下文、可视化绘图以及对 MATLAB 代码进行逐节分析，并完全访问 MATLAB 的计算功能。
- **[Maton](https://github.com/maton-ai/agent-toolkit/tree/main/modelcontextprotocol)** - 连接到您的 SaaS 工具，例如 HubSpot、Salesforce 等。
- **[Matrix](https://github.com/mjknowles/matrix-mcp-server)** - 与 Matrix 家庭服务器交互。
- **[Maven Tools MCP](https://github.com/arvindand/maven-tools-mcp)** - Maven JVM 构建工具的中央依赖智能。支持所有构建工具（Maven、Gradle、SBT、Mill），并集成 Context7 以提供文档支持。
- **[Maybe Don't AI Policy Engine](https://www.maybedont.ai/download/)** - 另一个 MCP 安全网关 Maybe Don’t AI 在任何呼叫到达下游 MCP 服务器之前都会对其进行策略检查，以保护用户免受代理行为不良的影响。
- **[MCP Bundles Hub](https://github.com/thinkchainai/mcpbundles)** - 通过 [MCP Bundles](https://mcpbundles.com) 发现、安装和管理 500 多个 MCP 提供商集成和捆绑包。
- **[MCP Compass](https://github.com/liuyoshio/mcp-compass)** - 建议适合您需求的 MCP 服务器
- **[MCP Context Provider](https://github.com/doobidoo/MCP-Context-Provider)** - 静态服务器为 AI 模型提供持久的特定于工具的上下文和规则，防止聊天会话之间的上下文丢失，并在交互中实现一致的行为。
- **[MCP Create](https://github.com/tesla0225/mcp-create)** - 动态 MCP 服务器管理服务，可动态创建、运行和管理模型上下文协议服务器。
- **[MCP Documentation Server](https://github.com/andrea9293/mcp-documentation-server)** - 通过嵌入或 Gemini AI（推荐）提供本地优先文档管理和语义搜索的服务器。通过磁盘持久性、内存索引和缓存优化性能。
- **[MCP Dynamic Tool Groups](https://github.com/ECF/MCPToolGroups)** - 使用 [annotated](https://github.com/spring-ai-community/mcp-annotations) Java 接口/类作为“工具组”的示例 MCP 服务器。  使用标准 MCP 注释，服务实现可以在运行时用于生成工具规范，然后动态地添加到 MCP 服务器或从 MCP 服务器中删除。   该功能在示例工具组中进行了演示，但可以类似地用于任何 API 或服务。
- **[MCP Installer](https://github.com/anaisbetts/mcp-installer)** - 该服务器是为您安装其他 MCP 服务器的服务器。
- **[MCP on Android TV](https://github.com/MiddlePoint-Solutions/mcp-on-android-tv)** - 直接在 Android TV 上运行的模型上下文协议 (MCP) 服务器，可对设备上的 ADB 进行捆绑访问。
- **[MCP OpenProject Server](https://github.com/boma086/mcp-openproject)** - 全面的 MCP 服务器，用于与 GitHub 安装、CLI 工具集成 OpenProject，并支持包括 Claude Code 和 Windsurf 在内的多个 AI 助手。
- **[MCP ProjectManage OpenProject](https://github.com/boma086/mcp-projectmanage-openproject)** - 该服务器为项目周报告提供 MCP 服务，并包含由 OpenProject 提供的项目管理信息。
- **[MCP Proxy Server](https://github.com/TBXark/mcp-proxy)** - MCP 代理服务器通过单个 HTTP 服务器聚合和服务多个 MCP 资源服务器。
- **[MCP Server Creator](https://github.com/GongRzhe/MCP-Server-Creator)** - 强大的模型上下文协议 (MCP) 服务器，可创建其他 MCP 服务器！该元服务器提供了用于动态生成 FastMCP 服务器配置和 Python 代码的工具。
- **[MCP Server Generator](https://github.com/SerhatUzbas/mcp-server-generator)** - 一个创建和管理MCP服务器的MCP服务器！通过 AI 指导、自动依赖性管理和 Claude Desktop 集成，帮助非技术用户和开发人员构建自定义 JavaScript MCP 服务器。
- **[MCP STDIO to Streamable HTTP Adapter](https://github.com/pyroprompts/mcp-stdio-to-streamable-http-adapter)** - 即使 MCP 客户端仅支持 STDIO，也可以连接到可流式 HTTP MCP 服务器。
- **[MCP Toolz](https://github.com/taylorleese/mcp-toolz)** - Claude Code 的上下文管理、todo 持久性和 AI 第二意见。跨会话保存和恢复上下文、代码片段和待办事项列表，并从 ChatGPT、Claude、Gemini 和 DeepSeek 获取反馈。
- **[MCP-Airflow-API](https://github.com/call518/MCP-Airflow-API)** - 用于 Apache Airflow API 集成的模型上下文协议 (MCP) 服务器。提供用于管理 Airflow 集群的综合工具，包括服务操作、配置管理、状态监控和请求跟踪。
- **[MCP-Ambari-API](https://github.com/call518/MCP-Ambari-API)** - 用于 Apache Ambari API 集成的模型上下文协议 (MCP) 服务器。该项目提供了管理Hadoop集群的工具，包括服务操作、配置管理、状态监控和请求跟踪。
- **[mcp-containerd](https://github.com/jokemanfire/mcp-containerd)** - Rust实现的containerd MCP支持CRI接口的操作。
- **[MCP-Database-Server](https://github.com/executeautomation/mcp-database-server)** - 与 SQL Server、SQLite 和 PostgreSQL 等数据库交互的最快方式
- **[mcp-grep](https://github.com/erniebrodeur/mcp-grep)** - 基于 Python 的 MCP 服务器为法学硕士带来了 grep 功能。支持常见的 grep 功能，包括模式搜索、不区分大小写的匹配、上下文行和递归目录搜索。
- **[mcp-k8s-go](https://github.com/strowk/mcp-k8s-go)** - 基于 Golang 的 Kubernetes 服务器，供 MCP 浏览 Pod 及其日志、事件、命名空间等。构建为可扩展的。
- **[mcp-local-rag](https://github.com/nkapila6/mcp-local-rag)** - “原始”RAG 式 Web 搜索模型上下文协议 (MCP) 服务器，使用 Google 的 MediaPipe Text Embedder 和 DuckDuckGo Search 在本地运行。
- **[mcp-mcp](https://github.com/wojtyniak/mcp-mcp)** - Meta-MCP 服务器充当 MCP 客户端的工具发现服务。
- **[mcp-meme-sticky](https://github.com/nkapila6/mcp-meme-sticky)** - 使用适用于 WhatsApp 或 Telegram 的 MCP 服务器制作表情包或贴纸。
- **[mcp-memory-service](https://github.com/doobidoo/mcp-memory-service)** - 通用 MCP 内存服务为超过 13 个 AI 应用程序的 AI 助手提供语义内存搜索、持久存储和自主内存整合。
- **[mcp-n8n](https://github.com/gomakers-ai/mcp-n8n)** - 与 41 个用于工作流程管理、执行监控、凭证和 100 多个预构建模板的工具完成 n8n API 集成。通过 AI 对话控制整个 n8n 自动化基础设施。
- **[MCP-NixOS](https://github.com/utensils/mcp-nixos)** - 模型上下文协议服务器，为 AI 助手提供有关 NixOS 软件包、系统选项、Home Manager 设置和 nix-darwin macOS 配置的准确实时信息。
- **[mcp-notify](https://github.com/aahl/mcp-notify)** - 消息推送的MCP服务器，支持微信、钉钉、Telegram、Bark、Lark、飞书、家庭助理。
- **[mcp-open-library](https://github.com/8enSmith/mcp-open-library)** - 用于开放图书馆 API 的模型上下文协议 (MCP) 服务器，使 AI 助手能够搜索书籍和作者信息。
- **[MCP-OpenStack-Ops](https://github.com/call518/MCP-OpenStack-Ops)** - 通过 MCP 服务器实现专业 OpenStack 操作自动化。用于集群监控、实例管理、音量控制和网络分析的专用工具。 FastMCP + OpenStack SDK + 承载身份验证。克劳德桌面准备好了。非常适合 DevOps 和云自动化。
- **[MCP-PostgreSQL-Ops](https://github.com/call518/MCP-PostgreSQL-Ops)** - 用于 Apache Ambari API 集成的模型上下文协议 (MCP) 服务器。该项目提供了管理Hadoop集群的工具，包括服务操作、配置管理、状态监控和请求跟踪。
- **[mcp-proxy](https://github.com/sparfenyuk/mcp-proxy)** - 连接到在 SSE 传输上运行的 MCP 服务器，或将 stdio 服务器公开为 SSE 服务器。
- **[mcp-proxy](https://github.com/mikluko/mcp-proxy)** - 轻量级代理，可为缺乏本机 OAuth 支持的 MCP 客户端处理 OAuth 2.0/PKCE 身份验证和令牌管理。
- **[mcp-read-website-fast](https://github.com/just-every/mcp-read-website-fast)** - 快速、高效的 Web 内容提取，可将网站转换为干净的 Markdown。具有 Mozilla 可读性、智能缓存、支持 robots.txt 的礼貌爬行以及具有最小依赖性的并发获取。
- **[mcp-salesforce](https://github.com/lciesielski/mcp-salesforce-example)** - MCP 服务器，提供与 Salesforce 实例交互的基本演示
- **[mcp-sanctions](https://github.com/madupay/mcp-sanctions)** - 根据全球制裁名单（OFAC、SDN、联合国等）对个人和组织进行筛查。通过提示或文件上传查询。
- **[mcp-screenshot-website-fast](https://github.com/just-every/mcp-screenshot-website-fast)** - 针对 Claude Vision API 优化的高质量屏幕截图。自动将整个页面平铺为 1072x1072 块（1.15 兆像素），并具有可配置的视口和动态内容的等待策略。
- **[mcp-server-leetcode](https://github.com/doggybee/mcp-server-leetcode)** - 练习并从 LeetCode 中检索问题。自动进行编码实践和竞赛的问题检索、解决方案和见解。
- **[Mcp-Swagger-Server](https://github.com/zaizaizhao/mcp-swagger-server)** (by zaizaizhao) - 该MCP服务器将OpenAPI规范转换为MCP工具，使AI助手能够通过标准化协议与REST API进行交互
- **[mcp-vision](https://github.com/groundlight/mcp-vision)** - MCP 服务器将 HuggingFace 计算机视觉模型（例如零样本目标检测）作为工具公开，从而增强大语言或视觉语言模型的视觉功能。
- **[mcp-weather](https://github.com/TimLukaHorstmann/mcp-weather)** - 通过 AccuWeather API（提供免费套餐）提供准确的天气预报。
- **[mcp-youtube-extract](https://github.com/sinjab/mcp_youtube_extract)** - 用于 YouTube 操作的模型上下文协议服务器，使用智能回退逻辑提取视频信息和文字记录。具有全面的日志记录、错误处理功能，并支持自动生成和手动转录。
- **[mcp_weather](https://github.com/isdaniel/mcp_weather_server)** - 从https://api.open-meteo.com API获取天气信息。
- **[mcpcap](https://github.com/mcpcap/mcpcap)** - 用于分析 PCAP 文件的模块化 Python MCP（模型上下文协议）服务器。
- **[MCPfinder](https://github.com/mcpfinder/server)** - AI 代理的“应用程序商店”：发现、安装 AI 功能并从中获利——所有这些都在 MCP 生态系统内。
- **[MCPIgnore Filesytem](https://github.com/CyberhavenInc/filesystem-mcpignore)** - 数据安全第一文件系统 MCP 服务器，实现 .mcpignore 以防止 MCP 客户端访问敏感数据。
- **[MCPJungle](https://github.com/mcpjungle/MCPJungle)** - 适用于企业 AI 代理的自托管 MCP 注册表和网关
- **[MCPShell](https://github.com/inercia/mcpshell)** - 该工具允许法学硕士安全地执行命令行工具，在法学硕士和操作系统命令之间提供安全的桥梁。
- **[Md2doc](https://github.com/Yorick-Ryu/md2doc-mcp)** - 使用外部转换服务将 Markdown 文本转换为 DOCX 格式
- **[MeasureSpace MCP](https://github.com/MeasureSpace/measure-space-mcp-server)** - 免费的[Model Context Protocol (MCP) Server](https://smithery.ai/server/@MeasureSpace/measure-space-mcp-server)，由[measurespace.io](https://measurespace.io)提供全球天气、气候、空气质量预报和地理编码服务。
- **[MediaWiki](https://github.com/ProfessionalWiki/MediaWiki-MCP-Server)** - 与任何 MediaWiki wiki 交互的模型上下文协议 (MCP) 服务器
- **[MediaWiki MCP adapter](https://github.com/lucamauri/MediaWiki-MCP-adapter)** - 适用于 MediaWiki 和 WikiBase API 的自定义模型上下文协议适配器
- **[medRxiv](https://github.com/JackKuo666/medRxiv-MCP-Server)** - 使 AI 助手能够通过简单的 MCP 界面搜索和访问 medRxiv 论文。
- **[mem0-mcp](https://github.com/mem0ai/mem0-mcp)** - Mem0 的模型上下文协议服务器，有助于管理编码首选项。
- **[Membase](https://github.com/unibaseio/membase-mcp)** - 通过 Membase 以分布式方式保存和查询您的代理内存。
- **[Meme MCP](https://github.com/lidorshimoni/meme-mcp)** - 通过模型上下文协议使用 Imgflip API 通过 AI 生成表情包。
- **[memento-mcp](https://github.com/gannonh/memento-mcp)** - 基于 Neo4j 构建的知识图谱存储系统，具有语义搜索、时间感知功能。
- **[memos-api-mcp](https://github.com/MemTensor/memos-api-mcp)** - [MemOS](https://memos.openmem.net/)（专为人工智能应用程序设计的内存管理操作系统）API 服务的模型上下文协议实现。
- **[Meta Ads Remote MCP](https://github.com/pipeboard-co/meta-ads-mcp)** - 远程 MCP 服务器与 Meta Ads API 交互 - 访问、分析和管理 Facebook、Instagram 和其他 Meta 平台广告活动。
- **[MetaTrader MCP](https://github.com/ariadng/metatrader-mcp-server)** - 使 AI LLM 能够使用 MetaTrader 5 平台执行交易。
- **[Metricool MCP](https://github.com/metricool/mcp-metricool)** - 模型上下文协议服务器与 Metricool 的社交媒体分析平台集成，可检索性能指标并跨 Instagram、Facebook、Twitter、LinkedIn、TikTok 和 YouTube 等网络安排内容。
- **[Microsoft 365](https://github.com/merill/lokka)** - （由 Merill 提供）适用于 Microsoft 365 的模型上下文协议 (MCP) 服务器。包括对所有服务的支持，包括 Teams、SharePoint、Exchange、OneDrive、Entra、Intune 等。有关更多详细信息，请参阅 [Lokka](https://lokka.dev/)。
- **[Microsoft 365](https://github.com/softeria/ms-365-mcp-server)** - 使用 Graph API 连接到 Microsoft Office 和整个 Microsoft 365 套件的 MCP 服务器（包括 Outlook/邮件、文件、Excel、日历）
- **[Microsoft 365](https://github.com/pnp/cli-microsoft365-mcp-server)** - 单个 MCP 服务器允许管理 Microsoft 365 的许多不同区域，例如：Entra ID、OneDrive、OneNote、Outlook、Planner、Power Apps、Power Automate、Power Platform、SharePoint Embedded、SharePoint Online、Teams、Viva Engage 等等。
- **[Microsoft 365 Files (SharePoint/OneDrive)](https://github.com/godwin3737/mcp-server-microsoft365-filesearch)** (by godwin3737) - MCP 服务器提供用于从 Microsoft 365 搜索和获取文件内容的工具，包括 Onedrive 和 SharePoint。适用于文档 (pdf/docx)、演示文稿、电子表格和图像。
- **[Microsoft Teams](https://github.com/InditexTech/mcp-teams-server)** - 集成 Microsoft Teams 消息传递（阅读、发布、提及、列出成员和线程）的 MCP 服务器
- **[Mifos X](https://github.com/openMF/mcp-mifosx)** - Mifos X 开源银行的 MCP 服务器可用于管理客户、贷款、储蓄、股票、金融交易和生成财务报告。
- **[Mikrotik](https://github.com/jeff-nasseri/mikrotik-mcp)** - Mikrotik MCP 服务器涵盖网络操作（IP、DHCP、防火墙等）
- **[Mindmap](https://github.com/YuChenSSR/mindmap-mcp-server)** (by YuChenSSR) - 从包含 Markdown 代码的输入生成思维导图的服务器。
- **[Minima](https://github.com/dmayboroda/minima)** - 用于本地文件上的 RAG 的 MCP 服务器
- **[MLflow](https://github.com/kkruglik/mlflow-mcp)** - MLflow MCP 服务器，用于通过高级查询、运行比较、工件访问和模型注册表进行 ML 实验跟踪。
- **[Mobile MCP](https://github.com/mobile-next/mobile-mcp)** (by Mobile Next) - MCP 服务器，用于使用物理设备或模拟器/仿真器进行移动 (iOS/Android) 自动化、应用程序抓取和开发。
- **[Modao Proto MCP](https://github.com/modao-dev/modao-proto-mcp)** - 由人工智能驱动的 HTML 原型生成服务器，可将自然语言描述转换为具有现代设计和响应式布局的完整 HTML 代码。支持设计描述扩展并与魔道工作空间无缝集成。
- **[Monday.com (unofficial)](https://github.com/sakce/mcp-server-monday)** - MCP 服务器与 Monday.com 版块和项目进行交互。
- **[MongoDB](https://github.com/kiliczsh/mcp-mongo-server)** - MongoDB 的模型上下文协议服务器。
- **[MongoDB & Mongoose](https://github.com/nabid-pf/mongo-mongoose-mcp)** - 具有 Mongoose 架构和验证的 MongoDB MCP 服务器。
- **[MongoDB Lens](https://github.com/furey/mongodb-lens)** - 适用于 MongoDB 数据库的全功能 MCP 服务器。
- **[Monzo](https://github.com/BfdCampos/monzo-mcp-bfdcampos)** - 通过自然语言访问和管理您的 Monzo 银行账户，包括跨多种账户类型（个人、联名、灵活）的余额检查、底池管理、交易列表和交易注释。
- **[Morningstar](https://github.com/Morningstar/morningstar-mcp-server)** - MCP 服务器与晨星研究、编辑和数据点进行交互
- **[MSSQL](https://github.com/aekanun2020/mcp-server/)** - MSSQL 数据库与可配置访问控制和模式检查集成
- **[MSSQL](https://github.com/JexinSam/mssql_mcp_server)** (by jexin) - Python 中用于 MSSQL 数据库的 MCP 服务器
- **[MSSQL-MCP](https://github.com/daobataotie/mssql-mcp)** (by daobataotie) - MSSQL MCP即参考官网的SQLite MCP进行修改以适应MSSQL
- **[MSSQL-MCP-Node](https://github.com/mihai-dulgheru/mssql-mcp-node)** (by mihai - dulgheru) – 适用于 Microsoft SQL Server 的 Node.js MCP 服务器，具有自动检测的单/多数据库配置、执行 SQL 和模式工具、强大的 Zod 验证以及用于本地测试的可选 Express 端点
- **[MSSQL-Python](https://github.com/amornpan/py-mcp-mssql)** (by amornpan) - 用于 MSSQL 数据库访问的只读 Python 实现，具有增强的安全功能、可配置的访问控制和架构检查功能。专注于通过 Python 生态系统进行安全的数据库交互。
- **[Multi-Model Advisor](https://github.com/YuChenSSR/multi-ai-advisor-mcp)** - 模型上下文协议 (MCP) 服务器可跨多个 Ollama 模型编排查询，综合其见解，为任何给定查询提供全面且多方面的 AI 视角。
- **[Multicluster-MCP-Sever](https://github.com/yanmxa/multicluster-mcp-server)** - GenAI 系统与多个 Kubernetes 集群交互的网关。
- **[MySQL](https://github.com/benborla/mcp-server-mysql)** (by benborla) - NodeJS 中的 MySQL 数据库集成，具有可配置的访问控制和模式检查
- **[MySQL](https://github.com/designcomputer/mysql_mcp_server)** (by DesignComputer) - Python 中的 MySQL 数据库集成，具有可配置的访问控制和模式检查
- **[MySQL-Server](https://github.com/tonycai/mcp-mysql-server)** (by TonyCai) - MySQL 数据库集成使用 Python 脚本，具有可配置的访问控制和模式检查，使用 stdio 模式进行合适的本地部署，您可以在 docker 容器中运行它。
- **[n8n](https://github.com/leonardsellem/n8n-mcp-server)** - 该MCP服务器为AI助手提供工具和资源来管理n8n工作流程和执行，包括列出、创建、更新和删除工作流程，以及监控其执行状态。
- **[Nacos MCP Router](https://github.com/nacos-group/nacos-mcp-router)** - 该MCP（模型上下文协议）服务器提供搜索、安装、代理其他MCP服务器的工具。
- **[Nanana](https://github.com/nanana-app/mcp-server-nano-banana)** - 该 MCP 提供由 Google Gemini Nano Banana 提供支持的 AI 文本到图像生成器和 AI 图像到图像编辑器。
- **[NASA](https://github.com/ProgramComputer/NASA-MCP-server)** (by ProgramComputer) - 访问 NASA 数据源的统一网关，包括但不限于 APOD、NEO、EPIC、GIBS。
- **[NASA Image MCP Server](https://github.com/adithya1012/NASA-MCP-Server/blob/main/README.md)** - MCP 服务器提供对 NASA 视觉数据 API 的访问，包括火星漫游者照片、地球卫星图像 (EPIC/GIBS) 和当天的天文图片。具有内置图像分析工具，具有自动格式检测、压缩和用于 LLM 集成的 Base64 转换功能。
- **[NASA Planetary Data System (PDS) MCP Server](https://github.com/NASA-PDS/pds-mcp-server)** - MCP 服务器用于连接 NASA 的行星数据系统 (PDS)，从而实现从 20 世纪 60 年代至今的所有 NASA 数据产品的智能数据发现。
- **[Nasdaq Data Link](https://github.com/stefanoamorelli/nasdaq-data-link-mcp)** (by stefanoamorelli) - MCP 服务器用于访问、探索 Nasdaq Data Link 广泛且有价值的金融和经济数据集并与之交互。
- **[National Parks](https://github.com/KyrieTangSheng/mcp-server-nationalparks)** - 该服务器提供美国国家公园的公园详细信息、警报、游客中心、露营地、远足路线和活动的最新信息。
- **[NAVER](https://github.com/pfldy2850/py-mcp-naver)** (by pfldy2850) - 该MCP服务器提供与各种Naver服务交互的工具，例如搜索博客、新闻、书籍等。
- **[Naver](https://github.com/isnow890/naver-search-mcp)** (by isnow890) - 用于 Naver 搜索 API 集成的 MCP 服务器，支持博客、新闻、购物搜索和 DataLab 分析功能。
- **[NBA](https://github.com/Taidgh-Robinson/nba-mcp-server)** - 该 MCP 服务器提供了获取最近和历史 NBA 比赛的工具，包括基本和高级统计数据。
- **[NCI GDC](https://github.com/QuentinCody/nci-gdc-mcp-server)** - 美国国家癌症研究所基因组数据共享 (GDC) 的非官方 MCP 服务器，为肿瘤学研究提供统一的癌症基因组和临床数据的访问。
- **[NCP](https://github.com/portel-dev/ncp)** (Natural Context Provider by portel.dev) - NCP 让您的 AI 梦想成为一种工具，并以用户故事的形式阐明其需求。然后，NCP 会智能地发现并立即提供该工具，从而简化思维流程、消除认知过载，并将代币成本削减高达 87%（发现时间为 47 毫秒）。为您的 AI 代理体验真正的按需工具访问、智能健康监控和能源效率。
- **[Neo4j](https://github.com/da-okazaki/mcp-neo4j-server)** - 与 Neo4j 图形数据库交互的社区构建的服务器。
- **[Neovim](https://github.com/bigcodegen/mcp-neovim-server)** - 用于 Neovim 会话的 MCP 服务器。
- **[Netbird](https://github.com/aantti/mcp-netbird)** - 列出并分析 Netbird 网络对等点、组、策略等。
- **[NetMind ParsePro](https://github.com/protagolabs/Netmind-Parse-PDF-MCP)** - PDF Parser AI服务，由[NetMind](https://www.netmind.ai/)团队构建和定制。
- **[NetSuite](https://github.com/dsvantien/netsuite-mcp-server)** - 用于 NetSuite ERP 与 OAuth 2.0 身份验证集成的 MCP 服务器，支持通过 SuiteQL 查询、报告、保存的搜索和 REST API 操作以自然语言访问 NetSuite 数据。
- **[Nikto MCP](https://github.com/weldpua2008/nikto-mcp)** (by weldpua2008) - 一个安全的 MCP 服务器，使 AI 代理能够与 Nikto Web 服务器扫描仪交互]（- 与 npx 或 docker 一起使用）。
- **[NocoDB](https://github.com/edwinbernadus/nocodb-mcp-server)** - 对 NocoDB 数据库的读写访问。
- **[Node Code Sandbox](https://github.com/alfonsograziano/node-code-sandbox-mcp)** – A Node.js MCP server that spins up isolated Docker - 基于沙箱，用于通过即时 npm 依赖项安装来执行 JavaScript 片段
- **[nomad-mcp](https://github.com/kocierik/mcp-nomad)** - 提供一组用于通过 MCP 管理 Nomad 集群的工具的服务器。
- **[Notion](https://github.com/suekou/mcp-notion-server)** (by suekou) - 与 Notion API 交互。
- **[Notion](https://github.com/v-3/notion-server)** (by v-3) - MCP 集成概念。通过 Claude 聊天搜索、阅读、更新和创建页面。
- **[Notion](https://github.com/njbrake/notion-mcp-server)** (by njbrake) - 官方 Notion MCP 服务器的分支，返回 markdown 表示而不是原始 json，以实现有效的令牌使用
- **[NPM Plus](https://github.com/shacharsol/js-package-manager-mcp)** - AI 支持的 JavaScript 包管理，具有安全扫描、捆绑分析和适用于 MCP 兼容编辑器的智能依赖关系管理。
- **[NS Travel Information](https://github.com/r-huijts/ns-mcp-server)** - 通过官方 NS API 访问荷兰铁路 (NS) 实时火车旅行信息和中断情况。
- **[ntfy-mcp](https://github.com/teddyzxcv/ntfy-mcp)** (by teddyzxcv) - MCP 服务器通过使用 ntfy 在手机上发送通知来让您了解情况
- **[ntfy-me-mcp](https://github.com/gitmotion/ntfy-me-mcp)** (by gitmotion) - 一个 ntfy MCP 服务器，用于从 AI Agents 发送/获取 ntfy 通知到您的自托管 ntfy 服务器📤（支持安全令牌身份验证及更多 - 与 npx 或 docker 一起使用！）
- **[oatpp-mcp](https://github.com/oatpp/oatpp-mcp)** - Oat++ 的 C++ MCP 集成。使用[Oat++](https://oatpp.io)构建MCP服务器。
- **[Obsidian Markdown Notes](https://github.com/calclavia/mcp-obsidian)** - 阅读并搜索您的 ObsidianVault 或任何包含 Markdown 笔记的目录
- **[Obsidian Notes](https://github.com/Piotr1215/mcp-obsidian)** - 通过安全第一的设计、包括 MOC（内容地图）发现在内的高级搜索功能以及对 obsidian.nvim 的支持，直接文件系统访问黑曜石保险库 - 无需黑曜石应用程序。
- **[obsidian-mcp](https://github.com/StevenStavrakis/obsidian-mcp)** - （作者：Steven Stavrakis）Obsidian.md 的 MCP 服务器，带有用于搜索、阅读、编写和组织笔记的工具。
- **[OceanBase](https://github.com/yuanoOo/oceanbase_mcp_server)** - （作者：yuanoOo）模型上下文协议（MCP）服务器，可实现与 OceanBase 数据库的安全交互。
- **[Octocode](https://github.com/bgauryy/octocode-mcp)** - （作者：Guy Bary）人工智能驱动的开发人员助手，可跨 GitHub 和 NPM 领域实时进行高级代码研究、分析和发现
- **[Odoo](https://github.com/ivnvxd/mcp-server-odoo)** - 将 AI 助手连接到 Odoo ERP 系统，以实现业务数据访问和工作流程自动化。
- **[Office-PowerPoint-MCP-Server](https://github.com/GongRzhe/Office-PowerPoint-MCP-Server)** - 用于创建、读取和操作 Microsoft PowerPoint 文档的模型上下文协议 (MCP) 服务器。
- **[Office-Visio-MCP-Server](https://github.com/GongRzhe/Office-Visio-MCP-Server)** - 用于创建、读取和操作 Microsoft Visio 文档的模型上下文协议 (MCP) 服务器。
- **[Office-Word-MCP-Server](https://github.com/GongRzhe/Office-Word-MCP-Server)** - 用于创建、读取和操作 Microsoft Word 文档的模型上下文协议 (MCP) 服务器。
- **[Okta](https://github.com/kapilduraphe/okta-mcp-server)** - 与 Okta API 交互。
- **[OKX-MCP-Server](https://github.com/memetus/okx-mcp-playground)** - MCP服务器通过OKX API提供各种区块链数据和市场价格数据。该服务器使 Claude 能够执行检索资产价格、交易数据、账户历史数据和交易指令数据等操作。
- **[OneCite](https://github.com/HzaCode/OneCite)** - 通用引文管理和学术参考工具包。从 DOI、arXiv、标题或 URL 生成多种格式（BibTeX、APA、MLA）的引文。支持7+文献类型和10+学术数据库，并具有智能元数据补全功能。
- **[OneNote](https://github.com/rajvirtual/MCP-Servers/tree/master/onenote)** - （作者 Rajesh Vijay）使用 Microsoft Graph API 连接到 Microsoft OneNote 的 MCP 服务器。从 OneNote 中读取笔记本、分区和页面，在 OneNote 中创建新笔记本、分区和页面。
- **[Onyx MCP Sandbox](https://github.com/avd1729/Onyx)** –（由 Aravind）在隔离的 Docker 沙箱中执行代码的安全 MCP 服务器。支持 Python、Java、C、C++、JavaScript 和 Rust。提供 `run_code` 工具，强制执行 CPU/内存限制，包括全面的测试和详细的设置说明。
- **[Open Strategy Partners Marketing Tools](https://github.com/open-strategy-partners/osp_marketing_tools)** - 产品营销的内容编辑代码、价值地图和定位工具。
- **[Open Targets](https://github.com/QuentinCody/open-targets-mcp-server)** - 开放目标平台的非官方 MCP 服务器，提供对目标疾病关联、药物发现数据和生物医学研究治疗假设生成的访问。
- **[OpenAI GPT Image](https://github.com/SureScaleAI/openai-gpt-image-mcp)** - OpenAI GPT 图像生成/编辑 MCP 服务器。
- **[OpenAI WebSearch MCP](https://github.com/ConechoAI/openai-websearch-mcp)** - 这是一个基于Python的MCP服务器，提供OpenAI `web_search`内置工具。
- **[OpenAlex.org MCP](https://github.com/drAbreu/alex-mcp)** - 专业 MCP 服务器使用 OpenAlex 数据库提供基于 ML 的作者消歧和全面的研究人员资料。
- **[OpenAPI](https://github.com/snaggle-ai/openapi-mcp-server)** - 与 [OpenAPI](https://www.openapis.org/) API 交互。
- **[OpenAPI AnyApi](https://github.com/baryhuang/mcp-server-any-openapi)** - 使用端点的内置语义搜索与大型 [OpenAPI](https://www.openapis.org/) 文档进行交互。允许自定义 MCP 服务器前缀。
- **[OpenAPI Schema](https://github.com/hannesj/mcp-openapi-schema)** - 允许法学硕士探索大型 [OpenAPI](https://www.openapis.org/) 模式，而不会导致上下文膨胀。
- **[OpenAPI Schema Explorer](https://github.com/kadykov/mcp-openapi-schema-explorer)** - 通过 MCP 资源对本地或远程 OpenAPI/Swagger 规范进行令牌高效访问。
- **[OpenCTI](https://github.com/Spathodea-Network/opencti-mcp)** - 与 OpenCTI 平台交互以检索威胁情报数据，包括报告、指标、恶意软件和威胁参与者。
- **[OpenCV](https://github.com/GongRzhe/opencv-mcp-server)** - 提供 OpenCV 计算机视觉功能的 MCP 服务器。这使得人工智能助手和语言模型能够访问强大的计算机视觉工具。
- **[OpenDigger MCP Server](https://github.com/X-lab2017/open-digger-mcp-server)** - [OpenDigger](https://open-digger.cn/en/) 的模型上下文协议 (MCP) 服务器，通过工具和提示实现高级存储库分析和见解。
- **[OpenDota](https://github.com/asusevski/opendota-mcp-server)** - 与 OpenDota API 交互以检索 Dota 2 比赛数据、玩家统计数据等。
- **[OpenLink Generic Java Database Connectivity](https://github.com/OpenLinkSoftware/mcp-jdbc-server)** - 通过开放数据库连接 (ODBC) 连接器（驱动程序）访问通用数据库管理系统 (DBMS)
- **[OpenLink Generic Open Database Connectivity](https://github.com/OpenLinkSoftware/mcp-odbc-server)** - 通过开放数据库连接 (ODBC) 连接器（驱动程序）访问通用数据库管理系统 (DBMS)
- **[OpenLink Generic Python Open Database Connectivity](https://github.com/OpenLinkSoftware/mcp-pyodbc-server)** - 通过 PyODBC 的开放数据库连接 (ODBC) 连接器（驱动程序）访问通用数据库管理系统 (DBMS)
- **[OpenLink Generic SQLAlchemy Object-Relational Database Connectivity for PyODBC](https://github.com/OpenLinkSoftware/mcp-sqlalchemy-server)** - 通过 SQLAlchemy (PyODBC) 连接器（驱动程序）访问通用数据库管理系统 (DBMS)
- **[OpenMetadata](https://github.com/yangkyeongmo/mcp-server-openmetadata)** - MCP Server for OpenMetadata，一个开源元数据管理平台。
- **[OpenNeuro](https://github.com/QuentinCody/open-neuro-mcp-server)** - OpenNeuro 的非官方 MCP 服务器，提供对开放神经影像数据集、研究元数据和脑成像数据的访问，以进行神经科学研究和分析。
- **[OpenReview](https://github.com/anyakors/openreview-mcp-server)** - 用于 [OpenReview](https://openreview.net/) 的 MCP 服务器，用于从 AI/ML 会议获取、读取和保存手稿。
- **[OpenRPC](https://github.com/shanejonas/openrpc-mpc-server)** - 通过 [OpenRPC](https://open-rpc.org) 与 JSON-RPC API 交互并发现。
- **[OpenStack](https://github.com/wangsqly0407/openstack-mcp-server)** - 提供 OpenStack 交互的 MCP 服务器实现。
- **[OpenWeather](https://github.com/mschneider82/mcp-openweather)** - 与免费的 openweathermap API 交互，获取某个位置的当前天气和预报天气。
- **[OpenZIM MCP](https://github.com/cameronrye/openzim-mcp)** - 现代、安全、高性能的 MCP 服务器，使 AI 模型能够离线访问和搜索 ZIM 格式的知识库，包括维基百科和教育内容档案。
- **[Operative WebEvalAgent](https://github.com/Operative-Sh/web-eval-agent)** (by [Operative.sh](https://www.operative.sh)) - 用于自主测试、调试和修复 Web 应用程序的 MCP 服务器。
- **[OPNSense MCP](https://github.com/vespo92/OPNSenseMCP)** - 用于 OPNSense 防火墙管理和 API 访问的 MCP 服务器
- **[Optimade MCP](https://github.com/dianfengxiaobo/optimade-mcp-server)** - MCP 服务器使用 Optimade 数据库进行实时材料科学数据查询（例如元素组成、晶体结构）。
- **[Oracle](https://github.com/marcelo-ochoa/servers)** (by marcelo-ochoa) - NodeJS 中的 Oracle 数据库集成，具有可配置的访问控制、查询解释、统计信息和模式检查
- **[Oracle Cloud Infrastructure (OCI)](https://github.com/karthiksuku/oci-mcp)** (by karthiksukumar) - 用于 OCI 基础设施（计算、自治数据库、对象存储）的 Python MCP 服务器。默认情况下，具有安全实例操作（启动/停止/重置）的大量读取。包括 Claude 桌面配置和 `.env` 隔间范围。
- **[Oura MCP server](https://github.com/tomekkorbak/oura-mcp-server)** - 用于 Oura API 检索睡眠数据的 MCP 服务器
- **[Oura Ring](https://github.com/rajvirtual/oura-mcp-server)** (by Rajesh Vijay) - MCP 服务器用于访问和分析您的 Oura Ring 数据。它提供了一种结构化的方式来获取和了解您的健康指标。
- **[Outline](https://github.com/Vortiago/mcp-outline)** - MCP 服务器与 [Outline](https://www.getoutline.com) 知识库交互，以搜索、读取、创建和管理文档及其内容、访问集合、添加评论以及管理文档反向链接。
- **[Outlook Mail + Calendar + OneDrive](https://github.com/Norcim133/OutlookMCPServer) - 具有 Outlook 邮件、日历和早期 OneDrive 支持的虚拟助理（需要 Azure 管理员）。
- **[Pacman](https://github.com/oborchers/mcp-server-pacman)** - 提供包索引查询功能的MCP服务器。该服务器能够从 PyPI、npm、crates.io、Docker Hub 和 Terraform Registry 等包存储库中搜索和检索信息。
- **[pancakeswap-poolspy-mcp](https://github.com/kukapay/pancakeswap-poolspy-mcp)** - 一个 MCP 服务器，用于跟踪 Pancake Swap 上新创建的流动性池。
- **[Pandoc](https://github.com/vivekVells/mcp-pandoc)** - MCP 服务器使用 Pandoc 进行无缝文档格式转换，支持 Markdown、HTML、PDF、DOCX (.docx)、csv 等。
- **[Paradex MCP](https://github.com/sv/mcp-paradex-py)** - MCP 本机服务器用于与 Paradex 平台交互，包括全功能交易。
- **[Parliament MCP]([https://github.com/sv/mcp-paradex-py](https://github.com/i-dot-ai/parliament-mcp))** - 用于查询英国议会数据的 MCP 服务器。
- **[PDF reader MCP](https://github.com/gpetraroli/mcp_pdf_reader)** - MCP 服务器用于读取和搜索本地 PDF 文件中的文本。
- **[PDF Tools MCP](https://github.com/Sohaib-2/pdf-mcp-server)** - 全面的 PDF 操作工具包（合并、分割、加密、优化等等）
- **[PDMT](https://github.com/paiml/pdmt)** - 实用的确定性 MCP 模板 - 高性能确定性模板库，具有全面的待办事项验证、质量执行和 0.0 温度生成，以实现可重现的输出。
- **[Peacock for VS Code](https://github.com/johnpapa/peacock-mcp)** - 适用于 VS Code 的 Peacock 扩展的 MCP 服务器，一次一个代码编辑器，为您的世界增添色彩。该项目的主要目标是展示如何使用 MCP 服务器与 API 交互。
- **[persistproc](https://github.com/irskep/persistproc)** - MCP 服务器 + 命令行工具，允许代理查看和控制长时间运行的进程，例如 Web 服务器。
- **[Pexels](https://github.com/garylab/pexels-mcp-server)** - MCP 服务器提供对 Pexels 免费图像 API 的访问，支持无缝搜索、检索和下载高质量免版税图像。
- **[pgtuner_mcp](https://github.com/isdaniel/pgtuner_mcp)** - 提供AI驱动的PostgreSQL性能调优能力。
- **[Pharos](https://github.com/QuentinCody/pharos-mcp-server)** - 美国国家转化科学促进中心 (NCATS) 为 Pharos 数据库提供非官方 MCP 服务器，为药物发现研究提供靶点、药物和疾病信息的访问。
- **[Phone MCP](https://github.com/hao-cyber/phone-mcp)** - 📱 一个强大的插件，可让您控制您的 Android 手机。使人工智能代理能够执行复杂的任务，例如根据天气自动播放音乐或拨打电话和发送短信。
- **[PIF](https://github.com/hungryrobot1/MCP-PIF)** - 个人智能框架 (PIF)，提供文件操作、结构化推理和基于日志的文档工具，以支持跨会话的连续性和不断发展的人类与人工智能协作。
- **[Pinecone](https://github.com/sirmews/mcp-pinecone)** - MCP 服务器用于搜索记录并将其上传到 Pinecone。利用 Pinecone 的推理 API，允许简单的 RAG 功能。
- **[Pinner MCP](https://github.com/safedep/pinner-mcp)** - 一个 MCP 服务器，用于将 GitHub Actions 和容器基础镜像固定到其不可变的 SHA 哈希值，以防止供应链攻击。
- **[Pixelle MCP](https://github.com/AIDC-AI/Pixelle-MCP)** - 全模式 AIGC 框架，可将 ComfyUI 工作流程无缝转换为零代码 MCP 工具，通过基于 Chainlit 的 Web 界面实现对文本、图像、声音和视频生成的全模式支持。
- **[Placid.app](https://github.com/felores/placid-mcp-server)** - 使用 Placid.app 模板生成图像和视频广告素材
- **[Plane](https://github.com/kelvin6365/plane-mcp-server)** - 该 MCP 服务器将帮助您通过 Plane 的 API 管理项目和问题
- **[Playwright](https://github.com/executeautomation/mcp-playwright)** - 该 MCP 服务器将帮助您使用 Playwright 运行浏览器自动化和网页抓取
- **[Playwright Wizard](https://github.com/oguzc/playwright-wizard-mcp)** - 使用最佳实践生成 Playwright E2E 测试的分步向导。
- **[Podbean](https://github.com/amurshak/podbeanMCP)** - MCP 服务器，用于通过 Podbean API 管理您的播客、剧集和分析。允许更新、添加、删除播客、查询节目描述、注释、分析等。
- **[Polarsteps](https://github.com/remuzel/polarsteps-mcp)** - MCP 服务器可帮助您查看以前的旅行并计划新的旅行！
- **[PostgreSQL](https://github.com/ahmedmustahid/postgres-mcp-server)** - PostgreSQL MCP 服务器提供双 HTTP/Stdio 传输，用于数据库架构检查和只读查询执行，并具有会话管理和 Podman（或 Docker）支持。
- **[Postman](https://github.com/shannonlal/mcp-postman)** - 用于通过 Newman 在本地运行 Postman Collections 的 MCP 服务器。允许简单执行Postman Server并返回集合是否通过所有测试的结果。
- **[Powerdrill](https://github.com/powerdrillai/powerdrill-mcp)** - 与 Powerdrill 数据集交互，使用 [Powerdrill](https://powerdrill.ai) 用户 ID 和项目 API 密钥进行身份验证。
- **[predictive-maintenance-mcp](https://github.com/LGDiMaggio/predictive-maintenance-mcp)** - 人工智能驱动的预测性维护和故障诊断。具有振动分析、轴承诊断、ISO 20816-3。工业机械的合规性和机器学习异常检测。
- **[Prefect](https://github.com/allen-munsch/mcp-prefect)** - 用于工作流程编排和 ELT/ETL 的 MCP 服务器，带有 Prefect Server 和 Prefect Cloud [https://www.prefect.io/]，使用 `prefect` python 客户端。
- **[Producer Pal](https://github.com/adamjmurray/producer-pal)** - 用于控制 Ableton Live 的 MCP 服务器，嵌入 Max for Live 设备中，以便轻松拖放安装。
- **[Productboard](https://github.com/kenjihikmatullah/productboard-mcp)** - 通过 MCP 将 Productboard API 集成到代理工作流程中。
- **[Prometheus](https://github.com/pab1it0/prometheus-mcp-server)** - 查询和分析 Prometheus - 开源监控系统。
- **[Prometheus (Golang)](https://github.com/tjhop/prometheus-mcp-server/)** - Prometheus MCP 服务器具有完整的 API 支持，除了基本查询支持之外，还可以进行全面管理并与 Prometheus 进行深度交互。它是用 go 编写的，是一个二进制安装，能够进行复杂部署的 STDIO、SSE 和 HTTP 传输。
- **[Prometheus (TypeScript)](https://github.com/yanmxa/prometheus-mcp-server)** - 使 AI 助手能够使用自然语言和 TypeScript 实现来查询 Prometheus。
- **[PubChem](https://github.com/sssjiang/pubchem_mcp_server)** - 从 pubchem API 中提取药物信息。
- **[PubMed](https://github.com/JackKuo666/PubMed-MCP-Server)** - 使 AI 助手能够通过简单的 MCP 界面搜索、访问和分析 PubMed 文章。
- **[Pulumi](https://github.com/dogukanakkaya/pulumi-mcp-server)** - MCP 服务器与 Pulumi API 交互，创建并列出堆栈
- **[Puppeteer vision](https://github.com/djannot/puppeteer-vision-mcp)** - 使用 Puppeteer 浏览网页并返回高质量的 Markdown。使用 AI 视觉功能自动处理 cookie、验证码和其他交互元素。
- **[Pushover](https://github.com/ashiknesin/pushover-mcp)** - 使用 [Pushover.net](https://pushover.net/) 向您的设备发送即时通知
- **[py-mcp-qdrant-rag](https://github.com/amornpan/py-mcp-qdrant-rag)** (by amornpan) - 模型上下文协议服务器实现，通过 Qdrant 矢量数据库集成提供 RAG 功能，使 AI 代理能够在 Mac、Linux 和 Windows 平台上通过本地或基于云的嵌入生成支持执行语义搜索和文档检索。
- **[pydantic/pydantic-ai/mcp-run-python](https://github.com/pydantic/pydantic-ai/tree/main/mcp-run-python)** - 通过由 Deno 和 Pyodide 提供支持的 MCP 工具调用在安全沙箱中运行 Python 代码
- **[Python CLI MCP](https://github.com/ofek/pycli-mcp)** - 与本地 Python 命令行应用程序交互。
- **[qa-use](https://github.com/desplega-ai/qa-use)** - 浏览器自动化和 QA 测试功能。该服务器与 [desplega.ai](https://desplega.ai) 集成，使用 AAA 框架提供自动化测试、会话监控、批量测试执行和智能测试指导。
- **[QGIS](https://github.com/jjsantos01/qgis_mcp)** - 通过 MCP 将 QGIS 连接到 Claude AI。这种集成可以实现快速辅助的项目创建、层加载、代码执行等。
- **[Qiniu MCP Server](https://github.com/qiniu/qiniu-mcp-server)** - 基于七牛云产品构建的模型上下文协议（MCP）服务器，支持用户在AI大模型客户端上下文中通过该MCP服务器访问七牛云存储、智能多媒体服务等。
- **[QuantConnect](https://github.com/taylorwilsdon/quantconnect-mcp)** - QuantConnect 算法交易平台编排 MCP - 代理法学硕士驱动的交易策略设计、研究和实施。
- **[Quarkus](https://github.com/quarkiverse/quarkus-mcp-servers)** - Quarkus Java 框架的 MCP 服务器。
- **[QuickChart](https://github.com/GongRzhe/Quickchart-MCP-Server)** - 用于使用 QuickChart.io 生成图表的模型上下文协议服务器
- **[Qwen_Max](https://github.com/66julienmartin/MCP-server-Qwen_Max)** - Qwen 模型的模型上下文协议 (MCP) 服务器实现。
- **[RabbitMQ](https://github.com/kenliao94/mcp-server-rabbitmq)** - 与 RabbitMQ 交互以发布和消费消息的 MCP 服务器。
- **[RAE](https://github.com/rae-api-com/rae-mcp)** - MPC 服务器将您的首选模型与 rae-api.com、Roya Academy of Spanish Dictionary 连接
- **[RAG Local](https://github.com/renl/mcp-rag-local)** - 该 MCP 服务器用于根据文本段落的语义在本地存储和检索文本段落。
- **[RAG Web Browser](https://github.com/apify/mcp-server-rag-web-browser)** Apify 的开源 RAG Web 浏览器 [Actor](https://apify.com/apify/rag-web-browser) 的 MCP 服务器，用于执行 Web 搜索、抓取 URL 并以 Markdown 形式返回内容。
- **[Raindrop.io](https://github.com/hiromitsusasaki/raindrop-io-mcp-server)** - 允许 LLM 使用模型上下文协议 (MCP) 与 Raindrop.io 书签进行交互的集成。
- **[Random Number](https://github.com/zazencodes/random-number-mcp)** - 为法学硕士提供基本的随机生成能力，完全基于 Python 标准库构建。
- **[RCSB PDB](https://github.com/QuentinCody/rcsb-pdb-mcp-server)** - 结构生物信息学蛋白质数据库研究合作实验室 (RCSB PDB) 的非官方 MCP 服务器，提供对 3D 蛋白质结构、实验数据和结构生物信息学信息的访问。
- **[Reaper](https://github.com/dschuler36/reaper-mcp-server)** - 与您的 [Reaper](https://www.reaper.fm/)（数字音频工作站）项目进行交互。
- **[Redbee](https://github.com/Tamsi/redbee-mcp)** - Redbee MCP 服务器提供与 Redbee API 交互的支持。
- **[Redfish](https://github.com/nokia/mcp-redfish)** - Redfish MCP 服务器提供与 [DMTF Redfish API](https://www.dmtf.org/standards/redfish) 交互的支持。
- **[Redis](https://github.com/GongRzhe/REDIS-MCP-Server)** - Redis 数据库操作和缓存微服务服务器，支持键值操作、过期管理和基于模式的键列表。
- **[Redis](https://github.com/prajwalnayak7/mcp-server-redis)** MCP 服务器与 Redis 服务器、AWS 内存数据库等进行交互，用于缓存或其他适合内存和键值存储的用例
- **[RedNote MCP](https://github.com/ifuryst/rednote-mcp)** - 用于访问RedNote(小红书、xhs)内容的MCP服务器
- **[Reed Jobs](https://github.com/kld3v/reed_jobs_mcp)** - 从 Reed.co.uk 搜索并检索职位列表。
- **[Rememberizer AI](https://github.com/skydeckai/mcp-server-rememberizer)** - MCP 服务器设计用于与 Rememberizer 数据源交互，促进增强的知识检索。
- **[Replicate](https://github.com/deepfates/mcp-replicate)** - 通过简单的基于工具的界面在 Replicate 上搜索、运行和管理机器学习模型。浏览模型、创建预测、跟踪其状态并处理生成的图像。
- **[Resend](https://github.com/Klavis-AI/klavis/tree/main/mcp_servers/resend)** - 使用重新发送服务发送电子邮件
- **[Restream](https://github.com/shaktech786/restream-mcp-server)** - 用于 Restream API 集成的模型上下文协议服务器 - 管理多平台直播流、控制通道和访问流分析。
- **[Revit MCP](https://github.com/revit-mcp)** - 为 Autodesk Revit 实施 MCP 协议的服务。
- **[Rijksmuseum](https://github.com/r-huijts/rijksmuseum-mcp)** - 与国家博物馆 API 接口，以搜索艺术品、检索艺术品详细信息、访问图像图块并探索用户收藏。
- **[Riot Games](https://github.com/jifrozen0110/mcp-riot)** - 英雄联盟的 MCP 服务器 – 通过 Riot API 获取玩家信息、排名、冠军统计数据和比赛历史记录。
- **[Rohlik](https://github.com/tomaspavlin/rohlik-mcp)** - 通过 Rohlik Group 平台（Rohlik.cz、Knuspr.de、Gurkerl.at、Kifli.hu、Sezamo.ro）购买杂货
- **[Rquest](https://github.com/xxxbrian/mcp-rquest)** - MCP 服务器提供逼真的类似浏览器的 HTTP 请求功能，具有准确的 TLS/JA3/JA4 指纹，可绕过反机器人措施。
- **[Rust MCP Filesystem](https://github.com/rust-mcp-stack/rust-mcp-filesystem)** - 快速、异步的 MCP 服务器，用于高效处理利用 Rust 的强大功能构建的各种文件系统操作。
- **[SafetySearch](https://github.com/surabhya/SafetySearch)** - 实时 FDA 食品安全数据：召回、不良事件、分析。
- **[Salesforce MCP](https://github.com/smn2gnt/MCP-Salesforce)** - 与 Salesforce 数据和元数据交互
- **[Salesforce MCP (AiondaDotCom)](https://github.com/AiondaDotCom/mcp-salesforce)** - 通用 Salesforce 与 OAuth 身份验证、智能学习系统、全面的备份功能以及适用于任何 Salesforce 组织（包括自定义对象和字段）的完整 CRUD 操作集成。
- **[Salesforce MCP Server](https://github.com/tsmztech/mcp-server-salesforce)** - Salesforce 与用于查询记录、执行 Apex、管理字段/对象以及处理调试日志的工具进行全面集成
- **[Scanova MCP Server](https://github.com/trycon/scanova-mcp)** - MCP 服务器，用于使用 [Scanova](https://scanova.io) API 创建和管理 QR 码。提供生成、管理和下载二维码的工具。
- **[SchemaCrawler](https://github.com/schemacrawler/SchemaCrawler-MCP-Server-Usage)** - 连接到任何关系数据库，并能够获取有效的 SQL，并提出诸如某个列前缀的含义之类的问题。
- **[SchemaFlow](https://github.com/CryptoRadi/schemaflow-mcp-server)** - 通过模型上下文协议对 AI-IDE 进行实时 PostgreSQL 和 Supabase 数据库模式访问。通过使用三个强大工具的安全 SSE 连接提供实时数据库上下文：get_schema、analyze_database 和 check_schema_alignment。 [SchemaFlow](https://schemaflow.dev)
- **[Scholarly](https://github.com/adityak74/mcp-scholarly)** - 用于搜索学术文章的 MCP 服务器。
- **[scrapling-fetch](https://github.com/cyberchitta/scrapling-fetch-mcp)** - 从受机器人保护的网站访问文本内容。使用 Scrapling 从具有反自动化措施的网站获取 HTML/markdown。
- **[Screeny](https://github.com/rohanrav/screeny)** - 隐私第一的 macOS MCP 服务器，通过窗口屏幕截图为 AI 代理提供视觉上下文
- **[ScriptFlow](https://github.com/yanmxa/scriptflow-mcp)** - 通过全面的脚本管理（添加、编辑、删除、列表、搜索、执行）和多语言支持（Bash、Python、Node.js、TypeScript），将复杂、重复的 AI 交互转换为持久的可执行脚本。
- **[SearXNG](https://github.com/ihor-sokoliuk/mcp-searxng)** - [SearXNG](https://docs.searxng.org) 的模型上下文协议服务器
- **[SearXNG](https://github.com/erhwenkuo/mcp-searxng)** - MCP 服务器通过 [SearXNG](https://docs.searxng.org) 提供 Web 搜索并以 makrdown 形式检索 url。
- **[SearXNG Public](https://github.com/pwilkin/mcp-searxng-public)** - 模型上下文协议服务器，用于从公共 [SearXNG](https://docs.searxng.org) 实例检索数据，并提供回退支持
- **[SEC EDGAR](https://github.com/stefanoamorelli/sec-edgar-mcp)** - （作者：Stefano Amorelli）社区模型上下文协议服务器，用于通过美国证券交易委员会 ([SEC](https://www.sec.gov/)) `Electronic Data Gathering, Analysis, and Retrieval` ([EDGAR](https://www.sec.gov/submit-filings/about-edgar)) 数据库访问财务文件和数据
- **[SendGrid](https://github.com/recepyavuz0/sendgrid-mcp-server)** - 与 SendGrid 的 API 集成的 MCP 服务器，使 AI 助手（如 Claude、ChatGPT 等）能够发送电子邮件、管理模板和跟踪电子邮件统计信息。
- **[SEO MCP](https://github.com/cnych/seo-mcp)** - 基于 Ahrefs 数据的免费 SEO 工具 MCP（模型控制协议）服务。包括反向链接、关键字提示等功能。通过 [claudemcp](https://www.claudemcp.com/servers/seo-mcp)。
- **[Serper](https://github.com/garylab/serper-mcp-server)** - 使用 [Serper](https://serper.dev) 执行 Google 搜索的 MCP 服务器。
- **[ServiceNow](https://github.com/osomai/servicenow-mcp)** - 用于与 ServiceNow 实例交互的 MCP 服务器
- **[ShaderToy](https://github.com/wilsonchenghy/ShaderToy-MCP)** - 该 MCP 服务器允许 LLM 与 ShaderToy API 交互，允许 LLM 从计算着色器示例中学习，并使他们能够创建以前无法创建的复杂 GLSL 着色器。
- **[ShareSeer](https://github.com/shareseer/shareseer-mcp-server)** - MCP 使用 [ShareSeer](https://shareseer.com) 实时访问 SEC 文件、财务和内幕交易数据
- **[Shell](https://github.com/sonirico/mcp-shell)** - 向人工智能伸出双手。 MCP 服务器可安全、可审核地按需运行 shell 命令
- **[Shodan MCP](https://github.com/Hexix23/shodan-mcp)** - MCP服务器与[Shodan](https://www.shodan.io/)交互
- **[Shopify](https://github.com/GeLi2001/shopify-mcp)** - MCP与Shopify API交互包括订单、产品、客户等。
- **[Shopify Storefront](https://github.com/QuentinCody/shopify-storefront-mcp-server)** - 非官方 MCP 服务器，允许 AI 代理发现 Shopify 店面并与其交互，以通过 Storefront API 获取产品、产品系列和其他商店数据。
- **[Simple Loki MCP](https://github.com/ghrud92/simple-loki-mcp)** - 一个简单的 MCP 服务器，用于使用 logcli 查询 Loki 日志。
- **[Siri Shortcuts](https://github.com/dvcrn/mcp-server-siri-shortcuts)** - MCP 可与 macOS 上的 Siri 快捷方式交互。将所有快捷方式公开为 MCP 工具。
- **[Skyvern](https://github.com/Skyvern-AI/skyvern/tree/main/integrations/mcp)** - MCP 让 Claude / Windsurf / Cursor / 你的 LLM 控制浏览器
- **[Slack](https://github.com/korotovsky/slack-mcp-server)** - 适用于 Slack Workspaces 的最强大的 MCP 服务器。此集成支持 Stdio 和 SSE 传输、代理设置，并且不需要 Workspace 管理员创建或批准任何权限或机器人。
- **[Slack](https://github.com/zencoderai/slack-mcp-server)** - Slack MCP 服务器支持 stdio 和 Streamable HTTP 传输。从原始 Anthropic 的实现扩展而来，现在是 [archived](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/slack)
- **[Slidespeak](https://github.com/SlideSpeak/slidespeak-mcp)** - 使用 [Slidespeak](https://slidespeak.com/) API 创建 PowerPoint 演示文稿。
- **[Smartlead](https://github.com/jean-technologies/smartlead-mcp-server-local)** - MCP 连接到 Smartlead。此外，还提供工具、功能以及与工作流程自动化平台的连接。
- **[Snowflake](https://github.com/Snowflake-Labs/mcp)** - Snowflake-Labs 官方提供的 Snowflake 开源 MCP 服务器支持提示 Cortex Agent、查询结构化和非结构化数据、对象管理、SQL 执行、语义视图查询等。 RBAC、细粒度 CRUD 控制以及支持的所有身份验证方法。
- **[Snowflake](https://github.com/isaacwasserman/mcp-snowflake-server)** - 该 MCP 服务器使 LLM 能够与 Snowflake 数据库交互，从而实现安全且受控的数据操作。
- **[Snowflake Cortex MCP Server](https://github.com/thisisbhanuj/Snowflake-Cortex-MCP-Server)** - 这款 Snowflake MCP 服务器为 Snowflake Cortex AI 功能提供工具，将这些功能引入 MCP 生态系统。当连接到 MCP 客户端（例如 Claude for Desktop、快速代理、Agentic Orchestration Framework）时，用户可以利用这些 Cortex AI 功能。
- **[SoccerDataAPI](https://github.com/yeonupark/mcp-soccer-data)** - 该MCP服务器提供基于SoccerDataAPI的实时足球比赛数据。
- **[Solana Agent Kit](https://github.com/sendaifun/solana-agent-kit/tree/main/examples/agent-kit-mcp-server)** - 该 MCP 服务器使 LLM 能够在 SendAI 的 Solana Agent Kit 的帮助下与 Solana 区块链进行交互，允许 40 多个协议操作，并且还在不断增长
- **[Solr MCP](https://github.com/mjochum64/mcp-solr-search)** - 该 MCP 服务器提供了在 Solr 服务器上执行搜索的基本功能。
- **[Solver](https://github.com/szeider/mcp-solver)** - 解决约束满足和优化问题。
- **[Solvitor](https://github.com/Adeptus-Innovatio/solvitor-mcp)** – Solvitor MCP server provides tools to access reverse engineering tools that help developers extract IDL files from closed - 获取 Solana 智能合约并对其进行反编译。
- **[Source to Knowledge Base](https://github.com/vezlo/src-to-kb)** - 使用 GPT-5、智能分块和 OpenAI 嵌入进行语义代码理解，通过人工智能驱动的搜索将源代码存储库转换为可搜索的知识库。
- **[Sourcerer](https://github.com/st3v3nmw/sourcerer-mcp)** - MCP 用于语义代码搜索和导航，减少令牌浪费。
- **[Specbridge](https://github.com/TBosak/specbridge)** - 轻松将您的 OpenAPI 规范转化为 MCP 工具。
- **[Splunk](https://github.com/jkosik/mcp-server-splunk)** - Splunk 的 Golang MCP 服务器（列出保存的搜索、警报、索引、宏...）。支持SSE和STDIO。
- **[Spotify](https://github.com/varunneal/spotify-mcp)** - 该 MCP 允许法学硕士播放和使用 Spotify。
- **[Spring Initializr](https://github.com/hpalma/springinitializr-mcp)** - 该 MCP 允许法学硕士使用自定义配置创建 Spring Boot 项目。您现在可以要求 AI 助手生成具有特定依赖项、Java 版本和项目结构的项目，而无需手动访问 start.spring.io。
- **[Squad AI](https://github.com/the-basilisk-ai/squad-mcp)** – 产品发现和战略平台集成。创建、查询和更新机会、解决方案、结果、要求和任何 MCP 意识的法学硕士的反馈。
- **[SSH](https://github.com/AiondaDotCom/mcp-ssh)** - 用于管理和控制 SSH 连接的代理。
- **[SSH](https://github.com/classfang/ssh-mcp-server)** - MCP服务器，可以远程执行SSH命令、上传文件、下载文件等。
- **[SSH MCP Server](https://github.com/sinjab/mcp_ssh)** - 用于 SSH 自动化的生产就绪模型上下文协议服务器，具有后台执行、文件传输和全面的超时保护。具有结构化输出、进度跟踪和企业级测试（87% 覆盖率）。
- **[sslmon](https://github.com/firesh/sslmon-mcp)** - 域名/HTTPS/SSL域名注册信息和SSL证书监控功能。查询任意域名的域名注册和过期信息，以及SSL证书信息和有效性状态。
- **[STAC](https://github.com/Wayfinder-Foundry/stac-mcp)** - STAC 目录和项目搜索 MCP 服务器，用于快速发现地理空间数据。
- **[Standard Korean Dictionary](https://github.com/privetin/stdict)** - 搜索 the dictionary using API
- **[Star Wars](https://github.com/johnpapa/mcp-starwars)** -SWAPI 星球大战 API 的 MCP 服务器。该项目的主要目标是展示如何使用 MCP 服务器与 API 交互。
- **[Starknet MCP Server](https://github.com/mcpdotdirect/starknet-mcp-server)** - 一个全面的 MCP 服务器，用于与 Starknet 区块链交互，提供查询区块链数据、解析 StarknetID 和执行代币传输的工具。
- **[Starling Bank](https://github.com/domdomegg/starling-bank-mcp)** - 通过 Starling Bank API 查看和管理 Starling Bank 账户和交易，包括账户余额检查和交易历史记录。
- **[Starwind UI](https://github.com/Boston343/starwind-ui-mcp/)** - 该 MCP 提供相关命令、文档和其他信息，使法学硕士能够充分利用 Starwind UI 的开源 Astro 组件。
- **[Stellar](https://github.com/syronlabs/stellar-mcp/)** - 该 MCP 服务器使 LLM 能够与 Stellar 区块链交互，以创建帐户、检查地址余额、分析交易、查看交易历史记录、铸造新资产、与智能合约交互等等。
- **[Stitch AI](https://github.com/StitchAI/stitch-ai-mcp/)** - 具有内存空间创建和检索功能的人工智能代理知识管理系统。
- **[Stockfish](https://github.com/sonirico/mcp-stockfish)** - MCP 服务器将 AI 系统连接到 Stockfish 国际象棋引擎
- **[Storybook](https://github.com/stefanoamorelli/storybook-mcp-server)** (by Stefano Amorelli) - 与 Storybook 组件库交互，支持跨不同视口的组件发现、故事管理、道具检查和视觉测试。
- **[Strava](https://github.com/r-huijts/strava-mcp)** - 连接到 Strava API 以访问活动数据、运动员档案、分段和路线，从而与 Claude 一起实现健身跟踪和分析。
- **[Strava API](https://github.com/tomekkorbak/strava-mcp-server)** - Strava API 的 MCP 服务器可检索用户的活动
- **[Stripe](https://github.com/atharvagupta2003/mcp-stripe)** - 该 MCP 允许与 Stripe 集成来处理付款、客户和退款。
- **[Substack/Medium](https://github.com/jonathan-politzki/mcp-writer-substack)** - 将 Claude 连接到您的 Substack/Medium 写作，从而对您发布的内容进行语义搜索和分析。
- **[System Health](https://github.com/thanhtung0201/mcp-remote-system-health)** - MCP（多通道协议）系统运行状况监控是一个强大的实时监控解决方案，旨在为远程 Linux 服务器提供全面的运行状况指标和警报。
- **[SystemSage](https://github.com/Tarusharma1/SystemSage)** - 适用于 Windows、Linux 和 macOS 的强大的跨平台系统管理和监控工具。
- **[Talk To Figma](https://github.com/sonnylazuardi/cursor-talk-to-figma-mcp)** - 该 MCP 服务器使 LLM 能够与 Figma 交互，从而允许他们以编程方式读取和修改设计。
- **[Talk To Figma via Claude](https://github.com/gaganmanku96/talk-with-figma-claude)** - TMCP 服务器专门为 Claude Desktop 提供无缝 Figma 集成，通过自然语言命令实现设计创建、修改和实时协作。
- **[TAM MCP Server](https://github.com/gvaibhav/TAM-MCP-Server)** - 通过 TAM/SAM 计算进行市场研究和商业情报，并集成 8 个经济数据源：Alpha Vantage、BLS、人口普查局、FRED、IMF、纳斯达克数据链、经合组织和世界银行。
- **[Tasks](https://github.com/flesler/mcp-tasks)** - 高效的任务管理器。旨在最大限度地减少工具混乱并最大限度地提高 LLM 预算效率，同时提供跨多种文件格式（Markdown、JSON、YAML）的强大搜索、过滤和组织功能
- **[Tavily search](https://github.com/RamXX/mcp-tavily)** - 用于 Tavily 搜索和新闻 API 的 MCP 服务器，具有明确的站点包含/排除
- **[TcpSocketMCP](https://github.com/SpaceyKasey/TcpSocketMCP/)** - 模型上下文协议 (MCP) 服务器提供原始 TCP 套接字访问，使 AI 模型能够使用原始 TCP 套接字直接与网络服务交互。支持多个并发连接，缓冲响应数据并触发自动响应。
- **[TeamRetro](https://github.com/adepanges/teamretro-mcp-server)** - 该 MCP 服务器允许 LLM 与 TeamRetro 交互，允许 LLM 管理用户、团队、团队成员、回顾、健康检查、操作、协议并获取报告。
- **[Telegram](https://github.com/chigwell/telegram-mcp)** - 一个 MCP 服务器，通过 Telethon 集成为 Telegram 提供分页聊天阅读、消息检索和消息发送功能。
- **[Telegram-Client](https://github.com/chaindead/telegram-mcp)** - Telegram API 桥接器，用于管理用户数据、对话框、消息、草稿、阅读状态等，以实现无缝交互。
- **[Telegram-mcp-server](https://github.com/DLHellMe/telegram-mcp-server)** - 直接在 Claude 中访问 Telegram 频道和群组。具有双模式操作，具有 API 访问（速度提高 100 倍）或网页抓取、无限制的帖子检索和搜索功能。
- **[Template MCP Server](https://github.com/mcpdotdirect/template-mcp-server)** - 用于创建新模型上下文协议服务器项目的 CLI 工具，具有 TypeScript 支持、双重传输选项和可扩展结构
- **[Tempo](https://github.com/scottlepp/tempo-mcp-server)** - 用于从 [Grafana Tempo](https://github.com/grafana/tempo) 查询跟踪/跨度的 MCP 服务器。
- **[Tensorboard Query](https://github.com/Alir3z4/tb-query)** - 用于查询和分析 TensorBoard 事件文件的 MCP 服务器。
- **[Teradata](https://github.com/arturborycki/mcp-teradata)** - 他的 MCP 服务器使法学硕士能够与 Teradata 数据库交互。该MCP服务器支持多任务数据分析的工具和提示
- **[Terminal-Control](https://github.com/GongRzhe/terminal-controller-mcp)** - MCP 服务器可通过标准化接口实现安全的终端命令执行、目录导航和文件系统操作。
- **[Terraform-Cloud](https://github.com/severity1/terraform-cloud-mcp)** - MCP 服务器将 AI 助手与 Terraform Cloud API 集成，让您可以通过自然对话来管理您的基础设施。
- **[TFT-Match-Analyzer](https://github.com/GeLi2001/tft-mcp-server)** - MCP服务器用于获取团战战术比赛历史和比赛详细信息，为用户提供每场比赛的详细背景。
- **[Thales CDSP CAKM MCP Server](https://github.com/sanyambassi/thales-cdsp-cakm-mcp-server)** - 用于 Thales CipherTrust 数据安全平台 (CDSP) 云密钥管理 (CAKM) 连接器的 MCP 服务器。此 MCP 服务器支持 Ms SQL 和 Oracle 数据库。
- **[Thales CDSP CRDP MCP Server](https://github.com/sanyambassi/thales-cdsp-crdp-mcp-server)** - 模型上下文协议 (MCP) 服务器，允许与 CipherTrust RestFul 数据保护 (CRDP) 数据保护服务进行交互。
- **[Thales CipherTrust Manager MCP Server](https://github.com/sanyambassi/ciphertrust-manager-mcp-server)** - 用于 Thales CipherTrust Manager 集成的 MCP 服务器，可实现安全密钥管理和加密操作。
- **[thegraph-mcp](https://github.com/kukapay/thegraph-mcp)** - 一个 MCP 服务器，使用来自 The Graph 的索引区块链数据为 AI 代理提供支持。
- **[TheHive MCP Server](https://github.com/redwaysecurity/the-hive-mcp-server)** - [TheHive](https://strangebee.com/thehive/) 安全事件响应平台的 MCP 服务器。
- **[Things3 MCP](https://github.com/urbanogardun/things3-mcp)** - 适用于 macOS 的 Things3 任务管理集成，具有全面的 TODO、项目和标签管理。
- **[Think MCP](https://github.com/Rai220/think-mcp)** - 通过集成思考工具增强任何代理的推理能力，如 [Anthropic's article](https://www.anthropic.com/engineering/claude-think-tool) 中所述。
- **[Think Node MCP](https://github.com/abhinav-mangla/think-tool-mcp)** - 通过集成思考工具增强任何代理的推理能力，如 [Anthropic's article](https://www.anthropic.com/engineering/claude-think-tool) 中所述。 （与节点一起使用）
- **[Ticket-Generator MCP](https://github.com/trycon/ticket-generator-mcp)** - 在 Streamable HTTP 传输中实现的模型上下文协议 (MCP) 服务器允许 AI 模型与 [Ticket Generator](https://ticket-generator.com/) API 交互，从而能够获取活动事件列表并通过 3 种不同的模式生成票证。
- **[Ticketmaster](https://github.com/delorenj/mcp-server-ticketmaster)** - 通过 Ticketmaster Discovery API 搜索活动、场地和景点
- **[Ticketmaster MCP Server](https://github.com/mochow13/ticketmaster-mcp-server)** - 在 Streamable HTTP 传输中实现的模型上下文协议 (MCP) 服务器，允许 AI 模型与 Ticketmaster Discovery API 交互，从而能够搜索活动、场地和景点。
- **[TickTick](https://github.com/alexarevalo9/ticktick-mcp-server)** - 模型上下文协议 (MCP) 服务器旨在与 TickTick 任务管理平台集成，从而实现智能上下文感知任务操作和自动化。
- **[Tideways](https://github.com/abuhamza/tideways-mcp-server)** - 模型上下文协议服务器，使 AI 助手能够查询 Tideways 性能监控数据并为 PHP 应用程序提供对话式性能见解。
- **[TigerGraph](https://github.com/custom-discoveries/TigerGraph_MCP)** - 社区构建的 MCP 服务器，可与 TigerGraph 图形数据库交互。
- **[TikTok Ads](https://github.com/AdsMCP/tiktok-ads-mcp-server)** - MCP 服务器，用于与 TikTok 广告平台交互，以进行活动管理、绩效分析、受众定位、创意管理和自定义报告。
- **[time-mcp-nuget](https://github.com/domdomegg/time-mcp-nuget)** - 获取 RFC 3339 格式的当前 UTC 时间（.NET/NuGet 实现）。
- **[time-mcp-pypi](https://github.com/domdomegg/time-mcp-pypi)** - 获取 RFC 3339 格式的当前 UTC 时间（Python/PyPI 实现）。
- **[tip.md](https://github.com/tipdotmd#-mcp-server-for-ai-assistants)** - MCP 服务器使 AI 助手能够与tip.md 的加密小费功能进行交互，从而允许代理或支持者直接从 AI 聊天界面向注册开发人员提供小费。
- **[TMD Earthquake](https://github.com/amornpan/tmd-earthquake-server-1.0)** - 🌍 泰国气象部门实时地震监测。具有震级过滤、基于位置的搜索（泰语/英语）、今日事件跟踪、危险地震警报和综合统计数据。涵盖区域和全球地震活动。
- **[TMDB](https://github.com/Laksh-star/mcp-server-tmdb)** - 该 MCP 服务器与电影数据库 (TMDB) API 集成，提供电影信息、搜索功能和推荐。
- **[Todoist](https://github.com/abhiz123/todoist-mcp-server)** - 与Todoist交互来管理您的任务。
- **[Todos](https://github.com/tomelliot/todos-mcp)** - 实用的待办事项列表管理器，可与您最喜欢的聊天机器人一起使用。
- **[token-minter-mcp](https://github.com/kukapay/token-minter-mcp)** - MCP 服务器为 AI 代理提供跨多个区块链铸造 ERC-20 代币的工具。
- **[token-revoke-mcp](https://github.com/kukapay/token-revoke-mcp)** - 用于跨多个区块链检查和撤销 ERC-20 代币配额的 MCP 服务器。
- **[Ton Blockchain MCP](https://github.com/devonmojito/ton-blockchain-mcp)** - 用于与 Ton 区块链交互的 MCP 服务器。
- **[Topolograph MCP](https://github.com/Vadims06/topolograph-mcp-server)** – A MCP server that enables LLMs to interact with OSPF and IS - IS 协议并分析网络拓扑、查询网络事件以及为 OSPF 和 IS-IS 协议执行路径计算。
- **[TouchDesigner](https://github.com/8beeeaaat/touchdesigner-mcp)** - 用于 TouchDesigner 的 MCP 服务器，支持与 TouchDesigner 项目、节点和参数进行交互。
- **[Transcribe](https://github.com/transcribe-app/mcp-transcribe)** - MCP 服务器为音频/视频文件和语音备忘录提供快速可靠的转录。它允许法学硕士与音频/视频文件的文本内容进行交互。
- **[Travel Planner](https://github.com/GongRzhe/TRAVEL-PLANNER-MCP-Server)** - 旅行规划和行程管理服务器与 Google 地图 API 集成，用于位置搜索、地点详细信息和路线计算。
- **[Trello MCP Server](https://github.com/lioarce01/trello-mcp-server)** - 与用户 Trello 看板交互并根据提示修改它们的 MCP 服务器。
- **[Trino](https://github.com/tuannvm/mcp-trino)** - 用 Go 实现的 Trino 高性能模型上下文协议 (MCP) 服务器。
- **[Tripadvisor](https://github.com/pab1it0/tripadvisor-mcp)** - MCP 服务器使法学硕士能够与 Tripadvisor API 交互，通过标准化 MCP 接口支持位置数据、评论和照片
- **[Triplyfy MCP](https://github.com/helpful-AIs/triplyfy-mcp)** - 一个 MCP 服务器，让法学硕士可以使用 Triplyfy 中的交互式地图来规划和管理行程；管理行程、地点和注释，以及搜索/保存航班。
- **[TrueNAS Core MCP](https://github.com/vespo92/TrueNasCoreMCP)** - 用于与 TrueNAS Core 交互的 MCP 服务器。
- **[TuriX Computer Automation MCP](https://github.com/TurixAI/TuriX-CUA/tree/mac_mcp)** - MCP服务器用于帮助自动化控制您的计算机完成您的预设任务。
- **[Tyk API Management](https://github.com/TykTechnologies/tyk-dashboard-mcp)** - 与组织的所有托管 API 聊天并执行其他 API 生命周期操作，管理令牌、用户、分析等。
- **[Typesense](https://github.com/suhail-ak-s/mcp-typesense-server)** - 模型上下文协议 (MCP) 服务器实现，为 AI 模型提供对 Typesense 搜索功能的访问。该服务器使法学硕士能够发现、搜索和分析存储在 Typesense 集合中的数据。
- **[UniFi Dream Machine](https://github.com/sabler/mcp-unifi)** 一个 MCP 服务器，可从 UniFi 站点管理器和本地 UniFi 路由器获取网络遥测数据。
- **[UniProt](https://github.com/QuentinCody/uniprot-mcp-server)** - UniProt 的非官方 MCP 服务器，提供对蛋白质序列数据、功能注释、分类信息以及蛋白质组学和生物信息学研究的交叉引用的访问。
- **[uniswap-poolspy-mcp](https://github.com/kukapay/uniswap-poolspy-mcp)** - MCP 服务器可跨九个区块链网络跟踪 Uniswap 上新创建的流动性池。
- **[uniswap-trader-mcp](https://github.com/kukapay/uniswap-trader-mcp)** - 用于 AI 代理的 MCP 服务器，用于跨多个区块链在 Uniswap DEX 上自动进行代币交换。
- **[Unity Catalog](https://github.com/ognis1205/mcp-server-unitycatalog)** - MCP 服务器使 LLM 能够与 Unity Catalog AI 交互，支持 Unity Catalog Functions 上的 CRUD 操作并将其作为 MCP 工具执行。
- **[Unity Integration (Advanced)](https://github.com/quazaai/UnityMCPIntegration)** - 高级 Unity3d 游戏引擎 MCP 支持直接在 Unity 内部执行任何编辑器相关代码、获取日志、获取编辑器状态并允许项目的文件访问，使其在脚本编辑或资产创建中更加有用。
- **[Unity MCP (AI Game Developer)](https://github.com/IvanMurzak/Unity-MCP)** - `Unity Editor` 和 `Unity Runtime` MCP 集成。单元测试、编码、C# Roslyn、反射、资产。帮助用人工智能创建游戏。并有助于在运行时运行游戏中的AI逻辑。
- **[Unity3d Game Engine](https://github.com/CoderGamester/mcp-unity)** - 一个 MCP 服务器，使 LLM 能够与 Unity3d 游戏引擎交互，支持访问各种单元的编辑器引擎工具（例如控制台日志、测试运行器日志、编辑器功能、层次结构状态等）并将它们作为 MCP 工具执行或将它们收集为资源。
- **[Universal MCP Servers](https://github.com/universal-mcp)** - 使用 [AgentR Universal MCP SDK](https://github.com/universal-mcp/universal-mcp) 创建的 MCP 服务器的集合。
- **[Unleash Integration (Feature Toggle)](https://github.com/cuongtl1992/unleash-mcp)** - 与 Unleash 功能切换系统集成的模型上下文协议 (MCP) 服务器实现。在LLM申请和Unleash功能标记系统之间提供桥梁
- **[Upbit MCP Server](https://github.com/solangii/upbit-mcp-server)** – An MCP server that enables real - 及时访问 Upbit 交易所的加密货币价格、市场摘要和资产列表。
- **[USA Spending MCP Server](https://github.com/thsmale/usaspending-mcp-server)** – 这利用了政府支出数据 [USASPENDING.gov](https://www.usaspending.gov/) 的官方来源。这使得人们能够跟踪一段时间内的政府支出、按机构搜索政府支出、探索政府对社区的支出等等。
- **[use_aws_mcp](https://github.com/runjivu/use_aws_mcp)** - amazon-q-cli 的 use_aws 工具提取到独立的 mcp 中，用于一般 aws api 使用。
- **[User Feedback](https://github.com/mrexodia/user-feedback-mcp)** - 简单的 MCP 服务器，可在 Cline 和 Cursor 等工具中启用人机交互工作流程。
- **[Useless Toolkit](https://uselesstoolkit.com/apis/mcp-servers)** - UselessToolkit.com 提供适用于实用程序 API（包括密码生成器、IP2Geo 等）的 MCP 就绪服务器端点，允许通过安全的 RapidAPI 连接与 AI 代理无缝集成。
- **[USPTO](https://github.com/riemannzeta/patent_mcp_server)** - MCP 服务器用于通过其开放数据协议 (ODP) API 访问美国专利商标局数据。
- **[Vectara](https://github.com/vectara/vectara-mcp)** - 查询 Vectara 值得信赖的 RAG 即服务平台。
- **[Vega-Lite](https://github.com/isaacwasserman/mcp-vegalite-server)** - 使用 VegaLite 格式和渲染器从获取的数据生成可视化效果。
- **[Vertica](https://github.com/nolleh/mcp-vertica)** - Vertica 数据库在 Python 中集成，具有可配置的访问控制和模式检查
- **[Vibe Check](https://github.com/PV-Bhat/vibe-check-mcp-server)** - MCP 服务器利用外部监督层来“氛围检查”代理，并随着时间的推移自我提高准确性和用户一致性。防止范围蔓延、代码膨胀、错位、误解、狭隘视野和过度复杂化。
- **[Video Editor](https://github.com/burningion/video-editing-mcp)** - 模型上下文协议服务器，用于使用 [Video Jungle](https://www.video-jungle.com/) 添加、编辑和搜索视频。
- **[Video Still Capture](https://github.com/13rac1/videocapture-mcp)** - 📷 从兼容 OpenCV 的网络摄像头或其他视频源捕获视频静态图像。
- **[Virtual location (Google Street View,etc.)](https://github.com/mfukushim/map-traveler-mcp)** - 集成 Google Map、Google Street View、PixAI、Stability.ai、ComfyUI API 和 Bluesky，在 LLM 中提供虚拟位置模拟（用 Effect.ts 编写）
- **[VMware Fusion](https://github.com/yeahdongcn/vmware-fusion-mcp-server)** - 通过 Fusion REST API 管理 VMware Fusion 虚拟机。
- **[Voice Status Report](https://github.com/tomekkorbak/voice-status-report-mcp-server)** - MCP 服务器使用 OpenAI 的文本转语音 API 提供语音状态更新，与 Cursor 或 Claude Code 一起使用。
- **[VoiceMode](https://github.com/mbailey/voicemode)** - 使用任何 OpenAI 兼容的 STT/TTS 服务 [getvoicemode.com](https://getvoicemode.com/) 启用与 Claude 的语音对话
- **[VolcEngine TOS](https://github.com/dinghuazhou/sample-mcp-server-tos)** - VolcEngine TOS 的示例 MCP 服务器，可灵活地从 TOS 获取对象。
- **[Voyp](https://github.com/paulotaylor/voyp-mcp)** - VOYP MCP 服务器，用于使用人工智能拨打电话。
- **[vscode-ai-model-detector](https://github.com/thisis-romar/vscode-ai-model-detector)** - VS Code Copilot 的实时 AI 模型检测，准确率 100%。通过聊天参与者 API 识别活动模型（Claude、GPT、Gemini），实现正确的 git 归因。
- **[vulnicheck](https://github.com/andrasfe/vulnicheck)** - 实时 Python 包漏洞扫描器，可检查 OSV 和 NVD 数据库的依赖关系，提供包含 CVE 详细信息、锁定文件支持和可操作升级建议的全面安全分析。
- **[Wanaku MCP Router](https://github.com/wanaku-ai/wanaku/)** - Wanaku MCP 路由器是基于 SSE 的 MCP 服务器，提供可扩展的路由引擎，允许将企业系统与 AI 代理集成。
- **[weather-mcp-server](https://github.com/devilcoder01/weather-mcp-server)** - 使用 Wea​​therAPI 获取任何位置的实时天气数据。
- **[Web Search MCP](https://github.com/mrkrsl/web-search-mcp)** - 提供完整网络搜索、摘要和页面提取以与本地法学硕士一起使用的服务器。
- **[Webex](https://github.com/Kashyap-AI-ML-Solutions/webex-messaging-mcp-server)** - 模型上下文协议 (MCP) 服务器，为 AI 助手提供对 Cisco Webex 消息传递功能的全面访问。
- **[Webflow](https://github.com/kapilduraphe/webflow-mcp-server)** - 与 Webflow API 交互
- **[webhook-mcp](https://github.com/noobnooc/webhook-mcp)** (by Nooc) - 模型上下文协议 (MCP) 服务器，在调用时发送 Webhook 通知。
- **[Wekan](https://github.com/namar0x0309/wekan-mcp)** - Wekan 的非官方 MCP 服务器，提供所有其余 api 功能来添加、编辑、删除任务和板。
- **[whale-tracker-mcp](https://github.com/kukapay/whale-tracker-mcp)**  - 用于跟踪加密货币鲸鱼交易的 mcp 服务器。
- **[WhatsApp MCP Server](https://github.com/lharries/whatsapp-mcp)** - MCP 服务器用于您的个人 WhatsApp 处理个人、群组、搜索和发送。
- **[Whois MCP](https://github.com/bharathvaj-ganesan/whois-mcp)** - MCP 服务器，针对域、IP、ASN 和 TLD 执行 whois 查找。
- **[Withings](https://github.com/akutishevsky/withings-mcp)** - 通过自然对话访问和分析 Withings 健康数据，包括睡眠分析、身体测量、锻炼、心电图记录和健身目标。
- **[Wikidata MCP](https://github.com/zzaebok/mcp-wikidata)** - Wikidata MCP 服务器通过搜索标识符、提取元数据和执行 sparql 查询与 Wikidata 进行交互。
- **[Wikidata SPARQL](https://github.com/QuentinCody/wikidata-sparql-mcp-server)** - 用于 Wikidata 的 SPARQL 端点的非官方 REMOTE MCP 服务器，提供对结构化知识数据、实体关系和语义查询的访问，以进行研究和数据分析。
- **[Wikifunctions](https://github.com/Fredibau/wikifunctions-mcp-fredibau)** - 允许 AI 模型发现并执行 WikiFunctions 库中的函数。
- **[Wikipedia MCP](https://github.com/Rudra-ravi/wikipedia-mcp)** - 通过 MCP 访问和搜索维基百科文章，以进行人工智能支持的信息检索。
- **[WildFly MCP](https://github.com/wildfly-extras/wildfly-mcp)** - WildFly MCP 服务器使 LLM 能够与正在运行的 WildFly 服务器交互（检索指标、日志、调用操作等）。
- **[Windows CLI](https://github.com/SimonB97/win-cli-mcp-server)** - MCP 服务器用于在 Windows 系统上进行安全的命令行交互，支持对 PowerShell、CMD 和 Git Bash shell 的受控访问。
- **[Windsor](https://github.com/windsor-ai/windsor_mcp)** - Windsor MCP（模型上下文协议）使您的法学硕士能够通过零 SQL 编写或自定义脚本来查询、探索和分析集成到 Windsor.ai 中的全栈业务数据。
- **[Wordle MCP](https://github.com/cr2007/mcp-wordle-python)** - 获取特定日期的 Wordle 解决方案的 MCP 服务器。
- **[WordPress MCP](https://github.com/Automattic/wordpress-mcp)** - 将您的 WordPress 网站变成一个简单的 MCP 服务器，向 LLM 和 AI 代理公开功能。
- **[WordPress MCP Adapter](https://github.com/WordPress/mcp-adapter)** - 一个 MCP 适配器，将功能 API 桥接到模型上下文协议，使 MCP 客户端能够以编程方式发现和调用 WordPress 插件、主题和核心功能。
- **[Workflowy](https://github.com/danield137/mcp-workflowy)** - 与[workflowy](https://workflowy.com/)交互的服务器。
- **[World Bank data API](https://github.com/anshumax/world_bank_mcp_server)** - 获取世界银行提供的数据指标作为其数据 API 一部分的服务器
- **[Wren Engine](https://github.com/Canner/wren-engine)** - 模型上下文协议 (MCP) 客户端和 AI 代理的语义引擎
- **[X (Twitter)](https://github.com/EnesCinr/twitter-mcp)** (by EnesCinr) - 与 Twitter API 交互。发布推文并通过查询搜索推文。
- **[X (Twitter)](https://github.com/vidhupv/x-mcp)** (by vidhupv) - 直接通过 Claude 聊天创建、管理和发布 X/Twitter 帖子。
- **[Xcode](https://github.com/r-huijts/xcode-mcp-server)** - MCP 服务器将 AI 引入您的 Xcode 项目，实现智能代码辅助、文件操作、项目管理和自动化开发任务。
- **[Xcode-mcp-server](https://github.com/drewster99/xcode-mcp-server)** (by drewster99) - 最佳 Xcode 集成 - ClaudeCode 和 Cursor 可以*使用* Xcode 构建您的项目，并看到与您相同的错误。设置快速简单。
- **[xcodebuild](https://github.com/ShenghaiWang/xcodebuild)**  - 🍎 构建 iOS Xcode 工作区/项目并将错误反馈给 llm。
- **[Xero-mcp-server](https://github.com/john-zhang-dev/xero-mcp)** - 使客户能够与 Xero 系统交互，以简化会计、发票和业务运营。
- **[Xero-mcp-server](https://github.com/XeroAPI/xero-mcp-server)** - 使客户能够与 Xero 系统交互，以简化会计、发票和业务运营。
- **[XiYan](https://github.com/XGenerationLab/xiyan_mcp_server)** - 🗄️ 一个 MCP 服务器，支持使用自然语言查询从数据库中获取数据，由 XiyanSQL 作为文本到 SQL LLM 提供支持。
- **[XMind](https://github.com/apeyroux/mcp-xmind)** - 阅读并搜索包含 XMind 文件的 XMind 目录。
- **[Yahoo Finance](https://github.com/AgentX-ai/yahoo-finance-server)** - 📈 让您的 AI 与雅虎财经互动，获取全面的股市数据、新闻、财务等。支持代理。
- **[YetiBrowser MCP](https://github.com/yetidevworks/yetibrowser-mcp)** - 浏览器 MCP 工作流程的完全开源实现，具有出色的功能，例如优化的屏幕截图、dom 差异、控制台访问、多 Websocket 支持等。
- **[yfinance](https://github.com/Adity-star/mcp-yfinance-server)** -💹MCP YFinance 股票服务器以标准格式提供实时和历史股票数据，为仪表板、人工智能代理和研究工具提供无缝的金融见解。
- **[YNAB](https://github.com/ChuckBryan/ynabmcpserver)** - 模型上下文协议 (MCP) 服务器，用于与 YNAB（您需要预算）集成，允许 AI 助手安全地访问和分析您的财务数据。
- **[YouTrack](https://github.com/tonyzorin/youtrack-mcp)** - JetBrains YouTrack 的模型上下文协议 (MCP) 服务器实现，允许 AI 助手与 YouTrack 问题跟踪系统交互。
- **[YouTube](https://github.com/Klavis-AI/klavis/tree/main/mcp_servers/youtube)** - 提取 Youtube 视频信息（有代理支持）。
- **[YouTube](https://github.com/ZubeidHendricks/youtube-mcp-server)** - 全面的 YouTube API 集成，用于视频管理、Shorts 创建和分析。
- **[YouTube DLP](https://github.com/AgentX-ai/youtube-dlp-server)** - 使用代理检索视频信息、字幕和热门评论。
- **[YouTube MCP](https://github.com/aardeshir/youtube-mcp)** - 使用 OAuth2 从歌曲列表创建播放列表。搜索视频、管理播放列表，让 AI 管理您的 YouTube 收藏。
- **[Youtube Uploader MCP](https://github.com/anwerj/youtube-uploader-mcp)** - 由 AI 驱动的 YouTube 上传器 — 无需 CLI，无需 YouTube Studio。
- **[YouTube Video Summarizer](https://github.com/nabid-pf/youtube-video-summarizer-mcp)** - 总结冗长的 YouTube 视频。
- **[yutu](https://github.com/eat-pray-ai/yutu)** - 适用于 YouTube 的功能齐全的 MCP 服务器和 CLI，可实现 YouTube 操作自动化。
- **[ZapCap](https://github.com/bogdan01m/zapcap-mcp-server)** - ZapCap API 的 MCP 服务器通过自然语言提供视频字幕和 B-roll 生成
- **[Zettelkasten](https://github.com/joshylchen/zettelkasten)**- 实施 Zettelkasten 方法的综合人工智能知识管理系统。具有原子笔记创建、全文搜索、人工智能驱动的 CEQRC 工作流程（捕获→解释→问题→细化→连接）、智能链接发现和多界面访问（CLI、API、Web UI、MCP）。非常适合研究人员、学生和知识工作者。
- **[ZincBind](https://github.com/QuentinCody/zincbind-mcp-server)** - ZincBind 的非官方 MCP 服务器，提供对蛋白质中锌结合位点的综合数据库、结构协调数据和金属蛋白质组学研究信息的访问。
- **[Zoom](https://github.com/Prathamesh0901/zoom-mcp-server/tree/main)** - 创建、更新、读取和删除您的 Zoom 会议。
## 📚 框架

这些是更高层级的框架，可让构建 MCP 服务器或客户端变得更容易。

### 面向服务器

* **[Anubis MCP](https://github.com/zoedsoupe/anubis-mcp)** (Elixir) - Elixir 中的高性能和高级模型上下文协议 (MCP) 实现。像 MCP 的“实时视图”一样思考。
* **[ModelFetch](https://github.com/phuctm97/modelfetch/)** (TypeScript) - 与运行时无关的 SDK，用于在运行 TypeScript/JavaScript 的任何地方创建和部署 MCP 服务器
* **[EasyMCP](https://github.com/zcaceres/easy-mcp/)**（打字稿）
* **[FastAPI to MCP auto generator](https://github.com/tadata-org/fastapi_mcp)** – 一个零配置工具，用于通过 **[Tadata](https://tadata.com/)** 自动将 FastAPI 端点公开为 MCP 工具
* **[FastMCP](https://github.com/punkpeye/fastmcp)**（打字稿）
* **[Foobara MCP Connector](https://github.com/foobara/mcp-connector)** - 通过 MCP 轻松将用 Ruby 编写的 Foobara 命令公开为工具
* **[Foxy Contexts](https://github.com/strowk/foxy-contexts)** – 用于在 Golang 中构建 MCP 服务器的库 **[strowk](https://github.com/strowk)**
* **[Higress MCP Server Hosting](https://github.com/alibaba/higress/tree/main/plugins/wasm-go/mcp-servers)** - 通过使用 wasm 插件扩展 API 网关（基于 Envoy）来托管 MCP 服务器的解决方案。
* **[MCP Declarative Java SDK](https://github.com/codeboyzhou/mcp-declarative-java-sdk)** 使用Java进行注解驱动的MCP服务器开发，不需要Spring框架，尽可能减少依赖。
* **[MCP-Framework](https://mcp-framework.com)** 在 TypeScript 中优雅而快速地构建 MCP 服务器。附带 CLI，可使用 `mcp create app` 创建项目。 **[Alex Andru](https://github.com/QuantGeekDev)** 在 5 分钟内开始使用您的第一台服务器
* **[MCP Plexus](https://github.com/Super-I-Tech/mcp_plexus)**：一个安全、**多租户**和多用户 MCP python 服务器框架，旨在通过 OAuth 2.1 轻松与外部服务集成，为管理复杂的 AI 应用程序提供可扩展且强大的解决方案。
* **[mcp_sse (Elixir)](https://github.com/kEND/mcp_sse)** Elixir 中的 SSE 实现，用于快速创建 MCP 服务器。
* **[mxcp](https://github.com/raw-labs/mxcp)** (Python) - 用于仅使用 YAML、SQL 和 Python 构建企业级 MCP 服务器的开源框架，具有内置身份验证、监控、ETL 和策略执行功能。
* **[Next.js MCP Server Template](https://github.com/vercel-labs/mcp-for-next.js)** (Typescript) - Next.js 入门项目，使用 MCP 适配器允许 MCP 客户端连接和访问资源。
* **[PayMCP](https://github.com/blustAI/paymcp)** (Python & TypeScript) - MCP 服务器的轻量级支付层：使用两行装饰器将工具转变为付费端点。 [PyPI](https://pypi.org/project/paymcp/) · [npm](https://www.npmjs.com/package/paymcp) · [TS repo](https://github.com/blustAI/paymcp-ts)
* **[Perl SDK](https://github.com/mojolicious/mojo-mcp)** - 用于使用 Perl 编程语言构建 MCP 服务器和客户端的 SDK。
* **[Quarkus MCP Server SDK](https://github.com/quarkiverse/quarkus-mcp-server)** (Java)
- **[R mcptools](https://github.com/posit-dev/mcptools)** - R SDK，用于创建基于 R 的 MCP 服务器并从第三方 MCP 服务器检索功能作为 R 函数。
* **[SAP ABAP MCP Server SDK](https://github.com/abap-ai/mcp)** - 构建基于 SAP ABAP 的 MCP 服务器。 ABAP 7.52 基于 7.02 下行端口；在本地 R/3 和 S/4HANA 上运行，目前尚未支持云。
* **[Spring AI MCP Server](https://docs.spring.io/spring-ai/reference/api/mcp/mcp-server-boot-starter-docs.html)** - 提供自动配置以在 Spring Boot 应用程序中设置 MCP 服务器。
* **[Template MCP Server](https://github.com/mcpdotdirect/template-mcp-server)** - 用于创建新模型上下文协议服务器项目的 CLI 工具，具有 TypeScript 支持、双重传输选项和可扩展结构
* **[AgentR Universal MCP SDK](https://github.com/universal-mcp/universal-mcp)** - 一个 python SDK，用于通过 **[Agentr](https://agentr.dev/home)** 构建具有内置凭证管理的 MCP 服务器
* **[Vercel MCP Adapter](https://github.com/vercel/mcp-adapter)** (TypeScript) - 一个简单的包，用于在大多数主要 JS 元框架（包括 Next、Nuxt、Svelte 等）上开始为 MCP 服务器提供服务。
* **[PHP MCP Server](https://github.com/php-mcp/server)** (PHP) - 模型上下文协议 (MCP) 服务器的核心 PHP 实现

### 面向客户端

* **[codemirror-mcp](https://github.com/marimo-team/codemirror-mcp)** - CodeMirror 扩展，实现资源提及和提示命令的模型上下文协议 (MCP)
* **[llm-analysis-assistant](https://github.com/xuzexin-hz/llm-analysis-assistant)** <img height="12" width="12" src="https://raw.githubusercontent.com/xuzexin-hz/llm-analysis-assistant/refs/heads/main/src/llm_analysis_assistant/pages/html/imgs/favicon.ico" alt="Langfuse Logo" /> - 一个非常精简的mcp客户端，支持调用和监控stdio/sse/streamableHttp，还可以通过/logs页面查看请求响应。它还支持ollama/openai接口的监控和模拟。
* **[MCP-Agent](https://github.com/lastmile-ai/mcp-agent)** - 一个简单的、可组合的框架，用于使用 **[LastMile AI](https://www.lastmileai.dev)** 的模型上下文协议构建代理
* **[Spring AI MCP Client](https://docs.spring.io/spring-ai/reference/api/mcp/mcp-client-boot-starter-docs.html)** - 为 Spring Boot 应用程序中的 MCP 客户端功能提供自动配置。
* **[MCP CLI Client](https://github.com/vincent-pli/mcp-cli-host)** - CLI 主机应用程序，使大型语言模型 (LLM) 能够通过模型上下文协议 (MCP) 与外部工具交互。
* **[OpenMCP Client](https://github.com/LSTM-Kirigaya/openmcp-client/)** - 用于 MCP 服务器调试的一体化 vscode/trae/cursor 插件。 [Document](https://kirigaya.cn/openmcp/) 和 [OpenMCP SDK](https://kirigaya.cn/openmcp/sdk-tutorial/)。
* **[PHP MCP Client](https://github.com/php-mcp/client)** - 模型上下文协议 (MCP) 客户端的核心 PHP 实现
* **[Runbear](https://runbear.io/solutions/integrations/slack/mcp)** - 适用于团队聊天平台（例如 Slack、Microsoft Teams 和 Discord）的无代码 MCP 客户端。

## 📚 资源

有关 MCP 的补充资源。

- **[A2A-MCP Java Bridge](https://github.com/vishalmysore/a2ajava)** - A2AJava 将强大的 A2A-MCP 直接集成到您的 Java 应用程序中。它使开发人员能够注释标准 Java 方法并立即将它们公开为 MCP 服务器、A2A 可发现的操作 - 没有样板或服务注册开销。
- **[AiMCP](https://www.aimcp.info)** - MCP 客户端和服务器的集合，可通过 **[Hekmon](https://github.com/hekmon8)** 找到合适的 mcp 工具
- **[Awesome Crypto MCP Servers by badkk](https://github.com/badkk/awesome-crypto-mcp-servers)** - **[Luke Fan](https://github.com/badkk)** 精选的 MCP 服务器列表
- **[Awesome MCP Servers by appcypher](https://github.com/appcypher/awesome-mcp-servers)** - **[Stephen Akinyemi](https://github.com/appcypher)** 精选的 MCP 服务器列表
- **[Awesome MCP Servers by punkpeye](https://github.com/punkpeye/awesome-mcp-servers)** (**[website](https://glama.ai/mcp/servers)**) - **[Frank Fiegel](https://github.com/punkpeye)** 精选的 MCP 服务器列表
- **[Awesome MCP Servers by wong2](https://github.com/wong2/awesome-mcp-servers)** (**[website](https://mcpservers.org)**) - **[wong2](https://github.com/wong2)** 精选的 MCP 服务器列表
- **[Awesome Remote MCP Servers by JAW9C](https://github.com/jaw9c/awesome-remote-mcp-servers)** - **远程** MCP 服务器的精选列表，包括 **[JAW9C](https://github.com/jaw9c)** 的身份验证支持
- **[Discord Server](https://glama.ai/mcp/discord)** – **[Frank Fiegel](https://github.com/punkpeye)** 专用于 MCP 的社区不和谐服务器
- **[Install This MCP](https://installthismcp.com)** - 通过精美的安装指南减少安装摩擦
- <img height="12" width="12" src="assets/042-klavis-ai-b51f9599f6.png" alt="Klavis Logo" /> **[Klavis AI](https://www.klavis.ai)** - 开源 MCP 基础设施。在 Slack 和 Discord 上托管 MCP 服务器和 MCP 客户端。
- **[MCP Badges](https://github.com/mcpx-dev/mcp-badges)** – 通过 **[Ironben](https://github.com/nanbingxyz)** 使用清晰、引人注目的徽章快速突出显示您的 MCP 项目
- <img height="12" width="12" src="https://mcpproxy.app/favicon.svg" alt="MCPProxy Logo" /> **[MCPProxy](https://github.com/smart-mcp-proxy/mcpproxy-go)** - 开源本地应用程序，可通过 MCP 协议通过智能发现访问多个 MCP 服务器和数千种工具，在隔离环境中运行服务器，并具有针对恶意工具的自动隔离保护功能。
- **[MCPRepository.com](https://mcprepository.com/)** - 一个存储库，用于索引和组织所有 MCP 服务器以便于发现。
- **[mcp-cli](https://github.com/wong2/mcp-cli)** - **[wong2](https://github.com/wong2)** 的模型上下文协议的 CLI 检查器
- **[mcp-dockmaster](https://mcp-dockmaster.com)** - 用于安装和管理适用于 Windows、Linux 和 macOS 的 MCP 服务器的开源 UI。
- **[mcp-get](https://mcp-get.com)** - 用于通过 **[Michael Latman](https://github.com/michaellatman)** 安装和管理 MCP 服务器的命令行工具
- **[mcp-guardian](https://github.com/eqtylab/mcp-guardian)** - GUI 应用程序 + 用于通过 **[EQTY Lab](https://eqtylab.io)** 代理/管理 MCP 服务器控制的工具
- **[MCP Linker](https://github.com/milisp/mcp-linker)** - 跨平台 Tauri GUI 工具，用于一键设置和管理 MCP 服务器，支持 Claude Desktop、Cursor、Windsurf、VS Code、Cline 和 Neovim。
- **[mcp-manager](https://github.com/zueai/mcp-manager)** - 通过 **[Zue](https://github.com/zueai)** 为 Claude Desktop 安装和管理 MCP 服务器的简单 Web UI
- **[MCP Marketplace Web Plugin](https://github.com/AI-Agent-Hub/mcp-marketplace)** MCP Marketplace 是一个小型 Web UX 插件，可与 AI 应用程序集成，支持各种 MCP 服务器 API 端点（例如pulsemcp.com/deepnlp.org 等）。允许用户按不同类别浏览、分页和选择各种 MCP 服务器。 [Pypi](https://pypi.org/project/mcp-marketplace) | [Maintainer](https://github.com/AI-Agent-Hub) | [Website](http://www.deepnlp.org/store/ai-agent/mcp-server)
- **[mcp.natoma.ai](https://mcp.natoma.ai)** – 托管 MCP 平台，用于通过 **[Natoma Labs](https://www.natoma.ai)** 发现、安装、管理和部署 MCP 服务器
- **[mcp.run](https://mcp.run)** - 用于安装和运行安全+便携式 MCP 服务器的托管注册表和控制平面。
- **[MCPHub](https://www.mcphub.com)** - 列出高质量 MCP 服务器和真实用户评论的网站。还为流行的 LLM 模型提供在线聊天机器人，并支持 MCP 服务器。
- **[MCP Router](https://mcp-router.net)** – 免费的 Windows 和 macOS 应用程序，可简化 MCP 管理，同时通过 **[MCP Router](https://github.com/mcp-router/mcp-router)** 提供无缝应用程序身份验证和强大的日志可视化
- **[MCP Servers Hub](https://github.com/apappascs/mcp-servers-hub)** (**[website](https://mcp-servers-hub-website.pages.dev/)**) - **[apappascs](https://github.com/apappascs)** 精选的 MCP 服务器列表
- **[MCPServers.com](https://mcpservers.com)** - 不断增长的高质量 MCP 服务器目录，为各种 MCP 客户端提供清晰的设置指南。由 **[Highlight MCP client](https://highlightai.com/)** 背后的团队构建
- **[MCP Servers Rating and User Reviews](http://www.deepnlp.org/store/ai-agent/mcp-server)** - 对 MCP 服务器进行评级、撰写真实用户评论和 [search engine for agent & mcp](http://www.deepnlp.org/search/agent) 的网站
- **[MCP Sky](https://bsky.app/profile/brianell.in/feed/mcp)** - Bluesky 提供 MCP 相关新闻和讨论，作者：**[@brianell.in](https://bsky.app/profile/brianell.in)**
- **[MCP X Community](https://x.com/i/communities/1861891349609603310)** – **[Xiaoyi](https://x.com/chxy)** 的 MCP X 社区
- **[MCPHub](https://github.com/Jeamee/MCPHub-Desktop)** – 开源 macOS 和 Windows GUI 桌面应用程序，用于通过 **[Jeamee](https://github.com/jeamee)** 发现、安装和管理 MCP 服务器
- **[mcpm](https://github.com/pathintegral-institute/mcpm.sh)** ([website](https://mcpm.sh)) - MCP Manager (MCPM) 是一种类似于 Homebrew 的服务，用于通过 **[Pathintegral](https://github.com/pathintegral-institute)** 跨客户端管理模型上下文协议 (MCP) 服务器
- **[MCPVerse](https://mcpverse.dev)** - 用于创建和托管经过身份验证的 MCP 服务器并安全连接到它们的门户。
- **[MCP Servers Search](https://github.com/atonomus/mcp-servers-search)** - MCP 服务器提供用于从此列表中查询和发现可用 MCP 服务器的工具。
- **[Search MCP Server](https://github.com/krzysztofkucmierz/search-mcp-server)** - 通过搜索此 README 文件，根据客户端的查询推荐最相关的 MCP 服务器。
- **[MCPWatch](https://github.com/kapilduraphe/mcp-watch)** - 适用于模型上下文协议 (MCP) 服务器的全面安全扫描器，可检测 MCP 服务器实现中的漏洞和安全问题。
- <img height="12" width="12" src="https://mkinf.io/favicon-lilac.png" alt="mkinf Logo" /> **[mkinf](https://mkinf.io)** - 托管 MCP 服务器的开源注册表，用于加速 AI 代理工作流程。
- **[Open-Sourced MCP Servers Directory](https://github.com/chatmcp/mcp-directory)** - 一个精选列表，收录了 MCP servers by **[mcpso](https://mcp.so)**
- <img height="12" width="12" src="https://opentools.com/favicon.ico" alt="OpenTools Logo" /> **[OpenTools](https://opentools.com)** - 一个开放的注册表，用于通过 **[opentoolsteam](https://github.com/opentoolsteam)** 查找、安装和构建 MCP 服务器
- **[Programmatic MCP Prototype](https://github.com/domdomegg/programmatic-mcp-prototype)** - 实验代理原型演示了编程式 MCP 工具组合、渐进式工具发现、状态持久性以及通过 **[Adam Jones](https://github.com/domdomegg)** 执行 TypeScript 代码进行技能构建
- **[PulseMCP](https://www.pulsemcp.com)** ([API](https://www.pulsemcp.com/api)) - 社区中心和每周简讯，用于发现 **[Tadas Antanavicius](https://github.com/tadasant)**、**[Mike Coughlin](https://github.com/macoughl)** 和 **[Ravina Patel](https://github.com/ravinahp)** 的 MCP 服务器、客户端、文章和新闻
- **[r/mcp](https://www.reddit.com/r/mcp)** – 由 **[Frank Fiegel](https://github.com/punkpeye)** 致力于 MCP 的 Reddit 社区
- **[MCP.ing](https://mcp.ing/)** - MCP服务列表，用于发现社区中的MCP服务器，并通过**[iiiusky](https://github.com/iiiusky)**提供便捷的MCP服务搜索功能
- **[MCP Hunt](https://mcp-hunt.com)** - 通过势头跟踪、投票和社区讨论来发现趋势 MCP 服务器的实时平台 - 就像 Product Hunt 与 Reddit for MCP 的结合
- **[Smithery](https://smithery.ai/)** - MCP 服务器注册表，可通过 **[Henry Mao](https://github.com/calclavia)** 为您的 LLM 代理找到合适的工具
- **[Toolbase](https://gettoolbase.ai)** - 只需点击几下即可管理工具和 MCP 服务器的桌面应用程序 - **[gching](https://github.com/gching)** 无需编码
- **[ToolHive](https://github.com/StacklokLabs/toolhive)** - 一个轻量级实用程序，旨在简化 MCP 服务器的部署和管理，通过 **[StacklokLabs](https://github.com/StacklokLabs)** 的容器化确保易用性、一致性和安全性
- **[NetMind](https://www.netmind.ai/AIServices)** - 通过简单的 API 或 MCP 服务器访问强大的 AI 服务，以提高您的工作效率。
- **[Webrix MCP Gateway](https://github.com/webrix-ai/secure-mcp-gateway)** - 企业 MCP 网关具有 SSO、RBAC、审计跟踪和令牌库，可实现安全、集中的 AI 代理访问控制。通过本地或云中的 Helm 图表进行部署。 [webrix.ai](https://webrix.ai)

## 🚀 快速开始

### 使用此仓库中的 MCP 服务器
此仓库中基于 TypeScript 的服务器可直接通过 `npx` 使用。

例如，下面的命令会启动 [Memory](src/memory) 服务器：
```sh
npx -y @modelcontextprotocol/server-memory
```

此仓库中基于 Python 的服务器可直接通过 [`uvx`](https://docs.astral.sh/uv/concepts/tools/) 或 [`pip`](https://pypi.org/project/pip/) 使用。为了更便于使用和配置，推荐使用 `uvx`。

例如，下面的命令会启动 [Git](src/git) 服务器：
```sh
# 使用 uvx
uvx mcp-server-git

# 使用 pip
pip install mcp-server-git
python -m mcp_server_git
```

按照 [these](https://docs.astral.sh/uv/getting-started/installation/) 说明安装 `uv` / `uvx` 和 [these](https://pip.pypa.io/en/stable/installation/) 说明安装 `pip`。

### 使用 MCP 客户端
不过，单独运行一个服务器并不十分有用，更合理的做法是将其配置进一个 MCP 客户端。例如，下面是使用上述服务器的 Claude Desktop 配置：

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

将 Claude Desktop 作为 MCP 客户端使用的其他示例如下：

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/allowed/files"]
    },
    "git": {
      "command": "uvx",
      "args": ["mcp-server-git", "--repository", "path/to/git/repo"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://localhost/mydb"]
    }
  }
}
```

## 🛠️ 创建你自己的服务器

想创建你自己的 MCP 服务器？请访问 [modelcontextprotocol.io](https://modelcontextprotocol.io/introduction) 上的官方文档，获取有关实现 MCP 服务器的完整指南、最佳实践和技术细节。

## 🤝 贡献

有关向此仓库贡献内容的信息，请参阅 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 🔒 安全

有关报告安全漏洞的信息，请参阅 [SECURITY.md](SECURITY.md)。

## 📜 许可证

本项目对新的贡献采用 Apache License, Version 2.0 许可，现有代码采用 MIT 许可，详情请参阅 [LICENSE](LICENSE) 文件。

## 💬 社区

- [GitHub Discussions](https://github.com/orgs/modelcontextprotocol/discussions)

## ⭐ 支持

如果你觉得 MCP servers 有帮助，请考虑为仓库点个 Star，并贡献新的服务器或改进！

---

由 Anthropic 维护，但与社区共同构建。Model Context Protocol 是开源的，我们鼓励所有人贡献自己的服务器和改进！
