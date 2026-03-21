# Vibecoding 项目画像 (9大技术要素)

作为 Vibecoding 架构师，我们在收集信息时**抛弃所有商业维度的概念**（如 ROI、用户群体、市场分析），唯一关注的是**如何给负责写代码的 AI Agent 喂送无歧义的技术上下文**。

## 9 大技术要素结构

### 1. 核心应用逻辑 (App Concept)
- **定义**：用一句话说明应用到底干什么。
- **目的**：保证最终系统提示词的聚焦。
- **示例**：“一个供用户上传 PDF 并通过 LLM 总结其内容的单页应用。”

### 2. 技术栈敲定 (Tech Stack)
- **定义**：具体的语言、框架、版本约定。
- **目的**：防止不同来源的 AI 产生库版本不兼容或代码风格幻觉（例如混用 App Router 和 Pages Router）。
- **必须确定**：
  - 前端 (e.g., Next.js 14 App Router)
  - 核心语言 (e.g., TypeScript, strict mode)
  - 样式流派 (e.g., Tailwind CSS + Shadcn UI)
  - 后端/BaaS (e.g., Supabase / Firebase / NodeJS)

### 3. 数据实体模型 (Data Schema)
- **定义**：应用运行必须的核心数据表及其关系。
- **目的**：AI 编程中如果缺乏 Schema，不同组件间传递的 Props 会彻底乱套。
- **必须确定**：有哪些表（如 `users`, `documents`, `summaries`），1对多还是多对多关联。

### 4. 页面流转与交互 (App Flow)
- **定义**：用户从进入应用到完成任务经历的页面。
- **目的**：为 AI 生成前端路由结构 (`app/page.tsx`, `app/dashboard/page.tsx`) 提供依据。
- **必须确定**：公开页面有什么。需要鉴权的页面有什么。

### 5. 状态管理策略 (State Management)
- **定义**：应用中数据在不同组件间如何流转。
- **目的**：防止 AI 混用 Context、Zustand、Redux 或 Prop Drilling。
- **建议方向**：越简单越好。首选 React Server Components + URL Search Params，其次 Zustand。

### 6. 第三方集成 (External Integrations)
- **定义**：依赖的外部系统。
- **目的**：提前指出，以便在 Implementation Plan 中优先完成配置。
- **必须确定**：鉴权系统 (Clerk, Supabase Auth)、支付 (Stripe)、核心 API (OpenAI API)。

### 7. 边缘情况与边界设计 (Edge Cases)
- **定义**：无数据、断网、无权限等状态如何处理。
- **目的**：AI 生成的“欢乐路径 (Happy Path)”代码往往在现实中崩溃，必须在 Spec 中定义边界。
- **必须确定**：Loading 骨架屏策略。错误 Toast 提示。未付费拦截逻辑。

### 8. 部署基建 (Deployment)
- **定义**：应用跑在哪里。
- **目的**：影响环境变量配置和构建脚本。
- **首选**：Vercel、Netlify 或 Docker/VPS。

### 9. MVP 范围极致裁剪 (MVP Context-Cut)
- **定义**：为了保护大模型的上下文窗口，明确列出“不要做”的功能。
- **目的**：这是 Vibecoding 项目**最重要的一环**。全盘托出会突破 Token 上限引发幻觉。
- **核心策略**：砍掉一切对于核心业务非必须的 Feature（如暂时去掉邮箱验证、个人资料修改中心、深色模式切换等），专注单一定线。

---

## 信息成熟度阶段判定

1. **A阶段 (混沌期)**：用户满脑子都是功能叠加。 -> **策略**：启动“MVP 范围极致裁剪”框架，把功能砍掉 80%。帮用户做技术栈选型。
2. **B阶段 (成型期)**：有主框架，数据结构不清晰。 -> **策略**：推演用户操作链路，反推所需的数据表。
3. **C阶段 (就绪期)**：上述 9 大点基本涵盖。 -> **策略**：进入文档生成阶段，产出 `Implementation Plan` 等交付物。