# DEBATE-009 — Flutter offline/sync seçenek aileleri: primary research

**Durum:** Araştırma taslağı — Phase 4 / NO-CODE / karar yok / kazanan yok  
**Araştırma tarihi:** 2026-09-18 (Europe/Istanbul)  
**Kapsam:** Flutter + user-approved Supabase-centred backend/API boundary için yerel veri, bounded offline package, delta sync, durable operation ve provider-native Realtime/cache seçenekleri.  
**Yetki sınırı:** Bu belge provider hesabı açmaz, satın alma yapmaz, kod/prototip üretmez, package seçmez ve ADR/verdict oluşturmaz. “No winner” statüsü korunmuştur. Fiyatlar ve package sürümleri bu tarihte resmi sayfalarda görülen değerlerdir; dinamik olabilir.

## 1. Karar bağlamı ve değerlendirme kuralları

Bu araştırma aşağıdaki mevcut kararlarla sınırlıdır:

- DEC-0023: offline veri task-scoped ve data-efficient olmalı; seçili motorcycle/task/safe-core dışındaki tam kütüphane veya ilgisiz medya cihaza taşınmamalı; ağır medya on-demand olmalı.
- DEC-0024: risk-tiered bounded offline; exact release/client compatibility; critical unknown/stale durumda fail-closed; safe-stop/recovery closure; Internal Operations approve/publish/recall/role mutation için online authority.
- DEC-0029: AI-operated ve nontechnical product owner; deterministik araçlar, bounded context/change surface, otomatik doğrulama, gözlemlenebilirlik, dependency churn ve external-dependency yükü TCO'nun parçası.
- DEC-0034: canonical transactional authority/provider-neutral; Flutter/browser sensitive access server/API-mediated; versioned integrity-bound offline package; durable identified operations; idempotent submission; visible conflict/hold/unknown; high-consequence için silent last-write-wins yok; current state/history/protected audit ayrımı; restore/export/exit cross-plane manifest ve quarantine.
- DEC-0035: Supabase-centred managed backend working direction (PostgreSQL/Auth/private Storage candidate, server/API mediation, Edge Functions/equivalent low-ops API candidate); RLS/Storage defense-in-depth olup high-consequence authority'nin tek kanıtı değil; service_role server-only; offline protocol ve engine henüz seçilmedi.

Bu nedenle “yerel SQLite çalışıyor” veya “reconnect sonrası veri geliyor” tek başına güvenlik, geri çağırma, idempotency ya da authority kanıtı değildir.

### 1.1 Kanıt etiketleri

- **[CONFIRMED]** Resmi doküman, resmi repository, package maintainer metadata veya upstream primary kaynakta açıkça belirtilen mevcut davranış.
- **[INFERRED]** Bu primitive'lerden Kavriva için çıkan mimari sonuç; ADR ve test öncesi garanti değildir.
- **[OPEN]** Resmi kaynakta kesinleşmeyen, plan/konfigürasyon/ürün politikası veya kabul testine bağlı soru.

“Marketing claim” hiçbir yerde safety proof olarak kabul edilmemiştir. Ürün sayfasındaki “real-time”, “offline-first”, “consistent” gibi ifadeler capability sinyalidir; recall, restore, loss, duplicate, stale-session ve hostile-client testinin yerine geçmez.

## 2. Araştırma yöntemi ve güncel snapshot

### 2.1 Resmi/primary kaynak önceliği

Öncelik sırası: Supabase ve PowerSync resmi dokümanları/changelog/pricing; resmi GitHub repository ve maintainer tarafından yayımlanan package metadata; Brick resmi repository/package changelog/issues; Drift/sqflite resmi docs ve SQLite upstream. Üçüncü taraf benchmark, blog, forum ve topluluk iddiası karar kanıtı sayılmamıştır.

Supabase-özel talimat dosyası C:\Users\Xpike\.codex\skills\supabase\SKILL.md tamamen okunmuş; talimat gereği resmi [Supabase changelog](https://supabase.com/changelog.md) 2026-09-18 tarihinde breaking-change sinyalleri için taranmıştır. Changelog notları §12'de ayrıca tutulmuştur.

### 2.2 Sürüm/olgunluk gözlemi

- **Drift ailesi:** [drift](https://pub.dev/packages/drift) 2.35.0 (2026-09-09), [drift_flutter](https://pub.dev/packages/drift_flutter) 0.3.1 (2026-07-11), [sqlite3](https://pub.dev/packages/sqlite3) 3.6.0 (2026-09-13). [CONFIRMED] Active package/repository sinyali vardır; bu, Kavriva sync protokolünün güvenli olduğu anlamına gelmez.
- **sqflite:** [sqflite](https://pub.dev/packages/sqflite) 2.4.4 (2026-09-11 civarı yayımlanmış güncel package snapshot), Flutter Android/iOS/macOS; desktop için sqflite_common_ffi; web experimental. [CONFIRMED]
- **PowerSync:** [powersync](https://pub.dev/packages/powersync) 2.4.0 (2026-09-03 civarı), Flutter/Dart SDK Apache-2.0; web desteği resmi metadata'da hâlâ beta olarak anılır. [CONFIRMED]
- **PowerSync yardımcı katmanı:** [sqlite_async](https://pub.dev/packages/sqlite_async) 0.14.5 (2026-08-27); maintainer powersync.com. [CONFIRMED] Bu, ham SQLite alternatifi gibi görünse de maintainer/vendor coupling'i tamamen ortadan kaldırmaz.
- **Brick:** [brick_offline_first](https://pub.dev/packages/brick_offline_first/changelog) 4.0.2, [brick_offline_first_with_supabase](https://pub.dev/packages/brick_offline_first_with_supabase/versions) 2.1.0 (2025-07-08), [brick_supabase](https://pub.dev/packages/brick_supabase/versions) 2.1.1, [brick_sqlite](https://pub.dev/packages/brick_sqlite/versions) 4.1.0+1 (2025-11-11). [CONFIRMED] Current date'e göre son Supabase adapter yayımları 2025'te kalmıştır; unverified publisher metadata ve release-lag bakım riski olarak kaydedilmiştir, abandonment iddiası yapılmamıştır.

Bu tarihler “maturity score” değildir. Critical path için release cadence, SDK/Flutter compatibility, security fix SLA, migration/backfill behavior ve owner'ın sağlayıcı değişiminde neyi taşıyacağı ayrıca kabul edilmelidir.

## 3. Kısa karşılaştırma matrisi

| Aile | Yerel DB / migration / transaction | Delta ve selective sync | Write, conflict, idempotency | Şifreleme / background | Auth, recall/delete, provider coupling | Maliyet / exit / AI-operability ilk okuma |
|---|---|---|---|---|---|---|
| **A — Drift + Kavriva bounded package/delta + durable API** | [CONFIRMED] Drift reactive/type-safe SQLite; generated schema snapshots, tested migrations, transactions/savepoints. [INFERRED] Domain contract tamamen bizim işimiz. | [INFERRED] En dar task/package scope ve manifest/generation/tombstone modeli kurulabilir; hazır sync servisi yok. | [INFERRED] Durable operation API, idempotency key, conditional version ve explicit hold/unknown bizim sorumluluğumuz; silent LWW yok. | Drift encryption built-in değil; sqlite3mc/SQLCipher/key storage ayrıca. Background OS/isolate opportunistic. | Supabase Auth/API ile uyarlanır; recall/delete/tombstone/floor bizim protocol. Supabase schema/Storage/backup ve API coupling devam eder. | Sync vendor fee yok; engineering ve Supabase/network maliyeti yüksek. Exit/portability güçlü fakat custom protocol surface geniş ve AI guardrail ister. |
| **B — PowerSync + Supabase** | [CONFIRMED] Client SQLite, local writes atomik data + upload queue; Sync Streams client schema/view yaklaşımı. | [CONFIRMED] SQL-like Sync Streams ile on-demand/auto-subscribe partial sync; type mapping ve bucket/row limitleri vardır. | [CONFIRMED] FIFO upload queue, per-client operation id; backend idempotent ve conflict policy implement eder. Basit öneri per-field LWW; high-consequence policy built-in değildir. | Encryption option var ama key lifecycle app işi; WorkManager Android testli, iOS background sync OS/plugin sınırlı. | Supabase Auth JWT connector; Supabase RLS upload authority, streams yalnızca download filter. Recall/offline revocation ve tombstone semantics ayrıca test. PowerSync service/Mongo/license/provider coupling eklenir. | Cloud Free soft limits, Pro/Team usage billing; service/API/Supabase dahil değil. Self-host exit mümkün ama FSL service + Mongo/LB/replicator/backup operasyonu gerekir. Config yüzeyi azalır; distributed failure surface artar. |
| **C — Brick/offline-first + Supabase** | [CONFIRMED] Generated models/migrations/build_runner; brick_sqlite; local-first repository. [CONFIRMED] Queue/transaction primitive'leri vardır. | [INFERRED] Query ile fetch daraltılabilir; PowerSync düzeyinde server-side durable partial replication/stream contract kanıtı yok. Realtime optional. | [CONFIRMED] OfflineFirstWithRest request queue retry. [INFERRED] High-consequence conflict/idempotent command authority app/backend işidir; HTTP retry delta ledger değildir. | SQLite encryption built-in kanıtı yok; external SQLCipher. Background OS işi. | Supabase endpoint/Auth path coupling; Realtime filter gaps ve remote delete issue evidence var. Recall/delete, tombstone, stale queue ve session expiry app işi. | Service fee yok; MIT package ama generated code/provider adapter/churn surface geniş. Supabase exit devam eder. 2025 release-lag ve unverified publisher not edilir. |
| **D — raw sqflite / sqlite3 / sqlite_async** | [CONFIRMED] sqflite transaction/batch, version-on-open, native background thread; Drift/sqlite_async daha structured. | Sync yok; package/delta/outbox/reconcile tamamen Kavriva işi. | Sync semantics, idempotency, conflict, operation result tamamen Kavriva/API işi. | sqflite core encryption sağlamaz; SQLCipher fork veya sqlite3mc/SQLCipher; key storage ve platform integration owner işi. OS background opportunistic. | Auth/API/delete/recall/provenance custom; Supabase coupling yalnızca seçilen API seviyesinde. | Cloud sync fee yok, exit en sade; semantic code/test surface en geniş. AI için raw SQL ve migration drift riskli; deterministic tooling ile sınırlandırılmalı. |
| **E — Supabase Realtime/cache-only baseline** | [CONFIRMED] Realtime event channel/cache; persistent normalized local store ve migration/durable queue yok. SQLite cache yazılırsa A/D problemine geri dönülür. | [CONFIRMED] Broadcast/Postgres Changes event stream; reconnect gap/re-fetch gerekir. [INFERRED] Bounded package/durable delta değildir. | Offline write, ordered operation, dedupe ve conflict primitive yok; online API'nin ayrıca idempotent olması gerekir. | TLS/channel authorization; local cache encryption ve background OS işi. | RLS policy connection/JWT yenilemesinde değerlendirilir; JWT expiry disconnect eder. Missed event, recall/delete ve tombstone kendi API/re-fetch işimiz. Provider coupling düşük ek yüzeyde ama Supabase'e doğrudan bağlı. | Ek sync provider ücreti yok; Realtime connection/egress/DB usage vardır. Exit A/D custom protocol kadar zor olmayabilir ama event semantics'i yeniden kurmak gerekir. |

Bu tablo sıralama değildir. Her satır **candidate / evidence pending / ADR later** durumundadır.

## 4. Ortak güvenlik ve correctness contract'i

Seçenek ne olursa olsun aşağıdaki sözleşme olmadan offline capability kabul edilmemelidir.

### 4.1 Bounded package floor

[INFERRED] Her offline paket/manifest en az şu öğeleri taşımalıdır:

- user/tenant ve task scope;
- package id, schema version, policy/release version;
- base generation ve package generation;
- issued-at, expires-at, recall/revoke floor;
- content digest ve manifest digest;
- minimum client build / compatible provider contract;
- included entity class ve data classification;
- tombstone/delete/recall generation;
- optional media digest/size/on-demand policy;
- online revalidation requirement ve fail-closed reason.

Bu alanlar önerilen tasarım sınırıdır; herhangi bir adayın mevcut package formatı olarak sunulmamıştır. Offline package canonical authority değildir ve backup/restore sonrasında tek başına authority oluşturamaz.

### 4.2 Durable operation floor

[INFERRED] Yüksek sonuçlu write için local transaction, durable outbox ve server operation record aynı mantıksal işlem akışında olmalıdır:

- stable operation id ve actor/session/device id;
- command/resource id ve base version/generation;
- client timestamp yalnızca gözlem; server acceptance order authority;
- payload/content digest ve idempotency scope;
- auth/policy context;
- accepted / rejected / held / unknown / duplicate sonucu;
- retry sırasında aynı operation id ile safe replay;
- timeout sonrası “unknown” state; başarı varsayımı yok;
- conflict görünür ve review/hold'a gider; silent LWW veya silent drop yok;
- accepted operation protected audit/history'den kaybolmaz.

PowerSync veya Brick queue'su bu contract'in bazı taşıyıcı parçalarını sağlayabilir; canonical high-consequence semantics'in tamamını kendiliğinden sağlamaz.

### 4.3 Recall, delete ve session floor

- Online revoke/recall, gelecekte yeni package üretimini durdurmalı; mevcut online client revalidate etmelidir.
- Offline client için maximum exposure window, package expiry ve critical action block net olmalıdır.
- Delete yalnızca current row silmek değil; delta/tombstone, cache, local package, media, queue, backup/export ve restore floor'larını kapsar.
- “Event geldi” veya “row yok” gözlemi, old package/late operation yeniden yazamaz kanıtı değildir.
- Auth sign-out, role change, password/session termination ve device loss sonrasında local user partition, token, queue ve cached media için policy açık olmalıdır.

### 4.4 Background ve encryption floor

Background execution OS scheduling'dir; Android/iOS task'ın tam zamanında çalışacağı veya uygulama kapatıldıktan sonra recall'ı uygulayacağı varsayılamaz. Correctness, foreground reconnect ve next-authorized-request revalidation ile de sağlanmalıdır.

SQLite encryption at rest, cihaz/backup/debug/root/jailbreak/exfiltration risklerinin tamamını çözmez. Key provisioning, rotation, deletion, secure storage, backup exclusion ve crash/log redaction ayrıca kanıtlanmalıdır.

## 5. A — App-owned SQLite/Drift + Kavriva bounded package/delta + durable operation API

### 5.1 Yerel DB maturity

- **[CONFIRMED]** Drift reactive/type-safe SQLite wrapper ve code generator sağlar: [Drift repository](https://github.com/simolus3/drift), [Drift API overview](https://drift.simonbinder.eu/).
- **[CONFIRMED]** Drift migration docs schema snapshot, generated step-by-step migration ve migration test önerir; make-migrations ve schema history, manual migration hatalarını azaltır: [Drift migrations](https://drift.simonbinder.eu/migrations/).
- **[CONFIRMED]** Drift transactions birden fazla statement'ı atomic yapar, nested transactions/savepoints destekler; transaction içindeki tüm Future'ların await edilmesi gerekir: [Drift transactions](https://drift.simonbinder.eu/dart_api/transactions/).
- **[CONFIRMED]** Native platformlarda database'i background isolate'ta açma yolu vardır (NativeDatabase.createInBackground); WAL/read-pool concurrency seçeneği database lock ve lifecycle testleri ister: [Drift native platforms](https://drift.simonbinder.eu/platforms/vm/).
- **[CONFIRMED]** Web Wasm/worker/OPFS veya IndexedDB path'leri mobil SQLite ile aynı değildir; Safari/Android Chrome tab race, COOP/COEP header ve wasm MIME gibi deployment koşulları vardır: [Drift web](https://drift.simonbinder.eu/platforms/web/).

Drift bu family'de local projection, package table, tombstone table ve outbox için deterministik bir schema/migration omurgası verir. **[INFERRED]** Sync protocol, authority, delta cursor, package issuance, rebase ve recall floor Drift'in özelliği değildir.

### 5.2 Transaction, migration ve encryption sınırı

- **[CONFIRMED]** Drift'in kendisi encryption engine değildir. sqlite3mc/SQLite3MultipleCiphers veya SQLCipher gibi native/web seçeneği ayrıca bağlanmalıdır: [Drift encryption](https://drift.simonbinder.eu/platforms/encryption/).
- **[CONFIRMED]** Encryption key uygulama secure storage/key lifecycle'ına bırakılır; key rotation, existing DB rekey/copy, PRAGMA doğrulaması ve platform binary packaging test ister.
- **[INFERRED]** Key cihazdan silinse bile server backup, OS backup, crash dump, exported package veya screenshot üzerinden disclosure kapanmış sayılmaz. Data classification package manifestinde encryption requirement olarak taşınmalıdır.
- **[OPEN]** Kavriva için Android-first local encryption path olarak SQLite3MultipleCiphers, SQLCipher veya platform keystore + per-user key arasında karar verilmemiştir. iOS/Android restore, reinstall, key loss ve app upgrade testleri gerekir.

### 5.3 Custom bounded package ve delta şekli

Drift üzerindeki domain tasarımında minimum conceptual flow:

1. Online API, task scope ve user policy'ye göre package manifest + rows + tombstones + digest üretir.
2. Client package'i geçici staging transaction'ında doğrular; schema/release/policy/digest/expiry/recall floor uyumsuzsa quarantine eder.
3. Accepted package current projection'a atomik olarak alınır; outbox ve local package generation aynı transaction boundary'sinde güncellenir.
4. Pull cursor/generation yalnızca doğrulanmış delta transaction'ı tamamlandıktan sonra ilerler.
5. Deletion/recall satır silmekle kalmaz; tombstone ve generation floor bırakır.
6. Cursor gap, checksum mismatch, old client veya unknown generation'da incremental apply yerine full bounded reissue/quarantine yapılır.

Bu, yapılması gereken contract'in bir araştırma şemasıdır; mevcut uygulama kodu değildir. **[INFERRED]** A family'si task-specific data minimization, explicit fail-closed ve provider exit üzerinde en fazla kontrolü verebilir; bunun karşılığı sync correctness, API, test ve observability surface'ini owner'ın taşımasıdır.

### 5.4 Write ve conflict semantics

- Local mutation, domain row + durable outbox append'ini tek local transaction'da yapabilir.
- API command, stable operation id + base generation + conditional write taşır.
- Server result accepted, rejected, held, unknown veya duplicate olabilir; timeout sonrası client accepted varsayamaz.
- High-consequence field için server transaction/constraint ve domain state machine kullanılır; LWW yalnızca düşük riskli cosmetic field'lerde açıkça izin verilirse kullanılabilir.
- Concurrent accepted operations history/protected audit'e yazılmalı; conflict client'a visible hold/review olarak dönmelidir.

**[OPEN]** API'nin Supabase Edge Function/equivalent mi, bağımsız thin API mi olacağı DEC-0035'te adaydır; bu seçim operation API'nin idempotency store, auth verification, audit ve rate-limit yüzeyini değiştirir.

### 5.5 Selective sync, data usage ve recall/delete

- **[INFERRED]** Package manifest task/unit/role/generation bazında yalnızca gereken satırları ve gerekirse thumbnail/metadata'yı taşıyabilir; full-library replication zorunlu değildir.
- Heavy media package dışında tutulup signed/on-demand ve digest-bound yapılabilir. Supabase Storage DB backup kapsamına girmediği için object manifest ve independent export/restore floor ayrıca gerekir: [Supabase backups](https://supabase.com/docs/guides/platform/backups).
- Recall event kaçırılırsa, next online package refresh veya high-consequence action revalidation old package'i durdurmalıdır. Realtime yalnızca hint/latency accelerator olabilir; authority re-check yerine geçmez.
- Local DELETE veya DB vacuum, server tombstone/old operation prevention olmadan resurrection riskini kapatmaz.

### 5.6 Auth/session and background

- **[CONFIRMED]** Supabase access token'ları genellikle 5 dakika–1 saat kısa ömürlü; refresh token tek kullanımlı rotation modelindedir; default session indefinite olabilir: [Supabase user sessions](https://supabase.com/docs/guides/auth/sessions).
- **[INFERRED]** Local outbox, token expire/sign-out sırasında silent retry yapmamalı; token refresh başarısızsa operation auth-held state'e alınmalı. User/tenant partition ve logout cleanup açık olmalıdır.
- **[CONFIRMED]** OS background/isolate, sync correctness için kesin zamanlama sağlamaz. Foreground open, push hint ve scheduled worker yalnızca latency optimizasyonu kabul edilmelidir.

### 5.7 Cost, exit ve AI-operability

- **[CONFIRMED]** Drift/sqflite/SQLite için ayrı managed sync service ücreti yoktur; Supabase DB/Auth/Storage/API/network usage maliyeti devam eder.
- **[INFERRED]** Sync vendor lock-in'i düşüktür: package/delta/operation records PostgreSQL ve portable SQLite/JSON manifest olarak export edilebilir. Ancak custom protocol ve runbook'ları yeniden yazma maliyeti gerçek exit maliyetidir.
- **[CONFIRMED]** Supabase spend cap bütün usage kalemlerini kapsayan evrensel hard cap değildir; compute, PITR, storage/egress/object ve vendor fiyat satırları ayrıca kontrol edilmelidir: [Supabase cost control](https://supabase.com/docs/guides/platform/cost-control).
- AI-operability açısından migration snapshots, machine-readable manifest, schema diff, deterministic fixtures ve invariant tests zorunlu olmalıdır. Raw sync code “AI halleder” varsayımı ile bırakılırsa en geniş hidden state bu family'de oluşur.

### 5.8 A-specific hold/gates

1. Package manifest, tombstone/recall floor ve cursor-gap behavior yazılı spec olarak review edilmeden A candidate sayılır.
2. Duplicate timeout, retry, process kill, clock skew, stale client, old package ve restore-quarantine fixture'ları geçmeden operation API sayılmaz.
3. Supabase session expiry/sign-out/role revoke/device loss testleri local queue ve media cleanup ile kapanmadan auth-safe değildir.
4. SQLCipher/SQLite3MC seçimi, key loss/rotation/backup/upgrade matrix'i ve iOS+Android binary check olmadan encrypted olarak işaretlenmez.

## 6. B — PowerSync with Supabase

### 6.1 Capability ve boundary

- **[CONFIRMED]** PowerSync Flutter SDK client-side SQLite oluşturur; local reads/writes offline çalışır ve reactive watch API sunar: [Dart/Flutter SDK](https://docs.powersync.com/client-sdks/reference/flutter), [package metadata](https://pub.dev/packages/powersync).
- **[CONFIRMED]** Supabase integration, PowerSync'in Supabase'e invasive schema/write permission zorunluluğu olmadan seçilmiş datayı local SQLite'a stream ettiğini; client write'larının upload queue'ya girdiğini; custom backend conflict logic'in owner'a ait olduğunu anlatır: [Supabase integration](https://supabase.com/partners/integrations/powersync).
- **[CONFIRMED]** Supabase Auth JWT doğrulama ve legacy HS256/new RS256 JWKS modelleri desteklenir; self-host configuration'da JWKS/manual setup gerekir: [PowerSync Supabase Auth](https://docs.powersync.com/configuration/auth/supabase-auth).

Bu, A'daki raw delta stream/outbox mekanizmasının bir bölümünü ürünleştirir; Supabase canonical authority, high-consequence API ve recall policy'sini otomatik devraldığı anlamına gelmez.

### 6.2 Sync Streams, selective sync ve schema coupling

- **[CONFIRMED]** Sync Streams SQL-like query ile partial sync, user/auth/subscription parameter ve on-demand veya auto_subscribe modeli verir: [Sync Streams overview](https://docs.powersync.com/sync/streams/overview).
- **[CONFIRMED]** Default auto-subscribe false ve unsubscribe sonrası TTL default 24 saat olarak belgelenir; stream subscription task scope için data volume'ünü sınırlayabilir.
- **[CONFIRMED]** Synced table'larda id text primary key, SQLite type mapping (text/integer/real) ve bucket/user limitleri vardır; default bucket limit ve higher-limit request sınırı belgelenmiştir: [performance and limits](https://docs.powersync.com/resources/performance-and-limits), [type mapping](https://docs.powersync.com/sync/streams/type-mapping).
- **[CONFIRMED]** Protocol schemaless/client schema local SQLite view yaklaşımı kullanır; synced schema için normal client migration gerekmeyebilir. Raw tables veya uygulama-owned tables yine migration ister: [implementing schema changes](https://docs.powersync.com/maintenance-ops/implementing-schema-changes).
- **[INFERRED]** Stream definition, source Postgres schema, casts, column names, row filters ve app release arasında provider coupling vardır. Rename/type change için additive dual mapping/versioned stream/backfill/old-client support planlanmalıdır: [deploying schema changes](https://docs.powersync.com/maintenance-ops/deploying-schema-changes).

Selective sync burada güçlü bir capability'dir; **[OPEN]** Kavriva'nın package generation/recall floor, maximum exposure window ve role-aware stream filter'ını current PowerSync stream semantics ile bire bir nasıl bağlayacağı kabul testidir.

### 6.3 Local writes, queue, idempotency ve conflict

- **[CONFIRMED]** Local write, data table değişimini ve ps_crud upload queue kaydını atomik yapar. uploadData() connection/reconnect/keepalive/retry ile çağrılır; queue sırayla drain edilir: [client-side integration](https://docs.powersync.com/configuration/app-backend/client-side-integration).
- **[CONFIRMED]** Upload backend operation'ları PUT/PATCH/DELETE formatında karşılar; operation must be idempotent ve per-client incrementing operation id deduplication için kullanılabilir: [writing client changes](https://docs.powersync.com/handling-writes/writing-client-changes), [handling update conflicts](https://docs.powersync.com/handling-writes/handling-update-conflicts).
- **[CONFIRMED]** PowerSync backend conflict konusunda “unopinionated”dir; basit backend davranışı per-field LWW olabilir, fakat backend custom policy uygulamalıdır. Docs deletes-win ve server-received-last örneklerini öneri olarak verir; high-consequence authority değildir.
- **[CONFIRMED]** Queue'da hata atan upload aynı operation'ı tekrarlar ve ilerlemeyi bloklayabilir; validation/conflict için backend'in 2xx dönüp response body veya ayrı synced error table ile sonucu görünür kılması önerilir: [write validation errors](https://docs.powersync.com/handling-writes/handling-write-validation-errors).
- **[CONFIRMED]** Causal consistency/checkpoint ilerlemesi upload queue empty ve stream state koşullarıyla ilişkilidir: [consistency](https://docs.powersync.com/architecture/consistency).

**Kavriva yorumu:** PowerSync FIFO/idempotent transport değerlidir; ancak accepted/held/unknown/protected audit, high-consequence transition ve server-side command semantics ayrıca yazılmalıdır. 2xx “handled” sinyali accepted authority ile karıştırılmamalıdır.

### 6.4 Supabase RLS, auth/session and recall

- **[CONFIRMED]** Supabase RLS upload CRUD için authoritative protection olarak kullanılır; Sync Streams yalnızca download filtering'dir ve uploads'ı korumaz. Stream filters RLS ile mirror edilmelidir: [RLS and Sync Streams](https://docs.powersync.com/integrations/supabase/rls-and-sync-streams).
- **[INFERRED]** RLS policy değişikliği, stream re-evaluation, cached JWT ve subscription lifecycle aynı anda yönetilmezse former role/user data local'de exposure window boyunca kalabilir.
- **[CONFIRMED]** fetchCredentials() token'ı ilk bağlantıda ve expiry yaklaşınca çağrılır; docs kısa-lived token (ör. 5–15 veya 30–60 dakika) ve offline token expiry sonrası connectivity'de refresh önerir: [PowerSync client-side integration](https://docs.powersync.com/configuration/app-backend/client-side-integration).
- **[INFERRED]** Supabase sign-out/role revoke/refresh-token reuse failure durumunda PowerSync local DB, upload queue ve stream subscription otomatik olarak Kavriva retention/recall contract'ini sağlamış sayılmaz; sign-out/partition wipe/hold policy test edilmelidir.
- **[OPEN]** Supabase source delete veya recall event'inin tüm ilgili bucket/stream ve old client'lara tombstone olarak hangi koşulda ulaşacağı; stream deletion/reprocess, reconnect gap ve late upload against deleted ID fixture'larıyla doğrulanmalıdır. “Source row silindi” ile “ciktaki bütün kopyalar silindi ve yeniden oluşamaz” eşit değildir.

### 6.5 Encryption and background execution

- **[CONFIRMED]** TLS in transit vardır; Flutter at-rest için SQLite3MultipleCiphers veya SQLCipher community option'ı docs'ta açıklanır. Key secure storage ve upgrade setup app sahibine aittir: [PowerSync data encryption](https://docs.powersync.com/client-sdks/advanced/data-encryption).
- **[CONFIRMED]** Background syncing Flutter'da workmanager ile test edilmiştir; Android beklenen şekilde çalışırken docs'taki iOS test notları partial/failed fetch riskini ve plugin/OS dependency'sini gösterir: [background syncing](https://docs.powersync.com/client-sdks/advanced/background-syncing).
- **[INFERRED]** Background sync “recall guaranteed” veya “fresh by deadline” proof değildir; app foreground/action revalidation ve expiry floor'a dayanmalıdır.
- **[OPEN]** PowerSync encrypted local DB + Supabase Auth secure storage + device backup exclusion matrix'i iOS later hedefi için ayrıca tamamlanmalıdır.

### 6.6 Pricing, hard-cap, self-host ve exit

**[CONFIRMED]** 2026-09-18 resmi pricing snapshot:

- Free: $0/month; 2 GB data synced/month, 500 MB hosted, 50 peak concurrent clients, 2 service instances, instance başına 1 source DB connection; free project 1 hafta inactivity sonrası deactivate olur.
- Pro: $49/month'tan; 30 GB synced/month dahil, 10 GB hosted, 1,000 peak client; synced/hosted overage ve peak client/instance satırları usage-based.
- Team: $599/month'tan; version locking, custom write checkpoints, customer-provided bucket storage DB, private endpoints/SLAs gibi ekler.
- Enterprise: custom.

Güncel değerler [PowerSync pricing](https://powersync.com/pricing) sayfasında görünür. Free plan “soft limits” olarak tanımlanır; bu, universal hard kill-switch veya fatura tavanı değildir. Supabase/API/DB/egress maliyetleri bu rakamlara dahil değildir.

**[CONFIRMED]** Self-host deployment docs Mongo replica set, replication service, API containers, load balancer, compaction, backups ve observability yükünü gösterir: [self-host overview](https://docs.powersync.com/maintenance-ops/self-hosting/overview), [deployment architecture](https://docs.powersync.com/maintenance-ops/self-hosting/deployment-architecture).

**[CONFIRMED]** Client SDK Apache-2.0; PowerSync service source/open edition için license terms FSL/source-available modelini açıklar; service'in permissive OSS olduğu varsayılmamalıdır: [Dart repository](https://github.com/powersync-ja/powersync.dart), [service repository](https://github.com/powersync-ja/powersync-service), [licensing terms](https://powersync.com/legal/licensing-terms).

**[INFERRED]** Self-host bir exit path'tir; fakat gerçek exit yalnızca client package'ini başka SQLite'a taşımak değildir. Mongo bucket state, replicator config, stream definitions, upload API, JWT/JWKS, source Postgres and historical conflict records için restore/rebuild drill gerekir. Cloud → self-host veya provider değişimi planı yazılmadan “portable” iddiası safety proof değildir.

### 6.7 AI-operability and B-specific hold

PowerSync docs ve package surface, A'ya göre transport/partial sync kodunu azaltabilir; buna karşılık source schema, stream DSL, auth connector, upload backend, Supabase RLS, bucket state, service version ve billing dashboard olmak üzere daha fazla operational surface oluşturur. Docs'taki AI tools linki capability'dir; owner'ın doğru stream/security policy yazacağına dair proof değildir.

Hold gates:

1. Supabase RLS matrix ile Sync Stream matrix otomatik karşılaştırılmadan role/tenant isolation tamam sayılmaz.
2. Duplicate timeout, FIFO blocked queue, validation 2xx, dead-letter, concurrent delete/update, late operation ve reconnect gap fixture'ları geçmeden high-consequence write yoktur.
3. Recall/delete tombstone, stream reprocess, local wipe, old-client quarantine ve offline expiry drill geçmeden bounded offline kabul edilmez.
4. Pricing soft limits, deactivation, egress and service outage için alert + fail-closed runbook olmadan cost-safe sayılamaz.
5. Self-host restore/rebuild + license review yapılmadan exit-ready sayılamaz.

## 7. C — Brick/offline-first style libraries

### 7.1 Current package ve architecture

- **[CONFIRMED]** Brick resmi repository offline-first repository pattern, local provider-first reads ve generated models/migrations/build_runner kullanır: [Brick repository](https://github.com/GetDutchie/brick).
- **[CONFIRMED]** Supabase adapter, Supabase'in PostgREST tabanlı ince bir wrapper'ı olarak OfflineFirstWithRest request queue yaklaşımını kullanır: [brick_offline_first_with_supabase README](https://github.com/GetDutchie/brick/blob/main/packages/brick_offline_first_with_supabase/README.md).
- **[CONFIRMED]** brick_sqlite migration support ve generated schema surface sağlar; brick_offline_first changelog 4.0 breaking changes, queue/policy updates ve 4.0.2 fixes içerir: [brick offline-first changelog](https://pub.dev/packages/brick_offline_first/changelog), [brick_sqlite changelog](https://pub.dev/packages/brick_sqlite/changelog).

### 7.2 Queue, local transaction ve selective sync

- **[CONFIRMED]** Brick local-first repository local provider'ı önce okur; remote request sonra yapılır; client queue endpoint request'lerini retry/queue edebilir.
- **[CONFIRMED]** Supabase adapter queue default olarak /auth/v1 ve /storage/v1 endpoint'lerini ignore eder; endpoint path değişimi veya custom API için queue config ayrıca ayarlanır: [adapter README](https://github.com/GetDutchie/brick/blob/main/packages/brick_offline_first_with_supabase/README.md).
- **[INFERRED]** Bu queue transport-level HTTP retry/cache behavior'dır; PowerSync-style bidirectional durable delta ledger, causal checkpoint, selective server stream ve conflict authority olarak okunamaz.
- **[INFERRED]** Brick Query/provider filters ile initial/fresh fetch scope'u daraltabilir; ancak PowerSync Sync Streams gibi server-maintained partial replication contract'i resmi docs'ta görülmemiştir. App, Realtime subscription ve re-fetch policy'sini kendisi bağlar.
- **[CONFIRMED]** Realtime subscription support vardır; complex/nested/unsupported filters ignored olursa daha geniş subscription ve ardından local filtering riski README'de belirtilir. Realtime, local subscribe() ile karıştırılmamalıdır.

### 7.3 Conflict, idempotency, remote delete ve recall

- **[INFERRED]** Brick queue retry duplicate HTTP request üretebilir; endpoint idempotency key/conditional version/command result contract'i backend'in sorumluluğudur.
- **[INFERRED]** Built-in high-consequence conflict policy, protected accepted-operation ledger, visible unknown/hold veya no-silent-LWW proof'u yoktur. Provider/app policy explicit yazılmalıdır.
- **[OBSERVED RISK]** Resmi repository issue [#451](https://github.com/GetDutchie/brick/issues/451)'de remote Supabase delete'in cihazdaki local row'u kaldırmaması raporlanmıştır; issue kapanmış olsa da bu, Brick adapter'ın Kavriva recall/delete semantics'ini otomatik kanıtlamadığını gösterir. Bu tek issue genel bug rate veya abandonment proof'u değildir.
- **[OBSERVED RISK]** Reactive remote change discussion [#448](https://github.com/GetDutchie/brick/issues/448) explicit subscription/re-fetch ihtiyacını gösterir. Realtime event, durable tombstone/anti-resurrection floor değildir.
- **[OPEN]** Brick Realtime adapter'ın 2026 current release, filter conversion ve delete behavior'ı için Kavriva fixture'ları gerekir; local row'ın görünmez olması ile server delete authority'sinin kanıtı ayrılmalıdır.

### 7.4 Migration, encryption, background ve auth

- **[CONFIRMED]** Generated code/migration/build_runner deterministic tooling sağlar fakat model, adapter, generated file ve schema migration birden fazla package version'a bağlıdır.
- **[OPEN]** Brick SQLite path için built-in encryption guarantee bulunamadı; SQLCipher/sqflite fork veya encryption-capable SQLite ayrıca seçilmelidir. Key lifecycle package tarafından otomatik çözüldü varsayılmaz.
- **[INFERRED]** Queue app kapalıyken OS background scheduler'a ve next token'a bağlıdır; Supabase session expiry queue retry'nin trusted success olduğu anlamına gelmez.
- **[INFERRED]** Supabase /auth/v1 ve /storage/v1 queue exclusion, auth refresh ve private object handling için iyi default olabilir; fakat custom API endpoint, token rotation ve object manifest için explicit adapter test gerekir.

### 7.5 Maintenance, AI-operability, cost and exit

- **[CONFIRMED]** Brick package'leri MIT lisanslı görünür; sync service usage fee yoktur. Supabase/API/network/Storage cost yine vardır.
- **[CONFIRMED]** Current package snapshot'ın Supabase adapter'ı 2025-07, SQLite package'ı 2025-11 release'lerine dayanır; publisher metadata bazı package'lerde unverified'dir.
- **[INFERRED]** Codegen, generator, provider adapter, Realtime mapping ve queue policy AI-operated change surface'ini büyütür. Generated diff, lockfile, migration snapshot ve Flutter upgrade fixture'ı şarttır.
- **[INFERRED]** MIT/source exit güçlü görünür; ancak app data model, generated adapter ve Supabase/PostgREST/Realtime semantics'i doğrudan taşımak gerekir. Queue records ve unresolved conflicts export manifestine dahil edilmelidir.

### 7.6 C-specific hold

Brick ancak aşağıdaki kanıtlar tamamlanırsa bounded offline candidate olarak tutulabilir:

1. Remote delete/recall, tombstone, reconnect gap, old-client package ve late queue operation fixture'ları.
2. Supabase session expiry/sign-out/role change sonrası queue behavior ve local wipe.
3. Unsupported Realtime filter'in geniş subscription yapmadığını veya data classification sınırının bunu tolere ettiğini gösteren test.
4. SQLCipher/encryption path, migration rollback/upgrade ve generator compatibility.
5. 2025 adapter release'lerinin current Flutter/Dart/Supabase SDK ile maintenance owner'ı ve security response yolu.

## 8. D — Raw sqflite ve diğer Flutter local DB alternatifleri

### 8.1 sqflite

- **[CONFIRMED]** sqflite 2.4.4 Flutter SQLite plugin'dir; iOS/Android/macOS, transaction/batch, open sırasında basic version migration ve iOS/Android background DB thread destekler: [sqflite package](https://pub.dev/packages/sqflite).
- **[CONFIRMED]** Linux/Windows için sqflite_common_ffi, web için experimental implementation vardır. Platform matrix Flutter/iOS later target'ında ayrı test ister.
- **[CONFIRMED]** README current issues, concurrent read/write transaction'ın desteklenmediğini; calls serialized ve transactions exclusive olduğunu belirtir. Bu, local DB maturity eksikliği değil, throughput/locking constraint'idir.
- **[CONFIRMED]** Transaction callback error throw ederse rollback; batch helper ve onCreate/onUpgrade version lifecycle vardır.

sqflite, A'daki DB primitive'lerini daha düşük abstraction ile verir; sync, bounded package, tombstone, idempotency, auth, conflict ve selective delta sağlamaz. **[INFERRED]** Code surface azaltılırken domain correctness surface artar.

### 8.2 Encryption alternatifleri

- **[CONFIRMED]** sqflite core encryption sağlamaz; resmi README encryption notes'a yönlendirir. [SQLCipher fork](https://pub.dev/packages/sqflite_sqlcipher) 3.4.1, iOS/Android SQLCipher 4.x native implementation, password parameter ve platform-specific ProGuard/dependency override gerektirir.
- **[CONFIRMED]** sqflite_sqlcipher package publisher metadata unverified'dir; iOS'ta FMDB/SQLCipher pod çakışması ve Android migration asymmetry'si README'de görülebilir.
- **[CONFIRMED]** Drift path'i için sqlite3mc/SQLCipher seçilebilir; bu, local DB encryption primitive'idir, key management/secure deletion/recovery proof değildir.

### 8.3 sqlite3 ve sqlite_async

- **[CONFIRMED]** Upstream SQLite transaction/WAL, one-writer concurrency ve checkpoint semantics tanımlar: [SQLite WAL](https://www.sqlite.org/wal.html). WAL network filesystem için değildir; birden çok reader olsa da tek writer vardır.
- **[CONFIRMED]** SQLite Session extension changeset/patchset/diff/apply API'leri içerir: [SQLite Session](https://www.sqlite.org/session.html). Flutter package'de kullanılabilmesi, server protocol, schema compatibility, conflict policy veya encryption'ı otomatik çözmez.
- **[CONFIRMED]** sqlite_async async DB calls, watches, concurrent read/write/WAL ve migration utilities sunar; web desteği beta; package maintainer powersync.com: [sqlite_async](https://pub.dev/packages/sqlite_async).
- **[INFERRED]** sqlite_async background/read concurrency'yi iyileştirir fakat PowerSync service olmadan A/D'nin custom sync surface'ini ortadan kaldırmaz; maintainer coupling'i procurement/exit review'e yazılmalıdır.

### 8.4 Background, data usage, auth ve exit

- Background task WorkManager/BGTaskScheduler/OS lifecycle'a bağlıdır; raw DB'nin background thread'de çalışması network sync'ın zamanında olacağı anlamına gelmez.
- Selective data, object/media lifecycle, package expiry, recall/delete ve operation API tamamen Kavriva protocol'üdür.
- Supabase Auth access/refresh token rotation, local queue partition ve secure storage yine app/API responsibility'dir.
- Cloud sync provider eklenmediği için exit ve fatura yüzeyi sadedir; buna karşılık API, delta, conflict, observability, incident runbook ve migration tests'in tamamı owner'a kalır.

### 8.5 D-specific hold

Raw sqflite/sqlite3 ancak “minimum dependency” ile “minimum correctness burden” ayrıldığı zaman candidate'dir. Aşağıdakiler yoksa raw DB seçimi basitlik değil, görünmeyen risk transferidir:

1. Schema snapshots/migration tests ve old-client compatibility.
2. Atomic local row + outbox + package cursor transaction.
3. Idempotent durable API, unknown/hold state ve conflict audit.
4. Tombstone/recall floor, local wipe ve restore quarantine.
5. Encryption key, platform upgrade, backup/restore ve iOS later matrix.

## 9. E — Provider-native Supabase Realtime / cache-only baseline

### 9.1 Realtime primitive'leri

- **[CONFIRMED]** Supabase database changes için Broadcast (scalability/security recommended) ve Postgres Changes (simpler, less scalable) seçenekleri sunar: [subscribing to database changes](https://supabase.com/docs/guides/realtime/subscribing-to-database-changes).
- **[CONFIRMED]** Broadcast row change trigger ile private channel'a event gönderebilir; channel receive/send authorization realtime.messages RLS ile kontrol edilir: [Realtime authorization](https://supabase.com/docs/guides/realtime/authorization).
- **[CONFIRMED]** Postgres Changes'te RLS izin verdiği satırlar gönderilir; UPDATE/DELETE old row values için Dart docs'ta REPLICA IDENTITY FULL ihtiyacı belirtilir: [Dart subscribe](https://supabase.com/docs/reference/dart/subscribe).
- **[CONFIRMED]** Realtime realtime schema'sı 2026-07'de create/alter/drop'e kilitlenmiştir; realtime.messages RLS policy yönetimi izinlidir. Bu, internal schema'ya custom table/function ekleme varsayımını kapatır: [Realtime authorization](https://supabase.com/docs/guides/realtime/authorization).
- **[CONFIRMED]** Broadcast mesajları realtime.messages içinde 3 gün retention sonrası partition cleanup ile tutulur: [Realtime architecture](https://supabase.com/docs/guides/realtime/architecture).

### 9.2 Neden cache-only bounded sync değildir

- WebSocket bağlantısı koparsa client event'i kaçırabilir; reconnect sonrası full re-fetch veya durable cursor gerekir.
- Server-side 3-day message retention, client task package generation, tombstone floor veya accepted operation ledger değildir.
- Cache memory veya local SQLite'ta tutulursa migration/encryption/eviction/recall problemi A/D'ye geri döner; yalnızca on callback data'yı canonical authority yapmaz.
- Realtime channel filter'i high-consequence authorization, task package manifest, expiry veya selective media classification yerine geçmez.
- Realtime event, idempotent write API, ordered durable operation, conflict hold veya unknown result sağlamaz. Online mutation için ayrı API/DB transaction gerekir.

### 9.3 Auth/session ve policy cache

- **[CONFIRMED]** Realtime channel RLS policy connection/join sırasında değerlendirilir; policy cache connection boyunca kullanılır. Yeni JWT gönderilirse policy cache update olur; JWT expiry öncesi yeni JWT gelmezse client disconnect olur: [Realtime authorization](https://supabase.com/docs/guides/realtime/authorization).
- **[INFERRED]** Role revoke/recall için existing connection, offline client ve missed event behavior ayrıca revalidate edilmelidir; channel disconnect'in local cache wipe veya queued write cancellation olduğu varsayılmaz.
- Supabase Auth default indefinite session ve refresh token rotation nedeniyle cache-only baseline bile sign-out/expiry/secure storage policy'siz güvenli değildir: [user sessions](https://supabase.com/docs/guides/auth/sessions).

### 9.4 Maliyet, exit ve baseline kullanım alanı

- **[CONFIRMED]** Ek sync provider ücreti yoktur; Realtime connection, DB connection, egress, Broadcast/Postgres Changes usage ve Supabase plan limitleri devam eder.
- **[INFERRED]** Exit surface B'ye göre daha azdır; fakat production sync ihtiyaçları çıktığında A/D custom package/API yine inşa edilir. Baseline'ı “read-only online hint/cache + mandatory re-fetch” olarak sınırlamak daha açık bir contract'tir.
- **[OPEN]** E'nin Kavriva'da yalnızca low-risk read freshness hint'i olarak mı, yoksa durable local task data olarak mı kullanılacağı karar aşamasında cevaplanmalıdır. İkinci durum E değil, A/D sınıfına girer.

### 9.5 E-specific hold

E ancak:

1. Read-only/low-risk hint kapsamı;
2. reconnect full re-fetch;
3. missed event/delete/revoke handling;
4. no offline high-consequence write;
5. session expiry and private channel policy

yazılı ve testli ise baseline olarak tutulabilir. “Realtime active” tek başına offline sync kabul edilmez.

## 10. Gereksinim bazında karşılaştırma

| Gereksinim | A — Drift/custom | B — PowerSync | C — Brick | D — raw local DB | E — Realtime/cache |
|---|---|---|---|---|---|
| Task-scoped selective data | [INFERRED] Package protocol ile tam kontrol | [CONFIRMED] Sync Streams güçlü; stream/RLS mirror gerekir | [INFERRED] Query/fetch; durable partial stream proof eksik | [INFERRED] Tamamen custom | [INFERRED] Channel/filter yalnızca hint; re-fetch gerekir |
| Local transaction + durable local operation | Custom outbox + DB transaction | [CONFIRMED] Data + upload queue atomik | [CONFIRMED] HTTP queue; semantic operation record custom | Custom | Yok |
| Duplicate/timeout/idempotency | Custom explicit | [CONFIRMED] operation id + backend idempotency required | HTTP queue retry; backend custom | Custom | API custom |
| High-consequence conflict | Explicit hold/command policy possible | Backend owner; LWW simplest default | App/backend custom | Custom | Offline conflict yok; online API custom |
| Server delta/checkpoint | Custom | [CONFIRMED] Sync Streams/checkpoint | Re-fetch/Realtime; full protocol proof yok | Custom | Ephemeral events |
| Recall/delete anti-resurrection | Tombstone/generation custom | Stream/delete plus Kavriva floor custom | Risk; issue evidence; custom | Custom | Missed event risk |
| Auth expiry/session revoke | API/session integration custom | Connector + Supabase Auth; local queue policy custom | Adapter/queue policy custom | Custom | JWT channel disconnect; cache wipe custom |
| At-rest encryption | External SQLite encryption | Official option; key lifecycle custom | External SQLite encryption | External plugin | Cache policy custom |
| Background freshness | OS/isolate opportunistic | WorkManager; iOS/OS limit | OS/plugin limit | OS/plugin limit | WebSocket not background guarantee |
| Schema coupling | App migrations/API contract | Source schema + streams + client app | Generated model/adapter/provider | App migration/API contract | Supabase schema/publication/RLS |
| Self-host/exit | Strong if protocol exported | Service self-host but FSL/ops/Mongo | MIT package; provider semantics remain | Strongest local, API remains | Supabase Realtime coupling |
| AI-operability | Clear but largest custom semantic surface | Less transport code, more distributed config | Generated + adapter churn | Raw code/migrations largest | Simple surface, hidden event gaps |
| Provider fee/hard cap | Supabase/API usage; no sync fee | Usage-based, Free soft limits; no universal hard cap | No sync fee; Supabase/API usage | No sync fee; own infra/API | Supabase Realtime/egress usage |

Bu tablo “best” veya “winner” belirtmez. “Strong” yalnızca documented primitive veya control surface anlamındadır; safety proof için fixture gerekir.

## 11. Failure/recall/delete scenario matrix

| Senaryo | Kabul edilmesi gereken davranış | A | B | C | D | E |
|---|---|---|---|---|---|---|
| Client offline iken package expiry | Critical action block; bounded read-only safe state; next online revalidation | Custom | Stream/token/expiry + app floor | Custom | Custom | Cache-only re-fetch; offline high-consequence yok |
| User/role recall while offline | Event kaçsa bile expiry/generation floor eventual block; no new authority | Tombstone/floor custom | Stream/filter/reprocess + app floor | Realtime/re-fetch risk | Custom | Missed event; full re-fetch |
| Remote delete + local stale row | Tombstone/anti-resurrection; old package reapply edilemez | Custom | Verify stream delete/tombstone and late upload | Issue #451 risk; fixture required | Custom | Event missed; re-fetch |
| Duplicate response timeout | Same operation id replay safe; unknown visible | Custom | Backend idempotency/2xx result custom | HTTP queue retry; backend custom | Custom | No queue; API custom |
| Concurrent delete/update | Explicit domain conflict/hold; delete policy auditable | Custom | Docs sample deletes-win is not required policy | Custom | Custom | Online API only |
| Auth access token expiry | Refresh/hold, no stale token success | API custom | fetchCredentials + queue hold | Queue connector custom | API custom | JWT channel disconnect; cache wipe custom |
| App killed mid-apply | Local transaction atomic; cursor not advanced half-way | Drift transaction | PowerSync local atomic queue | SQLite/queue transaction test | SQLite transaction | No durable apply |
| Schema incompatible old client | Quarantine/forced update/full bounded reissue | App migrations/package version | versioned streams/dual mappings | generated migrations/adapter | migration gate | API/cache re-fetch |
| Provider outage / sync service outage | Safe read-only/hold; no unbounded retry or silent success | API timeout/unknown | FIFO blocking/dead-letter policy | Queue may grow; policy custom | custom | cache stale/online unavailable |
| Restore from backup | Package/queue/recall/audit floor + object manifest quarantine | custom | source DB + service bucket rebuild | DB/queue custom | custom | Re-fetch only, no local authority |

Bu matrix test planı için fixture adlarıdır; gerçekleşmiş test sonucu değildir.

## 12. Supabase 2026 changelog / breaking-change watch

Changelog taraması bu debate için iki sonucu netleştirir: (1) Supabase-centred path'in API/schema/auth/Realtime defaults'i release watch ister; (2) provider-managed primitive değişiklikleri offline client contract'inin sabit olduğu anlamına gelmez.

- **Tables not auto-exposed:** Yeni public table'lar Data/GraphQL API'ye otomatik expose edilmez; tüm mevcut project'ler için enforcement 2026-10-30 takviminde duyurulmuştur; explicit grant gerekir. RLS değişmez ama direct Data API/API-boundary surface değişir: [breaking change](https://supabase.com/changelog/45329-breaking-change-tables-not-exposed-to-data-and-graphql-api-automatically).
- **Realtime schema locked:** realtime schema create/alter/drop'e kilitlenmiştir; realtime.messages RLS yönetimi kalır. Custom Realtime table/function veya internal schema migration varsayımı yapılmamalı: [Realtime schema lock](https://supabase.com/changelog/realtime-schema-locked-down-against-modification).
- **Anon OpenAPI removal:** Anon key ile OpenAPI schema spec erişimi yeni project'lerde 2026-03-11, tüm project'lerde 2026-04-08 takvimiyle kaldırılmıştır; normal Data API çalışması ayrı konudur: [OpenAPI breaking change](https://supabase.com/changelog/42949-breaking-change-removing-access-to-openapi-spec-via-the-anon-key).
- **pg_graphql defaults:** pg_graphql yeni project'lerde otomatik enable edilmez; 1.6 introspection yeni project'lerde default disabled hale gelir. Brick/GraphQL tooling veya schema discovery varsayımı explicit config ister: [no automatic pg_graphql](https://supabase.com/changelog/42180-breaking-change-pg-graphql-no-longer-enabled-automatically-within-approx-3-weeks-from-today), [introspection](https://supabase.com/changelog/46320-breaking-change-pg-graphql-1-6-0-graphql-introspection-disabled-by-default).
- **Self-host API gateway:** Self-host Envoy default API gateway olarak Kong'un yerini alır; HTTPS listener, custom kong.yml veya service name'e bağlı runbook'lar etkilenebilir: [Envoy breaking change](https://supabase.com/changelog/48048-self-hosted-supabase-envoy-becomes-the-default-api-gateway-breaking-change).
- **Self-host auth URL:** API_EXTERNAL_URL self-host auth/v1 path'i içerecek şekilde değişmiştir; SAML IdP repoint gerekir: [API_EXTERNAL_URL](https://supabase.com/changelog/47093-self-hosted-supabase-api-external-url-to-include-auth-v1).
- **Self-host database/runtime:** PostgreSQL 15→17 default image migration ve supabase_admin→postgres Studio/postgres-meta migration gibi değişiklikler self-host restore/runbook surface'ini etkiler: [PG 15→17](https://supabase.com/changelog/46080-self-hosted-supabase-upgrading-from-pg-15-to-17-breaking-change), [admin role](https://supabase.com/changelog/46081-self-hosted-supabase-switching-studio-from-supabase-admin-to-postgres-breaking-change).
- **OAuth response status:** OAuth token endpoint HTTP 201 yerine 200 döner; clients exact 201 varsaymamalı, any-2xx contract kullanmalı: [OAuth status](https://supabase.com/changelog/45468-breaking-change-oauth-token-endpoint-will-return-http-200-instead-of-201).
- **Extension version pinning:** Explicit CREATE/ALTER EXTENSION version clause ignore edilip default version kurulabilir; migration reproducibility için extension inventory/export kontrolü gerekir: [extension version pinning](https://supabase.com/changelog/extension-version-pinning-ignored).
- **Management logs endpoint:** logs.all endpoint'i 2026-09-23'te kaldırılacak; logs endpoint/ClickHouse SQL'e migration gerekir. Bu mobile data path değil, fakat AI-operability/incident evidence watch'tır: [logs endpoint](https://supabase.com/changelog/48235-migration-of-supabase-management-api-logs-all-analytics-endpoint-to-logs-endpoint).
- **PostgREST retries:** GET/HEAD transient 520/503/network için automatic retry duyurulmuştur; bu mutation idempotency kanıtı değildir ve POST/command retry'yi app API'si çözmelidir: [PostgREST retries](https://supabase.com/changelog/45071-automatic-postgrest-retries-for-transient-errors).
- **SMTP/free template and self-host analytics/vector:** Free SMTP template customization removal, self-host Analytics/Vector opt-in gibi değişiklikler auth/ops surface'ini etkileyebilir; auth email ve observability'nin free/default olduğu varsayımı yapılmamalı: [email templates](https://supabase.com/changelog/46599-changes-to-email-template-customisation-on-free-tier), [Analytics/Vector](https://supabase.com/changelog/46084-self-hosted-supabase-making-analytics-and-vector-opt-in).

Bu liste Supabase'i eliyor veya seçmiyor. Deployment/package release watch listesine eklenmesi gereken current breaking-change evidence'idir.

## 13. Cost, hard-cap, data usage ve exit karşılaştırması

### 13.1 Maliyet sınıfları

- **Mandatory:** Supabase project/DB/Auth/Storage/API, device/app-store, required monitoring/backups; adaydan bağımsız temel runtime.
- **Deferrable:** Realtime, PowerSync Cloud, advanced PITR, extra replicas, premium support, object CDN.
- **Optional:** heavy media, rich history, background refresh frequency.
- **Scale-triggered:** PowerSync hosted volume/clients, Supabase egress/compute/PITR, self-host Mongo/LB/replicator, audit retention.

### 13.2 Hard-cap ayrımı

- **Supabase:** spend cap bazı usage kalemlerini durdurabilir; universal bill hard cap değildir. Compute, PITR, egress/object ve tax/FX ayrı okunmalıdır.
- **PowerSync Cloud:** Free plan soft limits ve inactivity deactivation içerir; Pro/Team usage-based overage vardır. Pricing page universal hard stop garantisi vermez.
- **Brick/Drift/sqflite:** Sync-provider fee yok; fakat custom API/Supabase egress and engineering cost'u owner'a taşır.
- **Realtime/cache:** Ek engine olmadan başlanabilir; Realtime connection/egress/DB usage ile scale cost'u vardır. “Free” operational hard cap değildir.

### 13.3 Exit/portability

| Exit konusu | A/D | B | C | E |
|---|---|---|---|---|
| Local data format | SQLite/JSON app-owned; portable manifest yapılabilir | SQLite client + PowerSync protocol metadata | SQLite/Brick generated model | Cache/re-fetch |
| Server sync state | Kavriva API/DB records custom | Source DB + PowerSync buckets/Mongo + service config | API/queue/Realtime/provider semantics custom | Supabase source + re-fetch |
| Conflict/audit history | Export contract bizim | Backend custom; service replication ayrı | Queue/custom backend | Online API custom |
| Self-host | Supabase/API still separate | PowerSync service FSL + Mongo/LB/ops | Package MIT but Supabase semantics remain | Supabase/API remains |
| Practical exit burden | Protocol docs/test migration burden | Distributed service/license/ops burden | Adapter/codegen/realtime migration burden | Rebuild durable offline if required |

Exit “SDK değiştirilebilir” demek değildir; package manifest, operation history, tombstones, unresolved conflicts, object digests, auth mapping ve restore/quarantine runbook'unun başka platformda çalıştırılabildiği clean-room drill'dir.

## 14. AI-operability ve owner riskleri

AI-operated bir projede değerlendirme yalnızca Dart API sayısı değildir:

1. **Deterministic state:** migration snapshots, package manifests, stream definitions, operation schemas ve lockfiles version-control'da diff edilebilir olmalı.
2. **Bounded change surface:** client'ın canonical DB'ye genel write erişimi olmamalı; high-consequence command'lar tek API boundary'sinde olmalı.
3. **Machine-checkable invariants:** no-duplicate operation, no-stale-critical-read, generation monotonicity, tombstone anti-resurrection, RLS/stream equivalence ve storage/object digest checks otomatik olmalı.
4. **Observable unknown:** timeout, blocked queue, validation reject, auth-held, stream lag, recall pending ve restore quarantine görünür status olmalı; AI “başarılı görünüyor” diye infer etmemeli.
5. **Dependency watch:** Supabase changelog, Flutter/Dart SDK, provider SDK, package generator, SQLCipher/SQLite ABI, PowerSync service version ve pricing release watch listesinde olmalı.
6. **Human approval boundary:** Internal Operations approve/publish/recall/role mutation işlemleri client offline queue tarafından otomatik execute edilememeli; online API + human/audit policy ile kapanmalı.

AI-operability ilk okuması:

- A/D semantik olarak en fazla custom surface taşır ama manifest/operation formatı owner'ın tam kontrolündedir.
- B transport/partial sync kodunu azaltır; karşılığında stream DSL, service, bucket, RLS mirror, upload backend, billing ve self-host surface'i ekler.
- C generated code deterministik olabilir; adapter/provider/Realtime edge-case ve package release-lag görünür dependency riskidir.
- E başlangıçta basittir; event loss, cache invalidation ve recall gap production'da gizli custom protocol'e dönüşebilir.

## 15. No-code validation gates / sonraki fazın soruları

Henüz bir aday seçmeden her family için şu kanıt paketi istenmelidir:

### Product/safety

- Offline window ve critical/non-critical action sınıfları nedir?
- Recall/delete SLA online ve offline için nedir?
- Hangi rows/media task package'e girecek, size/data usage budget'i nedir?
- Old client, restored backup, mixed release ve clock anomaly nasıl fail-closed olur?

### Protocol

- Package manifest/generation/tombstone schema'sı nedir?
- Delta cursor gap/checksum mismatch/reorder/duplicate nasıl kapanır?
- Operation result accepted/rejected/held/unknown/duplicate nasıl görünür?
- Conflict hangi alanlarda hold, hangi alanlarda deterministic merge olabilir?
- Late operation deleted/recalled resource'u yeniden yaratabilir mi? Kanıt nedir?

### Auth/privacy

- Session max age/inactivity/single-session ve role revoke policy'si nedir?
- Sign-out/device loss sonrası local DB, outbox, media ve encryption key ne zaman silinir?
- Queue/token storage ve background worker hangi auth boundary'ye tabidir?
- Stream/filter/RLS equality nasıl otomatik kontrol edilir?

### Ops/recovery/cost

- Background task çalışmadığında safe state nedir?
- PowerSync stream lag/queue block, Brick queue growth, Realtime disconnect veya API outage nasıl alarm olur?
- Supabase DB backup + Storage object + package/queue/audit + encryption key restore manifesti nasıl doğrulanır?
- Current cost tavanı soft alert mi, gerçek hard stop mu; tax/FX/egress/overage kim izler?
- Supabase-only, PowerSync self-host ve custom API exit drill hangi sırayla yapılır?

### Maintenance/AI

- Flutter/iOS later, package upgrade, generated code and schema migration test matrix'i kim sahiplenir?
- Official security issue/changelog/release watch cadence'i nedir?
- AI'nin değiştirebileceği files/configs ile human approval gerektiren migration/policy boundary'si nedir?

Bu sorular cevaplanmadan “en uygun teknoloji” cümlesi yazılmamalı; cevaplar sonraki ADR/evidence packet'e girmelidir.

## 16. Sonuç — kazanan yok

Bu primary research şu ayrımı doğrular:

- **A/D:** Kavriva bounded offline contract'ini ve exit'i en çok özelleştirebilir; karşılığında durable delta, operation API, conflict, recall, encryption, background ve test yükünü owner'a verir.
- **B:** Local SQLite, partial sync, queue/checkpoint ve connector capability'sini hazır verir; karşılığında backend conflict/command semantics, RLS/stream equivalence, recall floor, service/license/usage/self-host operations'ı ortadan kaldırmaz.
- **C:** Flutter/Supabase local-first queue ve codegen ile hızlı başlangıç sağlayabilir; request queue/retry ile high-consequence bidirectional sync, deletion/recall/tombstone proof'u birbirine karıştırmamak gerekir. Current release-lag ve observed remote-delete riskleri hold'dadır.
- **D:** Mature local SQLite path ve düşük provider coupling verir; sync correctness tamamen Kavriva'nın semantic/API/test yüküdür.
- **E:** Düşük başlangıç yüzeyli Realtime/cache baseline olabilir; durable offline package, replayable delta, idempotent operation ve recall/delete guarantee değildir.

Hiçbir aile, resmi marketing/capability dokümanından tek başına Kavriva'nın safety, recall, restore, offline authorization veya hard-cap gereksinimlerini kanıtlamaz. Bu belge teknoloji seçmez; ADR öncesi kanıt ve validation gates'i daraltır.

**Karar:** NO WINNER — candidate evidence pending — no implementation / no purchase.

## 17. Resmi/primary kaynak envanteri

### Supabase

- [Supabase changelog](https://supabase.com/changelog.md)
- [Realtime authorization](https://supabase.com/docs/guides/realtime/authorization)
- [Subscribing to database changes](https://supabase.com/docs/guides/realtime/subscribing-to-database-changes)
- [Dart subscribe](https://supabase.com/docs/reference/dart/subscribe)
- [Realtime architecture](https://supabase.com/docs/guides/realtime/architecture)
- [User sessions](https://supabase.com/docs/guides/auth/sessions)
- [Database backups](https://supabase.com/docs/guides/platform/backups)
- [Cost control](https://supabase.com/docs/guides/platform/cost-control)
- [Supabase–PowerSync integration](https://supabase.com/partners/integrations/powersync)

### PowerSync

- [Dart/Flutter SDK](https://docs.powersync.com/client-sdks/reference/flutter)
- [Sync Streams](https://docs.powersync.com/sync/streams/overview)
- [Client-side backend integration](https://docs.powersync.com/configuration/app-backend/client-side-integration)
- [Writing client changes](https://docs.powersync.com/handling-writes/writing-client-changes)
- [Handling update conflicts](https://docs.powersync.com/handling-writes/handling-update-conflicts)
- [Handling validation/write errors](https://docs.powersync.com/handling-writes/handling-write-validation-errors)
- [Consistency](https://docs.powersync.com/architecture/consistency)
- [Supabase Auth](https://docs.powersync.com/configuration/auth/supabase-auth)
- [RLS and Sync Streams](https://docs.powersync.com/integrations/supabase/rls-and-sync-streams)
- [Schema changes](https://docs.powersync.com/maintenance-ops/implementing-schema-changes)
- [Data encryption](https://docs.powersync.com/client-sdks/advanced/data-encryption)
- [Background syncing](https://docs.powersync.com/client-sdks/advanced/background-syncing)
- [Performance and limits](https://docs.powersync.com/resources/performance-and-limits)
- [Self-hosting architecture](https://docs.powersync.com/maintenance-ops/self-hosting/deployment-architecture)
- [Pricing](https://powersync.com/pricing)
- [Licensing terms](https://powersync.com/legal/licensing-terms)
- [Dart package](https://pub.dev/packages/powersync), [Dart repository](https://github.com/powersync-ja/powersync.dart), [service repository](https://github.com/powersync-ja/powersync-service)

### Brick

- [Brick repository](https://github.com/GetDutchie/brick)
- [Supabase adapter README](https://github.com/GetDutchie/brick/blob/main/packages/brick_offline_first_with_supabase/README.md)
- [offline-first changelog](https://pub.dev/packages/brick_offline_first/changelog)
- [brick_sqlite changelog](https://pub.dev/packages/brick_sqlite/changelog)
- [remote delete report #451](https://github.com/GetDutchie/brick/issues/451)
- [reactive remote change discussion #448](https://github.com/GetDutchie/brick/issues/448)

### Drift/SQLite/sqflite

- [Drift repository](https://github.com/simolus3/drift)
- [Drift migrations](https://drift.simonbinder.eu/migrations/)
- [Drift transactions](https://drift.simonbinder.eu/dart_api/transactions/)
- [Drift native/background](https://drift.simonbinder.eu/platforms/vm/)
- [Drift web](https://drift.simonbinder.eu/platforms/web/)
- [Drift encryption](https://drift.simonbinder.eu/platforms/encryption/)
- [sqflite package](https://pub.dev/packages/sqflite)
- [sqflite repository](https://github.com/tekartik/sqflite)
- [sqflite_sqlcipher](https://pub.dev/packages/sqflite_sqlcipher)
- [sqlite_async](https://pub.dev/packages/sqlite_async)
- [SQLite WAL](https://www.sqlite.org/wal.html)
- [SQLite Session/changesets](https://www.sqlite.org/session.html)

Bu envanterdeki her kaynak, ilgili bölümdeki iddianın sınırını belirler; kaynakta olmayan safety conclusion [INFERRED] veya [OPEN] olarak bırakılmıştır.
