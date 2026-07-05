# Review Gate Checklist

Use this checklist before an AI coding agent moves from analysis to action, or before a change is committed, pushed, released, published, or extracted into public documentation.

The checklist is a consolidated gate. It sits above the specific review files in this repository, such as software change, architecture, security/privacy, release readiness, and public release reviews. It does not replace those reviews; it helps decide which ones are required and whether the current work can proceed.

This process is tool-agnostic. It works with Codex, Claude Code, Gemini, or similar coding agents as long as the agent can report evidence, respect approval boundaries, and stop when a gate fails.

## Output Format

Use this structure for each gate:

```text
Gate:
Status: pass / fail / blocked / not applicable
Evidence:
Findings:
Missing checks:
Required approval:
Next action:
```

Prefer `blocked` when evidence is missing and the next action would be risky.

## Privacy Gate

Purpose:

- prevent private, personal, customer, operational, or local-machine information from entering public or shared artifacts

Pass criteria:

- no personal names unless explicitly intended for public use
- no private project names, customer names, or organization details
- no local machine paths
- no private memory, private handoffs, or internal operating notes
- examples are synthetic or clearly public-safe
- data is minimized to what the task actually needs

Fail conditions:

- public-facing content includes private paths, names, domains, handoffs, customer details, or internal records
- private project context is used as a public example
- sensitive information is reproduced when a summary would be enough

Required evidence:

- files or artifacts reviewed
- privacy scan terms used, when applicable
- statement of whether examples are synthetic, public, or private
- unresolved privacy questions

## Security Gate

Purpose:

- prevent secrets, unsafe permissions, external side effects, or unapproved security-sensitive actions

Pass criteria:

- no secrets, tokens, credentials, private keys, or `.env` values are present
- logs and examples do not expose sensitive data
- external systems are not changed without explicit approval
- security-sensitive claims are backed by evidence
- rollback or stop conditions are identified when risk is meaningful

Fail conditions:

- secret-like values appear in code, docs, logs, or examples
- the agent triggers an external system without approval
- a security claim is made without evidence
- access, permissions, or infrastructure are changed without a clear gate

Required evidence:

- secret scan result
- files, logs, or configuration reviewed
- external systems touched, or confirmation that none were touched
- remaining security risks

## Scope Gate

Purpose:

- keep the work inside the approved task, file list, repository, and risk boundary

Pass criteria:

- target repository or folder is confirmed
- changed files match the approved scope
- unrelated roadmap items are not edited
- existing work is not reverted or overwritten
- public issues, milestones, projects, or releases are not created unless explicitly approved

Fail conditions:

- files outside the approved scope are changed
- unrelated refactoring or roadmap work is included
- an existing dirty worktree is ignored
- public planning surfaces are changed without approval

Required evidence:

- `git status`
- changed file list
- scope statement
- unexpected files or untracked files, if any

## Architecture Gate

Purpose:

- confirm that a change fits the system model instead of weakening boundaries, portability, or maintainability

Pass criteria:

- goal and non-goals are clear
- source of truth is identified
- tool-agnostic behavior is preserved
- new structure fits existing rules, workflows, adapters, and reviews
- trade-offs and coupling are named when relevant

Fail conditions:

- one AI tool becomes the hidden core of the system
- public documentation starts driving private governance
- new terminology conflicts with existing concepts
- ownership or responsibility boundaries become unclear

Required evidence:

- documents or files reviewed
- affected concepts, workflows, rules, or adapters
- known trade-offs
- unresolved architecture questions

## Implementation Gate

Purpose:

- verify that any concrete change is controlled, reviewable, and not overstated

Pass criteria:

- task approval exists for file changes
- changed files are in the approved target
- checks are appropriate for the change size
- skipped checks are listed with reasons
- no unreviewed generated files, binary artifacts, or temporary files are included

Fail conditions:

- edits happen before approval
- changed files do not match the intended scope
- tests or checks are reported as passed when they were not run
- unrelated files are staged or committed

Required evidence:

- changed file list
- commands or checks run
- checks not run and why
- current repository status

## Documentation Gate

Purpose:

- make sure written artifacts are useful, public-safe when public, and clear about evidence

Pass criteria:

- documentation is direct, practical, and understandable without hidden context
- verified facts, assumptions, unknowns, and recommendations are separated when relevant
- links and referenced files are valid when changed
- terminology matches the rest of the repository
- public documentation contains no private assumptions

Fail conditions:

- stale next-step language remains
- placeholders are left without purpose
- public text includes private context or internal process history
- claims are made without sources or current repository evidence

Required evidence:

- files reviewed
- links or references checked
- remaining placeholders, if any
- known documentation gaps

## Public Extraction Gate

Purpose:

- ensure public content is generalized from an approved source pattern and not copied from private context

Pass criteria:

- the candidate has been approved for public extraction
- target public files are explicitly scoped
- public text is clean-room, generic, and written for public use
- private names, paths, handoffs, memory, domains, and operational records are absent
- public release or publication review is planned before high-risk actions

Fail conditions:

- public work starts without an approved extraction candidate
- private source text is copied mechanically
- a public roadmap item is treated as an implementation command without review
- public issues, milestones, projects, releases, or visibility changes are created without explicit approval

Required evidence:

- approved candidate or extraction decision
- target public files
- sanitization result
- secret scan result
- confirmation that public planning surfaces were not changed unless approved

## Commit / Push / Release Gate

Purpose:

- separate local edits from high-risk Git, deployment, publication, and release actions

Pass criteria:

- `git status` is understood
- staged files exactly match the approved scope
- commit message is approved or clearly provided
- push, deploy, delete, publish, release, and visibility changes have separate explicit approval
- force push is not used unless explicitly approved

Fail conditions:

- unexpected files are staged
- commit is created without approval
- push is performed without approval
- deploy, delete, publish, release, migration, remote change, or visibility change happens without explicit approval
- release readiness is claimed without current evidence

Required evidence:

- `git status`
- staged file list
- commit hash, if created
- remote and branch, if pushing
- release or deployment target, if applicable
- confirmation of no force push, when relevant

## Decision

Use one of these outcomes:

- `pass`: the gate is satisfied and the next approved step may proceed
- `pass after small patch`: a small correction is required before proceeding
- `blocked`: evidence, approval, or scope is missing
- `reject`: the proposed change should not proceed in its current form

When uncertain, choose `blocked` and name the smallest safe next action.
