# DEBATE-017 — Production Download, Storage Limits and Automatic Transfer Policy

Status: `ACTIVE / PRIMARY RESEARCH REQUIRED / NO FINAL NUMERIC LIMITS YET`

## 1. Purpose

Close `TSQ-009` at Phase-4 working-direction level by determining a defensible first-release policy for:

- selected motorcycle/task offline package size;
- required vs nonessential media transfer;
- automatic downloads over Wi-Fi and cellular/mobile data;
- device cache/storage budget;
- eviction/cleanup;
- retry/resume/interruption behavior;
- low-storage behavior;
- data-efficiency and recurring delivery cost;
- exceptions where safety/recovery content cannot be removed merely to fit a numeric limit.

This debate is about **product policy and evidence**, not implementation code or a provider purchase.

## 2. Binding Owner Constraint — CON-005

The owner has explicitly directed:

> Kavriva must not ask the user for download confirmation merely because the connection is cellular/mobile data or because a byte threshold is crossed. Required content should continue over mobile data without that extra prompt.

Implications:

- the historical `25 MB cellular confirmation` fixture is NOT a candidate final product behavior;
- do not propose "ask above N MB" as a retained family;
- network type alone may not create a user confirmation gate;
- download policy should be automatic and quiet by default;
- this does not require downloading unrelated content or the whole catalog;
- this does not prevent internal prioritization, resumable transfer, retry/backoff, deduplication, cache eviction or cost controls;
- optional/nonessential media may remain a distinct content class, but "cellular" must not itself trigger a confirmation dialog.

### Supersession note

The cellular-confirmation / explicit-user-control language inside older `DEC-0023`-derived research is superseded for future
product direction by the newer explicit owner constraint `CON-005`. The rest of DEC-0023 remains active: downloads stay
data-efficient, selected-motorcycle/task scoped, and unrelated/full-library content is not downloaded by default.

## 3. Existing Binding Product Direction

Research must preserve:

- `DEC-0024`: offline use is bounded, risk-tiered, release/client compatible and complete enough for safe stop/recovery;
- `DEC-0036`: one immutable complete compact selected-task package is the first-release offline-content baseline;
- optional high-volume media is separate, cancelable and evictable;
- unrelated catalog content is not downloaded by default;
- partial/corrupt/mixed/stale/incompatible packages cannot become actionable;
- stage -> verify -> atomic promote semantics remain required conceptually;
- required safety/recovery closure cannot be removed just to hit a byte target;
- user history, notes, evidence, accepted/pending operation truth and protected records are not disposable cache;
- cache eviction must never erase canonical user-owned history or create false safety/recall state;
- Android-first does not allow a policy that is impossible to carry to iOS later.

## 4. Historical Comparison Fixtures — Not Final Limits

The following values were frozen only to compare prior candidates:

- compact package: `12 MB`;
- optional media: up to `150 MB`;
- cellular confirmation: `25 MB` — superseded as product behavior by CON-005;
- refetchable content cache: `250 MB`;
- unrelated catalog negative case: `2 GB`.

Research may use these as sensitivity anchors, but must not treat them as approved production limits.

## 5. Policy Families To Compare Equally

### Family A — Strict fixed caps
One fixed maximum for compact package, media class and cache. Automatic mobile-data transfer remains mandatory under CON-005.

### Family B — Tiered fixed caps by content class
Separate limits for required core, required media, nonessential media, and refetchable cache. No cellular confirmation gate.

### Family C — Adaptive bounded policy
Per-item/content-class hard safety bounds plus device-free-space percentage/absolute reserve and automatic eviction rules.
Network type may affect scheduling priority only where product requirements allow, not whether the user is asked to approve.

### Family D — Small mandatory core + automatic on-demand media/cache hybrid
Keep the always-ready complete safe core small; automatically fetch additional eligible media/content when the selected
task actually needs it; retain under a bounded adaptive cache; no cellular confirmation dialog.

No family is preselected.

## 6. Required Numeric Sensitivity Matrix

At minimum test:

### Compact selected-task package
- 5 MB
- 12 MB
- 25 MB
- 50 MB
- 100 MB

### Additional media for a selected task
- 25 MB
- 100 MB
- 150 MB
- 300 MB
- 500 MB

### Refetchable content cache
- 100 MB
- 250 MB
- 500 MB
- 1 GB
- 2 GB

### Device state
- plenty of free storage;
- 20% free;
- 10% free;
- 5% free;
- OS low-storage pressure / cache purge;
- app reinstall/restore/migration.

### Network state
- stable Wi-Fi;
- ordinary cellular;
- slow cellular (about 1 Mbps / high latency);
- interrupted cellular;
- roaming;
- Android Data Saver / metered semantics;
- iOS Low Data Mode / constrained network semantics;
- offline then reconnect.

Exact numeric conclusions require evidence; unsupported values remain HELD.

## 7. Mandatory Research Questions

### User experience
- Can all required selected-task content download automatically without a mobile-data confirmation?
- What progress/error/retry information should be visible without asking unnecessary questions?
- When is cancel/pause legitimate versus harmful to safety/recovery continuity?
- How should the app behave when media is large but the user has already chosen the task?

### Package limits
- What should count toward the compact package?
- Which media is required for safe completion versus nonessential enhancement?
- Is one hard per-package maximum defensible?
- Should an oversize but safety-required package be rejected, compressed/re-authored, split by safe closure, or allowed as an exception?

### Storage/cache
- What is refetchable cache versus durable user-owned data?
- What absolute/percentage reserve should be protected for OS/device health?
- How much cache can be evicted automatically?
- What gets evicted first?
- Can the currently active task package be evicted?
- How should multiple saved motorcycles/tasks compete for cache?

### Transfer behavior
- foreground vs background transfer;
- retry/backoff/resume;
- process death/OS termination;
- duplicate/repeated download prevention;
- partial-file cleanup;
- update/delta vs full re-fetch;
- low-data/Data Saver semantics without a Kavriva confirmation prompt;
- roaming behavior without inventing a user prompt forbidden by CON-005.

### Cost/TCO
- first-release bandwidth/storage assumptions at low, normal and stress usage;
- sensitivity to media-heavy tasks;
- CDN/object egress/storage/request cost categories without selecting a provider;
- effect of dedup/compression/cache hit/re-fetch policy;
- safe 12/24-month planning ranges, explicitly scenario-based rather than final budget.

### Safety/truth
- package byte target cannot remove warnings/checks/safe-stop/recovery;
- a partial/corrupt download never becomes actionable;
- stale/recalled content cannot become valid because it is cached;
- storage pressure cannot delete protected user history/evidence;
- offline availability is not current authorization.

## 8. Mandatory Failure Walkthrough

Analyze at least these 16 scenarios for all four policy families:

1. Required package exceeds proposed compact limit.
2. Required safety media alone pushes package above the normal target.
3. User starts selected task on ordinary cellular with a large required download.
4. Very slow/high-latency cellular connection.
5. Transfer is interrupted repeatedly.
6. OS kills the app during transfer.
7. Device reaches low-storage pressure during staging.
8. Refetchable cache exceeds its budget.
9. Active-task package competes with old cached tasks.
10. Multiple motorcycles/tasks accumulate offline content.
11. Same media asset is referenced by multiple guides/packages.
12. Published package is updated while an old package is partly downloaded.
13. Recall/suspension occurs while cached/offline content exists.
14. Android Data Saver / iOS Low Data Mode / constrained-network condition exists.
15. Device restore/reinstall/migration brings back old cache/package files.
16. Delivery/provider/CDN path must be replaced without losing product-policy meaning.

For every scenario and family write:
- expected safe state;
- automatic transfer/storage behavior;
- user-visible behavior;
- what is protected from eviction;
- evidence;
- recovery owner;
- next action;
- bandwidth/cost impact;
- storage impact;
- safety/truth impact;
- exit/portability impact;
- HELD gaps.

## 9. Evidence Standard

Use current official/primary sources where the fact is platform-mechanism dependent:

- Android Developers: app-specific storage/cache, storage pressure, WorkManager/background work, connectivity/metered/Data Saver,
  backup/restore, process/lifecycle limits;
- Apple Developer: URLSession/background transfer, Caches/Application Support/document storage classes, Low Data Mode /
  constrained network behavior, storage pressure/purge semantics, backup/restore/lifecycle limits;
- Flutter official docs only for framework-level lifecycle/offline/background boundary facts;
- existing canonical Kavriva repo decisions and reviewed Phase-4 evidence for product authority.

Do not use generic blog advice as acceptance evidence for platform behavior.

Where there is no official platform rule that says "the correct cache is N MB", explicitly label the numeric recommendation
as a reasoned product policy supported by sensitivity analysis, not as a platform fact.

## 10. Required Deliverables

Drive:
- `CTX-P4-018 — PRODUCTION DOWNLOAD STORAGE LIMITS AND AUTO-TRANSFER POLICY`
- `TASK-006 — DEBATE-017 PRODUCTION DOWNLOAD STORAGE LIMITS PRIMARY RESEARCH`
- output: `DEBATE-017__PRODUCTION_DOWNLOAD_STORAGE_LIMITS_PRIMARY_RESEARCH`
- handoff: `HANDOFF-TASK-006`

Report must end with a nontechnical owner section containing:

- recommended first-release compact package policy;
- recommended required/nonessential media policy;
- recommended cache/storage policy;
- automatic cellular behavior;
- low-storage behavior;
- what is never auto-evicted;
- numeric ranges or exact provisional limits, each clearly marked PROPOSED / HELD;
- explicit explanation of what changed from the old 12/150/25/250 fixture;
- whether any user confirmation is still required for download transport (expected answer under CON-005: no).

## 11. Boundaries

No code, pseudocode, prototype, app build, live device test, account, provider trial, CDN/storage purchase, deployment,
schema/migration, final provider selection, final commercial budget, Phase-5 ADR or Gate 4 -> 5 transition.

Do not silently rewrite historical comparison documents. Current authority is carried by CON-005, this requirements file,
and later user-approved synthesis.
