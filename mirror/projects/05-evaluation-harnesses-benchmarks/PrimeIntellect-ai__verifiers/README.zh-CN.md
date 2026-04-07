<p align="center">
  <picture>
    <source media="(prefers-color-scheme: light)" srcset="assets/002-40c36e38-c5bd-4c5a-9cb3-f7b902cd155d-63efeed1ae.png">
    <source media="(prefers-color-scheme: dark)" srcset="assets/001-6414bc9b-126b-41ca-9307-9e982430cde8-13d42a0152.png">
    <img alt="Prime Intellect" src="assets/001-6414bc9b-126b-41ca-9307-9e982430cde8-13d42a0152.png" width="312" style="max-width: 100%;">
  </picture>
</p>

---

<h3 align="center">
Verifiers：用于 LLM 强化学习的环境
</h3>

<p align="center">
  <a href="https://docs.primeintellect.ai/verifiers">文档</a> ·
  <a href="https://app.primeintellect.ai/dashboard/environments?ex_sort=most_stars">环境中心</a> ·
  <a href="https://github.com/PrimeIntellect-ai/prime-rl">PRIME-RL</a>
</p>

---

<p align="center">
  <a href="https://github.com/PrimeIntellect-ai/verifiers/actions/workflows/style.yml">
    <img src="https://github.com/PrimeIntellect-ai/verifiers/actions/workflows/style.yml/badge.svg" alt="Style" />
  </a>
  <a href="https://github.com/PrimeIntellect-ai/verifiers/actions/workflows/test.yml">
    <img src="https://github.com/PrimeIntellect-ai/verifiers/actions/workflows/test.yml/badge.svg" alt="Test" />
  </a>
  <a href="https://github.com/PrimeIntellect-ai/verifiers/actions/workflows/publish-envs.yml">
    <img src="https://github.com/PrimeIntellect-ai/verifiers/actions/workflows/publish-envs.yml/badge.svg" alt="Envs" />
  </a>
</p>

## 新闻与更新

- [03/22/26] v0.1.12.dev0 发布准备就绪，包含 opencode RLM 环境、性能和自动伸缩改进、更强的取消/运行时处理、多模态保存保真度以及更新的开发文档。
- [03/12/26] v0.1.11 发布，包含统一的客户端栈、重大的 `RLMEnv` 和环境服务器可靠性改进、大幅优化的评估 TUI、新的 pass@k 和消融实验支持，以及捆绑的 opencode 环境。
- [02/10/26] v0.1.10 发布，包含 OpenEnv 和 BrowserEnv 集成、恢复评估、改进的 rollout 和 token 追踪、更安全的沙箱生命周期行为、刷新的工作区设置和 opencode harbor 改进。
- [01/08/26] v0.1.9 发布，包含多个新的实验性环境类类型、用于自动指标收集的监控 rubric、改进的工作区设置流程、改进的错误处理、bug 修复和文档重构。
- [11/19/25] v0.1.8 发布，包含对 rollout 系统的重大重构，使用基于轨迹的跟踪实现跨回合的 token-in token-out 训练，以及支持截断或分支 rollout。
- [11/07/25] Verifiers v0.1.7 发布！包括改进的使用 [prime-rl](https://github.com/PrimeIntellect-ai/prime-rl) 训练的快速入门配置、新的内置"nano"训练器（`vf.RLTrainer`，替代 `vf.GRPOTrainer`），以及大量 bug 修复和文档改进。
- [10/27/25] Prime Intellect [环境计划](https://docs.google.com/spreadsheets/d/13UDfRDjgIZXsMI2s9-Lmn8KSMMsgk2_zsfju6cx_pNU/edit?gid=0#gid=0)的新一轮上线！

# 概述

Verifiers 是我们用于创建环境来训练和评估 LLM 的库。

环境包含在特定任务上运行和评估模型所需的一切：
- 任务输入的*数据集*
- 模型的 *harness*（工具、沙箱、上下文管理等）
- 用于对模型性能进行评分的奖励函数或 *rubric*

环境可用于使用强化学习（RL）训练模型、评估能力、生成合成数据、实验代理 harness 等。

Verifiers 与[环境中心](https://app.primeintellect.ai/dashboard/environments?ex_sort=most_stars)以及我们的训练框架 [prime-rl](https://github.com/PrimeIntellect-ai/prime-rl) 和[托管训练](https://app.primeintellect.ai/dashboard/training)平台紧密集成。

## 快速开始

确保您已安装 `uv` 以及 `prime` [CLI](https://docs.primeintellect.ai/cli-reference/introduction) 工具：
```bash
# install uv
curl -LsSf https://astral.sh/uv/install.sh | sh
# install the prime CLI
uv tool install prime
# log in to the Prime Intellect platform
prime login
```
要设置一个新的工作区来开发环境，请执行：
```bash
# ~/dev/my-lab
prime lab setup 
```

这将设置一个 Python 项目（如果需要）（使用 `uv init`），安装 `verifiers`（使用 `uv add verifiers`），创建推荐的工作区结构，并下载有用的启动文件：
```
configs/
├── endpoints.toml      # OpenAI-compatible API endpoint configuration
├── rl/                 # Example configs for Hosted Training
├── eval/               # Example multi-environment eval configs
└── gepa/               # Example configs for prompt optimization
.prime/
└── skills/             # Bundled workflow skills for create/browse/review/eval/GEPA/train/brainstorm
environments/
└── AGENTS.md           # Documentation for AI coding agents
AGENTS.md               # Top-level documentation for AI coding agents
CLAUDE.md               # Claude-specific pointer to AGENTS.md
```

或者，将 `verifiers` 添加到现有项目中：
```bash
uv add verifiers && prime lab setup --skip-install
```

使用 Verifiers 构建的环境是自包含的 Python 模块。要初始化一个全新的环境模板，请执行：
```bash
prime env init my-env # creates a new template in ./environments/my_env
```
对于 OpenEnv 集成，使用：
```bash
prime env init my-openenv --openenv
```
然后将您的 OpenEnv 项目复制到 `environments/my_openenv/proj/` 并使用以下命令构建镜像：
```bash
uv run vf-build my-openenv
```

这将创建一个名为 `my_env` 的新模块，包含基本环境模板。
```
environments/my_env/
├── my_env.py           # Main implementation
├── pyproject.toml      # Dependencies and metadata
└── README.md           # Documentation
```

环境模块应暴露一个 `load_environment` 函数，该函数返回 Environment 对象的实例，并且可以接受自定义参数。例如：
```python
# my_env.py
import verifiers as vf

def load_environment(dataset_name: str = 'gsm8k') -> vf.Environment:
    dataset = vf.load_example_dataset(dataset_name) # 'question'
    async def correct_answer(completion, answer) -> float:
        completion_ans = completion[-1]['content']
        return 1.0 if completion_ans == answer else 0.0
    rubric = Rubric(funcs=[correct_answer])
    env = vf.SingleTurnEnv(dataset=dataset, rubric=rubric)
    return env
```

要将环境模块安装到您的项目中，请执行：
```bash
prime env install my-env # installs from ./environments/my_env
```

要从环境中心安装环境到您的项目中，请执行：
```bash
prime env install primeintellect/math-python
```

要使用任何 OpenAI 兼容模型运行本地评估，请执行：
```bash
prime eval run my-env -m gpt-5-nano # run and save eval results locally
```
评估默认使用 [Prime Inference](https://docs.primeintellect.ai/inference/overview)；在 `./configs/endpoints.toml` 中配置您自己的 API 端点。

在终端 UI 中查看本地评估结果：
```bash
prime eval tui
```

要将环境发布到[环境中心](https://app.primeintellect.ai/dashboard/environments?ex_sort=most_stars)，请执行：
```bash
prime env push --path ./environments/my_env
```

要直接从环境中心运行评估，请执行：
```bash
prime eval run primeintellect/math-python
```

## 文档

**[环境](docs/environments.md)** — 创建数据集、rubric 和自定义多回合交互协议。

**[评估](docs/evaluation.md)** - 使用您的环境评估模型。

**[训练](docs/training.md)** — 在您的环境中使用强化学习训练模型。

**[开发](docs/development.md)** — 为 verifiers 做贡献

**[API 参考](docs/reference.md)** — 理解 API 和数据结构

**[常见问题](docs/faqs.md)** - 其他常见问题。

## 引用

最初由 Will Brown（[@willccbb](https://github.com/willccbb)）创建。

如果您在研究中使用此代码，请引用：

```bibtex
@misc{brown_verifiers_2025,
  author       = {William Brown},
  title        = {{Verifiers}: Environments for LLM Reinforcement Learning},
  howpublished = {\url{https://github.com/PrimeIntellect-ai/verifiers}},
  note         = {Commit abcdefg • accessed DD Mon YYYY},
  year         = {2025}
}
```
