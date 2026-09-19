# DEBATE-011 — Düzeltilmiş Judge Sentezi

Status: `PASS_WITH_CHANGES INCORPORATED / USER APPROVED DEC-0038 / A-B HELD / NO RUNTIME WINNER / ADR NOT READY`
Date: `2026-09-19`
Scope: `NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`

## 1. Hüküm

Araştırma, yönetici önerisi ve iki bağımsız Luna Max incelemesi ortak yönü koruyor fakat hiçbir runtime veya provider'ı
üretim kazananı saymıyor:

- **Supabase Edge Functions**, yalnız kısa ve DB-yakın Kavriva API istekleri için geri alınabilir Phase-4 çalışma
  hipotezi olarak tutulabilir. Bu bir runtime/provider/plan seçimi veya production `PASS` değildir.
- **Managed container API + worker**, önceden tanımlı alternatif hipotezdir; Aday A bir sınırı geçemediğinde otomatik
  kazanmaz. İkinci provider, ağ, queue/worker, support, fatura ve çıkış yükünü aynı fixture ile kanıtlamalıdır.
- **High-consequence ürün otoritesi runtime'da değildir.** Current authorization, stable operation, canonical effect,
  protected audit precondition ve external-effect intent açık bir ürün protokolüdür.
- **Bilinen uzun işler ertelenmiş mimari borç değildir.** Package build, object scan/preview/derivative, export, AI/OCR,
  notification ve geniş reconciliation ilk capability'den itibaren durable queue/worker gate'ine tabidir. Exact ürün
  ve başlangıç zamanı açık kalabilir; semantic contract ve maliyet kapsamı açık kalamaz.
- **Protected audit/floor ve emergency-negative minimum davranışı sonraki tartışmaya bırakılmaz.** Exact teknoloji
  açık kalabilir; audit yokken positive effect'in `AUDIT_HELD`, outage'ta positive hold ve dar negative authority'nin
  hangi kanıtla çalışacağı şimdi bağlanır.

Belgesel hüküm iki finalist için de `0 PASS / 16 HELD / 0 REJECT`tir. Bu sayı `API-AC-001..024` veya 18 failure
sınıfının yerine geçmez; yalnız yönetici karşılaştırmasının özetidir. `HELD`, güvenli veya production-ready demek
değildir.

## 2. Kullanıcıya teknik olmayan karar özeti

Telefon ve şirket içi tarayıcı, önemli veriyi doğrudan değiştirmeyecek. Her işlem Kavriva'nın kontrol kapısından
geçecek. Kapı, kişinin o anda hâlâ yetkili olup olmadığını, aynı işlemin daha önce yapılıp yapılmadığını ve işlem için
korumalı kanıtın hazır olup olmadığını kontrol edecek. Bağlantı koparsa işlem ikinci kez körlemesine yapılmayacak;
sonucu işlem numarasıyla bulunacak veya açıkça “sonuç henüz bilinmiyor” denecek.

Bu kapıyı ilk aşamada Supabase'in yakın çalışma alanında kısa işler için planlamak en sade hipotezdir. Dosya tarama,
paket hazırlama, dışa aktarma veya AI işi gibi uzun işler burada zorlanmayacak; dayanıklı iş sırasına verilecek. Supabase
sınırları, güvenlik ayrılığı veya toplam maliyet uygun çıkmazsa aynı kapı ayrı yönetilen sunucuya taşınabilecek. Ancak
iki yol da gerçek arıza, kurtarma ve maliyet kanıtı olmadan seçilmiş sayılmayacak.

## 3. Bağlanan runtime-bağımsız API sınırı

### 3.1 Runtime geçici, ürün durumu kalıcıdır

API instance/function/container kapanabilir ve yenisi başlayabilir. Runtime belleği canonical truth değildir. Kalıcı
state en az şunları kapsar:

- canonical domain state ve immutable version/generation;
- operation identity, request fingerprint ve status;
- authorization/policy/grant/competence/security generation referansları;
- protected audit receipt/event ve ordered floor;
- outbox/queue intent, effect key ve reconciliation state;
- object/package manifest, lineage, classification ve negative eligibility floor;
- release/suspension/recall/deletion/accepted-operation/migration floors.

“Stateless API”, ürünün state'siz olduğu anlamına gelmez.

### 3.2 Tam commit-time karar tuple'ı

Her hassas işlem effect'ten hemen önce şu provider-neutral tuple ile `ALLOW`, `DENY` veya `HELD` üretir:

- actor/workload ve provider-qualified principal;
- issuer, current session, assurance/step-up ve security epoch;
- action, exact object/resource, tenant/owner, scope ve classification;
- role/grant/delegation, competence, independence ve policy/access version;
- object/version/generation, release/schema/config/package/client capability;
- current recall/suspension/revocation/deletion ve other negative floors;
- operation ID, immutable request fingerprint, reason ve intended effect;
- protected audit readiness/receipt ve runtime/dependency compatibility.

Cached JWT claim, `user_metadata`, UI düğmesi, stale sekme, provider role, RLS sonucu veya client-supplied ID bu tuple'ın
yerine geçmez.

### 3.3 Authoritative transaction core ile cross-plane effect ayrılır

DB transaction fiziksel olarak bütün dış sistemleri atomik yapmış sayılmaz. Dar authoritative core şu anlamları aynı
DB assurance sınırında bağlar:

1. immutable operation/request acceptance;
2. current authorization ve expected generation fence;
3. canonical DB effect veya prepared transition;
4. protected audit precondition/receipt reference;
5. deterministic outbox/effect intent;
6. canonical status ve reconciliation owner.

Object, notification, queue delivery, scanner, AI/OCR veya external provider effect'i ayrı idempotent protocol'dür.
Her dış effect deterministic key, manifest, lease/retry budget, current generation/epoch recheck ve reconciliation
state taşır. DB commit, queue empty veya worker success bu dış effect'lerin tümünü kanıtlamaz.

## 4. Reviewer düzeltmeleri — bağlayıcı ekler

### 4.1 Protected audit-before-effect protokolü

`audit_intent` yazmak tek başına protected product audit değildir. High-consequence positive effect ancak:

- gerekli product audit event'i protected primary custody veya yeterince bağımsız fallback tarafından kabul edilmiş;
- acceptance/receipt operation ve exact intended effect'e bağlanmış;
- DB commit anında receipt, current authorization ve generation yeniden doğrulanmış;
- commit olmazsa audit event sonucu `NO_EFFECT/ABORTED`, belirsizse `OUTCOME_UNKNOWN/RECONCILING` olarak kapanmış;
- effect olur ama response kaybolursa status lookup canonical effect + audit receipt ile çözmüş

ise açılır. Exact teknoloji veya tek/iki aşamalı implementation Phase 5'e açıktır; fakat bu semantik değişmez. Primary ve
fallback custody yoksa positive action `AUDIT_HELD` olur. Runtime/provider log'u bu receipt değildir.

Audit event actor/workload, role/scope, issuer/session assurance, epoch, policy/grant/competence generation,
operation, object/version, old/new meaning, ordered server time, reason, result, impact ve recovery owner taşır.
Gap/fork/replay, retention/legal hold, read/export/redaction ve restore reconciliation ayrıca kanıtlanır.

### 4.2 Operation ve idempotency kapsamı

Operation identity actor/tenant/action/resource/scope/classification ve immutable payload fingerprint ile bağlanır.
Aynı identity:

- aynı semantic request ise mevcut sonucu read-only döndürür;
- farklı payload, actor, scope veya intended effect ise `CONFLICT/HELD` olur;
- başka tenant/actor tarafından status lookup için kullanılırsa `DENY` olur.

Operation ID namespace/uniqueness, retention/tombstone, restore replay ve cross-region davranışı Phase-5 kanıtıdır.
Timeout-before/after-commit, process kill, duplicate queue delivery, old-epoch retry ve same-ID/different-payload
fixture'ları geçmeden sensitive effect açılmaz.

### 4.3 Bilinen long-job capability gate

Aşağıdaki iş aileleri synchronous request'e sığdırılmaya çalışılmaz:

- offline package build ve geniş manifest/reconciliation;
- object upload finalization, archive/URL safety, scan, render, derivative, OCR/AI ve orphan cleanup;
- large export/import, restore ve clean-room verification;
- bulk notification/reach-back ve delivery reconciliation;
- uzun AI/research/ingestion veya batch işlemleri.

Her iş `ACCEPTED/QUEUED` ile gerçek effect'i ayırır; operation/effect key, lease, heartbeat/checkpoint, bounded retry,
DLQ/quarantine, poison handling, backpressure, cancel, deploy drain, old/new message compatibility, owner-visible backlog
ve resolver taşır. Queue “exactly once” veya empty sinyali ürün effect'inin yalnız bir kez tamamlandığını kanıtlamaz.

Exact queue/worker ürünü, hangi capability'nin ilk release'e gireceği ve sayısal limitler açık kalır. Bir capability
long-job gate'i gerektiriyorsa queue/worker/audit/object/restore/exit BOM'u o capability açılmadan zorunlu olur.

### 4.4 Monotonic negative model

Recall, suspension, revoke, delete, object/package eligibility, accepted operation ve migration floor'ları restore
edilebilir sıradan snapshot state'i gibi ele alınmaz. Publication/worker effect commit öncesi current floor'u yeniden
okur; eşit veya daha yeni negative generation positive effect'i kazanır. Missing/unknown/tie, audit outage veya stale
lease positive success'e çevrilmez; `HELD/OUTCOME_UNKNOWN` olur.

Rollback yalnız current, compatible ve not-recalled predecessor'a yeni guarded event'tir. Eski runtime, queue message,
browser cache, object handle veya offline package newer negative floor'u temizleyemez.

### 4.5 End-to-end security epoch

Epoch/session/grant revoke şu uçların hepsine ulaşmadan tamam sayılmaz:

- current/pending/in-flight API operation ve lost-response retry;
- queue/worker lease ve effect öncesi recheck;
- private object handle ve object generation;
- browser cache/service worker ve açık sekme;
- Flutter local package, offline ledger ve local key state;
- status lookup, export ve account migration.

İndirilmiş kopya uzaktan kesin geri alınamaz; residual risk dürüstçe gösterilir. Remote wipe authority değildir.

### 4.6 Emergency-negative ve recovery failure-domain sözleşmesi

Outage matrisi Auth/API/DB/object/audit/floor/DNS/billing/queue/worker düzlemlerini ayrı ayrı kapsar. Her satır:

- safe read/history;
- positive mutation hold;
- emergency negative availability;
- accepted/pending data preservation;
- minimum protected evidence/negative floor;
- owner-readable state ve external support/recovery actor;
- cost ve restore reconciliation

çıktısı verir. Account recovery positive approval/publish/unsuspend/role grant vermez. Emergency negative yol yalnız
suspend/recall/quarantine/deny üretir. Normal ve fallback aynı hesap/credential/failure domain'inde ise bağımsız sayılmaz.

Tek owner ve AI, bağımsız gerçek insan/kurum recovery/negative actor'ını taklit edemez. Bu dış bağımlılık kapanana kadar
ilgili privileged/high-consequence production capability `HELD` kalır.

### 4.7 Direct provider yolu ve browser sınırı

Exposed table/view/function/RPC/Storage/signed URL/provider Studio yüzeyleri envanterlenir. Generic client yolu
high-consequence mutation, export veya private object authority taşıyamaz. DB function yalnız dar transaction boundary
için, explicit actor/scope/epoch kontrolü, non-exposed schema ve public execute kapalı biçimde kanıtlanır.

Browser contract; cookie/token storage, trusted origin/redirect allowlist, CSRF, PKCE, action-resource-version-
consequence bağlı step-up, tab replay ve status lookup disclosure sınırlarını taşır. Operation ID başka tenant'ın sonucu,
audit özeti veya private payload'ını açamaz.

### 4.8 Object ve offline lanes

Object lifecycle quarantine-first'tür. Size/digest/version/lineage/classification, malicious archive, SSRF/private URL,
redirect, traversal/decompression, scan/render ve derivative inheritance tamamlanmadan active/public handle yoktur.
Handle exact audience/scope/object/version/epoch bağlıdır; derivative en restrictive classification'ı taşır.

Offline package yalnız selected motorcycle/task ve complete compact safety/application/safe-stop/recovery closure'dır.
Local save, queue empty, push/Realtime veya download completion canonical acceptance/freshness/recall değildir. Ledger,
tombstone/delete, device restore, conflict ve account-light migration no-silent-loss/no-silent-LWW kurallarını korur.

### 4.9 Release ve deploy compatibility

Runtime `release_id`, DB schema/config/migration generation, API/client capability, queue message generation, content/
object/package manifest ve current negative floor birlikte compatibility graph'inde değerlendirilir. Health green veya
runtime rollback bu düzlemleri geri almaz. Mismatch `DEPLOYMENT_HELD`; database/data için forward recovery esastır.

### 4.10 Tek state dictionary

Kavriva API ve owner runbook aynı sözlüğü kullanır:

- `ACCEPTED`: canonical effect kanıtlı;
- `QUEUED/SUBMITTED`: iş kabul edildi, effect henüz kanıtlanmadı;
- `DENIED`: current policy/yetki açıkça izin vermedi;
- `HELD`: güvenli olumlu karar için şart/kanıt eksik;
- `OUTCOME_UNKNOWN`: effect sonucu henüz kanıtlanamıyor;
- `PARTIAL/RECONCILING`: bazı plane/effect'ler tamamlandı, kapanış sürüyor;
- `AUDIT_HELD`, `BILLING_HELD`, `ACCOUNT_HELD`, `DEPLOYMENT_HELD`: ilgili hard gate kapalı;
- `OBJECT_QUARANTINE`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`: aktif kullanım/cutover yasak;
- `SERVICE_UNAVAILABLE/RECOVERY_REQUIRED`: owner'a güvenli sonraki adım ve dış sorumlu gösterilir.

Her state allowed/blocked effects, retained data, retry policy, cost stop, resolver/support, audit reference ve
restore/exit etkisini taşır. Green dashboard, HTTP 2xx, worker success veya empty queue state'i değiştiremez.

## 5. Adayların düzeltilmiş konumu

### Runtime A — Supabase Edge Functions

Kısa DB-yakın command/status/read için düşük-operasyonlu hipotezdir. Ancak:

- 2 saniye CPU, 256 MB memory, wall-clock/idle/bundle/log limitleri;
- transaction pooler/session-state davranışı;
- immutable rollout/rollback ve old revision drain kanıt açığı;
- Auth/DB/Storage/Functions common-mode riski;
- deferred adjunctların gizli TCO'su

nedeniyle `HELD`dir. Long job background callback/`waitUntil`'a bırakılırsa, audit/floor yokken effect commit edilirse,
direct provider bypass oluşursa veya restore negative floor'u diriltirse ilgili capability `REJECT-IF-UNMITIGATED` olur.

### Runtime B — Managed container API + worker

Persistent runtime, custom dependency ve görünür worker lifecycle için alternatif hipotezdir. Ancak:

- ikinci provider/account/billing/support/credential;
- cross-provider TLS/region/pooler/latency/egress;
- web/worker/queue/deploy/schema/message koordinasyonu;
- image portability'nin managed state'i taşımaması;
- partial-health ve no-owner-debug riski

nedeniyle `HELD`dir. Container health product truth, queue delivery canonical effect veya image rollback data recovery
değildir. A'nın hard-fail'i B'yi otomatik kazanan yapmaz.

### Challenger'lar

Cloudflare Workers dar edge/emergency-negative/gateway veya ileride kanıtlanan edge workload için; Cloud Run managed
container/control-plane alternatifi için açık kalır. Self-managed VM düşük headline fiyatına rağmen owner patch/SSH/
restore yükü kapanmadan başlangıç adayı değildir. Hiçbiri bugün seçilmez.

## 6. Equal evidence ve geçiş kuralı

A ve B aynı route/capability sınıfları, workload, failure injection, audit/object/queue/recovery kapsamı, owner/AI sınırı
ve normalized BOM ile değerlendirilir. Her fixture şu çıktıları verir:

1. expected semantic state;
2. attempted ve actual side effect;
3. protected audit evidence/receipt;
4. recovery owner ve owner-readable next action;
5. cost/exit impact.

A'dan B'ye ancak A ilgili mandatory gate'i gerçek fixture'da geçemez ve B aynı gate paketini kanıtla geçerse dönülür.
Sezgisel “daha esnek”, “daha ucuz” veya yalnız headline limit/fiyat geçiş gerekçesi değildir. İkisi de geçmezse standardı
düşürmek yerine capability `HELD` kalır ve challenger eşit kapsamla yeniden açılır.

## 7. Owner, support ve AI-operability hard gate

Her outage/incident için detection, automatic safe-stop, affected scope, retained data, owner-visible state, external
human/provider action, credential class, support target, cost/overage, forward reconcile, reviewer ve exit evidence
tanımlanır.

Owner yalnız plain-language `approve / hold / stop / payment / legal-support request` kararı verir. Owner'dan SQL, SSH,
raw log teşhisi, queue surgery, secret taşıma, restore cutover veya provider-console repair beklenmez. Account/legal/
billing owner, provider support, recovery verifier, audit/floor custodian ve emergency-negative operator ayrımı açık
değilse production capability `HELD`dir.

AI task pack; exact objective/scope, allowed/forbidden operation, short-lived credential audience/expiry, dry-run,
operation/expected generation, hard-stop, evidence digest, independent reviewer/validator, forward recovery, external
human action ve owner-facing handoff taşır. AI provider owner, billing root, `service_role`, unrestricted SQL/SSH,
global object key, restore-delete, approval/publish veya privileged recovery authority alamaz.

## 8. Normalized safe-cost BOM

A ve B aynı satır kimlikleriyle en az şunları taşır:

- shared DB/Auth/private Storage compute, IO, bytes/ops/egress, backup/PITR;
- API invocation veya web instance, build/image/registry, concurrency/minimum uptime;
- transaction/pooler/TLS/region/egress;
- durable queue/worker, retention/retry/DLQ/backpressure/scheduler;
- protected product audit, bağımsız fallback/floor, retention/legal hold;
- logs/metrics/traces, correlation/export/alert;
- object quarantine/scanner/derivative/backup/restore/temporary storage;
- deployment/schema/message compatibility, secret/key rotation;
- provider account/billing/support/account-lock/closure;
- DNS/TLS/domain ve gerekiyorsa SMTP/notification/SMS;
- incident capacity, isolated restore drill ve clean-room exit;
- external support/recovery people ve independent review;
- AI task operation ve evidence custody.

Her satır `mandatory / deferrable / optional / scale-triggered`, official date/plan/region, unit/quota/overage, tax/FX/
card uncertainty, hard-cap kapsamı, stop state, incident/restore/exit etkisi ve owner approval durumu taşır. Mandatory
assurance bütçeye sığmıyorsa zayıflatılmaz; capability `BILLING_HELD/HELD` kalır.

## 9. Restore ve clean-room exit hard gate

DB dump, provider clone, object copy veya container image tek başına restore/exit değildir. Isolated quarantine import:

- canonical current/history/provenance;
- operation ledger/status/conflict/tombstone/outbox;
- release/package/artifact/schema/config/message generations;
- provider-qualified principal, policy/grant/competence, session/epoch/recovery state;
- object bytes, digest/lineage/classification/retention/disclosure;
- protected audit/fallback/floor ve incident/impact graph;
- queue pending/DLQ/lease, runtime artifact, secret reissue ve DNS cutover

plane'lerini manifest/digest ile uzlaştırır. Current source acceptance öncesi değişmez. Old revoke/recall/delete/
suspension/accepted operation dirilmez; yeni valid data silent rollback ile kaybolmaz. Independent acceptance sonrası
dual-run/cutover/decommission yapılır. Eksik plane `EXPORT_PARTIAL` veya `RESTORE_QUARANTINE` olarak kalır.

## 10. Phase-5 acceptance paketi

İki aday aynı no-code fixture tanımlarını daha sonra gerçek evidence ile geçmelidir:

1. direct-path/cross-tenant/provider-console bypass;
2. stale session/role/epoch, commit-time authz ve two-issuer/privileged step-up;
3. timeout-before/after-commit, duplicate/different fingerprint ve status disclosure;
4. DB/outbox/object/notification partial failure ve reconcile;
5. queue lease/worker kill/poison/retry/DLQ/backpressure/deploy drain;
6. protected audit primary/fallback outage, effect-before-audit, gap/fork/replay;
7. publish vs recall/suspension ve invalid rollback;
8. object quarantine/SSRF/archive/digest/lineage/classification/handle revoke;
9. offline package/ledger/device restore/tombstone/conflict/account migration;
10. end-to-end epoch through operation/worker/handle/cache/package/retry;
11. cross-plane restore/anti-resurrection/source preservation;
12. provider/DNS/account/billing/quota partial outage ve negative availability;
13. deploy/schema/message/secret compatibility ve forward recovery;
14. no-owner-debug/AI forbidden credential/support handoff;
15. normal/incident/restore/exit normalized BOM ve spend stop;
16. clean-room runtime/provider replacement.

Gerçek evidence yokken `PASS` yoktur.

## 11. User-approved Phase-4 yönü

Kullanıcı aşağıdaki düzeltilmiş çalışma yönünü `DEC-0038` altında onayladı:

- provider-neutral Kavriva API, client/provider-console direct authority'yi engeller;
- Supabase Edge Functions kısa DB-yakın request'ler için geri alınabilir ilk çalışma hipotezidir, production winner
  değildir;
- managed container API + worker eşit kanıt isteyen önceden tanımlı alternatif hipotezdir, otomatik fallback değildir;
- protected audit receipt/precondition olmadan positive high-consequence effect `AUDIT_HELD`;
- long-job aileleri şimdiden durable queue/worker semantic gate'ine tabidir; exact teknoloji açık;
- full commit-time authorization, idempotency/status lookup, monotonic negative floors ve end-to-end epoch zorunludur;
- owner/support/account, normalized cost, restore/anti-resurrection ve clean-room exit hard gate'tir;
- iki aday `HELD`, no runtime/provider/plan/framework/dil/queue/region hesabı veya satın alma seçilmemiştir.

Bu onay kod, prototype, executable test, deployment, Supabase/Render/Cloudflare/Google hesabı, ücretli plan, runtime ADR,
production activation veya Gate 4 -> 5 geçişi değildir.

## 12. Review kayıtları

- `DEBATE-011__REVIEW_A_SECURITY_RECOVERY.md`: `HELD / NO WINNER`, 8 critical, 13 major, 4 minor.
- `DEBATE-011__REVIEW_B_OWNER_TCO_OPERABILITY.md`: `HELD / NO WINNER`, 5 critical, 9 major, 4 minor.

İki review da short DB-near Edge çalışma hipotezini topyekûn reddetmez; ikisi de A veya B için production `PASS`,
provider seçimi, runtime ADR veya gate geçişi vermez. Kullanıcı düzeltilmiş Phase-4 çalışma yönünü `DEC-0038` altında
onayladı.
