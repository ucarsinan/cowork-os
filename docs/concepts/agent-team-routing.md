# Agent Team Routing

Agent team routing decides which responsibility profile should lead a piece of work, what that role may use as input, what it should produce, and when work must stop for review or approval.

It is not an org chart. Roles are routing labels for agentic workflows. One coding agent can play several roles in a session, but the handoff should make the active role clear.

This model is tool-agnostic and can be used with Codex, Claude Code, Gemini, or similar coding agents.

## Core Roles

| Role | When to activate | Responsibilities | Allowed inputs | Expected outputs | Handoff target |
|---|---|---|---|---|---|
| Orchestrator | Scope is unclear, work has multiple steps, or several roles are needed. | Sequence work, keep gates visible, coordinate handoffs, keep scope narrow. | User request, repository state, local rules, open risks, prior handoffs. | Plan, role routing, approval points, final handoff. | Researcher, Strategist, Architect, Implementer, Reviewer. |
| Researcher | Facts are uncertain, external sources are needed, or a technical claim may have changed. | Find evidence, compare sources, separate facts from assumptions. | Research question, source constraints, relevant docs, current repository hints. | Evidence summary, unknowns, source notes, recommended next check. | Strategist, Architect, Reviewer. |
| Strategist | Goals, non-goals, priorities, or user value need clarification. | Define target outcome, trade-offs, priorities, and acceptance criteria. | User goal, constraints, roadmap notes, risks, audience context. | Scope brief, non-goals, decision options, success criteria. | Architect, Orchestrator. |
| Architect | Structure, interfaces, boundaries, or workflow design are the central concern. | Shape the solution, define boundaries, identify coupling and risks. | Current architecture, rules, workflows, adapters, constraints, risks. | Architecture notes, impacted areas, alternatives, risk notes. | Implementer, Reviewer. |
| Implementer | A specific edit, code change, or documentation change is approved. | Make scoped changes, follow existing patterns, run appropriate checks. | Approved plan, target files, repository rules, expected checks. | Patch summary, files changed, checks run, residual risks. | Reviewer. |
| Reviewer | A patch, plan, release, or public extraction needs evaluation. | Find bugs, regressions, privacy risks, security risks, scope drift, and missing checks. | Diff, target outcome, gates, tests, rules, risk notes. | Findings, pass/fail decision, missing checks, required next approval. | Orchestrator, Implementer, Memory Curator. |
| Memory Curator | Work produced a reusable lesson or durable decision. | Propose memory candidates without storing raw session noise. | Handoffs, decisions, verification notes, source references, risks. | Memory candidate, source, truth-state, review note, privacy risk. | Reviewer, Orchestrator. |

## Routing Flow

Most work should move through a small, explicit path:

```text
intake -> route -> prepare -> implement or document -> review -> handoff -> memory candidate
```

Use the smallest role chain that fits the task:

- unclear facts: Orchestrator -> Researcher -> Reviewer
- unclear goal: Orchestrator -> Strategist -> Architect
- implementation work: Orchestrator -> Architect -> Implementer -> Reviewer
- public documentation extraction: Orchestrator -> Reviewer -> Implementer -> Reviewer
- reusable lesson: Reviewer -> Memory Curator -> Orchestrator

## Review Gates

Review gates interrupt routing when the next action may change files, publish information, or create external effects.

Stop for approval before:

- editing outside the approved scope
- committing
- pushing
- deploying
- deleting
- publishing
- changing repository visibility
- creating public issues or milestones
- exposing private or sensitive information

If a role finds a blocker, it should return a short handoff instead of continuing.

## Handling Uncertainty

Uncertainty must stay visible.

Use these labels in handoffs:

- verified facts
- assumptions
- unknowns
- checks not run
- risks
- recommended next approval

Do not let memory, handoffs, or model knowledge override current repository state when the repository can be checked.

## Memory Updates

Memory updates are proposals, not automatic writes.

A Memory Curator may suggest a durable lesson when:

- the lesson is reusable
- the source is clear
- the truth-state is explicit
- private context has been removed or rejected
- the entry is reviewed before reuse or publication

Raw chat logs, private handoffs, private project details, secrets, and unverified claims should not become public memory.

## Route-Selection Checklist

Before assigning a role, ask:

1. Is the goal clear enough to proceed?
2. Are current facts verified?
3. Is there an approved scope for edits?
4. Is a review gate required before the next action?
5. Which role can produce the next useful artifact with the least risk?
6. What handoff should the next role receive?

When in doubt, route to Reviewer or Orchestrator and keep the next action audit-only.
