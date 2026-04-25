# .github

Organization-wide defaults for PlanetPulse-ESG.

This repository is special: GitHub looks here for community health files (PR templates, issue templates, CODEOWNERS, etc.) when the per-repo equivalent doesn't exist. Nothing is copied into other repos — files here serve as runtime fallbacks.

## What's in here

| Path | Purpose |
|------|---------|
| `PULL_REQUEST_TEMPLATE.md` | Default PR template — auto-loaded for new PRs in any repo |
| `CODEOWNERS` | Default code owners — auto-assigns reviewers |
| `.github/ISSUE_TEMPLATE/` | Default issue templates — auto-loaded for new issues |
| `.github/workflows/` | Reusable workflows callable from any repo |
| `profile/README.md` | Org profile page (visible at github.com/planetpulse-esg) |
| `SECURITY.md` | Security disclosure policy |
| `CONTRIBUTING.md` | Contribution workflow |

> Note: GitHub accepts community health files in the repo root, the `.github/` folder, or the `docs/` folder. Each path resolves identically. The mix above (some at root, some in `.github/`) is the result of GitHub's own conventions: ISSUE_TEMPLATE and workflows must live inside `.github/`, while CODEOWNERS and PR templates work in either location.

## How a per-repo override works

If `planetpulse/.github/PULL_REQUEST_TEMPLATE.md` exists in the `planetpulse` repo, that one wins. Files here are fallbacks, not stamps — nothing is copied into other repos when they're created.

## Calling reusable workflows

From any repo's own workflow file:

```yaml
