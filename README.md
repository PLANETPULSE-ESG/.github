# .github

Organization-wide defaults for PlanetPulse-ESG.

This repository is special: GitHub treats files inside the inner `.github/` folder as defaults that apply to every other repository in the `planetpulse-esg` organization.

## What's in here

+-----------------------------------------------+--------------------------------------------------------------+
| Path                                          | Purpose                                                      |
+-----------------------------------------------+--------------------------------------------------------------+
| .github/PULL_REQUEST_TEMPLATE.md              | Default PR template for all repos                            |
| .github/ISSUE_TEMPLATE/                       | Default issue templates                                      |
| .github/CODEOWNERS                            | Default reviewers auto-assigned                              |
| .github/workflows/                            | Reusable workflows                                           |
| profile/README.md                             | Organization profile README (shown on org homepage)          |
| SECURITY.md                                   | Security disclosure policy                                   |
| CONTRIBUTING.md                               | Contribution guidelines                                      |
| CODE_OF_CONDUCT.md                            | Community behavior expectations                              |
+-----------------------------------------------+--------------------------------------------------------------+

## Important note about `profile/README.md`

- This file is **not a fallback config**
- It is used by GitHub to render the **organization’s public profile page**
- It only shows up if:
  - The repo is public
  - The file is located at `profile/README.md`

## How per-repo overrides work

If a repository defines its own file (e.g. `.github/PULL_REQUEST_TEMPLATE.md`), it overrides the default defined here.

## Calling reusable workflows

In any repo:

```yaml
jobs:
  call-workflow:
    uses: planetpulse-esg/.github/.github/workflows/<workflow-file>.yml@main
```