# DEBATE-009 — Finalist B: PowerSync + Supabase source + Kavriva API

**Durum:** HELD — PHASE-4 EŞİT NO-CODE FINALIST DOSSIER / NO WINNER / ADR NOT READY  
**Araştırma ve resmi kaynak kontrol tarihi:** 2026-09-18 (Europe/Istanbul)  
**Aday:** PowerSync + Supabase PostgreSQL/Auth/private Storage kaynakları; bütün high-consequence write'lar Kavriva server/API boundary'sinde  
**Yetki sınırı:** Bu dosya yalnızca documentary planlama ve eşit aday kanıtıdır. Kod, prototip, executable spike, provider hesabı, satın alma, abonelik, self-host kurulumu veya Phase-5 ADR oluşturmaz.

## Bu dosyanın anlamı

Bu dosya DEBATE-009 için **Finalist B**'yi, Aday A ile aynı frozen fixture, aynı 18 EQ ve aynı 18 MPR senaryosu
üzerinden inceler. PowerSync'in selective sync, local SQLite, upload queue ve checkpoint primitive'leri candidate
capability olarak gösterilir; bunlar Kavriva'nın canonical authority, high-consequence approval, recall, protected audit,
anti-resurrection, owner-operability veya clean-room exit kanıtı olarak sunulmaz.

Finalist B'nin bağlayıcı yorumu:

1. Flutter consumer app PowerSync Dart/Flutter SDK ile local SQLite kullanır.
2. Supabase PostgreSQL source/canonical domain ve Supabase Auth/private Storage başlangıç fiziksel adaylarıdır.
3. PowerSync Sync Streams yalnız task-scoped, role/user-scoped, data-efficient download projection'ı sağlar.
4. Local PowerSync upload queue, high-consequence command'ları doğrudan Supabase Data API'ye veya PostgreSQL'e yazmaz.
   Queue uploadData yolu Kavriva API'ye gider; API current authorization, operation id, expected generation, conflict,
   audit/floor ve Supabase transaction'ını yeniden kontrol eder.
5. Internal Operations approval, publication, recall/suspension, role/policy, deletion, protected audit ve diğer
   high-consequence mutations yalnızca online Kavriva API authority'sidir.
6. Supabase RLS, Storage policy, PowerSync stream filter ve JWT doğrulaması layered defense-in-depth'tir; bunların
   herhangi biri tek başına Kavriva product authority'si değildir.
7. PowerSync Realtime/stream delivery, push veya network callback'i recall, freshness, deletion veya server acceptance
   kanıtı değildir.

Bu dosyanın disposition'ı **HELD**'dir. No-code documentary evidence tamamlanmadan herhangi bir satır PASS veya
production-ready olarak okunmamalıdır; finaliste puan veya kazanan sonucu verilmemiştir.

### Kanıt etiketleri

- **[CONFIRMED-2026]** 2026-09-18 tarihinde okunmuş resmi PowerSync/Supabase/Flutter/Android/Apple/SQLite kaynağında
  açıkça belirtilen capability, sınır veya resmi fiyat snapshot'ı.
- **[INFERRED]** Resmi primitive'in DEC-0033/0034/0035 ve DEBATE-009 fixture'ı ile birlikte okunmasından çıkan mimari
  sonuç; kabul testi ve ADR öncesi garanti değildir.
- **[OPEN]** Resmi kaynakta yeterince kesinleşmeyen, proje politikası/konfigürasyonu/sağlayıcı seçimi veya sonraki
  evidence packet'e bağlı konu.
- **[HELD]** Güvenli pozitif etki için kanıt eksik; bu durum kullanıcıya SQL/SSH/provider-console repair görevi yüklemez.
- **[REJECT-IF-UNMITIGATED]** Belirtilen sınır kapatılmazsa Finalist B'nin ilgili kullanımı reddedilir.

Marketing claim, pricing headline, “real-time/offline-first/consistent” ifadesi veya hazır SDK bulunması safety proof
değildir. Özellikle PowerSync'in resmi conflict dokümanı backend'i conflict konusunda unopinionated olarak tanımlar;
en basit LWW davranışı öneri örneğidir, Kavriva policy'si değildir.

## Bağlayıcı proje girdileri ve eşitlik sınırı

- **DEC-0033:** Flutter consumer-mobile working direction; Android-first, iOS-later; portable data/safety/provenance
  truth; generated registrant, platform channel, native dependency ve owner-operability reversal triggers.
- **DEC-0034:** canonical authority per domain; server/API mediation; bounded versioned integrity-bound offline package;
  durable identified operations; idempotent submission; visible conflict/hold/unknown; high-consequence silent LWW yok;
  current/history/protected-audit/object-media ayrımı; non-restorable negative/deletion/accepted-operation/migration
  floor; cross-plane restore/export/exit manifesti.
- **DEC-0035:** managed Supabase-centred physical backend working direction; PostgreSQL/Auth/private Storage candidates;
  Kavriva API authority; RLS/Storage defense-in-depth; service_role server-only; Supabase Studio product admin surface
  değil; object backup/audit/floor bağımsız; PowerSync veya local engine seçilmemiş.
- **DEBATE-009 Requirements Synthesis:** package closure, wrong-base delta, cache eviction, recall/suspension,
  restore/clone, account-light migration, API boundary ve 18 EQ requirements.
- **DEBATE-009 Mobile Platform Failure Research:** process/lifecycle, backup/restore, keys, migrations, network,
  background, cellular, storage, clock, accessibility, native/plugin ve 18 MPR requirements.
- **DEBATE-009 Manager Proposal:** Drift/custom primary working direction proposed; PowerSync second challenger; bu
  finalist dosyası proposal'ı override etmez ve otomatik fallback seçmez.

Tüm adaylarda aynı frozen fixture kullanılır. PowerSync selective sync capability'si, Aday A'nın bounded package
contract'inden daha kolay görünse bile fixture küçültülmez; provider/service maliyeti ve failure surface'i gizlenmez.

## Candidate B logical topology

    Flutter consumer
      ├─ PowerSync Dart SDK
      │    ├─ local SQLite / synced tables / app-owned durable operation metadata
      │    ├─ Sync Streams subscription (selected motorcycle/task scope only)
      │    └─ upload queue
      ├─ foreground/API revalidation
      └─ optional push/Realtime hint (not authority)

    PowerSync uploadData / sync protocol
      ├─ PowerSync Cloud OR self-hosted PowerSync service [OPEN]
      ├─ selected download stream from Supabase PostgreSQL
      └─ upload endpoint = Kavriva API, not direct client write

    Kavriva API authority
      ├─ Supabase Auth/JWT/session verification
      ├─ action-time authorization, idempotency, generation fence
      ├─ high-consequence command/conflict/hold/unknown result
      ├─ Supabase PostgreSQL transaction/current state
      ├─ private Storage object capability/manifest
      └─ protected audit / negative floor / package issuance [OPEN adjunct custody]

Bu diagram önerilen boundary'dir; executable topology, host, region, plan, API framework, schema ve account seçimi
değildir. PowerSync Cloud ile self-host arasında da karar verilmemiştir.

## 1/16 — Exact candidate composition ve authority boundary

| Mantıksal rol | Finalist B'deki aday primitive | Kavriva authority yorumu | Durum |
|---|---|---|---|
| Flutter client | Flutter Android-first, iOS-later | UI ve local projection; canonical DB/object authority yok | [CONFIRMED-2026] framework direction / implementation yok |
| Local sync DB | PowerSync Dart SDK 2.4.0 ile SQLite | Synced projection + local queue; package/operation policy için app-owned metadata gerekir | [CONFIRMED-2026] package metadata |
| Partial download | PowerSync Sync Streams | SQL-like stream, user/auth/subscription parameter, on-demand/auto-subscribe; stream filter RLS yerine geçmez | [CONFIRMED-2026] |
| Local write transport | PowerSync local data + ps_crud/upload queue | Queue command'ı Kavriva API'ye gitmeli; direct Supabase write yasak | [INFERRED] binding requirement |
| Upload backend | Kavriva API; Edge Function/equivalent aday | Idempotency, current authorization, conflict, protected audit, generation fence ve result lookup | [OPEN] runtime |
| Canonical source | Managed Supabase PostgreSQL | Current domain/history/operation ledger için candidate; client general access yok | [DEC-0035] direction |
| Auth/session | Supabase Auth JWT/JWKS connector + Kavriva API verification | Authenticated olmak approval/competence değildir; session/security epoch ve actor/action check gerekir | [CONFIRMED-2026] primitive; policy [OPEN] |
| Object plane | Supabase private Storage candidate | Signed/scoped handle, digest/generation, quarantine; DB backup object bytes değildir | [DEC-0035] / [CONFIRMED-2026] |
| Realtime/push | Supabase Realtime/PowerSync stream wake-up hint | Delivery, recall, freshness, acceptance veya delete proof'u değil | [CONFIRMED-2026] limitation |
| Protected audit/floor | API + sufficiently independent custody | Release/suspension/security/deletion/accepted-operation/migration negative floor | [OPEN] physical custody |
| PowerSync service | PowerSync Cloud veya self-hosted service | Sync transport/cursor/bucket; canonical Kavriva authority değil | [OPEN] deployment/licensing |
| Studio/provider console | Supabase/PowerSync administration | Kavriva Internal Operations product surface veya approval bypass değil | [DEC-0035] |

### Direct-write rule

PowerSync documentation, upload backend'in CRUD operation'larını işlemesini ve conflict validation'ını geliştiriciye
bırakır. Finalist B'de bu endpoint doğrudan PostgREST/Supabase table write yüzeyi olamaz; Kavriva API boundary'si
olarak modellenir. Bir PowerSync setup, client veya upload worker'ın service_role, global Storage key veya unrestricted
Postgres credential taşıdığı görülürse bu adayın ilgili path'i [REJECT-IF-UNMITIGATED] olur.

## 2/16 — Resmi capability, version, migration ve provider coupling snapshot

### 2.1 PowerSync client/service capability

- **[CONFIRMED-2026]** PowerSync Dart/Flutter package 2.4.0 snapshot'ında Android, iOS, Linux, macOS, web ve Windows
  metadata'sı vardır; Flutter Web resmi package metadata'sında beta olarak belirtilir: [Dart package](https://pub.dev/packages/powersync).
- **[CONFIRMED-2026]** Client local SQLite read/write ve reactive watch sunar; local write data table ile upload queue'yu
  atomik ekler: [Flutter SDK](https://docs.powersync.com/client-sdks/reference/flutter),
  [client-side integration](https://docs.powersync.com/configuration/app-backend/client-side-integration).
- **[CONFIRMED-2026]** Sync Streams user/auth/subscription parameter ile SQL-like partial sync sağlar; default
  auto-subscribe false, unsubscribe sonrası TTL default 24 saattir: [Sync Streams overview](https://docs.powersync.com/sync/streams/overview).
- **[CONFIRMED-2026]** Synced tables için id text primary key, SQLite type mapping, bucket/user limitleri ve row/column
  limitleri vardır: [performance and limits](https://docs.powersync.com/resources/performance-and-limits),
  [type mapping](https://docs.powersync.com/sync/streams/type-mapping).

### 2.2 Schema/migration behavior

- **[CONFIRMED-2026]** Sync protocol schemaless/client-side schema view yaklaşımı kullanır; synced schema'da normal client
  migration gerekmeyebilir. Raw/app-owned tables migration ister: [implementing schema changes](https://docs.powersync.com/maintenance-ops/implementing-schema-changes).
- **[CONFIRMED-2026]** Kaynak Postgres DDL, stream definition, transforms, casts, app release ve old-client compatibility
  additive order ile deploy edilmelidir; rename/type change dual mapping veya versioned stream gerektirebilir:
  [deploying schema changes](https://docs.powersync.com/maintenance-ops/deploying-schema-changes).
- **[INFERRED]** “Client migration yok” ifadesi application semantics, package manifest, operation ledger, encryption
  metadata, local indexes veya API contract migration'ını ortadan kaldırmaz. Eski client'ın yeni safety-critical
  field'i anlamaması capability hold olmalıdır.

### 2.3 Provider coupling

PowerSync source database, stream DSL, bucket/checkpoint service, upload API, auth/JWKS, Supabase RLS mirror, SQLite
schema ve package release graph'ını aynı operational contract'e bağlar. Bu coupling Aday A'nın custom protocol riskini
azaltabilir; ancak service outage, stream lag, reprocessing, bucket backup, license/version, billing ve migration
surface'lerini ekler. “No schema change to Supabase” integration claim'i source/API/RLS/stream operational coupling'in
olmadığı anlamına gelmez.

## 3/16 — Download, write and reconciliation contract

### 3.1 Download / bounded offline package

PowerSync stream'i yalnızca package payload projection'ı için kullanılabilir. Kavriva'nın package contract'i stream
filter'ına indirgenemez. Her selected motorcycle/task package'i için API veya source domain şu conceptual manifest
alanlarını sağlamalıdır:

- motorcycle/model-year/resolved-variant and applicable modification;
- task/guide, exact approved release ve package generation;
- schema/client/provider capability window;
- base generation/stream version ve target generation;
- content/manifest/digest/dependency closure;
- freshness/eligibility context, suspension/revocation floor;
- required versus optional media and data classification;
- language/unit/accessibility meaning;
- safe-stop/recovery closure ve re-fetch/full-package fallback.

**[INFERRED]** Synced row'ların doğru stream'de gelmesi, package'ın atomic, complete, anti-rollback ve safety-closed
olduğunu kanıtlamaz. Staging, manifest/digest verification, old generation retention ve promote boundary'si
PowerSync table update'lerinin üstünde Kavriva application contract'i olarak ayrıca kurulmalıdır.

### 3.2 Upload queue / Kavriva API

PowerSync docs'a göre:

- local write data table + ps_crud queue'ya atomik eklenir;
- uploadData initial/reconnect/keepalive/retry ile çağrılır;
- queue FIFO drain edilir;
- backend operation'ları idempotent olmalıdır;
- per-client operation id deduplication için kullanılabilir;
- upload error queue'yu bloklayabilir;
- validation/conflict için 2xx body veya ayrı synced error table önerilir.

Finalist B'de Kavriva API şu result semantics'i ayrıca taşımak zorundadır:

| Sonuç | PowerSync transport davranışı | Kavriva meaning |
|---|---|---|
| ACCEPTED | Queue operation acknowledged; server state stream'e geri gelebilir | API current authorization, expected generation, audit/floor ve transaction ile accepted effect'i kanıtlamış olmalı |
| DUPLICATE | Same operation id yeniden geldi | Önceki accepted/rejected/held result değişmeden döner; payload fingerprint değişirse reject |
| REJECTED/VALIDATION | Docs'taki 2xx response body veya synced error path | Domain state değişmez; user-readable reason ve correction path |
| CONFLICT | Queue ilerlemesi için backend result gerekir | High-consequence iki taraf korunur; explicit hold/review; universal LWW yok |
| HELD | Queue'da permanent transient error gibi sonsuz retry yapılmamalı | Auth/policy/floor/provider/billing dependency unresolved; visible held, manual owner repair değil |
| UNKNOWN | Network/timeout response yok | Same operation id status lookup/reconcile; success/failure tahmini yok |
| PARTIAL | Cross-plane operation tam kapanmadı | Object/audit/package/current state manifesti ile reconcile; complete success gösterilmez |

**[OPEN]** PowerSync queue'unun 2xx conflict response'ını nasıl surface edeceği, blocked FIFO ile Kavriva'nın HELD/
OUTCOME_UNKNOWN state'inin nasıl ayrılacağı, dead-letter'ın out-of-order riskinin nasıl kapatılacağı ve status lookup
endpoint'inin owner-readable runbook'ı sonraki evidence packet'e bağlıdır.

### 3.3 Conflict semantics

- **[CONFIRMED-2026]** PowerSync backend conflict konusunda unopinionated'dir; simplest implementation per-field LWW
  olabilir; custom conflict resolution geliştiriciye bırakılır: [handling update conflicts](https://docs.powersync.com/handling-writes/handling-update-conflicts).
- **[CONFIRMED-2026]** Docs deletes-win, server receive order ve idempotent operation id örnekleri verir; built-in
  domain approval veya high-consequence policy iddiası yoktur.
- **[INFERRED]** Kavriva API high-consequence fields için conditional generation, state machine, hold/review ve protected
  audit kullanmazsa PowerSync default kullanımını kabul edemez. Cosmetic/local low-risk field sınırı açıkça
  yazılmadan LWW uygulanamaz.

### 3.4 Causal consistency and checkpoint

- **[CONFIRMED-2026]** PowerSync causal consistency/checkpoint behavior, committed and consistent stream state'i ve
  upload queue ile checkpoint ilerlemesini tanımlar: [consistency](https://docs.powersync.com/architecture/consistency).
- **[INFERRED]** Causal checkpoint, Kavriva release/suspension/deletion/accepted-operation negative floor'u değildir.
  Stream checkpoint'in ileri gitmesi, API command'ın current authority olarak kabul edildiği anlamına gelmez.
- **[OPEN]** Package generation ile PowerSync checkpoint/base version'ın one-to-one fence olarak kullanılıp kullanılamayacağı
  ve mismatch'te full compact package reissue path'i kanıtlanmalıdır; “checkpoint var” yeterli değildir.

## 4/16 — Supabase source/Auth/Storage boundary and security checklist

### 4.1 Supabase source and API

- Supabase PostgreSQL source, source RLS, publication/replication ve Storage candidate'dir; Flutter/PowerSync client
  general canonical DB/object authority taşımaz.
- Kavriva API source write'ı action-time actor/session/scope/state/classification/consequence/independence/expected
  generation ile yeniden yetkilendirir.
- RLS ve Storage policy mandatory defense-in-depth'tir; approval/publication/recall/provenance/protected-audit/
  separation-of-duties authority'si değildir.
- **[CONFIRMED-2026]** Supabase source'da yeni table'ların Data/GraphQL API'ye otomatik expose edilmemesi ve existing
  project enforcement takvimi duyurulmuştur; explicit GRANT ile RLS birbirinden ayrıdır:
  [tables not exposed automatically](https://supabase.com/changelog/45329-breaking-change-tables-not-exposed-to-data-and-graphql-api-automatically).
- **[INFERRED]** PowerSync source access için Data API exposure değişikliği doğrudan client API görünürlüğü olmasa bile
  stream/replication/config/runbook'ını etkileyebilir; new table grant, source schema, stream visibility ve API path
  birlikte inventory edilmelidir.

### 4.2 Supabase skill security traps inherited by B

Bu adayda aşağıdaki guardrails binding kabul edilir:

- service_role/secret key yalnız server-side; Flutter, browser, repository, logs, exports veya AI task context'ine
  girmez.
- RLS exposed schema'daki her table'da etkin olmalı; UPDATE için SELECT policy de gerekir; UPDATE policy hem USING hem
  WITH CHECK ile row reassignment'ı engeller.
- auth.role() deprecated pattern değildir; TO authenticated tek başına row authorization değildir; ownership/scope
  predicate gerekir.
- user_metadata user-editable olduğundan JWT authorization claim'i olarak kullanılmaz; app_metadata veya server-side
  authoritative relation kullanılır.
- User delete mevcut access token'ları otomatik invalidate etmez; sensitive API operation session_id/auth.sessions
  veya security epoch ile ayrıca kontrol edebilir; JWT claims refresh edilmeden stale olabilir.
- Views default RLS bypass edebilir; exposed view kullanılırsa security_invoker veya unexposed schema/revoke gerekir.
- SECURITY DEFINER public function privileged bypass yaratabilir; gerekirse non-exposed schema, auth.uid check, narrow
  grant ve independent review gerekir.
- Storage upsert INSERT + SELECT + UPDATE ister; private bucket/signed handle global authority değildir.

Bu maddeler PowerSync'in RLS/stream docs'unda geçerli olsa da PowerSync service veya Supabase default'larının otomatik
uyguladığı Kavriva policy olarak varsayılmayacaktır.

### 4.3 Auth/session/stream

- **[CONFIRMED-2026]** PowerSync Supabase Auth JWT verification, HS256/RS256 JWKS modelleri ve fetchCredentials lifecycle
  destekler: [Supabase Auth integration](https://docs.powersync.com/configuration/auth/supabase-auth).
- **[CONFIRMED-2026]** Supabase access token'ları kısa ömürlü (genellikle 5 dakika–1 saat), refresh token rotate/single-use
  modelindedir; default session indefinite olabilir: [Supabase user sessions](https://supabase.com/docs/guides/auth/sessions).
- **[CONFIRMED-2026]** Supabase Realtime channel policy connection/JWT refresh'te cache'lenir; yeni JWT gelmezse expiry'de
  disconnect olur: [Realtime authorization](https://supabase.com/docs/guides/realtime/authorization).
- **[INFERRED]** Token expiry, sign-out, role revoke veya session termination local PowerSync DB, queue, stream cache ve
  optional object'leri otomatik olarak Kavriva policy'sine göre silmiş sayılmaz. User partition wipe/hold, stream
  unsubscribe, API revalidation ve object capability revoke ayrıca tasarlanmalıdır.

### 4.4 Storage/object

- Private Storage object'leri package manifest, digest, generation, classification, quarantine ve API-mediated short-lived
  capability ile bağlanmalıdır.
- PowerSync rows ile Supabase Storage bytes aynı transaction değildir.
- DB backup Storage object bytes'ını içermez; cross-plane restore/export manifesti ve independent object recovery
  gereklidir: [Supabase database backups](https://supabase.com/docs/guides/platform/backups).
- Signed URL bearer credential'dır; URL possession policy/recall/freshness/technical correctness kanıtı değildir.

## 5/16 — Bounded package, selective stream, recall/delete ve anti-resurrection

### 5.1 Selective sync versus complete safety package

PowerSync Sync Streams Finalist B'nin en güçlü documented capability'sidir: selected user/task rows, partial sync ve
on-demand subscription data usage'ünü azaltabilir. Ancak Kavriva requirement'ı “en az veri” değil, “en küçük tam güvenli
paket”tir. Bu nedenle:

- stream query full guide library/unrelated 2 GB catalog'u istememeli;
- selected motorcycle/variant/task ve applicable modification scope'u server-side filter ile bağlamalı;
- critical warning, prerequisite/check, expected outcome, safe-stop/recovery branch, freshness/release/suspension
  context ve required media dependency closure stream'e dahil olmalı;
- optional high-resolution media ayrı subscription/object capability olarak kalmalı;
- stream row acceptance manifest/digest/generation/policy/capability ile staging'e alınmalı;
- missing/out-of-order/wrong-base stream veya partial sync, current application authority olamamalı;
- full compact package reissue veya recovery-only hold state'i bulunmalı.

**[OPEN]** PowerSync stream, source schema ve package manifest'i arasında exact safety closure proof'u yoktur. Sync Stream
filter'i RLS mirror ile aynı olsa bile guide semantics, safe-stop completeness, optional media dependency ve anti-rollback
floor'ını kendiliğinden kanıtlamaz.

### 5.2 Recall/suspension/delete

- **[CONFIRMED-2026]** PowerSync stream source change'lerini local SQLite'a aktarabilir; local offline state reconnect'e
  kadar eski kalabilir.
- **[INFERRED]** Offline device yeni recall'ı anında öğrenemez. Bounded exposure window, expiry/freshness boundary,
  foreground/API revalidation ve current suspension generation gerekir.
- Source row'un fiziksel silinmesi, stream deletion event'i, local row eviction, tombstone, old package, queue late
  update ve restore snapshot'ının anti-resurrection floor'u farklı şeylerdir.
- Late upload deleted/recalled resource'u aynı id ile yeniden yaratamamalı; API accepted-operation/deletion tombstone/
  generation policy'si bunu açıkça reddetmeli veya hold etmelidir.
- Recall event miss, stream TTL expiry, service outage, RLS policy change, cached JWT ve old client durumu aynı
  incident matrix'te test edilmelidir.

**[REJECT-IF-UNMITIGATED]** Recall/delete yalnız stream delivery, push, local DELETE veya periodic auto-subscribe'e
bırakılırsa B high-consequence offline capability'si reddedilir.

### 5.3 Anti-resurrection floor

PowerSync source/bucket checkpoint'i, Kavriva protected floor'unun yerine geçemez. Finalist B'nin required floor'ı:

- latest release and compatibility floor;
- suspension/recall/revocation generation;
- deletion/privacy floor;
- accepted-operation idempotency floor;
- migration/schema/client floor;
- security/session epoch;
- package/object generation and digest;
- protected audit checkpoint.

Bu floor'ların ordinary Supabase DB backup, PowerSync bucket storage veya restored local SQLite ile aynı mutable
failure domain'de bırakılması [REJECT-IF-UNMITIGATED]'tir. Physical custody [OPEN] kalır.

## 6/16 — Migrations, config, schema coupling and release compatibility

### 6.1 Source and stream change order

PowerSync official schema-change docs'a göre safe additive sequence conceptual olarak:

1. Supabase source schema add/compatibility;
2. API/upload backend accepts old and new representations;
3. PowerSync stream/transform/column mapping update;
4. replication/reprocessing or bucket rebuild;
5. new Flutter app capability release;
6. old-client retirement/forced hold;
7. package generation and manifest migration;
8. delete/rename cleanup only after old clients/queues are closed.

Bu order'ın exact commands, downtime, reprocessing duration ve rollback behavior'ı [OPEN] ve no-code evidence'e
bağlıdır. Stream rename/type change veya source deletion direct cutover olarak kabul edilmez.

### 6.2 Local schema and app-owned tables

- Synced PowerSync protocol tables/views normal app migration gerektirmeyebilir.
- Kavriva package manifest, durable operation status, encryption metadata, migration ledger, quarantine, tombstones,
  local history/evidence and object dependency tables app-owned ise migration ister.
- App-owned schema migration process kill/low-space/old build/backup restore matrix'inde transaction/quarantine ile
  kapanmalıdır.
- PowerSync client schema view update, old Flutter semantics veya high-consequence field meaning mismatch'ini tek başına
  çözmez.

### 6.3 Version locking and service release

- PowerSync pricing page Team planında version locking, custom write checkpoints, customer bucket storage DB ve private
  endpoint gibi özellikler gösterilir; Free/Pro'da aynı assurance varsayılmaz.
- PowerSync Cloud service version, client SDK, stream config, Supabase source schema, API contract and package release
  graph'ı birlikte pinlenmeli ve change watch yapılmalıdır.
- **[OPEN]** Version locking'in hangi deployment path/plan ve service update window'unda Kavriva release contract'ini
  koruyacağı procurement/contract review'e bağlıdır.

### 6.4 Supabase breaking-change watch inherited by B

Skill gereği 2026-09-18'de [Supabase changelog](https://supabase.com/changelog.md) yeniden tarandı. B için önemli
watch items:

- New tables not automatically exposed; all-project enforcement 2026-10-30 duyurusu: [Data/GraphQL exposure](https://supabase.com/changelog/45329-breaking-change-tables-not-exposed-to-data-and-graphql-api-automatically).
- Realtime schema create/alter/drop lock; yalnız RLS policy yönetimi: [Realtime schema lock](https://supabase.com/changelog/realtime-schema-locked-down-against-modification).
- Anon key ile OpenAPI spec access removal: [OpenAPI removal](https://supabase.com/changelog/42949-breaking-change-removing-access-to-openapi-spec-via-the-anon-key).
- pg_graphql automatic enable/introspection defaults değişimi; schema discovery/GraphQL assumptions explicit olmalı:
  [no automatic pg_graphql](https://supabase.com/changelog/42180-breaking-change-pg-graphql-no-longer-enabled-automatically-within-approx-3-weeks-from-today),
  [introspection disabled](https://supabase.com/changelog/46320-breaking-change-in-pg-graphql-1-6-0-graphql-introspection-disabled-by-default).
- Self-host Envoy default gateway, API_EXTERNAL_URL auth/v1 path, PG 15→17, Studio role changes: [Envoy](https://supabase.com/changelog/48048-self-hosted-supabase-envoy-becomes-the-default-api-gateway-breaking-change),
  [API_EXTERNAL_URL](https://supabase.com/changelog/47093-self-hosted-supabase-api-external-url-to-include-auth-v1),
  [PG 15→17](https://supabase.com/changelog/46080-self-hosted-supabase-upgrading-from-pg-15-to-17-breaking-change).
- OAuth token 201→200; client any-2xx contract kullanmalı: [OAuth status](https://supabase.com/changelog/45468-breaking-change-oauth-token-endpoint-will-return-http-200-instead-of-201).
- Extension version pinning ignore, logs.all endpoint retirement ve PostgREST GET/HEAD retry changes; mutation idempotency
  çıkarımı yapılmamalı: [extension pinning](https://supabase.com/changelog/extension-version-pinning-ignored),
  [logs endpoint](https://supabase.com/changelog/48235-migration-of-supabase-management-api-logs-all-analytics-endpoint-to-logs-endpoint),
  [PostgREST retries](https://supabase.com/changelog/45071-automatic-postgrest-retries-for-transient-errors).

Changelog watch B'yi eler veya seçmez; source/API/Realtime/self-host coupling'in release-managed olduğuna dair
operational evidence'tir.

## 7/16 — Encryption, background, Flutter platform ve accessibility

### 7.1 At-rest encryption

- **[CONFIRMED-2026]** PowerSync docs TLS in transit ve Flutter local at-rest için SQLite3MultipleCiphers veya SQLCipher
  seçeneklerini açıklar: [data encryption](https://docs.powersync.com/client-sdks/advanced/data-encryption).
- Key secure storage, provisioning, rotation, rekey, delete, backup exclusion, crash/log redaction ve restore/key-loss
  state'i application responsibility'dir.
- **[INFERRED]** Encrypted SQLite, PowerSync Cloud/service, Supabase Storage, API logs, OS backup, screenshot, rooted
  device veya object export disclosure risklerini tek başına çözmez.
- [OPEN] Android Keystore/iOS Keychain accessibility, lock-screen/biometric invalidation, reinstall, restore,
  ThisDeviceOnly/backup policy ve PowerSync encryption library upgrade matrix'i kanıtlanmalıdır.

### 7.2 Background and process death

- **[CONFIRMED-2026]** Flutter PowerSync background sync WorkManager ile Android'de beklenen şekilde test edildiği,
  iOS testlerinde partial/failed fetch ve plugin/OS limitation bulunduğu docs'ta belirtilir:
  [background syncing](https://docs.powersync.com/client-sdks/advanced/background-syncing).
- Android Doze/App Standby, process kill, incoming call, force-quit, low battery ve iOS suspend/force-quit correctness
  dependency olamaz.
- Background yalnız durable queue/stream catch-up fırsatıdır; foreground/API revalidation, stale/recall floor ve
  user-readable pending/unknown/held states zorunludur.
- Background worker'ın PowerSync service veya API credential'ı global secret olarak taşıması yasaktır.

### 7.3 Flutter/iOS later and accessibility

- PowerSync Dart SDK Android/iOS surface'i candidate capability'dir; native SQLite/encryption binary, generated
  registrant, plugin ABI, Gradle/CocoaPods/SwiftPM ve iOS background lifecycle ayrı kanıt ister.
- Flutter Web metadata beta'dır; bu mobile-first B'nin browser/Internal Operations offline authority'si olduğunu iddia
  etmez.
- TalkBack/VoiceOver/Switch Access ile PowerSync queue/sync/recovery state'leri product UI'da semantic Turkish labels,
  hints, announcements ve keyboard/touch action olarak görünür olmalıdır. SDK callback'i accessibility proof değildir.

## 8/16 — Pricing, billing cap, service outage, self-host and license

### 8.1 PowerSync Cloud official snapshot

**[CONFIRMED-2026]** [PowerSync Pricing](https://powersync.com/pricing) sayfasında 2026-09-18 tarihinde görülen
USD list signals:

| Katman | Resmi görülen değer | Kavriva/UNVERIFIED sınırı |
|---|---|---|
| Free | $0/month; 2 GB data synced/month; 500 MB hosted; 50 peak concurrent clients; 2 service instances; instance başına 1 source DB connection; community support/basic alerting; 1 hafta inactivity sonrası deactivation | Soft limits; universal hard invoice ceiling değil. Supabase/API/DB/egress dahil değil. Gerçek workload, tax/FX ve outage behavior [UNVERIFIED]. |
| Pro | $49/month'tan; 30 GB synced/month; 10 GB hosted; 1,000 peak clients; no project deactivation | 30 GB üstü synced $1/GB, hosted 10 GB üstü $1/GB, peak 1,000 üstü $30/1,000, extra instance $25/month olarak pricing page'de listelenir. Total monthly bill [UNVERIFIED] until fixture usage/egress/API/Supabase is priced. |
| Team | $599/month'tan; version locking, custom alerts/roles, write checkpoints, customer-provided bucket storage DB, private endpoints available, SLA/compliance options | Custom write checkpoints/version assurance contract'i [UNVERIFIED] until terms/procurement. Bu fiyat satın alma onayı değildir. |
| Enterprise | Custom | Price, SLA, limits, retention and support [UNVERIFIED]. |

PowerSync free plan “soft limits” olarak anılır; hard stop/fail-closed veya billing cap garantisi olarak yazılamaz. Supabase
plan/compute/PITR/Storage/egress, Kavriva API runtime, monitoring, object/audit/floor custody ve Flutter store/device
maliyetleri ayrıca hesaplanır.

### 8.2 Cost envelope and outage states

- Usage dashboard/alert, overage warning veya account email owner-readable evidence'tir; tek başına hard cap değildir.
- PowerSync free deactivation, quota/connection/hosted storage limit veya service outage durumunda local data authoritative
  sayılmaz; sync-dependent positive actions HELD/UNAVAILABLE/UNKNOWN'a geçer.
- Queue error retries unlimited block yaratabileceğinden, transient vs validation vs permanent conflict ayrımı ve
  dead-letter/hold runbook'ı gerekir. Poison operation bütün FIFO queue'yu görünmezce kilitleyemez.
- Provider billing/region/account failure, Supabase outage, API outage, JWKS failure ve PowerSync service outage
  independent status states olarak gözlemlenmelidir. Owner'a SQL/SSH/provider-console recovery görevi verilmez.

### 8.3 Self-host architecture

**[CONFIRMED-2026]** PowerSync self-host docs production için replication service, API containers, load balancer, Mongo
replica set, compaction, backups ve observability surface'i gösterir: [self-host overview](https://docs.powersync.com/maintenance-ops/self-hosting/overview),
[deployment architecture](https://docs.powersync.com/maintenance-ops/self-hosting/deployment-architecture).

Self-host B'nin Cloud billing dependency'sini azaltabilir; Mongo, network, TLS/JWKS, source DB, backups, version,
replicator, stream config, API worker, monitoring, security patch, restore and on-call burden'ını Kavriva'ya taşır.
Tek replication container ve bucket storage DB backup/rebuild behavior'ı ayrı runbook ister. Exact infrastructure,
region, RTO/RPO and total cost [UNVERIFIED].

### 8.4 License and exit

- **[CONFIRMED-2026]** PowerSync Dart/client SDK Apache-2.0 package metadata/repository'de görünür.
- **[CONFIRMED-2026]** PowerSync service source/open edition için official licensing terms FSL/source-available modelini
  açıklar; service'in permissive OSS olduğu varsayılmaz: [Dart repository](https://github.com/powersync-ja/powersync.dart),
  [service repository](https://github.com/powersync-ja/powersync-service),
  [licensing terms](https://powersync.com/legal/licensing-terms).
- **[INFERRED]** Self-host çıkış seçeneğidir, fakat “SDK değiştirilebilir” eşitliğinde değildir. Exit package source
  PostgreSQL, package/stream definitions, PowerSync bucket/checkpoint mapping, upload API records, unresolved conflicts,
  tombstones, local operation schema, Auth/JWKS mapping, object/audit/floor manifests ve encryption key references
  taşımalıdır.
- **[OPEN]** PowerSync cloud-to-self-host data export, bucket rebuild completeness, historical conflict/operation
  preservation, license transition and clean-room import acceptance planı satın alma/ADR öncesi doğrulanmalıdır.

## 9/16 — AI-operability and owner-safe operations

PowerSync custom sync code'yu azaltabilir ama operational surfaces'i çoğaltır: stream DSL, source schema, RLS mirror,
upload API, queue result mapping, checkpoint/lag, service version, Cloud billing, Mongo/self-host, JWT/JWKS,
encryption key, Supabase Storage/object manifest, package builder ve protected audit/floor.

### 9.1 Machine-readable/AI-safe boundaries

1. Stream definitions, RLS policy matrix, package manifest, API operation schema, client capability and migration
   versionleri version-controlled and diffable olmalı.
2. Every stream must name source relation, selected columns, user/task predicate, classification, retention/TTL,
   expected generation, recall/delete semantics and reprocessing plan.
3. Every upload operation must carry stable operation id, client/device generation, actor/session, payload digest,
   expected version, command type and result lookup key.
4. AI task packs must forbid direct PowerSync/Supabase production mutations, service_role, global Storage keys,
   provider billing/account changes, schema destructive changes and silent queue deletion.
5. AI can prepare dry-run stream diff, RLS/stream equivalence report, package closure report, cost worksheet,
   queue/lag dashboard query and restore manifest; independent review/human authority must approve high-consequence effect.
6. No AI or owner may infer “synced/accepted/current” from local row presence, queue empty, checkpoint advancement,
   HTTP 2xx, push delivery, Realtime status or provider backup.
7. Provider/account/billing/region/JWKS/key outage returns HELD/UNKNOWN/UNAVAILABLE with plain-language owner next
   action; manual SQL/SSH repair is not the next action.

### 9.2 Reversal triggers

Finalist B must be reopened or held if:

- RLS and Sync Stream filters cannot be proven equivalent for every user/task/classification boundary;
- uploadData path bypasses Kavriva API or lets PowerSync write high-consequence source rows directly;
- queue blocked/dead-letter semantics can lose, reorder or silently acknowledge operations;
- stream checkpoint cannot bind to package generation, tombstone, recall floor and old-client compatibility;
- PowerSync service outage, account deactivation or billing restriction lacks safe hold/read-only behavior;
- encryption/key invalidation, background iOS, process death or migration requires owner debugging;
- self-host/cloud exit cannot preserve source data, streams, operations, conflicts, tombstones and negative floor;
- real-device Android/iOS accessibility/platform evidence remains absent;
- total safe recurring cost is beyond owner-approved ceiling or exact overage is [UNVERIFIED].

## 10/16 — Frozen equal-comparison fixture

This fixture is identical to DEBATE-009 Requirements Synthesis and Mobile Platform Failure Research. It is not final
product/commercial limits.

| Dimension | Frozen comparison condition |
|---|---|
| Consumer surfaces | Android and iOS phone-focused Flutter consumer app; browser Internal Operations. |
| Publication order | Android first, iOS later; both must preserve same data/safety/recovery contract. |
| Horizon/cadence | First release + 24 months maintenance; four release windows/year plus safety-critical correction when needed. |
| MAU | 1,000 launch; 10,000 growth; 50,000 stress. |
| Monthly workload | Two compact task package transfers/MAU; optional media 10% at 100 MB; 0.5 new user photo at 3 MB. |
| Constrained Android | Android 10/API 29, 64-bit, 4 GB RAM, 64 GB storage, 2 GB free. |
| Main Android | Android 13+, 6 GB RAM, 128 GB. |
| iOS | Oldest iOS 16.4-capable profile and current non-Pro device at release window. |
| Network | Wi-Fi 50 Mbps; ordinary cellular 10 Mbps; constrained 1 Mbps, 300 ms, 5% loss; 72-hour offline. |
| Transfer/data | Selected motorcycle/variant + one task; compact safety core target 12 MB; optional media 150 MB; cache 250 MB; unrelated catalog 2 GB never default. |
| Consent | Downloads above 25 MB cellular require explicit user choice; safety core cannot be split to evade consent. |
| Local data | 3/10 motorcycles; 250/2,000 history/evidence; 50/500 photos at 3 MB; 100/1,000 notes; 20/200 pending operations; 3/30 conflicts. |
| Failure injection | Interrupt/kill/restart/lock/call/Doze/force-quit; clock change/restore; corrupt package; source correction/withdrawal/recall; key loss; schema migration; billing/provider outage. |
| Accessibility | Turkish TalkBack/Switch Access and VoiceOver/Switch Control; every pending/paused/failed/conflict/stale/unknown/blocked/complete state. |

The same fixture means PowerSync cannot claim selective sync by testing a smaller catalog, omit 2 GB negative proof,
skip iOS, or count a stream callback as recall evidence. All numeric values are comparison constants only.

## 11/16 — Equal EQ coverage: repository/product scenarios

All rows below use the frozen fixture in Section 10 and the requirements synthesis EQ-01 through EQ-18. The disposition
is documentary: no executable implementation or real-device evidence exists, so all rows are HELD. A row can become PASS
only after the same manifest, operation, user-state and recovery evidence is produced; a missing boundary becomes
REJECT-IF-UNMITIGATED.

| ID | Same-fixture failure injection | Finalist B expected path | Evidence gap / disposition |
|---|---|---|---|
| EQ-01 | Selected motorcycle/task against unrelated 2 GB catalog; compact core 12 MB | Sync Stream predicate and subscription scope request only selected motorcycle/variant/task rows; optional media separate; source/API refuses general catalog query. | Stream SQL, RLS mirror, bucket/row usage and actual transfer manifest not exercised. [HELD]; unbounded stream is [REJECT-IF-UNMITIGATED]. |
| EQ-02 | Compact package transfer interrupted/corrupt/digest failure | PowerSync local transaction/checkpoint must not advance into incomplete stream state; app-owned package staging verifies manifest/digest/dependency closure and retains last complete package. | PowerSync stream checkpoint is not proof of Kavriva package atomic promotion; process-kill/peak-space evidence absent. [HELD]. |
| EQ-03 | Wrong-base/out-of-order/missing delta | Source/API or stream metadata declares exact base/target package generation; mismatch pauses stream or requests full compact reissue; no closest-base merge. | Sync Streams/checkpoint does not automatically implement package base/digest/tombstone fence. Custom reissue/quarantine evidence absent. [HELD]; partial merge is [REJECT-IF-UNMITIGATED]. |
| EQ-04 | 72-hour offline, selected task, no new recall knowledge | Local SQLite serves only bounded cached stream and complete safe closure; token expiry or stale critical generation holds high-consequence progression; teaching/history/safe stop remain where valid. | Exposure window, stream TTL, expiry and API revalidation policy [OPEN]. Offline positive authority is [REJECT-IF-UNMITIGATED]. |
| EQ-05 | Recall while offline; push/Realtime missed | On foreground/network return, API checks current suspension/revocation generation before progression; stream tombstone/delete and local floor prevent stale row or old package from reopening. | PowerSync cannot teach a disconnected client a new recall; tombstone/reprocess/late-upload anti-resurrection not proven. [HELD]. |
| EQ-06 | Network returns during sync; duplicate retry/out-of-order acknowledgement | fetchCredentials refreshes token; queue uploadData sends stable operation id to Kavriva API; API status lookup and generation fence reconcile source/stream state. | Connector/API result mapping, timeout and cross-plane status fixture absent. [HELD]. |
| EQ-07 | Freshness expires during active work | Stream/package has release/freshness context; API revalidation blocks next physical progression and preserves active safe-stop/recovery closure. Queue cannot grant fresh authority. | PowerSync TTL/checkpoint is not product freshness; active-work closure mapping [OPEN]. [HELD]. |
| EQ-08 | Material guide change during active task | New source generation stops old continuation; API/package builder maps current physical state or sends recovery-only state; old stream row remains historical, not current authority. | Safe remap/closure and old-client stream version evidence absent. [HELD]; client-invented reversal [REJECT-IF-UNMITIGATED]. |
| EQ-09 | Device clock rollback/reboot/backup restore | Server generations and PowerSync checkpoint, not client wall clock, control freshness; restored local DB enters RESTORE_QUARANTINE and revalidates source/floor before use. | PowerSync local restore has no automatic Kavriva anti-resurrection floor; clean restore evidence absent. [HELD]. |
| EQ-10 | Old client receives new safety-critical semantic | Stream/API declares minimum app/schema/client capability; unsupported fields stop affected application, while representable history/safe recovery remains visible. | Synced view schema flexibility does not prove semantic capability negotiation or old-client hold. [HELD]; silent unknown field use [REJECT-IF-UNMITIGATED]. |
| EQ-11 | Duplicate high-consequence operation/lost HTTP response | PowerSync operation id reaches Kavriva API; same id/payload returns original result; timeout is OUTCOME_UNKNOWN and status lookup, not blind resubmit. | PowerSync per-client id alone is not protected Kavriva accepted-operation ledger; API implementation/negative test absent. [HELD]. |
| EQ-12 | High-consequence conflict versus low-risk merge | Kavriva API receives expected generation and preserves both sides/holds high-consequence conflict; only explicitly classified low-risk fields may merge. PowerSync default LWW is not used for authority. | Conflict taxonomy, audit/hold UI and 2xx error/dead-letter handling [OPEN]. Universal LWW is [REJECT-IF-UNMITIGATED]. |
| EQ-13 | Cache pressure with active work/pending queue/required attachments | Optional media and re-fetchable inactive stream material are evicted first; active task closure, pending queue, conflicts and required attachments are protected; PowerSync DB cleanup is policy-aware. | PowerSync storage/eviction does not prove Kavriva classification/pinning. 250 MB/peak temporary data real-device evidence absent. [HELD]. |
| EQ-14 | Device loss/replacement with local-only and server-accepted work | Source API ledger distinguishes uploaded/accepted operations from local-only queue; replacement reauth/stream downloads server truth; lost local-only work remains local-loss/held, never invented completion. | PowerSync sees uploaded queue only; account/device migration and object attachment recovery [OPEN]. [HELD]. |
| EQ-15 | Account-light to profile migration with private/shared/conflicting rows | Migration is a Kavriva API operation with scope preview, stable IDs, explicit classification/conflict/attachment state; PowerSync stream user filter changes only after accepted binding. | Supabase Auth user stream and PowerSync subscription switch do not implement migration semantics. [HELD]; silent merge [REJECT-IF-UNMITIGATED]. |
| EQ-16 | Supabase/API/PowerSync outage, quota, billing hold | Queue stops or holds with visible reason; no unbounded retry or false acceptance; app retains safe local/reference/closure state and owner-readable next action. | PowerSync Free deactivation/soft limit, Supabase spend cap gaps and service outage fail-closed runbook not tested. [HELD]. Owner repair is [REJECT-IF-UNMITIGATED]. |
| EQ-17 | Publication racing emergency suspension | Kavriva API commit checks current suspension generation; newer negative generation rejects/holds publication; PowerSync stream only propagates resulting state. | PowerSync checkpoint cannot fence publication; independent negative authority/audit floor [OPEN]. [HELD]. |
| EQ-18 | Cross-plane restore/export/clean-room import | Reconcile Supabase source, private Storage objects, PowerSync stream/bucket/checkpoint, API operation ledger, protected audit and negative floor under one manifest; partial import labeled. | PowerSync bucket backup/rebuild plus DB backup excludes Storage/audit/floor; clean-room export and license/ops evidence absent. [HELD]; “backup succeeded” alone [REJECT-IF-UNMITIGATED]. |

### EQ evidence record required for every row

Each future record must include scenario_id, fixture revision, candidate/client/service versions, platform/device/network/
battery/storage/clock state, stream definition and RLS policy hash, operation/package/schema IDs, pre/post generation/
digest, source/API result, local queue/checkpoint state, user-visible Turkish state, accessibility observation,
object/audit/floor evidence, recovery action, owner/debug dependency and PASS/HELD/REJECT result.

## 12/16 — Equal MPR coverage: mobile-platform failure scenarios

All rows below use the identical Android/iOS/network/data fixture in Section 10 and MPR-01 through MPR-18 from the
Mobile Platform Failure Research. PowerSync transport does not lower the platform evidence bar. All dispositions are
HELD because no implementation/real-device evidence is authorized in this dossier.

| ID | Same-fixture platform failure | Finalist B mitigation/path | Evidence gap / disposition |
|---|---|---|---|
| MPR-01 | Cache cleared/rebuilt under 250 MB budget; durable local state versus purgeable cache | PowerSync synced SQLite projection may be re-synced; app-owned operation ledger, package manifest, required closure and history must be non-purgeable/separate; local row presence is not authority. | Exact table/storage classes, cleanup policy and queue retention not proven. [HELD]; pending/safety data in purgeable cache [REJECT-IF-UNMITIGATED]. |
| MPR-02 | 12 MB compact package interrupted at 50%, wrong digest, promote-time process death | Stream/checkpoint remains at last consistent state; app staging verifies manifest/digest/closure before promote; last complete package remains. | PowerSync checkpoint does not validate cross-row safety closure or object digest; atomic promote/peak-space evidence absent. [HELD]. |
| MPR-03 | History + outbox + media metadata transaction killed/power loss | PowerSync data+ps_crud queue local atomicity helps synced writes; app-owned metadata/object dependencies require one local transaction or explicit recovery state; orphan object quarantined. | Multi-plane local transaction and attachment cleanup not covered by SDK primitive. [HELD]; half-row/duplicate accepted effect [REJECT-IF-UNMITIGATED]. |
| MPR-04 | Flutter lifecycle callback skipped; Android kill/incoming call/task-manager, iOS force-quit | Correctness is committed before callback; PowerSync queue survives ordinary durable commit; foreground restart resumes/reconciles. iOS force-quit/background does not count as completion. | Real process-death/restart matrix and exact queue durability on target SDK absent. [HELD]. Lifecycle-only commit [REJECT-IF-UNMITIGATED]. |
| MPR-05 | Android Auto Backup/iOS restore supplies stale local DB/cache | Restore quarantine, auth/session rebind, current stream/source generation and negative floor reconciliation precede positive use; restored local row is derived. | PowerSync bucket/local SQLite restore and cross-plane floor behavior not built/tested. [HELD]; direct restored authority [REJECT-IF-UNMITIGATED]. |
| MPR-06 | Uninstall/reinstall, possible OS restore, account continuity | New install fetches only after Auth/API rebind; local-only queue loss is truthful; server-accepted operations re-stream; stale token/device binding cannot grant entitlement. | Reinstall/keychain/PowerSync subscription and account-light recovery plan [OPEN]. [HELD]. |
| MPR-07 | Android Keystore/iOS Keychain lock/biometric/passcode/key corruption | PowerSync encryption option plus platform secure key state distinguishes KEY_UNAVAILABLE/AUTH_REQUIRED/INVALIDATED/REKEY; no plaintext fallback; queue held safely. | Key storage/rotation/backup exclusion/upgrade matrix and actual SQLCipher/SQLite3MC build evidence absent. [HELD]; plaintext fallback [REJECT-IF-UNMITIGATED]. |
| MPR-08 | App update/schema migration interrupted, unknown future schema, low space | Synced stream schema/version order is additive; app-owned tables use staged transaction/quarantine; incompatible old client holds; PowerSync protocol view change cannot bypass app migration. | Old/new client, service/source/schema release graph and low-space migration evidence absent. [HELD]; destructive reset [REJECT-IF-UNMITIGATED]. |
| MPR-09 | Android Doze/App Standby; iOS suspend/force-quit; background worker delayed | PowerSync/WorkManager catch-up is best effort; queue remains durable; foreground revalidation completes. iOS partial/failed background fetch cannot be a freshness/recall guarantee. | MPR real-device background and battery/network trace absent. [HELD]; safety depends on worker [REJECT-IF-UNMITIGATED]. |
| MPR-10 | Low battery/thermal/low-power while optional 150 MB media and 12 MB core compete | Required core/safe closure and queue progress are prioritized; optional media pause/cancel; no retry storm; user sees deferred reason. | Scheduler, thermal, media priority and measurement not implemented. [HELD]; optional media blocking safety core [REJECT-IF-UNMITIGATED]. |
| MPR-11 | 1 Mbps/300 ms/5% loss, 72-hour offline, kill during request, duplicate/out-of-order ack | PowerSync FIFO upload queue + operation id sends to Kavriva API; API idempotency/expected generation; unknown lookup; no client optimistic accepted. | API mapping, queue blockage/dead-letter and duplicate evidence absent. [HELD]. HTTP callback authority [REJECT-IF-UNMITIGATED]. |
| MPR-12 | Metered cellular/Low Data Mode; 12 MB core, 150 MB optional, >25 MB consent, 2 GB negative | Stream subscription and object download require app size preview, explicit user consent for >25 MB cellular, optional pause; required closure remains complete; no full catalog stream. | PowerSync service does not itself prove consent/size UI or per-user data budget; network evidence absent. [HELD]; hidden large transfer [REJECT-IF-UNMITIGATED]. |
| MPR-13 | Low storage/removable storage unavailable; old + new package/verify peak space | Local DB/queue/package staging report NEEDS_SPACE; optional material evicts first; pending queue, closure and history protected; partial stream not promoted. | SQLite file/WAL/temp/PowerSync compaction and app eviction behavior not measured on 2 GB free cohort. [HELD]. Silent cleanup [REJECT-IF-UNMITIGATED]. |
| MPR-14 | Device wall clock forward/back/timezone/restore | PowerSync server/checkpoint ordering plus API server time/generation controls; device wall clock is context only; freshness/expiry anomaly holds. | Product freshness/floor and PowerSync clock assumptions not integrated/tested. [HELD]; clock extends authority [REJECT-IF-UNMITIGATED]. |
| MPR-15 | Turkish TalkBack/VoiceOver/Switch Access for pending/paused/failed/conflict/stale/unknown/blocked/complete | Flutter UI maps PowerSync queue/checkpoint/API states to semantic labels, values, hints, announcements and usable actions; color/icon not sole signal. | SDK offers no product accessibility proof; real device AT evidence absent. [HELD]; indistinguishable complete/unknown [REJECT-IF-UNMITIGATED]. |
| MPR-16 | Android capability works; iOS plugin/native/channel/generated registrant asymmetry | Version-pinned PowerSync/SQLite/encryption dependencies, capability detection and owned fallback; domain state portable; Android success cannot release iOS. | Current Flutter/Gradle/CocoaPods/SwiftPM/native ABI/release evidence absent; web beta not substituted. [HELD]; unmaintained critical plugin [REJECT-IF-UNMITIGATED]. |
| MPR-17 | 12 MB core, 150 MB optional media, 250 MB cache, 2 GB unrelated catalog; optional cancel/evict | PowerSync rows/queue stay separate from Supabase Storage object lane; object digest/generation/classification and signed handle; core closure works without optional media; 2 GB stream denied. | Object backup/restore, cache peak, signed URL revoke and classification tests absent. [HELD]; optional media required for safe closure or full catalog default [REJECT-IF-UNMITIGATED]. |
| MPR-18 | Mixed old/new client, new stream/package, pending update, offline recall/suspension, rollback | Stream/API declares client capability, package generation and negative floor; incompatible/stale client holds; current API suspension wins; restored rollback cannot lower floor. | Versioned stream/old-client/reprocess/anti-rollback and real-device evidence absent. [HELD]; mixed generation or rollback resurrection [REJECT-IF-UNMITIGATED]. |

### MPR evidence record required for every row

Each record must include MPR id, exact Flutter/PowerSync/SQLite/encryption package versions, Android/iOS device cohort,
OS state, lifecycle callback trace, process/worker result, network/battery/storage/clock values, package/stream/checkpoint/
operation IDs, key state, schema version, accessibility observation, source/API/floor evidence, user-visible state,
recovery path, owner/debug dependency and PASS/HELD/REJECT disposition.

## 13/16 — Equal pass/hold/reject rules and current disposition

### Documentary PASS

Finalist B can be marked PASS for an individual scenario only when all of the following are available:

1. official primitive is stated with its actual boundary, not a marketing extrapolation;
2. PowerSync stream, RLS, upload API and Supabase source configuration are inspectable and version-pinned;
3. same frozen fixture runs on constrained/main Android and the iOS later gate has an equivalent plan/evidence;
4. local operation/package/checkpoint/generation/digest state is exportable;
5. user-visible Turkish state distinguishes complete, pending, paused, failed, conflict, stale, unknown and blocked;
6. duplicate/timeout/process-death/restore/recall/delete/key/migration/outage behavior preserves truth;
7. accessibility, recovery, cost, owner-runbook and exit evidence is independent from the implementation claim.

### Mandatory HOLD

Finalist B remains HELD when stream/RLS equivalence, high-consequence API path, protected floor, iOS/background,
encryption/key, schema/version, pricing/overage, self-host/license, cross-plane restore/exit or real-device evidence is
missing. That is the current state of all 36 rows in this no-code dossier.

### Reject-if-unmitigated

Reject the affected B usage if:

- PowerSync client or service can directly mutate canonical high-consequence Supabase rows;
- service_role/global Storage key reaches client, PowerSync config exposed to client, repository, logs or AI context;
- a stream filter/RLS policy mismatch exposes another tenant/user/task/classification;
- queue empty/checkpoint/HTTP 2xx/push/Realtime event is shown as current authority or accepted operation;
- backend uses silent high-consequence LWW or discards one side of conflict;
- recall/delete depends solely on a live stream, push, background job or local delete;
- old package/client/backup can re-enter authority or recreate deleted/recalled/accepted state;
- blocked FIFO/dead-letter silently loses/reorders operations or makes unknown look accepted;
- encryption key failure falls back to plaintext or silently loses ciphertext;
- background/iOS worker is required for correctness;
- billing/service outage requires nontechnical owner SQL/SSH/provider-console repair;
- self-host/cloud export cannot preserve source data, stream config, bucket/checkpoint state, conflicts, tombstones,
  operation ledger, object bytes, audit/floor and key references;
- exact total safe cost, overage/soft-limit exposure or exit contract remains unbounded and [UNVERIFIED].

No weighted score can mask a reject condition.

## 14/16 — Cost, data-usage and exit worksheet (no purchase)

### 14.1 Mandatory/deferrable/optional/scale-triggered

| Cost class | Finalist B items |
|---|---|
| Mandatory | Supabase PostgreSQL/Auth/private Storage/API runtime; PowerSync client package; monitoring/backup/audit/floor; Flutter Android/iOS build/store/device costs. |
| Deferrable | PowerSync Cloud Pro/Team, version locking, private endpoint, custom write checkpoints, PITR, extra observability, independent object/audit custody. |
| Optional | 150 MB media, galleries/video, high-frequency background refresh, Realtime/push hints, rich derived projections. |
| Scale-triggered | PowerSync synced/hosted overage, peak clients/instances; Supabase egress/compute/PITR/Storage; API workers; self-host Mongo/LB/replicator; audit/object retention. |

### 14.2 Data usage behavior

- Sync Streams can reduce unrelated catalog transfer only when predicates, subscription lifecycle, filters and stream
  reprocessing are correct.
- Auto-subscribe false and TTL default 24h are not Kavriva retention/deletion policy.
- Local queue, retries, stream checkpoint, reprocessing and API status calls can multiply network usage; the 2 GB/30 GB
  pricing line is not the same as task package bytes or Supabase egress.
- Optional media must be separate from rows/stream, size-previewed and user-cancelable; source Storage egress/object
  request costs are not included in PowerSync pricing.
- Exact 24-month MAU/data/egress bill for the frozen workload is [UNVERIFIED] until stream cardinality, update
  frequency, queue retry, object access, Supabase plan and PowerSync deployment are measured/priced together.

### 14.3 Exit manifest

A safe B exit package must include:

1. Supabase logical PostgreSQL export/current/history/operation rows and schema/config versions;
2. package/stream definitions, source filters, casts, bucket/checkpoint mapping, reprocessing order and client capability;
3. PowerSync service/bucket metadata and unresolved conflict/dead-letter/queue state;
4. operation IDs, accepted/rejected/held/unknown results, tombstones and deletion/recall floors;
5. Supabase Storage object bytes, digest/generation/classification/lineage and quarantine/finalization state;
6. protected audit and non-restorable negative/security/deletion/accepted-operation/migration floor;
7. Auth/JWKS/session/security-epoch mapping without raw secret export;
8. local SQLite/package manifest schema, encryption/key references, migration history and old-client support;
9. clean-room import result with partial/quarantine labels and reconciliation manifest;
10. license/terms review and service replacement or self-host operation runbook.

PowerSync client Apache-2.0 alone does not prove this exit. Service FSL/source-available terms, Cloud export details,
Mongo bucket state and custom upload API records remain [OPEN]/[UNVERIFIED] until evidence.

## 15/16 — Evidence gates before an ADR or user decision

### Contract and architecture gates

1. Write a candidate-neutral package/operation state contract mapping each EQ/MPR row to PowerSync stream/checkpoint,
   local SQLite, Kavriva API, Supabase source, Storage object and protected floor.
2. Produce a stream/RLS equivalence matrix by tenant/user/task/role/classification with explicit deny tests.
3. Prove uploadData never bypasses Kavriva API and high-consequence API operations use operation id, expected generation,
   status lookup, protected audit and conflict hold.
4. Define tombstone/delete/recall/anti-resurrection and old-client/restore floor independent of stream delivery.
5. Define service outage, queue poison/dead-letter, billing/deactivation, JWKS/key failure and API unknown states.

### Platform and security gates

6. Android API 29/main and iOS oldest/current real devices with process kill, background, force-quit, Doze, low storage,
   network loss, 72h offline, restore, key invalidation and accessibility.
7. PowerSync encryption path, key provisioning/rotation/rekey/delete, backup exclusion and reinstall/restore.
8. Source schema/stream/app/API migration order with interrupted migration and old-client mixed-release quarantine.
9. Supabase Data API exposure/grants, RLS USING/WITH CHECK/SELECT policies, views, storage permissions and service_role
   isolation review per current Supabase skill.
10. Object/audit/floor independent custody and cross-plane restore/export/clean-room evidence; DB/PowerSync backup alone
    is insufficient.

### Cost/exit/AI gates

11. Reprice current PowerSync and Supabase pages at approval time; model 1k/10k/50k MAU with retries, stream updates,
    optional media and outage replays. Any unpriced total is UNVERIFIED.
12. Compare Cloud Pro/Team versus self-host Mongo/replicator/LB/backup/monitoring and license terms; no soft limit is
    called a hard cap.
13. Run an AI task simulation with bounded context, dry-run stream diff, RLS equivalence, package closure, queue/status
    incident and restore manifest; no unrestricted credentials.
14. Produce clean-room exit packet and identify who can operate it without nontechnical owner debugging.

## 16/16 — Candidate conclusion: no winner

Finalist B has a legitimate documentary basis:

- PowerSync provides a stronger off-the-shelf partial-sync/local-queue/checkpoint transport than provider-native
  Realtime/cache-only.
- Sync Streams can support the DEC-0023 data-efficient selected-task goal when filters, stream lifecycle and RLS
  equivalence are independently proven.
- Local SQLite + upload queue gives a durable transport foundation for offline user work, with operation id and backend
  idempotency requirements visible in official docs.
- Supabase remains a workable source/Auth/private Storage direction under DEC-0035 if all high-consequence effects
  remain behind Kavriva API.

The unresolved burden is material:

- PowerSync backend is conflict-unopinionated; high-consequence semantics remain Kavriva API work.
- Stream/checkpoint does not equal package safety closure, freshness, recall, delete/tombstone, anti-resurrection,
  protected audit or accepted-operation floor.
- RLS is upload defense; Sync Streams are download filtering; their equivalence must be maintained as policy/schema
  changes.
- Service outage, queue blocking/dead-letter, Cloud billing soft limits, Supabase costs and owner-readable recovery
  remain open.
- Cloud/self-host choice, FSL service license, Mongo/replicator/bucket backups, version locking and clean-room exit
  are not free capabilities.
- Encryption/key lifecycle, background/iOS, migration and accessibility remain platform evidence gates.

**Disposition:** HELD — candidate evidence pending.  
**Decision:** NO WINNER — no implementation / no purchase / no Phase-5 ADR from this dossier.

## Primary sources

### PowerSync

- [Dart/Flutter package](https://pub.dev/packages/powersync)
- [Flutter SDK reference](https://docs.powersync.com/client-sdks/reference/flutter)
- [Sync Streams overview](https://docs.powersync.com/sync/streams/overview)
- [Client-side backend integration](https://docs.powersync.com/configuration/app-backend/client-side-integration)
- [Writing client changes](https://docs.powersync.com/handling-writes/writing-client-changes)
- [Handling update conflicts](https://docs.powersync.com/handling-writes/handling-update-conflicts)
- [Handling validation errors](https://docs.powersync.com/handling-writes/handling-write-validation-errors)
- [Consistency](https://docs.powersync.com/architecture/consistency)
- [Supabase Auth integration](https://docs.powersync.com/configuration/auth/supabase-auth)
- [RLS and Sync Streams](https://docs.powersync.com/integrations/supabase/rls-and-sync-streams)
- [Implementing schema changes](https://docs.powersync.com/maintenance-ops/implementing-schema-changes)
- [Deploying schema changes](https://docs.powersync.com/maintenance-ops/deploying-schema-changes)
- [Data encryption](https://docs.powersync.com/client-sdks/advanced/data-encryption)
- [Background syncing](https://docs.powersync.com/client-sdks/advanced/background-syncing)
- [Performance and limits](https://docs.powersync.com/resources/performance-and-limits)
- [Self-hosting overview](https://docs.powersync.com/maintenance-ops/self-hosting/overview)
- [Self-host deployment architecture](https://docs.powersync.com/maintenance-ops/self-hosting/deployment-architecture)
- [Pricing](https://powersync.com/pricing)
- [Licensing terms](https://powersync.com/legal/licensing-terms)
- [Dart SDK repository](https://github.com/powersync-ja/powersync.dart)
- [PowerSync service repository](https://github.com/powersync-ja/powersync-service)

### Supabase

- [Supabase changelog](https://supabase.com/changelog.md)
- [PowerSync partner integration](https://supabase.com/partners/integrations/powersync)
- [User sessions](https://supabase.com/docs/guides/auth/sessions)
- [Realtime authorization](https://supabase.com/docs/guides/realtime/authorization)
- [Database changes](https://supabase.com/docs/guides/realtime/subscribing-to-database-changes)
- [Database backups](https://supabase.com/docs/guides/platform/backups)
- [Data API security/exposure](https://supabase.com/docs/guides/api/securing-your-api)
- [Postgres RLS](https://supabase.com/docs/guides/database/postgres/row-level-security)
- [Storage access control](https://supabase.com/docs/guides/storage/security/access-control)
- [Tables not automatically exposed breaking change](https://supabase.com/changelog/45329-breaking-change-tables-not-exposed-to-data-and-graphql-api-automatically)
- [Realtime schema lock breaking change](https://supabase.com/changelog/realtime-schema-locked-down-against-modification)
- [Supabase Auth URL self-host breaking change](https://supabase.com/changelog/47093-self-hosted-supabase-api-external-url-to-include-auth-v1)
- [Supabase self-host Envoy breaking change](https://supabase.com/changelog/48048-self-hosted-supabase-envoy-becomes-the-default-api-gateway-breaking-change)

### Platform and local storage

- [Android process lifecycle](https://developer.android.com/guide/components/activities/process-lifecycle)
- [Android Auto Backup](https://developer.android.com/identity/data/autobackup)
- [Android Doze/App Standby](https://developer.android.com/training/monitoring-device-state/doze-standby)
- [Android persistent work](https://developer.android.com/develop/background-work/background-tasks/persistent)
- [Android network state](https://developer.android.com/develop/connectivity/network-ops/reading-network-state)
- [Android KeyPermanentlyInvalidatedException](https://developer.android.com/reference/android/security/keystore/KeyPermanentlyInvalidatedException)
- [Apple files/directories](https://developer.apple.com/documentation/technologyoverviews/files-and-directories)
- [Apple background execution](https://developer.apple.com/documentation/uikit/extending-your-app-s-background-execution-time)
- [Apple background URLSession](https://developer.apple.com/documentation/foundation/urlsessionconfiguration/background(withIdentifier:))
- [Apple keychain accessibility](https://developer.apple.com/documentation/security/restricting-keychain-item-accessibility)
- [Apple NWPath](https://developer.apple.com/documentation/network/nwpath)
- [Flutter AppLifecycleState](https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html)
- [Flutter common architecture](https://docs.flutter.dev/app-architecture/concepts)
- [Flutter platform channels](https://docs.flutter.dev/platform-integration/platform-channels)
- [SQLite WAL](https://www.sqlite.org/wal.html)

Bu source inventory candidate capability sınırlarını destekler; source'ta olmayan safety, recovery, pricing total,
license, owner-operability veya exit sonucu [INFERRED], [OPEN] veya [HELD] bırakılmıştır.
