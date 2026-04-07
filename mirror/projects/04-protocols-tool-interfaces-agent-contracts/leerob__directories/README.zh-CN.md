# Cursor Directory

Cursor 的社区中心，汇聚了插件、MCP 服务器、活动、职位，以及成千上万名共同构建的开发者。

**[cursor.directory](https://cursor.directory)**

---

## 项目结构

```
├── apps/
│   └── cursor/          # Next.js 应用
├── packages/
│   └── email/           # 邮件模板 (React Email)
├── supabase/
│   └── migrations/      # 数据库迁移
└── package.json         # Bun 工作区配置
```

所有数据都存储在数据库中，仓库中没有本地数据。

## 快速开始

### 前提条件

- [Bun](https://bun.sh)
- 一个 [Supabase](https://supabase.com) 项目

### 设置

1. **克隆仓库**

```bash
git clone https://github.com/pontusab/cursor.directory.git
cd cursor.directory
```

2. **安装依赖**

```bash
bun install
```

3. **配置环境变量**

```bash
cp apps/cursor/.env.example apps/cursor/.env
```

填写所需的值：

| 变量 | 必填 | 描述 |
|----------|----------|-------------|
| `NEXT_PUBLIC_SUPABASE_URL` | 是 | Supabase 项目 URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | 是 | Supabase 匿名/公开密钥 |
| `SUPABASE_SERVICE_ROLE_KEY` | 是 | Supabase 服务角色密钥 |
| `RESEND_API_KEY` | 否 | Resend API 密钥（邮件） |
| `NEXT_PUBLIC_APP_URL` | 否 | 默认为 `http://localhost:3000` |

4. **运行数据库迁移**

将 `supabase/migrations/` 中的迁移应用到你的 Supabase 项目。

5. **启动开发服务器**

```bash
bun dev
```

打开 [http://localhost:3000](http://localhost:3000)。

---

## 贡献

所有内容都通过网站提交，无需通过 Pull Request 提交数据。

### 提交插件

1. 前往 [cursor.directory/plugins/new](https://cursor.directory/plugins/new)
2. 使用 GitHub 或 Google 登录
3. 粘贴 GitHub 仓库 URL，我们会自动检测遵循 [Open Plugins](https://open-plugins.com) 标准的组件
4. 点击 **Submit**

自动检测的组件：

| 组件 | 路径 |
|-----------|------|
| Rules | `rules/*.mdc` |
| MCP Servers | `.mcp.json` |
| Skills | `skills/*/SKILL.md` |
| Agents | `agents/*.md` |
| Hooks | `hooks/hooks.json` |
| LSP Servers | `.lsp.json` |

详见 [Open Plugins specification](https://open-plugins.com/plugin-builders/specification) 和 [plugin template](https://github.com/cursor/plugin-template)。

### 举办活动

社区活动由 [Luma](https://lu.ma) 提供支持：

1. 前往 [cursor.directory/events](https://cursor.directory/events)
2. 点击 **Host an event**
3. 填写表单，你的活动会自动显示在网站上

### 发布职位

1. 在 [cursor.directory](https://cursor.directory) 登录
2. 导航到 **Jobs → Post a job**
3. 填写详情并提交

---

## 技术栈

- **框架**: [Next.js](https://nextjs.org) (App Router, Turbopack)
- **运行时**: [Bun](https://bun.sh)
- **数据库**: [Supabase](https://supabase.com) (PostgreSQL)
- **样式**: [Tailwind CSS](https://tailwindcss.com)
- **UI**: [Radix UI](https://radix-ui.com) + [shadcn/ui](https://ui.shadcn.com)
- **邮件**: [React Email](https://react.email) + [Resend](https://resend.com)
- **搜索**: [Fuse.js](https://fusejs.io)（客户端模糊搜索）
- **URL 状态**: [nuqs](https://nuqs.47ng.com)
- **活动**: [Luma API](https://docs.lu.ma)
- **代码检查**: [Biome](https://biomejs.dev)
