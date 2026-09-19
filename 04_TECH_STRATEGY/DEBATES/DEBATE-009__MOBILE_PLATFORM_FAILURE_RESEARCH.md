# DEBATE-009 — Mobile Platform Failure Research

Durum: `BAĞIMSIZ RESMİ PLATFORM FAILURE RESEARCH / NO-CODE / PROVIDER-NEUTRAL / ADR DEĞİL`  
Tarih: `2026-09-18`  
Kapsam: `Flutter Android-first / iOS-later consumer-mobile yönü`

## 1. Kısa hüküm

Bu araştırma bir prototip, kütüphane seçimi, provider seçimi, uygulama kodu veya Phase-5 ADR değildir. Android,
iOS ve Flutter/Dart’ın kendi resmi belgeleri birlikte okunduğunda şu sınır kesinleşir:

- Flutter yaşam döngüsü bildirimi, Android/iOS arka plan planlaması, cihaz saati, OS backup/restore, key store erişimi
  veya network bağlantısı hiçbir zaman tek başına kanonik doğruluk kanıtı değildir.
- Uygulama süreci bellek baskısı, Doze/low-power, telefon görüşmesi, force-quit, ani güç kesilmesi veya OS kararıyla
  beklenmedik anda durabilir. `onPause`, `onStop`, `didChangeAppLifecycleState` veya benzeri bir callback’in mutlaka
  geleceği varsayılamaz.
- Yerel veri; dayanıklı kullanıcı işi, bekleyen idempotent operasyon, paket manifesti ve güvenli anahtar durumu olarak
  açıkça ayrılmalıdır. Geçici dosya/cache hiçbir kritik safety, recall, authorization veya accepted-operation otoritesi
  olamaz.
- İndirme veya senkronizasyon ancak stage → manifest/digest/dependency doğrulama → atomic promote sınırından sonra
  kullanılabilir sayılmalıdır. Yarım, karışık, eski veya bozuk nesne kullanıcıya “tamamlandı” diye gösterilemez.
- OS backup/restore ve uninstall/reinstall bir kurtarma mekanizmasıdır; güncel yetki, recall, silme, revoke, suspension
  veya kabul edilmiş operasyon tabanını yeniden dirilten bir authority değildir.
- Background execution en iyi ihtimalle dayanıklı bir kuyruğu ilerletme fırsatıdır; correctness için önkoşul yapılamaz.
  Kullanıcıya `bekliyor`, `ertelendi`, `yeniden doğrulanıyor`, `başarısız`, `çatışma`, `bilinmiyor` ve `tamamlandı`
  durumları açık ve erişilebilir biçimde gösterilmelidir.
- Android-first, iOS sorumluluğunu ortadan kaldırmaz. Android release lane’i önce kapanabilir; iOS ikinci lane’i aynı
  veri sürekliliği, lifecycle, accessibility, recovery ve release sözleşmesini gerçek cihazlarda kanıtlamadan açılmaz.

Sonuç: Flutter, `DEC-0033` uyarınca çalışma yönü olarak kalabilir; ancak platform belgeleri Flutter’ın kendisinin
`DEC-0034` içindeki durable outbox, bounded package, migration, key continuity, anti-resurrection veya accessibility
kanıtını otomatik verdiğini göstermez. Bu kapanışlar uygulamanın provider-neutral sözleşmeleri ve iki platforma ait
kanıt planı olarak tasarlanmalıdır.

## 2. Araştırma yöntemi ve sınırlama

Resmi Android Developers, Apple Developer Documentation ve Flutter/Dart API belgeleri 2026-09-18 tarihinde kontrol
edildi. Aşağıdaki ayrım kullanıldı:

| Etiket | Anlamı |
|---|---|
| `CONFIRMED` | Resmi belgenin doğrudan söylediği platform mekanizması veya sınır. |
| `INFERRED` | Bu mekanizmadan Kavriva’nın safety/data/recovery sözleşmesine çıkan provider-neutral sonuç. Üretim kanıtı değildir. |
| `OPEN` | Resmi mekanizma mevcut olsa da cihaz/OS/build/veri matrisiyle ayrıca kanıtlanması gereken konu. |
| `REJECT` | Güvenli kapanış için kabul edilemeyecek yaklaşım. Adayın ağırlıklı puanıyla telafi edilemez. |

Bu metin, resmi API’lerin varlığını ürün gereksiniminin tamamının karşılandığı şeklinde yorumlamaz. Android’de resmi bir
arka plan API’sinin bulunması, işin belirli sürede çalışacağını; iOS’ta background URLSession bulunması, kullanıcının
force-quit ettiği uygulamanın otomatik yeniden başlayacağını; Flutter’da state restoration bulunması, kanonik local
database’in kurtarıldığını kanıtlamaz.

## 3. Bağlayıcı kararlar ve ortak fixture

Araştırma aşağıdaki kararları değiştirmez, onları mobil failure sınırına çevirir:

- `DEC-0023`: offline indirme seçili motorcycle + task kapsamındaki en küçük güvenli paket olmalı; full library, ilgisiz
  motorcycle veya kullanılmayan media varsayılan olarak inmemeli; büyük cellular transfer explicit user control olmadan
  başlamamalı.
- `DEC-0024`: stale, unknown, incompatible old client, mixed package, restored backup veya time anomaly yeni positive
  authority üretemez; Internal Operations approve/publish/recall/role mutasyonları online-authoritative kalır.
- `DEC-0031`: tüm mobil adaylar aynı fixture, aynı S1–S15 karşılaştırma ailesi, aynı cihaz/network cohort’u ve aynı
  `PASS/HOLD/REJECT` kuralı ile değerlendirilir; gerçek cihaz ve TalkBack/VoiceOver kanıtı simülatör iddiasıyla ikame
  edilemez.
- `DEC-0033`: Flutter çalışma yönü; Android ilk lane, iOS sonraki lane; platform-channel/generated/native etkileri
  görünür olmalı; kritik capability’nin sahipsiz veya güvenli native fallback’siz plugin bağımlılığı reversal trigger’dır.
- `DEC-0034`: domain başına kanonik transactional authority; server/API mediation; bounded versioned offline package;
  durable identified operations; current/history/protected-audit/object-media ayrımı; restore/migration için
  non-restorable negative/security/deletion/accepted-operation floor.
- `DEC-0035`: managed Supabase-centered fiziksel yön bu mobil sınırları gevşetmez. Flutter/browser genel canonical DB veya
  object authority taşımaz; API boundary, backup/exit, quarantine ve anti-resurrection koşulları aynıdır. Hiçbir backend,
  local storage kütüphanesi veya ücretli servis bu dosyada seçilmemiştir.

Karşılaştırma fixture’ı:

- compact selected-task package: hedef en fazla `12 MB`;
- optional high-resolution media: ayrı, en fazla `150 MB`;
- cellular explicit confirmation eşiği: `25 MB` üstü;
- default offline-content cache fixture’ı: `250 MB`;
- unrelated catalog: `2 GB`, varsayılan olarak indirilmeyecek negative test;
- 3/10 motorcycle, 250/2.000 history/evidence, 50/500 photo, 20/200 pending change ve 3/30 deliberate conflict;
- stable Wi-Fi, ordinary cellular, 1 Mbps/300 ms/%5 packet-loss cellular, transfer sırasında bağlantı kesilmesi,
  72 saat offline, background/lock/call/process termination ve clock change/restore profilleri.

`12 MB`, `150 MB`, `25 MB`, `250 MB` ve `2 GB` burada yalnızca eşit Phase-4 comparison constants’tır; final product
limitleri değildir. Android Auto Backup’ın resmi `25 MB/app user` backup kotası, Kavriva’nın `25 MB cellular confirmation`
fixture’ı ile aynı şey değildir ve ürün limiti olarak alınamaz.

## 4. Resmi platform bulguları

| Alan | `CONFIRMED` resmi mekanizma | Kavriva için `INFERRED` sınır |
|---|---|---|
| Android process lifetime | Android process’i sistem bellek geri kazanımı için her an sonlandırabilir; cached process’te `onDestroy()` garanti değildir. [A1] | Commit edilmeyen iş kaybolabilir. Lifecycle callback yalnızca yardımcı sinyaldir; dayanıklı operation state’in yerine geçemez. |
| Flutter lifecycle | Flutter, tüm lifecycle bildirimlerinin her zaman gelmeyeceğini; kill signal, task manager, güç kesintisi gibi durumlarda state’lerin atlanabileceğini söyler. [F1] | `paused`/`inactive`/`detached` callback’ine güvenerek son anda veri yazmak `REJECT`tir. |
| Android app-specific storage | External app-specific dosyalar uninstall’da kaldırılır; removable storage erişilebilirliği de garanti değildir. [A2] | Reinstall sonrası yerel kimlik, pending work veya media varmış gibi davranılamaz; indirme tekrar üretilebilir olmalıdır. |
| Android Auto Backup | Çoğu internal file/database/shared preference otomatik backup’a girer; cache/code-cache/no-backup hariçtir; app başına 25 MB kotası vardır; restore install sırasında gerçekleşebilir; backup hiç oluşmayabilir. [A3] | Backup seçimi, kapsamı, kota ve restore generation’ı doğrulanmadan “tam kurtarma” denemez. Backup’tan authority geri gelmez. |
| iOS file locations | `Documents` ve `Application Support` kalıcı/support data için; `Caches` ve `tmp` purge edilebilir ve yeniden üretilebilir olmalıdır. Documents/Application Support varsayılan backup davranışına sahiptir. [P1][P2][P3] | Critical closure purgeable alana konamaz. Backup kapsamı ve kullanıcı görünürlüğü data classification ile eşleştirilir. |
| Atomic file operations | Android `AtomicFile` yeni dosyaya yazıp başarıdan sonra rename eder; locking sağlamaz. Apple atomic write bütününü ya kaydeder ya da başarısız olur. Dart `File.writeAsBytes` varsayılan olarak mevcut dosyayı truncate eder. [A9][P11][F3] | Platform primitive’i ancak manifest/digest/lock/transaction tasarımıyla birlikte yeterlidir. Ham Dart overwrite `REJECT`tir. |
| Background / power | Android Doze/App Standby network/JobScheduler işlerini erteleyebilir; persistent-work API’leri constraint ve retry sağlar ama zaman garantisi vermez. [A4][A5] | Background yalnızca best-effort reconciliation/transfer yardımcısıdır; safety authority veya recall immediacy olamaz. |
| iOS background | iOS uygulamayı background’a aldıktan kısa süre sonra suspend edebilir; background URLSession transferi ayrı süreçte sürdürebilir, fakat kullanıcı force-quit ederse transfer iptal olur ve app otomatik relaunch edilmez. [P4][P5] | Foreground’da da çalışabilen resumable state gerekir; force-quit sonrası “tamamlandı” iddiası yapılamaz. |
| Network truth | Android `INTERNET` yalnızca yapılandırılmış erişimi gösterir; `VALIDATED` bile ani kaybı garanti etmez; `NOT_METERED` ve capability snapshot’ı stale olabilir. [A6] Apple `NWPath` expensive/constrained ve status verir; satisfied status başarılı endpoint bağlantısı garantisi değildir. [P7] | Reconnect callback’i authority değildir. Her request timeout/duplicate/out-of-order/unknown sonucunu taşımalıdır. |
| Cellular/data consent | Android meteredness’i transport adına bakarak değil capability ile değerlendirmeyi önerir. [A6] Apple request’i cellular’a uygun/uygunsuz kılabilir; Low Data Mode/expensive path ayrı sinyallerdir. [P6][P7] | Boyut önizlemesi, explicit consent, pause/cancel ve per-user network policy zorunludur; OS sinyali user consent yerine geçmez. |
| Clocks | Android wall clock kullanıcı/ağ tarafından ileri/geri sıçrayabilir; interval için `elapsedRealtime()` ayrıdır. [A7] Apple `systemUptime` reboot’tan beri monotonic uptime’dır. [P9] | Freshness/timeout/retry/eligibility yalnız cihaz wall clock’una bağlanamaz; server generation ve clock-anomaly state gerekir. |
| Secure keys | Android auth-bound keys lock-screen/biometric değişiminde kalıcı invalid olabilir. [A11] Apple Keychain item erişimi unlock/passcode/backup/`ThisDeviceOnly` koşullarına bağlıdır; erişim yokluğu ve migrasyon ayrıdır. [P8] | Key unavailable, auth required, invalidated ve re-key durumları ayrı ve kullanıcıya görünür olmalıdır; plaintext fallback yoktur. |
| Accessibility | Android manual TalkBack/Switch Access testini ve geçici mesajların okunmasını ister. [A8] Apple VoiceOver için label, hint ve state’in görsel renkten bağımsız verilmesini ister; announcements assistive app’e gönderilebilir. [P10][P11] | `pending`, `paused`, `failed`, `conflict`, `stale`, `unknown`, `blocked`, `complete` durumları renk/icon/snackbar’a terk edilemez. |
| Update identity | Android update aynı application ID, imza/proof-of-rotation ve uygun version code ister; uninstall ederek kurulan farklı paket app data’sını siler. [A10] Apple bundle ID uygulamayı sistemde benzersiz tanımlar ve dosya formatında version number/older-version handling önerilir. [P1][P13] | Update ≠ migration proof. Schema/data formatı explicit versioned ve failure-safe olmalıdır; bundle/package identity değişimini reinstall gibi ele al. |
| Flutter data boundary | Flutter’ın resmi mimari rehberi repository/data layer’ı source of truth, cache/error/retry/sync sorumluluklarını ayrı tutar; platform-specific capability için native integration/channel gerekir. [F4][F5] | UI state, plugin cache veya generated native state kanonik truth olamaz. Channel/plugin sözleşmesi versioned, exportable ve iOS fallback’li olmalıdır. |

## 5. Eşit failure kabul sözleşmesi

Her senaryo bütün mobile candidate’lar için aynı girdiyi, aynı failure injection’ı, aynı kullanıcı görünürlüğünü ve aynı
kanıt alanlarını kullanır. Flutter’ın seçilmiş olması bu eşiği düşürmez.

### 5.1 PASS

Bir senaryo ancak şu koşullar birlikte gösterilirse `PASS` olur:

1. Resmi platform mekanizması doğru kapsamıyla belgelenmiş; belge mekanizmanın ürün guarantee’si olmadığı açıkça
   ayrıştırılmıştır.
2. Aynı fixture Android constrained/main ve iOS oldest/current cohort’unda yürütülmüş veya iOS ikinci lane için
   bağlayıcı test planına alınmıştır.
3. Failure sırasında eski geçerli state ya da güvenli boş state korunur; yarım/karışık/duplicate/unknown sonuç positive
   authority’ye dönüşmez.
4. Operation/package ID, schema/version, generation/digest, client/build/OS, network/battery/storage/clock koşulu ve
   pre/post state export edilebilir.
5. Kullanıcı, `complete` ile `pending/paused/failed/conflict/stale/unknown/blocked` durumlarını Turkish ve TalkBack /
   VoiceOver ile ayırt edebilir; yalnız renk veya ikon kullanılmaz.
6. Retry/resume/idempotency, quarantine, re-auth, migration veya cleanup yolu owner’ın SQL/SSH/native repair/debug
   zorunluluğu olmadan tanımlanmıştır.

### 5.2 HOLD

`HOLD`, resmi docs mekanizmayı desteklese de gerçek cihaz, assistive technology, restore, uninstall/reinstall, low
storage, process kill, schema migration, metered-network veya iOS lane evidence’ı eksikse kullanılır. “Çalışabilir”,
“plugin bunu yapıyor”, “OS backup geri getirir” veya “simülatörde geçti” tek başına `PASS` değildir.

### 5.3 REJECT

Aşağıdakilerden biri varsa senaryo `REJECT`tir ve başka güçlü özelliklerle telafi edilemez:

- safety/recovery closure, user history, pending accepted operation veya protected audit sessizce kaybolur/ezilir;
- yarım/yanlış generation, stale restore, changed clock veya cached role yeni positive authority üretir;
- background, push, notification, lifecycle callback, cache veya cellular network guarantee gibi kullanılır;
- 25 MB cellular consent atlanır, full library/2 GB catalog veya optional media gizlice iner;
- key erişim hatası plaintext/secret export veya sessiz yeni key ile geçiştirilir;
- migration failure destructive reset, mixed schema veya owner-only manual repair gerektirir;
- kritik durum assistive technology ile ayırt edilemez;
- unmaintained/unexportable dependency veya provider lock-in olmadan native fallback yoktur.

## 6. 18 eşit failure senaryosu

Her satırdaki `PASS/HOLD/REJECT` aynı şekilde Flutter ve ileride karşılaştırılacak tüm mobile adaylara uygulanır. “Platform
kanıtı” sütunundaki link, seçim değil, failure’ın dış otoritesidir.

| ID | Failure injection / sınanan invariant | PASS koşulu | HOLD / REJECT koşulu |
|---|---|---|---|
| `MPR-01` | **Kanonik local state ile cache ayrımı.** Cold start, cache temizliği veya rebuild sonrası 250 MB content cache’inin bir bölümü yok. | User history, pending operations, package manifesti ve required recovery closure dayanıklı alanda kalır; cache miss yalnızca rebuild/redownload üretir; cache’teki kopya authority değildir. | `HOLD`: storage sınıfları ve purge testi yok. `REJECT`: safety data, pending work veya audit yalnız purgeable cache’te ya da cache temizliği sessiz data loss yaratıyor. [A2][A3][P2][F4] |
| `MPR-02` | **Yarım/bozuk compact package.** 12 MB indirme %50’de kesilir; digest yanlışlanır; cihaz promote sırasında kapanır. | Stage alanı manifest + digest + dependency closure doğrulanmadan görünmez; eski complete generation korunur; retry/resume idempotent’tir; kullanıcı `paused/failed` görür. | `HOLD`: yalnız checksum veya yalnız platform atomic primitive’i test edilmiş. `REJECT`: partial/mixed generation okunur, eski paket üzerine doğrulanmadan yazılır veya başarısızlık “complete” gösterilir. [A9][P11][F3] |
| `MPR-03` | **Local DB/file transaction interruption.** History + outbox + media metadata güncellemesinin ortasında process kill/power loss. | İlgili transaction ya tamamen yoktur ya da tamdır; operation ID duplicate üretmez; orphan media quarantine edilir; restart sonrası reconciliation bilinçli state gösterir. | `HOLD`: yalnız happy-path restart. `REJECT`: half-row, silently dropped photo/note, duplicate accepted operation veya yüksek sonuçlu işte silent last-write-wins. [A1][A9][P11][F4] |
| `MPR-04` | **Lifecycle bildirimi gelmeden process death.** Background, incoming call, task-manager kill, force-quit ve ani güç kesilmesi. | Correctness commit boundary callback dışındadır; Flutter/OS lifecycle event gelmese bile durable state korunur; ephemeral form restoration kanonik operation sayılmaz. | `HOLD`: `onPause/onStop/didChangeAppLifecycleState` geldiği varsayılmış. `REJECT`: son kayıt yalnız lifecycle callback’inde yapılıyor veya yeniden açılışta kayıp iş başarılıymış gibi görünüyor. [A1][P4][F1][F2] |
| `MPR-05` | **Stale/partial OS backup restore.** Android Auto Backup restore’u install sırasında gelir; iOS backup’ta cache/tmp yoktur; eski generation geri yüklenir. | Restore önce quarantine/reconciliation’a girer; client/package/identity/generation/digest ve server negative floor doğrulanır; revoked/recall/deleted/accepted state dirilmez; cache yeniden üretilebilir. | `HOLD`: yalnız backup dosyasının varlığı gösterilmiş. `REJECT`: restore doğrudan authority, entitlement veya “current” state yapıyor; cross-plane inconsistency gizleniyor. [A3][P1][P2][P3] |
| `MPR-06` | **Uninstall/reinstall ve account continuity.** Android app-specific data silinir, olası backup restore ile geri gelir; iOS container/keychain erişimi koşula bağlıdır. | Reinstall local state’in varlığını varsaymaz; re-auth + server/API rebind gerekir; kayıp key/pending work için explicit recovery/export yolu vardır; eski cache yeni device entitlement vermez. | `HOLD`: OS varsayılan davranışı cihazda denenmemiş. `REJECT`: reinstall sonrası stale token/key ile yetki, sessiz unsynced work loss veya duplicate device/account binding. [A2][A3][P1][P8] |
| `MPR-07` | **Secure key unavailable/invalidated.** Android lock-screen/biometric değişimi; iOS locked state/passcode/`ThisDeviceOnly`; key missing/corrupt. | `KEY_UNAVAILABLE`, `AUTH_REQUIRED`, `KEY_INVALIDATED` ve `REKEY_REQUIRED` ayrı state’tir; protected field plaintext’e düşmez; user re-auth/recovery ile ilerler; yeni key eski ciphertext’i sessizce yok saymaz. | `HOLD`: yalnız unlocked happy path. `REJECT`: secret log/export, insecure fallback, key exception’ı yutma veya yeni key ile eski veriyi görünmez kılma. [A11][P8][P1] |
| `MPR-08` | **App update + schema migration failure.** Eski release üzerinde yeni build; migration yarıda kesilir; unknown future schema; düşük free space. | Schema/data formatı versioned; preflight ve yeterli temp space kontrolü vardır; migration idempotent/transactional’dır; failure safe-stop/rollback/quarantine’a gider; eski data kaybolmaz; migration log/export edilir. | `HOLD`: migration yalnız mock/tek cihazda. `REJECT`: destructive reset/drop, mixed schema write, her açılışta tekrarlanan bozuk migration veya owner-only repair. [A10][P1][P13][F4] |
| `MPR-09` | **Background schedule/Doze/suspend failure.** App lock/background; Android Doze/App Standby; iOS suspend; force-quit sonrası pending transfer. | Foreground açılışında aynı durable queue güvenle devam eder; background gecikmesi kullanıcıya görünür; transfer resumable/cancelable; correctness background execution’a bağlı değildir. | `HOLD`: yalnız scheduling API’nin adı var, interruption matrix yok. `REJECT`: background/push/notification “kesin çalışır” kabul edilmiş veya force-quit sonrası completion iddiası var. [A4][A5][P4][P5][F1] |
| `MPR-10` | **Battery/thermal/low-power pressure.** Low battery, charging yok, thermal/low-power; optional 150 MB media ile compact core aynı anda bekliyor. | Required compact closure önce/ayrı ilerler; optional media pause/cancel edilebilir; retry storm yoktur; düşük battery/thermal/storage gerekçesi kullanıcıya açık; battery/data ölçümü tutulur. | `HOLD`: yalnız nominal Wi-Fi/şarj testi. `REJECT`: optional media safety core’u bloke ediyor, unbounded foreground/background work veya cihazı tüketen retry var. [A4][A5][P12] |
| `MPR-11` | **Network loss/reconnect/duplicate outbox.** 1 Mbps/300 ms/%5 loss, 72 saat offline, request ortasında kill, reconnect’te duplicate/out-of-order ack. | Operation ID/idempotency key ve expected version vardır; `pending/accepted/rejected/unknown` ayrılır; server ack olmadan accepted denmez; retry duplicate side-effect üretmez; conflict/hold görünür. | `HOLD`: yalnız mocked 200 response. `REJECT`: local optimistic success canonical kabul, silent last-write-wins veya network callback’ine authority yükleniyor. [A5][A6][P7][F4] |
| `MPR-12` | **Metered/cellular consent.** Cellular/Low Data Mode; compact 12 MB; optional 150 MB; test package 25 MB üstü. | Measured size/class transfer öncesi görünür; `>25 MB` cellular için explicit choice gerekir; no hidden large background download; required closure threshold’ı aşmamak için safety içeriği eksiltilmez; pause/resume vardır. | `HOLD`: yalnız “cellular mı Wi-Fi mı” transport etiketi. `REJECT`: consent olmadan optional/full catalog, 2 GB veya büyük background transfer; optional media yüzünden compact closure eksik. [A6][P6][P7] |
| `MPR-13` | **Storage pressure/eviction/removable storage.** Android low storage, external media unavailable, iOS `Caches/tmp` purge; old + new package + verify için peak space yetersiz. | Free/peak space preflight edilir; required package durable alanda kalır; optional cache evict edilebilir; user history/photo silinmez; failure `NEEDS_SPACE` olarak retry/cleanup gösterir; partial stage temizlenir. | `HOLD`: yalnız nominal free-space. `REJECT`: required closure cache’te, low-space otomatik overwrite/silent delete, ya da external/removable storage varlığı garanti kabul ediliyor. [A2][A5][P2][P3] |
| `MPR-14` | **Device clock/time anomaly.** User clock ileri/geri alınır, timezone değişir, restore sonrası reconnect olur. | Timeout/retry/age için monotonic interval ve server generation kullanılır; wall-clock change/anomaly görünür; freshness/eligibility yalnız device time ile yükselmez; high-consequence state unknown/stale fail-closed olur. | `HOLD`: yalnız launch’ta bir kez clock oku. `REJECT`: saat değişimi stale guide’ı fresh yapıyor, recall/expiry atlıyor veya retry’ı kalıcı kilitliyor. [A7][P9] |
| `MPR-15` | **Accessible sync/recovery states.** TalkBack, VoiceOver ve Switch Access ile `pending`, `paused`, `failed`, `conflict`, `stale`, `unknown`, `blocked`, `complete`. | Her state’in Türkçe name/value/hint’i semantik olarak okunur; geçici olay announcement ile duyurulur; action touch/color/icon olmadan tamamlanır; manual real-device AT evidence vardır. | `HOLD`: yalnız screenshot, contrast veya automated tree. `REJECT`: renk/icon-only, erişilemeyen snackbar, stale ile complete’in ayrıştırılamaması veya retry/hold action’ının AT ile kullanılamaması. [A8][P10][P11] |
| `MPR-16` | **Flutter platform bridge/plugin/native asymmetry.** Android capability çalışır; iOS lane’de permission/lifecycle/API farklıdır; generated registrant/channel hata verir veya dependency bakımsız kalır. | Domain/schema/state UI’dan bağımsızdır; channel contract ve error mapping versioned/exportable; capability detection ve owned native fallback vardır; Android-first kanıtı iOS release gate’i yerine geçmez; owner native repair’e zorlanmaz. | `HOLD`: package/plugin sürümü, generated/native diff veya iOS planı eksik. `REJECT`: critical capability unmaintained/unexportable dependency’ye kilitli, native state reproduciable değil veya Android-only success iOS failure’ını gizliyor. [F1][F4][F5] |
| `MPR-17` | **Optional media ve cache boundary.** 12 MB compact core, 150 MB optional media, 250 MB cache ve 2 GB unrelated catalog birlikte; optional download cancel/evict edilir. | Core optional media olmadan complete safe/recovery closure sağlar; media ayrı classification/version/digest ve on-demand consent taşır; cache pressure optional’ı evict eder, core’u etmez; 2 GB hiç seçilmez; peak storage ayrıca ölçülür. | `HOLD`: fixture değeri final product cap gibi kullanılıyor veya installed/temporary peak ölçülmemiş. `REJECT`: safety anlamı optional media’ya bağlı, full catalog default, optional media core’u silerek yer açıyor. [A2][P2][A6] |
| `MPR-18` | **Mixed client/package/release ve recall.** Eski client, yeni server package, pending update, offline recall/suspension, rollback veya mixed manifest. | Manifest exact client compatibility/eligibility/generation taşır; stale/unknown/incompatible package fail-closed olur; online negative authority reach-back sağlar; old client positive authority üretemez; rollback anti-resurrection floor’u bozmaz. | `HOLD`: yalnız latest client test edilmiş. `REJECT`: mixed generation kabul, mutable runtime substitution approved meaning’i değiştiriyor, recalled/revoked/deleted/accepted state rollback ile diriliyor. [A3][A10][P1] |

## 7. Eşit gerçek-cihaz kanıt paketi

No-code aşamasında aşağıdaki kanıt henüz üretim readiness iddiası değildir; Phase-5 ADR ve release gate için zorunlu
kanıt şablonudur:

| Kanıt | Android-first lane | iOS-later lane |
|---|---|---|
| Process/lifecycle | Android 10/API 29 constrained ve Android 13+ main; background/lock/call/kill/restart/Doze/low storage | En eski desteklenen iOS ve güncel non-Pro; background/lock/call/suspend/force-quit/restart/low storage |
| Data/package | 12 MB compact, corrupt/wrong digest, interrupted promote, old+new peak storage, 150 MB optional, 250 MB cache | Aynı fixture; `Documents`/`Application Support`/`Caches`/`tmp` sınıfları ve restore kapsamı ayrıca gözlenir |
| Backup/reinstall | Auto Backup include/exclude, 25 MB backup quota path, restore-before-launch, uninstall/reinstall, stale generation | device/iCloud restore kapsamı, container/keychain accessibility, uninstall/reinstall ve same bundle identity |
| Connectivity | Wi-Fi, ordinary cellular, constrained cellular, captive/validated change, offline 72h, reconnect duplicate | Wi-Fi/cellular/Low Data Mode/expensive path, offline/reconnect, background URLSession/force-quit sınırı |
| Security/key | locked device, lock-screen/biometric change, missing/invalid key, re-auth | locked device, passcode/keychain accessibility/`ThisDeviceOnly`, missing/invalid key, re-auth |
| Migration | Eski build → yeni build; interrupted/schema unknown/low-space migration; safe rollback/quarantine | Aynı migration matrix; app container korunumu varsayılmadan gerçek update/restore testi |
| Accessibility | Turkish TalkBack + Switch Access; every sync state and transient announcement | Turkish VoiceOver + Switch Control; every sync state, label/value/hint and announcement |

Her evidence record şu minimum alanları taşır: `scenario_id`, candidate/build/version, platform/OS/device cohort,
fixture value, network/battery/storage/clock state, operation/package/schema ID, pre/post generation/digest, user-visible
Turkish state, AT observation, logs/export, recovery action, owner/debug dependency ve `PASS/HOLD/REJECT` hükmü.

## 8. Mobil tasarım için provider-neutral minimum sözleşme

Teknik seçim yapılmadan, her adayın kapanması gereken minimum sözleşme:

1. `DurableStore`: user history, operation envelope, package manifest ve migration metadata için non-purgeable,
   versioned, exportable logical boundary.
2. `Outbox`: stable operation ID, expected version, idempotency, dependency, retry/unknown/conflict state; server/API
   ack olmadan high-consequence accepted state yok.
3. `PackageStore`: stage/current/quarantine ayrımı; manifest, dependency closure, digest, client compatibility ve
   generation; optional media ayrı namespace/lifecycle.
4. `KeyState`: key available/locked/missing/invalidated/re-auth/re-key; protected data plaintext’e dönmez.
5. `ClockState`: server time/generation, monotonic interval, device clock anomaly; wall clock tek authority değildir.
6. `LifecycleState`: foreground, background, deferred, killed, resumed; callback kaybı normal failure olarak işlenir.
7. `NetworkState`: actual request result, metered/expensive/constrained hint, timeout, retry, duplicate ve unknown;
   connectivity callback “online authority” değildir.
8. `UserState`: Türkçe ve assistive-technology ile okunabilir sync/recovery state; visual-only feedback yok.
9. `MigrationState`: current schema, supported old schemas, staged migration, failure quarantine, rollback/forward
   recovery ve release stop trigger’ı.
10. `RecoveryFloor`: restore, reinstall, rollback veya provider/account failure sonrası revoked, recalled, deleted,
    suspended ve accepted-operation negative state’lerini eski backup’ın üstünde tutan non-restorable floor.

Bu sözleşme bir local database kütüphanesi, Flutter plugin’i, object provider’ı veya backend runtime’ı seçmez. İleride
seçilecek her teknoloji aynı 18 senaryoda kanıt üretmek zorundadır.

## 9. Açık riskler ve karar sınırı

- Resmi docs platformun neyi yapabileceğini açıklar; belirli Flutter plugin’inin lifecycle, generated registrant,
  native permission, key continuity veya background transfer kalitesi için üretim kanıtı değildir.
- Android Auto Backup’ın 25 MB/app-user kotası küçük offline package’ı otomatik olarak tam backup yapmaz; backup’a girmeyen
  cache ve dışlanması gereken token/device-ID ayrıca tasarlanmalıdır.
- iOS background URLSession, normal system termination ile user force-quit’i aynı ele almaz. Bu fark transfer state’inde
  mutlaka görülmelidir.
- Apple `Application Support` veya Android internal files’in backup’a girmesi, restore edilen içeriğin güncel server
  authority olduğu anlamına gelmez.
- Flutter state restoration ephemeral UI içindir; 1 MB Android instance-state sınırı ve process-death olasılığı, uzun
  history/outbox/package yerine konamaz.
- “Atomic write” tek dosyanın bütünlüğünü artırır; çoklu dosya/package/DB + manifest + key + server generation
  consistency’sini tek başına çözmez.
- Numeric fixture’lar ürün sözleşmesi değildir. Gerçek peak space, compression, file count, database journal, backup
  quota, network cost, battery/thermal ve OS-version davranışı ölçülmeden final limit veya RPO/RTO ilan edilemez.

Bu nedenle DEBATE-009 sonucu `PLATFORM FAILURE RESEARCH COMPLETE / IMPLEMENTATION HELD` olarak kalır. Flutter
Android-first yönüyle devam edebilir; ancak Phase-5’e geçiş için 18 senaryonun her biri evidence-gated olmalı ve
`REJECT` bulunan bir safety/data/recovery/accessibility failure ağırlıklı skorla maskelenmemelidir.

## 10. Resmi kaynaklar

### Android Developers

- [A1 — Processes and app lifecycle](https://developer.android.com/guide/components/activities/process-lifecycle)
- [A2 — Access app-specific files](https://developer.android.com/training/data-storage/app-specific)
- [A3 — Back up user data with Auto Backup](https://developer.android.com/identity/data/autobackup)
- [A4 — Optimize for Doze and App Standby](https://developer.android.com/training/monitoring-device-state/doze-standby)
- [A5 — Task scheduling / persistent work](https://developer.android.com/develop/background-work/background-tasks/persistent)
- [A6 — Read network state](https://developer.android.com/develop/connectivity/network-ops/reading-network-state)
- [A7 — SystemClock](https://developer.android.com/reference/android/os/SystemClock)
- [A8 — Test your app’s accessibility](https://developer.android.com/guide/topics/ui/accessibility/testing)
- [A9 — AtomicFile](https://developer.android.com/reference/android/util/AtomicFile)
- [A10 — How app updates work](https://developer.android.com/google/play/app-updates)
- [A11 — KeyPermanentlyInvalidatedException](https://developer.android.com/reference/android/security/keystore/KeyPermanentlyInvalidatedException)

### Apple Developer Documentation

- [P1 — Files and directories](https://developer.apple.com/documentation/technologyoverviews/files-and-directories)
- [P2 — Using the file system effectively](https://developer.apple.com/documentation/foundation/using-the-file-system-effectively)
- [P3 — Optimizing your app’s data for iCloud Backup](https://developer.apple.com/documentation/foundation/optimizing-your-app-s-data-for-icloud-backup)
- [P4 — Extending your app’s background execution time](https://developer.apple.com/documentation/uikit/extending-your-app-s-background-execution-time)
- [P5 — Background URLSession](<https://developer.apple.com/documentation/foundation/urlsessionconfiguration/background(withIdentifier:)>)
- [P6 — URLRequest `allowsCellularAccess`](https://developer.apple.com/documentation/foundation/urlrequest/allowscellularaccess)
- [P7 — Network `NWPath`](https://developer.apple.com/documentation/network/nwpath)
- [P8 — Restricting keychain item accessibility](https://developer.apple.com/documentation/security/restricting-keychain-item-accessibility)
- [P9 — ProcessInfo `systemUptime`](https://developer.apple.com/documentation/foundation/processinfo/systemuptime)
- [P10 — Supporting VoiceOver in your app](https://developer.apple.com/documentation/uikit/supporting-voiceover-in-your-app)
- [P11 — Accessibility notifications](https://developer.apple.com/documentation/accessibility/accessibilitynotification)
- [P12 — ProcessInfo / thermal and power state](https://developer.apple.com/documentation/foundation/processinfo)
- [P13 — Shared data and file-format versioning](https://developer.apple.com/documentation/technologyoverviews/shared-data)
- [P14 — Atomic data writes](https://developer.apple.com/documentation/foundation/nsdata/writingoptions/atomic)

### Flutter / Dart

- [F1 — `AppLifecycleState`](https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html)
- [F2 — Restore state on Android](https://docs.flutter.dev/platform-integration/android/restore-state-android)
- [F3 — Dart `File.writeAsBytes`](https://api.dart.dev/dart-io/File/writeAsBytes.html)
- [F4 — Flutter common architecture concepts](https://docs.flutter.dev/app-architecture/concepts)
- [F5 — Flutter platform channels](https://docs.flutter.dev/platform-integration/platform-channels)
