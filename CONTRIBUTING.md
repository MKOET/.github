# Contributing to MKOET

All contributions across MKOET repositories must follow the naming and
structure conventions documented here and in
[`docs/MIGRATION_MAP.md`](docs/MIGRATION_MAP.md).

## Repository Naming

New repositories must use the format `mkoet-{domain}-{purpose}`.

- **Domains**: `finance`, `ops`, `dev`, `product`, `infra`, `data`
- **Purpose**: a short noun phrase such as `ledger`, `auth-service`,
  `repo-manager`

Existing repositories are NOT renamed. The complete legacy-to-convention
mapping is in [`docs/MIGRATION_MAP.md`](docs/MIGRATION_MAP.md).

## Required Files in Every Repository

- `README.md` â€” purpose, setup, usage
- `LICENSE` â€” added individually (not inherited from `.github`)
- `.gitignore` â€” appropriate to the language
- `.github/workflows/` â€” CI pipeline

Issue templates and the pull request template are inherited from this
repository. Do not duplicate them unless a repository needs a specialized
version.

## Branch Naming

| Type | Pattern | Example |
|---|---|---|
| Feature | `feat/{ticket}-{description}` | `feat/MKO-42-add-export` |
| Fix | `fix/{ticket}-{description}` | `fix/MKO-87-auth-timeout` |
| Docs | `docs/{description}` | `docs/api-reference` |
| Chore | `chore/{description}` | `chore/update-deps` |

## Commit Convention

Format: `{type}({scope}): {subject}`

Types: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`

Examples:

- `feat(auth): add OAuth login`
- `fix(api): handle empty response`

## Issue Labels

- `domain:{area}` â€” finance, ops, dev, product
- `type:{kind}` â€” bug, feature, docs, chore
- `priority:{level}` â€” critical, high, medium, low

## Pull Requests

- Title follows the commit format
- Body references an issue: `Closes #123`
- Minimum one approving review
- All CI checks must pass