# Security

## Redaction Policy

All public artifacts must be reviewed before publication. Remove or replace:

- Secrets, tokens, API keys, private keys, certificates, and passwords.
- Raw `.env` files and environment dumps.
- OAuth access tokens, refresh tokens, provider account IDs, and service account JSON.
- Cloud provider account identifiers and tunnel metadata.
- Live hostnames, private IPs, private admin URLs, and private routes.
- Logs containing private paths, credentials, user data, request bodies, or operational secrets.
- PM2 metadata that may include environment values.

Use placeholders such as:

- `example.invalid`
- `localhost`
- `127.0.0.1`
- `demo-windows-host`
- `demo-fedora-control-plane`
- `demo-postgres`
- `demo-service-a`
- `demo-service-b`

## Secret-Handling Rules

- Secrets stay backend-only.
- Secrets are never stored in operational memory.
- Secrets are never rendered in the frontend.
- Secrets are never copied into screenshots, videos, logs, or public JSON fixtures.
- Diagnostics must redact known sensitive fields before display.
- Public docs must describe contracts and patterns, not live credentials or routes.

## Allowed Public Content

Allowed:

- Sanitized architecture diagrams.
- Mock service inventory.
- Mock health results.
- Mock log excerpts.
- Mock operational memory entries.
- Mock Codex task results.
- Abstract bridge contract examples.
- Safety principles and validation flow.
- Placeholder hostnames and service names.

## Forbidden Public Content

Forbidden:

- Working live endpoint URLs for private infrastructure.
- Real tunnel routes or ingress mappings.
- Real PM2 process metadata or environment values.
- Raw production logs.
- Private file paths that reveal account or host details.
- Database connection strings.
- OAuth credentials or account identifiers.
- Any tool or script that can control the private system.

## Why This Demo Does Not Expose Live Infrastructure

This package is a reference architecture, not an operational control surface.

It uses mock JSON and static documentation because the value of the submission is the operating pattern: AI-assisted infrastructure work through narrow, auditable, allowlisted tools. Publishing a working control-plane endpoint would create unnecessary risk and would undermine the safety model the project is meant to demonstrate.

The public demo boundary keeps all examples inert. It can be shown in a repository, a slide deck, a video, or a local static preview without granting access to private infrastructure.

## Operator Safety Principles

- Start with read-only diagnostics.
- Keep host boundaries explicit.
- Prefer structured evidence over raw output.
- Cap and redact logs.
- Treat restarts, migrations, deletes, repairs, and daemon changes as state-changing actions.
- Require operator approval for state-changing actions.
- Validate after changes.
- Record what changed, what passed, and what remains unknown.
- Fail closed when an action is unsupported or evidence is stale.
