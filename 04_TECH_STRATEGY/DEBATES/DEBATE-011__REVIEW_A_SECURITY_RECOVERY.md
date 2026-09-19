# DEBATE-011 — Bağımsız Reviewer A: API Runtime, Güvenlik, Tutarlılık ve Kurtarma

Durum: `HELD — bağımsız adversarial no-code inceleme / A-B eşit / winner yok / ADR hazır değil`  
Tarih: `2026-09-19 (Europe/Istanbul)`  
İnceleyen: `Reviewer A — security, data consistency, transaction/idempotency, recovery`  
Kapsam: Kavriva API boundary'si, Flutter consumer, browser Internal Operations, Aday A ve Aday B runtime bileşimleri, yüksek sonuçlu işlem, queue/worker, object, outage, restore, exit.  
Çalışma modu: Kod, prototip, executable spike, hesap, satın alma veya üretim testi yoktur.

## 1. Kısa hüküm

Manager Proposal doğru güvenlik yönlerini tanıyor: client doğrudan canonical database/object authority taşımıyor; authentication ile authorization ayrılıyor; operation identity, idempotent retry, `OUTCOME_UNKNOWN`, commit-time kontrolü, quarantine, restore quarantine ve no-owner-debug ilkeleri anılıyor. Bununla birlikte bu ilkeler henüz saldırı altında çalışacak, bağımsız kanıtla kabul edilecek sözleşmelere çevrilmiş değil. Özellikle `audit intent` ile korunan product audit, DB transaction ile cross-plane effect, “queue gerektiğinde eklenir” ile dayanıklı worker capability'si, generation fence ile gerçekten negatif kazanan recall ve “restore quarantine” ile anti-resurrection aynı şeymiş gibi okunabilir.

| Aday | Hüküm | Adversarial okuma | Bu review sonucu |
|---|---|---|---|
| **A — Supabase'e yakın Edge API** | `HELD` | Kısa request için geri alınabilir aday; Edge limitleri, deferred queue, ortak Supabase failure-domain'i, audit/floor/object bağımsızlığı ve transaction-pooling kanıtı yok. | `PASS` değil, winner değil. Uzun iş veya protected positive effect için kanıt gelene kadar güvenli hold gerekir. |
| **B — Managed container API + worker** | `HELD` | Uzun iş ve lifecycle daha görünür; ancak ikinci runtime/queue ağı, DB bağlantısı, schema/message uyumu, audit/object/floor ve exit kanıtı yok. | `PASS` değil, A'nın otomatik fallback'i veya daha güvenli winner'ı değil. |
| Ortak Kavriva API contract'ı | `HELD` | Critical authz, audit-before-effect, idempotency, negative race, restore, epoch ve outage kapanışları belgesel düzeyde. | High-consequence positive effect açılmaz. |

Bu proposal için mevcut no-code aşamada `REJECT` hükmü vermiyorum; düzeltilebilir bir tasarım önerisi inceleniyor. Fakat aşağıdaki hard-fail davranışlarından biri gerçek bileşimde ortaya çıkarsa ilgili capability `REJECT-IF-UNMITIGATED` olur: protected audit yokken positive effect, stale authorization ile commit, blind duplicate, eski restore ile authority dirilmesi, quarantine'siz object activation, owner'ın SQL/SSH/queue surgery yapması veya direct provider path ile API'nin aşılması. `HELD`, güvenli veya production-ready demek değildir.

### Önem derecesi

- **CRITICAL:** Kapanmadan high-consequence positive effect, private object disclosure, recall/revoke, audit veya recovery authority açılırsa geri döndürülmesi zor bir güvenlik/tutarlılık sonucu doğabilir.
- **MAJOR:** Güvenlik standardını açıkça gevşetmese de ADR/activation için zorunlu contract, fixture veya işletim sınırı eksiktir.
- **MINOR:** Tek başına capability açmayan; ancak eşit karşılaştırmayı, terminolojiyi veya kanıt okumasını bozabilecek düzeltmedir.

## 2. Okunan kanıt tabanı

Bu review aşağıdaki belgelerin tamamı okunarak hazırlanmıştır:

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/DECISION_LOG.md` — özellikle `DEC-0025`–`DEC-0037`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_FAILURE_TCO_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__JUDGE_SYNTHESIS.md`

Özellikle `API-AC-001..024`, 18 runtime failure sınıfı (`F01..F18`), `DEC-0034`–`DEC-0037` ve DEBATE-010’un end-to-end revoke, protected audit, ayrı recovery/emergency-negative authority, last-admin, no-owner-debug ve clean-room exit hard gate'leri bu incelemenin bağlayıcı karşılaştırma sınırıdır. Bu review provider veya runtime seçmez.

## 3. Bulgular özeti

| ID | Seviye | Uygulama | Kısa bulgu | Hükme etkisi |
|---|---|---|---|---|
| C-01 | **CRITICAL** | A+B | `audit intent`/DB commit ile protected audit-before-effect ve bağımsız fallback aynı sözleşme olarak kapanmamış. | Positive approval/publish/recall/role/recovery/export/delete `HELD`; effect-before-audit varsa reject. |
| C-02 | **CRITICAL** | A+B | Commit-time authorization tuple eksiksiz, typed ve direct-path negatif kanıtlı değil. | Stale role/session, BOLA/IDOR veya provider bypass ihtimali kapanmadan mutation yok. |
| C-03 | **CRITICAL** | A+B | Operation ledger, outbox ve external side-effect idempotency'sinin atomik/tek anlamı tanımlı değil. | Timeout/worker retry/restore sonrası duplicate veya farklı payload riski. |
| C-04 | **CRITICAL** | A+B | Publish/recall/suspension race için yalnız “newer negative floor” deniyor; negatif kazanımın ordering/fence/unknown sözleşmesi yok. | Eski publish yeni recall'ı temizleyebilirse reject. |
| C-05 | **CRITICAL** | A+B (A'da daha yüksek runtime riski) | Restore quarantine, non-restorable floor ve cross-plane cutover kriteri ayrıntılı değil. | Eski revoke/recall/delete/accepted operation dirilirse reject. |
| C-06 | **CRITICAL** | A+B | Security epoch'in object handle, package, browser cache, queued/in-flight operation ve status/retry uçlarına end-to-end ulaşması bağlanmamış. | Revoke tamamlanmış sayılamaz; private/high-consequence akışlar `HELD`. |
| C-07 | **CRITICAL** | A+B (A'da Edge sınırı daha doğrudan) | “Uzun iş doğduğunda queue/worker eklenir” ifadesi bilinen uzun işleri ve ilk release capability gate'ini açıkta bırakıyor. | `waitUntil`/HTTP callback/worker eksikliğiyle partial/duplicate effect riski. |
| C-08 | **CRITICAL** | A+B | Outage sırasında bağımsız emergency-negative authority, positive hold ve account recovery ayrımı uygulanabilir bir failure-domain contract'ına bağlanmamış. | Recall/deny/revoke veya güvenli hold yolu yoksa privileged production açılmaz. |
| M-01 | **MAJOR** | A+B | Object lifecycle, quarantine, classification/lineage/digest ve handle audience/epoch semantiği tamamlanmamış. | Private object ve derivative activation kanıtlanamaz. |
| M-02 | **MAJOR** | A+B | Queue/worker lease, dedupe, retry/DLQ, poison, backpressure, shutdown drain ve message compatibility fixture'ları yok. | Uzun işlerin `ACCEPTED` ile gerçek effect'i karışabilir. |
| M-03 | **MAJOR** | A+B | Response semantic envelope ve canonical/delivery/consumer reconciliation state'leri tam taşınmıyor. | `ACCEPTED`, `OUTCOME_UNKNOWN`, `PARTIAL`, `HELD` yanlış UI/API anlamına dönüşebilir. |
| M-04 | **MAJOR** | A+B | DEBATE-010 identity adapter, issuer-qualified subject, privileged step-up/recovery/CSRF/PKCE ve iki issuer hard gate'i runtime contract'a alınmamış. | Runtime seçimi authn'i authorization sanabilir. |
| M-05 | **MAJOR** | A+B | Closed release manifest, client/API/schema/config/package compatibility ve artifact-bound generation açıkça bağlanmamış. | Config/derived asset/migration değişimi veya yanlış rollback yeni meaning yaratabilir. |
| M-06 | **MAJOR** | A+B | Offline package + durable ledger + local restore/migration/anti-resurrection sınırı runtime proposal'da yeterince görünür değil. | Offline capture, recall ve account-light migration sonucu belirsiz kalır. |
| M-07 | **MAJOR** | A+B | Browser stale tab dışında CSRF, origin/redirect, status lookup data leakage ve direct REST/RPC/Storage deny fixture'ı yok. | Çalınmış session veya operation enumeration riski. |
| M-08 | **MAJOR** | A+B | No-owner-debug ve AI task sınırı ilke olarak var; state-specific runbook, credential class, reviewer ve external escalation kanıtı yok. | “Provider console'a bak/SQL çalıştır” gizli recovery olabilir. |
| M-09 | **MAJOR** | A+B | Equal normalized BOM, hard cap/overage/stop ve incident/restore/exit maliyetleri gerçek fixture'a dönüşmemiş. | A'nın deferred queue'su maliyeti düşük gösterir; güvence bütçesi sessizce zayıflayabilir. |
| M-10 | **MAJOR** | A+B | Provider/runtime exit için clean-room export/import, secret reissue, source untouched, dual-run ve cross-plane acceptance sırası yok. | DB dump veya container image “exit” sanılabilir. |
| M-11 | **MAJOR** | A+B | Postgres merkezli logical authority ile object/audit/floor/queue/package plane'lerinin owner/version/manifest ilişkisi net değil. | DB transaction başarısı diğer plane'leri kanıtlamaz. |
| M-12 | **MAJOR** | A+B | A başlangıç adayı, B fallback diye çerçevelenirken aynı capability/workload ve aynı kanıt yükü gerçekten eşitlenmemiş. | Provider/runtime seçimi evidence yerine varsayılan tercih ile yönlenebilir. |
| M-13 | **MAJOR** | A+B | Observability product state, denominator, impact, resolver ve safe-read/positive-hold/negative-availability ayrımını tam vermiyor. | Yeşil runtime dashboard'u yanlış başarı izlenimi yaratabilir. |
| m-01 | **MINOR** | A+B | `0 PASS / 16 HELD` sayısı 24 API acceptance criterion ve 18 failure sınıfının yerine karar kanıtı gibi okunabilir. | Sonuç formatı normalize edilmeli. |
| m-02 | **MINOR** | A+B | “Tek authoritative DB transaction” ifadesi object/audit/queue effect'lerinin de fiziksel olarak atomik olduğu izlenimini veriyor. | Logical transaction core / external effect protocol dili kullanılmalı. |
| m-03 | **MINOR** | A+B | Supabase/Render gibi temsilci isimleri fixture'da geçse de provider seçimi gibi okunmamalı. | Provider-neutral candidate labels korunmalı. |
| m-04 | **MINOR** | A+B | `HELD`, `AUDIT_HELD`, `RESTORE_QUARANTINE`, `BILLING_HELD` ve `REJECT-IF-UNMITIGATED` geçiş koşulları tek state dictionary'de birleşmiyor. | UI/runbook ve bağımsız review aynı dili kullanmalı. |

## 4. Ayrıntılı adversarial bulgular

### C-01 — Audit-before-effect, `audit intent` ve custody ayrımı kapanmıyor

**Kanıt.** Manager Proposal §4.2, current authorization, `operation_id`, canonical değişiklik, “protected audit intent/event” ve outbox'ı “aynı DB assurance sınırında” bağlar. §4.6 runtime log'unun product audit olmadığını söyler; ancak protected custody, bağımsız fallback ve custody unavailable iken effect'in hangi atomik durumda tutulacağını açıkça yazmaz. Requirements §9.2 ise normal protected custody ve yeterince bağımsız fallback yoksa positive high-consequence action'ın `HELD` olmasını; ordered event, gap/fork/replay, retention/legal-hold, read/export/redaction ve restore reconciliation kanıtını ister.

**Saldırı.** Transaction, DB'de `audit_intent` ve canonical publish/recall değişikliğini commit eder; log drain, fallback veya audit export daha sonra kesilir. HTTP 2xx/DB commit gerçek product audit değildir. Restore eski DB audit intent'ini geri getirirken protected sequence/floor geri gelmeyebilir. Aday A'da Edge/DB/Auth/Storage ortak failure-domain'i bu boşluğu büyütür. Aday B'de ayrı container olması audit custody'sini kendiliğinden bağımsız yapmaz. “DB transaction başarılı” sonucu effect-before-audit'i başarı gibi gösterebilir.

**Düzeltme / kabul kapısı.**

1. `product_audit_event` için actor/workload, effective role/scope, issuer/session assurance, security epoch, policy/grant/competence version, operation ID, exact object/version/generation, old/new meaning, ordered server time, reason, result, impact ve recovery owner zorunlu tutulmalı.
2. Audit event effect'ten önce protected custody'de durmalı veya eşdeğer, denetlenebilir transactional assurance kanıtlanmalı. Normal custody veya yeterince bağımsız fallback hazır değilse `AUDIT_HELD`; positive effect yok.
3. Fallback'ın failure-domain'i, retention/legal hold, append-only/tamper evidence, gap/fork/replay, read/export/redaction ve restore reconciliation'ı ayrı kanıtlanmalı. Auth/runtime log'u ürün audit'i sayılmamalı.
4. Audit outage, fallback outage, effect-before-audit negatif testi ve restore sonrası sequence/floor uzlaştırması geçmeden A veya B high-consequence activation'ı açılmamalı.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`. Gerçek bileşim protected custody yokken effect commit ederse ilgili capability `REJECT-IF-UNMITIGATED`; aday seçimi yapılmaz.

### C-02 — Commit-time authorization tuple ve direct-path deny test edilebilir değil

**Kanıt.** Proposal §4.2 current actor/session/epoch/action/resource/scope/yetki kontrolü ve expected generation'ı söyler; §4.4 generic Data API/RPC/Storage/signed URL/provider console bypass'ını reddeder. Ancak tam current tuple'da bulunması gereken issuer/session assurance, exact classification, role/grant/delegation, competence, independence, policy/access version, release/schema/package compatibility, current suspension/recall/revocation generation ve protected audit readiness tek bir typed contract olarak verilmez. Requirements `API-AC-006..007`, `DEC-0026` ve DEBATE-010 bunu zorunlu kılar.

**Saldırı.** Sayfa açılırken olumlu görünen rol, cached claim veya stale browser operation commit'e kadar değişir; client `tenant_id`, `owner_id` veya `object_id` ile başka scope'a çağrı yapar. Exposed Data API/RPC/view/`SECURITY DEFINER`/Storage/signed URL yolu API'yi atlar. Provider role, `user_metadata`, RLS veya UI button gizleme ürün approval/tenant/competence authority'si gibi yorumlanır. A ve B'nin farklı runtime'ı bu mantıksal açığı kapatmaz.

**Düzeltme / kabul kapısı.** Her hassas request için provider-neutral karar tuple'ı zorunlu yapılmalı: actor/workload + issuer/session assurance + current security epoch; action + exact object/resource/tenant/scope/classification; role/grant/delegation + competence + independence + policy version; object/version/generation + release/schema/config/package ve negative floor; operation ID + fingerprint + reason + audit readiness. Tuple effect'ten hemen önce current olarak yeniden değerlendirilip yalnız `ALLOW`, `DENY` veya `HELD` üretmeli. Exposed table/view/function/RPC/Storage/signed URL/Studio yüzeyi envanterlenmeli; direct client writes, client-supplied authority ve cross-tenant access negatif testte deny olmalı. `service_role`, owner/billing root ve unrestricted SQL/SSH yalnız dar server-side task scope'unda kalmalı.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`. Direct canonical/object path veya stale auth ile effect gerçek fixture'da çalışırsa ilgili path `REJECT-IF-UNMITIGATED`.

### C-03 — Idempotency, transaction ve outbox tek effect protokolüne bağlanmıyor

**Kanıt.** Proposal §4.2'de operation identity/fingerprint, expected generation, canonical change, audit intent ve outbox aynı DB transaction'ında anılır; §4.3 aynı ID ile lookup ve farklı fingerprint'te conflict der. Ancak operation ID namespace/retention/cross-region uniqueness, request snapshot, actor/scope binding, status lookup authorization, outbox effect key, external object/notification/worker retry ve restore edilmiş tombstone davranışı tanımlı değildir. Requirements `API-AC-008..010`, `F01`, `F02`, `F05`, `F13`, `F17` bunları ayırır.

**Saldırı.** Commit sonrası response kaybolur; client yeni ID ile kör retry yapar veya aynı ID'yi farklı payload/scope ile tekrar kullanır. Queue at-least-once teslimi, worker kill/restart veya restore edilmiş outbox iki object/notification/publish effect'i doğurur. Aynı ID başka tenant/actor tarafından status lookup ile enumeration'a dönüşür. Security epoch değişmişken eski pending operation retry edilirse current authority olmadan effect sürer.

**Düzeltme / kabul kapısı.** Immutable request envelope ve canonical unique key; operation identity actor/tenant/action/resource/scope/classification ile bağlanmalı, payload fingerprint ve expected versions/generations ilk kabulde dondurulmalı. Aynı fingerprint yalnız aynı semantic sonucu read-only olarak döndürmeli; farklı fingerprint/scope/actor `CONFLICT/HELD` olmalı. Canonical effect ile outbox kaydı aynı DB assurance sınırında atomic bağlanmalı; her dış side-effect deterministic effect key, idempotent worker, manifest/status ve reconcile state taşımalı. Status endpoint'i operation sahibi/scope/role ile yetkilendirilmeli ve private payload sızdırmamalı. Timeout-before/after-commit, duplicate, process kill, queue redelivery, old epoch retry, restore replay ve cross-region uniqueness fixture'ları zorunlu.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`; blind duplicate veya different-payload overwrite gözlenirse `REJECT-IF-UNMITIGATED`.

### C-04 — Publish/recall/suspension race'te negatif authority'nin gerçekten kazandığı kanıtlanmıyor

**Kanıt.** Proposal §4.2 ve §4.7 expected generation/newer negative floor kontrolünü ve restore quarantine'ı söyler; §8 tablo “generation fence; negative wins” der. Fakat generation'ın monotonik üretimi, commit serialization/isolation, tie/unknown sonucu, emergency negative path ile normal publication arasındaki ordering ve queue worker'ın effect öncesi ikinci kontrolü verilmez.

**Saldırı.** Publish G okur. Recall/suspension G+1 yazar. Publish stale transaction olarak commit eder, veya recall response kaybolur ve publication optimistic success ile açılır. Bir worker eski manifest'i aldıktan sonra yeni negative floor oluşur. `OUTCOME_UNKNOWN` recall'ı “olmadı” kabul eden retry, yeni suspension'ı temizler. Aynı version numarası farklı scope/generation ile karşılaştırılırsa most-restrictive negative authority kaybolur.

**Düzeltme / kabul kapısı.** Negative floor, release/suspension/recall generation ve object/package eligibility aynı canonical fence ile monotonik tutulmalı; effect commit anında atomic compare-and-fence yapılmalı. Tie, missing current floor, provider/audit unknown, worker lease expiry veya response loss `HELD/OUTCOME_UNKNOWN` olup positive publication'a dönüşmemeli. Queue worker effect öncesi current generation/epoch/audit readiness tekrar kontrol etmeli; negative generation eşit veya daha yeni ise negative kazanmalı. Rollback yalnız current, compatible, not-recalled predecessor'a yeni guarded publication event'i olmalı. Publish-vs-recall, recall timeout, in-flight worker, concurrent scopes ve invalid rollback fixture'ları geçmeli.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`. Stale/in-flight publish newer negative authority'yi temizleyebiliyorsa ilgili release/recall capability `REJECT-IF-UNMITIGATED`.

### C-05 — Restore quarantine, non-restorable floors ve cross-plane cutover eksik

**Kanıt.** Proposal §4.7 restore'u `RESTORE_QUARANTINE` yapar ve revoke/recall/delete/accepted-operation dirilmemesini ister. Requirements `API-AC-022..023`, `DEC-0034`, `DEC-0035` ve failure research F17/F18; DB, object bytes, protected audit, identity, policy/config, queue, package, runtime release ve release/security/deletion/operation/migration floor'larının birlikte taşınmasını; source'un acceptance öncesi değiştirilmemesini ister. Proposal bu cross-plane manifesti, floor karşılaştırmasını, queue replay fence'ini ve clean-room cutover sırasını ayrıntılı sözleşmeye bağlamaz.

**Saldırı.** Eski DB/PITR snapshot'ı yeni object storage, audit, queue mesajı veya runtime config ile birleştirilir. Snapshot'ta silinmiş private object tekrar handle alır; recalled release tekrar eligible olur; accepted operation outbox replay ile iki kez uygulanır; eski worker message yeni DB'de geçerli sayılır. Container image/Edge revision rollback'i DB schema, object generation veya negative floor'u geri almaz.

**Düzeltme / kabul kapısı.** Non-restorable release, security epoch, suspension/recall, deletion/privacy, object generation, accepted-operation, migration/tombstone ve package generation floor'ları ayrı custody'de monotonik karşılaştırılmalı. DB/current state, history/provenance, operation ledger, protected audit, identity/policy, object bytes+lineage, release/package manifest, queue/outbox ve runtime/schema/config birlikte cross-plane manifest ile import edilmeli. Import yalnız quarantine'da; current negative floor, audit continuity, digest/lineage, classification, compatibility ve anti-resurrection negatifleri geçmeden positive cutover yok. Old queue/message/worker epoch'i deny edilmeli; source ortam kabul edilene kadar untouched kalmalı. Restore, partial migration, deletion, recall, accepted-operation ve clean-room import fixture'ları gerekir.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`; eski restore authority veya accepted effect diriltiyorsa `REJECT-IF-UNMITIGATED`.

### C-06 — Security epoch end-to-end revoke'e bağlanmamış

**Kanıt.** Proposal §4.2 ve §4.3 session/epoch'i tuple'a koyar; fakat epoch'in object handle, browser cache/service worker, local offline package/key state, queued/in-flight work, lost-response status/retry ve account-light migration'a nasıl yayıldığını belirtmez. DEBATE-010 Judge §4.1 ile Requirements §13.2 bu uçları açıkça bağlar; downloaded copy'nin remote retract edilemeyeceği ve remote wipe'ın authority olmadığı da bağlayıcıdır.

**Saldırı.** Logout-all veya factor recovery yalnız JWT'yi iptal eder; önceden alınmış signed URL/handle expiry'ye kadar çalışır. Browser service worker/private cache eski scope'u gösterir. Queue worker eski epoch ile commit eder. Offline package recalled/expired olmasına rağmen foreground'da physical progression açar. Response kaybolduktan sonra status lookup/retry eski authority ile positive effect üretir. Device restore local private evidence'ı current epoch doğrulamadan açar.

**Düzeltme / kabul kapısı.** Epoch operation'ı provider session/account state, grant/policy/competence generation, pending/in-flight operations, status lookup/retry, object handle/generation, browser cache/service worker ve classified local package/key state ile tek current decision'e bağlanmalı. Handle exact audience/scope/object/version/epoch ile kısa ömürlü veya server-mediated olmalı; revoke sonrası yeni handle yok, local downloaded copy için residual-risk disclosure ve safe-mode olmalı. Epoch bump sonrası old operation `DENY/HELD`, status lookup read-only reconciliation; local restore/migration quarantine olmalı. Lost token, logout-all, factor loss, stale handle/package, in-flight commit ve old retry fixture'ları A ve B'de eşit çalışmalı.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`; revoked epoch ile private/high-consequence effect sürerse `REJECT-IF-UNMITIGATED`.

### C-07 — Queue/worker capability'si “uzun iş gerektiğinde” ertelenemez

**Kanıt.** Proposal §4.5 ve §5, synchronous API'yi kısa işlerle sınırlar; package build, object scan/preview, export, AI/OCR, notification ve reconciliation için durable queue/worker'ı uzun iş doğduğunda eklemeyi önerir. Aynı bölüm function background callback/`waitUntil`'ın durable queue olmadığı konusunda doğrudur, fakat ilk release'te hangi işlerin uzun olduğu, route classifier'ın nasıl enforce edildiği ve queue capability'si eklenmeden bu işlerin nasıl `HELD` kalacağı söylenmez. Failure research F12/F13, Edge wall-clock/CPU/memory ve queue durability sınırlarını; Requirements §19 aynı long-job fixture'ını zorunlu kılar.

**Saldırı.** “Geçici olarak kısa” görünen object transform, package build veya export Edge request'ine alınır; timeout sonrası DB commit/side-effect ayrılır. `waitUntil` tamamlanmış effect kanıtı sanılır. Aday A'da Edge CPU/wall-clock sınırı bunu daha erken üretir. B'de worker varmış gibi yazılsa da queue lease/DLQ/message compatibility yoksa worker kill sonrası partial/duplicate olur. Queue sonradan eklenirken eski pending operation/message anlamı korunmayabilir.

**Düzeltme / kabul kapısı.** İlk release capability inventory'si her route'u `short-transaction`, `read/status` veya `durable-long-job` olarak sınıflandırmalı; long-job capability'si hazır değilse o route `HELD/UNAVAILABLE`, callback/`waitUntil` veya optimistic completion kullanılamamalı. Bilinen package build, object scan/derivative, export, reconciliation ve notification gibi işler için queue/worker contract'ı baştan tanımlanmalı; boş mikroservis ağı kurmak gerekmese de capability'nin varlığı ve maliyeti gizlenmemeli. Long job sadece `PENDING/QUEUED` döndürmeli; operation ledger, lease/heartbeat, dedupe, retry budget, DLQ/poison, backpressure, cancellation, shutdown drain, message schema/version ve effect-before-commit fence taşımalı. A ve B aynı workload/TCO ile değerlendirilmeli.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`; A'da required long work `waitUntil`/Edge timeout'a bırakılırsa, B'de worker/queue durability yoksa ilgili capability `REJECT-IF-UNMITIGATED`. Bu bulgu B'yi otomatik kazandırmaz.

### C-08 — Outage, account recovery ve emergency-negative authority tek güvenlik sözleşmesi değil

**Kanıt.** Proposal §9, protected audit/floor ve emergency-negative yolunun Supabase ortak failure-domain'inden ne kadar ayrılacağının sonraki debate/evidence gate'inde kapanacağını söyler. §10 yalnız trigger'ları listeler. DEBATE-010 Judge §4.2 ve Requirements §7/§13/§16 ise privileged account recovery ile emergency negative authority'nin ayrı state machine'ler olduğunu; recovery'nin approve/publish/role grant veremeyeceğini, negative path'in yalnız suspend/recall/quarantine/deny üreteceğini ve normal IdP/API/audit failure-domain'inden gereken ölçüde ayrılması gerektiğini bağlar.

**Saldırı.** Supabase Auth/API/DB/Storage veya audit sink outage'ında operator revoke/recall yapamaz; owner provider console'a veya SQL'e yönlendirilir. A'nın ortak Supabase failure-domain'i bunu büyütebilir. B'nin ayrı API container'ı Supabase data plane unavailable ise negative authority sağlamaz; ikinci runtime yalnızca ek failure-domain'dir. Recovery için kullanılan actor yanlışlıkla positive role/publish yetkisi kazanabilir. Audit/fallback unavailable iken system guessed success döndürebilir.

**Düzeltme / kabul kapısı.** Account recovery ve emergency-negative için ayrı state machine, actor/role/scope/TTL, expiry, reason, protected audit/fallback, notification ve post-incident reconciliation yazılmalı. Negative path yalnız monotonic suspension/recall/quarantine/access deny floor artırmalı; positive truth, unsuspend, competence, role grant veya publication üretememeli. Provider/API/audit outage sırasında safe read, positive hold, negative availability, `SERVICE_UNAVAILABLE`/`ACCOUNT_HELD`/`AUDIT_HELD` ve `OUTCOME_UNKNOWN` ayrılmalı. Gerçek bağımsız insan/kurum ve last-admin yolu yoksa high-consequence positive activation `HELD` kalmalı; AI veya tek owner bunu taklit edemez.

**Öneriye etkisi.** A ve B için `CRITICAL / HELD`; owner/SQL/console ile manual repair veya recovery-positive bypass zorunluysa ilgili capability `REJECT-IF-UNMITIGATED`. A'nın ortak failure-domain'i B'ye karşı otomatik puan veya seçim oluşturmaz.

### M-01 — Object lifecycle ve handle mediation eksik

**Kanıt.** Proposal §4.4 API-issued scoped private object handle der; §4.5 object scan/preview'ı long job'a koyar. Requirements §10 ise `RECEIVED → QUARANTINED → VALIDATED/SCANNED/RENDERED-AS-UNTRUSTED → CLASSIFIED → ACTIVATED`, SSRF/private-address/redirect/ambient credential/traversal/decompression bomb/oversize, exact lineage/digest/version, most-restrictive classification, handle audience/scope/object/version/generation/epoch ve downloaded-copy residual riskini ister.

**Kusur ve düzeltme.** Proposal bu state machine'i, malicious archive/URL ve derivative lineage sözleşmesini, handle TTL/audience/epoch, orphan cleanup, object backup/restore ve revoke sonrası eski handle davranışını açıkça bağlamıyor. Upload “dosya var” veya scan/render/OCR sonucu technical correctness/publication authority sayılmamalı. A ve B için aynı object fixture'ı; classification/lineage/digest/handle/recall/partial upload kanıtı; tamamlanana kadar `OBJECT_QUARANTINE` gerekir.

**Öneriye etkisi.** A ve B `MAJOR / HELD`. Global/public handle veya quarantine'siz activation gerçekse `REJECT-IF-UNMITIGATED`.

### M-02 — Queue/worker yaşam döngüsü ve delivery semantics'i yazılmamış

**Kusur.** C-07 capability'nin ertelenmesine ilişkindir; burada queue zaten açıldığında bile lease/visibility timeout, heartbeat, max concurrency, dedupe, retry budget, poison-message quarantine/DLQ, backlog/backpressure, cancellation, worker kill/restart, graceful shutdown drain, message version compatibility, partial output manifest ve stuck-operation resolver tanımlı değildir.

**Düzeltme.** Her queue message operation ID, fingerprint, expected generation/epoch, release/schema version, idempotent effect key ve recovery owner taşımalı. Duplicate delivery effect'i çoğaltmamalı; poison iş positive path'i kilitlemeden `HELD/QUARANTINE` olmalı. Queue empty `ACCEPTED` değildir. A'nın external queue/worker maliyeti ve B'nin web+worker+queue lifecycle'ı aynı fixture'da ölçülmeli.

**Öneriye etkisi.** A ve B `MAJOR / HELD`; manual cursor/queue surgery owner'a bırakılırsa C-08 ve no-owner hard-fail'i de tetikler.

### M-03 — API semantic envelope ve state ayrımı eksik

**Kusur.** Proposal operation ID ve `OUTCOME_UNKNOWN`'ı doğru biçimde anıyor; ancak Requirements §4.3, §8 ve `API-AC-009..010`'daki `ALLOW`, `DENY`, `HELD`, `FAILED`, `PARTIAL`, `OUTCOME_UNKNOWN`, `RECONCILING`; operation status ile release delivery ve consumer reconciliation; current generation, audit reference, effect summary, impact, resolver ve next action alanlarını tek response contract'ta zorunlu kılmıyor. “Commit oldu” veya “queue boş” response'u consumer-reconciled anlamına gelmemeli.

**Düzeltme.** Fiziksel wire formatı seçmeden provider-neutral semantic envelope tanımlanmalı. Status lookup read-only current effect, audit ref, generation, conflict/hold reason, resolver ve next action vermeli; private payload/other tenant sızdırmamalı. `AUTHORITATIVE_CURRENT`, `DELIVERY_OBSERVED`, `CONSUMER_RECONCILED` ayrı state'ler ve `PARTIAL` affected-scope ile tutulmalı.

**Öneriye etkisi.** A ve B `MAJOR / HELD`.

### M-04 — Identity adapter ve privileged activation gate runtime contract'a taşınmamış

**Kusur.** Proposal authentication'ın authority olmadığını ve current session/epoch'i söyler; fakat DEBATE-010 Judge'ın provider-qualified `(issuer, subject)`, allowlisted `iss/aud/alg/JWKS`, current account/session state, factor loss, recovery, browser origin/RP-ID, user verification, CSRF/PKCE, transaction-bound fresh step-up, logout-all ve two-issuer mapping hard gate'lerini tek API runtime contract'a bağlamaz. A'da passkey “stable/GA” etiketi kanıt yerine geçemez; B'de ikinci issuer otomatik güvenli değildir.

**Düzeltme.** Identity adapter ile Kavriva principal/authorization tuple açıkça ayrılmalı. A ve B aynı privileged fixture'ını taşımalı; A için passkey/step-up/factor loss/key rotation/outage; B için issuer collision/claim disagreement/cross-issuer revoke/logout ve ikinci recovery/support dahil. Auth provider winner yoktur; fixture kapanmadan privileged production `HELD`.

**Öneriye etkisi.** A ve B `MAJOR / HELD`; provider seçimi yapılmaz.

### M-05 — Closed release meaning ve compatibility graph eksik

**Kusur.** Proposal §4.7 runtime rollback'ın database schema/data, queue message, object, audit veya negative floor'u geri çevirmediğini söyler; fakat exact immutable release manifestin content/claim/localization/media/transform/config/feature input'larını, source/evidence/provenance/classification, binary/web/API/schema/client capability, migration forward-recovery, offline package closure, release/suspension generations ve verifier/promotion/audit identity'lerini bağlamaz. Runtime revision rollback'ı eski meaning'i otomatik olarak geçerli yapamaz.

**Düzeltme.** `release_id`/artifact digest/manifest/version/generation compatibility graph'ı ve old/new request/message acceptance penceresi yazılmalı. Mismatch `DEPLOYMENT_HELD`; code rollback yerine forward migration veya current valid predecessor'a guarded new publication event'i kullanılmalı. Config/feature/derived artifact meaning değiştirebiliyorsa closed manifest'e girmeli.

**Öneriye etkisi.** A ve B `MAJOR / HELD`.

### M-06 — Offline package, durable ledger ve account-light migration API boundary'de yeterince görünür değil

**Kusur.** Proposal DEC-0036'yı devralır; fakat selected motorcycle/task için complete compact safety/application/safe-stop/recovery closure, manifest/generation/digest/compatibility, optional media ayrımı, process-death/storage-pressure/device-restore, operation ledger states, tombstone/delete, recall foreground return ve local-to-profile migration'ın source possession/reauth/preview/immutable mapping/conflict/split/rollback contract'ını runtime acceptance'a bağlamaz.

**Düzeltme.** Package fetch/verify/resume/cancel, ledger submit/status lookup ve migration aynı provider-neutral API semantic contract'ını kullanmalı. Local save, upload queue empty, Realtime/push veya downloaded package canonical acceptance/freshness/recall değildir. Restore/migration quarantine, negative floor/security epoch recheck ve no-silent-LWW fixture'ı eklenmeli.

**Öneriye etkisi.** A ve B `MAJOR / HELD`; local plaintext/key fallback veya recalled package ile positive progression varsa ilgili capability `REJECT-IF-UNMITIGATED`.

### M-07 — Browser boundary ve operation status disclosure eksik

**Kusur.** Proposal stale tab/cached claim ve disabled button'ın authority olmadığını doğru söyler; fakat browser cookie/token storage, trusted origin/redirect allowlist, CSRF, PKCE/deep-link, CSP, transaction nonce/action-resource-version-consequence binding, tab replay ve status endpoint enumeration/disclosure contract'ı yoktur. Internal Operations provider Studio değildir; generic Data API/RPC/Storage yolu da ayrıca negative test edilmelidir.

**Düzeltme.** Browser threat model, exact session storage/lifetime, origin/redirect/PKCE/CSRF, step-up binding ve status-scope policy yazılmalı. Operation ID tahmin edilebilir veya başka tenant'ın audit/effect summary'sini açığa çıkarırsa `DENY`; stale tab `DENY/HELD`; direct provider path hard-fail.

**Öneriye etkisi.** A ve B `MAJOR / HELD`.

### M-08 — No-owner-debug ve AI task operability ilke seviyesinde kalmış

**Kusur.** Proposal §9 her iki aday için owner'a SQL/SSH/queue repair yaptırmama sözü verir; ancak outage, billing, quota, audit sink gap, object quarantine, restore conflict, migration partial, secret rotation, deploy/schema mismatch ve unknown result için state-specific runbook, resolver, external support/real-human action, credential class, reviewer/validator ve evidence custody sunmaz. Requirements `API-AC-019..020`, `DEC-0028`, `DEC-0029` ve DEBATE-010 §7 bunları task pack olarak ister.

**Düzeltme.** Her task exact objective/scope, allowed/forbidden operation, short-lived audience/expiry, dry-run, operation ID, hard-stop states, evidence digest, independent reviewer, forward recovery/reconciliation ve owner-readable handoff taşımalı. Owner yalnız `approve/hold/stop/payment/support` kararı vermeli; AI provider owner, billing root, `service_role`, unrestricted SQL/SSH, global object secret, recovery/approval/publication authority alamamalı. Bu yol yoksa managed etiketi yeterli değil; capability `HELD`/gerekirse `REJECT-IF-UNMITIGATED`.

**Öneriye etkisi.** A ve B `MAJOR / HELD`.

### M-09 — Equal normalized BOM ve safe cost stop kapanmamış

**Kusur.** Proposal §11 shared Supabase, API/container, queue/worker, audit/floor, object, monitoring, DNS, support, incident/restore/exit ve tax/FX kalemlerini listeler; ancak güncel resmi quote, quota/hard-cap/overage, free/capped path, stop action ve mandatory/deferrable/optional/scale-triggered sınıfları doldurulmamıştır. A'nın queue/worker'ı “ihtiyaç doğduğunda” ertelenirse A normal ayda B'den yapay olarak ucuz görünür; audit/floor/object/restore dış adjunctları da headline'a gizlenebilir.

**Düzeltme.** A ve B aynı workload, same normal/incident/restore/exit horizon, shared core ve adjunct BOM ile ölçülmeli. Her satır resmi tarih/plan/region/quota/hard cap/overage/stop owner action, tax/FX/card uncertainty ve provider exit maliyeti taşımalı. Mandatory assurance bütçeye sığmıyorsa güvenlik düşürülmemeli; ilgili capability `BILLING_HELD/HELD`.

**Öneriye etkisi.** A ve B `MAJOR / HELD`; güvenceyi ucuzlatmak için silently degraded mode varsa `REJECT-IF-UNMITIGATED`.

### M-10 — Clean-room exit, source preservation ve runtime replacement contract'ı yok

**Kusur.** Proposal provider-neutral operation/authorization/audit/object/package/recovery contract'ı hedefler; ancak exit sırasında canonical current/history/provenance, operation ledger/status/conflict/tombstone, release/package/compatibility/revocation generations, policy/grant/competence/epoch, object bytes+lineage+classification+digest, protected audit/floor, runtime artifact/config/queue message compatibility, secret reissue, DNS cutover ve decommission sırasını kanıtlamaz.

**Düzeltme.** Source untouched until acceptance; plane-by-plane export manifest/digest; isolated clean-room import/quarantine; current negative floor/audit continuity/object/package integrity/identity mapping/no-resurrection testleri; old/new dual-run ve pending operation reconciliation; secrets/factors reissued; only after independent acceptance cutover/decommission yapılmalı. `pg_dump`, provider clone veya container image tek başına exit sayılmamalı.

**Öneriye etkisi.** A ve B `MAJOR / HELD`; proprietary handle/queue/identity state kaybı gösterilirse `REJECT-IF-UNMITIGATED`.

### M-11 — Plane ownership ve consistency manifest yeterince açık değil

**Kusur.** Proposal persistent truth'i Postgres merkezine koyar; object, audit/floor ve queue için bağımsızlık gerektiğini kabul eder. Fakat current state/history/provenance/protected audit/object/package/operation ledger/release/config/negative floor plane'lerinin canonical owner, immutable identity/version/generation, classification ve reconciliation manifest'i yoktur. Database transaction yalnız DB anlamını bağlayabilir; object bytes, audit custody, queue delivery, cache/search/analytics veya package consumer reconciliation'ı fiziksel olarak commit etmez.

**Düzeltme.** Domain/plane inventory; writer/reader boundary; authoritative vs rebuildable projection; cross-plane manifest; each transition's accepted/observed/reconciled meanings; orphan/partial/unknown resolver ve restore/exit reconciliation matrix yazılmalı. Runtime/provider değişirken bu contract değişmemeli.

**Öneriye etkisi.** A ve B `MAJOR / HELD`.

### M-12 — A/B eşit evidence sınırı proposal'daki başlangıç/fallback diliyle bozuluyor

**Kusur.** Proposal A'yı “başlangıç adayı”, B'yi “ilk runtime fallback'i” diye konumlandırırken 16 satırlık no-code tabloda her ikisine aynı `HELD` etiketi verir. A'nın required queue/worker capability'si ertelenmiş, B'nin worker/queue bileşimi ise baştan yazılmıştır; bu, aynı workload/capability ve TCO'nun karşılaştırıldığı anlamına gelmez. A'nın daha az hizmet görünümü bir production advantage kanıtı değildir; B'nin ikinci provider yüzeyi de otomatik security loss veya win değildir.

**Düzeltme.** Aday A/B'ye aynı API semantic contract, same route classification, same queue/object/audit/floor/recovery capability, same fault injection, same owner/AI restrictions, same evidence template ve same normalized BOM uygulanmalı. `A` veya `B` yalnız conditional working hypothesis olarak anılmalı; runtime/provider/plan seçilmemeli. A fixture'ı geçemezse B yeniden eşit evidence ile değerlendirilir; B de geçemezse konu `HELD`, başka challenger'lar açılabilir.

**Öneriye etkisi.** A ve B `MAJOR / HELD`; bu review provider seçmez.

### M-13 — Observability runtime health ile product truth'ı ayırmıyor

**Kusur.** Proposal runtime logs/audit ayrımını söyler; ancak owner-readable product surface'in current state, last transition/reason/generation, operation/audit/correlation references, affected scope/impact, resolver/next action, `unknown/partial/held/unavailable/reconciling` denominator'ı ve safe read/positive hold/negative availability ayrımını standardize etmez. Green health check, empty queue, function completion veya provider dashboard product acceptance değildir.

**Düzeltme.** Her operation/release/object/package/ledger state için state dictionary + correlation/trace/audit reference + privacy/redaction + incident impact graph'i görünür olmalı; dashboard/KPI state değiştirmemeli. Log gap/sample/retention gap product effect'i `UNKNOWN/HELD` yapmalı.

**Öneriye etkisi.** A ve B `MAJOR / HELD`.

## 5. Zorunlu eksik fixture ve kanıt paketi

Manager Proposal §12'nin Phase-5 listesi doğru yöndedir; aşağıdaki fixture'lar bu review'deki boşlukları kapatacak şekilde **A ve B için aynı input, aynı fault, aynı beklenen state ve aynı evidence formatıyla** çalıştırılmalıdır. No-code plan belgesi bu fixture'ların yerine geçmez.

| Fixture | Saldırı / kontrol | Beklenen minimum çıktı |
|---|---|---|
| F-01 Boundary/direct-path | Flutter/browser direct REST/Data API, RPC/view/function, Storage/signed URL, provider Studio publish, client-supplied tenant/object ID, leaked secret | API dışı high-consequence path `DENY`; cross-tenant/object disclosure yok; audit ve no-effect kanıtı |
| F-02 Commit authz | Stale tab/role/JWT/session/epoch, expired delegation, changed policy/competence/independence, cross-tenant/classification ve dependency mismatch | Commit-time `DENY/HELD`; cached claim/UI/provider role authority değil; current tuple/audit reference |
| F-03 Timeout/idempotency | Timeout before/after commit, lost response, same fingerprint retry, same ID/different payload/scope/actor, process kill, duplicate status lookup | `OUTCOME_UNKNOWN` tahmin edilmez; one effect; same result read-only; different payload `CONFLICT/HELD` |
| F-04 Transaction/outbox | DB partial failure, outbox retry, object/notification side-effect failure, queue duplicate, restore edilmiş pending operation | Atomic canonical core; external effect manifest; `RECONCILING/PARTIAL`; accepted operation iki kez uygulanmaz |
| F-05 Queue/worker | Lease expiry, worker kill/restart, concurrent claim, poison message, retry storm, DLQ, backpressure, cancel, graceful deploy drain, old/new message schema | Dedupe/effect key; bounded retry; poison quarantine; owner-readable backlog; queue empty `ACCEPTED` değil |
| F-06 Audit custody | Primary audit unavailable, fallback unavailable, effect-before-audit, gap/fork/replay, retention/legal hold, read/export/redaction, restore reconciliation | Positive action `AUDIT_HELD`; protected event minimum fields; independent fallback/floor; gap/fork visible |
| F-07 Publish/negative race | Publish vs recall/suspension, equal/new generation, response-loss recall, in-flight worker, overlapping scope, invalid rollback | Newer/most restrictive negative wins; stale publication `DENY/HELD`; ordered audit; no guessed rollback |
| F-08 Object | Partial upload, digest mismatch, malicious archive, SSRF/private URL/redirect, traversal/decompression bomb, mixed derivative classification, handle leak/revoke | Quarantine state; exact lineage/digest/version; scoped audience/epoch handle; no public/private cross-scope; downloaded-copy residual disclosure |
| F-09 Package/ledger | Interrupted/mixed/wrong-base package, process death, storage pressure, recalled package foreground return, tombstone/delete, offline conflict, account-light merge | Complete compact closure; no silent LWW; explicit ledger states; reconcile/hold; package generation/epoch check |
| F-10 Revoke/epoch | Logout-all, stolen token, factor loss/recovery, pending/in-flight op, lost-response retry, browser cache/service worker, object handle, local key/package | End-to-end deny/hold; new handle yok; downloaded copy remote-retract edilemez disclosure; old retry cannot effect |
| F-11 Restore/anti-resurrection | Old DB/PITR + object + audit + queue + runtime/config; deleted private data; recalled release; revoked grant; accepted operation/tombstone replay | `RESTORE_QUARANTINE`; cross-plane manifest/floor comparison; source untouched; no positive cutover or resurrection |
| F-12 Outage/negative authority | DB/Auth/Storage/API/queue/audit/DNS/region/account/billing/quota partial outage; safe read, positive hold, negative action | `SERVICE_UNAVAILABLE`/`ACCOUNT_HELD`/`BILLING_HELD`/`AUDIT_HELD`; safe history/stop; independent negative semantics; no owner repair |
| F-13 Deploy/secret | Old/new runtime and schema, forward migration, rollback, queue message compatibility, leaked key, rotation, in-flight drain | `DEPLOYMENT_HELD` on mismatch; forward recovery; old credential/session/handle/worker fenced; no schema rollback data loss |
| F-14 Identity/browser | A step-up origin/RP-ID/UV/challenge/factor loss; B issuer collision/claim disagreement/cross-issuer revoke; CSRF/PKCE/redirect | `DENY/HELD` on uncertainty; recovery cannot positive role/publish; no provider winner by label |
| F-15 No-owner-debug/AI | Provider account/secret/queue/audit/object/restore task, forbidden credential request, half-complete AI task, missing reviewer | Narrow task pack; dry-run/hard stop/evidence/reviewer/forward recovery; plain-language owner handoff; no SQL/SSH/console repair |
| F-16 Cost/exit | Normal/incident/restore/exit month, overage/hard cap, optional service disabled, clean-room provider/runtime replacement | Same normalized BOM; explicit stop; `BILLING_HELD` preserves accepted/history/pending; export partial leaves source untouched |

Her fixture satırı için A ve B'de şu beş çıktı zorunludur: expected semantic state, attempted/actual side effect, protected audit evidence, recovery owner/next action ve cost/exit impact. Fixture yoksa `PASS` değil `HELD/UNVERIFIED`; hard-fail davranışında `REJECT-IF-UNMITIGATED`.

## 6. Önerilen düzeltme sırası

1. **Ortak semantic contract'ı kilitlemeden runtime seçmeyin:** request/response envelope, operation identity/fingerprint, expected versions/generations, current authz tuple, `ALLOW/DENY/HELD/UNKNOWN/PARTIAL/RECONCILING`, status-scope ve audit reference tek provider-neutral contract olarak yazılmalı.
2. **High-consequence transaction core'ı daraltın:** DB transaction; current authorization, operation ledger, immutable request/fingerprint, canonical state, audit precondition ve outbox intent'i bağlasın. Protected audit/fallback ve object/queue side-effect'lerini fiziksel atomiklik varsayımından çıkarıp explicit custody/reconcile state'lerine ayırın.
3. **Long-job capability gate'i ilk günden tanımlayın:** route classifier, queue/worker contract, lease/retry/DLQ/backpressure/shutdown/message version ve operation fence olmadan package/object/export/reconcile/AI/OCR/notification çalışmasın. A ve B aynı queue requirement/TCO'yu taşısın.
4. **Recall/restore/revoke'yi tek monotonic negative modelde birleştirin:** release/suspension/object/package/security/deletion/accepted-operation/migration floors; in-flight queue/worker/handle/cache/package recheck; negative wins; restore quarantine ve source untouched.
5. **Identity/authz adapter'ını ayrı ama zorunlu boundary yapın:** DEBATE-010 issuer/session/factor/recovery/step-up/CSRF/PKCE ve two-issuer semantics runtime contract'a taşınsın; provider role/RLS/signed URL/API key authority sayılmasın.
6. **Object ve offline lanes'i kapatın:** quarantine-first lifecycle, classification/lineage/digest, scoped handle, package closure, durable ledger, local key/revoke disclosure, account-light migration ve status reconciliation.
7. **No-owner-debug + TCO + exit'i activation hard gate yapın:** state-specific runbook, AI task pack, independent support/recovery, same BOM, hard cap/stop, incident/restore/exit month, cross-plane clean-room import ve negative tests.
8. **A/B'yi yeniden eşit değerlendirin:** aynı fixture, same fault, same workload, same evidence and same cost horizon. Evidence yoksa iki aday da `HELD`; B otomatik fallback, A otomatik winner değildir.

## 7. Nihai hüküm

### Aday A — Supabase'e yakın Edge API

`HELD / NO WINNER / ADR NOT READY`.

Kısa DB-yakın request için geri alınabilir çalışma adayı olarak tutulabilir; ancak Edge limitleri, queue/worker activation, audit/floor/object bağımsızlığı, commit-time authz, idempotent effect, recall race, end-to-end revoke, restore/exit ve no-owner-debug fixture'ları kapanmadan production high-consequence path açılmaz. Required long work Edge callback/`waitUntil`'a bırakılırsa, direct provider path oluşursa, audit/floor yokken effect commit edilirse veya old restore authority diriltirse ilgili capability `REJECT-IF-UNMITIGATED`.

### Aday B — Managed container API + worker

`HELD / NO WINNER / ADR NOT READY`.

Uzun iş için görünür worker/queue boundary'si bir inceleme avantajıdır; fakat bu, queue delivery'nin canonical effect, container health'in product truth, ayrı provider'ın audit/negative independence veya image rollback'ın data recovery olduğu anlamına gelmez. Network/pool/secret/schema/message compatibility, audit/object/floor, outage, cost, clean-room exit ve no-owner-debug fixture'ları A ile aynı eşikte kapanmadan production high-consequence path açılmaz. Worker/queue durability, direct bypass, restore anti-resurrection veya owner repair hard-fail'i gerçeklenirse ilgili capability `REJECT-IF-UNMITIGATED`; B otomatik seçilmez.

### Ortak karar

**Genel hüküm: `HELD — A/B eşit incelendi / 0 PASS / 0 production winner / ADR not ready`.**

Belgesel öneri düzeltilmeye açıktır; bu nedenle şu an overall `REJECT` değildir. Ancak C-01–C-08 kapanmadan approval, publication, recall/suspension, role/policy, privileged recovery, export/delete veya authoritative object/content mutation positive olarak `ALLOW` edilemez. Adaylardan biri bir hard-fail'i güvenli hold ile çeviremiyorsa o capability `REJECT-IF-UNMITIGATED`; diğer aday bu review ile otomatik kazanan olmaz. Phase-5 ADR, provider/runtime/dil/framework seçimi veya Gate 4 → 5 geçişi için önce eşit fixture evidence, bağımsız audit/recovery ve owner/TCO/operability review gerekir.
