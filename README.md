# OpenCode Skills Repository

A monorepo containing a collection of custom agent skills designed to automate and enforce standards in software engineering tasks, specifically tailored for Git, GitHub, and other advanced development workflows.

---

## 📂 Repository Structure

All custom skills are organized by namespace inside the `skills/` directory to keep the workspace tidy and modular.

### Custom Git & GitHub Skills (`ghr/`)

- **`skills/ghr/gh-split-commits`**: Intelligently splits mixed working tree changes into scoped, Conventional Commits compliant commits.
- **`skills/ghr/gh-release-create`**: Analyzes git history, calculates the next Semantic Version (SemVer), and automatically creates a GitHub Release.
- **`skills/ghr/gh-pr-create`**: Automates the creation of professional GitHub Pull Requests.
- **`skills/ghr/gh-pr-review`**: Performs focused local code reviews on Git/GitHub Pull Requests.
- **`skills/ghr/gh-issue-create`**: Automatically creates GitHub Issues from code comments or descriptions.

---

## 🛠️ Monorepo Guidelines

### Architecture & Naming
- **Namespaces:** Skills reside in namespace subdirectories under `skills/` (e.g., `skills/ghr/`) to facilitate bulk installation and clean organization.
- **Naming Convention:** Any skill designed for GitHub or Git automation **MUST** be prefixed with `gh-` (e.g., `gh-pr-create`).
- **Main Config:** The primary configuration, workflows, and prompts for each skill live in `skills/<namespace>/<skill-name>/SKILL.md`.

### Skill Template Standard (`SKILL.md`)
Every skill in this repository strictly adheres to a standard template ensuring consistent, safe execution and predictable user interaction:

1. **Frontmatter (YAML):** Contains metadata such as the skill `name` and `description`.
2. **Objective / Description:** Clear, concise purpose of the skill.
3. **Safety Rules:** Strict boundaries and operational safety constraints (e.g., restrictions on force pushing, data loss, etc.).
4. **Workflow:** Step-by-step execution plan, detailing the explicit bash commands and reasoning patterns.
5. **Communication Contract:** Explicit rules defining how the agent must interact, seek confirmation, or report progress to the user.

---

## 🤝 Version Control Conventions

This project uses **Strict Conventional Commits** to keep history clean and structured:
- `feat`: A new feature / skill
- `fix`: A bug fix in a skill or config
- `docs`: Documentation updates (like this README)
- `chore`: Maintenance tasks (like .gitignore configuration)

These commits are scanned by release-creation skills to automatically increment SemVer tags and generate changelogs.

