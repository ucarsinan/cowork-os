# Choose A Tool Adapter

Use this guide to decide which AI tool context should handle a task in CoWork-OS.

The goal is not to rank tools. The goal is to route work to a suitable execution context while keeping the same rules, gates, and handoff expectations.

## Before Choosing

Clarify the task:

- What needs to be read?
- What may be changed?
- Which evidence is required?
- Which actions are high-risk?
- What approval is already granted?
- What must stay private?

If the task requires current tool-specific facts, verify against current tool documentation before relying on them.

## Routing Matrix

| Task Need | Useful Adapter Context | Typical Output | Main Risk |
|---|---|---|---|
| Inspect a repository and prepare scoped edits | Repository-aware coding agent, such as Codex or Claude Code | Patch, checks, implementation handoff | Accidental scope drift or unapproved file changes |
| Compare options or define architecture | Planning or strategy assistant | Options, trade-offs, recommendation | Confident claims without repository evidence |
| Review a change before commit or release | Review-oriented assistant | Findings, risks, missing checks, approval needs | Treating a review as approval |
| Analyze screenshots, diagrams, or interface states | Multimodal-capable assistant, such as Gemini or similar tools | Visual findings and evidence notes | Stale or incomplete context |
| Maintain public-safe lessons | Memory curation context | Generalized lesson, source references, rejection notes | Leaking private facts into public memory |
| Prepare a handoff across tools | Any adapter with strong summarization | Verified facts, assumptions, unknowns, checks, risks | Blurring facts with assumptions |

## Approval Rules

Adapter selection does not grant action permission.

These actions require explicit high-risk approval:

- commit
- push
- deploy
- delete
- publish
- change repository visibility
- create public issues or milestones
- call external systems with real effects

Edits also require task approval and must stay inside the approved scope.

## Use A Repository-Aware Adapter When

- files must be inspected directly
- a patch is expected
- tests or checks need to run
- the current repository state may differ from prior notes
- dirty worktree boundaries matter

The handoff should include changed files, checks run, checks not run, risks, and required approval.

## Use A Planning Or Review Adapter When

- the task is still ambiguous
- several implementation paths are possible
- you need a second-pass risk review
- the output should be a plan, critique, or decision brief

The handoff should label assumptions and unknowns clearly.

## Use A Multimodal Adapter When

- visual evidence matters
- screenshots or diagrams are the source
- UI layout, readability, or visual state must be inspected

The handoff should identify what was visible, what was inferred, and what still needs direct verification.

## Use Memory Curation When

- a repeated lesson should become reusable
- private facts must be rejected or generalized
- a public-safe rule or template should be proposed

Memory updates should be curated and reviewed. Never mirror raw chat logs or private records into public documentation.

## Final Check

Before handing work to an adapter, confirm:

- the task has a clear scope
- private data boundaries are understood
- the adapter is suitable for the evidence needed
- high-risk actions are still gated
- current tool details are verified when they matter
- the expected handoff format is clear
