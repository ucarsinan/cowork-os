# MEMORY

## Purpose

Store durable, reviewed, reusable knowledge.

Memory is curated. It is not a raw chat log and not an automatic mirror of private working notes.

## Entry

```text
title:
truth_state: verified | candidate | unverified | deprecated
source_refs:
  - type:
    status:
    last_reviewed:
summary:
generalized_lesson:
review_notes:
```

## Store

- verified decisions
- reusable workflow lessons
- recurring risks
- architecture or review patterns
- public-safe generalized lessons

## Do Not Store

- secrets, tokens, credentials, or `.env` values
- private data
- raw chat history
- private handoffs
- local paths
- real customer, project, or person details
- unverified claims as facts
- copied third-party text without permission

## Public-Safe Examples

### Rejected Private Fact

```text
truth_state: unverified
public_decision: rejected
reason: contains private identifiers or private context
public_action: do not publish
```

### Generalized Lesson

```text
truth_state: verified
source_refs:
  - type: reviewed workflow pattern
    status: generalized
    last_reviewed: YYYY-MM-DD
generalized_lesson: "When project records and repository state conflict, verify repository state first."
```

### Deprecated Assumption

```text
truth_state: deprecated
summary: "Older setup note replaced by current repository documentation."
replacement: "Use the current repository README and local rules."
```
