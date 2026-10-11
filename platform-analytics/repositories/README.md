# Repository Analytics Index

This directory contains centrally published, repository-specific analytics. Each repository gets a stable lowercase directory: `platform-analytics/repositories/<repository-name>/`.

## Expected artifacts

- `latest.json` — most recently verified published summary.
- `state.json` — analyzer state/history needed for comparisons.
- `collect.json` — evidence payload only after privacy/secret redaction review.
- `report-YYYY-MM-DD.md` — dated human-readable report.
- `_weekly-YYYY-MM-DD.md` — weekly roll-up when produced.
- `runs/YYYY-MM-DD/` — optional immutable per-run snapshots.

Each report must identify the canonical source repository and source commit. Do not treat this README or an unverified local output as evidence that a repository has been analyzed. A repository directory is created when the first safe report is ready for publication.
