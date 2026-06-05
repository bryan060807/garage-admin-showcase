# Garage Admin

**A guarded AI operator console for real infrastructure**

> Public-safe package note: this `showcase/` directory is a sanitized reference architecture and demo package. It is not the live private Garage Admin control plane and contains no working endpoint capable of operating private infrastructure.

## Problem Statement

Infrastructure operators increasingly use AI assistants for diagnosis, code maintenance, and operational planning. The risky version of that pattern gives an assistant broad shell access, unbounded logs, secrets in context, or unclear authority over production systems.

Garage Admin addresses a narrower problem: how can an AI assistant help operate real split-host infrastructure while staying inside explicit, auditable, low-risk boundaries?

The private architecture coordinates Windows app runtimes, Fedora control-plane infrastructure, operational memory, and Codex-assisted maintenance tasks. This public package presents the reference pattern without exposing live hosts, private routes, credentials, logs, or working control endpoints.

## Solution Overview

Garage Admin is a guarded operator console. It gives a human operator and AI assistant shared visibility into services, memory, health checks, capped logs, and maintenance tasks. The assistant can help interpret evidence, draft plans, and produce patches, but operational actions remain narrow, allowlisted, validated, and auditable.

The core idea is not "AI with shell access." The core idea is AI-assisted operations through small contracts:

- Read current operational memory.
- Discover known services.
- Run bounded health checks.
- Review redacted and capped log excerpts.
- Request a guarded action through an allowlisted bridge.
- Use Codex for patch and verification workflows.
- Record what was checked, what changed, and what remains unknown.

## Package Contents

- `ARCHITECTURE.md`: reference architecture and contract pattern.
- `SECURITY.md`: public-release safety model and forbidden content.
- `DEMO_SCRIPT.md`: 35 minute walkthrough using mock evidence.
- `SUBMISSION_COPY.md`: Showcase-ready fields and manual TODOs.
- `FORM_READY_ANSWERS.md`: copy/paste-ready Showcase draft answers.
- `FINAL_SUBMISSION_CHECKLIST.md`: final form, repo, media, and security checks.
- `REPO_RELEASE_PLAN.md`: local-only public repository packaging plan.
- `PUBLICATION_COMMANDS.md`: exact manual publication commands with a pre-push safety gate.
- `LICENSE_TODO.md`: placeholder until Bryan selects a public license.
- `diagram/architecture.mmd`: Mermaid architecture diagram.
- `mock-data/`: public-safe sample service, health, log, memory, and Codex task fixtures.
- `REDACTION_CHECKLIST.md`: screenshot, video, and public repository review checklist.

## Architecture Summary

Garage Admin uses a split-host model:

- **Windows runtime host**: PM2-managed application runtimes, operator UI, local dashboards, and runtime helper bridges.
- **Fedora control plane**: ingress, infrastructure services, Postgres, durable storage patterns, worker services, and infrastructure automation.
- **File-backed operational memory**: startup-visible active context, task board, project state, decision notes, and audit-oriented session notes.
- **Bridge APIs**: narrow, token-gated, backend-only interfaces for service inventory, health checks, log review, and guarded actions.
- **Codex task flow**: inspect, patch, validate, and summarize with evidence before any live rollout claim.

The public demo boundary replaces real hosts and services with placeholders such as `demo-windows-host`, `demo-fedora-control-plane`, `demo-postgres`, `demo-service-a`, and `demo-service-b`.

## Safety Model

Garage Admin is designed around constraints:

- No arbitrary shell executor in the operator UI.
- No secrets in memory, logs, frontend state, screenshots, or public docs.
- Diagnostics before changes.
- Explicit Windows vs. Fedora host responsibility boundaries.
- Allowlisted bridge contracts instead of broad host access.
- Capped and redacted outputs.
- Guarded restart requests with risk classification, freshness checks, and audit records.
- Validation evidence separated from assumptions and unknown runtime state.

## OpenAI / Codex Usage

OpenAI and Codex are used as assistant layers over the guarded system:

- ChatGPT-style interaction helps the operator ask operational questions, compare evidence, and plan next steps.
- Codex inspects code, makes targeted patches, runs focused validation, and reports what was or was not verified.
- The assistant consumes curated operational memory and bounded tool outputs rather than raw secrets or unrestricted host access.
- The operator remains responsible for approving state-changing actions and for final production rollout decisions.

This package does not claim OpenAI endorsement or Showcase acceptance.

## Demo Flow

The companion `DEMO_SCRIPT.md` describes a 35 minute walkthrough:

1. Open startup-visible memory.
2. Review service inventory.
3. Run a bounded health check.
4. Inspect redacted log excerpts.
5. Walk through a guarded restart request.
6. Show a Codex patch and verification workflow.
7. Close with an audit summary.

The mock data in `mock-data/` supports the walkthrough without touching live infrastructure.

## What Is Mocked vs. Real

**Real architecture pattern**

- Split Windows/Fedora responsibilities.
- Operational memory concept.
- Narrow bridge/tool contract model.
- Diagnostics-first operating style.
- Codex-mediated maintenance workflow.
- Audit and redaction requirements.

**Mocked in this package**

- Service names and inventory.
- Health results.
- Log excerpts.
- Memory entries.
- Codex task result.
- Hostnames, routes, and infrastructure identifiers.

**Not included**

- Private source code.
- Raw `.env` files.
- PM2 metadata.
- Real logs.
- Live hostnames or tunnel routes.
- Working endpoint that can control the private system.

## Submission Notes

This package is intended to support an OpenAI Showcase submission as a reference architecture and demo. Before submission, Bryan should add only the manual public fields that cannot be generated safely here:

- Public repo URL: `https://github.com/bryan060807/garage-admin-showcase.git`.
- TODO: hosted/demo URL or N/A.
- TODO: video URL, if recorded.
- TODO: screenshot/cover image URL, after redaction review.
- TODO: submitter identity.
- TODO: public contact.
- TODO: website/social link, if desired.
- TODO: license choice, if a public repository is published.

## How To Submit Or Publish

Use these files for final local preparation:

- `FINAL_SUBMISSION_CHECKLIST.md`: final form, repo, media, and security checks.
- `FORM_READY_ANSWERS.md`: copy/paste-ready Showcase draft answers with manual TODO fields.
- `REPO_RELEASE_PLAN.md`: optional public repository packaging plan.
- `COVER_IMAGE_BRIEF.md`: safe cover image concepts and redaction requirements.
- `SCREENSHOT_SHOT_LIST.md`: exact screenshot plan and upload review checks.
- `PUBLICATION_COMMANDS.md`: local commands for Bryan to initialize, check, commit, and push only after final review.

Do not publish until the final security review passes and Bryan has filled only the allowed public TODO fields.
