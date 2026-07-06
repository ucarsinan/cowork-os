# Tool Adapters

Tool adapters describe how an AI tool can participate in CoWork-OS without becoming part of the core rules.

CoWork-OS treats tools as interchangeable execution contexts. A tool may be useful for repository work, planning, review, multimodal analysis, or handoff writing, but the control plane stays in the Markdown rules, workflows, reviews, and approval gates.

## Core Rule

Adapter capability is not approval.

If a tool can edit files, run commands, create commits, push code, deploy, delete data, publish content, or change visibility, that only describes a possible capability. It does not grant permission to use it. High-risk actions still require the relevant CoWork-OS approval gate.

## What An Adapter Documents

Each adapter should describe:

- execution model
- file access model
- approval model
- memory and context handling
- review and handoff behavior
- strengths
- risks
- when to use it
- checks that should be run before relying on its output

Adapters must not weaken core rules.

## Comparison Dimensions

Use these dimensions when comparing tools such as Codex, Claude Code, Gemini, Antigravity, or similar coding agents.

| Dimension | What To Capture | Public-Safe Guidance |
|---|---|---|
| Execution model | How the tool performs work | Describe the work mode, not a ranking. |
| File access | Whether it can inspect or edit repository files | Mark access as context-dependent. |
| Approval model | Which actions require explicit permission | Keep edits, commits, pushes, deploys, deletes, publication, and visibility changes gated. |
| Memory/context handling | How context is provided or retained | Do not assume raw chat history or private memory is safe to reuse. |
| Review handoff | How results are summarized for the next agent or human | Require facts, assumptions, checks not run, risks, and next approval. |
| Strengths | Where the adapter is likely useful | Keep claims conservative and task-based. |
| Risks | Where misuse or overconfidence can happen | Include stale tool knowledge, missing file access, and unverified output. |
| Use cases | When to select the adapter | Route by task need and evidence, not brand preference. |

## Stable And Unstable Claims

Stable claims are general workflow principles, such as:

- repository-aware tools can be useful for implementation when file access is available
- chat or planning tools can be useful for strategy, critique, and handoff drafting
- multimodal tools can be useful for reviewing screenshots, diagrams, or visual evidence
- all tools need review gates before high-risk actions

Unstable claims must be verified against current tool documentation before publication or operational use:

- exact feature availability
- model names
- pricing
- quotas and limits
- account or subscription behavior
- plugin, connector, or IDE support
- default retention or memory behavior

When current tool details matter, write: "verify against current tool documentation."

## Adapter Selection

Choose an adapter by the work to be done:

- Use a repository-aware coding context when the task requires file inspection, edits, tests, or commit preparation.
- Use a planning or strategy context when the task requires options, architecture critique, or decision framing.
- Use a review context when the task requires risk finding, quality gates, or release readiness checks.
- Use a multimodal context when the task depends on screenshots, diagrams, interface states, or visual evidence.
- Use a memory-curation context when the task is to turn a lesson into public-safe, generalized knowledge.

The selected adapter must still follow the same truth-state, memory, privacy, security, review, and approval rules.

## Handoff Expectations

An adapter handoff should separate:

- verified facts
- assumptions
- unknowns
- checks run
- checks not run
- risks
- recommendations
- required approval before the next action

This keeps work portable across tools and prevents one adapter from becoming the hidden source of truth.
