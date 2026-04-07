<p align="center">
<a href="https://www.traceloop.com/openllmetry#gh-light-mode-only">
<img width="600" src="assets/001-logo-light-99c7dfcc93.png">
</a>
<a href="https://www.traceloop.com/openllmetry#gh-dark-mode-only">
<img width="600" src="assets/002-logo-dark-8fa401ddf8.png">
</a>
</p>
<p align="center">
  <p align="center">面向你的 LLM 应用的开源可观测性方案</p>
</p>
<h4 align="center">
    <a href="https://traceloop.com/docs/openllmetry/getting-started-python"><strong>快速开始 »</strong></a>
    <br />
    <br />
  <a href="https://traceloop.com/slack">Slack</a> |
  <a href="https://traceloop.com/docs/openllmetry/introduction">文档</a> |
  <a href="https://www.traceloop.com/openllmetry">网站</a>
</h4>

<h4 align="center">
  <a href="https://github.com/traceloop/openllmetry/releases">
    <img src="https://img.shields.io/github/release/traceloop/openllmetry">
  </a>
  <a href="https://pepy.tech/project/opentelemetry-instrumentation-openai">
  <img src="https://static.pepy.tech/badge/opentelemetry-instrumentation-openai/month">
  </a>
   <a href="https://github.com/traceloop/openllmetry/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-Apache 2.0-blue.svg" alt="OpenLLMetry is released under the Apache-2.0 License">
  </a>
  <a href="https://github.com/traceloop/openllmetry/actions/workflows/ci.yml">
  <img src="https://github.com/traceloop/openllmetry/actions/workflows/ci.yml/badge.svg">
  </a>
  <a href="https://github.com/traceloop/openllmetry/issues">
    <img src="https://img.shields.io/github/commit-activity/m/traceloop/openllmetry" alt="git commit activity" />
  </a>
  <a href="https://www.ycombinator.com/companies/traceloop"><img src="https://img.shields.io/website?color=%23f26522&down_message=Y%20Combinator&label=Backed&logo=ycombinator&style=flat-square&up_message=Y%20Combinator&url=https%3A%2F%2Fwww.ycombinator.com"></a>
  <a href="https://github.com/traceloop/openllmetry/blob/main/CONTRIBUTING.md">
    <img src="https://img.shields.io/badge/PRs-Welcome-brightgreen" alt="PRs welcome!" />
  </a>
  <a href="https://traceloop.com/slack">
    <img src="https://img.shields.io/badge/chat-on%20Slack-blueviolet" alt="Slack community channel" />
  </a>
  <a href="https://twitter.com/traceloopdev">
    <img src="https://img.shields.io/badge/follow-%40traceloopdev-1DA1F2?logo=twitter&style=social" alt="Traceloop Twitter" />
  </a>
</h4>

**🎉 新消息**：
我们的语义约定现已成为 OpenTelemetry 的一部分！欢迎加入[讨论](https://github.com/open-telemetry/community/blob/1c71595874e5d125ca92ec3b0e948c4325161c8a/projects/llm-semconv.md)，帮助我们共同塑造 LLM 可观测性的未来。

在找 JS/TS 版本？请查看 [OpenLLMetry-JS](https://github.com/traceloop/openllmetry-js)。

OpenLLMetry 是一组构建在 [OpenTelemetry](https://opentelemetry.io/) 之上的扩展，为你的 LLM 应用提供完整的可观测性。由于它底层使用 OpenTelemetry，[因此可以接入你现有的可观测性解决方案](https://www.traceloop.com/docs/openllmetry/integrations/introduction)，例如 Datadog、Honeycomb 等。

它由 Traceloop 基于 Apache 2.0 许可构建并维护。

该仓库包含面向 LLM 提供商和向量数据库的标准 OpenTelemetry 插桩，同时也提供了一个 Traceloop SDK，帮助你轻松开始使用 OpenLLMetry，并仍然输出可接入你可观测性技术栈的标准 OpenTelemetry 数据。
如果你已经接入了 OpenTelemetry，也可以直接添加我们的任意插桩。

## 🚀 快速开始

最简单的入门方式是使用我们的 SDK。
完整指南请参阅我们的[文档](https://traceloop.com/docs/openllmetry/getting-started-python)。

安装 SDK：

```bash
pip install traceloop-sdk
```

然后，要开始为你的代码添加插桩，只需在代码中加入这一行：

```python
from traceloop.sdk import Traceloop

Traceloop.init()
```

就是这样。你现在已经在使用 OpenLLMetry 对代码进行追踪了！
如果你是在本地运行，可能会希望禁用批量发送，这样就能立即看到 traces：

```python
Traceloop.init(disable_batch=True)
```

## ⏫ 支持（并经过测试）的目标端

- ✅ [Traceloop](https://www.traceloop.com/docs/openllmetry/integrations/traceloop)
- ✅ [Axiom](https://www.traceloop.com/docs/openllmetry/integrations/axiom)
- ✅ [Azure Application Insights](https://www.traceloop.com/docs/openllmetry/integrations/azure)
- ✅ [Braintrust](https://www.traceloop.com/docs/openllmetry/integrations/braintrust)
- ✅ [Dash0](https://www.traceloop.com/docs/openllmetry/integrations/dash0)
- ✅ [Datadog](https://www.traceloop.com/docs/openllmetry/integrations/datadog)
- ✅ [Dynatrace](https://www.traceloop.com/docs/openllmetry/integrations/dynatrace)
- ✅ [Google Cloud](https://www.traceloop.com/docs/openllmetry/integrations/gcp)
- ✅ [Grafana](https://www.traceloop.com/docs/openllmetry/integrations/grafana)
- ✅ [Highlight](https://www.traceloop.com/docs/openllmetry/integrations/highlight)
- ✅ [Honeycomb](https://www.traceloop.com/docs/openllmetry/integrations/honeycomb)
- ✅ [HyperDX](https://www.traceloop.com/docs/openllmetry/integrations/hyperdx)
- ✅ [IBM Instana](https://www.traceloop.com/docs/openllmetry/integrations/instana)
- ✅ [KloudMate](https://www.traceloop.com/docs/openllmetry/integrations/kloudmate)
- ✅ [Laminar](https://www.traceloop.com/docs/openllmetry/integrations/laminar)
- ✅ [New Relic](https://www.traceloop.com/docs/openllmetry/integrations/newrelic)
- ✅ [OpenTelemetry Collector](https://www.traceloop.com/docs/openllmetry/integrations/otel-collector)
- ✅ [Oracle Cloud](https://www.traceloop.com/docs/openllmetry/integrations/oraclecloud)
- ✅ [Scorecard](https://www.traceloop.com/docs/openllmetry/integrations/scorecard)
- ✅ [Service Now Cloud Observability](https://www.traceloop.com/docs/openllmetry/integrations/service-now)
- ✅ [SigNoz](https://www.traceloop.com/docs/openllmetry/integrations/signoz)
- ✅ [Sentry](https://www.traceloop.com/docs/openllmetry/integrations/sentry)
- ✅ [Splunk](https://www.traceloop.com/docs/openllmetry/integrations/splunk)
- ✅ [Tencent Cloud](https://www.traceloop.com/docs/openllmetry/integrations/tencent)

关于如何连接到每个目标端，请参阅[我们的文档](https://traceloop.com/docs/openllmetry/integrations/exporting)。

## 🪗 我们对什么进行插桩？

OpenLLMetry 可以对 [OpenTelemetry 已经支持的所有内容](https://github.com/open-telemetry/opentelemetry-python-contrib/tree/main/instrumentation)进行插桩，例如数据库、API 调用等等。在此基础上，我们还构建了一组自定义扩展，用于对 OpenAI、Anthropic 等调用，或 Chroma、Pinecone、Qdrant、Weaviate 等向量数据库进行插桩。

- ✅ [Aleph Alpha](https://www.aleph-alpha.com/)
- ✅ [Anthropic](https://www.anthropic.com/)
- ✅ [Bedrock (AWS)](https://aws.amazon.com/bedrock/)
- ✅ [Cohere](https://cohere.com/)
- ✅ [Google Generative AI (Gemini)](https://ai.google/)
- ✅ [Groq](https://groq.com/)
- ✅ [HuggingFace](https://huggingface.co/)
- ✅ [IBM Watsonx AI](https://www.ibm.com/watsonx)
- ✅ [Mistral AI](https://mistral.ai/)
- ✅ [Ollama](https://ollama.com/)
- ✅ [OpenAI / Azure OpenAI](https://openai.com/)
- ✅ [Replicate](https://replicate.com/)
- ✅ [SageMaker (AWS)](https://aws.amazon.com/sagemaker/)
- ✅ [Together AI](https://together.xyz/)
- ✅ [Vertex AI (GCP)](https://cloud.google.com/vertex-ai)
- ✅ [WRITER](https://writer.com/)

### 向量数据库

- ✅ [Chroma](https://www.trychroma.com/)
- ✅ [LanceDB](https://lancedb.com/)
- ✅ [Marqo](https://marqo.ai/)
- ✅ [Milvus](https://milvus.io/)
- ✅ [Pinecone](https://www.pinecone.io/)
- ✅ [Qdrant](https://qdrant.tech/)
- ✅ [Weaviate](https://weaviate.io/)

### 框架

- ✅ [Agno](https://github.com/agno-agi/agno)
- ✅ [AWS Strands](https://strandsagents.com/)（内置 OTEL 支持）
- ✅ [CrewAI](https://docs.crewai.com/introduction)
- ✅ [Haystack](https://haystack.deepset.ai/integrations/traceloop)
- ✅ [LangChain](https://python.langchain.com/docs/introduction/)
- ✅ [Langflow](https://docs.langflow.org/)
- ✅ [LangGraph](https://langchain-ai.github.io/langgraph/concepts/why-langgraph/)
- ✅ [LiteLLM](https://docs.litellm.ai/docs/observability/opentelemetry_integration)
- ✅ [LlamaIndex](https://docs.llamaindex.ai/en/stable/module_guides/observability/observability.html#openllmetry)
- ✅ [OpenAI Agents](https://openai.github.io/openai-agents-python/)

### 协议

- ✅ [MCP](https://modelcontextprotocol.io/)

## 🔎 遥测

我们已不再在 SDK 或这些插桩中记录或收集任何遥测数据。请确保升级到 v0.49.2 及以上版本。

### 为什么我们会收集遥测

- 主要目的是检测插桩内部的异常。由于 LLM 提供商会频繁更新其 API，这有助于我们快速识别并修复任何破坏性变更。
- 我们只收集匿名数据，不包含任何可识别个人身份的信息。你可以在我们的[隐私文档](https://www.traceloop.com/docs/openllmetry/privacy/telemetry)中准确查看我们收集了哪些数据。
- 遥测仅在 SDK 中收集。如果你直接使用这些插桩而不使用 SDK，则不会收集任何遥测数据。

## 🌱 参与贡献

无论贡献大小，我们都非常欢迎 ❤️ 查看我们的指南，了解如何[开始参与](https://traceloop.com/docs/openllmetry/contributing/overview)。

如果不确定从哪里开始，你可以：

- [预约一次与我们团队成员的免费结对交流](mailto:nir@traceloop.com?subject=Pairing%20session&body=I'd%20like%20to%20do%20a%20pairing%20session!)！
- 加入我们的 <a href="https://traceloop.com/slack">Slack</a>，并在里面向我们提问。

## 💚 社区与支持

- [Slack](https://traceloop.com/slack)（与社区和 Traceloop 团队进行实时讨论）
- [GitHub Discussions](https://github.com/traceloop/openllmetry/discussions)（获取构建帮助以及围绕功能展开更深入的讨论）
- [GitHub Issues](https://github.com/traceloop/openllmetry/issues)（报告你在使用 OpenLLMetry 时遇到的任何 bug 和错误）
- [Twitter](https://twitter.com/traceloopdev)（快速获取最新消息）

## 🙏 特别鸣谢

感谢 @patrickdebois，[是他建议了这个很棒的名字](https://x.com/patrickdebois/status/1695518950715473991?s=46&t=zn2SOuJcSVq-Pe2Ysevzkg)，我们现在将其用作这个仓库的名称！

## 💫 贡献者

<a href="https://github.com/traceloop/openllmetry/graphs/contributors">
  <img alt="contributors" src="assets/003-image-25334b3608.svg"/>
</a>
