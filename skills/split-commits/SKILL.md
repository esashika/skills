---
name: split-commits
description: Split Git commits by diff hunks to create clean, scoped, and Conventional Commits compliant changes.
---

# Split Commits

Use this skill to turn a mixed working tree into clean, scoped commits following the Conventional Commits specification.

## Strict Conventional Commits Rules

Every commit message MUST strictly follow the conventionalcommits.org specification:
- **Format:** `<type>[optional scope]: <description>`
- **Blank Line:** A blank line MUST separate the description from the body.
- **Primary Types:** Use `feat` for new features and `fix` for bug fixes.
- **Auxiliary Types:** Use `build`, `chore`, `ci`, `docs`, `style`, `refactor`, `perf`, `test` appropriately.
- **Breaking Changes:** If the diff introduces a breaking change, append a `!` after the type/scope (e.g., `feat(api)!: remove legacy endpoint`) AND/OR include a `BREAKING CHANGE:` footer in the body.
- **Grouping:** Group staged hunks primarily by the semantic type they represent. Do not mix a `feat` and a `test` in the same commit if they can be cleanly separated.

## Safety Rules

- Never run destructive git commands (`reset --hard`, `checkout --`, force push) unless the user explicitly asks.
- Never rewrite history (`commit --amend`, rebase) unless the user explicitly asks.
- Never commit secrets or credential-like files (`.env`, key files, token dumps).
- If pre-commit hooks modify files, include those modifications in a new commit unless the user asks otherwise.
- If there are no real changes, do not create an empty commit.

## Workflow

### 1) Inspect the repository state
Run these first:
```bash
git status --short
git diff
git diff --cached
git log -n 12 --pretty=format:"%h %s"
```

### 2) Build a commit grouping plan
Create a grouping proposal before staging based on the Conventional Commits rules. Keep dependent changes together when splitting would break tests/build.

For each proposed group, define:
- Type and Scope (e.g., `feat(auth)`)
- Files/hunks included
- Rationale
- Commit message draft (adhering strictly to Conventional Commits)

### 3) Stage and Commit
Execute the staging process (`git add` or `git add -p`).
After staging the exact hunks for a group, create the commit.

### 4) Final verification
Check the final log to ensure all commits match the conventional format.
```bash
git log --oneline -n <number_of_new_commits>
git status
```

## Communication Contract
1. Briefly summarize the current diff shape.
2. Show the proposed commit groups categorized by conventional types.
3. Ask for confirmation before modifying the index or creating commits.
4. Execute staging + commit per group.
5. Report the final commit list.
