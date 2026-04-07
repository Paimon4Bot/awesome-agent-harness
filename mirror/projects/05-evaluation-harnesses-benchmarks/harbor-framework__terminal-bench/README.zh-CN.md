# terminal-bench

```text
#####################################################################
#  _____                   _             _     ______________       #
# |_   _|__ _ __ _ __ ___ (_)_ __   __ _| |   ||            ||      #
#   | |/ _ \ '__| '_ ` _ \| | '_ \ / _` | |   || >          ||      #
#   | |  __/ |  | | | | | | | | | | (_| | |   ||            ||      #
#   |_|\___|_|  |_| |_| |_|_|_| |_|\__,_|_|   ||____________||      #
#   ____                  _                   |______________|      #
#  | __ )  ___ _ __   ___| |__                 \\############\\     #
#  |  _ \ / _ \ '_ \ / __| '_ \                 \\############\\    # 
#  | |_) |  __/ | | | (__| | | |                 \      ____    \   #
#  |____/ \___|_| |_|\___|_| |_|                  \_____\___\____\  #
#                                                                   #
#####################################################################
```

[![Discord](https://img.shields.io/badge/Join_our_discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/6xWPKhGDbA) [![Github](https://img.shields.io/badge/T--Bench-000000?style=for-the-badge&logo=github&logoColor=000&logoColor=white)](https://github.com/laude-institute/terminal-bench) [![Docs](https://img.shields.io/badge/Docs-000000?style=for-the-badge&logo=mdbook&color=105864)](https://www.tbench.ai/docs)

> **📢 公告**：新用户请查看 [**harbor**](https://github.com/laude-institute/harbor)，这是我们可用于运行 Terminal-Bench 2.0 的新框架！

Terminal-Bench 是一个用于在真实终端环境中测试 AI 代理的基准。从编译代码到训练模型再到搭建服务器，Terminal-Bench 评估代理自主处理现实世界端到端任务的能力。

无论您是在构建 LLM 代理、基准测试框架，还是对系统级推理进行压力测试，Terminal-Bench 都提供了可复现的任务套件，以及一个专为实际场景评估设计的执行框架。

Terminal-Bench 由两部分组成：一个**任务数据集**和一个将语言模型连接到终端沙箱的**执行框架**。

Terminal-Bench 目前处于 **beta** 阶段，包含约 100 个任务。在接下来的几个月里，我们将把 Terminal-Bench 扩展为面向文本环境中 AI 代理的综合测试平台。欢迎任何贡献，尤其是新的高难度任务！

## 快速开始

我们的[快速开始指南](https://www.tbench.ai/docs/installation)将引导您完成仓库安装和[贡献](https://www.tbench.ai/docs/contributing)。

Terminal-Bench 以 pip 包形式分发，可通过 Terminal-Bench CLI 运行：`tb`。

```bash
uv tool install terminal-bench
```

或

```bash
pip install terminal-bench
```

## 更多文档

- [任务画廊](https://www.tbench.ai/tasks)
- [任务想法](https://www.tbench.ai/docs/task-ideas) - 浏览社区贡献的任务想法
- [仪表板文档](https://www.tbench.ai/docs/dashboard) - 关于 Terminal-Bench 仪表板的信息

## 核心组件

### 任务数据集

Terminal-Bench 中的每个任务包括

- 一段英文指令，
- 一个测试脚本，用于验证语言模型 / 代理是否成功完成任务，
- 一个用于解决该任务的参考（“oracle”）解答。

任务位于仓库的 [`tasks`](./tasks) 文件夹中，而前面提到的当前任务列表则提供了一个便于浏览的概览。

### 执行框架

执行框架将语言模型连接到沙箱化的终端环境。在[安装 terminal-bench 包](https://www.tbench.ai/docs/installation)（以及依赖项 `uv` 和 `Docker`）后，您可以使用以下命令查看如何运行该框架：

```bash
tb run --help
```

有关运行该执行框架及其选项的详细信息，请参阅[文档](https://www.tbench.ai/docs/first-steps)。

### 提交到排行榜

Terminal-Bench-Core v0.1.1 是 Terminal-Bench beta 版发布所对应的任务集，也对应当前的排行榜。要在其上进行评估，请向执行框架传递 `--dataset-name terminal-bench-core` 和 `--dataset-version 0.1.1`。例如：

```bash
tb run \
    --agent terminus \
    --model anthropic/claude-3-7-latest \
    --dataset-name terminal-bench-core
    --dataset-version 0.1.1
    --n-concurrent 8
```

有关提交到排行榜的更详细说明，请查看我们的[排行榜提交指南](https://www.tbench.ai/docs/submitting-to-leaderboard)。

有关 Terminal-Bench 数据集和版本管理的更多信息，请查看我们的[注册表概览](https://www.tbench.ai/docs/registry)。

## 贡献

### 创建新任务

查看我们的[任务贡献快速开始](https://harborframework.com/docs/task-format)来创建新任务。

### 创建新适配器

查看[如何为新基准测试创建新适配器](https://harborframework.com/docs/adapters)来贡献新适配器。

## 引用

如果您觉得 Terminal-Bench 有用，请按以下方式引用：

```bibtex
@misc{merrill2026terminalbenchbenchmarkingagentshard,
      title={Terminal-Bench: Benchmarking Agents on Hard, Realistic Tasks in Command Line Interfaces}, 
      author={Mike A. Merrill and Alexander G. Shaw and Nicholas Carlini and Boxuan Li and Harsh Raj and Ivan Bercovich and Lin Shi and Jeong Yeon Shin and Thomas Walshe and E. Kelly Buchanan and Junhong Shen and Guanghao Ye and Haowei Lin and Jason Poulos and Maoyu Wang and Marianna Nezhurina and Jenia Jitsev and Di Lu and Orfeas Menis Mastromichalakis and Zhiwei Xu and Zizhao Chen and Yue Liu and Robert Zhang and Leon Liangyu Chen and Anurag Kashyap and Jan-Lucas Uslu and Jeffrey Li and Jianbo Wu and Minghao Yan and Song Bian and Vedang Sharma and Ke Sun and Steven Dillmann and Akshay Anand and Andrew Lanpouthakoun and Bardia Koopah and Changran Hu and Etash Guha and Gabriel H. S. Dreiman and Jiacheng Zhu and Karl Krauth and Li Zhong and Niklas Muennighoff and Robert Amanfu and Shangyin Tan and Shreyas Pimpalgaonkar and Tushar Aggarwal and Xiangning Lin and Xin Lan and Xuandong Zhao and Yiqing Liang and Yuanli Wang and Zilong Wang and Changzhi Zhou and David Heineman and Hange Liu and Harsh Trivedi and John Yang and Junhong Lin and Manish Shetty and Michael Yang and Nabil Omi and Negin Raoof and Shanda Li and Terry Yue Zhuo and Wuwei Lin and Yiwei Dai and Yuxin Wang and Wenhao Chai and Shang Zhou and Dariush Wahdany and Ziyu She and Jiaming Hu and Zhikang Dong and Yuxuan Zhu and Sasha Cui and Ahson Saiyed and Arinbjörn Kolbeinsson and Jesse Hu and Christopher Michael Rytting and Ryan Marten and Yixin Wang and Alex Dimakis and Andy Konwinski and Ludwig Schmidt},
      year={2026},
      eprint={2601.11868},
      archivePrefix={arXiv},
      primaryClass={cs.SE},
      url={https://arxiv.org/abs/2601.11868}, 
}
```
