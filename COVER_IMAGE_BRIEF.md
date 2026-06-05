# Cover Image Brief

The cover image should communicate a guarded AI operator console without revealing private infrastructure. Use mock data only.

## Safe Cover Image Concepts

- Clean architecture diagram showing assistant, operator console, operational memory, guarded bridge contracts, Windows runtime boundary, and Fedora control-plane boundary.
- Sanitized UI screenshot using mock service inventory, mock health states, and redacted/capped log evidence.
- Abstract operator console visual with panels for memory, services, health, logs, and guarded actions, using placeholder names only.

## Screenshot Requirements

- Use only demo names such as `demo-service-a`, `demo-service-b`, `demo-windows-host`, `demo-fedora-control-plane`, `demo-postgres`, and `example.invalid`.
- Show host boundaries and evidence types clearly.
- Prefer mock JSON fixtures or a mock UI surface over live dashboards.
- Crop browser chrome unless it is intentionally neutral and contains no account information.
- Keep text readable at thumbnail size.

## Must Be Redacted

- API keys, tokens, passwords, cookies, auth headers, connection strings, private keys, certificates, and service account details.
- Real hostnames, domains, private IPs, live admin routes, route maps, tunnel IDs, ingress mappings, or account identifiers.
- Private filesystem paths, usernames, terminal prompts, local shell history, and editor tabs that reveal private paths.
- Raw logs, request bodies, stack traces with private paths, PM2 metadata, provider dashboards, billing pages, email, notifications, bookmarks, or extension menus.

## Recommended Image Dimensions

TODO screenshot/cover image URL after final asset is created. Recommended dimensions should be confirmed against the current OpenAI Showcase upload guidance before export.

## Candidate Concept A: Architecture Diagram

Create a polished diagram based on `diagram/architecture.mmd`.

Should show:

- Human operator.
- ChatGPT/Codex assistant layer.
- Garage Admin UI.
- File-backed operational memory.
- Guarded bridge contracts.
- Windows runtime boundary.
- Fedora control-plane boundary.
- Mock service evidence and audit trail.

Avoid:

- Live service names.
- Network route details.
- Provider logos unless they are necessary and allowed.
- Dense text that becomes unreadable at small sizes.

## Candidate Concept B: UI Screenshot With Mock Data

Capture a mock Garage Admin operator surface.

Should show:

- Startup memory.
- Service inventory.
- Health status with freshness.
- Redacted log excerpt.
- Guarded action preflight summary.
- Codex validation summary.

Use:

- `mock-data/memory-entries.json`.
- `mock-data/service-inventory.json`.
- `mock-data/health-results.json`.
- `mock-data/log-excerpts.json`.
- `mock-data/codex-task-result.json`.

Avoid:

- Any live browser tabs, terminals, paths, usernames, route names, account menus, or notifications.

## Candidate Concept C: Abstract Operator Console Visual

Create a non-literal but product-relevant visual of a guarded console.

Should show:

- Distinct panels for memory, services, health, logs, guarded action, and audit.
- Clear "read evidence first, approve actions explicitly" visual hierarchy.
- Placeholder labels only.

Avoid:

- Generic AI imagery that does not show the operator-console workflow.
- Decorative visuals that obscure the safety model.
- Any real infrastructure identifiers.
