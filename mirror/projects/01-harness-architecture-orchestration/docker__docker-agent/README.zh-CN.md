# 🤖 Docker Agent 🤖

> 通过声明式 YAML 配置、丰富的工具生态和多代理编排来构建、运行和共享 AI 代理。

![docker agent in action](assets/001-docker-agent-in-action-282dc7e69d.gif)

## Docker Agent 是什么？

`docker-agent` 让你创建和运行智能 AI 代理来协作解决复杂问题 — 无需编写代码。

`docker-agent` 是一个 `docker` CLI 插件，可通过 `docker agent` 运行。

用 YAML 定义代理，赋予它们工具，然后让它们工作。

```yaml
agents:
  root:
    model: openai/gpt-5-mini
    description: A helpful AI assistant
    instruction: |
      You are a knowledgeable assistant that helps users with various tasks.
      Be helpful, accurate, and concise in your responses.
    toolsets:
      - type: mcp
        ref: docker:duckduckgo
```

```sh
docker agent run agent.yaml
```

## 核心特性

- **多代理架构** — 创建专业代理团队，自动委派任务
- **丰富的工具生态** — 内置工具 + 任何 [MCP](https://modelcontextprotocol.io/) 服务器（本地、远程或基于 Docker）
- **AI 供应商无关** — 支持 OpenAI、Anthropic、Gemini、AWS Bedrock、Mistral、xAI、[Docker Model Runner](https://docs.docker.com/ai/model-runner/) 等
- **YAML 配置** — 声明式、可版本化、可共享
- **高级推理** — 内置思考、待办和记忆工具
- **RAG** — 可插拔的检索方案，支持 BM25、嵌入、混合搜索和重排序
- **打包与共享** — 将代理推送到任意 OCI 注册表，随处拉取运行

## 安装

**Docker Desktop**（4.63+）— docker-agent CLI 插件已预装。直接运行 `docker agent` 即可。

**Homebrew** — `brew install docker-agent`。直接运行 `docker-agent`，或将二进制文件符号链接到 `~/.docker/cli-plugins/docker-agent`，然后运行 `docker agent`。

**二进制发布版** — 从 [GitHub Releases](https://github.com/docker/docker-agent/releases) 下载。将 `docker-agent` 二进制文件符号链接到 `~/.docker/cli-plugins/docker-agent` 以使用 `docker agent`，或直接使用 `docker-agent`。

至少设置一个 API 密钥（或使用 [Docker Model Runner](https://docs.docker.com/ai/model-runner/) 运行本地模型）：

```sh
export OPENAI_API_KEY=sk-...        # or ANTHROPIC_API_KEY, GOOGLE_API_KEY, etc.
```

## 快速开始

```sh
# 运行默认代理
docker agent run

# 从代理目录运行
docker agent run agentcatalog/pirate

# 交互式生成新代理
docker agent new

# 运行你自己的配置
docker agent run agent.yaml
```

更多示例请参见 [`examples/`](examples/README.md) 目录。

## 文档

📖 **[完整文档](https://docker.github.io/docker-agent/)**

- [安装](https://docker.github.io/docker-agent/getting-started/installation) · [快速开始](https://docker.github.io/docker-agent/getting-started/quickstart)
- [代理](https://docker.github.io/docker-agent/concepts/agents) · [模型](https://docker.github.io/docker-agent/concepts/models) · [工具](https://docker.github.io/docker-agent/concepts/tools) · [多代理](https://docker.github.io/docker-agent/concepts/multi-agent)
- [配置参考](https://docker.github.io/docker-agent/configuration/overview)
- [TUI](https://docker.github.io/docker-agent/features/tui) · [CLI](https://docker.github.io/docker-agent/features/cli) · [MCP 模式](https://docker.github.io/docker-agent/features/mcp-mode) · [RAG](https://docker.github.io/docker-agent/features/rag)
- [模型供应商](https://docker.github.io/docker-agent/providers/overview) · [Docker Model Runner](https://docker.github.io/docker-agent/providers/dmr)

## 贡献

阅读[贡献指南](https://docker.github.io/docker-agent/community/contributing)开始参与。我们使用 `docker-agent` 来构建 `docker-agent`：

```sh
docker agent run ./golang_developer.yaml
```

## 遥测

我们收集匿名使用数据以改进工具。参见[遥测说明](https://docker.github.io/docker-agent/community/telemetry)。

## 社区

[Docker Community Slack](http://dockr.ly/comm-slack) · [#docker-agent 频道](https://dockercommunity.slack.com/archives/C09DASHHRU4)
