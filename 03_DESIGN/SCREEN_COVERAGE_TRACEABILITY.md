# SCREEN COVERAGE TRACEABILITY

Status: APPROVED
Approved by: USER — 2026-09-15
Source: approved Phase-2 product snapshot + `SCREEN_INVENTORY_REVIEW.md`

Bu dosya approved working screen/state architecture'in approved journeys ve business-rule clusters ile coverage izini tutar. Screen IDs implementation routes degildir.

## Journey Coverage

| Journey | Approved working screen coverage |
|---|---|
| J-001 Known task → prepare → execute → verify → record | 005 → 009 → 010 → 011/012 → 014 → 018 → 026 |
| J-002 Symptom → diagnosis → repair | 005 → 019 → 020 → 021 → 010 |
| J-003 Variant/modification mismatch | 003 → 004 → 013 or 010/011 |
| J-004 Readiness stop → remediation → re-entry | 011 → 012 → 011/014 |
| J-005 High-consequence teaching → conditional application | 013 → 011/012 → 014 |
| J-006 Stuck/mistake/unexpected behavior | 014 → 015 → 018/re-entry |
| J-007 Pause/version/freshness/remap/resume | 016 → 017 → 014/015/018 |
| J-008 Maintenance due/remind/record | 022 → 023/024 → 009/027 |
| J-009 Review/correct/dispute history | 025 → 026 → 028 |
| J-010 External service/hobby contribution | 027 → 026 → 028 |
| J-011 Community lifecycle | 038 read separate community content; 035 → 036 contribution/review; downstream 028/029 when relevant |
| J-012 Commercial support without technical influence | Constraint across 009-014/023/037; no marketplace screen invented |
| J-013 Multi-motorcycle isolation → advanced garage | 008 + motorcycle-scoped 005/022/025; 037 for gated advanced capacity |
| J-014 Shared motorcycle collaboration | 034 → 027/026/028 |
| J-015 Ownership transfer | 031 → 032 → 025/026 |
| J-016 Archive / actual delete | 031 → archive state or 033 |
| J-017 User data export | 025 → 030 |
| J-018 Roadside/offline continuity | States across 010/013-018/029; no artificial standalone offline screen |
| J-019 Accessible active repair | 011-018, especially 014 with safety invariants |
| J-020 Record-only first use | 001 → 002-005 → 027/022 |
| J-021 Account-light → profile migration | 006 → 007 |
| J-022 Active-repair interruption | 014 → 016 → 014/015/017 |
| J-023 Risk-adaptive evidence explanation | 026/028 + compact provenance in 010/014 |

## Late Refinement Coverage

| Refinement | Coverage |
|---|---|
| Evidence withdrawal → dependent re-review | 026,028,029,036 |
| New evidence → dispute resolution/refinement | 028 → 026 |
| Current claim state vs claim-event history | 026 |
| Material guide change after physical action | 017 |
| Long interruption / state drift | 016 |
| Migration cancel/failure | 007 |
| Correction reach-back by impact depth | 029 |
| Trust facts invariant across experience modes | 010-018,026-029 |
| Basic shared-bike trust | 034 |
| Advanced coordination as scale value | 034 + 037 |
| Active → inactive motorcycle historical continuity | 008,025-030,037 |
| Selected-guide lifecycle / withdrawal | 010,017,026,029,037 |
| Entitlement loss during physical repair | 014-018; 037 cannot interrupt safe closure |
| Premium downgrade preserving trust | 008,025-030,034,037 |

## Business-Rule Cluster Coverage

| Rule cluster | Representative approved rules | Approved working coverage |
|---|---|---|
| Motorcycle fit / variant certainty | BR-001–003,029-030,050-051,087-088 | 003,004,010-013,015 |
| Provenance / source conflict | BR-004–006,093-094,114-116 | 010,013,014,026,028 |
| Experience adaptation | BR-007-008 + late trust refinements | 011-014,026 |
| Readiness / tools / safe equivalent | BR-009-010,036-038,081-083,108-110 | 011,012 |
| Safety / stop gates | BR-011–014,052-053,126-127 | 011-018,019 |
| Diagnosis | BR-015–017,040-042 | 019-021 |
| Recovery / interruption | BR-018–021,148-149 | 015-018 |
| Completion semantics | BR-022-024 | 018,022,027 |
| Maintenance / uncertainty | BR-025-027,044,047,060-062 | 022-024 |
| Content governance / correction | BR-031-035 | 010,017,029,035-036 |
| Visual correctness | BR-039 | 003,014 |
| Multi-motorcycle isolation | BR-045,134-135 | 008 + motorcycle-scoped screens |
| External-work trust | BR-046,120,150 | 026-028 |
| Notifications / critical priority | BR-054-056,095-097 | 023,024,029; control placement remains design gap |
| History integrity / correction | BR-057-059,131,136-138 | 025,026,028,032 |
| Estimates | BR-063-064 | 010,011 |
| Community/privacy/moderation | BR-065-069,089-092,139-142 | 035,036,038,028,029 |
| Commercial neutrality | BR-070-073 | Constraint across task/support surfaces; no invented commerce home |
| Offline/freshness | BR-075,104,124-125 | 010,013-017 |
| Data ownership / portability / deletion | BR-076-080,111,113 | 030-033 |
| First value / profile transition | BR-105,128-130,147 | 001,005-007 |
| Ownership transfer | BR-102,117-118,137-138 | 031,032,026,028 |
| Accessibility/localization | BR-106-107,126-127 | Cross-cutting; especially 011-018; preference placement unresolved |
| Evidence disclosure depth | BR-144-146 | 010,014,026,028 |
| Collaboration | BR-101,141-143 + late collaboration refinements | 034,026-028 |
| Entitlement / historical preservation | Batch-08 rules/refinements | 008,010,014-018,025-030,034,037 |

## Reverse Audit

Main-manager result before user approval: `PASS_WITH_REFINEMENTS`.
User approval: 2026-09-15.

No context is present solely because generic mobile apps usually contain such a screen.

Explicitly NOT invented as canonical screens:
- generic dashboard/KPI home,
- permanent social feed,
- marketplace home,
- achievements/badges,
- AI chat home,
- statistics dashboard,
- settings megascreen,
- subscription pricing page,
- permanent bottom-nav architecture.

Main-manager refinement added `SCR-038` because confirmed product rules require community Q&A/experiences to remain separate from official guide steps and carry provenance/review-status semantics when present.

## Approval Boundary

This traceability is APPROVED as the working coverage map for downstream screen-family/specification work.

It does not lock route implementation, visual components, MVP prioritization or technology.