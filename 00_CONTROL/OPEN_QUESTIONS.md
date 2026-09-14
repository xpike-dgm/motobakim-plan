# OPEN QUESTIONS

Bu dosya, proje hafizasinda henuz kesinlesmemis konulari, celiskileri ve ileride cevaplanmasi gereken sorulari tutar.

Bir AI burada bulunan bir konuyu kendi varsayimiyla kapatamaz. Kesin cevap kullanicidan veya yetkili karar surecinden gelmelidir.

## Status Values

- `OPEN`
- `BLOCKED`
- `ANSWERED`
- `CANCELLED`

---

## Aktif Sorular

### Q-0002 — Motosiklete ozellik icin gerekli kimlik bilgileri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q008-Q009; Batch 02 Q036-Q039  
**Question:** Kullanici-dostu marka/model/yil, motor hacmi, donanim, islemi etkileyen ozellikler ve fotograflar ilgili versiyonu kesinlestirmeye yetmediginde hangi ek kimlik kaniti kullanici acisindan kabul edilebilir olmalidir?  
**Impact:** Onboarding, icerik esleme ve rehber guvenligi.  
**Resolution so far:** Kullanicidan teknik kimlikleri ezbere bilmesi beklenmemeli; ancak islem/malzeme/guvenlik degisiyorsa ilgili versiyon kesinlesmeden rehber baslamamali. Modifiye sistem ayrica degerlendirilmelidir.

### Q-0004 — Tehlikeli veya uzmanlik gerektiren islemler
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q018-Q021/Q034; Batch 02 Q045-Q053  
**Question:** Yuksek gerilim ve Batch 02'de tek tek derinlestirilmeyen diger yuksek-sonuclu alanlarda hangi on kosul, beceri, ekipman, stop-gate ve profesyonel yardim sinirlari beklenir?  
**Impact:** Urun guvenligi ve kapsam politikasi.  
**Resolution so far:** Fren, direksiyon/on takim, yakit, kaldirma/destekleme ve motor ici icin kosullu rehberlik modeli CONFIRMED edildi. Genel ilke kategori yasagindan cok dogrulanabilir kosullara dayanir.

### Q-0010 — Hatirlatma davranisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q032-Q033; Batch 02 Q064  
**Question:** Bakim onceligi/risk/gecikme belli oldugunda notification yogunlugu, tekrar sikligi, birden fazla gecikmis isin gruplanmasi ve kullanici kontrolu nasil davranmalidir?  
**Impact:** Notification UX ve product rules.  
**Resolution so far:** Yaklasan/due/overdue genel davranisi ve kullanici ayari CONFIRMED; birden fazla gecikmede guvenlik/kullanim etkisi once, sonra gecikme ve kosullar dikkate alinmali ve gerekce gosterilmeli.

### Q-0021 — Kullanici katkisi / moderation / content governance
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 saturation LOW; Batch 02 professional content governance gelisti fakat community katmani sorulmadi  
**Question:** Kullanici notu, fotografi, yorum, duzeltme veya topluluk katkisi urunde yer alacaksa hangileri ozel kalmali, hangileri diger kullanicilara gorunebilir ve nasil denetlenmelidir?  
**Impact:** Icerik guveni, moderation ve urun kapsami.  
**Resolution:**

### Q-0022 — Birden fazla motosiklet ve gecmis duzeltme
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 02 Q062-Q063  
**Question:** Yanlis/eksik eski kayit nasil duzeltilmeli; duzeltme izi nasil korunmali ve disarida yapilan isi `dogrulanmis` kabul etmek icin hangi kanit seviyeleri yeterli olmalidir?  
**Impact:** Gecmis guveni ve bakim takibi.  
**Resolution so far:** Coklu motosiklet baglamlari kesin olarak ayrilmali; dis islem provenance ile kaydedilmeli ve kanitsiz kayit dogrulanmis gibi gosterilmemeli. Fatura tek basina otomatik dogrulama sayilmadi.

### Q-0023 — Sosyal/ticari ozelliklerin urun siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q035; Batch 02 Q065 monetization baseline  
**Question:** Topluluk, servis bulma, parca/arac satin alma, ticari yonlendirme veya sponsorlu yuzeylerden hangileri temel teknik rehberligi destekleyebilir; hangileri dikkat dagitici veya guven bozucu olur?  
**Impact:** Non-goals, guven ve urun kapsami.  
**Resolution:**

### Q-0024 — Bakim istisnalari ve agir kullanim
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q031; Batch 02 Q061  
**Question:** Degistirilmis parca, ureticiye ozel istisna veya kullanicinin kosul bilgisi vermedigi durumlarda bakim planinin nasil davranmasi beklenir?  
**Impact:** Bakim kurallari ve reminder dogrulugu.  
**Resolution so far:** Kullanim kosullari istege bagli sorulabilir; bakim araligi yalniz motosiklete uygun dogrulanmis bilgi destekliyorsa degistirilmeli ve gerekce gorunur olmalidir.

### Q-0025 — Islem suresi ve maliyet tahmininin guven siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** ASM-008; Batch 01 Q013  
**Question:** Yaklasik sure ve maliyet hangi kosullarda yararli ve guvenilir sayilir; degiskenlik nasil ifade edilmeli ve hangi durumda tahmin hic gosterilmemelidir?  
**Impact:** Islem oncesi karar destegi ve kullanici guveni.  
**Resolution:**

### Q-0026 — Ucretli model / paketleme / ticari guven
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 02 Q065; Q-0020 baseline monetization ANSWERED  
**Question:** Ucretli deger abonelik, tekil ileri icerik veya baska bir modelle nasil paketlenirse kullanici icin makul olur; sponsor/ticari etki teknik onerilerin tarafsizligina nasil yansimamalidir?  
**Impact:** Ticari strateji ve teknik guven.  
**Resolution so far:** Lisansli ileri icerik, zengin gorseller ve ek kolayliklar ucretli deger adayi; temel dogrulanmis rehber, kritik safety bilgisi, bakim kaydi ve temel hatirlatmalar ucretsiz bekleniyor.

### Q-0027 — Kullanici motivasyonlari ve kullanim baglamlari
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** User types saturation MEDIUM  
**Question:** Kullanicilar MotoBakim'i maliyet, ogrenme, hobi, uzak lokasyon, acil ihtiyac veya baska hangi motivasyonlarla kullanir ve bu motivasyonlar urun beklentisini nasil degistirir?  
**Impact:** User segmentation, prioritization ve core journeys.  
**Resolution:**

### Q-0028 — Kullanici verisi uzerinde urun kontrol beklentisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Bakim gecmisi, fotograf/not ve coklu motosiklet verisi buyuyor  
**Question:** Kullanici kendi motosiklet, gecmis, fotograf ve not verilerini goruntuleme, duzeltme, disa aktarma veya silme konusunda hangi urun kontrolunu bekler?  
**Impact:** User trust, future product requirements; teknik implementasyon bu asamada belirlenmez.  
**Resolution:**

### Q-0029 — Zayif/olmayan baglanti durumunda temel deneyim beklentisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Rehberler garaj/yol gibi farkli ortamlarda kullanilabilir; baglanti beklentisi henuz sorulmadi  
**Question:** Kullanici islem sirasinda internet zayif veya yokken hangi bilgi ve devam eden islem baglamina erisebilmeyi bekler?  
**Impact:** Product continuity; teknik cozum sonraki asamalara aittir.  
**Resolution:**

---

## Answered Questions

### Q-0001 — Dogrulanmis teknik bilgi standardi
**Status:** ANSWERED  
**Evidence:** Batch 01 Q010-Q011  
**Resolution:** Motosiklet/varyantla uyumlu guvenilir teknik kaynak, belge surumu/sayfa-bolum kaniti ve insan incelemesi beklenir; internet tekrar sayisi yeterli degildir; kritik kaynak celiskisi cozulmeden tek deger secilmez.

### Q-0003 — Teknik mudahale kapsaminin ust ve alt siniri
**Status:** ANSWERED  
**Evidence:** Q020, Q034, Q045-Q052  
**Resolution:** Kullanici kategori bazinda butun sistemleri ogrenebilmek ister. Genel urun siniri mutlak kategori yasagindan cok motosiklet uyumu, gerekli ekipman/beceri/calisma kosulu ve sonucun dogrulanabilirligine dayanir. Kritik kosul eksikse uygulamali rehberlik durur veya hazirlik/ogrenme duzeyinde kalir. Kategoriye ozel ayrintilar Q-0004 gibi daha dar sorularla izlenir.

### Q-0005 — Deneyim seviyesine gore rehber farkliligi
**Status:** ANSWERED  
**Evidence:** Q007, Q014  
**Resolution:** Yeni kullanici ayrintili gorsel/hareket anlatimi; deneyimli kullanici kisa checklist/teknik detay ister. Guvenlik ve kritik dogrulama ikisinde de ayni kalmali.

### Q-0006 — `Guvenle yapilabilir` olcutu
**Status:** ANSWERED  
**Evidence:** Q017-Q021, Q034  
**Resolution:** Dogru motosiklet-rehber eslesmesi, dogrulanmis kaynak, hazir arac/parca/ekipman, anlasilmis riskler ve kritik sonucun dogrulanabilir olmasi gerekir; bu kosullar kaybolursa ilerleme durmalidir.

### Q-0007 — Gorsel anlatim gereksinimleri
**Status:** ANSWERED  
**Evidence:** Q014-Q015, Q025  
**Resolution:** Parcayi bulmak icin gercek/isaretli fotograf; gizli baglantida cizim; hareket yonu/sira kritikse kisa video; guvenlik/olcum/kontrol icin acik metin ve temel adimlarda basari kontrolu beklenir.

### Q-0008 — Bakim zamanlamasi kriterleri
**Status:** ANSWERED  
**Evidence:** Q031, Q033  
**Resolution:** Motosiklete uygun uretici kilometre ve sure araliklari temel alinmali, hangisi once dolarsa izlenmeli; onceki dogrulanmis tamamlanma tarihi ve gerekcelendirilebilen kullanim kosullari etkili olabilir; dogrulanmamis aralik uretilmemeli.

### Q-0009 — Bakim gecmisi veri beklentisi
**Status:** ANSWERED  
**Evidence:** Q029-Q030  
**Resolution:** Motor, islem/neden, tarih, kilometre, parca/malzeme, olcum ve son kontroller, fotograflar, notlar, yasanan sorun, isi yapan kisi ve rehber surumu saklanmak istenir; yarim/dogrulanamayan is tamamlandi sayilmaz.

### Q-0011 — Ariza teshisi ve onarim rehberligi ayrimi
**Status:** ANSWERED  
**Evidence:** Q012, Q022-Q024  
**Resolution:** Teshis belirtiden baslayip tehlike kontrolu ve ayirt edici kontrollerle kanit toplayan bir surectir; yeterli kanit olustugunda onarim rehberine baglanir. Olasi neden kesin teshis gibi sunulmaz.

### Q-0012 — Islem sirasinda beklenmeyen durum
**Status:** ANSWERED  
**Evidence:** Q025-Q028  
**Resolution:** Takilma/uyumsuzluk/hata durumunda daha ayrintili destek saglanir, gerekirse normal ilerleme durur; emniyete alma, dokunmama bilgisi, kanit kaydi, guvenli geri donus/profesyonel yardim yolu ve yarim islem baglaminin korunmasi beklenir.

### Q-0013 — Icerik governance ve insan incelemesi
**Status:** ANSWERED  
**Evidence:** Q040-Q044  
**Resolution:** Insan incelemesinde ilgili sistemde uygulamali deneyim ve uyum/kaynak/gorsel/arac/risk/son-kontrol degerlendirmesi beklenir. Kritik rehberde bagimsiz ikinci inceleme ek guven verir fakat tum kritik rehberlerde zorunlu politika olarak kanitlanmamistir. Kaynaklar uygulanabilirlik, guncellik ve amacla degerlendirilir; kritik guncelleme/hata durumunda yeniden inceleme, askiya alma/durdurma, kullanici uyarisi ve tarihsel surumun korunmasi beklenir. Cozulemeyen kritik kaynak celiskisinde uygulamali yonlendirme verilmez.

### Q-0014 — Modifikasyon ve fabrika disi degisikliklerin etkisi
**Status:** ANSWERED  
**Evidence:** Q038-Q039  
**Resolution:** Modifiye sistemde fabrika rehberi otomatik uygun sayilamaz. Degisiklik kullaniciya sorulur/gorselle ayristirilmaya calisilir; uygunluk belirlenemezse ilgili kritik adimlar baslamaz.

### Q-0015 — Gorsel icerik bulunamadiginda fallback
**Status:** ANSWERED  
**Evidence:** Q054  
**Resolution:** Gercek varyant fotografi yoksa tam motosiklete ait dogrulanmis cizim veya acik isaretli sema kabul edilebilir. Baska motosiklet fotografi ayniymis gibi kullanilamaz; fark belirsizse gorsele dayali adim baslatilmaz.

### Q-0016 — Guvenli esdeger arac/malzeme kriteri
**Status:** ANSWERED  
**Evidence:** Q053, Q055  
**Resolution:** Esdeger olcu, uyum, dayanim, malzeme, islev ve guvenlik gerekliliklerini karsilamali. Hassas olcum, dogru sikma veya guvenli kaldirma icin zorunlu ekipman yoksa islem ertelenmelidir.

### Q-0017 — Teshiste yeterli kanit esigi
**Status:** ANSWERED  
**Evidence:** Q056-Q058  
**Resolution:** En olasi neden icin birden fazla ayirt edici belirti/guvenli kontrol ayni nedeni desteklemeli ve alternatifler degerlendirilmelidir. Esit olasiliklarda ayristirici kontroller surer; sonuc yine belirsizse `Neden dogrulanamadi` olarak kapanir ve kanit ozeti uzmana aktarilabilir. Bu sabit nicel test sayisi degildir.

### Q-0018 — Kullanici beceri/readiness degerlendirmesi
**Status:** ANSWERED  
**Evidence:** Q050-Q052  
**Resolution:** Benzer is gecmisi, arac/olcum bilgisi, onceki kayitlar ve on kosul anlayisi degerlendirilir; oz-beyan tek basina yeterli degildir. Guvenle ogrenilebilir eksik beceri hazirliga yonlendirilebilir; ciddi sonuclu veya uzman dogrulamasi gerektiren kritik adim acilmaz.

### Q-0019 — Rehber surumu degistiginde davranis
**Status:** ANSWERED  
**Evidence:** Q059-Q060  
**Resolution:** Yarim iste surum farklari devamdan once gosterilir; kritik duzeltmede eski akista ilerleme durur ve mevcut fiziksel durum yeni rehberle eslestirilirken ilerleme/notlar korunur. Tamamlanmis tarihsel kayit sessizce degistirilmez; kullanilan surum ve geri cekilme/yeniden kontrol bilgisi korunur.

### Q-0020 — Monetization beklentisi
**Status:** ANSWERED  
**Evidence:** Q065  
**Resolution:** Lisansli ileri icerik, zengin gorseller ve ek kolayliklar ucretli deger adayi olabilir. Temel dogrulanmis rehberler, kritik guvenlik bilgisi, bakim kaydi ve temel hatirlatmalar ucretsiz beklenir. Guvenlik bilgisini ucretle gizlemek guven bozucudur. Kesin ticari model Q-0026'da aciktir.

---

## Kullanim Kurali

Yeni bir belirsizlik ortaya ciktiginda ayni format kullanilir. Soru ancak kullanici cevabi veya yetkili karar sureciyle `ANSWERED` yapilir. Genis bir soru cevaplandiginda daha dar yeni sorular acilabilir; eski cevap sessizce silinmez.
