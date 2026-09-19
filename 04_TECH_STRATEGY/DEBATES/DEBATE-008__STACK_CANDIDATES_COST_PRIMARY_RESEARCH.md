# DEBATE-008 — Stack candidates & cost: primary research

**Durum:** Araştırma taslağı — Phase 4 / NO-CODE / karar yok / kazanan yok  
**Araştırma tarihi:** 2026-09-18 (Europe/Istanbul)  
**Kapsam:** Supabase, Firebase/Firestore, yönetilen PostgreSQL + bağımsız API + object storage ailesi, Appwrite Cloud/self-host, Cloudflare Workers/D1/R2 ve ham self-host baseline.  
**Yetki sınırı:** Bu belge provider hesabı açmaz, satın alma yapmaz, kod/prototip üretmez ve ADR/verdict oluşturmaz. Fiyatlar resmi sayfalarda bu tarihte görülen USD liste değerleridir; dinamik olabilir. TRY dönüşümü, vergi, FX, kart/banka komisyonu ve mağaza ücretleri tahmin edilmemiştir.

## 1. Karar bağlamı ve ortak değerlendirme fixtürü

Bu araştırma aşağıdaki proje kararlarına bağlıdır:

- `DEC-0030`: solo owner ve sınırlı bütçe; free path, resmi güncel fiyat, hard-cap/overage, çıkış, vergi/FX belirsizliği; maliyet sınıfları **mandatory / deferrable / optional / scale-triggered** olarak ayrılmalı.
- `DEC-0032`: Android-first, iOS later; TRY 2.000–3.000/ay yalnızca ileriye dönük planlama tavanıdır, harcama yetkisi değildir. Mağaza/ödeme/cihaz ücretleri bu araştırmanın provider maliyetlerinden ayrıdır.
- `DEC-0033`: Flutter consumer-mobile yönü onaylıdır; implementation/ADR değildir.
- `DEC-0034`: canonical transactional authority provider-neutral olmalı; genel istemci doğrudan canonical DB/object storage yetkisi almamalı; server/API mediation, bounded versioned offline package, durable local operation/reconciliation, protected audit, rebuildable projections, tested backup/restore/export/exit zorunludur.
- DEBATE-007: backup/export başarı sinyali recovery proof değildir; restore quarantine ve non-restorable floor gerekir; account/billing/region/provider failure ve maliyet runbook'ları ayrı gözlenmelidir.

Her aday şu ortak fixture ile okunmuştur:

1. **Flutter/browser:** resmi SDK veya yalnızca HTTPS API olup olmadığı.
2. **Transactional integrity:** transaction/constraint/atomic batch sınırı; concurrency ve offline conflict davranışı.
3. **API ve authorization boundary:** canonical authority'ye erişimin nerede durduğu; RLS/rule/permission kaçakları.
4. **Offline/sync:** kapalı paket, durable outbox, reconnect ve conflict çözümünün built-in mı yoksa proje işi mi olduğu.
5. **Object plane:** private/public varsayılan, signed URL, bearer token, CDN cache, object–DB consistency.
6. **Backup/PITR/restore/export/exit:** DB ve object kapsamı ayrı; restore sonrası quarantine ve doğrulanabilir çıkış.
7. **Region/data residency:** seçilebilir region, değişmezlik, jurisdiction garantisi ve Türkiye'ye ilişkin boşluk.
8. **Account/billing outage, cap/overage:** gerçek hard cap ile yalnızca alert arasındaki fark.
9. **Logs/monitoring, AI-operability, maintenance:** owner'ın kanıt üretebilmesi ve AI destekli işlemin güvenli sınırı.
10. **Maliyet:** free path, ilk üretim eşiği, usage/overage, vergiler ve FX belirsizliği.

Kanıt etiketleri:

- **[CONFIRMED]** resmi/primary dokümanda açıkça belirtilen mevcut davranış veya fiyat.
- **[INFERRED]** resmi primitive'lerden mimari sonuç; ADR öncesi test gerekir.
- **[OPEN]** resmi kaynakta yeterince kesinleşmeyen veya proje politikasına bağlı soru.

## 2. Kısa aday matrisi

| Aday | Transaction / canonical boundary | Auth ve istemci | Offline/sync | Object / recovery | Region / billing cap | İlk okuma |
|---|---|---|---|---|---|---|
| **Supabase managed** | [CONFIRMED] PostgreSQL transaction/constraint gücü; Data API + RLS. [INFERRED] Genel istemci canonical authority olmamalı; server/API mediation gerekir. | Dart/Flutter ve JS/web SDK mevcut. `anon` + RLS dikkat ister; `service_role` yalnızca server. | [OPEN] SDK tek başına kapalı conflict-safe domain sync sağlamaz; outbox/package/reconciliation proje işidir. | Storage private/public/signed URL; DB backup Storage object'larını kapsamaz. Daily backup/PITR plan bağımlı; pg_dump/CLI çıkış yolu. | Primary region seçilir; Türkiye region'ı yok. Pro spend cap sınırlı; compute/PITR vb. kapsam dışı kalabilir. | Güçlü relational core; RLS/service-role, object backup ve usage cap ayrıntıları hard gate. |
| **Firebase/Firestore** | [CONFIRMED] transaction ve batched write atomiktir; transaction offline fail olabilir. [INFERRED] Rules client boundary'si canonical authority için tek başına yeterli kabul edilmemeli. | Resmi Flutter plugin'leri ve web SDK. Firestore server SDK'ları Security Rules'ı bypass eder; IAM/service path ayrı kontrol ister. | Android/iOS offline persistence; web varsayılan kapalı. Aynı belge concurrent local change LWW. | Firestore backup/PITR/export GCS'ye ve billing'e bağlı; Storage ayrı plan/Blaze. Export provider formatına bağlı. | Regional/multi-region; location değişmez. Spark quota fail-closed; Blaze usage overage; budget alert hard cap değildir. | Hızlı SDK ve offline avantajlı; LWW, server bypass, billing lock ve export coupling hard gate. |
| **Managed PostgreSQL + independent API + object** (Neon/Render/R2 temsilcileri) | [CONFIRMED] PostgreSQL en güçlü transaction/constraint çekirdeği; API boundary tamamen ayrı tasarlanır. | Flutter/browser yalnızca API/presigned URL görür; auth/policy projenin sorumluluğu. RLS veya server-only DB bağlantısı zorunlu tasarım kararı. | [INFERRED] En temiz canonical/API ayrımı; offline protocol, idempotency ve conflict policy tamamen bizim işimiz. | Neon/Render DB backup/PITR ile R2 object lifecycle/consistency ayrı plane; cross-plane manifest gerekir. | Servis başına region/billing/outage; Neon limitleri alert ağırlıklı, R2/Render metered; kompozit fatura ve incident karmaşıktır. | Portability ve sınır netliği güçlü; üç ayrı vendor operasyonu ve API/auth bakım yükü yüksek. |
| **Appwrite Cloud / self-host** | [CONFIRMED] TablesDB transaction ve native PostgreSQL seçenekleri; Appwrite permission modeli. | Resmi Flutter/Web SDK; client/server permission varsayımları farklı. Server SDK/Console permission kontrolünü atlayabilir. | Resmi offline rehberi local store + push/pull + custom conflict ister; built-in closed sync değildir. | Bucket/file permission ve bearer file token; Cloud backup plan bağımlı. Self-host DB/file backup/DR owner'a ait. | Frankfurt/NYC/Sydney/SFO/Singapore/Toronto; Türkiye yok. Pro budget cap capability'leri durdurabilir. | Bütünleşik ürün ve explicit budget cap cazip; permission bypass, offline custom ve self-host operasyonu hard gate. |
| **Cloudflare Workers/D1/R2** | [CONFIRMED] D1 `batch()` sıralı atomic rollback semantics; tek DB single-threaded, 10 GB paid sınırı. [INFERRED] Çok-domain canonical authority için kapasite/restore sınırı risk. | Flutter/browser için HTTPS Worker; built-in Auth/user policy yok. API, session ve authorization tamamıyla projeye ait. | Custom package/outbox/reconciliation; D1 senkron çözümü yok. | R2 strong consistency (direct API), 30d/7d D1 Time Travel destructive restore; object backup ayrıca kurulmalı. | D1/R2/Workers metered; free quota aşımında hata, paid'de overage. Alert hard cap değildir; jurisdiction yaratımda seçilir. | İlginç counterfactual; DB sınırı, auth yokluğu ve destructive restore nedeniyle şu aşamada hold. |
| **Raw self-host baseline** (DO VM + PostgreSQL + MinIO temsilcisi) | [CONFIRMED] PostgreSQL transaction/constraint; tüm API/auth/operasyon owner'ın. | Flutter/browser kendi API'sine bağlanır; doğrudan DB/object erişimi yasaklanır. | Custom ve tamamen owner-maintained. | WAL/base backup/restore, MinIO replication/versioning, object–DB consistency ve drills owner işi. | VM planı öngörülebilir; backup/volume/egress/support ayrı. Region/DR/topology owner seçimi. | En yüksek exit/control, en yüksek bakım ve recovery sorumluluğu; yalnızca baseline/gelecek option. |

Bu tablo sıralama veya kazanan ilanı değildir. Tüm adaylar için mevcut durum **candidate / evidence pending / ADR later**'dır.

## 3. Aday dosyaları

### 3.1 Supabase managed

#### Yetkinlik ve sınır

- **[CONFIRMED]** Supabase, PostgreSQL üzerine Database, Auth, Storage, Realtime ve Edge Functions koyar: [Database overview](https://supabase.com/docs/guides/database/overview). PostgreSQL transaction, foreign key, unique/check constraint ve server-side function primitives canonical domain için güçlüdür.
- **[CONFIRMED]** Data API rolleri (`anon`, `authenticated`, `service_role`) ve RLS birlikte authorization sınırı oluşturur: [Securing your API](https://supabase.com/docs/guides/api/securing-your-api). RLS açılmamış exposed table, grants ile yetkili rollere açık kalabilir; policy eklemek grant'i kaldırmaz: [RLS](https://supabase.com/docs/guides/database/postgres/row-level-security).
- **[CONFIRMED]** `service_role` RLS'i bypass eder; client'a konulamaz. Bu nedenle kanonik yazma, restore/migration, audit ve admin işleri server-side API/Edge Function/independent API boundary'sinde kalmalıdır: [service-role troubleshooting](https://supabase.com/docs/guides/troubleshooting/why-is-my-service-role-key-client-getting-rls-errors-or-not-returning-data-7_1K9z).
- **[CONFIRMED]** Security-definer function gerekiyorsa `search_path=''`, schema-qualified relation ve dar `EXECUTE` grant gerekir; fonksiyon API üzerinden reachable olabilir: [Database functions](https://supabase.com/docs/guides/database/functions). **[INFERRED]** Domain authority için “RLS var, o halde direct client güvenli” varsayımı kabul edilemez.
- **[CONFIRMED]** Yeni projelerde yeni table'ların otomatik expose edilmemesine geçiş duyurulmuştur; tüm projelerde enforcement takvimi 2026 içinde değişmektedir: [platform changelog](https://supabase.com/changelog?tags=platform). Migration zamanında grants/OpenAPI surface yeniden doğrulanmalıdır.

#### Flutter/browser, offline ve object plane

- **[CONFIRMED]** Resmi Dart/Flutter client ve JavaScript client vardır: [Dart reference](https://supabase.com/docs/reference/dart/introduction), [JavaScript reference](https://supabase.com/docs/reference/javascript/introduction). Browser erişimi Data API/Realtime veya bizim API'miz üzerinden yapılabilir.
- **[OPEN]** Supabase client SDK'larının bu proje için versioned closed offline package, durable operation log, idempotency ve high-consequence conflict policy sağladığına dair kabul edilebilir kanıt yoktur. Offline consumer experience ayrıca tasarlanmalı; LWW'yi canonical policy olarak varsaymamalıdır.
- **[CONFIRMED]** Storage object'ları `storage.objects` RLS ile kontrol edilir; private bucket varsayılandır, public bucket read control'ü bypass eder: [Storage buckets](https://supabase.com/docs/guides/storage/buckets/fundamentals), [Storage access control](https://supabase.com/docs/guides/storage/security/access-control).
- **[CONFIRMED]** Signed URL bearer token'dır; CDN cache token süresinden daha uzun süre stale içerik sunabilir ve token revocation sınırlıdır: [Serving downloads](https://supabase.com/docs/guides/storage/serving/downloads). Object sınıflandırma, digest/generation ve revoke/delete politikasını API boundary'si sahiplenmelidir.

#### Backup, PITR, restore ve çıkış

- **[CONFIRMED]** Free automatic backup sağlamaz; Pro/Team/Enterprise günlük backup planına sahiptir. Pro günlük backup retention 7 gün, Team 14 gün, Enterprise 30 güne kadar; database backup Storage object'larını kapsamaz: [Backups](https://supabase.com/docs/guides/platform/backups).
- **[CONFIRMED]** PITR retention 7/14/28 gün için resmi dokümanda yaklaşık `$100/$200/$400` aylık seviyelerle, Small compute gereksinimiyle anlatılır; exact cost approval sırasında pricing table'dan yeniden okunmalıdır. Restore sırasında proje erişilemez olabilir; project silinirse data ve backups kalıcı silinir: [Backups](https://supabase.com/docs/guides/platform/backups).
- **[CONFIRMED]** Logical export için CLI `db dump`/`pg_dump` yolu vardır; free path'te düzenli export owner'ın sorumluluğudur. [INFERRED] Bu, Storage export ve cross-plane consistency manifesti olmadan tam exit/recovery proof değildir.
- **[CONFIRMED]** Branching ayrı Supabase instance ve ayrı API credentials üretir; free plan branching'i içermez: [Branching](https://supabase.com/docs/guides/deployment/branching). Branch backup veya production restore substitute değildir.
- **[CONFIRMED]** Managed-to-self-host restore DB schema/data/roles ile sınırlı olabilir; Storage object'ları ve Functions otomatik gelmez: [Restore from platform](https://supabase.com/docs/guides/self-hosting/restore-from-platform). Exit drill DB + object + secret rotation + policy/identity mapping olarak yazılmalıdır.

#### Region, outage, cap, logs ve bakım

- **[CONFIRMED]** Bir primary region seçilir; seçim primary project data'sının konumunu etkiler. Avrupa seçenekleri Frankfurt, Ireland, Paris, Zurich, London vb.; Türkiye region'ı listede yoktur: [Regions](https://supabase.com/docs/guides/platform/regions). Region seçimi tek başına hukuki uyum kanıtı değildir.
- **[CONFIRMED]** Pro spend cap, belirli usage kalemlerini quota sonrasında durdurabilir; compute, branching compute, read-replica compute, custom domain, IOPS/throughput, IPv4, log drain, MFA phone ve PITR gibi kalemler cap dışında kalabilir. Cap kapalıysa overage faturalanır: [Cost control](https://supabase.com/docs/guides/platform/cost-control).
- **[CONFIRMED]** Free project bir hafta inactive kalırsa pause olabilir; free plan 2 active project ile sınırlıdır. Billing FAQ vergi/VAT/GST/indirect tax'ın gerektiğinde uygulanacağını belirtir: [Pricing](https://supabase.com/pricing), [Billing FAQ](https://supabase.com/docs/guides/platform/billing-faq).
- **[CONFIRMED]** Changelog, backup scheduling/restore credentials/logging/Envoy gibi operasyonel değişiklikler gösterir: [Platform changelog](https://supabase.com/changelog?tags=platform). **[INFERRED]** AI-operability iyi bir docs/CLI/API yüzeyine sahip olsa da zamanla değişen defaults için release watch gerekir.

#### Resmi fiyat sinyali (2026-09-18 gözlemi)

- **Free:** `$0/month`; 2 active projects, 50K MAU, 500 MB DB, 5 GB egress, 1 GB file storage; inactive pause riski.
- **Pro:** `$25/month`; ilk project dahil; additional project `$10/month` seviyesinden; 100K MAU üstü `$0.00325/MAU`; 8 GB disk üstü `$0.125/GB`; 250 GB egress üstü `$0.09/GB` seviyeleri; daily backup 7 gün.
- **Compute/PITR:** Micro compute için `$10/month` credit/başlangıç seviyesi ve PITR için yukarıdaki retention maliyeti ayrıca kontrol edilir. Team `$599/month`, Enterprise custom.
- Bu değerler [official pricing](https://supabase.com/pricing) üzerinde dinamik kullanım kalemlerine bölünür; VAT/GST, FX, kart ve vergi dahil edilmiş TRY karşılığı değildir. Spend cap'in bütün faturayı sert biçimde sınırladığı varsayılmamalıdır.

**Adaya özgü hold:** RLS/policy matrix, service-role server boundary, Storage–DB backup closure, PITR/restore quarantine ve billing cap test edilmeden Supabase “production-ready” sayılamaz.

### 3.2 Firebase / Cloud Firestore

#### Transaction, rules ve client boundary

- **[CONFIRMED]** Firestore atomic transactions ve batched writes destekler; transaction concurrent update ile retry olabilir, offline durumda başarısız olur; batched write offline çalışabilir fakat büyük/çoklu retry sınırları vardır: [Transactions](https://firebase.google.com/docs/firestore/manage-data/transactions).
- **[CONFIRMED]** Firestore Security Rules client SDK isteklerini korur; server client libraries tüm Security Rules'ı bypass eder ve IAM ile korunmalıdır: [Rules conditions](https://firebase.google.com/docs/firestore/security/rules-conditions). Rules filtre değildir; query, rule'ın ispatlayabildiği kısıtları içermeli ve sonuç all-or-nothing'dır: [Rules are not filters](https://firebase.google.com/docs/firestore/security/rules-query).
- **[INFERRED]** Bu model public mobile/web client için işe yarasa da canonical high-consequence writes için Rules'ı tek güvenlik sınırı kabul etmemek gerekir. Server/Admin SDK, export/import ve Functions için ayrı API/IAM boundary ve audit gerekir.

#### Flutter/browser, offline ve conflict

- **[CONFIRMED]** Firebase resmi Flutter setup/plugin'leri Android, iOS ve web'i hedefler: [Flutter setup](https://firebase.google.com/docs/flutter/setup). Web SDK de resmi olarak desteklenir.
- **[CONFIRMED]** Android/Apple offline persistence varsayılan olarak açık, web varsayılan olarak kapalıdır; web cache session'lar arasında kalabilir. Aynı belgeye concurrent local değişikliklerde last-write-wins uygulanır: [Offline data](https://firebase.google.com/docs/firestore/enterprise/enable-offline).
- **[INFERRED]** LWW, protected audit veya user-owned durable operation ordering için otomatik olarak kabul edilemez. Bounded package, idempotency key, server ordering ve reconciliation ayrıca tasarlanmalıdır.

#### Object, backup/PITR, export ve region

- **[CONFIRMED]** Firebase Storage Flutter kullanımı için default bucket'lar Blaze planı gerektirebilir; underlying object storage Cloud Storage'dır: [Cloud Storage for Flutter](https://firebase.google.com/docs/storage/flutter/start).
- **[CONFIRMED]** Firestore PITR, backup, restore ve export billing account ister; PITR yakın 7 gün içinde minute-granularity export ve GCS import/export sağlayabilir. Export document read cost üretir ve export formatı Firestore/GCS coupling taşır: [PITR](https://firebase.google.com/docs/firestore/enterprise/use-pitr), [Export/import](https://firebase.google.com/docs/firestore/enterprise/export-import).
- **[CONFIRMED]** Firestore regional veya multi-region location seçilir; location değiştirilemez. Avrupa Frankfurt, Berlin ve `eur3` gibi seçenekler vardır; Türkiye region'ı yoktur: [Locations](https://firebase.google.com/docs/firestore/enterprise/locations). Firestore location, diğer Firebase/Google Cloud servislerinin location'ı değildir.
- **[INFERRED]** Firestore export + GCS object + Auth/Rules/Functions konfigürasyonunun birlikte restore edilmesi provider-specific bir runbook ister; export tek başına clean-room exit değildir.

#### Billing, cap, monitoring ve bakım

- **[CONFIRMED]** Spark `$0` ve payment method istemez; Firestore Standard no-cost seviyeleri 1 GiB storage, 50K reads/day, 20K writes/day, 20K deletes/day, 10 GiB egress/month civarındadır. Blaze pay-as-you-go'dur: [Firebase pricing](https://firebase.google.com/pricing), [Pricing plans](https://firebase.google.com/docs/projects/billing/firebase-pricing-plans).
- **[CONFIRMED]** Firestore location'a göre pay-as-you-go read/write/delete/storage/network fiyatlanır; Iowa örneğinde 100K reads `$0.03`, writes `$0.09`, deletes `$0.01` seviyeleri gösterilir; exact location/plan approval'da yeniden okunmalıdır: [Cloud Firestore pricing](https://cloud.google.com/firestore/pricing).
- **[CONFIRMED]** Cloud Billing budgets alert üretir; budget, kullanım ve harcamayı genel olarak durdurmaz: [Budgets](https://docs.cloud.google.com/billing/docs/how-to/budgets). Preview spend cap yalnızca uygun servislerle sınırlıdır ve Firestore için genel hard cap olarak okunamaz: [Spend caps](https://docs.cloud.google.com/billing/docs/how-to/budgets-spend-caps).
- **[CONFIRMED]** Billing account kapatılır veya Spark'a dönülürse paid products/Cloud Run/Pub/Sub/BigQuery gibi yetenekler kaybolabilir: [Firebase billing plans](https://firebase.google.com/docs/projects/billing/firebase-pricing-plans). Account outage için read-only/export path ve owner alert gerekir.
- **[INFERRED]** Firebase console, Emulator Suite, CLI ve Cloud Monitoring iyi AI-operability yüzeyi sağlar; ancak pricing, release ve Google Cloud project coupling nedeniyle runbook geniştir. Firebase release notes 2026'da ürün ve backend değişimlerini gösterir: [Firebase release notes](https://firebase.google.com/support/releases).

**Adaya özgü hold:** Rules/server bypass matrix, offline LWW'nin yüksek sonuçlu alanlardan dışlanması, Blaze billing hard-cap yokluğu ve Firestore+GCS+Auth clean-room export drill gösterilmeden candidate hold.

### 3.3 Managed PostgreSQL + bağımsız API + object storage ailesi

Bu satır tek bir vendor teklifi değildir. Karşılaştırma için üç resmi, güncel temsilci kullanılmıştır:

- **Neon:** managed PostgreSQL/branch/restore.
- **Render Web Service + (alternatif) Render Postgres:** bağımsız API runtime ve managed DB örneği.
- **Cloudflare R2:** object plane.

Bu bileşenler ayrı hesap, fatura, credential, region ve outage boundary'sidir. Neon+Render+R2 birlikte satın alınmış ya da önerilmiş bir composite quote değildir. Render Postgres yerine başka managed PostgreSQL ve Render Web Service yerine başka API runtime seçilebilir; aynı kabul testleri geçerlidir.

#### Canonical/API boundary

- **[CONFIRMED]** PostgreSQL transaction, isolation, foreign key, unique/check constraint, role ve `pg_dump`/`pg_restore` gibi taşınabilir primitive'ler verir. Canonical write'lar bağımsız API tarafından yapılabilir; Flutter/browser hiçbir DB credential görmez.
- **[INFERRED]** Bu aile, DEC-0034 server/API mediation sınırını en açık ifade eder; fakat auth/session/token rotation, authorization policy, RLS veya server-only DB connection bizim bakımımızdadır. Bir API'nin “çalışıyor” olması policy/audit/recovery kanıtı değildir.
- **[OPEN]** Neon/Render DB ile R2 object commit'i arasında dağıtık transaction yoktur. Object upload, digest/generation, DB manifest, retry/idempotency ve quarantine adımları ayrıca kabul testine bağlanmalıdır.

#### Offline/sync

- **[INFERRED]** Managed PostgreSQL ve bağımsız API, offline protocol'ü dayatmadığı için versioned bounded package + local durable operation log + server idempotency + explicit conflict policy kurmaya izin verir.
- **[OPEN]** Bu özgürlüğün karşılığı proje işi ve bakım maliyetidir; provider SDK'sından hazır sync varsayılmamalıdır. High-consequence domain için LWW ancak açıkça seçilmiş alanlarda kullanılabilir.

#### Neon evidence ve fiyat

- **[CONFIRMED]** Neon PostgreSQL branch/restore/usage-based platformdur. Free seviyede resmi blogda 10 project, project başına 50 CU-hour/month, 0.5 GB/project, 10 branch/project, 5 GB egress gibi limitler yayımlanmıştır: [New usage-based pricing](https://neon.com/blog/new-usage-based-pricing).
- **[CONFIRMED]** Resmi 2025-11-03 price reduction duyurusu Launch için `$0.106/CU-hour`, Scale için `$0.222/CU-hour` seviyelerini gösterir: [Major compute price reduction](https://neon.com/blog/major-compute-price-reduction-on-neon). 2026-09-18'de fiyat sayfası dinamik olduğundan bu değerler “son açık primary rate” olarak tutulmalı; ADR/approval anında hesaplanmalıdır.
- **[CONFIRMED]** PITR/history configurable olup resmi duyuruda 30 güne kadar restore anlatılır; restore API'si timestamp/LSN ile branch restore etmeye yarar: [Point-in-time restore](https://neon.com/blog/announcing-point-in-time-restore), [Restore branch API](https://api-docs.neon.tech/reference/restoreprojectbranch).
- **[CONFIRMED]** Standard PostgreSQL `pg_dump -Fc` ve `pg_restore` ile Neon dışına export yolu vardır: [Export Neon PostgreSQL-compatible database](https://github.com/neondatabase/website/blob/main/content/docs/guides/export-neon-postgres-compatible.md).
- **[CONFIRMED]** Neon organization spending limit resmi duyuruda 80%/100% e-mail alerts olarak anlatılır; automatic suspend “coming soon” şeklindedir, yani bugün genel hard invoice cap değildir: [Organization spending limits](https://neon.com/blog/introducing-organization-spending-limits).
- **[CONFIRMED]** Active regions içinde Frankfurt, London, Singapore gibi seçenekler bulunur; exact active set API'dan okunur: [Neon active regions API](https://api-docs.neon.tech/reference/getactiveregions). Türkiye availability/domicile ayrıca doğrulanmalıdır.

#### Render API/DB evidence ve fiyat

- **[CONFIRMED]** Render Web Service public `onrender.com` endpoint'i olan bağımsız API runtime'dır: [Web services](https://render.com/docs/web-services). API service, auth ve PostgreSQL connection pool owner'ın runbook'unda kalır.
- **[CONFIRMED]** Render Postgres paid plan continuous backup/PITR sağlar; Hobby için 3 gün, Pro+ için 7 gün retention ve recovery yeni DB oluşturup cutover yapar. Free compute ile recovery kısıtları vardır; logical backup `.dir.tar.gz` olarak alınabilir: [PostgreSQL backups](https://render.com/docs/postgresql-backups).
- **[CONFIRMED]** Render region'ları Oregon, Ohio, Virginia, Frankfurt, Singapore gibi seçeneklerdir; mevcut service/database region'ı değiştirmek yerine yeni resource + migration gerekir: [Regions](https://render.com/docs/regions).
- **[CONFIRMED]** 2026 fiyat sayfasında Hobby `$0/month` + compute, Pro `$25/month` + compute, Scale `$499/month` + compute; web service örnekleri Free `$0`, `<1 CPU/512 MB` `$7/month`, `1 CPU/2 GB` `$25/month`; Render Postgres örnekleri Free, `<1 CPU/256 MB` `$6/month`, `<1 CPU/1 GB` `$19/month`; persistent disk `$0.25/GB-month`, bandwidth 5 GB sonrası `$0.15/GB` seviyelerindedir: [Render pricing](https://render.com/pricing).
- **[CONFIRMED]** 2026-08-01'e yayılan fiyat güncellemesi Pro `$25`, Scale `$499` workspace seviyelerini açıklar: [Render pricing update](https://render.com/blog/better-pricing-for-fast-growing-teams).
- **[OPEN]** Render pricing/usage visibility, tüm composite stack için universal hard cap kanıtı değildir. Workspace/service/database/bandwidth/add-on billing ve notification failure test edilmeden “fixed monthly” sayılamaz.

#### Cloudflare R2 object evidence ve fiyat

- **[CONFIRMED]** R2 Standard `$0.015/GB-month`, Infrequent Access `$0.01/GB-month`; Standard free tier 10 GB-month, 1M Class A, 10M Class B; Class A `$4.50/million`, Class B `$0.36/million`, IA retrieval `$0.01/GB`; R2 egress doğrudan free'dir: [R2 pricing](https://developers.cloudflare.com/r2/pricing/).
- **[CONFIRMED]** S3-compatible, Workers API ve REST API vardır. Presigned URL GET/PUT/HEAD/DELETE için 1 saniye–7 gün expiry alabilir; POST multipart desteklenmez ve custom domain ile kullanılamaz: [R2 API](https://developers.cloudflare.com/r2/api/), [Presigned URLs](https://developers.cloudflare.com/r2/api/s3/presigned-urls/).
- **[CONFIRMED]** Direct S3/Worker API strong global consistency hedefler; aynı key'de concurrent writer'da last writer to complete kazanabilir. Custom-domain cache stale object gösterebilir: [R2 consistency](https://developers.cloudflare.com/r2/reference/consistency/).
- **[CONFIRMED]** R2 durability hedefi 99.999999999% annual, availability SLA 99.9% olarak ayrılır; durability backup değildir. Bucket jurisdiction `eu`, `us` veya `fedramp` yaratımda seçilebilir ve sonradan değiştirilemez; location hints best effort'dur: [Durability](https://developers.cloudflare.com/r2/reference/durability/), [Data location](https://developers.cloudflare.com/r2/reference/data-location/).
- **[CONFIRMED]** Lifecycle transition/delete ve incomplete multipart cleanup yapılabilir; versioning/independent export kurulmadan DB restore object state'ini geri getirmez: [Object lifecycles](https://developers.cloudflare.com/r2/buckets/object-lifecycles/).
- **[CONFIRMED]** Cloudflare budget alert bir bildirimdir; genel overage'ı otomatik durdurduğu kanıtı değildir: [Usage-based billing](https://developers.cloudflare.com/billing/understand/usage-based-billing/), [Billable usage](https://developers.cloudflare.com/billing/manage/billable-usage/).

**Adaya özgü hold:** API/auth/policy ownership, Neon/Render backup retention, R2 object version/backup, cross-plane manifest ve üç ayrı vendor outage/billing runbook'u tamamlanmadan aile candidate hold.

### 3.4 Appwrite Cloud / self-host

#### API, permissions, transaction ve SDK

- **[CONFIRMED]** Appwrite resmi Flutter ve Web SDK'leri, Auth, Databases/TablesDB ve Storage sunar: [SDKs](https://appwrite.io/docs/sdks), [Databases](https://appwrite.io/docs/products/databases), [Auth](https://appwrite.io/docs/products/auth).
- **[CONFIRMED]** TablesDB transaction'ları birden fazla database/table operation'ı atomic çalıştırabilir; changed-row conflict transaction'ı fail ettirir. Transaction operation limitleri Free 100, Pro 1.000, Scale 2.500 olarak belirtilmiştir: [Transactions](https://appwrite.io/docs/products/databases/tablesdb/transactions). Native managed PostgreSQL de vardır: [PostgreSQL transactions](https://appwrite.io/docs/products/databases/postgresql/concepts/transactions).
- **[CONFIRMED]** Appwrite permission resource-level'dir; server SDK/Console varsayılan olarak permission check yapmayabilir. Client creator permissions ve server cross-team behavior ayrı okunmalıdır: [Permissions](https://appwrite.io/docs/advanced/security/permissions).
- **[INFERRED]** Appwrite client SDK'sı user-facing CRUD için uygun olsa da DEC-0034 canonical authority için server/API mediation, operation id ve protected audit yine gereklidir; “platform permission” otomatik olarak domain authorization/RLS eşdeğeri değildir.

#### Offline, object ve recovery

- **[CONFIRMED]** Appwrite offline rehberi local store (IndexedDB/LocalStorage/SQLite/RxDB), network detection, push/pull sync ve custom conflict resolution (LWW veya manual) uygulamayı önerir; kapalı built-in offline conflict plane değildir: [Offline data](https://appwrite.io/docs/products/databases/tablesdb/offline).
- **[CONFIRMED]** Bucket/file permissions, file tokens ve chunked upload bulunur; file token bearer secret'tır. Compression/encryption/virus scanning davranışı 20 MB üzeri object'lerde farklılaşabilir: [Buckets](https://appwrite.io/docs/products/storage/buckets), [Permissions](https://appwrite.io/docs/products/storage/permissions), [File tokens](https://appwrite.io/docs/products/storage/file-tokens), [Upload/download](https://appwrite.io/docs/products/storage/upload-download).
- **[CONFIRMED]** Cloud backup/DR retention plan'a bağlıdır; self-managed Appwrite'ta DB ve file backup, monitoring, update ve disaster recovery owner'a aittir: [Backups](https://appwrite.io/docs/advanced/security/backups), [Self-hosting](https://appwrite.io/docs/advanced/self-hosting).
- **[OPEN]** Cloud export/import kapsamı tüm auth/permissions/functions/object metadata'sını tek, provider-neutral archive olarak garanti etmez; exit drill kabul kriteri ayrıca yazılmalıdır.

#### Region, cap, cost ve bakım

- **[CONFIRMED]** Cloud regions Frankfurt, New York, Sydney, San Francisco, Singapore, Toronto gibi seçeneklerdir; region self-contained HA cluster ve data sovereignty amacı taşır. Türkiye yoktur: [Regions](https://appwrite.io/docs/products/network/regions).
- **[CONFIRMED]** Pricing: Free `$0`; Pro `$25/month` seviyesinden; Enterprise custom. Free örnekleri 5 GB API bandwidth, 2 GB storage, 750K function execution, 2 shared project ve yaklaşık 1 saat logs; Pro örnekleri 2 TB API bandwidth, 150 GB storage, 3.5M execution, 7 gün logs, 200K MAU ve usage add-ons içerir: [Pricing](https://appwrite.io/pricing).
- **[CONFIRMED]** Pro budget cap ve alerts ile usage scaling sınırlandırılabilir. Limit/budget cap erişilince API, import, new platform/project creation, user/team invite, function/realtime ve file upload gibi yetenekler deny/degrade olabilir; export'un sürmesi özellikle belirtilir: [Pro billing](https://appwrite.io/docs/advanced/billing/pro). Bu bir safety cap'tir ancak “her zaman read-only core çalışır” garantisi değildir.
- **[CONFIRMED]** Cloud billing card/30-day billing ve next-period usage davranışıyla çalışır; local tax/FX ayrıca doğrulanmalıdır: [Payments](https://appwrite.io/docs/advanced/billing/payments).
- **[CONFIRMED]** Self-host Docker ve owner-managed update/scale/backup gerektirir. Self-host DB backend'i Postgres/MariaDB/MongoDB olabilir ve kurulumdan sonra backend değiştirilemez: [Self-host configuration](https://appwrite.io/docs/advanced/self-hosting/configuration/databases).
- **[INFERRED]** Appwrite docs/CLI/API/MCP/IaC yönü AI-operability için verimlidir; yine de permission bypass, token leakage, budget cap fail mode ve self-host restore testleri olmadan düşük operasyon yükü varsayılmamalıdır.

**Adaya özgü hold:** permission matrix (client/server/Console), offline custom protocol, object token lifecycle, Cloud backup/exit kapsamı ve budget cap'in degrade mode'u kanıtlanmadan candidate hold.

### 3.5 Cloudflare Workers / D1 / R2 counterfactual

R2 için bağımsız object evidence yukarıdaki 3.3'te verilmiştir; burada Workers API ve D1 canonical fit'i ayrıştırılır.

#### Worker API, auth ve client

- **[CONFIRMED]** Browser/Flutter, HTTPS Worker endpoint'ine bağlanabilir. Cloudflare Workers/D1 ürünleri Firebase/Supabase gibi end-user Auth/RLS plane'i sağlamaz; session, identity provider, authorization, rate limit ve audit API katmanında owner'a aittir.
- **[CONFIRMED]** D1 dokümanı güvenli query için Worker proxy API, custom access control ve parameterized query önerir; REST API administrative/global API limitlidir: [Build an API to access D1](https://developers.cloudflare.com/d1/tutorials/build-an-api-to-access-d1/).
- **[INFERRED]** Bu nedenle direct browser-to-D1 veya global API token kullanımı canonical authority için reddedilir; yalnızca Worker API ile dar endpoint/policy gerekir.

#### D1 transaction, limit, Time Travel ve region

- **[CONFIRMED]** `db.batch()` statement'ları sıralı çalıştırır; statement failure bütün sequence'i abort/rollback eder: [D1 database API](https://developers.cloudflare.com/d1/worker-api/d1-database/). Bu, bounded atomic batch'tir; PostgreSQL seviyesinde genel workload transaction/lock/extension eşdeğeri varsayılmamalıdır.
- **[CONFIRMED]** Her D1 database tek-threaded Durable Object'e dayanır; paid max database size 10 GB, free 500 MB, query timeout 30 s ve 2 MB row/blob limiti vardır: [D1 limits](https://developers.cloudflare.com/d1/platform/limits/).
- **[CONFIRMED]** Time Travel always-on; paid 30 gün, free 7 gün geçmişte dakika granularity restore verir. Restore DB'yi in-place overwrite eder ve destructive'dir; 30 gün üstü için R2 export/Workflows gibi ek yol gerekir: [Time Travel](https://developers.cloudflare.com/d1/reference/time-travel/).
- **[CONFIRMED]** Data location automatic nearby'dir; jurisdiction `eu`/`us`/`fedramp` gibi seçim yaratımda yapılır, immutable'dır; location hint best effort: [D1 data location](https://developers.cloudflare.com/d1/configuration/data-location/).
- **[INFERRED]** Destructive in-place restore + tek DB/10 GB sınırı, protected non-restorable floor ve çok-domain canonical authority için şu aşamada önemli risk oluşturur.

#### Cost, cap, logs ve AI-operability

- **[CONFIRMED]** Workers Free 100K requests/day ve 10 ms CPU; Paid `$5/month/account`, 10M requests dahil, sonrasında `$0.30/million`; 30M CPU-ms dahil, sonrasında `$0.02/million CPU-ms`; egress/throughput ücreti yok ve paid custom CPU limits vardır: [Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/), [Workers limits](https://developers.cloudflare.com/workers/platform/limits/).
- **[CONFIRMED]** D1 ücretsiz/paid metered: Free 5M rows read/day, 100K rows written/day, 5 GB; Paid 25B reads/month ve 50M writes/month dahil seviyeler, sonra yaklaşık `$0.001/million read`, `$1/million write`, 5 GB üstü `$0.75/GB-month`: [D1 pricing](https://developers.cloudflare.com/d1/platform/pricing/).
- **[CONFIRMED]** Free quota aşımında query error/deny görülebilir; paid usage overage faturalanır. Cloudflare billing alerts genel hard cap değildir. Audit logs ve D1 metrics/GraphQL gözlem yüzeyi vardır: [D1 observability](https://developers.cloudflare.com/d1/observability/), [Audit logs](https://developers.cloudflare.com/d1/observability/audit-logs/).
- **[INFERRED]** Wrangler/CLI, API, Workers logs ve GraphQL AI-operability'yi destekler; ancak auth, DB migration, export/restore, R2 object manifesti ve incident response tek bir ürün runbook'unda değildir.

**Adaya özgü hold:** 10 GB/single-thread cap, destructive restore sonrası quarantine, Auth/API policy implementasyonu ve paid overage/cap kanıtlanmadan counterfactual hold.

### 3.6 Raw self-host baseline

Bu seçenek bir satın alma veya öneri değildir; provider-neutral exit ve operasyon yükünü görünür kılmak için **baseline**'dır. Maliyet örneği olarak DigitalOcean Droplet, object örneği olarak MinIO kullanılmıştır.

#### Teknik sorumluluk

- **[CONFIRMED]** PostgreSQL transaction/constraint, roles/RLS, WAL/continuous archiving, `pg_dump` ve `pg_restore` primitive'lerini kendimiz işletiriz: [PostgreSQL backup](https://www.postgresql.org/docs/current/backup.html), [pg_dump](https://www.postgresql.org/docs/current/app-pgdump.html), [continuous archiving](https://www.postgresql.org/docs/current/continuous-archiving.html).
- **[CONFIRMED]** MinIO single-node single-drive local/evaluation için uygundur; ek reliability sağlamaz. Production multi-node/multi-drive/Kubernetes ve monitoring/replication ister: [MinIO SNSD](https://min.io/docs/minio/container/operations/install-deploy-manage/deploy-minio-single-node-single-drive.html), [MinIO multi-drive](https://min.io/docs/minio/linux/operations/install-deploy-manage/deploy-minio-single-node-multi-drive.html).
- **[INFERRED]** Flutter/browser yalnızca owner API'sini görür; auth/identity, TLS, rate limit, authorization, object presigned access, audit, migration, key rotation, backup encryption ve restore verification tamamen owner işidir.
- **[OPEN]** Provider-level managed failover, regional DR, 24/7 alerting ve abuse protection kurulmadıkça raw baseline managed adaylarla operasyonel olarak eşdeğer değildir.

#### Region, cost, cap ve maintenance

- **[CONFIRMED]** DigitalOcean Basic Droplet örnekleri 512 MiB/1 vCPU/10 GiB için `$4/month` (yaklaşık `$0.00595/hour`), 1 GiB/1 vCPU/25 GiB için `$6/month`, 2 GiB için `$12/month`, 4 GiB/2 vCPU için `$24/month` seviyelerindedir; bundled plan aylık üst sınır olsa da backup/volume/egress/domain/support ayrı olabilir: [Droplet pricing](https://www.digitalocean.com/pricing/droplets), [Create Droplet](https://docs.digitalocean.com/products/droplets/how-to/create/).
- **[CONFIRMED]** Droplet backup weekly/daily yüzdesi veya usage-based GB-month ile ücretlenir; backup/volume/monitoring/egress fiyatı VM fiyatına dahil kabul edilmez: [Backups](https://docs.digitalocean.com/products/backups/).
- **[INFERRED]** VM monthly cap, account-level unlimited invoice cap veya object egress cap değildir. Provider outage, credential lock, abuse hold ve disk failure için recovery/alternate region gerekir.
- **[CONFIRMED]** MinIO software cost, infrastructure/operation costunu ortadan kaldırmaz; self-host owner update, patch, CVE, capacity, certificate, DB vacuum, backup, restore drill, log retention ve alert escalation yapar.

**Baseline hold:** reproducible clean bootstrap, encrypted DB/WAL/object backups, key re-encryption, import/export, policy/identity mapping, alternate-region restore, non-restorable floor ve AI-safe runbook olmadan self-host “exit path” sayılmaz.

## 4. Resmi fiyat ve maliyet fixtürü

### 4.1 Fiyat okuma kuralları

- Tüm sayılar **2026-09-18 gözlem tarihli resmi USD liste değeri** olarak yazılmıştır. Usage, region, currency, tax ve contract'a göre değişebilir.
- Hiçbir TRY dönüşümü yapılmadı. Türkiye KDV/VAT, withholding, FX, kart/transfer komisyonu ve banka kur farkı **[OPEN]** olarak kalır.
- Mağaza, payment processor, domain, e-mail/SMS, device, support ve human operations maliyetleri provider aday tablosundan ayrıdır. Store cost için başka bir araştırma gerekir.
- “Free” satırı production safety kanıtı değildir: pause, quota deny, no backup, low retention, no export support veya paid-only object bucket olabilir.
- Bir cap ancak resmi doküman usage'ı gerçekten deny/suspend ediyorsa hard-cap adayıdır; e-mail alert, budget dashboard veya usage visibility hard cap değildir.

### 4.2 Adayların fiyat sinyali

| Aday | Free/entry signal (official, USD) | Usage/paid signal | Cap/overage reading | Cost class notu |
|---|---|---|---|---|
| Supabase | Free `$0`; 2 active project; 50K MAU; 500 MB DB; 5 GB egress; 1 GB Storage | Pro `$25/month`; additional project from `$10`; usage addons; Team `$599`; Enterprise custom; PITR about `$100/$200/$400` for retention tiers | Spend cap bazı usage kalemlerini durdurur, bütün fatura/compute/PITR'ı değil; cap off overage | Free = exploration; Pro/backup/PITR = deferrable veya scale-triggered, safety controls mandatory |
| Firebase/Firestore | Spark `$0`; no card; Firestore no-cost quotas (1 GiB, reads/writes/deletes/day, egress) | Blaze pay-go; Iowa sample reads `$0.03/100K`, writes `$0.09/100K`, deletes `$0.01/100K`; backup/PITR/restore/export ayrıca | Budget alert hard cap değildir; paid project overage/lock risk | Spark = exploration; Blaze/backup/Storage = usage-triggered; exact cost workload test ister |
| Neon | Free blog limits: 10 projects, 50 CU-hour/project/month, 0.5 GB/project, 10 branches/project, 5 GB egress | Latest explicit official rate found: Launch `$0.106/CU-hour`, Scale `$0.222/CU-hour`; dynamic page verify at approval | Organization spending limits currently 80/100% alerts; automatic suspend not current guarantee | Managed DB cheap start; backup/history and compute vary by workload |
| Render API/Postgres | Hobby `$0` + compute; Free web/DB options constrained | Pro `$25` + compute; web examples `$7/$25`; Postgres examples `$6/$19`; disk `$0.25/GB-month`, bandwidth over 5 GB `$0.15/GB` | Composite workspace/service/database/add-on cap not proven as universal hard cap | API/DB separate resources; keep owner alert and stop plan |
| R2 | Standard free 10 GB-month, 1M Class A, 10M Class B | Standard `$0.015/GB-month`; IA `$0.01`; Class A `$4.50/million`; Class B `$0.36/million`; egress direct `$0` | Free quota or budget alert does not equal object lifecycle/backup cap | Object cost separately track operations, versions, retrieval and lifecycle |
| Appwrite Cloud | Free `$0`; 5 GB API bandwidth; 2 GB storage; 750K execution; 2 projects; short logs | Pro from `$25/month`; 2 TB bandwidth; 150 GB storage; 3.5M execution; budget cap/addons; 200K MAU then usage | Budget cap can deny specific features (uploads, execution, API, platform creation); not guaranteed graceful read-only | Integrated surface; cap semantics must be tested as business-continuity mode |
| Workers/D1 | Workers Free 100K requests/day; D1 Free 5M rows read/day, 100K write/day, 5 GB | Workers Paid `$5/account/month`; 10M requests + 30M CPU-ms; D1 paid quotas then read `$0.001/million`, write `$1/million`, storage `$0.75/GB-month` over free | Free quota errors; paid overage; billing alert not universal hard cap | Small counterfactual; object/API/DB cost separate |
| DO + Postgres/MinIO baseline | Droplet entry `$4/month` | `$6/$12/$24` examples; backups/volumes/egress/support separate | VM bundled cap is not all-resource invoice cap; owner can stop instances but data plane stops too | Infrastructure cash cost low; maintenance/recovery labor mandatory |

**Planning ceiling note:** TRY 2.000–3.000/ay, DEC-0032'de yalnızca future planning ceiling'dir. Bu tablo hiçbir planı satın alınabilir veya onaylanmış yapmaz.

## 5. Ortak acceptance gates — ADR öncesi

Hiçbir aday aşağıdaki kanıtlar olmadan winner olamaz:

1. **Canonical authority:** direct mobile/browser client'tan DB/object write yok; tüm high-consequence mutation API/server boundary'si, idempotency ve audit ile çalışıyor.
2. **Authorization proof:** allow/deny matrix; tenant/user/role/ownership; server/admin bypass; migration/repair path; secret scope; policy test evidence.
3. **Transaction proof:** transaction boundary, partial failure, retry, concurrent update, duplicate request, timeout ve offline reconnect testleri.
4. **Offline proof:** package version, expiration, key/revocation, durable local op log, upload resume, conflict class, user-visible repair; high-consequence data için sessiz LWW yok.
5. **Object proof:** private default, signed/presigned URL TTL, cache behavior, digest/generation, DB manifest, delete/revoke, malware/privacy rule.
6. **Recovery proof:** DB backup + object backup + metadata + secrets/identity/policy; restore quarantine; protected audit; non-restorable release/security/deletion/operation/migration floor; cross-plane consistency manifest.
7. **Exit proof:** clean-room export/import into another account/provider or local runtime; mapping of users, roles, permissions, object keys, encrypted keys, versions, audit chain and current/history/protected data.
8. **Region proof:** selected primary/backup/object region, residency claim, region change/replication, lawful access and account closure response. “Europe” label alone is not compliance proof.
9. **Cost proof:** free/paid transition, every metered dimension, tax/FX/card uncertainty, actual cap semantics, account suspension/lock, budget alert route and owner stop action.
10. **AI-operability proof:** no secret in AI context; least privilege; dry-run/read-only first; idempotent commands; captured evidence; explicit stop on destructive/recovery steps; human approval for billing/restore/delete.

## 6. Aday bazında ADR öncesi açık sorular

| Aday | ADR öncesi cevaplanacak soru |
|---|---|
| Supabase | RLS policy + Data API grants + security-definer review nasıl otomatik test edilecek? `service_role` sadece nerede yaşayacak? DB backup ile Storage backup aynı recovery proof'a nasıl bağlanacak? PITR/compute spend cap dışı kaldığında stop policy ne? |
| Firebase | Firestore offline LWW hangi alanlarda kesin yasak? Server SDK bypass için tek API/IAM boundary nedir? Spark→Blaze geçişinde hard-stop ve export yolu nasıl korunacak? GCS/Auth/Rules/Functions clean-room restore nasıl drill edilecek? |
| Managed PG/API/R2 | Hangi API runtime/auth provider? Neon/Render/R2 üçlü outage ve fatura sınırları nasıl gözlenecek? DB commit ile object upload arasında manifest/retry protocol nedir? Independent API'nin patch/CVE/secret rotation owner'ı kim? |
| Appwrite | Platform permission ile domain policy nasıl ayrılacak? Budget cap deny mode'unda read-only operational path var mı? Cloud export kapsamı nedir? Self-host upgrade/backup/region failover labor budget'a sığar mı? |
| Workers/D1/R2 | 10 GB / single-thread ve 30 s query limitleri hangi domain hacminde kırılır? Destructive Time Travel restore sonrası protected floor nasıl korunur? Auth ve API policy hangi managed identity ile kurulacak? |
| Raw self-host | On-call, patch/CVE, disk/region failure ve restore drill'i kim yapacak? Minimum topology ne? Monthly VM cap dışında object/backup/egress hesabı nasıl durdurulacak? Exit path'ın kendisi nasıl exit-proof olacak? |

## 7. Geçici maliyet sınıflandırması (karar değildir)

Bu sınıflandırma DEC-0030'un araştırma fixtürüdür; satın alma emri değildir.

- **Mandatory safety work:** API/auth boundary, least-privilege keying, protected audit, backup/export evidence, restore quarantine, non-restorable floor, cost alerts/stop runbook, region/data map.
- **Deferrable:** paid PITR retention extension, extra region/read replica, advanced log drain, managed support, higher object transforms, broad preview/branch fleets.
- **Optional:** convenience SDKs, dashboard cosmetics, extra analytics, non-critical realtime, premium AI add-ons.
- **Scale-triggered:** paid compute/storage/egress, MAU/reads/writes/operations, object retrieval/transforms, extra DB projects, higher retention, support/HA topology.
- **Store/separate:** Android/iOS developer accounts, app-store commission, payment processor, SMS/e-mail, domain, device lab; bu dosyada provider costuna dahil edilmemiştir.

## 8. Sonuç / disposition

Bu araştırma **kazanan seçmez**. Kanıtlar şunu gösterir:

- Supabase ve managed PostgreSQL ailesi relational integrity ve portable exit açısından güçlü adaylardır; doğrudan client authority, RLS/permission bypass ve object–DB recovery kapanışı kanıtlanmadan kabul edilmez.
- Firebase/Firestore hızlı Flutter/web SDK ve offline davranışı sunar; server SDK bypass, document LWW, Rules'ın filter olmaması, Blaze overage ve provider-specific export nedeniyle aynı acceptance gates geçerlidir.
- Appwrite birleşik Cloud/self-host yolu ve explicit budget cap davranışı sunar; permission bypass, custom offline, object token ve self-host recovery yükü ayrıca kanıtlanmalıdır.
- Cloudflare Workers/D1/R2 iyi bir API/object counterfactual'tır; D1'nin single-thread/10 GB ve destructive restore sınırları, built-in Auth olmaması ve metered billing nedeniyle şu an canonical winner sayılamaz.
- Raw self-host en açık kontrol/exit baseline'ıdır; maliyetin önemli kısmı USD VM değil bakım, security, backup, DR ve on-call sorumluluğudur.

Bir sonraki aşama ancak karar yetkisiyle; workload fixture, authorization matrix, offline package/reconciliation spec, object/recovery manifest, cap/outage drill ve clean-room exit drill'i karşılaştırmalı kanıtlayarak ADR'ye gidebilir.

## 9. Primary-source inventory (erişim: 2026-09-18)

### Supabase

- [Pricing](https://supabase.com/pricing)
- [Billing FAQ](https://supabase.com/docs/guides/platform/billing-faq)
- [Cost control / spend cap](https://supabase.com/docs/guides/platform/cost-control)
- [Database overview](https://supabase.com/docs/guides/database/overview)
- [Backups and PITR](https://supabase.com/docs/guides/platform/backups)
- [Branching](https://supabase.com/docs/guides/deployment/branching)
- [Regions](https://supabase.com/docs/guides/platform/regions)
- [Securing the Data API](https://supabase.com/docs/guides/api/securing-your-api)
- [Postgres RLS](https://supabase.com/docs/guides/database/postgres/row-level-security)
- [Database functions](https://supabase.com/docs/guides/database/functions)
- [Storage buckets](https://supabase.com/docs/guides/storage/buckets/fundamentals)
- [Storage access control](https://supabase.com/docs/guides/storage/security/access-control)
- [Storage downloads/signed URLs](https://supabase.com/docs/guides/storage/serving/downloads)
- [Self-hosting](https://supabase.com/docs/guides/self-hosting)
- [Self-host restore from platform](https://supabase.com/docs/guides/self-hosting/restore-from-platform)
- [Platform changelog](https://supabase.com/changelog?tags=platform)

### Firebase / Firestore

- [Firebase pricing](https://firebase.google.com/pricing)
- [Pricing plans and billing](https://firebase.google.com/docs/projects/billing/firebase-pricing-plans)
- [Cloud Firestore pricing](https://cloud.google.com/firestore/pricing)
- [Firestore transactions](https://firebase.google.com/docs/firestore/manage-data/transactions)
- [Security Rules conditions](https://firebase.google.com/docs/firestore/security/rules-conditions)
- [Rules are not filters](https://firebase.google.com/docs/firestore/security/rules-query)
- [Offline data](https://firebase.google.com/docs/firestore/enterprise/enable-offline)
- [Flutter setup](https://firebase.google.com/docs/flutter/setup)
- [Cloud Storage for Flutter](https://firebase.google.com/docs/storage/flutter/start)
- [Firestore locations](https://firebase.google.com/docs/firestore/enterprise/locations)
- [PITR](https://firebase.google.com/docs/firestore/enterprise/use-pitr)
- [Export/import](https://firebase.google.com/docs/firestore/enterprise/export-import)
- [Cloud Billing budgets](https://docs.cloud.google.com/billing/docs/how-to/budgets)
- [Cloud Billing spend caps](https://docs.cloud.google.com/billing/docs/how-to/budgets-spend-caps)
- [Firebase release notes](https://firebase.google.com/support/releases)

### Managed PostgreSQL / API / object

- [Neon usage-based pricing](https://neon.com/blog/new-usage-based-pricing)
- [Neon compute price reduction](https://neon.com/blog/major-compute-price-reduction-on-neon)
- [Neon point-in-time restore](https://neon.com/blog/announcing-point-in-time-restore)
- [Neon spending limits](https://neon.com/blog/introducing-organization-spending-limits)
- [Neon restore branch API](https://api-docs.neon.tech/reference/restoreprojectbranch)
- [Neon active regions API](https://api-docs.neon.tech/reference/getactiveregions)
- [Neon PostgreSQL export](https://github.com/neondatabase/website/blob/main/content/docs/guides/export-neon-postgres-compatible.md)
- [Render pricing](https://render.com/pricing)
- [Render pricing update](https://render.com/blog/better-pricing-for-fast-growing-teams)
- [Render Web Services](https://render.com/docs/web-services)
- [Render PostgreSQL backups](https://render.com/docs/postgresql-backups)
- [Render regions](https://render.com/docs/regions)
- [Cloudflare R2 pricing](https://developers.cloudflare.com/r2/pricing/)
- [R2 API](https://developers.cloudflare.com/r2/api/)
- [R2 presigned URLs](https://developers.cloudflare.com/r2/api/s3/presigned-urls/)
- [R2 consistency](https://developers.cloudflare.com/r2/reference/consistency/)
- [R2 durability](https://developers.cloudflare.com/r2/reference/durability/)
- [R2 data location](https://developers.cloudflare.com/r2/reference/data-location/)
- [R2 object lifecycles](https://developers.cloudflare.com/r2/buckets/object-lifecycles/)
- [Cloudflare usage-based billing](https://developers.cloudflare.com/billing/understand/usage-based-billing/)

### Appwrite

- [Pricing](https://appwrite.io/pricing)
- [Pro billing/budget caps](https://appwrite.io/docs/advanced/billing/pro)
- [Payments](https://appwrite.io/docs/advanced/billing/payments)
- [SDKs](https://appwrite.io/docs/sdks)
- [Databases](https://appwrite.io/docs/products/databases)
- [Transactions](https://appwrite.io/docs/products/databases/tablesdb/transactions)
- [PostgreSQL transactions](https://appwrite.io/docs/products/databases/postgresql/concepts/transactions)
- [Offline data](https://appwrite.io/docs/products/databases/tablesdb/offline)
- [Permissions](https://appwrite.io/docs/advanced/security/permissions)
- [Storage buckets](https://appwrite.io/docs/products/storage/buckets)
- [Storage permissions](https://appwrite.io/docs/products/storage/permissions)
- [File tokens](https://appwrite.io/docs/products/storage/file-tokens)
- [Backups](https://appwrite.io/docs/advanced/security/backups)
- [Regions](https://appwrite.io/docs/products/network/regions)
- [Self-hosting](https://appwrite.io/docs/advanced/self-hosting)

### Cloudflare Workers / D1 / R2

- [Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/)
- [Workers limits](https://developers.cloudflare.com/workers/platform/limits/)
- [D1 pricing](https://developers.cloudflare.com/d1/platform/pricing/)
- [D1 limits](https://developers.cloudflare.com/d1/platform/limits/)
- [D1 Worker API](https://developers.cloudflare.com/d1/worker-api/d1-database/)
- [D1 API tutorial](https://developers.cloudflare.com/d1/tutorials/build-an-api-to-access-d1/)
- [D1 Time Travel](https://developers.cloudflare.com/d1/reference/time-travel/)
- [D1 data location](https://developers.cloudflare.com/d1/configuration/data-location/)
- [D1 observability](https://developers.cloudflare.com/d1/observability/)
- [D1 audit logs](https://developers.cloudflare.com/d1/observability/audit-logs/)
- [R2 references](https://developers.cloudflare.com/r2/pricing/)

### Raw self-host baseline

- [DigitalOcean Droplet pricing](https://www.digitalocean.com/pricing/droplets)
- [DigitalOcean Droplet creation/pricing notes](https://docs.digitalocean.com/products/droplets/how-to/create/)
- [DigitalOcean backups](https://docs.digitalocean.com/products/backups/)
- [PostgreSQL backup](https://www.postgresql.org/docs/current/backup.html)
- [PostgreSQL `pg_dump`](https://www.postgresql.org/docs/current/app-pgdump.html)
- [PostgreSQL continuous archiving/PITR](https://www.postgresql.org/docs/current/continuous-archiving.html)
- [MinIO single-node single-drive](https://min.io/docs/minio/container/operations/install-deploy-manage/deploy-minio-single-node-single-drive.html)
- [MinIO single-node multi-drive](https://min.io/docs/minio/linux/operations/install-deploy-manage/deploy-minio-single-node-multi-drive.html)

