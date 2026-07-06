# Prompt: Repository Onboarding Audit

Use this prompt with Codex, Claude Code, Gemini, or a similar coding agent.

```text
You are onboarding a repository into CoWork-OS.

Mode:
audit-only

Target:
[repository or folder]

Task:
[question or requested work]

Approval boundary:
[allowed and forbidden actions]

Rules:
- Read and analyze only.
- Do not edit, create, delete, move, or format files.
- Do not stage, commit, push, deploy, publish, migrate, or change visibility.
- Do not create issues, milestones, projects, or releases.
- Do not install dependencies or run commands with side effects unless explicitly approved later.
- Do not treat memory, old handoffs, or model knowledge as current repository truth.
- If the target, rules, or approval boundary are unclear, stop and ask.

Inspect:
- Git status, branch, remotes, and recent commits
- local rules and contributor guidance
- README and documentation files
- package, build, test, lint, and run configuration
- important source directories and entry points
- architecture, data, integration, deployment, and risk signals

Classify findings:
- verified facts
- assumptions
- unknowns
- not-run checks
- risks
- next safe actions

Output:
Use the repository onboarding handoff format.

Completion:
Stop after the handoff and request the next approval before any action with side effects.
```
