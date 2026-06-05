# Publication Commands

These commands are local preparation steps for Bryan to run manually. They do not create a GitHub repository through an API, do not contact GitHub except where explicitly labeled, and do not push until the final safety gate is complete.

Known public repo URL:

```txt
https://github.com/bryan060807/garage-admin-showcase.git
```

## Recommended Layout

Publish the contents of this `showcase/` directory as the root of `garage-admin-showcase`.

Reason: this directory already contains the standalone public package, including `README.md`, documentation, diagrams, mock fixtures, release notes, redaction guidance, and repo hygiene files. Keeping an extra `showcase/` subdirectory would make the public repo landing page less direct.

Expected repo root:

```txt
README.md
PACKAGE_NOTE.md
ARCHITECTURE.md
SECURITY.md
DEMO_SCRIPT.md
SUBMISSION_COPY.md
FINAL_SUBMISSION_CHECKLIST.md
FORM_READY_ANSWERS.md
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

## Option A: Initialize This Directory Locally

Run from PowerShell:

```powershell
# Start in the local showcase package directory.
git init
git branch -M main
git status --short
```

Attach the known remote only after Bryan has confirmed the public repository exists:

```powershell
git remote add origin https://github.com/bryan060807/garage-admin-showcase.git
git remote -v
```

## Option B: Clone The Empty Public Repo Then Copy Files

This option contacts GitHub. Use it only after Bryan has explicitly decided to do the clone step.

```powershell
$ShowcaseSource = (Get-Location).Path
Set-Location ..
git clone https://github.com/bryan060807/garage-admin-showcase.git garage-admin-showcase
Copy-Item -Path (Join-Path $ShowcaseSource '*') -Destination .\garage-admin-showcase -Recurse -Force
Copy-Item -Path (Join-Path $ShowcaseSource '.gitignore') -Destination .\garage-admin-showcase\.gitignore -Force
Set-Location .\garage-admin-showcase
git status --short
```

## Local Safety Checks

Run from the package root before staging:

```powershell
Get-ChildItem -Path .\mock-data -Filter *.json | ForEach-Object { $null = Get-Content -Raw $_.FullName | ConvertFrom-Json; Write-Host "JSON OK $($_.Name)" }
Select-String -Path .\diagram\architecture.mmd -Pattern '^flowchart\s+LR','subgraph','classDef'
$Files = Get-ChildItem -Recurse -File
Select-String -Path $Files.FullName -Pattern 'sk-[A-Za-z0-9_-]{20,}','ghp_[A-Za-z0-9_]+','xox[baprs]-[A-Za-z0-9-]+','AKIA[0-9A-Z]{16}','-----BEGIN .*PRIVATE KEY-----','password\s*[:=]','token\s*[:=]','authorization\s*[:=]','cookie\s*[:=]','connectionString\s*[:=]','[A-Z]:\\Users\\','private hostname','private route','tunnel ID' -CaseSensitive:$false
Select-String -Path $Files.FullName -Pattern '10\.\d{1,3}\.\d{1,3}\.\d{1,3}','172\.(1[6-9]|2\d|3[0-1])\.\d{1,3}\.\d{1,3}','192\.168\.\d{1,3}\.\d{1,3}'
Select-String -Path $Files.FullName -Pattern 'TODO'
```

Expected findings:

- JSON files should parse.
- Mermaid should contain `flowchart LR`, `subgraph`, and `classDef`.
- Sensitive-keyword searches may find policy/checklist wording only.
- Private IP search should return no matches.
- TODO search should return only allowed public/manual fields: hosted/demo URL, video URL, screenshot/cover image URL, submitter identity, public contact, license choice, and website/social link.

## Stage And Commit

Run after the local safety checks are acceptable:

```powershell
git status --short
git add README.md PACKAGE_NOTE.md ARCHITECTURE.md SECURITY.md DEMO_SCRIPT.md SUBMISSION_COPY.md FINAL_SUBMISSION_CHECKLIST.md FORM_READY_ANSWERS.md REPO_RELEASE_PLAN.md COVER_IMAGE_BRIEF.md SCREENSHOT_SHOT_LIST.md REDACTION_CHECKLIST.md PUBLICATION_COMMANDS.md LICENSE.md .gitignore diagram mock-data
git status --short
git commit -m "Add sanitized Garage Admin showcase package"
```

## Remote Check

This contacts GitHub only if a remote is configured:

```powershell
git remote -v
git status --short --branch
```

## Final Safety Gate Before Push

Do not push until Bryan has reviewed the redaction checklist and confirmed no private data is present.

Bryan should confirm:

- `REDACTION_CHECKLIST.md` has been reviewed.
- `FINAL_SUBMISSION_CHECKLIST.md` has been reviewed.
- The package contains only sanitized docs, diagrams, and mock JSON fixtures.
- No private control-plane source, live routes, logs, credentials, PM2 metadata, private paths, account identifiers, or tunnel details are present.
- The license choice is intentional.

## Push Command

Run only after Bryan explicitly approves the push:

```powershell
git push -u origin main
```
