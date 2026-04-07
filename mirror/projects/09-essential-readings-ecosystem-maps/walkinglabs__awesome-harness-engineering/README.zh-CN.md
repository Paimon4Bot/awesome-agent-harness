# Awesome Harness Engineering [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 精选的文章、实践手册、基准测试、规范和开源项目清单，涵盖 harness 工程的核心实践：围绕 AI 代理塑造环境，使其能够可靠地工作。

Harness 工程处于上下文工程、评估、可观测性、编排、安全自治与软件架构的交汇处。本清单聚焦于让代理在实际工作流（尤其是长时间运行的编码和研究任务）中更加可靠的资源。

通用代理工具不在本清单范围内，除非该页面直接涉及 harness 设计、上下文管理、评估、运行时控制或其他对可靠性至关重要的 harness 原语。

## 目录

- [课程与学习资源](#课程与学习资源)
- [基础](#基础)
- [上下文、记忆与工作状态](#上下文记忆与工作状态)
- [约束、安全护栏与安全自治](#约束安全护栏与安全自治)
- [规范、Agent 文件与工作流设计](#规范agent-文件与工作流设计)
- [评估与可观测性](#评估与可观测性)
- [基准测试](#基准测试)
- [运行时、Harness 与参考实现](#运行时harness-与参考实现)
- [贡献](#贡献)
- [许可证](#许可证)

## 课程与学习资源

- [walkinglabs/learn-harness-engineering](https://github.com/walkinglabs/learn-harness-engineering) - 基于项目的课程仓库，围绕一个 Electron 个人知识库应用，讲解如何让 Codex 和 Claude Code 更加可靠，包含课程讲义、示例产出物和实践 harness 项目。

## 基础

- [Harness engineering: leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/) - OpenAI 的旗舰实战报告，讲解如何利用架构约束、仓库本地指令、浏览器验证和遥测技术，基于 Codex 构建大型应用。
- [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) - Anthropic 的核心文章，涵盖初始化代理、特性列表、`init.sh`、自验证以及跨多个上下文窗口的交接产出物。
- [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) - Anthropic 的后续文章，聚焦于通过更好的任务状态和评估器设计来改进长时间运行的应用生成。
- [The Anatomy of an Agent Harness](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) - LangChain 简明地将代理定义为模型加 harness，涵盖提示词、工具、中间件、编排和运行时基础设施。
- [Harness Engineering](https://martinfowler.com/articles/exploring-gen-ai/harness-engineering.html) - Thoughtworks 将 harness 工作划分为上下文工程、架构约束和对抗熵增的"垃圾回收"。
- [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) - Anthropic 关于工作流、代理、工具以及结构化系统何时优于纯提示词的全面指南。
- [Skill Issue: Harness Engineering for Coding Agents](https://www.humanlayer.dev/blog/skill-issue-harness-engineering-for-coding-agents) - 一篇务实的论证，指出编码代理效果不佳往往是 harness 问题而非模型问题。
- [Your Agent Needs a Harness, Not a Framework](https://www.inngest.com/blog/your-agent-needs-a-harness-not-a-framework) - Inngest 主张将状态、重试、追踪和并发视为一等基础设施。

## 上下文、记忆与工作状态

- [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) - Anthropic 关于将上下文窗口作为工作记忆预算来管理（而非信息垃圾场）的指导。
- [Context Engineering for AI Agents: Lessons from Building Manus](https://manus.im/blog/Context-Engineering-for-AI-Agents-Lessons-from-Building-Manus) - Manus 的详细实践手册，涵盖 KV 缓存局部性、工具掩码、文件系统记忆以及在上下文中保留有价值的失败信息。
- [Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html) - Thoughtworks 关于塑造任务环境的指导，使编码代理能够保持聚焦和高效。
- [Advanced Context Engineering for Coding Agents](https://www.humanlayer.dev/blog/advanced-context-engineering) - HumanLayer 的模式集，用于减少上下文漂移并使编码会话更容易恢复。
- [Context-Efficient Backpressure for Coding Agents](https://www.humanlayer.dev/blog/context-efficient-backpressure) - HumanLayer 关于防止代理在嘈杂或低价值工作上消耗上下文的思路。
- [OpenHands Context Condensensation for More Efficient AI Agents](https://openhands.dev/blog/openhands-context-condensensation-for-more-efficient-ai-agents) - OpenHands 的有界对话记忆设计，在保持长时间编码会话高效的同时，保留目标、进展、关键文件和失败测试。
- [Writing a good CLAUDE.md](https://www.humanlayer.dev/blog/writing-a-good-claude-md) - 一份实用指南，讲解如何创建持久、仓库本地的指令，让代理可以反复遵循。

## 约束、安全护栏与安全自治

- [Beyond permission prompts: making Claude Code more secure and autonomous](https://www.anthropic.com/engineering/claude-code-sandboxing) - Anthropic 讲解如何通过更好的沙箱化和策略设计来减少审批摩擦而不丧失控制力。
- [Code execution with MCP: building more efficient agents](https://www.anthropic.com/engineering/code-execution-with-mcp) - Anthropic 通过显式、可检查的工具边界，为代理提供受控执行能力的方法。
- [Writing effective tools for agents](https://www.anthropic.com/engineering/writing-tools-for-agents) - Anthropic 关于工具接口设计的指导，使模型更容易正确、安全地调用。
- [Mitigating Prompt Injection Attacks in Software Agents](https://openhands.dev/blog/mitigating-prompt-injection-attacks-in-software-agents) - OpenHands 的实用指南，涵盖确认模式、分析器、沙箱化和硬性策略，以降低自主编码代理中的提示词注入风险。
- [Assessing internal quality while coding with an agent](https://martinfowler.com/articles/exploring-gen-ai/ccmenu-quality.html) - Thoughtworks 主张将质量检查纳入循环，而非依赖事后的人工审查。
- [Anchoring AI to a reference application](https://martinfowler.com/articles/exploring-gen-ai/anchoring-to-reference.html) - Thoughtworks 关于用具体范例约束代理，使其产出更加一致的思路。
- [Humans and Agents in Software Engineering Loops](https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html) - 一个清晰的心智模型，说明人类应该在何处加强 harness，而非对每个产出物进行微观管理。
- [Claude Code: Best practices for agentic coding](https://code.claude.com/docs) - Anthropic 关于在代理式编码工作流中仓库结构、检查点、验证和委派的实用建议。

## 规范、Agent 文件与工作流设计

- [AGENTS.md](https://github.com/agentsmd/agents.md) - 轻量级开放格式，用于仓库本地指令，告诉代理如何在代码库中工作。
- [agent.md](https://github.com/agentmd/agent.md) - 一个相关的标准化项目，面向跨项目和工具的机器可读代理指令。
- [GitHub Spec Kit](https://github.com/github/spec-kit) - GitHub 的规范驱动开发工具包，当你希望代理按照显式产品和工程规范执行时非常有用。
- [Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) - Thoughtworks 讲解为什么强规范能让 AI 辅助的软件交付更加可靠。
- [12 Factor Agents](https://www.humanlayer.dev/blog/12-factor-agents) - HumanLayer 的生产级代理运营原则，包括显式提示词、状态所有权和干净的暂停-恢复行为。
- [12-Factor AgentOps](https://www.12factoragentops.com/) - 一个面向运维的配套方案，聚焦于上下文纪律、验证和可复现的代理工作流。

## 评估与可观测性

- [Testing Agent Skills Systematically with Evals](https://developers.openai.com/blog/eval-skills/) - OpenAI 的具体指南，讲解如何将代理轨迹转化为可重复的评估，使用 JSONL 日志和确定性检查。
- [How to Evaluate Agent Skills (And Why You Should)](https://openhands.dev/blog/evaluating-agent-skills) - OpenHands 的实操手册，使用有界任务、确定性验证器、无技能基线和轨迹审查来衡量技能是否真正有用。
- [Agent evals](https://platform.openai.com/docs/guides/agent-evals) - OpenAI 的产品指南，用于通过可复现的任务级和工作流级评估来衡量代理质量。
- [Evaluation best practices](https://platform.openai.com/docs/guides/evaluation-best-practices) - OpenAI 关于构建匹配真实世界分布并尽早发现回归的评估套件的一般指南。
- [Trace grading](https://platform.openai.com/docs/guides/trace-grading) - OpenAI 关于直接对代理轨迹进行评分的文档，对长时间多步任务尤其有帮助。
- [Learning to Verify AI-Generated Code](https://openhands.dev/blog/20260305-learning-to-verify-ai-generated-code) - OpenHands 概述了一种分层验证栈，使用基于生产轨迹训练的轨迹评判器进行重排序、早停和审查时的质量控制。
- [Demystifying Evals for AI Agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) - Anthropic 关于在代理存在多种可能的成功或失败路径时该测量什么的指导。
- [Quantifying infrastructure noise in agentic coding evals](https://www.anthropic.com/engineering/infrastructure-noise) - Anthropic 讲解运行时配置如何使编码基准测试分数的波动超过许多排行榜上的差距。
- [Evaluating Deep Agents: Our Learnings](https://blog.langchain.com/evaluating-deep-agents-our-learnings/) - LangChain 对有状态代理的单步评估、全流程评估和多轮评估设计的实践分解。
- [Improving Deep Agents with harness engineering](https://blog.langchain.com/improving-deep-agents-with-harness-engineering/) - LangChain 用证据表明，仅凭 harness 改进就能显著提升基准测试性能。

## 基准测试

当你想要比较 harness 质量而不仅仅是模型质量时，这些基准测试尤其有用。它们考验上下文处理、工具调用、环境控制、验证逻辑以及围绕模型的运行时脚手架。

- [Agent Arena](https://www.agent-arena.com/leaderboard) - 一个使用 ELO 评级系统通过对战来对 AI 代理、模型、工具和框架进行排名的排行榜，提供了一种结构化的方式来跨类别比较 harness 级别的选择。
- [AgentBench](https://github.com/THUDM/AgentBench) - 跨环境基准测试，涵盖操作系统、数据库、知识图谱、网页浏览等，可用于检验 harness 是否能超越单一狭窄任务循环进行泛化。
- [AgentBoard](https://github.com/HKUST-NLP/AgentBoard) - 面向多轮 LLM 代理的基准测试，配有分析评估面板，可在最终成功率之外评估模型表现，使部分进展和轨迹质量可见。
- [AgentStudio](https://github.com/SkyworkAI/agent-studio) - 集成式基准测试套件，配有逼真的环境和综合工具包，用于在真实计算机软件上评估虚拟代理，适合衡量 harness 在广泛任务面上的深度。
- [AppWorld](https://appworld.dev/) - 一个由应用和人组成的可控世界，用于对交互式编码代理进行基准测试，配有基于状态和基于执行的单元测试，能揭示规划、代码生成和附带损害控制方面的 harness 质量。
- [AssistantBench](https://github.com/oriyor/AssistantBench) - 评估网页代理在需要多步工具使用和信息综合的、耗时真实研究任务上表现的基准测试，是长周期网页场景下 harness 质量的良好代理指标。
- [BrowseComp](https://www.kaggle.com/benchmarks/openai/browsecomp) - 评估 AI 代理定位难找信息能力的基准测试，在困难条件下考验搜索策略、上下文管理和检索 harness 设计。
- [BrowserGym Leaderboard](https://huggingface.co/spaces/ServiceNow/browsergym-leaderboard) - 用于在网页导航任务上评估 LLM、VLM 和代理的健身房环境和排行榜，提供一个可复现的框架，在一个地方跨多个网页基准测试比较 harness。
- [CharacterEval](https://github.com/morecry/CharacterEval) - 使用多轮对话和角色档案评估角色扮演对话代理的基准测试，在角色保真度和对话连贯性等四个维度上提供指标。
- [ClawBench](https://clawbench.net) - 跨搜索、推理、编码、安全和多轮对话任务评估 AI 代理的基准测试，在单一套件中覆盖 harness 需求的广度。
- [ClawWork](https://github.com/HKUDS/ClawWork) - 一个真实世界经济基准测试，AI 代理完成横跨 44 个职业的专业任务，在管理 token 成本和经济偿付能力的同时赚取收入，直接测试资源约束下的 harness 效率。
- [Computer Agent Arena](https://github.com/xlang-ai/computer-agent-arena) - 一个开放评估平台，用户在从通用计算机使用到编码、数据分析和视频编辑的真实计算机任务上比较基于 LLM/VLM 的代理，在广泛任务面上暴露 harness 差异。
- [EvoClaw: Evaluating AI Agents on Continuous Software Evolution](https://openhands.dev/blog/evoclaw-benchmark) - 一篇关于在真实仓库历史的依赖里程碑序列上评估代理的基准测试文章，揭示回归积累和长周期精度损失。
- [GAIA](https://huggingface.co/datasets/gaia-benchmark/GAIA) - 通用 AI 助手的基准测试，常用于比较围绕工具、规划、验证和长周期自治的 harness 级别选择。
- [Galileo Agent Leaderboard](https://huggingface.co/spaces/galileo-ai/agent-leaderboard) - 一个开放评估平台，跟踪 LLM 代理在跨业务领域的任务完成和工具调用上的表现，适合比较企业级代理场景中的 harness 质量。
- [GTA](https://github.com/open-compass/GTA) - 使用人工编写的查询、真实部署的工具和真实多模态输入来评估基于 LLM 的代理工具使用能力的基准测试，暴露独立测试与真实部署之间的 harness 缺口。
- [HAL: Holistic Agent Leaderboard](https://hal.cs.princeton.edu/) - 关注可靠性、成本和广泛任务覆盖的代理系统基准测试和排行榜，适合比较端到端的 harness 行为。
- [Introducing Terminal-Bench 2.0 and Harbor](https://www.tbench.ai/news/announcement-2-0) - Terminal-Bench 2.0 公告，有助于理解 Harbor 背后更难的任务和通用化评估 harness。
- [LeetCode-Hard Gym](https://github.com/GammaTauAI/leetcode-hard-gym) - LeetCode 提交服务器的 RL 环境接口，用于评估代码生成代理，让 harness 能直接获取困难算法问题上的执行反馈。
- [LLM Colosseum Leaderboard](https://github.com/OpenGenerativeAI/llm-colosseum) - 通过让 LLM 在 Street Fighter III 中对战来评估 LLM 的平台，测试速度、适应性和实时决策能力，作为紧延迟约束下 harness 响应能力的代理指标。
- [MAgIC](https://zhiyuanhubj.github.io/MAgIC/) - 在多代理系统中衡量 LLM 认知、适应性、理性和协作能力的基准测试，适合评估 harness 如何协调代理交互和共享状态。
- [MCP Bench](https://github.com/modelscope/MCPBench) - 评估 AI 模型在 MCP 服务器交互上表现的基准测试，衡量跨服务器类型的工具准确率、延迟和 token 使用量，直接反映 MCP 集成相关的 harness 设计选择。
- [MCP Universe](https://mcp-universe.github.io/) - 比较 AI 模型在 MCP 任务上表现的排行榜，跟踪不同模型和 harness 配置如何处理工具增强的代理工作流。
- [MCPMark](https://github.com/eval-sys/mcpmark) - 用于在 Notion、GitHub 和 Postgres 等工具的真实 MCP 任务中对模型和代理能力进行压力测试的基准测试，使 harness 的 MCP 集成质量可直接衡量。
- [Olas Predict Benchmark](https://github.com/valory-xyz/olas-predict-benchmark) - 在历史预测市场数据上评估代理的基准测试，测试长周期推理任务中研究、检索和预测的 harness 设计。
- [OSWorld](https://os-world.github.io/) - 真实计算机使用基准测试，包含横跨 Ubuntu、Windows 和 macOS 的 369 个任务，配有初始状态设置和基于执行的评估器，非常适合测试桌面和多模态 harness。
- [OSWorld-MCP](https://osworld-mcp.github.io) - OSWorld 的扩展，使用 Model Context Protocol 在真实计算机任务上评估 AI 代理，适合在真实桌面任务套件上比较启用 MCP 的 harness。
- [SEC-bench](https://github.com/SEC-bench/SEC-bench) - 在真实世界软件安全任务（包括漏洞复现和修补）上评估 LLM 代理的基准测试，考验围绕代码执行、容器化环境和安全感知工具的 harness 设计。
- [SWE-bench Verified](https://www.swebench.com/) - 面向在真实 GitHub 问题和测试上工作的软件工程代理的强基准测试，使围绕检索、补丁和验证的 harness 选择高度可见。
- [τ-Bench](https://github.com/sierra-research/tau-bench) - 模拟用户与配备领域特定 API 工具和策略指南的语言代理之间动态对话的基准测试，适合评估围绕结构化工具使用和策略执行的 harness。
- [tau2-bench](https://github.com/sierra-research/tau2-bench) - 面向真实多步代理任务的基准测试，成功取决于工具使用和执行质量，而非单次回答。
- [Terminal-Bench](https://www.tbench.ai/) - 面向在 shell、文件系统和重度验证环境中运行的终端原生代理的基准测试套件，特别适合比较编码代理的 harness。
- [TravelPlanner](https://github.com/OSU-NLP-Group/TravelPlanner) - 评估 LLM 代理在多重约束下使用工具和复杂规划能力的基准测试，揭示 harness 设计如何处理多约束满足和长周期规划。
- [VAB](https://github.com/THUDM/VisualAgentBench) - VisualAgentBench 在具身、GUI 和视觉设计任务上评估大型多模态模型作为视觉基础代理的表现，适合在以视觉为基础的多步代理工作流上比较 harness。
- [VisualWebArena](https://jykoh.com/vwa) - 面向多模态网页代理在真实视觉基础任务上的基准测试，通过图像和截图输入扩展了 WebArena，考验 harness 在浏览器环境中对视觉上下文的支持。
- [WebArena](https://webarena.dev/) - 独立、可自托管的网页环境，用于在真实任务上评估自主代理，是比较面向网页的 harness 设计的可复现基线。
- [WebArena-Verified](https://github.com/ServiceNow/webarena-verified) - 经验证的网页代理基准测试，配有精心筛选的任务和针对代理响应及捕获的网络轨迹的确定性评估器，适合衡量面向网页的 harness。
- [WildClawBench](https://github.com/InternLM/WildClawBench) - 野外基准测试，在实时 OpenClaw 环境中运行 60 个原创任务的代理，包括多模态、长周期和安全关键场景，使真实世界条件下的 harness 稳健性直接可见。
- [WorkArena](https://github.com/ServiceNow/WorkArena) - 面向浏览器代理在常见知识工作任务的基准测试，适合在真实企业风格网页工作流（而非玩具浏览器任务）上比较 harness。

## 运行时、Harness 与参考实现

- [Agent Frameworks, Runtimes, and Harnesses, Oh My!](https://blog.langchain.com/agent-frameworks-runtimes-and-harnesses-oh-my/) - LangChain 对框架、运行时和 harness 各自职责的拆解分析。
- [Building agents with the Claude Agent SDK](https://claude.com/blog/building-agents-with-the-claude-agent-sdk) - Anthropic 的面向生产的代理 SDK 指南，包含会话、工具和编排支持。
- [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) - Anthropic 的多代理系统架构文章，涵盖角色分离和结构化协调。
- [deepagents](https://github.com/langchain-ai/deepagents) - LangChain 的开源项目，用于使用中间件和 harness 模式构建更深层次、更长运行的代理。
- [SWE-agent](https://github.com/SWE-agent/SWE-agent) - 成熟的研究编码代理，使 harness、提示词、工具和环境设计可直接检查。
- [SWE-ReX](https://github.com/SWE-agent/SWE-ReX) - 面向 AI 代理的沙箱化代码执行基础设施，当 harness 工作开始融入执行运行时设计时非常有用。
- [AgentKit](https://github.com/inngest/agent-kit) - Inngest 的 TypeScript 工具包，用于在事件驱动基础设施之上构建持久的、工作流感知的代理。
- [Harbor](https://github.com/harbor-framework/harbor) - 通用化 harness，用于大规模评估和改进代理，随 Terminal-Bench 2.0 一同发布。
- [Harness Evolver](https://github.com/raphaelchristi/harness-evolver) - Claude Code 插件，使用多代理提案器、LangSmith 支持的评估和 git worktree 隔离，自主进化 LLM 代理 harness。基于 Meta-Harness (Lee et al., 2026)。

## 贡献

欢迎贡献。请优先选择以下资源：

- 具体说明代理如何被约束、评估、恢复、观察或编排的内容
- 原始实现、一手来源文章或高信噪比的技术文章
- 对构建真实 harness 的实践者有用，而非泛泛的 AI 评论

如果两个链接说的是同一件事，请优先选择更原始、更实用、更面向实现的那一个。

有关贡献指南和首选的条目格式，请参阅 [CONTRIBUTING.md](./CONTRIBUTING.md)。

## 许可证

[CC0 1.0](./LICENSE)
