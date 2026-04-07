<a name="readme-top"></a>

<div align="center">
  <img src="assets/002-logo-0172f76209.png" alt="Logo" width="200">
  <h1 align="center" style="border-bottom: none">OpenHands：AI 驱动的开发</h1>
</div>

<div align="center">
  <a href="https://github.com/OpenHands/OpenHands/blob/main/LICENSE"><img src="https://img.shields.io/badge/LICENSE-MIT-20B2AA?style=for-the-badge" alt="MIT License"></a>
  <a href="https://docs.google.com/spreadsheets/d/1wOUdFCMyY6Nt0AIqF705KN4JKOWgeI4wUGUP60krXXs/edit?gid=811504672#gid=811504672"><img src="https://img.shields.io/badge/SWEBench-77.6-00cc00?logoColor=FFE165&style=for-the-badge" alt="Benchmark Score"></a>
  <br/>
  <a href="https://docs.openhands.dev/sdk"><img src="https://img.shields.io/badge/Documentation-000?logo=googledocs&logoColor=FFE165&style=for-the-badge" alt="Check out the documentation"></a>
  <a href="https://arxiv.org/abs/2511.03690"><img src="https://img.shields.io/badge/Paper-000?logoColor=FFE165&logo=arxiv&style=for-the-badge" alt="Tech Report"></a>

  <!-- Keep these links. Translations will automatically update with the README. -->
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=de">Deutsch</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=es">Español</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=fr">français</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=ja">日本語</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=ko">한국어</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=pt">Português</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=ru">Русский</a> |
  <a href="https://www.readme-i18n.com/OpenHands/OpenHands?lang=zh">中文</a>
</div>

<hr>

🙌 欢迎来到 OpenHands，这是一个专注于 AI 驱动开发的[社区](COMMUNITY.md)。欢迎[加入我们的 Slack](https://dub.sh/openhands)。

你可以通过以下几种方式使用 OpenHands：

### OpenHands 软件 Agent SDK
该 SDK 是一个可组合的 Python 库，包含我们全部的智能体技术。它是驱动下方所有其他内容的引擎。

在代码中定义代理，然后在本地运行，或扩展到云端的数千个代理。

[查看文档](https://docs.openhands.dev/sdk) 或 [查看源码](https://github.com/OpenHands/software-agent-sdk/)

### OpenHands CLI
CLI 是开始使用 OpenHands 最简单的方式。对于使用过 Claude Code 或 Codex 等工具的人来说，体验会非常熟悉。你可以使用 Claude、GPT 或任何其他 LLM 来驱动它。

[查看文档](https://docs.openhands.dev/openhands/usage/run-openhands/cli-mode) 或 [查看源码](https://github.com/OpenHands/OpenHands-CLI)

### OpenHands 本地 GUI
使用本地 GUI 在笔记本电脑上运行智能体。它附带 REST API 和单页 React 应用。对于使用过 Devin 或 Jules 的人来说，这种体验会很熟悉。

[查看文档](https://docs.openhands.dev/openhands/usage/run-openhands/local-setup) 或在本仓库中查看源码。

### OpenHands Cloud
这是部署在托管基础设施上的 OpenHands GUI。

你可以通过 [GitHub 或 GitLab 账号登录](https://app.all-hands.dev)，使用 Minimax 模型免费试用。

OpenHands Cloud 提供源码可见的功能和集成：
- Slack、Jira 和 Linear 集成
- 多用户支持
- RBAC 和权限管理
- 协作功能（例如对话共享）

### OpenHands Enterprise
大型企业可以与我们合作，通过 Kubernetes 在自己的 VPC 中自行部署 OpenHands Cloud。
OpenHands Enterprise 也可以与上述 CLI 和 SDK 配合使用。

OpenHands Enterprise 采用源码可见模式，你可以在 `enterprise/` 目录中查看所有源代码；但如果你想运行超过一个月，则需要购买许可证。

企业合同还包含延长支持服务，以及与我们研究团队合作的权限。

了解更多信息请访问 [openhands.dev/enterprise](https://openhands.dev/enterprise)

### 其他内容

请查看我们的 [产品路线图](https://github.com/orgs/openhands/projects/1)，如果有你希望看到的内容，也欢迎[提交 issue](https://github.com/OpenHands/OpenHands/issues)！

你可能也会对我们的 [评测基础设施](https://github.com/OpenHands/benchmarks)、[Chrome 扩展](https://github.com/OpenHands/openhands-chrome-extension/) 或 [心智理论模块](https://github.com/OpenHands/ToM-SWE) 感兴趣。

除本仓库中的 `enterprise/` 目录外，我们所有的工作成果均采用 MIT 许可证发布（详见[企业许可证](enterprise/LICENSE)）。
核心的 `openhands` 和 `agent-server` Docker 镜像也完全采用 MIT 许可证。

如果你需要任何帮助，或者只是想聊天，欢迎[来 Slack 找我们](https://dub.sh/openhands)。

<hr>

### 感谢我们的贡献者

<div align="center">

[![OpenHands Contributors](assets/001-openhands-contributors-70e1e4b38a.svg)](https://github.com/OpenHands/OpenHands/graphs/contributors)

</div>

<hr>

### 受到以下公司工程师的信赖

<div align="center">
  <br/><br/>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/015-tiktok-367f0891f7.svg">
    <img src="assets/003-tiktok-39aa9c2179.svg" alt="TikTok" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/016-vmware-07a5f2592b.svg">
    <img src="assets/004-vmware-3a1d5e2b83.svg" alt="VMware" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/017-roche-f75621d28c.svg">
    <img src="assets/005-roche-948de5bd23.svg" alt="Roche" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/018-amazon-98733729be.svg">
    <img src="assets/006-amazon-7c97b87d12.svg" alt="Amazon" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/019-c3-ai-af0f07123d.svg">
    <img src="assets/007-c3-ai-1cca10123d.svg" alt="C3 AI" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/020-netflix-d115736be3.svg">
    <img src="assets/008-netflix-5878dd8b38.svg" alt="Netflix" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/021-mastercard-dde924d53d.svg">
    <img src="assets/009-mastercard-9fd9a94a18.svg" alt="Mastercard" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/022-red-hat-8918d393ef.svg">
    <img src="assets/010-red-hat-742caff0d2.svg" alt="Red Hat" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/023-mongodb-1a082ec22c.svg">
    <img src="assets/011-mongodb-18c73e4c2d.svg" alt="MongoDB" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/024-apple-111052cb38.svg">
    <img src="assets/012-apple-7841783f66.svg" alt="Apple" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/025-nvidia-10c520ed18.svg">
    <img src="assets/013-nvidia-b0a26dd37d.svg" alt="NVIDIA" height="17" hspace="5">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/026-google-ee8fc9fd55.svg">
    <img src="assets/014-google-4eb71fe823.svg" alt="Google" height="17" hspace="5">
  </picture>
</div>

</div>
