<a href="./assets/WorkArena_banner.png">
  <img src="assets/001-workarena-banner-972c7f53ae.png" width="1000" />
</a>

# WorkArena：评估知识工作任务的代理基准测试
[[基准测试内容]](#基准测试内容) ♦ [[快速开始]](#快速开始) ♦ [[在线演示]](#在线演示) ♦ [[BrowserGym]](https://github.com/ServiceNow/BrowserGym) ♦ [[引用本文]](#引用本文) ♦ [加入我们的 Discord！](https://discord.gg/rDkP69X7)

---

### 探索 BrowserGym 生态系统

正在寻找更多工具和资源？请查看这些开源项目：

- **[AgentLab](https://github.com/ServiceNow/AgentLab)**
- **[BrowserGym](https://github.com/ServiceNow/BrowserGym)**

两者都是更广泛的 [BrowserGym 生态系统](https://arxiv.org/abs/2412.05467) 的一部分

### 论文
*  [ICML 2024] WorkArena：Web 代理在解决常见知识工作任务方面有多强？[[论文]](https://arxiv.org/abs/2403.07718)
 
*  [NeurIPS 2024] WorkArena++：面向组合规划与推理的常见知识工作任务 [[论文]](https://arxiv.org/abs/2407.05291)
 

`WorkArena` 是一套基于浏览器的任务，专门用于衡量 Web 代理在支持知识工作者日常任务方面的有效性。
借助被广泛使用的 [ServiceNow](https://www.servicenow.com/what-is-servicenow.html) 平台，该基准测试将有助于评估此类自动化在当今知识工作环境中的整体发展水平。

在 WorkArena 上进行评估的首选方式是使用 [AgentLab](https://github.com/ServiceNow/AgentLab/)，它将通过 [BrowserGym](https://github.com/ServiceNow/BrowserGym) 进行并行实验，并在[统一排行榜](https://huggingface.co/spaces/ServiceNow/browsergym-leaderboard)上报告结果。

https://github.com/ServiceNow/WorkArena/assets/2374980/68640f09-7d6f-4eb1-b556-c294a6afef70

## 快速开始

要设置 WorkArena，您需要获取 ServiceNow 实例的访问权限并在本地安装我们的 Python 包。请按照以下步骤操作。

### a) 获取 ServiceNow 实例访问权限

1. 访问 https://huggingface.co/datasets/ServiceNow/WorkArena-Instances。
2. 填写表单，接受条款以获取受限仓库的访问权限，然后等待审批。
3. 确保您将运行 WorkArena 的机器已[通过 Hugging Face 认证](https://huggingface.co/docs/hub/en/datasets-polars-auth)（例如，通过 huggingface-cli login 或 HUGGING_FACE_HUB_TOKEN 环境变量）。
4. 如果您是从之前的安装升级，请取消设置之前的 WorkArena 环境变量（`SNOW_INSTANCE_URL` 等）。

### b) 安装 WorkArena

运行以下命令在 [BrowswerGym](https://github.com/servicenow/browsergym) 环境中安装 WorkArena：
```
pip install browsergym-workarena
```

然后，安装 [Playwright](https://github.com/microsoft/playwright)：
```
playwright install
```

您的安装现已完成！🎉

## 基准测试内容

目前，WorkArena-L1 包含从 `33` 个任务中抽取的 `19,912` 个唯一实例，覆盖了 ServiceNow 用户界面的主要组件，这些组件也被称为“原子”任务。WorkArena++ 包含 682 个任务，每个任务都会从数千种潜在配置中采样。WorkArena++ 使用 WorkArena 中介绍的原子组件，并将它们组合成现实世界的使用场景，用于评估代理的规划、推理和记忆能力。

以下视频展示了一个基于 `GPT-4-vision` 构建的代理与基准测试中每个原子组件交互的过程。正如我们的结果所强调的，该基准测试尚未被攻克，因此该代理的表现并不总是理想。

### 知识库

**目标：** 代理必须在公司知识库中搜索特定信息。

_代理通过 BrowserGym 的对话界面与用户交互。_

https://github.com/ServiceNow/WorkArena/assets/1726818/352341ba-b501-46ac-bfa6-a6c9be1ac2b7

### 表单

**目标：** 代理必须用特定值填写一个复杂的表单。

https://github.com/ServiceNow/WorkArena/assets/1726818/e2c2b5cb-3386-4f3c-b073-c8c619e0e81b

### 服务目录

**目标：** 代理必须从公司的服务目录中订购具有特定配置的项目。

https://github.com/ServiceNow/WorkArena/assets/1726818/ac64db3b-9abf-4b5f-84a7-e2d9c9cee863

### 列表

**目标：** 代理必须根据某些规范筛选列表。

_在此示例中，代理在操作 UI 时遇到困难，未能创建筛选器。_

https://github.com/ServiceNow/WorkArena/assets/1726818/7538b3ef-d39b-4978-b9ea-8b9e106df28e

### 菜单

**目标：** 代理必须使用主菜单导航到特定应用程序。

https://github.com/ServiceNow/WorkArena/assets/1726818/ca26dfaf-2358-4418-855f-80e482435e6e

### 仪表板

**目标：** 代理必须回答一个需要读取图表并（可选）基于图表进行简单推理的问题。

*注意：出于演示目的，由人类控制光标，因为这是一个纯信息检索任务*

https://github.com/ServiceNow/WorkArena/assets/1726818/0023232c-081f-4be4-99bd-f60c766e6c3f

## 在线演示

运行以下代码以查看 WorkArena 的实际运行效果。

注意：以下示例执行 WorkArena 的 oracle（作弊）函数来解决每个任务。要评估代理，必须改用对 `env.step()` 的调用。

- 要使用 BrowserGym 运行 WorkArena-L1（ICML 2024）任务的演示，请使用以下脚本：
```python
import random

from browsergym.core.env import BrowserEnv
from browsergym.workarena import ATOMIC_TASKS
from time import sleep

random.shuffle(ATOMIC_TASKS)
for task in ATOMIC_TASKS:
    print("Task:", task)

    # Instantiate a new environment
    env = BrowserEnv(task_entrypoint=task,
                    headless=False)
    env.reset()

    # Cheat functions use Playwright to automatically solve the task
    env.chat.add_message(role="assistant", msg="On it. Please wait...")
    cheat_messages = []
    env.task.cheat(env.page, cheat_messages)

    # Send cheat messages to chat
    for cheat_msg in cheat_messages:
        env.chat.add_message(role=cheat_msg["role"], msg=cheat_msg["message"])

    # Post solution to chat
    env.chat.add_message(role="assistant", msg="I'm done!")

    # Validate the solution
    reward, stop, message, info = env.task.validate(env.page, cheat_messages)
    if reward == 1:
        env.chat.add_message(role="user", msg="Yes, that works. Thanks!")
    else:
        env.chat.add_message(role="user", msg=f"No, that doesn't work. {info.get('message', '')}")

    sleep(3)
    env.close()
```

- 要使用 BrowserGym 运行 WorkArena-L2（WorkArena++）任务的演示，请使用以下脚本。将第 6 行的 filter 更改为 `l3` 以采样 L3 任务。

```python
import random

from browsergym.core.env import BrowserEnv
from browsergym.workarena import get_all_tasks_agents
 
AGENT_L2_SAMPLED_SET = get_all_tasks_agents(filter="l2")
 
AGENT_L2_SAMPLED_TASKS, AGENT_L2_SEEDS = [sampled_set[0] for sampled_set in AGENT_L2_SAMPLED_SET], [
    sampled_set[1] for sampled_set in AGENT_L2_SAMPLED_SET
]
from time import sleep

for (task, seed) in zip(AGENT_L2_SAMPLED_TASKS, AGENT_L2_SEEDS):
    print("Task:", task)

    # Instantiate a new environment
    env = BrowserEnv(task_entrypoint=task,
                    headless=False)
    env.reset()

    # Cheat functions use Playwright to automatically solve the task
    env.chat.add_message(role="assistant", msg="On it. Please wait...")
    
    for i in range(len(env.task)):
        sleep(1)
        env.task.cheat(page=env.page, chat_messages=env.chat.messages, subtask_idx=i)
        sleep(1)
        reward, done, message, info = env.task.validate(page=env.page, chat_messages=env.chat.messages)
   
    if reward == 1:
        env.chat.add_message(role="user", msg="Yes, that works. Thanks!")
    else:
        env.chat.add_message(role="user", msg=f"No, that doesn't work. {info.get('message', '')}")

    sleep(3)
    env.close()
```

注意：以下示例执行 WorkArena 的 oracle（作弊）函数来解决每个任务。要评估代理，必须改用对 `env.step()` 的调用。

## 引用本文

请使用以下 BibTeX 引用我们的工作：

### WorkArena
```
@misc{workarena2024,
      title={WorkArena: How Capable Are Web Agents at Solving Common Knowledge Work Tasks?}, 
      author={Alexandre Drouin and Maxime Gasse and Massimo Caccia and Issam H. Laradji and Manuel Del Verme and Tom Marty and Léo Boisvert and Megh Thakkar and Quentin Cappart and David Vazquez and Nicolas Chapados and Alexandre Lacoste},
      year={2024},
      eprint={2403.07718},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```
### WorkArena++
```
@misc{boisvert2024workarenacompositionalplanningreasoningbased,
      title={WorkArena++: Towards Compositional Planning and Reasoning-based Common Knowledge Work Tasks}, 
      author={Léo Boisvert and Megh Thakkar and Maxime Gasse and Massimo Caccia and Thibault Le Sellier De Chezelles and Quentin Cappart and Nicolas Chapados and Alexandre Lacoste and Alexandre Drouin},
      year={2024},
      eprint={2407.05291},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2407.05291}, 
}
```
