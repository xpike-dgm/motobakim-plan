# DEBATE-002 — REVIEW A: PRODUCT SAFETY & USER TRUST

Status: `COMPLETE — PASS_WITH_CHANGES`
Date: 2026-09-17
Reviewer: independent Luna Max adversarial review
Repository edits by reviewer: none

## Verdict

C+D is directionally compatible with approved product rules, but is not ADR-ready. Several safety guarantees were
stronger than the policy could yet enforce.

## Critical Findings and Disposition

| ID | Finding | Manager disposition |
|---|---|---|
| `C-01` | Release metadata alone does not stop replay/downgrade or restored recalled state. | Added required authenticated/complete context, ordering/anti-rollback property, capability binding and restored-eligibility distrust; exact technology remains open. |
| `C-02` | Risk tiering lacked a safe default for unknown or transitive risk. | Unknown holds; guide inherits highest dependent consequence; changes require attributable review. |
| `C-03` | Recall during active physical work lacked an explicit safe-stop contract. | Offline start now requires complete independently reviewed task-specific recovery coverage for all reachable states; safe-stop/recheck/remap/closure states made explicit. |
| `C-04` | Foreground reconciliation cannot eliminate recall immediately after a check. | Residual race recorded; highest-consequence always-online vs tightly bounded server authority remains explicit user/strategy decision. |

## Major Findings and Disposition

- Old-client fail-closed needed capability negotiation before use and no incompatible fallback — incorporated.
- Time/reboot policy could overblock normal reboot while still failing restore/clone — intact-anchor distinction added.
- Browser online-only mutation needed stale-cache, revoked-session and unknown-commit handling — incorporated.
- Dependency closure and interaction-depth reach-back were absent — added to evidence model.

## Minor Corrections

- Ambiguous states mapped to `SCR-015`–`SCR-018`.
- Fresh install with partial content now has explicit no-application/no-recovery-authority behavior.
- Evidence scenarios require pass/fail and visible-state criteria.
- Account-light use is explicitly not converted into a profile prerequisite.

## Sound Elements

- Teaching/history/application distinction.
- Resume revalidation and material-change remap.
- Push as hint, not authority.
- Restore does not create current authority.
- Old-client incompatibility fails closed.
- Browser authoritative mutations stay online.
- No-code evidence process.

Final position: `PASS_WITH_CHANGES`; critical properties remain unimplemented/unapproved until later architecture and ADR.
