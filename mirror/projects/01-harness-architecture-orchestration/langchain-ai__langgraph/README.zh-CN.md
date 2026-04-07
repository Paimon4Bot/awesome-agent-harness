<div align="center">
  <a href="https://www.langchain.com/langgraph">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/001-logo-dark-ca69196b81.svg">
      <source media="(prefers-color-scheme: light)" srcset="assets/002-logo-light-e2a9640e05.svg">
      <img alt="LangGraph Logo" src="assets/001-logo-dark-ca69196b81.svg" width="50%">
    </picture>
  </a>
</div>

<div align="center">
  <h3>用于构建有状态智能体的底层编排框架。</h3>
</div>

<div align="center">
  <a href="https://opensource.org/licenses/MIT" target="_blank"><img src="https://img.shields.io/pypi/l/langgraph" alt="PyPI - License"></a>
  <a href="https://pypistats.org/packages/langgraph" target="_blank"><img src="https://img.shields.io/pepy/dt/langgraph" alt="PyPI - Downloads"></a>
  <a href="https://pypi.org/project/langgraph/" target="_blank"><img src="https://img.shields.io/pypi/v/langgraph.svg?label=%20" alt="Version"></a>
  <a href="https://x.com/langchain" target="_blank"><img src="https://img.shields.io/twitter/url/https/twitter.com/langchain.svg?style=social&label=Follow%20%40LangChain" alt="Twitter / X"></a>
</div>

<br>

LangGraph 受到 Klarna、Replit、Elastic 等众多正在塑造智能体未来的公司的信赖，是一个用于构建、管理和部署长时间运行的有状态智能体的底层编排框架。

```bash
pip install -U langgraph
```

如果你想使用 LangChain 的 `create_agent`（基于 LangGraph 构建）来快速创建智能体，请参阅 [LangChain 智能体文档](https://docs.langchain.com/oss/python/langchain/agents)。

> [!NOTE]
> 正在寻找 JS/TS 版本？请查看 [LangGraph.js](https://github.com/langchain-ai/langgraphjs) 和 [JS 文档](https://docs.langchain.com/oss/javascript/langgraph/overview)。

## 为什么使用 LangGraph？

LangGraph 为 *任何* 长时间运行的有状态工作流或智能体提供底层支撑基础设施：

- **[持久化执行](https://docs.langchain.com/oss/python/langgraph/durable-execution)** — 构建能够在故障后继续运行并可长时间运行的智能体，自动从中断处精确恢复。
- **[人在环](https://docs.langchain.com/oss/python/langgraph/interrupts)** — 通过在执行过程中的任意时刻检查和修改智能体状态，无缝引入人工监督。
- **[全面的记忆能力](https://docs.langchain.com/oss/python/langgraph/memory)** — 创建真正有状态的智能体，同时具备用于持续推理的短期工作记忆和跨会话的长期持久记忆。
- **[使用 LangSmith 调试](https://www.langchain.com/langsmith)** — 借助可视化工具深入了解复杂的智能体行为，追踪执行路径、捕获状态转换，并提供详细的运行时指标。
- **[生产就绪的部署](https://docs.langchain.com/langsmith/deployments)** — 借助专为应对有状态、长时间运行工作流独特挑战而设计的可扩展基础设施，自信地部署复杂的智能体系统。

> [!TIP]
> 如需开发、调试和部署 AI 智能体及 LLM 应用，请参阅 [LangSmith](https://docs.langchain.com/langsmith/home)。

## LangGraph 生态系统

LangGraph 可以独立使用，也能与任何 LangChain 产品无缝集成，为开发者提供构建智能体的完整工具集。

为了提升你的 LLM 应用开发体验，可以将 LangGraph 与以下工具搭配使用：

- [Deep Agents](https://github.com/langchain-ai/deepagents) *(全新！)* – 构建能够规划、使用子智能体并利用文件系统完成复杂任务的智能体。
- [LangChain](https://docs.langchain.com/oss/python/langchain/overview) – 提供集成和可组合组件，简化 LLM 应用开发流程。
- [LangSmith](https://www.langchain.com/langsmith) – 有助于进行智能体评估和可观测性分析。调试表现不佳的 LLM 应用运行、评估智能体轨迹、获得生产环境可见性，并持续优化性能。
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployments) – 使用专为长时间运行的有状态工作流打造的部署平台，轻松部署和扩展智能体。可在团队间发现、复用、配置和共享智能体，并通过 [LangSmith Studio](https://docs.langchain.com/langsmith/studio) 中的可视化原型快速迭代。

---

## 文档

- [docs.langchain.com](https://docs.langchain.com/oss/python/langgraph/overview) – 综合文档，包含概念概述和使用指南
- [reference.langchain.com/python/langgraph](https://reference.langchain.com/python/langgraph) – LangGraph 包的 API 参考文档
- [LangGraph 快速入门](https://docs.langchain.com/oss/python/langgraph/quickstart) – 开始使用 LangGraph 构建
- [Chat LangChain](https://chat.langchain.com/) – 与 LangChain 文档对话，获取你问题的答案

**讨论交流**：访问 [LangChain 论坛](https://forum.langchain.com) 与社区交流，分享你的技术问题、想法和反馈。

## 更多资源

- **[指南](https://docs.langchain.com/oss/python/learn)** – 关于流式处理、添加记忆与持久化、以及设计模式（如分支、子图等）主题的快速实用代码片段。
- **[LangChain Academy](https://academy.langchain.com/courses/intro-to-langgraph)** – 通过我们的免费结构化课程学习 LangGraph 基础知识。
- **[案例研究](https://www.langchain.com/built-with-langgraph)** – 了解行业领导者如何使用 LangGraph 大规模交付 AI 应用。
- [贡献指南](https://docs.langchain.com/oss/python/contributing/overview) – 了解如何为 LangChain 项目做贡献并找到适合新手的 issue。
- [行为准则](https://github.com/langchain-ai/langchain/?tab=coc-ov-file) – 我们的社区准则和参与标准。

---

## 致谢

LangGraph 的设计灵感来源于 [Pregel](https://research.google/pubs/pub37252/) 和 [Apache Beam](https://beam.apache.org/)。公开接口的设计借鉴了 [NetworkX](https://networkx.org/documentation/latest/)。LangGraph 由 LangChain Inc（LangChain 的创建者）开发，但可以独立于 LangChain 使用。
