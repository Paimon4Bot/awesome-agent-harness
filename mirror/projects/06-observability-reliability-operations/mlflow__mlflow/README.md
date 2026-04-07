<h1 align="center" style="border-bottom: none">
    <a href="https://mlflow.org/">
        <img alt="MLflow logo" src="assets/001-logo-4e51215a09.svg" width="200" />
    </a>
</h1>
<h2 align="center" style="border-bottom: none">The Open Source AI Engineering Platform for Agents, LLMs & Models</h2>

MLflow is the largest open source **AI engineering platform for agents, LLMs, and ML models**. MLflow enables teams of all sizes to [debug](https://mlflow.org/llm-tracing),
[evaluate](https://mlflow.org/llm-evaluation), [monitor](https://mlflow.org/ai-monitoring), and [optimize](https://mlflow.org/prompt-optimization) production-quality AI applications while
controlling costs and managing access to models and data. With over **60 million monthly downloads**,
thousands of organizations rely on MLflow each day to ship AI to production with confidence.

MLflow's comprehensive feature set for agents and LLM applications includes production-grade [observability](https://mlflow.org/docs/latest/genai/tracing), [evaluation](https://mlflow.org/docs/latest/genai/eval-monitor),
[prompt management](https://mlflow.org/docs/latest/genai/prompt-registry), [prompt optimization](https://mlflow.org/prompt-optimization) and an [AI Gateway](https://mlflow.org/docs/latest/genai/governance/ai-gateway) for managing costs and model access.
Learn more at [MLflow for LLMs and Agents](https://mlflow.org/docs/latest/genai).

<div align="center">

[![Python SDK](https://img.shields.io/pypi/v/mlflow)](https://pypi.org/project/mlflow/)
[![PyPI Downloads](https://img.shields.io/pypi/dm/mlflow)](https://pepy.tech/projects/mlflow)
[![License](https://img.shields.io/github/license/mlflow/mlflow)](https://github.com/mlflow/mlflow/blob/master/LICENSE.txt)
<a href="https://twitter.com/intent/follow?screen_name=mlflow" target="_blank">
<img src="https://img.shields.io/twitter/follow/mlflow?logo=X&color=%20%23f5f5f5"
      alt="follow on X(Twitter)"></a>
<a href="https://www.linkedin.com/company/mlflow-org/" target="_blank">
<img src="https://custom-icon-badges.demolab.com/badge/LinkedIn-0A66C2?logo=linkedin-white&logoColor=fff"
      alt="follow on LinkedIn"></a>
[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/mlflow/mlflow)

</div>

<div align="center">
   <div>
      <a href="https://mlflow.org/"><strong>Website</strong></a> ·
      <a href="https://mlflow.org/docs/latest"><strong>Docs</strong></a> ·
      <a href="https://github.com/mlflow/mlflow/issues/new/choose"><strong>Feature Request</strong></a> ·
      <a href="https://mlflow.org/blog"><strong>News</strong></a> ·
      <a href="https://www.youtube.com/@mlflowoss"><strong>YouTube</strong></a> ·
      <a href="https://lu.ma/mlflow?k=c"><strong>Events</strong></a>
   </div>
</div>

<br>

## Get Started in 3 Simple Steps

From zero to full-stack LLMOps in minutes. No complex setup or major code changes required. [Get Started →](https://mlflow.org/docs/latest/genai/tracing/quickstart/)

**1. Start MLflow Server**

```bash
uvx mlflow server
```

**2. Enable Logging**

```python
import mlflow

mlflow.set_tracking_uri("http://localhost:5000")
mlflow.openai.autolog()
```

**3. Run Your Code**

```python
from openai import OpenAI

client = OpenAI()
client.responses.create(
    model="gpt-5.4-mini",
    input="Hello!",
)
```

Explore traces and metrics in the MLflow UI at `http://localhost:5000`.

## LLMs & Agents

MLflow provides everything you need to build, debug, evaluate, and deploy production-quality LLM applications and AI agents. Supports Python, TypeScript/JavaScript, Java and any other programming language. MLflow also natively integrates with [OpenTelemetry](https://opentelemetry.io/) and MCP.

<table>
  <tr>
    <td width="50%">
    <img src="assets/002-readme-tracing-5c49c69bee.png" alt="Observability" width=100%>
    <div align="center">
        <br>
        <a href="https://mlflow.org/docs/latest/genai/tracing/"><strong>Observability</strong></a>
        <br><br>
        <div>Capture complete traces of your LLM applications and agents for deep behavioral insights. Built on OpenTelemetry, supporting any LLM provider and agent framework. Monitor production quality, costs, and safety.</div><br>
        <a href="https://mlflow.org/docs/latest/genai/tracing/quickstart/">Getting Started →</a>
        <br><br>
    </div>
    </td>
    <td width="50%">
    <img src="assets/003-readme-llm-eval-d9b7f70083.png" alt="Evaluation" width=100%>
    <div align="center">
        <br>
        <a href="https://mlflow.org/docs/latest/genai/eval-monitor/"><strong>Evaluation</strong></a>
        <br><br>
        <div>Run systematic evaluations, track quality metrics over time, and catch regressions before they reach production. Choose from 50+ built-in metrics and LLM judges, or define your own.</div><br>
        <a href="https://mlflow.org/docs/latest/genai/eval-monitor/">Getting Started →</a>
        <br><br>
    </div>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <img src="assets/004-readme-prompt-b7024e1c91.png" alt="Prompts & Optimization" width=100%>
    <div align="center">
        <br>
        <a href="https://mlflow.org/docs/latest/genai/prompt-registry/"><strong>Prompts & Optimization</strong></a>
        <br><br>
        <div>Version, test, and deploy prompts with full lineage tracking. <a href="https://mlflow.org/prompt-optimization">Automatically optimize prompts</a> with state-of-the-art algorithms to improve performance.</div><br>
        <a href="https://mlflow.org/docs/latest/genai/prompt-registry/create-and-edit-prompts/">Getting Started →</a>
        <br><br>
    </div>
    </td>
    <td width="50%">
      <img src="assets/005-readme-gateway-75392623f7.png" alt="AI Gateway" width=100%>
    <div align="center">
        <br>
        <a href="https://mlflow.org/docs/latest/genai/governance/ai-gateway/"><strong>AI Gateway</strong></a>
        <br><br>
        <div>Unified API gateway for all LLM providers. Route requests, manage rate limits, handle fallbacks, and control costs through an OpenAI-compatible interface with built-in credential management, guardrails and traffic splitting for A/B testing.</div><br>
        <a href="https://mlflow.org/docs/latest/genai/governance/ai-gateway/quickstart/">Getting Started →</a>
        <br><br>
    </div>
    </td>
  </tr>
</table>

## Model Training

For machine learning and deep learning model development, MLflow provides a full suite of tools to manage the ML lifecycle:

- [**Experiment Tracking**](https://mlflow.org/docs/latest/ml/tracking/) — Track models, parameters, metrics, and evaluation results across experiments
- [**Model Evaluation**](https://mlflow.org/docs/latest/ml/evaluation/) — Automated evaluation tools integrated with experiment tracking
- [**Model Registry**](https://mlflow.org/docs/latest/ml/model-registry/) — Collaboratively manage the full lifecycle of ML models
- [**Deployment**](https://mlflow.org/docs/latest/ml/deployment/) — Deploy models to batch and real-time scoring on Docker, Kubernetes, Azure ML, AWS SageMaker, and more

Learn more at [MLflow for Model Training](https://mlflow.org/docs/latest/ml).

## Integrations

MLflow supports all agent frameworks, LLM providers, tools, and programming languages. We offer one-line automatic tracing for more than 60 frameworks. See the [full integrations list](https://mlflow.org/docs/latest/genai/tracing/integrations/).

### OpenTelemetry

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/app-instrumentation/opentelemetry"><img src="assets/006-opentelemetry-logo-only-670290b020.png" height="40"><br><sub><b>OpenTelemetry</b></sub></a></td>
  </tr>
</table>

### Agent Frameworks (Python)

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/langchain"><img src="assets/007-langchain-logo-only-51be9e0f0d.png" height="40"><br><sub><b>LangChain</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/langgraph"><img src="assets/008-langgraph-logo-only-1f09fac42c.png" height="40"><br><sub><b>LangGraph</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/openai-agent"><img src="assets/009-openai-logo-only-b9742aa9ed.png" height="40"><br><sub><b>OpenAI Agent</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/dspy"><img src="assets/010-dspy-logo-075aee5a1d.png" height="40"><br><sub><b>DSPy</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/pydantic_ai"><img src="assets/011-pydantic-ai-logo-only-5829c8fd87.png" height="40"><br><sub><b>PydanticAI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/google-adk"><img src="assets/012-google-adk-logo-0c9128e8a6.png" height="40"><br><sub><b>Google ADK</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/microsoft-agent-framework"><img src="assets/013-microsoft-agent-framework-logo-3a6610ef71.png" height="40"><br><sub><b>Microsoft Agent</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/crewai"><img src="assets/014-crewai-logo-a50e2b1004.svg" height="40"><br><sub><b>CrewAI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/llama_index"><img src="assets/015-llamaindex-logo-4c3ab63af5.svg" height="40"><br><sub><b>LlamaIndex</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/autogen"><img src="assets/016-autogen-logo-14b66500f6.png" height="40"><br><sub><b>AutoGen</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/strands"><img src="assets/017-strands-logo-e33dcf3fcc.png" height="40"><br><sub><b>Strands</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/livekit"><img src="assets/018-livekit-logo-cd48e04d6e.png" height="40"><br><sub><b>LiveKit Agents</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/agno"><img src="assets/019-agno-logo-425d55165e.png" height="40"><br><sub><b>Agno</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/bedrock-agentcore"><img src="assets/020-bedrock-logo-6bec6af019.png" height="40"><br><sub><b>Bedrock AgentCore</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/smolagents"><img src="assets/021-smolagents-logo-bb97da1c7c.png" height="40"><br><sub><b>Smolagents</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/semantic_kernel"><img src="assets/022-semantic-kernel-logo-c6cb04e61d.png" height="40"><br><sub><b>Semantic Kernel</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/deepagent"><img src="assets/023-deepagent-logo-14f7ed332f.svg" height="40"><br><sub><b>DeepAgent</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/ag2"><img src="assets/024-ag2-logo-8da2547bc0.png" height="40"><br><sub><b>AG2</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/haystack"><img src="assets/025-haystack-logo-cc7f0069e2.png" height="40"><br><sub><b>Haystack</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/koog"><img src="assets/026-koog-874287a239.png" height="40"><br><sub><b>Koog</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/txtai"><img src="assets/027-txtai-logo-4f889805d1.png" height="40"><br><sub><b>txtai</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/pipecat"><img src="assets/028-pipecat-8da0cb6894.png" height="40"><br><sub><b>Pipecat</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/watsonx-orchestrate"><img src="assets/029-watsonx-orchestrate-f5c9e8e581.png" height="40"><br><sub><b>Watsonx</b></sub></a></td>
  </tr>
</table>

### Agent Frameworks (TypeScript)

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/langchain"><img src="assets/007-langchain-logo-only-51be9e0f0d.png" height="40"><br><sub><b>LangChain</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/langgraph"><img src="assets/008-langgraph-logo-only-1f09fac42c.png" height="40"><br><sub><b>LangGraph</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/vercelai"><img src="assets/030-vercel-logo-531b7c1a84.svg" height="40"><br><sub><b>Vercel AI SDK</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/mastra"><img src="assets/031-mastra-logo-2c87e26be1.png" height="40"><br><sub><b>Mastra</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/voltagent"><img src="assets/032-voltagent-logo-8174064f21.png" height="40"><br><sub><b>VoltAgent</b></sub></a></td>
  </tr>
</table>

### Agent Frameworks (Java)

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/spring-ai"><img src="assets/033-spring-ai-logo-45a171797b.png" height="40"><br><sub><b>Spring AI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/quarkus-langchain4j"><img src="assets/034-langchain4j-03796ddf31.svg" height="40"><br><sub><b>Quarkus LangChain4j</b></sub></a></td>
  </tr>
</table>

### Model Providers

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/openai"><img src="assets/009-openai-logo-only-b9742aa9ed.png" height="40"><br><sub><b>OpenAI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/anthropic"><img src="assets/035-anthropic-logo-f010b1d6d3.png" height="40"><br><sub><b>Anthropic</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/databricks"><img src="assets/036-databricks-logo-5c184052c7.png" height="40"><br><sub><b>Databricks</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/gemini"><img src="assets/037-google-gemini-logo-9c9f163082.svg" height="40"><br><sub><b>Gemini</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/bedrock"><img src="assets/020-bedrock-logo-6bec6af019.png" height="40"><br><sub><b>Amazon Bedrock</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/litellm"><img src="assets/038-litellm-logo-1514757073.png" height="40"><br><sub><b>LiteLLM</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/mistral"><img src="assets/039-mistral-ai-logo-9bd6cf2a59.svg" height="40"><br><sub><b>Mistral</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/xai-grok"><img src="assets/040-grok-logo-ae64b77bab.png" height="40"><br><sub><b>xAI / Grok</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/ollama"><img src="assets/041-ollama-logo-5484a68a80.png" height="40"><br><sub><b>Ollama</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/groq"><img src="assets/042-groq-logo-06b1012fe7.svg" height="40"><br><sub><b>Groq</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/deepseek"><img src="assets/043-deepseek-logo-41bc0f4b86.png" height="40"><br><sub><b>DeepSeek</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/qwen"><img src="assets/044-qwen-logo-933423c55c.jpg" height="40"><br><sub><b>Qwen</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/moonshot"><img src="assets/045-kimi-logo-835aaeb635.png" height="40"><br><sub><b>Moonshot AI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/cohere"><img src="assets/046-cohere-logo-aab737f96c.png" height="40"><br><sub><b>Cohere</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/byteplus"><img src="assets/047-byteplus-logo-525d7ed95e.png" height="40"><br><sub><b>BytePlus</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/novitaai"><img src="assets/048-novitaai-logo-abbf2f4868.jpg" height="40"><br><sub><b>Novita AI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/fireworksai"><img src="assets/049-fireworks-ai-logo-60d58779ee.png" height="40"><br><sub><b>FireworksAI</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/togetherai"><img src="assets/050-together-ai-logo-c92c5beaf0.png" height="40"><br><sub><b>Together AI</b></sub></a></td>
  </tr>
</table>

### Gateways

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/databricks-ai-gateway"><img src="assets/036-databricks-logo-5c184052c7.png" height="40"><br><sub><b>Databricks</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/litellm-proxy"><img src="assets/038-litellm-logo-1514757073.png" height="40"><br><sub><b>LiteLLM Proxy</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/vercel-ai-gateway"><img src="assets/030-vercel-logo-531b7c1a84.svg" height="40"><br><sub><b>Vercel AI Gateway</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/openrouter"><img src="assets/051-openrouter-logo-f048192af5.png" height="40"><br><sub><b>OpenRouter</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/portkey"><img src="assets/052-portkey-logo-41de1a42dd.png" height="40"><br><sub><b>Portkey</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/helicone"><img src="assets/053-helicone-logo-2898b69050.png" height="40"><br><sub><b>Helicone</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/kong"><img src="assets/054-kong-logo-d8d19f88b5.png" height="40"><br><sub><b>Kong AI Gateway</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/pydantic-ai-gateway"><img src="assets/011-pydantic-ai-logo-only-5829c8fd87.png" height="40"><br><sub><b>PydanticAI Gateway</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/truefoundry"><img src="assets/055-truefoundry-logo-39c5ae5b26.png" height="40"><br><sub><b>TrueFoundry</b></sub></a></td>
  </tr>
</table>

### Tools & No-Code

<table>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/instructor"><img src="assets/056-instructor-logo-6d8233cf5c.svg" height="40"><br><sub><b>Instructor</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/claude_code"><img src="assets/057-claude-code-logo-21bc975499.png" height="40"><br><sub><b>Claude Code</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/opencode"><img src="assets/058-opencode-logo-3379a303bb.png" height="40"><br><sub><b>Opencode</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/langfuse"><img src="assets/059-langfuse-logo-cffcae1761.png" height="40"><br><sub><b>Langfuse</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/arize"><img src="assets/060-arize-phoenix-logo-89aaec73ed.png" height="40"><br><sub><b>Arize / Phoenix</b></sub></a></td>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/goose"><img src="assets/061-goose-logo-7d48884385.png" height="40"><br><sub><b>Goose</b></sub></a></td>
  </tr>
  <tr>
    <td align="center" width="110"><a href="https://mlflow.org/docs/latest/genai/tracing/integrations/listing/langflow"><img src="assets/062-langflow-fc819f551c.svg" height="40"><br><sub><b>Langflow</b></sub></a></td>
  </tr>
</table>

## Hosting MLflow

MLflow can be used in a variety of environments, including your local environment, on-premises clusters, cloud platforms, and managed services. Being an open-source platform, MLflow is **vendor-neutral** — whether you're building AI agents, LLM applications, or ML models, you have access to MLflow's core capabilities.

<table>
  <tr>
    <td align="center" width="130"><a href="https://docs.databricks.com/aws/en/mlflow3/genai/"><img src="assets/036-databricks-logo-5c184052c7.png" height="40"><br><sub><b>Databricks</b></sub></a></td>
    <td align="center" width="130"><a href="https://aws.amazon.com/sagemaker-ai/experiments/"><img src="assets/063-amazon-sagemaker-logo-531bed6bdb.png" height="40"><br><sub><b>Amazon SageMaker</b></sub></a></td>
    <td align="center" width="130"><a href="https://learn.microsoft.com/en-us/azure/machine-learning/concept-mlflow?view=azureml-api-2"><img src="assets/064-azure-ml-logo-11ac995bc3.png" height="40"><br><sub><b>Azure ML</b></sub></a></td>
    <td align="center" width="130"><a href="https://nebius.com/services/managed-mlflow"><img src="assets/065-nebius-logo-f2f3dccf10.png" height="40"><br><sub><b>Nebius</b></sub></a></td>
    <td align="center" width="130"><a href="https://mlflow.org/docs/latest/ml/tracking/"><img src="assets/066-kubernetes-logo-13b784d686.png" height="40"><br><sub><b>Self-Hosted</b></sub></a></td>
  </tr>
</table>

## 💭 Support

- For help or questions about MLflow usage (e.g. "how do I do X?") visit the [documentation](https://mlflow.org/docs/latest).
- In the documentation, you can ask the question to our AI-powered chat bot. Click on the **"Ask AI"** button at the right bottom.
- Join the [virtual events](https://lu.ma/mlflow?k=c) like office hours and meetups.
- To report a bug, file a documentation issue, or submit a feature request, please [open a GitHub issue](https://github.com/mlflow/mlflow/issues/new/choose).
- For release announcements and other discussions, please subscribe to our mailing list (mlflow-users@googlegroups.com)
  or join us on [Slack](https://mlflow.org/slack).

## 🤝 Contributing

We happily welcome contributions to MLflow!

- Submit [bug reports](https://github.com/mlflow/mlflow/issues/new?template=bug_report_template.yaml) and [feature requests](https://github.com/mlflow/mlflow/issues/new?template=feature_request_template.yaml)
- Contribute for [good-first-issues](https://github.com/mlflow/mlflow/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) and [help-wanted](https://github.com/mlflow/mlflow/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22)
- Writing about MLflow and sharing your experience

Please see our [contribution guide](CONTRIBUTING.md) to learn more about contributing to MLflow.

## ⭐️ Star History

<a href="https://star-history.com/#mlflow/mlflow&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="assets/068-svg-1fb2473206.svg" />
   <source media="(prefers-color-scheme: light)" srcset="assets/067-svg-8e90a570fd.svg" />
   <img alt="Star History Chart" src="assets/067-svg-8e90a570fd.svg" />
 </picture>
</a>

## ✏️ Citation

If you use MLflow in your research, please cite it using the "Cite this repository" button at the top of the [GitHub repository page](https://github.com/mlflow/mlflow), which will provide you with citation formats including APA and BibTeX.

## 👥 Core Members

MLflow is currently maintained by the following core members with significant contributions from hundreds of exceptionally talented community members.

- [Ben Wilson](https://github.com/BenWilson2)
- [Corey Zumar](https://github.com/dbczumar)
- [Daniel Lok](https://github.com/daniellok-db)
- [Gabriel Fu](https://github.com/gabrielfu)
- [Harutaka Kawamura](https://github.com/harupy)
- [Joel Robin P](https://github.com/joelrobin18)
- [Matt Prahl](https://github.com/mprahl)
- [Pat Sukprasert](https://github.com/PattaraS)
- [Serena Ruan](https://github.com/serena-ruan)
- [Tomu Hirata](https://github.com/TomeHirata)
- [Weichen Xu](https://github.com/WeichenXu123)
- [Yuki Watanabe](https://github.com/B-Step62)
