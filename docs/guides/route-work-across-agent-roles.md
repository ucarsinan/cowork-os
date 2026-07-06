# Route Work Across Agent Roles

Use this guide when a task needs more structure than a single direct edit.

The goal is not to create a large team. The goal is to route work to the role that can produce the next useful artifact with clear evidence and bounded risk.

## 1. Start With Intake

Capture:

- requested outcome
- known constraints
- approved scope
- files or artifacts involved
- checks expected
- actions that require approval

If the task is unclear, keep the next step audit-only.

## 2. Pick the First Role

Use this quick router:

| Situation | First role |
|---|---|
| Scope or sequence is unclear | Orchestrator |
| Facts may be stale or external | Researcher |
| Goal, priority, or non-goal is unclear | Strategist |
| Structure or interface is unclear | Architect |
| A narrow edit is approved | Implementer |
| A change needs evaluation | Reviewer |
| A reusable lesson should be retained | Memory Curator |

## 3. Define the Handoff

Each handoff should include:

- role that just worked
- role that should work next
- verified facts
- assumptions
- unknowns
- files or artifacts touched
- checks run
- checks not run
- risks
- required approval before continuing

Do not hand off vague responsibility. Hand off the next decision or artifact.

## 4. Interrupt With Gates

Stop and request approval before:

- changing files outside scope
- committing
- pushing
- deploying
- deleting
- publishing
- changing visibility
- creating public issues or milestones
- exposing private or sensitive information

Review gates are allowed to stop work. A stopped workflow with a clear handoff is better than an unsafe continuation.

## 5. Close the Loop

At the end, report:

- what changed
- what was reviewed
- what was not changed
- checks run
- residual risks
- recommended next approval

If a durable lesson exists, route it to Memory Curator as a candidate. Do not store raw chat logs or private working notes.

## Example Routing Paths

### Documentation Extraction

```text
Orchestrator -> Reviewer -> Implementer -> Reviewer -> Memory Curator
```

Use this when a private pattern needs a public-safe rewrite.

### Feature Planning

```text
Orchestrator -> Strategist -> Architect -> Reviewer
```

Use this when the work needs scope and structure before implementation.

### Bug Fix

```text
Orchestrator -> Implementer -> Reviewer
```

Add Researcher only when the fix depends on external or changing facts.

## Tool-Agnostic Use

The same routing model can be used with Codex, Claude Code, Gemini, or similar coding agents.

The tool may change; the approval gates and handoff quality should not.
