# MKOET Governance

## Overview

MKOET operates as a single-maintainer organization with domain ownership.
Each repository has one or more domain owners responsible for its direction,
quality, and security.

## Roles

### Maintainer

Full administrative access. Approves new repositories, renames, and major
architectural changes.

### Domain Owner

Responsible for one domain (`finance`, `ops`, `dev`, `product`, `infra`,
`data`). Reviews pull requests, triages issues, and approves releases within
their domain.

### Contributor

Submits pull requests, files issues, and participates in discussions.
Follows [CONTRIBUTING.md](CONTRIBUTING.md).

## Decision-Making

1. **Reversible decisions** â€” made by the domain owner
2. **Cross-domain decisions** â€” require maintainer approval
3. **Naming, licensing, or structural changes** â€” require maintainer
   approval and must update `docs/MIGRATION_MAP.md`

## Adding or Renaming Repositories

1. Open an issue describing the new or renamed repository
2. Apply the naming convention: `mkoet-{domain}-{purpose}`
3. Get maintainer approval
4. Update `docs/MIGRATION_MAP.md` if a legacy repository is being replaced

## Amendments

Changes to this document require maintainer approval and must be documented
in the commit message.