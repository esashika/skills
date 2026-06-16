---
name: gh-release-create
description: Calculate the next Semantic Version (SemVer) based on Conventional Commits history and create a GitHub Release.
---

# GitHub Release Create

Use this skill to automatically calculate the next version number and create a formal release on GitHub, leveraging the repository's Conventional Commits history.

## Objective
Read the git history since the last version tag, apply Semantic Versioning (SemVer) rules based on commit types, and execute the GitHub CLI to publish the release.

## SemVer Calculation Rules
1. **Find Last Version:** Identify the most recent tag (e.g., `v1.2.3`).
2. **Analyze Commits:** Examine all commits between the last tag and `HEAD`.
3. **Calculate Bump:**
   - **MAJOR:** If ANY commit contains a breaking change indicator (`!` in the type/scope or `BREAKING CHANGE:` footer). Example: `v1.2.3` -> `v2.0.0`.
   - **MINOR:** If NO breaking changes exist, but there is at least one `feat` commit. Example: `v1.2.3` -> `v1.3.0`.
   - **PATCH:** If NO breaking changes and NO `feat` commits exist (only `fix`, `chore`, `docs`, etc.). Example: `v1.2.3` -> `v1.2.4`.

## Safety Rules
- Do not create tags or releases without explicit user confirmation of the calculated version.
- Do not push directly to protected branches as part of this workflow.
- Handle repositories with no previous tags gracefully (default to `v1.0.0` or ask the user).

## Workflow

### 1) Analyze State
```bash
git fetch --tags
git describe --tags --abbrev=0
```
*(If no tags exist, notify the user).*

```bash
git log <last_tag>..HEAD --oneline
```

### 2) Calculate Next Version
Apply the SemVer Calculation Rules to determine the new version string.

### 3) Confirm with User
Present the findings:
- Current version
- Summary of changes (Counts of Features, Fixes, Breaking Changes)
- Calculated Next Version

Ask: "Do you want to proceed with creating release <Next Version>?"

### 4) Execute Release
Using GitHub CLI (`gh`), create the release and auto-generate release notes.
```bash
gh release create <Next Version> --generate-notes -t "Release <Next Version>"
```

## Communication Contract
- Be highly concise.
- Clearly present the version bump calculation logic (e.g., "Found 1 'feat' commit -> Minor version bump").
- Always wait for user approval before executing the `gh release create` command.
