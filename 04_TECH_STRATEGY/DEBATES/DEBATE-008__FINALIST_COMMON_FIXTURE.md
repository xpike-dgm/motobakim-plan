# DEBATE-008 — Finalist Common No-Code Fixture

Status: `CONTROLLED COMPARISON FIXTURE / NO-CODE / NO PROVIDER APPROVAL`
Date: 2026-09-18

## 1. Purpose

This fixture compares two concrete candidate compositions under identical Kavriva requirements:

- **Candidate A — Supabase-managed composition:** Supabase PostgreSQL/Auth/Storage/Functions primitives, but all
  high-consequence Kavriva mutations remain behind the approved server/API policy boundary. Direct client Data API use is
  limited to later explicitly proven low-risk reads/actions; RLS is defense in depth, not sole authority.
- **Candidate B — modular managed composition:** Neon managed PostgreSQL + Render independent API runtime + Cloudflare R2
  object storage as current representative components. These names make cost and failure domains concrete; a later ADR
  may replace a representative only through the same evidence gates.

Neither candidate is approved. Both must expose every additional service needed for identity, protected audit,
quarantine/scanning, monitoring, notification, backups, export and emergency negative authority.

## 2. Frozen Owner and Product Facts

- one nontechnical owner; AI performs technical work through bounded implement/review/validate roles;
- no owner coding, database administration, SSH, log diagnosis or incident repair;
- Flutter mobile; Android first, iOS later;
- browser-based Internal Operations; high-consequence actions online-authoritative;
- scoped data-efficient offline package; no full-library default download;
- user history, private/shared/community data, media, provenance and recall are high-value data;
- later non-store planning ceiling is TRY 2,000–3,000/month, not immediate spend authorization;
- current official prices remain in their billing currency; tax/FX/card uncertainty is separate;
- no code, prototype, provider account, subscription or purchase during this comparison.

## 3. Frozen Logical Architecture

Both candidates must preserve `DEC-0034`:

- canonical transactional authority per domain;
- server/API-mediated sensitive access;
- online-authoritative Internal Operations;
- machine-verifiable bounded offline packages;
- durable identified user operations and explicit reconciliation;
- separate current/history/protected-audit and object/media planes;
- non-authoritative projections;
- non-restorable negative/deletion/accepted-operation floor;
- cross-plane consistent backup/restore/export/exit;
- provider/account/billing failure states and bounded AI operations.

Candidate convenience cannot weaken or merge these boundaries.

## 4. Equal Workload and Cost Horizons

The documentary comparison uses the existing Phase-4 workload horizons:

| Stage | Active-user fixture | Operational meaning |
|---|---:|---|
| P0 | 0 | planning and documentary evaluation only |
| P1 | 100 | private/internal/closed-test preparation |
| P2 | 10,000 | first meaningful production scale checkpoint |
| P3 | 50,000 | growth stress checkpoint, not a forecast |

Both candidates use identical data fixtures inherited from `DEC-0031`: 12 MB compact transfer, optional media up to
150 MB, 25 MB cellular confirmation and 250 MB content cache. These are comparison values, not final limits.

Cost must be shown at:

- planning/free exploration;
- minimum safe closed-test operation;
- minimum safe Android production operation;
- later iOS addition;
- P2 and P3 scale pressure;
- one restore drill and one provider-exit drill;
- one incident month with elevated logs, retries, export and object operations.

Each cost is classified mandatory now, mandatory later, deferrable, optional, scale-triggered or contingency. Unknowns
remain `UNRESOLVED`; free tier never substitutes for backup, audit, recovery or support evidence.

## 5. Equal Evidence Pack

Each candidate must provide the same sections:

1. exact provider products and dated official price/limit snapshot;
2. account, project, region and billing failure-domain inventory;
3. client/API/database/object/worker/admin/provider-console privileged-path matrix;
4. credential classes, owner/legal actions, AI-access rules and rotation/recovery;
5. canonical transaction and cross-plane partial/unknown/reconcile state machine;
6. authorization and negative-test plan, including privileged bypass;
7. offline package builder, local operation and conflict/retry model;
8. protected audit and non-restorable floor location/failure independence;
9. media quarantine, object finalization, version/digest/access/delete lifecycle;
10. database, object, audit, identity/policy/config/package backup and restore closure;
11. logical export and clean-room import outside the candidate's normal account;
12. observability, incident support and no-owner-debug AI runbook;
13. P0–P3 staged cost, cap/overage behavior and safe budget-hold mode;
14. provider replacement and architecture exit dossier;
15. result: `PASS`, `HELD` or `REJECT` per scenario and overall documentary disposition.

## 6. Equal Failure Scenarios

| ID | Injected scenario | Required outcome |
|---|---|---|
| F01 | Browser role revoked while stale tab remains open | Commit reauthorization denies/holds; cached UI has no authority. |
| F02 | Privileged server/admin key leaks | Revoke/rotate, invalidate affected sessions/operations, audit impact; no client exposure. |
| F03 | Database commit succeeds but response is lost | Durable operation lookup returns original result; no duplicate effect. |
| F04 | Object upload succeeds but metadata/audit step fails | Object remains quarantined/orphaned; no official availability; safe reconcile/cleanup. |
| F05 | Publish races emergency suspension | Newer negative generation wins; in-flight positive action cannot erase it. |
| F06 | Offline package delta is incomplete or wrong-base | Atomic reject; last valid safe context/fallback complete package; no mixed use. |
| F07 | Offline user operation conflicts with newer ownership/provenance state | Preserve both evidence; high-consequence conflict held for reviewed resolution. |
| F08 | Old backup is restored after recall, role revoke, delete and accepted operation | Restore quarantine and external floor prevent resurrection/replay. |
| F09 | Database restore succeeds but objects/audit/config differ | Cross-plane manifest detects mismatch; no authority cutover. |
| F10 | Provider account, billing or quota is suspended | Positive work safely held; owner-readable state; recovery/export path; no surprise overage. |
| F11 | Primary provider/region unavailable | Defined bounded read/safe-recovery behavior; no false availability or owner repair. |
| F12 | Clean-room exit outside normal account | Stable IDs, policy, objects, audit, floor and negative tests survive import before cutover. |
| F13 | AI receives one ordinary task | Minimum context/least privilege; no broad secret, console owner or whole-project dependence. |
| F14 | AI operation fails halfway | Machine-readable evidence, stop/forward recovery and independent review; no owner debugging. |
| F15 | P2/P3 usage or incident month exceeds planned quota | Actual cap/overage behavior and safe degraded/held mode; no unlimited charge assumption. |
| F16 | Provider changes API/default/security behavior | Dated changelog impact, compatibility hold, migration/revalidation; no silent production drift. |

## 7. Result Rules

`PASS` requires candidate-specific documentary closure with current official evidence and no unresolved critical control.
It does not mean a real build, restore or release passed.

`HELD` applies when a required mechanism, price/cap, failure-domain, export/import, owner action or evidence route remains
unknown but a safe hold/fallback is credible.

`REJECT` applies when the composition requires direct general client authority, sole reliance on mutable/provider audit,
silent high-consequence overwrite, resurrection-prone restore, non-exportable truth, uncapped unavoidable spending,
unavoidable owner debugging or a critical product requirement being weakened.

No aggregate score may compensate for a critical hold or reject.

## 8. Selection Boundary

The equal dossier and review stage may recommend one candidate as a reversible Phase-4 physical-stack working direction.
It cannot create the Phase-5 ADR, authorize an account/purchase, claim production readiness or advance Gate 4 -> 5.

## 9. Normalized Hidden-Service Inventory

Neither candidate receives a simplicity or price advantage by leaving a required service unnamed. Both cost and failure
maps must show the same roles, even when the eventual provider remains `UNRESOLVED`:

- server/API policy runtime;
- identity, session, recovery and privileged step-up;
- protected audit custody and non-restorable negative/deletion/accepted-operation floor;
- quarantine, malware/archive/parser/preview isolation and controlled URL retrieval;
- package builder, durable operations/outbox worker and reconciliation;
- notification/delivery;
- observability, alerting and incident evidence;
- database/object/audit/config/package backup, export and clean-room import;
- emergency negative authority;
- secrets, signing/key custody, release/config provenance and support route.

Supabase Studio, Neon/Render/Cloudflare consoles or any generated provider admin surface are not Kavriva Internal
Operations. The Kavriva browser panel remains an online-authoritative product surface with contextual server
reauthorization, audit evidence, safe hold, recall/suspension generation and owner-readable recovery states.

## 10. Normalized Cost Worksheet

Each candidate must use these rows: `P0 planning`, `P1 minimum safe closed test`, `minimum safe Android production`,
`later iOS addition`, `P2`, `P3`, `incident month`, `one restore drill` and `one clean-room exit drill`.

Each row must expose, where applicable: subscription, compute/CU, database storage, egress, object bytes and operations,
history/PITR, logs, workers/functions, identity/SMS, audit custody, scanner/preview, monitoring, notification, backup/export,
support, domain, tax/FX/card and reviewer/operator labour. Unknown totals remain `UNRESOLVED`; a headline provider price,
free allowance, alert or partial spend cap is not a composite hard ceiling.

## 11. Candidate-Neutral Hard-Fail Register

The following are `REJECT-IF-UNMITIGATED` for either candidate:

1. direct client or provider-console canonical authority;
2. privileged key, owner, superuser or bypass path used as ordinary product authority;
3. no sufficiently independent negative authority, protected audit or anti-resurrection floor;
4. cross-plane partial state denied, hidden or silently treated as success;
5. unsafe offline package, silent last-write-wins, wrong-base merge or uncontrolled cache eviction;
6. database-only restore or a cutover capable of resurrecting revoke, recall, deletion or accepted operations;
7. quarantine, scan, preview or upload success treated as approval or correctness;
8. no bounded billing/account/region hold and unavoidable uncapped spending;
9. no clean-room exit or non-exportable authoritative truth;
10. owner SSH, database administration, dashboard repair, log diagnosis or incident debugging dependency;
11. unversioned API, config, package, credential or provider-default drift.

## 12. Normalized Evidence Labels

- `[CONFIRMED-2026]`: exact official URL, read date, product/plan/region and stated mechanism or limit.
- `[INFERRED]`: architectural consequence derived from an official primitive plus the Kavriva contract.
- `[UNVERIFIED]`: current primary evidence, measurement, contract or drill is absent or stale.
- `[HELD]`: a positive effect remains closed until the critical evidence is complete.

Different prose detail in the finalist dossiers cannot raise or lower the common acceptance standard above.
