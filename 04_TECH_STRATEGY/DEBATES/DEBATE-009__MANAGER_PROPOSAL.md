# DEBATE-009 — Manager Proposal: Data-Efficient Offline and Sync Direction

Status: `REVIEWED / CORRECTED BY DEBATE-009 JUDGE SYNTHESIS / NO-CODE / ADR NOT READY`  
Date: 2026-09-18

## Plain-language proposal

Kavriva telefona bütün veri kataloğunu kopyalamayacak. Kullanıcının seçtiği motosiklet ve o anda yaptığı görev için
gereken küçük, kapalı ve doğrulanabilir paket indirilecek. Yüksek boyutlu fotoğraf/video ayrıca ve yalnız kullanıcı
isterse indirilecek.

Önerilen yerel temel **SQLite + Drift** yönüdür. Bu, telefondaki verinin dosya/tablolarını Kavriva'nın kontrol etmesini,
indirme paketlerini ve kullanıcı işlemlerini birbirinden ayırmasını sağlar. Drift senkronizasyonu kendi başına çözmez;
Kavriva'nın API sözleşmesi paketi, işlem kimliğini, çakışmayı, geri çağırmayı ve toparlanmayı açıkça yönetir.

PowerSync ikinci aday olarak korunur. Hazır kısmi eşitleme ve kuyruk sağlayabilir; fakat yeni ücret, yapılandırma,
sağlayıcı ve arıza yüzeyi ekler. Kavriva'nın temel ihtiyacı genel veritabanı kopyalamak değil, seçili görevin kapalı
paketini güvenli taşımaktır. Bu nedenle ilk çalışma yönü app-owned Drift/custom protocol'dür.

## Proposed reversible direction

### 1. Two local data lanes

1. **Offline content package lane**
   - selected motorcycle/model-year/resolved variant + one active task;
   - immutable package generation, manifest, dependency closure, digest and compatibility;
   - compact safety/application/safe-stop/recovery content complete without optional media;
   - package data is authorized content delivery, not user history or server truth.
2. **Durable local user-operation lane**
   - history, notes, evidence metadata, pending uploads and account-light work;
   - stable operation identity, payload fingerprint, expected version and visible state;
   - `PENDING`, `SUBMITTED`, `ACCEPTED`, `CONFLICT`, `HELD`, `FAILED`, `OUTCOME_UNKNOWN`, `RECONCILING`;
   - local persistence never means server acceptance.

Re-fetchable cache, optional media and temporary package staging are separate from both durable lanes.

### 2. Package and delta rule

- A complete package is the recovery baseline.
- A delta is accepted only against the exact declared base generation and compatibility contract.
- Missing/out-of-order/corrupt/wrong-base delta is rejected atomically; no closest-match or partial merge.
- The last valid complete package stays intact until the replacement package is fully verified and promoted.
- If a valid delta chain cannot close, the app requests a new complete compact package.

### 3. Server/API rule

- Flutter communicates through the Kavriva API boundary approved by `DEC-0034` and `DEC-0035`.
- General direct client writes to canonical Supabase tables or Storage are not the sync design.
- Server operation identity and result lookup make response loss/retry safe.
- High-consequence conflicts are held for explicit resolution; no universal last-write-wins.
- Supabase RLS/Storage policies remain defense in depth.

### 4. Realtime and notification rule

Supabase Realtime, push notifications or ordinary network callbacks may tell the app that newer information could exist.
They do not prove delivery, freshness, recall, deletion, package completion or server acceptance. Foreground/API
reconciliation rechecks the authoritative generation and suspension floor.

### 5. Data-consumption rule

The current comparison fixture remains:

- compact transfer target: up to 12 MB;
- optional media: separately selected, up to 150 MB;
- cellular confirmation: above 25 MB;
- default re-fetchable content cache: 250 MB;
- unrelated 2 GB catalog: must not be downloaded by default.

These are evaluation constants, not final commercial limits. Required safety/recovery closure cannot be removed merely to
fit a size number. The app shows expected transfer class and keeps optional media cancelable/evictable.

### 6. Device and restore rule

- Correctness cannot depend on background execution or a lifecycle callback arriving.
- App kill, reboot, storage pressure and interrupted migration preserve durable operations and the last valid package.
- OS backup/restore enters reconciliation quarantine; restored data cannot revive newer recall, revoke, deletion or an
  already accepted operation.
- Device clock cannot grant freshness or extend authority.
- Local encryption is a separate decision: Drift/SQLite does not by itself solve encryption, key custody or recovery.

### 7. Account-light migration rule

Local-to-profile transfer shows scope before upload, preserves source data until accepted/reconciled, uses stable IDs and
operation identity, and surfaces duplicates/private-data conflicts. Cancel/failure leaves local value usable; partial
target state is not reported as success.

## Candidate disposition before independent review

| Family | Proposed role | Reason |
|---|---|---|
| Drift/SQLite + Kavriva package/operation API | Primary reversible working direction | Best fit for bounded selected-task packages, explicit user truth, provider independence and no extra sync subscription. |
| PowerSync + Supabase | First challenger/fallback | Strong selective replication/queue primitives, but adds service/config/billing/failure and still needs Kavriva conflict/recall/API rules. |
| Raw sqflite/SQLite | Reference fallback | Fewer abstractions, but larger handwritten migration/query/reactivity/correctness surface for AI maintenance. |
| Brick/offline-first adapters | Conditional challenger | Useful repository/queue/codegen primitives; current delete/realtime/adapter evidence does not close Kavriva recall semantics. |
| Supabase Realtime/cache only | Hint/baseline only | Useful online notification, not durable offline sync, conflict resolution, package verification or recall proof. |

No family is production-ready or purchased by this proposal.

## Why this direction fits the owner

- no separate sync-provider subscription is assumed at the start;
- only one app-owned local format and one Kavriva API contract are canonical for AI task packs;
- data download is explicitly bounded instead of inferred from table subscriptions;
- unresolved operations and conflicts remain visible and exportable;
- provider exit preserves app-owned package, operation and SQLite/JSON export contracts;
- the nontechnical owner is not expected to inspect queues, databases, logs or repair migrations.

The trade-off is real: more protocol meaning belongs to Kavriva. AI implementers must work through small contract-governed
tasks with independent review and machine-checkable fixtures; “custom” cannot mean undocumented code.

## Mandatory reversal triggers

The primary direction is reopened in favor of PowerSync or another retained candidate if:

1. the bounded delta/checkpoint and operation protocol cannot be represented as small, testable AI task contracts;
2. migration, transaction, process-death or restore behavior requires owner debugging;
3. selective data transfer cannot stay within approved package/data-use rules;
4. retry, duplicate, conflict, delete, recall or anti-resurrection semantics remain ambiguous;
5. encryption/key recovery cannot protect sensitive local data without unacceptable plugin/native risk;
6. maintenance cost exceeds a current priced PowerSync route after comparing service, exit and incident costs equally;
7. Android-first evidence works but the later iOS path cannot reproduce the same truth and recovery contract;
8. clean-room export/import cannot preserve pending operations, conflicts, tombstones and package generations.

PowerSync is rejected as an automatic fallback if its stream configuration, RLS equivalence, upload backend, billing,
outage handling or exit path cannot satisfy the same controls.

## Required no-code evidence before user decision

- one equal package/delta/state-machine dossier for Drift/custom and PowerSync;
- all 18 repository scenarios plus all 18 mobile-platform failure scenarios;
- equal P1/P2/P3, incident, restore and exit cost/data-usage worksheet;
- dependency, migration, encryption/key and Android/iOS maintenance map;
- AI task simulation for one interrupted compact package plus one conflicting offline user operation;
- two independent adversarial reviews and manager/Judge synthesis.

Until then this remains a proposal. It creates no code, database, account, subscription, provider purchase, ADR or gate
transition.
