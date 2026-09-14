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
| ASM-003 | Uygulama, kullanicinin sonraki bakim ihtiyacini yeterince dogru belirleyebilir. | Siradaki bakim ve zamanlama isteniyor. | Agir kullanim/istisna kosullari ve farkli bakim turlerinde yeterlilik test edilmeli. | SUPPORTED |
| ASM-004 | Metinsel ve gorsel asamali rehber, genis bir islem yelpazesinde deneyimsiz kullanici icin yeterli olabilir. | Temel hedef hic bilmeyen kullaniciyi yonlendirmek. | Gercek fotograf, cizim, video, recovery, stop-gate ve farkli islem kategorilerinin gereksinimleri daha fazla dogrulanmali. | CHALLENGED |
| ASM-005 | Uzmanlik gerektiren veya tehlikeli sayilabilecek islemler, kabul edilebilir bir guvenlik modeli icinde self-service rehber olarak sunulabilir. | Kullanici bu islemleri de ogrenmek istiyor. | Islem sinifi bazli beceri, ekipman, dogrulama ve durdurma sinirlari belirlenmeli. | SUPPORTED |
| ASM-006 | Marka, model, uretim yili ve islemi etkileyen ozellikler her motosiklette dogru varyanti kesin belirlemek icin yeterli olabilir. | Q008-Q009 minimum alanlari belirtti ama eksiksiz kimlik seti bilinmiyor. | Motor tipi/kodu, pazar varyanti, uretim donemi, fabrika opsiyonu ve modifikasyon ihtiyacini test et. | OPEN |
| ASM-007 | Hedeflenen islem katalogu boyunca kullanicinin gercek motosiklet/varyantina ait yeterli kalitede fotograf/cizim/video saglanabilir. | Q015 ve Q025 gorsel kaniti kritik goruyor. | Gorsel bulunamadigi veya varyantla eslesmedigi durumdaki urun davranisini netlestir. | OPEN |
| ASM-008 | Yaklasik sure ve tahmini maliyet bilgisi kullaniciyi yaniltmadan yeterince guvenilir sunulabilir. | Q013 bu bilgileri islem oncesi karar icin istiyor. | Degiskenlik, guven araligi ve hangi durumlarda gosterilmemesi gerektigini kesfet. | OPEN |
| ASM-009 | `Guvenli esdeger arac/malzeme` icin islem ve motosiklete gore guvenilir urun kurallari tanimlanabilir. | Q017 guvenli alternatif beklentisi belirtti. | Bir alternatifin ne zaman gercekten guvenli esdeger oldugunu netlestir. | OPEN |
| ASM-010 | Belirti ve kontrollerden sonra `yeterli kanit` seviyesine ulasildigi urun acisindan tutarli bicimde belirlenebilir. | Q022-Q024 teshis akisini kanit esigine bagliyor. | Eşit olasilik, sonucsuz test ve olcum gerektiren durumlari kesfet. | OPEN |
| ASM-011 | Kullanicinin gerekli beceri/readiness seviyesine sahip olup olmadigi uygulamali rehberlikten once anlamli bicimde degerlendirilebilir. | Q020-Q021 ve Q034 beceriyi guvenli ilerleme kosulu yapiyor. | Kullanici beyanı, onceki deneyim, gorev bazli on kosul veya baska urun sinyallerinin rolunu kesfet. | OPEN |
| ASM-012 | Rehber surum degisikliklerinin yarim ve gecmis islemler uzerindeki etkisi kullaniciya anlasilir ve guvenli bicimde yonetilebilir. | Q028-Q030 rehber surumunu islem baglaminin parcasi yapiyor. | Surum degisince devam/yeniden baslama/uyari davranisini netlestir. | OPEN |

## Batch 01 evidence update

- **ASM-001 RESOLVED — Q008-Q009:** Marka/model tek basina yeterli degildir; uretim yili ve islemi degistiren ozellikler de beklenir, varyant kesinlestirilmelidir.
- **ASM-002 RESOLVED — Q007, Q014:** Yeni kullanici ayrintili gorsel/hareket anlatimi; deneyimli kullanici hizli checklist/teknik detay ister. Guvenlik ve kritik dogrulama ortaktir.
- **ASM-003 SUPPORTED — Q031, Q033:** Uretici kilometre/sure araliklari ve dogrulanmis son tamamlanma kaydi temel adaylardir; tum istisnalar henuz kapsanmadi.
- **ASM-004 CHALLENGED — Q014-Q015, Q025-Q027:** Salt metin+gorsel yeterli olmayabilir; fotograf, cizim, video, basari kontrolu ve recovery ihtiyaci ortaya cikti.
- **ASM-005 SUPPORTED — Q019-Q021, Q034:** Zorlu islemler tamamen gizlenmemeli; fakat gerekli kosullar yoksa uygulamali ilerleme durmalidir.
