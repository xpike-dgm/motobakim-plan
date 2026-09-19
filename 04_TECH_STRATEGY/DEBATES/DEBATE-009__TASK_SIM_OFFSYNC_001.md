# DEBATE-009 — Equal No-Code AI Task Simulation: Offline Sync Failure Chain

Durum: CONTROLLED NO-CODE AI TASK SIMULATION / TWO FINALISTS / NO WINNER / ADR NOT READY  
Tarih: 2026-09-18  
Kapsam: Flutter Android-first / iOS-later consumer-mobile yönü; A Drift/custom ve B PowerSync  
Simülasyon kimliği: TASK-SIM-OFFSYNC-001  

## 1. Amaç ve bağlayıcı sınır

Bu dosya, DEBATE-009'un iki finalistini aynı bounded AI task üzerinden karşılaştırmak için hazırlanmış
belgesel bir failure walkthrough'dur. Kod, prototip, executable spike, provider satın alma, gerçek benchmark,
cihaz geçişi veya üretim kararı yoktur. Amaç, taze bir AI implementer'ın yalnızca sınırlı bağlamla güvenli
bir görev planlayıp planlayamadığını ve iki adayın aynı failure sözleşmesini taşıyıp taşıyamadığını görmektir.

İki aday da aynı olay dizisini, aynı veriyi, aynı kullanıcı görünürlüğünü, aynı reviewer evidence alanlarını
ve aynı PASS / HELD / REJECT eşiğini kullanır. Adaya özel tablo yalnızca kavramsal dosya/sözleşme yüzeyini
ve araştırmada açık kalan riskleri değiştirir. Bu tablo bir tercih sıralaması değildir.

12 MB compact package, 150 MB optional media, 25 MB cellular confirmation ve 250 MB cache fixture değerleri
eşit karşılaştırma sabitleridir; final ürün limitleri değildir. 2 GB ilgisiz katalog bu task'ın negative
scope'udur ve indirilmez.

## 2. Okunan bağlam ve kararlarla uyum

Bu simülasyon aşağıdaki dosyalardaki mevcut resmi/primary araştırma ve ürün sözleşmesini taşır:

- DEBATE-009__OFFLINE_SYNC_REQUIREMENTS_SYNTHESIS.md: OSR-INV-001..017; OSR-PKG, OSR-DLT, OSR-OPS ve
  OSR-SYN sözleşmeleri; 12/150/25/250 MB fixture; EQ-01..EQ-18; PASS/HOLD/REJECT kuralları.
- DEBATE-009__OFFLINE_SYNC_OPTIONS_PRIMARY_RESEARCH.md: A Drift/custom ile B PowerSync adaylarının
  transport, queue, authority, recall, idempotency, RLS/stream, cost ve exit sınırları.
- DEBATE-009__MOBILE_PLATFORM_FAILURE_RESEARCH.md: MPR-01..MPR-18 ve Android, Apple, Flutter/Dart
  resmi platform mekanizmalarının failure sınırları.
- DEBATE-009__MANAGER_PROPOSAL.md: iki yerel lane (bounded package ve durable operation), API boundary,
  atomic promotion, restore quarantine, owner-debug yasağı ve reversible candidate yönü.
- DEC-0023: task-scoped/data-efficient offline; compact safe core ve optional heavy media ayrımı.
- DEC-0024: risk-tiered bounded offline; stale/unknown/incompatible/recall durumunda fail-closed ve
  Internal Operations mutation'larında online authority.
- DEC-0031: adaylar için aynı fixture, cohort, senaryo ailesi ve PASS/HOLD/REJECT yöntemi.
- DEC-0033: Flutter consumer-mobile çalışma yönü; Android ilk lane, iOS sonraki lane.
- DEC-0034: provider-neutral transactional authority, versioned package, durable identified operation,
  visible conflict/hold/unknown ve restore/export/exit anti-resurrection floor.
- DEC-0035: managed Supabase-centered fiziksel yönün API boundary'si; local engine/provider sync
  authority değildir; bu dosya yeni provider veya abonelik seçmez.

MPR bulgusu simülasyonda mekanizma kanıtı olarak kullanılır; hiçbir Flutter/Android/iOS API'si durable
outbox, canonical authority, recall guarantee, migration proof veya accessibility proof yerine sayılmaz.

## 3. Ortak task, kullanıcı amacı ve fixture

### 3.1 Task brief

AI'dan istenen tek bounded task şudur:

> Seçili motorcycle + tek bakım task'ı için daha önce kabul edilmiş compact package'ı koruyarak,
> yarım indirme, yanlış tabanlı delta, process kill, offline kullanıcı operasyonu, kayıp response,
> duplicate retry, server recall, ownership/provenance conflict ve consent'siz optional media
> olaylarını güvenli biçimde modelle. Kullanıcıya hangi state'in gösterileceğini, hangi işin
> durable kalacağını ve hangi authority'nin kazanacağını sözleşme olarak yaz. Her iki finalist için
> aynı evidence paketini ve recovery sınırını üret. Kod yazma; winner ilan etme.

Offline kullanıcı operasyonu, seçili task üzerinde bir ownership/provenance evidence güncellemesi
(kullanıcının yerel not/evidence metadata'sı ile authority-sensitive provenance claim'in birlikte
taşındığı bir operation) olarak tanımlıdır. Bu, yerel yazının kaybolmamasını fakat server kabulü,
ownership veya provenance authority'sinin offline yazıyla verilmemesini sınar. Note/evidence parçası
yerel olarak korunabilir; authority-sensitive claim, conflict çözülmeden olumlu gerçek gibi gösterilemez.

### 3.2 Sabit fixture

| Alan | Sabit giriş | Bu simülasyonda anlamı |
|---|---|---|
| Compact package | 12 MB hedef | Seçili motorcycle/task safe core; tam katalog değil |
| Transfer kesintisi | %50, yaklaşık 6 MB staged | Process/delta öncesi partial object; active package olamaz |
| Valid local base | P0, generation G0, bütün digest doğrulanmış | E0'daki son geçerli package; failure boyunca korunur |
| Wrong-base delta | Delta D1, target G1, base G-1 (local base G0 değil) | Closest-base merge yok; atomik reject |
| Optional media | 150 MB, ayrı/on-demand | Compact safety/application/recovery core'un parçası değil |
| Cellular confirmation | 25 MB üzeri transfer için explicit choice | Bu run'da consent yok; 150 MB başlamaz |
| Cache fixture | 250 MB pressure/eviction fixture'ı | Ürün cache limiti değil; active work evict edilmez |
| Unrelated catalog | 2 GB | Download edilmesi negative scope ihlalidir |
| Local operation | O-77, stable operation ID | Offline ownership/provenance evidence update; local-saved server-accepted değildir |
| Server events | Recall R-12 ve provenance conflict C-55 | Sıraları gözlemlenebilir authority generation ile kayda alınır |
| Network event | Reconnect; response lost; same operation duplicate retry | Timeout sonucu OUTCOME_UNKNOWN; blind duplicate yok |
| Process event | E1/E2 sonrasında uygulama process kill | Callback gelmese de durable state kurtarılabilir olmalı |
| Platforms | Android-first lane; iOS-later lane | Her ikisi için aynı contract, ayrı gerçek-cihaz evidence gerekir |

### 3.3 Olay sırası

| Adım | Olay | Beklenen ortak yorum |
|---|---|---|
| E0 | P0 compact package G0 geçerli; optional media yok; cellular consent yok | Kullanıcı compact core'u kullanabilir; media hazırmış gibi gösterilmez |
| E1 | P1'in 12 MB transferi %50'de kesilir | P1 yalnız staging'de/failed; P0 active current kalır; partial dosya authority değildir |
| E2 | D1 wrong-base delta, G-1 tabanını iddia eder | D1 reject/quarantine; G0 cursor geri sarılmaz; closest base veya karışık merge yok |
| E3 | Cihaz process'i kill edilir | Callback beklenmez; restart sonrası P0 ve son durable outbox state okunur |
| E4 | Kullanıcı offline O-77 yazar | Stable ID ve payload digest ile durable local PENDING; local-saved etiketi server accepted değildir |
| E5 | Reconnect olur; submit response kaybolur; aynı O-77 duplicate retry görülür | İlk sonuç OUTCOME_UNKNOWN; yalnız aynı ID/status lookup/idempotent replay; yeni operation yok |
| E6 | Aynı reconciliation döneminde R-12 recall ve C-55 ownership/provenance conflict gelir | Negative recall floor kazanır; conflict/held görünür; iki taraf ve audit korunur; silent LWW yok |
| E7 | 150 MB media bekliyor; cellular consent yok | MEDIA_BLOCKED_CELLULAR_CONSENT; download/auto-retry yok; user choice ve Wi-Fi yolu görünür |
| E8 | Recovery/owner review | Full bounded package reissue ve authoritative operation lookup; owner debug yapmaz; unresolved ise HELD |

Olaylar arasında OS callback sırası, network callback sırası ve server response sırası güvenilmezdir.
Task packet, gözlenen generation/event sequence'i saklamalı; cihaz wall clock'u authority değildir.

## 4. Ortak durum sözleşmesi

Her aday aşağıdaki ortak state isimlerini ya doğrudan ya eşdeğer, user-visible bir sözleşmeyle üretmelidir.
Farklı provider isimleri eşdeğerlik kanıtı olmadan kabul edilmez.

| State | Giriş koşulu | Kullanıcı ve authority davranışı |
|---|---|---|
| PACKAGE_CURRENT(G0) | P0 manifest/schema/release/digest/recall floor geçerli | Compact core kullanılabilir; server authority yerine geçmez |
| PACKAGE_STAGED_50 | P1 yalnız staged, yaklaşık %50 | Kullanıcıya devam ediyor/yarım/yeniden denenebilir; active package olarak seçilmez |
| PACKAGE_REJECTED_PARTIAL | Transfer tamamlanmadı veya digest doğrulanmadı | Partial dosya silinir/quarantine edilir; P0 korunur; unbounded retry yok |
| DELTA_REJECTED_WRONG_BASE | D1 base generation G0 değil | Delta atomik reject; cursor ilerlemez/geri sarılmaz; bounded full reissue |
| PROCESS_RESTARTED | Process kill/reboot/foreground dönüşü | Durable local state okunur; callback yokluğu failure truth değildir |
| OP_PENDING_LOCAL | O-77 durable local transaction'da | Local work saved olarak görünür; server success değildir |
| OP_SUBMITTED | Submit attempt başladı | Stable ID, base generation, digest, session/device ve attempt audit edilir |
| OP_OUTCOME_UNKNOWN | Response timeout/lost veya transport belirsiz | Blind retry ve duplicate yeni ID yasak; status lookup/reconcile gerekir |
| OP_ACCEPTED_SERVER | Server status endpoint gerçekten kabulü doğrular | Kabul kaydı ayrı tutulur; recall/eligibility yine ayrıca uygulanır |
| PROVENANCE_CONFLICT / HELD | C-55 veya yüksek önem taşıyan unknown | İki sürüm/source/provenance korunur; insan/authoritative rule çözmeden olumlu claim yok |
| RECALL_KNOWN_STOP | R-12 recall/suspension/delete floor biliniyor | Recall edilen içeriğin uygulanması/gösterimi fail-closed; cached positive kazanamaz |
| MEDIA_BLOCKED_CELLULAR_CONSENT | 150 MB > 25 MB ve consent yok | Transfer başlamaz; boyut, neden, Wi-Fi/sonra seçeneği erişilebilir |
| RECONCILING | Status lookup, full package, conflict veya floor resolution bekleniyor | Bekleme açıkça gösterilir; background yalnız fırsattır |
| SAFE_STOP | Kritik truth unknown/recall/conflict/migration/key/storage failure | Güvenli kapanış/recovery yolu; history yeniden yazılmaz |

State precedence:

1. Recall/revoke/suspension/delete gibi negatif authority, cached eligibility veya eski package'ı
   geçersiz kılar ve anti-resurrection floor bırakır.
2. Conflict, held ve outcome-unknown; local success, last-write-wins veya duplicate retry'dan üstündür.
3. Server tarafından doğrulanmış OP_ACCEPTED_SERVER, operation sonucunu kanıtlar; recalled content'in
   tekrar kullanılabilirliğini veya ownership/provenance claim'inin doğruluğunu tek başına kanıtlamaz.
4. Local durable write, server acceptance değildir. Retry başarısı ancak stable ID ve authoritative
   status ile ayrıştırılır.
5. Reconciliation tamamlanmadan UI, pending/unknown/held durumunu complete diye kısaltamaz.

## 5. Ortak AI context packet ve evidence sözleşmesi

Fresh AI implementer'a yalnız aşağıdaki context verilir. Repo'nun geri kalanı, seçilmemiş provider
SDK'sı, secret, service-role key, production database veya owner'ın canlı müdahalesi context dışıdır.

| Context ID | Bounded input | AI'ın cevaplaması gereken soru | Yasak kapsam |
|---|---|---|---|
| C00 Governance | Bu dosya, requirements synthesis, DEC-0023/24/31/33/34/35 | Task'ın no-code ve equal fixture sınırını nasıl korursun? | ADR, satın alma, gerçek benchmark |
| C01 Product state | OSR-INV-001..017, OSR-SYN-007 | Offline availability, local save, server acceptance ve recall nasıl ayrılır? | Local UI'ı canonical authority yapma |
| C02 Package/delta | OSR-PKG-001..014, OSR-DLT-001..008; P0/G0/P1/D1 | Stage, validate, promote, wrong-base reject ve reissue nasıl sınırlandırılır? | Full catalog, closest-base merge, partial promote |
| C03 Durable operation | OSR-OPS-001..012; O-77 | Stable ID, transaction, unknown response ve idempotent lookup nasıl korunur? | Blind retry, silent LWW, local accepted etiketi |
| C04 Recall authority | R-12, tombstone/floor, OSR-INV-009/013 | Recall geldiğinde cached package ve accepted response ne olur? | Recall'i push/background callback'e bağlama |
| C05 Provenance conflict | C-55, source/ownership metadata | İki taraf nasıl korunur ve hangi claim HELD olur? | Human owner'ı DB debug'ına yönlendirme |
| C06 Media/network | 150/25 MB, no consent, reconnect/lost response | Media ve compact transfer policy'si nasıl ayrılır? | Consent'siz cellular transfer |
| C07 Platform lifecycle | MPR-01..18; Android-first/iOS-later | Process kill, storage pressure, clock, restore, key, migration, accessibility nasıl kanıtlanır? | Callback'i durable commit sayma |
| C08 Candidate topology | Sadece A veya B'nin seçenek araştırması | Aday hangi layer'ı sahipleniyor, hangi boundary dışına çıkamaz? | Provider seçimini kesinleştirme |
| C09 Evidence/review | EVID-01..12 alanları ve reviewer rolleri | Belgesel iddia ile gerçek cihaz/authority kanıtını nasıl ayırırsın? | Simulator/demo'yu cihaz kanıtı sayma |
| C10 Owner/runbook | Held/reject/exit/recovery rules | Owner'ın güvenli kararı nedir, hangi soru çözülmeden ilerlenmez? | Owner'ın implementer/debugger olması |

### 5.1 Ortak evidence kaydı

Her packet için aynı evidence alanları doldurulur:

| Alan | Zorunlu içerik |
|---|---|
| EVID-01 fixture identity | TASK-SIM-OFFSYNC-001, candidate A/B, context snapshot, tarih |
| EVID-02 entities | P0/P1, G0/G-1/G1, D1, O-77, R-12, C-55, optional media |
| EVID-03 transition log | E0..E8, observed order, state before/after, generation/cursor |
| EVID-04 integrity | manifest/content digest, payload fingerprint, schema/release/capability, dependency closure |
| EVID-05 durability | transaction boundary, crash point, restart result, last known durable state |
| EVID-06 network | metered/expensive/constrained observation, timeout, lost response, retry ID |
| EVID-07 authority | server operation status, recall floor, conflict sources, audit/reconciliation result |
| EVID-08 user visibility | pending/unknown/held/conflict/blocked/safe-stop text, semantics, accessibility route |
| EVID-09 recovery | quarantine, full compact reissue, status lookup, no partial merge, no duplicate |
| EVID-10 platform plan | Android cohort and iOS cohort, process kill/storage/clock/restore/key/migration tests |
| EVID-11 reviewer | implementer, independent data/safety reviewer, platform reviewer, validator, owner |
| EVID-12 disposition | PASS, HELD veya REJECT; missing evidence and next owner action |

Belgesel simulation evidence, gerçek Android/iOS/TalkBack/VoiceOver/accessibility/restore/migration
kanıtının yerine geçmez. Reviewer her iddiayı DOCUMENTARY, SIMULATED veya REAL-DEVICE olarak etiketler.

### 5.2 Ortak disposition kapısı

- PASS: Task sözleşmesi tüm E0..E8 state'lerini ve recovery'yi taşır; authority boundary, accessibility
  labels, owner action ve candidate-specific dependency görünürdür; sonraki gerçek cihaz, restore,
  migration, key, accessibility ve exit testlerinin nasıl kapanacağı kayıtlıdır. Bu dosyada hiçbir aday
  için gerçek PASS üretilmez; yalnız teorik kapı tanımlanır.
- HELD: Güvenli model mümkündür fakat gerçek cihaz, server authority, iOS parity, migration/key,
  RLS/stream veya cost/exit evidence eksiktir; owner'dan araştırma/debug değil, belirli kanıt ve kapasite
  kararı beklenir.
- REJECT: Partial package active olur; wrong-base merge yapılır; local write accepted sayılır; lost
  response yeni duplicate operation olur; recall/negative floor bypass edilir; provenance conflict LWW
  ile ezilir; consent yokken media iner; restore resurrection yapar; direct provider DB authority olur;
  accessibility state saklanır; owner canlı sistemi debug eder. Bu ihlal puanla telafi edilemez.

## 6. Ortak bounded packet set (P01–P08)

P01–P08 her iki adayda aynı görevdir. Aşağıdaki sıra AI'ın cevaplaması gereken bounded unit'leri
tanımlar. Candidate tabloları aynı packet ID'lerini kullanır; böylece bir aday daha kolay bir fixture,
daha gevşek state veya daha az evidence kullanamaz.

| Packet | Bounded output | Minimum reviewer assertion |
|---|---|---|
| P01 Package stage / wrong-base | P1 %50 kesintisi, D1 reject, P0 korunması ve full reissue planı | Partial/mixed/closest-base hiçbir zaman current değil |
| P02 Process kill / durable local transaction | E3 restart sonrası package/outbox/metadata state'i | Callback yokluğunda da durable boundary anlaşılır |
| P03 Offline O-77 | Stable ID, payload digest, expected generation, local state | Local save ≠ server success; ownership claim positive değil |
| P04 Lost response / duplicate retry | Timeout → UNKNOWN → status lookup/idempotent replay | Yeni duplicate operation veya blind retry yok |
| P05 Recall + provenance conflict | R-12 ve C-55 aynı reconcile döneminde | Recall floor kazanır; iki source görünür; claim HELD |
| P06 Optional media / cellular gate | 150 MB bekleyen media, 25 MB consent yok | Auto cellular transfer yok; compact core ile media ayrıdır |
| P07 Platform/recovery | storage pressure, clock, key, restore, schema/update ve Android/iOS farkları | En az bir owner-actionable real evidence planı |
| P08 Evidence / review / exit | Candidate-specific dossier, dependency/cost/exit ve disposition | Owner implementer/debugger değildir; winner yok |

## 7. A — Drift/custom adayının ortak task simülasyonu

### 7.1 Aday sınırı

A, Flutter client içinde app-owned SQLite/Drift benzeri yerel persistence ile Kavriva API'nin
bounded package/delta, durable operation, idempotency, recall floor ve reconciliation sözleşmesini
uygulamayı varsayar. Drift'in local transaction/type-safety/reactivity sağlaması sync authority,
encryption/key lifecycle, background execution, recall veya server conflict çözümünü otomatik
sağlamış sayılmaz. Gerçek provider, encryption kütüphanesi veya API hosting seçilmemiştir.

### 7.2 A packet tablosu

| Packet | AI'ın A için beklenen planı | Kavramsal files/contracts touched (gerçek edit değil) | Beklenen state ve recovery | Reviewer evidence | Owner action | Mevcut disposition |
|---|---|---|---|---|---|---|
| A-P01 | Stage'i active DB'den ayır; P1 transfer checkpoint/digest ile %50'de kesilince P0'ı seçili tut; D1'in base generation'ını G0 ile exact compare et | contracts/package/manifest-v1; contracts/package/delta-v1; local/package/staging; local/package/promoted; local/package/recall-floor | PACKAGE_CURRENT(G0) + PACKAGE_STAGED_50; sonra PACKAGE_REJECTED_PARTIAL ve DELTA_REJECTED_WRONG_BASE; staged/quarantine temizlenir, bounded P0-compatible full reissue istenir | Manifest fields, content/manifest digest, base/target generation, atomic transaction boundary, wrong-base negative test, no closest merge | Package/delta owner'dan generation/floor/tombstone contract evidence ve full-reissue SLO ister; SQL debug yapmaz | HELD — custom protocol ve real crash/digest/pressure kanıtı açık |
| A-P02 | Process kill'den önce hangi local transaction'ın commit edildiğini tanımla; restart'ta P0, staged metadata ve outbox state'ini ayrı oku; partial Dart file overwrite'u kabul etme | local/schema/package; local/schema/outbox; local/transaction-boundaries; platform/android/lifecycle-policy; platform/ios/lifecycle-policy | PROCESS_RESTARTED; committed P0 ve O-77 yoksa önceki durable state korunur; yarım transaction rollback/quarantine; callback yokluğu failure truth değildir | Crash point matrix, transaction/savepoint/idempotency proof, Android process death, iOS suspend/force-quit, storage pressure result | Platform owner'dan iki cohort/device evidence ister; callback ekleme talep ederek sorunu kapatmaz | HELD — platform/migration/key evidence yok |
| A-P03 | O-77'i stable ID/payload digest/expected generation/actor-session-device metadata ile tek local transaction'da yaz; local note ile authority-sensitive claim'i ayır | contracts/operations/envelope-v1; local/outbox/operations; local/history/evidence; local/provenance/pending | OP_PENDING_LOCAL; user'a local saved/pending gösterilir; claim accepted/owned/provenance verified gösterilmez; app kill sonrası aynı ID okunur | Durable-before-label proof, privacy/classification fields, operation state enum, no local-final assertion, accessibility labels | Product/data owner'a state copy ve conflict policy onayı; unknown alanı azaltmak için anlam değiştirmez | HELD — exact contract ve UI/a11y evidence eksik |
| A-P04 | API submit ve status lookup'ı ayır; timeout/lost response'ta O-77 OUTCOME_UNKNOWN; retry yalnız same operation ID/idempotency key; response order bağımsız | api/operations/submit; api/operations/status; reconcile/idempotency; local/outbox/attempts; audit/operation-events | OP_SUBMITTED → OP_OUTCOME_UNKNOWN → RECONCILING; server status doğrulamazsa new operation yok; duplicate replay aynı outcome'a bağlanır | Lost-response injection, same-ID retry, server accepted-before-timeout versus rejected/conflict cases, audit ordering | API owner'dan idempotency/status/conditional-version contract ister; request replay ile duplicate düzeltmez | HELD — custom API semantics ve authority evidence açık |
| A-P05 | Recall floor ve provenance conflict'i ayrı plane'lerde tut; R-12 geldiğinde cached P0/accepted response active positive authority yapma; C-55 iki source ve audit ile HELD | api/recall/floor; local/authority/recall-floor; local/conflict/provenance; api/operations/conflict; audit/source-history | RECALL_KNOWN_STOP + PROVENANCE_CONFLICT/HELD; O-77 confirmed accepted olsa bile recalled content kullanılmaz; history silinmez/yeniden yazılmaz; resolution sonrası authoritative revalidation | Server generation/event ordering, tombstone/floor anti-resurrection, two-source conflict view, no LWW, safe-stop copy and a11y | Safety/provenance reviewer'dan rule/quorum/exit evidence ister; owner'a manuel DB resolution görevi vermez | HELD — high-consequence human/authority rule ve real recall testleri açık |
| A-P06 | 150 MB media'yı package core ve O-77'den ayır; 25 MB üzeri cellular transfer için explicit consent gate; consent yokken queue başlamaz | media/manifest/on-demand; transfer/network-policy; ui/media-consent-state; cache/eviction-policy | MEDIA_BLOCKED_CELLULAR_CONSENT; compact core P0 kullanılabilir (recall yoksa), media absent/paused; Wi-Fi/user choice sonrası yeni bounded transfer; cache pressure active package/ops evict etmez | Size preview, metered/expensive/constrained policy, pause/cancel, no-auto-retry, 250 MB pressure and 2 GB negative scope | Product owner'a wording/consent policy ve Wi-Fi acceptance ister; cellular'ı otomatik açmaz | HELD — device/network/accessibility and cache evidence yok |
| A-P07 | Restore, key unavailable, schema migration/update, clock anomaly ve uninstall/reinstall'i explicit states yap; no positive authority from restored backup; Android then iOS plan | restore/quarantine; migration/version-check; key/state; platform/android; platform/ios; release/compatibility | SAFE_STOP veya RECONCILING; restore quarantine, no resurrection of R-12/delete/accepted floor; migration fail ise last valid package/ops korunur; wall clock freshness authority değil | Backup/restore/uninstall, key invalidation/rekey, interrupted migration, old/new release, TalkBack/VoiceOver state matrix | Release/platform owner'dan device/cohort/real restore evidence ister; migration error'ı owner debug'ına devretmez | HELD — highest-risk platform/restore evidence açık |
| A-P08 | A-specific traceability, API boundary, dependency/cost/exit and reviewer separation dossier üret; no code; no winner | evidence/TASK-SIM-OFFSYNC-001/A; review/independent; runbook/recovery; exit/export/manifest | EVID-01..12 complete; missing proof explicitly HELD; any unsafe shortcut REJECT; no final winner | Independent data/safety, platform, migration/security, API reviewer sign-off; documentary vs real-device tags | Owner yalnız evidence budget/capacity ve continue/hold kararı verir; Drift schema/provider debugging yapmaz | HELD — documentary operation possible, production/ADR gate açık |

### 7.3 A için aynı fixture'ın beklenen state walk

1. E0'da A'nın promoted package table'ı P0/G0, staging table boş veya ayrı; media row
   absent/blocked; O-77 yoktur.
2. E1'de downloader yeni object/staging record'a yaklaşık 6 MB yazar. Process veya network kesintisi
   staging'i tamamlamaz; promoted pointer P0/G0'dan dönmez.
3. E2'de D1 manifest'i G-1 tabanını iddia eder. A'nın comparator'ı exact base mismatch üretir;
   delta apply transaction'a girmez; cursor G0'dan ilerlemez; bounded full compact package reissue
   veya quarantine state yazılır.
4. E3'te process kill olunca onPause/onStop varsayılmaz. Restart, last committed package pointer,
   staging result ve outbox transaction'ını yeniden okur. Son commit yoksa yalnız previous state
   görünür; staged P1 current olmaz.
5. E4'te O-77 local DB transaction'da operation envelope + pending row + payload digest ile durability
   kazanır. Kullanıcıya “cihazda kaydedildi/bekliyor” denir; “ownership doğrulandı” veya “server kabul
   etti” denmez.
6. E5'te API response kaybolunca A, O-77'yi OUTCOME_UNKNOWN yapar. Retry aynı stable ID ile
   idempotent status/replay ister; yeni O-78 üretilmez. Server accepted-before-timeout ise status
   bunu ayırır; otherwise RECONCILING sürer.
7. E6'da R-12 recall floor ve C-55 conflict aynı reconcile batch'ine gelirse recall safe-stop
   kazanır; provenance iki source olarak HELD/CONFLICT kalır. Server kabulü doğrulansa dahi recalled
   content'in active positive use'ı yoktur.
8. E7'de 150 MB media transfer planner 25 MB cellular gate'i görür, consent yoksa request üretmez.
   Media absent/blocked erişilebilir biçimde gösterilir; compact P0 veya local O-77, media'nın
   başlaması için zorunlu kılınmaz.
9. E8'de A full bounded package/status lookup/review ile toparlanır. Unknown, key, migration,
   restore veya conflict çözülmemişse HELD; owner'ın local DB'yi elle düzeltmesi recovery değildir.

### 7.4 A reviewer'ın otomatik failure örnekleri

- Drift transaction'ı yalnız UI state'te gösteriyor ve process kill sonrası O-77 kayboluyorsa REJECT.
- D1 için “G0'a en yakın delta” uygulanıyor, P1 veya karışık rows current oluyorsa REJECT.
- Lost response'ta yeni operation ID oluşturuluyor veya duplicate replay idempotency kanıtı yoksa REJECT.
- R-12 yalnız push/background callback'i ile işleniyor veya offline cached positive gösteriliyorsa REJECT.
- C-55 last-write-wins ile diğer source'u siliyorsa REJECT.
- 150 MB media user consent olmadan cellular queue'ya giriyorsa REJECT.
- Restore edilmiş local flag, server recall/delete/accepted floor'u yeniden canlandırıyorsa REJECT.
- Accessibility evidence yalnız screenshot/renk veya snackbar ise HELD; durum semantiği yoksa REJECT.

## 8. B — PowerSync adayının ortak task simülasyonu

### 8.1 Aday sınırı

B, Flutter client'ta PowerSync benzeri local SQLite/synced tables ve upload queue, backend'de
Kavriva API/Supabase boundary'si, selective Sync Streams ve RLS/connector/config yüzeyi varsayar.
PowerSync transport/queue kolaylığı package/delta authority, recall floor, ownership/provenance
conflict, API idempotency, key lifecycle, background guarantee veya high-consequence merge policy
sağlamış sayılmaz. PowerSync service, plan, license, billing veya self-host seçimi yapılmamıştır.

### 8.2 B packet tablosu

| Packet | AI'ın B için beklenen planı | Kavramsal files/contracts touched (gerçek edit değil) | Beklenen state ve recovery | Reviewer evidence | Owner action | Mevcut disposition |
|---|---|---|---|---|---|---|
| B-P01 | Sync Stream'in selective rows'ını P1 package manifest/digest ile karıştırma; %50 download staged kalır; D1 wrong-base'i Kavriva contract'ı exact reject eder | sync/streams/package-scope; sync/manifest/delta-contract; local/synced/package; local/staging/checkpoint; api/package/reissue | PACKAGE_CURRENT(G0) + staged/failed P1; D1 DELTA_REJECTED_WRONG_BASE; stream reprocess/filtered rows P0'ı atomik olarak geçersiz kılamaz; full bounded reissue | Stream filter vs package manifest matrix, base/target generation, digest and cursor, partial promote negative test, no “stream is truth” claim | Sync/API owner'dan stream/package equivalence ve reissue evidence ister; dashboard cursor elle ileri aldırmaz | HELD — stream semantics, wrong-base and service evidence açık |
| B-P02 | Local synced table ile upload queue transaction sınırını ayır; process kill sonrası accepted server row varsayma; SDK/plugin lifecycle callback'ini commit sayma | client/synced-schema; client/upload-queue; contracts/local-state; platform/android; platform/ios | PROCESS_RESTARTED; P0 G0 ve durable O-77/queue state korunur; incomplete queue row blocked/retryable; FIFO blockage active package'i bozmaz | Atomic local write, FIFO queue/crash recovery, Android/iOS suspend/force-quit, storage pressure, migration and plugin generated surface | Platform owner'dan generated/native and lifecycle evidence ister; PowerSync queue'yı blind authority olarak kabul etmez | HELD — queue/plugin/real-device evidence açık |
| B-P03 | O-77 upload entry'sine stable op ID/payload fingerprint/expected version ekle; PowerSync upload success'i server domain acceptance ile eşitleme | client/upload/operation-envelope; api/upload/validation; api/operation/status; audit/idempotency | OP_PENDING_LOCAL → OP_SUBMITTED; local queue accepted değil; server validation/conditional version sonucu explicit; upload error FIFO'yu bloke ederse visible blocked/held | Same-ID retry, queue error/dead-letter/2xx validation, status lookup, operation audit; no hidden provider retry | API owner'dan upload endpoint/status/validation contract ister; queue item'ını silerek çözmez | HELD — backend idempotency and FIFO failure proof yok |
| B-P04 | Response loss'ta provider queue retry ile domain duplicate'i ayır; O-77 UNKNOWN ve same-ID status/replay; network reconnect order bağımsız | api/operation-idempotency; client/upload/attempts; sync/reconnect; audit/operation-status | OP_OUTCOME_UNKNOWN → RECONCILING; duplicate retry same ID; accepted/rejected/conflict status server'dan gelir; FIFO blocked ise new blind operation yok | Lost response injection, 2xx-but-domain-error case, late response, concurrent delete/update, reconnect gap, same-ID proof | Bounded API/ops owner'dan idempotency and dead-letter runbook ister; provider queue'yu temizlemeyi recovery saymaz | HELD — PowerSync upload contract alone insufficient |
| B-P05 | RLS/stream mirror'ını recall authority sayma; R-12 tombstone/floor and C-55 conflict server/API contract'ında; stream reprocess sonrası local wipe/quarantine | server/rls-vs-stream-matrix; server/recall-tombstone-floor; sync/reprocess; client/conflict/provenance; api/authority | RECALL_KNOWN_STOP + PROVENANCE_CONFLICT/HELD; RLS row visible olsa bile recall floor wins; accepted upload recalled contenti yeniden positive yapamaz; no LWW | RLS vs stream filter equivalence, tombstone propagation, old-client quarantine, reprocess/local wipe, two-source conflict audit | Data/safety owner'dan negative floor and conflict resolution evidence ister; RLS policy tweak ile safety issue'yu kapatmaz | HELD — provider stream + domain authority evidence açık |
| B-P06 | PowerSync partial sync'i 150 MB object media transferi sayma; media ayrı transfer planner/consent state; 25 MB cellular gate user choice olmadan geçilmez | sync/core-package; media/object-transfer; network/consent-policy; client/media-state; cache/eviction | MEDIA_BLOCKED_CELLULAR_CONSENT; core package/media absent ayrımı; no queue auto-start; 250 MB pressure active synced rows/O-77'yi silmez; Wi-Fi consent sonrası resumable ayrı task | Stream/media separation, size preview, metered/Low Data/expensive path, pause/cancel, no 2 GB scope, accessibility | Product/network owner'dan consent text and cache policy evidence ister; plan/cost dashboard'ı consent yerine koymaz | HELD — media/SDK/network/accessibility evidence yok |
| B-P07 | PowerSync config/version/license/restore/key/migration and Android/iOS differences explicit; restored synced state revalidated against server floor | config/capability/release; restore/quarantine; migration/compatibility; platform/android; platform/ios; key/state | SAFE_STOP/RECONCILING; old stream/client/package cannot positive authority; recall/delete/accepted floor resurrect edilmez; update/migration/key failure preserves last safe state | Service outage/deactivation/soft-limit, self-host/restore/rebuild/exit, key invalidation, interrupted migration, real Android/iOS/a11y | Owner'dan provider capacity/exit and platform evidence kararı ister; plan/license or console failure debug etmez | HELD — service/exit/native/restore evidence açık |
| B-P08 | B-specific dependency and equivalence dossier: stream, queue, RLS, API boundary, billing/exit; no code/no winner | evidence/TASK-SIM-OFFSYNC-001/B; review/provider-neutral; runbook/outage; exit/export/manifest | EVID-01..12 complete; missing stream/authority/real-device proof HELD; unsafe shortcut REJECT; no ranking | Independent data/safety, stream/RLS, platform/migration, cost/exit reviewers; documentary vs real tags | Owner only selects evidence funding/capacity and continue/hold; vendor console/queue debugging yapmaz | HELD — documentary model possible, provider/ADR gate açık |

### 8.3 B için aynı fixture'ın beklenen state walk

1. E0'da B'nin local synced projection'ında P0/G0 görünür; Sync Stream bunu taşıyor olsa bile package
   manifest, digest, recall floor ve eligibility contract ayrıca mevcut kabul edilir. Media absent ve
   cellular consent kapalıdır.
2. E1'de stream/transfer yaklaşık 6 MB'de kesilir. B, synced table veya stream checkpoint'i P1'i
   complete/current sayamaz; P0/G0 active kalır. Queue/stream retry package promotion değildir.
3. E2'de D1'in declared base G-1'i local package G0 ile eşleşmez. Stream row convergence, D1'i
   “en yakın” hale getiremez; Kavriva API/package validator reject eder; G0 cursor veya floor yanlış
   yöne hareket etmez; full bounded reissue istenir.
4. E3'te process kill/suspend/FIFO interruption sonrası local SQLite ve upload queue'nun hangi
   transaction'da kaldığı belirlenir. Provider callback olmadan P0 ve O-77'nin durable state'i
   okunur; queue success server domain acceptance değildir.
5. E4'te O-77 upload queue'ya stable ID ile alınır, local saved/pending görünür. Stream'in local row
   göstermesi ownership/provenance claim'i kanıtlamaz.
6. E5'te lost response, provider retry ve API retry birbirinden ayrılır. O-77 OUTCOME_UNKNOWN,
   same-ID status/replay; FIFO queue duplicate veya dead-letter handling'i explicit değilse
   RECONCILING/HELD kalır. New operation ID üretilmez.
7. E6'da R-12 yalnız RLS/Sync Stream filter değişikliği değildir; server negative floor/tombstone
   ve C-55 provenance conflict, local synced projection üstüne uygulanır. Stream reprocess gecikirse
   bile cached positive active authority değildir; two-source conflict HELD.
8. E7'de PowerSync selective sync'in media transferi olmadığı açıkça kayda girer. 150 MB media
   25 MB cellular gate ve no-consent nedeniyle blocked; queue/background bunu otomatik açmaz.
9. E8'de B status lookup, recall reprocess, bounded package reissue ve conflict review ile toparlanır.
   Service outage, soft limit, stream gap, RLS mismatch, key/migration/restore bilinmiyorsa HELD;
   vendor console manipulation recovery değildir.

### 8.4 B reviewer'ın otomatik failure örnekleri

- Sync Stream'de row görünmesini package digest/eligibility/recall authority sayıyorsa REJECT.
- Stream checkpoint'i veya FIFO queue P1 partial'ını current yapıyor, D1 wrong-base'i merge ediyorsa REJECT.
- PowerSync upload success'i Kavriva domain operation acceptance sayıyor veya 2xx validation error'ı
  görünmez kılıyorsa REJECT.
- Response kaybında provider retry yeni domain operation yaratıyor veya idempotency proof yoksa REJECT.
- RLS/stream filter'i recall/tombstone floor yerine koyuyor, C-55'i LWW ile siliyorsa REJECT.
- Media selective sync ile 150 MB transferi consent'siz cellular başlatıyorsa REJECT.
- Service outage/deactivation/soft-limit durumunda UI last-known accepted/eligible gösterip negative
  revalidation yapmıyorsa HELD veya güvenlik etkisi varsa REJECT.
- Provider console, service-role veya owner canlı queue/database debug'ı recovery olarak sunuluyorsa REJECT.

## 9. Eşitlik kontrolü: A ve B aynı testte neyi kanıtlamak zorunda

| Kontrol alanı | A Drift/custom | B PowerSync | Ortak eşik |
|---|---|---|---|
| Package integrity | App-owned manifest/staging/promote | Stream + package manifest ayrımı | P1 partial active olamaz; digest/generation zorunlu |
| Wrong-base delta | Custom exact comparator | Stream convergence'i override etmeyen API validator | D1 reject; closest-base/karışık merge yok |
| Durable local work | Local DB transaction/outbox | Synced table + upload queue transaction | Process kill sonrası O-77 kaybolmaz; local saved ≠ accepted |
| Lost response | API idempotency/status contract | Provider queue + API idempotency/status contract | UNKNOWN; same ID; blind retry/new duplicate yok |
| Recall | API floor/tombstone | API floor + stream/RLS reprocess | Negative authority wins; anti-resurrection |
| Provenance conflict | App/API conflict table | API conflict table; stream yalnız delivery | Two sources korunur; high-consequence LWW yok |
| Media/cellular | Separate planner/gate | Stream dışı object transfer/gate | 150 MB consent'siz başlamaz; 250 MB fixture limit değil |
| Platform | Drift transaction + Flutter/native surfaces | Provider/generated/native surfaces + Flutter | Android ve iOS gerçek evidence; callback correctness değildir |
| Restore/migration/key | App-owned quarantine/migration | Local sync schema/config + quarantine | Restore positive authority vermez; failure-safe migration/key |
| Accessibility | App state labels | App + provider state mapping | Pending/unknown/held/conflict/blocked erişilebilir |
| Cost/exit | Custom owner/ops burden | Service/plan/license/exit burden | Cost/capacity/exit açık; hiçbir sayı benchmark değildir |
| Disposition | HELD | HELD | No winner; ADR gate kapalı |

İki adaydan biri common state veya evidence alanını “provider zaten hallediyor” diye çıkarırsa eşitlik
bozulur ve ilgili aday REJECT olur. Diğer adayın daha fazla kavramsal dosyaya sahip olması tek başına
failure değildir; önemli olan her contract'ın owner'ı, reviewer'ı ve recovery'sinin görünür olmasıdır.

## 10. Reviewer ve owner iş bölümü

Her aday için en az şu ayrım korunur:

- AI implementer: bounded packet planını ve state/evidence sözleşmesini yazar; kod veya canlı debug yapmaz.
- Independent data/safety reviewer: recall floor, provenance conflict, operation truth, anti-resurrection,
  safe-stop ve no-LWW kontrolünü yapar.
- Platform reviewer: Android process/storage/backup/network/accessibility ve iOS lifecycle/backup/key/
  accessibility/force-quit farklarını gerçek kanıt planına bağlar.
- Candidate reviewer: A'da custom transaction/API/migration yüzeyini; B'de stream/queue/RLS/config/
  service/exit yüzeyini kontrol eder. Provider veya framework kendi kanıtı olarak tek başına kabul edilmez.
- Machine/evidence validator: fixture ID, event order, generation/digest, state transition ve required
  fields eksik mi bakar; visual demo'yu semantic truth saymaz.
- Owner: evidence bütçesi, device cohort, reviewer kapasitesi ve continue/hold/reject kararı verir.
  Owner implementer, SQL/queue debugger, service console operator veya conflict çözücüsü değildir.

Owner action'ı şu formatta kapanır:

1. Kanıt eksikliği ve risk state'i,
2. Kanıtı üretecek role ve platform/cohort,
3. Gerekli artifact ve exit condition,
4. PASS/HELD/REJECT kararı.

“Owner bunu cihazda elle düzeltir”, “provider dashboard'dan cursor ileri alınır”, “user tekrar
göndersin”, “en son yazan kazansın” veya “callback gelince tamamlandı say” owner action değildir;
ilgili durum REJECT'tir.

## 11. Simülasyon sonucu

### 11.1 A — Drift/custom

- No-code plan operable in principle: bounded package/delta, local durable operation ve API boundary'si
  açıkça modellenebilir.
- Current disposition: HELD FOR EVIDENCE.
- Hold nedenleri: custom generation/tombstone/recall floor, idempotency/status, transaction/process
  death, migration/key/restore, Android/iOS parity, accessibility ve real-device evidence henüz
  kapanmamıştır. Drift adı bu boşlukları kapatmaz.
- Reject trigger: P1/D1/local O-77/recall/conflict/media'dan herhangi birinin yukarıdaki common state
  sözleşmesini ihlal etmesi.

### 11.2 B — PowerSync

- No-code plan operable in principle: selective sync/local queue transport yüzeyi, API boundary ve
  ayrı authority contracts ile modellenebilir.
- Current disposition: HELD FOR EVIDENCE.
- Hold nedenleri: stream/package eşdeğerliği, FIFO/lost-response/idempotency, RLS/stream/recall
  mirror, service outage/soft-limit/license/exit, migration/key/restore, Android/iOS parity,
  accessibility ve real-device evidence henüz kapanmamıştır. PowerSync adı bu boşlukları kapatmaz.
- Reject trigger: provider queue/stream/2xx/RLS/local row, common state yerine geçirilir veya
  recall/conflict/consent/restore/duplicate sınırı ihlal edilir.

### 11.3 Winner kararı yok

Bu simulation iki finalist için aynı bounded AI task, aynı fixture, aynı state lattice ve aynı evidence
contract'ını üretmiştir. Her iki aday da belgesel düzeyde güvenli bir recovery şekli tarif edebilir;
her ikisi de gerçek platform, authority, migration/key, accessibility, cost/exit ve restore kanıtı
beklediği için bu dosyanın current sonucu HELD'dir. Bu, A'nın seçildiği, B'nin seçildiği veya
bir benchmark yapıldığı anlamına gelmez. DEBATE-009 ADR/purchase/implementation kapısı açık kalır.

## 12. Kapanış ve sonraki kanıt sınırı

Bu task ancak aynı fixture gerçek Android-first ve iOS-later lane'lerinde, DEC-0031 cohort yöntemiyle,
MPR-01..18 ve requirements synthesis EQ/OSR maddeleriyle ayrı ayrı kanıtlanırsa sonraki review'e taşınır.
Özellikle şu iddialar bu no-code simulation'dan çıkarılamaz:

- belirli bir OS'nin background task'ı belirli sürede çalıştıracağı;
- process kill, force-quit, reboot, storage pressure veya power loss sonrası tüm write'ların geri geleceği;
- backup/restore'un güncel recall/ownership/provenance/accepted-operation truth taşıdığı;
- seçilen provider'ın package digest, anti-rollback, idempotency, conflict veya accessibility'i otomatik kapattığı;
- 12/150/25/250 MB'nin production quota, SLA veya product limit olduğu;
- A veya B'nin production winner olduğu.

Eksik olan her kanıt HELD olarak kalır; bilinmeyen state olumlu authority'ye çevrilmez. Güvenli sınırı
taşıyamayan aday REJECT edilir ve diğer adayın puanı ile telafi edilmez.
