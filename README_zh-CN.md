<div align="center">

# VibePM (Vibecoding 架构师) 🎯

<!-- <img src="assets/banner.png" alt="VibePM Banner" width="100%"> -->

**最强前置规划大脑，专为 Cursor、Codex、Windsurf 和 get-shit-done(GSD) 设计。**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Multi-Platform](https://img.shields.io/badge/Platforms-Cursor%20%7C%20Windsurf%20%7C%20Codex%20%7C%20GSD-success)](#)
[![GitHub stars](https://img.shields.io/github/stars/PM-creator/vibepm?style=social)](https://github.com/PM-creator/vibepm/stargazers)
[![Version](https://img.shields.io/badge/version-2.1.0-green)](#)

*[Read this in English](README.md)*

</div>

---

这是一个专为 **Vibecoding (AI辅助编程)** 设计的架构师级 AI Skill。它通过结构化对话，将你模糊的应用想法转化为 **AI 编程智能体 (如 Cursor/Windsurf) 能够无脑执行** 的技术规范和分步实施计划。

## 🚀 这是什么？

用大模型写代码（Vibecoding）时最容易遇到的灾难是：**上下文崩溃**与**技术栈幻觉**。你给 Cursor 描述一个宏大的应用，它写出来的代码前后端不分、数据库连不上、用错第三方库版本。

**VibePM (Vibecoding 架构师)** 就是为了解决这个问题而生。它是 **get-shit-done (GSD)** 等自动编程系统最完美的前置规划插件：
它不写具体的业务代码，也不写商业计划书。它负责在写代码前“逼问”你，帮你锁定 9 大核心技术要素，砍掉多余需求，最后为你输出一份完美兼容 GSD / Cursor 语法的发版蓝图 (`PROJECT.md`, `ROADMAP.md`, `PLAN.md`)。

## ✨ 核心特性

- **🛡️ 极致预防 AI 幻觉 (Scope Control)**：主动防止你脑洞开得太大。当需求超过单一 Session 能承载的 Token 上限时，VibePM 会坚决要求切分 MVP。
- **🧠 强制锁定技术栈**：在开工前逼迫你敲定所有的数据库、UI 库、状态管理方案，绝不允许把模棱两可的需求丢给写代码的 AI。
- **📄 专供 AI 阅读的 4 大输出**：支持生成极度结构化的 `PROJECT.md`, `ROADMAP.md`，带 XML 并行执行指令的 `PLAN.md`，以及 Database Schema。
- **🧩 纯原生 / 适配主流 Agent**：纯 Markdown 构建。在 Claude Code, OpenClaw, Antigravity, 甚至是 Cursor 的 Composer 中直接加载生效。

## 📂 目录结构

```text
vibepm/
├── SKILL.md                          # ⚡ 核心能力注入 (System Prompt)
├── references/                       # 📚 AI防幻觉知识库
│   ├── discovery-framework.md        # 9大 Vibecoding 技术要素定义
│   ├── questioning-rules.md          # 防雪崩提问规则与反模式
│   └── output-templates.md           # .cursorrules 等 4 种输出模板
├── examples/                         # 💡 演示案例
│   ├── example-vague-idea.md         # 演示如何帮用户极限裁剪需求
│   └── example-output-project-brief.md # 输出的分步计划示例
├── .agents/workflows/vibepm.md     # 🔌 适配 Antigravity / OpenClaw
├── .claude/commands/vibepm.md      # 🔌 适配 Claude Code 自定义指令
└── .codex/skills-index.json          # 🔌 适配 Codex / VSCode 插件
```

## 🛠️ 安装与使用

将此目录作为工作区加载到您习惯的 AI Agent 环境中：

### 在 Claude Code 中
直接输入指令：
```bash
/vibepm
```
或者使用自然语言触发：*“我要用Cursor写个全栈项目，用 VibePM 帮我做架构规划。”*

### 在 Antigravity / OpenClaw 中
通过工作流触发：
```text
运行 vibepm 工作流。我想做一个可以总结 YouTube 视频的 AI 网站。
```

## 🧐 它是如何工作的？

每一次对话，Skill 都会在后台严格评估以下 9 大技术要素的缺口：
1. **核心逻辑** (Core Concept)
2. **技术栈约定** (Tech Stack)
3. **数据流与 Schema** (Data Schema)
4. **页面流转** (App Flow)
5. **状态管理层** (State Management)
6. **外部 API 与鉴权** (Integrations)
7. **边缘状态** (Edge Cases)
8. **部署环境** (Deployment)
9. **上下文裁剪** (MVP Scope Cut) （**最重要的一环**）

只有这 9 个点清晰且收敛，它才会判断“安全”，并为你吐出执行文档。

## 🤝 参与贡献

如果你有更适合 Cursor 或者 Windsurf 的 `.cursorrules` 模板，欢迎提交 PR 补充到 `output-templates.md` 中。我们的目标是建立一套人人可用的 AI 编程前置护栏。详细内容请参阅 [贡献指南](CONTRIBUTING_zh-CN.md)。

---

## 🌟 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=PM-creator/vibepm&type=Date)](https://star-history.com/#PM-creator/vibepm&Date)

---

## 📜 开源协议

本项目基于 [MIT 协议](LICENSE) 许可，可自由使用和修改。

<div align="center">
  <sub>Built with ❤️ by the PM-Creator team for the Vibecoding Era.</sub>
</div>