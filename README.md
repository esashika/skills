# Opencode Skills Repository

A monorepo containing a collection of custom skills designed to automate and enforce standards in software engineering tasks, specifically tailored for Git and GitHub workflows.

## Directory Structure

All individual skills are located in the `skills/` directory.

- **`split-commits`**: Intelligently splits mixed working tree changes into scoped, Conventional Commits compliant commits.
- **`gh-release-create`**: Analyzes the git history, calculates the next Semantic Version (SemVer), and creates a GitHub Release.
- **`gh-pr-create`**: Automates the creation of GitHub Pull Requests.
- **`gh-pr-review`**: Performs focused local code reviews on GitHub Pull Requests.
- **`gh-issue-create`**: Automatically creates GitHub Issues from code comments or descriptions.

## Skill Template Standard

Every skill in this repository strictly adheres to a standard `SKILL.md` template ensuring consistent behavior and communication:

1. **Frontmatter:** Identifies the skill name and description.
2. **Objective:** Clear purpose of the skill.
3. **Safety Rules:** Strict boundaries on what the skill cannot do.
4. **Workflow:** Step-by-step execution plan.
5. **Communication Contract:** Rules on how the AI should interact with the user.
