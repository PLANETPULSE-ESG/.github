# Contributing to PlanetPulse

> The full Engineering Workflow Guide will move to Docmost once it's deployed (docs.planetpulse.cloud). Until then, this file is the canonical reference.

## Workflow

1. **Plane issue first.** Find or create the Plane issue (PP-XXXX) before writing code.
2. **Fork the repo** to your personal GitHub account.
3. **Branch:** `feature/PP-XXXX-short-description`. Hotfixes use `hotfix/PP-XXXX-...`.
4. **Commit messages:** include the Plane ID. Example: `PP-142: add emissions export`.
5. **Open a PR** from your fork to `planetpulse-esg/<repo>:main`. Fill in the PR template.
6. **Wait for CI** — lint, type-check, tests, gitleaks, trivy must all pass.
7. **Wait for review** — at least one approval from `@planetpulse-esg/eng-leads`. Two for changes to `packages/auth/` or `packages/db/`.
8. **Squash-merge.** Plane closes the issue automatically via webhook (once integration is set up).

## Branch naming

Format: `<type>/PP-<number>-<short-description>`

Type prefixes: `feature` · `fix` · `hotfix` · `chore` · `refactor` · `docs` · `test`

Example: `feature/PP-142-add-emissions-export`

## Commit messages

Format: `<type>: <short summary in present tense>`

Examples:
- `feat: add /api/exports/emissions endpoint`
- `fix: prevent login redirect loop on expired session`
- `chore: bump Next.js to 15.2.1`

Header line under 72 chars, lowercase, present tense, no period.

## Pre-push hook

Each repo includes a Husky pre-push hook that blocks pushes to `main` from your local machine. Don't bypass it with `--no-verify`. If you have a legitimate reason, post in the eng channel first.

## Code review expectations

+------------+------------------------------------------------------------------+
| Role       | Expectation                                                      |
+------------+------------------------------------------------------------------+
| Author     | Self-review before review. Respond within 1 business day.        |
| Reviewer   | Review within 1 business day. Block issues; "nit:" for style.    |
| Eng-leads  | Final approval. Resolve disagreements.                           |
+------------+------------------------------------------------------------------+

## What to flag in review

- Multi-tenancy bugs (missing `tenant_id` filter, RLS bypass)
- Secrets in code or config
- New dependencies — is the package maintained? license-compatible?
- Migrations that aren't reversible
- N+1 queries on hot paths
- Missing tests for new logic

## Things you must never do

- Force-push to a shared branch
- Commit secrets, API keys, or `.env` files (rotate at source if you do — deletion isn't enough)
- Use `git push --force` (use `--force-with-lease` instead)
- Bypass pre-commit hooks with `--no-verify`
- Merge your own PR without review
- Push directly to `main`

## Questions

Ask in the eng channel or DM Hayyan. Don't suffer in silence.