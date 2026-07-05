# Workflow: Audit-Only Onboarding

Audit-only onboarding is the safest first step when an AI coding agent enters a repository, project folder, or unfamiliar work context.

The goal is to understand the current state before making changes. In audit-only mode, the agent reads, verifies, classifies risk, and reports. It does not edit, commit, push, deploy, delete, publish, or trigger external systems.

This workflow is tool-agnostic. It can be used with Codex, Claude Code, Gemini, or similar coding agents as long as the agent can follow the same approval boundaries.

## Purpose

Use audit-only onboarding to create a reliable starting point for later work.

The workflow should answer:

- What is the current repository or project state?
- Which local rules and documentation apply?
- What is verified, assumed, unknown, or not checked?
- What risks or blockers exist?
- What approval is needed before any change?

## When To Use It

Use this workflow when:

- opening a repository for the first time
- returning to a project after a break
- receiving a handoff that may be stale
- seeing a dirty worktree
- preparing a review before edits
- checking whether public documentation is safe to update
- comparing user instructions with local repository rules
- any task could affect files, Git history, deployments, publication, or external systems

## Required Inputs

Start with the smallest available context:

- user request or task goal
- target repository or folder
- known constraints or approval boundaries
- local instructions, if present
- expected output format, if provided
- any specific files, branches, or artifacts to inspect

If the target is unclear, stop and ask for the target before inspecting or changing anything.

## Allowed Actions

In audit-only mode, the agent may:

- read files and directory structure
- inspect Git status, branch, log, and remotes
- read local rules, documentation, templates, and configuration
- inventory scripts, tests, build commands, and deployment hints
- identify risks, unknowns, stale claims, and missing context
- report verified facts and assumptions separately
- recommend the next smallest approval-gated step

## Forbidden Actions

In audit-only mode, the agent must not:

- edit, create, move, rename, delete, format, or overwrite files
- stage, commit, push, tag, release, or change remotes
- deploy, publish, migrate, or run infrastructure changes
- install dependencies or run commands with meaningful side effects
- call external APIs with real effects
- open public issues, milestones, projects, or release records
- store assumptions as verified facts
- expose secrets, credentials, private paths, or private operational data

No-side-effect rule: if an action can change local files, Git state, external systems, public visibility, or production data, it is outside audit-only mode unless a later explicit approval grants that specific action.

## Audit Steps

1. Restate the task and non-goals.
2. Confirm the target repository or folder.
3. Inspect repository state:
   - current branch
   - dirty worktree
   - recent relevant commits
   - configured remotes
4. Read local instructions and documentation:
   - `AGENTS.md`
   - `README.md`
   - `CONTRIBUTING.md`
   - `SECURITY.md`
   - project-specific docs or rules
5. Inventory project structure:
   - main directories
   - package or build files
   - test, lint, and formatting commands
   - deployment or CI hints
6. Compare claims against current evidence.
7. Classify findings:
   - verified facts
   - assumptions
   - unknowns
   - checks not run
   - risks
8. Identify stop conditions or approval gates.
9. Recommend the next smallest safe step.
10. Produce a handoff.

## Output Handoff

The handoff should be concise and evidence-oriented.

Recommended structure:

```text
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
[smallest next approval needed]
```

## Stop Conditions

Stop audit-only work and report a blocker when:

- the target path or repository is unclear
- local instructions conflict with the user request
- secrets or credentials are found
- the worktree contains unexpected changes
- the task would require file changes
- the task would require Git write operations
- the task would affect a deployment, publication, database, or external system
- the agent cannot separate verified facts from assumptions

## Approval Gates

| Gate | Required before |
|---|---|
| Task approval | creating or editing files |
| Command approval | running commands with possible side effects |
| Commit approval | staging or committing changes |
| External approval | pushing, publishing, deploying, migrating, or changing remotes |
| Release approval | tagging, releasing, or changing public visibility |

When the needed approval is missing, keep the result audit-only and ask for the smallest specific approval.
