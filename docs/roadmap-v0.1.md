# CoWork-OS v0.1 Roadmap

This roadmap defines the first public release target for CoWork-OS.

v0.1 should turn the current clean-room scaffold into a usable starter framework for agentic AI work. The release is documentation-first: it should help a new user audit a repository, define agent roles, apply safety gates, capture handoffs, and adapt the system to their own tools without depending on a specific AI vendor.

## Target Outcome

v0.1 should make CoWork-OS useful as a practical Markdown control plane for small agentic AI workflows.

A new user should be able to:

1. Understand the operating model in under 15 minutes.
2. Run an audit-only onboarding workflow on a synthetic or public-safe repository.
3. Choose an agent team structure from a simple routing matrix.
4. Apply review gates before file edits, commits, pushes, releases, or publication.
5. Capture state in handoffs and memory notes without storing private data.
6. Compare tool adapters without treating any tool as the core system.
7. Follow a demo session from intake to handoff.

## Non-Goals

v0.1 will not include:

- A web app, CLI, SaaS service, or hosted product.
- Tool-specific automation that makes one AI assistant the default core.
- Real customer stories, private project examples, or local machine paths.
- Complex package installation, plugin distribution, or marketplace mechanics.
- Enterprise governance, compliance certification, or production policy enforcement.
- GitHub Issues or Milestones generated from this roadmap before explicit approval.

## Core Features

### 1. Audit-Only Onboarding Workflow

Improve the first-run workflow so a user can inspect a repository without editing it.

Expected output:

- A clearer audit-only prompt.
- A step-by-step workflow that separates reading, findings, risks, and next approvals.
- A short checklist for when to stop and ask before editing.

### 2. Complete Repo Onboarding Example

Add a full public-safe example that shows how to onboard a synthetic repository.

Expected output:

- A complete example using `sample-api` or another neutral demo target.
- Example project record, status file, risk list, verification notes, and handoff.
- Clear labels that all example data is synthetic.

### 3. Agent Team Routing Matrix

Define when to use each agent role and how responsibility moves between them.

Expected output:

- A routing matrix across orchestrator, architect, implementer, reviewer, QA, security/privacy, documentation, researcher, and memory curator.
- Trigger examples for common tasks.
- Clear boundaries for when one agent should hand off to another.

### 4. Review Gate Checklist

Turn review gates into concise, repeatable checklists.

Expected output:

- Pre-edit, pre-commit, pre-push, pre-release, and pre-publication checks.
- Pass/fail output format.
- Explicit escalation points for high-risk actions.

### 5. Public-Safe Memory Model

Document how to capture durable project context without storing sensitive data.

Expected output:

- Memory categories and allowed content.
- Redaction rules for names, paths, credentials, customer data, and private operations.
- Examples of safe and unsafe memory notes.

### 6. Tool Adapter Comparison

Explain how adapters differ while keeping the core tool-agnostic.

Expected output:

- A comparison table for capabilities, limits, and best-fit workflows.
- Guidance for adding a new adapter.
- A rule that adapter capability must not redefine core behavior.

### 7. Demo Session Walkthrough

Create one end-to-end walkthrough from intake to final handoff.

Expected output:

- A synthetic task scenario.
- Step-by-step agent actions.
- Review gate decision points.
- Final handoff with verified facts, risks, and next approvals.

### 8. Starter Kit Path

Create the shortest path for a new user to adopt CoWork-OS.

Expected output:

- A recommended reading order.
- Minimal files to copy into a new project.
- First-session checklist.
- Guidance for staying public-safe while adapting the framework.

## Priorities

### Now

1. Audit-only onboarding workflow.
2. Complete repo onboarding example.
3. Review gate checklist.
4. Starter kit path.

These define the minimum useful loop: inspect, decide, review, and hand off.

### Next

1. Agent team routing matrix.
2. Public-safe memory model.
3. Demo session walkthrough.

These make the framework easier to repeat across different projects and assistants.

### Later

1. Tool adapter comparison.
2. Adapter contribution guidance.
3. Additional synthetic examples.

These improve breadth after the first user journey works end to end.

## Quality Criteria

Every v0.1 item should meet these criteria:

- Public-safe: no private names, paths, domains, customers, secrets, or operational records.
- Tool-agnostic: no assistant, model, or vendor becomes the core workflow.
- Actionable: a user can follow the document without additional hidden context.
- Reviewable: each workflow has a clear gate, expected output, and stop condition.
- Lightweight: Markdown-first, no required runtime, no required external service.
- Consistent: terminology matches README, architecture, rules, workflows, prompts, reviews, and templates.

## Planned Issue Candidates

These are issue candidates only. They should not be created on GitHub until explicitly approved.

- [ ] Improve audit-only onboarding workflow.
- [ ] Add a complete repo onboarding example using synthetic data.
- [ ] Create an agent team routing matrix.
- [ ] Turn review gates into reusable checklists.
- [ ] Document the public-safe memory model.
- [ ] Expand the tool adapter comparison.
- [ ] Add an end-to-end demo session walkthrough.
- [ ] Add a first starter kit path for new users.
- [ ] Review terminology across agents, rules, workflows, prompts, reviews, templates, adapters, and examples.
- [ ] Run a v0.1 release-readiness review before tagging.

## Portfolio Narrative

CoWork-OS should demonstrate practical AI engineering judgment, not just prompt collection.

The repository should show:

- How to design tool-agnostic agent workflows.
- How to separate autonomy from approval-gated risk.
- How to make AI work auditable with Markdown records.
- How to preserve project reality through truth-state priority, reviews, and handoffs.
- How to publish an AI workflow framework without leaking private operational context.

## v0.1 Release Criteria

v0.1 is ready when:

- The audit-only onboarding path is complete and tested against synthetic examples.
- A new user can follow the starter kit path without private context.
- Review gates cover edits, commits, pushes, releases, deletion, deployment, and publication.
- The memory model explains safe retention and unsafe retention clearly.
- At least one complete demo session walkthrough exists.
- README links to the roadmap and first-use path.
- CHANGELOG has a v0.1 entry.
- A final privacy and security scan passes.
- A release-readiness review marks the repository ready for v0.1.
