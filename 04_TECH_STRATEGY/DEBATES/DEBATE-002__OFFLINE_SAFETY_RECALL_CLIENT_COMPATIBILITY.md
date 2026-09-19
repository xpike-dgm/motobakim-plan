# DEBATE-002 — OFFLINE SAFETY, RECALL & CLIENT COMPATIBILITY

Status: `APPROVED WORKING DIRECTION — CONSTRAINTS RECORDED / ADR PENDING`
Date: 2026-09-17
Decision level: Phase-4 product/technology policy recommendation; no code, no ADR, no numeric TTL decision

## 1. Decision Question

How can Kavriva preserve useful offline access without presenting stale, recalled or client-incompatible technical
content as safe/current motorcycle-facing application guidance?

The decision must cover:

- fully offline devices that cannot receive a new recall;
- background/push delivery that may be delayed or lost;
- freshness expiry during new or active physical work;
- device-time change, reboot and backup restore;
- old clients that cannot understand new safety semantics;
- teaching/history/provenance and safe-stop access that must remain available;
- browser-based Internal Operations behavior when disconnected or stale.

## 2. Approved Product Invariants

1. Downloaded guide/visual/safety/progress/history can remain offline-accessible; version/freshness is visible.
2. Offline availability is not application authorization.
3. Safety-critical stale content may remain teaching/reference but cannot appear as current application guidance.
4. Saved progress is context, not proof of current physical state; resume requires revalidation.
5. Material guide change stops old continuation until current physical state is safely remapped.
6. Known recalled/suspended content cannot start or continue normal application.
7. Historical use, provenance and the version actually used are not erased by correction/recall.
8. Started physical work retains the task-specific guidance needed for safe stop/closure/recovery.
9. Partial, unresolved and safely stopped outcomes are not false completion.
10. Exact numeric freshness limits are not yet approved and cannot be invented in this debate.

Primary repo authority:

- `02_DISCOVERY/SYNTHESIS/BUSINESS_RULES.md` — `BR-020`, `BR-021`, `BR-034`, `BR-043`, `BR-075`, `BR-104`, `BR-124`, `BR-125`, `BR-148`, `BR-149`
- `03_DESIGN/STATE_MATRIX.md` — interrupted work, resume, critical correction, stale/recall and safe recovery
- `03_DESIGN/NAVIGATION_MAP.md` — N-06, N-07 and N-16
- `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md`

## 3. Official Platform Evidence

Official primary documentation reviewed on 2026-09-17:

- Apple background updates: https://developer.apple.com/documentation/usernotifications/pushing-background-updates-to-your-app
- Apple background task strategies: https://developer.apple.com/documentation/backgroundtasks/choosing-background-strategies-for-your-app
- Apple background downloads: https://developer.apple.com/documentation/foundation/downloading-files-in-the-background
- Android Doze/App Standby: https://developer.android.com/training/monitoring-device-state/doze-standby
- Android persistent background work: https://developer.android.com/develop/background-work/background-tasks/persistent
- Firebase Android message receipt/delivery: https://firebase.google.com/docs/cloud-messaging/android/receive-messages
- Firebase delivery behavior: https://firebase.google.com/docs/cloud-messaging/understand-delivery
- Android system clocks: https://developer.android.com/reference/android/os/SystemClock.html
- Android Auto Backup: https://developer.android.com/identity/data/autobackup
- Apple file-system/backup placement: https://developer.apple.com/documentation/foundation/using-the-file-system-effectively
- Android in-app updates: https://developer.android.com/guide/playcore/in-app-updates
- Android AtomicFile: https://developer.android.com/reference/android/util/AtomicFile.html

Evidence-supported constraints:

- iOS and Android may defer background CPU/network work. Background/push delivery is not an exact-time guarantee.
- Android Doze can suspend network access and defer jobs, sync and ordinary alarms until maintenance windows.
- A fully offline device cannot receive a newly issued recall.
- User/device wall time can change. Monotonic time is useful within a running boot context but does not by itself
  prove elapsed real time across reboot or backup restore.
- Application data or databases may be included in device backup depending on platform/configuration; restored data
  is not proof of current content eligibility.
- Store update mechanisms do not guarantee that all installed clients immediately move to a compatible version.
- Local encryption, secure keys and atomic file replacement can protect confidentiality/write integrity, but none
  proves current approval, freshness or recall state.

Therefore Kavriva must not claim:

- recall reaches every device immediately;
- a scheduled background job always runs;
- push receipt is publication/recall authority;
- a local clock alone proves freshness across reboot/restore;
- restored or encrypted cached content is necessarily current;
- app-store update prompts instantly eliminate incompatible old clients.

## 4. Policy Options

### A — Online-only motorcycle-facing application

Offline permits teaching, history, saved context and safe recovery only. Every new/resumed application requires an
online eligibility check.

**Benefit:** smallest unknown-recall/time/restore exposure.

**Cost:** defeats much of Kavriva's approved roadside/offline application value.

### B — One uniform offline validity rule

All application content uses the same bounded offline rule.

**Benefit:** simplest user explanation and operations model.

**Cost:** treats routine and high-consequence work as equivalent; either over-blocks routine work or under-protects
critical work. It does not follow `BR-124` consequence-sensitive freshness meaning.

### C — Risk-tiered bounded offline eligibility

Teaching/history is separate. Motorcycle-facing application receives a bounded offline eligibility policy based on
claim/task consequence, freshness sensitivity, motorcycle fit and current readiness.

**Benefit:** preserves useful offline behavior while applying stricter rules where stale guidance could cause harm.

**Cost:** requires controlled risk classification, dependency propagation and clear user explanation. Exact windows
must be governed rather than guessed.

### D — Release-bound offline eligibility context

Every downloaded application bundle is associated with an exact content release, motorcycle/applicability scope,
client capability requirement, last authoritative validation and eligibility state. Backup/rollback does not create
new authority.

**Benefit:** strengthens version, downgrade/replay, old-backup and old-client handling.

**Cost:** heavier release/compatibility governance; still cannot teach an offline device about a brand-new recall.

### Rejected — Unbounded cached application

“Downloaded once, usable indefinitely for physical application” conflicts with critical freshness, recall and
material-change rules. It is not retained as an acceptable option.

## 5. Manager Recommendation

Carry **C + D together** as the provisional Phase-4 working policy:

> Risk-tiered, bounded offline application eligibility carried in release-bound context, with conservative
> fail-closed behavior for unknown critical state and permanently separate teaching/history/safe-recovery access.

This policy does not choose the mobile framework, database, sync transport, signing mechanism or numeric time limits.
It cannot become an ADR until the critical safety properties and user choices below are closed.

Required default rules:

- unknown/unclassified consequence is held, not treated as low risk;
- a guide/bundle inherits the highest consequence of every dependent claim, step and safety prerequisite;
- stale, disputed or missing dependency cannot silently lower the effective risk;
- classification and later risk change are attributable review decisions;
- if the required anti-replay/restore and safe-recovery properties cannot be established for a highest-consequence
  category, that category becomes online-only rather than receiving optimistic offline eligibility.

## 6. Proposed Product-State Policy

| Situation | Motorcycle-facing application | What remains available |
|---|---|---|
| Teaching/history content is old but not an application-critical claim | Not automatically blocked by age alone | Teaching, provenance, source/date, history |
| Low-consequence application; release/fit/readiness/validity remain satisfied | May remain eligible offline under its governed risk policy | Full applicable guide plus status |
| High-consequence application; bounded validity satisfied and client supports required semantics | May be eligible offline, subject to fit/readiness and resume rules | Applicable guide, safety and recovery |
| Freshness expired or authoritative status cannot be established | New/next physical progression held pending online re-check | Teaching, history, evidence capture, safe stop/recovery |
| Device time is contradictory, reboot/restore context cannot be trusted | Eligibility cannot be extended by local time; critical application held | Teaching/history/safe recovery; re-check route |
| Content is known recalled/suspended | Normal application closed | Recall reason, history, correction/re-check/remap, safe stop/recovery |
| Material change affects active work | Old continuation closed; current physical state must be remapped | Saved context, evidence, safe recovery, change explanation |
| Old client lacks a required safety capability/field | Affected application fails closed | Supported teaching/history/recovery and update explanation |
| Partial/mixed/corrupt download | Never current/eligible | Last known valid safe context, retry/recovery explanation |

For a fresh install with no prior complete safe context, partial/mixed/corrupt content provides no physical application
or task-specific recovery authority. The user receives a clear unavailable/do-not-proceed state and safe escalation.

## 7. Recall and Connectivity Rules

1. Push/background delivery is a **wake-up or re-check hint**, not recall truth.
2. Authoritative reconciliation occurs when connectivity is available at defined boundaries: application launch,
   foreground return, network return, before new application and before interrupted-work resume where required.
3. A fully offline device may not know a new recall; bounded eligibility limits the exposure rather than pretending
   it can be eliminated.
4. On reconnection, current release/eligibility/recall/client-capability state is reconciled before further physical
   progression. Material change routes to remap; mismatch routes to recovery; only successful validation reopens.
5. Known recall always overrides an otherwise unexpired local eligibility state.
6. Missed push or delayed background work cannot leave an online/foreground user silently on known unsafe content.
7. `Known to server`, `known to client` and `last authoritatively reconciled` are distinct states. A recall can occur
   immediately after a successful check; this residual race cannot be described as eliminated.
8. Highest-consequence steps require a later explicit decision between always-online checks and a tightly bounded,
   server-issued eligibility authority with defined re-check boundaries. This debate does not choose between them.
9. APNs/FCM is never the sole emergency-recall channel. Emergency suspension, service-outage behavior and external
   reach-back require a separate controlled strategy.

## 8. Active Work and Safe Closure

- Resume restores motorcycle, guide version, last definite step, notes/photos and saved context—not prior critical
  confirmations as current proof.
- If freshness becomes uncertain during physical work, the system stops ordinary next-step progression at the next
  safe decision boundary; it does not abandon the user mid-task.
- Task-specific safe-stop/closure/recovery material required for the current physical state remains accessible even
  when normal application eligibility closes.
- Safe-recovery access cannot be used as a hidden route into unrelated/new application steps.
- The final state is truthfully recorded as completed, partial/unresolved or safely stopped.

The exact definition of each task's “safe decision boundary” belongs to the reviewed guide content and must not be
invented by the client at runtime.

Offline-start eligibility additionally requires a complete, version-pinned and independently reviewed safe-stop/
recovery package for every physical state the offline guide can create. Its dependency closure and client capability
must be accepted before the application bundle becomes eligible. Missing, incomplete, expired or unsupported recovery
coverage blocks offline start. The recovery package is governed separately enough that recalling a normal application
step does not automatically remove the only safe closure guidance.

If local recovery content becomes unavailable unexpectedly during active work because of device/storage failure, the
product must not promise an impossible perfect recovery. It presents the safest available do-not-proceed/preserve-state/
support path, records the interruption when possible and does not mark the work complete.

## 9. Device Time, Reboot and Backup/Restore

- Wall-clock rollback/forward anomalies cannot be used as proof to extend eligibility.
- Local monotonic time may support same-boot duration reasoning but is not sufficient across restart/restore.
- Restore/clone suspicion, missing validation anchor or contradictory time moves critical application to
  `eligibility uncertain / online re-check required`. A normal reboot with a later-approved intact trust anchor need
  not be universally blocked; reboot handling remains evidence-dependent rather than assumed.
- Restored user history/progress retains the guide version historically used.
- Restored downloaded content is treated as derived cache/reference until current eligibility is established.
- Account/device/profile binding conflicts are quarantined for explicit migration review; no silent merge.

Release-bound context must provide these technology-neutral safety properties before offline critical use:

- authenticated and complete release/recovery manifest;
- content/dependency integrity and capability binding;
- monotonic release/revocation ordering or equivalent anti-rollback floor;
- separation of content integrity, positive eligibility authority and historical provenance;
- restored/cloned positive eligibility is non-authoritative until trust context is re-established;
- mixed release graphs are rejected and a complete snapshot is promoted as one controlled state.

These are required properties, not a decision for a particular signature, database or storage implementation.

## 10. Client–Content Compatibility

Every application release must be expressible with:

- content/release version,
- required client capability/contract version,
- motorcycle/applicability scope,
- application eligibility and freshness context,
- recall/suspension/current-state meaning,
- preserved historical version relation.

Unknown safety-critical fields or an unmet minimum capability close the affected application flow. A store update
prompt may help recovery but is not itself a guaranteed enforcement mechanism. Teaching/history/safe recovery remains
available only where the old client can represent it without hiding critical meaning.

Every supported client must understand a minimal immutable envelope before rendering content: release identity,
eligibility/recall state, required capability and whether unknown fields are safety-critical. Capability negotiation
occurs before download/use; there is no fallback to an incompatible old release for physical application. Long-dormant
client policy remains unresolved and bounded validity still limits what a fully offline old client may do.

## 11. Browser-Based Internal Operations

The browser client may not claim authoritative offline success for approve, publish, recall, role change or audit
events. These mutations require current server-side authorization and version checks.

Initial recommendation:

- authoritative operations are online-only;
- stale tabs/sessions cannot approve or publish a changed version;
- cached read-only material, if later allowed, is visibly non-authoritative;
- offline draft support is not a Phase-4 baseline requirement and needs a separate user decision if desired.

Online-only does not make network outcomes unambiguous. Every authoritative mutation requires a unique idempotent
operation identity and current server version/authorization check. If connectivity fails after submission, the UI
records `outcome unknown`, asks the server for the authoritative result and never invites blind duplicate approval,
publication or recall. Server time/result supplies the audit meaning. Stale private cached data, revoked sessions and
service-worker/back-cache behavior require explicit browser security policy.

## 12. No-Code Evidence Matrix

Before ADR, every mobile technology candidate is assessed against the same written scenarios using official evidence,
known platform behavior and explicit unknowns:

1. long-offline critical content;
2. recall issued while offline;
3. missed push/background task;
4. freshness expiry during active work;
5. device-time rollback and reboot;
6. old backup restoring old content/history;
7. old client missing a new safety semantic;
8. material guide change during active work;
9. partial/mixed download;
10. server/identity/publishing outage during recall.

Each written scenario must state pass/fail and visible states, including mappings to:

- `SCR-015` mismatch/recovery,
- `SCR-016` resume revalidation,
- `SCR-017` material-change remap,
- `SCR-018` completed vs partial/unresolved vs safely stopped.

Release/recall evidence also retains dependency closure, effective highest risk, affected interaction depth (view,
open, active step, evidence, completion) and acknowledgment/recheck state so dependent guides and active users are not
missed. Account-light local use remains valid; eligibility must not silently become a profile prerequisite.

No prototype, executable test or application code is authorized by this matrix.

## 13. Data-Efficient Offline Package Policy

User authority: `DEC-0023`.

Offline support must minimize network and storage use without stripping safety context. It is not a bulk-download
mirror of the complete Kavriva content library.

### Default package boundary

The default unit is scoped to:

- the selected motorcycle/model/year/variant and applicable modifications;
- the selected guide/task;
- the exact approved release/client capability context;
- the current/expected physical-work states;
- the minimum complete task-specific safe-stop/recovery closure.

Unrelated motorcycles, other guides and unused media are excluded.

### Package layers

| Layer | Default | Contents |
|---|---|---|
| Safety/application core | Required | Fit/version/status, compact text/steps, critical warnings, required checks, completion states and complete task-specific safe-stop/recovery. |
| Essential instructional media | Required only when the guide cannot be safely understood without it | Optimized images/diagrams or other verified minimum media tied to specific steps. |
| Enhanced media | Optional/on-demand | High-resolution images, extended galleries, video and nonessential teaching material. Size is shown before download. |
| Personal work context | Small and persistent | Progress, confirmations, notes, selected evidence references and historically used guide version. User media follows separate storage/privacy policy. |

### Data controls

- No automatic full-library or full-motorcycle-catalog download.
- No large cellular background download by default.
- Show package size and what it contains before optional/large download.
- Allow network preference and explicit cellular consent for large packages; exact size thresholds remain open.
- Reuse identical assets rather than downloading duplicates.
- Prefer changed/required assets over complete replacement when later integrity architecture can prove a safe update.
- Keep cache size/expiry understandable and provide user-controlled cleanup.
- Never evict active-work safe-stop/recovery content while the work is open.
- Never reduce a package below the safety/application closure needed for its reachable physical states.
- A small package that is incomplete, mixed-version or missing a required dependency is ineligible, not “data efficient.”

### No-code comparison evidence

Every mobile technology candidate must explain, from official capability evidence:

- task-scoped package storage;
- resumable/interrupted download behavior;
- duplicate asset avoidance and incremental update feasibility;
- package-size visibility and cellular/Wi-Fi policy controls;
- active-work pinning and safe cleanup;
- partial/mixed package rejection;
- optional media separation without hiding required safety meaning.

No numeric package limit is invented at this stage.

## 14. Unresolved Decisions

1. Exact risk taxonomy and which claims/tasks belong to each class.
2. Numeric validity windows and who may approve/change them.
3. Whether any highest-consequence category is always online-only.
4. Formal guide-authoring rule for task-specific safe decision boundaries and recovery packages.
5. Minimum supported client/capability window and long-dormant-client policy.
6. Server-outage behavior versus recall/emergency-suspension behavior.
7. Backup inclusion/exclusion by user data, history, content cache and trust/eligibility metadata.
8. Whether Internal Operations needs offline drafts; authoritative mutations remain online-only either way.
9. Recall reach-back channels, acknowledgment and SLA by consequence/interaction depth.
10. Accepted residual race between two authoritative checks and the categories that therefore require online-only use.
11. Emergency suspension authority and behavior during publishing, identity, database or CDN outage.
12. Package-size classes, cellular-download threshold and default cache/storage budget.
13. Which media is truly safety-essential per guide, versus optional enhanced teaching.
14. User-photo/evidence retention and upload/download policy, which is separate from official guide packages.

## 15. User Decision

The user approved the following working direction under `DEC-0024` after the data-efficiency refinement:

1. risk-tiered bounded offline eligibility rather than always-online or unlimited offline application;
2. release-bound version/compatibility context;
3. fail-closed critical uncertainty while preserving teaching/history/task-specific safe recovery;
4. browser-based Internal Operations authoritative actions being online-only by default.
5. offline downloads being task/motorcycle-scoped and layered, with optional heavy media and mandatory compact safety/recovery core.

This approval does not decide any numeric limit or implementation technology.

## 16. ADR Status

No ADR is created or approved. Two independent Luna Max reviews returned `PASS_WITH_CHANGES`; their critical findings
are incorporated. The working direction is user-approved, while named unresolved decisions remain Phase-4 work.

Canonical review records:

- `DEBATE-002__REVIEW_A_PRODUCT_SAFETY.md`
- `DEBATE-002__REVIEW_B_PLATFORM_SECURITY.md`
