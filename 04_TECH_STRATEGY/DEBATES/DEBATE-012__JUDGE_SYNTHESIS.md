# DEBATE-012 — Internal Operations Web Frontend ve Hosting Judge Sentezi

**Durum:** `USER-APPROVED DEC-0039 / 0 PASS / 4 FRAMEWORK HELD / NO WINNER / ADR NOT READY`  
**Tarih:** `2026-09-19`  
**Kapsam:** `PHASE 4 / NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`

## 1. Teknik olmayan kısa karar

Kavriva'nın şirket içi yönetim yüzeyi tarayıcıda çalışan, masaüstü ağırlıklı bir çalışma alanı olacaktır. Araştırma;
React/Next, Angular, Vue/Nuxt ve Svelte/SvelteKit arasında bugün güvenilir bir kazanan göstermemiştir. Bu nedenle yalnız
popülerlik, AI aşinalığı veya paket sayısıyla framework seçilmeyecektir.

Public SEO gerektirmeyen bu iç uygulama için en sade başlangıç yönü şudur:

> Giriş yapılmış kullanıcıya tarayıcıda çalışan bir çalışma alanı sunulur; ekran dosyaları yönetilen statik/CDN
> dağıtımından gelir, bütün hassas veri ve işlemler Kavriva API üzerinden yürür. SSR, BFF, edge ve container ancak somut
> bir ihtiyaç gösterilirse belirli route/capability için yeniden açılır.

Bu, framework veya hosting sağlayıcısı seçimi değildir. Dört framework eşit `HELD` kalır; gerçek seçim Phase 5'te aynı
görev, tarayıcı, erişilebilirlik, güvenlik, bakım, maliyet ve çıkış kanıtlarıyla yapılır.

## 2. Okunan kanıt ve review sonucu

Judge aşağıdaki paketleri birlikte değerlendirdi:

- requirements synthesis, official-primary research ve failure/TCO research;
- ilk manager proposal;
- iki bağımsız Luna Max adversarial review;
- `WEB-TASK-001..003` no-code task simulation;
- dört aday eşdeğerlik denetimi;
- component/dependency ecosystem tie-break;
- render/hosting tie-break.

Reviewer A, React'in AI aşinalığıyla öne çıkarılmasını ve Vue/Svelte'nin daha düşük kanıtla challenger yapılmasını
reddetti. Reviewer B; session, CSRF/XSS/CSP, stale tab/outcome, cache/service worker, quarantine, deploy, privacy,
owner-support, cost ve clean-room exit kapanmadan hiçbir framework veya hosting biçiminin seçilemeyeceğini gösterdi.
Sonraki eşdeğerlik çalışmaları aynı üç görevi dört aileye uyguladı ve sonucu `0 PASS / 0 REJECT / 4 HELD` olarak
doğruladı.

## 3. Düzeltilen framework hükmü

| Aile | Phase-4 hükmü | Açık kalan ana kanıt |
|---|---|---|
| React + TypeScript; Vite/static veya gerektiğinde Next | `HELD / eşit aday` | exact composition, component closure, cache/server boundary, upgrade ve exit |
| Angular | `HELD / eşit aday` | dense component closure, toolchain/RxJS/major upgrade, AI task consistency ve exit |
| Vue + Nuxt | `HELD / eşit aday` | module/support closure, render/cache sınırı, dense/a11y package BOM ve exit |
| Svelte + SvelteKit | `HELD / eşit aday` | support/major/adapter closure, dense package BOM, AI maintenance ve exit |

React'in “koşullu lider”, Angular'ın “fallback”, Vue/Nuxt ile Svelte/SvelteKit'in ise ancak diğerleri başarısız olursa
açılacak aday olduğu dili geri çekilmiştir. Framework popülerliği veya AI'ın daha çok örnek üretmesi ürün güvenliği,
tasarım tutarlılığı, erişilebilirlik, bakım kolaylığı ya da düşük toplam maliyet kanıtı değildir.

## 4. Düzeltilen render/hosting hükmü

| Biçim | Çalışma sırası | Hüküm |
|---|---:|---|
| CSR-first statik artifact/CDN + Kavriva API | Koşullu başlangıç yönü | `HELD` |
| Same-origin server shell/BFF | İhtiyaç kanıtlanırsa ikinci seçenek | `HELD` |
| Serverless/edge SSR | Route-specific istisna | `HELD` |
| Managed/portable Node container | Operasyon ve exit challenger'ı | `HELD` |

Statik yönün tercih edilme nedeni “ücretsiz” olması değildir. Public SEO gerekmeyen bir iç uygulamada ikinci bir web
sunucusu, SSR cache'i, secret, runtime ve incident yüzeyi eklemeden daha küçük bir başlangıç alanı sunmasıdır. Şu
koşullardan biri kapanmazsa statik yön açılmaz ve otomatik olarak BFF/SSR/container'a da geçilmez:

- session/cookie-or-token sınırı, server-side CSRF/CORS/origin ve XSS/CSP;
- kullanıcıya özel veri ve operation status için private/no-store cache davranışı;
- stale tab, revoke/security epoch, lost response ve `OUTCOME_UNKNOWN` çözümü;
- quarantine-first dosya akışı ve uzun işlerin browser request'inden ayrılması;
- immutable artifact, API N/N-1 uyumu, old-client drain ve forward recovery;
- privacy-safe log/correlation, owner-readable incident/support, bounded cost ve source-untouched clean-room exit.

Service worker varsayılan olarak privileged/offline authority değildir; hassas işlem, rol, audit, recalled data veya
operation status cache'lemez. BFF açılırsa yalnız allowlisted transport/DTO adapter'dır; ürün yetkisi veya ikinci veri
otoritesi olamaz.

## 5. Değişmeyen ürün sözleşmesi

1. Browser, route guard, gizli düğme, framework server action, cache, service worker ve provider paneli ürün otoritesi
   değildir.
2. Hassas işlem her commit'te Kavriva API'de actor/session/epoch, tenant/scope, rol/yetki, exact resource version,
   operation fingerprint, idempotency ve protected audit koşullarıyla yeniden değerlendirilir.
3. Timeout veya cevap kaybı başarı/başarısızlık tahmini üretmez; `OUTCOME_UNKNOWN` ve aynı operation ID ile güvenli
   status lookup kullanılır.
4. Dosya ve dış içerik private quarantine, digest, classification, lineage ve exact scoped handle olmadan aktif/yayınlı
   kullanıma giremez.
5. Büyük tablo, diff ve provenance graph için bounded data, keyboard/screen-reader yolu ve erişilebilir metinsel karşılık
   gerekir. Framework/component iddiası tek başına WCAG kanıtı değildir.
6. Teknik olmayan owner SQL, SSH, raw log, queue surgery, secret, DNS/TLS veya provider-console tamiri yapmaz.

## 6. Tasarım ve çoklu-AI tutarlılık kapısı

Farklı AI'ların ürettiği ekranların birleşince garip görünmemesi framework seçimine bırakılamaz. Phase 5 task sistemi;
approved Phase-3 workspace/screen mimarisini, ortak design token ve component contract'ını, state/copy/focus/density
kurallarını, dosya sahipliğini, traceability graph'ını, reviewer'ı ve görsel + semantik regression kanıtını her web
görevine minimum context pack olarak bağlamalıdır.

Bir AI yalnız sıradaki task dosyasını ve onun açık dependency/context paketini okuyarak çalışabilmeli; proje çapında
gizli karar vermemeli. Task tamamlanması, ilgili acceptance/evidence/review kayıtları kapanmadan “bitti” sayılmamalıdır.

## 7. Phase-5 eşit kanıt kapısı

Dört aday için aynı fixture ile en az şu kanıtlar üretilmeden framework ADR'si açılamaz:

- exact dependency/lock/SBOM/license/support BOM;
- aynı büyük queue/table/diff/graph/form iş yükü;
- gerçek browser, keyboard, screen reader, zoom, Turkish label ve narrow/degraded görünüm;
- stale session/role/epoch, CSRF/XSS/CSP, direct-path/BOLA/IDOR ve response-loss;
- upload/quarantine/preview/SSRF/archive/restore;
- framework/runtime major upgrade, immutable artifact, API/schema/message compatibility ve guarded recovery;
- AI task collision, design consistency ve no-owner handoff;
- normal, incident, upgrade, restore ve exit maliyeti;
- source untouched clean-room rebuild/import ve anti-resurrection.

Bir adayın hard-fail vermesi diğerini otomatik kazanan yapmaz. Direct authority bypass, inaccessible critical path,
stale positive authority, false success, quarantine bypass, effect-before-audit, incompatible rollback, owner technical
repair, unbounded mandatory spend veya unsafe exit görülürse ilgili bileşim `REJECT-IF-UNMITIGATED` olur.

## 8. Kullanıcı tarafından onaylanan karar

Kullanıcının `DEC-0039` altında onayladığı Phase-4 çalışma yönü:

1. Internal Operations tarayıcı ve masaüstü ağırlıklı kalır.
2. Başlangıç render/hosting hipotezi `CSR-first statik artifact/CDN + Kavriva API` olur.
3. SSR, BFF, edge, container ve service worker varsayılan olmaz; yalnız somut gereksinimle yeniden açılır.
4. React/Next, Angular, Vue/Nuxt ve Svelte/SvelteKit arasında Phase 4'te kazanan seçilmez; dördü eşit `HELD` kalır.
5. Framework seçimi Phase 5'te aynı gerçek evidence paketiyle yapılır.
6. API authority, accessibility, design consistency, no-owner-debug, bounded cost ve clean-room exit zorunlu kapıdır.

## 9. Nihai disposition

**Judge sonucu:** `PASS_WITH_CHANGES FOR PHASE-4 DIRECTION / USER-APPROVED DEC-0039`  
**Framework sonucu:** `0 PASS / 0 REJECT / 4 HELD / NO WINNER`  
**Render/hosting sonucu:** `CSR-FIRST STATIC + API = CONDITIONAL DEFAULT / HELD`  
**ADR durumu:** `NOT READY`  
**Gate 4 -> 5:** `CLOSED`

Bu belge framework, exact version, component library, hosting provider, domain, region, plan, hesap, abonelik, ödeme,
kod, prototip, deployment veya Phase-5 ADR onayı değildir.
