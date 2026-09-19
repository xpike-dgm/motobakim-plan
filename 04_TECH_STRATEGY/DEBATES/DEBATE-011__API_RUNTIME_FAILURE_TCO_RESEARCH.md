# DEBATE-011 — API Runtime Failure, TCO ve Operability Araştırması

**Durum:** `PHASE-4 / NO-CODE / EŞİT KÖTÜ-DURUM FİXTÜRÜ / NO WINNER / ADR NOT READY`  
**Tarih:** 2026-09-19 (Europe/Istanbul)  
**Kapsam:** Kavriva API authority boundary'sinin çalışacağı runtime katmanı; HTTP request işleme, kısa/uzun iş ayrımı,
queue/worker, deployment/rollback, secret, runtime log/metric ve runtime işletim maliyeti.  
**Yetki sınırı:** Bu belge hesap, provider, plan, abonelik, satın alma, kod, prototip, migration, production proof,
Phase-5 ADR veya Gate 4 -> 5 geçişi oluşturmaz.

## 1. Kısa sonuç

`DEC-0035` ile Supabase merkezli yapı Phase-4 için geri alınabilir çalışma yönüdür. Supabase Edge Functions/Deno,
Kavriva API için başlangıçtaki düşük-operasyonlu runtime adayıdır; ancak exact runtime seçilmemiştir. Render üzerinde
çalışan yönetilen container API, Cloudflare Workers tabanlı edge runtime ve self-managed container/VM baseline eşit
karşılaştırma adayları olarak tutulur. Hiçbiri burada kazanan değildir.

En önemli sonuç şudur: runtime, Kavriva ürün otoritesi değildir. Sağlıklı HTTP cevabı, başarılı deployment, yeşil
provider dashboard'u, boş queue, tamamlanmış function veya DB driver'sının `commit` cevabı tek başına ürün sonucunu
kanıtlamaz. Her aday aynı operation ledger, idempotency, current authority/security epoch, protected audit-before-effect,
object quarantine, restore quarantine, anti-resurrection floor, billing hold ve clean-room exit sözleşmesini taşımak
zorundadır.

Belgesel durum bütün adaylarda **`HELD`**'dir: mekanizmaların bir bölümü resmi dokümanlarda doğrulanabilir, fakat
Kavriva'nın gerçek timeout/commit, revoke race, audit/object recovery, owner-operability, maliyet ve çıkış kanıtı henüz
yoktur. Güvenli hold yolu tasarlanamayan veya teknik olmayan sahibin SQL/SSH/debug yapmasını zorunlu kılan kullanım
`REJECT-IF-UNMITIGATED` olur.

## 2. Bağlayıcı karar bağlamı

Bu araştırma aşağıdaki kararları runtime seviyesine taşır:

- `DEC-0034`: Her alanın canonical transactional authority'si, server/API-mediated sensitive access, online-authoritative
  Internal Operations, durable identified operation, bounded offline package, protected audit, ayrı object boundary,
  cross-plane restore/export/exit ve non-restorable negative/deletion/accepted-operation floor zorunludur.
- `DEC-0035`: Managed Supabase PostgreSQL/Auth/private Storage çalışma yönüdür; Flutter ve browser doğrudan genel DB veya
  object authority alamaz; yüksek sonuçlu mutation'lar Kavriva API arkasında kalır; RLS/Storage defense-in-depth'tir;
  database backup object bytes, protected audit veya floor'u kapsamaz; Neon + bağımsız API + R2 ilk fallback'tir.
- `DEC-0036`: Kullanıcı operasyonları operation identity, payload fingerprint, expected version/generation ve görünür
  `pending/submitted/accepted/conflict/held/failed/outcome-unknown/reconciling` durumlarını taşır. HTTP success veya queue
  boşluğu canonical acceptance değildir.
- `DEC-0037`: Authentication authority değildir. API current actor/session/issuer, security epoch, action, resource,
  tenant/scope, grant, competence, independence, policy, object generation ve operation identity ile karar verir.
  `service_role`, owner/billing/root/recovery authority veya sınırsız SQL/SSH AI bağlamına giremez.
- `DEC-0029` ve `DEC-0030`: Proje AI-operated, tek ve teknik olmayan sahip içindir. Sahip kod yazmaz, SQL/SSH çalıştırmaz,
  log teşhisi veya incident repair yapmaz. Harcama ve operasyon sonucu ürün dilinde gösterilmelidir.
- `DEC-0032`: TRY 2.000–3.000/ay yalnızca ilerideki non-store planning ceiling'dir; ödeme yetkisi değildir. Güvenlik,
  recovery, erişilebilirlik veya çıkış kolaylığı bütçeye sığmıyorsa zayıflatılmaz; ilgili capability `HELD` kalır.

## 3. Runtime'ın sınırı ve eşit karşılaştırma fixtürü

### 3.1 Runtime neyi yapar, neyin sahibi değildir?

Runtime; Kavriva API endpoint'lerini, kısa request'leri, auth adapter çağrılarını, queue/worker işlerini, deployment
version'ını, secret erişimini ve runtime gözlemlenebilirliğini çalıştırır. Aşağıdakilerin hiçbirini kendi başına ürün
otoritesi sayamaz:

- approval, publication, recall, suspension, role/grant veya provenance kararı;
- tenant/ownership kontrolü için client-supplied ID veya cached claim;
- başarılı HTTP yanıtı ile canonical kabul;
- provider dashboard'u ile protected product audit;
- DB snapshot/PITR ile object bytes, audit, identity, policy, config, package veya negative floor recovery;
- AI görevi, provider owner/billing hesabı veya teknik olmayan sahibin incident debugger'ı.

### 3.2 Adaylar

Karşılaştırma runtime katmanını izole etmek için bütün adaylarda aynı Supabase PostgreSQL/Auth/private Storage çekirdeği,
aynı Kavriva API sözleşmesi ve aynı protected audit/object/floor gereksinimleri varsayılmıştır. Bu, adayların gerçek
üretim bileşimini seçmez; fiziksel çalışma farkını görünür kılar.

| Kod | Runtime adayı | Eşit fixtürdeki rolü | Resmi mekanizma sinyali ve ilk risk okuması |
|---|---|---|---|
| **R1** | **Supabase Edge Functions / Deno** | Supabase çekirdeğine yakın API; kısa request + external queue/worker | [CONFIRMED] Hosted Edge Functions 256 MB memory, paid planda 400 saniye azami wall-clock, 150 saniye request idle timeout ve request başına 2 saniye CPU limiti taşır. `waitUntil`/background task uzun işin tamamlandığını kanıtlamaz; limitte worker kapanır. Düşük görünen control-plane ve Supabase coupling aynı anda risklidir. |
| **R2** | **Managed container API + worker** (Render Web Service + Background Worker temsilcisi) | Uzun yaşayan HTTP API, ayrı worker ve queue | [CONFIRMED] Render health check ile yeni deploy'ü trafiğe almadan doğrular; başarısız deploy iptal edilip mevcut sürüm korunabilir. Background Worker ayrı queue consumer modeli ister; rollback build/config/disk/migration ile aynı şey değildir. Daha görünür operasyon yüzeyi, daha fazla service/queue hesabı demektir. |
| **R3** | **Edge isolate** (Cloudflare Workers; Supabase çekirdeğine HTTPS) | Edge HTTP API; Queue/Workflows ile async iş | [CONFIRMED] Workers Paid için 128 MB memory, varsayılan 30 saniye CPU (en fazla 5 dakika), 1 saniye startup ve Queue consumer için 15 dakika wall-clock sınırı vardır. Client disconnect/response sonrası `waitUntil` en fazla 30 saniye uzatır; Workers Logs retention en fazla 7 gündür. Auth, DB connection, tenant policy, audit ve recovery bağları proje işidir. |
| **R4** | **Self-managed container/VM API baseline** (DigitalOcean/Fly benzeri temsil) | Aynı API/queue sözleşmesini owner-managed process olarak çalıştırma | [CONFIRMED] VM/container kaynakları ve process ömrü daha doğrudan kontrol edilir; fakat patch, CVE, network, disk,
  backup, restore, failover, secret vault, log retention, on-call ve exit işletimi adayın kendisine geçer. Düşük VM
  fiyatı, teknik olmayan sahibin bakım emeğini veya incident riskini sıfırlamaz. |

R2'deki Render, R3'teki Cloudflare ve R4'teki VM isimleri eşit fixture için temsilcilerdir; hesap/plan satın alma veya
provider seçimi değildir. Neon + bağımsız API + R2, `DEC-0035`'in ilk documented fallback composition'ıdır; bu belgede
runtime karşılaştırmasına referans olarak kalır, otomatik fallback değildir.

### 3.3 Eşitlik kuralları

Her runtime aynı workload, aynı data/authorization contract ve aynı safety evidence'ı taşımadıkça fiyat veya latency
karşılaştırması yapılmaz:

1. Flutter/browser yalnız Kavriva API endpoint'i ve kısa ömürlü scoped object handle görür; generic Data API, RPC,
   Storage veya direct DB write yoktur.
2. Aynı PostgreSQL transaction, idempotency ledger, expected version/generation, security epoch, protected audit,
   quarantine ve cross-plane manifest kullanılır. Bir runtime primitive'i bunları sağlamıyorsa proje işi açıkça
   maliyete yazılır.
3. Request path kısa tutulur. Package build, object scan/preview, AI/OCR, notification, export ve reconcile gibi uzun
   işler durable queue/worker ile, lease/visibility timeout, dedupe, retry budget ve DLQ ile çalışır. "Background task"
   veya `waitUntil` durable queue yerine sayılmaz.
4. Aynı primary region, DNS/TLS, auth/session policy, object classification, audit/floor custody ve monitoring kabul
   edilir; farklı provider seçimi bu planes'leri gizleyemez.
5. Aynı failure sonucu adlandırılır: `ACCEPTED`, `DENIED`, `HELD`, `OUTCOME_UNKNOWN`, `SERVICE_UNAVAILABLE`,
   `BILLING_HELD`, `AUDIT_HELD`, `OBJECT_QUARANTINE`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`.
6. Aynı maliyet horizon'ları ölçülür: normal ay, incident ayı, restore drill'i ve clean-room exit. Headline runtime
   fiyatı tek başına TCO değildir.

### 3.4 Operation sözleşmesi

Her yüksek sonuçlu işlem en az şu immutable/monotonic alanları taşır:

`operation_id`, `payload_fingerprint`, `actor/principal`, `session/issuer`, `security_epoch`, `action`,
`tenant/scope`, `resource_id`, `expected_version/generation`, `policy/grant/competence_generation`, `classification`,
`created_at/server_time`, `current_state`, `audit_event_id`, `object_manifest_id` ve `recovery_owner`.

Request timeout, process kill, provider outage veya response loss olduğunda sistem yeni tahmini bir işlem yaratmaz;
aynı `operation_id` ile status lookup/reconciliation yapar. Aynı fingerprint'in kabul edilmiş sonucu tekrar `ACCEPTED`
olarak okunabilir; farklı fingerprint `CONFLICT/HELD` olur. `OUTCOME_UNKNOWN`, `FAILED` ile eşit değildir.

## 4. Kötü durum matrisi — 18 failure sınıfı

**Okuma kuralı:** Her satırda önce bütün adaylar için bağlayıcı ürün sonucu, sonra runtime'a özgü kötü durum riski vardır.
`HOLD` güvenli mekanizma tasarlanabilir fakat kanıt yok demektir; olumlu üretim kararı değildir. `REJECT-IF-UNMITIGATED`,
güvenli hold/recovery veya no-owner-debug yolu kurulamıyorsa uygulanır.

### 4.1 Request, authorization, transaction ve object olayları

| ID / kötü durum | Bütün adaylar için kabul sonucu, hold ve recovery | R1 — Edge Functions | R2 — Managed container | R3 — Workers | R4 — Self-managed |
|---|---|---|---|---|---|
| **F01 — Commit sonrası request timeout / response loss** | `OUTCOME_UNKNOWN`; kullanıcıya sahte failure/success gösterilmez. Aynı operation status endpoint'i, DB ledger + audit + queue/object manifest ile reconcile edilir. Restore/exit'te operation history korunur. | 150 s idle/400 s paid wall-clock sınırı ve worker shutdown, DB commit ile cevabı ayırabilir; background `waitUntil` commit kanıtı değildir. **HELD.** | Load balancer, instance restart veya graceful shutdown commit sonrası cevabı kaybettirebilir; worker/status ledger zorunlu. **HELD.** | Client disconnect sonrası iş iptal olabilir; `waitUntil` yalnız sınırlı devam eder. Queue/Workflow olmadan **HELD.** | Process cevap vermeden commit edebilir veya ölebilir; status ledger ve watchdog tamamen işletim sorumluluğudur. **HELD.** |
| **F02 — Duplicate retry / aynı işlem yeniden gönderimi** | `operation_id + payload_fingerprint` unique olmalıdır. Aynı fingerprint mevcut sonucu okur; farklı payload aynı logical operation'ı değiştiremez, `CONFLICT/HELD` olur. Blind retry `REJECT`. | Function idempotency primitive'i vermez; Postgres ledger ve retry budget runtime dışına yazılmalıdır. **HELD.** | Web process ve worker aynı ledger'ı atomik kullanmazsa iki effect oluşabilir; queue dedupe gerekir. **HELD.** | Isolate/queue yeniden delivery normaldir; idempotency uygulama ve queue contract'ıdır. **HELD.** | Retry, cron ve operator script'leri çoğalabilir; self-managed queue duplicate proof olmadan **REJECT-IF-UNMITIGATED.** |
| **F03 — Concurrent approval vs revoke/recall/suspension** | Current version/generation/security epoch ile transaction fence gerekir; yeni negative generation positive effect'i yener. Race sonucu `HELD` ise publication/approval açılmaz; ordered audit ve negative floor kanıtlanır. | DB yakınlığı latency avantajı verse de Edge gateway/RLS race çözmez; function + DB transaction ve ayrı negative floor gerekir. **HELD.** | API instance/worker/DB clock veya stale cache yarış yaratabilir; serializable/version fence gerekir. **HELD.** | Edge locality authority değildir; iki request farklı isolate/region'da görülebilir; current DB check zorunlu. **HELD.** | Lock/clock/process yönetimi tamamen adaya aittir; “tek process” varsayımı güvenlik kanıtı değildir. **HELD.** |
| **F04 — Stale JWT / stale role / stale grant** | JWT yalnız kimlik sinyalidir. API current session, issuer, security epoch, grant/policy/competence generation ve action/scope kontrolü yapar. Stale claim `DENIED` veya `HELD`; provider role direct authority olamaz. | Gateway JWT doğrulaması güncel role/revoke kararının yerini tutmaz; RLS defense-in-depth kalır. **HELD.** | Session/role recheck, cache invalidation ve key/JWKS rotation proje işidir. **HELD.** | Built-in product authorization yoktur; issuer/audience/epoch adapter'ı proje işidir. **HELD.** | Auth, rotation, session store ve network perimeter'ın tamamı owner-run olur. **REJECT-IF-UNMITIGATED.** |
| **F05 — DB transaction partial failure** | Canonical DB effect tek transaction/constraint sınırında atomik; dış side-effect outbox/manifest ile idempotent. Commit sonucu ile audit/object/queue arasında mismatch `HELD/RECONCILING`; provider success sayılmaz. | Remote pooled Postgres bağlantısı, CPU/timeout ve function shutdown transaction dışı işleri kesebilir; DB transaction yeterli ama cross-plane değil. **HELD.** | API process, worker ve DB ayrı lifecycle'dır; transaction boundary açıkça yazılmalı, queue/outbox recovery gerekir. **HELD.** | Connection pooling/long transaction edge'de kırılgan olabilir; DB access pattern ve retry ayrı kanıt ister. **HELD.** | Connection, WAL, process restart ve failover tamamen işletilir; partial recovery runbook yoksa **REJECT-IF-UNMITIGATED.** |
| **F06 — Protected audit sink failure / audit loss** | High-consequence positive effect, audit-before-effect veya eşdeğer transactional assurance yoksa `AUDIT_HELD`. Normal runtime log'u protected product audit yerine geçmez. Independent fallback custody, gap/fork/replay ve restore reconciliation kanıtı gerekir. | Platform logs function audit'i değildir; log limit/retention ve provider ortak failure domain'i audit custody olamaz. **HELD.** | Service log, worker log ve audit sink farklı olabilir; sink outage'da transaction hold ve durable fallback gerekir. **HELD.** | Workers Logs retention en fazla 7 gün; sampling/Logpush olsa da immutable audit değildir. **HELD.** | Audit storage, WAL/disk, replication ve tamper separation adaya aittir; aynı root erişimi varsa **REJECT-IF-UNMITIGATED.** |
| **F07 — Object upload incomplete / orphan / digest mismatch** | Upload önce private quarantine; size/digest/lineage/classification/scan manifesti tamamlanmadan active/public handle yok. Partial/orphan cleanup ayrı operation; DB effect ve object generation reconcile edilir. | Supabase Storage upload ve function yaşam süresi ayrıdır; resumable upload, object backup ve quarantine runtime tarafından otomatik kapanmaz. **HELD.** | Worker ile resumable transfer uygun olabilir; queue retry ve orphan cleanup yine ürün contract'ıdır. **HELD.** | Request body/CPU/memory/startup sınırları büyük body ve transform işini dış queue/object direct upload'a iter. **HELD.** | Disk/volume/replication ve cleanup tamamen işletilir; upload'ın “dosya var” sonucu yayın kanıtı olamaz. **HELD.** |
| **F08 — Provider/region/DNS outage** | Owner-readable `SERVICE_UNAVAILABLE`/`ACCOUNT_HELD`; positive mutation, approval, publication, recall dışındaki güvenli history/safe-stop mümkünse sürer. DNS failover önceden test edilir; blind retry yok. | Supabase DB/Auth/Storage/Functions aynı control-plane failure domain'ini büyütebilir; independent negative/audit path gerekir. **HELD.** | Render API, queue, DB, DNS ve adjunct farklı outage yüzeyleridir; partial health yanlış “sistem çalışıyor” sinyali yaratabilir. **HELD.** | Workers ayakta kalsa bile Supabase DB/Auth erişimi olmayabilir; edge success canonical success değildir. **HELD.** | Tek VM/network veya failover sağlayıcısı için çok daha fazla owner-run hazırlık gerekir; **REJECT-IF-UNMITIGATED**. |
| **F09 — Billing/quota/throttle / account restriction** | Limit yaklaşınca positive work `BILLING_HELD`; accepted history, pending operation ve safe recovery korunur. Cost alert hard cap sayılmaz; cap dışı kalemler ayrıca durdurulur. | Supabase Spend Cap bütün fatura/compute/PITR/log drain/domain gibi kalemleri kapsamaz; quota davranışı planla doğrulanmalı. **HELD.** | Web + worker + queue + DB + log faturası composite hard cap değildir; Free web spin-down/worker kısıtı production kanıtı değildir. **HELD.** | Free quota aşımı fail eder; Paid request/CPU overage ve log/queue maliyetleri vardır. Custom CPU limit yalnız bir runaway sınıfını sınırlar. **HELD.** | VM planı ucuz görünse de backup/volume/egress/account lock ayrı; hizmeti kapatmak data availability/recovery'yi de kesebilir. **HELD.** |

### 4.2 Secret, deploy, long job, observability ve boundary olayları

| ID / kötü durum | Bütün adaylar için kabul sonucu, hold ve recovery | R1 — Edge Functions | R2 — Managed container | R3 — Workers | R4 — Self-managed |
|---|---|---|---|---|---|
| **F10 — Secret leak / key rotation** | Etkilenen credential scope'u dondurulur; fresh secret rollout, security epoch artırımı, session/handle/in-flight op invalidation, audit ve reconciliation yapılır. Leaked key ile devam edilmez; raw secret log/context'e girmez. | Project secrets rahat görünse de service key/Storage handle leak'i runtime içi değil tüm Supabase etkisini kapsayabilir; secret rotation ve function version cutover kanıtı gerekir. **HELD.** | Environment groups, deploy version, worker ve DB/R2/identity anahtarları ayrı rotasyon ister. **HELD.** | Worker vars/keys ile provider API token'ları ayrılmalı; versioned rollout ve old isolate drain kanıtı gerekir. **HELD.** | Host root, SSH, `.env`, vault, image layer ve backup anahtarları yüksek blast radius taşır; owner/debug bağımlılığı **REJECT-IF-UNMITIGATED**. |
| **F11 — Deployment rollback / schema mismatch** | Expand-contract migration, backward-compatible API/schema window, runtime `release_id` + schema generation check, queue version fence ve forward recovery gerekir. Code rollback DB schema rollback değildir; mismatch `DEPLOYMENT_HELD`. | Function bulk deploy atomikliği function version'ını değiştirir; DB migration, object schema ve floor'la birlikte rollback olmaz. **HELD.** | Health check deploy'ü korur; rollback build'i/config'i kısmen hedef sürümden alabilir, disk state'i geri dönmeyebilir. Pre-deploy migration ile schema fence şart. **HELD.** | Worker version, queue message schema ve Supabase schema ayrı deploy olur; old/new isolate karışımında explicit compatibility gerekir. **HELD.** | Migration/rollback, process drain ve artifact pinning manuel yüzeydir; rehearsal yoksa **REJECT-IF-UNMITIGATED**. |
| **F12 — Cold start / long job** | HTTP path kısa iş için; long job `accepted/queued` ile döner, status endpoint'i ve lease/heartbeat ile izlenir. Timeout işin başarısız olduğu anlamına gelmez. Kill/restart sonrası retry aynı operation'dır. | Edge docs cold start olabileceğini ve heavy long-running işi worker'a taşımayı önerir; 150/400 s ve 2 s CPU sınırları long job için güçlü hold sinyalidir. **HELD.** | Sürekli web/Background Worker modeli long job'a daha uygun olabilir; worker process kill/restart, queue lease ve shutdown drain kanıtı gerekir. **HELD.** | HTTP `waitUntil` sonrası yalnız 30 s devam edebilir; Queue/Workflow consumer ile 15 dakika ve idempotent checkpoint gerekir. **HELD.** | Uzun process mümkün olsa da host restart, deploy, memory leak ve orphan job recovery tamamen işletilir. **HELD.** |
| **F13 — Queue/backpressure / retry storm** | Durable queue; dedupe, lease/visibility timeout, max concurrency, retry budget, DLQ/quarantine, poison-message policy ve owner-readable backlog state gerekir. Queue boşluğu acceptance değildir. | External queue/worker ek maliyet ve failure plane'dir; nested function çağrıları için 2026 rate limitleri de release watch ister. **HELD.** | Key Value/Workflows/harici queue ve worker sayısı görünür; at-least-once delivery, graceful deploy drain ve backlog alarmı kanıtlanır. **HELD.** | Native Queues/Workflows seçilirse 15 dakika/CPU/billing sınırı ve queue retention/cost ayrıca doğrulanır. **HELD.** | Queue broker, persistence, failover ve DLQ bakımını owner-run yapmak no-owner-debug kuralıyla çatışabilir. **REJECT-IF-UNMITIGATED.** |
| **F14 — Log loss / sampling / retention gap** | Audit ayrı custody'de; log gap, metric gap veya trace loss varsa etki sonucu `UNKNOWN/HELD`, tamamlanmış sayılamaz. Incident evidence digest, clock/correlation ve export manifesti korunur. | Function log message 10.000 karakter ve event rate limitleri ile sınırlıdır; platform log retention plan bağımlıdır. **HELD.** | Web/worker/deploy logları farklı stream'ler olabilir; plan retention/export ve correlation ID olmadan **HELD**. | Workers Logs retention 7 gün; günlük limit aşımında sampling/truncation olabilir. Logpush/OTel bağımsız product audit değildir. **HELD.** | Disk/logrotate/replication arızası logu yok edebilir; tamper-evident remote sink yoksa **REJECT-IF-UNMITIGATED**. |
| **F15 — Cross-tenant direct call / BOLA / IDOR** | Tenant/scope actor'dan türetilir; client `tenant_id/resource_id` yalnız istek verisidir. API exact ownership/grant/policy/version kontrol eder, deny ve audit üretir. Generic direct DB/object path kapalıdır. | Data API grants/RLS/Storage policy defense-in-depth'tir; `service_role` veya exposed function bypass'ı product API yerine geçemez. **HELD.** | DB role ve object credential API içinde tutulur; internal/private service'i public endpoint sanmak risklidir. **HELD.** | Built-in Kavriva tenant policy yoktur; JWT/JWKS/issuer/audience ve tenant mapping tamamen proje contract'ıdır. **HELD.** | Network/DB firewall ve code policy birlikte işletilir; root/SQL erişimi nedeniyle blast radius en yüksektir. **REJECT-IF-UNMITIGATED.** |
| **F16 — AI task overprivilege / half-completed task** | AI görevi exact scope, credential class, dry-run, operation ID, forbidden actions, hard stop, evidence artifact,
  reviewer ve forward recovery taşır. AI owner/billing/root/service_role/unrestricted SQL/SSH/approval/publication yetkisi
  alamaz. Yarım iş `PARTIAL/RECONCILING`, otomatik “başarılı” değildir. | Supabase secret/function/admin bağlamları aynı project'te kolay karışabilir; least-privilege task pack kanıtı gerekir. **HELD.** | Üçüncü taraf API/queue/DB secret'ları AI context'ine sızabilir; service-by-service grant ve handoff gerekir. **HELD.** | Account token, worker secret ve edge deploy yetkisi ayrılmalı; dashboard'da görünür olması AI'ya verilebilir anlamına gelmez. **HELD.** | Root/SSH ve unrestricted SQL'e yakın operasyon yüzeyi vardır; no-owner-debug ve AI boundary kanıtı yoksa **REJECT-IF-UNMITIGATED**. |
| **F17 — Restore/failover anti-resurrection** | Restore önce isolated/quarantine ortamına alınır. Protected non-restorable release/security/deletion/operation/migration floor olmadan positive cutover yoktur. Eski revoke, recall, deletion, suspension veya accepted operation yeniden authority olursa `REJECT`. Cross-plane manifest DB+object+audit+identity+config+package+runtime release'i bağlar. | Managed core yakınlığı restore'ları kolay gösterebilir; fakat DB backup Storage bytes, audit/floor, function secret/config veya queue state'i otomatik geri getirmez. **HELD.** | DB, object, queue, artifact/config ve runtime release ayrı restore edilir; health green cutover kanıtı değildir. **HELD.** | Runtime version/Workers state ile Supabase data/floor ayrı düzlemlerdir; queue replay anti-resurrection test edilmelidir. **HELD.** | Restore/failover topology owner-run olduğu için eski volume/WAL/secret ile resurrection riski en görünür ve en ağırdır. **REJECT-IF-UNMITIGATED.** |
| **F18 — Provider exit / account closure / runtime migration** | Logical export; DB schema/data/roles; object bytes+digest+lineage; protected audit/floor; identity mapping; policy/config; package/operation generations; runtime artifact/contract ve secret reissue birlikte clean-room import edilir. Partial export `EXPORT_PARTIAL`; source değişmeden kalır. | Deno function kodu görece taşınabilir olsa da Supabase Auth/Storage/Management API/secret/config semantics adapter ister. `pg_dump` tek başına exit değildir. **HELD.** | Container image/API contract portable olabilir; Render deploy/health/queue/config ve adjunct audit semantics ayrıca taşınır. **HELD.** | Workers API, bindings, Queues/Workflows/Durable Objects ve edge assumptions provider-specific'tir; HTTPS contract yazılı değilse **HELD**. | Process/DB/object kontrolü en açık olabilir; yine de undocumented host, backup encryption, identity ve operational knowledge tek sahibin bağımlılığıdır. **HELD / no-owner gate.** |

## 5. Ortak kabul, incident, restore ve exit sonucu

Her failure için beklenen ürün sonucu aşağıdaki gibi görünür:

| Durum | Kullanıcı/owner'a görünen sonuç | Runtime'ın kanıtlaması gerekenler |
|---|---|---|
| `ACCEPTED` | Operation identity ve canonical version/generation görünür; audit ve object manifest bağlıdır. | DB transaction sonucu, protected audit event, object/queue side-effect status ve release/schema generation. |
| `DENIED` | Yetki yok; neden ürün diliyle görünür; retry yeni yetki yaratmaz. | Current actor/session/epoch/scope/policy, deny event ve no-effect proof. |
| `HELD` | Güvenli positive action yapılmadı; kullanıcı ve owner bekleyen nedeni görür. | Missing/uncertain dependency, hold timestamp/owner, retry/reconcile yolu. |
| `OUTCOME_UNKNOWN` | Request sonucu tahmin edilmez; status lookup/reconciliation beklenir. | Aynı operation ID'nin current state'i, duplicate guard ve effect/audit inspection. |
| `SERVICE_UNAVAILABLE` / `BILLING_HELD` | Safe history/safe-stop mümkünse sürer; positive mutation ve nonessential work durur. | Provider/account/quota evidence, stopped-work listesi, pending preservation, recovery owner. |
| `AUDIT_HELD` / `OBJECT_QUARANTINE` | Audit veya dosya güvenilir değil; yayın/approval yok. | Fallback custody, digest/lineage/scan/classification, orphan ve reconcile state. |
| `RESTORE_QUARANTINE` | Restored data authority değildir; eski negative state yeniden açılmaz. | Cross-plane manifest, protected floor comparison, version/epoch/policy check, no-cutover proof. |
| `EXPORT_PARTIAL` | Exit tamamlanmadı; source account silinmez ve yeni runtime authority kazanmaz. | Plane-by-plane export checklist, missing parts, digest, re-import result ve cleanup planı. |

### 5.1 Common hard-fail / reject cues

Aşağıdaki davranışlar runtime'dan bağımsız `REJECT-IF-UNMITIGATED`'dir:

1. Flutter/browser direct canonical DB/object write, public object veya global credential authority'si.
2. RLS, Storage policy, provider role, admin SDK veya dashboard'un product approval/recall/audit authority sayılması.
3. Timeout sonrası blind retry, guessed success veya duplicate side-effect.
4. Audit sink yokken positive effect; provider runtime log'unun immutable audit sayılması.
5. Quarantine/scan/digest tamamlanmadan object active/public handle verilmesi.
6. Restore snapshot'ının revoke/recall/deletion/suspension/accepted-operation floor olmadan cutover edilmesi.
7. Billing/quota/overage belirsizken safety plane'inin kapatılması veya unavoidable unbounded spend.
8. AI'ya provider owner/billing/root/service_role/unrestricted SQL/SSH/recovery/approval/publication yetkisi verilmesi.
9. Teknik olmayan sahibin SQL, SSH, log teşhisi, queue surgery, manual migration veya incident repair yapmasının
   gerekli olması.
10. Export/exit'in yalnız DB dump, provider clone, object durability veya image copy ile tamam kabul edilmesi.

## 6. TCO: normal, incident, restore ve exit maliyeti

### 6.1 Maliyeti okuma kuralı

Güvenli aylık toplam şu bileşenleri içerir:

`mandatory normal run-rate + metered usage + protected audit/floor + object backup + monitoring/notification + queue/long-job
runtime + support + incident reserve + restore/exit amortization + tax/FX/card uncertainty`.

TRY dönüşümü bu belgede yapılmamıştır. USD liste fiyatı, Türkiye KDV/VAT, kur, kart/banka komisyonu, support/SLA,
mağaza, domain/e-mail/SMS, cihaz ve AI/provider adjunct'larının yerini tutmaz. `Free`, quota deny, pause, alert veya
provider dashboard'u güvenli üretim toplam maliyetinin sıfır olduğu anlamına gelmez.

### 6.2 Runtime maliyet şekli (2026-09-19 resmi sinyal; purchase quote değildir)

| Aday | Normal aylık görünür sinyal | TCO'da hemen ayrıca yazılacak kalemler | Owner-operability okuması |
|---|---|---|---|
| **R1 Edge Functions** | Supabase Pro için önceki resmi snapshot yaklaşık `$25/ay`; Edge/compute, egress, log, Storage/Auth ve plan usage'ı ayrıca yeniden okunur. | Durable queue/worker, protected audit/floor, object backup/quarantine, monitoring/log drain, custom domain/DNS, incident/restore/exit ortamı; Spend Cap dışı compute/PITR gibi kalemler. | Görünen provider yüzeyi dar olabilir; Supabase coupling ve cap dışı kalemler gizli TCO üretmemeli. Routine burden potansiyel olarak düşük, kanıt yok. |
| **R2 Managed container** | Render Web Service için resmi fiyat sayfasında free/paid compute seçenekleri; araştırma snapshot'ında örnek paid web service `$7`/`$25` seviyeleri. Background Worker ücretsiz değildir; plan/region/usage tekrar doğrulanır. | Web + worker + queue/Key Value/Workflow, workspace/bandwidth/log/deploy, DB/object/audit adjunctları, support, graceful drain ve incident kapasitesi. | Service sınırları görünür; aynı zamanda hesap, fatura, deploy ve queue koordinasyonu artar. |
| **R3 Workers** | Workers Paid resmi snapshot minimum `$5/ay`; 10M request ve 30M CPU-ms dahil, ek request/CPU usage ücretli. Workers Logs Paid için 20M event/ay ve 7 gün retention sinyali vardır. | Supabase DB/Auth/Storage, Queue/Workflow, Logpush/OTel, audit/floor, object backup, DNS/TLS, custom auth/policy ve provider exit adapter'ı. | Küçük edge request için nakit tabanı düşük olabilir; core data plane ve authority işi ortadan kalkmaz. Overages ve retention gap ayrıca tutulur. |
| **R4 Self-managed** | DigitalOcean gibi baseline VM için önceki resmi snapshot `$4/ay` giriş sinyali; bu yalnız VM cash cost'tur. | Backup/volume/egress, alternate region, monitor/alert, patch/CVE, vault, object/audit backup, support, incident labor, restore/exit drill ve owner-independent operation. | En düşük headline cash ≠ en düşük TCO. Owner SQL/SSH/debug yapamayacağı için AI-operable managed controls kanıtlanmazsa üretim adayı değildir. |

Bu tutarlar 2026-09-19 tarihli araştırma sinyalleridir; plan değişikliği, tax/FX ve usage nedeniyle satın alma teklifi
değildir. R1–R4'ün shared Supabase core maliyeti ayrı normalized BOM satırı olarak her adayda aynı yazılmalıdır; aksi
halde edge/runtime adayı olduğundan ucuz görünür.

### 6.3 Maliyet horizon matrisi

| Horizon | Zorunlu maliyet kapsamı | R1 | R2 | R3 | R4 | Kabul/hold sonucu |
|---|---|---|---|---|---|---|
| **Normal ay** | Shared DB/Auth/Storage; API runtime; durable queue/worker; protected audit/floor; object backup; logs/monitoring; DNS/TLS; support; normal egress/usage. | Tek control-plane sinyali daha sade olabilir; compute, Storage/object, audit ve queue adjunctları görünür yazılmalı. | Web + worker + queue + logs/workspace ayrı kalem; free path üretim varsayılmaz. | `$5` base ve usage; DB/Storage/Auth/audit yine ayrı; 7 günlük logs yeterlilik kanıtı değildir. | VM küçük; bakım, backup, security ve human/AI operasyonu zorunlu maliyettir. | Exact bill yoksa `HELD`; shared adjunct gizlenirse `REJECT`. |
| **Incident ayı** | Duplicate capacity; retry/queue/log spike; temporary object/audit export; support/escalation; customer communication; cap/overage; safe-stop/failover. | Supabase ortak outage/billing etkisi blast radius yaratabilir; cap dışı kalemler sürer. | Partial provider health ve üçlü coordination correlation maliyeti artırır. | Edge ayakta iken DB outage olabilir; queue/Logpush/alternative endpoint maliyeti eklenir. | Alternate host/failover ve manual repair en pahalı owner riskidir. | Önceden owner-readable hold ve budget stop yoksa `REJECT-IF-UNMITIGATED`. |
| **Restore drill** | Isolated environment; DB+object+audit+identity+config+package+floor import; egress; verification; quarantine; reviewer; downtime/read-only. | DB backup/PITR Storage/audit/floor/queue state'i otomatik kapsamaz; cross-plane adjunct gerekir. | Web/worker artifact, queue, DB/object ve config ayrı restore edilir; health green yeterli değil. | Worker version/binding + Supabase planes + queue replay anti-resurrection kontrolü gerekir. | Backup/WAL/volume/failover/secret restore ve alternate region owner-run olur. | Clean-room/anti-resurrection evidence yoksa `RESTORE_QUARANTINE`. |
| **Exit drill** | Logical export; object bytes/metadata/digest; protected audit/floor; identity/policy/config; runtime artifact/API contract; secret reissue; dual-run; DNS cutover; decommission. | Deno taşınabilirliği olumlu sinyal; Auth/Storage/Functions/config semantics için adapter gerekir. | Container image/API contract güçlü; Render config/health/queue adjunctları taşınır. | Worker bindings/Queues/Workflows provider semantics; API contract ve DB portability ayrı. | Host kontrolü geniş; undocumented operational knowledge/identity/backup encryption riski yüksek. | `EXPORT_PARTIAL` source'u değiştirmez; clean-room import + negative tests olmadan çıkış yok. |

### 6.4 Cost class ve budget-hold

- **Mandatory:** API boundary, auth/session/epoch, idempotency ledger, protected audit/fallback, object quarantine/backup,
  restore/exit evidence, logs/monitoring, billing alert/stop, queue durability, no-owner-debug runbook.
- **Deferrable:** longer PITR/history, extra region/read replica, premium support, broad log drain, advanced media
  transforms, extra previews/branches. Deferrable kalem safety floor'un yerine geçmez.
- **Optional:** convenience realtime, dashboard cosmetics, noncritical analytics, nonessential heavy media, premium AI.
- **Scale-triggered:** request/CPU/CU, MAU, DB storage/history, object bytes/ops/retrieval, egress, queue/worker,
  logs, scanner, notification, support/HA.
- **Incident/restore/exit reserve:** duplicate runtime, isolated project/account, temporary storage, export/import,
  re-encryption/key rotation, support, independent review, DNS/cutover and decommission.

Ortak safe budget-hold:

1. Approval, publication, high-consequence mutation ve nonessential upload durur.
2. `BILLING_HELD` veya `ACCOUNT_HELD` owner-readable reason ile görünür olur.
3. Accepted operation, audit intent, local pending work, son güvenli package ve history korunur.
4. Blind retry, quota bypass, silently spend, manual DB/queue surgery ve owner dashboard repair yapılmaz.
5. Provider/billing ve cross-plane state doğrulanıp reconcile edilmeden positive path açılmaz.

Bu state machine uygulanamıyorsa maliyet belirsizliği yalnız finansal risk değildir; safety/no-owner-debug ihlalidir ve
ilgili runtime kullanımı `REJECT-IF-UNMITIGATED` olur.

## 7. Operability: tek teknik olmayan sahip ve bounded AI

### 7.1 Sahibin yapacağı / yapmayacağı

Sahip plain-language olarak `approve`, `hold`, `stop`, ödeme/hesap sahibi ve dış destek/insan bağımlılığı kararlarını
verebilir. Sahipten aşağıdakiler beklenmez ve ürün akışının gizli recovery yolu olamaz:

- SQL, SSH, provider console'da teknik repair veya migration;
- raw log/trace teşhisi, queue cursor surgery veya object orphan cleanup;
- `service_role`, root, billing-owner, recovery veya global object secret taşıma;
- restore cutover, deletion, key compromise veya cross-provider reconciliation'i elle yönetme.

Bir runtime için tek reliable recovery yolu bunlardan biri ise, managed görünse bile aday `REJECT-IF-UNMITIGATED`'dır.

### 7.2 AI task-pack sınırı

Her runtime task'ı aynı 10 alanı taşır:

1. Exact objective ve resource scope;
2. allowed / forbidden operations;
3. credential class, audience ve expiry;
4. read-only/dry-run başlangıcı;
5. `operation_id`, expected version/generation ve payload fingerprint;
6. hard-stop koşulu (`UNKNOWN`, `AUDIT_HELD`, `BILLING_HELD`, `RESTORE_QUARANTINE` dahil);
7. evidence artifact/digest ve reviewer;
8. forward recovery/reconciliation, rollback yerine güvenli ilerleme;
9. owner-facing plain-language handoff;
10. irreversible action için bağımsız approval.

AI'nın alamayacağı yetkiler bütün runtime'larda aynıdır: provider owner/billing root, raw `service_role`, unrestricted
SQL/SSH, global object key, restore-delete, role grant, approval/publication veya recovery authority. AI yalnız task-scoped
API/queue/observability/validation yüzeyinde çalışır.

### 7.3 Incident çıktısı

Her incident'te AI/otomasyon şu çıktıyı üretmelidir:

| Olay | Owner-readable çıktı |
|---|---|
| Timeout/response loss | `OUTCOME_UNKNOWN`, operation ID, status lookup ve duplicate guard durumu |
| Auth/role/key | Etkilenen actor/scope/epoch, durdurulan effects, rotation/reconciliation durumu; raw secret yok |
| Audit/object | `AUDIT_HELD`/`OBJECT_QUARANTINE`, hangi effect'in açılmadığı, manifest/digest durumu |
| Outage/billing | `SERVICE_UNAVAILABLE`/`BILLING_HELD`, son güvenli history/package, pending operations |
| Deploy mismatch | `DEPLOYMENT_HELD`, release/schema/queue generations ve no-cutover nedeni |
| Restore/exit | `RESTORE_QUARANTINE`/`EXPORT_PARTIAL`, eksik planes, source'un neden dokunulmadığı |

Provider dashboard'un yeşil görünmesi bu owner output'unu ikame etmez.

## 8. Kanıt paketi ve kabul gates

Bu belgedeki adaylardan birinin Phase-5 ADR'ye girebilmesi için aynı kanıt paketi gerekir. Belgesel araştırma kanıtı
mekanizma düzeyindedir; aşağıdaki gerçek evidence yokken candidate status `HELD` kalır:

1. **Timeout/duplicate:** commit-before-response, process kill, network loss, retry, same/different fingerprint ve
   exact outcome lookup; duplicate effect yok.
2. **Concurrency:** approval/publication ile revoke/recall/suspension race; generation fence, negative wins, ordered
   protected audit.
3. **Auth/tenant:** stale JWT/role, logout-all, security epoch, cross-tenant IDOR, direct DB/object/API bypass deny.
4. **Transaction:** DB partial failure, queue duplicate, outbox retry, provider timeout ve `RECONCILING` closure.
5. **Audit/object:** sink outage, log loss, object incomplete/digest mismatch, quarantine/scan/manifest/cleanup.
6. **Provider/billing:** region/DNS/provider outage, quota/throttle, account/billing hold, cap dışı kalem ve owner-readable
   safe-stop.
7. **Secret/deploy:** leaked key, rotation, in-flight revoke, old/new runtime compatibility, schema mismatch, rollback +
   forward migration, queue message version.
8. **Long jobs:** cold start, max duration, worker kill, backpressure, poison message, DLQ, retry storm, shutdown drain.
9. **Restore:** old revoked/deleted/recalled/accepted states restored into quarantine; no resurrection; cross-plane manifest.
10. **Exit:** alternate clean environment/provider/runtime import; identity/policy/object/audit/floor/package/operation
    negative tests; secret reissue; source untouched until acceptance.
11. **Cost:** same normalized BOM for normal, incident, restore and exit; plan/region/usage/tax/FX/support and hard-cap
    semantics; no budget weakening.
12. **AI-operability:** all task packs, forbidden scope, dry-run, stop/reconcile, evidence, reviewer and owner handoff;
    no SQL/SSH/debug dependency.

### 8.1 Belgesel sonuç tablosu

| Aday | Runtime mekanizması research | 18 failure | Normal/incident/restore/exit TCO | No-owner-debug | Genel Phase-4 durumu |
|---|---|---|---|---|---|
| R1 Supabase Edge | Kısmen `CONFIRMED`; limits/background/deploy kaynakları var | 18 satır için gerçek fixture yok | Shared core, cap-dışı kalemler ve adjunctlar açık değil | Potansiyel olarak en sade; kanıt yok | **HELD** |
| R2 Managed container | Health/deploy/rollback/worker primitives `CONFIRMED` | Cross-service/queue/schema evidence yok | Runtime + worker + queue + support composition açık değil | Orta; provider coordination kanıtlanmadı | **HELD** |
| R3 Workers | Limits/pricing/logging `CONFIRMED` | DB/Auth/audit/queue exit coupling açık değil | Base düşük olabilir; usage/retention/core adjunctlar açık değil | Orta; custom authority işi yüksek | **HELD** |
| R4 Self-managed | Process/control primitive'leri `CONFIRMED` | Owner-run failure/recovery rehearsal yok | Cash düşük olabilir; labor/DR/exit yüksek | No-owner-debug ile gerilimli | **HELD / REJECT-IF-UNMITIGATED** |

`HELD`, güvenli veya production-ready demek değildir; yalnızca proof eksikliğiyle birlikte güvenli hold yolu
tasarlanabilir demektir. Aynı kritik evidence üç kez eksik kaldığında karar dili `BLOCKED` değil, ilgili capability için
`HELD/REJECT-IF-UNMITIGATED` olarak kalır; provider otomatik kazanan olmaz.

## 9. Phase-4 disposition ve Phase-5 giriş koşulu

### 9.1 Bu araştırmanın disposition'ı

- `R1 Supabase Edge Functions` düşük-operasyonlu başlangıç adayı olarak `DEC-0035` ile uyumludur, fakat production
  runtime winner değildir. Long job, queue, audit/floor, object/recovery, spend-cap exclusion ve no-owner-debug kanıtı
  olmadan yalnız **reversible working candidate** olarak kalır.
- `R2 managed container` API/worker/deploy/rollback sınırlarını görünür kılar; `Neon + Render + R2` fallback'inin API
  runtime temsilidir. Daha çok control-plane ve account/billing korelasyonu maliyeti vardır; bu aday da `HELD`'dir.
- `R3 Workers` edge request ve metered base için geçerli counterfactual'tır. Supabase DB/Auth/Storage, custom
  authorization, audit/floor, Queue/Workflow ve exit adapter'ı işi ortadan kalkmaz; `HELD`'dir.
- `R4 self-managed` exit/control baseline'ıdır. Teknik olmayan owner modelinde patch/restore/failover/SSH/SQL burden
  güvenli biçimde AI-runbook ile dışlanamıyorsa üretim adayı değildir; **automatic low-cost fallback değildir**.

### 9.2 Phase-5 ADR'ye geçmeden önce

1. Aynı 18 senaryo ve aynı workload fixture için gerçek runtime fault evidence;
2. API contract, idempotency ledger, audit/floor, object manifest, queue/worker ve auth/tenant negative testleri;
3. Supabase/DB/object/audit/identity/config/package/runtime release cross-plane restore manifesti ve anti-resurrection;
4. Provider outage, DNS, billing/quota, account closure, secret rotation ve owner-readable hold rehearsal;
5. Container/function/worker deploy rollback + schema/message compatibility ve clean-room exit;
6. Her aday için normal/incident/restore/exit normalized BOM; TRY ceiling, tax/FX ve support/incident reserve;
7. AI task-pack ve no-owner-debug evidence; owner yalnız plain-language hold/approval verir;
8. Independent security/recovery review + owner/TCO/operability review.

Bu kanıtlar olmadan ADR, provider account, paid plan veya Gate 4 -> 5 transition yapılmaz.

## 10. Primary sources and repository evidence

### Supabase / runtime

- [Edge Functions overview](https://supabase.com/docs/guides/functions) — kısa, idempotent request; cold start ve heavy
  long-running işlerin worker'a taşınması; server-side auth/policy boundary.
- [Edge Functions limits](https://supabase.com/docs/guides/functions/limits) — 256 MB, 150/400 saniye, 2 saniye CPU,
  log/event/secrets limitleri.
- [Background Tasks](https://supabase.com/docs/guides/functions/background-tasks) — `waitUntil`, shutdown ve limitlerde
  task kesilmesi; durable queue yerine geçmediği için bu belgede ayrıca queue şartı vardır.
- [Supabase Edge Functions changelog](https://supabase.com/changelog?tags=edge+functions) ve [nested call rate limit](https://supabase.com/changelog/43644-edge-functions-rate-limits-on-recursive-nested-edge-functions-calls) — deploy/API ve 2026 nested-call drift watch.
- [Supabase cost control](https://supabase.com/docs/guides/platform/cost-control), [backups/PITR](https://supabase.com/docs/guides/platform/backups), [securing Data API](https://supabase.com/docs/guides/api/securing-your-api), [RLS](https://supabase.com/docs/guides/database/postgres/row-level-security), [Storage access control](https://supabase.com/docs/guides/storage/security/access-control).

### Managed container

- [Render Web Services](https://render.com/docs/web-services) — HTTP service, secrets, health check, zero-downtime ve
  service boundary.
- [Render Health Checks](https://render.com/docs/health-checks) — 5 saniye health response, yeni deploy health gate'i,
  failed deploy cancellation ve instance restart davranışı.
- [Render Deploys](https://render.com/docs/deploys) — zero-downtime, pre-deploy migration, graceful `SIGTERM`/shutdown,
  ephemeral filesystem ve worker task davranışı.
- [Render Rollbacks](https://render.com/docs/rollbacks) — build artifact rollback; current config/disk state'in otomatik
  olarak target deploy'e dönmediği sınırlar.
- [Render Background Workers](https://render.com/docs/background-workers) ve [Render pricing](https://render.com/pricing).

### Cloudflare Workers

- [Workers limits](https://developers.cloudflare.com/workers/platform/limits/) — 128 MB, 1 saniye startup, CPU/wall-time,
  Queue consumer 15 dakika, `waitUntil` için 30 saniye uzatma sınırı.
- [Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/) — `$5` Paid base, included request/CPU,
  metered overage ve custom CPU limit.
- [Workers Logs](https://developers.cloudflare.com/workers/observability/logs/workers-logs/) — retention, sampling,
  truncation ve Logpush seçenekleri.

### Kavriva karar ve önceki eşit araştırma

- [`DEC-0034`](../../00_CONTROL/DECISION_LOG.md) — logical authority, server/API, protected audit/floor, restore/exit.
- [`DEC-0035`](../../00_CONTROL/DECISION_LOG.md) — Supabase-centered working direction, API mediation, independent
  object/audit/recovery controls and Neon+API+R2 fallback.
- [`DEC-0036`](../../00_CONTROL/DECISION_LOG.md) — durable operations, outcome-unknown and offline package boundaries.
- [`DEC-0037`](../../00_CONTROL/DECISION_LOG.md) — auth != authority, security epoch, protected audit and AI limits.
- [`DEBATE-008 Manager Synthesis`](DEBATE-008__MANAGER_SYNTHESIS.md) — managed Supabase vs modular fallback and reversal
  triggers.
- [`DEBATE-008 Owner/TCO review`](DEBATE-008__REVIEW_OWNER_TCO_OPERABILITY.md) — no-owner-debug, normalized BOM,
  cost horizons and common failure states.
- [`DEBATE-008 Stack primary research`](DEBATE-008__STACK_CANDIDATES_COST_PRIMARY_RESEARCH.md) — dated candidate
  pricing/limits/caps, backup/object separation, AI-operability and common acceptance gates.

