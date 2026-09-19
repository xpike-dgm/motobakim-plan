# DEBATE-010 — Kimlik, Oturum ve Ayrıcalıklı Erişim Yönetici Önerisi

Status: `REVIEWED MANAGER PROPOSAL / CORRECTED JUDGE DIRECTION USER-APPROVED VIA DEC-0037`
Date: `2026-09-18`
Scope: `NO-CODE / NO ACCOUNT / NO PURCHASE / ADR NOT READY`

## 1. Teknik olmayan kısa anlatım

Kavriva'da giriş yapmak ile yetkili olmak aynı şey olmayacak. Telefon uygulamasında kullanıcı, hesap açmadan temel
değeri deneyebilecek; profil isterse verisini açık bir kontrolle kalıcı hesaba taşıyacak. Şirket içi tarayıcıda ise
bir kişi giriş yapmış olsa bile eski sekmeyle, eski rolle veya kurtarılmış hesapla içerik onaylayamayacak. Kritik işlem
anında sistem hem kişinin oturumunu hem güncel görev yetkisini yeniden kontrol edecek.

Başlangıçta tüketici hesapları için Supabase Auth en sade yön. Personel tarafında iki yol var: Supabase'in geçiş anahtarı
özelliği kararlı ve test edilmiş hale gelirse aynı sistemi kullanmak; gelmezse yalnız personel için ayrı, geçiş anahtarlı
bir kimlik hizmeti kullanmak. Şimdiden ikinci hizmet satın alınmayacak. Güvenli yöntem hazır değilse kritik personel
işlemi açılmayacak; güvenlik standardı düşürülmeyecek.

## 2. Devralınan kararlar

- `DEC-0026`: privileged kimlik phishing-resistant olmalı; hassas işlem fresh step-up ve commit-time authorization ister.
- `DEC-0034`: browser ve Flutter hassas işlemleri Kavriva API'sinden geçer; Internal Operations online-authoritative'dir.
- `DEC-0035`: backend Supabase-merkezli çalışma yönündedir ama provider doğrudan ürün yetkisi değildir.
- `DEC-0036`: tüketici offline verisi seçili görev paketidir; offline approval/publish/role authority yoktur.
- `DEC-0029/0030`: teknik olmayan tek sahip SQL/SSH/debug veya gizli işletim yükü taşımamalıdır; maliyet açık olmalıdır.

## 3. Ortak mimari — iki adayda da değişmez

1. **Stable Kavriva principal:** Provider user ID, yerel installation ID, ürün profili, personel actor ve service/AI
   identity ayrı kayıtlardır. Sağlayıcı değişse de geçmiş actor ve audit kimliği kaybolmaz.
2. **Authentication ≠ authorization:** IdP yalnız oturum/kimlik kanıtı verir. API güncel action, object, tenant,
   classification, role/grant, competence, independence, policy version ve security epoch ile `ALLOW/DENY/HELD` verir.
3. **Security epoch:** Şifre/factor kurtarma, hesap compromise, privileged revoke veya global logout eski session,
   refresh/recovery artifact ve pending high-consequence authority'yi geçersiz kılar.
4. **Sensitive session check:** Hassas endpoint verilmiş JWT'ye tek başına güvenmez; current account/session ve epoch
   kontrol eder. Role/claim yalnız hızlı ipucudur.
5. **Account-light:** İlk değer için server hesabı şart değildir. Yerel installation principal, kalıcı profile açık
   önizleme + verified re-auth + conflict hold ile bağlanır; e-posta benzerliği silent merge nedeni değildir.
6. **Privileged browser:** Approval, publish, recall, export, role/policy, recovery ve audit mutation offline veya stale
   sayfada çalışmaz. Fresh phishing-resistant doğrulama ve işlem-bağlı step-up gerekir.
7. **Recovery:** Tüketici self-service olabilir; privileged recovery normal girişten zayıf olamaz, dual-control veya
   separately governed time-limited break-glass ister ve kendisi approval/publish yetkisi vermez.
8. **Protected audit:** Auth log ayrı; Kavriva product audit ayrı ve korunmuş kanıttır. Actor, session assurance, grant,
   policy, operation, object/version, result ve effect zinciri tutulur.
9. **AI sınırı:** AI task-scoped, kısa ömürlü service identity kullanır; provider owner, service role, SQL/SSH,
   approval/publish/recovery authority taşımaz.
10. **No-owner-debug:** Failure, revoke ve outage anlaşılır `HELD`, `ACCESS_DENIED`, `OUTCOME_UNKNOWN` veya
    `RECOVERY_REQUIRED` durumu ve güvenli sonraki adımla görünür.

## 4. Aday A — Tek Supabase Auth, privileged aktivasyon kapısı

### Bileşim

- Consumer profile: Supabase Auth.
- Account-light: varsayılan olarak yalnız Kavriva local installation principal; server anonymous user ancak gerçekten
  server-bound bir özellik gerekirse ayrı restrictive policy ile.
- Internal Operations: Supabase Auth; ancak high-consequence production yalnız passkey/WebAuthn özelliği stable/GA,
  browser akışı ve recovery/revoke fixture'ları kabul edilmişse açılır.
- TOTP, SMS veya magic link phishing-resistant yerine geçmez.

### Güçlü taraflar

- Tek kimlik control plane'i ve Supabase-merkezli backend ile en düşük başlangıç karmaşıklığı.
- Flutter + browser desteği ve profile/anonymous/link primitive'leri mevcut.
- Ek IdP aboneliği ve ikinci issuer mapping'i ilk günden gerekmez.

### Zayıf taraflar / hard hold

- Supabase passkeys `2026-05-28` itibarıyla beta/experimental. Bu durum sürerken privileged production `HELD`dir.
- User silme/ban verilmiş access JWT'yi anında etkisizleştirmez; sensitive session lookup + epoch uygulama sorumluluğudur.
- Tek provider kesintisi hem consumer login'i hem personel step-up'ı etkiler; bağımsız negative suspension yolu ayrıca gerekir.

## 5. Aday B — Supabase consumer + ayrı privileged IdP

### Bileşim

- Consumer profile ve account-light sınırı A ile aynıdır.
- Internal Operations girişinde passkey/WebAuthn destekli ayrı managed IdP kullanılır.
- Clerk ve Auth0 mevcut kısa liste/challenger'dır; bu belge ikisinden birini seçmez.
- API iki issuer'ı stable Kavriva principal'a map eder; global security epoch ve Kavriva authorization ikisine de uygulanır.

### Güçlü taraflar

- Supabase passkey beta takviminden bağımsız privileged production yolu oluşturabilir.
- Personel kimliği tüketici saldırı yüzeyinden ve kullanıcı hacminden daha açık ayrılabilir.

### Zayıf taraflar / hard hold

- İkinci aylık ücret, ikinci outage/support/recovery ve iki sağlayıcı arasında logout/revoke/actor mapping yükü.
- Clerk'in Flutter olgunluğu consumer için uygun görünmediğinden kapsam yalnız browser internal olmalıdır; Auth0/Clerk
  exact plan ve recovery semantiği fixture olmadan `PASS` sayılamaz.
- İki IdP güvenliği otomatik yükseltmez; Kavriva epoch veya mapping bozuksa revoke boşluğu büyür.

## 6. Eşit no-code senaryo sonucu

Bu sonuçlar yalnız belge incelemesidir; hiçbiri üretim `PASS` değildir.

| Senaryo | Aday A | Aday B | Ortak kabul kapısı |
|---|---|---|---|
| Çalınmış access token | `HELD` | `HELD` | Sensitive API current session + epoch kontrolü sonrası deny |
| User silindi/banlandı, JWT canlı | `HELD` | `HELD` | Provider fark etmeksizin short JWT + current session/account check |
| Açık sekmede eski rol | `HELD` | `HELD` | Commit-time grant/policy/epoch recheck |
| E-posta hesabı ele geçirildi | `HELD` | `HELD` | Privileged işlem passkey + fresh step-up; email-only yetersiz |
| MFA/passkey cihazı kayıp | `HELD` | `HELD` | Controlled recovery, eski session/pending authority iptali |
| Local kullanıcı profile geçiyor | `HELD` | `HELD` | Scope preview, verified target, no-silent-merge, conflict ledger |
| Telefon offline iken revoke | `HELD` | `HELD` | Safe read only; online olunca reconcile; privileged offline yok |
| Son admin kilitlendi | `HELD` | `HELD` | Dual/independent recovery; positive work hold; no SQL/SSH |
| IdP kesintisi | `HELD` | `HELD` | Consumer safe read; Internal positive actions hold; negative path independent |
| Cross-tenant ID değişimi | `HELD` | `HELD` | API object/tenant/scope check + defense-in-depth RLS |
| Identity merge/split | `HELD` | `HELD` | Stable principal; immutable mapping; audit attribution preserved |
| AI geniş credential istiyor | `HELD` | `HELD` | Task-scoped service identity; no provider owner/service_role |
| Provider değiştirme | `HELD` | `HELD` | User/principal/audit export + clean-room import/reconciliation |
| Phishing-resistant privileged login | `HELD`: beta kapısı | `HELD`: exact IdP/plan/test | Stable feature + real browser/recovery fixture |
| Owner monthly cost | Daha düşük aday | Daha yüksek aday | Kur/vergi/SMTP/log/support dahil satın alma öncesi toplam |

Belge düzeyinde iki adayın sonucu: `0 PASS / 15 HELD / 0 REJECT`. Aday B güvenlik özelliğini daha erken sağlayabilir,
ama iki-system recovery ve maliyetini kanıtlamadan üstün sayılamaz. Aday A daha sade ve ucuzdur, fakat beta passkey ile
privileged production açamaz.

## 7. Yönetici önerisi — Koşullu A, hazırlıklı B

Phase 4 çalışma yönü olarak:

1. **Consumer identity:** Supabase Auth lider çalışma yönü.
2. **Account-light:** ilk değer local installation principal ile; gereksiz server anonymous account oluşturma yok.
3. **Provider-neutral core:** Kavriva principal, authorization tuple, security epoch, protected audit ve recovery state
   provider SDK'sına gömülmez.
4. **Internal Operations:** geliştirme/planlama Aday A'ya göre sade tutulabilir; high-consequence production activation
   ayrı kontrol kapısıdır.
5. **Activation kapısı:** Supabase passkey stable/GA + acceptance fixture geçerse Aday A sürer. Geçmezse Aday B,
   yalnız Internal Operations için dar bir ayrı IdP olarak devreye alınmak üzere eşit kanıtla değerlendirilir.
6. **Güvenlik bütçeye göre düşmez:** Ek IdP bütçeye sığmıyorsa TOTP/magic link ile kural gevşetilmez; privileged
   production `HELD` kalır veya yalnız low-risk/read-only operasyon açılır.

Bu öneri bugün ikinci IdP seçmez, hesap açmaz veya ödeme yapmaz. Ayrıca Supabase passkey'in gelecekte GA olacağını garanti
etmez. Ama iki sonucu da hazırlıklı hale getirir ve daha sonra kimlik sağlayıcısı değiştirmeyi bütün ürünü yeniden yazma
zorunluluğuna dönüştürmez.

## 8. Phase 5+ gerçek kabul kanıtları

- Android deep-link/PKCE, reinstall, lost phone, local-key ve profile migration gerçek cihaz fixture'ı.
- Browser passkey register/login/step-up, RP-ID/origin, accessibility ve factor-loss recovery fixture'ı.
- Revoke/delete/ban sonrası çalınmış tokenla sensitive endpoint negatif testi.
- Role/policy/competence change sırasında açık sekme ve in-flight operation testi.
- Last-admin/dual-control recovery; eski session ve pending authority'nin kapandığı kanıt.
- IdP outage, lost response ve independent negative suspension testi.
- İki issuer seçilirse global logout/epoch/actor mapping ve provider-by-provider incident runbook.
- Auth data + Kavriva principal + protected audit clean-room export/import provası.
- Güncel plan/fiyat/kur/vergi/SMTP/SMS/log/support ve overage toplamı; owner-readable cost stop.

## 9. Kullanıcı kararından sonra kayıt altına alınabilecek yön

Kullanıcı onaylarsa yeni karar şunu bağlayabilir: consumer Supabase Auth; account-light local-first; provider-neutral
Kavriva identity/authorization/session epoch; privileged production için phishing-resistant stable feature ve gerçek test
kapısı; Supabase bu kapıyı karşılamazsa internal-only ayrı IdP değerlendirmesi. Exact provider, plan, session süreleri,
factor/recovery ayrıntıları, kod ve satın alma açık kalır.
