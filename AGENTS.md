# OpenCode Skills Monorepo Guidelines

## Architecture & Naming
- This is a monorepo for custom agent skills intended to be distributed and installed across different environments.
- All skills must reside in namespace subdirectories under `skills/` (e.g., `skills/ghr/gh-split-commits/` for GitHub-related skills) to keep the root tidy and allow users to install entire namespaces.
- The primary configuration and instructions for each skill live in `skills/<namespace>/<skill-name>/SKILL.md`.
- **Naming Convention:** Skills designed for GitHub or git automation MUST be prefixed with `gh-` (e.g., `gh-pr-create`).

## Skill File Template (`SKILL.md`)
When creating or modifying a skill, the `SKILL.md` file MUST contain these specific sections:
1. **Frontmatter (YAML):** Must include `name` and `description`.
2. **Objective / Description:** Clear, concise purpose.
3. **Safety Rules:** Strict operational boundaries (e.g., restrictions on force pushing or history rewriting).
4. **Workflow:** Step-by-step execution plan, including the explicit bash commands the agent should run.
5. **Communication Contract:** Explicit rules on how the agent must interact with the user (e.g., "Wait for user confirmation before running `gh release create`").

## Version Control Conventions
- **Strict Conventional Commits:** All changes to this repository MUST use standard Conventional Commits format (`feat`, `fix`, `chore`, `docs`, etc.). This is a hard requirement as the skills in this repo (like `gh-release-create`) rely on this semantic history.

## Environment Notes
- There are currently no build tools, test runners, or CI pipelines configured. The repository consists entirely of Markdown-based agent instructions.
