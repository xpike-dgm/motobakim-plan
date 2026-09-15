# NAVIGATION MAP

Status: APPROVED
Approved by: USER — 2026-09-15
Architecture decision: DEC-0016
Global shell decision: DEC-0017

Bu belge **product transition map**'tir. Technical router/route-name implementation karari degildir.

Approved global shell: `GLOBAL_NAVIGATION.md`.

## Approved Global Entry Responsibilities

Bottom bar:
- **Garaj** -> motorcycle context / switching / lifecycle (`SCR-005`, `SCR-008`, `SCR-031` related)
- **Bakim** -> maintenance plan/reminder/catch-up (`SCR-022` — `SCR-024`)
- **AI Usta** -> known-task (`SCR-009`) + symptom-first (`SCR-019`) primary assistance entry
- **Gecmis** -> history/evidence/trust (`SCR-025` — `SCR-030`)
- **Topluluk** -> community experiences/contribution/moderation (`SCR-038`, `SCR-035`, `SCR-036`)

`AI Usta` bir UX entry label'idir; technical/AI architecture karari degildir.

## N-01 — First Use / Progressive Onboarding

`SCR-001 First-Value Entry`
→ `SCR-002 Add Motorcycle`
→ `SCR-003 Identification / Variant Resolution`
→ `SCR-004 Fit Confirmation / Missing Distinction`
→ usable motorcycle context / global shell.

Account/profile otomatik olarak bu zincirin onune konmaz.

Durable-value trigger olusursa:
`current context`
→ `SCR-006 Profile / Persistence Transition`
→ `SCR-007 Migration Scope & Conflict Review`
→ origin context.

Cancel/failure usable local state'i korur.

First post-onboarding selected tab henuz final degildir.

## N-02 — Known Task via AI Usta

`AI Usta`
→ `SCR-009 Known Task Find / Select`
→ `SCR-010 Guide Scope / Fit / Selection Preview`
→ `SCR-011 Preparation & Readiness`.

Branches:
- application-ready → `SCR-014 Active Guide Step`
- missing prerequisite → `SCR-012 Readiness Hold`
- learning valid, application unavailable → `SCR-013 Teaching-Only`
- genuinely new activity entitlement gate → `SCR-037`.

Normal execution:
`SCR-014` → next `SCR-014` → `SCR-018 Completion / Safe Closure / Record`.

Exception:
`SCR-014` → `SCR-015 Problem / Mismatch / Recovery`.

## N-03 — Symptom-First Diagnosis via AI Usta

`AI Usta`
→ `SCR-019 Symptom Capture`
→ `SCR-020 Diagnosis Checks`
→ `SCR-021 Diagnosis Outcome / Handoff`.

Supported repair:
`SCR-021` → `SCR-010`.

Unresolved diagnosis valid result state'tir; invented repair path yok.

## N-04 — Readiness / Teaching / Application Separation

`SCR-011` → missing critical condition → `SCR-012`.

From `SCR-012`:
- remediation/equipment/new evidence → recheck,
- verified → `SCR-011` veya `SCR-014`,
- application still unavailable → `SCR-013`,
- professional support optional olabilir.

Professional help != mandatory safety closure.

## N-05 — Problem / Mismatch / Recovery

`SCR-014` → mismatch/problem → `SCR-015`.

No `ignore and continue` transition exists.

Valid outcomes:
- state reliably re-established → controlled re-entry,
- safe stop/partial closure → `SCR-018`,
- unresolved → stopped / handoff/support context.

## N-06 — Interrupted Work / Resume

`SCR-014` context preserved → later return → `SCR-016 Resume Revalidation`.

Then:
- current state verified → `SCR-014`,
- drift/mismatch → `SCR-015`,
- material guide change → `SCR-017`.

Saved UI progress current physical proof degildir.

## N-07 — Material Guide Change

`SCR-014` veya `SCR-016`
→ old progression stops
→ `SCR-017 Material Guide Change / Physical-State Remap`.

Outcomes:
- safe mapping → `SCR-014`,
- recovery → `SCR-015`,
- only safe closure → `SCR-018`,
- unresolved mapping → application closed; teaching/state capture may continue.

No automatic reversal of previous physical work.

## N-08 — Maintenance / Reminder / Catch-Up via Bakim

`Bakim`
→ `SCR-022 Maintenance Plan`
→ `SCR-023 Maintenance Item / Reminder Detail`.

Actions:
- perform task → `AI Usta` / `SCR-009`,
- record existing/external work → `SCR-027`,
- routine postpone → `SCR-022`.

Long absence / multiple issues:
entry → `SCR-024 Catch-Up & Critical Priorities`
→ `SCR-029` or `SCR-023` or `SCR-025`.

## N-09 — History / Evidence / Dispute via Gecmis

`Gecmis`
→ `SCR-025 History`
→ `SCR-026 Historical Record & Provenance`.

From detail:
- correction/dispute/new evidence → `SCR-028`,
- critical later correction → `SCR-029`,
- export → `SCR-030`.

Evidence withdrawal trust-maintenance event'tir; silent historical deletion degildir.

## N-10 — Self / Hobby / Service Work Record

`Garaj`, `Bakim`, `Gecmis` veya relevant context
→ `SCR-027 Record Work`
→ `SCR-026 Historical Record`.

Conflicting service document vs owner evidence:
`SCR-026` → `SCR-028`.

Unresolved completion maintenance'i verified completion gibi reset etmez.

## N-11 — Active / Inactive Motorcycle via Garaj

`Garaj` / contextual motorcycle control
→ `SCR-008`.

Inactive motorcycle preserves:
- `SCR-025 History`,
- `SCR-026 Provenance`,
- `SCR-028 Correction/Dispute`,
- `SCR-029 Safety Reach-Back`,
- `SCR-030 Export`.

Unrelated new activity may enter `SCR-037`.

Reactivation:
`SCR-008` → current km/use/context re-evaluation → usable Garaj context.

Interrupted physical work requires `SCR-016`.

## N-12 — Motorcycle Lifecycle / Transfer / Delete via Garaj

`Garaj` / `SCR-008`
→ `SCR-031 Motorcycle Lifecycle`.

Branches:
- archive → inactive/archive state, history preserved,
- reactivate → context re-evaluation,
- transfer/sale → `SCR-032 Transfer Scope & Coverage`,
- actual delete → `SCR-033 Delete Scope & Warning`.

Transfer != delete. Archive != delete. Partial transfer != complete history.

## N-13 — Collaboration

Garaj/profile-relevant context
→ `SCR-034 Collaboration & Permissions`.

Participant activity can lead to:
- `SCR-027` work record,
- `SCR-028` correction/dispute,
- `SCR-026` historical record.

Revoke future access/activity'yi durdurabilir; prior attribution/history silinmez.

## N-14 — Community via Topluluk

Reading:
`Topluluk` or related context
→ `SCR-038 Community Experiences / Q&A`.

From `SCR-038`:
- explicit contribution → `SCR-035`,
- report/correction → moderation/review context,
- official guide content remains separate.

Contribution:
relevant private evidence/context
→ explicit opt-in
→ `SCR-035 Community Contribution`
→ `SCR-036 Contribution Review / Moderation / Appeal`.

Withdrawal affecting downstream claims re-review tetikleyebilir; safety impact varsa `SCR-029`.

## N-15 — Critical Correction / Safety Reach-Back

Affected user → `SCR-029`.

Then:
- historical-only explanation → `SCR-026`,
- active/interrupted work → `SCR-016` or `SCR-017`,
- result recheck → `SCR-018`.

This path inactive motorcycle ve entitlement downgrade sonrasinda da korunur.

## N-16 — Offline / Stale Critical Content

Offline primarily a state'tir, standalone route degildir.

Downloaded teaching/history may remain usable.

Application-critical stale content:
`SCR-010/011/014/016`
→ freshness hold
→ reference/teaching may use `SCR-013`.

After current-version recheck:
- materially unchanged → normal flow,
- materially changed → `SCR-017`.

## N-17 — Export / Delete / Migration

Export:
`Gecmis` / relevant profile context → `SCR-030`.

Delete:
`Garaj` → `SCR-031` → `SCR-033`.

Local/profile transition:
`SCR-006` → `SCR-007`.

Migration cancel/failure usable local state'e doner; partial profile false-success degildir.

## N-18 — New-Activity Entitlement Gate

`new activity` → `SCR-037` when entitlement applies.

Preserved exits where relevant:
- Gecmis / `SCR-025`,
- provenance / `SCR-026`,
- correction/dispute / `SCR-028`,
- safety reach-back / `SCR-029`,
- started-work revalidation/safe closure / `SCR-016` / `SCR-018`.

No entitlement transition historical truth'u silemez veya physically started job'i terk edemez.

## N-19 — Global Bottom Bar Behavior

Approved global shell:
**Garaj · Bakim · AI Usta · Gecmis · Topluluk**.

Controlled architecture refinement:
- `SCR-005` tum capabilities'i ayni anda gosteren broad hub olarak kullanilmaz; Garaj/motorcycle context responsibility'sine daralir.
- Known-task + symptom primary entry AI Usta'dadir.
- Maintenance primary entry Bakim'dadir.
- History primary entry Gecmis'tedir.
- Community primary entry Topluluk'tadir.

This distribution preserves all approved contexts while reducing dashboard/card-stack pressure.

### Still open

- active physical-work flows sirasinda bottom-bar'in exact visibility/interaction treatment'i,
- first post-onboarding landing tab,
- platform-specific navigation behavior.

## Approval Boundary

This map and five-tab responsibility split are APPROVED working Phase-3 navigation truth.

Approval does NOT lock technical routing, exact animation/component treatment or active-repair shell behavior.
