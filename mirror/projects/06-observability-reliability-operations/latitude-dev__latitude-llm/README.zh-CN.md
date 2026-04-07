<h1 align="center" style="border: none; margin-bottom: 8px;">
  开源 AI 工程平台
</h1>

<p align="center">
  先做可观测性和评估，然后通过评估驱动的可靠性循环持续改进提示词。
</p>

<p align="center">
  <a href="https://docs.latitude.so" rel="dofollow">Docs</a>&nbsp;&nbsp;·&nbsp;&nbsp;
  <a href="https://join.slack.com/t/trylatitude/shared_invite/zt-35wu2h9es-N419qlptPMhyOeIpj3vjzw">Slack</a>&nbsp;&nbsp;·&nbsp;&nbsp;
  <a href="https://x.com/trylatitude">X</a>
</p>

> [!WARNING]
> 你正在查看 **Latitude v2 Alpha** 分支（`main`）。此分支处于**活跃开发中**，**尚未准备好用于生产**。API、功能和数据格式可能会随时更改。
>
> 生产使用请使用 [`latitude-v1`](https://github.com/latitude-dev/latitude-llm/tree/latitude-v1) 分支上的稳定版本。

<p align="center">
  <img src="docs/assets/readme/gif_ui.gif?raw=true" alt="Latitude demo — observability, evals, and prompt management" width="800"/>
</p>

## 🌈 为什么选择 Latitude？

Latitude 是一个用于在生产环境中构建和运行 LLM 功能的开源平台。

大多数团队分阶段采用 Latitude：首先对现有的 LLM 调用进行埋点以获取可观测性和评估覆盖，然后进入一个可靠性循环，将生产故障转化为可复现的修复。

**从可观测性 + 评估开始：**

- **可观测性** → 捕获提示词、输入/输出、工具调用，以及来自真实流量的延迟/Token 用量/成本
- **提示词 Playground** → 复现运行、使用真实输入迭代、版本管理变更，并发布到 AI Gateway
- **数据集** → 策划真实样本用于批量测试和回归测试套件
- **评估** → 内置评估、LLM-as-judge 和人工评分
- **实验** → 比较模型/提供商和提示词版本，获取可量化的结果

**逐步进入可靠性循环：**

- **标注** → 将人工判断转化为可跟踪和优化的信号
- **问题发现** → 将故障聚类为反复出现的问题和故障模式
- **自动评估** → 将问题转化为保护发布的持续测试
- **提示词优化器 (GEPA)** → 在你的评估套件中搜索提示词变体，减少反复出现的故障

Latitude Telemetry 开箱即支持大多数模型提供商和框架，并可扩展以实现自定义集成。查看[完整集成列表](https://docs.latitude.so/guides/getting-started/quick-start-dev)（包括 OTLP 数据摄取）。

## 📚 目录

- [快速开始](https://docs.latitude.so/guides/getting-started/introduction)
- [评估](https://docs.latitude.so/guides/evaluations/overview)
- [数据集与测试](https://docs.latitude.so/guides/datasets/overview)
- [提示词管理器](https://docs.latitude.so/guides/prompt-manager/overview)
- [自定义 AI 代理](https://docs.latitude.so/guides/prompt-manager/agents)
- [集成与部署](https://docs.latitude.so/guides/integration/publishing-deployment)
- [自托管](https://docs.latitude.so/guides/self-hosted/production-setup)
- [进阶：PromptL](https://docs.latitude.so/promptl/getting-started/introduction)
- [贡献](#-贡献)
- [许可证](#-许可证)

## ⚡ 快速开始

Latitude 提供托管云产品和自托管部署两种方式：

1. **Latitude Cloud**：完全托管。
2. **Latitude Self-Hosted**：在你自己的基础设施上运行开源发行版。

选择最适合你需求的方案，按照下方相应说明操作。

### Latitude Cloud

开始使用 Latitude，请按照以下步骤操作：

1. **注册** → 在 [latitude.so](https://latitude.so) 创建账户并创建项目。
2. **埋点** → 添加遥测 SDK（推荐）或将 OTLP 追踪导出到兼容的后端。
3. **评估** → 创建数据集和评估来衡量质量并捕获回归问题。
4. **管理 + 发布** → 对提示词/代理进行版本管理，发布变更，并通过 Gateway 部署。
5. **优化** → 使用评估驱动的优化来减少反复出现的故障。

关于每个步骤的更多详情，请参阅我们的[文档](https://docs.latitude.so)或加入[社区](https://join.slack.com/t/trylatitude/shared_invite/zt-35wu2h9es-N419qlptPMhyOeIpj3vjzw)。

### Latitude Self-Hosted

按照[自托管指南](https://docs.latitude.so/guides/self-hosted/production-setup)中的说明开始使用 Latitude Self-Hosted。

设置好 Latitude Self-Hosted 后，你可以按照与 Latitude Cloud 指南相同的步骤来创建、测试、评估和部署你的提示词。

## 👥 社区

Latitude 社区在
[Slack](https://join.slack.com/t/trylatitude/shared_invite/zt-3cl2m3xph-k5DBp3sJOtt_u6u3vxzZ0g) 上，你可以在那里提问、分享反馈和展示你正在构建的内容。

## 🤝 贡献

欢迎贡献。关于仓库及其架构的概述，请参阅
[贡献者指南](https://docs.latitude.so/guides/contribution/contributors)。

如果你想提供帮助，请加入 [Slack 社区](https://join.slack.com/t/trylatitude/shared_invite/zt-35wu2h9es-N419qlptPMhyOeIpj3vjzw)，创建一个
[issue](https://github.com/latitude-dev/latitude-llm/issues/new)，或提交 pull request。

## 📄 许可证

Latitude 使用 [LGPL-3.0](LICENSE) 许可证授权。

另外，我们为需要更宽松许可的用户提供商业许可证。请联系 [licensing@latitude.so](mailto:licensing@latitude.so) 了解更多信息。

## 🔗 链接

- [主页](https://latitude.so?utm_campaign=github-readme)
- [文档](https://docs.latitude.so/)
- [Slack 社区](https://join.slack.com/t/trylatitude/shared_invite/zt-35wu2h9es-N419qlptPMhyOeIpj3vjzw)
- [X / Twitter](https://x.com/trylatitude)

由 Latitude 团队用心打造
