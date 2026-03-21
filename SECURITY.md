# Security Policy

## Scope

This repository is a prompt-and-reference bundle. It does not run a production service, but it still accepts pull requests, issues, and fixture files. Treat unsafe automation, malicious fixture content, and secret leakage as security-relevant.

## Report Here

Use GitHub private reporting if available, or contact the maintainer privately for:

- malicious code or workflow changes
- secrets accidentally committed to the repo
- fixture files that contain sensitive or non-public data
- contribution paths that could cause unsafe automation or prompt injection

## Do Not Put In Public Issues

- API keys
- tokens
- credentials
- private corporate documents
- non-public terminal exports
- material non-public information

## Repository-Specific Safety Rules

- Keep fixtures sanitized and minimal.
- Do not commit proprietary terminal exports unless the maintainer explicitly wants them in public.
- Do not commit regulator or issuer excerpts that violate copyright or access restrictions.
- Keep eval fixtures focused on structure and gating behavior, not on large source dumps.
