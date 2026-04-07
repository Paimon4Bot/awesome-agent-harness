# ContextForge

> 一个开源注册表与代理，可联邦化 MCP、A2A 以及 REST/gRPC API，并提供集中式治理、发现与可观测性。可优化智能体与工具调用，并支持插件。

![ContextForge Banner](assets/001-contextforge-banner-f28bd10bb2.png)

<!-- === CI / Security / Build Badges === -->
[![Build Python Package](https://github.com/IBM/mcp-context-forge/actions/workflows/python-package.yml/badge.svg)](https://github.com/IBM/mcp-context-forge/actions/workflows/python-package.yml)&nbsp;
[![Bandit Security](https://github.com/IBM/mcp-context-forge/actions/workflows/bandit.yml/badge.svg)](https://github.com/IBM/mcp-context-forge/actions/workflows/bandit.yml)&nbsp;
[![Dependency Review](https://github.com/IBM/mcp-context-forge/actions/workflows/dependency-review.yml/badge.svg)](https://github.com/IBM/mcp-context-forge/actions/workflows/dependency-review.yml)&nbsp;
[![Tests & Coverage](https://github.com/IBM/mcp-context-forge/actions/workflows/pytest.yml/badge.svg)](https://github.com/IBM/mcp-context-forge/actions/workflows/pytest.yml)&nbsp;
[![Lint & Static Analysis](https://github.com/IBM/mcp-context-forge/actions/workflows/lint.yml/badge.svg)](https://github.com/IBM/mcp-context-forge/actions/workflows/lint.yml)

<!-- === Package / Container === -->
[![Async](https://img.shields.io/badge/async-await-green.svg)](https://docs.python.org/3/library/asyncio.html)
[![License](https://img.shields.io/github/license/ibm/mcp-context-forge)](LICENSE)&nbsp;
[![PyPI](https://img.shields.io/pypi/v/mcp-contextforge-gateway)](https://pypi.org/project/mcp-contextforge-gateway/)&nbsp;
[![Docker Image](https://img.shields.io/badge/docker-ghcr.io%2Fibm%2Fmcp--context--forge-blue)](https://github.com/ibm/mcp-context-forge/pkgs/container/mcp-context-forge)&nbsp;

**ContextForge** 是一个开源注册表与代理，可将工具、智能体和 API 联邦到一个面向 AI 客户端的统一端点中。它为你的 AI 基础设施提供集中式治理、发现与可观测性：

- **Tools Gateway** — MCP、REST、gRPC-to-MCP 转换，以及 TOON 压缩
- **Agent Gateway** — A2A 协议、兼容 OpenAI 的智能体路由与 Anthropic 智能体路由
- **API Gateway** — 面向 REST 服务的限流、认证、重试与反向代理
- **Plugin Extensibility** — 40+ 插件，支持更多传输方式、协议与集成
- **Observability** — 基于 OpenTelemetry 的追踪，支持 Phoenix、Jaeger、Zipkin 及其他 OTLP 后端

它可作为完全兼容 MCP 的服务器运行，可通过 PyPI 或 Docker 部署，并可在 Kubernetes 上扩展到多集群环境，支持基于 Redis 的联邦与缓存。

![ContextForge](assets/002-contextforge-4d61701942.gif)
---

<!-- vscode-markdown-toc -->
## 目录

- [概览与目标](#overview--goals)
- [快速开始 - PyPI](#quick-start---pypi)
- [快速开始 - 容器](#quick-start---containers)
- [VS Code 开发容器](#quick-start-vs-code-dev-container)
- [安装](#installation)
- [升级](#upgrading)
- [配置](#configuration)
- [运行](#running)
- [云部署](#cloud-deployment)
- [API 参考](#api-reference)
- [测试](#testing)
- [项目结构](#project-structure)
- [开发](#development)
- [故障排查](#troubleshooting)
- [贡献](#contributing)

---

### 📌 快速链接

| 资源 | 说明 |
|----------|-------------|
| **[5-Minute Setup](https://github.com/IBM/mcp-context-forge/issues/2503)** | 快速上手：uvx、Docker、Compose 或本地开发 |
| **[Getting Help](https://github.com/IBM/mcp-context-forge/issues/2504)** | 支持渠道、常见问题与社区渠道 |
| **[Issue Guide](https://github.com/IBM/mcp-context-forge/issues/2502)** | 如何提交 bug、请求功能与参与贡献 |
| **[Full Documentation](https://ibm.github.io/mcp-context-forge/)** | 完整指南、教程与 API 参考 |

---

<a id="overview--goals"></a>
## 概览与目标

**ContextForge** 是一个开源注册表与代理，可联邦化任意 [Model Context Protocol](https://modelcontextprotocol.io)（MCP）服务器、A2A 服务器或 REST/gRPC API，并提供集中式治理、发现与可观测性。它可优化智能体与工具调用，并支持插件。更多细节请参见 [项目路线图](https://ibm.github.io/mcp-context-forge/architecture/roadmap/)。

它当前支持：

* 跨多个 MCP 与 REST 服务进行联邦
* 面向外部 AI 智能体（OpenAI、Anthropic、自定义）的 **A2A（Agent-to-Agent）集成**
* 通过基于反射的自动服务发现实现 **gRPC-to-MCP 转换**
* 将遗留 API 虚拟化为兼容 MCP 的工具与服务器
* 支持 HTTP、JSON-RPC、WebSocket、SSE（可配置 keepalive）、stdio 与 streamable-HTTP 传输
* 提供用于实时管理、配置和日志监控的管理 UI（支持 airgapped 部署）
* 内置认证、重试与限流，支持按用户范围划分的 OAuth 令牌以及无条件 `X-Upstream-Authorization` 请求头支持
* 基于 **OpenTelemetry 的可观测性**，支持 Phoenix、Jaeger、Zipkin 及其他 OTLP 后端
* 可通过 Docker 或 PyPI 扩展部署，支持基于 Redis 的缓存与多集群联邦

![ContextForge Architecture](assets/003-contextforge-architecture-dc6dc34e00.svg)

如需查看即将推出的功能列表，请参阅 [ContextForge Roadmap](https://ibm.github.io/mcp-context-forge/architecture/roadmap/)

---

<details>
<summary><strong>🔌 具备协议灵活性的网关层</strong></summary>

* 可联邦任意 MCP 服务器或 REST API
* 允许你选择 MCP 协议版本（例如 `2025-11-25`）
* 为多样化后端暴露单一统一接口

</details>

<details>
<summary><strong>🧩 REST/gRPC 服务虚拟化</strong></summary>

* 将非 MCP 服务封装为虚拟 MCP 服务器
* 以极少配置注册工具、提示词与资源
* 通过服务器反射协议实现 **gRPC-to-MCP 转换**
* 自动服务发现与方法自省

</details>

<details>
<summary><strong>🔁 REST-to-MCP 工具适配器</strong></summary>

* 将 REST API 适配为工具，并提供：

  * 自动提取 JSON Schema
  * 支持请求头、令牌与自定义认证
  * 重试、超时与限流策略

</details>

<details>
<summary><strong>🧠 统一注册表</strong></summary>

* **Prompts**：Jinja2 模板、多模态支持、回滚/版本管理
* **Resources**：基于 URI 的访问、MIME 检测、缓存、SSE 更新
* **Tools**：原生或适配型工具，带输入校验与并发控制

</details>

<details>
<summary><strong>📈 管理 UI、可观测性与开发体验</strong></summary>

* 基于 HTMX + Alpine.js 构建的管理 UI
* 支持过滤、搜索和导出的实时日志查看器
* 认证：Basic、JWT 或自定义方案
* 结构化日志、健康检查端点、指标
* 7,000+ 测试、Makefile 目标、实时重载、pre-commit hooks

</details>

<details>
<summary><strong>🔍 OpenTelemetry 可观测性</strong></summary>

* 通过 OpenTelemetry（OTLP）协议支持实现 **厂商无关的追踪**
* **多后端支持**：Phoenix（面向 LLM）、Jaeger、Zipkin、Tempo、DataDog、New Relic
* 跨联邦网关与服务的 **分布式追踪**
* 对工具、提示词、资源与网关操作进行 **自动插桩**
* **LLM 专属指标**：Token 用量、成本、模型性能
* **禁用时零额外开销**，并具备平滑降级能力

有关 Phoenix、Jaeger 及其他后端的设置指南，请参见 **[Observability Documentation](https://ibm.github.io/mcp-context-forge/manage/observability/)**。

</details>

---

<a id="quick-start---pypi"></a>
## 快速开始 - PyPI

ContextForge 已发布到 [PyPI](https://pypi.org/project/mcp-contextforge-gateway/)，包名为 `mcp-contextforge-gateway`。

---

**TLDR;**：
（使用 [uv](https://docs.astral.sh/uv/) 的单条命令）

```bash
# Quick start with environment variables
BASIC_AUTH_PASSWORD=pass \
MCPGATEWAY_UI_ENABLED=true \
MCPGATEWAY_ADMIN_API_ENABLED=true \
PLATFORM_ADMIN_EMAIL=admin@example.com \
PLATFORM_ADMIN_PASSWORD=changeme \
PLATFORM_ADMIN_FULL_NAME="Platform Administrator" \
uvx --from mcp-contextforge-gateway mcpgateway --host 0.0.0.0 --port 4444

# Or better: use the provided .env.example
cp .env.example .env
# Edit .env to customize your settings
uvx --from mcp-contextforge-gateway mcpgateway --host 0.0.0.0 --port 4444
```

<details>
<summary><strong>📋 前置条件</strong></summary>

* **Python ≥ 3.11**
* **curl + jq** - 仅用于最后的 smoke-test 步骤

</details>

### 1 - 安装并运行（可直接复制粘贴）

```bash
# 1️⃣  Isolated env + install from pypi
mkdir mcpgateway && cd mcpgateway
python3 -m venv .venv && source .venv/bin/activate
pip install --upgrade pip
pip install mcp-contextforge-gateway

# 2️⃣  Copy and customize the configuration
# Download the example environment file
curl -O https://raw.githubusercontent.com/IBM/mcp-context-forge/main/.env.example
cp .env.example .env
# Edit .env to customize your settings (especially passwords!)

# Or set environment variables directly:
export MCPGATEWAY_UI_ENABLED=true
export MCPGATEWAY_ADMIN_API_ENABLED=true
export PLATFORM_ADMIN_EMAIL=admin@example.com
export PLATFORM_ADMIN_PASSWORD=changeme
export PLATFORM_ADMIN_FULL_NAME="Platform Administrator"

BASIC_AUTH_PASSWORD=pass JWT_SECRET_KEY=my-test-key-but-now-longer-than-32-bytes \
  mcpgateway --host 0.0.0.0 --port 4444 &   # admin/pass

# 3️⃣  Generate a bearer token & smoke-test the API
export MCPGATEWAY_BEARER_TOKEN=$(python3 -m mcpgateway.utils.create_jwt_token \
    --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes)

curl -s -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     http://127.0.0.1:4444/version | jq
```

<details>
<summary><strong>Windows（PowerShell）快速开始</strong></summary>

```powershell
# 1️⃣  Isolated env + install from PyPI
mkdir mcpgateway ; cd mcpgateway
python3 -m venv .venv ; .\.venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install mcp-contextforge-gateway

# 2️⃣  Copy and customize the configuration
# Download the example environment file
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/IBM/mcp-context-forge/main/.env.example" -OutFile ".env.example"
Copy-Item .env.example .env
# Edit .env to customize your settings

# Or set environment variables (session-only)
$Env:MCPGATEWAY_UI_ENABLED        = "true"
$Env:MCPGATEWAY_ADMIN_API_ENABLED = "true"
# Note: Basic auth for API is disabled by default (API_ALLOW_BASIC_AUTH=false)
$Env:JWT_SECRET_KEY               = "my-test-key-but-now-longer-than-32-bytes"
$Env:PLATFORM_ADMIN_EMAIL         = "admin@example.com"
$Env:PLATFORM_ADMIN_PASSWORD      = "changeme"
$Env:PLATFORM_ADMIN_FULL_NAME     = "Platform Administrator"

# 3️⃣  Launch the gateway
mcpgateway.exe --host 0.0.0.0 --port 4444

#   Optional: background it
# Start-Process -FilePath "mcpgateway.exe" -ArgumentList "--host 0.0.0.0 --port 4444"

# 4️⃣  Bearer token and smoke-test
$Env:MCPGATEWAY_BEARER_TOKEN = python3 -m mcpgateway.utils.create_jwt_token `
    --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes

curl -s -H "Authorization: Bearer $Env:MCPGATEWAY_BEARER_TOKEN" `
     http://127.0.0.1:4444/version | jq
```

<details>
<summary><strong>⚡ 备选方案：uv（更快）</strong></summary>

```powershell
# 1️⃣  Isolated env + install from PyPI using uv
mkdir mcpgateway ; cd mcpgateway
uv venv
.\.venv\Scripts\activate
uv pip install mcp-contextforge-gateway

# Continue with steps 2️⃣-4️⃣ above...
```

</details>

</details>

<details>
<summary><strong>更多配置</strong></summary>

将 [.env.example](https://github.com/IBM/mcp-context-forge/blob/main/.env.example) 复制为 `.env`，并调整任意设置项（或将其作为环境变量使用）。

</details>

<details>
<summary><strong>🚀 端到端演示（注册一个本地 MCP 服务器）</strong></summary>

```bash
# 1️⃣  Spin up the sample GO MCP time server using mcpgateway.translate & docker (replace docker with podman if needed)
python3 -m mcpgateway.translate \
     --stdio "docker run --rm -i ghcr.io/ibm/fast-time-server:latest -transport=stdio" \
     --expose-sse \
     --port 8003

# Or using the official mcp-server-git using uvx:
pip install uv # to install uvx, if not already installed
python3 -m mcpgateway.translate --stdio "uvx mcp-server-git" --expose-sse --port 9000

# Alternative: running the local binary
# cd mcp-servers/go/fast-time-server; make build
# python3 -m mcpgateway.translate --stdio "./dist/fast-time-server -transport=stdio" --expose-sse --port 8002

# NEW: Expose via multiple protocols simultaneously!
python3 -m mcpgateway.translate \
     --stdio "uvx mcp-server-git" \
     --expose-sse \
     --expose-streamable-http \
     --port 9000
# Now accessible via both /sse (SSE) and /mcp (streamable HTTP) endpoints

# 2️⃣  Register it with the gateway
curl -s -X POST -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"name":"fast_time","url":"http://localhost:8003/sse"}' \
     http://localhost:4444/gateways

# 3️⃣  Verify tool catalog
curl -s -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" http://localhost:4444/tools | jq

# 4️⃣  Create a *virtual server* bundling those tools. Use the ID of tools from the tool catalog (Step #3) and pass them in the associatedTools list.
curl -s -X POST -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"server":{"name":"time_server","description":"Fast time tools","associated_tools":[<ID_OF_TOOLS>]}}' \
     http://localhost:4444/servers | jq

# Example curl
curl -s -X POST -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN"
     -H "Content-Type: application/json"
     -d '{"server":{"name":"time_server","description":"Fast time tools","associated_tools":["6018ca46d32a4ac6b4c054c13a1726a2"]}}' \
     http://localhost:4444/servers | jq

# 5️⃣  List servers (should now include the UUID of the newly created virtual server)
curl -s -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" http://localhost:4444/servers | jq

# 6️⃣  Client HTTP endpoint. Inspect it interactively with the MCP Inspector CLI (or use any MCP client)
npx -y @modelcontextprotocol/inspector
# Transport Type: Streamable HTTP, URL: http://localhost:4444/servers/UUID_OF_SERVER_1/mcp,  Header Name: "Authorization", Bearer Token
```

</details>

<details>
<summary><strong>🖧 使用 stdio 包装器（mcpgateway-wrapper）</strong></summary>

```bash
export MCP_AUTH="Bearer ${MCPGATEWAY_BEARER_TOKEN}"
export MCP_SERVER_URL=http://localhost:4444/servers/UUID_OF_SERVER_1/mcp
python3 -m mcpgateway.wrapper  # Ctrl-C to exit
```

你也可以配合 `uv` 运行，或在 Docker/Podman 中运行，详见上面的“容器”小节。

在 MCP Inspector 中，定义 `MCP_AUTH` 和 `MCP_SERVER_URL` 环境变量，并将 `python3` 设为命令，将 `-m mcpgateway.wrapper` 设为参数。

```bash
echo $PWD/.venv/bin/python3 # Using the Python3 full path ensures you have a working venv
export MCP_SERVER_URL='http://localhost:4444/servers/UUID_OF_SERVER_1/mcp'
export MCP_AUTH="Bearer ${MCPGATEWAY_BEARER_TOKEN}"
npx -y @modelcontextprotocol/inspector
```

或者

将 URL 和认证信息作为参数传入（无需设置环境变量）
```bash
npx -y @modelcontextprotocol/inspector
命令填写为 `python`
参数填写为 `-m mcpgateway.wrapper --url "http://localhost:4444/servers/UUID_OF_SERVER_1/mcp" --auth "Bearer <your token>"`
```

当你在 Claude 等使用 stdio 的 MCP Client 中使用时：

```json
{
  "mcpServers": {
    "mcpgateway-wrapper": {
      "command": "python",
      "args": ["-m", "mcpgateway.wrapper"],
      "env": {
        "MCP_AUTH": "Bearer your-token-here",
        "MCP_SERVER_URL": "http://localhost:4444/servers/UUID_OF_SERVER_1",
        "MCP_TOOL_CALL_TIMEOUT": "120"
      }
    }
  }
}
```

</details>

---

<a id="quick-start---containers"></a>
## 快速开始 - 容器

使用来自 GHCR 的官方 OCI 镜像，支持 **Docker** 或 **Podman**。
请注意：当前生产环境不支持 arm64。比如你在搭载 Apple Silicon 芯片（M1、M2 等）的 macOS 上运行时，可以通过 Rosetta 运行容器，或者改为通过 PyPI 安装。

### 🚀 快速开始 - Docker Compose

在 30 秒内启动包含 PostgreSQL 与 Redis 的完整栈：

```bash
# Clone and start the stack
git clone https://github.com/IBM/mcp-context-forge.git
cd mcp-context-forge

# Start with PostgreSQL (recommended for production)
docker compose up -d

# Check status
docker compose ps

# View logs
docker compose logs -f gateway

# Access Admin UI: http://localhost:8080/admin (login with PLATFORM_ADMIN_EMAIL/PASSWORD)
# Generate API token
docker compose exec gateway python3 -m mcpgateway.utils.create_jwt_token \
  --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes
```

**你将获得：**
- 🗄️ **PostgreSQL** - 具备生产可用性的数据库，包含 55+ 张表
- 🚀 **ContextForge** - 带管理 UI 的完整功能网关
- 📊 **Redis** - 高性能缓存与会话存储
- 🔧 **Admin Tools** - 用于数据库管理的 pgAdmin、Redis Insight
- 🌐 **Nginx Proxy** - 运行在 8080 端口上的缓存反向代理

**启用 HTTPS（可选）：**
```bash
# Start with TLS enabled (auto-generates self-signed certs)
make compose-tls

# Access via HTTPS: https://localhost:8443/admin

# Or bring your own certificates:
# Unencrypted key:
mkdir -p certs
cp your-cert.pem certs/cert.pem && cp your-key.pem certs/key.pem
make compose-tls

# Passphrase-protected key:
mkdir -p certs
cp your-cert.pem certs/cert.pem && cp your-encrypted-key.pem certs/key-encrypted.pem
echo "KEY_FILE_PASSWORD=your-passphrase" >> .env
make compose-tls
```

### ☸️ 快速开始 - Helm（Kubernetes）

使用企业级特性部署到 Kubernetes：

```bash
# Add Helm repository (when available)
# helm repo add mcp-context-forge https://ibm.github.io/mcp-context-forge
# helm repo update

# For now, use local chart
git clone https://github.com/IBM/mcp-context-forge.git
cd mcp-context-forge/charts/mcp-stack

# Install with PostgreSQL (default)
helm install mcp-gateway . \
  --set mcpContextForge.secret.PLATFORM_ADMIN_EMAIL=admin@yourcompany.com \
  --set mcpContextForge.secret.PLATFORM_ADMIN_PASSWORD=changeme \
  --set mcpContextForge.secret.JWT_SECRET_KEY=your-secret-key

# Check deployment status
kubectl get pods -l app.kubernetes.io/name=mcp-context-forge

# Port forward to access Admin UI
kubectl port-forward svc/mcp-gateway-mcp-context-forge 4444:80
# Access: http://localhost:4444/admin

# Generate API token
kubectl exec deployment/mcp-gateway-mcp-context-forge -- \
  python3 -m mcpgateway.utils.create_jwt_token \
  --username admin@yourcompany.com --exp 10080 --secret your-secret-key
```

> SSRF 说明：Helm 默认启用严格的 SSRF 设置（`SSRF_ALLOW_PRIVATE_NETWORKS=false`）。
> 如果你要注册集群内的工具 URL（例如 fast-time 或 fast-test 服务），
> 请仅通过 `mcpContextForge.config.SSRF_ALLOWED_NETWORKS` 放行你的集群 CIDR；或者，
> 对于仅限本地的基准测试环境，可临时设置 `SSRF_ALLOW_PRIVATE_NETWORKS=true`。
> 详见 `docs/docs/manage/configuration.md#ssrf-protection` 与 `docs/docs/deployment/helm.md`。

**企业特性：**
- 🔄 **自动扩缩容** - 基于 CPU/内存目标的 HPA
- 🗄️ **数据库选项** - PostgreSQL（生产）、SQLite（开发）
- 📊 **可观测性** - Prometheus 指标、OpenTelemetry 追踪
- 🔒 **安全性** - RBAC、网络策略、密钥管理
- 🚀 **高可用** - 基于 Redis 集群的多副本部署
- 📈 **监控** - 内置 Grafana 仪表板与告警

---

### 🐳 Docker（单容器）

```bash
docker run -d --name mcpgateway \
  -p 4444:4444 \
  -e MCPGATEWAY_UI_ENABLED=true \
  -e MCPGATEWAY_ADMIN_API_ENABLED=true \
  -e HOST=0.0.0.0 \
  -e JWT_SECRET_KEY=my-test-key-but-now-longer-than-32-bytes \
  -e AUTH_REQUIRED=true \
  -e PLATFORM_ADMIN_EMAIL=admin@example.com \
  -e PLATFORM_ADMIN_PASSWORD=changeme \
  -e PLATFORM_ADMIN_FULL_NAME="Platform Administrator" \
  -e DATABASE_URL=sqlite:///./mcp.db \
  -e SECURE_COOKIES=false \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2

# Tail logs and generate API key
docker logs -f mcpgateway
docker run --rm -it ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2 \
  python3 -m mcpgateway.utils.create_jwt_token --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes
```

访问 **[http://localhost:4444/admin](http://localhost:4444/admin)**，并使用 `PLATFORM_ADMIN_EMAIL` / `PLATFORM_ADMIN_PASSWORD` 登录。

<details>
<summary><strong>高级：持久化存储、宿主机网络、隔离网络部署</strong></summary>

**持久化 SQLite 数据库：**
```bash
mkdir -p $(pwd)/data && touch $(pwd)/data/mcp.db && chmod 777 $(pwd)/data
docker run -d --name mcpgateway --restart unless-stopped \
  -p 4444:4444 -v $(pwd)/data:/data \
  -e DATABASE_URL=sqlite:////data/mcp.db \
  -e MCPGATEWAY_UI_ENABLED=true -e MCPGATEWAY_ADMIN_API_ENABLED=true \
  -e HOST=0.0.0.0 -e JWT_SECRET_KEY=my-test-key-but-now-longer-than-32-bytes \
  -e PLATFORM_ADMIN_EMAIL=admin@example.com -e PLATFORM_ADMIN_PASSWORD=changeme \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2
```

**宿主机网络**（访问本地 MCP 服务器）：
```bash
docker run -d --name mcpgateway --network=host \
  -v $(pwd)/data:/data -e DATABASE_URL=sqlite:////data/mcp.db \
  -e MCPGATEWAY_UI_ENABLED=true -e HOST=0.0.0.0 -e PORT=4444 \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2
```

**隔离网络部署**（无互联网）：
```bash
docker build -f Containerfile.lite -t mcpgateway:airgapped .
docker run -d --name mcpgateway -p 4444:4444 \
  -e MCPGATEWAY_UI_AIRGAPPED=true -e MCPGATEWAY_UI_ENABLED=true \
  -e HOST=0.0.0.0 -e JWT_SECRET_KEY=my-test-key-but-now-longer-than-32-bytes \
  mcpgateway:airgapped
```

</details>

---

### 🦭 Podman（对 rootless 更友好）

```bash
podman run -d --name mcpgateway \
  -p 4444:4444 -e HOST=0.0.0.0 -e DATABASE_URL=sqlite:///./mcp.db \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2
```

<details>
<summary><strong>高级：持久化存储、宿主机网络</strong></summary>

**持久化 SQLite：**
```bash
mkdir -p $(pwd)/data && chmod 777 $(pwd)/data
podman run -d --name mcpgateway --restart=on-failure \
  -p 4444:4444 -v $(pwd)/data:/data \
  -e DATABASE_URL=sqlite:////data/mcp.db \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2
```

**宿主机网络：**
```bash
podman run -d --name mcpgateway --network=host \
  -v $(pwd)/data:/data -e DATABASE_URL=sqlite:////data/mcp.db \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2
```

</details>

---

<details>
<summary><strong>✏️ Docker/Podman 使用提示</strong></summary>

* **.env 文件** - 将所有 `-e FOO=` 行放入一个文件中，然后用 `--env-file .env` 替代。可参考提供的 [.env.example](https://github.com/IBM/mcp-context-forge/blob/main/.env.example)。
* **固定标签** - 使用显式版本（例如 `1.0.0-RC-2`）而不是 `latest`，以获得可复现的构建。
* **JWT 令牌** - 在运行中的容器内生成：

  ```bash
  docker exec mcpgateway python3 -m mcpgateway.utils.create_jwt_token --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes
  ```
* **升级** - 停止、删除并用同样的 `-v $(pwd)/data:/data` 挂载重新运行；你的数据库和配置会保留。

</details>

---

<details>
<summary><strong>🚑 对运行中的容器进行 smoke-test</strong></summary>

```bash
curl -s -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     http://localhost:4444/health | jq
curl -s -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     http://localhost:4444/tools | jq
curl -s -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     http://localhost:4444/version | jq
```

</details>

---

<details>
<summary><strong>🖧 运行 ContextForge stdio 包装器</strong></summary>

`mcpgateway.wrapper` 允许你在保留 JWT 认证的同时，通过 **stdio** 连接到网关。你应当从 MCP Client 中运行它。下面的示例仅用于测试。

```bash
# Set environment variables
export MCPGATEWAY_BEARER_TOKEN=$(python3 -m mcpgateway.utils.create_jwt_token --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes)
export MCP_AUTH="Bearer ${MCPGATEWAY_BEARER_TOKEN}"
export MCP_SERVER_URL='http://localhost:4444/servers/UUID_OF_SERVER_1/mcp'
export MCP_TOOL_CALL_TIMEOUT=120
export MCP_WRAPPER_LOG_LEVEL=DEBUG  # or OFF to disable logging

docker run --rm -i \
  -e MCP_AUTH=$MCP_AUTH \
  -e MCP_SERVER_URL=http://host.docker.internal:4444/servers/UUID_OF_SERVER_1/mcp \
  -e MCP_TOOL_CALL_TIMEOUT=120 \
  -e MCP_WRAPPER_LOG_LEVEL=DEBUG \
  ghcr.io/ibm/mcp-context-forge:1.0.0-RC-2 \
  python3 -m mcpgateway.wrapper
```

</details>

---

<a id="quick-start-vs-code-dev-container"></a>
## 快速开始：VS Code 开发容器

克隆仓库并在 VS Code 中打开，编辑器会检测到 `.devcontainer`，并提示你 **“Reopen in Container”**。该容器内含 Python 3.11、Docker CLI 以及全部项目依赖。

有关详细设置、工作流以及 GitHub Codespaces 指南，请参见 **[Developer Onboarding](https://ibm.github.io/mcp-context-forge/development/developer-onboarding/)**。

---

<a id="installation"></a>
## 安装

```bash
make venv install          # create .venv + install deps
make serve                 # gunicorn on :4444
```

<details>
<summary><strong>备选方案：UV 或 pip</strong></summary>

```bash
# UV (faster)
uv venv && source .venv/bin/activate
uv pip install -e '.[dev]'

# pip
python3 -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
```

</details>

<details>
<summary><strong>PostgreSQL 适配器设置</strong></summary>

安装 PostgreSQL 的 `psycopg` 驱动：

```bash
# Install system dependencies first
# Debian/Ubuntu: sudo apt-get install libpq-dev
# macOS: brew install libpq

uv pip install 'psycopg[binary]'   # dev (pre-built wheels)
# or: uv pip install 'psycopg[c]'  # production (requires compiler)
```

连接 URL 格式：
```bash
DATABASE_URL=postgresql+psycopg://user:password@localhost:5432/mcp
```

快速启动 Postgres 容器：
```bash
docker run --name mcp-postgres \
  -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=mysecretpassword \
  -e POSTGRES_DB=mcp -p 5432:5432 -d postgres
```

</details>

---

<a id="upgrading"></a>
## 升级

有关升级说明、迁移指南与回滚流程，请参见：

- **[Upgrade Guide](https://ibm.github.io/mcp-context-forge/manage/upgrade/)** — 通用升级流程
- **[CHANGELOG.md](./CHANGELOG.md)** — 版本历史与破坏性变更
- **[MIGRATION-0.7.0.md](./MIGRATION-0.7.0.md)** — 多租户迁移（v0.6.x → v0.7.x）

---

<a id="configuration"></a>
## 配置

> ⚠️ 如果任何必需的 `.env` 变量缺失或无效，网关会在启动时通过 Pydantic 抛出校验错误并立即失败。

将提供的 [.env.example](https://github.com/IBM/mcp-context-forge/blob/main/.env.example) 复制为 `.env`，并更新下列安全敏感值。

### 🔐 必需：使用前必须修改

这些变量具有不安全的默认值，在部署到生产环境前 **必须修改**：

| 变量 | 说明 | 默认值 | 必需操作 |
|----------|-------------|---------|-----------------|
| `JWT_SECRET_KEY` | 用于签名 JWT 令牌的密钥（32+ 字符） | `my-test-key-but-now-longer-than-32-bytes` | 用 `openssl rand -hex 32` 生成 |
| `AUTH_ENCRYPTION_SECRET` | 用于加密已存储凭据的口令 | `my-test-salt` | 用 `openssl rand -hex 32` 生成 |
| `BASIC_AUTH_USER` | HTTP Basic 认证用户名 | `admin` | 在生产环境中修改 |
| `BASIC_AUTH_PASSWORD` | HTTP Basic 认证密码 | `changeme` | 设置强密码 |
| `PLATFORM_ADMIN_EMAIL` | 初始管理员用户邮箱 | `admin@example.com` | 使用真实管理员邮箱 |
| `PLATFORM_ADMIN_PASSWORD` | 初始管理员用户密码 | `changeme` | 设置强密码 |
| `PLATFORM_ADMIN_FULL_NAME` | 初始管理员显示名称 | `Admin User` | 设置管理员名称 |

### 🔒 安全默认值（默认安全）

出于安全考虑，这些设置默认启用，仅应在需要兼容旧行为时关闭：

| 变量 | 说明 | 默认值 |
|----------|-------------|---------|
| `REQUIRE_JTI` | 要求令牌中包含 JTI 声明，以支持撤销 | `true` |
| `REQUIRE_TOKEN_EXPIRATION` | 要求令牌中包含 exp 声明 | `true` |
| `PUBLIC_REGISTRATION_ENABLED` | 允许公开的用户自助注册 | `false` |

### 🛡️ 内容安全

内容大小限制可防止 DoS 攻击，并确保系统稳定性：

| 变量 | 说明 | 默认值 |
|----------|-------------|---------|
| `CONTENT_MAX_RESOURCE_SIZE` | 资源内容最大大小（字节） | `102400`（100KB） |
| `CONTENT_MAX_PROMPT_SIZE` | 提示模板最大大小（字节） | `10240`（10KB） |

**注意：** 大小限制仅适用于新的创建/更新操作；已有内容不会被追溯校验。

### ⚙️ 项目默认值（开发环境设置）

这些值与代码默认值不同，用于提供一个可工作的本地/开发环境设置：

| 变量 | 说明 | 默认值 |
|----------|-------------|---------|
| `HOST` | 绑定地址 | `0.0.0.0` |
| `MCPGATEWAY_UI_ENABLED` | 启用管理 UI 仪表板 | `true` |
| `MCPGATEWAY_ADMIN_API_ENABLED` | 启用管理 API 端点 | `true` |
| `DATABASE_URL` | SQLAlchemy 连接 URL | `sqlite:///./mcp.db` |
| `SECURE_COOKIES` | 在 HTTP（非 HTTPS）开发环境中设为 `false` | `false` |

### 📚 完整配置参考

如需查看按类别组织的 300+ 个环境变量完整列表（认证、缓存、SSO、可观测性等），请参见 **[Configuration Reference](https://ibm.github.io/mcp-context-forge/manage/configuration/)**。

---

<a id="running"></a>
## 运行

### 快速参考

| 命令 | 服务器 | 端口 | 数据库 | 使用场景 |
|---------|--------|------|----------|----------|
| `make dev` | Uvicorn | **8000** | SQLite | 开发（单实例、自动重载） |
| `make serve` | Gunicorn | **4444** | SQLite | 生产单节点（多 worker） |
| `make serve-ssl` | Gunicorn | **4444** | SQLite | 启用 HTTPS 的生产单节点 |
| `make compose-up` | Docker Compose + Nginx | **8080** | PostgreSQL + Redis | 完整栈（3 副本、负载均衡） |
| `make compose-sso` | Docker Compose + Keycloak | **8080 / 8180** | PostgreSQL + Redis | 本地 SSO 测试（Keycloak profile） |
| `make testing-up` | Docker Compose + Nginx | **8080** | PostgreSQL + Redis | 测试环境 |

### 开发服务器（Uvicorn）

```bash
make dev                 # Uvicorn on :8000 with auto-reload and SQLite
# or
./run.sh --reload --log debug --workers 2
```

> `run.sh` 是对 `uvicorn` 的封装，会加载 `.env`、支持热重载，并将参数传给服务器。

关键参数：

| 参数             | 用途             | 示例               |
| ---------------- | ---------------- | ------------------ |
| `-e, --env FILE` | 加载 env 文件    | `--env prod.env`   |
| `-H, --host`     | 绑定地址         | `--host 127.0.0.1` |
| `-p, --port`     | 监听端口         | `--port 8080`      |
| `-w, --workers`  | gunicorn worker 数 | `--workers 4`    |
| `-r, --reload`   | 自动重载         | `--reload`         |

### 生产服务器（Gunicorn）

```bash
make serve               # Gunicorn on :4444 with multiple workers
make serve-ssl           # Gunicorn behind HTTPS on :4444 (uses ./certs)
```

### Docker Compose（完整栈）

```bash
make compose-up          # Start full stack: PostgreSQL, Redis, 3 gateway replicas, Nginx on :8080
make compose-sso         # Start SSO stack with Keycloak on :8180
make sso-test-login      # Run SSO smoke checks (providers + login URL + test users)
make compose-logs        # Tail logs from all services
make compose-down        # Stop the stack
```

### 手动运行（Uvicorn）

```bash
uvicorn mcpgateway.main:app --host 0.0.0.0 --port 4444 --workers 4
```

---

<a id="cloud-deployment"></a>
## 云部署

ContextForge 可部署到任意主流云平台：

| 平台 | 指南 |
|----------|-------|
| **AWS** | [ECS/EKS Deployment](https://ibm.github.io/mcp-context-forge/deployment/aws/) |
| **Azure** | [AKS Deployment](https://ibm.github.io/mcp-context-forge/deployment/azure/) |
| **Google Cloud** | [Cloud Run](https://ibm.github.io/mcp-context-forge/deployment/google-cloud-run/) |
| **IBM Cloud** | [Code Engine](https://ibm.github.io/mcp-context-forge/deployment/ibm-code-engine/) |
| **Kubernetes** | [Helm Charts](https://ibm.github.io/mcp-context-forge/deployment/minikube/) |
| **OpenShift** | [OpenShift Deployment](https://ibm.github.io/mcp-context-forge/deployment/openshift/) |

有关完整部署指南，请参见 **[Deployment Documentation](https://ibm.github.io/mcp-context-forge/deployment/)**。

---

<a id="api-reference"></a>
## API 参考

服务器运行后，可使用交互式 API 文档：

- **[Swagger UI](http://localhost:4444/docs)** — 直接在浏览器中试用 API 调用
- **[ReDoc](http://localhost:4444/redoc)** — 浏览完整端点参考

**快速认证：**
```bash
# Generate a JWT token
export TOKEN=$(python3 -m mcpgateway.utils.create_jwt_token \
  --username admin@example.com --exp 10080 --secret my-test-key-but-now-longer-than-32-bytes)

# Test API access
curl -H "Authorization: Bearer $TOKEN" http://localhost:4444/health
```

有关覆盖所有端点的完整 curl 示例，请参见 **[API Usage Guide](https://ibm.github.io/mcp-context-forge/manage/api-usage/)**。

---

<a id="testing"></a>
## 测试

```bash
make test            # Run unit tests
make lint            # Run all linters
make doctest         # Run doctests
make coverage        # Generate coverage report
```

有关文档测试细节，请参见 [Doctest Coverage Guide](https://ibm.github.io/mcp-context-forge/development/doctest-coverage/)。

---

<a id="project-structure"></a>
## 项目结构

```
mcpgateway/          # Core FastAPI application
├── main.py          # Entry point
├── config.py        # Pydantic Settings configuration
├── db.py            # SQLAlchemy ORM models
├── schemas.py       # Pydantic validation schemas
├── services/        # Business logic layer (50+ services)
├── routers/         # HTTP endpoint definitions
├── middleware/      # Cross-cutting concerns
└── transports/      # SSE, WebSocket, stdio, streamable HTTP

tests/               # Test suite (7,000+ tests)
docs/docs/           # Full documentation (MkDocs)
charts/              # Kubernetes/Helm charts
plugins/             # Plugin framework and implementations
mcp-servers/         # Sample/test MCP servers (see note below)
```

> **注意：** `mcp-servers/` 目录包含**不受支持的示例与测试服务器**，
> 其中大多数来自社区贡献，仅用于演示和集成测试。
> 它们通常缺少会话管理、持久化状态、多租户、认证以及其他生产级关注点。
> 它们不会经历与 ContextForge 核心代码库相同级别的审查、测试与安全严格性，因此
> **不应在生产环境中运行**。
>
> **安全性：** 永远不要直接在本地文件系统上运行不受信任的 MCP 服务器。
> 始终使用带受限能力的沙箱、容器或 microVM（例如 gVisor、Firecracker）。
> 注册任何远程 MCP 服务器时也应保持谨慎，包括公共目录中的服务器。
> 在授予其访问网关的权限前，请先自行完成安全评估。

如需查看完整结构，请参见 [CONTRIBUTING.md](./CONTRIBUTING.md) 或运行 `tree -L 2`。

---

<a id="development"></a>
## 开发

```bash
make dev             # Dev server with auto-reload (:8000)
make test            # Run test suite
make lint            # Run all linters
make coverage        # Generate coverage report
```

运行 `make` 可查看所有可用目标。

有关开发工作流，请参见：
- **[Developer Workstation Setup](https://ibm.github.io/mcp-context-forge/development/developer-workstation/)**
- **[Building & Packaging](https://ibm.github.io/mcp-context-forge/development/building/)**

---

<a id="troubleshooting"></a>
## 故障排查

常见问题与解决方案：

| 问题 | 快速修复 |
|-------|-----------|
| macOS 上 SQLite 报错 “disk I/O error” | 避免使用 iCloud 同步目录；改用 `~/mcp-context-forge/data` |
| 在 WSL2 上无法访问 4444 端口 | 在 Docker Desktop 中配置 WSL 集成 |
| 网关启动后立即退出 | 将 `.env.example` 复制为 `.env` 并配置必需变量 |
| `ModuleNotFoundError` | 运行 `make install-dev` |

有关详细故障排查指南，请参见 **[Troubleshooting Documentation](https://ibm.github.io/mcp-context-forge/manage/troubleshooting/)**。

---

<a id="contributing"></a>
## 贡献

1. Fork 该仓库，并创建功能分支。
2. 运行 `make lint` 并修复所有问题。
3. 保持 `make test` 通过。
4. 使用签名提交打开 PR（`git commit -s`）。

完整指南请参见 **[CONTRIBUTING.md](CONTRIBUTING.md)**；有关如何提交 bug、请求功能和查找可处理 issue，请参见 **[Issue Guide #2502](https://github.com/IBM/mcp-context-forge/issues/2502)**。

---

## 变更日志

完整变更日志见：[CHANGELOG.md](./CHANGELOG.md)

## 许可证

基于 **Apache License 2.0** 许可发布，详见 [LICENSE](./LICENSE)

## 核心作者与维护者

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai) - 杰出工程师，Agentic AI

特别感谢各位贡献者帮助我们持续改进 ContextForge：

<a href="https://github.com/ibm/mcp-context-forge/graphs/contributors">
  <img src="assets/005-image-f60f2c04ca.svg" alt="mcp-context-forge 仓库的贡献者" />
</a>

## Star 历史与项目活跃度

[![Star History Chart](assets/004-star-history-chart-39639bab21.svg)](https://www.star-history.com/#ibm/mcp-context-forge&Date)

<!-- === Usage Stats === -->
[![PyPi Downloads](https://static.pepy.tech/badge/mcp-contextforge-gateway/month)](https://pepy.tech/project/mcp-contextforge-gateway)&nbsp;
[![Stars](https://img.shields.io/github/stars/ibm/mcp-context-forge?style=social)](https://github.com/ibm/mcp-context-forge/stargazers)&nbsp;
[![Forks](https://img.shields.io/github/forks/ibm/mcp-context-forge?style=social)](https://github.com/ibm/mcp-context-forge/network/members)&nbsp;
[![Contributors](https://img.shields.io/github/contributors/ibm/mcp-context-forge)](https://github.com/ibm/mcp-context-forge/graphs/contributors)&nbsp;
[![Last Commit](https://img.shields.io/github/last-commit/ibm/mcp-context-forge)](https://github.com/ibm/mcp-context-forge/commits)&nbsp;
[![Open Issues](https://img.shields.io/github/issues/ibm/mcp-context-forge)](https://github.com/ibm/mcp-context-forge/issues)&nbsp;
