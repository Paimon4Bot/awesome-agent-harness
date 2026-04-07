<div align="center">
<a href="https://swe-rex.com"><img src="assets/004-swerex-logo-ff8bc5c8e6.svg" alt="SWE-ReX" style="height: 7em"/></a>
</div>

# SWE-agent 远程执行框架

[![Docs](https://img.shields.io/badge/Docs-green?style=for-the-badge&logo=materialformkdocs&logoColor=white)](https://swe-rex.com/latest/)
[![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)](https://join.slack.com/t/swe-bench/shared_invite/zt-36pj9bu5s-o3_yXPZbaH2wVnxnss1EkQ)
[![PyPI - Version](https://img.shields.io/pypi/v/swe-rex?style=for-the-badge&logo=python&logoColor=white&labelColor=black&color=deeppink)](https://pypi.org/project/swe-rex/)

SWE-ReX 是一个与沙箱化 shell 环境交互的运行时接口，让你能够轻松地让 AI 代理在*任意环境*上运行*任意命令*。

无论命令是在本地执行，还是在 Docker 容器、AWS 远程机器、Modal 或其他平台上远程执行，你的代理代码都保持不变。
需要并行运行 100 个代理？同样没问题！

具体来说，SWE-ReX 允许你的代理

* ✅ **与运行中的 shell 会话交互**。SWE-ReX 会识别命令何时完成，提取输出和退出码并返回给你的代理。
* ✅ 让你的代理在 shell 中使用**交互式命令行工具**，如 `ipython`、`gdb` 等。
* ✅ **并行交互多个 shell 会话**，类似于人类可以同时运行 shell、ipython、gdb 等。

我们构建 SWE-ReX 的目的是帮助你专注于开发和评估代理，而不是基础设施。

SWE-ReX 源自我们在 [SWE-agent][] 和 [SWE-agent enigma][enigma] 中的经验。
通过使用 SWE-ReX，我们

* 🦖 支持**快速、大规模并行**的代理运行（让大规模基准测试评估变得轻而易举）。
* 🦖 支持**广泛的平台**，包括没有 Docker 的非 Linux 机器。
* 🦖 **将代理逻辑与基础设施关注点解耦**，使 SWE-agent 更稳定、更易于维护。

这是 [SWE-agent][] 使用 SWE-ReX 并行运行 30 个 [SWE-bench][] 实例的演示：

<div align="center">
<img src="assets/005-swerex-55ddd61f6d.gif" alt="SWE-ReX in action" width=600px>
</div>

## 快速开始

```bash
pip install swe-rex
# With modal support
pip install 'swe-rex[modal]'
# With fargate support
pip install 'swe-rex[fargate]'
# With daytona support (WIP)
pip install 'swe-rex[daytona]'
# Development setup (all optional dependencies)
pip install 'swe-rex[dev]'
```

然后前往[我们的文档](https://swe-rex.com/)了解更多！

[SWE-agent]: assets/001-asset-60ebe362be.html
[SWE-bench]: assets/002-asset-c3824812b2.html
[enigma]: assets/003-asset-917b6dc558.html

## 我们的其他项目

<div align="center">
  <a href="https://github.com/SWE-agent/SWE-agent"><img src="assets/006-sweagent-logo-text-below-8a963c4f12.svg" alt="SWE-agent" height="120px"></a>
   &nbsp;&nbsp;
  <a href="https://github.com/SWE-agent/mini-SWE-agent"><img src="assets/007-mini-logo-text-below-873dabe7cc.svg" alt="Mini-SWE-Agent" height="120px"></a>
   &nbsp;&nbsp;
  <a href="https://github.com/SWE-bench/SWE-smith"><img src="assets/008-swesmith-logo-text-below-6f299db492.svg" alt="SWE-smith" height="120px"></a>
   &nbsp;&nbsp;
  <a href="https://github.com/SWE-bench/SWE-bench"><img src="assets/009-swebench-logo-text-below-c09495dc1b.svg" alt="SWE-bench" height="120px"></a>
  &nbsp;&nbsp;
  <a href="https://github.com/codeclash-ai/codeclash"><img src="assets/010-codeclash-logo-text-below-26f1afca1a.svg" alt="CodeClash" height="120px"></a>
  &nbsp;&nbsp;
  <a href="https://github.com/SWE-bench/sb-cli"><img src="assets/011-sbcli-logo-text-below-aaeff3f911.svg" alt="sb-cli" height="120px"></a>
</div>
