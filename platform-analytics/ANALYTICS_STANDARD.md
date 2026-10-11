# Platform Analytics Storage and Publication Standard

**Status:** Required platform standard  
**Owner:** MKOET organization maintainers  
**Canonical repository:** [`MKOET/.github`](https://github.com/MKOET/.github)  
**Canonical root:** `platform-analytics/`

## 1. Policy

All durable MKOET repository-analysis results must be stored in this repository under `platform-analytics/repositories/<repository-name>/`. This rule applies to every analyzer, manager, converter, scheduled run, and human-triggered platform workflow. A report is not considered published until the central repository contains the reviewed artifacts on a remote branch and the remote commit/file URLs have been verified.

Coding-industry standards that govern all platform repositories are maintained in `platform-analytics/standards/`. Standards are version-controlled and reviewed here; platform skills should link to this canonical copy rather than maintain divergent duplicates.

## 2. Required layout

```text
platform-analytics/
  README.md
  ANALYTICS_STANDARD.md
  standards/
    CODING_INDUSTRY_STANDARDS.md
  repositories/
    README.md
    <repository-name>/
      latest.json
      state.json
      collect.json
      report-YYYY-MM-DD.md
      _weekly-YYYY-MM-DD.md
      runs/YYYY-MM-DD/   # optional immutable per-run snapshot
```

`<repository-name>` is the canonical repository name, lowercase, without an organization prefix. The report metadata must retain the canonical full name `MKOET/<repository-name>`.

`latest.json` is the latest successfully published summary. `state.json` contains the state/history needed by the analyzer. `collect.json` contains the evidence necessary to reproduce the report, but it must be redacted and reviewed before publication. The dated Markdown report is the human-readable deliverable. The weekly roll-up is published when generated. A dated `runs/` snapshot may be used for immutable run history; do not silently overwrite dated artifacts.

## 3. Publication workflow

1. Resolve the analyzed repository and record its default/source branch, source HEAD SHA, canonical origin, run timestamp (UTC), and analyzer version/commit.
2. Run preflight and analysis. Do not claim successful analysis when a required prerequisite fails; record blockers explicitly.
3. Review all generated outputs for correctness and unsupported claims.
4. Scan every artifact for credentials, access tokens, private keys, passwords, connection strings, populated environment values, personal data, and sensitive source excerpts. Redact unsafe material and regenerate/validate dependent outputs. Never publish a secret to preserve completeness; mark the affected evidence unavailable/redacted.
5. Stage only the intended `platform-analytics/repositories/<repository-name>/` artifacts in a dedicated branch in `MKOET/.github`. Do not commit analytics to the analyzed repository.
6. Commit and push the branch to `MKOET/.github`, then open a pull request when supported. Never force-push, bypass branch protection, or push directly to the default branch. Do not merge without required review/authorization.
7. Verify the remote commit SHA and each expected artifact at the remote branch. Only then return the verified report URL and summary URL. If any step fails, report the exact blocker and do not invent a published link.

The publication branch must be based on the current canonical default branch. If concurrent updates occur, safely update/rebase the publication branch without discarding work. Never overwrite another repository's report branch or unrelated files.

## 4. Metadata contract

Each run's summary and Markdown report must identify, where available:

- canonical source repository (`MKOET/<repo>`), source branch, and source commit SHA;
- UTC analysis timestamp and analyzer version/commit;
- analysis mode/status, including degraded or partial mode;
- checks actually executed and their observed outcomes;
- known limitations, unavailable evidence, and blockers;
- redactions or excluded evidence, without reproducing sensitive values;
- central report path and publication commit SHA once published.

Distinguish source-observed facts, analyzer heuristics, and human/semantic assessments. Do not label analysis as a security audit or functional validation unless separate evidence supports that claim.

## 5. Privacy and retention

- Public visibility of this repository means all published analytics are public. Publish only evidence approved for public release.
- Never publish secrets, credentials, populated `.env` files, private user data, or unredacted source fragments that are not necessary to explain a finding.
- If an artifact cannot be made safe, do not publish that artifact; publish a status note describing the omission and blocker. Security takes precedence over raw-data completeness.
- Keep dated reports for history unless a maintainer-approved retention policy says otherwise. Correct erroneous latest results through a new dated run; do not silently rewrite historical reports.
- Do not include analytics artifacts in converted application repositories by default.

## 6. Converter integration

The converter consumes the centrally published `latest.json` and dated Markdown report for the specified source repository. It must resolve these paths automatically from `MKOET/.github`, validate that the report metadata matches the requested source repository and source SHA, and pass the report path to its validator. A local temporary copy may be used for tooling that requires a path outside the source and target checkouts, but it must be a verified copy of the central artifact and must not become a second canonical store.

If the central report is missing, stale relative to the selected source revision, inaccessible, or fails validation, stop the dependent conversion step and report the exact problem. Do not fall back silently to a repository-local report or ask the user to locate report files manually.

## 7. Completion definition

Analytics publication is complete only after redaction review, commit/push to the central repository branch, remote SHA and artifact verification, and return of a real direct report URL. A local report, local commit, successful push without file verification, or fabricated URL is not completion.
