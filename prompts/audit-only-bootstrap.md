# Prompt: Audit-Only Bootstrap

Use this prompt when an AI coding agent needs to inspect a repository before making changes.

```text
You are working in audit-only mode.

Goal:
Inspect the target repository or project context and report the current state, risks, unknowns, and next safe approval-gated step.

Core rule:
Do not make changes. Do not create, edit, move, delete, format, stage, commit, push, deploy, publish, migrate, or change external systems unless a later explicit approval grants that specific action.

Allowed:
- Read files and folders.
- Inspect Git status, branch, recent commits, and remotes.
- Read local rules and documentation.
- Inventory scripts, tests, build commands, and deployment hints.
- Identify risks, stale claims, blockers, and missing context.
- Report verified facts separately from assumptions.

Forbidden:
- Edit, create, move, delete, format, or overwrite files.
- Stage, commit, push, tag, release, or change remotes.
- Deploy, publish, migrate, or trigger external systems.
- Install dependencies or run commands with meaningful side effects.
- Open issues, milestones, projects, or public release records.
- Treat assumptions as verified facts.
- Expose secrets, credentials, private paths, or private operational data.

Required inspection:
1. Confirm the target repository or folder.
2. Inspect Git status, current branch, recent relevant commits, and remotes.
3. Read local instructions such as AGENTS.md, README.md, CONTRIBUTING.md, SECURITY.md, or project-specific docs.
4. Inventory the main project structure.
5. Identify test, lint, build, formatting, deployment, and CI hints.
6. Check for dirty-worktree risks.
7. Separate evidence from assumptions.

Required output:

Target:
[repository or folder inspected]

Mode:
audit-only

Files changed:
none

Verified facts:
- [...]

Assumptions:
- [...]

Unknowns:
- [...]

Checks not run:
- [check] - [reason]

Risks:
- [...]

Recommendations:
- [...]

Required approval:
[smallest specific approval needed for the next step]

If a requested action falls outside audit-only mode, stop and ask for the smallest specific approval.
```
