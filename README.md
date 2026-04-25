# .github

Organization-wide defaults for PlanetPulse-ESG.

This repository is special: GitHub treats files inside the inner `.github/` folder as defaults that apply to **every other repository** in the `planetpulse-esg` organization.

## What's in here

| Path | Purpose |
|------|---------|
| `.github/PULL_REQUEST_TEMPLATE.md` | Default PR template — auto-loaded for new PRs in any repo |
| `.github/ISSUE_TEMPLATE/` | Default issue templates — auto-loaded for new issues |
| `.github/CODEOWNERS` | Default code owners — auto-assigns reviewers |
| `.github/workflows/` | Reusable workflows callable from any repo |
| `profile/README.md` | Org profile page (only visible if a public repo exists) |
| `SECURITY.md` | Security disclosure policy |
| `CONTRIBUTING.md` | Contribution workflow |
| `CODE_OF_CONDUCT.md` | Behavior expectations |

## How a per-repo override works

If `planetpulse/.github/PULL_REQUEST_TEMPLATE.md` exists in the `planetpulse` repo, that one wins. Files here are fallbacks, not forced.

## Calling reusable workflows

In any repo's own workflow:

```yaml
jobs:
  audit:
    uses: planetpulse-esg/.github/.github/workflows/audit-direct-push.yml@main
```

The double `.github/.github/` in the path is correct.

## Editing

Changes here propagate immediately to every repo. Run them through PR review, even though branch protection isn't enforced on Free.
