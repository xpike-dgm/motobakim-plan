# DEBATE-010 — KİMLİK, OTURUM, HESAP KURTARMA VE İÇ AYRICALIK GEREKSİNİMLERİ

Durum: `PHASE-4 GEREKSİNİM SENTEZİ / NO-CODE / ADR DEĞİL`
Tarih: 2026-09-18
Kapsam: Kavriva Android-first Flutter tüketici uygulaması + tarayıcı tabanlı Internal Operations + ortak API, audit ve recovery sınırı
Karar seviyesi: Repo kaynaklı gereksinim sentezi. Kimlik sağlayıcısı, giriş yöntemi, RBAC ürünü, policy engine, şema veya kod seçmez.

## 1. Yönetici özeti

Kavriva’da “kimlik” tek bir şey değildir. Bir kişinin hesabına giriş yapmış olması, onun belirli bir motosiklet alanını
görebileceği, bir teknik iddiayı değerlendirebileceği veya yüksek riskli bir iç işlemi onaylayabileceği anlamına gelmez.
Sistem en az şu anlamları ayrı tutmalıdır:

- hesabı/aktörü ve mevcut oturumu,
- hangi kapsamda hangi işlemi yapma iznini,
- teknik alan yeterliliğini ve bağımsızlığını,
- o anda geçerli politika ve güvenlik durumunu,
- gerçekleşmiş işlemin değiştirilemez geçmiş kanıtını.

Kullanıcı tarafında ilk değer, kayıt veya zorunlu üyelik duvarından önce görülebilir. Account-light/local kullanım; seçili
motosiklet, geçmiş, not ve kanıt bağlamını yerelde başlatabilir. Profil, kalıcılık, cihazlar arası devam ve işbirliği için
sonradan önerilir; profil oluşturmak ilk/core değerin ön koşulu değildir. Yerelden profile geçişte kapsam önizlemesi,
çakışma incelemesi, no-silent-loss ve no-silent-overwrite gerekir.

Internal Operations, teknik içeriğin araştırıldığı, incelendiği, onaylandığı, yayımlandığı, geri çağrıldığı ve yetkilerin
yönetildiği tarayıcı ürünüdür. Bu işlemler çevrimdışı “başarılı” sayılamaz. Tarayıcıdaki gizli düğme, önbellekteki rol,
eski sekme veya doğrudan veri tabanı isteği yetki değildir; her hassas okuma ve yazma güncel Kavriva server/API sınırında
yeniden değerlendirilir.

Kullanıcı uygulaması Android-first Flutter yönündedir; iOS ikinci yayın hattıdır. Flutter yalnız sunum katmanı değildir:
yerel veri, offline paket, operasyon günlüğü, geri çağırma, audit ve recovery anlamları Flutter widget’larına gömülmeden
taşınabilir sözleşmelerle korunmalıdır. Telefon, seçili motosiklet + seçili görev için küçük, kapalı ve doğrulanabilir paket
alır; katalog tamamı indirilmez. Offline paket positive approval, güncel recall veya sunucu kabulü değildir.

Privileged recovery eski browser oturumlarını, refresh/recovery materyallerini ve bekleyen yüksek etkili yetkilendirmeleri
geçersiz kılmalıdır. Güvenlik gerçeği doğrulanamıyorsa yüksek etkili olumlu işlem `HELD` kalır. Recovery yolu kendi başına
teknik içerik onaylayamaz veya yayımlayamaz. Küçük ekipte bağımsız yeterlilik yoksa sistem kuralları gevşetilmez; iş görünür
`HELD` durumu, gerekçe, sahip ve sonraki eylemle bekler.

Audit, yalnızca “log tutuldu” demek değildir: aktör, rol/kapsam, oturum güveni, politika sürümü, operasyon kimliği,
etkilenen sürüm, eski/yeni anlam, sonuç ve etki zinciri korunur. Normal audit ve korumalı fallback kanıtı yoksa yüksek
sonuçlu işlem uygulanmaz. Eski backup/restore; recall, revoke, deletion veya kabul edilmiş operasyonu diriltemez.

Proje tek ve teknik olmayan bir sahip tarafından AI ile işletilecektir. Sahipten SQL/SSH, build/debug, provider konsolu,
şifre/anahtar yönetimi veya olay onarımı beklenemez. AI, hukuki hesap sahibi, mağaza sahibi, yetkin teknik/safety reviewer
veya kurumsal yetkiyi taklit edemez. Uygulanabilir her AI görevi dar kapsamlı sözleşme, negatif senaryo, kimlik bilgisi sınıfı,
rollback/forward-recovery ve bağımsız inceleme kanıtı taşımalıdır.

Bu dosya bir teknoloji kararı değildir. Ama sonraki ADR ve fiziksel tasarım, aşağıdaki gereksinimlerden birini “sağlayıcı bunu
otomatik çözer” diyerek çıkaramaz.

## 2. Otorite ve kanıt haritası

| Kaynak | Bu sentez için bağlayıcı sonuç |
|---|---|
| `00_CONTROL/DECISION_LOG.md#DEC-0026` | Anlaşılır taban roller + server-authoritative scoped/contextual authorization; deny-by-default; commit-time yeniden yetkilendirme; phishing-resistant privileged auth; step-up; security epoch ile recovery/session iptali; kontrollü policy; protected audit; quarantine-first ingestion. |
| `00_CONTROL/DECISION_LOG.md#DEC-0034` | Domain başına canonical authority; Flutter ve browser client için server/API mediation; online-authoritative Internal Operations; bounded/versioned offline paket; durable operation/reconciliation; current/history/audit/object ayrımı; anti-resurrection recovery. |
| `00_CONTROL/DECISION_LOG.md#DEC-0035` | Supabase-centered fiziksel yön yalnızca Kavriva API sınırının arkasında; RLS/Storage savunma katmanı; secret/service key server-only; Internal Operations Supabase Studio değildir; object/audit/floor recovery ayrı kanıt ister. |
| `00_CONTROL/DECISION_LOG.md#DEC-0036` | Flutter’da SQLite/Drift yerel persistence yönü; ilk sürümde complete compact selected-task package; ayrı durable user-operation ledger; API üzerinden durum; delta ertelenmiş; restore/device migration quarantine; plaintext fallback yok. |
| `00_CONTROL/DECISION_LOG.md#DEC-0028` ve `PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md` | Obsidian-uyumlu graph, minimum yeterli AI context pack’i, allowed/forbidden scope, bidirectional closure, no-code task simulation ve bağımsız kanıt. |
| `00_CONTROL/DECISION_LOG.md#DEC-0029` ve `#DEC-0030` | Kullanıcı teknik olmayan product/decision owner’dır; tek sahip ve sınırlı bütçe; AI owner-debug’a dayanamaz; maliyet ve dış insan/kurum yetkisi açıkça yönetilir. |
| `00_CONTROL/DECISION_LOG.md#DEC-0032` ve `#DEC-0033` | Android-first, iOS-later yayın sırası; Flutter consumer-mobile çalışma yönü; gerçek cihaz/build/ADR kanıtı henüz yok. |
| `03_DESIGN/PROFILE_COLLABORATION_VISUAL_REFERENCES.md` (`REF-PROFILE-001`) | Profil zorunlu değildir; local value sürer; migration kapsam/çakışma incelemelidir; collaboration sınırlı, attributed ve revocable; revoke geçmiş attribution/evidence’i silmez; private content shared motorcycle’dan ayrıdır. |
| `03_DESIGN/STATE_MATRIX.md` | Offline, permission denied/revoked, profile migration conflict/rollback, collaboration revoke, stale critical content, restore ve recovery için doğrulanabilir state anlamları. |
| `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md` (`IDCO-RQ-045–051`, `IDCO-RQ-060–064`) | Audit olayları, least-privilege scoped roller, proposal/review/approval/publication ayrımı, future access revoke ile geçmişin korunması, blocked/failure/access-denied açıklığı ve erişilebilir iç workspace. |
| `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md` (`W-06`, `W-07`, `W-11`, §6–§8) | Human review/approval, controlled publish, recall/recovery, role hand-off/separation of duties, failed/partial/unknown durumları ve audit event aileleri. |
| `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md` (`WS-06`, `WS-10`, `WS-11`, `WS-12`) | Reviewer/approval, audit/change history, correction/recall ve roles/access/policy görünürlüğü; kapsamın workspace’ler arasında kaybolmaması. |
| `04_TECH_STRATEGY/DEBATES/DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md` | Kimlik doğrulama, yetki, oturum, privileged recovery, policy admin, audit, export ve AI/OCR sınırlarının ayrıntılı teknik olmayan çalışma yönü. |
| `04_TECH_STRATEGY/DEBATES/DEBATE-002__OFFLINE_SAFETY_RECALL_CLIENT_COMPATIBILITY.md` ve `DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md` | Offline eligibility bounded/fail-closed; push hint’tir; browser privileged mutation online; immutable release, guarded transition, idempotency, outcome-unknown ve bağımsız negative suspension. |
| `04_TECH_STRATEGY/DEBATES/DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS.md` ve `__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES.md` | D01–D15 truth/domain sahipliği, LB-01 API/policy’den LB-14 AI assistance’a sınırlar, S1–S36 no-code senaryoları ve anti-resurrection. |
| `04_TECH_STRATEGY/DEBATES/DEBATE-008__MANAGER_SYNTHESIS.md` | Supabase-centered çalışma yönünün yalnız API arkasında, geri döndürülebilir ve owner-debug gerektirmeyen kontrol koşullarıyla kabulü. |
| `04_TECH_STRATEGY/DEBATES/DEBATE-009__JUDGE_SYNTHESIS.md` | Drift’in yalnız local persistence olması; complete compact package + durable operation ledger + API; restore, deletion, recall ve tombstone/floor reconciliation. |

### 2.1 Bu dosyanın kanıt dili

- `BAĞLAYICI`: Kullanıcı onaylı karar veya APPROVED tasarım/gereksinimdir.
- `GEREKSİNİM`: Yukarıdaki bağlayıcı kaynaklardan aşağı akış implementasyonun mutlaka kapatması gereken davranıştır.
- `ÇIKARIM`: Birden fazla bağlayıcı sınırın birleşmesinden çıkan, teknoloji seçmeyen sonuçtur; sonraki ADR’de kanıtlanmalıdır.
- `AÇIK/HELD`: Bu belgeyle kapatılamayan provider, sayı, hukuk, staffing veya gerçek cihaz/restore kanıtıdır.

## 3. Yüzeylere göre kimlik ve yetki sınırı

| Yüzey | Kullanıcıya görünen amaç | Identity/session gereksinimi | Yetki gerçeği |
|---|---|---|---|
| Flutter consumer app — Android-first | Motosiklet bağlamı, görev, bakım, geçmiş, kanıt, safe-stop/recovery | İlk değer ve temel local value account-light başlayabilir; profile kalıcılık, cihazlar arası devam ve collaboration için sonraki geçiştir. Android ilk fiziksel kanıt hattıdır; iOS aynı domain/state sözleşmesinin sonraki lane’idir. | Yerel UI, Drift transaction, cache, push veya HTTP `2xx` canonical acceptance/approval/recall değildir. Hassas server işlemi Kavriva API üzerinden gider. |
| Browser-based Internal Operations | Research, source/provenance, draft, review, approval, release, publish, recall, audit, access/policy | Current actor + fresh session + scope + competence + independence + policy/security epoch her hassas okumada/yazmada değerlendirilir. Stale/offline sayfa read-only/non-authoritative kalır. | Approval, publication, recall/suspension, role/policy/competence/recovery ve protected audit online-authoritative’dir. Supabase Studio provider adminidir; Kavriva ürün yüzeyi değildir. |
| Kavriva server/API boundary | İki client’ın hassas işlemleri için ortak karar ve durum kapısı | Actor/session/security epoch, exact action/resource/scope/classification, expected version/generation, operation identity ve reason bağlanır. | Allow/deny/hold + açıklanabilir reason üretir; commit’te yeniden yetkilendirir; audit intent effect’ten önce korunur; kayıp cevap `OUTCOME_UNKNOWN` olur. |
| Provider/control plane | Hesap, fatura, bölge, Auth/Storage/compute veya deployment yönetimi | Provider owner, billing/legal owner, recovery contact ve workload identity product actor’dan ayrıdır. | Provider console işlemi Kavriva approval/publication/review sayılmaz; provider/account/billing/region arızası `HELD`/`ACCOUNT_HELD`/`BILLING_HELD`/`SERVICE_UNAVAILABLE` durumlarıyla yönetilir. |

## 4. Identity sözleşmesi: ayrıştırılması gereken aktörler

Aşağıdaki sınıflar aynı “user id” alanına indirgenemez. Her hassas işlemde hangi sınıfın hangi anlamda kullanıldığı kanıtlanmalıdır.

| Kimlik sınıfı | Gereken anlam | Yanlış eşitleme reddi |
|---|---|---|
| Product actor/account | Kavriva’da bir kişi/kurumun görünen aktör kimliği ve kendi geçmişi | Hesaba giriş, teknik yeterlilik veya her motosiklete erişim anlamına gelmez. |
| Local installation/device partition | Account-light kullanımda yerel bağlamın, cihazın ve pending work’ün kaynağı | Yerel kayıt otomatik olarak server hesabı, sahiplik veya official truth olamaz. |
| Authenticated session | Bir aktörün belirli cihaz/kanal/oturum güveniyle şu anki isteği | Eski token, açık browser sekmesi veya cached claim güncel yetki değildir. |
| Role/capability | Araştırma, edit, review, approval, publish, recall, audit veya access/policy gibi aday yetenek | Rol etiketi tek başına resource scope, competence, independence veya current policy değildir. |
| Competence/independence record | Reviewer/approver’ın belirli domain/motosiklet/risk kapsamındaki verilmiş, süreli ve iptal edilebilir yeterliliği | Job title, delegation veya “professional/service” etiketi teknik doğruluk garantisi değildir. |
| Delegation/grant | Belirli action/scope/reason/issuer/start/expiry için izlenebilir geçici yetki | Self-delegation, nested/transitive delegation, competence kopyalama veya classification bypass yapılamaz. |
| Workload/service identity | Package builder, relay, worker veya sınırlı non-interactive işin kimliği | Service account insan onaylayıcısı, reviewer veya product actor yerine geçemez. |
| Provider/control-plane identity | Supabase organization/project, billing, domain, IdP, storage, key veya deployment sahibi | Provider admin, Kavriva safety approver/publisher/auditor olarak otomatik tanınamaz. |
| Legal/external authority | Mağaza sahipliği, hukuki hesap, qualified safety/domain attestation gibi AI’nin taklit edemeyeceği insan/kurum | AI veya yerel kullanıcı bu dış otoriteyi sessizce temsil edemez. |
| Audit subject | İşlemi yapan veya denenen işlemin effective actor/workload kimliği | Audit event’i sonradan aktör değiştirerek geçmişi yeniden yazamaz. |

Her canonical object için en az stable identity/type, scope, classification, current state/reason, version/generation,
provenance/dependency, actor/role/operation links, freshness/eligibility ve historical-use ilişkisi korunmalıdır.
Bu gereksinim `DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS.md` §4.2–§4.4 ve D13 domain’iyle kanıtlanır.

## 5. Repo kaynaklı gereksinimler

### 5.1 Account-light, profile geçişi ve tüketici kimliği

1. **İlk değer profile bağlı olamaz.** Known-task, symptom-first veya record-first değer account/permission zorlamasından önce gösterilebilmelidir (`03_DESIGN/SCREEN_CATALOG.md`, `SCR-001`; `OPEN_QUESTIONS.md`, Q-0041).
2. **Local core value korunur.** Profil; persistence/continuity, cihazlar arası devam ve collaboration için açıkça açıklanan bir sonraki adımdır; coercive sign-up wall değildir (`REF-PROFILE-001`, K01).
3. **Yerel iş official truth değildir.** Account-light active work, history, notes, evidence metadata ve pending upload yerelde dayanıklı tutulabilir; server kabulü değildir (`DEBATE-007` §8.4; `DEBATE-009` Judge).
4. **Profile migration bir güvenlik/kimlik işlemi olarak ele alınır.** Taşınacak kapsam, kaynak, actor, kullanılan guide/release, event order, private/shared classification, duplicate ve conflict önceden gösterilir. Target accepted/reconciled olmadan local source silinemez veya local kayıt profile’ın official claim’i sayılamaz.
5. **Silent merge yoktur.** Local ve server event’leri çakışırsa iki tarafın anlamı, provenance’i ve operation ID’si korunur; `CONFLICT`/`HELD` ve inceleme yolu görünürdür. Last-write-wins critical history/provenance/ownership için yasaktır.
6. **İptal ve başarısızlık değer kaybı gibi gösterilemez.** Kullanıcı migration’ı iptal ederse veya işlem kısmi kalırsa yerel state kullanılabilir kalır; partial target success olarak sunulmaz (`SCR-007`, `STATE_MATRIX.md`).
7. **Device loss gerçekçi anlatılır.** Server’a ulaşmamış local-only iş kaybolabilir/held olabilir; ürün server completion uyduramaz. Restore/reinstall/device replacement yeni sahibi veya entitlement’ı sessizce miras alamaz.
8. **Profil hesabı destek ve erişim tercihlerinin ön koşulu değildir.** Language, units ve accessibility desteği profile/account creation’a bağlanamaz (`REF-PROFILE-001`, `SOURCE_OF_TRUTH.md`).

### 5.2 Android-first Flutter consumer app

1. Flutter consumer-mobile çalışma yönüdür; Android ilk yayın/gerçek cihaz lane’idir, iOS ikinci lane’dir. Bu, production
   readiness veya Phase-5 ADR kanıtı değildir (`DEC-0032`, `DEC-0033`, `DEBATE-006__FINAL_TIEBREAK_JUDGE.md`).
2. Domain truth, auth/session, offline package, operation ledger, revocation and recovery Flutter presentation code içine
   gömülmez. Flutter/native/plugin/generated state etkileri ayrı, izlenebilir ve geri döndürülebilir task/contracts olarak
   kapatılır.
3. Android’de geçirilen bir lifecycle, encryption, process-death, accessibility veya background kanıtı iOS’a otomatik
   taşınmaz. iOS lane’i daha sonra aynı platform-neutral state/identity contract’ı ve kendi device evidence matrisiyle
   açılır; Android-first iOS parity gate’ini kaldırmaz (`DEBATE-009` Review A, MAJ-04; `DEBATE-006` closure).
4. Store/signing identity ve developer hesabı owner’ın dış yetkisidir; AI bu hesapların sahibi gibi davranamaz. Signing,
   re-authentication, key recovery veya platform account değişimi identity/custody/release kanıtı gerektiren kontrollü
   olaylardır.

### 5.3 Tarayıcı tabanlı Internal Operations ve privileged erişim

1. Internal Operations browser-based ve online-authoritative’tir. Approval, publication, recall/suspension, role/policy,
   competence/recovery ve protected-audit mutation’ları offline tamamlanamaz (`DEBATE-002` §11; `DEBATE-007` §7.5).
2. Browser/UI role cache, hidden button, service worker, optimistic UI, direct object ID veya client-supplied scope yetki
   değildir. Her hassas request server-side current actor/session/action/object/scope/workflow/classification/consequence/
   independence ile kararlandırılır.
3. Browser mutation şu anlamları taşır: actor/session/security epoch, requested capability, exact resource/scope/classification,
   expected version/generation, operation identity, intended effect/reason. Commit’te policy, competence, independence,
   version, release and suspension/revocation generation yeniden kontrol edilir.
4. High-consequence official content için `propose/edit ≠ domain review ≠ safety/technical approval ≠ publication`.
   Bağımsız competence/staffing yoksa `HELD`; shared account, admin abuse veya emergency path self-approval değildir.
5. Product-level role families en az şunları ayırır: research/contribution, editorial/data preparation, domain review,
   safety/technical approval, release/publication operation, emergency suspension, quality/operations analysis,
   audit/investigation, access/policy administration ve community moderation. Düşük riskli kombinasyonlar ve exact role
   matrix ayrıca kararlaştırılacaktır.
6. Policy, role/group mapping, competence ve privileged recovery high-consequence controlled objects’tir. Material change
   için distinct author/independent approver/activator, explicit effective time, impact simulation, pending-work recheck,
   protected audit ve controlled rollback gerekir. Admin “superuser” yolu üründe olumlu yetki üretmez.
7. Export ayrı bir capability/disclosure event’idir. Ekranı görme yetkisi export, private evidence erişimi veya audit export
   yetkisi sayılmaz; scope/field/recipient/purpose preview ve gereken step-up/independent approval gerekir.
8. Upload/URL materyali quarantine-first’tir. Scan, parse, render, OCR veya AI extraction yalnız processing/proposal state’i
   üretir; teknik doğruluk, official evidence, approval veya publication yetkisi vermez.

### 5.4 Authentication, session ve step-up

1. Normal authentication yalnız account/session claim’ini kanıtlar; teknik competence, motorcycle scope veya approval
   yetkisi kanıtlamaz (`DEBATE-004` §4.1).
2. Privileged approval, publication, emergency suspension, access administration, audit/export veya quarantine-release
   authority phishing-resistant authentication gerektirir. Exact authenticator/provider daha sonra seçilir.
3. High-consequence action transaction-bound fresh step-up/re-authentication ister. Step-up yapılmış olsa bile server current
   policy, scope, version, independence ve security epoch’i tekrar kontrol eder.
4. Session’lar server-side revocable, explicit inactivity/absolute bounds’lu ve rotation’lıdır; numeric durations açık
   karardır. Operator active session’ları görebilir/sonlandırabilir; compromise response tüm session’ları iptal edebilir.
5. Browser storage reusable long-lived authority taşımamalıdır. Trusted origins, CSRF/cross-site request protection ve
   transaction binding gereklidir.
6. Stale/offline Internal Operations page read-only/non-authoritative’dir; approval/publish/recall/role/audit mutation
   kuyruğa atılarak başarı sayılamaz. Offline draft desteği ayrıca karar gerektirir.
7. Network timeout success/failure tahmini değildir. Aynı operation identity ile status lookup ve reconciliation gerekir;
   blind duplicate submit yasaktır.

### 5.5 Hesap kurtarma, privileged recovery ve revoke

1. Privileged recovery bir “şifre sıfırla ve devam et” kısayolu değildir; açık bir güvenlik state transition’dır.
2. Recovery, account/session security epoch’i artırır; tüm relying-party browser session’larını, refresh/recovery
   artifact’lerini ve bekleyen high-consequence transaction authorization’larını iptal eder.
3. Recovery sonrası fresh phishing-resistant authentication ve transaction-bound step-up gerekir. Owner/security bağımsız
   notification’ı ve post-event review’ü alır.
4. Help-desk/last-admin recovery dual-control veya separately governed, time-bounded break-glass yoludur. Recovery kendi
   başına approve/publish/unsuspend/replacement technical truth üretemez.
5. Revocation state authoritative olarak okunamıyorsa privileged positive action fail-closed `HELD` olur; eski session’ın
   çalışmaya devam etmesine güvenilmez.
6. Role/delegation revoke yeni istekleri hemen deny/hold eder; açık session, queued/in-flight sensitive operation commit’te
   invalid olur veya yeniden yetkilendirilir. Atıf, audit, evidence, historical meaning ve sahipliği yapılan iş korunur.
7. Delegation exact capability/scope/reason/approver/start/expiry ile sınırlıdır; issuer’ın competence’ini kopyalayamaz,
   self/nested/transitive delegation yapamaz, classification/SoD aşamaz.
8. Recovery factor, legal account owner, provider/control-plane owner ve product actor ayrıdır. AI bunlardan birinin yerine
   geçmez. Kayıp factor veya provider account lock güvenli recovery planı yoksa `ACCOUNT_HELD`/`SERVICE_UNAVAILABLE` olur;
   owner’a teknik repair görevi atanmaz.

### 5.6 Shared motorcycle, collaboration ve private data

1. Shared motorcycle erişimi explicit invitation/permission ve motorcycle/scope sınırı taşır. Owner, invited helper/service/
   collaborator’dan ayrılır.
2. Helper/service/contributor action’ları kendi actor kimliğiyle kaydedilir; bu roller technical verification veya official
   truth authority’si vermez.
3. Collaborator revoke gelecekteki erişim/aksiyonları durdurur; önceki attribution, evidence, history ve audit silinmez.
4. Private/personal content shared motorcycle context’ten ayrıdır. Private/shared/community/official classification her
   derivative, export, AI/OCR, package, backup ve audit reference’a restrictive olarak taşınır.
5. Shared ownership/transfer, profile migration, entitlement change veya device restore sırasında pending operation actor,
   device, motorcycle, exact scope, entitlement/security generation ve used release ile bağlanır. Mismatch silent attach değil
   `CONFLICT`/`HELD`/reconciliation sonucudur.
6. Community publication/moderation/withdrawal official technical verification değildir. Withdrawal, dependent claim/review
   açabilir fakat independent history/provenance’ı sessizce silmez.

### 5.7 Offline, operation ledger ve API sınırı

1. Offline content package yalnız selected motorcycle/model-year/resolved variant + selected task + exact release/client
   capability + reachable physical states için hazırlanır. Full library/catalog veya unrelated motorcycle indirilmez.
2. Compact package; fit/version/status, text/steps, critical warnings/checks, outcome states ve complete task-specific
   safe-stop/recovery closure taşır. Essential media ancak güvenli anlama zorunluysa pakete girer; high-volume media ayrı,
   explicit, cancelable ve evictable’dır.
3. Package immutable generation/manifest/dependency closure/digest/compatibility ve anti-rollback koşullarıyla atomik kabul
   edilir. Partial, mixed, wrong-base veya corrupt package reddedilir; son geçerli complete package korunur.
4. Freshness expired, fit/readiness unresolved, critical status unknown, recall/suspension known veya client capability
   missing ise normal new/next physical application fail-closed/hold olur. Teaching, history, evidence capture ve safe
   recovery representable olduğu ölçüde açık kalır.
5. Push/Realtime/background callback yalnız re-check hint’tir. Foreground/network return/resume/new application ve gerekli
   high-consequence boundary’de API reconciliation yapılır. Local clock, cache, queue empty, push receipt veya HTTP success
   current eligibility/recall/acceptance kanıtı değildir.
6. User-owned history, notes, evidence metadata ve pending uploads ayrı durable operation ledger’da tutulur. En az stable
   operation ID, actor/device/context, payload fingerprint, expected version/generation, used release, status ve reason taşır.
7. Operation durumları görünürdür: `PENDING/SUBMITTED/ACCEPTED/CONFLICT/HELD/FAILED/OUTCOME_UNKNOWN/RECONCILING`.
   Response loss yeni operation ile tekrar edilmez; aynı identity status lookup/replay kullanılır.
8. Flutter/browser genel canonical database veya object-storage authority taşımaz. High-consequence write/read/export ve
   tüm server submission Kavriva API’den geçer. RLS/Storage policy defense-in-depth’tir; API authority’sinin yerine geçmez.

### 5.8 Audit, history, revoke ve restore anti-resurrection

1. Current state, domain history/provenance ve protected audit üç ayrı anlamdır. Current view event history’yi silemez veya
   history’yi current truth gibi gösteremez.
2. Audit en az authentication/recovery/session/step-up, access grant/deny/revoke, sensitive read/export, draft/edit/review/
   approval/publication/rollback/recall/restore, failed/partial/unknown ve emergency/break-glass denemelerini kapsar.
3. Her material event actor/workload, effective role/scope, session assurance/security epoch, server time + ordered
   sequence, operation ID, object/version/state, reason, policy/grant/competence version, old/new meaning, result ve
   impact/recovery owner’ı taşımalıdır.
4. High-consequence effect’ten önce minimum protected evidence durable olmalıdır. Normal sink ve protected fallback yoksa
   normal action `HELD`; emergency exception varsa ayrı quarantine/reconciliation ve `OUTCOME_UNKNOWN` kurallarıyla çalışır.
5. Audit custody ordinary publisher/admin’den bağımsız yeterlilikte, append-only/tamper-evident ve restore edilebilir olmalı;
   audit retrieval/redaction/retention/export da audit edilmelidir. Audit, authorization’ın yerine geçmez.
6. Restore/failover otomatik authority değildir. Restore state `RESTORE_QUARANTINE` olur; latest release/suspension/revocation
   floor, security epoch, role/policy/competence, audit continuity, object/media manifest, deletion/withdrawal tombstones ve
   accepted-operation ledger uzlaştırılmadan positive eligibility veya normal publish başlamaz.
7. Non-restorable monotonic floor; revoke, recall/suspension, deletion/retention, security epoch, accepted operation ve
   migration generation’ın eski backup ile geriye alınmasını engeller.
8. Cross-plane restore/export database/history, user work/media, release/package, identity/policy, protected audit,
   object bytes, configuration/migration/outbox ve key references için consistency manifest + clean-room import evidence
   ister. “Backup başarılı” veya “dosya export edildi” yeterli kanıt değildir.
9. Delete/export ayrı scope, classification, recipient/purpose ve legal-hold kararlarıdır. Link revoke daha sonraki online
   erişimi durdurabilir; indirilmiş/kopyalanmış/forward edilmiş veriyi geri alamaz ve bu disclosure olarak audit edilir.

### 5.9 AI ile uygulanabilir görev sözleşmesi

Kimlik ve recovery gibi yüksek etkili alanlarda “AI bunu halleder” bir kabul kriteri değildir. Her uygulanabilir görev için
minimum context pack şu alanları taşımalıdır (`DEC-0028`, `DEBATE-007` §15, `DEBATE-006 TASK-SIM`):

1. tek ölçülebilir amaç ve kullanıcı sonucu;
2. requirement/decision/design/state source yolları ve hangi boundary/contract’ın uygulandığı;
3. ön koşul/dependency ve graph’ta `depends_on/used_by/implements/tasks/tests/evidence` bağları;
4. izinli path/module ve forbidden scope; API boundary, audit, identity veya secret alanını sessizce genişletme yasağı;
5. actor/session/role/competence/delegation/generation state transition’ları ve public result states;
6. allow/deny/hold, stale/revoked, timeout/outcome-unknown, duplicate, conflict, restore ve rollback negatif senaryoları;
7. credential class (insan, workload, read-only, step-up gerektiren vb.), secret/key’in repo/log/browser/AI context’ine
   girmeyeceği açık kural;
8. idempotent operation identity, payload fingerprint, expected version/generation ve status-lookup sözleşmesi;
9. migration/rollback/forward-recovery/data protection ve anti-resurrection koşulu;
10. çalıştırılacak validation/architecture/traceability kontrolleri, expected evidence ve handoff biçimi;
11. implementer, independent reviewer ve evidence validator ayrımı; yüksek etkili görevde implementer kendi sonucunu tek
    başına doğru sayamaz;
12. plain-language owner output: `HELD`, `OUTCOME_UNKNOWN`, `ACCESS_DENIED`, `RECONCILING`, `SERVICE_UNAVAILABLE`,
    `BILLING_HELD`, `KEY_UNAVAILABLE`, `RESTORE_QUARANTINE` gibi state’lerde ne oldu, kim çözer ve sonraki güvenli adım.

Kimlik alanı için önerilen task dilimleri — henüz `TASK-xxx` kaydı değildir — actor/session contract, contextual authorization
decision tuple, privileged session/security epoch, account recovery/break-glass, protected audit/fallback, account-light
migration, collaboration revoke, API operation/result lookup, offline package eligibility ve provider/control-plane recovery
olarak ayrı kanıtlanabilir işler halinde tutulmalıdır. Hiçbir dilim doğrudan provider superuser, service key, billing account,
SQL/SSH veya high-consequence approval credential’i istememelidir.

## 6. Açık bırakılması gereken kararlar

Bu sentez aşağıdakileri çözmez; sonraki Phase-4/Phase-5 çalışmasında açık, owner’ı ve kanıt eşiği belirtilmiş halde taşır:

- exact identity provider/auth composition; email/phone/passkey/social/other login policy;
- consumer account-light local identity’nin profile hesabına bağlanma ve unlink/merge sınırları;
- session inactivity/absolute/refresh/rotation/re-auth sayıları ve token/cookie storage biçimi;
- phishing-resistant authenticator, step-up UX ve recovery factor/key custody;
- exact role/capability matrix, low-risk role combinations, reviewer competence issuer/recertification ve quorum;
- emergency negative authority’nin failure-domain, break-glass, single-actor exception ve notification ayrıntıları;
- protected audit custody, fallback storage, retention/privacy/legal hold ve investigation access;
- local encryption mechanism, key provisioning/rotation/revocation/recovery; plaintext fallback yasaktır ama mekanizma açıktır;
- final API runtime, RLS/Storage mapping, object-capability transport, scanner/quarantine and provider exit;
- exact freshness/offline windows, risk taxonomy, client support window, package/cache/media limits;
- profile/shared motorcycle merge, transfer, deletion, entitlement ve collaboration role semantics’in ayrıntılı policy’si;
- legal account owner, billing/recovery contact, store identity ve qualified technical/safety authority’nin insan/kurum modeli;
- exact staged cost, caps/overage, incident/restore/exit budget and support/escalation path.

Bir açık karar pozitif authority’yi güvenle doğrulamıyorsa sonuç `HELD/UNVERIFIED` olur; sessiz varsayım veya kullanıcıya teknik
onarım görevi atanmaz.

## 7. DEBATE-010 kabul kriterleri

Aşağıdaki kriterler sonraki strateji/ADR adayının bu sentezi kapattığını gösterecek minimum barıdır. Kriterler teknoloji seçmez;
her biri no-code walkthrough, contract/fixture veya daha sonra uygun gerçek evidence ile kanıtlanır.

| ID | Kabul kriteri | Beklenen kanıt / red sinyali |
|---|---|---|
| AC-ID-01 | Authenticated session, product role, scope, competence ve independence birbirinden ayrıdır. | Role/capability/competence matrisi ve actor örnekleri; “giriş yaptı = onaylayabilir” red. |
| AC-ID-02 | Hassas API isteği client rolüne/hidden button’a değil current server context’ine göre allow/deny/hold döner. | Direct API/object-ID, cached-role ve stale-scope negative walkthrough; UI gizlemek tek başına kanıt sayılmaz. |
| AC-ID-03 | Internal Operations’ın approval, publish, recall/suspend, role/policy, recovery ve protected-audit mutation’ları online current authorization ister. | Offline/stale tab senaryosu `READ_ONLY` + `HELD/DENY`; local optimistic success red. |
| AC-ID-04 | Commit anında actor/session security epoch, policy/grant version, resource version/generation, consequence ve independence yeniden kontrol edilir. | Role revoke/policy change/two-tab race; eski sayfanın side effect üretmemesi. |
| AC-ID-05 | High-consequence privileged action fresh phishing-resistant auth ve transaction-bound step-up ister. | Approval/publish/export/privilege-change/emergency senaryosunda step-up yoksa deny/hold; auth başarıyor ama competence yoksa yine deny/hold. |
| AC-ID-06 | Privileged recovery security epoch’i artırır; mevcut session/refresh/recovery artifact’leri ve pending high-consequence authority’yi iptal eder. | Eski session ve bekleyen operation denemesi; yeni fresh auth + step-up olmadan olumlu etki yok. |
| AC-ID-07 | Recovery/break-glass pozitif technical truth veya publish yetkisi vermez; revocation state belirsizse normal olumlu action fail-closed olur. | Dual-control/time-bound path, independent notification/review ve audit; “last admin bypass” red. |
| AC-ID-08 | Role/policy/grant/competence material değişikliği versioned, attributable, testable, author/approver/activator ayrımlı ve pending work için recheck’lidir. | Self-grant, nested delegation, provider admin escalation negative matrix. |
| AC-ID-09 | High-consequence proposal/review/approval/publication ayrıdır; bağımsız competence yoksa `HELD` olur. | Small-team scenario; shared account veya emergency path ile self-approval red. |
| AC-ID-10 | Product actor, workload/service, provider-control-plane, billing/legal owner ve recovery contact ayrıdır. | Identity ownership/failure-domain matrix; provider console action’ı Kavriva approval sayılmaz. |
| AC-ID-11 | Her mutation durable operation identity, exact scope/payload fingerprint, expected version/generation ve result lookup taşır. | Lost response aynı ID ile `OUTCOME_UNKNOWN`→reconcile; blind duplicate veya changed-payload reuse red. |
| AC-ID-12 | Protected audit effect’ten önce veya eşdeğer güvenceyle durur; normal + fallback custody yoksa high-consequence action `HELD` kalır. | Başarılı/denied/failed/partial/unknown/recovery olaylarında actor, role/scope, session epoch, server order, old/new, reason, result ve impact zinciri. |
| AC-ID-13 | Revocation gelecekteki authority’yi durdurur, geçmiş attribution/evidence/history/audit’i silmez. | Internal role revoke ve shared motorcycle collaborator revoke; future deny + historical read/provenance preserved. |
| AC-ID-14 | Account-light→profile migration kapsamı ve classification’ı gösterir; local source accepted/reconciled olana kadar korunur. | Duplicate/conflict/partial/failure/cancel walkthrough; no-silent-loss/no-silent-overwrite. |
| AC-ID-15 | Shared motorcycle pending work owner/actor/device/motorcycle/scope/entitlement generation ve used release ile bağlanır. | Revoke/transfer/downgrade/restore race; yanlış profile’a silent attach red. |
| AC-ID-16 | Flutter offline package selected motorcycle/task ile sınırlı, immutable generation’lı ve tüm reachable safety/application/safe-stop/recovery durumlarını kapatır. | Manifest/dependency/digest/compatibility; partial/mixed/wrong-base package red; full-library default red. |
| AC-ID-17 | Offline content, local write, queue empty, push/Realtime veya HTTP success current eligibility, recall veya server acceptance değildir. | Missed recall, stale client, unsupported field, clock change, process death ve foreground reconciliation walkthrough. |
| AC-ID-18 | User history/notes/evidence/pending uploads ayrı durable operation ledger’da görünür state’ler taşır; critical conflict LWW ile çözülmez. | `PENDING/SUBMITTED/ACCEPTED/CONFLICT/HELD/FAILED/OUTCOME_UNKNOWN/RECONCILING`; API idempotency/status lookup kanıtı. |
| AC-ID-19 | Restore/device migration `RESTORE_QUARANTINE` olur; newer recall/revoke/delete/security epoch/accepted operation eski backup ile geriye alınamaz. | Non-restorable floor/tombstone/operation ledger + cross-plane consistency manifest + clean-room import. |
| AC-ID-20 | Private/shared/community/official/quarantine/protected-audit classification tüm derivative, package, export, backup ve AI yolunda korunur. | Unknown/mixed → most restrictive; export field preview; scan/OCR/AI/publication verification sayılmaz. |
| AC-ID-21 | Supabase-centered fiziksel yön, API boundary’sini ve independent audit/object/floor/recovery kanıtını korur. | `service_role`/secret client, browser, repo, log veya AI context’inde değil; RLS/Storage sole authority değil; Studio Internal Ops değil. |
| AC-ID-22 | Android-first Flutter lane’inde portable truth/state sözleşmesi ile Android/iOS native/generated/plugin etkileri ayrıdır. | Android-first release evidence, iOS-later parity plan, owner-controlled signing/recovery; Android kanıtının iOS’a otomatik sayılması red. |
| AC-ID-23 | Her identity/recovery task’ı minimum context pack, allowed/forbidden scope, credential class, negative cases, rollback ve independent review/evidence taşır. | Fresh AI yalnız task pack ile çalışır; bütün repo varsayımı, secret erişimi, silent path expansion veya testsiz critical change red. |
| AC-ID-24 | AI yalnız attributable proposal/inspection/bounded retry/reconciliation yapabilir; policy, approval, recovery-to-authority, billing, key rotation veya high-consequence publish/recall’ı tek başına yapamaz. | AI task simülasyonu; owner’a SQL/SSH/log diagnosis/queue surgery/debug görevi çıkmaması. |
| AC-ID-25 | Her failure/blocked/revoked/recovery state plain-language reason, owner/resolver, timestamp/order, affected scope ve safe next action gösterir. | `HELD`, `ACCESS_DENIED`, `OUTCOME_UNKNOWN`, `RECONCILING`, `SERVICE_UNAVAILABLE`, `ACCOUNT_HELD`, `BILLING_HELD`, `KEY_UNAVAILABLE`, `RESTORE_QUARANTINE`; genel “hata oldu” red. |
| AC-ID-26 | Ücret, provider/account/billing/region veya recovery assurance karşılanamıyorsa güvenlik standardı düşürülmez; capability `HELD` veya dar safe read/recovery moduna geçer. | Owner-readable staged cost/exit/failure-domain planı; gizli overage, unbounded subscription veya owner repair dependency red. |

## 8. Handoff ve sonraki karar için gereken paket

DEBATE-010’ın kapanışı için aşağıdaki paket, kod yazmadan hazırlanmalıdır:

1. actor/session/role/competence/delegation/provider identity sözlüğü ve authority matrix;
2. consumer account-light/profile migration ve shared-motorcycle state/operation contract’ları;
3. Internal Operations API mutation, stale-session, step-up, outcome-unknown ve status-lookup contract’ı;
4. privileged recovery/security-epoch/break-glass ve revocation floor state machine’i;
5. protected audit event schema, custody/fallback/hold matrix ve restore reconciliation manifest’i;
6. Flutter selected-task package manifest, client capability, freshness/recall/recovery ve durable operation ledger contract’ı;
7. browser/mobile/provider/workload/legal identity yollarını içeren privileged-path negative test matrix’i;
8. IDCO workspace’leri için role/policy visibility, audit, recall, export ve access-denied walkthrough’ları;
9. her sözleşme için minimum AI task context pack, allowed/forbidden paths, fixtures, reviewer ve completion evidence;
10. açık numeric/legal/provider/owner kararları için owner, risk, cost, reversibility ve `HELD/UNVERIFIED` durumu.

Bu paket olmadan implementation “kimlik eklenmiş”, “session güvenli”, “recovery tamam” veya “audit çalışıyor” sayılmaz.
DEBATE-010 yalnızca gereksinim sentezini kapatır; Phase-5 ADR, gerçek cihaz/restore/accessibility/exit kanıtı ve uygulama
kodlaması için ayrı karar ve gate gerekir.

## 9. Kapsam dışı / özellikle kararlaştırılmayanlar

- Auth provider, OAuth/social login, passkey/email/phone yöntemi;
- exact RBAC/ABAC/policy engine ürünü ve RLS/Storage implementation;
- session/token süreleri, MFA/step-up cihazı ve recovery quorum sayıları;
- database, API runtime, Flutter package/plugin, encryption library, scanner, renderer, audit product veya cloud region;
- exact offline TTL/freshness/package/cache/media limits, final RPO/RTO ve legal retention;
- final pricing/tier/quota, billing planı ve satın alma;
- browser visual tokens/routes ve production mobile component implementation.

Bu kararların açık olması, identity/session/recovery davranışının belirsiz bırakılmasına izin vermez; yalnızca nasıl
uygulanacaklarının daha sonra eşit kanıt kapısından geçirilmesi gerektiğini gösterir.

