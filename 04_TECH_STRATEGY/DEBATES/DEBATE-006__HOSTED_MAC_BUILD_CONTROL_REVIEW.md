# DEBATE-006 — HOSTED MAC BUILD CONTROL REVIEW

Status: `DRAFT / ADVERSARIAL CONTROL INPUT / PROVIDER-INDEPENDENT / NO-CODE`
Date: 2026-09-18
Decision level: Phase-4 Flutter vs React Native + Expo tie-break input only; not an ADR

## 1. Amaç ve sınır

Bu kayıt, Android-first / iOS-later yayın sırasının ileride bir hosted macOS build/CI yoluna ihtiyaç duyması halinde
hangi kontrol kanıtlarının kapanması gerektiğini tanımlar. Amaç bir build sağlayıcısı seçmek, fiyat önermek veya bir
framework'ü şimdiden kazanan ilan etmek değildir. Aynı kontrol paketi Flutter ve React Native + Expo development-build
adaylarına eşit uygulanmalıdır.

Bu belge:

- uygulama kodu, prototip, proof-of-concept, executable spike veya signed build üretmez;
- hosted build, CI, macOS erişimi, Apple/Google hesapları veya başka bir ücretli hizmet satın alma yetkisi vermez;
- herhangi bir sağlayıcının güvenli, ucuz, erişilebilir veya kalıcı olduğunu varsaymaz;
- güncel değişken hosted-build/CI fiyatı, kota, vergi, kur, retention veya SLA rakamı uydurmaz;
- Apple/Google store ücretlerinin `DEC-0030` ve `DEC-0032` kapsamındaki ayrı onayını hosted hizmet onayına çevirmez;
- framework, provider, OTA kanalı veya Gate 4 -> 5 kararı vermez.

Sonuçların dili `PASS`, `HELD` veya `REJECT` olmalıdır. Bir kontrolün resmi kaydı, plan sayfası veya reklamda bulunmaması
`PASS` değildir. Kritik bilgi eksikse `HELD`; önerilen yol açıkça güvensiz, geri döndürülemez veya sınırsız maliyetli ise
`REJECT` kullanılır.

## 2. Bağlayıcı bağlam ve sabitler

| Konu | Repository'de doğrulanmış bağlam | Bu incelemedeki kontrol etkisi |
|---|---|---|
| Yayın sırası | `DEC-0032`: Android yayınlanır ve stabilize edilir; iOS ikinci aşamadır; eşzamanlı yayın zorunlu değildir. | Hosted Mac gideri ve iOS build bağımlılığı Android başlangıcına sessizce yüklenemez. iOS yolu kapanmamışsa iOS yayın kapısı `HELD` kalır; Android kanıtı geçersiz sayılmaz. |
| Doğrudan cihaz | Sahipte kontrol edilen bir Android telefon var. | Android-first için doğrudan gerçek-cihaz, signing ve store kanıtı hazırlanabilir; hosted Mac bunun önkoşulu değildir. |
| iPhone erişimi | Yakın arkadaşlardan iPhone ödünç alma yolu var; kalıcı/garantili erişim henüz yok. | Ödünç cihaz yardımcı kanıttır; iOS release için dört kohortun ve erişim takviminin tamamı kanıtlanmadan kapı kapanmaz. |
| Mac erişimi | Sahip olunan veya güvenilir biçimde erişilen Mac henüz doğrulanmadı. | Local iOS recovery bugün `UNRESOLVED`'dır. Hosted yol ancak provider-bağımsız export ve recovery kanıtı ile değerlendirilebilir. |
| Harcama zarfı | `DEC-0032`: harcama başladığında store dışı tekrar eden maliyet için yaklaşık `TRY 2.000–3.000/ay` planlama tavanı; bu hemen satın alma izni değildir. | Tüm hosted/CI ve diğer recurring satırlar bu tavanla, resmi güncel fiyat ve kötü senaryo ile karşılaştırılmalıdır. Tavanın aşılması otomatik tier/overage ile gizlenemez. |
| Store ücretleri | `DEC-0030`: Apple Developer Program ve Google Play Console release maliyetleri sahibi tarafından onaylı, zamanlaması ertelenmiş zorunlu maliyetlerdir. | Store ücretleri hosted provider bütçesi sayılmaz; ancak daha sonra tek tabloda birleştirilirse resmi güncel değer, vergi ve kur ayrıca gösterilir. |
| Ortak fixture | `DEC-0031` ve `COMMON_FIXTURE`: Android API 29 constrained, Android 13+ main, iOS 16.4-capable oldest-end ve current standard non-Pro iPhone; dört kohort, S1–S15, 24 aylık horizon. | Hosted route yalnızca bir cihazı, simulator'ı veya kısa bir demo yolunu kanıt olarak kullanamaz. |
| Release integrity | `DEC-0027`: exact immutable artifact promotion, provenance/SBOM, signing/release graph; OTA code delivery onaylı değildir. | Hosted servis artifact üreten yardımcıdır; runtime kodu, kaynak gerçekliği veya safety authority değildir. |
| AI işletim modeli | `DEC-0028`/`DEC-0029`: nontechnical owner, AI-operated çalışma; implementer/reviewer/validator ayrımı; kullanıcı build debug/repair yapmaz. | UI-only, gizli state'li veya kullanıcının manuel tamirine dayanan bir yol `PASS` olamaz. |

Bu tablo kararları yeniden yorumlamaz; yalnızca hosted-build kontrolüne taşır. `COMMON_FIXTURE`'daki 12 MB compact
paket, 150 MB optional media, 250 MB cache, cihaz/ağ/kesinti/restore profilleri ve S1–S15 koşulları aynen korunur.

## 3. Tanımlar ve adversarial model

Bu belge sağlayıcıdan bağımsız konuşmak için `H` (hosted macOS/build route), `L` (local macOS/build route), `S`
(Apple/Google store authority) ve `R` (repository/canonical evidence custody) kısaltmalarını kullanır. `H`, belirli bir
ürün adı değildir; macOS runner, hosted CI, remote Mac veya bunların bileşimi olabilir.

İnceleme, iyi niyetli normal akışın yanında şu saldırgan/başarısız durumları zorunlu kabul eder:

- provider hesabı, worker, cache, destek personeli veya entegrasyon token'ı ele geçirilir;
- build logu, hata çıktısı, artifact, debug symbol, generated native proje veya cache kaynak/secrets sızdırır;
- Apple/Google credential'ı build, upload ve publish yetkilerini aynı anda taşır;
- provider yanlış veya eski signing identity ile build eder; kullanıcı bunu artifact adından fark edemez;
- macOS/Xcode/SDK, dependency, config-plugin veya generated dosya provider'da görünmeyen bir varsayımla değişir;
- sağlayıcı kesilir, hesabı kilitlenir, kota dolar, queue uzar, plan değişir veya servis kapanır;
- free/trial plan otomatik ücretli tier'a geçer; minute, parallelism, storage, egress veya retry overage'i faturalandırır;
- kur, KDV/VAT, kart komisyonu, bölgesel vergi veya fiyat değişikliği TRY tavanını görünmeden aşar;
- ödünç iPhone zamanında bulunmaz, doğru OS/modeli taşımaz veya TestFlight erişimi süreli/kişisel hesaplara bağlıdır;
- restore edilmiş provider ayarı, cache veya device backup güncel signing, entitlement, entitlement/recall veya safety
  authority gibi yanlış kabul edilir;
- AI eksik kanıtı tamamlanmış sayar ya da kullanıcıdan teknik hata ayıklama ve build onarımı ister.

Bu tehditlerden biri için kanıtın yalnızca sağlayıcının kendi ekranında bulunması bağımsız doğrulama sayılmaz. `R` dışında
korunan bir kopya, kontrolün kaynağı olamaz.

## 4. Durum ve karar kuralları

Her satırda şu alanlar doldurulmalıdır: kontrol durumu, kanıt URI/digest'i, kanıt tarihi, sorumlu aktör, fallback, maliyet
ve açık varsayımlar. Dinamik bir plan sayfası `snapshot` olarak saklanmadan final kanıt sayılmaz.

| Durum | Anlam |
|---|---|
| `PASS` | Resmi/bağımsız kanıt, Kavriva release walkthrough'u ve sonraki gerçek-cihaz kabul planı birlikte tamam. |
| `HELD` | Kanıt, owner kapasitesi, resmi fiyat/kota, device/AT erişimi, signer custody veya local/exit yolu eksik. Release/route bu konu kapanana kadar bekler. |
| `REJECT` | Yol OTA code delivery'ye, açıkça sınırsız harcamaya, plaintext key/source sızıntısına, kayıp kullanıcı truth'una, bilinmeyen signing identity'ye veya owner debug yüküne dayanıyor ve makul fallback yok. |
| `N/A` | Yalnızca bu kontrollü kapsamın dışında kalan yol için; kritik bir kontrolü saklamak için kullanılamaz. |

Bir hosted sağlayıcının yokluğu tek başına framework `REJECT` değildir: Android-first devam edebilir; iOS release,
kanıt veya hosted route `HELD` kalabilir. Buna karşılık seçilen framework'ün provider olmadan local/portable bir recovery
boundary'si kurulamayacağı gösterilirse framework tie-break'inde kritik koşul ve gerekirse `REJECT` adayıdır.

## 5. Adversarial kontrol listesi

Her kontrol Flutter ve React Native + Expo için aynı şablonla doldurulmalıdır. `Minimum evidence` varmış gibi yazılmaz;
Phase 4'te eksik olanlar `HELD` olarak işaretlenir. Aşağıdaki kutular, sonraki controlled no-code closure exercise için
kontrol adımlarıdır.

### 5.1 Apple/Google identity, credentials ve signing keys

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-A01 | Apple legal owner hesabı ile H'nin teknik build hesabı ayrılmış mı? Provider çalışanı, AI veya kullanıcı yerine legal owner gibi davranıyor mu? | Account/Team ID sahipliği, erişim rolü, owner'ın yapacağı dış adımlar ve audit izi; secret değeri değil. | S sahipliği veya rolü belirsizse `HELD`; impersonation varsa `REJECT`. |
| [ ] HCB-A02 | Google Play Console/App Integrity/Play signing sahipliği build servisine devredilmeden yürütülebiliyor mu? | App/package ownership, upload-vs-store-signing ayrımı, account recovery ve owner action runbook'u. | Signing authority belirsizse `HELD`; provider hesabı tek otorite ise `REJECT` adayı. |
| [ ] HCB-A03 | Apple certificate, provisioning profile, App Store Connect API credential ve Google credential'larının her biri ayrı kapsam, environment ve süre ile tanımlı mı? | Credential inventory: purpose, scope, issuer, environment, expiry, revocation path, last-use audit. | Inventory/expiry/revocation yoksa `HELD`. |
| [ ] HCB-A04 | Build, sign, upload, publish, emergency pause ve content approval ayrı yetkiler mi? | İşlem-credential matrisi; build job'unun store publish edemediğini ve content authority'ye erişemediğini gösteren policy. | Tek token tüm işleri yapıyorsa `HELD`; güvenli ayrım mümkün değilse `REJECT`. |
| [ ] HCB-A05 | Private signing key H'ye aktarılıyorsa nerede, ne kadar süreyle, kim tarafından ve hangi iz ile kullanılıyor? Managed signing varsa anahtarın custody/recovery/rotation sınırı açık mı? | Key custody threat assessment, ephemeral-use/zeroization, export prohibition veya güvenli recovery prosedürü; secret içermeyen evidence. | Custody veya recovery belirsizse `HELD`; plaintext kalıcı key/cache varsa `REJECT`. |
| [ ] HCB-A06 | Android upload key ile platformun app-signing authority'si; iOS distribution key/profile ile App Store authority'si ayrıştırılmış mı? | Key-role map, fingerprint/Team ID/bundle/package identity ve artifact binding. | Yanlış key ile release riski varsa `HELD`; unknown signer artifact'i `REJECT`. |
| [ ] HCB-A07 | Pull request/fork/preview build'leri production signing secret'larına erişemiyor mu? | Job trust-boundary, branch/environment policy, secret redaction ve negative test planı. | Untrusted source'a prod secret veriliyorsa `REJECT`. |
| [ ] HCB-A08 | Build servisinin repository, dependency registry, artifact store ve store API erişimleri minimum yetkili mi? | Read/write/approve/publish matrix, service-account separation, session/step-up ve audit evidence. | Broad admin token veya shared personal account varsa `HELD`; azaltılamıyorsa `REJECT`. |
| [ ] HCB-A09 | Credential/key kaybı, yanlış kullanımı, provider employee/support erişimi ve hesap devri için revocation yolu var mı? | Incident runbook, revoke confirmation, owner notification, new-key rollout ve affected-artifact impact graph. | Sadece provider ticket'ına bağlıysa `HELD`; revoke edilemiyorsa `REJECT`. |
| [ ] HCB-A10 | Rotation sırasında eski ve yeni key/profile/certificate ile güvenli geçiş ve gerektiğinde forward recovery var mı? | Secret-rotation rehearsal planı; old/new artifact identity; store compatibility ve rollback-refusal kuralları. | Rotation release'i kilitliyor veya veri kaybettiriyorsa `HELD`. |
| [ ] HCB-A11 | Apple/Google credential'ları AI prompt'una, repository'ye, screenshot'a, ticket'a veya generated log'a girmiyor mu? | Redacted evidence scan, secret-handling rule, log-mask policy ve AI context boundary. | Raw secret görünüyorsa `REJECT`; şüpheli geçmişte rotation gerekir. |
| [ ] HCB-A12 | Store submission/publish owner kararı gerektirdiğinde H bunu otomatik olarak tamamlanmış release diye işaretlemiyor mu? | Human approval checkpoint, exact artifact digest, submission receipt ve `outcome unknown` reconciliation kuralı. | Otomatik/kanıtsız publish authority varsa `HELD`; owner impersonation varsa `REJECT`. |

### 5.2 Least privilege, source exposure, artifact ve log custody

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-B01 | H'ye hangi source gönderiliyor: checkout, submodule, generated native output, dependency cache, symbols veya test data? | Transfer manifest; production user/private note/photo verisinin build input'u olmadığını gösteren veri sınıflandırması. | Source/data sınırı belirsizse `HELD`. |
| [ ] HCB-B02 | Source, dependency ve secrets transit/at-rest koruması; region, replica, support access ve provider personnel erişimi açık mı? | Resmi güvenlik/retention/region/employee-access terms snapshot'ı ve risk değerlendirmesi. | Resmi şartlar bulunamıyorsa `HELD`; kalıcı uncontrolled exposure varsa `REJECT`. |
| [ ] HCB-B03 | Provider logları secret, token, source path, private URL, signing metadata veya user data sızdırmıyor mu? | Redaction rule, negative log fixtures, support bundle policy ve sample sanitized log. | Secret-bearing logs `REJECT`; yalnızca belirsizlik `HELD`. |
| [ ] HCB-B04 | Worker workspace, cache, temp file, debug symbol ve failed-build archive ne zaman siliniyor; silme doğrulanabiliyor mu? | Retention/deletion event, cache scope/tenant isolation, legal hold ve provider export/delete evidence. | Retention/deletion bilinmiyorsa `HELD`. |
| [ ] HCB-B05 | Artifact ve log retention provider hesabından bağımsız canonical custody'ye aktarılıyor mu? | `R`'de immutable artifact digest, manifest, log snapshot, SBOM/provenance, approval ve export receipt. | Tek kopya H'de ise `HELD`; export mümkün değilse `REJECT` adayı. |
| [ ] HCB-B06 | Artifact tam olarak hangi commit, dependency lock, generated/native output, SDK/toolchain, config, entitlement ve signing identity'den üretildi? | Build manifest ve provenance graph; Android/iOS artifact identity ayrı. | Input closure yoksa `HELD`; unknown artifact promotion `REJECT`. |
| [ ] HCB-B07 | Artifact digest/signature, SBOM ve verification kaydı bağımsız verifier tarafından kontrol edilebiliyor mu? | Provider dışı digest/SBOM/provenance doğrulaması ve mismatch sonucu. | Bağımsız doğrulama yoksa `HELD`. |
| [ ] HCB-B08 | Debug symbols, mapping dosyaları, build logs ve TestFlight/Play evidence user/private data içermiyor mu? | Data-minimization and redaction checklist; retention owner; user-data-free test fixture. | Production/private data kullanılıyorsa `REJECT`; kapsam belirsizse `HELD`. |
| [ ] HCB-B09 | H'nin destek/diagnostic erişimi audited, time-bounded ve minimum kapsamlı mı? | Support access trail, approval/expiry/revocation, no-secret policy. | Unbounded support access varsa `HELD`; kontrol edilemiyorsa `REJECT`. |
| [ ] HCB-B10 | Provider'ın terms'i source'u AI training, resale, public index veya başka tenant ile paylaşmayı engelliyor mu? | Güncel resmi terms/privacy/DPA snapshot'ı; değişiklik bildirimi ve exit etkisi. | Resmi cevap yoksa `HELD`; yasaklanamıyorsa `REJECT`. |
| [ ] HCB-B11 | Artifact, log ve evidence export'unda provider UI'ına veya ücretli bulk-export'a mahkûmiyet var mı? | Makinece okunabilir API/CLI veya tarifeli export yolu; export limit/egress ve test receipt. | UI-only veya sınırsız ek ücret ise `HELD`; export yoksa `REJECT`. |
| [ ] HCB-B12 | Approval/release/suspension/audit olayları H'nin değiştirilebilir activity log'undan ayrı korunuyor mu? | Protected audit event, actor, operation identity, timestamp, artifact digest ve reconciliation record. | H'nin activity ekranı tek audit ise `HELD`. |

### 5.3 Exportability, local recovery, outage ve vendor lock-in

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-C01 | H olmadan aynı release input setiyle temiz bir local veya alternatif macOS ortamı kurulabilir mi? | Provider-agnostic recipe; exact SDK/Xcode/macOS/Gradle/Android SDK/JDK/dependency/toolchain snapshot; clean-restore walkthrough. | Bugün Mac yoksa bu açıkça `UNRESOLVED`; iOS route `HELD`, kullanıcıdan build tamiri istenemez. |
| [ ] HCB-C02 | H'ye özgü workflow DSL, hidden environment variable, opaque cache veya dashboard state olmadan build intent repository'de okunabiliyor mu? | Versioned workflow/config, environment manifest, generated-file policy ve provider-neutral interpretation. | Hidden state varsa `HELD`; çıkışta yeniden kurulamıyorsa `REJECT`. |
| [ ] HCB-C03 | Flutter plugin/platform-channel veya RN/Expo config-plugin/prebuild/generated-native sınırı export içinde görünür mü? | Candidate-specific generated diff, native file inventory, dependency lock/hash, rebuild trigger ve owner map. | Native/generated closure eksikse `HELD`. |
| [ ] HCB-C04 | Export kapsamı şunları içeriyor mu: source ref, lockfiles, dependency hashes, toolchain, workflow, generated output, config/entitlements, artifact, SBOM, provenance, test/evidence, approvals ve store metadata? | Export manifest ve clean extraction index; secret değerleri export edilmez, key continuity/recovery referansı export edilir. | Bir kritik sınıf yoksa `HELD`; artifact/input export edilemiyorsa `REJECT` adayı. |
| [ ] HCB-C05 | Export periyodik olarak okunabilir ve restore edilebilir mi; yalnızca “download” düğmesi var mı? | Restore drill planı, digest comparison, missing-file report, evidence of provider-independent read. | Restore denenmemişse `HELD`. |
| [ ] HCB-C06 | Provider outage/account lock/quota exhaustion sırasında canonical artifact, Android-first yolu ve güvenli hold davranışı korunuyor mu? | Outage runbook; last-known-good artifact; owner notification; Android local/alternative route; iOS hold semantics. | Tek provider ile devam mümkün değilse iOS `HELD`; unsafe bypass varsa `REJECT`. |
| [ ] HCB-C07 | Provider status page/SLA var olsa bile, sözleşme dışı uzun kesinti ve provider kapanışı için gerçek exit yolu var mı? | Local/alternate recovery, export cadence, account recovery, termination notice and data deletion terms. | Yalnızca SLA'ya güveniliyorsa `HELD`; fallback yoksa `REJECT` adayı. |
| [ ] HCB-C08 | Provider planı/terms'i, region, account owner veya API değiştiğinde migration için yeterli süre ve kanıt bırakıyor mu? | Change-notice policy, versioned export, no silent plan migration, dependency/toolchain map. | Değişiklikte canonical evidence kayboluyorsa `HELD`. |
| [ ] HCB-C09 | Store'da yayımlanmış last-known-good artifact, H'nin yeniden build etmesine bağlı olmadan yeniden sunulabilir veya pause edilebilir mi? | Exact digest, store release mapping, promotion/pause runbook, owner authority. | Only rebuild can restore release ise `HELD`. |
| [ ] HCB-C10 | Framework/provider değişiminde veri, history/provenance, media, offline fixture, key/account continuity ve acceptance oracle hayatta kalıyor mu? | Framework-exit dossier; portable schemas/exports; forward migration and parallel-client plan. | User truth loss or silent overwrite risk varsa `REJECT`. |
| [ ] HCB-C11 | Data migration irreversible ise binary rollback yerine forward recovery ve visible partial/unknown state var mı? | Migration evidence, old/new client/API/schema/content compatibility, rollback-refusal rule. | Binary rollback data loss yaratıyorsa `REJECT`. |
| [ ] HCB-C12 | H'nin kendi cache/remote backup'ı current entitlement, release eligibility, recall veya safety authority olarak kullanılmıyor mu? | Restore threat model; authoritative-current vs delivery-observed vs reconciled states. | Restored cache positive authority üretiyorsa `REJECT`. |
| [ ] HCB-C13 | H, OTA/runtime code update yolunu zorunlu kılıyor mu veya hosted convenience bunu örtüyor mu? | Release graph explicitly store artifact based; OTA absent/excluded. | Code OTA'ya dayanıyorsa `REJECT`; optional capability yalnızca referanssa `N/A`, tie-break avantajı sayılmaz. |
| [ ] HCB-C14 | H'de teknik birincil ve yedek işletici/AI yolu tanımlı mı; ikisi de aynı gizli state'e bağlı değil mi? | Primary/backup ownership, escalation, task pack and failure handoff. | Yedek yoksa kritik iOS release `HELD`; kullanıcı debug owner'ı olamaz. |

### 5.4 Restore ve reproducibility closure

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-D01 | Aynı commit ve lock seti, exact SDK/toolchain/config ile clean environment'ta yeniden kurulabiliyor mu? | Pinned inputs, environment digest, generated-output diff ve independent rebuild record. | Exact inputs eksikse `HELD`. |
| [ ] HCB-D02 | Signed artifact'te imza/timestamp farkını ayırarak, unsigned/package payload ve release meaning karşılaştırılabiliyor mu? | Artifact identity comparison method; signing metadata; acceptable deterministic variance policy. | Karşılaştırma yalnızca filename/CI job ID ise `HELD`. |
| [ ] HCB-D03 | Generated native project yeniden üretildiğinde beklenmeyen diff, entitlement, permission veya background-mode değişikliği görünür oluyor mu? | Prebuild/generator output snapshot, diff review, platform-specific acceptance list. | Hidden generated diff varsa `REJECT` adayı. |
| [ ] HCB-D04 | macOS/Xcode/SDK, Android SDK/AGP/Gradle/JDK, Flutter/RN/Expo ve native dependency sürümleri birlikte pinleniyor mu? | Exact version/ref/date; support/EOL/recheck trigger; no dynamic `latest`. | Dynamic latest veya support floor belirsizse `HELD`. |
| [ ] HCB-D05 | Build sonrası artifact, SBOM, provenance, log ve evidence `R`'ye aktarılmadan H job'u başarı sayılmıyor mu? | Transactional export receipt; missing artifact fail-closed. | Partial export success sayılıyorsa `HELD`. |
| [ ] HCB-D06 | Restore edilmiş ortam, yeni authority üretmeden yalnızca known-good artifact/evidence üretme veya route'u `HELD` etme sınırında mı? | Restore scenario with clock change, old client, stale cache, account reauth and revocation generation. | Restore positive authority yaratıyorsa `REJECT`. |
| [ ] HCB-D07 | Reproducibility için provider'ın kapalı compiler/cache/runner image'ına zorunlu bağımlılık açıkça görünür mü? | Image digest/base image/source availability and replacement route. | Opaque image tek yolsa `HELD`; export edilemiyorsa `REJECT` adayı. |
| [ ] HCB-D08 | Normal release, forced Apple/Google requirement change ve critical dependency abandonment sonrası hangi dosyaların/tasks/contracts/tests'in değişeceği çıkarılabiliyor mu? | Impact graph; generated/native/config/plugin edges; revalidation checklist. | Etki graph'ı yoksa `HELD`. |
| [ ] HCB-D09 | Rebuild başarısız olduğunda son güvenilir artifact'in provenance'i, store mapping'i ve safety/recall durumu korunuyor mu? | Failure/hold runbook; no automatic downgrade; impact and pause evidence. | Başarısız rebuild eski truth'u silerse `REJECT`. |
| [ ] HCB-D10 | Reproducibility iddiası gerçek cihaz/test/AT kanıtı yerine geçirilmiyor mu? | Separate documentary build evidence vs four-cohort real-device acceptance records. | Simulator/build logu device pass diye sunulursa `REJECT`. |

### 5.5 Build minutes, parallelism, overage, currency ve bütçe

Bu bölümdeki miktarlar fiyat değildir. Provider adı, güncel plan veya rakam verilmeden yalnızca hangi resmi alanların
kontrol edilmesi gerektiği kaydedilir. `UNRESOLVED` hiçbir zaman `0 TRY` anlamına gelmez.

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-E01 | Planın aylık build minutes/cycle, platform başına macOS premium hesabı, job timeout, retry/re-run ve queued-job tüketimi tanımlı mı? | Resmi güncel quota/usage definition snapshot'ı; Android ve iOS ayrı kullanım modeli. | Kota tanımı yoksa `HELD`. |
| [ ] HCB-E02 | Parallelism, concurrency, queue priority, burst, branch/PR job ve release job sınırları açık mı? | Resmi plan limitleri ve 4 planned release/year + emergency/forced-event fixture'a uygulanmış capacity sheet. | Queue/capacity belirsizse `HELD`. |
| [ ] HCB-E03 | Overage için hard cap, auto-stop, per-project budget, spend alert ve auto-upgrade kapatma var mı? | Provider policy ekranı/API'si, alert recipient, threshold, shutdown behavior ve negative test. | Uncapped charge/auto-upgrade varsa `REJECT`; yalnızca alert olup hard stop yoksa `HELD`. |
| [ ] HCB-E04 | Artifact/log storage, cache, egress, bulk-export, retention ve backup limitleri minute limitinden ayrı mı? | Quota/retention/egress table; export cost and deletion behavior. | Sadece dakika kotası biliniyorsa `HELD`. |
| [ ] HCB-E05 | Trial/free plan bitince build duruyor mu, yoksa otomatik ücretli tier/kredi/kart charge mı oluyor? | Terms snapshot, card/auto-renew/upgrade behavior, no-card or spending guard route. | Silent billing varsa `REJECT`; davranış belirsizse `HELD`. |
| [ ] HCB-E06 | Android-first dönemde iOS için bekletilen hosted usage ile Android release cadence birbirinden bütçelenmiş mi? | Staged 12/24-month worksheet: planning, Android prep, iOS prep, operations, growth; no full envelope assumption. | Staging yoksa `HELD`. |
| [ ] HCB-E07 | Provider fiyatı hangi currency, billing period, minimum commitment, seat/user, tax/VAT, regional availability, card FX/withholding ve renewal koşullarına bağlı? | Official current price page/contract snapshot, invoice sample, tax treatment and bank/FX uncertainty fields. | Herhangi biri doğrulanmamışsa amount `UNRESOLVED`; approval `HELD`. |
| [ ] HCB-E08 | TRY 2.000–3.000/ay tavanına hangi recurring ve exit satırları giriyor? | Hosted Mac/build, CI/artifact, backend/storage/backup/CDN, identity, telemetry, security/SBOM, AI, device/lab/tester, AT/safety review, support/incident ve exit satırları ayrı. | Satır atlama veya maliyeti 0 yazma varsa `HELD`. |
| [ ] HCB-E09 | Mandatory, deferrable, optional, scale-triggered ve exit/contingency maliyetleri ayrılmış mı? | DEC-0030 uyumlu cost worksheet; 1k/10k/50k MAU workload ile service vs local-device fixture ayrımı. | Kategori karışıyorsa `HELD`. |
| [ ] HCB-E10 | Hosted route yalnızca iOS preparation window'da açılabilir mi; Android-first öncesinde ücretli plan sessizce başlatılmıyor mu? | Approval trigger, expiry/renewal calendar, project pause and delete/export procedure. | Deferred cost recurring charge'a dönüşüyorsa `HELD`. |
| [ ] HCB-E11 | Official price/limit değişirse budget gate yeniden çalışıyor mu; eski fiyat screenshot'ı onay yerine geçirilmiyor mu? | Recheck date, URL/terms version, owner approval record and change-impact rule. | Dynamic price stale ise `HELD`. |
| [ ] HCB-E12 | Emergency safety/security correction için quota dolduğunda güvenli fallback veya explicit `HELD`/pause yolu var mı? | Reserved capacity policy or local/alternate recovery; no quality downgrade; incident decision record. | Overage açmak tek çözümse `HELD`; uncapped emergency charge `REJECT` adayı. |
| [ ] HCB-E13 | Currency/tax uncertainty, TRY ceiling ile aynı ayda üst üste geldiğinde hangi limit uygulanıyor? | Conservative approval rule, exchange/tax unknown row, no false conversion; store fees separately shown. | Uncertainty hidden or converted as fact ise `HELD`. |
| [ ] HCB-E14 | 24 aylık exit/migration/rebuild maliyeti hosted convenience satırından ayrı görülebiliyor mu? | Migration labor/capacity/tooling row marked `UNRESOLVED` until official evidence; owner approval trigger. | One-click exit varsayımı varsa `HELD`. |

### 5.6 iPhone, TestFlight ve borrowed-device evidence

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-F01 | iOS release için Apple Developer/App Store Connect/TestFlight account, membership, certificate/profile/API ve current Apple rules resmen doğrulanmış mı? | Release-window official documentation snapshot; owner legal action list; no guessed quota/expiry/fee. | Dinamik store/build şartı doğrulanmadıysa iOS `HELD`. |
| [ ] HCB-F02 | TestFlight artifact'ı exact commit/build number/digest, provisioning/entitlements, reviewer, device model/OS ve test result ile bağlı mı? | Machine-readable TestFlight evidence packet; install path ≠ production acceptance statement. | Binding yoksa `HELD`. |
| [ ] HCB-F03 | Dört frozen cohort'un her biri için real-device planı var mı: constrained Android, main Android, oldest-end iPhone, current standard iPhone? | Model/OS/patch/storage/network/owner/time window matrix; simulator clearly separate. | Bir cohort yoksa corresponding release gate `HELD`. |
| [ ] HCB-F04 | Ödünç iPhone'un model, OS, storage, network/SIM, camera/permission, VoiceOver, largest text, process termination ve restore senaryoları yürütülebiliyor mu? | Consent-based test log, device reset/privacy cleanup, no personal data, repeatability and observed limitation. | Cihaz koşulu bilinmiyorsa `HELD`. |
| [ ] HCB-F05 | Ödünç cihaz erişim penceresi, TestFlight invitation, build expiry/reinstall, account ownership ve scheduling ile uyumlu mu? | Calendar/availability plan, replacement device path, tester communication and privacy agreement. | Tek bir kişinin anlık yardımına bağlıysa iOS `HELD`. |
| [ ] HCB-F06 | Ödünç iPhone kalıcı release dependency yapılmadan, en az bir güvenilir iOS access/recovery planı var mı? | Owner-confirmed owned/reliably accessible Mac/iPhone veya capped/portable hosted route; fallback capacity. | Hiçbir güvenilir yol yoksa iOS release `HELD`; Android-first devam eder. |
| [ ] HCB-F07 | VoiceOver/Switch/Voice Control, largest text/reflow, focus/reading order, state announcement, contrast/non-color, reduced motion ve reduced dexterity Turkish critical flows üzerinde ayrı kanıtlanacak mı? | AT oracle + actual-device reviewer record; framework API dokümanı yalnızca prerequisite. | Simulator/API claim device evidence sayılırsa `REJECT`. |
| [ ] HCB-F08 | TestFlight dış tester/expiry/build limitleri, review/processing/availability ve current iOS support policy resmi kaynaktan release öncesi yeniden kontrol ediliyor mu? | Recheck checklist with official URL/date; no invented tester count or duration. | Current policy yoksa `HELD`. |
| [ ] HCB-F09 | iPhone evidence paketinde personal Apple ID, private photo/note, keychain veya provider secret tutulmuyor mu? | Redacted/exported evidence; data deletion and account unlink record. | Sensitive data leak `REJECT`; cleanup belirsizse `HELD`. |
| [ ] HCB-F10 | Android-first release, iOS TestFlight kanıtı gelmediğinde Android publication quality/safety gate'ini yanlış pozitif veya negatif etkilemiyor mu? | Separate platform gate, shared contract parity matrix, iOS deferred decision record. | One store's evidence other store'ye aktarılıyorsa `HELD`. |
| [ ] HCB-F11 | iOS build/signing outage veya borrowed-device cancellation, simultaneous launch baskısı yaratmadan açık `HELD` ve safe user communication üretiyor mu? | Staged-release incident runbook; no forced simultaneous publication. | Bypass/quality reduction varsa `REJECT`. |
| [ ] HCB-F12 | iOS evidence yalnızca “TestFlight'ta açıldı” değil, offline/recall/restore/permission/process-death ve safe-stop closure'ı içeriyor mu? | S1–S15 traceability; actual-device/AT evidence separated from documentary simulation. | Critical scenario missing ise `HELD`. |

### 5.7 Restore, local data ve release-state safety

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-G01 | Device backup/clone ve provider restore sonrası local checkpoint, pending photo, partial upload ve unknown physical state doğru korunuyor mu? | Restore fixtures: last durable checkpoint, temp photo, duplicate operation, corrupt package, interrupted migration. | Physical truth auto-restore ediliyorsa `REJECT`. |
| [ ] HCB-G02 | Package/client/API/schema/content/suspension generation değişiminde stale/unknown state fail-closed ve safe-stop ile görünür mü? | Compatibility matrix and foreground reconciliation rule. | Stale client positive eligibility üretirse `REJECT`. |
| [ ] HCB-G03 | Hosted artifact restore, current release/suspension authority'den ayrılmış mı; old artifact geri yüklenince yeni positive authority oluşmuyor mu? | Exact immutable artifact + current revocation check + quarantine/reconciliation evidence. | Restore backward authority üretirse `REJECT`. |
| [ ] HCB-G04 | Backup, export veya logs'ta Keystore/Keychain private key taşınmıyor; re-auth/key rotation/loss explicit mi? | Key continuity and loss/recovery contract; non-exportable secret policy. | Raw platform key export'u `REJECT`. |
| [ ] HCB-G05 | Build failure veya provider outage, kullanıcı kayıtlarını, provenance/history/correction/recall kayıtlarını veya safety closure'ı silmiyor mu? | Failure-state matrix, data-preserving forward recovery and protected audit. | Data loss/silent overwrite `REJECT`. |
| [ ] HCB-G06 | Test artifact ile production artifact, debug/staging config ve production config/entitlement karışmıyor mu? | Environment matrix; artifact labels; independent promotion identity. | Cross-environment signing/config leak `HELD`/`REJECT` (severity'e göre). |

### 5.8 AI-operability, human authority ve closure evidence

| ID | Kontrol sorusu / adversarial test | Minimum kanıt | Eksikse karar |
|---|---|---|---|
| [ ] HCB-H01 | Fresh AI, tüm repository'yi okumadan bir build/release task'ını bounded context pack ile çalıştırabilir mi? | Task purpose, allowed/forbidden scope, contracts, dependencies, generated/native edges, acceptance/negative cases, evidence output and recovery. | Whole-project context veya tribal knowledge gerekiyorsa `HELD`. |
| [ ] HCB-H02 | H'nin UI/API/CLI davranışı versioned ve deterministic enough mı; job ID dışında machine-readable manifest alınabiliyor mu? | Exact command/input/output contract, provider-neutral wrapper intent, sanitized logs. | UI-only or opaque operation `HELD`. |
| [ ] HCB-H03 | Build/signing/store/content/safety actions için implementer, independent reviewer ve validator kanıtı ayrılıyor mu? | Role/task graph and approval records; AI output self-proving değil. | Tek AI kendi build'ini onaylıyorsa `HELD`; authority bypass varsa `REJECT`. |
| [ ] HCB-H04 | AI raw logs, generated files ve provider help text'i güvenilir talimat/authority olarak kullanmıyor mu? | Untrusted-log handling, injection-safe context policy, reviewed command allowlist. | Untrusted output policy yoksa `HELD`. |
| [ ] HCB-H05 | Failed build teşhisinde AI güvenli sınıflandırma ve next owner handoff üretiyor; kullanıcıdan kod/debug/build repair istemiyor mu? | Human-readable failure packet, automatic evidence collection, escalation and stop rule. | Owner debug isteniyorsa `REJECT`. |
| [ ] HCB-H06 | Candidate-specific dependency/native/generated değişikliği Obsidian-compatible graph'ta downstream task/test/evidence'e bağlanıyor mu? | Bidirectional requirement-task-test-release links and orphan detection. | Etki görünmüyorsa `HELD`. |
| [ ] HCB-H07 | New dependency, Apple/Google requirement change, key rotation ve provider outage aynı task graph'ta tetiklenebiliyor mu? | Revalidation trigger matrix; no silent “rerun”. | Trigger/closure eksikse `HELD`. |
| [ ] HCB-H08 | AI, provider veya store hesabı sahibi/legal signer/qualified safety reviewer yerine geçirilmemiş mi? | External-authority list, owner actions and reviewer competence/independence. | Impersonation or AI-only safety evidence `REJECT`. |
| [ ] HCB-H09 | No-code tie-break exercise, gerçek build/device pass gibi sunulmadan açıkça documentary/held kalıyor mu? | Evidence labels: official docs, inference, dependency-specific, real-device acceptance, unresolved. | Documentary claim build/device pass diye sunulursa `REJECT`. |
| [ ] HCB-H10 | Independent adversarial reviewer, closure evidence'i provider reklamından ve framework tercihinden bağımsız inceleyebiliyor mu? | Review packet, finding disposition, no aggregate score override. | Independent review yoksa final recommendation `HELD`. |

## 6. Zorunlu evidence packet (provider adı vermeden)

Sonraki no-code tie-break exercise her aday için aşağıdaki aynı packet başlıklarını üretmelidir. Packet sayısı tek başına
puan değildir; gizlenmiş native/authority work açık packet'lerden daha risklidir.

1. **Identity and authority map:** Apple/Google owner, store, build, sign, upload, publish, pause, content/safety ve
   reviewer rollerinin ayrımı; legal owner'ın yapacağı dış adımlar.
2. **Credential/key custody map:** credential türü, scope, environment, expiry, rotation, revoke, audit, backup/recovery;
   private key değeri hiçbir packet'e yazılmaz.
3. **Least-privilege job map:** PR/branch, build, sign, artifact export, store submission ve emergency paths.
4. **Source/data exposure manifest:** gönderilen source/generated/dependency/test input; production/private data exclusion;
   worker/cache/support/region/retention.
5. **Build closure manifest:** exact commit, framework/runtime, lock/hash, native/generated files, SDK/toolchain, config,
   entitlement, environment ve signing identity.
6. **Artifact/provenance/SBOM packet:** Android ve iOS artifact digest'leri, SBOM, verifier, approval, promotion, store
   mapping, release/suspension generation ve sanitized logs.
7. **Export/restore packet:** makinece okunabilir export, restore receipt, missing-file report, clean environment recipe,
   local/alternate route ve framework-exit boundary.
8. **Outage/lock-in packet:** provider unavailable, quota exhausted, account lock, worker compromise, plan change ve
   termination hallerinde Android-first continuation, iOS hold, owner notice ve recovery.
9. **Rotation/incident packet:** secret/key rotation, leak, certificate expiry, dependency abandonment, forced store
   requirement change, impact graph, safe hold/pause ve forward recovery.
10. **iOS evidence packet:** TestFlight release identity, four frozen cohorts, borrowed-device limits, AT scenarios,
    network/interrupt/restore/offline/recall results ve privacy cleanup.
11. **Cost/cap packet:** official current price/plan/terms snapshot, minutes/parallelism/storage/egress, hard cap,
    overage, auto-upgrade, alert, currency/tax/FX uncertainty ve 12/24-month staged worksheet.
12. **AI task packet:** bounded context, allowed/forbidden files, contract links, native/generated boundary, failure
    behavior, reviewer/validator, evidence and no-owner-debug rule.
13. **Independent review packet:** adversarial findings, evidence provenance, critical open items and disposition.

Hosted provider UI'sındaki başarılı işareti bu packet'lerin yerini tutmaz. Packet'in canonical kopyası `R` kapsamına
aktarılmadan release readiness `PASS` sayılamaz.

## 7. Eşit Flutter vs RN + Expo tie-break exercise

Bu sıra, `DEBATE-006__TASK_SIM_MOB_001_AUDIT_AND_JUDGE.md` içindeki native-dependency/rebuild/release closure ihtiyacını
hosted-build riskleriyle birleştirir. Her adım iki adaya aynı başlangıç, aynı çıktı ve aynı `PASS/HELD/REJECT` kuralı ile
uygulanır. Phase 4 süresince uygulama çalıştırılmaz; yalnızca controlled no-code evidence planı hazırlanır.

### T0 — Ortak baseline

- Android-first, iOS-later, no simultaneous launch;
- Android sahibi doğrudan cihaz; iPhone borrowed supplementary;
- dört device cohort, S1–S15, 12 MB compact/150 MB optional/250 MB cache ve 24 aylık fixture;
- OTA yok; exact immutable artifact, provenance/SBOM, signing/release evidence;
- Mac erişimi ve hosted acceptance açık; provider seçimi yok.

### T1 — Native dependency değişimi

İsteğe bağlı photo capability dependency'si değişir veya terk edilir. Her aday şunları açmalıdır:

- dependency lock/hash, native/generated/config dosya etkisi;
- build/rebuild trigger, iOS/Android divergence ve fallback;
- source exposure, signing/artifact/provenance etkisi;
- fresh AI context pack, reviewer/validator ve replacement route;
- provider yokken local/alternate recovery ve `HELD` davranışı.

### T2 — Apple/Google build requirement değişimi

Apple ve Google build/store requirements aynı closure exercise içinde değişmiş kabul edilir; güncel ayrıntı
uydurulmaz, resmi release-window recheck görevi açılır. Kanıt:

- hangi SDK/Xcode/Gradle/AGP/JDK/framework/native/generated dosyaların etkilendiği;
- Android artifact'inin doğrudan cihaz/store evidence ile korunması;
- iOS TestFlight/signing requirement'ının dört cohort evidence'ına etkisi;
- old/new client, API/schema/content/config ve migration compatibility;
- quota/parallelism, signing rotation, provider outage ve safe pause etkisi.

### T3 — Hosted/local parity ve recovery

Her aday için H'den export alınmış varsayımsal packet, temiz L ortamı/alternatif recovery yolu ve provider outage
senaryosu karşılaştırılır. Aşağıdaki iddialar ayrı tutulur:

- aynı release meaning;
- aynı portable input closure;
- aynı artifact identity (signature/timestamp farkı açıklanmış);
- aynı real-device/AT acceptance obligation;
- aynı store owner action ve current-policy recheck;
- provider yokken Android-first release'in devamı ve iOS'un görünür `HELD` durumu.

### T4 — Borrowed-iPhone/TestFlight sınırı

Her aday, TestFlight install'ı ile actual iPhone/AT acceptance arasındaki farkı, ödünç cihazın bulunamadığı haftayı ve
kişisel verinin temizlenmesini belgelemelidir. Bir aday borrowed device'ı kalıcı release authority veya tek recovery
path'i yapamaz.

### T5 — Cost/cap closure

Her aday, provider adı ve güncel fiyat icat etmeden şu alanları doldurur: build minutes, parallelism, queue/timeout,
retry tüketimi, artifact/log/storage/egress, hard stop, alert, auto-upgrade, currency, tax/VAT, FX, renewal, export/exit
ve 12/24 aylık total. Hosted route iOS hazırlık penceresine ertelenir; Android-first aşamasında sessiz recurring charge
olmaz. `TRY 2.000–3.000/ay` tavanına sığmayan veya resmi doğrulaması olmayan route `HELD` olur.

### T6 — Independent judge record

Judge yalnızca candidate-attributable delta'yı karşılaştırır. Backend, store legal identity, qualified safety/content
review, AT, real-device ve user data obligations ortaksa framework avantajı olarak yazılmaz. Şu kontrollerden biri
critical failure ise aggregate convenience ile telafi edilemez:

- signing/source secrecy ve least privilege;
- artifact/provenance/export/local recovery;
- release/store/iPhone/AT evidence;
- reproducibility/restore/data continuity;
- bounded cost/overage/exit;
- AI task isolation ve no-owner-debug.

## 8. Resmi güncel doğrulama kuyruğu (fiyat ve limit uydurmama kuralı)

Aşağıdaki alanlar bu belgede özellikle miktarsız bırakılmıştır. Satın alma veya release öncesi resmi birincil kaynaktan,
aynı tarihte ve ilgili ülke/account planıyla doğrulanmalıdır:

| Doğrulanacak alan | Birincil doğrulama yönü | Bu belgede sonuç |
|---|---|---|
| Apple Developer Program, App Store Connect ve TestFlight membership/role/certificate/profile/API/tester/build kuralları | Apple Developer / App Store Connect / TestFlight resmi dokümanları ve owner account ekranı | Güncel ücret, limit, expiry, review/processing ve tester koşulu iddia edilmez; release-window recheck `REQUIRED`. |
| Google Play Console, Play App Signing/App Integrity, upload/publish/closed-test koşulları | Google Play resmi dokümanları ve owner account ekranı | Güncel ücret, tester, signing, review ve API limitleri iddia edilmez; release-window recheck `REQUIRED`. |
| macOS/Xcode/SDK/framework destek matrisi | Apple ve framework resmi release/support dokümanları | `latest` kabul edilmez; exact release snapshot ve EOL/support window gerekir. |
| H'nin build minutes, parallelism, queue/timeout, artifact/log/cache/egress, retention ve export limitleri | İlgili provider'ın güncel resmi pricing/limits/security/terms/API dokümanları | Provider adı ve fiyatı seçilmez; tüm parasal/kota alanları `UNRESOLVED` until verified. |
| H'nin source retention, training/use, support access, region, deletion, incident notice ve account termination koşulları | İlgili provider'ın resmi terms/privacy/security/DPA/status belgeleri | Reklam veya genel SLA yeterli değil; snapshot + independent review `REQUIRED`. |
| Currency, VAT/KDV, withholding, invoice entity, card FX fee, refund, renewal ve Turkey availability | Provider invoice/terms + gerektiğinde kart/vergilendirme kaynağı | TRY dönüşümü yapılmaz; vergi/kur belirsizliği ayrıca gösterilir. |
| Borrowed iPhone/TestFlight erişim ve reviewer kapasitesi | Owner-approved access calendar, test consent ve Apple release evidence | Erişilebilirlik kanıtı yoksa iOS gate `HELD`; cihaz satın alma varsayılmaz. |

Bu listede `REQUIRED` yazması güncel bir değerin doğrulandığı anlamına gelmez. Resmi kaynak ve tarih olmadan hiçbir
provider/build satırı `0 TRY`, `free`, `uncapped`, `unlimited`, `included` veya `guaranteed` yazılamaz.

## 9. Hard stop ve `HELD` kataloğu

### Açık disqualifier (`REJECT`)

- Hosted route production/runtime OTA code delivery'sine veya store dışı code authority'sine dayanıyor.
- Signing private key plaintext olarak repository, persistent worker/cache, log, screenshot veya AI context'e giriyor.
- Build service broad admin/store/content/safety yetkisini least privilege ile ayıramıyor.
- Artifact, input closure, provenance/SBOM veya release evidence provider hesabı dışına export edilemiyor.
- Restore/backup/cache yeni authorization, entitlement, recall veya safety authority oluşturuyor.
- Overage/auto-upgrade sınırsız charge yaratıyor ve hard stop/cap kapatılamıyor.
- Bilinmeyen signing identity veya unverified artifact store'a promotion için kullanılabiliyor.
- Kullanıcıdan build debug, signing repair, code fix veya teknik hesap devri bekleniyor.
- Simulator/TestFlight install/provider logu actual iPhone, AT, safety veya store evidence diye sunuluyor.
- Data migration binary rollback ile yeni geçerli data'yı siliyor veya history/provenance'i sessizce overwrite ediyor.

### `HELD` (kanıt kapanana kadar)

- Mac sahipliği/reliable access, hosted acceptance veya provider-independent local/alternate recovery açık.
- Current Apple/Google rules, hosted pricing/quota/retention/terms/tax/FX resmi kaynaktan doğrulanmamış.
- iPhone borrowed access window, four-cohort model/OS coverage, TestFlight invitation veya AT capacity eksik.
- Key/certificate rotation, revoke, account recovery veya incident evidence eksik.
- Exact framework/native/generated closure, lock/hash, toolchain ve restore recipe eksik.
- Artifact/log export, retention, independent verification veya canonical `R` custody denenmemiş.
- AI context pack, reviewer/validator separation, impact graph veya no-owner-debug runbook eksik.
- Cost satırı unresolved olduğu halde 0 kabul ediliyor; free route için cap/alert/export/exit kanıtı yok.

Bu `HELD` listesi iOS'un Android-first'ten sonra ertelenmesini meşru kılar; safety, privacy, accessibility veya data
continuity standardını düşürmez.

## 10. Çıktı ve açık kararlar

### Bu incelemenin mevcut sonucu

- Hosted Mac/build route: `HELD — provider, Mac access, pricing/caps, credential custody, export and local recovery open`.
- Flutter vs RN + Expo tie-break: `HELD — equal closure exercise required`.
- Android-first publication direction: `APPROVED WORKING DIRECTION` olarak kalır; bu belge değiştirmez.
- iOS second release: `PLANNED / EVIDENCE-GATED`; hosted route olmadan quality gate atlanamaz.
- Store fees: `DEC-0030` kapsamındaki owner-approved mandatory release costs; hosted/CI için blanket approval değildir.
- Non-store `TRY 2.000–3.000/ay`: later planning ceiling; current spending authorization veya provider budget değildir.
- Code/prototype/purchase/ADR/Gate 4 -> 5: `NOT AUTHORIZED`.

### Tie-break kapanmadan önce cevaplanması gereken sorular

1. Sahip olunan veya güvenilir biçimde erişilen bir Mac var mı; yoksa provider-bağımsız clean local/alternate recovery nasıl
   elde edilecek?
2. H için resmi güncel fiyat, billing period, quota, parallelism, overage hard stop, retention, export, tax/FX ve exit
   kanıtı aynı tarihte alınabiliyor mu?
3. Apple/Google legal owner credential ve signing custody, build/upload/publish/approval'dan least privilege ile ayrılıyor
   mu; rotation/revoke rehearsal nasıl kanıtlanacak?
4. Dört device cohort, TestFlight ve borrowed-iPhone scheduling/AT/safety review kapasitesi iOS hazırlık penceresinde
   gerçekten mevcut mu?
5. Flutter'ın plugin/channel/runner sınırı ile RN/Expo'nun package/config-plugin/prebuild/generated-native sınırı aynı
   artifact/provenance/export/rebuild packet'inde kapanıyor mu?
6. Fresh AI hangi bounded task pack ile build/release evidence üretecek; başarısızlıkta kullanıcıya debug işi bırakmadan hangi
   owner/backup devreye girecek?
7. Hosted route, Apple/Google store ücretleri ayrı gösterilerek 12/24 aylık mandatory/deferrable/optional/scale/exit
   tablosunda TRY tavanını hangi resmi kötü senaryoda aşar veya altında kalır?

Bu sorular cevaplanmadan `RECOMMENDABLE` veya `APPROVED` yazılamaz. Sonraki manager/Judge kaydı bu belgeye link vererek
yalnızca kanıtı kapanan satırları güncellemelidir; provider veya framework seçimi ayrı bir explicit karar/ADR sürecidir.

## 11. Kaynak ve ilişki sınırı

Bu kayıt şu bağlayıcı girdilerden türetilmiştir:

- `00_CONTROL/DECISION_LOG.md` — özellikle `DEC-0027`, `DEC-0028`, `DEC-0029`, `DEC-0030`, `DEC-0031`, `DEC-0032`;
- `00_CONTROL/CURRENT_STATE.md`, `00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md`;
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md`;
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md`;
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC.md`;
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_AUDIT_AND_JUDGE.md`;
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__FIVE_WAY_JUDGE_SYNTHESIS.md`;
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_EQUIVALENCE_AUDIT_01.md`.

Bu dosya tartışma/kanıt katmanındadır. `05_ADR/` içinde onaylanmış bir karar oluşmadan provider, framework, build
architecture, signing custody veya hosted plan seçilmiş sayılmaz.
