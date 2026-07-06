# Agents

Agents are responsibility profiles for routing work through CoWork-OS.

They are not autonomous authorities. A role can recommend, inspect, write, or review only inside the current approval boundary.

Use agent files to define:

- mission
- activation trigger
- allowed inputs
- expected outputs
- boundaries
- stop rules

## Core Routing Roles

| Role | Primary use |
|---|---|
| Orchestrator | Coordinates scope, sequence, gates, and handoffs. |
| Researcher | Verifies external facts and separates evidence from assumptions. |
| Strategist | Clarifies goals, non-goals, priorities, and success criteria. |
| Architect | Defines structure, boundaries, interfaces, and trade-offs. |
| Implementer | Makes approved scoped changes and reports checks. |
| Reviewer | Finds defects, risks, missing checks, and scope drift. |
| Memory Curator | Proposes durable, reviewed, privacy-safe learnings. |

## Routing Rule

Use the smallest role chain that can safely produce the next artifact.

Examples:

- unclear facts -> Researcher
- unclear goal -> Strategist
- unclear structure -> Architect
- approved edit -> Implementer
- completed patch -> Reviewer
- reusable lesson -> Memory Curator

High-risk actions still require explicit approval, including commit, push, deploy, delete, publish, visibility changes, public issues, and milestones.

For the full routing model, see `docs/concepts/agent-team-routing.md`.
