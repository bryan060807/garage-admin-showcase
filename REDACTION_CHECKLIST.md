# Redaction Checklist

Use this checklist before publishing a repository, screenshot, video, slide deck, or Showcase submission.

## Must Not Appear

- [ ] API keys, tokens, passwords, private keys, certificates, or service account JSON.
- [ ] Raw `.env` files or environment dumps.
- [ ] OAuth access tokens, refresh tokens, or account identifiers.
- [ ] Cloud provider tokens, tunnel IDs, or private route details.
- [ ] Live private hostnames, internal admin URLs, or private tunnel URLs.
- [ ] Private IPs other than approved local placeholders like `127.0.0.1`.
- [ ] Real PM2 metadata that may include environment values.
- [ ] Raw logs with private paths, user data, request bodies, credentials, or account details.
- [ ] Browser tabs showing private dashboards, accounts, email, billing, or admin consoles.
- [ ] Terminal output that includes secrets, personal paths, or live operational commands.

## Allowed Placeholders

- [ ] `example.invalid`
- [ ] `localhost`
- [ ] `127.0.0.1`
- [ ] `demo-windows-host`
- [ ] `demo-fedora-control-plane`
- [ ] `demo-postgres`
- [ ] `demo-service-a`
- [ ] `demo-service-b`

## Screenshot / Video Review

- [ ] Crop or blur browser bookmarks, account menus, extension icons, and OS notifications.
- [ ] Hide terminal prompts if they reveal private usernames, hostnames, or paths.
- [ ] Use mock data views whenever possible.
- [ ] Confirm the UI does not show real service names that should remain private.
- [ ] Confirm any health or log views are sanitized and capped.
- [ ] Confirm no QR codes, signed URLs, auth headers, or cookies are visible.
- [ ] Confirm the final video does not show accidental clipboard or autocomplete secrets.

## Repository Review

- [ ] Run a secret scanner before publishing.
- [ ] Search for `.env`, `token`, `password`, `secret`, `authorization`, `cookie`, and `connection`.
- [ ] Search for private hostnames and private IP ranges.
- [ ] Confirm all JSON fixtures are mock data.
- [ ] Confirm no scripts can contact or control the private system.
- [ ] Confirm TODOs are limited to hosted/demo URL, video URL, screenshot/cover image URL, submitter identity, public contact, license choice, and website/social link.

## Final Statement

- [ ] The published artifact clearly states that it is a sanitized reference package.
- [ ] The published artifact does not claim OpenAI endorsement or acceptance.
- [ ] The published artifact explains what is mocked versus real.
