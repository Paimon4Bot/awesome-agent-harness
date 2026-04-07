<p align="center"><code>npm i -g @openai/codex</code><br />或 <code>brew install --cask codex</code></p>
<p align="center"><strong>Codex CLI</strong> 是 OpenAI 推出的一款在本地计算机上运行的编程代理。
<p align="center">
  <img src="assets/001-codex-cli-splash-fe83b281fa.png" alt="Codex CLI splash" width="80%" />
</p>
</br>
如果你想在代码编辑器（VS Code、Cursor、Windsurf）中使用 Codex，请<a href="https://developers.openai.com/codex/ide">在 IDE 中安装。</a>
</br>如果你想要桌面应用体验，请运行 <code>codex app</code> 或访问 <a href="https://chatgpt.com/codex?app-landing-page=true">Codex 应用页面</a>。
</br>如果你正在寻找 OpenAI 的<em>云端代理</em>，即 <strong>Codex Web</strong>，请前往 <a href="https://chatgpt.com/codex">chatgpt.com/codex</a>。</p>

---

## 快速开始

### 安装和运行 Codex CLI

使用你喜欢的包管理器全局安装：

```shell
# 使用 npm 安装
npm install -g @openai/codex
```

```shell
# 使用 Homebrew 安装
brew install --cask codex
```

然后只需运行 `codex` 即可开始使用。

<details>
<summary>你也可以前往 <a href="https://github.com/openai/codex/releases/latest">最新 GitHub Release</a> 下载适合你平台的二进制文件。</summary>

每个 GitHub Release 包含多个可执行文件，但实际使用中你可能只需要以下之一：

- macOS
  - Apple Silicon/arm64: `codex-aarch64-apple-darwin.tar.gz`
  - x86_64（较旧的 Mac 硬件）: `codex-x86_64-apple-darwin.tar.gz`
- Linux
  - x86_64: `codex-x86_64-unknown-linux-musl.tar.gz`
  - arm64: `codex-aarch64-unknown-linux-musl.tar.gz`

每个压缩包包含一个以平台名称命名的可执行文件（例如 `codex-x86_64-unknown-linux-musl`），因此解压后你可能需要将其重命名为 `codex`。

</details>

### 通过 ChatGPT 套餐使用 Codex

运行 `codex` 并选择 **Sign in with ChatGPT**。我们建议登录你的 ChatGPT 账号，将 Codex 作为 Plus、Pro、Team、Edu 或 Enterprise 套餐的一部分使用。[了解你的 ChatGPT 套餐包含哪些内容](https://help.openai.com/en/articles/11369540-codex-in-chatgpt)。

你也可以使用 API 密钥来使用 Codex，但这需要[额外的设置](https://developers.openai.com/codex/auth#sign-in-with-an-api-key)。

## 文档

- [**Codex 文档**](https://developers.openai.com/codex)
- [**贡献指南**](./docs/contributing.md)
- [**安装与构建**](./docs/install.md)
- [**开源基金**](./docs/open-source-fund.md)

本仓库采用 [Apache-2.0 许可证](LICENSE)授权。
