# Tool Adapters

Tool adapters explain how different AI tools can participate in a CoWork-OS workflow.

They do not define the core rules. The core remains tool-agnostic and is governed by the shared rules, workflows, reviews, templates, and approval gates.

## Adapter Boundary

Capability is not approval.

An adapter may describe that a tool can inspect files, edit files, run commands, create commits, push code, deploy, delete content, publish, or change visibility. Those capabilities still require explicit approval when they are high-risk actions.

## What Adapter Docs Should Include

Each adapter should document:

- execution model
- file access
- approval model
- memory and context handling
- review handoff behavior
- strengths
- risks
- when to use it
- what must be verified against current tool documentation

## Tool-Agnostic Defaults

- Do not treat any tool as the default authority.
- Do not rank tools as universally better or worse.
- Do not assume current feature availability without verification.
- Do not turn private usage history into public guidance.
- Do not weaken privacy, security, memory, review, or release gates.

## Existing Adapter Notes

This directory may include short notes for tools such as Codex, Claude Code, Gemini, Antigravity, or similar coding agents.

Treat those notes as adapter context, not as permission to act.
