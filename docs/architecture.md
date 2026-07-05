# Architecture

CoWork-OS is organized as a Markdown control plane.

## Layers

1. Core documentation explains purpose and operating model.
2. Agents define reusable responsibilities.
3. Rules define non-negotiable boundaries.
4. Workflows define repeatable action sequences.
5. Prompts define task starters.
6. Reviews define quality gates.
7. Templates define reusable project records and handoffs.
8. Adapters describe tool capabilities and limits.
9. Examples show synthetic usage.

## Design Principle

The core must remain tool-agnostic. A tool can implement a workflow, but a tool must not become the workflow.
