# DEBATE-007 — Review B: Security, Operations, Cost and Provider Exit

**Tarih:** 2026-09-18  
**Reviewer:** Bağımsız adversarial security / operations / cost / provider-exit reviewer  
**Mod:** Read-only, no code, no prototype, no provider seçimi  
**İncelenen kayıtlar:** `DEC-0023`–`DEC-0033`, `CURRENT_STATE.md`, `SOURCE_OF_TRUTH.md`,
`DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES.md`,
`DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS.md`,
`DEBATE-007__DATA_BACKBONE_PRIMARY_RESEARCH.md` ve
`DEBATE-007__EXTERNAL_RESEARCH_INTAKE_REVIEW.md`

## Verdict

**`PASS_WITH_CHANGES AS PHASE-4 DIRECTION`** — Mantıksal ayrımlar, server/API otoritesi,
task-scoped offline paket, current/history/audit ayrımı, quarantine-first ingestion, outbox ve
restore/exit'in trust transition olarak ele alınması doğru yöndedir ve `DEC-0023`–`DEC-0033` ile
genel olarak uyumludur.

**`REJECT AS ADR, PROVIDER DECISION OR GATE-4→5 BASIS`** — Bu kayıt şu haliyle fiziksel
mimariyi, PostgreSQL'i, managed provider'ı, object-storage düzenini, audit ürününü, self-host
fallback'i veya harcama yetkisini onaylayamaz. Kritik bulgular kapanmadan bir aday `ACCEPT`
değil, `HELD/UNVERIFIED` kalmalıdır.

**`REJECT AS DIRECTION`** olan alt yorumlar da açıkça ayrılmalıdır: PostgreSQL-centric
önderlik, managed relational'ın varsayılan olarak tercih edilmesi ve PITR'in tek başına
ürün kurtarma kanıtı sayılması yalnızca hipotez/kontrol adayı olarak kalabilir. Bunlar yön
olarak yazılmaya devam ederse bu alt yönleri reddediyorum; bütün provider-neutral kontrol
şekli ise düzeltmelerle geçebilir.

Bu karar, “eksik sayısal hedef var” gerekçesiyle yönü toptan reddetmiyor. Ancak aşağıdaki
critical kontroller fiziksel aday karşılaştırmasına girmeden önce sözleşme ve no-code kanıt
barına eklenmelidir.

## Kabul edilen sağlam yön

- Client, browser, cache, push, backup veya object URL'sinin approval, publication, recall,
  authorization ya da current-eligibility authority olmaması.
- Internal Operations approval/publication/recall/role-policy mutation'larının online ve
  commit-time server authority ile sınırlandırılması.
- RLS/IAM/storage policy'nin savunma katmanı olması; tek başına authorization kanıtı
  sayılmaması.
- Selected motorcycle/task kapsamlı compact package; safety/application/safe-stop/recovery
  çekirdeğinin korunması; heavy media'nın optional olması.
- Current state, domain history, protected audit, provenance, release ve derived projection'ın
  ayrı anlamlar taşıması; LWW'nin high-consequence alanlarda yasaklanması.
- Quarantine-first upload/URL işleme, AI/OCR'nin attributable proposal olarak kalması ve
  untrusted içeriğin privileged origin/credential alamaması.
- Operation identity, idempotency, `OUTCOME_UNKNOWN`, conflict/hold ve restore quarantine
  durumlarının görünür tutulması.
- Logical export, restore drill, object/audit/config/identity kapsamı ve provider-exit'in
  sonraki ADR için zorunlu kanıt olarak görülmesi.
- No-code, AI-operated ve nontechnical-owner kısıtlarının teknoloji seçiminin parçası
  sayılması; owner'ın kod, database, build veya incident repair yapmasının varsayılmaması.

## Critical findings and required corrections

### C-01 — API/RLS sınırı tüm privileged yolları kapsamıyor

**Kanıt:** `D7-02`, `DB-AC-008`, `DB-AC-016`, `LB-01` ve S11–S17 server-side
authorization'ı doğru yönde ister. Ancak “server/API contract” ifadesi, alternatif privileged
yolların ve RLS istisnalarının tamamını bağlayan uygulanabilir bir path inventory ve negatif test
barı vermiyor.

PostgreSQL RLS veya benzeri row policy; table owner, superuser/BYPASSRLS, migration/restore
hesabı, admin/server SDK, RPC/function, bulk job, package builder, support console ya da doğrudan
object-storage policy'si üzerinden aşılabilir. API'nin var olması da API'nin doğru object/action/
scope kontrolü yaptığını kanıtlamaz. Bir istemci public/authenticated olsa bile object ID, query
filter, export, signed URL, websocket/poll, callback veya async job ile BOLA/IDOR ve scope
kaçışı yapılabilir.

**Zorunlu düzeltme:**

1. Her sensitive read, export, download, upload-finalize, mutation ve administrative operation
   için path matrix oluşturulmalı: browser/mobile API, RPC/function, admin SDK, worker/outbox,
   migration, restore/cutover, package builder, support path ve provider control-plane dahil.
2. Her path commit anında actor/workload identity, session/security epoch, exact action/object/
   scope, classification, workflow state, consequence, competence/independence, policy version
   ve expected generation'ı yeniden değerlendirmeli. Collection/bulk/filter/export yolları da
   object-level negative test kapsamına girmeli.
3. Runtime database identity, schema owner/superuser/BYPASSRLS veya sınırsız storage admin
   olmamalı; aday, eşdeğer bir non-bypass enforcement ve migration/restore ayrımını kanıtlamalı.
   “RLS enabled” veya “service account” tek başına geçiş koşulu değildir.
4. Workload identity insan onaylayıcısı gibi kullanılamamalı. Initiating human actor,
   operation identity ve security epoch service/job sınırından audit'e taşınmalı; service
   account approval/self-approval veya policy bypass yapamamalı.
5. Denied/not-found davranışı da enumeration, timing, error-detail ve bulk leakage açısından
   test edilmeli; deny/hold/failure denemeleri korunmuş audit evidence üretmeli.
6. Privileged/break-glass yol; dar kapsamlı, kısa süreli, step-up/dual-control'lu, attributable,
   security-epoch revoke edilebilir ve sonradan bağımsız review edilebilir olmalı. Emergency
   positive approval/unsuspend veya audit'i kapatma yetkisi alamaz.

Bu düzeltme `DB-AC-008`, `DB-AC-016`, S11–S17 ve hard-rejection koşullarına açıkça eklenmeden
authorization direction `PASS` sayılamaz.

### C-02 — Object credential ve capability contract'ı yetersiz

**Kanıt:** `D7-07` global storage credential verilmemesini doğru biçimde söyler; ancak bunun
yerine kullanılacak upload/download/export credential'ının kapsamını, süresini, object
generation'ını ve quarantine sınırını normatif olarak tanımlamaz. “Presigned/multipart/proxy/
resumable aday” demek object authorization'ı kapatmaz.

Geniş prefix'e veya mutable object key'e izin veren kısa ömürlü bir URL bile private media'yı
okutabilir, untrusted original'ı privileged origin'e taşıyabilir, approved artifact'ı
overwrite edebilir veya quarantine'ı atlayabilir. Digest/metadata sonradan kontrol edilmezse
canonical kayıt ile byte içeriği ayrışır.

**Zorunlu düzeltme:**

- Her object capability actor, operation, canonical object identity/version, classification,
  allowed method, expected size/content-type/digest, target namespace ve expiry ile bağlanmalı;
  arbitrary key/prefix listing, overwrite, delete, public ACL ve unrestricted read vermemeli.
- Upload capability tek kullanımlı veya açıkça resumable state'e bağlı olmalı. Finalize işlemi
  server-side authorization, checksum/digest, generation, size/type/scan state ve object
  metadata'yı tekrar kontrol etmeden object'ı canonical/active yapamamalı.
- Quarantine original, derived preview, official release artifact, private user media, export
  ve backup object'ları en azından policy/failure-domain anlamıyla ayrılmalı; operations origin,
  ambient cookie, native viewer, public URL veya raw object key ile servis edilmemeli.
- Capability/URL, object key, private metadata ve secret'lar application/proxy/audit log'larına
  sızmamalı; revocation, abort, orphan cleanup, expired upload ve version/delete-marker
  davranışı görünür state taşımalı.
- Download/export capability de aynı classification, recipient/purpose, step-up ve disclosure
  kaydıyla verilmeli; object storage policy'nin canonical API authorization'ını bypass etmediği
  negative testlerle gösterilmeli.

Bu contract olmadan `DB-AC-015`, `DB-AC-019`, S28–S32 ve quarantine-first iddiası eksik kalır.

### C-03 — Protected audit custody hâlâ “sonraki ADR tanımlar” seviyesinde

**Kanıt:** `D7-06` ve `D7-10` ordered evidence, custody, checkpoint/fork detection ve
fallback gerektiğini söyler; fakat high-consequence effect öncesi hangi custody'nin yeterli
olacağı, normal canonical store/provider/account ile ne kadar bağımsız olması gerektiği ve
compromise/account-loss sırasında nasıl çalışacağı bağlayıcı değildir.

Aynı mutable database, aynı provider account, aynı admin credential veya aynı region içindeki
ikinci tablo “protected/independent custody” değildir. `AUDIT` satırının transaction'a yazılmış
olması; privileged operator'ın geçmişi değiştiremeyeceğini, restore'un sequence'i fork
etmeyeceğini veya provider account compromise'ının hem truth hem kanıtı silmeyeceğini göstermez.

**Zorunlu düzeltme:**

1. Approval, publication, suspension/recall, role/policy/competence, restore, export, delete,
   key/recovery ve provider-plane high-impact olayları için effect öncesi minimum protected
   evidence koşulu konmalı. Normal custody ve bounded fallback ikisi de unavailable ise action
   `HELD` olmalı.
2. Audit event actor/workload, effective role/scope, session assurance/security epoch, server
   order, operation ID, exact object/classification, old/new state, policy/grant/competence ve
   release/suspension generation, reason/evidence, result ve impact/recovery owner'ı taşımalı.
   Denied, failed, partial ve attempted privileged actions da kapsanmalı.
3. Append-only/tamper-evident checkpoint, gap/fork/replay detection, restore reconciliation,
   sequence continuity ve custody health ölçümü; canonical truth'ten bağımsızlığı kanıtlanmış
   failure-domain/account/credential matrisiyle birlikte gösterilmeli. “Separate table”
   yeterli kanıt sayılmamalı.
4. Emergency negative authority'nin fallback'ı açıkça sınırlandırılmalı: evidence yoksa
   positive success varsayılmamalı; request `OUTCOME_UNKNOWN`/quarantine olarak kalmalı ve
   reconciliation owner'ı bulunmalı. Audit fallback'ı normal publish/role mutation için
   gizli bypass olmamalı.
5. Audit payload'ındaki kişisel verinin minimization, retention, legal hold, investigator
   access ve deletion/erasure istisnaları; audit custody'nin private user payload'ı kazara
   undeletable yapmayacağı şekilde tanımlanmalı.

Bu düzeltme `DB-AC-017`, S16–S17 ve restore/compromise drill'lerinin ön koşuludur.

### C-04 — Backup/PITR kapsamı ürünün tamamını kurtarmayı garanti etmiyor

**Kanıt:** `D7-10` logical export, PITR/equivalent, media/audit/config/identity/policy/secrets
inventory ve restore quarantine ister. Buna rağmen PITR'in database cluster'ı için; object,
audit, identity, keys, release packages, DNS/config ve in-flight operation'lar için aynı
zamanda tutarlı bir recovery point üretmediği açık bir rejection koşulu değildir.

Bir database PITR başarıyla tamamlanıp private media/object generation'larını, delete marker'ları,
audit checkpoint'lerini, policy/security epoch'i, release manifest'lerini, outbox/idempotency
durumunu, KMS/key erişimini veya domain/DNS cutover bilgisini kaçırabilir. “Backup success” veya
“new database/server created” application recovery değildir.

**Zorunlu düzeltme:**

- Recovery manifest en az canonical current/history/provenance, user history/work, object
  version/generation/digest/delete-marker/metadata, quarantine/derived lineage, release/
  package/artifact manifest, audit custody/checkpoint, identity-role-policy-competence-
  delegation/security epoch, schema/migration/config/feature meaning, outbox/in-flight/
  idempotency records, key references/rotation state, DNS/deployment trust roots ve retention/
  legal-hold kayıtlarını sınıflandırmalı.
- Database recovery point/LSN/generation ile object, audit ve configuration cut marker'ları
  bağlanmalı; exact global atomicity mümkün değilse allowed skew ve resulting `PARTIAL`/
  `UNKNOWN` semantics açıkça gösterilmeli. Eksik sınıf restore'u `RESTORE_QUARANTINE` dışında
  authoritative yapmamalı.
- PITR/full snapshot, logical export ve object/audit export ayrı amaçlarla test edilmeli. Temiz
  bir bağımsız account/provider/region veya self-host ortamına import edilip referential
  integrity, IDs, versions, classification, provenance traversal, release eligibility ve
  audit-chain continuity otomatik/incelemeli doğrulanmalı.
- Restore sonrası latest suspension/revocation floor, policy/security epoch, accepted pending
  operations, newer valid user data ve incompatible client/release yeniden uzlaştırılmadan
  positive eligibility/publication açılamamalı. Binary rollback newer data'yı atamamalı;
  forward recovery ve controlled restore generation kullanılmalı.
- Her domain için RPO/RTO ve kabul edilebilir kayıp ayrı belirlenmeli: canonical truth,
  release/audit, user history, private media, unsynced device queue ve optional media aynı
  restore sınıfı değildir. Bu hedefler owner kararı olmadan ADR'ye geçiş kanıtı olamaz.

### C-05 — Export/import “çıkış” değil, yalnızca envanter olarak kalıyor

**Kanıt:** `D7-10` ve `DB-AC-024` logical export, manifest, provider-exit ve reversibility
ister. Fakat export'un bağımsız bir ortamda gerçekten import edilip aynı anlamı ürettiğini,
provider-specific policy/identity/object/audit ayrıntılarının kaybolmadığını ve import sonrası
consumer package/release semantics'in korunabildiğini zorunlu kılmıyor.

SQL dump veya object listesi alınabilmesi; RLS/policy/function/trigger/grant/extension,
identity mapping, classification/consent, object version/delete marker, audit sequence,
release/package, outbox, tombstone, legal hold, encryption key veya provider-control-plane
anlamlarının taşındığını kanıtlamaz. Secret'ların export edilmesi de çözüm değildir; plaintext
secret taşımak yeni bir compromise yaratır, hiç taşımamak ise encrypted backup'ı açılamaz hale
getirebilir.

**Zorunlu düzeltme:**

- Exit package, data ile birlikte schema/contract versions, stable IDs, all domain states,
  relationships, object inventory/digests/generations, audit/provenance checkpoints, role/
  policy/competence mapping, release manifests, migrations, configuration meaning, auth
  identity mapping, retention/legal-hold ve key-wrapping/reencryption planını göstermeli.
- Export completeness manifest item count/digest/absence reason taşımalı; missing roles,
  ACL/policy, object, audit segment, private/shared field, key mapping veya provider config
  package'ı “complete” diye geçirmemeli.
- En az bir clean-room import, aynı provider dışındaki bir candidate ortamda veya documented
  self-host path'te, gerçek fixture ile tekrarlanmalı. Import `DRY_RUN`, `PARTIAL`, `CONFLICT`,
  `RECONCILING`, `RECONCILED` durumlarını ayırmalı ve post-import negative authorization,
  release/recall, provenance traversal, object privacy ve restore checks çalıştırmalı.
- Exit'in canlı uygulamayı değiştirmeden çalıştığı, import başarısızlığında source'un
  bozulmadığı ve cutover'ın generation/DNS/API/client compatibility fence ile yapıldığı
  kanıtlanmalı. Provider-specific extension veya hosted auth kullanılıyorsa equivalent
  semantic export yoksa candidate `HELD/REJECT` olmalı.

### C-06 — Account, region, billing ve control-plane failure first-class değil

**Kanıt:** `D7-09` account lock, region incident, quota ve billing suspension risklerini listeler;
`DB-AC-023` cost/alert/overage ister. Ancak S1–S36 içinde provider account lock, payment failure,
quota hard-stop, region unavailability/deletion, DNS/IdP/key account loss ve support escalation
başarısızlıkları için beklenen state ve safe mode yoktur.

Managed database sağlıklı olsa bile provider tenant kilitli, fatura reddedilmiş, quota aşılmış,
region erişilemez, object/audit hesabı silinmiş veya owner recovery factor kaybolmuş olabilir.
Bu durum normal outage gibi yeniden denenemez; aksi halde sistem false success, data loss veya
recall/publish körlüğü üretir.

**Zorunlu düzeltme:**

- Canonical DB, object, audit custody, identity/IdP, DNS/domain, signing/key ve billing/control
  plane için failure-domain/account/region/credential ownership matrisi yazılmalı. Aynı owner,
  account, region veya secret'a bağımlı parçalar “independent fallback” diye adlandırılmamalı.
- Account lock/payment failure/quota/overage, region outage, provider-wide outage, credential
  loss, export window expiry ve provider termination için explicit `SERVICE_UNAVAILABLE`,
  `ACCOUNT_HELD`, `BILLING_HELD`, `RESTORE_QUARANTINE` ve `OUTCOME_UNKNOWN` akışları; normal
  write/publish/role action'ın durması; bounded consumer safe/recovery content; exact owner,
  provider escalation ve reconciliation evidence tanımlanmalı.
- Multi-region veya second-provider seçilmezse bu bir eksiklik olarak saklanmamalı: kabul edilen
  RPO/RTO, outage sırasında neyin güvenle çalışacağı, neyin `HELD` kalacağı ve exit/cutover
  süresi açıkça yazılmalı. Ucuzluk, availability veya audit independence varsayımı değildir.
- Legal account owner, billing authority, recovery factors, support contract ve domain/DNS
  access'i nontechnical owner'ın gizli teknik repair yapmasını gerektirmeyecek şekilde
  sahiplenilmeli; AI insan/kurumsal kimliği taklit ederek provider işlemine geçememeli.

### C-07 — Hard cost cap yerine yalnızca fiyat/alert dili var

**Kanıt:** `D7-09`, `DB-AC-023` ve `DEC-0030` current price, tax/FX, hard cap/overage,
free/capped path ve exit ister. Fakat draft, provider'ın gerçek spend cap'i uygulayamadığı,
restore/egress/backup/object version/log/audit maliyetinin burst yaptığı veya cap tetiklenince
hangi capability'nin nasıl güvenli duracağı durumda kabul kriteri tanımlamıyor.

TRY 2.000–3.000 aylık planlama tavanı harcama yetkisi değildir; ücretsiz tier de hard cap
değildir. Alert, ödeme reddi veya kredi kartı limiti “kontrollü maliyet” sayılmaz. Restore drill,
PITR/WAL, object egress, logs, audit custody, email/SMS/identity, support, tax/VAT, FX,
minimum bill ve emergency transfer birlikte hesaplanmazsa provider hesabı fark edilmeden
ödenecek veya account lock'a girecek bir borç biriktirebilir.

**Zorunlu düzeltme:**

- Her aday için mandatory-now/later, deferrable, optional, scale-triggered ve free/local/
  capped yolları; minimum bill, storage/compute/backup/PITR/WAL, object version/egress,
  API/compute, logs/monitoring/audit, auth/notification, support, restore/exit rehearsal,
  tax/FX ve account recovery kalemleri owner-readable cost sheet'te gösterilmeli.
- Uygulanabilir hard limit veya güvenilir pre-commit budget guard yoksa candidate “capped” diye
  sunulmamalı; overage, quota ve billing failure'da canonical/audit/recovery safety davranışı
  simüle edilmelidir. Cap'in emergency negative authority'yi de yanlışlıkla susturup sistemi
  daha tehlikeli hale getirmediği kanıtlanmalı.
- Spend alert, kill-switch, provider billing authority, credit/debit approval, export/restore
  için acil bütçe ve owner notification bağımsızca tanımlanmalı. Hard cap uygulanamıyorsa
  capability `HELD` veya dar güvenli read/recovery moduna geçmeli; otomatik kredi/overage
  kabul edilmemeli.
- Current official regional price ve terms, release-window öncesi tekrar doğrulanmalı; dolar
  tahmini veya vendor free-tier pazarlaması karar kanıtı sayılmamalı.

### C-08 — AI-operability “owner debug etmez” kuralını çalıştırılabilir hale getirmiyor

**Kanıt:** `DEC-0029`, `DB-AC-022` ve D7-09 AI-native task/operability yönünü doğru kurar;
ancak hangi işlemlerin AI tarafından gözlem, öneri, dry-run, execute veya yalnızca insan/onaylı
uzman ile yapılacağı; başarısız repair'in nasıl duracağı ve kanıtın nasıl üretileceği açık
değildir.

“AI işletir” ifadesi AI'nin superuser credential, billing, key rotation, migration, restore,
delete veya emergency authority elde etmesi anlamına gelmemeli. Aksi halde nontechnical owner
debug etmiyor görünürken sistem başka bir açıklanamaz privileged operator'a bağımlı olur.

**Zorunlu düzeltme:**

- Her routine operation için minimum-sufficient AI runbook/context pack: amaç, precondition,
  allowed/forbidden scope, credential class, dry-run, idempotent command, stop condition,
  expected state, alert/evidence, rollback/forward-recovery, escalation owner ve plain-language
  owner output.
- AI; health/read-only inspect, bounded retry/reconcile, export manifest check, restore dry-run
  ve test ortamı işlemlerini execute edebilir. Irreversible delete, privilege/policy change,
  key/recovery change, migration cutover, restore-to-authority, billing approval ve high-
  consequence publish/recall için independent human/organizational authority veya explicit
  dual control gerekir.
- Fresh AI'nin yalnızca task context pack ile backup/restore/exit, account failure, object
  quarantine, auth negative test ve unknown-outcome reconciliation simülasyonunu tamamladığı;
  repository'nin tamamını okuma, owner'ın log yorumlama veya SSH ile onarım yapma varsayılmadığı
  no-code evidence ile gösterilmeli.
- Alert, dead-letter, poison operation, quota, audit sink, backup freshness, object drift,
  auth failure ve spend threshold için owner-readable action state olmalı. “Support'a sor” veya
  “owner SSH ile düzeltir” recovery planı değildir.

### C-09 — Self-host fallback gerçek exit/cutover yolu değil

**Kanıt:** `D7-09` raw self-hosting'i yalnız routine maintenance/recovery otomatik ve reviewable
ise eligible bırakır. Bu, managed account/region/billing failure'da sistemi nasıl ayağa
kaldıracağını, hangi artifact/config/secret/identity ile bootstrap edeceğini veya yeni ortamın
audit/release generation'ı nasıl devralacağını göstermiyor.

Self-host “provider yoksa başka sunucuya kurulur” düzeyinde kalırsa; image/toolchain/extension,
network/TLS/DNS, object storage, key custody, identity mapping, policy/RLS, monitoring, WAL/
backup, cutover ve rollback için yine tek insanın teknik müdahalesine ihtiyaç doğar.

**Zorunlu düzeltme:**

- Reproducible bootstrap artifact'ı (OS/container/dependency/config schema/migration/trust-root),
  least-privilege identity, encrypted backup/object/audit import, key re-encryption, DNS/API/TLS
  cutover, generation fence ve rollback/forward-recovery path'i tanımlanmalı.
- Temiz bağımsız ortamda AI-run restore/exit rehearsal, provider outage simulation, object/audit
  reconciliation, authorization negative tests ve consumer compatibility checks yapılmalı.
- Bu kanıt yoksa self-host “fallback” değil, yalnızca future option olarak etiketlenmeli;
  managed candidate'ın exit barını düşürmemeli ve outage'da bounded offline/HELD davranışı
  dürüstçe gösterilmeli.

## Major findings and required corrections

### M-01 — Managed provider'ın operasyon yükünü otomatik azalttığı varsayımı fazla geniş

`D7-09` “managed relational preferred investigation posture” derken provider'ın patching,
backup ve disk işini azaltmasını öne çıkarıyor. Bu yarar; backup completeness, restore cutover,
account/billing, quota, region, IAM, object/audit, extension, egress, support ve incident
responsibility'sini ortadan kaldırmaz. Managed planın hangi kısmı provider, hangi kısmı Kavriva
owner/AI tarafından işletilecek bir shared-responsibility matrix olmadan bu ifade managed'ı
varsayılan doğru cevaba dönüştürür.

**Düzeltme:** Managed, self-host ve diğer candidate family'leri aynı DB-AC-001–024, account/
region failure, AI-run restore ve cost/exit fixture'ı üzerinden kıyaslanmalı. Provider dokümanı
mekanizma kanıtıdır; application audit, policy, object, data residency, semantic export veya
owner-operability garantisi değildir.

### M-02 — PostgreSQL-centric hipotez, provider-neutral logical contract'a erken sızıyor

`D7-01` ve ön belirleme relational/PostgreSQL-centric family'yi leading hypothesis yapıyor;
primary research ise PostgreSQL'in RLS, JSONB, WAL/PITR ve logical export mekanizmalarını
ayrıntılı anlatıyor. İlişkisel constraint ihtiyacı makul olsa da mevcut kayıt workload,
expected volume, query/concurrency, retention, region/legal, package shape, object ratio,
operator burden ve provider terms ile PostgreSQL'i diğer relational veya non-relational
adaylardan üstün kanıtlamıyor.

**Düzeltme:** “PostgreSQL-centric” ifadesi en fazla `relational transactional family —
engine hypothesis` olarak yeniden adlandırılmalı. Logical contract PostgreSQL terimlerine
bağımlı olmamalı; WAL/RLS/JSONB/PITR, eşdeğer mekanizma karşılaştırma notları olarak kalmalı.
En az iki relational candidate ve uygun bir document/BaaS veya self-host counterfactual'ı
aynı workload/DB-AC/S1–S36/restore/exit/cost fixture'ı ile karşılaştırılmadan engine/provider
önderliği kabul edilmemeli.

### M-03 — Canonical transaction ile object/audit/outbox arasında çapraz-sistem atomicity varsayımı

`D7-08` outbox'ı canonical mutation ile aynı transaction'a koyar; `D7-06` protected audit'ı
ayrı custody olarak ister; `D7-07` object boundary'yi ayırır. Bu üçü fiziksel olarak farklı
failure domain'lerde olduğunda tek transaction ile “hepsi commit oldu” kanıtlanamaz. Object
upload başarılı olup metadata commit olmazsa, audit yazılıp release commit olmazsa veya outbox
relay gecikirse `current`, object ve evidence farklı gerçeklikler taşıyabilir.

**Düzeltme:** Prepare/commit/partial/failed/outcome-unknown/reconcile state machine'i; object
digest/generation claim'i; audit evidence-before-effect koşulu; outbox pending/dead-letter ve
compensation/forward-recovery kuralları tanımlanmalı. Saga/compensation “rollback ile sessiz
silme” olmamalı. Approval ancak exact immutable object/artifact refs ve audit intent güvenli
şekilde bağlandığında authoritative olabilir.

### M-04 — Operation/idempotency contract'ı semantic edge-case'leri bağlamıyor

D7-03 ve D7-05 durable operation identity'yi doğru ister. Ancak later ADR için key scope,
payload fingerprint, actor/session binding, expected version/generation, retention/TTL,
cross-region uniqueness, replayed result, duplicate with changed payload, expired key,
poison/dead-letter, asynchronous callback ve status lookup authorization açıkça mandatory
değildir.

**Düzeltme:** API/worker contract'ı same operation identity + same intended effect/result,
changed payload reject, stale generation conflict, `OUTCOME_UNKNOWN` resolver/escalation,
partial scope and safe replay rules'ını fixture ile göstermeli. Idempotency key tek başına
authorization veya conflict resolution değildir.

### M-05 — Numeric unknown'lar geleceğe bırakılmış ama ADR-blocking olarak yeterince işaretli değil

Freshness/offline eligibility, client support window, RPO/RTO, audit retention, package/cache/
media limits, quota, idempotency TTL, restore drill cadence, support/escalation SLA ve cost
ceiling open kalabilir; fakat acceptance sonucu bunlar bilinmeden “candidate passes” izlenimi
vermemeli.

**Düzeltme:** Her açık sayı owner decision gerektirir ve ilgili capability `HELD/UNVERIFIED`
olmalıdır. Unknown threshold low-risk varsayılanına indirgenemez; high-consequence data,
release, authorization, audit ve recovery için safety-preserving conservative behavior
tanımlanmalı.

### M-06 — Privacy, retention ve key custody recovery/exit'e tam bağlanmamış

D7-10 privacy/retention rules der; `DB-AC-019` export/delete ayrımını kurar. Buna rağmen
backup, object version, audit copy, cache, log, signed URL, search projection, export file ve
provider snapshot'ında user-private data'nın ne zaman silineceği/minimize edileceği; legal hold,
incident hold ve key destruction'ın nasıl birlikte çalışacağı; encrypted backup'ın hangi
portable key mapping ile açılacağı açık değildir.

**Düzeltme:** Classification-copy matrix (canonical, object, audit, cache, backup, export,
device, provider log), retention/legal hold, deletion/redaction/tombstone, residual disclosure
warning ve key rotation/destruction/reencryption contract'ı eklenmeli. Protected audit'in
immutable metadata'sı ile private payload ayrılmalı; raw secret export kabul edilmemeli.

### M-07 — Provider/platform account identity ile product actor identity ayrımı eksik

Bir provider owner, billing admin, domain owner, IdP admin veya storage administrator'ın Kavriva
reviewer/approver olarak görünmesi confused deputy yaratabilir. `D7-02` actor/session kontrolü
ve `D7-09` identity/policy mapping söyler; ancak provider control-plane action'larının product
authority'ye nasıl bağlandığı, account transfer/recovery ve owner kaybında attribution
tanımlanmamıştır.

**Düzeltme:** Product actor, workload identity, provider control-plane identity, billing owner,
legal account owner ve recovery contact ayrı sınıflandırılmalı. Provider console'da yapılan
işlem application approval sayılmamalı; account transfer/recovery/key rotation audit'i
canonical release/recall semantics'e controlled reconciliation olmadan authority vermemeli.

### M-08 — Region/data-residency ve provider support failure acceptance'a bağlanmamış

Region, legal/compliance ve data residency `D7-09`, `D7-10` ve option listesinde açık kalıyor.
Bu doğru bir non-decision'dır; fakat private/user data, audit ve backup'ın aynı region'da tutulması
ile exit/restore region'ının farklı olması privacy, latency, availability ve legal outcome'ı
değiştirir. Provider incident sırasında nontechnical owner'ın support'a hangi evidence pack ile
başvuracağı da tanımsızdır.

**Düzeltme:** Candidate matrix region availability/residency, cross-region export, support
channel/SLA, account recovery ve incident evidence handoff'u göstermeli. “Multi-region” veya
“global backup” mevcut değilse bu açıkça accepted risk/HELD condition olarak yazılmalı.

## Minor findings and required corrections

### N-01 — “One canonical transactional core” fiziksel tek veritabanı gibi okunabilir

Bu ifade logical owner ile physical store ayrımını zayıflatabilir. “One canonical authority per
domain; cross-domain manifest/audit links” terminolojisiyle yazılmalı; protected audit ve object
plane'ın aynı transaction/store olduğu izlenimi verilmemeli.

### N-02 — PITR, logical export, snapshot, object copy ve device package terimleri recovery class'a
ayrılmalı

Her biri farklı RPO, consistency, restore speed ve portability taşır. “PITR/equivalent” yerine
canonical DB, user work, audit, media, release artifact, cache ve unsynced device için ayrı
amaç/kanıt tablosu kullanılmalı.

### N-03 — Outbox/relay operational minimum'ları daha görünür olmalı

Pending age, lag, retry budget, poison/dead-letter, replay, duplicate, schema compatibility,
slot/WAL/storage pressure ve owner-readable alert'ler acceptance walkthrough'unda gösterilmeli.
Outbox'ın varlığı teslimatın gerçekleştiği anlamına gelmemeli.

### N-04 — Local device loss ve encryption/key loss ayrı bir negative case olmalı

Device clone/restore için S21 vardır; theft, OS storage clearing, keychain reset, unsynced queue,
private media ve account rebind sonrasında neyin yeniden üretileceği görünür bir state ile
gösterilmeli. “Durable local” kayıpsız sync garantisi değildir.

### N-05 — Owner-readable observability standardı isimlendirilmemiş

Health, backup freshness, restore rehearsal, audit sink, object drift, auth denial, quota,
spend, outbox lag ve provider incident tek bir opaque dashboard'a sıkışmamalı; her alarm reason,
scope, owner, next action, evidence ve safe mode göstermeli.

### N-06 — Safe recovery media ile optional media'nın eviction sınırı birlikte gösterilmeli

`D7-04` ve `DB-AC-012` doğru yönde olsa da active work, safe-stop ve recovery closure'ın
cache-pressure/device-loss sonrasında korunması; optional asset'in yeniden indirilebilir olması
ve incomplete package'ın reject edilmesi aynı package manifest walkthrough'unda gösterilmeli.

## Required correction gate before ADR consideration

Manager/Judge bir sonraki aşamaya geçmeden aşağıdaki evidence pack'i istemeli:

1. **Authorization path matrix:** API/RPC/admin SDK/worker/migration/restore/object/callback/
   export/provider-console yolları; actor/workload identities; RLS/BYPASSRLS/owner bypass;
   BOLA/bulk/enumeration negative tests; break-glass and security-epoch behavior.
2. **Object capability contract:** scoped credential, digest/generation/type/size binding,
   quarantine/finalize, download/export disclosure, revocation, orphan cleanup ve log leakage.
3. **Audit custody matrix:** event-before-effect, normal/fallback custody, independence,
   checkpoint/fork/gap/replay, compromise/account-loss, restore reconciliation, privacy/retention.
4. **Cross-plane recovery manifest:** database/history, object/media, release/packages,
   audit, identity/policy/competence, config/migration/outbox, key references, DNS/trust roots.
   PITR, logical export, object/audit export ve clean-room import results.
5. **Export/import/exit rehearsal:** independent target, stable IDs/versions/classification,
   policy/auth mapping, object digests, audit continuity, release/recall and post-import negative
   authorization proof; source remains safe if import fails.
6. **Provider failure-domain matrix:** account lock, billing/quota/cap, region/provider outage,
   identity/DNS/key loss, support escalation, safe mode, fallback/cutover and exact RPO/RTO.
7. **Staged cost sheet:** mandatory/later/optional/scale, official regional current pricing,
   minimum/overage/egress/backup/log/support/tax/FX, enforceable cap or explicit HELD behavior,
   no silent subscription/credit, release-window re-verification.
8. **AI operations pack:** minimum context runbooks, least privilege, dry-run/reversible
   commands, stop conditions, alert/evidence, independent approvals, clean-room restore/exit
   simulation; no owner code/debug/SSH/credential improvisation.
9. **Engine/provider-neutral comparison:** PostgreSQL only as one engine hypothesis; equal
   relational, managed/self-host and viable adjunct counterfactuals against DB-AC-001–024 and
   S1–S36; no PostgreSQL-specific term in the logical contract unless translated.

Critical evidence yoksa candidate `ACCEPT` değildir. Affected capability `HELD/UNVERIFIED` kalır;
bu durum düşük maliyet veya hızlı teslim baskısıyla safety, privacy, audit, data continuity veya
owner-operability standardını düşürmez.

## Final position

After the corrections, the provider-neutral backbone can remain a strong Phase-4 working
direction: canonical authority boundaries, API-mediated authorization, bounded offline delivery,
separate object/audit planes, explicit operation states, and tested recovery/exit.

Until then:

- PostgreSQL is not selected; PostgreSQL-centric wording is rejected as a direction and may only
  remain a comparative hypothesis.
- Managed relational is not a safety or cost guarantee; “preferred investigation” is held until
  the provider responsibility, account failure, hard-cap and exit matrix closes.
- PITR, logical dump, provider snapshot or “backup succeeded” is not a complete recovery proof.
- RLS, API presence, signed object URL, service account, AI runbook or managed plan is not by
  itself an authorization, audit, object confidentiality, operability or exit proof.
- No Phase-5 ADR, provider approval, code/prototype, paid subscription or Gate 4→5 transition
  is authorized by this review.

**Final verdict:** `PASS_WITH_CHANGES AS DIRECTION`; `REJECT AS ADR/PROVIDER/GATE BASIS`.
If C-01 through C-09 and the required correction gate are not incorporated, the fallback verdict
is `REJECT AS DIRECTION`, not a silent pass or an implementation task.
