# PRODUCT MASTER

Status: DRAFT

Bu belge discovery boyunca surekli rafine edilen teknik olmayan ana urun sentezidir. Ham Q&A yerine gecmez; kanit dosyalari `02_DISCOVERY/SESSIONS/` altindadir.

## Current Evidence Base

- Phase-1 approved workspace baseline
- `SESSION-001_BATCH_01_Q006_Q035.md`
- `SESSION-002_BATCH_02_Q036_Q065.md`
- `SESSION-003_BATCH_03_Q066_Q095.md`
- `SESSION-004_BATCH_04_Q096_Q125.md`

## Product Model — Current Working Synthesis

### 1. Entry modes and first value

**CONFIRMED — Q006, Q012, Q022, Q090, Q123**

Kullanici urune yapmak istedigi islemi bilerek veya yalniz bir belirtiyle gelebilir. Belirti girisi gunluk dil, motosiklet bolgesi veya isaretli gorsel uzerinden ilerleyebilir. Yol-kenari baglaminda hizli belirti taramasi, once safety kontrolu, kisa gorsel adimlar ve suruse devam belirsizliginin gizlenmemesi beklenir.

Ilk kullanimda kullanici motosikletini secip rehber deneyiminin nasil calistigini hizla gormek ister. Account creation, notification permission veya uzun profil ilk degerden once zorunlu olmamali; kayit/esitleme gibi ihtiyac ortaya ciktiginda istenmelidir. Bu bir teknik auth karari degildir.

### 2. Motorcycle-guide fit, variant certainty and modification fit

**CONFIRMED — Q008-Q009, Q019, Q021, Q026, Q036-Q039, Q066-Q067, Q102-Q104**

Rehber kullanicinin gercek motosikletiyle yeterli eslesme kurulmadan motosiklete ozelmis gibi sunulamaz. Marka/model/yil, motor hacmi, donanim, islemi etkileyen ozellikler, gorunur donanim ve gerektiginde farkli acilardan fotograflar kullanilabilir.

Kullanici teknik kimlik kodlarini ezbere bilmek veya etiket/parca kodu/belge aramak zorunda birakilmak istemiyor. Observable kanit yetmezse hangi ayrimin eksik oldugu gorunur olmali ve versiyona ozel application adimlari baslamamalidir. Bu, gorsel ayristirmanin her motosiklette teknik olarak yeterli oldugu iddiasi degildir.

Sonradan degistirilmis sistemde fabrika rehberi otomatik uygun sayilamaz. Yaygin aftermarket degisikliklar gorsel/observable olarak ayristirilip uygunlugu dogrulanirsa motosiklete ozel rehbere dahil edilebilir; fabrika ve modifiye sokme/takma farklari acik olmali. Nadir/custom modifikasyonda dogrulanmis rehber yoksa hangi ozelligin neden dogrulanamadigi, hangi kanitin eksik oldugu ve rehber olusturmak icin hangi bilgi gerektigi gosterilebilir. Guvenilir genel bilgi `ogretici, bu motosiklete uygulama talimati degil` ayrimiyla kalabilir; zarar verebilecek sokme/baglama/ayar application adimlari dogrulanana kadar acilmaz.

### 3. Trust, provenance and content lifecycle

**CONFIRMED — Q010-Q011, Q040-Q044, Q073-Q074, Q081-Q083, Q109-Q110**

Dogrulanmis teknik bilgi motosiklet/varyantla uyumlu guvenilir kaynaga dayanmalidir; kaynak surumu ve ilgili bolum kaniti gorulebilmelidir. Insan incelemesinde ilgili sistemde uygulamali deneyim ve uyum/kaynak/gorsel/arac/risk/son-kontrol degerlendirmesi beklenir. Kritik rehberde bagimsiz ikinci inceleme ek guven sinyalidir fakat her kritik rehberde zorunlu iki-reviewer politikasi olarak kilitlenmemistir.

Kaynak update/hata/celiski durumunda yeniden inceleme, etkilenen application adimini askiya alma/durdurma, kullaniciya gerekli kontrol/yardim yolu ile uyari ve tarihsel rehber surumunu koruma beklenir. Community duzeltme onerisi resmi rehbere dogrudan giremez; kaynak, motosiklet uygunlugu ve safety etkisi incelenmeli, kabul edilirse degisen adim ve gerekce yeni surumde gorunmelidir.

Kanit dili product-level olarak ayrisir: `kullanici beyani` kullanicinin girdisi; `belgeli` supporting evidence tasiyan; `incelenmis` kaniti kontrol edilmis; `dogrulanmis` ise kaynak, ilgili motosiklet/islem uygunlugu, inceleme tarihi ve karar gorunurlugu bulunan bilgiyi ifade etmelidir. `Dogrulanmis`, `kesin sonuc verir` veya `her versiyonda aynidir` demek degildir. Bu etiketlerin tum domainlerde birebir ayni global taxonomy olmasi henuz karar degildir.

### 4. Guide detail, accessibility and active-repair use

**CONFIRMED — Q007, Q014-Q015, Q054, Q090, Q124-Q125**

Yeni/az deneyimli kullanici icin temel rehber birimi `tek hareket + ilgili gorsel + basari kontrolu` seviyesinde ayrintili olabilir. Deneyimli kullanici ayni dogrulanmis bilginin daha kisa checklist/teknik gorunumune hizla ulasmak ister. Safety ve kritik dogrulama deneyim seviyesine gore azaltilamaz.

Gorsel beklenti gercek/isaretli fotograf, gizli baglantida cizim, hareket/sira kritikse kisa video ve safety/olcum/kontrol icin acik metindir. Tam varyant fotografi yoksa dogrulanmis cizim/isaretli sema fallback olabilir; baska motosikletin gorseli ayniymis gibi sunulamaz.

Turkiye icin acik Turkce, alisilmis olcu birimleri ve anlasilir terminoloji beklenir. Erisilebilirlik ihtiyaclari buyuk yazi/dugmeler, yuksek kontrast, yalniz renge dayanmayan uyarilar, gorsel aciklamasi, video altyazisi, sesli adimlar ve kirli/mesgul ellerle kolay etkileşimdir. Belirli voice technology veya UI tasarimi bu asamada secilmemistir.

### 5. Readiness, re-validation and resume

**CONFIRMED — Q013, Q016-Q017, Q021, Q050-Q053, Q096-Q098**

Kullanici baslamadan amac, uygunluk, zorluk/risk, sure, maliyet, arac/parca/ekipman ve motosikletin kullanilabilirlik durumunu gormek ister. Zorunlu eksikler motosiklet yari sokulmeden once gorunur olmalidir.

Readiness yalniz `deneyimliyim` oz-beyanina dayanamaz. Benzer is gecmisi, arac/olcum bilgisi, onceki islem kayitlari ve on kosullari anlama dikkate alinabilir. Guvenle ogrenilebilen eksiklik hazirlik/ogrenme yoluna yonlendirebilir; ciddi sonucu veya uzman dogrulamasi gerektiren eksiklik kritik application adimini kapatir.

Readiness kullaniciyi durdurdugunda hangi kosulun eksik oldugu, neden gerektigi, nasil saglanacagi ve nasil yeniden kontrol edilecegi gosterilmelidir. Kullanici degerlendirmeyi yanlis bulursa salt `yapabilirim` diyerek gate'i gecemez; fotograf, olcum veya alternatif kontrol gibi yeni kanitla re-validation yapabilmelidir. Hazirlik tamamlaninca rehber baglamina kaldigi yerden donebilmelidir.

Dogru motosiklet versiyonu, kritik teknik bilgi, gerekli ekipman, guvenli calisma ortami veya zorunlu pre-check eksikse application adimi acilmaz.

### 6. Teaching vs application and high-consequence guidance

**CONFIRMED — Q018-Q021, Q034, Q045-Q053, Q068-Q069, Q099-Q101**

High-consequence kategori adi tek basina mutlak kapsam disi nedeni degildir. Kullanici fren, direksiyon, yakit, kaldirma, motor ici, yuksek gerilim, basincli veya yuksek sicaklik gibi sistemleri ogrenebilmek ister. Ancak motosiklet uyumu, gerekli ekipman/beceri, guvenli ortam veya kritik sonucun dogrulanabilirligi yoksa application progression acilmaz.

`Ogretici icerik` ile `gercek motosiklete uygulanabilir talimat` farkli guven seviyeleridir. Teaching content erisilebilir kalabilir. Gercek motosiklete ilk fiziksel mudahaleden once zorunlu kosullar kontrol edilmeli; islem sirasinda yeni risk, mismatch veya dogrulanamayan kosul ortaya cikarsa uygulamali akis o noktada durmalidir.

Profesyonel yardim `sen bunu yapamazsin` diliyle sunulmamalidir. Urun hangi kosulun dogrulanamadigini, kullanicinin bunu nasil tamamlayip yeniden deneyebilecegini anlatmali; belirti kaydi, fotograf, hazirlik, islemi anlama ve result-check destegi profesyonel yolu secse bile surmelidir. Exact professional-escalation trigger hala discovery konusudur.

### 7. Safe equivalents

**CONFIRMED — Q017, Q053, Q055**

Alternatif arac/sarf/ekipman sadece gerekli olcu, uyum, dayanim, malzeme, islev ve safety ozellikleri dogrulanmissa guvenli esdeger sayilabilir. Hassas olcum, dogru sikma ve guvenli kaldirma gibi kritik fonksiyonlarda zorunlu ekipman yoksa islem ertelenir.

### 8. Diagnosis before repair

**CONFIRMED — Q022-Q024, Q056-Q058, Q090**

Teshis, kanit toplayarak belirsizligi azaltan surectir. `En olasi` neden icin birden fazla ayirt edici belirti/kontrol ayni nedeni desteklemeli ve alternatifler degerlendirilmelidir. Esit olasiliklarda ayristirici kontroller surer; rastgele parca degisimi onerilmez. Makul kontroller sonunda neden dogrulanamazsa `Neden dogrulanamadi` sonucu, yapilan kontroller ve guvenli kullanim belirsizligiyle kapanabilir; ozet uzmana aktarilabilir.

### 9. Recovery and mismatch

**CONFIRMED — Q025-Q027, Q038-Q039, Q066-Q067, Q096-Q101**

Takilma durumunda yakin plan, isaretleme, hareket yonu, sik hatalar ve gerekirse video/aciklama acilabilir. Rehber gercek motosiklet/modifikasyon/versiyonla uyusmazsa normal ilerleme durur; fark kaydedilir ve uygunluk yeniden belirlenir.

Readiness/mismatch blokajinda urun sebebi gostermeli, self-remediation/re-validation yolunu aciklamali ve hazirlik tamamlaninca kaldigi baglama donusu desteklemelidir. Recovery veya profesyonel escalation, diger dogrulanmis self-service rehberlerin erisimini gereksiz yere kapatmamalidir.

### 10. Guide versioning, recall and critical corrections

**CONFIRMED — Q028-Q030, Q042-Q043, Q059-Q060, Q081-Q083, Q122**

Yarim iste rehber surumu korunur. Yeni surum varsa farklar devamdan once gosterilir; kritik duzeltmede eski akista ilerleme durur ve mevcut fiziksel durum yeni rehberle yeniden eslestirilirken ilerleme/notlar korunur.

Gecmis kayit yeni rehber nedeniyle sessizce degistirilmez. Kullanilan rehber surumu korunur; geri cekilme/duzeltme nedeni ve gerekiyorsa yeniden kontrol uyarisi eklenir.

Offline kritik rehberde son dogrulama zamani gorunmelidir. Bir product freshness limiti asilmissa, baglanti kurulup rehber yeniden kontrol edilene kadar application adimlarinin kapanmasi beklenir. Bu limitin sayisal degeri veya hangi rehberlere uygulanacagi henuz belirlenmemistir.

### 11. Maintenance/repair history, evidence and edit trail

**CONFIRMED — Q029-Q030, Q033, Q062-Q063, Q073-Q074, Q109-Q110**

Her motosikletin gecmis/rehber/reminder baglami ayridir. Dis islem provenance ile kaydedilebilir; tarih, kilometre, islem, fatura, fotograf/not gibi kanitlar eklenebilir.

Hatalı kayit duzeltilebilir; eski ve yeni bilgi, degisiklik zamani ve nedeni korunur. Duzeltme bakım takvimini etkiliyorsa etkisi gosterilir. Kullanici beyani, belgeli, incelenmis ve dogrulanmis ifadeleri ayni guven statusu gibi kullanilmamalidir.

### 12. Next maintenance, exceptions and uncertainty

**CONFIRMED — Q031-Q033, Q061, Q064, Q075-Q077**

Bakim zamanlamasinda motosiklete uygun uretici kilometre/sure araliklari temel alinmali ve once dolan izlenmelidir. Kullanim kosulu sadece motosiklete uygun dogrulanmis bilgi destekliyorsa araligi degistirebilir; gerekce gorunur olmalidir.

Modifiye/yeni parcanin guvenilir bakım araligi bilinmiyorsa MotoBakim sure uydurmamali veya eski araligi otomatik kullanmamalidir; `belirsiz bakım takvimi` gorunur olmalidir. Dogrulanmis ozel istisna genel planla birlikte ve neden gecerli olduguyla sunulmalidir.

### 13. Notification behavior and critical catch-up

**CONFIRMED — Q032-Q033, Q064, Q070-Q072, Q111-Q113**

Rutin bakım/kayit reminders gruplanabilir, kapatilabilir veya ertelenebilir. Mevcut kullanici onemli fakat acil olmayan gecikmis konuda gunluk tekrar yerine haftada en fazla bir ozet tercih eder; bu tum kullanicilar icin LOCKED cadence degildir.

Surus safety'sini etkileyen acil uyari ayri ve belirgin olmali; kritik safety bilgisi telefon bildirimi susturulsa bile app icinde ve ilgili islem oncesi gorunur kalmalidir.

Uzun sure ertelenen kritik konu routine reminders arasinda kaybolmamalidir. App acilisinda belirgin safety ozeti, gecikmenin sonucu ve ilgili kontrol/isleme dogrudan yol beklenir. Birden cok kritik konu olasi zarar ve aciliyete gore siralanmali; `neden once bu`, `ne zamandir acik`, `simdi hangi kontrol` bilgisi gorunmelidir. Uzun aradan donen kullanici eski notification'larin tek tek yagmasi yerine kritik safety -> geciken bakım -> kayitlar sirali tek catch-up ozeti bekler.

### 14. Time and cost estimate trust boundary

**CONFIRMED — Q013, Q078-Q079**

Yaklasik sure deneyime gore aralik olarak faydalidir; hasar/sikisma/ek sokme gibi belirsizliklerde kesin bitis vaadi verilmemelidir. Maliyet tahmininde parca, sarf, arac ve varsa iscilik ayri gosterilmeli; dahil olmayan kalemler, fiyat tarihi ve varsayimlar gorunur olmalidir.

### 15. Community contribution and moderation

**CONFIRMED — Q080-Q084, Q105-Q108**

Kisisel not/fotograflar default-private kalmalidir. Community contribution ayri explicit secim olmali ve personal info paylasim oncesi ayiklanmalidir. Community icerigi kaynak, motosiklet, review status ve tarih bilgisiyle resmi rehberden ayrilir.

Moderation yalniz `sil/birak` degildir. Kaldirma nedeni somut/saygili olmali, ilgili kural ve sorunlu bolum gosterilmeli; contributor duzeltip yeniden gonderebilmeli veya itiraz edebilmelidir. Tekrarlanan yanlis katkida pre-review, kasitli/surekli tehlikeli tekrarda contribution restriction olabilir. Teknik olarak dogrulanamayan fakat faydali deneyim `dogrulanmamis kisisel deneyim` olarak, motosiklet ve gozlem baglamiyla resmi rehberden ayri sunulabilir; safety-riskli oneriler review bitmeden yayinlanmamalidir.

Tehlikeli contribution hizla gizlenmeli; gerekiyorsa icerige maruz kalan kullanicilar uyarilmali ve olay kaydedilmelidir.

### 16. Commercial neutrality and monetization

**CONFIRMED — Q065, Q085-Q088, Q114-Q115**

MotoBakim'in onceligi kullanicinin islemi kendisinin yapabilmesidir. Servis/usta listesi veya parca/arac satin alma core self-service rehberin yerini almamalidir. Teknik uygunluk kriteri ticari yuzeyden once gelmeli; sponsorlu teklif acikca isaretlenmeli ve odeme teknik uygunluk kararini degistirmemelidir.

Motora uygun ayrintili rehber, safety bilgisi, temel bakım takibi ve kullanicinin kendi verisini almasi ucretsiz kalmalidir. Gelismis history analysis, ek fotograf depolama, multi-garage management ve optional personalization premium deger adaylaridir. Surekli hizmet maliyeti yaratmayan optional degerlerde, ornegin yazdirilabilir ayrintili bakım arsivi veya kisilestirilmis ogrenme aracinda, one-time odeme mevcut kullanici icin makul olabilir. Final subscription/one-time/hybrid paket karari yoktur.

### 17. User scope and motivation

**CONFIRMED — Q089, Q116-Q117**

Core identity bireysel surucunun kendi motosikletindeki islemi ogrenip yapmasidir. Mevcut kullanicinin motivasyon sirasi: self-service completion -> ogrenip bagimsizlasma -> masraf azaltma -> zaman -> keyif.

Multi-bike owners, ailece/shared motorcycle kullananlar, baskasinin motosikletinde islem yapan hobby users ve yalniz history/reminder takip eden record-only owners anlamli supported context'lerdir. Record-only user rehber kullanmasa da history, next maintenance, belge/fotograf saklama, reminders ve motosikletler arasi ayrimdan deger almali ve isterse sonradan uygulamali rehbere gecebilmelidir.

Profesyonel usta/servisin dogrudan target user olup olmadigi hala aciktir.

### 18. Shared motorcycle and collaboration expectations

**CONFIRMED — Q118-Q119**

Baskasinin motosikletinde calisan kisi icin owner access izni vermelidir. Islem yapan contributor kendi kimligiyle kayit eklemeli; kimin neyi beyan ettigi, kayit zamani ve sonraki edit trail gorunmelidir. Baskasinin kaydi sessizce degistirilememeli ve izin geri alinabilmelidir. Ortak kullanim private notes'u izinsiz acmamalidir.

Bu product expectation teknik permission/auth modelini secmez.

### 19. Ownership transfer, archive and long-term lifecycle

**CONFIRMED — Q120-Q121**

Motosiklet satis/devrinde kullanici sectigi islem tarihleri, kilometre ve bakım kanitlarini yeni sahibe aktarabilmek ister. Personal notes, konum/kimlik iceren fotograflar default-private kalmali; transfer oncesi preview olmalidir. Parsiyel transferin new-owner history completeness semantigi hala aciktir.

`Archive`, aktif garajdan cikarma ama history'yi koruma ve daha sonra yeniden active etme davranisidir. Archive, delete ile karistirilmamalidir.

### 20. Offline and constrained-context continuity

**CONFIRMED — Q090-Q091, Q122**

Indirilmis motosiklete ozel rehber, gorsel, safety warning, kalinan adim ve personal history internet zayif/yokken erisilebilir kalmalidir. Icerik surumu, son dogrulama ve guncellik durumu gorunmelidir.

Offline erisilebilirlik ile application yetkisi ayni sey degildir. Kritik guide stale limit'i asilmissa teaching/reference erisimi kalabilirken application progression online re-check'e kadar kapanabilir. Exact freshness semantics aciktir.

### 21. Data ownership and account isolation

**CONFIRMED — Q092-Q095, Q118-Q121**

Kullanici kendi motosiklet/kayit/not/fotograf verisini gorebilmeli, duzeltebilmeli, ekleyip silebilmelidir. Bir hesabin verisinin baska hesapta gorunmesi kabul edilmez. Kendi verisini anlasilir ve yeniden kullanilabilir bicimde export etmesi premium olmamalidir.

Silme oncesi kapsam ve geri alinmazlik gorunur olmali; sonrasinda neyin silindigi/ne bekledigi anlasilmalidir. Shared motorcycle ve transfer durumlarinda personal/private content ile motorcycle history ayrisabilmelidir. Gercek deletion, community withdrawal ve export provenance edge case'leri aciktir.

### 22. Trust-breakers / product non-goal direction

**CONFIRMED — Q035, Q065, Q088, Q095, Q096-Q110, Q122**

MotoBakim'in teknik guvenini bozan davranislar:
- uydurulmus/dogrulanmamis teknik bilgi,
- tehlikeyi gizlemek veya safety gate'i yalniz oz-beyanla gecirmek,
- belirsiz arizayi kesin teshis gibi sunmak,
- tehlikeli isin basarisini garanti etmek,
- teaching-level bilgiyi dogrulanmamis motosiklet application talimati gibi sunmak,
- kritik safety bilgisini paywall arkasina saklamak,
- cross-account veri karismasi veya gecmisin sessiz kaybi/overwrite'i,
- community deneyimini resmi rehber gibi gostermek,
- gizli reklam/ticari etkinin rehber veya teknik uygunluk kararini degistirmesi,
- kritik stale rehberi yeniden kontrol gerektigi halde uygulamali olarak acik tutmak.

## Working Interpretations — INFERRED, NOT DECIDED

- `Belirsizligi acikca gostermek` varyant, teshis, maintenance, estimate, roadside ve stale-content kararlarinda yatay guven ilkesi olabilir.
- `Teaching vs application` ayrimi product architecture'in temel guven semantigi olabilir; ayni icerik bilgilendirici olarak erisilebilirken application gate'li olabilir.
- Auditability; rehber surumu, history edit, evidence label, moderation, collaboration ve ownership lifecycle'da yatay product principle olabilir.
- Readiness itirazi serbest override degil, evidence-based re-validation modeli olabilir.
- Community authoritative source-of-truth'un alternatifi degil, ayri provenance/review statulu ikincil bilgi katmani olabilir.
- Offline continuity convenience degil, safety baglaminin korunmasi olabilir; ancak stale critical application ayrica gate'lenebilir.
- Teknik dogruluk, safety gating, veri izolasyonu, auditability ve ticari tarafsizlik birlikte ana guven modelini olusturabilir.

Bu yorumlar discovery ilerledikce test edilmeye devam edecektir.
