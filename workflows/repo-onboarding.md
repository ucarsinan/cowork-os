# Workflow: Repo Onboarding

## Purpose

Create a reliable repository context before changing a codebase. The workflow is audit-only by default and produces a handoff that separates evidence from assumptions.

## When To Use

Use this workflow when a repository is unfamiliar, documentation may be stale, the worktree may contain user changes, or the requested task could lead to file edits, commits, pushes, deployments, deletes, publication, or visibility changes.

## Inputs

- target repository or folder
- task or question
- explicit approval boundary
- known constraints or forbidden actions

## Allowed Actions

- read files and repository-local documentation
- inspect Git status, branch, remotes, and recent commits
- identify likely build, test, lint, and run commands
- map architecture, workflows, and risk areas
- report verified facts, assumptions, unknowns, not-run checks, risks, and next safe actions

## Forbidden Actions

- edit, create, delete, move, or format files
- stage, commit, or push
- deploy, publish, migrate, or change visibility
- create issues, milestones, projects, or releases
- run commands with side effects without approval
- mark a project as verified without current evidence

## Steps

1. Confirm the target and approval boundary.
2. Inspect Git status, branch, remotes, and recent commits.
3. Read local rules, README files, contributor guidance, and relevant docs.
4. Inventory important directories, entry points, and configuration files.
5. Identify build, test, lint, run, and deploy commands from current files.
6. Capture truth-state:
   - verified facts
   - assumptions
   - unknowns
   - not-run checks
   - risks
   - next safe actions
7. Map architecture and risk areas from evidence.
8. Stop before any side effect.
9. Produce the onboarding handoff.

## Handoff

Use `templates/REPO_ONBOARDING.md` when available.

The handoff must state:

- target
- mode
- files changed
- verified facts
- assumptions
- unknowns
- not-run checks
- repository map
- architecture notes
- risks
- next safe actions
- stop conditions
- required approval

## Completion Criteria

The workflow is complete when a reviewer can see what was inspected, what is verified, what remains uncertain, and what approval is required before any action with side effects.
