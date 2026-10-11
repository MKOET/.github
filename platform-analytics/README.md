# MKOET Platform Analytics

This directory is the canonical, organization-wide home for **platform analytics and coding-industry standards**. It lives in [`MKOET/.github`](https://github.com/MKOET/.github), the organization community-health and policy repository.

## Contents

- [`ANALYTICS_STANDARD.md`](ANALYTICS_STANDARD.md) — required storage, publication, privacy, metadata, and review contract.
- [`standards/CODING_INDUSTRY_STANDARDS.md`](standards/CODING_INDUSTRY_STANDARDS.md) — shared engineering and code-quality baseline.
- [`repositories/`](repositories/README.md) — repository-partitioned analytics artifacts.

## Authority

This directory is the single source of truth for organization-level analytics results and shared coding standards. Analyzer/converter implementations may keep temporary working files in local checkouts, but their published, durable analytics must be delivered here. Do not treat a report stored only in an analyzed repository or a separate reporting remote as published platform analytics.

Changes to the standard follow normal review in this repository. Reports are submitted on a dedicated branch and reviewed via pull request; no workflow may bypass branch protections or merge without authorization.
