# 语言模型评测框架

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10256836.svg)](https://doi.org/10.5281/zenodo.10256836)

---

## 最新动态 📣
- [2025/12] **CLI 已重构**，引入子命令（`run`、`ls`、`validate`），并通过 `--config` 支持 YAML 配置文件。参见 [CLI Reference](./docs/interface.md) 和 [Configuration Guide](./docs/config_files.md)。
- [2025/12] **安装更轻量**：基础包不再包含 `transformers`/`torch`。请单独安装模型后端：`pip install lm_eval[hf]`、`lm_eval[vllm]` 等。
- [2025/07] 为 `hf`（token/str）、`vllm` 和 `sglang`（str）新增 `think_end_token` 参数，用于从支持该功能的模型中剥离 CoT 推理痕迹。
- [2025/03] 新增对可操控 HF 模型的支持！
- [2025/02] 新增 [SGLang](https://docs.sglang.ai/) 支持！
- [2024/09] 我们正在原型化支持 LM Evaluation Harness 用户创建并评测文本+图像多模态输入、文本输出任务，刚刚新增了 `hf-multimodal` 和 `vllm-vlm` 模型类型，以及作为原型特性的 `mmmu` 任务。欢迎用户试用这一仍在开发中的特性并自行进行压力测试，同时也建议关注 [`lmms-eval`](https://github.com/EvolvingLMMs-Lab/lmms-eval)。这是一个最初从 lm-evaluation-harness 分叉出来的优秀项目，提供了更广泛的多模态任务、模型和功能。
- [2024/07] [API model](docs/API_guide.md) 支持已更新并重构，引入了批量与异步请求支持，并显著降低了自定义和使用门槛。**若要运行 Llama 405B，我们建议使用 VLLM 的 OpenAI 兼容 API 来托管模型，并使用 `local-completions` 模型类型进行评测。**
- [2024/07] 新增 Open LLM Leaderboard 任务！你可以在 [leaderboard](lm_eval/tasks/leaderboard/README.md) 任务组下找到它们。

---

## 公告

**lm-evaluation-harness 已发布新的 v0.4.0 版本**！

新的更新和功能包括：

- **新增 Open LLM Leaderboard 任务！你可以在 [leaderboard](lm_eval/tasks/leaderboard/README.md) 任务组下找到它们。**
- 内部重构
- 基于配置的任务创建与配置
- 更容易导入和共享外部定义的任务配置 YAML
- 支持基于 Jinja2 的提示词设计，可轻松修改提示词，并从 Promptsource 导入提示词
- 更高级的配置选项，包括输出后处理、答案提取、每个文档生成多个 LM 输出、可配置的小样本设置等
- 提速以及对新建模库的支持，包括：更快的数据并行 HF 模型使用方式、vLLM 支持、HuggingFace 的 MPS 支持等
- 日志与可用性改进
- 新任务，包括 CoT BIG-Bench-Hard、Belebele、用户定义的任务分组等

更多细节请参见我们位于 `docs/` 中的更新文档页面。

后续开发将继续在 `main` 分支上进行。欢迎通过 GitHub 上的 issue 或 PR，或者在 [EleutherAI discord](https://discord.gg/eleutherai) 中向我们反馈你希望加入的功能、如何进一步改进该库，或直接提出问题！

---

## 概览

这个项目提供了一个统一框架，用于在大量不同评测任务上测试生成式语言模型。

**特性：**

- 提供 60 多个 LLM 标准学术基准，并实现了数百个子任务和变体。
- 支持通过 [transformers](https://github.com/huggingface/transformers/)（包括使用 [GPTQModel](https://github.com/ModelCloud/GPTQModel) 和 [AutoGPTQ](https://github.com/PanQiWei/AutoGPTQ) 进行量化）、[GPT-NeoX](https://github.com/EleutherAI/gpt-neox) 和 [Megatron-DeepSpeed](https://github.com/microsoft/Megatron-DeepSpeed/) 加载模型，并提供灵活的、与分词方式无关的接口。
- 支持通过 [vLLM](https://github.com/vllm-project/vllm) 进行快速且节省内存的推理。
- 支持包括 [OpenAI](https://openai.com) 和 [TextSynth](https://textsynth.com/) 在内的商业 API。
- 支持评测 [HuggingFace 的 PEFT 库](https://github.com/huggingface/peft) 所支持的适配器（如 LoRA）。
- 支持本地模型和本地基准。
- 使用公开可用的提示词进行评测，确保论文间结果可复现、可比较。
- 易于支持自定义提示词和评测指标。

Language Model Evaluation Harness 是 🤗 Hugging Face 热门 [Open LLM Leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard) 的后端，已被用于[数百篇论文](https://scholar.google.com/scholar?oi=bibs&hl=en&authuser=2&cites=15052937328817631261,4097184744846514103,1520777361382155671,17476825572045927382,18443729326628441434,14801318227356878622,7890865700763267262,12854182577605049984,15641002901115500560,5104500764547628290)，并在 NVIDIA、Cohere、BigScience、BigCode、Nous Research 和 Mosaic ML 等数十个组织内部使用。

## 安装

要从 GitHub 仓库安装 `lm-eval` 包，请运行：

```bash
git clone --depth 1 https://github.com/EleutherAI/lm-evaluation-harness
cd lm-evaluation-harness
pip install -e .
```

### 安装模型后端

基础安装会提供核心评测框架。**模型后端必须通过可选 extras 单独安装**：

对于 HuggingFace transformers 模型：

```bash
pip install "lm_eval[hf]"
```

对于 vLLM 推理：

```bash
pip install "lm_eval[vllm]"
```

对于基于 API 的模型（OpenAI、Anthropic 等）：

```bash
pip install "lm_eval[api]"
```

也可以同时安装多个后端：

```bash
pip install "lm_eval[hf,vllm,api]"
```

本文档末尾提供了所有可选 extras 的详细表格。

## 基本用法

### 文档

| 指南 | 说明 |
|------|------|
| [CLI Reference](./docs/interface.md) | 命令行参数与子命令 |
| [Configuration Guide](./docs/config_files.md) | YAML 配置文件格式与示例 |
| [Python API](./docs/python-api.md) | 使用 `simple_evaluate()` 的编程式用法 |
| [Task Guide](./lm_eval/tasks/README.md) | 可用任务与任务配置 |

使用 `lm-eval -h` 查看可用选项，或使用 `lm-eval run -h` 查看评测选项。

列出可用任务：

```bash
lm-eval ls tasks
```

### Hugging Face `transformers`

> [!Important]
> 要使用 HuggingFace 后端，请先安装：`pip install "lm_eval[hf]"`

要在 [HuggingFace Hub](https://huggingface.co/models) 上托管的模型（例如 GPT-J-6B）上评测 `hellaswag`，可以使用以下命令（假设你使用的是兼容 CUDA 的 GPU）：

```bash
lm_eval --model hf \
    --model_args pretrained=EleutherAI/gpt-j-6B \
    --tasks hellaswag \
    --device cuda:0 \
    --batch_size 8
```

可以使用 `--model_args` 标志向模型构造函数传递额外参数。尤其是，这支持在 Hub 上使用常见的 `revisions` 特性来存储部分训练的 checkpoint，或者指定运行模型时使用的数据类型：

```bash
lm_eval --model hf \
    --model_args pretrained=EleutherAI/pythia-160m,revision=step100000,dtype="float" \
    --tasks lambada_openai,hellaswag \
    --device cuda:0 \
    --batch_size 8
```

支持通过 Huggingface 中的 `transformers.AutoModelForCausalLM`（自回归、仅解码器 GPT 风格模型）和 `transformers.AutoModelForSeq2SeqLM`（如 T5 这类编码器-解码器模型）加载的模型。

将 ```--batch_size``` 设为 ```auto``` 可以自动选择 batch size。这样会自动检测你的设备可容纳的最大 batch size。对于最长样本和最短样本差异较大的任务，定期重新计算最大 batch size 可能有助于进一步提速。为此，可在上述标志后追加 ```:N```，以自动重新计算最大 batch size 共 ```N``` 次。例如，要重新计算 4 次，命令如下：

```bash
lm_eval --model hf \
    --model_args pretrained=EleutherAI/pythia-160m,revision=step100000,dtype="float" \
    --tasks lambada_openai,hellaswag \
    --device cuda:0 \
    --batch_size auto:4
```

> [!Note]
> 就像你可以向 `transformers.AutoModel` 提供本地路径一样，你也可以通过 `--model_args pretrained=/path/to/model` 向 `lm_eval` 提供本地路径

#### 评测 GGUF 模型

`lm-eval` 支持使用 Hugging Face（`hf`）后端评测 GGUF 格式模型。这使你可以使用兼容 `transformers`、`AutoModel` 和 llama.cpp 转换的量化模型。

要评测 GGUF 模型，请通过 `--model_args` 传入包含模型权重的目录路径、`gguf_file`，以及可选的单独 `tokenizer` 路径。

**🚨 重要说明：**  
如果未提供单独的 tokenizer，Hugging Face 会尝试从 GGUF 文件重建 tokenizer，这可能会花费**数小时**，甚至无限期卡住。传入单独的 tokenizer 可以避免这个问题，并将 tokenizer 加载时间从数小时缩短到数秒。

**✅ 推荐用法：**

```bash
lm_eval --model hf \
    --model_args pretrained=/path/to/gguf_folder,gguf_file=model-name.gguf,tokenizer=/path/to/tokenizer \
    --tasks hellaswag \
    --device cuda:0 \
    --batch_size 8
```

> [!Tip]
> 请确保 tokenizer 路径指向一个有效的 Hugging Face tokenizer 目录（例如其中包含 tokenizer_config.json、vocab.json 等）。

#### 使用 Hugging Face `accelerate` 进行多 GPU 评测

我们支持三种主要方式，使用 Hugging Face 的 [accelerate 🚀](https://github.com/huggingface/accelerate) 库进行多 GPU 评测。

要执行*数据并行评测*（即每个 GPU 加载模型的**完整独立副本**），我们像下面这样使用 `accelerate` 启动器：

```bash
accelerate launch -m lm_eval --model hf \
    --tasks lambada_openai,arc_easy \
    --batch_size 16
```

（或者通过 `accelerate launch --no-python lm_eval`）。

对于模型能够放进单个 GPU 的情况，这样可以让你在 K 个 GPU 上以单卡 K 倍的速度完成评测。

**WARNING**：此设置不适用于 FSDP 模型切分，因此在 `accelerate config` 中必须禁用 FSDP，或者使用 NO_SHARD FSDP 选项。

第二种使用 `accelerate` 进行多 GPU 评测的方式适用于模型*太大，无法放进单个 GPU* 的情况。

在这种设置下，应在 *`accelerate` 启动器外部* 运行该库，但通过如下方式向 `--model_args` 传入 `parallelize=True`：

```bash
lm_eval --model hf \
    --tasks lambada_openai,arc_easy \
    --model_args parallelize=True \
    --batch_size 16
```

这意味着你的模型权重将被拆分到所有可用 GPU 上。

对于更高级的用户或更大的模型，当 `parallelize=True` 时，我们还允许使用以下参数：

- `device_map_option`：如何在可用 GPU 之间拆分模型权重。默认值为 `"auto"`。
- `max_memory_per_gpu`：加载模型时每块 GPU 最多使用的显存。
- `max_cpu_memory`：将模型权重卸载到 RAM 时最多使用的 CPU 内存。
- `offload_folder`：如果需要将模型权重卸载到磁盘，所使用的文件夹。

第三种选项是将两者同时使用。这样你既能利用数据并行，也能利用模型切分，这对于无法放进单个 GPU 的模型尤其有用。

```bash
accelerate launch --multi_gpu --num_processes {nb_of_copies_of_your_model} \
    -m lm_eval --model hf \
    --tasks lambada_openai,arc_easy \
    --model_args parallelize=True \
    --batch_size 16
```

若想进一步了解模型并行以及如何与 `accelerate` 库配合使用，请参见 [accelerate documentation](https://huggingface.co/docs/transformers/v4.15.0/en/parallelism)

**警告：我们原生不支持使用 `hf` 模型类型进行多节点评测！请参考 [我们的 GPT-NeoX 库集成](https://github.com/EleutherAI/gpt-neox/blob/main/eval.py)，其中展示了如何编写自定义多机评测脚本。**

**注意：我们目前也不原生支持多节点评测，并建议使用外部托管的推理服务器进行请求，或者像 [GPT-NeoX 库](https://github.com/EleutherAI/gpt-neox/blob/main/eval_tasks/eval_adapter.py) 那样，为你的分布式框架创建自定义集成。**

### 可操控的 Hugging Face `transformers` 模型

要在应用 steering vectors 的情况下评测 Hugging Face `transformers` 模型，请将模型类型指定为 `steered`，并提供一个路径，指向包含预定义 steering vectors 的 PyTorch 文件，或一个 CSV 文件，用于说明如何从预训练的 `sparsify` 或 `sae_lens` 模型中导出 steering vectors（使用这种方式时，你需要安装相应的可选依赖）。

指定预定义 steering vectors：

```python
import torch

steer_config = {
    "layers.3": {
        "steering_vector": torch.randn(1, 768),
        "bias": torch.randn(1, 768),
        "steering_coefficient": 1,
        "action": "add"
    },
}
torch.save(steer_config, "steer_config.pt")
```

指定导出的 steering vectors：

```python
import pandas as pd

pd.DataFrame({
    "loader": ["sparsify"],
    "action": ["add"],
    "sparse_model": ["EleutherAI/sae-pythia-70m-32k"],
    "hookpoint": ["layers.3"],
    "feature_index": [30],
    "steering_coefficient": [10.0],
}).to_csv("steer_config.csv", index=False)
```

在应用 steering vectors 的情况下运行评测框架：

```bash
lm_eval --model steered \
    --model_args pretrained=EleutherAI/pythia-160m,steer_path=steer_config.pt \
    --tasks lambada_openai,hellaswag \
    --device cuda:0 \
    --batch_size 8
```

### NVIDIA `nemo` 模型

[NVIDIA NeMo Framework](https://github.com/NVIDIA/NeMo) 是面向研究人员和使用 pytorch 开发语言模型的开发者构建的生成式 AI 框架。

要评测 `nemo` 模型，请先按照[文档](https://github.com/NVIDIA/NeMo?tab=readme-ov-file#installation)安装 NeMo。我们强烈建议使用 NVIDIA PyTorch 或 NeMo 容器，尤其是在安装 Apex 或其他依赖时遇到问题的情况下（参见[最新发布的容器](https://github.com/NVIDIA/NeMo/releases)）。另外，也请按照[安装章节](https://github.com/EleutherAI/lm-evaluation-harness/tree/main?tab=readme-ov-file#install)中的说明安装 lm evaluation harness 库。

NeMo 模型可以通过 [NVIDIA NGC Catalog](https://catalog.ngc.nvidia.com/models) 或 [NVIDIA 的 Hugging Face 页面](https://huggingface.co/nvidia) 获取。在 [NVIDIA NeMo Framework](https://github.com/NVIDIA/NeMo/tree/main/scripts/nlp_language_modeling) 中也有转换脚本，可将 llama、falcon、mixtral 或 mpt 等热门模型的 `hf` checkpoint 转换为 `nemo`。

在单个 GPU 上运行 `nemo` 模型：

```bash
lm_eval --model nemo_lm \
    --model_args path=<path_to_nemo_model> \
    --tasks hellaswag \
    --batch_size 32
```

建议将 `nemo` 模型预先解包，以避免在 docker 容器内解包，因为这可能会导致磁盘空间溢出。为此可以运行：

```bash
mkdir MY_MODEL
tar -xvf MY_MODEL.nemo -c MY_MODEL
```

#### 使用 NVIDIA `nemo` 模型进行多 GPU 评测

默认情况下仅使用一个 GPU。但我们支持在单节点上进行数据复制或张量/流水线并行评测。

1. 要启用数据复制，请将 `model_args` 中的 `devices` 设为需要运行的数据副本数。例如，在 8 个 GPU 上运行 8 个数据副本的命令如下：

```bash
torchrun --nproc-per-node=8 --no-python lm_eval \
    --model nemo_lm \
    --model_args path=<path_to_nemo_model>,devices=8 \
    --tasks hellaswag \
    --batch_size 32
```

1. 要启用张量并行和/或流水线并行，请设置 `model_args` 中的 `tensor_model_parallel_size` 和/或 `pipeline_model_parallel_size`。此外，还必须将 `devices` 设置为 `tensor_model_parallel_size` 和/或 `pipeline_model_parallel_size` 的乘积。例如，在单节点 4 个 GPU 上使用张量并行度 2、流水线并行度 2 的命令如下：

```bash
torchrun --nproc-per-node=4 --no-python lm_eval \
    --model nemo_lm \
    --model_args path=<path_to_nemo_model>,devices=4,tensor_model_parallel_size=2,pipeline_model_parallel_size=2 \
    --tasks hellaswag \
    --batch_size 32
```

注意，建议使用 `torchrun --nproc-per-node=<number of devices> --no-python` 替代 `python` 命令，以便更顺利地将模型加载到 GPU 中。这对于加载到多个 GPU 上的大型 checkpoint 尤其重要。

尚不支持：多节点评测，以及将数据复制与张量并行或流水线并行组合使用。

### Megatron-LM 模型

[Megatron-LM](https://github.com/NVIDIA/Megatron-LM) 是 NVIDIA 的大规模 transformer 训练框架。该后端允许直接评测 Megatron-LM checkpoint，无需转换。

**要求：**
- Megatron-LM 必须已安装，或可通过 `MEGATRON_PATH` 环境变量访问
- 带 CUDA 支持的 PyTorch

**设置：**

```bash
# Set environment variable pointing to Megatron-LM installation
export MEGATRON_PATH=/path/to/Megatron-LM
```

**基本用法（单 GPU）：**

```bash
lm_eval --model megatron_lm \
    --model_args load=/path/to/checkpoint,tokenizer_type=HuggingFaceTokenizer,tokenizer_model=/path/to/tokenizer \
    --tasks hellaswag \
    --batch_size 1
```

**支持的 checkpoint 格式：**
- 标准 Megatron checkpoint（`model_optim_rng.pt`）
- 分布式 checkpoint（`.distcp` 格式，自动检测）

#### 并行模式

Megatron-LM 后端支持以下并行模式：

| 模式 | 配置 | 说明 |
|------|------|------|
| Single GPU | `devices=1` (default) | 标准单 GPU 评测 |
| Data Parallelism | `devices>1, TP=1` | 每个 GPU 都有完整模型副本，数据被分发 |
| Tensor Parallelism | `TP == devices` | 模型层在多个 GPU 间拆分 |
| Expert Parallelism | `EP == devices, TP=1` | 用于 MoE 模型，专家分布在多个 GPU 上 |

> [!Note]
> - 当前不支持流水线并行（PP > 1）。
> - 专家并行（EP）不能与张量并行（TP）组合使用。

**数据并行（4 个 GPU，每个都有完整模型副本）：**

```bash
torchrun --nproc-per-node=4 -m lm_eval --model megatron_lm \
    --model_args load=/path/to/checkpoint,tokenizer_model=/path/to/tokenizer,devices=4 \
    --tasks hellaswag
```

**张量并行（TP=2）：**

```bash
torchrun --nproc-per-node=2 -m lm_eval --model megatron_lm \
    --model_args load=/path/to/checkpoint,tokenizer_model=/path/to/tokenizer,devices=2,tensor_model_parallel_size=2 \
    --tasks hellaswag
```

**MoE 模型的专家并行（EP=4）：**

```bash
torchrun --nproc-per-node=4 -m lm_eval --model megatron_lm \
    --model_args load=/path/to/moe_checkpoint,tokenizer_model=/path/to/tokenizer,devices=4,expert_model_parallel_size=4 \
    --tasks hellaswag
```

**使用 extra_args 传入额外的 Megatron 选项：**

```bash
lm_eval --model megatron_lm \
    --model_args load=/path/to/checkpoint,tokenizer_model=/path/to/tokenizer,extra_args="--no-rope-fusion --trust-remote-code" \
    --tasks hellaswag
```

> [!Note]
> `--use-checkpoint-args` 标志默认启用，它会从 checkpoint 中加载模型架构参数。对于通过 Megatron-Bridge 转换得到的 checkpoint，这通常已经包含所需的全部模型配置。

#### 使用 OpenVINO 模型进行多 GPU 评测

评测时支持对 OpenVINO 模型使用流水线并行。

要启用流水线并行，请设置 `model_args` 中的 `pipeline_parallel`。此外，还需要将 `device` 设置为 `HETERO:<GPU index1>,<GPU index2>`，例如 `HETERO:GPU.1,GPU.0`。例如，使用 2 路流水线并行的命令如下：

```bash
lm_eval --model openvino \
    --tasks wikitext \
    --model_args pretrained=<path_to_ov_model>,pipeline_parallel=True \
    --device HETERO:GPU.1,GPU.0
```

### 使用 `vLLM` 的张量 + 数据并行与优化推理

我们还支持 vLLM，可在[支持的模型类型](https://docs.vllm.ai/en/latest/models/supported_models.html)上实现更快推理，尤其是在将模型拆分到多个 GPU 上时更快。无论是单 GPU 还是多 GPU，张量并行、数据并行或两者组合的推理，例如：

```bash
lm_eval --model vllm \
    --model_args pretrained={model_name},tensor_parallel_size={GPUs_per_model},dtype=auto,gpu_memory_utilization=0.8,data_parallel_size={model_replicas} \
    --tasks lambada_openai \
    --batch_size auto
```

要使用 vllm，请执行 `pip install "lm_eval[vllm]"`。有关所有受支持 vLLM 配置的完整列表，请参阅我们的 [vLLM integration](https://github.com/EleutherAI/lm-evaluation-harness/blob/e74ec966556253fbe3d8ecba9de675c77c075bce/lm_eval/models/vllm_causallms.py) 和 vLLM 文档。

vLLM 的输出偶尔会与 Huggingface 不同。我们将 Huggingface 视为参考实现，并提供了一个[脚本](./scripts/model_comparator.py)，用于检查 vllm 结果相对于 HF 的有效性。

> [!Tip]
> 为了获得最快性能，我们建议在 vLLM 中尽可能使用 `--batch_size auto`，以利用其连续批处理功能！

> [!Tip]
> 通过 model args 向 vLLM 传入 `max_model_len=4096` 或其他合理默认值，可能会带来加速，或在尝试使用自动 batch size 时避免显存不足错误，例如默认最大长度为 32k 的 Mistral-7B-v0.1。

### 使用 `SGLang` 的张量 + 数据并行和快速离线批量推理

我们支持使用 SGLang 进行高效离线批量推理。它的 **[Fast Backend Runtime](https://docs.sglang.ai/index.html)** 通过优化的内存管理和并行处理技术提供高性能。关键特性包括张量并行、连续批处理，以及对多种量化方法（FP8/INT4/AWQ/GPTQ）的支持。

要将 SGLang 用作评测后端，请先根据 SGLang 文档[这里](https://docs.sglang.io/get_started/install.html#install-sglang)提前安装。

> [!Tip]
> 由于 [`Flashinfer`](https://docs.flashinfer.ai/) 这一快速注意力内核库的安装方式，我们没有在 [pyproject.toml](pyproject.toml) 中包含 `SGLang` 的依赖。请注意，`Flashinfer` 对 `torch` 版本也有一些要求。

SGLang 的服务器参数与其他后端略有不同，更多信息见[这里](https://docs.sglang.io/advanced_features/server_arguments.html)。下面给出一个使用示例：

```bash
lm_eval --model sglang \
    --model_args pretrained={model_name},dp_size={data_parallel_size},tp_size={tensor_parallel_size},dtype=auto \
    --tasks gsm8k_cot \
    --batch_size auto
```

> [!Tip]
> 当遇到显存不足（OOM）错误时（尤其是在多项选择任务上），可以尝试以下方案：
>
> 1. 使用手动指定的 `batch_size`，而不是 `auto`。
> 2. 通过调整 `mem_fraction_static` 来降低 KV cache pool 的内存占用，例如在模型参数中添加 `--model_args pretrained=...,mem_fraction_static=0.7`。
> 3. 增加张量并行大小 `tp_size`（如果使用多个 GPU）。

### Windows ML

我们支持 **Windows ML**，用于在 Windows 平台上进行硬件加速推理。这使得你可以在 CPU、GPU 和 **NPU（神经处理单元）** 设备上进行评测。

Windows ML 是什么？
https://learn.microsoft.com/en-us/windows/ai/new-windows-ml/overview

要使用 Windows ML，请安装所需依赖：

```bash
pip install wasdk-Microsoft.Windows.AI.MachineLearning[all] wasdk-Microsoft.Windows.ApplicationModel.DynamicDependency.Bootstrap onnxruntime-windowsml onnxruntime-genai-winml
```

在 Windows 上于 NPU/GPU/CPU 上评测 ONNX Runtime GenAI LLM：

```bash
lm_eval --model winml \
    --model_args pretrained=/path/to/onnx/model \
    --tasks mmlu \
    --batch_size 1
```

> [!Note]
> Windows ML 后端**仅**适用于 ONNX Runtime GenAI 模型格式。面向 `transformers.js` 的模型无法工作。你可以通过在模型文件夹中查找 `genai_config.json` 文件来验证这一点。

> [!Note]
> 要在目标设备上运行 ONNX Runtime GenAI 模型，你**必须**将原始模型转换为对应厂商和设备类型。已转换的模型无法在其他厂商或设备类型上工作，或者表现不佳。有关模型转换的更多信息，请访问 [Microsoft AI Tool Kit](https://code.visualstudio.com/docs/intelligentapps/modelconversion)

### 模型 API 与推理服务器

> [!Important]
> 要使用基于 API 的模型，请先安装：`pip install "lm_eval[api]"`

我们的库还支持评测通过若干商业 API 提供服务的模型，我们也希望实现对最常用的高性能本地/自托管推理服务器的支持。

调用托管模型时，请使用：

```bash
export OPENAI_API_KEY=YOUR_KEY_HERE
lm_eval --model openai-completions \
    --model_args model=davinci-002 \
    --tasks lambada_openai,hellaswag
```

我们也支持你使用自己的本地推理服务器，只要该服务器镜像实现了 OpenAI Completions 和 ChatCompletions API。

```bash
lm_eval --model local-completions --tasks gsm8k --model_args model=facebook/opt-125m,base_url=http://{yourip}:8000/v1/completions,num_concurrent=1,max_retries=3,tokenized_requests=False,batch_size=16
```

请注意，对于外部托管模型，不应使用类似 `--device` 这类与本地模型部署位置相关的配置，它们也不会生效。就像你可以使用 `--model_args` 向本地模型的构造函数传递任意参数一样，你也可以用它向托管模型的 API 传递任意参数。具体支持哪些参数，请参阅相应托管服务的文档。

| API 或推理服务器                                                                                                          | 已实现？                                                                                                | `--model <xxx>` 名称                                | 支持的模型：                                                                                                                                                                                                                                                                                                                                               | 请求类型：                                                                     |
|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| OpenAI Completions                                                                                                        | :heavy_check_mark:                                                                                      | `openai-completions`, `local-completions`           | 所有 OpenAI Completions API 模型                                                                                                                                                                                                                                                                                                                           | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| OpenAI ChatCompletions                                                                                                    | :heavy_check_mark:                                                                                      | `openai-chat-completions`, `local-chat-completions` | [所有 ChatCompletions API 模型](https://platform.openai.com/docs/guides/gpt)                                                                                                                                                                                                                                                                               | `generate_until`（不提供 logprobs）                                            |
| Anthropic                                                                                                                 | :heavy_check_mark:                                                                                      | `anthropic`                                         | [Anthropic 支持的引擎](https://docs.anthropic.com/claude/reference/selecting-a-model)                                                                                                                                                                                                                                                                      | `generate_until`（不提供 logprobs）                                            |
| Anthropic Chat                                                                                                            | :heavy_check_mark:                                                                                      | `anthropic-chat`, `anthropic-chat-completions`      | [Anthropic 支持的引擎](https://docs.anthropic.com/claude/docs/models-overview)                                                                                                                                                                                                                                                                             | `generate_until`（不提供 logprobs）                                            |
| Textsynth                                                                                                                 | :heavy_check_mark:                                                                                      | `textsynth`                                         | [所有支持的引擎](https://textsynth.com/documentation.html#engines)                                                                                                                                                                                                                                                                                         | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| Cohere                                                                                                                    | [:hourglass: - blocked on Cohere API bug](https://github.com/EleutherAI/lm-evaluation-harness/pull/395) | N/A                                                 | [所有 `cohere.generate()` 引擎](https://docs.cohere.com/docs/models)                                                                                                                                                                                                                                                                                       | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| [Llama.cpp](https://github.com/ggerganov/llama.cpp)（通过 [llama-cpp-python](https://github.com/abetlen/llama-cpp-python)） | :heavy_check_mark:                                                                                      | `gguf`, `ggml`                                      | [llama.cpp 支持的所有模型](https://github.com/ggerganov/llama.cpp)                                                                                                                                                                                                                                                                                         | `generate_until`, `loglikelihood`（尚未实现 perplexity 评测）                  |
| vLLM                                                                                                                      | :heavy_check_mark:                                                                                      | `vllm`                                              | [大多数 HF Causal Language Models](https://docs.vllm.ai/en/latest/models/supported_models.html)                                                                                                                                                                                                                                                           | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| Mamba                                                                                                                     | :heavy_check_mark:                                                                                      | `mamba_ssm`                                         | [通过 `mamba_ssm` 包支持的 Mamba 架构语言模型](https://huggingface.co/state-spaces)                                                                                                                                                                                                                                                                        | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| Huggingface Optimum（Causal LMs）                                                                                         | :heavy_check_mark:                                                                                      | `openvino`                                          | 任何使用 Huggingface Optimum 转换为 OpenVINO™ Intermediate Representation（IR）格式的仅解码器 AutoModelForCausalLM                                                                                                                                                                                                                                        | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| Huggingface Optimum-intel IPEX（Causal LMs）                                                                              | :heavy_check_mark:                                                                                      | `ipex`                                              | 任何仅解码器 AutoModelForCausalLM                                                                                                                                                                                                                                                                                                                           | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| Huggingface Optimum-habana（Causal LMs）                                                                                  | :heavy_check_mark:                                                                                      | `habana`                                            | 任何仅解码器 AutoModelForCausalLM                                                                                                                                                                                                                                                                                                                           | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| 通过 AWS Inf2 运行的 Neuron（Causal LMs）                                                                                 | :heavy_check_mark:                                                                                      | `neuronx`                                           | 任何受支持、可在 [inferentia2 的 huggingface-ami 镜像](https://aws.amazon.com/marketplace/pp/prodview-gr3e6yiscria2) 上运行的仅解码器 AutoModelForCausalLM                                                                                                                                                                                                | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| NVIDIA NeMo                                                                                                               | :heavy_check_mark:                                                                                      | `nemo_lm`                                           | [所有支持的模型](https://docs.nvidia.com/nemo-framework/user-guide/24.09/nemotoolkit/core/core.html#nemo-models)                                                                                                                                                                                                                                          | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| NVIDIA Megatron-LM                                                                                                        | :heavy_check_mark:                                                                                      | `megatron_lm`                                       | [Megatron-LM GPT 模型](https://github.com/NVIDIA/Megatron-LM)（标准与分布式 checkpoint）                                                                                                                                                                                                                                                                   | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| Watsonx.ai                                                                                                                | :heavy_check_mark:                                                                                      | `watsonx_llm`                                       | [Watsonx.ai 支持的引擎](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/fm-models.html?context=wx)                                                                                                                                                                                                                                       | `generate_until` `loglikelihood`                                               |
| Windows ML                                                                                                                | :heavy_check_mark:                                                                                      | `winml`                                             | [GenAI 格式的 ONNX 模型](https://code.visualstudio.com/docs/intelligentapps/modelconversion)                                                                                                                                                                                                                                                               | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |
| [你的本地推理服务器！](docs/API_guide.md)                                                                                 | :heavy_check_mark:                                                                                      | `local-completions` 或 `local-chat-completions`     | 支持 OpenAI API 兼容服务器，也可方便地为其他 API 做定制。                                                                                                                                                                                                                                                                                                   | `generate_until`, `loglikelihood`, `loglikelihood_rolling`                     |

不提供 logits 或 logprobs 的模型只能用于 `generate_until` 类型的任务；而本地模型，或那些能提供提示部分 logprobs/logits 的 API，则可以运行所有任务类型：`generate_until`、`loglikelihood`、`loglikelihood_rolling` 和 `multiple_choice`。

关于不同任务 `output_types` 与模型请求类型的更多信息，请参见[我们的文档](https://github.com/EleutherAI/lm-evaluation-harness/blob/main/docs/model_guide.md#interface)。

> [!Note]
> 对于 Anthropic Claude 3 和 GPT-4 等封闭式聊天模型 API，为了获得最佳性能，我们建议先使用 `--limit 10` 仔细查看一些示例输出，以确认生成任务中的答案提取与评分符合预期。在 `anthropic-chat-completions` 的 `--model_args` 中提供 `system="<some system prompt here>"` 来指示模型使用何种响应格式，可能会有帮助。

### 其他框架

还有一些其他库包含了通过其自身库调用 eval harness 的脚本，包括 [GPT-NeoX](https://github.com/EleutherAI/gpt-neox/blob/main/eval_tasks/eval_adapter.py)、[Megatron-DeepSpeed](https://github.com/microsoft/Megatron-DeepSpeed/blob/main/examples/MoE/readme_evalharness.md) 和 [mesh-transformer-jax](https://github.com/kingoflolz/mesh-transformer-jax/blob/master/eval_harness.py)。

如果你想创建自己的自定义集成，可以遵循[这个教程](https://github.com/EleutherAI/lm-evaluation-harness/blob/main/docs/interface.md#external-library-usage)中的说明。

### 附加功能

> [!Note]
> 对于不适合直接评测的任务，无论是由于执行不受信任代码带来的风险，还是由于评测流程本身过于复杂，都可以使用 `--predict_only` 标志来获取解码后的生成结果，供事后评测。

如果你有一台兼容 Metal 的 Mac，可以将 `--device cuda:0` 替换为 `--device mps`，使用 MPS 后端运行 eval harness（需要 PyTorch 2.1 或更高版本）。**请注意，PyTorch 的 MPS 后端仍处于开发早期阶段，因此可能存在正确性问题或不支持的操作。如果你在 MPS 后端观察到模型性能异常，我们建议先检查你的模型在 `--device cpu` 与 `--device mps` 上的一次前向传播结果是否一致。**

> [!Note]
> 你可以通过运行以下命令查看 LM 的输入长什么样：
>
> ```bash
> python write_out.py \
>     --tasks <task1,task2,...> \
>     --num_fewshot 5 \
>     --num_examples 10 \
>     --output_base_path /path/to/output/folder
> ```
>
> 这会为每个任务输出一个文本文件。

除了运行任务本身之外，如果你还想验证所执行任务的数据完整性，可以使用 `--check_integrity` 标志：

```bash
lm_eval --model openai \
    --model_args engine=davinci-002 \
    --tasks lambada_openai,hellaswag \
    --check_integrity
```

## 高级使用技巧

对于通过 HuggingFace `transformers` 库加载的模型，任何通过 `--model_args` 提供的参数都会直接传递给相应的构造函数。这意味着凡是你能用 `AutoModel` 做的事，也都可以通过我们的库完成。例如，你可以通过 `pretrained=` 传入本地路径，或者如果你使用的是通过 [PEFT](https://github.com/huggingface/peft) 微调的模型，只需在评测基础模型的调用后，在 `model_args` 参数中加上 `,peft=PATH`：

```bash
lm_eval --model hf \
    --model_args pretrained=EleutherAI/gpt-j-6b,parallelize=True,load_in_4bit=True,peft=nomic-ai/gpt4all-j-lora \
    --tasks openbookqa,arc_easy,winogrande,hellaswag,arc_challenge,piqa,boolq \
    --device cuda:0
```

通过 delta weights 提供的模型也可以借助 Hugging Face transformers 库轻松加载。在 `--model_args` 中设置 `delta` 参数以指定 delta weights，并使用 `pretrained` 参数指定它们所应用到的基础模型：

```bash
lm_eval --model hf \
    --model_args pretrained=Ejafa/llama_7B,delta=lmsys/vicuna-7b-delta-v1.1 \
    --tasks hellaswag
```

GPTQ 量化模型可以使用 [GPTQModel](https://github.com/ModelCloud/GPTQModel)（更快）或 [AutoGPTQ](https://github.com/PanQiWei/AutoGPTQ) 加载

GPTQModel：向 `model_args` 添加 `,gptqmodel=True`

```bash
lm_eval --model hf \
    --model_args pretrained=model-name-or-path,gptqmodel=True \
    --tasks hellaswag
```

AutoGPTQ：向 `model_args` 添加 `,autogptq=True`：

```bash
lm_eval --model hf \
    --model_args pretrained=model-name-or-path,autogptq=model.safetensors,gptq_use_triton=True \
    --tasks hellaswag
```

我们支持任务名中的通配符，例如你可以通过 `--task lambada_openai_mt_*` 运行所有机器翻译版的 lambada 任务。

## 保存与缓存结果

要保存评测结果，请提供 `--output_path`。我们也支持使用 `--log_samples` 标志记录模型响应，以便事后分析。

> [!TIP]
> 使用 `--use_cache <DIR>` 可以缓存评测结果，并在恢复同一组（model, task）组合的运行时跳过已评测的样本。请注意，缓存依赖 rank，因此如果运行被中断，请使用相同的 GPU 数量重新启动。你也可以使用 `--cache_requests` 来保存数据集预处理步骤，以更快恢复评测。

要将结果和样本推送到 Hugging Face Hub，请先确保具有写权限的访问令牌已设置到 `HF_TOKEN` 环境变量中。然后使用 `--hf_hub_log_args` 标志指定组织、仓库名、仓库可见性，以及是否将结果和样本推送到 Hub 中，[这里有一个 HF Hub 上的数据集示例](https://huggingface.co/datasets/KonradSzafer/lm-eval-results-demo)。例如：

```bash
lm_eval --model hf \
    --model_args pretrained=model-name-or-path,autogptq=model.safetensors,gptq_use_triton=True \
    --tasks hellaswag \
    --log_samples \
    --output_path results \
    --hf_hub_log_args hub_results_org=EleutherAI,hub_repo_name=lm-eval-results,push_results_to_hub=True,push_samples_to_hub=True,public_repo=False \
```

这样你就可以很方便地从 Hub 下载结果和样本：

```python
from datasets import load_dataset

load_dataset("EleutherAI/lm-eval-results-private", "hellaswag", "latest")
```

有关所有受支持参数的完整列表，请查看我们文档中的 [interface](https://github.com/EleutherAI/lm-evaluation-harness/blob/main/docs/interface.md) 指南！

## 结果可视化

你可以使用 Weights & Biases (W&B) 和 Zeno，无缝地可视化并分析评测框架运行结果。

### Zeno

你可以使用 [Zeno](https://zenoml.com) 来可视化 eval harness 运行结果。

首先，前往 [hub.zenoml.com](https://hub.zenoml.com) 创建账户，并在[你的账户页面](https://hub.zenoml.com/account)获取 API key。
将该 key 添加为环境变量：

```bash
export ZENO_API_KEY=[your api key]
```

你还需要安装 `lm_eval[zeno]` 这个可选扩展依赖。

要可视化结果，请使用 `log_samples` 和 `output_path` 标志运行 eval harness。
我们期望 `output_path` 包含多个文件夹，每个文件夹代表一个单独的模型名称。
因此，你可以在任意数量的任务和模型上运行评测，并将所有结果作为项目上传到 Zeno。

```bash
lm_eval \
    --model hf \
    --model_args pretrained=EleutherAI/gpt-j-6B \
    --tasks hellaswag \
    --device cuda:0 \
    --batch_size 8 \
    --log_samples \
    --output_path output/gpt-j-6B
```

然后，你可以使用 `zeno_visualize` 脚本上传结果数据：

```bash
python scripts/zeno_visualize.py \
    --data_path output \
    --project_name "Eleuther Project"
```

这会将 `data_path` 下的所有子文件夹视作不同模型，并把这些模型文件夹中的所有任务一起上传到 Zeno。
如果你在多个任务上运行 eval harness，那么 `project_name` 会作为前缀，并为每个任务创建一个项目。

你可以在 [examples/visualize-zeno.ipynb](examples/visualize-zeno.ipynb) 中找到该工作流的示例。

### Weights and Biases

通过 [Weights and Biases](https://wandb.ai/site) 集成，你现在可以花更多时间从评测结果中提炼更深层次的洞察。该集成旨在简化使用 Weights & Biases (W&B) 平台记录和可视化实验结果的流程。

该集成提供的功能包括

- 自动记录评测结果，
- 将样本记录为 W&B Tables 以便可视化，
- 将 `results.json` 文件记录为 artifact 以进行版本管理，
- 如果记录了样本，则记录 `<task_name>_eval_samples.json` 文件，
- 生成包含所有重要指标的综合报告，用于分析和可视化，
- 记录任务和 CLI 特定配置，
- 以及开箱即用地记录运行评测所用命令、GPU/CPU 数量、时间戳等更多信息。

首先你需要安装 `lm_eval[wandb]` 这个可选扩展依赖。执行 `pip install lm_eval[wandb]`。

使用你唯一的 W&B token 对当前机器进行认证。前往 https://wandb.ai/authorize 获取 token。在命令行终端中执行 `wandb login`。

像平常一样运行 eval harness，并添加 `wandb_args` 标志。使用该标志以逗号分隔字符串参数的方式提供初始化 wandb run 所需的参数（[wandb.init](https://docs.wandb.ai/ref/python/init)）。

```bash
lm_eval \
    --model hf \
    --model_args pretrained=microsoft/phi-2,trust_remote_code=True \
    --tasks hellaswag,mmlu_abstract_algebra \
    --device cuda:0 \
    --batch_size 8 \
    --output_path output/phi-2 \
    --limit 10 \
    --wandb_args project=lm-eval-harness-integration \
    --log_samples
```

在 stdout 中，你会看到指向 W&B run 页面和生成报告的链接。你可以在 [examples/visualize-wandb.ipynb](examples/visualize-wandb.ipynb) 中找到该工作流的示例，以及超出 CLI 范围的集成示例。

## 贡献

查看我们的 [未解决 issue](https://github.com/EleutherAI/lm-evaluation-harness/issues)，欢迎随时提交 pull request！

如果你想进一步了解这个库以及各部分如何协同工作，请参见我们的[文档页面](https://github.com/EleutherAI/lm-evaluation-harness/tree/main/docs)。

要开始进行开发，请先克隆仓库并安装开发依赖：

```bash
git clone https://github.com/EleutherAI/lm-evaluation-harness
cd lm-evaluation-harness
pip install -e ".[dev,hf]"
````

### 实现新任务

要在 eval harness 中实现一个新任务，请参见[这份指南](./docs/new_task_guide.md)。

总体来说，在处理提示词和其他评测细节相关问题时，我们遵循以下优先级列表：

1. 如果训练 LLM 的人群中已经广泛达成一致，就采用该一致认可的流程。
2. 如果存在清晰且毫无歧义的官方实现，就采用该流程。
3. 如果评测 LLM 的人群中已经广泛达成一致，就采用该一致认可的流程。
4. 如果存在多个常见实现，但尚未形成普遍或广泛共识，就在这些常见实现中使用我们的首选方案。与前面一样，优先从 LLM 训练论文中出现的实现中选择。

这些是指导原则而非硬性规则，在特殊情况下可以被推翻。

我们尽量优先与其他团队使用的流程保持一致，以减少人们无可避免地跨论文比较不同运行结果时带来的伤害，尽管我们并不鼓励这种做法。从历史上看，我们也优先参考 [Language Models are Few Shot Learners](https://arxiv.org/abs/2005.14165) 中的实现，因为我们最初的目标就是与该论文中的结果进行比较。

### 支持

获得支持的最佳方式是在此仓库中创建 issue，或加入 [EleutherAI Discord server](https://discord.gg/eleutherai)。`#lm-thunderdome` 频道专门用于该项目开发，`#release-discussion` 频道则用于为我们的发布版本提供支持。如果你使用过这个库，并且有积极或消极的体验，我们都很希望听到你的反馈！

## 可选 Extras

可以通过 `pip install -e ".[NAME]"` 安装 extras 依赖

### 模型后端

这些 extras 会安装运行特定模型后端所需的依赖：

| 名称           | 说明                                             |
|----------------|--------------------------------------------------|
| hf             | HuggingFace Transformers（torch、transformers、accelerate、peft） |
| vllm           | vLLM 快速推理                                    |
| api            | API 模型（OpenAI、Anthropic、本地服务器）        |
| gptq           | AutoGPTQ 量化模型                                |
| gptqmodel      | GPTQModel 量化模型                               |
| ibm_watsonx_ai | IBM watsonx.ai 模型                              |
| ipex           | Intel IPEX 后端                                  |
| habana         | Intel Gaudi 后端                                 |
| optimum        | Intel OpenVINO 模型                              |
| neuronx        | AWS Inferentia2 实例                             |
| winml          | Windows ML（ONNX Runtime GenAI）- CPU/GPU/NPU    |
| sparsify       | Sparsify 模型操控                                |
| sae_lens       | SAELens 模型操控                                 |

### 任务依赖

这些 extras 会安装特定评测任务所需的依赖：

| 名称                 | 说明                           |
|----------------------|--------------------------------|
| tasks                | 所有任务专用依赖               |
| acpbench             | ACP Bench 任务                 |
| audiolm_qwen         | Qwen2 音频模型                 |
| ifeval               | IFEval 任务                    |
| japanese_leaderboard | 日语 LLM 任务                  |
| longbench            | LongBench 任务                 |
| math                 | 数学答案校验                   |
| multilingual         | 多语言分词器                   |
| ruler                | RULER 任务                     |

### 开发与工具

| 名称          | 说明                           |
|---------------|--------------------------------|
| dev           | 代码检查与贡献相关依赖         |
| hf_transfer   | 加速 HF 下载                   |
| sentencepiece | SentencePiece 分词器           |
| unitxt        | Unitxt 任务                    |
| wandb         | Weights & Biases 日志记录      |
| zeno          | Zeno 结果可视化                |

## 引用方式

```text
@misc{eval-harness,
  author       = {Gao, Leo and Tow, Jonathan and Abbasi, Baber and Biderman, Stella and Black, Sid and DiPofi, Anthony and Foster, Charles and Golding, Laurence and Hsu, Jeffrey and Le Noac'h, Alain and Li, Haonan and McDonell, Kyle and Muennighoff, Niklas and Ociepa, Chris and Phang, Jason and Reynolds, Laria and Schoelkopf, Hailey and Skowron, Aviya and Sutawika, Lintang and Tang, Eric and Thite, Anish and Wang, Ben and Wang, Kevin and Zou, Andy},
  title        = {The Language Model Evaluation Harness},
  month        = 07,
  year         = 2024,
  publisher    = {Zenodo},
  version      = {v0.4.3},
  doi          = {10.5281/zenodo.12608602},
  url          = {https://zenodo.org/records/12608602}
}
```
