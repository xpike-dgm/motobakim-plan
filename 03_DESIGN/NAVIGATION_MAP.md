# NAVIGATION MAP

Status: REVIEW
Review source: `03_DESIGN/SCREEN_INVENTORY_REVIEW.md`

Bu belge **product transition map**'tir. Bottom-tab, drawer, router, route-name veya technical navigation implementation karari degildir.

## N-01 — First Use / Progressive Onboarding

`SCR-001 First-Value Entry`
→ `SCR-002 Add Motorcycle`
→ `SCR-003 Identification / Variant Resolution`
→ `SCR-004 Fit Confirmation / Missing Distinction`
→ `SCR-005 Motorcycle Context / Action Entry`

Account/profile otomatik olarak bu zincirin onune konmaz.

Durable-value trigger olusursa:

`current context`
→ `SCR-006 Profile / Persistence Transition`
→ `SCR-007 Migration Scope & Conflict Review`
→ origin context.

Cancel/failure usable local state'i korur.

## N-02 — Known Task

`SCR-005`
→ `SCR-009 Known Task Find / Select`
→ `SCR-010 Guide Scope / Fit / Selection Preview`
→ `SCR-011 Preparation & Readiness`

Branches:
- application-ready → `SCR-014 Active Guide Step`
- missing prerequisite → `SCR-012 Readiness Hold`
- learning valid, application unavailable → `SCR-013 Teaching-Only`
- genuinely new activity entitlement gate → `SCR-037`

Normal execution:
`SCR-014` → next `SCR-014` → `SCR-018 Completion / Safe Closure / Record`

Exception:
`SCR-014` → `SCR-015 Problem / Mismatch / Recovery`.

## N-03 — Symptom-First Diagnosis

`SCR-005`
→ `SCR-019 Symptom Capture`
→ `SCR-020 Diagnosis Checks`
→ `SCR-021 Diagnosis Outcome / Handoff`

Supported repair:
`SCR-021` → `SCR-010`.

Unresolved diagnosis remains a valid terminal/result state; no invented repair path.

## N-04 — Readiness / Teaching / Application Separation

`SCR-011` → missing critical condition → `SCR-012`.

From `SCR-012`:
- remediation/equipment/new evidence → recheck,
- verified → `SCR-011` or `SCR-014`,
- application still unavailable → `SCR-013`,
- professional support may remain optional.

Professional help != mandatory safety closure.

## N-05 — Problem / Mismatch / Recovery

`SCR-014`
→ mismatch/problem
→ `SCR-015`.

No `ignore and continue` transition exists.

Valid outcomes:
- state reliably re-established → controlled application re-entry,
- safe stop/partial closure → `SCR-018`,
- unresolved → remain stopped / handoff/support context.

## N-06 — Interrupted Work / Resume

`SCR-014` context preserved
→ later return
→ `SCR-016 Resume Revalidation`.

Then:
- current state verified → `SCR-014`,
- drift/mismatch → `SCR-015`,
- material guide change → `SCR-017`.

Saved UI progress is not current physical proof.

## N-07 — Material Guide Change

`SCR-014` or `SCR-016`
→ old progression stops
→ `SCR-017 Material Guide Change / Physical-State Remap`.

Outcomes:
- safe mapping → `SCR-014`,
- recovery → `SCR-015`,
- only safe closure → `SCR-018`,
- unresolved mapping → application remains closed; teaching/state capture may continue.

No automatic reversal of previous physical work.

## N-08 — Maintenance / Reminder / Catch-Up

Normal:
`SCR-005` → `SCR-022 Maintenance Plan` → `SCR-023 Maintenance Item / Reminder Detail`.

Actions:
- perform task → `SCR-009`,
- record existing/external work → `SCR-027`,
- routine postpone → `SCR-022`.

Long absence / multiple issues:
entry → `SCR-024 Catch-Up & Critical Priorities`
→ `SCR-029` or `SCR-023` or `SCR-025`.

## N-09 — History / Evidence / Dispute

`SCR-005`
→ `SCR-025 History`
→ `SCR-026 Historical Record & Provenance`.

From detail:
- correction/dispute/new evidence → `SCR-028`,
- critical later correction → `SCR-029`,
- export → `SCR-030`.

Evidence withdrawal is a trust-maintenance event, not silent historical deletion.

## N-10 — Self / Hobby / Service Work Record

`SCR-005`, `SCR-022`, `SCR-023` or `SCR-025`
→ `SCR-027 Record Work`
→ `SCR-026 Historical Record`.

Conflicting service document vs owner evidence:
`SCR-026` → `SCR-028`.

Unresolved completion does not reset maintenance as verified completion.

## N-11 — Active / Inactive Motorcycle

`SCR-008` manages active/inactive context.

Inactive motorcycle preserves:
- `SCR-025 History`,
- `SCR-026 Provenance`,
- `SCR-028 Correction/Dispute`,
- `SCR-029 Safety Reach-Back`,
- `SCR-030 Export`.

Unrelated new activity may enter `SCR-037`.

Reactivation:
`SCR-008` → current km/use/context re-evaluation → `SCR-005`.

Interrupted physical work still requires `SCR-016`.

## N-12 — Motorcycle Lifecycle / Transfer / Delete

`SCR-005` or `SCR-008`
→ `SCR-031 Motorcycle Lifecycle`.

Branches:
- archive → inactive/archive state, history preserved,
- reactivate → context re-evaluation,
- transfer/sale → `SCR-032 Transfer Scope & Coverage`,
- actual delete → `SCR-033 Delete Scope & Warning`.

Transfer != delete. Archive != delete. Partial transfer != complete history.

## N-13 — Collaboration

`SCR-005` or profile-relevant context
→ `SCR-034 Collaboration & Permissions`.

Participant activity can lead to:
- `SCR-027` work record,
- `SCR-028` correction/dispute,
- `SCR-026` historical record.

Revoke may stop future access/activity but does not erase prior attribution/history.

## N-14 — Community Contribution / Reading / Moderation

Reading:
`community entry or related context`
→ `SCR-038 Community Experiences / Q&A`.

From `SCR-038`:
- explicit contribution → `SCR-035`,
- report/correction path where appropriate → moderation/review context,
- official guide content remains separate.

Contribution:
`relevant private evidence/context`
→ explicit opt-in
→ `SCR-035 Community Contribution`
→ `SCR-036 Contribution Review / Moderation / Appeal`.

Outcomes:
- accepted as separate community content,
- held/rejected with reason,
- corrected/resubmitted,
- appealed,
- withdrawn.

Withdrawal affecting downstream claims may trigger re-review and `SCR-029` when safety impact warrants it.

## N-15 — Critical Correction / Safety Reach-Back

Affected user
→ `SCR-029`.

Then:
- historical-only explanation → `SCR-026`,
- active/interrupted work → `SCR-016` or `SCR-017`,
- result recheck → `SCR-018`.

This path survives inactive motorcycle and entitlement downgrade.

## N-16 — Offline / Stale Critical Content

Offline is primarily a state, not a standalone route.

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
`SCR-025` or relevant profile context → `SCR-030`.

Delete:
`SCR-031` → `SCR-033`.

Local/profile transition:
`SCR-006` → `SCR-007`.

Migration cancel/failure returns to usable local state; partial profile state is not false-success.

## N-18 — New-Activity Entitlement Gate

`new activity`
→ `SCR-037` when entitlement applies.

Preserved exits where relevant:
- history → `SCR-025`,
- provenance → `SCR-026`,
- correction/dispute → `SCR-028`,
- safety reach-back → `SCR-029`,
- started-work revalidation/safe closure → `SCR-016` / `SCR-018`.

No entitlement transition may erase historical truth or abandon a physically started job.

## Global Navigation Shell — OPEN DESIGN DECISION

This map does NOT decide:
- permanent home/dashboard,
- bottom tabs,
- tab count,
- drawer,
- persistent motorcycle switcher,
- route implementation.

Those decisions require screen-family/spec work and user review.

## Approval Boundary

Status remains `REVIEW`. Explicit user approval is required before this map becomes approved Phase-3 screen/navigation truth.
