# Requirements — github-repo-analyzer skill & documentation workstream

**Document ID**: REQ-GROK-REPO-001  
**Version**: 1.1  
**Date**: 2026-09-24  
**Status**: Active  
**Owner**: MKOET (via Grok session)

## 1. Purpose

Define the functional and non-functional requirements for a reusable skill that can:

1. Analyze any GitHub repository.
2. Recreate its documentation to industry standards.
3. Produce or complete an end-to-end execution plan.
4. Clean the repository of obsolete files after the above work.
5. Record every significant event with monitoring metrics (time, cost, tools, outcome, etc.).

All work products for this effort are stored under `tools/grok-repo-work/` in the organization default repository (`MKOET/.github`).

## 2. Functional Requirements

### FR-01 — Analyze mode
The skill SHALL be able to connect to a GitHub repository, read its structure and high-signal files, and produce a structured summary covering:
- Purpose
- Plan / Roadmap
- Design
- Architecture (tech stack, structure, patterns)
- Execution tracking (CI/CD, activity, open work)
- Key files examined and gaps/recommendations

### FR-02 — Phase 1: New Documentation
The skill SHALL be able to:
- Generate an industry-standard documentation set (`docs/architecture.md`, `docs/design.md`, `docs/contributing.md`, `docs/roadmap.md`, root `README.md`, optional ADRs and API docs).
- Enforce separation of documentation (`docs/` + root README) from execution/source files.
- Validate every document claim against the live implementation (code as ground truth).
- Fix discrepancies by updating documentation.
- Present a clear proposal and obtain explicit user confirmation before any push.

### FR-03 — Phase 2: Execution Plan
The skill SHALL be able to:
- Produce or complete an end-to-end execution plan (`docs/execution-plan.md` or equivalent).
- Ensure the plan covers all major flows described in the architecture and design documents.
- Add any missing implementation tasks discovered during validation.
- Present the plan for approval before pushing.

### FR-04 — Phase 3: Clean obsolete files
The skill SHALL be able to:
- Identify files that are superseded, duplicated, temporary, or unreferenced after Phases 1–2.
- Never propose deletion of source code, active CI, Dockerfiles, package manifests, LICENSE, or still-referenced files.
- Present a complete candidate list with reasons and evidence.
- Require explicit confirmation before any deletion.
- Prefer the same feature branch used for earlier phases.

### FR-05 — Action documentation
Every action performed against the organization default repository (or any target repository when this workstream is active) SHALL be recorded in `tools/grok-repo-work/ACTIONS-LOG.md`.

### FR-06 — Output location
All output of this workstream SHALL be placed under a designated folder inside `tools/`. The chosen designation is `tools/grok-repo-work`.

### FR-07 — Event tracking & metrics (NEW)
Every significant skill run or workstream event SHALL be recorded in `tools/grok-repo-work/TRACKING-LOG.md` with at least the following fields:
- Timestamp
- Duration
- Mode / Phase
- Target repository
- Tools used
- Estimated cost / tokens (when available)
- Outcome (success / partial / failed / pending confirmation)
- Key operational metrics (files read, files written/proposed, cleanup candidates, discrepancies found)
- Notes and link to corresponding ACTIONS-LOG entry

The tracking log exists for monitoring, analysis, cost awareness, and continuous improvement of the skill.

## 3. Non-Functional Requirements

### NFR-01 — Safety
- Read-only analysis first.
- Explicit user confirmation required before any write or delete (unless the user has already instructed “apply / push / clean”).
- Prefer dedicated feature branches for changes.

### NFR-02 — Efficiency
- Prefer tree + selective file reads over exhaustive reads.
- Limit deep source inspection to entry points and modules referenced by documentation.

### NFR-03 — Consistency
- Documentation must match the implementation.
- Execution plan must map to documented architecture and design.
- Cleanup must not break links, CI, or build paths.

### NFR-04 — Traceability
- Every generated document and every cleanup candidate must cite evidence (file paths, commits, or search results).

### NFR-05 — Observability
- All significant events must be measurable (time, volume of work, outcome).
- Metrics must be recorded in a machine- and human-readable log.

## 4. Out of Scope

- Inventing features or APIs that do not exist in the code.
- Automatic force-push to the default branch without confirmation.
- Deletion of source, CI, or license files.

## 5. Acceptance Criteria

- [x] Skill description and body contain Analyze + three Recreate phases (Docs, Execution Plan, Clean).
- [x] All output for this workstream lives under `tools/grok-repo-work/`.
- [x] ACTIONS-LOG.md is updated for every action taken in the default repository.
- [x] REQUIREMENTS.md (this document) is present and versioned.
- [x] TRACKING-LOG.md exists and records events with time, cost, and operational metrics.
- [ ] User confirmation is obtained before any push or deletion.
- [ ] Skill body explicitly requires writing to TRACKING-LOG.md on significant runs.

## 6. Related Artifacts

- Skill location: `/home/workdir/.grok/skills/github-repo-analyzer/SKILL.md`
- Target application example: `MKOET/focal-point-framework-grok`
- This folder: `tools/grok-repo-work/`
- Tracking log: `tools/grok-repo-work/TRACKING-LOG.md`
