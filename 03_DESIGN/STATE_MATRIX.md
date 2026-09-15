# STATE MATRIX

Status: APPROVED
Approved by: USER — 2026-09-15
Review source: `03_DESIGN/SCREEN_INVENTORY_REVIEW.md`

Bu matris critical product states'i screen contexts'e baglar. Presentation mode kolonlari implementation karari degil, screen-spec asamasi icin aday treatment'tir.

| State | Relevant screens/contexts | Required behavior | Presentation candidate |
|---|---|---|---|
| Loading | Most data/content screens | Completion/verification loading sirasinda inferred edilmez | Inline/skeleton |
| Empty | 022,025,030,034,038 | Absence meaning + relevant next action | Inline/full empty state |
| Error | Transactional/review flows | Context preserved; failed action success sayilmaz | Inline or blocking by consequence |
| Offline | 010,013-018,022-030,038 | History/teaching may remain; critical application freshness may close | Persistent contextual state |
| Permission denied/revoked | 003,012,015,019,020,027,028,035,038 | Missing evidence capability explained; certainty fabricated edilmez | Inline + platform handoff |
| Inactive motorcycle | 005,008,022,025-034,037 | Appropriate new activity gated; trust/history/safety preserved | Context status + gate |
| Entitlement gate | 009,010,027,034,037 | Gate only genuinely new capacity/activity | Sheet/full-screen/state family candidate |
| Historical access preserved | 025,026,028-030,034,037 | Read/search/export/provenance/correction/dispute remain | Normal enabled state |
| Safety hold | 004,011-017,019-021,029 | Physical progression stops; reason and re-entry shown | Strong inline/blocking state |
| Teaching-only | 004,010,012,013,017 | Non-application authority explicit | Full content state |
| Variant mismatch / uncertain fit | 003,004,010,011,014,015 | Nearby variant never guessed as correct | Blocking + re-evidence |
| Missing readiness prerequisite | 011,012,014 | Condition/reason/remediation/recheck visible | Hold flow candidate |
| Evidence insufficient | 003,004,020,021,028,036,038 | Uncertainty preserved; no false verification | Inline/result state |
| Diagnosis unresolved | 021 | `Neden dogrulanamadi` valid outcome | Full result state |
| Disputed history / claim | 025,026,028 | Claims/source/evidence separated | Record-detail state |
| Evidence withdrawal / re-review | 026,028,029,036 | Withdrawn evidence removed from current evaluation; historical trace remains | Detail + status transition |
| Critical correction | 005,014,016,026,029 | Reach-back proportional to impact; active work may stop | Dedicated action context |
| Interrupted work | 005,014,016 | Context preserved; unsaved step not assumed complete | Resume entry |
| Resume revalidation | 016 | Current physical/safety state rechecked | Dedicated flow |
| Material guide change | 016,017,029 | Old continuation stops; current state remapped | Dedicated flow |
| Recovery | 015,017,018,021 | Safe state/evidence prioritized; normal flow stays stopped until valid re-entry | Dedicated/contextual |
| Completed / success | 018,027 | Only after required result confirmation; no guarantee semantics | Completion state |
| Partial / unresolved | 018,021,027,028 | Preserved as partial/unresolved; never coerced to completed | Explicit outcome state |
| Profile migration conflict | 007 | Source/date/difference shown; no silent winner | Conflict-review flow |
| Migration rollback/failure | 007 | Local data remains usable; partial profile state != success | Recovery state |
| Collaboration revoke | 034 | Future access stops as applicable; prior attribution remains | Context state / confirmation flow |
| Archive warning/state | 031 | Removed from active garage, history preserved, reversible | Lifecycle state |
| Transfer warning/state | 031,032 | Selected/incomplete coverage + private exclusions visible | Dedicated flow |
| Delete warning/state | 031,033 | Scope/irreversibility/independent-data boundary before destructive action | Blocking confirmation flow |
| Stale critical content | 010,011,013,014,016,017 | Teaching/reference can remain; current application closes until recheck | Safety hold |
| Guide invalidated/withdrawn | 010,017,029,037 | Historical use/reach-back stays; replacement-selection semantics remain proposal-bound | Contextual state |
| Entitlement change during physical work | 014-018,037 | Guidance needed for safe completion/stop/recovery remains accessible | Ordinary gate suppressed until safe closure |
| Downgrade | 008,025-030,034,037 | Trust/history preserved; only future paid capacity/activity gated | Context status |
| Critical reminder catch-up | 024,029 | Safety > routine overdue; avoid notification flood | Prioritized summary |
| Community content accepted | 036,038 | Published content remains clearly community content, not official numbered guide | Community status/detail |
| Community content unverified | 035,036,038 | Unverified personal experience explicitly separated from verified/official guidance | Label + provenance detail |
| Community content withdrawn/held | 036,038,029 where downstream impact exists | Public visibility changes; downstream evidence dependency may trigger re-review/reach-back | Status + re-review path |

## Cross-State Invariants

1. **Gate action, not truth:** entitlement/inactive/downgrade cannot disable historical truth, provenance, correction, safety reach-back or safe started-work closure.
2. **Teaching != application:** readable reference may coexist with closed motorcycle-facing application.
3. **Saved UI != physical proof:** interruption/resume requires current-state revalidation where consequence demands it.
4. **Uncertainty is valid:** insufficient evidence, disputed, unresolved and teaching-only are legitimate states.
5. **No silent overwrite:** correction, transfer, evidence withdrawal, migration conflict and dispute keep provenance/history.
6. **Safety can promote itself:** U04 progressive disclosure never hides critical step-specific safety when it must be visible.
7. **Community != official:** community content cannot visually or semantically become official numbered guide instructions.

## Placement Gaps for Screen-Spec Phase

Still open:
- exact screen vs sheet/inline treatment,
- routine notification mute/snooze global vs contextual placement,
- accessibility modality preference placement,
- language/unit preference placement if user-configurable,
- exact historical claim-state vocabulary/iconography,
- exact correction reach-back channels/cadence.

## Approval Boundary

This matrix is APPROVED as the **working Phase-3 critical-state architecture**.

Presentation treatment, exact component choice and technical state implementation remain open.