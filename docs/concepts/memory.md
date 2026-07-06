# Memory

Memory stores reusable knowledge that helps an agentic workflow stay consistent across sessions.

In CoWork-OS, memory is curated documentation. It is not a raw chat log, transcript archive, or automatic mirror of a private workspace.

This model works with Codex, Claude Code, Gemini, or similar coding agents because it treats memory as a reviewable artifact instead of a tool-specific feature.

## Memory Buckets

### Private Memory

Private memory is any information that only belongs inside a private workspace or private project context.

It can include:

- private project decisions
- private implementation history
- private handoffs
- local workflow notes
- internal risks or constraints
- non-public business or customer context

Private memory must not be copied into public documentation.

### Public-Safe Memory

Public-safe memory is a generalized version of a lesson that can stand on its own without exposing private context.

It can include:

- a generic workflow rule
- a reusable review pattern
- a neutral architecture lesson
- a tool-agnostic operating principle
- a synthetic example

Public-safe memory must be reviewed before publication.

### Generalized Lessons

A generalized lesson turns a private observation into a reusable public rule.

Examples:

| Input | Public-safe result |
|---|---|
| A private fact includes a customer name or local path. | Rejected. Do not publish it. |
| A private project had outdated status notes. | Generalized lesson: when records and repository state conflict, verify the repository state first. |
| An assumption was useful earlier but is no longer current. | Mark it as `deprecated` and explain what replaced it. |

### Rejected / Non-Public Information

Reject memory for public use when it includes:

- secrets, tokens, credentials, or `.env` values
- personal data
- customer, employer, or organization details
- private project names or local file paths
- private handoffs or raw working notes
- sensitive logs or operational identifiers
- third-party text copied without permission
- unverified claims presented as facts

## Truth-State

Every memory entry should make its truth-state clear.

| State | Meaning | Use it when |
|---|---|---|
| `verified` | The entry is backed by current evidence. | A recent check, source, or review supports the statement. |
| `candidate` | The entry may be useful, but still needs review. | A pattern has been observed but is not yet stable. |
| `unverified` | The entry is not proven. | The source is missing, old, or unchecked. |
| `deprecated` | The entry used to be useful but should not guide new work. | A newer rule, file, or workflow replaced it. |

Never use memory state as proof by itself. `verified` still needs a source, date, or review note when the information can drift.

## Public-Safe `source_refs`

Public memory can cite generic sources without exposing private details.

Use public-safe references such as:

```text
source_refs:
  - type: review_pattern
    status: verified
    last_reviewed: YYYY-MM-DD
    notes: "Generalized from a reviewed workflow pattern."
```

Do not include:

- private file paths
- real customer, project, or person names
- private repository names
- operational identifiers
- raw chat excerpts
- secret names or values

## No Auto-Sync

Public memory is curated, reviewed, and generalized.

It must never be:

- raw chat logs
- automatic private-to-public mirroring
- a dump of private notes
- a copy of private handoffs
- a sync target for private memory files

The safe path is:

1. Identify a private or local lesson.
2. Remove private context.
3. Rewrite it as a generic rule or example.
4. Mark truth-state and source type.
5. Review privacy, security, usefulness, and documentation quality.
6. Publish only after explicit approval.

## Review Checklist

Before a memory entry becomes public-safe, confirm:

- it is useful without private context
- it contains no secrets or personal data
- it does not identify a private project, customer, person, path, or domain
- its truth-state is explicit
- assumptions are not presented as facts
- examples are synthetic
- the entry is tool-agnostic
- publication was explicitly approved
