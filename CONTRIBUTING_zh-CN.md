# 参与贡献指南

首先，感谢您考虑为本项目做出贡献！我们致力于建立全网最强壮的 **Vibecoding (AI 编程) 前置护栏**。

## 我可以如何贡献？

### 1. 提交更好用的 `.cursorrules` / System Prompts
目前 AI 编程的最佳实践每天都在变幻。如果您有适用于特定技术栈（例如 Next.js 14 App Router 极佳实践、Python FastAPI 防幻觉配置）的绝佳 `System Prompt` 妯℃澘？
* 请将其添加到 `references/output-templates.md` 中。

### 2. 优化防幻觉 Prompt 与 边界规则
该技能的核心在于 `SKILL.md`，用于前期压制大模型产生代码时的幻觉。如果您能优化：
* 更有攻击性的限制范围 (Scope Cut) 话术
* 更准确的架构问题库 (`references/discovery-framework.md`)

欢迎提交 Pull Request (PR)。**注意：** 对 `SKILL.md` 的任何更改必须保证文件总大小不超过 10KB。

### 3. 支持更多的写代码 Agent
目前原生支持供 Claude Code, OpenClaw, Antigravity 运行去生成计划给 Cursor/Windsurf 阅读。如果您想增加更原生直接的支持：
* 在根目录创建一个新的隐藏文件夹（例如 `.windsurf/`）
* 添加该平台所需的引导插件
* 同步更新中英文版的 `README`。

## Pull Request 提交流程
1. Fork 本仓库并从 `main` 分支拉取你的开发分支。
2. 确保您修改的提示词保持纯文本逻辑，专注于梳理程序的“架构”和“上下文安全评估”。
3. 提交 PR 并在说明中描述该 PR 防御了怎样的 AI 写代码崩溃场景。

## 行为准则
相互尊重，一起用 AI 造好软件。