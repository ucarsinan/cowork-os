# Rule: Memory Hygiene

Memory must be useful, source-aware, truth-state aware, and privacy-safe.

## Store

Store a memory entry only when it is reusable and reviewed.

Good candidates include:

- stable decisions
- verified project facts
- recurring risks
- reusable workflow lessons
- architecture or review patterns
- tool-agnostic operating rules

## Do Not Store

Do not store:

- secrets, tokens, credentials, or `.env` values
- private data
- raw chat logs
- noisy session history
- unverified claims as facts
- copied third-party text without permission
- private project, customer, person, path, or domain details in public-safe memory

## Truth-State

Every memory entry should use one of these states:

- `verified`: supported by current evidence
- `candidate`: useful but still under review
- `unverified`: not proven or not recently checked
- `deprecated`: retained for context but no longer current

If a fact can drift, include a last-reviewed date or equivalent review note.

## Public-Safe Rule

Public-safe memory is not a copy of private memory. It is a reviewed generalization.

Before moving a lesson into public documentation:

1. Remove private identifiers.
2. Replace real examples with synthetic examples.
3. Keep only the reusable pattern.
4. Mark the truth-state.
5. Use generic `source_refs`.
6. Run privacy and security review.

## Stop Conditions

Stop and keep the entry private when:

- the lesson depends on private context
- private identifiers cannot be removed
- the source is unclear
- the entry includes sensitive operational details
- the public version would imply automatic private-to-public sync
