# Claude Code 插件：编排与自动化

> **⚡ 已适配 Opus 4.6、Sonnet 4.6 和 Haiku 4.5** — 三层模型策略实现最优性能

[![Run in Smithery](https://smithery.ai/badge/skills/wshobson)](https://smithery.ai/skills?ns=wshobson&utm_source=github&utm_medium=badge)

> **🎯 代理技能已启用** — 147 项专业技能通过渐进式披露机制扩展 Claude 在各插件中的能力

一套全面的生产就绪系统，集成了 **182 个专业 AI 代理**、**16 个多代理工作流编排器**、**147 项代理技能**和 **95 条命令**，按 **75 个聚焦单一功能的插件**进行组织，专为 [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) 设计。

## 概述

这个统一的仓库提供了现代软件开发中智能自动化和多代理编排所需的一切：

- **75 个聚焦插件** — 粒度细、单一功能的插件，针对最小化 token 消耗和可组合性进行了优化
- **182 个专业代理** — 涵盖架构、编程语言、基础设施、质量保障、数据/AI、文档、业务运营和 SEO 的领域专家
- **147 项代理技能** — 采用渐进式披露的模块化知识包，提供专业能力
- **16 个工作流编排器** — 用于全栈开发、安全加固、ML 流水线和事件响应等复杂操作的多代理协调系统
- **95 条命令** — 经过优化的实用工具，包括项目脚手架、安全扫描、测试自动化和基础设施搭建

### 主要特性

- **粒度化插件架构**：75 个聚焦插件，针对最小化 token 消耗进行优化
- **全面的工具集**：95 条命令，包括测试生成、脚手架和安全扫描
- **100% 代理覆盖**：所有插件都包含专业代理
- **代理技能**：147 项专业技能，采用渐进式披露和 token 效率优化
- **清晰的组织结构**：23 个分类，每个分类包含 1-6 个插件，便于查找
- **高效设计**：平均每个插件 3.4 个组件（遵循 Anthropic 的 2-8 模式）

### 工作原理

每个插件完全独立，拥有自己的代理、命令和技能：

- **按需安装** — 每个插件仅加载其特定的代理、命令和技能
- **最小化 token 消耗** — 不会将不必要的资源加载到上下文中
- **自由组合** — 可组合多个插件以应对复杂工作流
- **清晰的边界** — 每个插件具有单一、聚焦的用途
- **渐进式披露** — 技能仅在激活时加载知识

**示例**：安装 `python-development` 会加载 3 个 Python 代理、1 个脚手架工具，并启用 16 项技能（约 1000 个 token），而不是加载整个市场。

## 快速开始

### 步骤 1：添加市场

将此市场添加到 Claude Code：

```bash
/plugin marketplace add wshobson/agents
```

这会使得所有 75 个插件可供安装，但**不会将任何代理或工具**加载到你的上下文中。

### 步骤 2：安装插件

浏览可用插件：

```bash
/plugin
```

安装所需的插件：

```bash
# 核心开发插件
/plugin install python-development          # Python，含 16 项专业技能
/plugin install javascript-typescript       # JS/TS，含 4 项专业技能
/plugin install backend-development         # 后端 API，含 3 项架构技能

# 基础设施与运维
/plugin install kubernetes-operations       # K8s，含 4 项部署技能
/plugin install cloud-infrastructure        # AWS/Azure/GCP，含 4 项云技能

# 安全与质量
/plugin install security-scanning           # SAST，含安全技能
/plugin install comprehensive-review       # 多视角代码分析

# 全栈编排
/plugin install full-stack-orchestration   # 多代理工作流
```

每个已安装的插件**仅将其特定的代理、命令和技能**加载到 Claude 的上下文中。

### 插件与代理

你安装的是**插件**，插件中捆绑了代理：

| 插件                    | 代理                                                |
| ----------------------- | --------------------------------------------------- |
| `comprehensive-review`  | architect-review, code-reviewer, security-auditor   |
| `javascript-typescript` | javascript-pro, typescript-pro                      |
| `python-development`    | python-pro, django-pro, fastapi-pro                 |
| `blockchain-web3`       | blockchain-developer                                |

```bash
# ❌ 错误 - 不能直接安装代理
/plugin install typescript-pro

# ✅ 正确 - 安装插件
/plugin install javascript-typescript@claude-code-workflows
```

### 故障排除

**"Plugin not found"** → 使用插件名称而非代理名称。添加 `@claude-code-workflows` 后缀。

**插件未加载** → 清除缓存并重新安装：

```bash
rm -rf ~/.claude/plugins/cache/claude-code-workflows && rm ~/.claude/plugins/installed_plugins.json
```

## 文档

### 核心指南

- **[插件参考](docs/plugins.md)** — 全部 75 个插件的完整目录
- **[代理参考](docs/agents.md)** — 按类别组织的全部 182 个代理
- **[代理技能](docs/agent-skills.md)** — 采用渐进式披露的 147 项专业技能
- **[使用指南](docs/usage.md)** — 命令、工作流和最佳实践
- **[架构](docs/architecture.md)** — 设计原则和模式
- **[PluginEval](docs/plugin-eval.md)** — 质量评估框架（层级、维度、评分）

### 快速链接

- [安装](#快速开始) — 2 步上手
- [核心插件](docs/plugins.md#quick-start---essential-plugins) — 立即提升生产力的首选插件
- [命令参考](docs/usage.md#command-reference-by-category) — 按类别组织的所有斜杠命令
- [多代理工作流](docs/usage.md#multi-agent-workflow-examples) — 预配置的编排示例
- [模型配置](docs/agents.md#model-configuration) — Haiku/Sonnet 混合编排

## 最新动态

### PluginEval — 质量评估框架（新增）

用于衡量和认证插件/技能质量的三层评估框架：

```bash
/plugin install plugin-eval@claude-code-workflows
```

- **三个评估层级** — 静态分析（即时）、LLM 评审（语义）、蒙特卡洛模拟（统计）
- **10 个质量维度** — 触发准确性、编排适配度、输出质量、范围校准、渐进式披露、token 效率、鲁棒性、结构完整性、代码模板质量、生态一致性
- **质量徽章** — 铂金 (★★★★★)、黄金 (★★★★)、白银 (★★★)、青铜 (★★)
- **反模式检测** — OVER_CONSTRAINED、EMPTY_DESCRIPTION、MISSING_TRIGGER、BLOATED_SKILL、ORPHAN_REFERENCE、DEAD_CROSS_REF
- **统计严谨性** — Wilson 分数置信区间、Bootstrap 置信区间、Clopper-Pearson 精确置信区间、Elo 排名
- **CLI + Claude Code** — `uv run plugin-eval score/certify/compare` 或 `/eval`、`/certify`、`/compare` 命令
- **CI 门控** — `--threshold` 标志在低于最低分数时以非零退出码退出

```bash
# 快速评估（仅静态分析，即时完成）
uv run plugin-eval score path/to/skill --depth quick

# 标准评估（静态分析 + LLM 评审）
uv run plugin-eval score path/to/skill --depth standard

# 完整认证（所有层级 + Elo 排名）
uv run plugin-eval certify path/to/skill
```

[→ 查看 PluginEval 文档](docs/plugin-eval.md)

### Agent Teams 插件

使用 Claude Code 实验性的 Agent Teams 功能编排多代理团队以实现并行工作流：

```bash
/plugin install agent-teams@claude-code-workflows
```

- **7 个团队预设** — `review`、`debug`、`feature`、`fullstack`、`research`、`security`、`migration`
- **并行代码审查** — `/team-review src/ --reviewers security,performance,architecture`
- **假设驱动调试** — `/team-debug "API returns 500" --hypotheses 3`
- **并行功能开发** — `/team-feature "Add OAuth2 auth" --plan-first`
- **研究团队** — 跨代码库和网络资源的并行调查
- **安全审计** — 4 个审查员覆盖 OWASP、认证、依赖项和密钥
- **迁移支持** — 具有并行流和正确性验证的协调迁移

包含 4 个专业代理、7 条命令和 6 项技能，附带参考文档。

[→ 查看 agent-teams 文档](plugins/agent-teams/README.md)

### Conductor 插件 — 上下文驱动开发

将 Claude Code 转变为项目管理工具，采用结构化的**上下文 → 规格与计划 → 实施**工作流：

```bash
/plugin install conductor@claude-code-workflows
```

- **交互式设置** — `/conductor:setup` 创建产品愿景、技术栈、工作流规则和风格指南
- **基于轨道的开发** — `/conductor:new-track` 生成规格说明和分阶段实施计划
- **TDD 工作流** — `/conductor:implement` 带验证检查点执行任务
- **语义回滚** — `/conductor:revert` 按逻辑单元（轨道、阶段或任务）撤销工作
- **状态持久化** — 通过持久化的项目上下文跨会话恢复设置
- **3 项技能** — 上下文驱动开发、轨道管理、工作流模式

[→ 查看 Conductor 文档](plugins/conductor/README.md)

### 代理技能（21 个插件中的 147 项技能）

遵循 Anthropic 渐进式披露架构的专业知识包：

**语言开发：**

- **Python**（5 项技能）：异步模式、测试、打包、性能优化、UV 包管理器
- **JavaScript/TypeScript**（4 项技能）：高级类型、Node.js 模式、测试、现代 ES6+

**基础设施与 DevOps：**

- **Kubernetes**（4 项技能）：清单文件、Helm Charts、GitOps、安全策略
- **云基础设施**（4 项技能）：Terraform、多云、混合网络、成本优化
- **CI/CD**（4 项技能）：流水线设计、GitHub Actions、GitLab CI、密钥管理

**开发与架构：**

- **后端**（3 项技能）：API 设计、架构模式、微服务
- **LLM 应用**（8 项技能）：LangGraph、提示词工程、RAG、评估、嵌入、相似性搜索、向量调优、混合搜索

**区块链与 Web3**（4 项技能）：DeFi 协议、NFT 标准、Solidity 安全、Web3 测试

**项目管理：**

- **Conductor**（3 项技能）：上下文驱动开发、轨道管理、工作流模式

**更多内容：** 框架迁移、可观测性、支付处理、ML 运维、安全扫描

[→ 查看完整技能文档](docs/agent-skills.md)

### 三层模型策略

针对最优性能和成本的策略性模型分配：

| 层级       | 模型      | 代理数量 | 用途                                                                                             |
| ---------- | --------- | -------- | ------------------------------------------------------------------------------------------------ |
| **Tier 1** | Opus 4.6  | 42       | 关键架构、安全、所有代码审查、生产编码（语言专家、框架）                                          |
| **Tier 2** | Inherit   | 42       | 复杂任务 — 用户选择模型（AI/ML、后端、前端/移动端、专业领域）                                     |
| **Tier 3** | Sonnet    | 51       | 辅助性智能任务（文档、测试、调试、网络、API 文档、开发者体验、遗留系统、支付）                     |
| **Tier 4** | Haiku     | 18       | 快速运营任务（SEO、部署、简单文档、销售、内容、搜索）                                              |

**为什么关键代理使用 Opus 4.6？**

- SWE-bench 得分 80.8%（行业领先）
- 复杂任务减少 65% 的 token 消耗
- 最适合架构决策和安全审计

**Tier 2 的灵活性（`inherit`）：**
标记为 `inherit` 的代理使用你当前的默认模型，让你在成本和能力之间取得平衡：

- 启动会话时通过 `claude --model opus` 或 `claude --model sonnet` 设置
- 如未指定默认模型，则回退到 Sonnet 4.6
- 非常适合希望控制成本的前端/移动端开发者
- AI/ML 工程师可以选择 Opus 处理复杂的模型工作

**成本考量：**

- **Opus 4.6**：每百万输入/输出 token $5/$25 — 关键工作的高级选择
- **Sonnet 4.6**：每百万 token $3/$15 — 性能与成本的平衡
- **Haiku 4.5**：每百万 token $1/$5 — 快速、经济的操作
- Opus 在复杂任务上 65% 的 token 减少量通常可抵消其更高的单价
- 使用 `inherit` 层级控制高频使用场景的成本

编排模式通过模型组合实现效率优化：

```
Opus（架构） → Sonnet（开发） → Haiku（部署）
```

[→ 查看模型配置详情](docs/agents.md#model-configuration)

## 热门使用场景

### 全栈功能开发

```bash
/full-stack-orchestration:full-stack-feature "user authentication with OAuth2"
```

协调 7 个以上代理：backend-architect → database-architect → frontend-developer → test-automator → security-auditor → deployment-engineer → observability-engineer

[→ 查看所有工作流示例](docs/usage.md#multi-agent-workflow-examples)

### 安全加固

```bash
/security-scanning:security-hardening --level comprehensive
```

多代理安全评估，包含 SAST、依赖项扫描和代码审查。

### 使用现代工具进行 Python 开发

```bash
/python-development:python-scaffold fastapi-microservice
```

创建生产就绪的 FastAPI 项目，支持异步模式，激活以下技能：

- `async-python-patterns` — AsyncIO 和并发
- `python-testing-patterns` — pytest 和 fixtures
- `uv-package-manager` — 快速依赖管理

### Kubernetes 部署

```bash
# 自动激活 k8s 技能
"Create production Kubernetes deployment with Helm chart and GitOps"
```

使用 kubernetes-architect 代理和 4 项专业技能生成生产级配置。

[→ 查看完整使用指南](docs/usage.md)

## 插件分类

**24 个分类，75 个插件：**

- 🎨 **开发**（4）— 调试、后端、前端、多平台
- 📚 **文档**（3）— 代码文档、API 规范、图表、C4 架构
- 🔄 **工作流**（5）— Git、全栈、TDD、**Conductor**（上下文驱动开发）、**Agent Teams**（多代理编排）
- ✅ **测试**（2）— 单元测试、TDD 工作流
- 🔍 **质量**（2）— 全面审查、性能
- 🤖 **AI 与 ML**（4）— LLM 应用、代理编排、上下文、MLOps
- 📊 **数据**（2）— 数据工程、数据验证
- 🗄️ **数据库**（2）— 数据库设计、迁移
- 🚨 **运维**（4）— 事件响应、诊断、分布式调试、可观测性
- ⚡ **性能**（2）— 应用性能、数据库/云优化
- ☁️ **基础设施**（5）— 部署、验证、Kubernetes、云、CI/CD
- 🔒 **安全**（4）— 扫描、合规、后端/API、前端/移动端
- 💻 **编程语言**（7）— Python、JS/TS、系统编程、JVM、脚本、函数式、嵌入式
- 🔗 **区块链**（1）— 智能合约、DeFi、Web3
- 💰 **金融**（1）— 量化交易、风险管理
- 💳 **支付**（1）— Stripe、PayPal、计费
- 🎮 **游戏**（1）— Unity、Minecraft 插件
- 📢 **营销**（4）— SEO 内容、技术 SEO、SEO 分析、内容营销
- 💼 **商业**（3）— 分析、HR/法律、客户/销售
- 更多...

[→ 查看完整插件目录](docs/plugins.md)

## 架构亮点

### 粒度化设计

- **单一职责** — 每个插件做好一件事
- **最小化 token 消耗** — 平均每个插件 3.4 个组件
- **可组合** — 自由组合应对复杂工作流
- **100% 覆盖** — 所有 182 个代理均可通过插件访问

### 渐进式披露（技能）

面向 token 效率的三层架构：

1. **元数据** — 名称和激活条件（始终加载）
2. **指令** — 核心指导（激活时加载）
3. **资源** — 示例和模板（按需加载）

### 仓库结构

```
claude-agents/
├── .claude-plugin/
│   └── marketplace.json          # 75 个插件
├── plugins/
│   ├── python-development/
│   │   ├── agents/               # 3 个 Python 专家
│   │   ├── commands/             # 脚手架工具
│   │   └── skills/               # 5 项专业技能
│   ├── kubernetes-operations/
│   │   ├── agents/               # K8s 架构师
│   │   ├── commands/             # 部署工具
│   │   └── skills/               # 4 项 K8s 技能
│   └── ...（另外 65 个插件）
├── docs/                          # 综合文档
└── README.md                      # 本文件
```

[→ 查看架构详情](docs/architecture.md)

## 贡献

添加新代理、技能或命令：

1. 在 `plugins/` 中识别或创建合适的插件目录
2. 在相应的子目录中创建 `.md` 文件：
   - `agents/` — 用于专业代理
   - `commands/` — 用于工具和工作流
   - `skills/` — 用于模块化知识包
3. 遵循命名约定（小写字母、连字符分隔）
4. 编写清晰的激活条件和全面的内容
5. 更新 `.claude-plugin/marketplace.json` 中的插件定义

详见[架构文档](docs/architecture.md)获取详细指南。

## 资源

### 文档

- [Claude Code 文档](https://docs.claude.com/en/docs/claude-code/overview)
- [插件指南](https://docs.claude.com/en/docs/claude-code/plugins)
- [子代理指南](https://docs.claude.com/en/docs/claude-code/sub-agents)
- [代理技能指南](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview)
- [斜杠命令参考](https://docs.claude.com/en/docs/claude-code/slash-commands)

### 本仓库

- [插件参考](docs/plugins.md)
- [代理参考](docs/agents.md)
- [代理技能指南](docs/agent-skills.md)
- [使用指南](docs/usage.md)
- [架构](docs/architecture.md)

## 许可证

MIT 许可证 — 详见 [LICENSE](LICENSE) 文件。

## Star 历史

[![Star History Chart](assets/001-star-history-chart-229168c8b2.svg)](https://www.star-history.com/#wshobson/agents&type=date&legend=top-left)
