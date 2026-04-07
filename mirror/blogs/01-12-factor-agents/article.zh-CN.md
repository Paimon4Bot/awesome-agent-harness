# 12 Factor Agents

基于 GitHub 上的 12 Factor Agents 原始文章。*秉承 12 Factor Apps 的精神。*

## 引言

我试过市面上所有的 agent 框架——从即插即用的 crew/langchains，到"极简主义"的 smolagents，再到"生产级"的 langraph、griptape 等等。

我和很多非常优秀的创始人聊过，YC 内外的都有，他们都在用 AI 打造令人印象深刻的产品。他们大多数人都在自己从零构建技术栈。我没有看到太多框架被用在面向客户的生产级 agent 中。

我惊讶地发现，市面上大多数标榜自己为"AI Agent"的产品，其实并没有那么"agentic"。它们很大程度上是确定性代码，只是在恰到好处的位置点缀了一些 LLM 步骤，让体验变得真正神奇。

Agent——至少那些优秀的 agent——并不遵循"给你一个提示词，给你一堆工具，循环直到达成目标"的模式。相反，它们主要由软件构成。

所以，我着手回答一个问题：

> **我们可以用哪些原则来构建足够好的、可以交付给生产用户的 LLM 驱动软件？**

![Image 26: 1c5-agent-foldl](assets/001-image-26-1c5-agent-foldl-6da98fe38b.png)

## 目录

* 我们是如何走到这里的：软件简史
* 因素 1：自然语言到工具调用
* 因素 2：掌控你的提示词
* 因素 3：掌控你的上下文窗口
* 因素 4：工具即结构化输出
* 因素 5：统一执行状态与业务状态
* 因素 6：用简单 API 实现 Launch/Pause/Resume
* 因素 7：通过工具调用联系人类
* 因素 8：掌控你的控制流
* 因素 9：将错误压缩进上下文窗口
* 因素 10：小型、专注的 Agent
* 因素 11：从任意位置触发
* 因素 12：让你的 Agent 成为无状态 Reducer

---

## 我们是如何走到这里的：软件简史

### 你不必听我的

无论你是 agent 领域的新手，还是像我一样的老顽固，我将试图说服你抛弃你对 AI Agent 的大部分认知，退后一步，从第一性原理重新思考它们。（剧透一下，如果你没有注意到几周前 OpenAI 发布的 responses，在 API 后面塞入更多 agent 逻辑并不是正道。）

## Agent 就是软件，以及其简史

让我们来聊聊我们是如何走到今天的

### 60 年前

我们将大量讨论有向图（DG）及其无环变体 DAG。我首先要指出的是……嗯……软件就是一个有向图。我们以前用流程图来表示程序是有原因的。

### 20 年前

大约 20 年前，我们开始看到 DAG 编排器变得流行。这里说的是经典之作如 Airflow、Prefect 以及一些前身，还有一些更新的如 dagster、inggest、windmill。它们遵循相同的图模式，同时增加了可观测性、模块化、重试、管理等功能。

### 10-15 年前

当 ML 模型开始变得足够好、能够发挥作用时，我们开始看到 ML 模型被嵌入到 DAG 中。你可以想象类似"将该列中的文本摘要到新列"或"按严重程度或情感对支持工单进行分类"这样的步骤。

但归根结底，它仍然主要是相同的、经典的确定性软件。

### Agent 的承诺

我不是第一个这么说的人，但当我开始学习 agent 时，最大的收获是：你可以把 DAG 扔掉了。不需要软件工程师为每个步骤和边界情况编写代码，你可以给 agent 一个目标和一组转换：

让 LLM 实时做出决策来确定路径。

这里的承诺是你编写更少的软件，只需给 LLM 提供图的"边"，让它自己找出节点。你可以从错误中恢复，编写更少的代码，而且你可能会发现 LLM 能找到解决问题的新颖方案。

### Agent 即循环

换个说法，你有一个由 3 个步骤组成的循环：

1. LLM 确定工作流中的下一步，输出结构化 JSON（"tool calling"）
2. 确定性代码执行工具调用
3. 结果被追加到上下文窗口
4. 重复，直到下一步被确定为"完成"

```
initial_event = {"message": "..."}
context = [initial_event]

while True:
  next_step = await llm.determine_next_step(context)
  context.append(next_step)
  if (next_step.intent === "done"):
    return next_step.final_answer
  result = await execute_step(next_step)
  context.append(result)
```

我们的初始上下文只是起始事件（可能是用户消息，可能是 cron 触发，可能是 webhook 等），然后我们让 LLM 选择下一步（工具）或确定是否已完成。

这是一个多步骤的例子：

而生成的"具象化"DAG 大致如下：

### "循环直到解决"模式的问题

这种模式最大的问题在于：

* 当上下文窗口变得太长时，agent 会迷失方向——它们会一遍又一遍地尝试同样失效的方法
* 说实话就这一个问题，但这足以让整个方法跛脚

即使你没有手搓过 agent，你在使用 agent 编程工具时可能也见过这种长上下文问题。过一阵子它们就会迷失方向，你需要重新开一个对话。

我甚至想大胆提出一个我经常听到、而且你可能也已经形成了自己直觉的观点：

> ### **即使模型支持越来越长的上下文窗口，使用小型、聚焦的提示词和上下文，你总是能获得更好的结果**

我交谈过的大多数构建者在意识到超过 10-20 轮交互就会变成 LLM 无法恢复的一团糟后，**把"工具调用循环"的想法推到了一边**。即使 agent 在 90% 的情况下都能做对，这也与"好到可以交付给客户"相距甚远。你能想象一个网页应用在 10% 的页面加载时崩溃吗？

### 真正有效的方法——微型 agent

我在实践中确实看到的一种模式是，将 agent 模式嵌入到更广泛的、更具确定性的 DAG 中。

你可能会问——"这种情况下为什么还要用 agent？"——我们很快会讨论这个问题，但基本上，让语言模型管理范围明确的任务集，可以轻松融入实时的人类反馈，将其转换为工作流步骤，而不会陷入上下文错误的循环。

> #### 让语言模型管理范围明确的任务集，可以轻松融入实时的人类反馈……而不会陷入上下文错误的循环

### 一个真实的微型 agent

这里有一个例子，展示确定性代码如何运行一个负责处理部署中人机交互步骤的微型 agent。

* **人类** 将 PR 合并到 GitHub main 分支
* **确定性代码** 部署到 staging 环境
* **确定性代码** 对 staging 运行端到端（e2e）测试
* **确定性代码** 将任务交给 agent 进行生产部署，初始上下文为："deploy SHA 4af9ec0 to production"
* **Agent** 调用 `deploy_frontend_to_prod(4af9ec0)`
* **确定性代码** 请求人类对该操作进行审批
* **人类** 拒绝该操作，并反馈"你能先部署后端吗？"
* **Agent** 调用 `deploy_backend_to_prod(4af9ec0)`
* **确定性代码** 请求人类对该操作进行审批
* **人类** 批准该操作
* **确定性代码** 执行后端部署
* **Agent** 调用 `deploy_frontend_to_prod(4af9ec0)`
* **确定性代码** 请求人类对该操作进行审批
* **人类** 批准该操作
* **确定性代码** 执行前端部署
* **Agent** 判断任务已成功完成，搞定！
* **确定性代码** 对生产环境运行端到端测试
* **确定性代码** 任务完成，或者传递给回滚 agent 来审查失败并可能执行回滚

这个例子基于我们在 Humanlayer 已经开源的一个管理部署的真实 agent——下面是我上周与它的真实对话：

我们没有给这个 agent 一大堆工具或任务。LLM 的核心价值在于解析人类的纯文本反馈并提出更新的行动方案。我们尽可能地隔离任务和上下文，让 LLM 专注于一个小型的 5-10 步工作流。

### 那么 agent 到底是什么？

* **提示词 (prompt)** — 告诉 LLM 如何行为，以及它有哪些可用的"工具"。提示词的输出是一个描述工作流下一步的 JSON 对象（即"工具调用"或"函数调用"）。
* **switch 语句** — 基于 LLM 返回的 JSON，决定如何处理它。
* **累积的上下文** — 存储已发生的步骤列表及其结果
* **for 循环** — 直到 LLM 发出某种"终止"工具调用（或纯文本响应），将 switch 语句的结果添加到上下文窗口，并让 LLM 选择下一步。

在"部署机器人"的例子中，通过掌控控制流和上下文累积，我们获得了几个好处：

* 在我们的 **switch 语句**和 **for 循环**中，我们可以劫持控制流来暂停等待人类输入或等待长时间运行的任务完成
* 我们可以轻松地将 **上下文** 窗口序列化以实现暂停+恢复
* 在我们的 **提示词** 中，我们可以尽情优化如何将指令和"到目前为止发生了什么"传递给 LLM

---

## 因素 1：自然语言到工具调用

Agent 构建中最常见的模式之一是将自然语言转换为结构化的工具调用。这是一种强大的模式，让你能够构建可以推理任务并执行它们的 agent。

这种模式在原子层面上的应用，就是将如下短语进行简单翻译

> 能否为 Terri 创建一个 750 美元的支付链接，用于赞助二月的 AI Tinkerers 聚会？

转换为一个描述 Stripe API 调用的结构化对象，如

```json
{
  "function": {
    "name": "create_payment_link",
    "parameters": {
      "amount": 750,
      "customer": "cust_128934ddasf9",
      "product": "prod_8675309",
      "price": "prc_09874329fds",
      "quantity": 1,
      "memo": "Hey Jeff - see below for the payment link for the february ai tinkerers meetup"
    }
  }
}
```

**注意**：实际上 Stripe API 比这更复杂，一个真正执行此操作的 agent（视频）会先列出客户、列出产品、列出价格等来构建带有正确 ID 的 payload，或者将这些 ID 包含在提示词/上下文窗口中（我们下面会看到这些在某种程度上其实是同一回事！）

接下来，确定性代码可以获取 payload 并对其进行处理。

```python
# LLM 接收自然语言并返回结构化对象
nextStep = await llm.determineNextStep("""
  create a payment link for $750 to Jeff
  for sponsoring the february AI tinkerers meetup
""")

# 根据函数类型处理结构化输出
if nextStep.function == 'create_payment_link':
  stripe.paymentlinks.create(nextStep.parameters)
  return # 或者做任何你想做的事，见下文
elif nextStep.function == 'something_else':
  # ... 更多情况
  pass
else: # 模型调用了一个我们不知道的工具
  # 做其他事情
  pass
```

**注意**：虽然一个完整的 agent 接下来会收到 API 调用的结果并继续循环，最终返回类似这样的内容

> 我已成功为 Terri 创建了一个 750 美元的支付链接，用于赞助二月的 AI Tinkerers 聚会。链接如下：https://buy.stripe.com/test_1234567890

**但在这里**，我们实际上要跳过这一步，把它留到另一个因素中讨论——你可能想、也可能不想将其纳入（由你决定！）

---

## 因素 2：掌控你的提示词

不要把你的提示词工程外包给框架。

顺便说一句，这远非什么新奇的建议：

一些框架提供了这样的"黑盒"方式：

```python
agent = Agent(
  role="...",
  goal="...",
  personality="...",
  tools=[tool1, tool2, tool3]
)

task = Task(
  instructions="...",
  expected_output=OutputModel
)

result = agent.run(task)
```

这对于引入一些顶级的提示词工程来快速上手来说很好，但通常难以调优和/或逆向工程，以将恰好正确的 token 输入到你的模型中。

相反，掌控你的提示词，把它们当作一等公民的代码来对待：

```
function DetermineNextStep(thread: string) -> DoneForNow | ListGitTags | DeployBackend | DeployFrontend | RequestMoreInformation {
  prompt #"
    {{ _.role("system") }}
    You are a helpful assistant that manages deployments for frontend and backend systems.
    You work diligently to ensure safe and successful deployments by following best practices
    and proper deployment procedures.

    Before deploying any system, you should check:
    - The deployment environment (staging vs production)
    - The correct tag/version to deploy
    - The current system status

    You can use tools like deploy_backend, deploy_frontend, and check_deployment_status
    to manage deployments. For sensitive deployments, use request_approval to get
    human verification.

    Always think about what to do first, like:
    - Check current deployment status
    - Verify the deployment tag exists
    - Request approval if needed
    - Deploy to staging before production
    - Monitor deployment progress

    {{ _.role("user") }}
    {{ thread }}
    What should the next step be?
  "#
}
```

（上面的例子使用 BAML 来生成提示词，但你可以使用任何提示词工程工具，甚至手动编写模板）

如果函数签名看起来有点奇怪，我们会在因素 4 中讨论——工具即结构化输出

`function DetermineNextStep(thread: string) -> DoneForNow | ListGitTags | DeployBackend | DeployFrontend | RequestMoreInformation {`

掌控提示词的核心好处：

1. **完全控制**：精确编写你的 agent 需要的指令，没有黑盒抽象
2. **测试与评估**：像对待任何其他代码一样，为你的提示词构建测试和评估
3. **快速迭代**：根据实际表现快速修改提示词
4. **透明性**：确切知道你的 agent 在使用什么指令
5. **角色黑客**：利用支持非标准使用 user/assistant 角色的 API——例如，现已弃用的 OpenAI "completions" API 的非聊天风格。这包括一些所谓的"模型心理暗示"技术

记住：你的提示词是应用逻辑与 LLM 之间的主要接口。

完全掌控你的提示词，能为你提供构建生产级 agent 所需的灵活性和提示词控制能力。

我不知道什么是最好的提示词，但我知道你需要能够尝试一切的灵活性。

---

## 因素 3：掌控你的上下文窗口

你不必使用标准的基于消息的格式来向 LLM 传达上下文。

> #### 在任意给定时刻，你在 agent 中对 LLM 的输入就是"到目前为止发生了什么，下一步是什么"

一切都是上下文工程。LLM 是将输入转化为输出的无状态函数。要获得最好的输出，你需要给它们最好的输入。

创建优秀的上下文意味着：

* 你给模型的提示词和指令
* 你检索的任何文档或外部数据（例如 RAG）
* 任何过去的状态、工具调用、结果或其他历史
* 来自相关但独立的历史/对话的任何过去消息或事件（Memory）
* 关于输出什么类型结构化数据的指令

### 关于上下文工程

本指南的核心是尽可能充分利用当今的模型。特别值得注意的是，以下内容并未被提及：

* 修改模型参数，如 temperature、top_p、frequency_penalty、presence_penalty 等
* 训练你自己的补全或嵌入模型
* 微调现有模型

再次强调，我不知道什么是向 LLM 传递上下文的最佳方式，但我知道你需要能够尝试一切的灵活性。

#### 标准上下文格式 vs 自定义上下文格式

大多数 LLM 客户端使用标准的基于消息的格式，如下所示：

```json
[
  { 'role': 'system', 'content': 'You are a helpful assistant...' },
  { 'role': 'user', 'content': 'Can you deploy the backend?' },
  {
    'role': 'assistant',
    'content': null,
    'tool_calls': [{ 'id': '1', 'name': 'list_git_tags', 'arguments': '{}' }],
  },
  {
    'role': 'tool',
    'name': 'list_git_tags',
    'content': '{"tags": [{"name": "v1.2.3", "commit": "abc123", "date": "2024-03-15T10:00:00Z"}, {"name": "v1.2.2", "commit": "def456", "date": "2024-03-14T15:30:00Z"}, {"name": "v1.2.1", "commit": "abe033d", "date": "2024-03-13T09:15:00Z"}]}',
    'tool_call_id': '1',
  },
]
```

虽然这对大多数用例来说效果很好，但如果你想真正最大限度地利用当今的 LLM，你需要以最高效的 token 和注意力方式将上下文传递给 LLM。

作为标准消息格式的替代方案，你可以构建针对你的用例优化的自定义上下文格式。例如，你可以使用自定义对象，并根据需要将它们打包/展开到一个或多个 user、system、assistant 或 tool 消息中。

下面是将整个上下文窗口放入单条 user 消息的例子：

```json
[
  {
    "role": "system",
    "content": "You are a helpful assistant..."
  },
  {
    "role": "user",
    "content": |
      Here's everything that happened so far:

      From: @alex
      Channel: #deployments
      Text: Can you deploy the backend?

      intent: "list_git_tags"

      tags:
      - name: "v1.2.3"
        commit: "abc123"
        date: "2024-03-15T10:00:00Z"
      - name: "v1.2.2"
        commit: "def456"
        date: "2024-03-14T15:30:00Z"
      - name: "v1.2.1"
        commit: "ghi789"
        date: "2024-03-13T09:15:00Z"

      what's the next step?
  }
]
```

模型可能会通过你提供的工具 schema 推断出你在要求它确定下一步，但将其纳入你的提示词模板总是有益的。

### 代码示例

我们可以用类似这样的方式来构建：

```python
class Thread:
  events: List[Event]

class Event:
  # 可以直接使用 string，也可以更明确 —— 由你决定
  type: Literal["list_git_tags", "deploy_backend", "deploy_frontend", "request_more_information", "done_for_now", "list_git_tags_result", "deploy_backend_result", "deploy_frontend_result", "request_more_information_result", "done_for_now_result", "error"]
  data: ListGitTags | DeployBackend | DeployFrontend | RequestMoreInformation |
    ListGitTagsResult | DeployBackendResult | DeployFrontendResult | RequestMoreInformationResult | string

def event_to_prompt(event: Event) -> str:
  data = event.data if isinstance(event.data, str) \
    else stringifyToYaml(event.data)
  return f"<{event.type}>\n{data}\n"

def thread_to_prompt(thread: Thread) -> str:
  return '\n\n'.join(event_to_prompt(event) for event in thread.events)
```

#### 上下文窗口示例

使用这种方法，上下文窗口可能如下所示：

**初始 Slack 请求：**

```
From: @alex
Channel: #deployments
Text: Can you deploy the latest backend to production?
```

**列出 Git Tags 后：**

```
From: @alex
Channel: #deployments
Text: Can you deploy the latest backend to production?
Thread: []

intent: "list_git_tags"

tags:
- name: "v1.2.3"
  commit: "abc123"
  date: "2024-03-15T10:00:00Z"
- name: "v1.2.2"
  commit: "def456"
  date: "2024-03-14T15:30:00Z"
- name: "v1.2.1"
  commit: "ghi789"
  date: "2024-03-13T09:15:00Z"
```

**错误和恢复后：**

```
From: @alex
Channel: #deployments
Text: Can you deploy the latest backend to production?
Thread: []

intent: "deploy_backend"
tag: "v1.2.3"
environment: "production"

error running deploy_backend: Failed to connect to deployment service

intent: "request_more_information_from_human"
question: "I had trouble connecting to the deployment service, can you provide more details and/or check on the status of the service?"

data:
response: "I'm not sure what's going on, can you check on the status of the latest workflow?"
```

从这里开始，你的下一步可能是：

`nextStep = await determine_next_step(thread_to_prompt(thread))`

```json
{
  "intent": "get_workflow_status",
  "workflow_name": "tag_push_prod.yaml",
}
```

XML 风格的格式只是一个例子——关键在于你可以构建自己的、适合你应用的格式。如果你有灵活性去实验不同的上下文结构，以及决定存储什么与传递什么给 LLM，你会获得更好的质量。

掌控上下文窗口的核心好处：

1. **信息密度**：以最大化 LLM 理解的方式组织信息
2. **错误处理**：以帮助 LLM 恢复的格式包含错误信息。考虑在错误和失败的调用解决后将其从上下文窗口中隐藏
3. **安全性**：控制传递给 LLM 的信息，过滤掉敏感数据
4. **灵活性**：随着你了解什么对你的用例最有效，调整格式
5. **Token 效率**：优化上下文格式以提升 token 效率和 LLM 理解

上下文包括：提示词、指令、RAG 文档、历史、工具调用、记忆

记住：上下文窗口是你与 LLM 的主要接口。掌控你如何组织和呈现信息，可以大幅提升 agent 的性能。

### 不必只听我的

在 12 Factor Agents 发布大约两个月后，上下文工程开始成为一个相当流行的术语。

@lenadroid 在 2025 年 7 月还发布了一份相当不错的 Context Engineering Cheat Sheet。

这里反复出现的主题是：我不知道什么是最好的方法，但我知道你需要能够尝试一切的灵活性。

---

## 因素 4：工具即结构化输出

工具不需要很复杂。从根本上说，它们只是 LLM 的结构化输出，用于触发确定性代码。

例如，假设你有两个工具 `CreateIssue` 和 `SearchIssues`。要求 LLM"使用多个工具中的一个"，其实就是要求它输出我们可以解析为表示那些工具的对象的 JSON。

```python
class Issue:
  title: str
  description: str
  team_id: str
  assignee_id: str

class CreateIssue:
  intent: "create_issue"
  issue: Issue

class SearchIssues:
  intent: "search_issues"
  query: str
  what_youre_looking_for: str
```

这个模式很简单：

1. LLM 输出结构化 JSON
2. 确定性代码执行适当的操作（如调用外部 API）
3. 结果被捕获并反馈回上下文

这在 LLM 的决策制定和你的应用操作之间创建了清晰的分离。LLM 决定做什么，但你的代码控制怎么做。LLM"调用了一个工具"并不意味着你必须每次以完全相同的方式去执行特定的对应函数。

如果你回想我们上面的 switch 语句

```python
if nextStep.intent == 'create_payment_link':
  stripe.paymentlinks.create(nextStep.parameters)
  return # 或者做任何你想做的事，见下文
elif nextStep.intent == 'wait_for_a_while':
  # 做一些 monadic 的事，idk
else: #... 模型调用了一个我们不知道的工具
  # 做其他事情
```

**注意**：关于"纯提示词"vs."工具调用"vs."JSON 模式"以及各自的性能权衡，已经有很多讨论。我们很快会链接一些相关资源，但这里不展开讨论。参见 Prompting vs JSON Mode vs Function Calling vs Constrained Generation vs SAP, When should I use function calling, structured outputs, or JSON mode? 以及 OpenAI JSON vs Function Calling。

"下一步"可能并不像"运行一个纯函数并返回结果"那么原子化。当你把"工具调用"仅仅看作模型输出 JSON 来描述确定性代码应该做什么时，你就能解锁大量灵活性。将此与因素 8 掌控你的控制流结合起来。

---

## 因素 5：统一执行状态与业务状态

即使在 AI 领域之外，许多基础设施系统也试图将"执行状态"与"业务状态"分离。对于 AI 应用来说，这可能涉及复杂的抽象来跟踪当前步骤、下一步、等待状态、重试计数等。这种分离增加了复杂性，可能是值得的，但对你的用例来说也可能是不必要的。

一如既往，由你来决定什么适合你的应用。但不要认为你 _必须_ 分开管理它们。

更清楚地说：

* **执行状态**：当前步骤、下一步、等待状态、重试计数等。
* **业务状态**：Agent 工作流中到目前为止发生了什么（例如 OpenAI 消息列表、工具调用和结果列表等）

如果可能的话，**简化**——尽可能统一它们。

实际上，你可以设计你的应用，使得你能够从上下文窗口推断出所有执行状态。在很多情况下，执行状态（当前步骤、等待状态等）只是"到目前为止发生了什么"的元数据。

你可能有一些无法放入上下文窗口的东西，比如 session ID、密码上下文等，但你的目标应该是尽量减少这些东西。通过拥抱因素 3，你可以控制实际传递给 LLM 的内容

这种方法有几个好处：

1. **简洁性**：所有状态的唯一真相来源
2. **序列化**：线程可以轻松地序列化/反序列化
3. **调试**：整个历史在一个地方清晰可见
4. **灵活性**：只需添加新的事件类型就能轻松添加新状态
5. **恢复**：只需加载线程就能从任意点恢复
6. **分叉**：可以通过将线程的某个子集复制到新上下文/状态 ID 来在任意点分叉
7. **人机界面与可观测性**：可以轻松地将线程转换为人类可读的 markdown 或丰富的 Web 应用 UI

---

## 因素 6：用简单 API 实现 Launch/Pause/Resume

Agent 就是程序，我们对如何启动、查询、恢复和停止它们有一定的期望。

用户、应用、流水线和其他 agent 应该能够通过简单的 API 来启动一个 agent。

Agent 及其编排的确定性代码应该能够在需要长时间运行的操作时暂停 agent。

像 webhook 这样的外部触发应该能够让 agent 从中断的地方恢复，而无需与 agent 编排器深度集成。

这与因素 5——统一执行状态与业务状态以及因素 8——掌控你的控制流密切相关，但可以独立实现。

**注意** — AI 编排器通常允许暂停和恢复，但不能在工具选择和工具执行之间进行暂停。另见因素 7——通过工具调用联系人类和因素 11——从任意位置触发，在用户所在的地方触达他们。

---

## 因素 7：通过工具调用联系人类

默认情况下，LLM API 依赖于一个关键的高风险 token 选择：我们是返回纯文本内容，还是返回结构化数据？

你把很多权重放在第一个 token 的选择上。在"东京的天气"的情况下，它是

> "the"

但在 `fetch_weather` 的情况下，它是某个表示 JSON 对象开始的特殊 token。

> |JSON>

如果你让 LLM _始终_ 输出 JSON，然后用一些自然语言 token 来声明其意图（如 `request_human_input` 或 `done_for_now`，而不是像 `check_weather_in_city` 这样的"正经"工具），你可能会获得更好的结果。

再次强调，你未必能从中获得性能提升，但你应该去实验，确保你有自由去尝试各种奇特的方法来获得最佳结果。

```python
class Options:
  urgency: Literal["low", "medium", "high"]
  format: Literal["free_text", "yes_no", "multiple_choice"]
  choices: List[str]

# 用于人机交互的工具定义
class RequestHumanInput:
  intent: "request_human_input"
  question: str
  context: str
  options: Options

# 在 agent 循环中的使用示例
if nextStep.intent == 'request_human_input':
  thread.events.append({
    type: 'human_input_requested',
    data: nextStep
  })
  thread_id = await save_state(thread)
  await notify_human(nextStep, thread_id)
  return # 打断循环，等待带有 thread ID 的响应返回
else:
  # ... 其他情况
```

之后，你可能会从处理 Slack、电子邮件、SMS 或其他事件的系统收到一个 webhook。

```python
@app.post('/webhook')
def webhook(req: Request):
  thread_id = req.body.threadId
  thread = await load_state(thread_id)
  thread.events.push({
    type: 'response_from_human',
    data: req.body
  })
  # ... 为简洁起见做了简化，你可能不想在这里阻塞 web worker
  next_step = await determine_next_step(thread_to_prompt(thread))
  thread.events.append(next_step)
  result = await handle_next_step(thread, next_step)
  # todo - 循环或中断或做任何你想做的事
  return {"status": "ok"}
```

上述代码包含了来自因素 5——统一执行状态与业务状态、因素 8——掌控你的控制流、因素 3——掌控你的上下文窗口，以及因素 4——工具即结构化输出等多种模式。

如果我们使用因素 3——掌控你的上下文窗口中的 XML 风格格式，经过几轮交互后，我们的上下文窗口可能如下所示：

```
(为简洁起见已截断)
From: @alex
Channel: #deployments
Text: Can you deploy backend v1.2.3 to production?
Thread: []

intent: "request_human_input"
question: "Would you like to proceed with deploying v1.2.3 to production?"
context: "This is a production deployment that will affect live users."
options: {
  urgency: "high"
  format: "yes_no"
}

response: "yes please proceed"
approved: true
timestamp: "2024-03-15T10:30:00Z"
user: "alex@company.com"

intent: "deploy_backend"
tag: "v1.2.3"
environment: "production"

status: "success"
message: "Deployment v1.2.3 to production completed successfully."
timestamp: "2024-03-15T10:30:00Z"
```

好处：

1. **清晰的指令**：用于不同类型人机联系的工具使 LLM 能够提供更具体的指令
2. **内循环 vs 外循环**：支持传统 ChatGPT 风格界面 **之外** 的 agent 工作流，其中控制流和上下文初始化可能是 `Agent->Human` 而不是 `Human->Agent`（想想由 cron 或事件触发的 agent）
3. **多人类接入**：可以通过结构化事件轻松跟踪和协调来自不同人类的输入
4. **多 Agent**：简单的抽象可以轻松扩展以支持 `Agent->Agent` 的请求和响应
5. **持久性**：结合因素 6——用简单 API 实现 launch/pause/resume，可以构建持久的、可靠的、可内省的多方协作工作流

更多关于外循环 Agent 的内容请看这里

与因素 11——从任意位置触发配合得很好，在用户所在的地方触达他们

---

## 因素 8：掌控你的控制流

如果你掌控了控制流，你就能做很多有趣的事情。

构建适合你特定用例的自定义控制结构。具体来说，某些类型的工具调用可能是跳出循环、等待人类响应或等待其他长时间运行任务（如训练流水线）的理由。你可能还想加入以下自定义实现：

* 工具调用结果的摘要或缓存
* 对结构化输出使用 LLM-as-judge
* 上下文窗口压缩或其他内存管理
* 日志、追踪和指标
* 客户端限流
* 持久化休眠/暂停/"等待事件"

下面的例子展示了三种可能的控制流模式：

* request_clarification：模型请求更多信息，打断循环并等待人类响应
* fetch_git_tags：模型请求获取 git tags 列表，获取 tags，追加到上下文窗口，然后直接传回给模型
* deploy_backend：模型请求部署后端，这是一个高风险操作，所以打断循环等待人类审批

```python
def handle_next_step(thread: Thread):
  while True:
    next_step = await determine_next_step(thread_to_prompt(thread))

    # 为清晰起见内联了 —— 实际上你可以把
    # 这些放到方法中，用异常做控制流，或任何你想要的方式
    if next_step.intent == 'request_clarification':
      thread.events.append({
        type: 'request_clarification',
        data: nextStep,
      })
      await send_message_to_human(next_step)
      await db.save_thread(thread)
      # 异步步骤 —— 打断循环，稍后会收到 webhook
      break
    elif next_step.intent == 'fetch_open_issues':
      thread.events.append({
        type: 'fetch_open_issues',
        data: next_step,
      })
      issues = await linear_client.issues()
      thread.events.append({
        type: 'fetch_open_issues_result',
        data: issues,
      })
      # 同步步骤 —— 将新上下文传给 LLM 确定下下一步
      continue
    elif next_step.intent == 'create_issue':
      thread.events.append({
        type: 'create_issue',
        data: next_step,
      })
      await request_human_approval(next_step)
      await db.save_thread(thread)
      # 异步步骤 —— 打断循环，稍后会收到 webhook
      break
```

这种模式允许你根据需要中断和恢复 agent 的流程，创建更自然的对话和工作流。

**示例** — 对于市面上每一个 AI 框架，我最大的功能需求就是：我们需要能够中断一个正在工作的 agent 并在稍后恢复，尤其是在工具 **选择** 和工具 **执行** 之间。

如果没有这种级别的可恢复性/粒度，就无法在工具调用运行之前进行审查/审批，这意味着你被迫：

1. 在等待长时间运行的任务完成时，将任务暂停在内存中（想想 `while...sleep`），并在进程中断时从头重启
2. 将 agent 限制为只执行低风险、低影响的调用，如研究和摘要
3. 给 agent 访问更大、更有用操作的权限，然后祈祷它不会搞砸

你可能注意到这与因素 5——统一执行状态与业务状态以及因素 6——用简单 API 实现 launch/pause/resume 密切相关，但可以独立实现。

---

## 因素 9：将错误压缩进上下文窗口

这一条比较简短，但值得一提。Agent 的好处之一是"自我修复"——对于短任务，LLM 可能会调用一个失败的工具。优秀的 LLM 有相当大的概率能通过阅读错误消息或堆栈跟踪来弄清楚在后续工具调用中需要改变什么。

大多数框架都实现了这一点，但你可以只做这一件事而不实现其他 11 个因素中的任何一个。下面是一个例子：

```python
thread = {"events": [initial_message]}

while True:
  next_step = await determine_next_step(thread_to_prompt(thread))

  thread["events"].append({
    "type": next_step.intent,
    "data": next_step,
  })

  try:
    result = await handle_next_step(thread, next_step) # 我们的 switch 语句
  except Exception as e:
    # 如果遇到错误，可以将其添加到上下文窗口并重试
    thread["events"].append({
      "type": 'error',
      "data": format_error(e),
    })
    # 循环，或在这里做任何其他尝试恢复的操作
```

你可能想为特定工具调用实现一个 errorCounter，限制单个工具最多尝试约 3 次，或任何对你用例有意义的逻辑。

```python
consecutive_errors = 0

while True:
  # ... 已有代码 ...
  try:
    result = await handle_next_step(thread, next_step)
    thread["events"].append({
      "type": next_step.intent + '_result',
      "data": result,
    })
    # 成功！重置错误计数器
    consecutive_errors = 0
  except Exception as e:
    consecutive_errors += 1
    if consecutive_errors < 3:
      # 继续循环并重试
      thread["events"].append({
        "type": 'error',
        "data": format_error(e),
      })
    else:
      # 打断循环，重置部分上下文窗口，升级给人类，或做任何其他你想做的事
      break
  }
}
```

达到某个连续错误阈值可能是一个升级给人类的好时机，无论是通过模型决策还是通过确定性接管控制流。

好处：

1. **自我修复**：LLM 可以阅读错误消息并弄清楚在后续工具调用中需要改变什么
2. **持久性**：即使某个工具调用失败，agent 也能继续运行

我相信你会发现，如果过度使用这种方式，你的 agent 会开始失控，可能会一遍又一遍地重复同样的错误。

这就是因素 8——掌控你的控制流和因素 3——掌控你的上下文构建发挥作用的地方——你不需要只是把原始错误放回去，你可以完全重构它的表示方式，从上下文窗口中移除先前的事件，或任何你发现能让 agent 回到正轨的确定性方法。

但防止错误失控的首要方法是拥抱因素 10——小型、专注的 agent。

---

## 因素 10：小型、专注的 Agent

与其构建试图做所有事情的单体 agent，不如构建小型、专注的、做好一件事的 agent。Agent 只是一个更大的、主要是确定性的系统中的一个构建模块。

这里的洞察是关于 LLM 的局限性的：任务越大越复杂，需要的步骤就越多，这意味着更长的上下文窗口。随着上下文增长，LLM 更容易迷失方向或失去焦点。通过让 agent 专注于特定领域，将步骤控制在 3-10 步，最多也许 20 步，我们保持上下文窗口的可管理性和 LLM 性能的高水平。

> #### 随着上下文增长，LLM 更容易迷失方向或失去焦点

小型、专注的 agent 的好处：

1. **可管理的上下文**：更小的上下文窗口意味着更好的 LLM 性能
2. **清晰的职责**：每个 agent 有明确的范围和目的
3. **更高的可靠性**：在复杂工作流中迷失的可能性更低
4. **更容易测试**：更简单地测试和验证特定功能
5. **更好的调试**：更容易识别和修复发生的问题

### 如果 LLM 变得更聪明呢？

如果 LLM 变得足够智能来处理 100 步以上的工作流，我们还需要这样做吗？

简短回答：是的。随着 agent 和 LLM 的进步，它们 **可能** 会自然扩展到能够处理更长的上下文窗口。这意味着能够处理更大型 DAG 的更多部分。这种小型、专注的方法确保你能在 **今天** 获得结果，同时为随着 LLM 上下文窗口变得更可靠而逐步扩展 agent 范围做好准备。（如果你曾经重构过大型确定性代码库，你现在可能在点头。）

有意识地控制 agent 的大小/范围，并只以能维持质量的方式扩展，是这里的关键。正如构建 NotebookLM 的团队所说：

> 我感觉在 AI 构建过程中，最神奇的时刻始终出现在我非常、非常、非常接近模型能力边界的时候

无论那个边界在哪里，如果你能找到那个边界并持续做对，你就会构建出神奇的体验。这里可以建立很多护城河，但一如既往，它们需要一些工程严谨性。

---

## 因素 11：从任意位置触发

如果你一直在等 Humanlayer 的推介，你等到了。如果你已经实现了因素 6——用简单 API 实现 launch/pause/resume 和因素 7——通过工具调用联系人类，你就准备好纳入这个因素了。

让用户能够从 Slack、电子邮件、SMS 或他们想要的任何其他渠道触发 agent。让 agent 能够通过同样的渠道进行响应。

好处：

* **在用户所在的地方触达他们**：帮助你构建感觉像真人的 AI 应用，或者至少像是数字同事
* **外循环 Agent**：允许 agent 被非人类触发，例如事件、cron、故障等。它们可能工作 5、20、90 分钟，但当到达关键点时，它们可以联系人类寻求帮助、反馈或审批
* **高风险工具**：如果你能快速拉入各种人类参与，你就可以给 agent 访问更高风险操作的权限，比如发送外部邮件、更新生产数据等。维持清晰的标准能让你获得可审计性和信心，让 agent 执行更大、更好的操作

---

## 因素 12：让你的 Agent 成为无状态 Reducer

好了，到这里我们已经超过 1000 行 markdown 了。这一条主要是图个乐。

![1c0-stateless-reducer](https://github.com/humanlayer/12-factor-agents/blob/main/img/1c0-stateless-reducer.png)

![1c5-agent-foldl](https://github.com/humanlayer/12-factor-agents/blob/main/img/1c5-agent-foldl.png)
