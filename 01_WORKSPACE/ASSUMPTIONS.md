# ASSUMPTIONS

Status: APPROVED

Kaniti veya kullanici onayi olmayan kabuller burada tutulur. Bu maddeler gercek gibi kullanilamaz ve discovery sirasinda dogrulanmalidir.

**Approved registry by user:** 2026-09-14  
**Important:** Belgenin `APPROVED` olmasi, icindeki acik varsayimlarin dogrulandigi anlamina gelmez.

## Status semantics

- `OPEN` — henuz yeterli kanit yok
- `SUPPORTED` — yeni kanit varsayimi destekliyor ama tamamen cozmuyor
- `CHALLENGED` — yeni kanit varsayimin fazla basit/yanlis olabilecegini gosteriyor
- `RESOLVED` — varsayimin sordugu urun belirsizligi kullanici kanitiyla yeterince cevaplandi; tarihsel kayit korunur

| ID | Assumption | Why It Exists | Validation Needed | Status |
|---|---|---|---|---|
| ASM-001 | Marka/model gibi temel motosiklet kimligi, motosiklete yeterince ozel rehber sunmak icin tek basina yeterli olabilir. | Ilk baseline varyant ayrimini bilmiyordu. | — | RESOLVED |
| ASM-002 | Yeni/az deneyimli ve deneyimli kullanicilar ayni temel rehber yapisini kullanabilir. | Iki deneyim seviyesi hedefleniyordu ancak fark bilinmiyordu. | — | RESOLVED |
| ASM-003 | Uygulama, kullanicinin sonraki bakim ihtiyacini yeterince dogru belirleyebilir. | Siradaki bakim ve zamanlama isteniyor. | Gercek icerik/kaynak kapsaminin yeterliligi sonraki teknoloji/operasyon asamalarinda test edilir; product expectation belirsizlik durumunu da desteklemelidir. | SUPPORTED |
| ASM-004 | Metinsel ve gorsel asamali rehber, genis bir islem yelpazesinde deneyimsiz kullanici icin yeterli olabilir. | Temel hedef hic bilmeyen kullaniciyi yonlendirmek. | Islem bazli readiness, ozel ekipman, olcum, destekleme ve high-consequence stop-gate ihtiyaci nedeniyle salt anlatim yeterliligi daha fazla sorgulanmali. | CHALLENGED |
| ASM-005 | Uzmanlik gerektiren veya tehlikeli sayilabilecek islemler, kabul edilebilir bir guvenlik modeli icinde self-service rehber olarak sunulabilir. | Kullanici bu islemleri de ogrenmek istiyor. | Profesyonel yardima gecis, readiness override ve kategoriye ozel uygulanabilirlik daha fazla kesfedilmeli. | SUPPORTED |
| ASM-006 | Marka, model, uretim yili ve islemi etkileyen ozellikler her motosiklette dogru varyanti kesin belirlemek icin yeterli olabilir. | Batch 01 minimum alanlari belirtti ama eksiksiz kimlik seti bilinmiyordu. | — | RESOLVED |
| ASM-007 | Hedeflenen islem katalogu boyunca kullanicinin gercek motosiklet/varyantina ait yeterli kalitede fotograf/cizim/video saglanabilir. | Gorsel kanit kritik goruluyor. | Gercek icerik kapsami daha sonra dogrulanmali; product fallback belirsizlikte stop-gate'tir. | CHALLENGED |
| ASM-008 | Yaklasik sure ve tahmini maliyet bilgisi kullaniciyi yaniltmadan yeterince guvenilir sunulabilir. | Q013 bu bilgileri islem oncesi karar icin istiyor. | — | RESOLVED |
| ASM-009 | `Guvenli esdeger arac/malzeme` icin islem ve motosiklete gore guvenilir urun kurallari tanimlanabilir. | Q017 guvenli alternatif beklentisi belirtti. | — | RESOLVED |
| ASM-010 | Belirti ve kontrollerden sonra `yeterli kanit` seviyesine ulasildigi urun acisindan tutarli bicimde belirlenebilir. | Teshis akisi kanit esigine bagli. | — | RESOLVED |
| ASM-011 | Kullanicinin gerekli beceri/readiness seviyesine sahip olup olmadigi uygulamali rehberlikten once anlamli bicimde degerlendirilebilir. | Beceri guvenli ilerleme kosulu. | — | RESOLVED |
| ASM-012 | Rehber surum degisikliklerinin yarim ve gecmis islemler uzerindeki etkisi kullaniciya anlasilir ve guvenli bicimde yonetilebilir. | Rehber surumu islem baglaminin parcasi. | — | RESOLVED |
| ASM-013 | Kullanici tarafindan bilinen ozellikler ve motosiklet fotograflari, teknik kimlik kodlarini ezbere istemeden cogu durumda dogru varyanti ayirt etmeye yeterli olabilir. | Kullanici belge/kod aramak istemiyor ve gorsel ayristirma bekliyor. | Gercek dunyada bu yaklasimin kapsama yeterliligi teknoloji/icerik feasibility asamalarinda dogrulanmali; product behavior belirsizlikte stop-gate olarak net. | OPEN |
| ASM-014 | Kritik rehberlerde bagimsiz ikinci insan incelemesi operasyonel olarak uygulanabilir ve yeterli nitelikli reviewer bulunabilir. | Q040 ikinci incelemenin guven verdigini soyluyor. | Hangi risk seviyesinde gerekli oldugu ve operasyonel feasibility sonraki asamalarda test edilmeli. | OPEN |
| ASM-015 | Modifiye motosikletler icin yeterli sayida dogrulanmis rehber veya guvenli ayristirma icerigi saglanabilir. | Q038-Q039 modifikasyonun rehber uygunlugunu degistirdigini gosterdi. | Yaygin/ozel modifikasyonlarda beklenen urun kapsami Batch 04+ discovery'de netlestirilmeli. | OPEN |
| ASM-016 | Islem bazli readiness sinyalleri, kullaniciyi gereksiz yere engellemeden riskli ilerlemeyi azaltacak kadar guvenilir degerlendirilebilir. | Q051-Q052 readiness icin birden fazla sinyal istedi. | Yanlis engelleme / fazla serbest birakma toleransi ve override beklentisi kesfedilmeli. | OPEN |
| ASM-017 | Disarida yapilan islemlerin kanit seviyesi kullaniciya anlasilir ve tutarli bir guven derecesiyle ifade edilebilir. | Q063 kanitsiz dis kaydin dogrulanmis sayilmamasini istedi. | Global evidence taxonomy'nin son hali Q-0033 ile derinlesecek. | RESOLVED |
| ASM-018 | Ileri kolayliklar temel ucretsiz deneyimi bozmadan ucretli deger olusturabilir. | Q065 ve Q087 premium deger ornekleri verdi. | Paketleme/model tercihi ve willingness-to-pay genellemesi kesfedilmeli. | SUPPORTED |
| ASM-019 | Yol kenari/seyahat baglaminda daha kisa ve gorsel rehber sunumu ayni kritik safety standardini koruyarak kullanisli olabilir. | Q090 hizli tarama ve kisa gorsel adim istedi. | Hangi bilgilerin kisaltilamayacagi ve normal rehbere gecis beklentisi test edilmeli. | OPEN |
| ASM-020 | Kanit/provenance ve inceleme durumunu gorunur gostermek, kullanicinin resmi rehber, community katkisi ve dis islem arasindaki guven farkini anlamasi icin yeterli olabilir. | Q074, Q082 farkli kanit seviyelerinin gorunur olmasini istedi. | Etiket/dil beklentileri ve edge case'ler Q-0033'te derinlestirilmeli. | OPEN |
| ASM-021 | Offline erisilen rehberin surum/guncellik durumunun gorunur olmasi stale-content riskini kullanici acisindan yonetilebilir hale getirebilir. | Q091 offline icerikte surum/guncellik gorunurlugu istedi. | Rehber offline iken geri cekilmis veya kritik duzeltilmis ise beklenen davranis Q-0040'ta kesfedilmeli. | OPEN |

## Evidence history

### Batch 01
- ASM-001 RESOLVED — Q008-Q009.
- ASM-002 RESOLVED — Q007, Q014.
- ASM-003 SUPPORTED — Q031, Q033.
- ASM-004 CHALLENGED — Q014-Q015, Q025-Q027.
- ASM-005 SUPPORTED — Q019-Q021, Q034.

### Batch 02
- ASM-003 SUPPORTED — Q061, Q064.
- ASM-004 CHALLENGED — Q047-Q054.
- ASM-005 SUPPORTED — Q045-Q050, Q052.
- ASM-006 RESOLVED — Q036-Q039.
- ASM-007 CHALLENGED — Q054.
- ASM-009 RESOLVED — Q053, Q055.
- ASM-010 RESOLVED — Q056-Q058.
- ASM-011 RESOLVED — Q050-Q052.
- ASM-012 RESOLVED — Q059-Q060.

### Batch 03
- **ASM-003 SUPPORTED — Q075-Q077:** Dogru davranis her durumda kesin tarih uretmek degil; kaynak eksikliginde belirsizligi acikca korumak ve yalniz dogrulanmis istisnalari uygulamaktir.
- **ASM-005 SUPPORTED — Q068-Q069:** Yuksek gerilim/basincli/yuksek-sicaklik gibi alanlar kategori olarak dislanmak istenmiyor; dogrulanmayan safety kosulunda uygulamali progression kapanir.
- **ASM-008 RESOLVED — Q078-Q079:** Sure aralik ve belirsizlikle; maliyet kalem/tarih/varsayim gorunurlugu ile sunulabilir.
- **ASM-013 OPEN — Q066-Q067:** Kullanici gorsel/observable ayristirmayi tercih eder; bunun gercek dunyada yeterlilik feasibility'si kanitlanmadi. Belirsizlikte stop-gate netlesti.
- **ASM-017 RESOLVED — Q073-Q074:** Duzeltme izi ve farkli evidence seviyelerinin gorunurlugu product expectation olarak netlesti.
- **ASM-018 SUPPORTED — Q087-Q088:** Core ucretsiz, convenience/deeper-analysis premium adayi olabilir; final paket/model yok.
- ASM-019 — ASM-021 yeni OPEN varsayimlar olarak eklendi.
