<p align="center">
  <a href="https://opencode.ai">
    <picture>
      <source srcset="assets/003-logo-ornate-dark-fed162acff.svg" media="(prefers-color-scheme: dark)">
      <source srcset="assets/002-logo-ornate-light-0ee5f497d4.svg" media="(prefers-color-scheme: light)">
      <img src="assets/002-logo-ornate-light-0ee5f497d4.svg" alt="OpenCode logo">
    </picture>
  </a>
</p>
<p align="center">开源 AI 编程代理。</p>
<p align="center">
  <a href="https://opencode.ai/discord"><img alt="Discord" src="https://img.shields.io/discord/1391832426048651334?style=flat-square&label=discord" /></a>
  <a href="https://www.npmjs.com/package/opencode-ai"><img alt="npm" src="https://img.shields.io/npm/v/opencode-ai?style=flat-square" /></a>
  <a href="https://github.com/anomalyco/opencode/actions/workflows/publish.yml"><img alt="Build status" src="https://img.shields.io/github/actions/workflow/status/anomalyco/opencode/publish.yml?style=flat-square&branch=dev" /></a>
</p>

<p align="center">
  <a href="README.md">English</a> |
  <a href="README.zh.md">简体中文</a> |
  <a href="README.zht.md">繁體中文</a> |
  <a href="README.ko.md">한국어</a> |
  <a href="README.de.md">Deutsch</a> |
  <a href="README.es.md">Español</a> |
  <a href="README.fr.md">Français</a> |
  <a href="README.it.md">Italiano</a> |
  <a href="README.da.md">Dansk</a> |
  <a href="README.ja.md">日本語</a> |
  <a href="README.pl.md">Polski</a> |
  <a href="README.ru.md">Русский</a> |
  <a href="README.bs.md">Bosanski</a> |
  <a href="README.ar.md">العربية</a> |
  <a href="README.no.md">Norsk</a> |
  <a href="README.br.md">Português (Brasil)</a> |
  <a href="README.th.md">ไทย</a> |
  <a href="README.tr.md">Türkçe</a> |
  <a href="README.uk.md">Українська</a> |
  <a href="README.bn.md">বাংলা</a> |
  <a href="README.gr.md">Ελληνικά</a> |
  <a href="README.vi.md">Tiếng Việt</a>
</p>

[![OpenCode Terminal UI](assets/001-opencode-terminal-ui-5de79fd10f.png)](https://opencode.ai)

---

### 安装

```bash
# YOLO
curl -fsSL https://opencode.ai/install | bash

# 包管理器
npm i -g opencode-ai@latest        # 或 bun/pnpm/yarn
scoop install opencode             # Windows
choco install opencode             # Windows
brew install anomalyco/tap/opencode # macOS 和 Linux（推荐，始终保持最新）
brew install opencode              # macOS 和 Linux（官方 brew formula，更新频率较低）
sudo pacman -S opencode            # Arch Linux（稳定版）
paru -S opencode-bin               # Arch Linux（AUR 最新版）
mise use -g opencode               # 任意操作系统
nix run nixpkgs#opencode           # 或 github:anomalyco/opencode 获取最新开发分支
```

> [!TIP]
> 安装前请先移除 0.1.x 及更早的版本。

### 桌面应用 (BETA)

OpenCode 也提供桌面应用程序。可直接从 [发布页面](https://github.com/anomalyco/opencode/releases) 或 [opencode.ai/download](https://opencode.ai/download) 下载。

| 平台                  | 下载文件                                |
| --------------------- | --------------------------------------- |
| macOS (Apple Silicon) | `opencode-desktop-darwin-aarch64.dmg`   |
| macOS (Intel)         | `opencode-desktop-darwin-x64.dmg`       |
| Windows               | `opencode-desktop-windows-x64.exe`      |
| Linux                 | `.deb`、`.rpm` 或 AppImage              |

```bash
# macOS (Homebrew)
brew install --cask opencode-desktop
# Windows (Scoop)
scoop bucket add extras; scoop install extras/opencode-desktop
```

#### 安装目录

安装脚本按以下优先级顺序确定安装路径：

1. `$OPENCODE_INSTALL_DIR` - 自定义安装目录
2. `$XDG_BIN_DIR` - 符合 XDG 基础目录规范的路径
3. `$HOME/bin` - 标准用户二进制目录（如果已存在或可创建）
4. `$HOME/.opencode/bin` - 默认回退路径

```bash
# 示例
OPENCODE_INSTALL_DIR=/usr/local/bin curl -fsSL https://opencode.ai/install | bash
XDG_BIN_DIR=$HOME/.local/bin curl -fsSL https://opencode.ai/install | bash
```

### 代理

OpenCode 内置两个代理，可通过 `Tab` 键切换。

- **build** - 默认代理，拥有完整权限，用于开发工作
- **plan** - 只读代理，用于分析和代码探索
  - 默认拒绝文件编辑
  - 执行 bash 命令前会请求许可
  - 非常适合探索不熟悉的代码库或规划改动

此外还包含一个 **general** 子代理，用于复杂搜索和多步骤任务。
它在内部使用，可通过在消息中使用 `@general` 来调用。

了解更多关于[代理](https://opencode.ai/docs/agents)的信息。

### 文档

了解更多关于 OpenCode 配置的信息，请参阅[**我们的文档**](https://opencode.ai/docs)。

### 贡献

如果你有兴趣为 OpenCode 做贡献，请在提交 pull request 前阅读我们的[贡献文档](./CONTRIBUTING.md)。

### 基于 OpenCode 构建

如果你正在开发与 OpenCode 相关的项目，并在项目名称中使用了 "opencode"（例如 "opencode-dashboard" 或 "opencode-mobile"），请在 README 中注明该项目并非由 OpenCode 团队构建，与我们没有任何关联。

### 常见问题

#### 它和 Claude Code 有什么区别？

在功能方面与 Claude Code 非常相似。以下是主要区别：

- 100% 开源
- 不绑定任何提供商。虽然我们推荐通过 [OpenCode Zen](https://opencode.ai/zen) 提供的模型，但 OpenCode 可以与 Claude、OpenAI、Google 甚至本地模型配合使用。随着模型的不断进化，它们之间的差距将逐渐缩小、价格也会下降，因此保持提供商无关性非常重要。
- 开箱即用的 LSP 支持
- 专注于 TUI。OpenCode 由 neovim 用户和 [terminal.shop](https://terminal.shop) 的创建者构建；我们将不断突破终端中的可能性边界。
- 客户端/服务器架构。例如，这允许 OpenCode 运行在你的电脑上，同时你可以从移动应用远程操控它，这意味着 TUI 前端只是众多可能的客户端之一。

---

**加入我们的社区** [Discord](https://discord.gg/opencode) | [X.com](https://x.com/opencode)
