<div align="center">
  <a href="https://cua.ai" target="_blank" rel="noopener noreferrer">
    <picture>
      <source media="(prefers-color-scheme: dark)" alt="Cua logo" width="150" srcset="assets/013-logo-white-ed34356fdd.svg">
      <source media="(prefers-color-scheme: light)" alt="Cua logo" width="150" srcset="assets/002-logo-black-e0155b81d0.svg">
      <img alt="Cua logo" width="150" src="assets/002-logo-black-e0155b81d0.svg">
    </picture>
  </a>

  <p align="center">Build, benchmark, and deploy agents that use computers</p>

  <p align="center">
    <a href="https://cua.ai" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/cua.ai-0ea5e9" alt="cua.ai"></a>
    <a href="https://discord.com/invite/cua-ai" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/Discord-Join%20Server-10b981?logo=discord&logoColor=white" alt="Discord"></a>
    <a href="https://x.com/trycua" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/twitter/follow/trycua?style=social" alt="Twitter"></a>
    <a href="https://cua.ai/docs" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/Docs-0ea5e9.svg" alt="Documentation"></a>
    <br>
<a href="https://trendshift.io/repositories/13685" target="_blank"><img src="https://trendshift.io/api/badge/repositories/13685" alt="trycua%2Fcua | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
  </p>

</div>

## Choose Your Path

<div align="center">
  <table>
    <tr>
      <td align="center">
        <a href="#cua---agentic-ui-automation--code-execution">
          <picture>
            <source media="(prefers-color-scheme: dark)" srcset="assets/014-card-cua-dark-4fccb3962c.png">
            <source media="(prefers-color-scheme: light)" srcset="assets/003-card-cua-light-607c488f1a.png">
            <img src="assets/003-card-cua-light-607c488f1a.png" alt="Cua" width="280">
          </picture>
        </a>
      </td>
      <td align="center">
        <a href="#cua-bench---benchmarks--rl-environments">
          <picture>
            <source media="(prefers-color-scheme: dark)" srcset="assets/015-card-cua-bench-dark-2af7276825.png">
            <source media="(prefers-color-scheme: light)" srcset="assets/004-card-cua-bench-light-fffa647c47.png">
            <img src="assets/004-card-cua-bench-light-fffa647c47.png" alt="Cua-Bench" width="280">
          </picture>
        </a>
      </td>
      <td align="center">
        <a href="#lume---macos-virtualization">
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

## Cua - Agent-Ready Sandboxes for Any OS

Build agents that see screens, click buttons, and complete tasks autonomously. One API for any VM or container image — cloud or local.

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

|                    | Linux container | Linux VM | macOS | Windows | Android | BYOI (.qcow2, .iso) |
| ------------------ | --------------- | -------- | ----- | ------- | ------- | ------------------- |
| **Cloud (cua.ai)** | ✅              | ✅       | ✅    | ✅      | ✅      | 🔜 soon             |
| **Local (QEMU)**   | ✅              | ✅       | ✅    | ✅      | ✅      | ✅                  |

**[Get Started](https://cua.ai/docs/cua/guide/get-started/set-up-sandbox)** | **[Examples](https://cua.ai/docs/cua/examples)** | **[API Reference](https://cua.ai/docs/cua/reference/agent-sdk)**

---

## CuaBot - Co-op computer-use for any agent

<div align="center">
  <img src="assets/008-cuabot-screenshot-ab0bab617d.png" alt="cuabot screenshot" width="720">
</div>

`cuabot` gives any coding agent a seamless sandbox for computer-use. Individual windows appear natively on your desktop with H.265, shared clipboard, and audio.

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

Built-in support for `agent-browser` and `agent-device` (iOS, Android) out of the box.

<div align="center">

**[Get Started](https://cua.ai/docs/cuabot/guide/getting-started/introduction)** | **[Installation](https://cua.ai/docs/cuabot/guide/getting-started/installation)** | First spotted at [ClawCon](https://www.claw-con.com/)

<img height="64" alt="cuaXclawdbot_nbg" src="assets/009-8b92237d-6e9b-4b3a-ae9a-b3560622ec1d-d17db7f3e3.png" />

</div>

---

## Cua-Bench - Benchmarks & RL Environments

Evaluate computer-use agents on OSWorld, ScreenSpot, Windows Arena, and custom tasks. Export trajectories for training.

<!-- <img src="assets/010-cua-bench-architecture-c5186ca6ef.png" alt="Cua-Bench Architecture" width="100%"> -->

```bash
# Install and create base image
cd cua-bench
uv tool install -e . && cb image create linux-docker

# Run benchmark with agent
cb run dataset datasets/cua-bench-basic --agent cua-agent --max-parallel 4
```

**[Get Started](https://cua.ai/docs/cuabench/guide/getting-started/first-steps)** | **[Partner With Us](https://cuabench.ai/)** | **[Registry](https://cuabench.ai/registry)** | **[CLI Reference](https://cua.ai/docs/cuabench/reference/cli-reference)**

---

## Lume - macOS Virtualization

Create and manage macOS/Linux VMs with near-native performance on Apple Silicon using Apple's Virtualization.Framework.

<!-- <img src="assets/011-lume-architecture-608eaac4fc.png" alt="Lume Architecture" width="100%"> -->

```bash
# Install Lume
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/trycua/cua/main/libs/lume/scripts/install.sh)"

# Pull & start a macOS VM
lume run macos-sequoia-vanilla:latest
```

**[Get Started](https://cua.ai/docs/lume)** | **[FAQ](https://cua.ai/docs/lume/guide/getting-started/faq)** | **[CLI Reference](https://cua.ai/docs/lume/reference/cli-reference)**

---

## Packages

| Package                                                                     | Description                                                |
| --------------------------------------------------------------------------- | ---------------------------------------------------------- |
| [cuabot](https://docs.trycua.com/cuabot/guide/getting-started/introduction) | Multi-agent computer-use sandbox CLI                       |
| [cua-agent](https://cua.ai/docs/cua/reference/agent-sdk)                    | AI agent framework for computer-use tasks                  |
| [cua-sandbox](https://cua.ai/docs/cua/reference/sandbox-sdk)                | SDK for creating and controlling sandboxes                 |
| [cua-computer-server](https://cua.ai/docs/cua/reference/sandbox-sdk)        | Driver for UI interactions and code execution in sandboxes |
| [cua-bench](https://cua.ai/docs/cuabench)                                   | Benchmarks and RL environments for computer-use            |
| [lume](https://cua.ai/docs/lume)                                            | macOS/Linux VM management on Apple Silicon                 |
| [lumier](https://cua.ai/docs/lume/guide/advanced/lumier)                    | Docker-compatible interface for Lume VMs                   |

## Resources

- [Documentation](https://cua.ai/docs) — Guides, examples, and API reference
- [Blog](https://www.cua.ai/blog) — Tutorials, updates, and research
- [Discord](https://discord.com/invite/mVnXXpdE85) — Community support and discussions
- [GitHub Issues](https://github.com/trycua/cua/issues) — Bug reports and feature requests

## Contributing

We welcome contributions! See our [Contributing Guidelines](CONTRIBUTING.md) for details.

## License

MIT License — see [LICENSE](LICENSE.md) for details.

Third-party components have their own licenses:

- [Kasm](libs/kasm/LICENSE) (MIT)
- [OmniParser](https://github.com/microsoft/OmniParser/blob/master/LICENSE) (CC-BY-4.0)
- Optional `cua-agent[omni]` includes ultralytics (AGPL-3.0)

## Trademarks

Apple, macOS, Ubuntu, Canonical, and Microsoft are trademarks of their respective owners. This project is not affiliated with or endorsed by these companies.

---

<div align="center">

[![Stargazers over time](assets/001-stargazers-over-time-6f74767723.svg)](https://starchart.cc/trycua/cua)

Thank you to all our [GitHub Sponsors](https://github.com/sponsors/trycua)!

<img width="300" alt="coderabbit-cli" src="assets/012-23a98e38-7897-4043-8ef7-eb990520dccc-d18267cf2f.png" />

</div>
