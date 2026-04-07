# Promptfoo: LLM 评估与红队测试

<p align="center">
  <a href="https://npmjs.com/package/promptfoo"><img src="https://img.shields.io/npm/v/promptfoo" alt="npm"></a>
  <a href="https://npmjs.com/package/promptfoo"><img src="https://img.shields.io/npm/dm/promptfoo" alt="npm"></a>
  <a href="https://github.com/promptfoo/promptfoo/actions/workflows/main.yml"><img src="https://img.shields.io/github/actions/workflow/status/promptfoo/promptfoo/main.yml" alt="GitHub Workflow Status"></a>
  <a href="https://github.com/promptfoo/promptfoo/blob/main/LICENSE"><img src="https://img.shields.io/github/license/promptfoo/promptfoo" alt="MIT license"></a>
  <a href="https://discord.gg/promptfoo"><img src="https://img.shields.io/discord/1146610656779440188?logo=discord&label=promptfoo" alt="Discord"></a>
</p>

<p align="center">
  <code>promptfoo</code> 是一个用于评估和红队测试 LLM 应用的 CLI 和库。告别反复试错，开始交付安全、可靠的 AI 应用。
</p>

<p align="center">
  <a href="https://www.promptfoo.dev">官网</a> ·
  <a href="https://www.promptfoo.dev/docs/getting-started/">快速入门</a> ·
  <a href="https://www.promptfoo.dev/docs/red-team/">红队测试</a> ·
  <a href="https://www.promptfoo.dev/docs/">文档</a> ·
  <a href="https://discord.gg/promptfoo">Discord</a>
</p>

> Promptfoo 现已成为 OpenAI 的一部分。Promptfoo 仍保持开源并采用 MIT 许可证。请阅读 [公司公告](https://www.promptfoo.dev/blog/promptfoo-joining-openai/)。

## 快速开始

```sh
npm install -g promptfoo
promptfoo init --example getting-started
```

也可以通过 `brew install promptfoo` 和 `pip install promptfoo` 安装。你还可以使用 `npx promptfoo@latest` 直接运行任何命令，无需安装。

大多数 LLM 提供商需要 API 密钥。将你的密钥设置为环境变量：

```sh
export OPENAI_API_KEY=sk-abc123
```

进入示例目录后，运行评估并查看结果：

```sh
cd getting-started
promptfoo eval
promptfoo view
```

详见[快速入门](https://www.promptfoo.dev/docs/getting-started/)（评估）或[红队测试](https://www.promptfoo.dev/docs/red-team/)（漏洞扫描）。

## Promptfoo 能做什么？

- **测试提示词和模型**：使用[自动化评估](https://www.promptfoo.dev/docs/getting-started/)
- **保护 LLM 应用安全**：通过[红队测试](https://www.promptfoo.dev/docs/red-team/)和漏洞扫描
- **并排比较模型**：支持 OpenAI、Anthropic、Azure、Bedrock、Ollama 及[更多](https://www.promptfoo.dev/docs/providers/)
- **在 [CI/CD](https://www.promptfoo.dev/docs/integrations/ci-cd/) 中自动化检查**
- **审查拉取请求**：通过[代码扫描](https://www.promptfoo.dev/docs/code-scanning/)检测 LLM 相关的安全与合规问题
- **与团队分享**结果

以下是实际使用效果：

<img src="assets/001-claude-vs-gpt-example-2x-06074a5e01.png" alt="prompt evaluation matrix - web viewer" width="700">

命令行同样可用：

<img src="assets/002-self-grading-7803e57b14.gif" alt="promptfoo command line" width="700">

还可以生成[安全漏洞报告](https://www.promptfoo.dev/docs/red-team/)：

<img src="assets/003-redteam-dashboard-2x-e389b55d49.jpg" alt="gen ai red team" width="700">

## 为什么选择 Promptfoo？

- **开发者优先**：快速高效，支持热重载和缓存等功能
- **隐私安全**：LLM 评估 100% 在本地运行——你的提示词永远不会离开你的机器
- **灵活适配**：支持任何 LLM API 或编程语言
- **久经考验**：已为生产环境中服务 1000 万+ 用户的 LLM 应用提供支持
- **数据驱动**：基于指标做决策，而非凭感觉
- **开源**：采用 MIT 许可证，拥有活跃的社区

## 了解更多

- [快速入门](https://www.promptfoo.dev/docs/getting-started/)
- [完整文档](https://www.promptfoo.dev/docs/intro/)
- [红队测试指南](https://www.promptfoo.dev/docs/red-team/)
- [CLI 使用](https://www.promptfoo.dev/docs/usage/command-line/)
- [Node.js 包](https://www.promptfoo.dev/docs/usage/node-package/)
- [支持的模型](https://www.promptfoo.dev/docs/providers/)
- [代码扫描指南](https://www.promptfoo.dev/docs/code-scanning/)

## 贡献

欢迎贡献代码！请查看我们的[贡献指南](https://www.promptfoo.dev/docs/contributing/)开始参与。

加入我们的 [Discord 社区](https://discord.gg/promptfoo) 获取帮助并参与讨论。

<a href="https://github.com/promptfoo/promptfoo/graphs/contributors">
  <img src="assets/004-image-dbaba6c803.svg" />
</a>
