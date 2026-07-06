# Sample API Repository Onboarding

This is a synthetic example. It does not describe a real project, customer, person, domain, or local path.

## Target

`sample-api`

## Mode

audit-only

## Files Changed

none

## Verified Facts

- The repository appears to contain an API service.
- A README file documents a test command.
- A `src/` directory and a `tests/` directory are present.

## Assumptions

- The documented test command is intended to be the default verification path.
- The API service likely has one primary runtime entry point.

## Unknowns

- Deployment target is not documented.
- Required environment variables are not fully known.
- The authoritative lint command is not documented.

## Not-Run Checks

- Tests not run - audit-only mode did not include execution approval.
- Dependency installation not run - it would change local state.
- Deployment check not run - deployment is outside onboarding scope.

## Repository Map

- Purpose: example API service
- Main stack: unknown until package/config files are reviewed
- Entry points: `src/` and README command references
- Important directories:
  - `src/` -> application code
  - `tests/` -> test surface
  - `docs/` -> supporting documentation, if present
- Local rules read: none found in this synthetic example
- Commands found:
  - test command from README

## Architecture Notes

- Runtime: candidate, based on repository files
- Data/storage: unknown
- External integrations: unknown
- Test surface: candidate, based on `tests/`
- Deployment surface: unknown

## Risks

| Risk | Evidence | Impact | Mitigation | Approval Required |
|---|---|---|---|---|
| Test command may be stale | README only | medium | Ask for approval to run tests and record result | task |
| Environment requirements are unclear | no complete env documentation observed | medium | Inspect config and request missing context | none |
| Deployment assumptions could be wrong | no deployment docs observed | high | Do not deploy; ask for deployment-specific approval later | high-risk |

## Next Safe Actions

- Request task approval to run the documented test command.
- Request task approval before editing files.
- Keep deployment and publishing out of scope until explicitly approved.

## Stop Conditions

- No file changes allowed in audit-only mode.
- No commit, push, deploy, delete, publish, or visibility change allowed.

## Required Approval

Task approval to run verification commands or edit files in a later phase.
