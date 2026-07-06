# Onboard a Repository

Repository onboarding turns an unfamiliar codebase into a documented working context before an agent changes anything. In CoWork-OS, onboarding is audit-only by default: the agent may inspect, classify, and report, but it must not edit files, commit, push, delete, deploy, publish, or change visibility unless a later phase explicitly approves that action.

This guide works with Codex, Claude Code, Gemini, or similar coding agents. The tool can change, but the approval boundary stays the same.

## Purpose

Use repository onboarding to answer three questions:

- What is currently true about this repository?
- What remains assumed, unknown, risky, or unchecked?
- What is the next safe action, and which approval does it require?

Onboarding does not verify a project by itself. It produces a reviewable handoff that keeps facts, assumptions, and gaps separate.

## When To Use

Use this workflow when:

- the repository is new to the agent
- the worktree may already contain user changes
- the task could affect files, Git history, deployments, or public documentation
- existing documentation may be stale
- the next action depends on build, test, or architecture reality

Do not use it as an auto-onboarding system. A human still decides whether the handoff is good enough to approve changes.

## Required Inputs

Provide:

- target repository or folder
- task or question
- approval boundary, such as "audit only" or "do not commit"
- any known constraints, such as protected branches, required checks, or forbidden actions

If the target or approval boundary is unclear, stop and ask before continuing.

## Allowed Actions

During onboarding, the agent may:

- inspect files and folders
- read repository-local rules and documentation
- inspect Git status, branch, remotes, and recent commits
- identify likely build, test, lint, and run commands
- map architecture, entry points, and data flow from current files
- classify verified facts, assumptions, unknowns, risks, and checks not run
- recommend the next safe action

## Forbidden Actions

During onboarding, the agent must not:

- edit, create, delete, move, or format files
- stage or commit changes
- push to a remote
- deploy, publish, migrate, or change visibility
- create issues, milestones, projects, or releases
- install dependencies or run state-changing commands without approval
- mark project records as verified without evidence
- treat memory, old handoffs, or model knowledge as current repository truth

Capability is not approval. If a tool can edit, commit, push, or deploy, that only means the action is technically possible. It still requires the appropriate gate.

## Preflight Checks

Start with lightweight checks:

```text
Repository target:
[path or repository name]

Current branch:
[branch]

Worktree status:
[clean/dirty/unknown]

Remote status:
[remote list or unknown]

Local rules found:
[AGENTS.md, CONTRIBUTING.md, docs, or none found]

Requested boundary:
[audit-only / task approval / high-risk approval]
```

If the worktree is dirty, do not clean it. Record the state and avoid overwriting user work.

## Repository Map

Create a compact map that helps the next phase navigate the project:

```text
Repository map:
- Purpose: [one-sentence description from current files]
- Main languages/frameworks: [observed stack]
- Entry points: [files or commands]
- Important directories: [path -> role]
- Local rules: [rules files read]
- Build/test commands found: [command -> source]
- External systems mentioned: [none / generic service type / unknown]
```

Only mark items as observed when they come from current files, Git state, or explicit user instructions.

## Truth-State Capture

Separate every important statement into one of these groups:

Verified facts:

- supported by current files, Git state, command output, or explicit user instruction

Assumptions:

- plausible interpretations that still need confirmation

Unknowns:

- missing information that blocks confident action

Not-run checks:

- useful checks skipped during onboarding, with the reason

Risks:

- anything that could cause data loss, privacy exposure, broken builds, bad commits, or misleading documentation

Next safe actions:

- recommended next steps, each tied to the approval required

## Architecture And Risk Capture

For architecture, record only what can be inferred from the repository:

```text
Architecture notes:
- Runtime: [observed or unknown]
- Data/storage: [observed or unknown]
- External integrations: [observed or unknown]
- Test surface: [observed or unknown]
- Deployment surface: [observed or unknown]
```

For risk, keep the evidence visible:

```text
Risk:
- Description: [risk]
- Evidence: [file, command output, or unknown]
- Impact: [low/medium/high]
- Mitigation: [next safe action]
- Approval required: [none/task/high-risk]
```

## Open Questions

Ask only questions that materially change the next safe action. Good onboarding questions are specific:

- "Should I treat this dirty worktree as user-owned and avoid formatting changes?"
- "Which test command should be considered authoritative?"
- "Is deployment out of scope for this phase?"

Avoid broad questions that the repository can answer by inspection.

## Handoff Format

Use this handoff at the end of onboarding:

```text
Repository onboarding handoff

Target:
[repository or folder]

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

Not-run checks:
- [check] - [reason]

Repository map:
- [...]

Architecture notes:
- [...]

Risks:
- [...]

Next safe actions:
- [action] - requires [approval]

Stop conditions encountered:
- [...]

Required approval:
[specific next approval]
```

## Stop Conditions

Stop and report instead of continuing when:

- the target repository is unclear
- Git status shows unexpected changes that affect the task
- local rules conflict with the requested action
- the next step would modify files, Git history, deployments, or public visibility
- a command could install, delete, migrate, publish, or contact external systems
- private or sensitive information appears in a public-facing context
- the agent cannot separate verified facts from assumptions

## Approval Gates

Use these gates:

| Gate | Required for |
|---|---|
| Read/analyze/report | default onboarding actions |
| Task approval | file edits, generated files, dependency changes, non-destructive state changes |
| High-risk approval | commit, push, deploy, delete, publish, migrate, visibility changes, external-system effects |

When approval is ambiguous, stop and request the smallest specific approval.

## Synthetic Example

For a synthetic repository named `sample-api`, an onboarding handoff might say:

```text
Verified facts:
- The repository contains an API service and a test directory.
- The README lists a test command.

Assumptions:
- The listed test command is intended to be the default verification path.

Unknowns:
- Deployment target is not documented.

Not-run checks:
- Tests not run - audit-only phase did not include execution approval.

Risks:
- The worktree is dirty, so formatting or broad edits could overwrite user work.

Next safe actions:
- Request task approval to run the documented tests.
- Request task approval before editing files.
```

The example is synthetic. Replace it with current repository evidence when you run the workflow.
