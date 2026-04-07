# AGENT.md：通用代理配置文件

**作者：** Geoffrey Huntley

**机构：** Sourcegraph, Inc.

**状态：** 说明性

**日期：** 2025 年 7 月

## 摘要

AI 驱动的编码工具正在重塑我们构建软件的方式，但它们分散在各种各样的配置文件中。

本文档定义了 `AGENT.md`，一种标准化格式，让你的代码库能够直接与任何代理编码工具对话。

## 目录

[1\. 简介](#introduction)

[2\. 规范](#specification)

[2.1\. 多个 AGENT.md 文件](#multiple-agent-files)

[2.2\. 文件引用](#file-references)

[3\. 实现指南](#implementation-guidelines)

[4\. 从遗留配置文件迁移](#migration)

[4.1\. 迁移命令](#migration-commands)

[4.2\. AGENT.md 内容结构](#content-structure)

[4.3\. 示例 AGENT.md 文件](#example-file)

[5\. 工具集成](#tool-integration)

[6\. IANA 注意事项](#iana-considerations)

[7\. 参考文献](#references)

[8\. 作者联系方式](#authors-addresses)

## 1\. 简介

一切都在变化。开发者工具公司正在构建能够阅读、理解和修改整个代码库的 AI 代理，但关键问题是：它们需要了解你的项目是如何运作的——运行什么命令、遵循什么约定、重要的东西在哪里。

目前这对用户来说是一团糟。他们必须为想要使用的每个工具维护单独的配置文件：`.cursorrules`、`.windsurfrules`、`.clauderules`，以及散布在各种工具中的十几个其他文件。每隔一两天就有新的代理带着自己的约定进入市场，让局面更加混乱。

`AGENT.md` 改变了这一切。一个文件，适配任意代理。你的代码库拥有了一个所有 AI 编码工具都能理解的统一表达方式。

Amp 团队正在与其他代理编码工具制造商合作，清理这种文件名的混乱局面。我们喜欢 AGENT.md，因为我们拥有 <https://agent.md> 的域名，并且我们承诺保持其供应商中立性，这样任何人在 X 或聊天中输入 "agent.md" 都会被引导到一个中立、可信赖的网站（目前 AGENTS.md 还做不到这一点），但我们愿意[妥协](https://x.com/sqs/status/1923794823238254629)。

## 2\. 规范

`AGENT.md` 文件必须放置在软件项目的根目录中，并且必须使用 Markdown 格式。该文件应包含以下部分：

* 项目结构和组织
* 构建、测试和开发命令
* 代码风格和约定
* 架构和设计模式
* 测试指南
* 安全注意事项

该格式旨在保持人类可读性，同时提供可被代理编码工具解析的结构化信息。

### 2.1\. 多个 AGENT.md 文件

实现应支持分层结构中的多个 `AGENT.md` 文件：

* 根目录的 `AGENT.md` 用于通用项目指导
* 子目录的 `AGENT.md` 文件用于特定子系统的指导
* `~/.config/AGENT.md` 中的用户全局 `AGENT.md` 用于个人偏好设置

当存在多个文件时，工具应合并配置，更具体的文件优先于通用文件。

### 2.2\. 文件引用

`AGENT.md` 文件可以使用 `@` 提及（例如 `@filename.md`）引用其他文件，以纳入在该项目中工作时应考虑的额外上下文或文档。

## 3\. 实现指南

工具实现者在添加 `AGENT.md` 支持时应遵循以下指南：

1. 在项目初始化期间解析 `AGENT.md` 文件
2. 提取与工具特定用例相关的配置
3. 在 `AGENT.md` 不存在时提供回退行为
4. 尊重现有的工具特定配置文件以实现向后兼容

## 4\. 从遗留配置文件迁移

准备好切换了吗？如果你的项目中散布着各种配置文件，我们将帮助你将它们整合到一个适用于所有工具的 `AGENT.md` 中。这比你想象的更简单。

### 4.1\. 迁移命令

以下是如何将现有配置迁移到 `AGENT.md` 同时保持向后兼容的方法：

```
# Cline
mv .clinerules AGENT.md && ln -s AGENT.md .clinerules

# Claude Code
mv CLAUDE.md AGENT.md && ln -s AGENT.md CLAUDE.md

# Cursor
mv .cursorrules AGENT.md && ln -s AGENT.md .cursorrules

# Firebase Studio
ln -s AGENT.md .idx/airules.md

# Gemini CLI, OpenAI Codex, OpenCode
ln -s AGENTS.md AGENT.md

# GitHub Copilot
mv .github/copilot-instructions.md AGENT.md && ln -s ../../AGENT.md .github/copilot-instructions.md

# Replit
mv .replit.md AGENT.md && ln -s AGENT.md .replit.md

# Windsurf
mv .windsurfrules AGENT.md && ln -s AGENT.md .windsurfrules
```

这些命令会将你现有的配置移动到 `AGENT.md`，并创建指回旧位置的符号链接。你的工具仍可继续正常工作，但现在它们都从同一个单一事实来源读取配置。

### 4.2\. AGENT.md 内容结构

`AGENT.md` 中应该放什么？想想你会对新团队成员第一天上班时说什么。以下内容效果很好：

* **项目概述：** 项目目的和架构的简要描述
* **构建与命令：** 开发、测试和部署命令
* **代码风格：** 格式规则、命名约定和最佳实践
* **测试：** 测试框架、约定和执行指南
* **安全：** 安全注意事项和数据保护指南
* **配置：** 环境设置和配置管理

### 4.3\. 示例 AGENT.md 文件

以下是一个可靠的 `AGENT.md` 示例。复制此结构并根据你的项目进行调整：

```
# MyApp Project

MyApp is a full-stack web application with TypeScript frontend and Node.js backend.
The core functionality lives in the `src/` folder, with separate client (`client/`)
and server (`server/`) components.

## Build & Commands

- Typecheck and lint everything: `pnpm check`
- Fix linting/formatting: `pnpm check:fix`
- Run tests: `pnpm test --run --no-color`
- Run single test: `pnpm test --run src/file.test.ts`
- Start development server: `pnpm dev`
- Build for production: `pnpm build`
- Preview production build: `pnpm preview`

### Development Environment

- Frontend dev server: http://localhost:3000
- Backend dev server: http://localhost:3001
- Database runs on port 5432
- Redis cache on port 6379

## Code Style

- TypeScript: Strict mode with exactOptionalPropertyTypes, noUncheckedIndexedAccess
- Tabs for indentation (2 spaces for YAML/JSON/MD)
- Single quotes, no semicolons, trailing commas
- Use JSDoc docstrings for documenting TypeScript definitions, not `//` comments
- 100 character line limit
- Imports: Use consistent-type-imports
- Use descriptive variable/function names
- In CamelCase names, use "URL" (not "Url"), "API" (not "Api"), "ID" (not "Id")
- Prefer functional programming patterns
- Use TypeScript interfaces for public APIs
- NEVER use `@ts-expect-error` or `@ts-ignore` to suppress type errors

## Testing

- Vitest for unit testing
- Testing Library for component tests
- Playwright for E2E tests
- When writing tests, do it one test case at a time
- Use `expect(VALUE).toXyz(...)` instead of storing in variables
- Omit "should" from test names (e.g., `it("validates input")` not `it("should validate input")`)
- Test files: `*.test.ts` or `*.spec.ts`
- Mock external dependencies appropriately

## Architecture

- Frontend: React with TypeScript
- Backend: Express.js with TypeScript
- Database: PostgreSQL with Prisma ORM
- State management: Zustand
- Styling: Tailwind CSS
- Build tool: Vite
- Package manager: pnpm

## Security

- Use appropriate data types that limit exposure of sensitive information
- Never commit secrets or API keys to repository
- Use environment variables for sensitive data
- Validate all user inputs on both client and server
- Use HTTPS in production
- Regular dependency updates
- Follow principle of least privilege

## Git Workflow

- ALWAYS run `pnpm check` before committing
- Fix linting errors with `pnpm check:fix`
- Run `pnpm build` to verify typecheck passes
- NEVER use `git push --force` on the main branch
- Use `git push --force-with-lease` for feature branches if needed
- Always verify current branch before force operations

## Configuration

When adding new configuration options, update all relevant places:
1. Environment variables in `.env.example`
2. Configuration schemas in `src/config/`
3. Documentation in README.md

All configuration keys use consistent naming and MUST be documented.
```

## 5\. 工具集成

`AGENT.md` 已可与以下工具配合使用，而且每天都有更多工具加入：

* **[Amp](/manual#AGENT.md)：** 自 [2025-05-07](/news/AGENT.md) 起原生支持。自 2025-07-07 起支持[多个 AGENT.md 文件](/news/multiple-AGENT.md-files)。
* **[Claude Code](https://www.anthropic.com/claude-code)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[Cursor](https://cursor.com)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[Firebase Studio](https://firebase.google.com/studio)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[Gemini CLI](https://github.com/google-gemini/gemini-cli)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[OpenAI Codex](https://openai.com/codex/)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[OpenCode](https://github.com/opencode-ai/opencode)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[Replit](https://replit.com)：** 通过符号链接支持 AGENT.md（参见迁移部分）。
* **[Windsurf](https://windsurf.com)：** 通过符号链接支持 AGENT.md（参见迁移部分）。

## 6\. IANA 注意事项

本文档不需要任何 IANA 操作。`.md` 文件扩展名已注册用于 Markdown 文件。

## 7\. 参考文献

**7.1\. 规范性引用**

\[RFC2119\] Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, March 1997.

\[MARKDOWN\] Gruber, J., "Markdown", https://daringfireball.net/projects/markdown/, 2004.

**7.2\. 资料性引用**

\[AGENT.MD\] Sourcegraph, "AGENT.md Domain", https://agent.md/, 2025.

\[AMP\] Sourcegraph, "Amp - An agentic coding tool, in research preview", https://ampcode.com/, 2025.

## 8\. 作者联系方式

Sourcegraph 团队

Sourcegraph, Inc.

Email: [amp-devs@sourcegraph.com](mailto:amp-devs@sourcegraph.com)

URI: <https://ampcode.com>

如需对本页面提出修改建议，请发送邮件至 [amp-devs@sourcegraph.com](mailto:amp-devs@sourcegraph.com) 或在 X 上提及 [@AmpCode](https://x.com/AmpCode)。
