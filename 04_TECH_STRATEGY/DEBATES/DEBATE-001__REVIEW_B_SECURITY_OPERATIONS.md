# DEBATE-001 — REVIEW B: SECURITY, OPERATIONS, FAILURE MODES & COST

Status: `COMPLETE — PASS_WITH_CHANGES`
Date: 2026-09-17
Reviewer: independent adversarial AI, security/operations/failure/cost role
Repository edits by reviewer: none

Later user constraint: `DEC-0021` prohibits executing the prototype/spike ideas named in this historical review.
They survive only as no-code architecture, failure-scenario and evidence requirements.

## Verdict

The main direction is preserved, but the topic is not ADR-ready. Offline recall, approval-to-publish integrity,
emergency suspension and old-client compatibility are critical unresolved architecture areas.

## Critical Findings

### B-C1 — A fully offline device cannot learn a new recall instantly

Required policy/architecture: risk-tiered bounded offline validity, last validation time, untrusted device-time
behavior, foreground reconciliation, old-backup handling and separately preserved safe-stop/recovery content.

Disposition: `ACCEPTED / SPLIT TO DEDICATED DEBATE + TESTS ADDED`.

### B-C2 — Approval snapshot to published payload has a TOCTOU/integrity gap

Required design candidates include immutable/content-addressed approved snapshot, approval-to-hash binding,
release-manifest integrity, sole publication writer, database-level denial of direct editorial writes,
idempotent promotion, atomic current-version behavior and replay/downgrade protection.

Disposition: `ACCEPTED / PHYSICAL TOPOLOGY DEFERRED; REQUIRED TESTS ADDED`.

### B-C3 — Emergency recall cannot depend only on normal publishing/identity availability

Required design: narrow emergency suspension authority, step-up/break-glass controls, tamper-evident audit,
cache/CDN propagation evidence, RTO/RPO and restore drills. New application must not silently fail open while
safe-stop/recovery remains accessible.

Disposition: `ACCEPTED / DEDICATED DEBATE REQUIRED`.

### B-C4 — Old clients may not understand new safety semantics

Required contract: versioned consumer schema/capabilities, minimum compatible client per bundle, fail-closed
unknown safety-critical fields, N/N-1/long-dormant client tests and server-side application holds.

Disposition: `ACCEPTED / COMPATIBILITY TESTS ADDED`.

## Major Findings

| ID | Finding | Disposition |
|---|---|---|
| `B-M1` | Web security/deployment scores were unproven and mixed client form with backend guarantees. | Scores removed; web remains a reversible hypothesis only. |
| `B-M2` | “Server-side policy” lacked scope, revoked token, phishing-resistant MFA/step-up, self-approval and direct-API tests. | Security experiment scope expanded; detailed architecture remains separate debate. |
| `B-M3` | Audit events lacked tamper resistance, trusted time, separated authority, retention and restore continuity. | Added to risk register and identity/RBAC/audit debate scope. |
| `B-M4` | Hostile document/media/URL ingestion was not covered. | Hostile-ingestion experiment added. |
| `B-M5` | Local/account-light migration lacked stolen-device, wrong-account, backup/key lifecycle threat model. | Added as open risk and future security/data-boundary work. |
| `B-M6` | Supply-chain, CI/signing and OTA release authority were missing. | OTA claim qualified; release-governance debate and risks added. |
| `B-M7` | Private/shared/community classification and deletion/audit tension were underweighted. | Added to open security/privacy obligations. |
| `B-M8` | TCO scores had no staffing/HA/media/retention/on-call evidence. | Cost scores removed; TCO evidence explicitly required. |
| `B-M9` | Risk register lacked ownership, signals, triggers, contingency and residual-risk tracking. | Register schema expanded. |

## Abuse and Failure Scenarios Retained

- Airplane mode plus device-time rollback against cached eligibility.
- Old backup restoring recalled content/metadata.
- Content edit after review but before publication.
- Stolen publisher token plus attempted role change/release.
- Partial DB/CDN/manifest update producing mixed release state.
- Recall during IdP or publishing outage.
- Old app ignoring a new safety-critical field.
- Malicious PDF/ZIP/source URL or poisoned derived content.
- Compromised dependency/CI/signing pipeline.
- Local motorcycle/history data bound to the wrong profile.
- Backup restore resurrecting an invalid release without audit/recall epoch.
- Stale browser/service-worker UI against newer policy/API.

## Required Pre-ADR Work

1. Offline Safety & Recall Protocol.
2. Immutable Approval-to-Publish design and fault injection.
3. Emergency Suspension / DR game-day specification.
4. Client–Content Compatibility Matrix.
5. Authorization & Audit adversarial specification.
6. Hostile Ingestion specification.
7. Supply-chain and Release Governance review.
8. 12–24 month TCO and staffing model.

## Final Reviewer Position

`PASS_WITH_CHANGES`. Critical findings remain unresolved decisions even where the debate now names a mitigation or
test. They must not be reported as implemented controls.
