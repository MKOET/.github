# MKOET Repository Naming Migration Map

## Policy

Existing repositories are NOT renamed. This document records the mapping
between legacy repository names and their convention-compliant equivalents.

New repositories created by the MKOET platform must use the convention format:
`mkoet-{domain}-{purpose}`

## Mapping Table

### Infrastructure (domain: infra)

| Legacy Name | Convention Name | Notes |
|---|---|---|
| env-paperclip-aide | mkoet-infra-paperclip-environment | Environment repo |
| env-deerflow-aide | mkoet-infra-deerflow-platform | Current agent platform |
| env-docker-aide | mkoet-infra-docker-environment | |
| env-grok-aide | mkoet-infra-grok-environment | |
| env-copilot-aide | mkoet-infra-copilot-environment | |
| env-docker-openbot | mkoet-infra-openbot-environment | |
| local_ai_env | mkoet-infra-local-ai-environment | |

### Client Applications (domain: product)

| Legacy Name | Convention Name |
|---|---|
| clients-koet-alpha | mkoet-product-client-alpha |
| clients-koet-beta | mkoet-product-client-beta |
| clients-koet-gamma | mkoet-product-client-gamma |
| clients-koet-delta | mkoet-product-client-delta |
| clients-koet-epsilon | mkoet-product-client-epsilon |
| clients-koet-zeta | mkoet-product-client-zeta |
| clients-koet-eta | mkoet-product-client-eta |
| clients-koet-theta | mkoet-product-client-theta |
| clients-koet-lota | mkoet-product-client-lota |
| clients-koet-kappa | mkoet-product-client-kappa |
| clients-koet-mu | mkoet-product-client-mu |
| web-clients-koet-ai-alpha | mkoet-product-web-client-ai-alpha |

### Backend Services (domain: ops)

| Legacy Name | Convention Name | Status |
|---|---|
| services-koet-beta | mkoet-ops-service-beta |
| services-koet-epsilon | mkoet-ops-service-epsilon | ✅ Converted 2026-10-09 |
| services-koet-mu | mkoet-ops-service-mu |
| server-koet-ai-alpha | mkoet-ops-server-ai-alpha |
| server-koet-ai-beta | mkoet-ops-server-ai-beta |

### Frameworks and Tooling (domain: dev)

| Legacy Name | Convention Name |
|---|---|
| focal-point-framework | mkoet-dev-focal-point-core |
| focal-point-framework-claude | mkoet-dev-focal-point-claude |
| focal-point-framework-grok | mkoet-dev-focal-point-grok |
| focal-point-framework-chatgpt | mkoet-dev-focal-point-chatgpt |
| singularity-networks-framework-chatgpt | mkoet-dev-singularity-chatgpt |

### Test and Automation (domain: dev)

| Legacy Name | Convention Name |
|---|---|
| testapp-automation | mkoet-dev-testapp-automation |
| test-rep01 | mkoet-dev-test-rep-01 |
| hereweare-automation | mkoet-dev-hereweare-automation |
| dify-test-bootstrap-001 | mkoet-dev-dify-bootstrap-01 |
| dify-test-bootstrap-002 | mkoet-dev-dify-bootstrap-02 |
| dify-test-bootstrap-003 | mkoet-dev-dify-bootstrap-03 |

### Organization-Level (no change)

| Name | Reason |
|---|---|
| .github | GitHub requires this exact name for org-wide conventions |

## Rules

1. Do NOT rename existing repositories without an explicit migration plan.
2. New repositories created by the MKOET platform must use the convention.
3. If a repository is renamed later, update this file to reflect the change.
4. Domain values are: finance, ops, dev, product, infra, data.
5. Purpose is a short noun phrase (ledger, auth-service, repo-manager).

## Revision History

- 2026-10-09 — Initial mapping created.
