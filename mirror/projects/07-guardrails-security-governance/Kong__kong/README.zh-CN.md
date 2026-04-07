[![][kong-logo]][kong-url]

![Stars](https://img.shields.io/github/stars/Kong/kong?style=flat-square) ![GitHub commit activity](https://img.shields.io/docker/pulls/_/kong?style=flat-square) [![Build Status][badge-action-image]][badge-action-url] ![Version](https://img.shields.io/github/v/release/Kong/kong?color=green&label=Version&style=flat-square)  ![License](https://img.shields.io/badge/License-Apache%202.0-blue?style=flat-square) [![Twitter Follow](https://img.shields.io/twitter/follow/thekonginc?style=social)](https://x.com/thekonginc)

Kong 或 Kong Gateway 是一款云原生、平台无关、可扩展的 **API 𖧹 LLM 𖧹 MCP** 网关，以其高性能和通过插件实现的扩展性而著称。它还提供高级 AI 流量能力，包括多 LLM 支持、语义安全、MCP 流量安全与分析等。

通过提供代理、路由、负载均衡、健康检查、认证（以及[更多功能](#功能特性)），Kong 可作为编排微服务或传统 API 流量的中心层，也能轻松编排智能体式 LLM 和 MCP 流量，实现统一管理。

得益于官方的 [Kubernetes Ingress Controller](https://github.com/Kong/kubernetes-ingress-controller)，Kong 可以原生运行在 Kubernetes 上。

<br />

[![][kong-diagram]][kong-url]

---

[安装](https://konghq.com/install/#kong-community) | [文档](https://docs.konghq.com) | [讨论](https://github.com/Kong/kong/discussions) | [论坛](https://discuss.konghq.com) | [博客](https://konghq.com/blog) | [构建版本][kong-master-builds] | [AI Gateway](https://konghq.com/products/kong-ai-gateway) | [云端托管 Kong](https://konghq.com/kong-konnect/)

---

## 快速入门

如果你希望使用云端托管的 Kong，可以[注册 Kong Konnect 免费试用](https://konghq.com/products/kong-konnect/register?utm_medium=Referral&utm_source=Github&utm_campaign=kong-gateway&utm_content=konnect-promo-in-gateway&utm_term=get-started)，几分钟内即可开始使用。否则，你可以按照以下说明在你自己的基础设施上开始使用 Kong。

让我们在 5 分钟内为 API 添加认证，快速体验 Kong。

我们建议通过以下说明使用 docker-compose 发行版，但如果你更愿意在无数据库模式下运行 Kong Gateway，也有 [Docker 安装](https://docs.konghq.com/gateway/latest/install/docker/#install-kong-gateway-in-db-less-mode)步骤可供参考。

无论你是在云端、裸金属服务器上运行，还是使用容器，都可以在我们的[官方安装](https://konghq.com/install/#kong-community)页面找到所有受支持的发行版。

1) 首先，克隆 Docker 仓库并进入 compose 目录。
```cmd
  $ git clone https://github.com/Kong/docker-kong
  $ cd docker-kong/compose/
```

2) 使用以下命令启动 Gateway 套件：
```cmd
  $ KONG_DATABASE=postgres docker-compose --profile database up
```

Gateway 现在可通过 localhost 的以下端口访问：

- `:8000` - 通过 Kong 将流量发送到你的服务
- `:8001` - 使用 Admin API 或通过 [decK](https://github.com/kong/deck) 配置 Kong
- `:8002` - 在 [localhost:8002](http://localhost:8002) 访问 Kong 的管理 Web UI（[Kong Manager](https://github.com/Kong/kong-manager)）

接下来，按照[快速入门指南](https://docs.konghq.com/gateway-oss/latest/getting-started/configuring-a-service/)浏览 Gateway 功能。

### AI Gateway for LLM 和 MCP 快速入门

如果你想开始使用 Kong AI Gateway 的 LLM 和 MCP 功能，请参阅[官方 AI 文档](https://developer.konghq.com/ai-gateway/)。

## 功能特性

通过在组织所有服务中集中管理通用的 API、AI 和 MCP 功能，Kong Gateway 让工程团队能够更自由地专注于最重要的挑战。

Kong 的核心功能包括：

- 高级路由、负载均衡、健康检查——全部可通过 RESTful Admin API 或声明式配置进行管理。
- 使用 JWT、基本认证、OAuth、ACL 等多种方式为 API 提供认证和授权。
- 通用 LLM API，支持跨多个提供商路由，包括 OpenAI、Anthropic、GCP Gemini、AWS Bedrock、Azure AI、Databricks、Mistral、Huggingface 等。
- MCP 流量治理、MCP 安全和 MCP 可观测性，此外还支持从任意 RESTful API 自动生成 MCP。
- 60 多项 AI 功能，包括 AI 可观测性、语义安全与缓存、语义路由等。
- L4 或 L7 流量的代理、SSL/TLS 终止和连接支持。
- 用于执行流量控制、速率限制、请求/响应转换、日志记录、监控的插件，以及插件开发者中心。
- 成熟的部署模式，如声明式无数据库部署和混合部署（控制面/数据面分离），不锁定任何供应商。
- 原生支持 [Ingress Controller](https://github.com/Kong/kubernetes-ingress-controller)，用于服务 Kubernetes。

[![][kong-benefits]][kong-url]

### 插件中心

插件提供扩展 Gateway 用途的高级功能。许多由 Kong Inc. 和社区开发的插件（如 AWS Lambda、Correlation ID 和 Response Transformer）展示在[插件中心](https://docs.konghq.com/hub/)。

欢迎向插件中心贡献，确保你的下一个创新想法得以发布并惠及更广泛的社区！

## 参与贡献

我们 ❤️ Pull Request，我们一直在不断努力让开发者尽可能轻松地参与贡献。在开始 Kong Gateway 开发之前，请先熟悉以下开发者资源：

- 社区承诺（[COMMUNITY_PLEDGE.md](COMMUNITY_PLEDGE.md)）——我们与开源社区互动的承诺。
- 贡献指南（[CONTRIBUTING.md](CONTRIBUTING.md)）——了解如何为 Kong 贡献。
- 开发指南（[DEVELOPER.md](DEVELOPER.md)）：设置你的开发环境。
- [行为准则](CODE_OF_CONDUCT.md)和[版权声明](COPYRIGHT)

使用[插件开发指南](https://docs.konghq.com/latest/plugin-development/)来构建新颖的插件，或在[插件开发套件 (PDK) 参考](https://docs.konghq.com/latest/pdk/)中浏览 Kong 源代码文档的在线版本。开发者可以使用 [Lua](https://docs.konghq.com/gateway/latest/plugin-development/)、[Go](https://docs.konghq.com/gateway-oss/latest/external-plugins/#developing-go-plugins) 或 [JavaScript](https://docs.konghq.com/gateway-oss/latest/external-plugins/#developing-javascript-plugins) 构建插件。

## 版本发布

有关特定版本的详细信息，请参阅[更新日志](CHANGELOG.md)。Gateway 版本号遵循 [SemVer 语义化版本规范](https://semver.org)。

## 加入社区

- 查阅[文档](https://docs.konghq.com/)
- 加入 [Kong 讨论区](https://github.com/Kong/kong/discussions)
- 在 Kong Nation 论坛参与讨论：[https://discuss.konghq.com/](https://discuss.konghq.com/)
- 加入我们的[社区 Slack](http://kongcommunity.slack.com/)
- 在我们的[博客](https://konghq.com/blog/)了解最新动态
- 在 [X](https://x.com/thekonginc) 上关注我们
- 订阅我们的 [YouTube 频道](https://www.youtube.com/c/KongInc/videos)
- 访问我们的[主页](https://konghq.com/)了解更多

## Konnect Cloud

Kong Inc. 提供商业订阅服务，从多个方面增强 Kong Gateway 的能力。Kong [Konnect Cloud](https://konghq.com/kong-konnect/) 订阅客户可享受额外的网关功能、商业支持以及访问 Kong 托管的 (SaaS) 控制面平台。Konnect Cloud 平台功能包括实时分析、服务目录、开发者门户等等！[立即开始](https://konghq.com/products/kong-konnect/register?utm_medium=Referral&utm_source=Github&utm_campaign=kong-gateway&utm_content=konnect-promo-in-gateway&utm_term=get-started)使用 Konnect Cloud。

## 许可证

```
Copyright 2016-2026 Kong Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

[kong-url]: assets/001-asset-2b91b4ebea.html
[kong-logo]: https://konghq.com/wp-content/uploads/2018/05/kong-logo-github-readme.png
[kong-diagram]: assets/002-68cc1bfd-kong-diagram-2b9053a2a5.png
[kong-benefits]: https://konghq.com/wp-content/uploads/2018/05/kong-benefits-github-readme.png
[kong-master-builds]: assets/003-tags-12ce73da5c.html
[badge-action-url]: assets/004-actions-8c04e80830.html
[badge-action-image]: https://github.com/Kong/kong/actions/workflows/build_and_test.yml/badge.svg?branch=master&event=push

[busted]: assets/005-busted-5437c23218.html
[luacheck]: assets/006-luacheck-d539705771.html
