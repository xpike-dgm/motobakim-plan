# INTERNAL DATA & CONTENT OPERATIONS — WORKFLOW / LIFECYCLE

Status: `APPROVED WORKING ADDENDUM — PHASE-3`
Date: 2026-09-17
Authority: `INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md` + approved product trust/safety rules
Scope: Platform-independent research, data/content governance, review, release, correction and recall lifecycle

## 1. Purpose and boundary

This document defines the controlled product lifecycle for internal motorcycle, technical-data and guide-content operations. It describes states, hand-offs, gates, recovery and audit expectations. It does not define a database schema, API/event protocol, CMS, application platform, analytics stack, identity provider or AI provider.

The lifecycle applies to:

- motorcycle/model/year/variant identity and applicability records,
- technical claims, measurements, prerequisites, warnings and expected outcomes,
- official guide content and its teaching/application distinction,
- source/evidence and provenance relationships,
- corrections, supersession, withdrawal, rollback and recall decisions,
- community-originated material when it is evaluated for separate community visibility or as a source that may affect dependent claims.

The words “state”, “queue”, “workspace” and “release” describe product behavior and control points. They do not prescribe a particular UI or implementation mechanism.

## 2. Lifecycle invariants

1. Research evidence is not automatically a product claim.
2. A draft is not review-approved; review approval is not publication.
3. A published version is not a guarantee of successful work or workmanship.
4. Current claim state and claim event history remain separate.
5. Conflicts, uncertainty, evidence withdrawal and incomplete coverage are valid outcomes, not errors to hide.
6. Source access, evidence visibility, current evaluation and historical provenance are separate concerns.
7. `Edit → instantly live in mobile` is forbidden for technical/safety content.
8. No transition may silently delete prior value, provenance, attribution, dispute, correction, source withdrawal or audit history.
9. A material critical change can stop or revalidate consumer application, while teaching/history/provenance access may remain available when safe.
10. Entitlement, inactive motorcycle state or role revocation can constrain new activity but cannot remove required historical trust, correction or safety reach-back.

## 3. Controlled object relationships

The lifecycle treats these as related but distinct objects:

```text
Research item
  └─> Source / evidence
        └─> Claim or content assertion
              └─> Record / guide version
                    └─> Approved release
                          └─> Mobile-consumable current state
```

An audit/decision event may be attached at every level. A source can support multiple claims; a claim can be used by multiple guide elements; a release can contain multiple approved versions. The relationship must remain inspectable so a correction or recall can calculate affected scope without guessing.

## 4. Canonical lifecycle

The default path is:

**Research → evidence collection → draft record/content → validation → conflict resolution (when needed) → human review → approval → release candidate → controlled publication → monitoring → correction / supersession / rollback / recall → re-review and republish**

Not every item visits every state. For example, an evidence withdrawal may bypass ordinary research intake and go directly to impact triage; a low-risk editorial correction may require a lighter review than a safety-critical guide change. The control points and audit obligations remain.

### 4.1 State definitions and allowed outcomes

| State | Meaning | What is allowed | What is not allowed |
|---|---|---|---|
| `Research requested` | Need, gap, correction or new scope has been identified. | Define scope, priority, owner and expected evidence. | Treating the request as technical truth. |
| `Research active` | Evidence gathering and identity/applicability work is in progress. | Add sources/evidence, resolve identity, record unknowns and dependencies. | Publishing an unreviewed result. |
| `Evidence pending` | Work cannot proceed because required evidence or source access is missing. | Add a gap reason, request evidence, keep teaching-only/reference context where safe. | Filling the gap with a guessed value or nearby variant. |
| `Draft` | A proposed record, claim or content version has been prepared. | Edit, link evidence, run validation, submit for review. | Consumer-live use or final approval by edit alone. |
| `Validation blocked` | A rule/consistency/applicability check found an unresolved issue. | Correct scope/value, add evidence, split the claim or return to research. | Suppressing the issue to pass the gate. |
| `Conflict review` | Sources or claims materially disagree or evidence is contested. | Compare claims, capture independent evidence, record decision/reason. | Silent winner, fabricated confidence or automatic resolution. |
| `In human review` | A reviewer is evaluating a bounded proposed change. | Request changes, approve bounded scope, reject or mark unresolved. | Editing the proposal without attribution or expanding scope silently. |
| `Changes requested` | Review found missing evidence, scope or content changes. | Return to draft/research with explicit reasons and required work. | Treating the prior proposal as approved. |
| `Approved` | A specific version/scope has passed the required human review. | Prepare controlled release, preserve snapshot and approval evidence. | Further unreviewed edits to the approved snapshot. |
| `Release candidate` | One or more approved versions are grouped for controlled availability. | Check dependency/impact scope, publication readiness and release status. | Mixing in draft, conflicted or recalled material without explicit status. |
| `Published` | The approved version is eligible for the shared product data source/mobile consumption. | Monitor freshness, feedback, evidence and downstream impact. | Calling it permanently correct or hiding provenance/status. |
| `Superseded` | A later accepted version replaces current use for the same scope. | Preserve historical relation and explain reason. | Deleting the prior version or rewriting historical use. |
| `Suspended / recalled` | Current use is restricted because safety, validity, applicability or trust has materially failed. | Block future application as needed, assess impact, issue correction/recheck/recovery and re-review. | Continuing to show it as current application guidance. |
| `Withdrawn` | A source/evidence/content item is no longer available or intentionally removed from current use. | Preserve provenance event, re-evaluate dependents and update visibility. | Erasing its historical use or assuming every dependent claim is invalid. |
| `Archived` | Work is no longer active but is retained for history/audit. | Read, trace, restore through a controlled new event where appropriate. | Using it as current authority without an explicit reactivation/review. |

## 5. Detailed workflow

### W-01 — Identify scope and start research

1. An operator, review finding, source change, user correction, community report or operational metric identifies a need.
2. The work item states the motorcycle/model/year/variant scope, technical/content domain, reason, consequence/risk, dependencies and desired outcome.
3. Identity and duplicate checks are performed before a new canonical scope is created.
4. The item is prioritized using explainable factors: safety/consequence, mobile demand, gap severity, stale age, conflict, dependent guide/record impact and operational urgency.
5. The item receives an owner or queue destination. Assignment does not imply technical approval.

Exit: `Research active`, or `Evidence pending` when the scope is known but required evidence cannot yet be obtained.

### W-02 — Collect and qualify evidence

1. The researcher records source identity/type, applicability, relevant date, collector/actor, access status and evidence relation.
2. Evidence is linked to a bounded claim/content assertion rather than attached as an unexplained file.
3. Nearby model/year/variant evidence is marked as non-applicable or uncertain when it cannot support the target scope.
4. Missing, stale, inaccessible, disputed and withdrawn source conditions remain explicit.
5. Generated imagery may support explanation or composition, but is not treated as identity, fit, diagnosis, maintenance or safety evidence.
6. Community contribution is labeled as community material; it does not silently enter official technical guidance.

Exit: enough evidence for a draft, or `Evidence pending` with an explicit gap/remediation path.

### W-03 — Build a draft record/content version

1. The operator proposes a new or changed motorcycle/variant record, technical claim or guide-content unit.
2. The draft shows current scope, evidence, freshness, open gaps, dependent content and intended consumer meaning.
3. Unknown, unresolved, partial, not-applicable and teaching-only outcomes are expressible.
4. The proposed diff records old/new meaning, change reason, proposer and evidence links. For a new item, “old” is an explicit absence, not an invented prior value.
5. Any guide step or warning that depends on a claim is linked for impact review.

Exit: `Draft` submitted to validation, or returned to research if identity/evidence is insufficient.

### W-04 — Validate applicability, completeness and consistency

Validation is a control point, not a truth oracle. It should surface:

- unresolved motorcycle/variant identity or fit,
- missing required evidence or provenance fields,
- stale or withdrawn sources,
- conflicting values and duplicate scopes,
- unsupported guide assertions,
- missing prerequisite/warning/outcome relationships,
- changes that affect a published or active physical-work context.

Passing validation means the proposal is reviewable. It does not mean it is correct or publishable. A blocked item returns to `Draft`, `Research active` or `Conflict review` with a reason.

### W-05 — Resolve conflicts without silent overwrite

1. The conflict view presents competing claims/sources, scope, dates, evidence and prior decisions side by side.
2. The reviewer may accept one bounded claim, retain both as disputed, mark insufficient evidence, supersede an older claim, split a variant scope or request new research.
3. The decision records what was considered, why, who decided, unresolved uncertainty and affected dependents.
4. Prior disagreement and prior decisions remain in event history even when a current state changes.
5. A conflicting service document and owner observation are not forced into a fabricated winner; an unresolved result must not be consumed as verified completion for future maintenance or guide decisions.

Exit: a bounded proposal proceeds to human review/approval, or remains `Conflict review`/`Evidence pending`.

### W-06 — Human review and approval

1. Review is assigned to an authorized reviewer appropriate to the domain and consequence.
2. The reviewer inspects scope, claim/content meaning, evidence/provenance, validation findings, previous versions, dependencies and proposed consumer impact.
3. The reviewer can approve only a bounded scope, request changes, reject, or explicitly leave unresolved.
4. High-consequence or materially changed content uses independent proposal/review/approval separation where appropriate. The exact staffing model remains a later product/strategy decision.
5. Approval records reviewer identity/role, time, evidence considered, rationale, conditions, expiry/freshness expectation and the exact version snapshot.
6. An approval cannot be silently extended to new motorcycle variants, new claims, changed procedure order or altered safety meaning.

Exit: `Approved`, `Changes requested`, `Rejected`/`Evidence pending`, or an explicit unresolved state that is not eligible for application publication.

### W-07 — Prepare and publish a controlled release

1. A release owner checks that every included item is approved, has required provenance, has no blocking conflict and has a known dependency/impact state.
2. The release candidate identifies included versions, excluded/unresolved scope, effective meaning and any freshness/expiry conditions.
3. Publication is a distinct controlled transition. Transport, scheduling, batching and synchronization mechanics are intentionally not decided here.
4. A successful publication marks the exact approved versions eligible for mobile consumption and records the release event.
5. Failure, partial completion or delay remains explicit. The system must not claim all content is live when only some scope became available.
6. Mobile consumption must preserve the current version/status/provenance/freshness semantics needed for fit, readiness, safety, history and trust behavior.

Exit: `Published`, explicit `Publication failed/partial`, or return to release preparation. No failure is silently treated as a success.

### W-08 — Monitor freshness, coverage and workflow health

Monitoring includes:

- scope coverage and unsupported gaps,
- completeness versus reviewed/published coverage,
- source/evidence freshness and withdrawal,
- unresolved conflicts and review backlog age,
- publication delays/failures,
- dependent claims/guides affected by new evidence or corrections,
- consumer feedback and critical safety impact,
- rollback/recall/re-review frequency.

An analytic signal creates a traceable research or correction item; it does not itself approve, reject or publish technical content.

### W-09 — Correct or supersede a published item

1. A correction trigger is triaged by consequence, scope, freshness, source quality, user interaction depth and whether work may be active.
2. The current published version remains historically visible with a correction/supersession relationship; it is not silently rewritten.
3. A new draft captures the corrected claim/content and links the reason/evidence.
4. Impact assessment identifies affected future application, open/in-progress work, completed records, evidence and dependent guides.
5. Review/approval/publish controls run again for the corrected version.
6. Affected user reach-back is proportional to risk and interaction depth: viewing-only may need an update indicator; opened/applied/completed work may need re-check, remap or safety guidance. Exact channels/SLA remain open.

### W-10 — Roll back a bad release

Rollback is a controlled corrective transition, not a history eraser:

1. Identify the release/version and reason for rollback.
2. Confirm a known-good approved version or safe fallback exists for the affected scope.
3. Assess whether users started work or recorded outcomes under the bad version.
4. Create a new rollback event/version that restores the known-good meaning where allowed.
5. Preserve the bad version, its publication window, provenance, decisions and affected-use relation in history.
6. Re-run review/approval appropriate to the risk and publish the controlled correction.

If no known-good version exists, the outcome is suspension/recall plus teaching-only or safe-recovery handling, not a guessed rollback.

### W-11 — Recall or suspend unsafe/invalid content

Recall is used when continued current application is unsafe, materially invalid, unfit for the scope or not supportable by remaining evidence.

1. Create a recall/suspension event with reason, severity, scope, source/evidence basis and decision owner.
2. Stop new motorcycle-facing application for the affected content as required; do not hide the problem behind a normal stale label.
3. Determine affected releases, motorcycle variants, guides, records and interaction depth.
4. Provide affected users a proportionate correction/re-check/remap/safe-stop path. Started work retains access to guidance needed for safe closure or recovery.
5. Keep historical use, version and provenance traceable; do not claim prior completion was verified merely because it was recorded.
6. Re-research/re-draft, independently review and publish a replacement only when the replacement is supported.
7. Close the recall only with a documented re-entry/replace decision; otherwise retain a current recalled/suspended state.

### W-12 — Source or evidence withdrawal

1. Record who/what withdrew or lost access, when, what scope is affected and whether the withdrawal is voluntary, unavailable or invalidated.
2. Preserve the historical provenance link and prior claim usage.
3. Remove withdrawn evidence from current evaluation where applicable.
4. Re-evaluate each dependent claim/content unit independently; do not globally invalidate unrelated claims by default.
5. If remaining evidence is sufficient, create a reviewed continuation; if not, downgrade to disputed/insufficient/recalled as appropriate.
6. Publish corrections/reach-back when the current consumer meaning changes.

### W-13 — Community contribution and downstream dependency

Community contribution follows a separate path:

`private experience → explicit opt-in scope → community review/moderation → community publication or revise/resubmit/appeal/withdraw`

Publication/acceptance remains distinct from official technical verification. If community material was used as a source or evidence input for a dependent claim, withdrawal creates a provenance event and dependent re-review; it does not silently erase the dependent history.

## 6. Role hand-offs and separation of duties

Role labels are capability-level requirements, not final organization or permission implementation:

| Role capability | Primary lifecycle responsibility | Must not imply |
|---|---|---|
| Researcher / domain contributor | Find scope, collect sources/evidence, propose facts and gaps. | Automatic correctness or publication authority. |
| Data/content editor | Structure records and guide content, prepare diffs and dependencies. | Final approval of their own high-consequence change by default. |
| Domain reviewer | Evaluate applicability, evidence, conflicts and content meaning. | That a review itself publishes or guarantees outcome. |
| Safety/technical approver | Accept or reject high-consequence/critical changes within scope. | Universal verification of every source or actor. |
| Release/publishing operator | Assemble and execute an approved controlled release, observe result. | Authority to turn unapproved edits live. |
| Quality/operations analyst | Inspect coverage, freshness, queues, incidents and workflow health. | Authority to change technical truth through a metric. |
| Auditor/administrator | Inspect history, manage controlled access/policy and investigate. | Permission to erase provenance or bypass review silently. |
| Community contributor/moderator | Provide or moderate separate community material. | Official technical-guide authority. |

High-consequence changes require an appropriate separation between proposing, reviewing/approving and publishing. Whether one person may hold multiple capabilities in low-risk cases, and the exact permission matrix, remain open for later controlled decisions.

## 7. Failure, interruption and recovery rules

- A failed action retains the last known state and exposes the failure reason and next safe action.
- A partially completed research/review/publish action is visibly partial; it is not promoted to complete.
- A reviewer interruption does not discard evidence, diffs or decision context.
- Concurrent changes create an explicit conflict/re-review path; last-write-wins is not an acceptable product rule for trust-critical content.
- An unavailable source or connectivity issue does not create a fabricated fresh/current state.
- A mobile consumer must not infer “verified” from a missing/empty internal field.
- When a critical publication is stale, withdrawn or recalled, teaching/reference may remain available only with explicit non-application semantics.
- Rollback, recall and restore operations are themselves auditable changes.

## 8. Required audit event families

At minimum, the lifecycle records events for:

`scope created → source linked → evidence added/withdrawn → draft created/edited → validation result → conflict opened/updated → review assigned → changes requested → approved/rejected → release prepared → published/partial/failed → superseded → correction → rollback → recall/suspension → re-review → republished → role/access change → export/audit inspection`.

Each event preserves actor, role/scope, time, reason, affected object/scope, old/new version/state and linked evidence/decision where applicable. The exact storage/immutability mechanism is not decided here; the product behavior must remain non-destructive and inspectable.

## 9. Phase-4 handoff questions

The next phase must evaluate, without changing these invariants:

1. Which platform form best supports the queues, diffs, review gates and audit depth?
2. Which data/content representation can preserve claim/version/provenance relationships and scoped applicability?
3. Which publication and consumer-freshness model makes partial/failure/recall states observable?
4. Which permission model separates proposal, review, approval, publication and audit while supporting real team size?
5. Which analytics approach supports drill-down from coverage/quality/workflow signals to evidence and audit events?
6. Where, if anywhere, can assistance/automation reduce research or editorial effort without becoming an unreviewed technical authority?
7. What retention, backup, legal/privacy and export controls are required for history, evidence withdrawal and community boundaries?

No answer to these questions is assumed by this Phase-3 document.
