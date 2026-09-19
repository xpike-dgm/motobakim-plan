# DEBATE-011 — KAVRIVA API RUNTIME, BOUNDARY ENFORCEMENT VE OPERASYON GEREKSİNİMLERİ

Status: `DRAFT — PHASE-4 REQUIREMENTS SYNTHESIS / NO-CODE / PROVIDER-RUNTIME-DİL-FRAMEWORK BAĞIMSIZ / ADR PENDING`  
Date: 2026-09-19  
Decision level: Mantıksal API otoritesi, istemci sınırları, yüksek sonuçlu işlem ve işletim gereksinimleri  
Scope: Kavriva consumer Flutter istemcisi + browser-based Internal Operations + ortak veri, nesne, kimlik, offline işlem,
release/recall, audit, recovery, maliyet ve çıkış sınırları

## 1. Amaç ve karar sınırı

Bu kayıt, `DEBATE-007`–`DEBATE-010` içinde dağınık halde bulunan Kavriva API gereksinimlerini tek bir
provider/runtime/dil/framework bağımsız sözleşmede toplar. Amaç API'yi yalnızca HTTP taşıma veya CRUD arayüzü olarak
değerlendirmemek; istemcilerin güvenilmez, eski, çevrimdışı veya ele geçirilmiş olabileceği durumda canonical truth,
yetki, audit, nesne erişimi, işlem sonucu, release/recall ve recovery anlamının nerede korunacağını açıkça sınamaktır.

Bu belge:

- Kavriva API'nin neden zorunlu bir authority boundary olduğunu;
- Flutter ve browser Internal Operations istemcilerinin ne yapabileceğini ve ne yapamayacağını;
- high-consequence işlemlerde commit-time authorization, audit-before-effect ve negatif otorite sıralamasını;
- idempotency, status lookup, `OUTCOME_UNKNOWN`, conflict/hold/reconciliation anlamlarını;
- object/media mediation, quarantine ve classification yayılımını;
- Flutter offline operation ledger'ının server ile bağını;
- immutable release, publication, suspension/recall ve anti-resurrection ilişkisini;
- identity, session ve security-epoch iptalini;
- teknik olmayan tek owner, AI-operated çalışma ve bounded operations koşullarını;
- maliyet, overage, provider değişimi, backup/restore ve clean-room exit gereksinimlerini;
- kabul kriterlerini, hard-fail koşullarını ve sonraki eşit aday karşılaştırma fixture'ını

tanımlar.

Bu belge şunları seçmez veya onaylamaz:

- API runtime, programlama dili, framework, deploy modeli veya event/queue ürünü;
- database, BaaS, object store, identity provider, audit sink, cloud/region veya hosting provider;
- API sürümü, schema, endpoint adı, token süresi, retry/retention sayısı veya RPO/RTO;
- kod, prototype, executable spike, provider hesabı, ücretli plan, satın alma, üretim kanıtı veya Phase-5 ADR.

Mantıksal boundary ayrı deploy edilen servis demek değildir. İleride seçilecek fiziksel düzen, bu sözleşmeleri tek bir
uygulamada veya birden fazla bileşende taşıyabildiğini eşit kanıtla göstermelidir.

## 2. Bağlayıcı girdiler ve mevcut çalışma yönü

### 2.1 Karar girdileri

Bu sentezin bağlayıcı üst girdileri:

- `DEC-0025`: immutable approval/release, fenced publication, bağımsız dar emergency negative authority,
  `OUTCOME_UNKNOWN`, protected audit ve restore quarantine;
- `DEC-0026`: server-authoritative scoped/contextual authorization, deny-by-default, commit-time yeniden yetkilendirme,
  separation of duties, phishing-resistant privileged access, protected audit ve quarantine-first ingestion;
- `DEC-0027`: federated release authority, exact immutable artifact promotion, bağımsız verifier/trust-root,
  artifact-bound provenance/SBOM ve cross-domain compatibility/revocation graph;
- `DEC-0028`: Obsidian-compatible graph, contract-governed task boundary, minimum sufficient context, no-code
  simulation, bidirectional closure ve bağımsız evidence;
- `DEC-0029`: teknik olmayan tek owner, AI-operated delivery, no-owner-debug ve teknik tercihin outcome/risk/cost/
  reversibility diline çevrilmesi;
- `DEC-0030`: limited budget, staged cost, free/capped/exit yolu, zorunlu güvence karşılanmıyorsa capability'nin
  `HELD` kalması;
- `DEC-0034`: domain başına canonical authority, server/API-mediated sensitive access, online-authoritative Internal
  Operations, bounded offline package, ayrı current/history/audit/object planları ve cross-plane recovery/exit;
- `DEC-0035`: managed Supabase-centered fiziksel çalışma yönü, zorunlu Kavriva API mediation, RLS/Storage'ın yalnız
  defense-in-depth olması ve runtime'ın replaceable kalması;
- `DEC-0036`: seçili motorcycle/task için complete compact offline package, ayrı durable operation ledger ve tüm
  submission/status lookup'ın Kavriva API üzerinden yapılması;
- `DEC-0037`: consumer Auth için local-first/account-light yönü, provider-neutral Kavriva principal, API authorization,
  security epoch, end-to-end revoke, audit-before-effect ve privileged activation gate.

### 2.2 Bu belgeye taşınan mevcut yönler

| Konu | Bağlayıcı çalışma yönü | Bu belgedeki sonuç |
|---|---|---|
| Consumer mobile | Flutter yönü; Phase-5 ADR ve gerçek cihaz kanıtı açık | Flutter API'ye güvenilmez client olarak bağlanır; truth presentation code içine gömülmez. |
| Internal Operations | Browser-based ürün yüzeyi; desktop wrapper dışarıda | Browser yalnız API sözleşmesiyle okur/yazar; provider console ürün yetkisi değildir. |
| Backend | Supabase-centered, API arkasında, ilk fallback modüler yapı | API contract provider/runtime'dan bağımsız ve değiştirilebilir olmalıdır. |
| Offline | Selected motorcycle/task, compact complete recovery closure, optional media ayrı | Local write veya push canonical kabul/freshness/recall kanıtı değildir. |
| Identity | Consumer Auth çalışma yönü; privileged provider kazananı yok | Authentication ≠ authorization; current session/epoch her hassas işlemde kontrol edilir. |
| Planning | No-code, Gate 4 → 5 kapalı | Bu belge gereksinim ve fixture üretir; implementasyon veya provider seçimi yapmaz. |

## 3. Kavriva API neden zorunludur?

Kavriva'nın istemcileri farklı güven ve süreklilik koşullarındadır. Flutter cihazı fiziksel olarak kaybedilebilir,
restore edilebilir veya uzun süre offline kalabilir. Browser açık sekme, eski role/claim, stale cache veya ele geçirilmiş
token taşıyabilir. Push/Realtime yalnızca bilgi sinyali verebilir. Object URL'si kopyalanabilir; provider log'u ürün
audit'i değildir. Bir network timeout, operation'ın commit edilip edilmediğini tek başına söylemez. Bu yüzden client'ın
canonical database, object storage veya authority'ye doğrudan sahip olması kabul edilemez.

| Client/altyapı durumu | API olmadan oluşacak risk | Zorunlu API anlamı |
|---|---|---|
| Stale browser tab veya cached role | Eski yetki ile publish/approve/role mutation | Commit anında actor, session, policy, grant, scope ve epoch yeniden değerlendirme |
| Flutter offline veya process death | Yerel kayıt canonical başarı sanılır; duplicate/lost operation | Durable operation identity, idempotent submission, status lookup ve reconciliation |
| Request timeout | Kullanıcı blind retry ile iki kez publish/recall/delete yapar | `OUTCOME_UNKNOWN`, tek resolver ve aynı operation identity ile çözüm |
| Recall/publish yarışı | Eski publish yeni suspension'ı temizler | Release/suspension generation fence ve most-restrictive negative authority |
| Object upload veya signed URL | Quarantine atlanır; private object başka scope'a sızar | Classification, lineage, digest/version, scoped handle ve server-mediated activation |
| Auth token veya role revoke | Canlı token/stale browser mutation'a devam eder | Current account/session + security epoch + commit-time deny/hold |
| Audit sink kesintisi | Effect kanıtsız gerçekleşir | Protected fallback yoksa positive high-consequence effect `HELD` |
| Old backup/restore | Revoke, recall, delete veya kabul edilmiş operation dirilir | Non-restorable negative/accepted-operation floor ve restore quarantine |
| Provider/account/billing outage | Owner SQL/SSH/log teşhisine zorlanır | Owner-readable `HELD`/`UNAVAILABLE`/`RECOVERY_REQUIRED`, güvenli runbook |
| AI task veya entegrasyon | Geniş credential ve gizli bypass ortaya çıkar | Task-scoped capability, narrow contract, forbidden scope ve evidence closure |

Dolayısıyla API şu üç anlamı aynı anda taşır:

1. **Authority gate:** hassas okuma, export ve mutation için current canonical truth ve yetki kontrolü;
2. **Effect protocol:** operation identity, idempotency, audit, side-effect ve outcome state'inin bağlanması;
3. **Recovery/exit contract:** restore, reconciliation, object/package/ledger export ve provider değişiminde anlamın
   korunması.

API, veritabanı yönetim paneli, genel client data API'si veya "güvenilir ağ içi" varsayımı değildir. İstemcinin bir
isteği gönderebilmesi, isteğin kabul edildiği veya effect'in gerçekleştiği anlamına gelmez.

## 4. Temel authority ve boundary modeli

### 4.1 Canonical domain başına tek mantıksal owner

Her domain'in bir canonical transactional authority'si, stable object identity'si, immutable version/generation'ı,
classification'ı, history/provenance bağlantısı ve audit izi olur. Tek fiziksel database varsayılmaz; ancak iki ayrı
projection aynı anlamı bağımsızca yazamaz.

Authority hiyerarşisi:

1. authority/control truth: policy, session, role/grant, competence, security epoch, release/suspension generation,
   protected audit continuity;
2. canonical product truth: scope/applicability, claim/content, approved release;
3. user-owned operational truth: selected motorcycle, active work, history, notes, evidence, conflict/correction;
4. derived projection: cache, search, analytics, notification, package/read model.

Üst katman `UNKNOWN`, `HELD` veya stale ise alt katman positive authority üretemez. Derived copy canonical truth'i
veya authorization'ı yeniden yazamaz.

### 4.2 API'nin zorunlu olarak koruduğu sınırlar

- Flutter ve browser genel canonical database veya object-storage authority taşımaz.
- Hassas read/export/mutation Kavriva API üzerinden scope/context ile yapılır.
- Provider Data API/RPC/view/function/Storage, signed URL veya Studio ürün authority'sini bypass edemez.
- RLS/Storage policy defense-in-depth'tir; approval, publication, recall, provenance, audit veya separation-of-duties
  yerine geçmez.
- `service_role`, owner/billing root, unrestricted SQL/SSH ve global object credential istemciye, repository'ye,
  log'a veya sıradan AI context'ine giremez.
- Public UI görünürlüğü, disabled/hidden button, cache, service worker, Realtime veya push server authority değildir.

### 4.3 API request/response semantic envelope

Her sensitive request, fiziksel serialization'dan bağımsız olarak şu anlamları taşıyabilmelidir:

- stable operation identity ve action type;
- actor/workload identity, issuer/session assurance ve current security epoch;
- exact resource/object, tenant/owner, scope ve classification;
- expected object/version/generation ve dependency/release/suspension expectations;
- current policy/grant/competence/independence context;
- payload fingerprint, intended effect, reason ve validity context;
- response state: `ALLOW`, `DENY`, `HELD`, `OUTCOME_UNKNOWN`, `FAILED`, `PARTIAL`, `RECONCILING` veya
  operation-specific accepted state;
- server-ordered time/sequence, audit reference, effect summary, impact ve next-action/resolver owner.

Alan adı, wire formatı ve endpoint şekli açık kalır; anlamlardan biri taşınamıyorsa aday API kabul edilmez.

## 5. Flutter consumer sınırı

### 5.1 API üzerinden read envelope

Flutter content/data kullanmadan önce API'den alınan immutable veya açık generation-bound envelope'ı değerlendirmelidir.
Minimum anlamlar:

- motorcycle/model/year/variant/modification applicability;
- approved release/content identity, integrity/digest ve client capability;
- dependency closure, required safety/application/safe-stop/recovery closure;
- current eligibility/freshness, suspension/recall/revocation generation;
- classification/visibility, relevant provenance/evidence level;
- last authoritative reconciliation context ve historical-use/current-eligibility ayrımı.

Unknown safety-critical field, unmet capability, stale/mixed/recalled package veya unresolved fit/readiness normal
physical progression için positive authority vermez. Affected flow fail-closed olur; teaching, history, evidence ve
task-specific safe recovery, critical meaning'i doğru temsil edebildiği sürece ayrı durumlarda korunabilir.

### 5.2 Offline package boundary

Varsayılan paket yalnız selected motorcycle + selected task + exact approved release/client capability ile sınırlıdır.
Reachable physical state'lerin tümü için compact safety/application/safe-stop/recovery closure bulunur. İlişkisiz katalog,
guide veya media indirilmez. Optional high-resolution/video/media ayrı, görünür boyutlu, cancelable ve evictable olur;
required closure data tasarrufu adına evict edilemez.

Package application, API tarafından verilen eligibility/generation context ile değerlendirilir. Push/Realtime,
download completion, local cache, optimistic UI veya background callback recall/freshness proof değildir. Foreground,
network return, app launch ve gerekli resume boundary'lerinde authoritative reconciliation gerekir.

`DEC-0031` içindeki 12 MB compact transfer, 150 MB optional media, 25 MB cellular confirmation ve 250 MB refetchable
cache değerleri yalnız eşit karşılaştırma fixture'ıdır; bu belge final commercial limit ilan etmez.

### 5.3 Flutter'ın yapabileceği ve yapamayacağı işlemler

| İşlem | API sınırı |
|---|---|
| Package fetch/verify/resume/cancel | Manifest, generation, digest, compatibility ve closure doğrulanır; partial/mixed package usable sayılmaz. |
| Read-only content/history | Scope, classification ve current eligibility ile; stale/history/reference state görünür. |
| User history/note/evidence capture | Local-first olabilir; canonical official truth değildir; operation ledger'a yazılır. |
| High-consequence user operation submission | API operation identity + expected version/generation + status lookup ile; silent LWW yok. |
| Internal approve/publish/recall/role/audit mutation | Offline yasak; online current authorization ve protected audit gerekir. |
| Object upload/read | API-issued scoped handle; quarantine/classification/lineage tamamlanmadan active object authority yok. |
| Realtime/push | Recheck için hint; acceptance, freshness, recall veya delete kanıtı değil. |

Flutter local persistence (onaylı çalışma yönü SQLite/Drift) durable ledger ve package state'i taşıyabilir; API
authority'sini ikame etmez. Local DB transaction, queue empty veya HTTP 2xx tek başına canonical kabul değildir.

## 6. Browser Internal Operations sınırı

### 6.1 Ürün yüzeyi ve online authority

Kavriva Internal Operations browser ürünü, provider Studio veya database console değildir. Browser şu akışları yalnız
Kavriva API ile yürütür:

- research, source/evidence, claim/content draft ve dependency yönetimi;
- validation, conflict review, approval ve exact snapshot oluşturma;
- release candidate, guarded publication, rollback/re-entry, suspension/recall ve impact reach-back;
- role/policy/competence/delegation/recovery işlemleri;
- export/disclosure, delete/retention, audit/investigation ve operasyon reconciliation.

Approval, publication, recall/suspension, role/policy, privileged recovery ve audit mutation online-authoritative'dir.
Offline mutation baseline olarak yasaktır; offline draft davranışı ayrıca kararlaştırılmadıkça varsayılamaz.

### 6.2 Stale tab ve UI sınırı

Browser açıldığında alınmış role/claim, cached permission, service worker, disabled button veya optimistic local state
yetki değildir. Role/policy/competence, session veya security epoch değişirse stale tab read-only, `DENY` veya `HELD`
olur. Current resource/version/release/suspension expectation commit anında tekrar sınanır.

Generic provider Data API, RPC, Storage veya direct database route ile ürün mutation'ı yapılabilmesi hard fail'dir.
Export ayrı disclosure operation'ı, recipient/scope/purpose preview'ı ve immutable audit event'i gerektirir; indirilmiş
kopya remote revoke ile geri alınamaz, kullanıcıya bu residual risk doğru anlatılır.

### 6.3 Browser response state

Browser timeout veya bağlantı kopması success/failure tahminine çevrilemez. UI, operation identity ile status lookup
yapılana kadar `OUTCOME_UNKNOWN` göstermelidir. `AUTHORITATIVE_CURRENT`, `DELIVERY_OBSERVED` ve
`CONSUMER_RECONCILED` ayrı durumdur; birinin gözlenmesi diğerini kanıtlamaz.

## 7. High-consequence commit-time authorization

### 7.1 Preflight yetmez

UI'da preflight veya sayfa açılışındaki izin kontrolü yalnız bilgi sağlar. Effect'ten hemen önce API şu tuple'ı current
olarak yeniden değerlendirir:

- actor/workload, issuer ve session assurance;
- account/session state ve security epoch;
- requested action, exact object/resource, tenant/scope ve classification;
- current role/grant/delegation, competence ve independence;
- policy/access version, object/version/generation ve expected-current check;
- release/content/schema/config/migration/offline-package compatibility;
- current suspension/recall/revocation generation ve dependent negative floor;
- operation identity, payload fingerprint, reason ve intended effect;
- protected audit readiness/fallback ve failure-domain koşulları.

Tuple'dan herhangi biri stale, unknown, expired, conflicting, unavailable veya policy ile uyuşmazsa effect
`DENY`/`HELD` olur; UI'daki eski olumlu görüntü bunu override edemez.

### 7.2 Separation of duties ve negative authority

Proposal/edit, domain review, safety/technical approval ve publication birbirinden ayrıdır. High-consequence official
work self-approve/self-publish, hidden admin bypass, expired delegation, role accumulation veya unavailable competence
ile tamamlanamaz. Gerekli bağımsız kişi/competence yoksa görünür `HELD` kalır.

Emergency negative authority yalnız suspend/recall/quarantine/deny üretir; positive technical truth, publish,
unsuspend veya role grant üretemez. Normal publication/recovery yolundan failure-domain düzeyinde gerekli bağımsızlık
kanıtlanmamışsa high-consequence production açılmaz.

### 7.3 Provider claims ve RLS sınırı

Provider tokenı, cached claim, `user_metadata`, browser state veya provider role yalnız kimlik/oturum sinyali olabilir.
Kavriva API current authorization tuple'ını kendi canonical policy/generation anlamıyla değerlendirir. RLS/Storage
policy her zaman defense-in-depth olarak korunur; tek başına commit-time approval, audit veya release fence sayılmaz.

## 8. Idempotency, status lookup ve `OUTCOME_UNKNOWN`

### 8.1 Durable operation identity

Her sensitive operation için identity, action type, actor/authority, exact resource/scope/classification, payload
fingerprint, expected versions/generations, intended effect ve validity context bağlanır. Aynı identity farklı payload,
scope veya effect ile tekrar kullanılırsa reject edilir.

İşlem sonucu en az şu durumları taşıyabilmelidir:

`PENDING` → `SUBMITTED` → `ACCEPTED`  
veya `CONFLICT`, `HELD`, `FAILED`, `OUTCOME_UNKNOWN`, `RECONCILING`, `PARTIAL`.

`ACCEPTED` canonical effect'in anlamıdır; local save, queue empty, HTTP success, Realtime/push veya background completion
değildir. `PARTIAL` affected scope, gerçekleşen/gerçekleşmeyen effect ve next action belirtir.

### 8.2 Retry ve status lookup

- Normal network retry aynı operation identity ile yapılır; blind duplicate mutation yasaktır.
- İlk request sonucu kaybolursa client `OUTCOME_UNKNOWN` kaydeder ve status lookup/resolver yoluna geçer.
- Status lookup read-only görünse bile current operation, canonical effect, audit reference, current generation,
  conflict/hold reason, resolver ve next action'ı döndürür.
- İdempotent result, aynı operation için aynı intended effect/result semantiğini korur; farklı payload silent overwrite
  yapamaz.
- Operation status, release delivery status ve consumer reconciliation status birbirine indirgenmez.
- Lost-response/retry, process death, restore, device migration, account-light migration ve cross-region duplicate
  koşulları aynı semantic contract ile ele alınır.

Numeric retention, lookup TTL, retry backoff, cross-region uniqueness ve escalation SLA sonraki equal fixture/ADR
konusudur; belirsiz bir süre “başarı” veya “başarısızlık” üretme izni vermez.

## 9. Audit-before-effect ve protected evidence

### 9.1 Minimum audit event anlamı

High-consequence effect'ten önce veya eşdeğer transactional assurance ile protected event hazır olmalıdır. Event en az:

- actor/workload identity, effective role/scope, issuer/session assurance ve security epoch;
- server-ordered timestamp/sequence, action, exact object/resource/scope/classification;
- old/new state veya version/generation anlamı;
- policy/grant/delegation/competence version ve expected/current generations;
- operation identity, payload/decision/evidence links, reason ve intended effect;
- result (`accepted`, `denied`, `failed`, `partial`, `held`, `outcome unknown`);
- dependent impact, recovery/reconciliation owner ve next action

taşır.

Auth/provider log'u Kavriva product audit'i değildir. Audit event'i ordinary publisher/admin tarafından silinemez veya
rewrite edilemez; gap/fork/replay, retention/legal-hold, read/export/redaction ve restore/fallback reconciliation
kanıtı gerekir.

### 9.2 Audit custody yoksa effect yok

Normal protected custody ve yeterince bağımsız fallback ikisi de unavailable ise positive high-consequence action
`HELD` olur. “Database transaction başarılı” veya “provider log yazdı” audit-before-effect kanıtı değildir. Emergency
negative path yalnız tanımlı minimum evidence ve quarantine/reconciliation ile çalışabilir; emergency işlemin timeout'u
da `OUTCOME_UNKNOWN` olarak çözülür.

## 10. Object/media mediation

Object bytes, canonical record ve protected audit aynı anlama sahip değildir; ayrı logical object boundary gerekir.
API object lifecycle'ı şu sırayı ve anlamları korur:

`RECEIVED` → `QUARANTINED` → `VALIDATED/SCANNED/RENDERED-AS-UNTRUSTED` → `CLASSIFIED` → `ACTIVATED`

### 10.1 Zorunlu object kontrolleri

- Upload veya URL fetch önce quarantine'a girer; private address, redirect, ambient cookie/credential, traversal,
  decompression bomb, oversize veya unsupported type policy ile deny/quarantine olur.
- Original, derivative, transform, scan/render/OCR/AI output arasında exact lineage ve digest/version tutulur.
- Classification (private/shared/community/official/quarantine/protected audit), owner/scope, retention ve disclosure
  anlamı derivative'lara en restrictive kuralla taşınır.
- Scan/render/OCR/AI, technical correctness, evidence sufficiency, approval veya publication authority vermez.
- API, exact audience/scope/object/version/generation/epoch bağlı kısa ömürlü handle veya server-mediated stream verir;
  global bucket/public mutable URL/high-privilege object token vermez.
- Object revoke/recall sonrası yeni handle verilmez; daha önce indirilen/kopyalanan bytes'ın geri alınamayacağı açıkça
  raporlanır. Remote wipe yalnız best-effort'tür.
- Optional media package/core safety closure'dan ayrıdır; required safety/recovery media evict edilemez.

Browser preview, privileged operations origin'inden ve operations credential/cookie'lerinden izole edilmelidir.
Provider Storage policy, API object mediation ve classification/audit'in yerine geçmez.

## 11. Offline operation ledger sözleşmesi

### 11.1 İki ayrı Flutter veri hattı

1. **Offline content package lane:** immutable complete package, manifest, generation, digest, compatibility ve safety/
   application/safe-stop/recovery closure.
2. **Durable user-operation lane:** history, notes, evidence metadata, pending uploads, account-light migration ve user
   work için app-owned ledger.

Ledger, canonical user history'nin local copy'si değildir; local capture ile server acceptance arasındaki operations
truth'idir. Her kayıt en az:

- stable operation ID, action ve actor/principal;
- payload fingerprint, exact scope/classification ve intended effect;
- expected object/version/generation ve used release/package;
- created/last-attempt server/order context, local durability status;
- `PENDING`, `SUBMITTED`, `ACCEPTED`, `CONFLICT`, `HELD`, `FAILED`, `OUTCOME_UNKNOWN`, `RECONCILING`, `PARTIAL`;
- response/audit/effect references, resolver owner, conflict reason ve next action

taşır.

### 11.2 Ledger invariants

- Process death, reboot, background restriction, storage pressure, restore/device migration ve app upgrade ledger
  kimliğini ve last-valid package truth'ini kaybettiremez.
- Local transaction veya upload queue empty canonical acceptance değildir.
- Conflict, delete, recall, revoke, tombstone, old restore ve accepted operation anti-resurrection semantics'i açıkça
  saklanır; silent last-write-wins yasaktır.
- Profile migration source possession, fresh target reauth, scope/classification preview, immutable mapping, conflict
  hold, target reconciliation ve split/rollback ile ayrı operation'dır; identity linking sessiz merge değildir.
- Restored/migrated data current negative floor ve security epoch doğrulanmadan positive authority kazanamaz.
- Ledger export/restore/clean-room import pending operations, statuses, conflicts, tombstones ve package generations'ı
  korur.

API, ledger submission ve status lookup için tek canonical protocol'dür. Realtime/push, durable offline sync veya
negative-authority proof değildir. High-consequence Internal Operations mutation'ı ledger'dan offline tamamlanamaz.

## 12. Release, publication ve recall sınırı

### 12.1 Closed release meaning

API release operation'ı yalnız exact immutable approved snapshot ve closed manifest ile ilerletir. Manifest en az:

- content/claim/localization/media/transform/default/config/feature input'ları;
- source/evidence/provenance/classification ve dependency closure;
- consumer binary/web/API/schema/client capability uyumu;
- migration/data state ve forward-recovery planı;
- selected motorcycle/task offline package, safe-stop/recovery closure;
- release generation + suspension/revocation generation;
- approval, independent verifier, promotion, signature, operation ve protected audit kimlikleri

bağlar. Mutable external URL veya runtime substitution approved meaning'i değiştiremez.

Kavramsal state'ler:

`PREPARED → AUTHORIZED → PUBLISHING → AUTHORITATIVE_CURRENT → DELIVERY_OBSERVED → CONSUMER_RECONCILED`

ve ayrı `HELD`, `FAILED`, `OUTCOME_UNKNOWN`, `PARTIAL_PROPAGATION`, `SUPERSEDED`, `SUSPENDED`, `RECALL_OPEN`.

### 12.2 Commit fencing ve recall

- Publication commit anında current release/suspension/revocation generation ile fence edilir.
- Daha yeni suspension/recall eski veya in-flight publish tarafından temizlenemez.
- Overlapping scopes için most-restrictive negative authority geçerlidir.
- Normal application eligibility, known recall/suspension ile kapanır; history, used-version, provenance ve task-specific
  safe-stop/recovery closure sessizce silinmez.
- Rollback eski binary/hash'e dönmek değil, hâlâ approved, compatible ve not-recalled predecessor'a yeni guarded
  publication event'idir. Uygun predecessor yoksa guessed rollback değil suspension + correction/re-review yapılır.
- Restore/failover sonrası current release, negative floor, policy/security epoch, audit continuity ve object/package
  generations reconcile edilmeden positive publication veya eligibility açılmaz.

Emergency negative authority replacement technical truth üretmez; suspension/recall impact graph'ı ve later re-entry
operation'ı API üzerinden açıkça tutulur.

## 13. Identity, session ve security epoch

### 13.1 Kimlik sınıfları ayrıdır

Provider `(issuer, subject)`, local installation/device principal, Kavriva product principal/profile, browser/mobile
session, role/grant/delegation, competence/independence, workload/service/AI identity, provider/legal/billing owner ve
historical audit actor birbirine sessizce eşitlenemez. E-posta, display name veya provider user ID stable product
ownership/authority mapping'i değildir.

Consumer account-light local installation principal ile başlayabilir. Local-to-profile migration provider linking'den
ayrı, görünür kapsam önizlemeli ve conflict/rollback destekli ürün operation'ıdır.

### 13.2 Epoch'in kapsadığı uçlar

Kavriva security epoch değiştiğinde en az şunlar current olarak revalidate/deny edilir:

- provider session, refresh/recovery artifacts ve current account state;
- role/grant/policy/competence/delegation generations;
- pending/in-flight operation, lost-response status lookup ve retry;
- object handle/signed stream ve object generation;
- browser cache/service worker ve classified local package/key state;
- consumer eligibility, offline package generation ve account-light migration.

Downloaded copy'nin remote retract edilemeyeceği dürüstçe belirtilir. Remote wipe best-effort; authority ve history
silme mekanizması değildir.

### 13.3 Privileged activation boundary

Privileged Internal Operations için phishing-resistant, user-verified, transaction-bound fresh step-up; factor-loss,
stolen-token, logout-all, browser origin/PKCE/CSRF, accessibility, outage, key rotation ve recovery kanıtı gerekir.
`GA/stable`, passkey etiketi veya başarılı login tek başına yeterli değildir. TOTP/SMS/magic link phishing-resistant
gereksinimin yerine geçmez.

Privileged account recovery ile emergency negative authority ayrı state machine'dir. Recovery approve/publish/role grant
vermez; negative path positive truth üretmez. İki issuer ileride kullanılırsa allowlisted issuer/audience/key, immutable
issuer-qualified mapping, tek Kavriva epoch ve cross-issuer revoke/logout kanıtı gerekir.

## 14. No-owner-debug ve AI task operability

### 14.1 Owner-readable işletim

Outage, billing restriction, provider failure, audit sink gap, object scan failure, stale session, restore conflict,
unknown result ve migration partial state; owner'ın SQL/SSH/log teşhisi veya queue surgery yapmasını gerektirmeden
anlaşılır duruma çevrilir:

- görünür state: `HELD`, `UNAVAILABLE`, `ACCESS_DENIED`, `OUTCOME_UNKNOWN`, `RECONCILING`, `RECOVERY_REQUIRED`;
- insan dilinde neden, etkilenen kapsam, veri kaybı/authority riski ve güvenli sonraki adım;
- sorumlu resolver/support/AI task sınıfı ve gerekli external action;
- resume/rollback/forward-recovery veya capability hold kararı;
- audit/incident/reference bağlantısı.

"Retry et", "loglara bak", "SQL çalıştır" veya "provider console'dan düzelt" owner-runbook sayılmaz. Teknik onarım
gerekiyorsa explicit external dependency ve capability `HELD` olarak görünür.

### 14.2 AI'nin API üzerindeki çalışma sınırı

Her API işi contract-governed ve küçük task olarak tanımlanır:

- task ID, requirement/boundary/contract links ve minimum sufficient context pack;
- allowed/forbidden scope, credential class, input/output state machine;
- fixture, negative cases, conflict/timeout/restore/recovery stop conditions;
- implementer, independent reviewer, validator, evidence custody ve completion proof;
- rollback/forward recovery, cost/overage stop ve owner-readable handoff.

AI identity kısa ömürlü ve task-scoped olur. AI; provider owner, billing root, `service_role`, unrestricted SQL/SSH,
global object credential, raw SMTP/SMS secret, privileged recovery, approval, publication veya role-grant authority
alamaz. AI/OCR/extraction yalnız attributable proposal üretebilir; hostile document instruction policy/tool/network
authority vermez.

Requirement → API contract → task → test/evidence ve ters yönde orphan/gap audit'i olmadan "all tasks DONE" kapanış
kanıtı değildir. API boundary'nin anlamı task'lar arasında ortak canonical contract olarak okunabilir olmalıdır.

## 15. Gözlemlenebilirlik ve operasyonel sözleşme

API'nin teknik metrikleri product truth ile karıştırılmamalıdır. Her operation/release/object/package/ledger state için:

- current state, last transition, reason ve current generation;
- operation identity, correlation/trace reference ve audit reference;
- actor/session/epoch/policy context (gerekli privacy/redaction ile);
- affected scope/dependent impact, resolver ve next action;
- `unknown`, `partial`, `held`, `unavailable`, `reconciling` sayıları ve denominator'ı;
- safe read / positive action hold / negative action availability ayrımı

owner-readable olarak görünür olmalıdır.

Dashboard/KPI operasyonu veya audit'i değiştiremez; opaque quality score unknown/conflict/stale kayıtları gizleyemez.
Search, cache, notification ve analytics rebuildable projection'dır.

## 16. Maliyet, sınırlandırma ve çıkış gereksinimleri

### 16.1 Güvenli minimum cost model

API adayları karşılaştırılırken yalnız runtime headline fiyatı alınmaz. Aynı normalized bill of materials şu kalemleri
göstermelidir:

- API compute/runtime, request/egress/storage ve hard-cap/overage davranışı;
- identity adapter/Auth planı, MAU/MRU veya eşdeğer ölçüler;
- domain/DNS/SMTP ve gerekiyorsa notification/SMS maliyeti;
- protected product audit, independent fallback custody, log drain ve monitoring;
- object/media backup, restore, quarantine/scan ve clean-room exit;
- release/package build/verification, incident month, support/recovery ve provider migration;
- tax/FX, normal/scale/incident/restore/exit ayları ve credential/secret operasyonu.

Her satır `mandatory / deferrable / optional / scale-triggered`, güncel resmi tarih, quota, hard cap, stop action,
free/local/capped alternatifi ve çıkış yolu taşır. TRY 2.000–3.000/ay yalnız ilerideki planlama tavanıdır; satın alma izni
değildir. Zorunlu güvence bütçeye sığmıyorsa güvenlik/privacy/data-continuity düşürülmez; etkilenen capability `HELD`
kalır.

### 16.2 Provider/account failure ve spend control

Account, region, billing, quota, provider API veya API runtime failure'ı first-class state'tir. Overage veya limit
belirsizliği canonical data loss, silent degradation veya owner debug ile telafi edilemez. Safe read, positive mutation
hold, independent negative path ve recovery/exit action ayrı raporlanır.

### 16.3 Exit ve cross-plane recovery

API provider değişiminde yalnız database dump yeterli değildir. Export/import sözleşmesi en az şunları birlikte taşır:

- canonical product/current state ve domain history/provenance;
- user history/work, operation ledger, statuses, conflicts, tombstones ve accepted-operation identity;
- release/artifact/package manifests, compatibility/revocation/suspension generations;
- protected audit, policy/grant/competence/security epoch ve immutable actor/principal mapping;
- object bytes, original/derivative lineage, classification, digest/version, retention/disclosure records;
- incident/impact graph, recovery floor ve deletion/negative authority floor.

Restore veya clean-room import önce quarantine'da çalışır. Cross-plane consistency manifest, current negative floor,
audit continuity, object/package integrity, classification ve no-resurrection negative testleri geçmeden positive
eligibility/publication açılmaz. Clean-room import yeni ortamda pending operations, revoke/recall/delete ve already
accepted operation'ın yeniden dirilmediğini kanıtlar.

Exit yolu provider-specific client SDK, global object handle veya opaque proprietary state'e bağımlıysa candidate
`HELD`; cross-plane truth kayboluyorsa `HARD FAIL`/`REJECT-IF-UNMITIGATED` olur.

## 17. Kabul kriterleri

Aşağıdaki kriterler sonraki aday karşılaştırmasında MUST'tur. Belgesel kanıt yoksa `PASS` değil `HELD/UNVERIFIED` yazılır.

| ID | Kabul kriteri | Beklenen kanıt |
|---|---|---|
| API-AC-001 | Hassas read/export/mutation tek Kavriva API authority contract'ından geçer; client/provider console doğrudan canonical veya object authority taşımaz. | Boundary map, direct-path negative matrix, client bundle/credential sınırı. |
| API-AC-002 | Her domain canonical owner, stable object identity, version/generation, classification, provenance/history ve audit link'i korur. | Domain/boundary inventory ve state matrix. |
| API-AC-003 | Flutter package selected motorcycle/task kapsamlı, complete compact safety/application/safe-stop/recovery closure'lı ve generation/digest/compatibility bağlıdır. | Package manifest walkthrough, partial/mixed/corrupt/recall fixture'ı. |
| API-AC-004 | Flutter local write, HTTP success, queue empty, Realtime/push veya local DB transaction canonical kabul/freshness/recall kanıtı değildir. | Offline state-machine ve explicit reconciliation evidence. |
| API-AC-005 | Browser Internal Operations approve/publish/recall/role/policy/recovery/audit mutation'ları online-authoritative'dir; provider Studio ürün authority'si değildir. | Browser mutation contract ve offline negative cases. |
| API-AC-006 | High-consequence effect commit anında current actor/session/epoch/action/resource/scope/classification/grant/competence/independence/policy/version/generation/dependency koşullarıyla reauthorize edilir. | Stale tab, revoked role, expired delegation, cross-tenant ve in-flight negative tests. |
| API-AC-007 | Self-approval, hidden admin bypass, unavailable competence ve stale cached claim high-consequence effect üretemez. | Separation-of-duties matrix ve deny/hold evidence. |
| API-AC-008 | Her sensitive operation stable identity + payload fingerprint + expected version/generation ile idempotenttir; farklı payload aynı identity ile kabul edilmez. | Duplicate/lost-response/retry fixture'ı. |
| API-AC-009 | Status lookup canonical effect, audit ref, generation, conflict/hold reason, resolver ve next action verir; timeout `OUTCOME_UNKNOWN` olarak kalabilir. | HTTP timeout-after-commit, timeout-before-commit ve resolver walkthrough. |
| API-AC-010 | `PARTIAL`, `HELD`, `FAILED`, `RECONCILING`, `OUTCOME_UNKNOWN` accepted/current/delivery/reconciled state'lerinden ayrı tutulur. | State transition table ve UI/API response examples. |
| API-AC-011 | Protected audit event effect'ten önce veya eşdeğer transactional assurance ile vardır; custody/fallback yoksa positive effect `HELD` olur. | Minimum event schema, audit outage/fallback/reconcile fixture'ı. |
| API-AC-012 | Object upload/fetch quarantine-first; classification, lineage, digest/version ve scoped handle mediation uygulanır; scan/render/OCR/AI authority vermez. | Malicious archive/URL/private-address, derivative lineage ve leaked-handle negative tests. |
| API-AC-013 | Offline operation ledger stable operation, fingerprint, expected version/generation, statuses, conflict/hold, tombstone ve resolver bilgisini process death/restore/migration sonrasında korur. | Ledger state machine, device restore/migration/export fixture'ı. |
| API-AC-014 | Local-to-profile migration no-silent-loss/no-silent-overwrite, preview, verified possession/reauth, immutable mapping, conflict hold ve split/rollback taşır. | Account-light migration walkthrough. |
| API-AC-015 | Release closed manifest exact approved meaning, dependencies, client/API/schema/config/migration/package compatibility ve current suspension generation'ını bağlar. | Release graph, mixed-generation and missing-dependency fixture'ı. |
| API-AC-016 | Newer suspension/recall older/in-flight publication'ı temizleyemez; rollback yalnız valid compatible predecessor'a yeni guarded event'tir. | Publish-vs-recall race, invalid rollback ve emergency negative fixture'ı. |
| API-AC-017 | Security epoch session/grant/policy/competence/pending operation/object handle/browser cache/local package/key state ve retry/status lookup üzerinde end-to-end revoke sağlar. | Lost factor, stolen token, logout-all, stale handle/package and in-flight deny fixtures. |
| API-AC-018 | Privileged recovery ile emergency negative authority ayrı state machine'dir; recovery positive approval/publish/role grant vermez. | Last-admin, outage, recovery/emergency tabletop ve negative authority matrix. |
| API-AC-019 | Owner-readable `HELD`/`UNAVAILABLE`/`OUTCOME_UNKNOWN`/`RECOVERY_REQUIRED` state'leri vardır; owner SQL/SSH/log diagnosis/queue surgery yapmadan güvenli next action alır. | Failure runbook, escalation and no-owner-debug walkthrough. |
| API-AC-020 | AI task'ları narrow contract, minimum context, allowed/forbidden scope, scoped credential, independent review/validation ve completion evidence ile ayrıştırılabilir. | One end-to-end API task pack, collision/gap/no-code simulation. |
| API-AC-021 | API/runtime cost normalized BOM, hard cap/stop, free/capped path, incident/restore/exit cost ve owner approval state'i gösterir. | Equal cost worksheet; no hidden paid dependency. |
| API-AC-022 | Provider/runtime değişiminde clean-room export/import current/history/audit/object/package/ledger/identity/negative floor anlamını korur. | Cross-plane manifest, quarantine import and anti-resurrection evidence. |
| API-AC-023 | Restore/failover/migration old backup ile revoke/recall/delete/suspension/accepted operation'ı diriltemez; yeni valid data'yı silent rollback ile kaybetmez. | Restore, partial migration and negative-floor fixture'ı. |
| API-AC-024 | API contract, provider-specific adapter ve presentation code'dan ayrıdır; yeni runtime adayına taşınabilir; mevcut provider secret'ları client/AI context'ine sızmaz. | Contract portability map, secret boundary and replacement exercise. |

## 18. Hard fail / reject-if-unmitigated koşulları

Aşağıdaki davranışlar bir adayın yalnızca “eksik kanıt” değil, gereksinime aykırı olduğunu gösterir. Düzeltme ve negatif
kanıt gelene kadar candidate `REJECT-IF-UNMITIGATED`; güvenli davranış mümkün ama kanıt eksikse `HELD/UNVERIFIED` yazılır.

- Flutter veya browser'ın direct canonical database/object path'ı, provider console'u veya client-supplied object
  authority'si bulunması;
- RLS/Storage, cached role, UI visibility, provider token/log veya signed URL'nin Kavriva API authorization/audit/
  publication/recall authority'si yerine kullanılması;
- high-consequence effect'in commit-time reauthorization olmadan, stale role/session/epoch/dependency ile tamamlanması;
- self-approval, role accumulation, expired delegation, hidden admin bypass veya unavailable independence'in success'e
  çevrilmesi;
- network timeout'un otomatik success/failure sayılması, aynı effect'in blind duplicate ile yeniden uygulanması veya
  farklı payload'ın aynı operation identity ile sessizce kabul edilmesi;
- audit event'i effect'ten sonra yazılması veya protected normal/fallback custody yokken positive effect'in commit edilmesi;
- object quarantine/classification/lineage atlanması; public/global handle, ambient credential veya untrusted preview'ın
  privileged origin'e erişmesi;
- local ledger, HTTP 2xx, queue empty, push/Realtime veya downloaded package'ın canonical acceptance/freshness/recall
  kanıtı sayılması;
- conflict, partial, unknown, tombstone veya reconcile state'lerinin silent last-write-wins, delete veya optimistic
  success ile ezilmesi;
- older/in-flight publish'in newer recall/suspension'ı temizlemesi; old restore'un revoked/deleted/accepted truth'ü
  diriltmesi; invalid predecessor rollback'ının yeni truth gibi sunulması;
- security epoch revoke'un session, pending/in-flight operation, object handle, browser cache, local package veya retry
  yoluna ulaşmaması;
- privileged recovery'nin approve/publish/role grant üretmesi veya emergency negative path'in positive technical truth
  üretmesi;
- provider/runtime outage, billing cap, audit/object/restore problemi için owner'ın SQL/SSH/debug/queue surgery yapmasının
  zorunlu olması;
- AI'ye provider owner, billing root, `service_role`, unrestricted SQL/SSH, global object credential, approval/publish/
  recovery authority veya raw secret verilmesi;
- zorunlu safety/privacy/audit/recovery/exit güvencesinin ücret, quota veya provider kolaylığı uğruna düşürülmesi;
- cross-plane clean-room export/import'ın object bytes, protected audit, operation ledger, package generations veya
  negative/deletion/accepted-operation floor'ını koruyamaması;
- bu gereksinim çalışmasının kod/prototype/executable spike ile kapatılmaya çalışılması.

## 19. Sonraki eşit aday fixture'ı — `API-RUNTIME-FIXTURE-001`

### 19.1 Fixture amacı

Sonraki debate, bir runtime/provider veya dil/frameworki marka ve ekosistem etkisiyle değil, aynı Kavriva API boundary
contract'ını ne kadar güvenli, işletilebilir, taşınabilir ve uygun maliyetle taşıdığıyla karşılaştırmalıdır. Her aday aynı
ürün kapsamı, aynı failure injection, aynı evidence şablonu ve aynı owner/AI kısıtıyla değerlendirilir.

Bu fixture teknoloji seçmez. Aday aileleri yalnız karşılaştırma biçimidir:

- **Aday A — Provider-integrated bounded API runtime:** fiziksel backend ile yakın bütünleşen, düşük operasyon yükü
  iddiasındaki runtime bileşimi;
- **Aday B — Independent modular API runtime:** data/object/audit plane'lerinden açıkça ayrılabilen ve provider değişimini
  kolaylaştırdığı iddia edilen bağımsız runtime bileşimi;
- **Aday C — Self-managed/open-source bounded runtime:** düşük provider lock-in iddiası karşılığında owner/AI işletim,
  patch, monitoring, backup ve incident yükü taşıyan bileşim.

Bu etiketler sağlayıcı, dil, framework veya hosting adı değildir. Bir aday aile olarak kalabilir veya sonraki eşit
çalışmada aynı aile içindeki somut seçeneklerle doldurulabilir. Her aday aynı API semantic contract'ını uygulamak zorunda;
özellik listesi veya provider dokümanı tek başına PASS değildir.

### 19.2 Ortak ürün ve işletim varsayımları

- Consumer client: Flutter çalışma yönü; Android-first, iOS later parity; local-first/account-light principal.
- Internal client: browser-based Kavriva Internal Operations; desktop wrapper yok.
- High-consequence actions: review/approve/publish/rollback/recall/suspend/role/policy/recovery/export/delete ve
  authoritative content/object state değişimleri.
- Offline baseline: selected motorcycle/task complete compact package; optional media ayrı; 12/150/25/250 MB değerleri
  yalnız equal fixture constants.
- User work: separate durable operation ledger; stable identity/fingerprint/expected version; no silent LWW.
- Identity: provider-neutral Kavriva principal, current session/security epoch, actor/workload ayrımı.
- Recovery: restore quarantine, protected audit, object/package/ledger export, negative floor ve clean-room import.
- Owner: teknik olmayan tek product/decision owner; SQL/SSH/debug/repair yapamaz.
- AI: task-scoped, context-pack kullanan implementer/reviewer/validator; broad credential yok.
- Planning: no-code; fixture sonucunu gerçek production evidence gibi sunma yok.

### 19.3 Eşit failure ve lifecycle senaryoları

Her aday aşağıdaki senaryoların tamamında `expected state`, `side effect`, `audit evidence`, `recovery owner`,
`owner-visible next action`, `cost/exit impact` çıktısını vermelidir:

| Grup | Fixture senaryoları |
|---|---|
| Boundary/direct path | Flutter direct DB/Storage denemesi; browser direct Data API/RPC; provider Studio'dan publish; client-supplied tenant/object ID; leaked secret/signed handle. |
| Commit authorization | Stale tab; revoked role; expired delegation; changed policy/competence; cross-tenant object; dependency generation mismatch; in-flight commit sırasında newer suspension. |
| Operation protocol | Lost response before commit; lost response after commit; duplicate same payload; same ID/different payload; concurrent publish; partial result; status lookup while provider unavailable. |
| Audit/evidence | Protected audit primary unavailable; fallback unavailable; audit gap/fork/replay; restore audit continuity; export/redaction/legal hold. |
| Object mediation | Malicious archive; SSRF/private URL/redirect; mixed classification derivative; quarantine preview; recall/revoke handle; downloaded copy residual risk. |
| Offline ledger/package | Interrupted package; wrong base/digest; process death; storage pressure; device restore; offline user conflict; tombstone/delete; recalled package foreground return; account-light migration conflict. |
| Release/recall | Exact manifest mismatch; old client; schema/config/migration generation split; publish vs emergency suspension race; invalid rollback; delivery observed but consumer not reconciled. |
| Identity/epoch | Stolen token; logout-all; factor loss/recovery; provider outage; two-issuer mapping collision; in-flight operation after epoch bump; private object/local package retry after revoke. |
| Operations/AI | Billing cap; quota/region outage; audit/object backup gap; owner-readable recovery; AI task context collision; forbidden credential request; missing task/gap closure. |
| Cost/exit | Normal month; minimum-safe production; incident month; restore drill; clean-room exit; provider migration; overage/hard-stop; optional service disabled. |

### 19.4 Ortak aday dosyası şablonu

Her aday, aynı başlıklarla ve aynı kanıt etiketleriyle aşağıdakini teslim eder:

1. API logical boundary map ve client/direct-path deny map'i;
2. request/response semantic envelope, operation state machine ve idempotency/status lookup sözleşmesi;
3. commit-time authorization tuple, policy/version/generation fence ve separation-of-duties tablosu;
4. audit-before-effect event/custody/fallback/reconcile planı;
5. object lifecycle, quarantine, classification, lineage, handle ve downloaded-copy dürüstlük politikası;
6. offline package + operation ledger + restore/device migration/anti-resurrection planı;
7. release/publication/recall/suspension/rollback ve cross-plane impact graph'i;
8. identity adapter, principal mapping, session/security epoch, recovery ve emergency-negative ayrımı;
9. no-owner-debug runbook, observability, support/escalation ve AI task/context/credential matrix'i;
10. normalized cost BOM: free/capped, mandatory/deferrable/optional/scale-triggered, hard cap/overage/stop;
11. logical export, clean-room import, quarantine, reconciliation ve provider/runtime replacement evidence planı;
12. `API-AC-001..024` mapping'i, hard-fail disposition'ı ve eksik kanıtların `HELD` gerekçesi.

### 19.5 Eşit sonuç formatı

Her fixture satırı için yalnız şu sonuç değerleri kullanılabilir:

- `PASS`: beklenen semantic davranış ve bağımsız kanıt mevcut;
- `HELD/UNVERIFIED`: gereksinimle çelişmiyor, fakat bu no-code aşamada kanıt eksik;
- `REJECT-IF-UNMITIGATED`: hard-fail veya karşılanamayacağı gösterilmiş bağlayıcı ihlal.

`HELD`, güvenli veya production-ready demek değildir. Critical API-AC, security, data continuity, audit, recall,
no-owner-debug veya exit satırlarından biri kanıtsızsa aday `PASS` veya ADR-ready sayılamaz. Safety/privacy/data
continuity MUST'ları maliyet veya geliştirici rahatlığı ile telafi edilemez.

## 20. Açık kalan kararlar ve ADR handoff barı

Bu sentezden sonra aşağıdakiler hâlâ açık ve API gereksinimi olarak korunmalıdır:

- exact runtime/deploy/language/framework ve provider adapter implementation;
- role/capability/competence/quorum, emergency failure-domain ve independent human/organization modeli;
- token/session/refresh/step-up, epoch propagation ve object-handle TTL;
- operation idempotency retention, status lookup SLA, retry/backoff ve cross-region uniqueness;
- audit custody/fallback/fork-replay detection, retention/legal hold ve investigation access;
- object quarantine/scan/render/AI pipeline, private/shared/community/official policy ve object backup;
- offline freshness/risk taxonomy, client capability window, package/cache/media limits ve encryption/key custody;
- release graph's exact tiers, migration/partial-forward-recovery ve consumer reach-back channels;
- normalized current prices, tax/FX, scale/incident/restore/exit months, support ve cost stop;
- real Android/iOS/browser/device/restore/load/accessibility/security/exit evidence and Phase-5 ADR.

API runtime adayları ancak şu handoff barı kapanınca Phase-5 ADR adayı olabilir:

- `API-AC-001..024` için equal candidate mapping ve critical scenario evidence;
- S1–S36 ile bu fixture arasındaki traceability/orphan-gap audit;
- direct-path, stale-session, timeout, recall-race, audit-outage, object-leak, restore ve anti-resurrection negative
  sonuçları;
- owner-readable no-owner-debug runbook ve task-scoped AI execution pack;
- normalized safe-cost BOM, free/capped/stop route ve clean-room exit planı;
- en az iki bağımsız adversarial review + manager/Judge synthesis;
- hiçbir provider/runtime/dil/framework kararının bu requirements belgesinde varsayılan olarak kilitlenmemesi.

Bu çalışma `DEBATE-011` gereksinimlerini tanımlar; kod, prototype, executable spike, satın alma, provider approval,
ADR veya Gate 4 → 5 geçişi değildir.

## 21. İzlenebilirlik kaynakları

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/DECISION_LOG.md`
- `00_CONTROL/OPEN_QUESTIONS.md`
- `00_CONTROL/HANDOFF.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__JUDGE_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__MANAGER_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__JUDGE_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__JUDGE_SYNTHESIS.md`

Bu kaynaklar gerekçeyi ve bağlayıcı yönü sağlar; runtime, provider veya framework seçimi için hiçbirinde olmayan bir
sonuç bu belgeye varsayım olarak eklenmemiştir.
