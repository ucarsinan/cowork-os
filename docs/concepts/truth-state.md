# Truth State

Truth-state defines how CoWork-OS labels evidence, assumptions, and memory.

It prevents old notes, handoffs, or model assumptions from being treated as current facts.

## Source Priority

When information conflicts, use this priority:

1. Current user instruction
2. Current repository state
3. Repository-local rules and documentation
4. Verified project record
5. Handoffs and memory
6. General model knowledge

## States

| State | Meaning | Required handling |
|---|---|---|
| `verified` | Current evidence supports the statement. | Include the source or review basis when the fact can drift. |
| `candidate` | The statement may be useful but still needs confirmation. | Use it as a prompt for review, not as a fact. |
| `unverified` | The statement has not been checked. | Label it clearly and do not make decisions from it alone. |
| `deprecated` | The statement is no longer current. | Keep only when historical context is useful, and point to the replacement. |

## Rules

- Do not promote `candidate` or `unverified` entries to `verified` without evidence.
- Do not use memory as the highest source of truth when repository state can be checked.
- Do not publish private evidence to make a public claim look stronger.
- Mark checks that were not run instead of implying they passed.
- Re-check drift-prone facts before relying on them.

## Public-Safe Use

Public documentation may explain truth-state labels, but it must not expose private sources.

Use generic references such as:

```text
truth_state: candidate
source_type: reviewed workflow pattern
last_reviewed: YYYY-MM-DD
```

Avoid private paths, real project names, customer details, person names, or raw handoff text.
