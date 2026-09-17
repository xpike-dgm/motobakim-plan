# DOCUMENT REGISTRY

Bu dosya kritik belgelerin nerede yasadigini ve otorite seviyesini listeler.

Status degerleri: `EMPTY`, `DRAFT`, `REVIEW`, `APPROVED`, `LOCKED`, `SUPERSEDED`, `ARCHIVED`.

| Alan | Ana belge | Status |
|---|---|---|
| Hafiza / kontrol | `00_CONTROL/*` | APPROVED |
| Calisma sistemi | `01_WORKSPACE/*` | APPROVED |
| Urun kesfi | `02_DISCOVERY/*` | APPROVED |
| Tasarim | `03_DESIGN/*` | REVIEW |
| Teknoloji tartismasi | `04_TECH_STRATEGY/*` | EMPTY |
| ADR | `05_ADR/*` | EMPTY |
| Teslimat planlama | `06_DELIVERY_PLANNING/*` | EMPTY |
| AI-native mimari | `07_AI_ARCHITECTURE/*` | EMPTY |
| Repository bootstrap | `08_REPOSITORY_BOOTSTRAP/*` | EMPTY |

`01_WORKSPACE` approved; Gate 1 -> 2 tamamlandi.

`02_DISCOVERY` Q006-Q245 raw evidence + approved synthesis snapshot ile APPROVED. Canonical entry point: `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`. Gate 2 -> 3 PASSED.

## Approved Project-Scope Addendum

- `00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md` — **APPROVED REQUIREMENT**
  - Internal motorcycle/technical Data & Content Operations capability is required.
  - Exact web/desktop/hybrid and technology architecture remain open.
  - Targeted requirements/workflow/platform-independent screen-workspace architecture addendum required before final Gate 3 review.

## Manager-Chat Transfer Controls

- `00_CONTROL/NEW_MANAGER_CHAT_HANDOFF.md` — ACTIVE transfer guide
- `00_CONTROL/NEW_MANAGER_CHAT_PROMPT.md` — ACTIVE fresh-chat bootstrap prompt

These files exist because the prior main-manager conversation became context-heavy. Repository truth remains authoritative; the fresh manager must not depend on old-chat memory.

## Phase-3 Design

`03_DESIGN` is the active phase and remains registry-level `REVIEW` because Gate 3 -> 4 has not passed.

Approved working design authorities include:
- `BRAND_NAME.md` — Kavriva
- `LOGO_DIRECTION.md` — L05A
- `ANCHOR_UX_STRUCTURE.md` — U04
- `ANCHOR_VISUAL_STYLE.md` — V10
- `SCREEN_CATALOG.md`
- `NAVIGATION_MAP.md`
- `STATE_MATRIX.md`
- `DESIGN_PRINCIPLES.md`
- `SCREEN_COVERAGE_TRACEABILITY.md`
- `GLOBAL_NAVIGATION.md` — 5-tab bottom bar
- `SCREEN_FAMILY_SPECS.md`
- `SCREEN_FAMILY_SPEC_REVIEW.md`
- `AI_USTA_UX_STRUCTURE.md`
- `MAIN_SHELL_VISUAL_REFERENCES.md`
- `GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md`
- `ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`
- `DIAGNOSIS_VISUAL_REFERENCES.md`
- `MAINTENANCE_REMINDER_VISUAL_REFERENCES.md`
- `HISTORY_EVIDENCE_TRUST_VISUAL_REFERENCES.md`
- `MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUAL_REFERENCES.md`
- `PROFILE_COLLABORATION_VISUAL_REFERENCES.md`
- `COMMUNITY_VISUAL_REFERENCES.md`

Approved review/evidence records exist for the above controlled visual families, including Community:
- `KAVRIVA_COMMUNITY_VISUALS_01_HANDOFF.md`
- `KAVRIVA_COMMUNITY_VISUALS_REVIEW.md`

Partial FAM-01 review record:
- `KAVRIVA_FIRST_USE_VISUALS_01_REVIEW.md` — `PASS_PARTIAL / USER-ACCEPTED PARTIAL SET`
  - accepted working visual directions: `SCR-001`, `SCR-002`, `SCR-003`
  - still pending: `SCR-004`
  - no full FAM-01 reference authority yet

`REFERENCE_INDEX.md` approved references currently include:
`REF-BRAND-001`, `REF-UX-001`, `REF-VISUAL-001`, `REF-ARCH-001`, `REF-NAV-001`, `REF-SPEC-001`, `REF-AIUSTA-001`, `REF-SHELL-001`, `REF-GUIDE-001`, `REF-ACTIVE-001`, `REF-DIAG-001`, `REF-MAINT-001`, `REF-HISTORY-001`, `REF-LIFECYCLE-001`, `REF-PROFILE-001`, `REF-COMMUNITY-001`.

## Current Phase-3 Task State

The earlier user-comments pause has been processed.

The user accepted the current FAM-01 working visual directions for:
- `SCR-001` First-Value Entry
- `SCR-002` Add Motorcycle
- `SCR-003` Motorcycle Identification & Variant Resolution

Two Community-family screens shown in the same screenshot batch were explicitly excluded from FAM-01 processing and do not count toward First Use coverage.

Remaining consumer-mobile visual coverage:
- `SCR-004` Fit Confirmation / Missing Distinction

`SCR-005 Garaj` is already covered by R01.

Current remaining Phase-3 sequence:
1. complete `SCR-004` visual coverage,
2. Internal Data & Content Operations requirements/workflow/platform-independent screen-workspace architecture,
3. Gate 3 -> 4 readiness review.

Phase 4'e Gate 3 saglanmadan gecilmez.

Bu tablo her gate gecisinde veya review-state degisiminde guncellenir.
