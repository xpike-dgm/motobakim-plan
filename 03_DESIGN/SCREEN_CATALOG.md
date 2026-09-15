# SCREEN CATALOG

Status: APPROVED
Approved by: USER — 2026-09-15
Review source: `03_DESIGN/SCREEN_INVENTORY_REVIEW.md`
Navigation refinement: DEC-0017 / `GLOBAL_NAVIGATION.md`
Phase: Phase 3 — Design

Bu katalog **product interaction context** envanteridir. `SCR-*` sayisi permanent route sayisi degildir. Full-screen / sheet / modal / inline-state karari source truth karar vermedigi yerde acik tutulur.

## Authority Boundary

- Product behavior: `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`
- Brand: `BRAND_NAME.md`
- Logo direction: `LOGO_DIRECTION.md` / `REF-BRAND-001`
- Anchor UX: `ANCHOR_UX_STRUCTURE.md` / `REF-UX-001`
- Anchor visual direction: `ANCHOR_VISUAL_STYLE.md` / `REF-VISUAL-001`
- Global navigation: `GLOBAL_NAVIGATION.md`
- Working screen specs: `SCREEN_FAMILY_SPECS.md`

U04/V10 yalniz ilgili baglami bilgilendirir; tum ekranlara universal layout olarak kopyalanmaz.

## Approved Working Catalog

| ID | Name | Surface candidate | Primary purpose | Main entries / exits | Critical product rules / states | Reference status |
|---|---|---|---|---|---|---|
| `SCR-001` | First-Value Entry | Full screen | Account/permission zorlamadan known-task, symptom-first veya record-first degeri gostermek | Fresh launch -> 002 veya intent branch | First value before profile; local-only possible | APPROVED working context |
| `SCR-002` | Add Motorcycle | Full screen | Ilk/yeni motorcycle context kurmak | 001, 008 -> 003 | Motorcycle contexts isolated | APPROVED working context |
| `SCR-003` | Motorcycle Identification & Variant Resolution | Full screen | Observable evidence ile task-relevant configuration ayirmak | 002 / fit challenge -> 004 | No technical-ID scavenger hunt; uncertain fit remains uncertain | APPROVED working context |
| `SCR-004` | Fit Confirmation / Missing Distinction | Screen/sheet candidate | Known/unknown fit ve application eligibility'yi aciklamak | 003,010 -> usable context / 003 / 013 | Unresolved fit cannot open variant-specific application | APPROVED working context |
| `SCR-005` | Garage / Motorcycle Context | Full screen/root candidate | Selected motorcycle context, identity, switching/lifecycle entry; global tabs other primary domains'i dagitir | 004 / return -> 008,031 or global bottom-bar domains | No dashboard inflation; critical reach-back cannot be buried; five-tab shell avoids broad card hub | APPROVED working context — refined DEC-0017 |
| `SCR-006` | Profile / Persistence Transition | Screen/sheet candidate | Local/account-light user'a profile/persistence nedenini ve data etkisini gostermek | Durable record / cross-device / collaboration -> 007 | Profile not forced before first value | APPROVED working context |
| `SCR-007` | Migration Scope & Conflict Review | Full screen | Local-to-profile scope, duplicate/conflict, partial/failure review | 006 -> prior context | No silent loss/overwrite; partial != success | APPROVED working context |
| `SCR-008` | Motorcycle Switch / Active-Inactive Management | Screen/sheet candidate | Active/inactive motorcycle lifecycle ve switching | Garaj/context affordance -> 005/025/031/037 | Inactive != deleted/locked; history/safety remain | APPROVED working context |
| `SCR-009` | Known Task Find / Select | Full screen | User'in yapmak istedigi operation'i bulmak | AI Usta -> 010 | Selection alone does not imply fit | APPROVED working context |
| `SCR-010` | Guide Scope / Fit / Selection Preview | Full screen | Scope, fit, trust/freshness, eligibility ve selection implication | 009/021 -> 011/013/003/037 | Verified != guarantee; fit before application | APPROVED working context |
| `SCR-011` | Preparation & Readiness | Full screen | Tools/parts/risks/prerequisites/readiness'i physical intervention oncesi gostermek | 010 -> 012 or 014 | Missing mandatory condition before teardown | APPROVED working context |
| `SCR-012` | Readiness Hold / Remediation / Recheck | Screen/sheet candidate | Block reason + remediation + evidence-based re-entry | 011/014 -> 011/013/014 | Self-assertion cannot bypass critical gate | APPROVED working context |
| `SCR-013` | Teaching-Only Topic View | Full screen | Application unavailable olsa da learning/reference'i korumak | 004/010/012/stale -> resolve or back | Teaching must not masquerade as application | APPROVED working context |
| `SCR-014` | Active Guide Step | Full screen | Tek physical step'i task-first hierarchy ile uygulatmak | 011/012/016/017 -> next 014 / 015 / 018 | U04 authoritative; safety visible; recovery visible secondary | `REF-UX-001`, `REF-VISUAL-001` anchor family |
| `SCR-015` | Problem / Mismatch / Recovery | Screen/sheet candidate | Unexpected state'te normal progression'i durdurup safe recovery kurmak | `Sorun var` / mismatch -> 014 only after revalidation / 018 | Never ignore-and-continue | APPROVED working context |
| `SCR-016` | Resume Revalidation | Full screen | Interrupted work'te current physical/safety state'i yeniden establish etmek | Interrupted return/reactivation -> 014/015/017 | Saved confirmation != current proof | APPROVED working context |
| `SCR-017` | Material Guide Change / Physical-State Remap | Full screen | Guide change ile current physical state'i safe path'e remap etmek | 016/029 -> 014/015/018 | No guessed continuation or automatic reversal | APPROVED working context |
| `SCR-018` | Completion / Safe Closure / Record | Full screen | Guided work sonunda verified completion vs partial/unresolved/safe closure ayrimi | 014/015/017 -> history/maintenance/context | Unverified/partial cannot become completed; safe closure cannot be paywalled | APPROVED working context |
| `SCR-019` | Symptom Capture | Full screen | Daily-language symptom capture + immediate danger triage | AI Usta -> 020 | Danger before diagnostic convenience | APPROVED working context |
| `SCR-020` | Diagnosis Checks | Full screen | Differentiating evidence toplamak | 019 -> 020/021 | Evidence narrows possibilities; no random replacement | APPROVED working context |
| `SCR-021` | Diagnosis Outcome / Handoff | Full screen | Supported conclusion veya explicit unresolved outcome | 020 -> 010 / return | `Neden dogrulanamadi` valid outcome | APPROVED working context |
| `SCR-022` | Maintenance Plan | Full screen | Due/upcoming/uncertain maintenance'i source-derived planla gostermek | Bakim / 024 -> 023/027 | No invented intervals; motorcycle scoped | APPROVED working context |
| `SCR-023` | Maintenance Item / Reminder Detail | Screen/sheet candidate | Interval source, due reasoning, uncertainty ve actions | 022/notification -> 009/027/026 | Postpone != completion; critical vs routine distinct | APPROVED working context |
| `SCR-024` | Catch-Up & Critical Priorities | Full screen | Long absence/multiple items'da safety-first catch-up | Re-engagement -> 029/023/025 | No notification flood; harm/urgency priority | APPROVED working context |
| `SCR-025` | History | Full screen | Longitudinal motorcycle history'yi gezmek/search etmek | Gecmis / inactive -> 026/027/030 | Historical access survives downgrade/inactive | APPROVED working context |
| `SCR-026` | Historical Record & Provenance | Full screen | Current claim state + event history + evidence/provenance | 025/029 -> 028/029 | Current state separate from event history; high-risk provenance explicit | APPROVED working context |
| `SCR-027` | Record Work — Self / Hobby / External Service | Full screen | Standalone/external work record etmek | Garaj/Bakim/Gecmis/relevant context -> 026/022 | Actor role does not create verification; partial allowed | APPROVED working context |
| `SCR-028` | Correction / Dispute / Evidence Review | Screen/modal-flow candidate | Competing claims/evidence/correction review without overwrite | 026/transfer/service conflict -> 026 | No silent winner; withdrawal/re-review supported | APPROVED working context |
| `SCR-029` | Critical Correction / Safety Reach-Back | Full screen | Later correction'in affected prior work impact'ini ve required action'i gostermek | Notification/026/active repair -> 016/017/026/018 | Survives inactive/entitlement; severity by impact | APPROVED working context |
| `SCR-030` | Data Export | Screen/sheet candidate | User/history data export scope + provenance | Gecmis/profile/lifecycle -> return | Export not premium; corrections/provenance included | APPROVED working context |
| `SCR-031` | Motorcycle Lifecycle | Full screen | Archive/reactivate/transfer/delete semantics'i ayirmak | Garaj/008 -> 008/032/033 | Archive != delete; transfer != delete | APPROVED working context |
| `SCR-032` | Transfer Scope & Coverage | Full screen | Selected transfer records, coverage/gaps/private exclusions | 031 -> lifecycle/history | Partial transfer must be marked incomplete | APPROVED working context |
| `SCR-033` | Delete Scope & Warning | Screen/confirmation-flow candidate | Destructive delete scope/irreversibility/independent-data boundary | 031 -> lifecycle | Scope before destructive action | APPROVED working context |
| `SCR-034` | Collaboration & Permissions | Full screen | Invite/manage/revoke limited collaboration with attribution | Motorcycle/profile context -> history/records | Revoke future access, not past attribution; exact role matrix open | APPROVED working context |
| `SCR-035` | Community Contribution | Full screen | Private content'ten explicit community contribution yapmak | Topluluk/evidence/detail/recovery contexts -> 036 | Opt-in; official guidance separate | APPROVED working context |
| `SCR-036` | Contribution Review / Moderation / Appeal | Screen/modal-flow candidate | Review status/rejection/correction/resubmit/appeal/withdraw | 035/moderation event -> 035/return | Reason + repair path; withdrawal dependencies preserved | APPROVED working context |
| `SCR-037` | New-Activity Entitlement Gate / Preserved Access | Screen/sheet/state-family candidate | Yalniz new activity/capacity'yi gate edip existing trust/safety access'i korumak | Task/new guide/inactive/advanced collab -> preserved exits | History/provenance/correction/safety/started-work recovery cannot be locked | APPROVED working context |
| `SCR-038` | Community Experiences / Q&A | Full screen / contextual-area / list+detail-family candidate | Published community experiences/questions'i official guide'dan ayri okumak | Topluluk / related context -> 035/036/report/back | Source/motorcycle/review status/date; unverified experience != official/verified step | APPROVED working context — main-manager refinement |

## Important Distinctions

### SCR-018 vs SCR-027
- `SCR-018`: guided physical-work outcome boundary before history mutation.
- `SCR-027`: standalone/external/hobby/service work record capture.

### SCR-037
Candidate gate surface/state family'dir; guaranteed permanent route degildir.

### SCR-005 after DEC-0017
Garaj selected-motorcycle context responsibility'sini tasir. Task/symptom, maintenance, history ve community primary entry'leri global bottom-bar ile dagitilmistir. Bu controlled refinement approved capability'leri silmez.

## Open Design Mapping

Still open:
- routine notification mute/snooze exact placement,
- language/unit preference exact exposure if configurable — profile prerequisite olamaz,
- accessibility modality exact placement — profile prerequisite olamaz,
- exact full-screen vs sheet/inline treatment for ambiguous candidates,
- active physical work sirasinda bottom-bar visibility/interaction,
- first post-onboarding landing tab.

Generic Settings screen convention ile uydurulmaz.

## Approval Boundary

This catalog is APPROVED working Phase-3 screen architecture as refined by DEC-0017.

It does NOT lock route count, exact surface type, final visual components, technology or implementation.
