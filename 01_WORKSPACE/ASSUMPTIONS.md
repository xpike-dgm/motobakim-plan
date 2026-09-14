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
| ASM-004 | Metinsel ve gorsel asamali rehber, genis bir islem yelpazesinde deneyimsiz kullanici icin yeterli olabilir. | Temel hedef hic bilmeyen kullaniciyi yonlendirmek. | Safety gating, olcum/ekipman, ses/altyazi/kolay etkileşim ve farkli aktif-islem baglamlari nedeniyle salt metin+gorsel yeterliligi daha fazla sorgulanmali. | CHALLENGED |
| ASM-005 | Uzmanlik gerektiren veya tehlikeli sayilabilecek islemler, kabul edilebilir bir guvenlik modeli icinde self-service rehber olarak sunulabilir. | Kullanici bu islemleri de ogrenmek istiyor. | Profesyonel yardima gecisin exact trigger'i ve kategoriye ozel uygulanabilirlik sonraki discovery'de netlesmeli. | SUPPORTED |
| ASM-006 | Marka, model, uretim yili ve islemi etkileyen ozellikler her motosiklette dogru varyanti kesin belirlemek icin yeterli olabilir. | Batch 01 minimum alanlari belirtti ama eksiksiz kimlik seti bilinmiyordu. | — | RESOLVED |
| ASM-007 | Hedeflenen islem katalogu boyunca kullanicinin gercek motosiklet/varyantina ait yeterli kalitede fotograf/cizim/video saglanabilir. | Gorsel kanit kritik goruluyor. | Gercek icerik kapsami daha sonra dogrulanmali; product fallback belirsizlikte stop-gate'tir. | CHALLENGED |
| ASM-008 | Yaklasik sure ve tahmini maliyet bilgisi kullaniciyi yaniltmadan yeterince guvenilir sunulabilir. | Q013 bu bilgileri islem oncesi karar icin istiyor. | — | RESOLVED |
| ASM-009 | `Guvenli esdeger arac/malzeme` icin islem ve motosiklete gore guvenilir urun kurallari tanimlanabilir. | Q017 guvenli alternatif beklentisi belirtti. | — | RESOLVED |
| ASM-010 | Belirti ve kontrollerden sonra `yeterli kanit` seviyesine ulasildigi urun acisindan tutarli bicimde belirlenebilir. | Teshis akisi kanit esigine bagli. | — | RESOLVED |
| ASM-011 | Kullanicinin gerekli beceri/readiness seviyesine sahip olup olmadigi uygulamali rehberlikten once anlamli bicimde degerlendirilebilir. | Beceri guvenli ilerleme kosulu. | — | RESOLVED |
| ASM-012 | Rehber surum degisikliklerinin yarim ve gecmis islemler uzerindeki etkisi kullaniciya anlasilir ve guvenli bicimde yonetilebilir. | Rehber surumu islem baglaminin parcasi. | — | RESOLVED |
| ASM-013 | Kullanici tarafindan bilinen ozellikler ve motosiklet fotograflari, teknik kimlik kodlarini ezbere istemeden cogu durumda dogru varyanti ayirt etmeye yeterli olabilir. | Kullanici belge/kod aramak istemiyor ve gorsel ayristirma bekliyor. | Gercek dunyada bu yaklasimin kapsama yeterliligi teknoloji/icerik feasibility asamalarinda dogrulanmali; product behavior belirsizlikte stop-gate olarak net. | OPEN |
| ASM-014 | Kritik rehberlerde bagimsiz ikinci insan incelemesi operasyonel olarak uygulanabilir ve yeterli nitelikli reviewer bulunabilir. | Q040 ikinci incelemenin guven verdigini soyluyor. | Hangi risk seviyesinde gerekli oldugu ve operasyonel feasibility sonraki asamalarda test edilmeli. | OPEN |
| ASM-015 | Modifiye motosikletler icin yeterli sayida dogrulanmis rehber veya guvenli ayristirma icerigi saglanabilir. | Q038-Q039 modifikasyonun rehber uygunlugunu degistirdigini gosterdi. | Yaygin aftermarket icin uyarlanmis rehber beklentisi, custom durumda teaching-only fallback net; gercek coverage feasibility'si hala acik. | OPEN |
| ASM-016 | Islem bazli readiness sinyalleri, kullaniciyi gereksiz yere engellemeden riskli ilerlemeyi azaltacak kadar guvenilir degerlendirilebilir. | Q051-Q052 readiness icin birden fazla sinyal istedi. | Product davranisi false-positive durumda yeni kanitla re-validation olarak netlesti; degerlendirme sinyallerinin gercek performansi sonraki validation/feasibility konusudur. | SUPPORTED |
| ASM-017 | Disarida yapilan islemlerin kanit seviyesi kullaniciya anlasilir ve tutarli bir guven derecesiyle ifade edilebilir. | Q063 kanitsiz dis kaydin dogrulanmis sayilmamasini istedi. | Global evidence taxonomy'nin baglama gore ayrismasi Q-0042 ile derinlesecek. | RESOLVED |
| ASM-018 | Ileri kolayliklar temel ucretsiz deneyimi bozmadan ucretli deger olusturabilir. | Q065 ve Q087 premium deger ornekleri verdi. | Paketleme/model tercihi ve willingness-to-pay genellemesi kesfedilmeli. | SUPPORTED |
| ASM-019 | Yol kenari/seyahat baglaminda daha kisa ve gorsel rehber sunumu ayni kritik safety standardini koruyarak kullanisli olabilir. | Q090 hizli tarama ve kisa gorsel adim istedi. | Hangi bilgilerin kisaltilamayacagi ve ses/kolay dokunus gibi aktif-islem erisilebilirligiyle iliskisi test edilmeli. | OPEN |
| ASM-020 | Kanit/provenance ve inceleme durumunu gorunur gostermek, kullanicinin resmi rehber, community katkisi ve dis islem arasindaki guven farkini anlamasi icin yeterli olabilir. | Q074, Q082 farkli kanit seviyelerinin gorunur olmasini istedi. | — | RESOLVED |
| ASM-021 | Offline erisilen rehberin surum/guncellik durumunun gorunur olmasi stale-content riskini kullanici acisindan yonetilebilir hale getirebilir. | Q091 offline icerikte surum/guncellik gorunurlugu istedi. | Kritik rehberlerde yalniz gorunurluk yeterli degil; anlamli freshness gate'in nasil tanimlanacagi acik. | CHALLENGED |
| ASM-022 | Kullanicinin transfer edecegi bakım gecmisini secmesi, yeni sahibin motosiklet gecmisini yaniltici bicimde eksiksiz sanmasina yol acmadan uygulanabilir. | Q120 selective transfer kontrolu istedi. | Eksik/parsiyel transferin yeni sahibine nasil temsil edilmesi gerektigi kesfedilmeli. | OPEN |
| ASM-023 | Kritik rehberlerde kullaniciyi gereksiz engellemeden stale-content riskini azaltacak anlamli bir `guncellik siniri` tanimlanabilir. | Q122 kritik offline rehberde freshness gate istedi. | Hangi rehberlerde, hangi risk kosullarinda ve hangi urun semantigiyle uygulanacagi kesfedilmeli; sayisal sure henuz yok. | OPEN |
| ASM-024 | Hesap/izinleri ilk degerden once zorunlu tutmadan rehber deneyimini gostermek, farkli user segmentlerinde de kabul edilebilir first-use modeli olabilir. | Q123 progressive first-use beklentisi verdi. | Record-only/shared/multi-bike/professional-adjacent baglamlarda first-use beklentisi test edilmeli. | OPEN |
| ASM-025 | Sesli veya minimum dokunuslu adim ilerletme, aktif bakım ortaminda usability'yi artirirken kritik safety teyitlerini koruyabilir. | Q125 dirty-hands/voice/easy-touch beklentisi verdi. | Gurultu, eldiven, yanlis komut ve kritik confirmation gibi product edge case'leri kesfedilmeli. | OPEN |

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
- ASM-003 SUPPORTED — Q075-Q077.
- ASM-005 SUPPORTED — Q068-Q069.
- ASM-008 RESOLVED — Q078-Q079.
- ASM-013 OPEN — Q066-Q067.
- ASM-017 RESOLVED — Q073-Q074.
- ASM-018 SUPPORTED — Q087-Q088.
- ASM-019 — ASM-021 yeni OPEN varsayimlar olarak eklendi.

### Batch 04
- **ASM-003 SUPPORTED — Q117:** Record-only kullanici icin de bakım tracking degeri teyit edildi; gercek coverage feasibility'si ayridir.
- **ASM-004 CHALLENGED — Q099, Q125:** Teaching/application gate ve alternatif erisim bicimleri salt metin+gorsel varsayimini daha da zayiflatti.
- **ASM-005 SUPPORTED — Q097-Q101:** High-consequence icerik ogrenilebilir kalir; application kosula baglidir ve profesyonel escalation self-service'in ziddi degildir.
- **ASM-016 SUPPORTED — Q096-Q098:** False-positive durumunda serbest override degil, yeni kanitla re-validation beklenir; safety eksigi oz-beyanla gecilemez.
- **ASM-018 SUPPORTED — Q114-Q115:** Analysis/storage/multi-garage/personalization premium adayi; non-recurring optional value icin one-time tercih olabilir; final paket yok.
- **ASM-020 RESOLVED — Q109-Q110:** User assertion/documented/reviewed/verified product semantigi yeterince netlesti; baglamsal taxonomy ayrimi ayri sorudur.
- **ASM-021 CHALLENGED — Q122:** Version/freshness visibility tek basina yeterli degil; kritik stale rehber application'i yeniden kontrol edilene kadar kapanabilir.
- ASM-022 — ASM-025 yeni OPEN varsayimlar olarak eklendi.
