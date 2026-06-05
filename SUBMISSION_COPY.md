# OpenAI Showcase Submission Copy

## Project Title

Garage Admin

## Tagline

A guarded AI operator console for real infrastructure.

## Short Description

Garage Admin is a reference architecture for AI-assisted infrastructure operations. It combines startup-visible operational memory, split-host service evidence, narrow bridge APIs, guarded action requests, and Codex-assisted maintenance workflows so operators can use AI without exposing secrets or granting arbitrary shell access.

## Long Description

Garage Admin explores a practical pattern for using AI in real infrastructure operations: give the assistant high-quality context and bounded tools, not broad authority.

The private architecture coordinates a Windows runtime/operator host and a Fedora control-plane host. Windows owns PM2-managed app runtimes, local dashboards, and operator workflows. Fedora owns ingress, infrastructure services, Postgres, durable storage patterns, and worker services. A file-backed memory system keeps active context, project state, task tracking, decisions, and runtime notes visible at startup.

The assistant layer helps the operator interpret service inventory, health checks, capped logs, and validation results. Codex helps inspect code, make targeted patches, and run focused verification. State-changing actions, such as restarts, are modeled as guarded requests with preflight evidence, approval, and audit records.

This public package is sanitized. It uses mock services and placeholders instead of live hostnames, secrets, logs, PM2 metadata, or production endpoints. The goal is to demonstrate the architecture and safety model in a reproducible way.

## Technologies Used

- OpenAI ChatGPT-style assistant workflows.
- Codex for code inspection, patching, and validation.
- Node.js / JavaScript service patterns.
- PM2-style runtime supervision pattern.
- Fedora/Linux control-plane pattern.
- Postgres-style durable storage pattern.
- File-backed operational memory.
- Mermaid architecture diagram.
- JSON mock evidence fixtures.

## How OpenAI / Codex Was Used

- To reason over operational context and turn it into concrete plans.
- To inspect code and existing patterns before making changes.
- To generate targeted patches.
- To run or specify focused validation checks.
- To produce concise audit summaries that separate verified facts, assumptions, and unknowns.
- To help build this sanitized public Showcase package without exposing private infrastructure details.

## What Makes It Novel

Garage Admin focuses on a safety-first operating pattern rather than a generic "AI can run commands" demo.

Key distinctions:

- Explicit split between runtime host and control-plane host.
- Startup-visible operational memory with secret exclusion.
- Narrow allowlisted bridges instead of arbitrary shell.
- Read-only diagnostics before state changes.
- Guarded action requests with approval and audit.
- Codex-mediated maintenance with validation evidence.
- Public demo boundary that proves the pattern without exposing live infrastructure.

## Safety Model

The safety model is built around practical constraints:

- No secrets in memory, frontend state, logs, screenshots, or public fixtures.
- No raw `.env` files or PM2 environment dumps.
- No live private hostnames, tunnels, or admin routes in public artifacts.
- No working endpoint that can operate the private system.
- Capped and redacted evidence.
- Explicit host ownership for every service.
- Operator approval required for state-changing actions.
- Unsupported actions fail closed.
- Validation results are reported separately from live-runtime confirmation.

## Setup / Demo Instructions

This public package is docs and mock data only.

Suggested walkthrough:

1. Read `README.md`.
2. Open `diagram/architecture.mmd` in any Mermaid renderer.
3. Walk through `DEMO_SCRIPT.md`.
4. Use `mock-data/service-inventory.json`, `mock-data/health-results.json`, `mock-data/log-excerpts.json`, `mock-data/memory-entries.json`, and `mock-data/codex-task-result.json` as the demo evidence.
5. Review `SECURITY.md` and `REDACTION_CHECKLIST.md` before publishing screenshots or video.

Public repo URL: https://github.com/bryan060807/garage-admin-showcase.git

TODO: hosted/demo URL or N/A.

TODO: video URL if recorded.

TODO: screenshot/cover image URL after redaction review.

TODO: submitter identity.

TODO: public contact.

TODO: website/social link.

## Suggested Screenshots / Video Shots

- Architecture diagram showing ChatGPT/Codex, Garage Admin UI, memory, bridge APIs, Windows runtime, Fedora control plane, PM2 apps, Postgres, and ingress.
- Startup memory view with sanitized active context.
- Service inventory view with host boundaries.
- Health result view with freshness and dependency status.
- Redacted log review view.
- Guarded restart request preflight view.
- Codex task result showing patch, validation, and remaining unknowns.
- Final audit summary.
