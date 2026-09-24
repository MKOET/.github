# Skill Overview — github-repo-analyzer

**Location**: User skill at `/home/workdir/.grok/skills/github-repo-analyzer/`  
**Last validated**: 2026-09-24  
**Lines**: ~254

## Capabilities

| Mode / Phase | Description |
|--------------|-------------|
| **Analyze** | Connect to a repo, read structure + high-signal files, produce structured summary (Purpose, Plan, Design, Architecture, Execution Tracking). |
| **Phase 1 — New Documentation** | Generate industry-standard docs, enforce docs vs. execution separation, validate against code, fix discrepancies. |
| **Phase 2 — Execution Plan** | Produce/complete end-to-end execution plan aligned with the new docs; add missing implementation tasks. |
| **Phase 3 — Clean** | Identify and (after confirmation) remove superseded, duplicated, or obsolete files. Never touch source/CI/LICENSE. |

## Safety Rules (enforced by the skill)

- Always analyze before writing or deleting.
- Prefer a new branch for any push or cleanup.
- Require explicit user confirmation unless the user already said “apply / push / clean”.
- Never invent features that do not exist in the code.
- Never delete source, active CI, Dockerfiles, package manifests, or LICENSE.

## Typical trigger phrases

- “Analyze https://github.com/owner/repo”
- “Recreate the documentation for owner/repo to industry standards”
- “Phase 1: rebuild docs. Phase 2: complete the execution plan. Phase 3: clean obsolete files”
- “After the new docs, clean the repository of obsolete files”

## Current status

Skill is validated and ready for use. First real target discussed: `MKOET/focal-point-framework-grok`.
