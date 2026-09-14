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
| ASM-018 | Ileri kolayliklar temel ucretsiz deneyimi bozmadan ucretli deger olusturabilir. | Q065/Q087 premium adaylari. | Core-vs-premium boundary guclendi; business viability, pricing ve WTP daha sonra validate edilmeli. | SUPPORTED |
| ASM-019 | Roadside/active-repair baglaminda daha kolay interaction ayni kritik safety standardini koruyarak kullanisli olabilir. | Q090/Q125 hizli ve hands-free ihtiyaclari. | Product safety invariants Q150-Q152 ve interruption re-validation Q181-Q183 ile desteklendi; actual usability/feasibility sonra test edilmeli. | SUPPORTED |
| ASM-020 | Provenance/review status gorunurlugu, resmi rehber/community/dis islem arasindaki trust farkini anlatabilir. | Q074/Q082. | Basit ayrim cozuldu; high-trust durumda label-only yeterli degil, explicit claim explanation gerekir. | RESOLVED |
| ASM-021 | Offline rehberin version/freshness gorunurlugu stale-content riskini tek basina yonetilebilir hale getirebilir. | Q091. | Q122 ve Q147-Q149 visibility'nin critical application icin yetersiz oldugunu gosterdi. | CHALLENGED |
| ASM-022 | Selective ownership transfer, yeni sahibin partial history'yi complete sanmasina yol acmadan uygulanabilir. | Q120 selective transfer istedi. | Product semantics Q135-Q137, Q162-Q165 ile guclendi; real comprehension/usability validation gerekir. | RESOLVED |
| ASM-023 | Kritik rehberlerde gereksiz bloklamadan stale riskini azaltacak anlamli bir `guncellik siniri` tanimlanabilir. | Q122 freshness gate istedi. | Claim/risk scope Q147-Q149 ile desteklendi; numeric/operational threshold ve real-world policy daha sonra belirlenmeli. | SUPPORTED |
| ASM-024 | Hesap/izinleri ilk degerden once zorunlu tutmadan farkli segmentlere acceptable first-use sunulabilir. | Q123 account-light value. | Q153-Q155 ve Q175-Q177 profile transition trust beklentilerini destekledi; broader validation acik. | SUPPORTED |
| ASM-025 | Voice/minimum-touch interaction usability'yi artirirken kritik safety confirmation korunabilir. | Q125 active-repair accessibility. | Q150-Q152 ve Q181-Q183 safety/re-entry boundaries'i destekliyor; technology/performance feasibility acik. | SUPPORTED |
| ASM-026 | Partial-history disclosure + covered period + visible gaps, new owner's incomplete history'yi complete sanma riskini yeterince azaltabilir. | Q135-Q136 product semantics bunu ongoruyor. | Q162-Q165 modelin nasil davranmasi gerektigini guclendirdi; gercek comprehension/usability validation gerekir. | SUPPORTED |
| ASM-027 | Reviewable explicit critical confirmations active repair safety'sini korurken kabul edilemez friction yaratmadan uygulanabilir. | Q151 critical confirmation istedi. | Q181-Q183 resume re-validation ihtiyacini destekliyor; gercek task usability/error-rate validation gerekir. | SUPPORTED |
| ASM-028 | Persistence/cross-device/collaboration ihtiyacinda profile istemek daha genis hedef user base icin dogal kabul edilir. | Q155 profile trigger'i tanimladi. | Q175-Q177 continuity beklentisini destekledi; hala tek-kullanici product evidence'i, broader segment validation gerekir. | SUPPORTED |
| ASM-029 | Contributor identity kaldirilirken de-identified safety review trace korunmasi withdrawal beklentisi ile safety-learning ihtiyacini birlikte karsilayabilir. | Q130. | Q166-Q168 downstream re-review ihtiyacini destekledi; privacy/legal/operational feasibility daha sonra degerlendirilmeli. | SUPPORTED |
| ASM-030 | Basic multi-bike + reasonable history free kalirken large media, advanced analysis ve extensive collaboration sustainable premium value yaratabilir. | Q144-Q146. | Q156-Q161 product boundary'yi guclendirdi; sustainability/WTP/business viability kaniti yoktur. | OPEN |
| ASM-031 | Attributed/disputed historical claims birden fazla ownership transfer boyunca kullanici tarafindan anlasilir kalabilir. | Q162-Q165 disputed/multi-transfer semantics istedi. | Gercek comprehension ve information-overload validation gerekir. | OPEN |
| ASM-032 | Risk-adaptive evidence explanation, dusuk riskte bilgi kalabaligini azaltirken high-risk trust clarity'yi koruyabilir. | Q172-Q174. | Beginner/experienced farklari ve real usability daha fazla validate edilmeli. | OPEN |
| ASM-033 | Local-to-profile transition'da scope preview + no-silent-loss + conflict review, duplicate/conflicting records'i kullanici guvenini bozmadan yonetebilir. | Q175-Q177. | Real migration usability ve failure/cancel edge case'leri discovery/validation gerektirir. | OPEN |
| ASM-034 | Photo/check-question tabanli physical-state remapping, materially changed guide veya interrupted repair'da yeterli sayida durumda safe resume state'i yeniden kurabilir. | Q178-Q183. | Gercek dunya feasibility/content/recognition reliability daha sonra test edilmeli. | OPEN |
| ASM-035 | Withdrawn evidence'den etkilenmis kullanicilari safety/technical impact'e gore belirlemek gereksiz alarm yaratmadan yeterli correction reach-back saglayabilir. | Q166-Q168. | Affected-user boundary ve notification over/under-reach discovery/validation gerektirir. | OPEN |

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
- ASM-005 SUPPORTED — Q126-Q128.
- ASM-016 SUPPORTED — Q126-Q127.
- ASM-017 RESOLVED refinement — Q132-Q134.
- ASM-018 SUPPORTED refinement — Q144-Q146.
- ASM-019 SUPPORTED — Q150-Q152.
- ASM-020 RESOLVED refinement — Q132-Q134.
- ASM-021 CHALLENGED — Q147-Q149.
- ASM-022 RESOLVED — Q135-Q137.
- ASM-023 SUPPORTED — Q147-Q149.
- ASM-024 SUPPORTED — Q153-Q155.
- ASM-025 SUPPORTED — Q150-Q152.
- ASM-026 — ASM-030 eklendi.

### Batch 06
- **ASM-026 SUPPORTED — Q162-Q165:** Partial/multi-transfer history coverage ve disputed correction semantics product-level olarak guclendi; comprehension validation hala acik.
- **ASM-027 SUPPORTED — Q181-Q183:** Critical resume re-validation explicit confirmation ihtiyacini guclendirdi; friction/performance validation acik.
- **ASM-028 SUPPORTED — Q175-Q177:** Local-to-profile continuity ve conflict review profile transition modelini destekledi; broader user validation acik.
- **ASM-029 SUPPORTED — Q166-Q168:** Withdrawal sonrasi downstream re-review safety-learning ihtiyacini guclendirdi; anonymization/legal feasibility acik.
- **ASM-030 OPEN refinement — Q156-Q161:** Free-core/premium product boundary guclendi fakat sustainable premium value/WTP kaniti olusmadi.
- ASM-031 — ASM-035 yeni OPEN varsayimlar olarak eklendi.

## QC Note — Batch 06 assumption-ID protection

Portable Batch 06 package kendi `ASM-026 — ASM-030` candidate anlamlarini onermisti; bu numaralar repository'de zaten farkli canonical assumption'lara aitti. Repository ID'leri sessizce yeniden kullanilmadi. Batch 06 kaniti mevcut canonical assumption anlamlarina baglandi ve yeni varsayimlar ASM-031'den devam ettirildi.
