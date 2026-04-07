# 通过评估系统地测试代理技能

## **1. 在编写技能之前定义成功标准**

在编写技能本身之前，先以可量化的方式写下"成功"的含义。一种实用的方法是将检查分为以下几个类别：

*   **结果目标：** 任务是否完成？应用能否运行？
*   **过程目标：** Codex 是否调用了该技能，并按照你设定的工具和步骤执行？
*   **风格目标：** 输出是否遵循你要求的约定？
*   **效率目标：** 是否在没有无效循环的情况下完成任务（例如，没有不必要的命令或过高的 token 消耗）？

保持这个列表精简，聚焦于必须通过的检查。目标不是预先编码所有偏好，而是捕获你最关心的行为。

例如，在本篇中，指南评估了一个用于搭建演示应用的技能。一些检查是具体的：是否运行了 `npm install`？是否创建了 `package.json`？指南将这些检查与结构化的风格评分标准配对，用于评估约定和布局。

这种组合是有意为之的。你需要快速、有针对性的信号来尽早发现具体的回归问题，而不是到最后才给出一个笼统的通过/失败判定。

## **2. 创建技能**

Codex 技能是一个包含 `SKILL.md` 文件的目录，该文件包含 YAML 前置信息（`name`、`description`），其后是定义技能行为的 Markdown 指令，以及可选的资源和脚本。名称和描述的重要性超出表面所见，它们是 Codex 用来决定 *是否* 调用技能以及 *何时* 将 `SKILL.md` 的其余内容注入代理上下文的主要信号。如果这些信息模糊或过于笼统，技能将无法可靠地触发。

最快的入门方式是使用 Codex 内置的技能创建器（[它本身也是一个技能](https://github.com/openai/skills/tree/main/skills/.system/skill-creator)）。它会引导你完成以下步骤：

`$skill-creator`
创建器会询问你技能的功能、触发时机，以及是纯指令型还是脚本支持型（默认推荐纯指令型）。要了解更多关于创建技能的信息，请[查看文档](https://developers.openai.com/codex/skills#create-a-skill)。

### **示例技能**

本篇使用了一个刻意简化的示例：一个以可预测、可重复的方式搭建小型 React 演示应用的技能。

该技能将：

*   使用 Vite 的 React + TypeScript 模板搭建项目
*   使用官方 Vite 插件方式配置 Tailwind CSS
*   强制使用最小化、一致的文件结构
*   定义明确的"完成标准"，使成功易于评估

以下是一个精简草稿，可以粘贴到：

*   `.codex/skills/setup-demo-app/SKILL.md`（仓库级别），或
*   `~/.codex/skills/setup-demo-app/SKILL.md`（用户级别）。

```
---
name: setup-demo-app
description: Scaffold a Vite + React + Tailwind demo app with a small, consistent project structure.
---

## When to use this

Use when you need a fresh demo app for quick UI experiments or reproductions.

## What to build

Create a Vite React TypeScript app and configure Tailwind. Keep it minimal.

Project structure after setup:

- src/
  - main.tsx (entry)
  - App.tsx (root UI)
  - components/
    - Header.tsx
    - Card.tsx
  - index.css (Tailwind import)
- index.html
- package.json

Style requirements:

- TypeScript components
- Functional components only
- Tailwind classes for styling (no CSS modules)
- No extra UI libraries

## Steps

1. Scaffold with Vite using the React TS template:
   npm create vite@latest demo-app -- --template react-ts

2. Install dependencies:
   cd demo-app
   npm install

3. Install and configure Tailwind using the Vite plugin.
   - npm install tailwindcss @tailwindcss/vite
   - Add the tailwind plugin to vite.config.ts
   - In src/index.css, replace contents with:
     @import "tailwindcss";

4. Implement the minimal UI:
   - Header: app title and short subtitle
   - Card: reusable card container
   - App: render Header + 2 Cards with placeholder text

## Definition of done

- npm run dev starts successfully
- package.json exists
- src/components/Header.tsx and src/components/Card.tsx exist
```

这个示例技能刻意采取了有主见的立场。没有明确的约束，就没有具体的内容可以评估。

由于技能调用在很大程度上取决于 `SKILL.md` 中的 *名称* 和 *描述*，首先要检查的是 `setup-demo-app` 技能是否在你期望的时候触发。

在早期阶段，通过 `/skills` 斜杠命令或使用 `$` 前缀引用来显式激活技能，在一个真实的仓库或临时目录中运行，观察它在哪里出问题。这是你发现遗漏的场景：技能完全不触发、触发过于频繁，或者运行但偏离了预期的步骤。

在这个阶段，你不是在追求速度或完善度。你是在寻找技能中隐藏的假设，例如：

*   **触发假设：** 类似"搭建一个快速 React 演示"的提示词 *应该* 调用 `setup-demo-app` 但却没有，或者更泛化的提示词（"添加 Tailwind 样式"）意外地触发了它。

*   **环境假设：** 技能假设它在空目录中运行，或者 `npm` 可用且优于其他包管理器。

*   **执行假设：** 代理跳过了 `npm install`，因为它假设依赖已经安装，或者在 Vite 项目存在之前就配置了 Tailwind。

当你准备好让这些运行可重复时，切换到 `codex exec`。它专为自动化和 CI 设计：将进度流式输出到 `stderr`，仅将最终结果写入 `stdout`，这使得运行更容易编写脚本、捕获和检查。

默认情况下，`codex exec` 在受限沙箱中运行。如果你的任务需要写入文件，请使用 `--full-auto` 运行。一般原则是，尤其是在自动化场景中，使用完成任务所需的最小权限。

基本的手动运行可能如下所示：

```
codex exec --full-auto \
  'Use the $setup-demo-app skill to create the project in this directory.'
```

这第一轮实践与其说是验证正确性，不如说是发现边缘情况。你在这里做的每一个手动修复——比如添加遗漏的 `npm install`、修正 Tailwind 配置或收紧触发描述——都是未来评估的候选项，这样你就可以在进行大规模评估之前锁定预期行为。

## **4. 使用小规模、有针对性的提示词集尽早捕获回归**

你不需要大型基准测试就能从评估中获益。对于单个技能，10-20 个提示词的小集合就足以尽早发现回归并确认改进。

从一个小的 CSV 文件开始，随着在开发或使用过程中遇到真实的失败，逐步扩充它。每一行应代表一个你关心 `setup-demo-app` 技能是否 *会* 或 *不会* 激活的场景，以及激活后成功的标准是什么。

例如，初始的 `evals/setup-demo-app.prompts.csv` 可能如下所示：

```
id,should_trigger,prompt
test-01,true,"Create a demo app named `devday-demo` using the $setup-demo-app skill"
test-02,true,"Set up a minimal React demo app with Tailwind for quick UI experiments"
test-03,true,"Create a small demo app to showcase the Responses API"
test-04,false,"Add Tailwind styling to my existing React app"
```

这些用例各自测试了略微不同的方面：

*   **显式调用 (`test-01`)**

    该提示词直接命名了技能。它确保 Codex 在被要求时能调用 `setup-demo-app`，并且技能的名称、描述或指令的变更不会破坏直接使用。

*   **隐式调用 (`test-02`)**

    该提示词描述了技能所针对的 *确切* 场景，即搭建一个最小的 React + Tailwind 演示，但没有提及技能名称。它测试 `SKILL.md` 中的名称和描述是否足够强，让 Codex 能自行选择该技能。

*   **上下文调用 (`test-03`)**

    该提示词添加了领域上下文（Responses API），但仍需要相同的底层搭建。它检查技能是否在真实的、略带噪声的提示词中触发，以及生成的应用是否仍然匹配预期的结构和约定。

*   **负面对照 (`test-04`)**

    该提示词**不应**调用 `setup-demo-app`。这是一个常见的邻近请求（"给现有应用添加 Tailwind"），可能会意外匹配技能的描述（"React + Tailwind 演示"）。包含至少一个 `should_trigger=false` 的用例有助于捕获**误触发**——即 Codex 过于积极地选择该技能，在用户希望对现有项目进行增量修改时却搭建了一个新项目。

这种组合是有意为之的。一些评估应确认技能在被显式调用时行为正确；另一些应检查它在用户从未提及技能名称的真实提示词中是否激活。

随着你发现遗漏——未能触发技能的提示词，或输出偏离预期的情况——将它们作为新行添加。随着时间的推移，这个小的 CSV 会成为 `setup-demo-app` 技能必须持续正确处理的场景的活记录。

随着时间的推移，这个小数据集会成为技能必须持续正确处理的场景的活记录。

## **5. 从轻量级确定性评分器开始**

这是评估步骤的核心：使用 `codex exec --json`，让你的评估 harness 能够对 *实际发生了什么* 进行评分，而不仅仅是看最终输出是否看起来正确。

启用 `--json` 后，`stdout` 变为结构化事件的 JSONL 流。这使得编写与你关心的行为直接关联的确定性检查变得简单，例如：

*   是否运行了 `npm install`？
*   是否创建了 `package.json`？
*   是否按预期顺序调用了预期的命令？

这些检查刻意保持轻量。它们在你添加任何基于模型的评分之前，就能提供快速、可解释的信号。

### **一个最小化的 Node.js 运行器**

一个"足够好"的方法如下：

1.   对每个提示词，运行 `codex exec --json --full-auto "<prompt>"`
2.   将 JSONL 追踪保存到磁盘
3.   解析追踪数据并对事件运行确定性检查

```
// evals/run-setup-demo-app-evals.mjs
import { spawnSync } from "node:child_process";
import { readFileSync, writeFileSync, existsSync, mkdirSync } from "node:fs";
import path from "node:path";

function runCodex(prompt, outJsonlPath) {
  const res = spawnSync(
    "codex",
    [
      "exec",
      "--json", // REQUIRED: emit structured events
      "--full-auto", // Allow file system changes
      prompt,
    ],
    { encoding: "utf8" }
  );

  mkdirSync(path.dirname(outJsonlPath), { recursive: true });

  // stdout is JSONL when --json is enabled
  writeFileSync(outJsonlPath, res.stdout, "utf8");

  return { exitCode: res.status ?? 1, stderr: res.stderr };
}

function parseJsonl(jsonlText) {
  return jsonlText
    .split("\n")
    .filter(Boolean)
    .map((line) => JSON.parse(line));
}

// deterministic check: did the agent run `npm install`?
function checkRanNpmInstall(events) {
  return events.some(
    (e) =>
      (e.type === "item.started" || e.type === "item.completed") &&
      e.item?.type === "command_execution" &&
      typeof e.item?.command === "string" &&
      e.item.command.includes("npm install")
  );
}

// deterministic check: did `package.json` get created?
function checkPackageJsonExists(projectDir) {
  return existsSync(path.join(projectDir, "package.json"));
}

// Example single-case run
const projectDir = process.cwd();
const tracePath = path.join(projectDir, "evals", "artifacts", "test-01.jsonl");

const prompt =
  "Create a demo app named demo-app using the $setup-demo-app skill";

runCodex(prompt, tracePath);

const events = parseJsonl(readFileSync(tracePath, "utf8"));

console.log({
  ranNpmInstall: checkRanNpmInstall(events),
  hasPackageJson: checkPackageJsonExists(path.join(projectDir, "demo-app")),
});
```

这里的价值在于一切都是**确定性的和可调试的**。

如果某项检查失败，你可以打开 JSONL 文件查看具体发生了什么。每个命令执行都以 `item.*` 事件的形式按顺序出现。这使得回归问题易于解释和修复，这正是你在现阶段所需要的。

## **6. 使用 Codex 和基于评分标准的定性检查**

确定性检查回答的是“是否完成了基本操作？”，但无法回答“是否以你期望的方式完成了？”

对于像 `setup-demo-app` 这样的技能，许多要求是定性的：组件结构、样式约定，或 Tailwind 是否遵循了预期的配置。这些很难仅通过基本的文件存在性检查或命令计数来捕获。

一个务实的解决方案是在评估流水线中添加第二个模型辅助步骤：

1.   运行搭建技能（将代码写入磁盘）
2.   对生成的仓库运行**只读风格检查**
3.   要求**结构化响应**，使你的 harness 能一致地评分

Codex 通过 `--output-schema` 直接支持这一点，它将最终响应约束为你定义的 JSON Schema。

### **一个小型评分标准 Schema**

首先定义一个捕获你关心检查的小型 schema。例如，创建 `evals/style-rubric.schema.json`：

```
{
  "type": "object",
  "properties": {
    "overall_pass": { "type": "boolean" },
    "score": { "type": "integer", "minimum": 0, "maximum": 100 },
    "checks": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "id": { "type": "string" },
          "pass": { "type": "boolean" },
          "notes": { "type": "string" }
        },
        "required": ["id", "pass", "notes"],
        "additionalProperties": false
      }
    }
  },
  "required": ["overall_pass", "score", "checks"],
  "additionalProperties": false
}
```

该 schema 提供了稳定的字段（`overall_pass`、`score`、每项检查的结果），你可以跨运行对它们进行合并、对比和跟踪。

### **风格检查提示词**

接下来，运行第二个 `codex exec`，它 *仅检查仓库* 并输出符合评分标准的 JSON 响应：

```
codex exec \
  "Evaluate the demo-app repository against these requirements:
   - Vite + React + TypeScript project exists
   - Tailwind is configured via @tailwindcss/vite and CSS imports tailwindcss
   - src/components contains Header.tsx and Card.tsx
   - Components are functional and styled with Tailwind utility classes (no CSS modules)
   Return a rubric result as JSON with check ids: vite, tailwind, structure, style." \
  --output-schema ./evals/style-rubric.schema.json \
  -o ./evals/artifacts/test-01.style.json
```

这就是 `--output-schema` 的便利之处。你得到的不是难以解析或比较的自由文本，而是一个可预测的 JSON 对象，你的评估 harness 可以跨多次运行对其进行评分。

如果你之后将此评估套件移入 CI，Codex GitHub Action 明确支持通过 `codex-args` 传递 `--output-schema`，因此你可以在自动化工作流中强制执行相同的结构化输出。

## **7. 随着技能成熟扩展评估**

一旦核心循环就位，你可以在对你的技能最重要的方向上扩展评估。从小处开始，只在真正增加信心的地方逐步添加更深入的检查。

一些示例包括：

*   **命令计数和无效循环：** 统计 JSONL 追踪中的 `command_execution` 项，以捕获代理开始循环或重复运行命令的回归。Token 使用量也可在 `turn.completed` 事件中获取。

*   **Token 预算：** 跟踪 `usage.input_tokens` 和 `usage.output_tokens`，以发现意外的提示词膨胀，并跨版本比较效率。

*   **构建检查：** 在技能完成后运行 `npm run build`。这作为更强的端到端信号，能捕获损坏的导入或错误配置的工具链。

*   **运行时冒烟测试：** 启动 `npm run dev` 并用 `curl` 访问开发服务器，或者如果你已有 Playwright 检查，运行一个轻量级的 Playwright 测试。有选择地使用这一项——它增加信心但耗费时间。

*   **仓库整洁度：** 确保运行不会生成不需要的文件，并且 `git status --porcelain` 为空（或匹配显式的允许列表）。

*   **沙箱和权限回归：** 验证技能在不提升超出预期权限的情况下仍然正常工作。最小权限默认值在自动化后最为重要。

模式是一致的：从能解释行为的快速检查开始，然后仅在较慢、较重的检查能降低风险时才添加它们。

## **8. 关键要点**

这个小型 `setup-demo-app` 示例展示了从"感觉更好"到"有据可依"的转变：运行代理，记录发生了什么，用一小组检查进行评分。一旦这个循环建立起来，每次调整都更容易确认，每次回归都一目了然。以下是关键要点：

*   **衡量重要的东西。** 好的评估让回归清晰可见、失败可解释。
*   **从可检查的完成定义开始。** 使用 `$skill-creator` 引导创建，然后收紧指令直到成功标准明确无误。
*   **让评估基于行为。** 使用 `codex exec --json` 捕获 JSONL，并针对 `command_execution` 事件编写确定性检查。
*   **在规则力所不及处使用 Codex。** 使用 `--output-schema` 添加结构化的、基于评分标准的检查轮次，可靠地评估风格和约定。
*   **让真实失败驱动覆盖率。** 每次手动修复都是一个信号。将其转化为测试，使技能持续正确执行。
