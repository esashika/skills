# My Custom OpenCode Skills

A personal monorepo containing a curated collection of tailor-made agent skills. These skills are built to supercharge my OpenCode agent's capabilities—automating repetitive tasks, enforcing elite standards, and streamlining complex Git & GitHub workflows.

> **Why this exists:** To offload cognitive overhead and manual steps into precise, safe, and repeatable AI-driven operations that integrate directly with my local environment.

---

## 🎯 The Skill Codex

Each folder in `skills/` represents a targeted capability. Here is the current directory of my custom skills:

| Namespace & Path | Skill Name | Core Capability |
| :--- | :--- | :--- |
| `skills/ghr/gh-split-commits` | `gh-split-commits` | Intelligently analyzes and splits complex working trees into clean, scoped, Conventional Commits. |
| `skills/ghr/gh-release-create` | `gh-release-create` | Scans repository commit logs, calculates the next SemVer bump, and deploys a clean GitHub Release. |
| `skills/ghr/gh-pr-create` | `gh-pr-create` | Automatically bundles staged work and initiates highly descriptive, professional GitHub Pull Requests. |
| `skills/ghr/gh-pr-review` | `gh-pr-review` | Runs a localized, focused code review on active pull requests, highlighting critical flaws and fixes. |
| `skills/ghr/gh-issue-create` | `gh-issue-create` | Converts inline TODO comments or plain-text requirements directly into structured GitHub Issues. |

---

## ⚙️ Integration & Usage

These skills are registered directly by placing them under my agent's active workspace or custom configuration directory (such as `~/.claude/skills/`). 

Whenever my OpenCode agent is active in a project, it loads these `.md` instruction blocks, transforming standard LLM context into a highly deterministic workflow engine:

```bash
# Example structure inside local environment
~/.claude/skills/
├── ghr/
│   ├── gh-split-commits/
│   │   └── SKILL.md
│   └── gh-release-create/
│       └── SKILL.md
```

---

## 🏗️ Monorepo Architecture

To ensure these skills remain highly robust and easy to distribute, I maintain a strict architectural pattern:

### 1. Naming & Namespacing
* **Namespaces:** All skills are nested under logical directory namespaces (e.g., `skills/ghr/` for Git/GitHub related skills) to allow modular installations.
* **Naming Conventions:** All automation skills interacting with Git/GitHub APIs **MUST** be prefixed with `gh-` (e.g., `gh-pr-create`).
* **Config Entrypoint:** The core instructions and rules for any skill must reside inside `SKILL.md` under its respective subdirectory.

### 2. The `SKILL.md` Blueprint
Every custom skill I write strictly implements this five-part schema to guarantee deterministic AI behavior:
1. **Frontmatter (YAML):** Declares metadata including the formal name and a high-level description.
2. **Objective:** A definitive statement explaining exactly what the skill achieves.
3. **Safety Rules:** Strict boundaries defining what the skill is forbidden from doing (e.g., no force pushes, no payload exposure).
4. **Workflow:** Step-by-step instructions accompanied by explicit shell commands.
5. **Communication Contract:** Specifies exactly when and how the agent must ask for confirmation or present updates.

---

## 🤝 Version Control Conventions

I enforce **Strict Conventional Commits** across this monorepo to ensure semantic clarity:

* `feat`: A brand new skill or feature
* `fix`: A bug fix or workflow correction inside a skill
* `docs`: Updates to documentation, README, or guides
* `chore`: Maintenance tasks (like `.gitignore` or workspace adjustments)

*Note: My `gh-release-create` skill parses this commit history to automatically determine the next version of this monorepo.*



