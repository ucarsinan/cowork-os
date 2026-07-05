# GitHub Repository Setup

This checklist defines public repository metadata and release-readiness gates for CoWork-OS.

## Repository Metadata

- Repository name: `cowork-os`
- Description: A tool-agnostic Markdown control plane for agentic AI workflows.
- Default branch: `main`
- Suggested topics: `agentic-ai`, `ai-agents`, `ai-engineering`, `markdown`, `workflow-automation`, `developer-tools`, `software-architecture`

## Visibility Plan

1. Keep the hosted repository private until the final public-visibility review passes.
2. Run a final privacy, security, and quality review before switching visibility.
3. Switch public visibility only after explicit approval.

## Repository Features

- Issues: enabled
- Wiki: optional, disabled by default
- Discussions: optional
- Actions: not required for the initial public scaffold

## Release Gate

Before public visibility:

- Run a final privacy scan for names, private project references, local paths, domains, and personal data.
- Run a final security scan for secrets, tokens, credentials, and environment values.
- Confirm that examples remain synthetic and neutral.
- Confirm that no private handoffs, memory files, or operational records are included.
- Confirm that `LICENSE` uses the approved public owner line.

## License Owner

The MIT license uses `CoWork-OS Contributors` as the public owner line.
