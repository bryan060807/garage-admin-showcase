# Screenshot Shot List

Use mock data unless a specific shot can be created from sanitized static docs. Do not capture the private live control plane.

## Shot 1: README Package Boundary

- Demonstrates: the package is a sanitized reference architecture and mock-data demo.
- Source: `README.md`.
- Must hide/redact: browser chrome, local paths, account menus, terminal prompts, editor tabs with private paths.
- Mock data allowed: yes.

## Shot 2: Architecture Diagram

- Demonstrates: assistant layer, Garage Admin UI, memory, guarded bridge contracts, Windows runtime boundary, Fedora control-plane boundary, service evidence, and audit.
- Source: `diagram/architecture.mmd` rendered in a Mermaid viewer.
- Must hide/redact: renderer URLs if private, local paths, browser profile details, account controls.
- Mock data allowed: yes.

## Shot 3: Startup-Visible Memory

- Demonstrates: active context, project update, decision entry, verified facts, unknowns, and concise operational memory.
- Source: `mock-data/memory-entries.json` or a mock UI built from it.
- Must hide/redact: real memory files, private task names, usernames, private paths, raw logs, account identifiers.
- Mock data allowed: yes.

## Shot 4: Service Inventory

- Demonstrates: split host ownership, service targets, allowed evidence types, and allowed action boundaries.
- Source: `mock-data/service-inventory.json` or a mock UI built from it.
- Must hide/redact: real service names, live ports, private hostnames, private IPs, route maps, PM2 metadata.
- Mock data allowed: yes.

## Shot 5: Health Evidence

- Demonstrates: healthy, degraded, and protected states; freshness; latency; dependency status; careful interpretation of auth-protected checks.
- Source: `mock-data/health-results.json` or a mock UI built from it.
- Must hide/redact: live health endpoints, request headers, cookies, account IDs, private dependency names.
- Mock data allowed: yes.

## Shot 6: Capped Log Review

- Demonstrates: bounded log evidence, capped excerpts, redaction policy, request IDs, and no raw sensitive data.
- Source: `mock-data/log-excerpts.json` or a mock UI built from it.
- Must hide/redact: raw operational logs, request bodies, stack traces with paths, auth headers, cookies, usernames, private account details.
- Mock data allowed: yes.

## Shot 7: Guarded Action Preflight

- Demonstrates: state-changing action discipline, preflight evidence, blast radius, approval requirement, and audit requirement.
- Source: `DEMO_SCRIPT.md` section "Guarded Restart Request" or a mock UI based on it.
- Must hide/redact: live action buttons connected to private services, real service names, real restart history, PM2 process IDs, operator account details.
- Mock data allowed: yes.

## Shot 8: Codex Patch / Verify Workflow

- Demonstrates: inspect, patch, validate, report; repo validation separated from live runtime confirmation.
- Source: `mock-data/codex-task-result.json` or a sanitized Codex transcript screenshot.
- Must hide/redact: private repo paths, branch names if sensitive, terminal prompts, real diffs, logs, tokens, account identifiers.
- Mock data allowed: yes.

## Shot 9: Final Audit Summary

- Demonstrates: what was inspected, what was verified, what was mocked, what requires approval, and what remains unknown.
- Source: `DEMO_SCRIPT.md` final section or a mock UI summary.
- Must hide/redact: real operational outcomes, live service statuses, private incident details, private personnel or account information.
- Mock data allowed: yes.

## Final Review Checklist Before Upload

- [ ] Every visible host, route, service, path, and account label is a placeholder or public-safe value.
- [ ] No private IPs, real hostnames, live admin route names, tunnel references, provider account pages, or route maps are visible.
- [ ] No API keys, tokens, passwords, cookies, auth headers, connection strings, private keys, certificates, or service account details are visible.
- [ ] No raw logs, PM2 metadata, environment values, database dumps, backup paths, or production terminal output are visible.
- [ ] Browser tabs, bookmarks, account menus, notifications, extension menus, and OS-level personal details are hidden or cropped.
- [ ] The screenshot caption or surrounding copy states that mock data is being used.
- [ ] The final asset matches the OpenAI Showcase upload size and format requirements.
