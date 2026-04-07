<!--
SPDX-FileCopyrightText: Copyright (c) 2024-2026, NVIDIA CORPORATION & AFFILIATES. All rights reserved.
SPDX-License-Identifier: Apache-2.0

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

![NVIDIA NeMo Agent Toolkit](assets/001-nvidia-nemo-agent-toolkit-8941ce87f8.png "NeMo Agent Toolkit banner image")

# NVIDIA NeMo Agent Toolkit

<!-- vale off (due to hyperlinks) -->
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-green.svg)](https://opensource.org/licenses/Apache-2.0)
[![GitHub Release](https://img.shields.io/github/v/release/NVIDIA/NeMo-Agent-Toolkit)](https://github.com/NVIDIA/NeMo-Agent-Toolkit/releases)
[![PyPI version](https://img.shields.io/pypi/v/nvidia-nat)](https://pypi.org/project/nvidia-nat/)
[![GitHub issues](https://img.shields.io/github/issues/NVIDIA/NeMo-Agent-Toolkit)](https://github.com/NVIDIA/NeMo-Agent-Toolkit/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/NVIDIA/NeMo-Agent-Toolkit)](https://github.com/NVIDIA/NeMo-Agent-Toolkit/pulls)
[![GitHub Repo stars](https://img.shields.io/github/stars/NVIDIA/NeMo-Agent-Toolkit)](https://github.com/NVIDIA/NeMo-Agent-Toolkit)
[![GitHub forks](https://img.shields.io/github/forks/NVIDIA/NeMo-Agent-Toolkit)](https://github.com/NVIDIA/NeMo-Agent-Toolkit/network/members)
[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/NVIDIA/NeMo-Agent-Toolkit)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NVIDIA/NeMo-Agent-Toolkit/)
<!-- vale on -->

<div align="center">

*NVIDIA NeMo Agent Toolkit 为各种框架中的 AI 代理注入智能，通过企业级仪表化、可观测性和持续学习提升速度、准确性和决策能力。*

</div>

## 🔥 新功能

- [**Dynamo 运行时智能：**](./examples/dynamo_integration/latency_sensitivity_demo/README.md) 自动从代理画像推断每个请求的延迟敏感性，并应用运行时提示，以实现缓存控制、负载感知路由和优先级感知服务。
- [**代理性能原语 (APP)：**](https://docs.langchain.com/oss/python/integrations/providers/nvidia#install-2) 引入框架无关的性能原语，通过并行执行、推测分支和节点级优先路由来加速 LangChain、CrewAI 和 Agno 等基于图的代理框架。
- [**LangSmith 原生集成：**](./docs/source/run-workflows/observe/observe-workflow-with-langsmith.md) 通过原生 LangSmith 追踪观测端到端的代理执行，运行评估实验，比较结果，并在开发和生产工作流中管理提示词版本。
- [**FastMCP 工作流发布：**](./docs/source/run-workflows/fastmcp-server.md) 使用 FastMCP 服务器运行时将 NeMo Agent Toolkit 工作流发布为 MCP 服务器，简化 MCP 原生部署和集成。
- **迁移说明：** `1.5.0` 简化了包安装和依赖管理。参见[迁移指南](./docs/source/resources/migration-guide.md#v150)。

## ✨ 核心特性

- 🛠️ **构建代理**：加速你的代理开发，提供让代理更快投入生产的工具。
  - 🧩 [**框架无关：**](./docs/source/components/integrations/frameworks.md) 与各类代理框架协同工作，添加观测、性能分析和优化代理所需的仪表化。可与 [LangChain](https://www.langchain.com/)、[LlamaIndex](https://www.llamaindex.ai/)、[CrewAI](https://www.crewai.com/)、[Microsoft Semantic Kernel](https://learn.microsoft.com/en-us/semantic-kernel/) 和 [Google ADK](https://google.github.io/adk-docs/) 等流行框架，以及自定义企业代理框架和简单 Python 代理配合使用。
  - 🔁 [**可复用性：**](./docs/source/components/sharing-components.md) 一次构建组件，多次使用，最大化开发投入的价值。
  - ⚡ [**可定制性：**](docs/source/get-started/tutorials/customize-a-workflow.md) 从预构建的代理、工具或工作流开始，根据需要自定义。
  - 💬 [**内置用户界面：**](./docs/source/run-workflows/launching-ui.md) 使用 NeMo Agent Toolkit UI 聊天界面与代理交互、可视化输出和调试工作流。
- 📈 **代理洞察**：利用 NeMo Agent Toolkit 的仪表化更好地理解代理在运行时的行为。
  - 📊 [**性能分析：**](./docs/source/improve-workflows/profiler.md) 从代理层到单个 token 层面分析整个工作流，识别瓶颈、分析 token 效率，并指导开发者优化代理。
  - 🔎 [**可观测性：**](./docs/source/run-workflows/observe/observe.md) 跟踪性能、追踪执行流程，深入了解代理在生产环境中的行为。
- 🚀 **代理优化**：通过覆盖代理生命周期各阶段的工具套件，提升代理的质量、准确性和性能。
  - 🧪 [**评估系统：**](./docs/source/improve-workflows/evaluate.md) 通过一套离线评估工具验证和保持代理工作流的准确性。
  - 🎯 [**超参数和提示词优化器：**](./docs/source/improve-workflows/optimizer.md) 自动识别最佳配置和提示词，确保代理发挥最大效能。
  - 🧠 [**强化学习微调：**](./docs/source/improve-workflows/finetuning/index.md) 专门为代理微调 LLM，将工作流的内在信息直接训练到模型中。
  - ⚡ [**NVIDIA Dynamo 集成：**](./examples/dynamo_integration/README.md) 结合 Dynamo 和 NeMo Agent Toolkit 大规模提升代理性能。
  - ⚙️ [**代理性能原语 (APP)：**](https://docs.langchain.com/oss/python/integrations/providers/nvidia#install-2) 通过并行执行、推测分支和节点级优先路由来加速 LangChain、CrewAI 和 Agno 等基于图的代理框架。
- 🔌 **协议支持**：集成构建代理时常用的协议。
  - 🔗 [**模型上下文协议 (MCP)：**](./docs/source/build-workflows/mcp-client.md) 将 [MCP 工具](./docs/source/build-workflows/mcp-client.md) 集成到代理中，或将你的工具和代理作为 [MCP 服务器](./docs/source/run-workflows/mcp-server.md) 供他人使用。
  - 🤝 [**代理间 (A2A) 协议：**](./docs/source/components/integrations/a2a.md) 构建分布式代理团队，全面支持身份验证。

通过 NeMo Agent Toolkit，你可以快速行动、自由实验，并确保所有代理驱动项目的可靠性。

## 🚀 安装

在开始使用 NeMo Agent Toolkit 之前，请确保系统已安装 Python 3.11、3.12 或 3.13。

> [!NOTE]
> 如果要运行示例，需要克隆仓库并从源码安装，以获取运行示例所需的文件。详情请参见 [示例](./examples/README.md) 文档。

要从 PyPI 安装最新稳定版 NeMo Agent Toolkit，运行以下命令：

```bash
pip install nvidia-nat
```

NeMo Agent Toolkit 有许多可选依赖，可与核心包一起安装。可选依赖按框架分组。例如，要安装 LangChain/LangGraph 插件，运行以下命令：

```bash
pip install "nvidia-nat[langchain]"
```

详细的安装说明，包括可选依赖的完整列表及其冲突，请参见 [安装指南](./docs/source/get-started/installation.md)。

## 🌟 Hello World 示例

在开始之前，可以在 Google Colab 中无配置运行此简单工作流和许多其他示例。点击此处打开介绍笔记本：[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NVIDIA/NeMo-Agent-Toolkit/)。

1. 确保已设置 `NVIDIA_API_KEY` 环境变量，以允许示例使用 NVIDIA NIM。可访问 [`build.nvidia.com`](https://build.nvidia.com/) 并创建账户来获取 API 密钥。

   ```bash
   export NVIDIA_API_KEY=<your_api_key>
   ```

2. 创建 NeMo Agent Toolkit 工作流配置文件。此文件将定义示例中使用的代理、工具和工作流。将以下内容保存为 `workflow.yml`：

   ```yaml
   functions:
      # Add a tool to search wikipedia
      wikipedia_search:
         _type: wiki_search
         max_results: 2

   llms:
      # Tell NeMo Agent Toolkit which LLM to use for the agent
      nim_llm:
         _type: nim
         model_name: nvidia/nemotron-3-nano-30b-a3b
         temperature: 0.0
         chat_template_kwargs:
            enable_thinking: false

   workflow:
      # Use an agent that 'reasons' and 'acts'
      _type: react_agent
      # Give it access to our wikipedia search tool
      tool_names: [wikipedia_search]
      # Tell it which LLM to use
      llm_name: nim_llm
      # Make it verbose
      verbose: true
      # Retry up to 3 times
      parse_agent_response_max_retries: 3
   ```

3. 使用 `nat` CLI 和 `workflow.yml` 文件运行 Hello World 示例。

   ```bash
   nat run --config_file workflow.yml --input "List five subspecies of Aardvarks"
   ```

   这将运行工作流并将结果输出到控制台。

   ```console
   Workflow Result:
   ['Here are five subspecies of Aardvarks:\n\n1. Orycteropus afer afer (Southern aardvark)\n2. O. a. adametzi  Grote, 1921 (Western aardvark)\n3. O. a. aethiopicus  Sundevall, 1843\n4. O. a. angolensis  Zukowsky & Haltenorth, 1957\n5. O. a. erikssoni  Lönnberg, 1906']
   ```

## 📚 更多资源

* 📖 [文档](https://docs.nvidia.com/nemo/agent-toolkit/latest)：浏览 NeMo Agent Toolkit 的完整文档。
* 🧭 [入门指南](./docs/source/get-started/installation.md)：设置环境并开始使用 NeMo Agent Toolkit 构建。
* 🤝 [贡献](./docs/source/resources/contributing/index.md)：了解如何为 NeMo Agent Toolkit 做贡献并设置开发环境。
* 🧪 [示例](./examples/README.md)：浏览源仓库 [`examples`](./examples) 目录中的 NeMo Agent Toolkit 工作流示例。
* 🛠️ [创建和自定义 NeMo Agent Toolkit 工作流](docs/source/get-started/tutorials/customize-a-workflow.md)：了解如何创建和自定义 NeMo Agent Toolkit 工作流。
* 🎯 [使用 NeMo Agent Toolkit 进行评估](./docs/source/improve-workflows/evaluate.md)：了解如何评估你的 NeMo Agent Toolkit 工作流。
* 🆘 [故障排除](./docs/source/resources/troubleshooting.md)：获取常见问题的帮助。

## 🛣️ 路线图

- [x] 自动强化学习 (RL) 来为特定代理微调 LLM。
- [x] 与 [NVIDIA Dynamo](https://github.com/ai-dynamo/dynamo) 集成以大规模降低 LLM 延迟。
- [x] 通过 KV-Cache 优化提升代理吞吐量。
- [ ] 改进独立评估框架，并迁移到 [ATIF](https://github.com/harbor-framework/harbor/blob/main/rfcs/0001-trajectory-format.md) 轨迹格式。
- [ ] 支持更多编程语言（TypeScript、Rust、Go、WASM）及编译库。
- [ ] 逐步淘汰包装式架构，以简化更多代理的上手流程。
- [ ] 支持为现有代理添加技能和沙箱。
- [ ] MCP 身份验证改进。
- [ ] 改进内存接口以支持自我改进的代理。

## 💬 反馈

我们期待听到你的声音！如有任何反馈或功能需求，请在 [GitHub](https://github.com/NVIDIA/NeMo-Agent-Toolkit/issues) 上提交 issue。

## 🤝 致谢

我们感谢以下团队对本工具包的贡献：

- [Synopsys](https://www.synopsys.com/)
  - Google ADK 框架支持。
  - Microsoft AutoGen 框架支持。
- [W&B Weave 团队](https://wandb.ai/site/weave/)
  - 对评估和遥测系统的贡献。

此外，我们感谢以下让 NeMo Agent Toolkit 成为可能的开源项目：

- [Agent2Agent (A2A) Protocol](https://github.com/a2aproject/A2A)
- [CrewAI](https://github.com/crewAIInc/crewAI)
- [Dynamo](https://github.com/ai-dynamo/dynamo)
- [FastAPI](https://github.com/tiangolo/fastapi)
- [Google Agent Development Kit (ADK)](https://github.com/google/adk-python)
- [LangChain](https://github.com/langchain-ai/langchain)
- [Llama-Index](https://github.com/run-llama/llama_index)
- [Mem0ai](https://github.com/mem0ai/mem0)
- [Microsoft AutoGen](https://github.com/microsoft/autogen)
- [MinIO](https://github.com/minio/minio)
- [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/modelcontextprotocol)
- [OpenTelemetry](https://github.com/open-telemetry/opentelemetry-python)
- [Phoenix](https://github.com/arize-ai/phoenix)
- [Ragas](https://github.com/explodinggradients/ragas)
- [Redis](https://github.com/redis/redis-py)
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel)
- [Strands](https://github.com/strands-agents/sdk-python)
- [uv](https://github.com/astral-sh/uv)
- [Weave](https://github.com/wandb/weave)
