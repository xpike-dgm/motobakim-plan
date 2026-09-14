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
| ASM-003 | Uygulama, kullanicinin sonraki bakım ihtiyacini yeterince dogru belirleyebilir. | Siradaki bakım ve zamanlama isteniyor. | Gercek icerik/kaynak coverage'i sonraki teknoloji/operasyon asamalarinda test edilir; product behavior uncertainty'yi de desteklemelidir. | SUPPORTED |
| ASM-004 | Metinsel ve gorsel asamali rehber, genis bir islem yelpazesinde deneyimsiz kullanici icin yeterli olabilir. | Temel hedef hic bilmeyen kullaniciyi yonlendirmek. | Safety gating, olcum/ekipman ve multimodal active-repair needs nedeniyle salt metin+gorsel yeterliligi sorgulanir. | CHALLENGED |
| ASM-005 | Uzmanlik gerektiren veya tehlikeli islemler kabul edilebilir safety modeli icinde self-service rehber olarak sunulabilir. | Kullanici bu islemleri de ogrenmek istiyor. | Product-level stop/re-entry semantigi net; gercek coverage/feasibility ve kategoriye ozel uygulanabilirlik daha sonra test edilmeli. | SUPPORTED |
| ASM-006 | Marka/model/yil ve islemi etkileyen ozellikler her motosiklette dogru varyanti kesin belirlemek icin yeterli olabilir. | Batch 01 minimum alanlari belirtti. | — | RESOLVED |
| ASM-007 | Hedeflenen katalog boyunca kullanicinin gercek motosiklet/varyantina ait yeterli kalitede fotograf/cizim/video saglanabilir. | Gorsel kanit kritik. | Gercek content coverage daha sonra dogrulanmali; product fallback belirsizlikte stop-gate'tir. | CHALLENGED |
| ASM-008 | Yaklasik sure ve tahmini maliyet kullaniciyi yaniltmadan sunulabilir. | Q013 pre-task karar destegi istiyor. | — | RESOLVED |
| ASM-009 | `Guvenli esdeger arac/malzeme` icin guvenilir product rules tanimlanabilir. | Q017 alternative beklentisi. | — | RESOLVED |
| ASM-010 | Belirti/kontrollerden sonra `yeterli kanit` product-level olarak tutarli belirlenebilir. | Diagnosis evidence threshold ihtiyaci. | — | RESOLVED |
| ASM-011 | Task-specific readiness anlamli bicimde degerlendirilebilir. | Safety progression buna bagli. | — | RESOLVED |
| ASM-012 | Guide-version degisiklikleri yarim/gecmis islerde anlasilir ve guvenli yonetilebilir. | Rehber surumu islem baglaminin parcasi. | — | RESOLVED |
| ASM-013 | Kullanici tarafindan bilinen ozellikler ve fotograflar teknik kimlik kodu istemeden cogu durumda dogru varyanti ayirt etmeye yeterli olabilir. | Kullanici belge/kod aramak istemiyor. | Gercek dunya coverage'i teknoloji/content feasibility asamalarinda test edilmeli. | OPEN |
| ASM-014 | Kritik rehberlerde bagimsiz ikinci insan incelemesi operasyonel olarak uygulanabilir ve yeterli reviewer bulunabilir. | Q040 ikinci incelemenin guven verdigini soyluyor. | Risk seviyesi ve operasyonel feasibility sonraki asamalarda test edilmeli. | OPEN |
| ASM-015 | Modifiye motosikletler icin yeterli verified guide veya guvenli ayrim icerigi saglanabilir. | Modification fit application'i etkiliyor. | Common aftermarket product expectation net; real coverage feasibility acik. | OPEN |
| ASM-016 | Task-specific readiness signals, gereksiz engellemeyi sinirlarken riskli progression'i azaltacak kadar guvenilir degerlendirilebilir. | Q051-Q052 readiness sinyalleri. | Product behavior re-validation ile net; actual signal performance sonraki validation/feasibility konusu. | SUPPORTED |
| ASM-017 | Disarida yapilan islemlerin evidence seviyesi anlasilir ve tutarli ifade edilebilir. | Q063 external work trust ihtiyaci. | Product semantics context-specific refinement ile yeterince cevaplandi. | RESOLVED |
| ASM-018 | Ileri kolayliklar temel ucretsiz deneyimi bozmadan premium value olusturabilir. | Q065/Q087 premium adaylari. | Core-vs-premium boundary guclendi; business viability, pricing ve WTP daha sonra validate edilmeli. | SUPPORTED |
| ASM-019 | Roadside/active-repair baglaminda daha kolay interaction ayni kritik safety standardini koruyarak kullanisli olabilir. | Q090/Q125 hizli ve hands-free ihtiyaclari. | Product safety invariants Q150-Q152 ile desteklendi; actual usability/feasibility sonra test edilmeli. | SUPPORTED |
| ASM-020 | Provenance/review status gorunurlugu, resmi rehber/community/dis islem arasindaki trust farkini anlatabilir. | Q074/Q082. | Basit ayrim cozuldu; high-trust durumda label-only yeterli degil, explicit claim explanation gerekir. | RESOLVED |
| ASM-021 | Offline rehberin version/freshness gorunurlugu stale-content riskini tek basina yonetilebilir hale getirebilir. | Q091. | Q122 ve Q147-Q149 visibility'nin critical application icin yetersiz oldugunu gosterdi. | CHALLENGED |
| ASM-022 | Selective ownership transfer, yeni sahibin partial history'yi complete sanmasina yol acmadan uygulanabilir. | Q120 selective transfer istedi. | Product semantics Q135-Q137 ile yeterince tanimlandi; real comprehension daha sonra usability validation olabilir. | RESOLVED |
| ASM-023 | Kritik rehberlerde gereksiz bloklamadan stale riskini azaltacak anlamli freshness siniri tanimlanabilir. | Q122 freshness gate istedi. | Claim/risk scope Q147-Q149 ile desteklendi; numeric/operational threshold ve real-world policy daha sonra belirlenmeli. | SUPPORTED |
| ASM-024 | Hesap/izinleri ilk degerden once zorunlu tutmadan farkli segmentlere acceptable first-use sunulabilir. | Q123 account-light value. | Record-only/shared/multi-bike first value ve profile trigger'lari Q153-Q155 ile desteklendi; broader validation acik. | SUPPORTED |
| ASM-025 | Voice/minimum-touch interaction usability'yi artirirken kritik safety confirmation korunabilir. | Q125 active-repair accessibility. | Product safety boundaries Q150-Q152 ile desteklendi; technology/performance feasibility acik. | SUPPORTED |
| ASM-026 | Partial-history disclosure + covered period + visible gaps, new owner's incomplete history'yi complete sanma riskini yeterince azaltabilir. | Q135-Q136 product semantics bunu ongoruyor. | Gercek comprehension/usability validation gerekir. | OPEN |
| ASM-027 | Reviewable explicit critical confirmations active repair safety'sini korurken kabul edilemez friction yaratmadan uygulanabilir. | Q151 critical confirmation istedi. | Gercek task usability ve error-rate validation gerekir. | OPEN |
| ASM-028 | Persistence/cross-device/collaboration ihtiyacinda profile istemek daha genis hedef user base icin dogal kabul edilir. | Q155 profile trigger'i tanimladi. | Tek kullanici kaniti; daha genis segment validation gerekir. | OPEN |
| ASM-029 | Contributor identity kaldirilirken de-identified safety review trace korunmasi withdrawal beklentisi ile safety-learning ihtiyacini birlikte karsilayabilir. | Q130. | Privacy/legal/operational feasibility sonraki asamalarda degerlendirilmeli. | OPEN |
| ASM-030 | Basic multi-bike + reasonable history free kalirken large media, advanced analysis ve extensive collaboration sustainable premium value yaratabilir. | Q144-Q146. | Business viability/WTP market research gerekir; product intent tek basina yeterli degil. | OPEN |

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
- ASM-019 — ASM-021 eklendi.

### Batch 04
- ASM-003 SUPPORTED — Q117.
- ASM-004 CHALLENGED — Q099, Q125.
- ASM-005 SUPPORTED — Q097-Q101.
- ASM-016 SUPPORTED — Q096-Q098.
- ASM-018 SUPPORTED — Q114-Q115.
- ASM-020 RESOLVED — Q109-Q110.
- ASM-021 CHALLENGED — Q122.
- ASM-022 — ASM-025 eklendi.

### Batch 05
- **ASM-005 SUPPORTED — Q126-Q128:** Professional recommendation ile mandatory safety closure ayrildi; re-entry evidence-gated.
- **ASM-016 SUPPORTED — Q126-Q127:** False-positive -> re-evaluation/self-remediation/re-validation; self-assertion stop'u kaldirmaz.
- **ASM-017 RESOLVED refinement — Q132-Q134:** Common vocabulary + context-specific verified claim.
- **ASM-018 SUPPORTED refinement — Q144-Q146:** Basic multi-bike/reasonable history core; large media/advanced analysis/extensive collaboration premium adayi.
- **ASM-019 SUPPORTED — Q150-Q152:** Alternate modalities critical safety invariants'i kaldirmadan deger sunabilir.
- **ASM-020 RESOLVED refinement — Q132-Q134:** High-trust contexts explicit evidence explanation ister.
- **ASM-021 CHALLENGED — Q147-Q149:** Critical stale application visibility ile degil gate ile yonetilir.
- **ASM-022 RESOLVED — Q135-Q137:** Partial disclosure, gaps, private isolation ve correction proposal semantigi netlesti.
- **ASM-023 SUPPORTED — Q147-Q149:** Freshness scope claim/risk sensitivity ile baglantili; numeric threshold yok.
- **ASM-024 SUPPORTED — Q153-Q155:** Segment-specific first value + persistence/collaboration profile trigger'lari.
- **ASM-025 SUPPORTED — Q150-Q152:** Voice/easy-touch safety confirmation boundaries.
- ASM-026 — ASM-030 yeni OPEN varsayimlar olarak eklendi.
