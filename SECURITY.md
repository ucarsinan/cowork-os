# Security Policy

## Reporting

If you find a security issue, report it privately through the repository maintainer's preferred security channel.

Do not open public issues containing secrets, credentials, exploit details, private data, or operational identifiers.

## Security Model

CoWork-OS is a Markdown workflow framework. It does not execute code by itself.

Risk comes from how an assistant or user applies the workflows. For that reason, all high-risk actions require explicit approval.

## High-Risk Actions

High-risk actions include:

- commit
- push
- deploy
- delete
- publish
- migrate
- change infrastructure
- access production data
- affect external systems

## Secret Handling

Never place secrets in this repository.

Examples:

- API keys
- tokens
- passwords
- private keys
- database URLs
- `.env` values

Run a secret scan before any public release.
