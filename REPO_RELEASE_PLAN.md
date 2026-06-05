# Repo Release Plan

This plan is for a local, optional public repository release. It does not publish, push, create a repository, contact GitHub, or make network calls.

## Recommended Public Repo Name

`garage-admin-showcase`

Known URL:

```txt
https://github.com/bryan060807/garage-admin-showcase.git
```

## Recommended Repo Description

Sanitized reference architecture and mock-data demo for a guarded AI operator console for split-host infrastructure.

## Suggested Topics / Tags

- `openai`
- `codex`
- `ai-ops`
- `operator-console`
- `infrastructure`
- `observability`
- `runbooks`
- `security`
- `mock-data`
- `reference-architecture`

## Suggested Root Layout If Publishing Only `showcase/`

```txt
README.md
ARCHITECTURE.md
SECURITY.md
DEMO_SCRIPT.md
SUBMISSION_COPY.md
FORM_READY_ANSWERS.md
FINAL_SUBMISSION_CHECKLIST.md
REPO_RELEASE_PLAN.md
COVER_IMAGE_BRIEF.md
SCREENSHOT_SHOT_LIST.md
REDACTION_CHECKLIST.md
PUBLICATION_COMMANDS.md
LICENSE.md
.gitignore
diagram/
mock-data/
```

In this option, the current `showcase/README.md` becomes the public repository root `README.md`.

This is the recommended option for the current package.

## Suggested Root Layout If Extracting To A Standalone Repo

```txt
README.md
docs/
  ARCHITECTURE.md
  SECURITY.md
  DEMO_SCRIPT.md
  SUBMISSION_COPY.md
  FORM_READY_ANSWERS.md
  FINAL_SUBMISSION_CHECKLIST.md
  REPO_RELEASE_PLAN.md
  COVER_IMAGE_BRIEF.md
  SCREENSHOT_SHOT_LIST.md
  REDACTION_CHECKLIST.md
diagram/
  architecture.mmd
mock-data/
  codex-task-result.json
  health-results.json
  log-excerpts.json
  memory-entries.json
  service-inventory.json
LICENSE
```

In this option, update README links after moving docs into `docs/`.

## Recommended License

TODO license choice

## Recommended README Landing Path

Use `README.md` at the repository root. It should open with the existing public-safe package note and clearly state that the artifact is a sanitized reference architecture and mock-data demo, not the private live control plane.

## What Not To Include

- Private source code outside this package.
- Environment files or environment dumps.
- API keys, tokens, passwords, cookies, auth headers, connection strings, private keys, certificates, or service account files.
- Raw operational memory from the private environment.
- Raw logs, PM2 metadata, process dumps, terminal history, or browser profiles.
- Private hostnames, private IPs, live admin routes, tunnel IDs, ingress mappings, account identifiers, or provider console screenshots.
- Backup archives, database dumps, uploaded files, audio, storage artifacts, or rollback bundles.
- Scripts that can contact or control private infrastructure.
- Screenshots or videos that reveal private browser chrome, account menus, usernames, paths, notifications, terminals, logs, or identifiers.

## Pre-Push Safety Checklist

- [ ] Confirm the repository contains only the sanitized package.
- [ ] Confirm all JSON fixtures parse.
- [ ] Search for private IP patterns.
- [ ] Search for real hostnames or domains.
- [ ] Search for private filesystem paths.
- [ ] Search for live admin route names.
- [ ] Search for Cloudflare/tunnel references and confirm they appear only in redaction or forbidden-content contexts.
- [ ] Search for secret-like values and credential keywords.
- [ ] Run a dedicated secret scanner if one is available locally.
- [ ] Confirm every TODO is one of the allowed public/manual TODO fields.
- [ ] Confirm README states what is mocked versus real.
- [ ] Confirm no executable file can operate private infrastructure.

## Suggested First Commit Message

```txt
Add sanitized Garage Admin showcase package
```
