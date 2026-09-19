# DEBATE-010 — Kimlik Sağlayıcısı Birincil Kaynak Karşılaştırması

Status: `PHASE-4 RESEARCH / NO-CODE / PROVIDER NOT SELECTED`
Date: `2026-09-18`
Research cut: `2026-09-18`

## 1. Karar sorusu ve değişmeyen sınır

Bu araştırma, Kavriva'nın tüketici hesabı ile tarayıcı tabanlı Internal Operations personel girişini hangi yönetilen
kimlik hizmeti bileşimiyle planlaması gerektiğini inceler. Sağlayıcı yalnız kimliği ve oturumu kanıtlayan bir katmandır.
Onay, yayın, recall, tenant, teknik yeterlilik, bağımsızlık ve veri kapsamı yetkisi her durumda Kavriva API'sinde güncel
durumla yeniden değerlendirilir.

Bu dosya kod, hesap açılışı, ücretli plan, satın alma, üretim güvenlik kanıtı veya ADR değildir. Fiyatlar ve beta/SDK
durumları değişkendir; satın alma ve Phase-5 ADR öncesi yeniden doğrulanır.

## 2. Ortak zorunluluklar

- Flutter Android-first tüketici uygulaması; iOS sonra; Internal Operations browser tabanlıdır.
- İlk ürün değeri hesap duvarına bağlı değildir. Yerel/hesap-hafif kullanım ile kalıcı profil aynı kimlik değildir.
- Profil bağlama ve hesap birleştirme açık onay, yeniden doğrulama, çakışma incelemesi ve geri alınabilir kanıt ister.
- Privileged Internal Operations işlemleri phishing-resistant giriş, fresh step-up, current session/account kontrolü ve
  server-side revocation ister.
- Silme, ban veya rol değişimi verilmiş JWT'yi anında yok etti varsayılmaz. Hassas commit güncel security epoch,
  session ve grant durumunu kontrol eder.
- `user_metadata`, browser düğmesi, cached claim, provider dashboard rolü veya RLS tek başına Kavriva yetkisi değildir.
- Teknik olmayan sahipten SQL, SSH, token onarımı veya provider log teşhisi beklenmez.

## 3. Resmi kaynaklardan doğrulanan gerçekler

### 3.1 Supabase Auth

- Flutter paketi Android, iOS ve web'i destekler; email/password, magic link/OTP, OAuth, SAML, anonymous user ve identity
  linking yolları vardır. Bu, Supabase-merkezli backend yönüyle en az ek bileşen kullanan seçenektir. [S1][S2]
- Anonymous user `authenticated` veritabanı rolünü kullanır ve `is_anonymous` ile ayrıştırılmalıdır. Sign-out, veri temizleme
  veya başka cihaz sonrası aynı anonymous hesaba geri dönemez. Kavriva bu nedenle account-light yerel kimliği otomatik
  olarak server anonymous user ile eşitlememelidir. [S2]
- Oturum access JWT + refresh token ile temsil edilir. Sign-out session kaydını kaldırır; fakat silinmiş kullanıcının
  verilmiş access JWT'si süresi bitene kadar çalışabilir. Hassas işlemlerde `session_id` kaydının ayrıca doğrulanması
  resmi olarak önerilir. [S3][S4]
- TOTP ve telefon tabanlı MFA ile `aal1/aal2` ayrımı vardır; MFA'nın API/RLS katmanında ayrıca uygulanması gerekir. TOTP
  phishing-resistant değildir. [S5]
- WebAuthn/passkey desteği `28 Mayıs 2026` tarihli beta/experimental özelliktir; API'nin bildirim olmadan değişebileceği
  açıkça belirtilir. Dart iki-aşamalı API yayımlanmış olsa da beta statüsü privileged üretim yolunu tek başına kanıtlamaz.
  [S6][S7]
- 2026-09-18 fiyat sayfasında Free 50.000 MAU; Pro başlangıcı aylık USD 25 ve 100.000 MAU dahil görünür. Session timeout,
  single-session, daha uzun Auth audit log ve leaked-password protection plan bağımlıdır. Telefon MFA ek ücreti vardır.
  Fiyat ve kur satın almada yeniden kontrol edilmelidir. [S8]

### 3.2 Firebase Authentication / Identity Platform

- Flutter için first-party dokümantasyon; anonymous sign-in ve mevcut anonymous hesabı kalıcı sağlayıcıya linkleme vardır.
  Account-light'tan profile geçiş primitive'i güçlüdür, fakat Kavriva veri merge/çatışma kararını yine kendisi verir. [F1][F2]
- Flutter MFA dokümanı Identity Platform yükseltmesiyle SMS tabanlı MFA'yı anlatır ve aynı doküman SMS'in kullanılmamasını
  öneren güvenlik uyarısı taşır. Bu, privileged phishing-resistant gereksinimini tek başına kapatmaz. [F3]
- Token revoke mümkündür; resmi dokümana göre mevcut ID token doğal süresi dolana kadar canlı kalabilir ve ciddi hesap
  değişimlerinde `auth_time`/revoke zamanı server-side kontrol edilmelidir. [F4]
- Base Auth ile Identity Platform fiyat ve limitleri farklıdır. Resmi sayfa Blaze için email/social/anonymous/custom
  kullanıcılarında 50.000 MAU ücretsiz katman bildirir; SMS, telefon, diğer Google Cloud kullanımı ve Identity Platform
  özellikleri ayrıca değerlendirilir. [F1]
- Supabase-merkezli veri omurgasının yanında ikinci genel tüketici platformu; iki kontrol düzlemi, iki incident/cost yolu
  ve ek token doğrulama yükü doğurur. Flutter uygunluğu bunu otomatik olarak daha düşük toplam sahiplik maliyeti yapmaz.

### 3.3 Clerk

- Web tarafında passkey/WebAuthn, MFA, session yönetimi ve prebuilt/custom akışlar güçlüdür. Güncel resmi fiyat sayfası
  passkey ve MFA'yı Pro özelliği olarak gösterir; Pro USD 25/ay veya yıllık ödemede USD 20/ay başlangıcı ve 50.000 MRU
  dahil bilgisi verir. Hobby planında passkey/MFA yoktur. MRU, MAU ile aynı ölçü değildir. [C1][C2]
- Resmi changelog Flutter SDK'yı Mart 2025'te public beta olarak duyurmuştur; güncel SDK referansı Flutter'ı community-
  maintained listesinde gösterir. Bu olgunluk belirsizliği, Flutter tüketici kimliğini Clerk'e taşımayı zayıflatır. [C3][C4]
- Browser Internal Operations için ayrı, küçük kullanıcı sayılı IdP adayı olarak değerlidir; ancak iki issuer/session/recovery
  sistemi ve Pro aboneliği ekler. Passkey kullansa bile Kavriva step-up, current grant ve recovery security epoch'ini yine
  kendi API'sinde uygular.

### 3.4 Auth0

- Resmi fiyat sayfası Free planda 25.000 MAU, passwordless ve passkey; Essentials'ta Pro MFA, audit log streaming ve
  ayrı prod/dev ortamları; Professional'da ek güvenlik özellikleri gösterir. 2026-09-18 görünen B2C Essentials başlangıcı
  500 MAU için USD 35/ay, Professional USD 240/aydır. Plan/MAU kademesi satın almada yeniden kontrol edilmelidir. [A1]
- Flutter için resmi SDK/quickstart vardır; ancak Auth0'nun resmi geliştirici merkezi Flutter SDK'yı beta ve production
  için önerilmeyen durumda işaretler. Bu, Internal Operations'ın browser Universal Login adaylığını bozmaz; Auth0'ı
  Flutter tüketici olgunluğu kazananı yapmaz. [A2][A3]
- Passkey varlığı tek başına recovery, factor reset, session revoke veya transaction-bound step-up'ın Kavriva koşullarını
  karşıladığını kanıtlamaz. Exact Auth0 action/flow, plan ve logout/revoke semantiği gerçek fixture ile sınanmalıdır.
- Tüm tüketici kimliğini Auth0'a taşımak Supabase entegrasyon avantajını azaltır ve başlangıç maliyetini büyütür; yalnız
  privileged browser kullanıcıları için ayrı issuer olarak kullanılması daha dar ama yine ek operasyonludur.

## 4. Eşit karşılaştırma matrisi

| Ölçüt | Supabase Auth | Firebase Auth | Clerk | Auth0 |
|---|---|---|---|---|
| Flutter tüketici olgunluğu | Güçlü ve mevcut backend yönüyle uyumlu | Güçlü first-party | `HELD`: Flutter beta/community sinyali | `HELD`: resmi Flutter SDK beta; ayrı platform yükü |
| Browser Internal Operations | Uygun; mevcut stack ile sade | Uygun; ikinci genel platform | Güçlü web UX | Güçlü ve olgun CIAM |
| Account-light/profile primitive | Anonymous + link; yanlış merge yine Kavriva sorunu | Anonymous + link; yanlış merge yine Kavriva sorunu | Provider hesap akışları; local domain migration ayrı | Provider hesap akışları; local domain migration ayrı |
| Phishing-resistant privileged auth | Passkey var ama `BETA/EXPERIMENTAL`; TOTP yeterli değil | Flutter MFA resmi yolu SMS ağırlıklı; `HELD` | Passkey + MFA Pro; web adayı | Passkey mevcut; exact step-up/plan `HELD` |
| Immediate sensitive revoke | `session_id` + Kavriva epoch şart | revoke time + Kavriva epoch şart | Provider revoke + Kavriva epoch şart | Provider revoke + Kavriva epoch şart |
| Tek sistem / owner yükü | En düşük bileşen sayısı | Supabase yanında ek control plane | Consumer'da yüksek; internal-only orta | Consumer'da yüksek; internal-only orta |
| Başlangıç liste fiyatı sinyali | Backend Pro ile birlikte USD 25/ay başlangıç | Kullanıma/Identity Platform'a bağlı | Pro USD 25/ay; yıllık USD 20/ay | Essentials USD 35/ay başlangıç |
| Vendor exit | User/identity export var; hash/claim/session geçişi ayrıca kanıtlanır | Export/migration ayrıca kanıtlanır | Export iddiası var; session/credential taşınabilirliği ayrı | Export/migration plan/connection bağımlı |
| Bu aşamadaki rol | Tüketici için lider; internal için koşullu | Challenger/reference | Internal-only challenger | Internal-only challenger |

Hiçbir hücre `PASS` değildir. Gerçek redirect/deep-link, revoke, stolen token, factor loss, provider outage, merge/split,
accessibility ve clean-room migration kanıtları Phase 5+ fixture'larıdır.

## 5. İki mimari ailesi

### A — Tek sağlayıcı, kontrollü aktivasyon

- Tüketici profili ve Internal Operations girişinde Supabase Auth kullanılır.
- Account-light kullanım varsayılan olarak Kavriva yerel installation principal'ıdır; server anonymous identity yalnız
  gerçekten server-bound bir özellik gerekirse ve ayrı restrictive policy ile açılır.
- Privileged production yetkisi, Supabase passkey beta statüsünden çıkıp gerekli browser/Dart/recovery/revoke testlerini
  geçene kadar açılmaz. TOTP veya magic link phishing-resistant yerine geçirilmez.
- Artı: tek control plane, düşük entegrasyon ve başlangıç maliyeti.
- Eksi: passkey kararlılığı gecikirse Internal Operations'ın high-consequence production açılışı `HELD` kalır.

### B — Ayrılmış tüketici ve personel kimliği

- Tüketici profili Supabase Auth'ta kalır.
- Internal Operations personeli, olgun passkey/WebAuthn destekli ayrı managed IdP'de tutulur; Clerk ve Auth0 güncel
  kısa listedir, seçim değildir.
- Kavriva API iki güvenilir issuer'ı stable Kavriva principal'a map eder; provider rol/claim'i doğrudan yetki olmaz.
- Artı: Supabase passkey beta takviminden bağımsız privileged güvenlik yolu.
- Eksi: ikinci ücret, ikinci outage/recovery/support alanı, issuer-mapping ve global revoke karmaşıklığı.

## 6. Araştırma sonucu

1. **Consumer lideri:** Supabase Auth; mevcut Supabase-merkezli yön, first-party Flutter desteği ve daha az owner yükü
   nedeniyle. Bu, kod/plan/satın alma onayı değildir.
2. **Privileged Internal Operations kararı koşullu kalmalıdır:** Supabase passkey bugün beta olduğu için tek-sistem
   mimarisi high-consequence production'a hazır sayılmaz.
3. **En geri döndürülebilir plan:** Kavriva principal/authorization/session-security-epoch sözleşmesini provider-neutral
   kurmak; production privileged activation kontrol noktasında Supabase passkey stable + test edilmişse A'yı, değilse
   yalnız Internal Operations için B'yi değerlendirmek.
4. **Firebase genel finalist değildir:** Flutter gücü vardır fakat Supabase yanında ikinci genel platform yükü ve
   privileged phishing-resistant açığı bu proje için üstünlük üretmez.
5. **Clerk/Auth0 bugün yalnız internal-only challenger'dır:** Clerk'in Flutter olgunluğu consumer için; Auth0/Clerk'in
   maliyet ve ikinci-control-plane yükü solo owner için açık `HELD`dir.

## 7. Satın alma/ADR öncesi zorunlu yeniden kontrol

- Passkey özelliğinin GA/stable durumu, Flutter/browser SDK desteği ve breaking-change politikası.
- Kayıp factor/last-admin recovery'nin eski oturumları ve pending authority'yi gerçekten iptal etmesi.
- Stolen access token ile provider revoke sonrası Kavriva sensitive API sonucu.
- İki issuer varsa tek global security epoch, logout-all, audit actor mapping ve IdP outage davranışı.
- Liste fiyatı, vergi, döviz, MAU/MRU, SMTP/SMS, log retention, support ve overage toplamı.
- User/identity export, password/passkey taşınabilirliği ve clean-room migration kanıtı.
- Android deep link/PKCE, iOS-later parity, browser origin/RP-ID ve accessibility testleri.

## 8. Resmi kaynaklar

- [S1 — Supabase Flutter quickstart](https://supabase.com/docs/guides/getting-started/quickstarts/flutter)
- [S2 — Supabase anonymous sign-ins](https://supabase.com/docs/guides/auth/auth-anonymous)
- [S3 — Supabase user sessions](https://supabase.com/docs/guides/auth/sessions)
- [S4 — Supabase user management](https://supabase.com/docs/guides/auth/managing-user-data)
- [S5 — Supabase MFA](https://supabase.com/docs/guides/auth/auth-mfa)
- [S6 — Supabase passkeys documentation](https://supabase.com/docs/guides/auth/passkeys)
- [S7 — Supabase passkeys beta changelog, 2026-05-28](https://supabase.com/changelog/46458-passkeys-for-supabase-auth-beta)
- [S8 — Supabase pricing](https://supabase.com/pricing)
- [F1 — Firebase Authentication](https://firebase.google.com/docs/auth/)
- [F2 — Firebase Flutter account linking](https://firebase.google.com/docs/auth/flutter/account-linking)
- [F3 — Firebase Flutter MFA](https://firebase.google.com/docs/auth/flutter/multi-factor)
- [F4 — Firebase manage sessions](https://firebase.google.com/docs/auth/admin/manage-sessions)
- [C1 — Clerk pricing](https://clerk.com/pricing)
- [C2 — Clerk sign-in options and passkeys](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options)
- [C3 — Clerk Flutter SDK public beta changelog](https://clerk.com/changelog/2025-03-26-flutter-sdk-beta)
- [C4 — Clerk SDK reference](https://clerk.com/docs/reference/overview)
- [A1 — Auth0 pricing](https://auth0.com/pricing)
- [A2 — Auth0 Flutter quickstart](https://auth0.com/docs/quickstart/native/flutter)
- [A3 — Auth0 Flutter SDK](https://developer.auth0.com/resources/libraries/flutter)
