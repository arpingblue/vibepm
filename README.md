<div align="center">

# VibePM (Vibecoding Architect) 🎯

<!-- <img src="assets/banner.png" alt="VibePM Banner" width="100%"> -->

**The Ultimate Upstream Planning Brain for Cursor, Codex, Windsurf, and get-shit-done (GSD).**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Multi-Platform](https://img.shields.io/badge/Platforms-Cursor%20%7C%20Windsurf%20%7C%20Codex%20%7C%20GSD-success)](#)
[![GitHub stars](https://img.shields.io/github/stars/PM-creator/vibepm?style=social)](https://github.com/PM-creator/vibepm/stargazers)
[![Version](https://img.shields.io/badge/version-2.1.0-green)](#)

*[Read this in Chinese (中文)](README_zh-CN.md)*

</div>

---

A Staff-level Architect AI Skill designed specifically for **Vibecoding** (AI-assisted programming). It transforms your vague app ideas into rigid, context-safe technical specifications and step-by-step implementation plans that coding agents (like Cursor or Windsurf) can execute blindly without hallucinating.

## 🚀 What is this?

The biggest disaster in AI coding is **Context Collapse & Stack Hallucination**. When you describe a massive app to Cursor all at once, it outputs spaghetti code, mixes up App and Pages router, fails database connections, and gets confused about component states.

**VibePM (Vibecoding Architect)** solves this by acting as the ultimate planning bridge for execution agents like **get-shit-done (GSD)** or Cursor. 
It does not write the app code, nor does it write business plans. It interrogates you *before* any code is written, locking down 9 core technical elements, aggressively slicing off feature creep, and finally generating native GSD-compatible execution documents (`PROJECT.md`, `ROADMAP.md`, and an XML-based `PLAN.md`).

## ✨ Core Features

- **🛡️ Extreme Hallucination Prevention**: Actively fights scope creep. Whenever a request exceeds the context window of a single AI coding session, it forcibly enforces an MVP cut.
- **🧠 Forced Stack Lock**: Forces you to establish the exact Database, UI Library, and State Management strategy before generation. No ambiguous requirements allowed.
- **📄 4 Native AI Artifacts**: Generates highly structured `PROJECT.md`, `ROADMAP.md`, a strictly XML-formatted `PLAN.md` with execution waves, and raw Database Schemas.
- **🧩 100% Native**: Built purely on Markdown. Loads seamlessly into Claude Code, OpenClaw, Antigravity, or directly into a Cursor Composer context list.

## 📂 Directory Structure

```text
vibepm/
├── SKILL.md                          # ⚡ Core Architect Engine (<10KB)
├── references/                       # 📚 Anti-Hallucination Knowledge Base
│   ├── discovery-framework.md        # The 9 Vibecoding Technical Elements
│   ├── questioning-rules.md          # Interrogation rules & scope-cutting scripts
│   └── output-templates.md           # 4 templates (.cursorrules, plans, schemas)
├── examples/                         # 💡 Live Examples
│   ├── example-vague-idea.md         # Example of aggressive scope cutting
│   └── example-output-project-brief.md # Example generated plan for an AI
├── .agents/workflows/vibepm.md     # 🔌 Antigravity / OpenClaw adapter
├── .claude/commands/vibepm.md      # 🔌 Claude Code instruction adapter
└── .codex/skills-index.json          # 🔌 Codex / VSCode plugin index
```

## 🛠️ Usage / Installation

Load this directory into your preferred AI Agent environment:

### For Claude Code
Type the following command:
```bash
/vibepm
```
Or simply say: *"I'm going to build a full-stack project with Cursor. Help me architect it using VibePM."*

### For Antigravity / OpenClaw
Trigger the workflow by saying:
```text
Run the vibepm workflow. I want to build an AI YouTube summarizer app.
```

## 🧐 How it Works

In every interaction, the Skill strictly evaluates the gaps in the 9 Technical Elements:
1. **Core Concept**
2. **Tech Stack Lock**
3. **Data Schema**
4. **App Flow**
5. **State Management**
6. **External Integrations & Auth**
7. **Edge Cases**
8. **Deployment**
9. **MVP Context-Cut** (**The most critical element**)

Only when these 9 points are absolutely clear and within context limits will it say "Go" and output the hand-off documents for your Coding AI.

## 🤝 Contributing

If you have highly optimized `.cursorrules` templates or better prompt architectures for LLM programmers, please open an issue or submit a PR. Our goal is to create the ultimate safety rails for AI developers. For details, see [Contributing Guidelines](CONTRIBUTING.md).

---

## 🌟 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=PM-creator/vibepm&type=Date)](https://star-history.com/#PM-creator/vibepm&Date)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

<div align="center">
  <sub>Built with ❤️ by the PM-Creator team for the Vibecoding Era.</sub>
</div>
