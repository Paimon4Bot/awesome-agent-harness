# OpenHands 基准测试

本仓库包含 [OpenHands](https://github.com/OpenHands/OpenHands/) 代理的基准测试评估基础设施。它提供了标准化的评估流水线，用于在各种现实世界任务中测试代理能力。

⚠️ **迁移进行中**：我们目前正在将 [OpenHands V0 的基准测试](https://github.com/OpenHands/OpenHands/tree/main/evaluation)迁移到 V1 中的 [OpenHands Software Agent SDK](https://github.com/OpenHands/software-agent-sdk) 基础设施上运行。

## 可用基准测试

| 基准测试 | 描述 | 状态 |
|-----------|------|--------|
| [SWE-Bench](benchmarks/swebench/) | 来自 GitHub issue 的软件工程任务 | ✅ 活跃 |
| [GAIA](benchmarks/gaia/) | 需要多步推理的通用 AI 助手任务 | ✅ 活跃 |
| [Commit0](benchmarks/commit0/) | 带单元测试的 Python 函数实现任务 | ✅ 活跃 |
| [OpenAgentSafety](benchmarks/openagentsafety/) | 工作场景中带有 NPC 交互的 AI 代理安全评估 | ✅ 活跃 |

各个基准测试目录中有详细的使用说明。

## 快速开始

### 前提条件

在运行任何基准测试之前，您需要设置环境并确保本地 Agent SDK 子模块已初始化。

```bash
make build
```

<details>
<summary>📦 子模块与环境设置（点击展开）</summary>

### 🧩 1. 初始化 Agent SDK 子模块

Benchmarks 项目使用 [OpenHands Agent SDK](https://github.com/OpenHands/software-agent-sdk) 的**本地 git 子模块**。
这确保您的代码针对特定的、可复现的 commit 运行。

克隆后运行一次（`make build` 已为您自动完成）：

```bash
git submodule update --init --recursive
```

此命令将：
- 将 SDK 克隆到 `vendor/software-agent-sdk/`
- 检出本仓库指定的精确 commit
- 使其可用于本地开发（`uv sync` 将从本地文件夹安装）

如果您再次克隆此仓库，请记住使用相同命令重新初始化子模块。

---

### 🏗️ 2. 构建环境

子模块设置完成后，通过 [uv](https://docs.astral.sh/uv) 安装依赖：

```bash
make build
```

这将运行：

```bash
uv sync
```

并确保 `openhands-*` 包（SDK、工具、workspace、agent-server）从 `pyproject.toml` 中声明的**本地工作区**安装。

---

### 🔄 3. 更新子模块（当 SDK 变更时）

如果您想更新到更新版本的 SDK：

```bash
cd vendor/software-agent-sdk
git fetch
git checkout <new_commit_or_branch>
cd ../..
git add vendor/software-agent-sdk
git commit -m "Update software-agent-sdk submodule to <new_commit_sha>"
```

然后重新运行：

```bash
make build
```

以使用新 SDK 代码重建环境。

</details>

### 配置您的 LLM

所有基准测试都需要一个 LLM 配置文件。按照 [LLM 类](https://github.com/OpenHands/software-agent-sdk/blob/main/openhands/sdk/llm/llm.py#L93) 中的模型字段定义您的 LLM 配置为 JSON 格式。

**示例**（`.llm_config/example.json`）：

```json
{
  "model": "litellm_proxy/anthropic/claude-sonnet-4-20250514",
  "base_url": "https://llm-proxy.eval.all-hands.dev",
  "api_key": "YOUR_API_KEY_HERE"
}
```

验证您的配置：

```bash
uv run validate-cfg .llm_config/YOUR_CONFIG_PATH.json
```

## 运行基准测试

设置环境并配置 LLM 后，请参阅各个基准测试目录获取具体使用说明：

- **[SWE-Bench](benchmarks/swebench/)**：来自 GitHub issue 的软件工程任务
- **[GAIA](benchmarks/gaia/)**：需要多步推理的通用 AI 助手任务
- **[OpenAgentSafety](benchmarks/openagentsafety/)**：工作场景中带有 NPC 交互的 AI 代理安全评估

## 增强日志

启用带有彩色编码、结构化日志的增强控制台输出：

```bash
export RICH_LOGGING=1   # 启用增强日志（默认：禁用）
export NO_COLOR=1       # 如需禁用颜色
```

增强日志显示实时的工具调用、代理消息以及每个实例结束时的摘要：

```
10:30:45 [django-12345]  TOOL   │ ▶ bash #1 cmd='ls -la'
10:30:46 [django-12345]  TOOL   │   └─ ok
OK patch=NONEMPTY msgs(a/u)=8/3 tool_calls=12 errors(agent/conv)=0/0 end=finish_tool
```

文件日志（`logs/instance_<id>.log`）不受此设置影响。

## 从本仓库触发云端评估

本仓库公开了一个手动 GitHub Actions 工作流，用于在 Software Agent SDK 中调度 `run-eval.yml` 工作流。当您想从基准测试仓库启动评估而不切换到 SDK 仓库时非常有用。

要求：
- 此仓库中必须有 `PAT_TOKEN` 密钥，且具有在 `OpenHands/software-agent-sdk` 中调度工作流的权限。

使用 `gh` 运行：

```bash
gh workflow run run-eval.yml --repo OpenHands/benchmarks --ref main \
  -f benchmark=swebench \
  -f sdk_ref=main \
  -f eval_limit=50 \
  -f model_ids=litellm_proxy/anthropic/claude-sonnet-4-20250514 \
  -f reason="benchmarks-trigger" \
  -f eval_branch=main \
  -f benchmarks_branch=main \
  -f instance_ids="" \
  -f num_infer_workers="" \
  -f num_eval_workers=""
```

输入参数（转发到 SDK 的 `run-eval.yml` 工作流）：
- `benchmark`：要运行的基准测试套件。选项：`gaia`、`swebench`、`swtbench`、`commit0`。默认：`swebench`。
- `sdk_ref`：用于评估的 SDK commit、标签或分支。默认：`main`。
- `eval_limit`：要运行的实例数量（任意正整数）。默认：`1`。
- `model_ids`：逗号分隔的模型 ID（SDK `.github/run-eval/resolve_model_config.py` 中 `MODELS` 的键）。留空则使用 SDK 默认值。
- `reason`：手动触发的原因（显示在日志/PR 评论中）。可选。
- `eval_branch`：要使用的评估仓库分支（例如功能测试）。默认：`main`。
- `benchmarks_branch`：要评估的 Benchmarks 仓库分支（使用您的功能分支来测试更改）。默认：`main`。
- `instance_ids`：逗号分隔的要运行的实例 ID（覆盖支持此参数的基准测试中的 `eval_limit`）。可选。
- `num_infer_workers`：覆盖推理工作器数量（留空使用基准测试默认值）。可选。
- `num_eval_workers`：覆盖评估工作器数量（留空使用基准测试默认值）。可选。

## 工作区类型

基准测试支持两种工作区类型来运行评估。

### Docker 工作区（默认）

使用本地 Docker 容器运行代理评估。镜像按需在本地构建。

- **优点**：无需额外设置，可离线工作
- **缺点**：对本地机器资源消耗大，大规模评估时较慢
- **适用场景**：开发、测试、小规模评估

### 远程工作区

使用[远程运行时 API](https://openhands.dev/blog/evaluation-of-llms-as-coding-agents-on-swe-bench-at-30x-speed) 在云环境中配置容器，实现大规模并行化。

- **优点**：可扩展至数百个并行工作器，无本地资源限制
- **缺点**：需要预构建镜像和 API 访问权限
- **适用场景**：大规模评估、基准测试运行

#### 远程运行时工作原理

1. **预构建代理镜像**：必须为特定 SDK commit（SHA）预构建 agent-server 镜像，并推送到公共容器注册表（例如 `ghcr.io/openhands/eval-agent-server`）

2. **运行时 API**：远程工作区连接到运行时 API 服务（默认：`https://runtime.eval.all-hands.dev`），按需配置容器

3. **镜像解析**：在开始评估之前，系统验证注册表中是否存在具有正确标签格式的所需镜像：`{IMAGE}:{SDK_SHA}-{CUSTOM_TAG}{SUFFIX}`

4. **并行执行**：每个评估实例在独立的容器中运行，允许大规模并行化（例如 32+ 并发工作器）

#### 远程工作区的前提条件

1. **预构建镜像**：镜像必须构建并推送到公共注册表
   - 在本仓库中，为 PR 添加以下标签之一以触发镜像构建：
     - `build-swebench-50`：构建 50 个镜像（快速测试）
     - `build-swebench-200`：构建 200 个镜像（中等测试）
     - `build-swebench`：构建所有镜像（完整评估）
   - 镜像使用 `vendor/software-agent-sdk` 子模块的 SDK SHA 标记

2. **运行时 API 密钥**：设置 `RUNTIME_API_KEY` 环境变量
   ```bash
   export RUNTIME_API_KEY="your-api-key-here"
   ```

3. **可选配置**：
   - `RUNTIME_API_URL`：覆盖默认 API 端点（默认：`https://runtime.eval.all-hands.dev`）
   - `SDK_SHORT_SHA`：覆盖用于镜像选择的 SDK SHA（默认：从子模块自动检测）

各个基准测试的 README 中有具体的使用示例。

## SDK 兼容性与版本管理

⚠️ **重要**：Benchmarks 仓库依赖于 [OpenHands Agent SDK](https://github.com/OpenHands/software-agent-sdk)，且**并非每个版本的 benchmarks 都与每个版本的 SDK 兼容**。随着 SDK 的发展和新功能的引入，benchmarks 代码可能采用这些功能，从而产生版本依赖关系。

### SWE-Bench 镜像分层（docutils/roman）

部分 SWE-Bench 实例（特别是 `sphinx-doc`）需要 `docutils<0.21` 和 `roman`。构建流水线现在仅对需要额外层的镜像进行包装：
- `benchmarks/swebench/build_images.py` 对小型白名单（目前为 `sphinx-doc`）中的仓库镜像进行包装。
- 其他仓库（例如 scikit-learn）保持基础镜像不变。
- 包装后的镜像使用相同的标签（无后缀），因为它们仅用于评估。

运行或调度构建时无需额外标志——选择性包装已自动处理。

### 评估不同 SDK 版本

在评估特定 SDK 版本时，您需要确保 benchmarks 代码与该 SDK 版本兼容。您有两种选择：

1. **使用工作流中的 `benchmarks-commit` 参数**（推荐）：
   - 手动触发 `build-swebench-images` 工作流（就地构建 + 包装镜像）时，同时指定：
     - `sdk-commit`：您要评估的 SDK 版本
     - `benchmarks-commit`：与该 SDK 版本兼容的 benchmarks commit

2. **在本地手动检出兼容版本**：
   ```bash
   # 检出与目标 SDK 版本兼容的 benchmarks commit
   git checkout <benchmarks-commit>
   
   # 将 SDK 子模块更新到目标版本
   cd vendor/software-agent-sdk
   git checkout <sdk-commit>
   cd ../..
   
   # 重建环境
   make build
   ```

### 示例：SDK Critic 模块

版本依赖的一个显著示例是 SDK critic 模块。自 SDK commit [`79868ae5`](https://github.com/OpenHands/software-agent-sdk/commit/79868ae5)（2025 年 11 月 17 日）起，OpenHands Agent SDK 引入了 `openhands.sdk.critic` 模块。当前的 benchmarks 代码从此模块导入 `CriticBase`，这意味着：

- **SDK 版本 ≥ `79868ae5`**：与当前 benchmarks 代码兼容
- **SDK 版本 < `79868ae5`**：需要较旧的 benchmarks commit（在 critic 导入添加之前）

要检查特定 benchmarks commit 是否需要 critic 模块：
```bash
git show <commit>:benchmarks/utils/models.py | grep "from openhands.sdk.critic"
```

如果此命令返回输出，则该 benchmarks commit 需要包含 critic 模块的 SDK 版本。

## 链接

- **OpenHands 原始仓库**：https://github.com/OpenHands/OpenHands/
- **Agent SDK**：https://github.com/OpenHands/software-agent-sdk
- **SWE-Bench**：https://www.swebench.com/
