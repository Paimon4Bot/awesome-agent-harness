# TermiGen: 面向终端智能体的高保真环境

**TermiGen** 的官方实现与数据集。TermiGen 是一个通过可验证环境与错误纠正轨迹来训练鲁棒终端智能体的框架。

📄 **论文：** [TermiGen: High-Fidelity Environment and Robust Trajectory Synthesis for Terminal Agents](https://arxiv.org/abs/2602.07274)  
🤖 **模型：** [TermiGen-32B](https://huggingface.co/UCSB-SURFI/TerminGen-32B)  
🧪 **基准：** [TerminalBench](https://github.com/laude-institute/terminal-bench)

---

## 📰 新闻

- [2026/02/23] TermiGen 已集成到 [harbor framework](https://harborframework.com/registry)！只需安装 harbor 并运行 `uvx harbor run -d termigen-environments@1.0`！
- [2026/02/10] 很荣幸入选 #2 [🤗 Huggingface Daily Papers](https://huggingface.co/papers/2602.07274)！

## 🎯 包含内容

本仓库提供：

1. **3,500+ 个已验证的 Docker 环境** - 涵盖 11 个类别的可执行任务。TerminalBench 1.0 格式以 ZIP 压缩包形式提供（因为部分任务涉及包含 `.git` 元数据的 GitHub 仓库），而 Harbor 2.0 格式则直接以 `environments_harbor/` 目录形式提供。
2. **BashAgent** - 极简 ReAct 风格智能体实现：
   - `bash_agent.py` - 用于 [TerminalBench](https://github.com/laude-institute/terminal-bench)（`tb`）框架
   - `bash_agent_harbor.py` - 用于 [Harbor](https://github.com/laude-institute/harbor) 评测框架

---

## 📊 性能

我们的 TermiGen-32B 达到：

| 基准 | Pass@1 |
|-----------|--------|
| TerminalBench 1.0 | **31.3%** |
| TerminalBench 2.0 | **19.3%** |
| SWE-Bench Verified | **21.4%** |

- 在 TerminalBench 1.0 上，相较基础 Qwen2.5-Coder-32B 绝对提升 **+26.8%**
- 在 TerminalBench 1.0 上，相较使用 Codex CLI 的 o4-mini 绝对提升 **+11.3%**

---

## 🗂️ 环境类别

我们的环境覆盖 **3 个层级**、共 **11 个任务类别**：

### Tier I: 基础设施与核心系统
- 🛠️ **软件构建与编译**：gcc、cmake、rustc、makefile 调试
- ⚙️ **系统管理与 DevOps**：Docker、Kubernetes、systemd、nginx
- 🔐 **安全与逆向工程**：Ghidra、Wireshark、gdb、Metasploit

### Tier II: 数据与算法应用
- 📊 **数据处理与 ETL**：Spark、Kafka、Parquet、SQL 转换
- 🤖 **机器学习与 MLOps**：PyTorch、CUDA、Hugging Face、模型调试
- 🧩 **算法与逻辑**：图算法、动态规划、搜索

### Tier III: 专业领域
- 💻 **软件开发**：React、Django、REST APIs、CI/CD
- 🧪 **科学计算**：Bioconductor、RDKit、GROMACS、NumPy
- 🎮 **交互式环境**：WebSocket、SSH、Jupyter、REPL
- 🌐 **分布式计算**：MPI、OpenMP、Ray、SLURM
- 🔬 **形式化验证**：Coq、Z3、OpenGL、Vulkan

**统计：**
- 420 个独特的命令行工具
- 16 个功能领域
- 任务平均复杂度：25.5 轮，8,722 tokens

---

## 🚀 快速开始

### 第 1 步：下载仓库
```bash
# Clone repository
git clone https://github.com/ucsb-mlsec/terminal-bench-env.git
cd terminal-bench-env

# Extract environments (TerminalBench 1.0 format)
unzip termigen_env.zip -d environments/

# Harbor 2.0 format is already included as environments_harbor/
```

### 第 2 步：部署 TermiGen 模型
```bash
# Install vLLM
pip install vllm

# Deploy model (requires GPU)
vllm serve UCSB-SURFI/TermiGen-32B \
  --port 8000 \
  --tensor-parallel-size 4 \
  --dtype bfloat16
```

### 第 3 步：在 TerminalBench 上运行 BashAgent
```bash
# Install dependencies
pip install openai
pip install terminal-bench

# Set environment variables
export MODEL_ENDPOINT="http://localhost:8000/v1"
export MODEL_NAME="UCSB-SURFI/TermiGen-32B"

# Run agent on TerminalBench 1.0 (example task: hello-world)
tb run --dataset terminal-bench-core==0.1.1 --agent-import-path bash_agent:BashAgent --task-id hello-world --log-level debug
```

**或者使用 Harbor 2.0：**
```bash
pip install harbor

# Run agent on local tasks
harbor run -p environments_harbor/ \
  --agent-import-path bash_agent_harbor:BashAgent \
  -t hello-world --debug

# Run agent on Terminal-Bench 2.0 (downloads from registry)
harbor run -d terminal-bench@2.0 \
  --agent-import-path bash_agent_harbor:BashAgent \
  --n-concurrent 4 --n-attempts 5 -e e2b

# Run agent on SWE-Bench Verified
harbor run -d swebench-verified \
  --agent-import-path bash_agent_harbor:BashAgent \
  --n-concurrent 4 -e e2b
```

---

## 🔧 环境细节

### 使用单个任务

在解压环境后（见第 1 步）：
```bash
# TerminalBench 1.0
tb run --agent claude-code --model anthropic/claude-sonnet-4-5-20250929 --dataset-path environments --task-id a_b_testing_models_medium --log-level debug --n-concurrent 1

# Harbor 2.0
harbor run -a claude-code -m anthropic/claude-sonnet-4-5-20250929 -p environments_harbor/ -t a_b_testing_models_medium --debug
```

### 使用完整数据集
```bash
# TerminalBench 1.0
tb run --agent claude-code --model anthropic/claude-sonnet-4-5-20250929 --dataset terminal-bench-core==0.1.1 --dataset-path environments --log-level debug --n-concurrent 2

# Harbor 2.0
harbor run -a claude-code -m anthropic/claude-sonnet-4-5-20250929 -p environments_harbor/ -n 2 --debug
# try using smaller n for stability.
```

### 任务结构

每个任务均提供两种格式：

**TerminalBench 1.0** (`termigen_env.zip`)：
```
task_name/
├── task.yaml              # Task description and metadata
├── Dockerfile             # Environment specification  
├── docker-compose.yaml    # Container orchestration
├── run-tests.sh          # Test execution script
├── tests/                # Unit tests (pytest)
│   └── test_*.py
└── [task files]          # Source code, configs, data, git repos
```

**Harbor 2.0** (`environments_harbor/`)：
```
task_name/
├── task.toml              # Task metadata
├── instruction.md         # Task description
├── environment/
│   └── Dockerfile         # Environment specification
├── tests/
│   └── test.sh           # Test script with reward logging
└── [task files]          # Source code, configs, data, git repos
```

---

## 📁 仓库结构
```
terminal-bench-env/
├── README.md                      # This file
├── bash_agent.py                  # BashAgent for TerminalBench (tb) framework
├── bash_agent_harbor.py           # BashAgent for Harbor framework
├── termigen_env.zip               # 3,500+ Docker tasks (TerminalBench 1.0 format)
├── environments/                  # Extracted from termigen_env.zip (after unzip)
└── environments_harbor/           # 3,500+ Docker tasks in Harbor 2.0 format
```

---

## 🤖 BashAgent

针对不同评测框架，提供了两个实现：

### `bash_agent.py`（TerminalBench / `tb` 框架）
- 通过 `TmuxSession` 与环境交互（send_keys、增量输出）
- 支持 asciinema 录制与详细的失败模式跟踪
- `command_duration_sec`：命令超时时间（秒，默认：10.0）

### `bash_agent_harbor.py`（Harbor 框架）
- 使用 Harbor 的 `BaseEnvironment.exec()` API 的异步实现
- 兼容 Harbor 的 e2b、Docker、Daytona 及其他环境后端
- `timeout_sec`：命令超时时间（秒，默认：120）

### 共享配置

两个智能体都可通过环境变量或构造参数接受以下配置：
- `MODEL_ENDPOINT`：模型 API URL（兼容 OpenAI，默认：`http://172.17.0.1:8001/v1`）
- `MODEL_NAME`：模型标识符
- `max_episodes`：最大对话轮数（默认：1000）
- `temperature`：采样温度（默认：0.6）

### 模型兼容性

✅ **完全支持**：Qwen2.5-Coder、TermiGen 模型（支持 `"tool"` message role）

⚠️ **需要修改**：不支持 `"tool"` role 的模型，需要将 observation message role 改为：
```python
# Change from:
{"role": "tool", "content": observation}

# To:
{"role": "user", "content": f"Observation: {observation}"}
```

---

## 🔄 复现基准结果

### Terminal-Bench 2.0 (19.3%)

```bash
# 1. Deploy model
vllm serve UCSB-SURFI/TermiGen-32B --port 8001 --tensor-parallel-size 2

# 2. Run evaluation (89 tasks × 5 attempts)
MODEL_NAME=UCSB-SURFI/TermiGen-32B \
MODEL_ENDPOINT=http://127.0.0.1:8001/v1 \
harbor run -d terminal-bench@2.0 \
  --agent-import-path bash_agent_harbor:BashAgent \
  --job-name tb2_termigen \
  --n-concurrent 4 --n-attempts 5 -e e2b
```

### SWE-Bench Verified (21.4%)

```bash
# Same model deployment as above, then:
MODEL_NAME=UCSB-SURFI/TermiGen-32B \
MODEL_ENDPOINT=http://127.0.0.1:8001/v1 \
harbor run -d swebench-verified \
  --agent-import-path bash_agent_harbor:BashAgent \
  --job-name swebench_verified_termigen \
  --n-concurrent 4 --n-attempts 1 -e e2b
```

> **注意：** 这些基准使用 [e2b](https://e2b.dev) 云沙箱（`-e e2b`）。你也可以使用本地 Docker（`-e docker`）。

<!-- ---

## 🔬 关键特性

### 高保真环境
- ✅ **100% 可执行**：每个环境都通过 Docker 构建与单元测试完成验证
- ✅ **覆盖多样**：涵盖从底层系统操作到科学计算的 11 个类别
- ✅ **自动化验证**：Judge Agent 确保任务可解

### 错误纠正训练
- 🔄 **主动错误注入**：20% 的轨迹步骤包含有意引入的错误
- 🎯 **5 类失败类型**：分析错误、命令错误、幻觉、违反要求、验证失败
- 📈 **+43% 提升**：相较标准 SFT，错误纠正训练带来更高表现 -->

---

## 📖 引用

如果你在研究中使用了 TermiGen，请引用：
```bibtex
@article{zhu2026termigen,
  title={TermiGen: High-Fidelity Environment and Robust Trajectory Synthesis for Terminal Agents},
  author={Zhu, Kaijie and Nie, Yuzhou and Li, Yijiang and Huang, Yiming and Wu, Jialian and Liu, Jiang and Sun, Ximeng and Yin, Zhenfei and Wang, Lun and Liu, Zicheng and Barsoum, Emad and Wang, William Yang and Guo, Wenbo},
  journal={arXiv preprint arXiv:2602.07274},
  url={https://arxiv.org/abs/2602.07274}, 
  year={2026}
}
```

---

## 🤝 贡献

欢迎贡献！你可以：
- 通过 [GitHub Issues](https://github.com/ucsb-mlsec/terminal-bench-env/issues) 报告 bug 或请求新特性
- 提交 pull request，修复 bug 或改进我们的环境与任务

---

## 📧 联系方式

- **第一作者**：Kaijie Zhu (kaijiezhu@ucsb.edu)
- **问题反馈**：[GitHub Issues](https://github.com/ucsb-mlsec/terminal-bench-env/issues)
- **论文**：[arXiv](https://arxiv.org/abs/XXXX.XXXXX)

---

## 🙏 致谢

- **基础模型**：[Qwen2.5-Coder](https://huggingface.co/Qwen/Qwen2.5-Coder-32B-Instruct)，由 Alibaba Cloud 提供
- **基准**：[TerminalBench](https://github.com/laude-institute/terminal-bench)，由 Laude Institute 提供
- **算力**：AMD MI325X GPUs
- **机构**：UC Santa Barbara、UC San Diego、AMD、University of Oxford、Google
