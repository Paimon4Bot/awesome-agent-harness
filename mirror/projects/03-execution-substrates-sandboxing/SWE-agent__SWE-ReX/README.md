<div align="center">
<a href="https://swe-rex.com"><img src="assets/004-swerex-logo-ff8bc5c8e6.svg" alt="SWE-ReX" style="height: 7em"/></a>
</div>

# SWE-agent Remote Execution Framework

[![Docs](https://img.shields.io/badge/Docs-green?style=for-the-badge&logo=materialformkdocs&logoColor=white)](https://swe-rex.com/latest/)
[![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)](https://join.slack.com/t/swe-bench/shared_invite/zt-36pj9bu5s-o3_yXPZbaH2wVnxnss1EkQ)
[![PyPI - Version](https://img.shields.io/pypi/v/swe-rex?style=for-the-badge&logo=python&logoColor=white&labelColor=black&color=deeppink)](https://pypi.org/project/swe-rex/)

SWE-ReX is a runtime interface for interacting with sandboxed shell environments, allowing you to effortlessly let your AI agent run *any command* on *any environment*.

Whether commands are executed locally or remotely in Docker containers, AWS remote machines, Modal, or something else, your agent code remains the same.
Running 100 agents in parallel? No problem either!

Specifically, SWE-ReX allows your agent to

* ✅ **Interact with running shell sessions**. SWE-ReX will recognize when commands are finished, extract the output and exit code and return them to your agent.
* ✅ Let your agent use **interactive command line tools** like `ipython`, `gdb` or more in the shell.
* ✅ Interact with **multiple such shell sessions in parallel**, similar to how humans can have a shell, ipython, gdb, etc. all running at the same time.

We built SWE-ReX to help you focus on developing and evaluating your agent, not on infrastructure.

SWE-ReX came out of our experiences with [SWE-agent][] and [SWE-agent enigma][enigma].
Using SWE-ReX, we

* 🦖 Support **fast, massively parallel** agent runs (which made evaluating on large benchmarks a breeze).
* 🦖 Support a **broad range of platforms**, including non-Linux machines without Docker.
* 🦖 **Disentangle agent logic from infrastructure concerns**, making SWE-agent more stable and easier to maintain.

This is [SWE-agent][] using SWE-ReX to run on 30 [SWE-bench][] instances in parallel:

<div align="center">
<img src="assets/005-swerex-55ddd61f6d.gif" alt="SWE-ReX in action" width=600px>
</div>

## Get started

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

Then head over to [our documentation](https://swe-rex.com/) to learn more!

[SWE-agent]: assets/001-asset-60ebe362be.html
[SWE-bench]: assets/002-asset-c3824812b2.html
[enigma]: assets/003-asset-917b6dc558.html

## Our other projects

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
