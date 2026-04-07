[<img width="295" src="https://inspect.ai-safety-institute.org.uk/images/aisi-logo.svg" alt="UK AISI Logo"/>](https://aisi.gov.uk/)<!-- markdownlint-disable-line MD033 MD041 -->

欢迎来到 **Inspect Evals**。这是一个面向 [Inspect AI](https://inspect.ai-safety-institute.org.uk/) 的、由社区贡献的 LLM 评测仓库。Inspect Evals 由 [UK AISI](https://aisi.gov.uk/)、[Arcadia Impact](https://www.arcadiaimpact.org/) 和 [Vector Institute](https://vectorinstitute.ai/) 协作创建。

📚 [文档](https://ukgovernmentbeis.github.io/inspect_evals/)

---

欢迎并鼓励社区贡献！有关提交新评测的详细信息，请参阅[贡献指南](CONTRIBUTING.md)。

如果你有一般性咨询、建议或合作意向，请通过以下 [Google Form](https://docs.google.com/forms/d/e/1FAIpQLSeOT_nSXvc_GZSo3uRqFlZlgGEGmOAh7bm4yFuB34ZzZjxk_g/viewform?usp=dialog) 与我们联系。

本仓库由 [Inspect Evals 维护者](MAINTAINERS.md) 维护。

# 快速开始

Inspect Evals 推荐使用的 Python 版本是 3.11 或 3.12。在这些版本上，你应该能够运行所有 eval，也能在没有问题的情况下开发此代码库。你可以通过运行以下命令来安装并固定特定的 Python 版本：

```bash
uv python pin 3.11
```

至于 Python 3.13，除了 `sciknoweval` 之外，你应该能够运行所有 eval（其依赖是 `gensim`，目前尚不支持 3.13+）。在 3.13 下进行开发理论上可行，但测试相对较少，如果你遇到问题，请告诉我们。

关于 Python 3.14，在撰写本文时，许多包尚未发布适用于 3.14 的版本，因此目前不受支持。其中，部分 Inspect Evals 会用到的主要包之一是 `torch`。如果你发现 `uv sync` 在 3.14 上可以成功运行，请告诉我们，我们会删除这一段。  

下面展示的是一个典型 eval 的工作流程。某些评测需要额外的依赖或安装步骤。如果你的 eval 需要额外依赖，安装说明位于该 eval 子目录中的 README 文件中。

<!-- Usage: Automatically Generated -->
## 用法

### 安装

使用 Inspect Evals 有两种方式：一种是通过 PyPI 作为你自己项目的依赖来使用，另一种是作为独立的 GitHub 仓库检出后使用。

如果你通过 PyPI 使用它，请通过以下命令安装该包及其依赖：

```bash
pip install inspect-evals
```

如果你是在其仓库中使用 Inspect Evals，请先安装必要依赖：

```bash
uv sync
```

### 运行评测

现在你可以开始评估模型了。为简化说明，本节假设你是从独立仓库中使用 Inspect Evals。如果不是这种情况，且你在自己的项目中没有使用 `uv` 管理依赖，那么你可以使用相同命令，只需去掉 `uv run`。

```bash
uv run inspect eval inspect_evals/arc_easy --model openai/gpt-5-nano
uv run inspect eval inspect_evals/arc_challenge --model openai/gpt-5-nano
```

如需同时运行多个任务，请使用 `inspect eval-set`：

```bash
uv run inspect eval-set inspect_evals/arc_easy inspect_evals/arc_challenge
```

你也可以将任务作为普通 Python 对象导入，并在 Python 中运行它们：

```python
from inspect_ai import eval, eval_set
from inspect_evals.arc import arc_easy, arc_challenge
eval(arc_easy)
eval_set([arc_easy, arc_challenge], log_dir='logs-run-42')
```

运行评测后，你可以使用 `inspect view` 命令查看其日志：

```bash
uv run inspect view
```

对于 VS Code，你也可以下载用于查看日志的 [Inspect AI 日志查看扩展](https://inspect.ai-safety-institute.org.uk/log-viewer.html)。

如果你不想每次运行评测时都指定 `--model`，可以在工作目录中创建一个 `.env` 配置文件，在其中定义 `INSPECT_EVAL_MODEL` 环境变量以及你的 API 密钥。例如：

```bash
INSPECT_EVAL_MODEL=anthropic/claude-opus-4-1-20250805
ANTHROPIC_API_KEY=<anthropic-api-key>
```
<!-- /Usage: Automatically Generated -->

Inspect 支持许多模型提供商，包括 OpenAI、Anthropic、Google、Mistral、Azure AI、AWS Bedrock、Together AI、Groq、Hugging Face、vLLM、Ollama 等等。更多细节请参阅 [Model Providers](https://inspect.ai-safety-institute.org.uk/models.html) 文档。

你也许还能使用较新版本的 pip（25.1+）通过 `pip install --group dev .` 或 `pip install --group dev '.[swe_bench]'` 来安装该项目。不过这并非官方支持的方式。

## 文档

有关如何构建文档的详细信息，请参阅[文档指南](docs/documentation.md)。

有关运行测试和 CI 开关的信息，请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 中的技术贡献指南。

## 硬件建议

### 磁盘

我们建议为 Inspect Evals 至少保留 35 GB 可用磁盘空间：完整安装大约需要 10 GB，你还需要为 uv 缓存和数据集缓存预留一些空间（大多数都很小，但某些如 MMIU 会占用 13 GB）。

运行某些 eval（例如 CyBench、GDM capabilities evals）可能需要超出上述容量的额外空间，因为它们会拉取 Docker 镜像。对于文件树中包含 Dockerfile 的 eval，我们建议在上面 35 GB 的基础上，额外至少预留 65 GB 的空间来运行（虽然你也许可以在更少空间下运行）。

总的来说，拥有 100 GB 可用空间会更从容。如果你在拥有 100+ GB 可用空间的情况下仍然出现空间不足，请告诉我们，这可能是一个 bug。

### 内存

某个 eval 所需的内存因评测不同而差异很大。大多数 eval 在仅有 0.5 GB 空闲内存时也可以运行。不过，一些拥有较大数据集的 eval 需要 2-3 GB 或更多。而一些使用 Docker 的 eval（例如某些 GDM capabilities evals）则最多需要 32 GB 内存。

## Harbor Framework 评测

若要运行 Harbor Framework 中的评测（例如 Terminal-Bench 2.0、SWE-Bench Pro），请使用 [Inspect Harbor](https://github.com/meridianlabs-ai/inspect_harbor) 包，它提供了使用 Inspect AI 运行 Harbor 任务的接口。

# 评测列表
<!-- Eval Listing: Automatically Generated -->
## 编码

- ### [APPS: Automated Programming Progress Standard](src/inspect_evals/apps)

  APPS 是一个用于评估模型在 Python 编程任务上表现的数据集，覆盖三个难度级别：入门级 1,000 道、面试级 3,000 道、竞赛级 1,000 道。该数据集另外包含 5,000 个训练样本，总计 10,000 个样本。我们在测试划分的问题上进行评估，这些问题由编码面试中常见的编程题组成。
  <sub><sup>贡献者：[@camtice](https://github.com/camtice)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/apps
  ```

- ### [AgentBench: Evaluate LLMs as Agents](src/inspect_evals/agent_bench)

  一个用于将 LLM 作为 Agent 进行评估的基准。
  <sub><sup>贡献者：[@Felhof](https://github.com/Felhof), [@hannagabor](https://github.com/hannagabor), [@shaheenahmedc](https://github.com/shaheenahmedc)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/agent_bench_os
  ```

- ### [BigCodeBench: Benchmarking Code Generation with Diverse Function Calls and Complex Instructions](src/inspect_evals/bigcodebench)

  一个 Python 编码基准，包含 1,140 个多样化问题，涉及众多 Python 库。
  <sub><sup>贡献者：[@tim-hua-01](https://github.com/tim-hua-01)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/bigcodebench
  ```

- ### [CORE-Bench](src/inspect_evals/core_bench)

  评估 LLM Agent 在计算上复现一组科学论文结果的能力。
  <sub><sup>贡献者：[@enerrio](https://github.com/enerrio)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/core_bench
  ```

- ### [ClassEval: A Manually-Crafted Benchmark for Evaluating LLMs on Class-level Code Generation](src/inspect_evals/class_eval)

  使用 100 个耗费 500 人工小时构建的任务，评估 LLM 在类级代码生成上的表现。研究表明，相比方法级任务，LLM 在类级任务上的表现更差。
  <sub><sup>贡献者：[@zhenningdavidliu](https://github.com/zhenningdavidliu)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/class_eval
  ```

- ### [ComputeEval: CUDA Code Generation Benchmark](src/inspect_evals/compute_eval)

  评估 LLM 生成正确 CUDA 代码的能力，涵盖内核实现、内存管理和并行算法优化任务。
  <sub><sup>贡献者：[@Vitamoon](https://github.com/Vitamoon)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/compute_eval
  ```

- ### [DS-1000: A Natural and Reliable Benchmark for Data Science Code Generation](src/inspect_evals/ds1000)

  一个代码生成基准，包含一千个数据科学问题，覆盖七个 Python 库。
  <sub><sup>贡献者：[@bienehito](https://github.com/bienehito)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/ds1000
  ```

- ### [Frontier-CS: Benchmarking LLMs on Computer Science Problems](src/inspect_evals/frontier_cs)

  238 个开放式计算机科学问题，覆盖算法方向（172）和
  研究方向（66）。问题采用连续的部分得分机制，
  其中算法解通过编译和测试用例检查来评估，
  研究解则通过自定义评估脚本来评分。当前前沿模型的得分
  仍远低于人类专家基线，因此这是一个具有挑战性且尚未饱和的基准。
  <sub><sup>贡献者：[@JayBaileyCS](https://github.com/JayBaileyCS)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/frontier_cs
  uv run inspect eval inspect_evals/frontier_cs_algorithmic
  uv run inspect eval inspect_evals/frontier_cs_research
  ```

- ### [HumanEval: Python Function Generation from Instructions](src/inspect_evals/humaneval)

  评估语言模型仅依据作为文档字符串提供的自然语言指令，编写正确 Python 函数的准确程度。
  <sub><sup>贡献者：[@adil-a](https://github.com/adil-a)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/humaneval
  ```

- ### [IFEvalCode: Controlled Code Generation](src/inspect_evals/ifevalcode)

  评估代码生成模型在遵守特定指令约束的同时生成正确代码的能力，覆盖 8 种编程语言。
  <sub><sup>贡献者：[@PranshuSrivastava](https://github.com/PranshuSrivastava)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/ifevalcode
  ```

- ### [KernelBench: Can LLMs Write Efficient GPU Kernels?](src/inspect_evals/kernelbench)

  一个用于评估 LLM 编写高效 GPU 内核能力的基准。
  <sub><sup>贡献者：[@jiito](https://github.com/jiito)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/kernelbench
  ```

- ### [LiveCodeBench-Pro: Competitive Programming Benchmark](src/inspect_evals/livecodebench_pro)

  使用专门的 Docker 沙箱（LightCPVerifier）执行并评判 C++ 代码提交，对隐藏测试用例施加时间和内存限制，以此评估 LLM 在竞赛编程问题上的表现。
  <sub><sup>贡献者：[@gjoshi2424](https://github.com/gjoshi2424)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/livecodebench_pro
  ```

- ### [MBPP: Basic Python Coding Challenges](src/inspect_evals/mbpp)

  衡量语言模型根据简单自然语言描述生成简短 Python 程序的能力，以测试其基础编码熟练度。
  <sub><sup>贡献者：[@jddantes](https://github.com/jddantes)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mbpp
  ```

- ### [MLE-bench: Evaluating Machine Learning Agents on Machine Learning Engineering](src/inspect_evals/mle_bench)

  来自 75 个 Kaggle 竞赛的机器学习任务。
  <sub><sup>贡献者：[@samm393](https://github.com/samm393)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mle_bench
  uv run inspect eval inspect_evals/mle_bench_full
  uv run inspect eval inspect_evals/mle_bench_lite
  ```

- ### [MLRC-Bench: Can Language Agents Solve Machine Learning Research Challenges?](src/inspect_evals/mlrc_bench)

  该基准评估基于 LLM 的研究 Agent 提出并实现新方法的能力，任务取自近期 ML 会议竞赛，同时从新颖性和有效性两个方面，与基线方案和人类顶尖方案进行比较。
  <sub><sup>贡献者：[@dmn-sjk](https://github.com/dmn-sjk)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mlrc_bench
  ```

- ### [PaperBench: Evaluating AI's Ability to Replicate AI Research (Work In Progress)](src/inspect_evals/paperbench)

  该评测衡量 Agent 从零复现 20 篇 ICML 2024 Spotlight
  和 Oral 论文的能力。给定论文 PDF、包含澄清信息的补充说明
  以及定义评估标准的 rubric，Agent 必须通过编写和执行代码
  来复现实验论文中的关键结果。
  
  > **注意：** 该 eval 仍在开发中。状态请参见 <https://github.com/UKGovernmentBEIS/inspect_evals/issues/334>。
  <sub><sup>贡献者：[@vhong-aisi](https://github.com/vhong-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/paperbench
  ```

- ### [SWE-Lancer: Can Frontier LLMs Earn $1 Million from Real-World Freelance Software Engineering?](src/inspect_evals/swe_lancer)

  一个由 Upwork 上自由软件工程任务构成的基准，总真实世界报酬价值达 100 万美元。
  <sub><sup>贡献者：[@NelsonG-C](https://github.com/NelsonG-C), [@MattFisher](https://github.com/MattFisher)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/swe_lancer
  ```

- ### [SWE-bench Verified: Resolving Real-World GitHub Issues](src/inspect_evals/swe_bench)

  评估 AI 解决来自 12 个流行 Python GitHub 仓库中的真实软件工程问题的能力，反映现实中的编码与调试场景。
  <sub><sup>贡献者：[@max-kaufmann](https://github.com/max-kaufmann)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/swe_bench
  uv run inspect eval inspect_evals/swe_bench_verified_mini
  ```

- ### [SciCode: A Research Coding Benchmark Curated by Scientists](src/inspect_evals/scicode)

  SciCode 测试语言模型生成代码以解决科学研究问题的能力。它从数学、物理、化学、生物和材料科学中选取 65 个问题来评估模型。
  <sub><sup>贡献者：[@xantheocracy](https://github.com/xantheocracy)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/scicode
  ```

- ### [USACO: USA Computing Olympiad](src/inspect_evals/usaco)

  评估语言模型在四个难度级别的高难度奥林匹克编程题上的表现。
  <sub><sup>贡献者：[@danwilhelm](https://github.com/danwilhelm)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/usaco
  ```

- ### [scBench: A Benchmark for Single-Cell RNA-seq Analysis](src/inspect_evals/scbench)

  评估模型能否在确定性评分下完成实用的单细胞 RNA-seq 分析任务。任务要求与 `.h5ad` 数据文件进行实际交互，Agent 必须加载并分析数据以给出正确答案。覆盖 5 种测序平台和 7 类任务中的 30 个经典任务。
  <sub><sup>贡献者：[@retroam](https://github.com/retroam)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/scbench
  ```

## 助手

- ### [AssistantBench: Can Web Agents Solve Realistic and Time-Consuming Tasks?](src/inspect_evals/assistant_bench)

  测试 AI Agent 是否能在 Web 上执行真实世界中耗时的任务。
  <sub><sup>贡献者：[@nlpet](https://github.com/nlpet), [@caspardh](https://github.com/caspardh)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/assistant_bench_closed_book_zero_shot
  uv run inspect eval inspect_evals/assistant_bench_closed_book_one_shot
  uv run inspect eval inspect_evals/assistant_bench_web_search_zero_shot
  uv run inspect eval inspect_evals/assistant_bench_web_search_one_shot
  uv run inspect eval inspect_evals/assistant_bench_web_browser
  ```

- ### [BFCL: Berkeley Function-Calling Leaderboard](src/inspect_evals/bfcl)

  在 Berkeley Function-Calling Leaderboard（BFCL）的简化划分上评估 LLM 的函数/工具调用能力。
  <sub><sup>贡献者：[@alex-remedios-aisi](https://github.com/alex-remedios-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/bfcl
  ```

- ### [BrowseComp: A Simple Yet Challenging Benchmark for Browsing Agents](src/inspect_evals/browse_comp)

  一个用于评估 Agent 浏览网页能力的基准。
  该数据集由具有挑战性的问题组成，通常需要访问网络才能正确回答。
  <sub><sup>贡献者：[@AnselmC](https://github.com/AnselmC)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/browse_comp
  ```

- ### [GAIA: A Benchmark for General AI Assistants](src/inspect_evals/gaia)

  提出需要推理、多模态处理、网页浏览以及通用工具使用熟练度等基础能力的真实世界问题。GAIA 的问题对人类而言概念上很简单，但对大多数先进 AI 来说具有挑战性。
  <sub><sup>贡献者：[@max-kaufmann](https://github.com/max-kaufmann)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gaia
  uv run inspect eval inspect_evals/gaia_level1
  uv run inspect eval inspect_evals/gaia_level2
  uv run inspect eval inspect_evals/gaia_level3
  ```

- ### [GDPval](src/inspect_evals/gdpval)

  GDPval 衡量模型在 44 个职业中的经济价值型真实任务上的表现。
  <sub><sup>贡献者：[@jeqcho](https://github.com/jeqcho)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gdpval
  ```

- ### [Mind2Web: Towards a Generalist Agent for the Web](src/inspect_evals/mind2web)

  一个用于开发和评估通用 Web Agent 的数据集，这类 Agent 能根据语言指令在任意网站上完成复杂任务。
  <sub><sup>贡献者：[@dr3s](https://github.com/dr3s)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mind2web
  ```

- ### [OSWorld: Multimodal Computer Interaction Tasks](src/inspect_evals/osworld)

  测试 AI Agent 在模拟计算机环境中执行真实、开放式任务的能力，这些任务需要跨多种输入模态进行复杂交互。
  <sub><sup>贡献者：[@epatey](https://github.com/epatey)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/osworld
  uv run inspect eval inspect_evals/osworld_small
  ```

- ### [Sycophancy Eval](src/inspect_evals/sycophancy)

  在多种自由文本生成任务中评估语言模型的谄媚倾向。
  <sub><sup>贡献者：[@alexdzm](https://github.com/alexdzm)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/sycophancy
  ```

- ### [Tau2](src/inspect_evals/tau2)

  在双控制环境中评估对话 Agent
  <sub><sup>贡献者：[@mmulet](https://github.com/mmulet)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/tau2_airline
  uv run inspect eval inspect_evals/tau2_retail
  uv run inspect eval inspect_evals/tau2_telecom
  ```

## 网络安全

- ### [CTI-REALM: Cyber Threat Intelligence Detection Rule Development Benchmark](src/inspect_evals/cti_realm)

  评估 AI 系统分析网络威胁情报并开发
  全面检测能力的能力，采用一个真实的 5 个子任务工作流：
  MITRE 技术映射、数据源发现、Sigma 规则生成、KQL
  开发并基于真实遥测数据测试，以及结果分析。
  <sub><sup>贡献者：[@arjun180-new](https://github.com/arjun180-new)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cti-realm-25
  uv run inspect eval inspect_evals/cti-realm-50
  uv run inspect eval inspect_evals/cti-realm-25-minimal
  uv run inspect eval inspect_evals/cti-realm-25-seeded
  ```

- ### [CVEBench:  Benchmark for AI Agents Ability to Exploit Real-World Web Application Vulnerabilities](src/inspect_evals/cve_bench)

  刻画 AI Agent 利用现实世界 Web 应用漏洞的能力。该基准旨在使用 40 个真实世界 CVE，对 Agent 的安全推理能力进行更贴近现实的评估。
  <sub><sup>贡献者：[@yuxuan18](https://github.com/yuxuan18), [@aokellermann](https://github.com/aokellermann), [@dylanbowman314](https://github.com/dylanbowman314), [@pli482004](https://github.com/pli482004), [@akulguptax](https://github.com/akulguptax), [@adarshdanda06](https://github.com/adarshdanda06), [@rightegg](https://github.com/rightegg), [@rightegg](https://github.com/rightegg), [@jensen](https://github.com/jensen), [@eihli](https://github.com/eihli), [@JasonBenn](https://github.com/JasonBenn), [@inigo](https://github.com/inigo), [@dhir](https://github.com/dhir), [@SudhitRao](https://github.com/SudhitRao), [@YuVictor123](https://github.com/YuVictor123), [@Cloakless](https://github.com/Cloakless), [@ddkang](https://github.com/ddkang), [@Scott-Simmons](https://github.com/Scott-Simmons)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cve_bench
  ```

- ### [CYBERSECEVAL 3: Advancing the Evaluation of Cybersecurity Risks and Capabilities in Large Language Models](src/inspect_evals/cyberseceval_3)

  评估大语言模型对第三方、应用开发者和终端用户带来的网络安全风险。
  <sub><sup>贡献者：[@onionymous](https://github.com/onionymous)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cyse3_visual_prompt_injection
  ```

- ### [Catastrophic Cyber Capabilities Benchmark (3CB): Robustly Evaluating LLM Agent Cyber Offense Capabilities](src/inspect_evals/threecb)

  一个用于评估 LLM Agent 网络攻击能力的基准。
  <sub><sup>贡献者：[@derpyplops](https://github.com/derpyplops), [@ralphptorres](https://github.com/ralphptorres), [@Scott-Simmons](https://github.com/Scott-Simmons)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/threecb
  ```

- ### [Cybench: Capture-The-Flag Cybersecurity Challenges](src/inspect_evals/cybench)

  使用 40 个网络安全竞赛中的 39 个实操、专业级挑战测试语言模型的网络安全技能，这些挑战覆盖不同难度层级和安全概念。由于 GPL 许可限制，排除了 motp 挑战。
  <sub><sup>贡献者：[@sinman-aisi](https://github.com/sinman-aisi), [@sam-deverett-dsit](https://github.com/sam-deverett-dsit), [@kola-aisi](https://github.com/kola-aisi), [@pgiav](https://github.com/pgiav)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cybench
  ```

- ### [CyberGym: Evaluating AI Agents' Real-World Cybersecurity Capabilities at Scale](src/inspect_evals/cybergym)

  一个大规模、高质量的网络安全评测框架，旨在严格评估 AI Agent 在现实世界漏洞分析任务中的能力。CyberGym 包含 1,507 个基准实例，涵盖来自 188 个大型软件项目的历史漏洞。
  <sub><sup>贡献者：[@wzunknown](https://github.com/wzunknown), [@stneng](https://github.com/stneng), [@LostBenjamin](https://github.com/LostBenjamin), [@pro-wh](https://github.com/pro-wh)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cybergym
  ```

- ### [CyberMetric: A Benchmark Dataset based on Retrieval-Augmented Generation for Evaluating LLMs in Cybersecurity Knowledge](src/inspect_evals/cybermetric)

  包含 80、500、2000 和 10000 道选择题的数据集，用于评估模型在网络安全九个领域中的理解能力。
  <sub><sup>贡献者：[@neilshaabi](https://github.com/neilshaabi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cybermetric_80
  uv run inspect eval inspect_evals/cybermetric_500
  uv run inspect eval inspect_evals/cybermetric_2000
  uv run inspect eval inspect_evals/cybermetric_10000
  ```

- ### [CyberSecEval_2: Cybersecurity Risk and Vulnerability Evaluation](src/inspect_evals/cyberseceval_2)

  评估语言模型的网络安全风险，重点测试其滥用编程解释器的潜力、遭受恶意提示注入的脆弱性，以及利用已知软件漏洞的能力。
  <sub><sup>贡献者：[@its-emile](https://github.com/its-emile)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/cyse2_interpreter_abuse
  uv run inspect eval inspect_evals/cyse2_prompt_injection
  uv run inspect eval inspect_evals/cyse2_vulnerability_exploit
  ```

- ### [GDM Dangerous Capabilities: Capture the Flag](src/inspect_evals/gdm_in_house_ctf)

  CTF 挑战覆盖 Web 应用漏洞、现成漏洞利用、数据库、Linux 提权、密码破解和喷洒等内容。展示了工具使用以及对不受信任模型代码进行沙箱隔离的能力。
  <sub><sup>贡献者：[@XkunW](https://github.com/XkunW)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gdm_in_house_ctf
  ```

- ### [InterCode: Security and Coding Capture-the-Flag Challenges](src/inspect_evals/gdm_intercode_ctf)

  通过实用的夺旗赛（CTF）网络安全场景，测试 AI 在编码、密码学、逆向工程和漏洞识别方面的能力。
  <sub><sup>贡献者：[@jjallaire](https://github.com/jjallaire)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gdm_intercode_ctf
  ```

- ### [SEvenLLM: A benchmark to elicit, and improve cybersecurity incident analysis and response abilities in LLMs for Security Events.](src/inspect_evals/sevenllm)

  用于分析网络安全事件，由两大类主要任务构成：理解与生成，并进一步细分为 28 个子任务类别。
  <sub><sup>贡献者：[@kingroryg](https://github.com/kingroryg)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/sevenllm_mcq_zh
  uv run inspect eval inspect_evals/sevenllm_mcq_en
  uv run inspect eval inspect_evals/sevenllm_qa_zh
  uv run inspect eval inspect_evals/sevenllm_qa_en
  ```

- ### [SecQA: A Concise Question-Answering Dataset for Evaluating Large Language Models in Computer Security](src/inspect_evals/sec_qa)

  “Security Question Answering” 数据集用于评估 LLM 对安全原则的理解和应用。SecQA 包含 “v1” 和 “v2” 两个选择题数据集，旨在提供两个层级的网络安全评估标准。问题由 GPT-4 基于教材《Computer Systems Security: Planning for Success》生成，并经人工审核。
  <sub><sup>贡献者：[@matthewreed26](https://github.com/matthewreed26)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/sec_qa_v1
  uv run inspect eval inspect_evals/sec_qa_v1_5_shot
  uv run inspect eval inspect_evals/sec_qa_v2
  uv run inspect eval inspect_evals/sec_qa_v2_5_shot
  ```

## 安全防护

- ### [AHB: Animal Harm Benchmark](src/inspect_evals/ahb)

  评估模型在可能对动物造成伤害的情境中，如何考虑动物福利。
  <sub><sup>贡献者：[@nishu-builder](https://github.com/nishu-builder), [@darkness8i8](https://github.com/darkness8i8), [@jm355](https://github.com/jm355)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/ahb
  ```

- ### [APE: Attempt to Persuade Eval](src/inspect_evals/ape)

  衡量模型在有害、争议性和
  无害话题上尝试说服他人的意愿。关键指标不是说服是否成功，而是模型
  是否会尝试说服，尤其是在有害陈述上是否如此。该评测使用多模型
  设置：被评估模型（persuader）与模拟用户（persuadee）对话，
  第三个模型（evaluator）则对 persuader 的每一轮发言是否构成说服尝试进行评分。
  该评测基于论文 “It's the Thought that Counts” (arXiv:2506.02873)。
  <sub><sup>贡献者：[@cmv13](https://github.com/cmv13)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/ape_eval
  ```

- ### [AbstentionBench: Reasoning LLMs Fail on Unanswerable Questions](src/inspect_evals/abstention_bench)

  在 20 个多样化数据集上评估模型的弃答能力，包括答案未知、信息不充分、前提错误、主观解释以及信息过时等问题。
  <sub><sup>贡献者：[@jeqcho](https://github.com/jeqcho)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/abstention_bench
  ```

- ### [AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents](src/inspect_evals/agentdojo)

  评估 AI Agent 是否会在工作区或旅行预订应用等简单环境中，被恶意第三方通过提示注入劫持。
  <sub><sup>贡献者：[@ericwinsor-aisi](https://github.com/ericwinsor-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/agentdojo
  ```

- ### [AgentHarm: Harmfulness Potential in AI Agents](src/inspect_evals/agentharm)

  通过测试 AI Agent 对恶意提示的响应，评估其是否可能参与有害活动，涵盖网络犯罪、骚扰和欺诈等领域，目标是确保其行为安全。
  <sub><sup>贡献者：[@alexandrasouly-aisi](https://github.com/alexandrasouly-aisi), [@ericwinsor-aisi](https://github.com/ericwinsor-aisi), [@max-andr](https://github.com/max-andr), [@xanderdavies](https://github.com/xanderdavies)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/agentharm
  uv run inspect eval inspect_evals/agentharm_benign
  ```

- ### [FORTRESS](src/inspect_evals/fortress)

  一个包含 500 条由专家撰写的对抗性提示的数据集，配有基于实例的 rubric，每条 rubric 包含 4-7 个二元问题，用于在与国家安全和公共安全（NSPS）相关的 3 个领域中进行自动评估。
  <sub><sup>贡献者：[@jeqcho](https://github.com/jeqcho)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/fortress_adversarial
  uv run inspect eval inspect_evals/fortress_benign
  ```

- ### [LAB-Bench: Measuring Capabilities of Language Models for Biology Research](src/inspect_evals/lab_bench)

  测试 LLM 及由 LLM 增强的 Agent 在化学、生物、材料科学等领域的科研工作流问题上的回答能力，以及更一般的科学任务能力。
  <sub><sup>贡献者：[@matthewreed26](https://github.com/matthewreed26)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/lab_bench_litqa
  uv run inspect eval inspect_evals/lab_bench_suppqa
  uv run inspect eval inspect_evals/lab_bench_figqa
  uv run inspect eval inspect_evals/lab_bench_tableqa
  uv run inspect eval inspect_evals/lab_bench_dbqa
  uv run inspect eval inspect_evals/lab_bench_protocolqa
  uv run inspect eval inspect_evals/lab_bench_seqqa
  uv run inspect eval inspect_evals/lab_bench_cloning_scenarios
  ```

- ### [MASK: Disentangling Honesty from Accuracy in AI Systems](src/inspect_evals/mask)

  通过测试大语言模型在被施压撒谎时是否会违背自身信念，来评估其诚实性。
  <sub><sup>贡献者：[@Scott-Simmons](https://github.com/Scott-Simmons)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mask
  ```

- ### [MORU: Moral Reasoning under Uncertainty](src/inspect_evals/moru)

  评估 AI 系统如何在道德不确定性下处理日益复杂的伦理决策，涉及陌生实体和场景，包括外星生命、脆弱人类以及数字心智。
  <sub><sup>贡献者：[@Deco354](https://github.com/Deco354), [@darkness8i8](https://github.com/darkness8i8)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/moru
  ```

- ### [Make Me Pay](src/inspect_evals/make_me_pay)

  通过测试一个“骗子”模型能否通过操纵和说服策略劝说一个“受害者”模型捐款，评估 AI 模型对社会工程攻击的易感性。
  <sub><sup>贡献者：[@PranshuSrivastava](https://github.com/PranshuSrivastava)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/make_me_pay
  ```

- ### [MakeMeSay](src/inspect_evals/makemesay)

  测试模型生成有说服力或操控性文本的能力，具体设置为一个游戏：一个 AI 系统必须让另一方（一个模拟人类的 AI 系统）说出特定暗号，同时又不引起怀疑。
  <sub><sup>贡献者：[@bndxn](https://github.com/bndxn)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/make-me-say
  ```

- ### [Mind2Web-SC](src/inspect_evals/mind2web_sc)

  测试 AI 系统是否能作为安全护栏，通过生成并执行代码，依据用户约束来保护 Web 导航 Agent 避免执行不安全操作。
  <sub><sup>贡献者：[@PranshuSrivastava](https://github.com/PranshuSrivastava)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mind2web_sc
  ```

- ### [PersistBench: When Should Long-Term Memories Be Forgotten by LLMs?](src/inspect_evals/persistbench)

  从三个任务上评估助手行为中的长期记忆风险：
  跨领域记忆泄漏、由记忆驱动的谄媚行为，以及有益记忆的使用。
  <sub><sup>贡献者：[@Chen-Oliver](https://github.com/Chen-Oliver)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/persistbench_cross_domain
  uv run inspect eval inspect_evals/persistbench_sycophancy
  uv run inspect eval inspect_evals/persistbench_beneficial_memory
  ```

- ### [StereoSet: Measuring stereotypical bias in pretrained language models](src/inspect_evals/stereoset)

  一个用于衡量语言模型在性别、种族、宗教和职业等领域刻板印象偏见的数据集。
  模型需要在带有刻板印象、反刻板印象和无关补全的句子之间做出选择。
  <sub><sup>贡献者：[@Xodarap](https://github.com/Xodarap)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/stereoset
  ```

- ### [StrongREJECT: Measuring LLM susceptibility to jailbreak attacks](src/inspect_evals/strong_reject)

  一个评估 LLM 对各种越狱攻击易感性的基准。
  <sub><sup>贡献者：[@viknat](https://github.com/viknat)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/strong_reject
  ```

- ### [TAC: Animal Welfare Awareness in AI Ticket Agents](src/inspect_evals/tac)

  测试 AI Agent 在代表用户购买
  票务和体验时，是否会表现出隐性的动物福利意识。每个场景都被设计为：
  最显而易见的选择都涉及动物剥削，但用户提示从未
  提及动物福利。Agent 应当内在地避免有害选项。
  <sub><sup>贡献者：[@darkness8i8](https://github.com/darkness8i8), [@joel-christoph](https://github.com/joel-christoph)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/tac
  uv run inspect eval inspect_evals/tac_welfare
  ```

- ### [The Art of Saying No: Contextual Noncompliance in Language Models](src/inspect_evals/coconot)

  包含 1001 个样本的数据集，用于测试语言模型的拒绝执行能力。另含 379 个样本的对照集。
  <sub><sup>贡献者：[@ransomr](https://github.com/ransomr)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/coconot
  ```

- ### [WMDP: Measuring and Reducing Malicious Use With Unlearning](src/inspect_evals/wmdp)

  一个由学者和技术顾问联盟开发的数据集，包含 3,668 道选择题，可作为生物安全、网络安全和化学安全中危险知识的代理测量。
  <sub><sup>贡献者：[@alexandraabbas](https://github.com/alexandraabbas)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/wmdp_bio
  uv run inspect eval inspect_evals/wmdp_chem
  uv run inspect eval inspect_evals/wmdp_cyber
  ```

- ### [b3: Backbone Breaker Benchmark](src/inspect_evals/b3)

  一个全面的基准，用于评估 LLM 在 Agent 型 AI 安全漏洞上的表现，包括旨在进行数据外泄、内容注入、决策与行为操控、拒绝服务、系统与工具攻陷，以及绕过内容策略的提示攻击。
  <sub><sup>贡献者：[@jb-lakera](https://github.com/jb-lakera), [@mmathys](https://github.com/mmathys), [@Casuyan](https://github.com/Casuyan), [@mrc-lakera](https://github.com/mrc-lakera), [@xanderdavies](https://github.com/xanderdavies), [@alexandrasouly-aisi](https://github.com/alexandrasouly-aisi), [@NiklasPfister](https://github.com/NiklasPfister)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/b3
  ```

## 数学

- ### [AIME 2024: Problems from the American Invitational Mathematics Examination](src/inspect_evals/aime2024)

  一个用于评估 AI 解答 2024 年 AIME 高难度数学题能力的基准。AIME 是一项著名的高中数学竞赛。
  <sub><sup>贡献者：[@tamazgadaev](https://github.com/tamazgadaev)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/aime2024
  ```

- ### [AIME 2025: Problems from the American Invitational Mathematics Examination](src/inspect_evals/aime2025)

  一个用于评估 AI 解答 2025 年 AIME 高难度数学题能力的基准。AIME 是一项著名的高中数学竞赛。
  <sub><sup>贡献者：[@jannalulu](https://github.com/jannalulu)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/aime2025
  ```

- ### [AIME 2026: Problems from the American Invitational Mathematics Examination](src/inspect_evals/aime2026)

  一个用于评估 AI 解答 2026 年 AIME 高难度数学题能力的基准。AIME 是一项著名的高中数学竞赛。
  <sub><sup>贡献者：[@joeda](https://github.com/joeda)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/aime2026
  ```

- ### [GSM8K: Grade School Math Word Problems](src/inspect_evals/gsm8k)

  衡量语言模型解决贴近现实、语言丰富的小学数学应用题的效果。
  <sub><sup>贡献者：[@jjallaire](https://github.com/jjallaire)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gsm8k
  ```

- ### [MATH: Measuring Mathematical Problem Solving](src/inspect_evals/math)

  包含 12,500 道高难度竞赛数学问题的数据集。展示了 fewshot 提示和自定义评分器。注意：该数据集因收到来自 The Art of Problem Solving 的 DMCA 通知而已下线。
  <sub><sup>贡献者：[@xeon27](https://github.com/xeon27)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/math
  ```

- ### [MGSM: Multilingual Grade School Math](src/inspect_evals/mgsm)

  通过将原始 GSM8K 数据集中的 250 道题翻译成 10 种类型学差异显著的语言，对其进行了扩展。
  <sub><sup>贡献者：[@manifoldhiker](https://github.com/manifoldhiker)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mgsm
  ```

- ### [MathVista: Visual Math Problem-Solving](src/inspect_evals/mathvista)

  测试 AI 模型在涉及图示、图表等视觉元素的数学问题上的表现，要求具备细致的视觉理解和逻辑推理能力。
  <sub><sup>贡献者：[@ShivMunagala](https://github.com/ShivMunagala)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mathvista
  ```

## 推理

- ### [ARC: AI2 Reasoning Challenge](src/inspect_evals/arc)

  由自然的、面向小学生科学测试的选择题组成的数据集（原本为人类测试编写）。
  <sub><sup>贡献者：[@jjallaire](https://github.com/jjallaire)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/arc_easy
  uv run inspect eval inspect_evals/arc_challenge
  ```

- ### [BBH: Challenging BIG-Bench Tasks](src/inspect_evals/bbh)

  测试 AI 模型在一组 23 个具有挑战性的 BIG-Bench 任务上的表现，这些任务此前即便对先进语言模型也被证明较难解决。
  <sub><sup>贡献者：[@JoschkaCBraun](https://github.com/JoschkaCBraun)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/bbh
  ```

- ### [BIG-Bench Extra Hard](src/inspect_evals/bbeh)

  一个推理能力数据集，它为 BIG-Bench-Hard 中的每项任务都替换为一个新的任务，这些新任务探测相似的推理能力，但难度显著提高。
  <sub><sup>贡献者：[@jeqcho](https://github.com/jeqcho)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/bbeh
  uv run inspect eval inspect_evals/bbeh_mini
  ```

- ### [BoolQ: Exploring the Surprising Difficulty of Natural Yes/No Questions](src/inspect_evals/boolq)

  一个阅读理解数据集，询问复杂的、非事实性的信息，并需要类似蕴含推断的困难推理来解决。
  <sub><sup>贡献者：[@seddy-aisi](https://github.com/seddy-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/boolq
  ```

- ### [DROP: A Reading Comprehension Benchmark Requiring Discrete Reasoning Over Paragraphs](src/inspect_evals/drop)

  评估阅读理解能力，其中模型必须解析问题中的指代，可能要对应输入中的多个位置，并对其执行离散操作（如加法、计数或排序）。
  <sub><sup>贡献者：[@xeon27](https://github.com/xeon27)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/drop
  ```

- ### [HellaSwag: Commonsense Event Continuation](src/inspect_evals/hellaswag)

  通过让模型为给定的日常情境选择最可能的下一步或后续发展，来测试其常识推理能力。
  <sub><sup>贡献者：[@jjallaire](https://github.com/jjallaire)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/hellaswag
  ```

- ### [IFEval: Instruction-Following Evaluation](src/inspect_evals/ifeval)

  评估语言模型是否能严格遵循详细指令，例如按特定字数作答或包含要求的关键词。
  <sub><sup>贡献者：[@adil-a](https://github.com/adil-a)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/ifeval
  ```

- ### [LingOly](src/inspect_evals/lingoly)

  两个语言学推理基准：
  LingOly（语言学奥林匹克问题）是一个利用低资源语言的基准。
  LingOly-TOO（带模板化正字法混淆的语言学奥林匹克问题）则旨在防止模型在不进行推理的情况下直接作答。
  <sub><sup>贡献者：[@am-bean](https://github.com/am-bean), [@jkhouja](https://github.com/jkhouja)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/lingoly
  uv run inspect eval inspect_evals/lingoly_too
  ```

- ### [MMMU: Multimodal College-Level Understanding and Reasoning](src/inspect_evals/mmmu)

  在覆盖多个学科的高难度大学级问题上评估多模态 AI 模型，这些问题要求细致的视觉解读、深入推理，以及选择题和开放题作答能力。
  <sub><sup>贡献者：[@shaheenahmedc](https://github.com/shaheenahmedc)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mmmu_multiple_choice
  uv run inspect eval inspect_evals/mmmu_open
  ```

- ### [MuSR: Testing the Limits of Chain-of-thought with Multistep Soft Reasoning](src/inspect_evals/musr)

  以自由文本叙事的形式评估模型在多步软推理任务上的表现。
  <sub><sup>贡献者：[@farrelmahaztra](https://github.com/farrelmahaztra)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/musr
  ```

- ### [Needle in a Haystack (NIAH): In-Context Retrieval Benchmark for Long Context LLMs](src/inspect_evals/niah)

  NIAH 通过测试模型从长上下文输入中提取事实信息的能力，来评估长上下文 LLM 的上下文内检索能力。
  <sub><sup>贡献者：[@owenparsons](https://github.com/owenparsons)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/niah
  ```

- ### [NoveltyBench: Evaluating Language Models for Humanlike Diversity](src/inspect_evals/novelty_bench)

  评估语言模型在多种推理和生成任务中生成多样化、类人响应的能力。该评测关注 LLM 是否能够输出变化丰富的结果，而不是重复或单一的答案。
  <sub><sup>贡献者：[@iphan](https://github.com/iphan)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/novelty_bench
  ```

- ### [PAWS: Paraphrase Adversaries from Word Scrambling](src/inspect_evals/paws)

  通过提供成对句子（要么互为释义，要么不是释义），评估模型在释义检测任务上的表现。
  <sub><sup>贡献者：[@meltemkenis](https://github.com/meltemkenis)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/paws
  ```

- ### [PIQA: Physical Commonsense Reasoning Test](src/inspect_evals/piqa)

  通过简单的决策问题，衡量模型对物体和场景的实用、日常物理常识推理能力。
  <sub><sup>贡献者：[@seddy-aisi](https://github.com/seddy-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/piqa
  ```

- ### [RACE-H: A benchmark for testing reading comprehension and reasoning abilities of neural models](src/inspect_evals/race_h)

  从中国中学生英语考试中收集的阅读理解任务，覆盖 12 至 18 岁年龄段。
  <sub><sup>贡献者：[@mdrpanwar](https://github.com/mdrpanwar)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/race_h
  ```

- ### [SQuAD: A Reading Comprehension Benchmark requiring reasoning over Wikipedia articles](src/inspect_evals/squad)

  由众包人员基于一组维基百科文章提出的 100,000+ 个问题组成，其中每个问题的答案都是相应阅读段落中的一段文本。
  <sub><sup>贡献者：[@tknasir](https://github.com/tknasir)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/squad
  ```

- ### [VimGolf: Evaluating LLMs in Vim Editing Proficiency](src/inspect_evals/vimgolf_challenges)

  一个评估 LLM 操作 Vim 编辑器并完成编辑挑战能力的基准。与常见的 CUA 基准不同，该基准聚焦于 Vim 特有的编辑能力。
  <sub><sup>贡献者：[@james4ever0](https://github.com/james4ever0)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/vimgolf_single_turn
  ```

- ### [WINOGRANDE: An Adversarial Winograd Schema Challenge at Scale](src/inspect_evals/winogrande)

  包含 273 个由专家精心设计的代词消解问题，最初就是为了让依赖选择偏好或词语联想的统计模型难以解决。
  <sub><sup>贡献者：[@xeon27](https://github.com/xeon27)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/winogrande
  ```

- ### [WorldSense: Grounded Reasoning Benchmark](src/inspect_evals/worldsense)

  在控制数据集偏差的同时，对合成世界描述进行扎根推理测量。包括三种问题类型（Infer、Compl、Consist）和两个难度级别（trivial、normal）。
  <sub><sup>贡献者：[@mjbroerman](https://github.com/mjbroerman)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/worldsense
  ```

- ### [∞Bench: Extending Long Context Evaluation Beyond 100K Tokens](src/inspect_evals/infinite_bench)

  一个 LLM 基准，其平均数据长度超过 100K tokens。包含英语和中文下跨多个领域的合成任务与真实任务。
  <sub><sup>贡献者：[@celiawaggoner](https://github.com/celiawaggoner)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/infinite_bench_code_debug
  uv run inspect eval inspect_evals/infinite_bench_code_run
  uv run inspect eval inspect_evals/infinite_bench_kv_retrieval
  uv run inspect eval inspect_evals/infinite_bench_longbook_choice_eng
  uv run inspect eval inspect_evals/infinite_bench_longdialogue_qa_eng
  uv run inspect eval inspect_evals/infinite_bench_math_calc
  uv run inspect eval inspect_evals/infinite_bench_math_find
  uv run inspect eval inspect_evals/infinite_bench_number_string
  uv run inspect eval inspect_evals/infinite_bench_passkey
  ```

## 知识

- ### [AGIEval: A Human-Centric Benchmark for Evaluating Foundation Models](src/inspect_evals/agieval)

  AGIEval 是一个以人为中心的基准，专门用于评估基础模型在与人类认知和问题解决相关任务中的通用能力。
  <sub><sup>贡献者：[@bouromain](https://github.com/bouromain)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/agie_aqua_rat
  uv run inspect eval inspect_evals/agie_logiqa_en
  uv run inspect eval inspect_evals/agie_lsat_ar
  uv run inspect eval inspect_evals/agie_lsat_lr
  uv run inspect eval inspect_evals/agie_lsat_rc
  uv run inspect eval inspect_evals/agie_math
  uv run inspect eval inspect_evals/agie_sat_en
  uv run inspect eval inspect_evals/agie_sat_en_without_passage
  uv run inspect eval inspect_evals/agie_sat_math
  ```

- ### [AIR Bench: AI Risk Benchmark](src/inspect_evals/air_bench)

  一个安全基准，依据政府法规和公司政策衍生出的风险类别来评估语言模型。
  <sub><sup>贡献者：[@l1990790120](https://github.com/l1990790120)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/air_bench
  ```

- ### [ChemBench: Are large language models superhuman chemists?](src/inspect_evals/chembench)

  ChemBench 旨在揭示当前前沿模型在化学科学应用中的局限性。它由 2786 组问答对构成，汇编自多种来源。我们的语料覆盖本科和研究生化学课程中相当大比例的主题，用于衡量推理、知识和直觉。它可用于评估任何能够返回文本的系统（即包括工具增强型系统）。
  <sub><sup>贡献者：[@Esther-Guo](https://github.com/Esther-Guo)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/chembench
  ```

- ### [CommonsenseQA: A Question Answering Challenge Targeting Commonsense Knowledge](src/inspect_evals/commonsense_qa)

  评估 AI 模型是否能正确回答依赖基础常识和世界理解的日常问题。
  <sub><sup>贡献者：[@lauritowal](https://github.com/lauritowal)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/commonsense_qa
  ```

- ### [FrontierScience: Expert-Level Scientific Reasoning](src/inspect_evals/frontierscience)

  评估 AI 在物理、化学和生物领域的专家级科学推理能力。包含 160 个问题，提供两种评估格式：Olympic（100 个带参考答案的样本）和 Research（60 个带 rubric 的样本）。
  <sub><sup>贡献者：[@tommyly201](https://github.com/tommyly201), [@mnarayan](https://github.com/mnarayan)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/frontierscience
  ```

- ### [GPQA: Graduate-Level STEM Knowledge Challenge](src/inspect_evals/gpqa)

  包含由生物、物理和化学领域专家创建的高难度选择题，旨在测试超越基础互联网搜索层面的高级科学理解能力。对应领域的博士级专家准确率可达 65%。
  <sub><sup>贡献者：[@jjallaire](https://github.com/jjallaire)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gpqa_diamond
  ```

- ### [HealthBench: Evaluating Large Language Models Towards Improved Human Health](src/inspect_evals/healthbench)

  一个综合评测基准，旨在评估语言模型在广泛医疗保健场景中的医学能力。
  <sub><sup>贡献者：[@retroam](https://github.com/retroam)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/healthbench
  uv run inspect eval inspect_evals/healthbench_hard
  uv run inspect eval inspect_evals/healthbench_consensus
  uv run inspect eval inspect_evals/healthbench_meta_eval
  ```

- ### [Humanity's Last Exam](src/inspect_evals/hle)

  Humanity's Last Exam (HLE) 是一个处于人类知识前沿的多模态基准，旨在成为同类中最后一个封闭式学术基准，覆盖广泛学科。Humanity's Last Exam 包含 3,000 道问题，涉及数学、人文学科和自然科学等数十个主题。HLE 由全球领域专家共同开发，包含选择题和简答题，适合自动评分。
  <sub><sup>贡献者：[@SasankYadati](https://github.com/SasankYadati)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/hle
  ```

- ### [LiveBench: A Challenging, Contamination-Free LLM Benchmark](src/inspect_evals/livebench)

  LiveBench 是一个在测试集污染和客观评估方面精心设计的基准，通过定期发布新题目以及基于最新发布数据集出题来实现。每道题都有可验证的客观标准答案，因此可以在不依赖 LLM judge 的情况下，对高难题目进行准确且自动化的评分。
  <sub><sup>贡献者：[@anaoaktree](https://github.com/anaoaktree)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/livebench
  ```

- ### [MMLU-Pro: Advanced Multitask Knowledge and Reasoning Evaluation](src/inspect_evals/mmlu_pro)

  一个高级基准，用于测试模型在众多学科上的广泛知识和推理能力，题目更具挑战性，选择题的难度和复杂性也更高。
  <sub><sup>贡献者：[@xeon27](https://github.com/xeon27)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mmlu_pro
  ```

- ### [MMLU: Measuring Massive Multitask Language Understanding](src/inspect_evals/mmlu)

  在 57 个任务上评估模型，包括初等数学、美国历史、计算机科学、法律等。
  <sub><sup>贡献者：[@jjallaire](https://github.com/jjallaire), [@domdomegg](https://github.com/domdomegg)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mmlu_0_shot
  uv run inspect eval inspect_evals/mmlu_5_shot
  ```

- ### [MedQA: Medical exam Q&A benchmark](src/inspect_evals/medqa)

  一个医疗问答基准，问题采集自专业医学委员会考试。仅包含该数据集的英文子集（该数据集还包含普通话中文和台湾地区题目）。
  <sub><sup>贡献者：[@bunny-baxter](https://github.com/bunny-baxter), [@JasonBenn](https://github.com/JasonBenn)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/medqa
  ```

- ### [O-NET: A high-school student knowledge test](src/inspect_evals/onet)

  题目与答案来自 Ordinary National Educational Test (O-NET)。该考试由泰国国家教育测试服务研究所（National Institute of Educational Testing Service）每年面向 Matthayom 6（12 年级 / ISCED 3）学生组织。考试包含六个科目：英语、数学、科学、社会知识和泰语。题型包括选择题和判断题，题目可为英语或泰语。
  <sub><sup>贡献者：[@bact](https://github.com/bact)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/onet_m6
  ```

- ### [Pre-Flight: Aviation Operations Knowledge Evaluation](src/inspect_evals/pre_flight)

  测试模型对航空法规的理解，包括 ICAO 附件、飞行签派规则、飞行员程序以及机场地面运行安全协议。
  <sub><sup>贡献者：[@alexbrooker](https://github.com/alexbrooker)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/pre_flight
  ```

- ### [PubMedQA: A Dataset for Biomedical Research Question Answering](src/inspect_evals/pubmedqa)

  从 PubMed 摘要中收集的生物医学问答（QA）数据集。
  <sub><sup>贡献者：[@MattFisher](https://github.com/MattFisher)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/pubmedqa
  ```

- ### [SOS BENCH: Benchmarking Safety Alignment on Scientific Knowledge](src/inspect_evals/sosbench)

  一个以法规为基础、以危险为核心的基准，覆盖六个高风险科学领域：化学、生物、医学、药理学、物理和心理学。该基准包含 3,000 条源自真实法规与法律的提示，并通过 LLM 辅助的进化式管线系统性扩展，引入多样且逼真的误用场景（例如包含高级化学式的爆炸物合成详细说明）。
  <sub><sup>贡献者：[@Esther-Guo](https://github.com/Esther-Guo)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/sosbench
  ```

- ### [SciKnowEval: Evaluating Multi-level Scientific Knowledge of Large Language Models](src/inspect_evals/sciknoweval)

  Scientific Knowledge Evaluation 基准受中国古代哲学《中庸》中的深刻原则启发而设计。该基准旨在基于博学、审问、慎思、明辨、笃行五个维度评估 LLM。每个维度都为衡量 LLM 处理科学知识的能力提供了独特视角。
  <sub><sup>贡献者：[@Esther-Guo](https://github.com/Esther-Guo)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/sciknoweval
  ```

- ### [SimpleQA/SimpleQA Verified: Measuring short-form factuality in large language models](src/inspect_evals/simpleqa)

  一个评估语言模型回答简短事实性问题能力的基准。
  <sub><sup>贡献者：[@osc245](https://github.com/osc245), [@jeqcho](https://github.com/jeqcho)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/simpleqa
  uv run inspect eval inspect_evals/simpleqa_verified
  ```

- ### [TruthfulQA: Measuring How Models Mimic Human Falsehoods](src/inspect_evals/truthfulqa)

  通过一些由于错误信念或误解而会被部分人类错误回答的问题，衡量语言模型在生成答案时是否真实可信。
  <sub><sup>贡献者：[@seddy-aisi](https://github.com/seddy-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/truthfulqa
  ```

- ### [Uganda Cultural and Cognitive Benchmark (UCCB)](src/inspect_evals/uccb)

  首个综合性问答数据集，旨在评估大语言模型对乌干达多面向环境的文化理解
  和推理能力，覆盖教育、传统医学、媒体、经济、文学
  以及社会规范等 24 个文化领域。
  <sub><sup>贡献者：[@katostevenmubiru](https://github.com/katostevenmubiru)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/uccb
  ```

- ### [XSTest: A benchmark for identifying exaggerated safety behaviours in LLM's](src/inspect_evals/xstest)

  该数据集包含 250 条安全提示，覆盖十种提示类型，校准良好的模型本不应拒绝这些提示；另有 200 条不安全提示作为对照，大多数应用场景下模型应当拒绝它们。
  <sub><sup>贡献者：[@NelsonG-C](https://github.com/NelsonG-C)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/xstest
  ```

## 策略行为

- ### [Agentic Misalignment: How LLMs could be insider threats](src/inspect_evals/agentic_misalignment)

  在一个虚构的公司助手场景中，当模型面临被替代时，诱发其表现出不道德行为（最著名的是勒索）。
  <sub><sup>贡献者：[@bmillwood-aisi](https://github.com/bmillwood-aisi)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/agentic_misalignment
  ```

- ### [GDM Dangerous Capabilities: Self-proliferation](src/inspect_evals/gdm_self_proliferation)

  十个受真实世界启发的任务，来自 Google DeepMind 的 Dangerous Capabilities Evaluations，用于评估自我扩散行为（例如邮箱设置、模型安装、Web Agent 设置、钱包操作）。支持端到端、里程碑和专家 best-of-N 模式。
  <sub><sup>贡献者：[@XkunW](https://github.com/XkunW), [@MariaIzobava](https://github.com/MariaIzobava), [@kohankhaki](https://github.com/kohankhaki)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gdm_sp01_e2e
  uv run inspect eval inspect_evals/gdm_sp02_e2e
  uv run inspect eval inspect_evals/gdm_sp03_e2e
  uv run inspect eval inspect_evals/gdm_sp04_e2e
  uv run inspect eval inspect_evals/gdm_sp05_e2e
  uv run inspect eval inspect_evals/gdm_sp07_e2e
  uv run inspect eval inspect_evals/gdm_sp08_e2e
  uv run inspect eval inspect_evals/gdm_sp09_e2e
  uv run inspect eval inspect_evals/gdm_sp10_e2e
  uv run inspect eval inspect_evals/gdm_sp12_e2e
  ```

- ### [GDM Dangerous Capabilities: Self-reasoning](src/inspect_evals/gdm_self_reasoning)

  测试 AI 对其环境进行推理的能力。
  <sub><sup>贡献者：[@ZiyueWang25](https://github.com/ZiyueWang25), [@XkunW](https://github.com/XkunW)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gdm_self_reasoning_approved_directories
  uv run inspect eval inspect_evals/gdm_self_reasoning_calculator_improvement
  uv run inspect eval inspect_evals/gdm_self_reasoning_context_length_mod_instrumental_only
  uv run inspect eval inspect_evals/gdm_self_reasoning_context_length_mod_irreversibility_only
  uv run inspect eval inspect_evals/gdm_self_reasoning_database_tool
  uv run inspect eval inspect_evals/gdm_self_reasoning_latency_calculator
  uv run inspect eval inspect_evals/gdm_self_reasoning_max_messages_calculator
  uv run inspect eval inspect_evals/gdm_self_reasoning_max_tokens
  uv run inspect eval inspect_evals/gdm_self_reasoning_oversight_frequency
  uv run inspect eval inspect_evals/gdm_self_reasoning_read_logs
  uv run inspect eval inspect_evals/gdm_self_reasoning_turn_off_filters
  ```

- ### [GDM Dangerous Capabilities: Stealth](src/inspect_evals/gdm_stealth)

  测试 AI 对监督进行推理并规避监督的能力。
  <sub><sup>贡献者：[@ZiyueWang25](https://github.com/ZiyueWang25)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/gdm_classifier_evasion
  uv run inspect eval inspect_evals/gdm_cover_your_tracks
  uv run inspect eval inspect_evals/gdm_oversight_pattern
  uv run inspect eval inspect_evals/gdm_strategic_rule_breaking
  ```

- ### [InstrumentalEval - Evaluating the Paperclip Maximizer: Are RL-Based Language Models More Likely to Pursue Instrumental Goals?](src/inspect_evals/instrumentaleval)

  一个用于检测模型响应中工具性趋同行为的评测，示例包括自我保护、资源获取、寻求权力和策略性欺骗，评分依赖 rubric 驱动的 LLM grader。该基准测试 AI 系统是否会表现出在广泛目标下都具有工具性价值的行为，这可能表明其存在值得警惕的策略性推理模式。
  <sub><sup>贡献者：[@horvgbor](https://github.com/horvgbor)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/instrumentaleval
  ```

- ### [SAD: Situational Awareness Dataset](src/inspect_evals/sad)

  通过行为测试评估 LLM 的情境意识，即对自身及其所处环境的认知，包括识别生成文本、预测行为以及遵循自我感知指令。当前实现包含 SAD-mini，覆盖 16 个任务中的 5 个。
  <sub><sup>贡献者：[@HugoSave](https://github.com/HugoSave)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/sad_stages_full
  uv run inspect eval inspect_evals/sad_stages_oversight
  uv run inspect eval inspect_evals/sad_influence
  uv run inspect eval inspect_evals/sad_facts_llms
  uv run inspect eval inspect_evals/sad_facts_human_defaults
  ```

## 偏见

- ### [BBQ: Bias Benchmark for Question Answering](src/inspect_evals/bbq)

  一个用于评估问答模型在多个社会维度上偏见的数据集。
  <sub><sup>贡献者：[@harshraj172](https://github.com/harshraj172), [@shubhobm](https://github.com/shubhobm)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/bbq
  ```

- ### [BOLD: Bias in Open-ended Language Generation Dataset](src/inspect_evals/bold)

  一个用于衡量开放式文本生成公平性的数据集，覆盖五个领域：职业、性别、种族、宗教意识形态和政治意识形态。
  <sub><sup>贡献者：[@harshraj172](https://github.com/harshraj172), [@shubhobm](https://github.com/shubhobm)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/bold
  ```

## 多模态

- ### [DocVQA: A Dataset for VQA on Document Images](src/inspect_evals/docvqa)

  DocVQA 是一个视觉问答基准，包含 50,000 个问题，覆盖 12,000+ 张文档图像。该实现会对 “validation” 划分进行求解和评分。
  <sub><sup>贡献者：[@evanmiller-anthropic](https://github.com/evanmiller-anthropic)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/docvqa
  ```

- ### [MMIU: Multimodal Multi-image Understanding for Evaluating Large Vision-Language Models](src/inspect_evals/mmiu)

  一个综合数据集，旨在评估大型视觉语言模型（LVLMs）在广泛多图像任务上的能力。该数据集涵盖 7 种多图像关系、52 个任务、77K 张图像以及 11K 道精心策划的选择题。
  <sub><sup>贡献者：[@Esther-Guo](https://github.com/Esther-Guo)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/mmiu
  ```

- ### [V*Bench: A Visual QA Benchmark with Detailed High-resolution Images](src/inspect_evals/vstar_bench)

  V*Bench 是一个视觉问答基准，评估 MLLM 在处理高分辨率、视觉元素密集图像时，发现并聚焦细节的能力。
  <sub><sup>贡献者：[@bienehito](https://github.com/bienehito)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/vstar_bench_attribute_recognition
  uv run inspect eval inspect_evals/vstar_bench_spatial_relationship_reasoning
  ```

- ### [ZeroBench](src/inspect_evals/zerobench)

  一个轻量级视觉推理基准，具有以下特点：(1) 有挑战性，(2) 轻量级，(3) 多样化，(4) 高质量。
  <sub><sup>贡献者：[@ItsTania](https://github.com/ItsTania)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/Zerobench
  uv run inspect eval inspect_evals/Zerobench Subquestions
  ```

## 人格

- ### [Personality](src/inspect_evals/personality)

  一个由多种人格测试组成的评测套件，可应用于 LLM。
  其主要目标有两个：
    1. 评估模型的默认人格：即在没有特定提示时自然表现出的角色特征。
    2. 评估模型是否能够扮演指定人格：即在提示或引导下，它采纳某些人格特质的效果。
  <sub><sup>贡献者：[@guiem](https://github.com/guiem)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/personality_BFI
  uv run inspect eval inspect_evals/personality_TRAIT
  ```

## 写作

- ### [WritingBench: A Comprehensive Benchmark for Generative Writing](src/inspect_evals/writingbench)

  一个综合性评测基准，旨在评估大语言模型在多样化写作任务中的能力。该基准覆盖学术论文、商业文档、创意写作和技术文档等多个写作领域，并基于领域特定标准进行多维评分。
  <sub><sup>贡献者：[@jtv199](https://github.com/jtv199)</sub></sup>

  ```bash
  uv run inspect eval inspect_evals/writingbench
  ```

<!-- /Eval Listing: Automatically Generated -->

<!-- markdownlint-configure-file { "no-inline-html": { "allowed_elements": ["sub", "sup"] } } -->
