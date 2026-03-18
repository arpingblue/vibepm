# Contributing to VibePM

First off, thank you for considering contributing to this project! We aim to build the strongest **Vibecoding (AI-assisted coding) Safety Rails** on the internet.

## How Can I Contribute?

### 1. Submit Better `.cursorrules` / System Prompts
The best practices for AI coding change daily. If you have an excellent `System Prompt` template for a specific tech stack (e.g., Next.js 14 App Router anti-hallucination configs, Python FastAPI strict modes)?
* Add it to `references/output-templates.md`.

### 2. Improve Anti-Hallucination Prompts & Boundary Rules
The core of this skill is `SKILL.md`, designed to suppress hallucinations when LLMs generate code. If you can optimize:
* More aggressive Scope Cut scripts
* More accurate architecture question banks (`references/discovery-framework.md`)

Please submit a Pull Request. **Note:** Any changes to `SKILL.md` must ensure the file remains under 10KB.

### 3. Support More Coding Agents
We currently support Claude Code, OpenClaw, and Antigravity. If you want to add native support for other agents:
* Create a new hidden folder (e.g., `.windsurf/`)
* Add the required bootstrapper plugins
* Update the `README.md` and `README_zh-CN.md`.

## Pull Request Process
1. Fork the repo and create your branch from `main`.
2. Ensure your prompts focus on "Architecture Clarification" and "Context Safety Evaluation" rather than commercial metrics.
3. Submit the PR and describe what kind of AI coding crash scenario your PR prevents.

## Code of Conduct
Respect each other. Let's build better software with AI together.
