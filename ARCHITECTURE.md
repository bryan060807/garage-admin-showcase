# Architecture

## Split-Host Model

Garage Admin separates runtime operations from control-plane infrastructure.

The split is intentional: the operator console can reason across both sides, but host responsibilities remain explicit. A Windows-local check is never treated as a Fedora-local check, and a Fedora infrastructure action is not hidden behind a generic UI shortcut.

## Windows Responsibilities

In the private architecture, the Windows host is the runtime and operator workstation.

Public-safe responsibilities represented in this package:

- PM2-managed app runtimes.
- Garage Admin UI and backend surfaces.
- Local runtime dashboards.
- Backend-only bridge calls to Windows helper APIs.
- Read-only service inventory and health evidence.
- Guarded restart requests for known demo services.

The demo represents this host as `demo-windows-host` and local service URLs as `127.0.0.1` or `localhost`.

## Fedora Responsibilities

In the private architecture, Fedora is the infrastructure and control-plane host.

Public-safe responsibilities represented in this package:

- Ingress/front-door ownership.
- Infrastructure workers.
- Postgres/durable storage ownership.
- Service and host health evidence.
- Backup and rollback context as documented state.
- Infrastructure automation behind guarded workflows.

The demo represents this host as `demo-fedora-control-plane` and database service as `demo-postgres`.

## Memory System Responsibilities

The operational memory system gives the assistant startup-visible context without exposing secrets.

It stores:

- Active context.
- Project index.
- Task board.
- Runtime state summaries.
- Current project notes.
- Decision records.
- Audit-friendly session notes.

It does not store:

- Secrets.
- Tokens.
- Raw environment files.
- Database passwords.
- OAuth credentials.
- Raw PM2 environment metadata.
- Unredacted private logs.

The public mock memory entries are in `mock-data/memory-entries.json`.

## Bridge / Tool Contract Pattern

Garage Admin uses narrow bridge contracts instead of arbitrary command execution.

Typical contract shape:

```json
{
  "tool": "health_check",
  "target": "demo-service-a",
  "hostBoundary": "windows-runtime",
  "allowed": true,
  "outputPolicy": "redacted_capped_json",
  "requiresApproval": false
}
```

State-changing actions use stricter contracts:

```json
{
  "tool": "guarded_restart_request",
  "target": "demo-service-a",
  "hostBoundary": "windows-runtime",
  "allowed": true,
  "requiresApproval": true,
  "preflightRequired": ["fresh_health", "recent_logs", "blast_radius"],
  "auditRequired": true
}
```

Unsupported actions fail closed with structured errors.

## Codex Task Flow

Codex is used for code maintenance and validation, not as an unrestricted production operator.

Standard flow:

1. Inspect repository state and local instructions.
2. Identify the smallest viable change.
3. Patch only the relevant files.
4. Run focused checks.
5. Separate repo validation from live runtime confirmation.
6. Report changed files, validation evidence, assumptions, and unknowns.

For public demo purposes, `mock-data/codex-task-result.json` shows a representative task result without private files, routes, or secrets.

## Validation and Audit Flow

Garage Admin distinguishes evidence types:

- **Verified**: directly checked by a bounded diagnostic or validation command.
- **Inferred**: a reasonable conclusion based on available evidence.
- **Unknown**: not checked, stale, auth-blocked, or outside the current demo boundary.

For guarded actions, the expected flow is:

1. Gather service inventory.
2. Run current health check.
3. Review capped and redacted logs.
4. Explain risk and blast radius.
5. Request explicit operator approval.
6. Execute only the allowlisted action.
7. Verify post-action health.
8. Write an audit summary.

The public package includes only mock action records and no executable live action endpoint.
