# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / MOTORCYCLE LIFECYCLE + ENTITLEMENT VISUALS 01

Status: USER ACCEPTED WORKING VISUAL SET  
Date: 2026-09-17  
Family: FAM-07 — Motorcycle Lifecycle / Entitlement  
Scope: SCR-008, SCR-031, SCR-032, SCR-033, SCR-037  
Repository source snapshot: `6117faea347e624b8d4862f0e28da0869dc45cd6`

## A. Source check

The repository was read as source-of-truth without writing to it. The required control, design and approved-discovery sources were reviewed, including:

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/DECISION_LOG.md`
- `00_CONTROL/OPEN_QUESTIONS.md`
- `00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`
- `03_DESIGN/README.md`
- `03_DESIGN/BRAND_NAME.md`
- `03_DESIGN/LOGO_DIRECTION.md`
- `03_DESIGN/ANCHOR_VISUAL_STYLE.md`
- `03_DESIGN/REFERENCE_INDEX.md`
- `03_DESIGN/SCREEN_CATALOG.md`
- `03_DESIGN/STATE_MATRIX.md`
- `03_DESIGN/DESIGN_PRINCIPLES.md`
- `03_DESIGN/GLOBAL_NAVIGATION.md`
- `03_DESIGN/SCREEN_FAMILY_SPECS.md`
- `03_DESIGN/MAIN_SHELL_VISUAL_REFERENCES.md`
- `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`
- `03_DESIGN/HISTORY_EVIDENCE_TRUST_VISUAL_REFERENCES.md`
- `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`
- `02_DISCOVERY/SYNTHESIS/BUSINESS_RULES.md`
- Relevant Batch-08 lifecycle/entitlement refinement: `02_DISCOVERY/SYNTHESIS/BATCH_08_DELTA.md`

Source result:

- Current phase remains Phase 3 Design.
- FAM-07 was the authorized current mobile visual family.
- Gate 3 -> 4 has not passed.
- No technology, backend, auth, sync, billing, exact price, tier or quota decision was introduced.
- No repository source file was changed.

## B. Attached reference check

All five required working references were present and used:

| Reference | Size | Current local SHA-256 |
|---|---:|---|
| `Kavriva_L05A.png` | 1448x1086 | `0dcbcd704014a0cec8a6f40a9fe6917ffe954ca4123e3b1a723aed8c222ea98d` |
| `Kavriva_V10_Signature-Kavriva.png` | 887x1774 | `9f2010a9cdab7ab85a00de89931867b34818fe3af350c702ceff8cbe2aebbd6d` |
| `R01-Garaj.png` | 887x1774 | `63a9e9bc0be734f40386bd375e7ae22f8f23a18901b4b1d216befbc7703fd90c` |
| `I05-SCR-029-Critical-Correction-Safety-Reach-Back.png` | 887x1774 | `fe103d2c58b2e627d301ffccdc844f714c167e47ba2d7f7f9e10afe1e9ed91f3` |
| `I06-SCR-030-Data-Export.png` | 887x1774 | `bf50ba4f2c3c27a89331fc3f05cfcec2b116d9c285174104455dd00e88cb0b92` |

The task used the current user-supplied binaries. Some current local binary hashes may differ from historical provenance hashes recorded in repository documents; this handoff records the actual files used in this accepted generation session.

## C. User feedback verbatim

> J05 de tasarımdan çok yazı var özellikle ekranın ilk 1/3 ü

> son tasarımı beğendim fakat birbirine sıkıştırmaadan tasarlarmısın en alt boş kalmış

> bu iyi handoff hazırla ve bu kabul edilen görselleri masaüstünde "yeni klasör" e kopyala , içindekilere elleme ve png isimlerini düzgün yaz

Resolution:

- J01–J04 received no requested change and remain the accepted generated candidates.
- J05 was refined twice.
- Accepted J05 is v3: reduced upper copy, preserved-access content retained, vertical rhythm redistributed, and bottom action area balanced.

## D. Accepted/refined J01–J05 set

| ID | Screen | Accepted file | Size | SHA-256 |
|---|---|---|---:|---|
| J01 | SCR-008 Motorcycle Switch / Active-Inactive Management | `J01-SCR-008-Motorcycle-Switch-Active-Inactive-Management.png` | 887x1774 | `56f3165940cbacef017012abe8fc819da21985b1333e48e733c6115a9875777e` |
| J02 | SCR-031 Motorcycle Lifecycle | `J02-SCR-031-Motorcycle-Lifecycle.png` | 887x1774 | `0f9a6f84ceae12882299e067260f7d26299d8621b8fcd439401556954924de57` |
| J03 | SCR-032 Transfer Scope & Coverage | `J03-SCR-032-Transfer-Scope-Coverage.png` | 887x1774 | `4af59472b5f338d3ec55e7dfaf88f913dee810594635e352ca3fb9727fecf86d` |
| J04 | SCR-033 Delete Scope & Warning | `J04-SCR-033-Delete-Scope-Warning.png` | 887x1774 | `721b87d9062d24158b7a0db4aeffa4e5d7b919bb251681116a9b05bbbbb8c684` |
| J05 | SCR-037 New-Activity Entitlement Gate / Preserved Access | `J05-SCR-037-New-Activity-Entitlement-Gate-Preserved-Access.png` — accepted v3 binary | 887x1774 | `3181ca7daa06a8531aefebf6f9dbe13afa9e1c2b02173ad4f76ab88955b0222e` |

## E. Active/inactive switching behavior

- Exactly one motorcycle is visually active in J01.
- Switching is explicit through selection plus the dominant `Aktif motosiklet yap` action.
- The inactive motorcycle remains readable and selectable.
- Inactive status pauses routine reminders where applicable but does not imply deletion.
- History, evidence, corrections and export remain visibly available.
- Critical safety corrections remain reachable for inactive motorcycles.
- No motorcycle-count limit, price or quota is shown.
- Reactivation must restore the same historical/evidence context; current mileage/use may require reminder recalculation.
- Interrupted physical work must not resume from old confirmations without current-state revalidation.

## F. Lifecycle action semantics

J02 preserves three distinct meanings:

- `Etkin değil yap`: non-destructive; removes from active garage while preserving history/evidence/corrections.
- `Geçmişi aktar`: opens a scoped transfer review; it is not deletion or automatic verification.
- `Motosikleti sil`: separated as a permanent/destructive action and limited to the applicable user-owned scope.

Archive/inactive, transfer and delete are not merged into a generic remove action. The screen uses one dominant review CTA instead of equal-weight competing actions.

## G. Transfer scope/coverage behavior

J03 establishes:

- `Kısmi geçmiş` is visible before confirmation.
- Included maintenance/work records, evidence/source context, corrections/disputes and attribution trail are named.
- Unselected periods and private/sensitive content exclusions are explicit.
- Transfer target remains generic; no identity was invented.
- Transfer does not convert records into verified records.
- Source, current state and provenance remain traceable.
- Partial coverage must never be presented as complete motorcycle history.

## H. Delete scope/boundary behavior

J04 establishes:

- Destructive meaning is clear but calm; red is restrained to the destructive context.
- User-visible affected categories are listed before confirmation.
- `Etkin değil yap` remains available as the history-preserving alternative.
- Other actors' independent evidence, transferred copies and historical attribution are not automatically deleted.
- Irreversibility requires explicit acknowledgement.
- One final destructive CTA exists; no countdown, fear wall or unrelated wipe language is used.

## I. Entitlement + preserved-access behavior

Accepted J05 v3 establishes:

- The blocked item is a new routine maintenance activity for an inactive motorcycle.
- The upper message is intentionally concise: `Yeni bakım kapalı` plus `Yalnızca yeni işlem etkilenir`.
- Existing history/records, evidence/source, correction/dispute, export and critical safety/recovery remain enabled.
- `Garaja dön` is the dominant safe return action.
- `Erişim seçeneklerini gör` is secondary and contains no price, tier, quota or marketing treatment.
- Already-started physical work retains safe completion, safe stop and recovery guidance.
- The gate is a contextual state, not a permanent paywall route.

## J. History/trust/safety continuity QA

| QA item | Result |
|---|---|
| Inactive motorcycle is distinct from deleted/locked | PASS |
| Inactive history/evidence/export/correction remains visible | PASS |
| Critical safety reach-back remains available | PASS |
| Archive, transfer and delete are semantically distinct | PASS |
| Transfer avoids complete/verified-history implication | PASS |
| Delete respects independent/shared-data boundaries | PASS |
| Entitlement gates only relevant new activity | PASS |
| Started-work safe closure/recovery remains available | PASS |
| Exact price/tier/quota was invented | PASS — none introduced |

## K. Clutter QA

- One primary job per screen.
- No garage analytics dashboard.
- No settings megascreen.
- No pricing cards or comparison grid.
- No five equal-weight actions.
- Transfer/delete scope uses grouped lists without nested-card proliferation.
- J05 upper-third repetition was removed after feedback.
- J05 v3 uses the full screen height with improved spacing rather than compressing content at the top or leaving a large unused bottom area.

## L. Accessibility notes

- Status and consequence use text plus iconography; color is not the only signal.
- Primary, secondary and destructive actions have explicit labels.
- List rows and buttons are drawn as mobile-sized touch targets.
- Amber caution, red destructive action and blue primary action retain distinct meanings.
- Inactive/protected access is not shown with disabled opacity.
- Production validation is still required for Dynamic Type, screen-reader order, Turkish localization expansion, contrast, focus states, reduced motion and dark mode.

## M. Navigation/surface treatment — PROPOSED ONLY

- J01 can be a Garaj-linked switching screen or sheet; exact modality remains open.
- J02–J04 are contextual lifecycle flows reached from Garaj/motorcycle context.
- J05 remains a contextual gate/state family, not a guaranteed permanent route.
- Focused screens use a back path and omit the five-tab bar in these visual fixtures.
- Bottom-bar visibility, exact modal/sheet/full-screen mappings and routing are PROPOSED ONLY.

## N. What remains non-final

- Exact production copy and localization variants.
- Final component library, icons, typography, spacing, radii and color tokens.
- Dark mode and final accessibility implementation.
- Exact archive/reactivation mechanics and reminder recalculation UI.
- Exact transfer target selection, permission model and transfer implementation.
- Exact delete retention/legal/backup behavior.
- Exact entitlement, billing, price, tier, quota or subscription structure.
- Backend, database, API, auth, sync, analytics, AI/model/provider and technical architecture.
- Gate 3 -> 4 status; it remains not passed.

## O. Recommended next critical visual family

Recommended next mobile visual family:

1. FAM-08 — Profile / Collaboration (`SCR-006`, `SCR-007`, `SCR-034`)
2. Then FAM-09 — Community (`SCR-035`, `SCR-036`, `SCR-038`)

Before Gate 3 -> 4 readiness, the already-approved Internal Data & Content Operations requirements/workflow/screen-architecture addendum also remains required. This handoff does not authorize moving to Phase 4.
