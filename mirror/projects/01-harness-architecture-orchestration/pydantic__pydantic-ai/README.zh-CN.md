<div align="center">
  <a href="https://ai.pydantic.dev/">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/003-pydantic-ai-dark-d6f178a330.svg">
      <img src="assets/001-pydantic-ai-light-90adc6ec72.svg" alt="Pydantic AI">
    </picture>
  </a>
</div>
<div align="center">
  <h3>GenAI 代理框架，Pydantic 之道</h3>
</div>
<div align="center">
  <a href="https://github.com/pydantic/pydantic-ai/actions/workflows/ci.yml?query=branch%3Amain"><img src="https://github.com/pydantic/pydantic-ai/actions/workflows/ci.yml/badge.svg?event=push" alt="CI"></a>
  <a href="https://coverage-badge.samuelcolvin.workers.dev/redirect/pydantic/pydantic-ai"><img src="assets/002-pydantic-ai-1e33f64bd8.svg" alt="Coverage"></a>
  <a href="https://pypi.python.org/pypi/pydantic-ai"><img src="https://img.shields.io/pypi/v/pydantic-ai.svg" alt="PyPI"></a>
  <a href="https://github.com/pydantic/pydantic-ai"><img src="https://img.shields.io/pypi/pyversions/pydantic-ai.svg" alt="versions"></a>
  <a href="https://github.com/pydantic/pydantic-ai/blob/main/LICENSE"><img src="https://img.shields.io/github/license/pydantic/pydantic-ai.svg?v" alt="license"></a>
  <a href="https://logfire.pydantic.dev/docs/join-slack/"><img src="https://img.shields.io/badge/Slack-Join%20Slack-4A154B?logo=slack" alt="Join Slack" /></a>
</div>

---

**文档**: [ai.pydantic.dev](https://ai.pydantic.dev/)

---

### <em>Pydantic AI 是一个 Python 代理框架，旨在帮助你快速、自信、轻松地构建生产级的生成式 AI 应用和工作流。</em>

FastAPI 通过基于 [Pydantic Validation](https://docs.pydantic.dev) 和类型提示等现代 Python 特性打造的创新且符合人体工程学的设计，彻底改变了 Web 开发。

然而，尽管几乎所有 Python 代理框架和 LLM 库都在使用 Pydantic Validation，但当我们在 [Pydantic Logfire](https://pydantic.dev/logfire) 中开始使用 LLM 时，却找不到任何能带来同样体验的产品。

我们构建 Pydantic AI 只有一个简单的目标：将 FastAPI 的体验带到 GenAI 应用和代理开发领域。

## 为什么选择 Pydantic AI

1. **由 Pydantic 团队打造**:
[Pydantic Validation](https://docs.pydantic.dev/latest/) 是 OpenAI SDK、Google ADK、Anthropic SDK、LangChain、LlamaIndex、AutoGPT、Transformers、CrewAI、Instructor 等众多项目的验证层。_既然可以直接用源头，何必退而求其次？_ :smiley:

2. **模型无关**:
支持几乎所有[模型](https://ai.pydantic.dev/models/overview)和提供商：OpenAI、Anthropic、Gemini、DeepSeek、Grok、Cohere、Mistral 和 Perplexity；Azure AI Foundry、Amazon Bedrock、Google Vertex AI、Ollama、LiteLLM、Groq、OpenRouter、Together AI、Fireworks AI、Cerebras、Hugging Face、GitHub、Heroku、Vercel、Nebius、OVHcloud、Alibaba Cloud、SambaNova 和 Outlines。如果你喜欢的模型或提供商未在列表中，可以轻松实现[自定义模型](https://ai.pydantic.dev/models/overview#custom-models)。

3. **无缝可观测性**:
与我们的通用 OpenTelemetry 可观测性平台 [Pydantic Logfire](https://pydantic.dev/logfire) 紧密[集成](https://ai.pydantic.dev/logfire)，支持实时调试、基于评估的性能监控，以及行为分析、追踪和成本跟踪。如果你已有支持 OTel 的可观测性平台，也[可以使用它](https://ai.pydantic.dev/logfire#alternative-observability-backends)。

4. **完全类型安全**:
旨在为你的 IDE 或 AI 编码代理提供尽可能多的上下文信息，用于自动补全和[类型检查](https://ai.pydantic.dev/agents#static-type-checking)，将整类错误从运行时提前到编写时，让你体验类似 Rust 的"能编译就能运行"的感觉。

5. **强大的评估功能**:
支持系统化地测试和[评估](https://ai.pydantic.dev/evals)你构建的代理系统的性能和准确性，并在 Pydantic Logfire 中持续监控性能表现。

6. **为可扩展性而设计**:
通过可组合的[能力模块](https://ai.pydantic.dev/capabilities)构建代理，将工具、钩子、指令和模型设置打包为可复用单元。使用内置的[网页搜索](https://ai.pydantic.dev/capabilities#provider-adaptive-tools)、[思考](https://ai.pydantic.dev/capabilities#thinking)和 [MCP](https://ai.pydantic.dev/capabilities#provider-adaptive-tools) 能力，或构建自己的能力模块，或安装[第三方能力包](https://ai.pydantic.dev/extensibility)。完全使用 [YAML/JSON](https://ai.pydantic.dev/agent-spec) 定义代理——无需编写代码。

7. **MCP、A2A 和 UI**:
集成 [Model Context Protocol](https://ai.pydantic.dev/mcp/overview)、[Agent2Agent](https://ai.pydantic.dev/a2a) 以及各种 [UI 事件流](https://ai.pydantic.dev/ui/overview)标准，让你的代理能够访问外部工具和数据，与其他代理互操作，并通过基于流式事件的通信构建交互式应用。

8. **人在回路中的工具审批**:
轻松标记某些工具调用在执行前[需要审批](https://ai.pydantic.dev/deferred-tools#human-in-the-loop-tool-approval)，可根据工具调用参数、对话历史或用户偏好灵活控制。

9. **持久化执行**:
支持构建[持久化代理](https://ai.pydantic.dev/durable_execution/overview/)，能够在临时性 API 故障、应用错误或重启后保留进度，并以生产级可靠性处理长时间运行、异步和人在回路中的工作流。

10. **流式输出**:
支持持续[流式传输](https://ai.pydantic.dev/output#streamed-results)结构化输出，即时进行验证，确保实时访问生成数据。

11. **图支持**:
提供使用类型提示定义[图](https://ai.pydantic.dev/graph)的强大方式，适用于标准控制流可能退化为面条代码的复杂应用。

不过说实话，任何功能列表都不如[亲自试试](#next-steps)，看看它带来的实际体验，更有说服力！

## Hello World 示例

以下是 Pydantic AI 的最小示例：

```python
from pydantic_ai import Agent

# Define a very simple agent including the model to use, you can also set the model when running the agent.
agent = Agent(
    'anthropic:claude-sonnet-4-6',
    # Register static instructions using a keyword argument to the agent.
    # For more complex dynamically-generated instructions, see the example below.
    instructions='Be concise, reply with one sentence.',
)

# Run the agent synchronously, conducting a conversation with the LLM.
result = agent.run_sync('Where does "hello world" come from?')
print(result.output)
"""
The first known use of "hello, world" was in a 1974 textbook about the C programming language.
"""
```

_（此示例是完整的，可以"原样"运行，前提是你已[安装 `pydantic_ai` 包](https://ai.pydantic.dev/install)）_

这段交互非常简短：Pydantic AI 会将指令和用户提示词发送给 LLM，模型返回文本响应。

这还不够有趣，但我们可以轻松添加[工具](https://ai.pydantic.dev/tools)、[动态指令](https://ai.pydantic.dev/agents#instructions)、[结构化输出](https://ai.pydantic.dev/output)或可组合的[能力模块](https://ai.pydantic.dev/capabilities)来构建更强大的代理。

以下是添加了[思考](https://ai.pydantic.dev/capabilities#thinking)和[网页搜索](https://ai.pydantic.dev/capabilities#provider-adaptive-tools)能力的同一个代理：

```python
from pydantic_ai import Agent
from pydantic_ai.capabilities import Thinking, WebSearch

agent = Agent(
    'anthropic:claude-sonnet-4-6',
    instructions='Be concise, reply with one sentence.',
    capabilities=[Thinking(), WebSearch()],
)

result = agent.run_sync('What was the mass of the largest meteorite found this year?')
print(result.output)
```

## 工具与依赖注入示例

以下是一个使用 Pydantic AI 构建银行客服代理的简洁示例：

**（更详细的示例请参见[文档](https://ai.pydantic.dev/#tools-dependency-injection-example)）**

```python
from dataclasses import dataclass

from pydantic import BaseModel, Field
from pydantic_ai import Agent, RunContext

from bank_database import DatabaseConn

# SupportDependencies is used to pass data, connections, and logic into the model that will be needed when running
# instructions and tool functions. Dependency injection provides a type-safe way to customise the behavior of your agents.
@dataclass
class SupportDependencies:
    customer_id: int
    db: DatabaseConn

# This Pydantic model defines the structure of the output returned by the agent.
class SupportOutput(BaseModel):
    support_advice: str = Field(description='Advice returned to the customer')
    block_card: bool = Field(description="Whether to block the customer's card")
    risk: int = Field(description='Risk level of query', ge=0, le=10)

# This agent will act as first-tier support in a bank.
# Agents are generic in the type of dependencies they accept and the type of output they return.
# In this case, the support agent has type `Agent[SupportDependencies, SupportOutput]`.
support_agent = Agent(
    'openai:gpt-5.2',
    deps_type=SupportDependencies,
    # The response from the agent will, be guaranteed to be a SupportOutput,
    # if validation fails the agent is prompted to try again.
    output_type=SupportOutput,
    instructions=(
        'You are a support agent in our bank, give the '
        'customer support and judge the risk level of their query.'
    ),
)

# Dynamic instructions can make use of dependency injection.
# Dependencies are carried via the `RunContext` argument, which is parameterized with the `deps_type` from above.
# If the type annotation here is wrong, static type checkers will catch it.
@support_agent.instructions
async def add_customer_name(ctx: RunContext[SupportDependencies]) -> str:
    customer_name = await ctx.deps.db.customer_name(id=ctx.deps.customer_id)
    return f"The customer's name is {customer_name!r}"

# The `tool` decorator let you register functions which the LLM may call while responding to a user.
# Again, dependencies are carried via `RunContext`, any other arguments become the tool schema passed to the LLM.
# Pydantic is used to validate these arguments, and errors are passed back to the LLM so it can retry.
@support_agent.tool
async def customer_balance(
        ctx: RunContext[SupportDependencies], include_pending: bool
) -> float:
    """Returns the customer's current account balance."""
    # The docstring of a tool is also passed to the LLM as the description of the tool.
    # Parameter descriptions are extracted from the docstring and added to the parameter schema sent to the LLM.
    balance = await ctx.deps.db.customer_balance(
        id=ctx.deps.customer_id,
        include_pending=include_pending,
    )
    return balance

...  # In a real use case, you'd add more tools and a longer system prompt

async def main():
    deps = SupportDependencies(customer_id=123, db=DatabaseConn())
    # Run the agent asynchronously, conducting a conversation with the LLM until a final response is reached.
    # Even in this fairly simple case, the agent will exchange multiple messages with the LLM as tools are called to retrieve an output.
    result = await support_agent.run('What is my balance?', deps=deps)
    # The `result.output` will be validated with Pydantic to guarantee it is a `SupportOutput`. Since the agent is generic,
    # it'll also be typed as a `SupportOutput` to aid with static type checking.
    print(result.output)
    """
    support_advice='Hello John, your current account balance, including pending transactions, is $123.45.' block_card=False risk=1
    """

    result = await support_agent.run('I just lost my card!', deps=deps)
    print(result.output)
    """
    support_advice="I'm sorry to hear that, John. We are temporarily blocking your card to prevent unauthorized transactions." block_card=True risk=8
    """
```

## 下一步

要亲自体验 Pydantic AI，请[安装它](https://ai.pydantic.dev/install)并按照[示例说明](https://ai.pydantic.dev/examples/setup)操作。

阅读[文档](https://ai.pydantic.dev/agents/)以了解更多关于使用 Pydantic AI 构建应用的信息。

阅读 [API 参考](https://ai.pydantic.dev/api/agent/)以了解 Pydantic AI 的接口。

如有任何问题，请加入 [Slack](https://logfire.pydantic.dev/docs/join-slack/) 或在 [GitHub](https://github.com/pydantic/pydantic-ai/issues) 上提交 issue。
