# Run an Audit-Only Session

An audit-only session lets an AI coding agent inspect a project before changing it. Use it as the first move when context is incomplete, the repository is unfamiliar, or the next action could affect files, Git history, deployments, or public documentation.

Audit-only mode is not a weaker implementation mode. It is a separate operating mode with one rule: no side effects.

## Before You Start

Prepare three inputs:

- the task or question to investigate
- the repository or folder to inspect
- any approval boundaries, such as "read only" or "do not commit"

If the target is missing, ask for it before proceeding.

## Start From The Prompt

Use `prompts/audit-only-bootstrap.md` as the session starter.

Paste or adapt it for the coding agent you use. The workflow works with Codex, Claude Code, Gemini, or similar agents, as long as the agent respects the same boundaries.

## Session Flow

1. Confirm the target.
2. Read the current task.
3. Inspect Git status, branch, recent commits, and remotes.
4. Read local rules and documentation.
5. Inventory the project structure and important commands.
6. Identify risks, blockers, stale claims, and missing context.
7. Separate findings into verified facts, assumptions, unknowns, checks not run, and recommendations.
8. Produce a handoff.
9. Ask for the next approval before making any change.

## What The Agent May Do

The agent may:

- read source files and documentation
- inspect repository status
- list commands that appear relevant
- identify likely test or build paths
- summarize risks and unknowns
- recommend the next safe step

The agent must not:

- edit files
- create files
- delete or move files
- stage or commit changes
- push to a remote
- deploy or publish
- open issues or milestones
- run commands that change state without approval

## Classify Findings

Use strict labels.

Verified facts:

- facts supported by current files, Git state, or explicit user instructions

Assumptions:

- plausible but unverified interpretations

Unknowns:

- information that is missing or cannot be confirmed from the available context

Checks not run:

- useful checks that were skipped, with the reason

Recommendations:

- next actions, each tied to the approval needed

## Handoff Template

```text
Audit-only handoff

Target:
[repository or folder]

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

Recommended next step:
- [...]

Required approval:
[specific approval needed]
```

## Example Scenario

A user asks an agent to "fix the failing build" in `sample-api`.

In audit-only mode, the agent should:

- inspect the repository state
- read local instructions
- identify the build command
- check whether the worktree is dirty
- report likely next steps

The agent should not edit code, install packages, run a destructive command, commit, or push until the user approves the next phase.

## Completion Criteria

An audit-only session is complete when the handoff clearly states:

- what was inspected
- what is verified
- what is assumed
- what remains unknown
- which checks were not run
- what risks exist
- what approval is needed next

If the answer cannot make that separation, the session should stay in audit mode.
