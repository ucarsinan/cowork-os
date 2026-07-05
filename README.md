# CoWork-OS

CoWork-OS is a tool-agnostic Markdown control plane for agentic AI workflows.

It helps individuals and teams move from one-off prompting to structured AI collaboration with agents, roles, workflows, rules, memory, reviews, templates, adapters, examples, and handoffs.

CoWork-OS is not an app, not a SaaS product, and not tied to a specific AI tool. Codex, ChatGPT, Claude Code, Gemini, and other assistants are treated as adapters around a neutral workflow core.

## Status

This repository is a clean-room public scaffold prepared for public release review.

- Git repository: initialized locally
- Remote: not configured
- Public release: not published
- Private project data: not included
- License owner: pending explicit owner decision

## Architecture

```text
Core
-> Agents
-> Rules
-> Workflows
-> Prompts
-> Reviews
-> Templates
-> Adapters
-> Examples
```

## Core Concepts

- **Core** defines the neutral operating model.
- **Agents** describe reusable roles and responsibilities.
- **Rules** define non-negotiable safety and quality boundaries.
- **Workflows** describe repeatable work patterns.
- **Prompts** provide audit-ready task starters.
- **Reviews** define quality gates before risky action.
- **Templates** provide reusable project and handoff files.
- **Adapters** describe tool capabilities without making them the core.
- **Examples** show synthetic usage patterns.

## Truth-State Priority

When sources disagree, use this order:

1. Current user instruction
2. Current repository state
3. Repository-local rules and documentation
4. Verified project record
5. Handoffs and memory
6. General model knowledge

Unverified information must be labeled as unverified.

## Autonomy Gates

- **Default**: read, analyze, plan, report.
- **Task Approval**: edit files, create files, run non-trivial commands.
- **High-Risk Approval**: commit, push, deploy, delete, publish, migrate, change infrastructure, or affect external systems.

When unsure, stop and ask for the smallest specific approval.

## Quickstart

1. Read `README.md`, `docs/architecture.md`, and `rules/autonomy-gates.md`.
2. Start with `prompts/audit-only-bootstrap.md`.
3. Produce a handoff using `templates/HANDOFF.md`.
4. Run the relevant review gate before any high-risk action.

## Example Use Cases

- Audit a `sample-api` repository before editing.
- Plan a `demo-product` feature with explicit approval gates.
- Review an `example-website` change before release.
- Organize `research-notes` into a verified handoff.

## Not Included

- Private projects
- Private memory
- Private handoffs
- Local machine paths
- Secrets or credentials
- Tool-specific private configuration
- Real customer, organization, or operational data
