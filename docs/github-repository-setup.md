# GitHub Repository Setup

This checklist defines public repository metadata and release-readiness gates for CoWork-OS.

## Repository Metadata

- Repository name candidate: `cowork-os`
- Description: A tool-agnostic Markdown control plane for agentic AI workflows.
- Default branch: `main`
- Suggested topics: `agentic-ai`, `ai-agents`, `ai-engineering`, `markdown`, `workflow-automation`, `developer-tools`, `software-architecture`

## Visibility Plan

1. Create the hosted repository as private first.
2. Run a final privacy, security, and quality review before connecting any remote.
3. Add a remote only after explicit approval.
4. Push only after explicit approval.
5. Switch public visibility only after the final release gate passes.

## Repository Features

- Issues: enabled
- Wiki: optional, disabled by default
- Discussions: optional
- Actions: not required for the initial public scaffold

## Release Gate

Before any remote, push, or public visibility:

- Run a final privacy scan for names, private project references, local paths, domains, and personal data.
- Run a final security scan for secrets, tokens, credentials, and environment values.
- Confirm that examples remain synthetic and neutral.
- Confirm that no private handoffs, memory files, or operational records are included.
- Confirm that `LICENSE` owner placeholder replacement has an explicit owner decision.

## License Owner Note

The MIT license currently uses the owner placeholder `[Your Name]`. Replace it only after an explicit owner decision.
