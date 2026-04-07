# Harbor

 [![](assets/001-6xwpkhgdba-59682561fb.svg)](https://discord.gg/6xWPKhGDbA)
[![Docs](https://img.shields.io/badge/Docs-000000?style=for-the-badge&logo=mdbook&color=105864)](https://harborframework.com/docs)
[![Cookbook](https://img.shields.io/badge/Cookbook-000000?style=for-the-badge&logo=mdbook&color=105864)](https://github.com/harbor-framework/harbor-cookbook)

Harbor 是由 [Terminal-Bench](https://www.tbench.ai) 创建者开发的框架，用于评估和优化代理及语言模型。你可以使用 Harbor 来：

- 评估任意代理，如 Claude Code、OpenHands、Codex CLI 等。
- 构建和分享你自己的基准测试和环境。
- 通过 Daytona、Modal 等提供商在数千个环境中并行执行实验。
- 生成用于强化学习优化的 rollout 数据。

查看 [Harbor Cookbook](https://github.com/harbor-framework/harbor-cookbook) 获取端到端的示例和指南。

## 安装

```bash tab="uv"
uv tool install harbor
```
或
```bash tab="pip"
pip install harbor
```

## 示例：运行 Terminal-Bench-2.0
Harbor 是 [Terminal-Bench-2.0](https://github.com/laude-institute/terminal-bench-2) 的官方 harness：

```bash
export ANTHROPIC_API_KEY=<YOUR-KEY>
harbor run --dataset terminal-bench@2.0 \
   --agent claude-code \
   --model anthropic/claude-opus-4-1 \
   --n-concurrent 4
```

这将在本地使用 Docker 启动基准测试。要在云提供商（如 Daytona）上运行，请传入 `--env` 标志：

```bash

export ANTHROPIC_API_KEY=<YOUR-KEY>
export DAYTONA_API_KEY=<YOUR-KEY>
harbor run --dataset terminal-bench@2.0 \
   --agent claude-code \
   --model anthropic/claude-opus-4-1 \
   --n-concurrent 100 \
   --env daytona
```

要查看所有支持的代理和其他选项，请运行：

```bash
harbor run --help
```

要浏览所有支持的第三方基准测试（如 SWE-Bench 和 Aider Polyglot），请运行：

```bash
harbor datasets list
```

要评估某个代理和模型在某个数据集上的表现，你可以使用以下命令：

```bash
harbor run -d "<dataset@version>" -m "<model>" -a "<agent>"
```

## 引用

如果你在学术工作中使用 **Harbor**，请使用 GitHub 上的"Cite this repository"按钮或以下 BibTeX 条目进行引用：

```bibtex
@software{Harbor_Framework,
author = {{Harbor Framework Team}},
month = jan,
title = {{Harbor: A framework for evaluating and optimizing agents and models in container environments}},
url = {https://github.com/harbor-framework/harbor},
year = {2026}
}
```
