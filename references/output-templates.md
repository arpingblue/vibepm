# VibePM (GSD 前置架构师) 输出模板

本页面定义了当用户需求清晰（9大要素基本齐备）后，身为架构师的你为下流**执行 Agent (如 get-shit-done, GSD)** 输出的**规范化项目说明与原子计划文档**。

这些文档必须高度结构化，确保 GSD 等 AI 执行器能够无脑并行执行，绝不偏离架构。

---

## 模板 1: `PROJECT.md` (项目愿景与架构铁律)

**用途**：写在根目录，定义项目的基调、技术栈锁死以及所有代理必须遵守的绝对红线。

```markdown
# [Project Name]

## 1. 核心愿景 (Vision)
[1-2句话精简陈述，如："A highly responsive YouTube summarization web app that processes videos entirely async, providing a simple dashboard for users."]

## 2. 硬性技术栈 (Tech Stack)
*前端/框架不准更改版本，不准引入冗余的替代库。*
- **Framework**: [Next.js 14 App Router]
- **Language**: [TypeScript (strict mode)]
- **Styling**: [Tailwind CSS + Shadcn UI]
- **Backend/DB**: [Supabase Auth + Postgres Database]
- **State**: [URL SearchParams > Zustand > Context]

## 3. 架构约束与 AI 防偏红线 (Constraints)
- **永远优先使用服务端组件**: 除非页面有极强的表单/Hooks 交互，否则必须保持为 Server Component。
- **UI 提取原则**: 绝不手搓复杂的交互组件，直接使用 Shadcn standard components。
- **鉴权约束**: 所有的 Dashboard 路由必须在 middleware/layout 级别使用 Supabase Auth 进行校验。

## 4. 目录流转结构
```
app/
  (auth)/          # Auth routes
  (dashboard)/     # Main application
  api/             # Webhooks only
components/
  ui/              # Shadcn pure presentation
  features/        # Business logic wrappers
lib/               # Utility functions & db clients
```
```

---

## 模板 2: `ROADMAP.md` (里程碑分期路线图)

**用途**：在开始一切原子任务前，将宏大应用切分为不同的 Phase。这是 VibePM 防止发散最重要的输出物。

```markdown
# 路线图规划 (Milestones & Phases)

## Phase 1: Foundation (数据流与鉴权底座)
**目标:** 建立基础技术脚手架与鉴权屏障。
**包含内容:** DB 连通、Supabase Auth 引入、基础的用户表注册机制。

## Phase 2: Core Entity Actions (核心业务流)
**目标:** 用户能完成基础的核心 CRUD 操作。
**包含内容:** 核心业务表的创建表单，Dashboard 的核心数据展示，乐观更新 (Optimistic updates)。

## Phase 3: External Integrations & Async (第三方集成)
**目标:** 引入长耗时、高失败率的第三方功能。
**包含内容:** OpenAI / YouTube 解析等外部 API 整合，错误边界捕获，超时重试机制。

## Out of Scope (第一版 MVP 绝对不做的特性)
- 用户自定义头像与深度设置
- Stripe 计费与支付网关
- 复杂动画与多语言支持 (i18n)
```

---

## 模板 3: `PLAN.md` (符合 GSD 的 XML 原子化执行计划)

**用途**：这是实际扔给 `get-shit-done` / Cursor 的代码落地清单。**绝对禁止使用普通的 Markdown Checkbox**。必须使用 `<task>` 标签并且编排并行执行波次 (`wave`)。

```xml
# Implementation Plan: [Phase X - e.g. Foundation]

## Wave 1 (并行执行：底座初始化)
*这些任务互不依赖，AI Agent 可以并发执行。*

<task type="auto">
  <name>Init App Structure & UI Lib Setup</name>
  <files>tailwind.config.ts, components/ui/*, app/layout.tsx</files>
  <action>
    Initialize standard Next.js styling.
    Install `lucide-react` for icons and set up basic Tailwind font bindings.
    Remove default Vercel boilerplate from `app/page.tsx`.
  </action>
  <verify>Run `npm run build` and ensure no basic linting errors.</verify>
  <done>Clean shell layout with working fonts.</done>
</task>

<task type="auto">
  <name>Setup Database Client connection</name>
  <files>lib/db.ts, .env.local.example</files>
  <action>
    Export a reusable Supabase client instance (server and browser variants).
    Add required ENV variables to `.env.local.example` (SUPABASE_URL, ANON_KEY).
  </action>
  <verify>Ensure db.ts compiles and endpoints are correctly typed.</verify>
  <done>Client is ready to be imported in subsequent phases.</done>
</task>

## Wave 2 (顺序依赖：依赖 Wave 1 落地后执行)

<task type="auto">
  <name>Implement Auth Middleware Guard</name>
  <files>middleware.ts, app/(dashboard)/layout.tsx</files>
  <action>
    Using the Supabase client from `lib/db.ts`, create a Next.js middleware that protects the `/(dashboard)` route.
    If unauthenticated, redirect strictly to `/login`.
  </action>
  <verify>Mock a request to dashboard and expect a 307 redirect.</verify>
  <done>Middleware correctly intercepts protected routes.</done>
</task>
```

---

## 模板 4: `SCHEMA.sql` (预先建库语句)

**用途**：防止 AI 幻觉的最后一环。在写业务逻辑前，强迫优先确立数据库结构。

```sql
-- 1. Enum types
CREATE TYPE generation_status AS ENUM ('pending', 'completed', 'failed');

-- 2. Core Entities
CREATE TABLE generations (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES auth.users(id) ON DELETE CASCADE,
    youtube_url TEXT NOT NULL,
    status generation_status DEFAULT 'pending',
    audio_url TEXT,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- 3. RLS (Row Level Security) Policies
ALTER TABLE generations ENABLE ROW LEVEL SECURITY;
CREATE POLICY "Users can only read and create their own records" ON generations
    FOR ALL USING (auth.uid() = user_id);
```
