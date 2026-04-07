![Context Space](https://r2.context.space/resources/20250724-235344_1753372441182.jpg)

<div align="center">

### Context Space：首个上下文工程基础设施，让你的生产力提升 10 倍

     
[![License](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](LICENSE)
[![Go Version](https://img.shields.io/badge/go-1.24-blue.svg)](https://golang.org/dl/)
[![Docker](https://img.shields.io/badge/docker-supported-blue.svg)](https://docker.com)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()
[![API Docs](https://img.shields.io/badge/API-documented-green.svg)](http://api.context.space/v1/docs)
[![Contributors](https://img.shields.io/badge/contributors-welcome-orange.svg)]()

English | [中文](docs/README.zh-CN.md)

</div>

**Context Space** 提供统一的 MCP 工具、安全且经过验证的集成，以及 5 分钟快速设置 —— 非常适合 AI 代理、自动化工作流和开发者工具。作为**首个上下文工程基础设施**，它将理论转化为实践，通过提供更好的上下文来使代理能够有效地与现实世界交互。

## 我们的愿景

当今的 AI 代理擅长推理，但在现实世界中行动的能力很差。它们与实时数据和工具隔绝，被分散的 API、不一致的数据源和复杂的身份验证所束缚。

Context Space 改变了这一切。它将任务编排和记忆等核心代理能力打包成标准化的、可调用的工具。通过内置的工具发现和推荐功能，它为代理提供了一条清晰、可控、可解释的调用现实世界上下文的路径。

Context Space 让 AI 代理真正可用。通过将企业级安全与零配置简易性相结合，我们正在构建工具优先的上下文工程基础设施，使代理能够无缝、安全地与任何服务或数据源交互。

## 用 Context Space 开启上下文工程

上下文工程是构建可靠 AI 代理的基础。它超越了提示词工程，不仅管理用户对模型说的话，还管理塑造模型行为的更广泛上下文，如工具、记忆和数据。

MCP 定义了代理安全访问现实世界服务的标准路径。Context Space 通过将 MCP 转化为生产就绪的基础设施来实现这一愿景。

如今，Context Space 提供了带有持久化凭证管理的安全集成层。在 MCP 原则的指导下，它正在演变为面向下一代 AI 的完整上下文工程平台。

## 🚀 一键 AI 集成

**几秒钟内**将你的 AI 助手变为强大的代理。

**Cursor IDE** - 通过 `cursor://` 深度链接一键安装。点击"Add to Cursor"即可立即让 Claude 访问 GitHub、Slack、Notion 等 38+ 服务，无需编辑任何 JSON 文件。

**Claude Code** - 简单的 CLI 集成：
```bash
claude mcp add "context-space" https://api.context.space/api/mcp --header "Authorization: Bearer YOUR_API_KEY"
```

### 实时演示

#### 1️⃣ OAuth 流程演示
*简单的 OAuth 设置 —— 不再需要编辑配置文件*

![OAuth Demo](https://r2.context.space/resources/readme-demo-oauth-flow-github-v2.gif)

#### 2️⃣ Star 一个 GitHub 仓库
*GitHub 集成 —— 用自然语言给仓库点星*

![GitHub Star Demo](https://r2.context.space/resources/readme-demo-github-star-repo.gif)

#### 3️⃣ 网页搜索
*实时网页搜索 —— 即时获取最新信息*

![Web Search Demo](https://r2.context.space/resources/readme-demo-web-search.gif)

**在线体验**：[https://context.space/integrations](https://context.space/integrations)

---

## 路线图：从基础到前沿

我们的开发按清晰的阶段推进，从当前可用的稳健生产基础演进到明天的智能上下文引擎。

### 1️⃣ 第一阶段：生产就绪基础（现已可用）
初始阶段解决了在生产环境中使用上下文协议的最关键挑战，提供稳定、安全、可扩展的基础设施。

| 生产环境挑战 | Context Space 的解决方案 |
| :----- | :----- |
| 手动、不安全的凭证处理 | **一键 OAuth 与保险库安全：**<br>通过安全 OAuth 流程连接 14+ 服务，由 HashiCorp Vault 提供企业级凭证管理。 |
| 不一致且复杂的 API | **单一统一的 RESTful API：**<br>通过一个简洁、一致、可靠的 API 与所有服务交互，使用体验出色。 |
| 复杂的部署和分散的 MCP 服务器 | **带工具聚合的统一上下文平面：**<br>连接一次，访问一切。从单个 MCP 服务器端点管理所有能力。 |

### 2️⃣ 第二阶段：智能上下文层（开发中）

在此基础之上，我们未来的工作重点是实现更高级的 AI 能力。

**路线图时间线：**

| 时间线 | 关键特性 | MCP 集成 |
|----------|--------------|------------------|
| 未来 6 个月 | 原生 MCP 支持、上下文记忆、智能聚合 | 完整 MCP 协议兼容 |
| 6-12 个月 | 语义检索、上下文优化、实时更新 | 增强的 MCP 工具能力 |
| 12 个月以上 | 上下文合成、预测性加载、AI 上下文推理 | 高级 MCP 生态系统功能 |

---

## 支持的服务与上下文源

### 生产就绪的集成

| 服务 | 类别 | 认证 | 上下文能力 | 状态 |
|---------|----------|------|---------------------|--------|
| **GitHub** | 开发 | OAuth | 代码仓库、Issues、PR、提交历史 | 就绪 |
| **Slack** | 通讯 | OAuth | 团队对话、频道、工作流 | 就绪 |
| **Airtable** | 数据管理 | OAuth | 结构化业务数据、CRM 记录 | 就绪 |
| **HubSpot** | CRM | OAuth | 客户数据、销售管道、交互 | 就绪 |
| **Notion** | 知识 | OAuth | 文档、项目计划、知识库 | 就绪 |
| **Spotify** | 个人 | OAuth | 音乐偏好、收听模式 | 就绪 |
| **Stripe** | 金融 | API Key | 支付数据、客户行为 | 就绪 |
| **更多...** | 多种 | 多种 | 5+ 额外集成 | 就绪 |

**✅ 14+ 集成立即可用 • 每周持续增加**

**[查看所有集成 →](https://context.space/integrations)**

---

## 📖 API 文档

### 快速 API 示例

#### 🔐 认证
```bash
curl -H "Authorization: Bearer <jwt-token>" \
     https://api.context.space/v1/users/me
```

#### 🔗 创建 OAuth 授权 URL
```bash
curl -H "Authorization: Bearer <jwt-token>" \
     -X POST \
     https://api.context.space/v1/credentials/auth/oauth/github/auth-url
```

#### ⚡ 执行操作
```bash
curl -H "Authorization: Bearer <jwt-token>" \
     -X POST \
     https://api.context.space/v1/invocations/github/list_repositories
```

**完整 API 文档**：http://api.context.space/v1/docs

---

## 贡献

**诚邀你来帮助塑造上下文工程的未来。**

[![Contributors](assets/001-contributors-32d34efcd4.svg)](https://github.com/context-space/context-space/graphs/contributors)

### 快速贡献指南

1. **签署 [CLA](CLA.md)**：在你的第一个 PR 中评论"I have read the CLA Document and I hereby sign the CLA"
2. **Fork 并创建分支**：`git checkout -b feat/amazing-feature`
3. **遵循标准**：使用 `make lint` 并包含测试
4. **提交 PR**：附带清晰的描述

**完整贡献指南**：[CONTRIBUTING.md](CONTRIBUTING.md)

### 适合新手的 Issue

| 类型 | 难度 | 示例 |
|------|------------|----------|
| **Bug 修复** | 简单 | 修复 API 响应格式 |
| **文档** | 简单 | 改进 API 示例 |
| **新集成** | 中等 | 添加 Discord/Twitter 支持 |
| **上下文特性** | 困难 | 实现语义搜索 |

**[查看所有 Issue →](https://github.com/context-space/context-space/issues)**

---

## 许可证

### 当前许可证：AGPL v3 → Apache 2.0 过渡

**为什么采用这种方式？**
- **现在**：AGPL v3 在我们的创业阶段提供保护
- **未来**：Apache 2.0 过渡（随着社区增长）以实现最大采用
- **CLA**：贡献者签署我们的 CLA 以支持这一过渡

| 利益相关者 | 现在 | 未来 |
|-------------|-------|----------|
| **👥 用户** | 免费生产访问 | 更广泛的生态系统兼容性 |
| **👨‍💻 贡献者** | 免受剥削 | 最大社区覆盖 |

---

## 社区与支持

Context Space 是一个社区驱动的项目。我们相信最好的基础设施是在开放环境中构建的，来自世界各地的开发者贡献他们的想法和专业知识。每一份贡献，无论大小，都帮助我们推动可能性的边界。

### 加入我们不断增长的社区

[![Twitter](https://img.shields.io/twitter/follow/hi_contextspace?style=social)](https://twitter.com/hi_contextspace)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-5865F2?logo=discord&logoColor=white)](https://discord.gg/BsNjUyxQYF)

### 资源

- **[API 文档](https://api.context.space/v1/docs)** - 完整 API 参考
- **[Discord 社区](https://discord.gg/BsNjUyxQYF)** - 实时聊天和协作
- **[GitHub Discussions](https://github.com/context-space/context-space/discussions)** - 社区问答
- **[Issues](https://github.com/context-space/context-space/issues)** - Bug 报告和功能请求

---

<div align="center">

**🌟 给项目点星并分享**

给仓库点星可以增加我们的可见度，帮助其他开发者发现这个项目。如果你喜欢 Context Space，不要犹豫，在 Twitter、Reddit 上分享，或推荐给你的同事。

[![GitHub stars](https://img.shields.io/github/stars/context-space/context-space?style=social)](https://github.com/context-space/context-space)
[![GitHub forks](https://img.shields.io/github/forks/context-space/context-space?style=social)](https://github.com/context-space/context-space)

</div>
