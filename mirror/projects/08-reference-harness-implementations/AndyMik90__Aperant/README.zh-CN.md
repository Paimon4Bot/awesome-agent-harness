# Aperant（原名 Auto Claude）

**为你规划、构建并验证软件的自主多智能体编码框架。**

![Aperant Kanban Board](assets/001-aperant-kanban-board-71bdc8ef46.png)

[![License](https://img.shields.io/badge/license-AGPL--3.0-green?style=flat-square)](./agpl-3.0.txt)
[![Discord](https://img.shields.io/badge/Discord-Join%20Community-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.gg/KCXaPBr4Dj)
[![YouTube](https://img.shields.io/badge/YouTube-Subscribe-FF0000?style=flat-square&logo=youtube&logoColor=white)](https://www.youtube.com/@AndreMikalsen)
[![CI](https://img.shields.io/github/actions/workflow/status/AndyMik90/Auto-Claude/ci.yml?branch=main&style=flat-square&label=CI)](https://github.com/AndyMik90/Auto-Claude/actions)
[![Mentioned in Awesome Claude Code](https://awesome.re/mentioned-badge-flat.svg)](https://github.com/hesreallyhim/awesome-claude-code)

---

## 下载

### 稳定版

<!-- STABLE_VERSION_BADGE -->
[![Stable](https://img.shields.io/badge/stable-2.7.6-blue?style=flat-square)](https://github.com/AndyMik90/Auto-Claude/releases/tag/v2.7.6)
<!-- STABLE_VERSION_BADGE_END -->

<!-- STABLE_DOWNLOADS -->
| 平台 | 下载 |
|------|------|
| **Windows** | [Auto-Claude-2.7.6-win32-x64.exe](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.6/Auto-Claude-2.7.6-win32-x64.exe) |
| **macOS (Apple Silicon)** | [Auto-Claude-2.7.6-darwin-arm64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.6/Auto-Claude-2.7.6-darwin-arm64.dmg) |
| **macOS (Intel)** | [Auto-Claude-2.7.6-darwin-x64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.6/Auto-Claude-2.7.6-darwin-x64.dmg) |
| **Linux** | [Auto-Claude-2.7.6-linux-x86_64.AppImage](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.6/Auto-Claude-2.7.6-linux-x86_64.AppImage) |
| **Linux (Debian)** | [Auto-Claude-2.7.6-linux-amd64.deb](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.6/Auto-Claude-2.7.6-linux-amd64.deb) |
| **Linux (Flatpak)** | [Auto-Claude-2.7.6-linux-x86_64.flatpak](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.6/Auto-Claude-2.7.6-linux-x86_64.flatpak) |
<!-- STABLE_DOWNLOADS_END -->

### 测试版

> ⚠️ 测试版可能包含 bug 和破坏性变更。[查看所有发布版本](https://github.com/AndyMik90/Auto-Claude/releases)

<!-- BETA_VERSION_BADGE -->
[![Beta](https://img.shields.io/badge/beta-2.8.0--beta.6-orange?style=flat-square)](https://github.com/AndyMik90/Auto-Claude/releases/tag/v2.8.0-beta.6)
<!-- BETA_VERSION_BADGE_END -->

<!-- BETA_DOWNLOADS -->
| 平台 | 下载 |
|------|------|
| **Windows** | [Aperant-2.8.0-beta.5-win32-x64.exe](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.8.0-beta.5/Aperant-2.8.0-beta.5-win32-x64.exe) |
| **macOS (Apple Silicon)** | [Aperant-2.8.0-beta.5-darwin-arm64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.8.0-beta.5/Aperant-2.8.0-beta.5-darwin-arm64.dmg) |
| **macOS (Intel)** | [Aperant-2.8.0-beta.5-darwin-x64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.8.0-beta.5/Aperant-2.8.0-beta.5-darwin-x64.dmg) |
| **Linux** | [Aperant-2.8.0-beta.5-linux-x86_64.AppImage](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.8.0-beta.5/Aperant-2.8.0-beta.5-linux-x86_64.AppImage) |
| **Linux (Debian)** | [Aperant-2.8.0-beta.5-linux-amd64.deb](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.8.0-beta.5/Aperant-2.8.0-beta.5-linux-amd64.deb) |
| **Linux (Flatpak)** | [Aperant-2.8.0-beta.5-linux-x86_64.flatpak](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.8.0-beta.5/Aperant-2.8.0-beta.5-linux-x86_64.flatpak) |
<!-- BETA_DOWNLOADS_END -->

> 所有发布版本均包含 SHA256 校验和以及 VirusTotal 扫描结果，用于安全验证。

---

## 要求

- **Claude Pro/Max 订阅** - [在这里获取](https://claude.ai/upgrade)
- **Claude Code CLI** - `npm install -g @anthropic-ai/claude-code`
- **Git 仓库** - 你的项目必须已初始化为 git 仓库

---

## 快速开始

1. **下载并安装**适用于你平台的应用
2. **打开你的项目** - 选择一个 git 仓库文件夹
3. **连接 Claude** - 应用会引导你完成 OAuth 设置
4. **创建任务** - 描述你想构建的内容
5. **查看其运行** - 智能体会自主进行规划、编码和验证

---

## 功能

| 功能 | 说明 |
|------|------|
| **Autonomous Tasks** | 描述你的目标；智能体会处理规划、实现和验证 |
| **Parallel Execution** | 最多可同时运行 12 个智能体终端，并行执行多个构建任务 |
| **Isolated Workspaces** | 所有更改都在 git worktree 中进行，你的主分支保持安全 |
| **Self-Validating QA** | 内置质量保障循环会在你审查前捕获问题 |
| **AI-Powered Merge** | 在合并回主分支时自动解决冲突 |
| **Memory Layer** | 智能体可跨会话保留洞察，从而实现更智能的构建 |
| **GitHub/GitLab Integration** | 导入 issue，使用 AI 调查，并创建合并请求 |
| **Linear Integration** | 与 Linear 同步任务，跟踪团队进度 |
| **Cross-Platform** | 面向 Windows、macOS 和 Linux 的原生桌面应用 |
| **Auto-Updates** | 发布新版本时，应用会自动更新 |

---

## 界面

### 看板
从规划到完成的可视化任务管理。创建任务并实时监控智能体进度。

### 智能体终端
由 AI 驱动的终端，支持一键注入任务上下文。可生成多个智能体以并行工作。

![Agent Terminals](assets/002-agent-terminals-f1d8cbb159.png)

### 路线图
由 AI 辅助的功能规划，包含竞品分析和目标受众定位。

![Roadmap](assets/003-roadmap-136604c279.png)

### 附加功能
- **Insights** - 用于探索代码库的聊天界面
- **Ideation** - 发现改进点、性能问题和漏洞
- **Changelog** - 从已完成任务生成发布说明

---

## 项目结构

```
Aperant/
├── apps/
│   └── desktop/     # Electron desktop application (TypeScript AI agent layer + UI)
├── guides/          # Additional documentation
└── scripts/         # Build utilities
```

---

## 开发

想从源码构建或参与贡献？请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 获取完整的开发环境设置说明。

有关 Linux 特定构建（Flatpak、AppImage），请参阅 [guides/linux.md](guides/linux.md)。

---

## 安全

Aperant 使用三层安全模型：

1. **OS Sandbox** - Bash 命令在隔离环境中运行
2. **Filesystem Restrictions** - 操作被限制在项目目录内
3. **Dynamic Command Allowlist** - 仅允许基于检测到的项目技术栈所批准的命令

所有发布版本都：
- 在发布前经过 VirusTotal 扫描
- 包含用于验证的 SHA256 校验和
- 在适用情况下进行代码签名（macOS）

---

## 可用脚本

| 命令 | 说明 |
|------|------|
| `npm run install:all` | 安装所有依赖 |
| `npm start` | 构建并运行桌面应用 |
| `npm run dev` | 以开发模式运行，并启用热重载 |
| `npm run package` | 为当前平台打包 |
| `npm run package:mac` | 为 macOS 打包 |
| `npm run package:win` | 为 Windows 打包 |
| `npm run package:linux` | 为 Linux 打包 |
| `npm run package:flatpak` | 打包为 Flatpak（见 [guides/linux.md](guides/linux.md)） |
| `npm run lint` | 运行 linter |
| `npm test` | 运行前端测试 |

---

## 贡献

欢迎贡献！请阅读 [CONTRIBUTING.md](CONTRIBUTING.md)，了解：
- 开发环境设置说明
- 代码风格指南
- 测试要求
- Pull Request 流程

---

## 社区

- **Discord** - [加入我们的社区](https://discord.gg/KCXaPBr4Dj)
- **Issues** - [报告 bug 或请求功能](https://github.com/AndyMik90/Auto-Claude/issues)
- **Discussions** - [提出问题](https://github.com/AndyMik90/Auto-Claude/discussions)

---

## 许可证

**AGPL-3.0** - GNU Affero General Public License v3.0

Aperant 可免费使用。如果你修改并分发它，或将其作为服务运行，你的代码也必须依据 AGPL-3.0 以开源方式发布。

针对闭源使用场景可提供商业许可。

---

## Star 历史

[![GitHub Repo stars](https://img.shields.io/github/stars/AndyMik90/Auto-Claude?style=social)](https://github.com/AndyMik90/Auto-Claude/stargazers)

[![Star History Chart](assets/004-star-history-chart-d8537da84a.svg)](https://star-history.com/#AndyMik90/Auto-Claude&Date)
