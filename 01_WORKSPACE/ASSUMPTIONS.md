# ASSUMPTIONS

Status: APPROVED

Kaniti veya kullanici onayi olmayan kabuller burada tutulur. Bu maddeler gercek gibi kullanilamaz ve discovery sirasinda dogrulanmalidir.

**Approved registry by user:** 2026-09-14  
**Important:** Belgenin `APPROVED` olmasi, icindeki acik varsayimlarin dogrulandigi anlamina gelmez.

## Status semantics

- `OPEN` — henuz yeterli kanit yok
- `SUPPORTED` — yeni kanit varsayimi destekliyor ama tamamen cozmuyor
- `CHALLENGED` — yeni kanit varsayimin fazla basit/yanlis olabilecegini gosteriyor
- `RESOLVED` — varsayimin sordugu belirsizlik kullanici kanitiyla yeterince cevaplandi; tarihsel kayit korunur

| ID | Assumption | Why It Exists | Validation Needed | Status |
|---|---|---|---|---|
| ASM-001 | Marka/model gibi temel motosiklet kimligi, motosiklete yeterince ozel rehber sunmak icin tek basina yeterli olabilir. | Ilk baseline varyant ayrimini bilmiyordu. | — | RESOLVED |
| ASM-002 | Yeni/az deneyimli ve deneyimli kullanicilar ayni temel rehber yapisini kullanabilir. | Iki deneyim seviyesi hedefleniyordu ancak fark bilinmiyordu. | — | RESOLVED |
| ASM-003 | Uygulama, kullanicinin sonraki bakim ihtiyacini yeterince dogru belirleyebilir. | Siradaki bakim ve zamanlama isteniyor. | Degistirilmis parca, ureticiye ozel istisna ve kullanici kosul bilgisi verilmedigi durumlar daha fazla test edilmeli. | SUPPORTED |
| ASM-004 | Metinsel ve gorsel asamali rehber, genis bir islem yelpazesinde deneyimsiz kullanici icin yeterli olabilir. | Temel hedef hic bilmeyen kullaniciyi yonlendirmek. | Islem bazli readiness, ozel ekipman, olcum, destekleme ve kategoriye ozel stop-gate ihtiyaci nedeniyle salt anlatim yeterliligi daha fazla sorgulanmali. | CHALLENGED |
| ASM-005 | Uzmanlik gerektiren veya tehlikeli sayilabilecek islemler, kabul edilebilir bir guvenlik modeli icinde self-service rehber olarak sunulabilir. | Kullanici bu islemleri de ogrenmek istiyor. | Yuksek gerilim ve diger kapsanmayan yuksek-sonuclu kategorilerde kosullar test edilmeli. | SUPPORTED |
| ASM-006 | Marka, model, uretim yili ve islemi etkileyen ozellikler her motosiklette dogru varyanti kesin belirlemek icin yeterli olabilir. | Batch 01 minimum alanlari belirtti ama eksiksiz kimlik seti bilinmiyordu. | — | RESOLVED |
| ASM-007 | Hedeflenen islem katalogu boyunca kullanicinin gercek motosiklet/varyantina ait yeterli kalitede fotograf/cizim/video saglanabilir. | Gorsel kanit kritik goruluyor. | Gercek varyant fotografi bulunmadiginda dogrulanmis cizim/sema fallback olabilir; katalog genelinde yeterli gorsel kapsama yine kanitlanmadi. | CHALLENGED |
| ASM-008 | Yaklasik sure ve tahmini maliyet bilgisi kullaniciyi yaniltmadan yeterince guvenilir sunulabilir. | Q013 bu bilgileri islem oncesi karar icin istiyor. | Degiskenlik, guven araligi ve hangi durumlarda gosterilmemesi gerektigini kesfet. | OPEN |
| ASM-009 | `Guvenli esdeger arac/malzeme` icin islem ve motosiklete gore guvenilir urun kurallari tanimlanabilir. | Q017 guvenli alternatif beklentisi belirtti. | — | RESOLVED |
| ASM-010 | Belirti ve kontrollerden sonra `yeterli kanit` seviyesine ulasildigi urun acisindan tutarli bicimde belirlenebilir. | Teshis akisi kanit esigine bagli. | — | RESOLVED |
| ASM-011 | Kullanicinin gerekli beceri/readiness seviyesine sahip olup olmadigi uygulamali rehberlikten once anlamli bicimde degerlendirilebilir. | Beceri guvenli ilerleme kosulu. | — | RESOLVED |
| ASM-012 | Rehber surum degisikliklerinin yarim ve gecmis islemler uzerindeki etkisi kullaniciya anlasilir ve guvenli bicimde yonetilebilir. | Rehber surumu islem baglaminin parcasi. | — | RESOLVED |
| ASM-013 | Kullanici tarafindan bilinen ozellikler ve motosiklet fotograflari, teknik kimlik kodlarini ezbere istemeden cogu durumda dogru varyanti ayirt etmeye yeterli olabilir. | Q036 kullanici-dostu kimlik toplama beklentisi belirtti. | Kullanici-dostu bilgiler/fotograf yetersiz kaldiginda kabul edilecek ek kanitlari kesfet. | OPEN |
| ASM-014 | Kritik rehberlerde bagimsiz ikinci insan incelemesi operasyonel olarak uygulanabilir ve yeterli nitelikli reviewer bulunabilir. | Q040 ikinci incelemenin guven verdigini soyluyor. | Hangi risk seviyesinde gerekli oldugu ve bunun kullanici beklentisi mi operasyon politikasi mi oldugu ayrilmali. | OPEN |
| ASM-015 | Modifiye motosikletler icin yeterli sayida dogrulanmis rehber veya guvenli ayristirma icerigi saglanabilir. | Q038-Q039 modifikasyonun rehber uygunlugunu degistirdigini gosterdi. | Yaygin/ozel modifikasyonlarda ne kadar kapsama beklendigi test edilmeli. | OPEN |
| ASM-016 | Islem bazli readiness sinyalleri, kullaniciyi gereksiz yere engellemeden riskli ilerlemeyi azaltacak kadar guvenilir degerlendirilebilir. | Q051-Q052 readiness icin birden fazla sinyal istedi. | Yanlis engelleme / fazla serbest birakma toleransi ve override beklentisi kesfedilmeli. | OPEN |
| ASM-017 | Disarida yapilan islemlerin kanit seviyesi kullaniciya anlasilir ve tutarli bir guven derecesiyle ifade edilebilir. | Q063 kanitsiz dis kaydin dogrulanmis sayilmamasini istedi. | Hangi kanitlarin hangi guven seviyesine denk geldigi ve kayit duzeltme izi kesfedilmeli. | OPEN |
| ASM-018 | Lisansli ileri icerik, zengin gorseller ve ek kolayliklar temel ucretsiz deneyimi bozmadan sürdürülebilir ucretli deger olusturabilir. | Q065 ilk monetization sinirini verdi. | Paketleme/model tercihi ve sponsor/ticari etkinin guvene etkisi kesfedilmeli. | OPEN |

## Evidence history

### Batch 01
- ASM-001 RESOLVED — Q008-Q009.
- ASM-002 RESOLVED — Q007, Q014.
- ASM-003 SUPPORTED — Q031, Q033.
- ASM-004 CHALLENGED — Q014-Q015, Q025-Q027.
- ASM-005 SUPPORTED — Q019-Q021, Q034.

### Batch 02
- **ASM-003 SUPPORTED — Q061, Q064:** Dogrulanmis kullanim kosulu ve oncelik mantigi netlesti; tum istisnalar kapsanmadi.
- **ASM-004 CHALLENGED — Q047-Q054:** Ayrintili anlatimin yaninda destek, ozel ekipman, olcum ve stop-gate kosullari gerekiyor.
- **ASM-005 SUPPORTED — Q045-Q050, Q052:** Yuksek-sonuclu alanlar tamamen dislanmiyor; kosullar yetersizse uygulamali ilerleme kapanmali.
- **ASM-006 RESOLVED — Q036-Q039:** Kimlik seti sabit minimum alanlardan ibaret degil; islemi/malzemeyi/guvenligi etkileyen versiyon kesinlesmeli, modifikasyon ayrica dikkate alinmali.
- **ASM-007 CHALLENGED — Q054:** Tam varyant fotografi her zaman sart degil; dogrulanmis cizim/sema fallback olabilir, fakat gorsel kapsama varsayimi hala guclu.
- **ASM-009 RESOLVED — Q053, Q055:** Esdegerlik olcu/uyum/dayanim/malzeme/islev/guvenlik gereksinimleriyle dogrulanmali; kritik ekipman yoksa erteleme gerekir.
- **ASM-010 RESOLVED — Q056-Q058:** En olasi neden icin birden fazla ayirt edici kanit ve alternatiflerin degerlendirilmesi; esit/sonucsuz durumda sahte kesinlikten kacinma beklentisi netlesti.
- **ASM-011 RESOLVED — Q050-Q052:** Benzer is gecmisi, arac/olcum bilgisi, kayitlar ve on kosul anlayisi readiness sinyalleridir; oz-beyan tek basina yeterli degildir.
- **ASM-012 RESOLVED — Q059-Q060:** Surum farklari gorunur olmali; kritik duzeltmede eski akış durmali; ilerleme/notlar ve tarihsel kullanilan surum korunmalidir.
