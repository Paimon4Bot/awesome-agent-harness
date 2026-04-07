<div align="center">
  <a href="https://cua.ai" target="_blank" rel="noopener noreferrer">
    <picture>
      <source media="(prefers-color-scheme: dark)" alt="Cua logo" width="150" srcset="assets/013-logo-white-ed34356fdd.svg">
      <source media="(prefers-color-scheme: light)" alt="Cua logo" width="150" srcset="assets/002-logo-black-e0155b81d0.svg">
      <img alt="Cua logo" width="150" src="assets/002-logo-black-e0155b81d0.svg">
    </picture>
  </a>

  <p align="center">构建、基准测试和部署使用计算机的代理</p>

  <p align="center">
    <a href="https://cua.ai" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/cua.ai-0ea5e9" alt="cua.ai"></a>
    <a href="https://discord.com/invite/cua-ai" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/Discord-Join%20Server-10b981?logo=discord&logoColor=white" alt="Discord"></a>
    <a href="https://x.com/trycua" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/twitter/follow/trycua?style=social" alt="Twitter"></a>
    <a href="https://cua.ai/docs" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/Docs-0ea5e9.svg" alt="Documentation"></a>
    <br>
<a href="https://trendshift.io/repositories/13685" target="_blank"><img src="https://trendshift.io/api/badge/repositories/13685" alt="trycua%2Fcua | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
  </p>

</div>

## 选择你的路径

<div align="center">
  <table>
    <tr>
      <td align="center">
        <a href="#cua---面向代理的跨操作系统沙箱">
          <picture>
            <source media="(prefers-color-scheme: dark)" srcset="assets/014-card-cua-dark-4fccb3962c.png">
            <source media="(prefers-color-scheme: light)" srcset="assets/003-card-cua-light-607c488f1a.png">
            <img src="assets/003-card-cua-light-607c488f1a.png" alt="Cua" width="280">
          </picture>
        </a>
      </td>
      <td align="center">
        <a href="#cua-bench---基准测试与强化学习环境">
          <picture>
            <source media="(prefers-color-scheme: dark)" srcset="assets/015-card-cua-bench-dark-2af7276825.png">
            <source media="(prefers-color-scheme: light)" srcset="assets/004-card-cua-bench-light-fffa647c47.png">
            <img src="assets/004-card-cua-bench-light-fffa647c47.png" alt="Cua-Bench" width="280">
          </picture>
        </a>
      </td>
      <td align="center">
        <a href="#lume---macos-虚拟化">
          <picture>
            <source media="(prefers-color-scheme: dark)" srcset="assets/016-card-lume-dark-2d7b9144b0.png">
            <source media="(prefers-color-scheme: light)" srcset="assets/005-card-lume-light-5d5d62a9e0.png">
            <img src="assets/005-card-lume-light-5d5d62a9e0.png" alt="Lume" width="280">
          </picture>
        </a>
      </td>
    </tr>
    <tr>
      <td colspan="3" align="center">
        <a href="https://cua.ai/docs/cuabot/guide/getting-started/introduction">
          <picture>
            <source media="(prefers-color-scheme: dark)" srcset="assets/017-card-cua-bot-dark-56d6149d7c.png">
            <source media="(prefers-color-scheme: light)" srcset="assets/006-card-cua-bot-light-0bae34b2ae.png">
            <img src="assets/006-card-cua-bot-light-0bae34b2ae.png" alt="Cua Bot" width="888">
          </picture>
        </a>
      </td>
    </tr>
  </table>
</div>

---

## Cua - 面向代理的跨操作系统沙箱

构建能够看到屏幕、点击按钮并自主完成任务的代理。一个 API 适配任意 VM 或容器镜像——云端或本地均可。

```sh
pip install cua
```

<!-- <img src="assets/007-cua-architecture-259a16d537.png" alt="Cua Architecture" width="100%"> -->

```python
# Requires Python 3.11 or later
from cua import Sandbox, Image

# Same API regardless of OS or runtime
async with Sandbox.ephemeral(Image.linux()) as sb:   # or .macos() .windows() .android()
    result = await sb.shell.run("echo hello")
    screenshot = await sb.screenshot()
    await sb.mouse.click(100, 200)
    await sb.keyboard.type("Hello from Cua!")
    await sb.mobile.gesture((100, 500), (100, 200))  # multi-touch gestures
```

|                    | Linux 容器 | Linux VM | macOS | Windows | Android | BYOI (.qcow2, .iso) |
| ------------------ | --------------- | -------- | ----- | ------- | ------- | ------------------- |
| **Cloud (cua.ai)** | ✅              | ✅       | ✅    | ✅      | ✅      | 🔜 即将推出             |
| **Local (QEMU)**   | ✅              | ✅       | ✅    | ✅      | ✅      | ✅                  |

**[入门指南](https://cua.ai/docs/cua/guide/get-started/set-up-sandbox)** | **[示例](https://cua.ai/docs/cua/examples)** | **[API 参考](https://cua.ai/docs/cua/reference/agent-sdk)**

---

## CuaBot - 为任意代理提供协作式计算机操控

<div align="center">
  <img src="assets/008-cuabot-screenshot-ab0bab617d.png" alt="cuabot screenshot" width="720">
</div>

`cuabot` 为任意编程代理提供无缝的计算机使用沙箱。独立窗口以原生方式显示在你的桌面上，支持 H.265、共享剪贴板和音频。

```bash
npx cuabot                 # Setup onboarding
```

```bash
# Run any agent in a sandbox
cuabot claude              # Claude Code
cuabot openclaw            # OpenClaw in the sandbox

# Run any GUI workflow in a sandbox
cuabot chromium
cuabot --screenshot
cuabot --type "hello"
cuabot --click <x> <y> [button]
```

内置支持 `agent-browser` 和 `agent-device`（iOS、Android），开箱即用。

<div align="center">

**[入门指南](https://cua.ai/docs/cuabot/guide/getting-started/introduction)** | **[安装](https://cua.ai/docs/cuabot/guide/getting-started/installation)** | 首次亮相于 [ClawCon](https://www.claw-con.com/)

<img height="64" alt="cuaXclawdbot_nbg" src="assets/009-8b92237d-6e9b-4b3a-ae9a-b3560622ec1d-d17db7f3e3.png" />

</div>

---

## Cua-Bench - 基准测试与强化学习环境

在 OSWorld、ScreenSpot、Windows Arena 和自定义任务上评估计算机操控代理。导出轨迹数据用于训练。

<!-- <img src="assets/010-cua-bench-architecture-c5186ca6ef.png" alt="Cua-Bench Architecture" width="100%"> -->

```bash
# Install and create base image
cd cua-bench
uv tool install -e . && cb image create linux-docker

# Run benchmark with agent
cb run dataset datasets/cua-bench-basic --agent cua-agent --max-parallel 4
```

**[入门指南](https://cua.ai/docs/cuabench/guide/getting-started/first-steps)** | **[与我们合作](https://cuabench.ai/)** | **[注册表](https://cuabench.ai/registry)** | **[CLI 参考](https://cua.ai/docs/cuabench/reference/cli-reference)**

---

## Lume - macOS 虚拟化

使用 Apple 的 Virtualization.Framework 在 Apple Silicon 上创建和管理 macOS/Linux VM，实现接近原生的性能。

<!-- <img src="assets/011-lume-architecture-608eaac4fc.png" alt="Lume Architecture" width="100%"> -->

```bash
# Install Lume
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/trycua/cua/main/libs/lume/scripts/install.sh)"

# Pull & start a macOS VM
lume run macos-sequoia-vanilla:latest
```

**[入门指南](https://cua.ai/docs/lume)** | **[常见问题](https://cua.ai/docs/lume/guide/getting-started/faq)** | **[CLI 参考](https://cua.ai/docs/lume/reference/cli-reference)**

---

## 包

| Package                                                                     | 描述                                                |
| --------------------------------------------------------------------------- | ---------------------------------------------------------- |
| [cuabot](https://docs.trycua.com/cuabot/guide/getting-started/introduction) | 多代理计算机操控沙箱 CLI                       |
| [cua-agent](https://cua.ai/docs/cua/reference/agent-sdk)                    | 用于计算机操控任务的 AI 代理框架                  |
| [cua-sandbox](https://cua.ai/docs/cua/reference/sandbox-sdk)                | 用于创建和控制沙箱的 SDK                 |
| [cua-computer-server](https://cua.ai/docs/cua/reference/sandbox-sdk)        | 沙箱中的 UI 交互和代码执行驱动 |
| [cua-bench](https://cua.ai/docs/cuabench)                                   | 计算机操控的基准测试和强化学习环境            |
| [lume](https://cua.ai/docs/lume)                                            | Apple Silicon 上的 macOS/Linux VM 管理                 |
| [lumier](https://cua.ai/docs/lume/guide/advanced/lumier)                    | Lume VM 的 Docker 兼容接口                   |

## 资源

- [文档](https://cua.ai/docs) — 指南、示例和 API 参考
- [博客](https://www.cua.ai/blog) — 教程、更新和研究
- [Discord](https://discord.com/invite/mVnXXpdE85) — 社区支持和讨论
- [GitHub Issues](https://github.com/trycua/cua/issues) — Bug 报告和功能请求

## 贡献

欢迎贡献代码！详情请参阅我们的[贡献指南](CONTRIBUTING.md)。

## 许可证

MIT 许可证 — 详情请参阅 [LICENSE](LICENSE.md)。

第三方组件拥有各自独立的许可证：

- [Kasm](libs/kasm/LICENSE) (MIT)
- [OmniParser](https://github.com/microsoft/OmniParser/blob/master/LICENSE) (CC-BY-4.0)
- 可选的 `cua-agent[omni]` 包含 ultralytics (AGPL-3.0)

## 商标

Apple、macOS、Ubuntu、Canonical 和 Microsoft 是其各自所有者的商标。本项目与这些公司没有附属或认可关系。

---

<div align="center">

[![Stargazers over time](assets/001-stargazers-over-time-6f74767723.svg)](https://starchart.cc/trycua/cua)

感谢所有 [GitHub 赞助者](https://github.com/sponsors/trycua)！

<img width="300" alt="coderabbit-cli" src="assets/012-23a98e38-7897-4043-8ef7-eb990520dccc-d18267cf2f.png" />

</div>
