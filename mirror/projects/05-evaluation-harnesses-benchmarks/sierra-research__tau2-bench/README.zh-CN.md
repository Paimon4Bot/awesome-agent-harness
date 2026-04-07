# $\tau$-Bench：真实世界领域中工具-代理-用户交互的基准测试

[![python](https://img.shields.io/badge/Python-3.12%2B-blue.svg?style=flat&logo=python&logoColor=white)](https://www.python.org)
[![Ruff](https://img.shields.io/badge/%20endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![arXiv](https://img.shields.io/badge/cs.AI-arXiv%3A2506.07982-B31B1B.svg?logo=arxiv&logoColor=red)](https://arxiv.org/abs/2506.07982)
[![blog](https://img.shields.io/badge/blog-tau--bench-green)](https://sierra.ai/blog/benchmarking-agents-in-collaborative-real-world-scenarios)
[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/sierra.svg?style=social&label=Follow%20%40SierraPlatform)](https://x.com/SierraPlatform/status/1932464265207889974)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?logo=linkedin&logoColor=white)](https://www.linkedin.com/posts/sierra_last-year-we-introduced-%F0%9D%9C%8F-bench-a-benchmark-activity-7338229693898231809-F8L4?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAdc8goBmhEsiEo1_t_XSJbAnY4_zMfAWcE)
[![Leaderboard](https://img.shields.io/badge/🏆_Live_Leaderboard-taubench.com-brightgreen?style=flat)](https://taubench.com)

<div align="center">
<img src="assets/001-traj-6dc3ddd763.png" width="95%" alt="Trajectory">
</div>

<div align="center">
<h3>🚀 τ³-bench 来了！</h3>
<p>从纯文本到多模态、知识感知的代理评估。<br>
语音全双工 · 知识检索 · 75+ 任务修复<br>
<a href="https://arxiv.org/abs/2603.13686">τ-Voice 论文</a> · <a href="https://arxiv.org/abs/2603.04370">τ-Knowledge 论文</a> · <a href="https://arxiv.org/abs/2512.07850">任务修复论文</a> · <a href="https://github.com/sierra-research/tau2-bench/releases/tag/v1.0.0">发布说明</a></p>
</div>

> **$\tau^3$-bench 怎么发音？** 我们就说"tau three"，但您随意！

## $\tau^3$-bench 的新内容

- **知识域（`banking_knowledge`）** — 一个基于知识检索的客服领域，支持可配置的 RAG 流水线、文档搜索、嵌入和基于代理 shell 的搜索。[了解更多 →](src/tau2/knowledge/README.md)
- **语音全双工（音频原生）** — 使用实时提供商（OpenAI、Gemini、xAI）进行端到端语音评估。[了解更多 →](src/tau2/voice/README.md)
- **任务质量（75+ 修复）** — 移除了不正确的预期操作，澄清了模糊的指令，修复了不可能的约束，并在航空、零售和银行领域中添加了缺失的回退行为。基于 [SABER](https://arxiv.org/abs/2512.07850)（Cuadron 等人，2025）的分析。[了解更多 →](https://taubench.com/blog/tau3-task-fixes.html)
- **更新的排行榜** — 现已包含语音和知识结果。在 [taubench.com](https://taubench.com) 比较模型性能。[提交您的结果 →](docs/leaderboard-submission.md)

完整的版本历史请参见 [CHANGELOG.md](CHANGELOG.md)。

> **向后兼容性说明**：如果您正在评估代理（而非训练），请使用 `base` 任务拆分在与原始 τ-bench 结构匹配的完整任务集上进行评估。这是默认设置。

> **从 $\tau^2$-bench 升级？** 安装现在使用 `uv` 而非 `pip install -e .`，且需要 Python `>=3.12, <3.14`（之前为 `>=3.10`）。部分内部 API 已重构——详情请参见 [CHANGELOG.md](CHANGELOG.md)。

## 概述

$\tau$-bench 是一个用于跨多个领域评估客服代理的模拟框架。它支持基于文本的半双工（回合制）评估和使用实时音频 API 的语音全双工（同步）评估。

每个领域指定：
- 代理必须遵循的**策略**
- 代理可以使用的一组**工具**
- 一组用于评估代理性能的**任务**
- 可选：一组用于用户模拟器的**用户工具**

**可用领域**：`mock` · `airline` · `retail` · `telecom` · `banking_knowledge`

| 模式 | 描述 |
|------|------|
| **文本（半双工）** | 带工具使用的回合制聊天 |
| **语音（全双工）** | 通过实时提供商（OpenAI、Gemini、xAI）的端到端音频 |

## 快速开始

### 1. 安装

```bash
git clone https://github.com/sierra-research/tau2-bench
cd tau2-bench
uv sync                        # core only (text-mode: airline, retail, telecom, mock)
```

可选扩展（按需安装）：

```bash
uv sync --extra voice          # + voice/audio-native features
uv sync --extra knowledge      # + banking_knowledge domain (retrieval pipeline)
uv sync --extra gym            # + gymnasium RL interface
uv sync --extra dev            # + pytest, ruff, pre-commit (required for contributing)
uv sync --all-extras           # everything
```

这需要 [uv](https://docs.astral.sh/uv/getting-started/installation/)。语音功能还需要系统依赖（macOS 上使用 `brew install portaudio ffmpeg`）。详情请参阅[完整安装指南](docs/getting-started.md)。

### 2. 设置 API 密钥

```bash
cp .env.example .env
# Edit .env with your API keys (uses LiteLLM — any supported provider works)
```

### 3. 运行评估

```bash
tau2 run --domain airline --agent-llm gpt-4.1 --user-llm gpt-4.1 \
  --num-trials 1 --num-tasks 5
```

结果保存到 `data/simulations/`。使用 `tau2 view` 浏览结果。

> **提示**：运行 `tau2 intro` 以获取可用领域、命令和示例的概览。

## 文档

### 入门

| 文档 | 描述 |
|------|------|
| [快速开始](docs/getting-started.md) | 安装、API 密钥、首次运行、输出结构、配置 |
| [CLI 参考](docs/cli-reference.md) | 所有 `tau2` 命令和选项 |

### 核心概念

| 文档 | 描述 |
|------|------|
| [代理开发者指南](src/tau2/agent/README.md) | 构建和评估您自己的代理 |
| [领域](src/tau2/domains/README.md) | 领域结构、数据格式和可用领域 |
| [编排器与通信模式](src/tau2/orchestrator/README.md) | 半双工和全双工编排 |

### 知识检索

| 文档 | 描述 |
|------|------|
| [知识检索](src/tau2/knowledge/README.md) | `banking_knowledge` 领域的检索流水线配置、嵌入、RAG 和沙箱设置 |

### 语音与音频

| 文档 | 描述 |
|------|------|
| [语音（全双工）](src/tau2/voice/README.md) | 语音评估的提供商、语音复杂度、CLI 选项和输出结构 |
| [音频原生架构](src/tau2/voice/audio_native/README.md) | 添加或修改实时提供商适配器的内部架构 |

### 强化学习与训练

| 文档 | 描述 |
|------|------|
| [Gym 接口](src/tau2/gym/README.md) | Gymnasium 兼容环境、play 模式、训练/测试拆分 |

### 排行榜与实验

| 文档 | 描述 |
|------|------|
| [排行榜提交](docs/leaderboard-submission.md) | 如何向 [taubench.com](https://taubench.com) 提交结果 |
| [实验](src/experiments/README.md) | 实验性功能和研究代码 |

### 项目

| 文档 | 描述 |
|------|------|
| [贡献](CONTRIBUTING.md) | 如何为 τ-bench 做贡献 |
| [更新日志](CHANGELOG.md) | 版本历史和发布说明 |

## 贡献

我们欢迎贡献！无论是修复 bug、添加功能、创建新领域还是贡献研究代码，请查看我们的[贡献指南](CONTRIBUTING.md)了解准则。

## 引用

如果您使用 $\tau^3$-bench 的特定组件，请引用下面相应的论文。

### 知识领域（`banking_knowledge`）

```bibtex
@article{shi2026tau,
  title={$\tau$-Knowledge: Evaluating Conversational Agents over Unstructured Knowledge},
  author={Shi, Quan and Zytek, Alexandra and Razavi, Pedram and Narasimhan, Karthik and Barres, Victor},
  journal={arXiv preprint arXiv:2603.04370},
  year={2026}
}
```

### 语音全双工基准测试

```bibtex

@misc{ray2026tauvoicebenchmarkingfullduplexvoice,
      title={$\tau$-Voice: Benchmarking Full-Duplex Voice Agents on Real-World Domains},
      author={Soham Ray and Keshav Dhandhania and Victor Barres and Karthik Narasimhan},
      year={2026},
      eprint={2603.13686},
      archivePrefix={arXiv},
      primaryClass={cs.SD},
      url={https://arxiv.org/abs/2603.13686},
}
```

### 核心 $\tau$-Bench

```bibtex

@misc{barres2025tau2,
      title={$\tau^2$-Bench: Evaluating Conversational Agents in a Dual-Control Environment}, 
      author={Victor Barres and Honghua Dong and Soham Ray and Xujie Si and Karthik Narasimhan},
      year={2025},
      eprint={2506.07982},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2506.07982}, 
}

@misc{yao2024tau,
      title={$\tau$-bench: A Benchmark for Tool-Agent-User Interaction in Real-World Domains}, 
      author={Shunyu Yao and Noah Shinn and Pedram Razavi and Karthik Narasimhan},
      year={2024},
      eprint={2406.12045},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2406.12045}, 
}
```

### 任务修复

```bibtex

@inproceedings{cuadron2026saber,
      title={{SABER}: Small Actions, Big Errors {\textemdash} Safeguarding Mutating Steps in {LLM} Agents},
      author={Alejandro Cuadron and Pengfei Yu and Yang Liu and Arpit Gupta},
      booktitle={ICLR 2026 Workshop on Memory for LLM-Based Agentic Systems},
      year={2026},
      url={https://openreview.net/forum?id=En2z9dckgP},
}
```
