# Demo Script

Target length: 35 minutes.

This script is designed for a public-safe walkthrough using mock data and sanitized screenshots. It does not require or expose the private Garage Admin control plane.

## 0:00 - 3:00 - Opening

Introduce Garage Admin:

- A guarded AI operator console for real infrastructure.
- Built around split Windows/Fedora responsibilities.
- Designed for diagnostics, evidence, Codex-assisted maintenance, and auditable action requests.

Clarify the public boundary:

- The walkthrough uses sanitized mock data.
- No live private endpoints, secrets, or production logs are exposed.
- The demo shows the reference pattern, not a public control surface.

## 3:00 - 7:00 - Startup-Visible Memory

Open the memory view using `mock-data/memory-entries.json`.

Show:

- Active context.
- Project state.
- Current task.
- Runtime summary.
- Known unknowns.

Narration points:

- The assistant starts with operational context instead of guessing.
- Memory is concise, current, and classified.
- Secrets and raw environment data are excluded.

## 7:00 - 11:00 - Service Discovery

Open `mock-data/service-inventory.json`.

Show:

- `demo-service-a` on `demo-windows-host`.
- `demo-service-b` on `demo-windows-host`.
- `demo-postgres` as infrastructure-owned storage.
- `demo-ingress` on `demo-fedora-control-plane`.
- Boundaries: runtime, control plane, memory, ingress.

Narration points:

- Service discovery is structured and allowlisted.
- The UI can show host ownership and allowed evidence types.
- Unknown or unsupported services do not become arbitrary shell targets.

## 11:00 - 15:00 - Health Check

Open `mock-data/health-results.json`.

Show:

- Current status.
- Latency.
- Freshness.
- Dependency status.
- Distinction between healthy, degraded, and unknown.

Narration points:

- A `401` or auth-blocked response can prove protection, but it does not prove full app health.
- Health checks are bounded and interpreted carefully.
- Evidence is timestamped and tied to a service target.

## 15:00 - 19:00 - Log Review

Open `mock-data/log-excerpts.json`.

Show:

- Capped log excerpts.
- Redacted request IDs.
- Sanitized paths.
- No request bodies, tokens, or private account details.

Narration points:

- Logs are useful but high risk.
- Garage Admin treats logs as bounded evidence, not bulk context dumps.
- Redaction happens before operator or assistant display.

## 19:00 - 25:00 - Guarded Restart Request

Walk through a mocked guarded restart flow.

Use the service inventory, health result, and logs to build a preflight summary:

- Target: `demo-service-a`.
- Host boundary: Windows runtime.
- Risk: state-changing action.
- Required evidence: current health, recent capped logs, known blast radius.
- Approval: required.
- Audit: required.

Show the expected decision point:

- The assistant may summarize risk and recommend next diagnostics.
- The assistant may not bypass approval.
- Unsupported targets fail closed.

Narration points:

- Restart discipline is part of the product.
- The important behavior is not "click restart"; it is the evidence and guardrail path around the action.

## 25:00 - 31:00 - Codex Patch / Verify Workflow

Open `mock-data/codex-task-result.json`.

Show:

- Inspect step.
- Minimal patch summary.
- Validation commands.
- Passing checks.
- Unknown live-runtime state.

Narration points:

- Codex is used for implementation and verification.
- Repo validation is separate from live runtime confirmation.
- The final answer includes evidence and remaining unknowns instead of implying more certainty than was checked.

## 31:00 - 35:00 - Final Audit Summary

Close with a synthesized audit summary:

- What was inspected.
- What was verified.
- What was mocked.
- What would require operator approval in a real environment.
- What remains unknown.

End with the safety thesis:

Garage Admin demonstrates AI-assisted infrastructure operations through narrow, auditable, allowlisted tools. The assistant improves operator speed and reasoning without receiving broad authority over production infrastructure.
