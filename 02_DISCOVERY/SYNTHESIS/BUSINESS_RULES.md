# BUSINESS RULES

Status: DRAFT

Bu kurallar kullanici kanitindan turetilen teknik olmayan urun davranis kurallaridir. Kesin technical implementation degildir.

| ID | Rule | Applies To | Exceptions / Notes | Source | Status |
|---|---|---|---|---|---|
| BR-001 | Motosiklete ozel rehber, gercek motosiklet konfigurasyonuyla yeterli eslesme kurulmadan motosiklete ozelmis gibi sunulamaz. | Rehber secimi | Sabit evrensel kimlik seti yok | Q008-Q009, Q026, Q036-Q039 | CONFIRMED |
| BR-002 | Yil/versiyon/donanim islemi degistiriyorsa farkli adimlar ayri rehber dallari olarak ele alinmalidir. | Rehber varyantlari | — | Q009, Q037 | CONFIRMED |
| BR-003 | Eslesme belirsizse yakin yil/varyant adimlari dogruymus gibi kullanilarak ilerlenemez. | Rehber guvenligi | — | Q009, Q026, Q037 | CONFIRMED |
| BR-004 | Dogrulanmis teknik bilgi motosiklet/varyanta uygun guvenilir kaynaga dayanmalidir. | Teknik icerik | Internet tekrar sayisi tek basina dogrulama degil | Q010, Q041 | CONFIRMED |
| BR-005 | Kullanici kaynak surumu ve ilgili sayfa/bolum kanitini gorebilmelidir. | Provenance | Gosterim tasarimi sonraki asama | Q010 | CONFIRMED |
| BR-006 | Cozulmemis kritik kaynak celiskisinde tek deger secilip application progression yaptirilamaz. | Kaynak celiskisi | Celismeyen preparation/safety bilgisi kalabilir | Q011, Q044 | CONFIRMED |
| BR-007 | Deneyim seviyesi rehber ayrinti/hizini degistirebilir fakat safety ve kritik dogrulamayi kaldiramaz. | Rehber sunumu | — | Q007, Q014 | CONFIRMED |
| BR-008 | Yeni/az deneyimli kullanici icin temel adim atlanan ara hareket birakmadan uygulanabilir ayrintida olmalidir. | Rehber adimlari | — | Q014 | CONFIRMED |
| BR-009 | Zorunlu arac/parca/ekipman eksigi motosiklet yari sokulmeden once gorunur olmalidir. | Readiness | — | Q016-Q017 | CONFIRMED |
| BR-010 | Zorunlu ozel arac/parca yoksa ilgili application adimina gecilmez. | Readiness | Verified safe equivalent bazi yardimci araclarda olabilir | Q017, Q053 | CONFIRMED |
| BR-011 | Kritik safety riski islem basinda ve ilgili adimdan hemen once gosterilmelidir. | Safety | — | Q018 | CONFIRMED |
| BR-012 | Safety uyarisi risk, onleme ve stop kosulunu somut aciklamalidir. | Safety | — | Q018 | CONFIRMED |
| BR-013 | Varyant uyusmazligi, hasar, gerekli olcum/arac eksigi, beklenmeyen baglanti veya kritik sonucun dogrulanamamasi stop nedenidir. | Stop-gate | — | Q019, Q034, Q045-Q050 | CONFIRMED |
| BR-014 | High-consequence alanlarda belirsizlikle ilerleme onerilmemeli; kategoriye ozel on kosul/stop-gate uygulanmalidir. | High-consequence | — | Q019, Q046-Q050 | CONFIRMED |
| BR-015 | Olasi ariza nedeni kesin teshis gibi sunulamaz. | Diagnosis | — | Q023-Q024 | CONFIRMED |
| BR-016 | Teshis olasiligi kanitla ilerlemeli ve yeni kanita gore daralmalidir. | Diagnosis | Sabit nicel test sayisi yok | Q022-Q024, Q056-Q058 | CONFIRMED |
| BR-017 | Kanit olmadan parca degisimi veya guvenli kullanim onerilmemelidir. | Diagnosis/safety | — | Q024, Q057-Q058 | CONFIRMED |
| BR-018 | Rehber gercek motosiklet/modifikasyonla uyusmuyorsa normal ilerleme durup uygunluk yeniden kurulmalidir. | Mismatch recovery | — | Q026, Q038-Q039 | CONFIRMED |
| BR-019 | Hata/beklenmeyen davranista normal ilerleme durmali; guvenliyse emniyete alma/dokunmama bilgisi sunulmalidir. | Recovery | — | Q027 | CONFIRMED |
| BR-020 | Yarim islem; adim, sokulu parca, olcum, fotograf/not ve rehber surumu baglamini korumalidir. | Interrupted work | — | Q028, Q059 | CONFIRMED |
| BR-021 | Degismis rehber devam eden isleme sessizce uygulanamaz. | Versioning | Kritik duzeltmede eski akis durur | Q028, Q059 | CONFIRMED |
| BR-022 | Yarim veya sonucu dogrulanamayan islem tamamlandi olarak isaretlenemez. | Completion | — | Q029 | CONFIRMED |
| BR-023 | Disarida yaptirilan islem kaydedilebilir; erteleme completion degildir. | History | Kanitsiz dis islem verified gibi sunulmaz | Q033, Q063 | CONFIRMED |
| BR-024 | Sonraki bakım hesabi dogrulanmis completion kaydindan devam etmelidir. | Maintenance | — | Q033, Q063 | CONFIRMED |
| BR-025 | Bakimda motosiklete uygun uretici km/sure araliklari temel alinmali ve once dolan izlenmelidir. | Maintenance | Dogrulanmis istisnalar olabilir | Q031, Q061 | CONFIRMED |
| BR-026 | Dogrulanmamis bakım araligi uretilmemelidir. | Maintenance | — | Q031, Q061 | CONFIRMED |
| BR-027 | Reminder ertelemesi saklanabilir fakat islemi yapilmis sayamaz. | Reminders | — | Q033 | CONFIRMED |
| BR-028 | Urun technical value uyduramaz, belirsiz arizayi definitive diagnosis sunamaz veya dangerous-work success guarantee veremez. | Tum urun | — | Q035 | CONFIRMED |
| BR-029 | Modifiye sistemde fabrika rehberi otomatik uygun sayilamaz. | Rehber eslesmesi | — | Q038-Q039 | CONFIRMED |
| BR-030 | Islem/malzeme/safety kontrolunu degistiren version farki kesinlesmeden rehber baslamamalidir. | Rehber gating | — | Q036-Q037 | CONFIRMED |
| BR-031 | Insan incelemesi ilgili sistemde uygulamali deneyim ve fit/source/visual/tool/risk/final-check degerlendirmesini icermelidir. | Governance | Sertifika/unvan varsayilmaz | Q040 | CONFIRMED |
| BR-032 | Bagimsiz ikinci inceleme kritik rehberde ek guven sinyalidir; evrensel zorunluluk degildir. | Governance | — | Q040 | CONFIRMED |
| BR-033 | Kritik source update'i rehber yeniden incelenene kadar ilgili adimlari askiya almayi gerektirebilir. | Content lifecycle | — | Q042 | CONFIRMED |
| BR-034 | Kritik rehber hatasinda rehber durdurulmali, etkilenenler gerekli kontrol/yardim yoluyla uyarilmali, history silinmemelidir. | Recall | — | Q043 | CONFIRMED |
| BR-035 | Yeni rehber surumu degisiklik gerekcesiyle yayimlanmali; eski surum tarihsel kayitlarda korunmalidir. | Versioning | — | Q042, Q059-Q060 | CONFIRMED |
| BR-036 | Readiness yalniz `deneyimliyim` beyanina dayanamaz. | Readiness | — | Q051 | CONFIRMED |
| BR-037 | Guvenle ogrenilebilir beceri eksigi hazirliga yonlendirilebilir; serious/uzman-dogrulamali kritik adim acilmaz. | Readiness/learning | — | Q052 | CONFIRMED |
| BR-038 | Safe equivalent olcu/fit/dayanim/material/function/safety requirements dogrulanmadan onerilemez. | Tools/materials | — | Q053, Q055 | CONFIRMED |
| BR-039 | Tam varyant fotografi yoksa verified drawing/schema kullanilabilir; baska motosiklet gorseli ayniymis gibi sunulamaz. | Visual guidance | Belirsizlikte adim baslamaz | Q054 | CONFIRMED |
| BR-040 | `En olasi` neden icin birden fazla ayirt edici kanit ve alternatives evaluation gerekir. | Diagnosis | Sabit sayisal esik degil | Q056 | CONFIRMED |
| BR-041 | Esit diagnosis possibilities ayri tutulmali; random part replacement onerilmemelidir. | Diagnosis | — | Q057 | CONFIRMED |
| BR-042 | Makul kontroller sonunda neden dogrulanamazsa `Neden dogrulanamadi` sonucu kabul edilebilir. | Diagnosis/escalation | — | Q058 | CONFIRMED |
| BR-043 | Historical work guide update/recall nedeniyle sessizce yeniden yazilamaz; used version korunur. | History/versioning | — | Q060 | CONFIRMED |
| BR-044 | Usage condition bakım araligini sadece motorcycle-specific verified source destekliyorsa degistirebilir; reason visible olmalidir. | Maintenance exceptions | — | Q061 | CONFIRMED |
| BR-045 | Multi-bike history/guide/reminder contexts ayrilmalidir; active motorcycle clear olmalidir. | Multi-motorcycle | — | Q062 | CONFIRMED |
| BR-046 | External work provenance ile saklanmali; kanit yoksa verified gibi gosterilmemelidir. | History trust | Fatura tek basina automatic verified degil | Q063 | CONFIRMED |
| BR-047 | Multiple overdue maintenance safety/use impact, sonra delay ve verified conditions ile prioritize edilmeli; reason shown olmalidir. | Maintenance priority | — | Q064 | CONFIRMED |
| BR-048 | Kritik safety bilgisi paywall arkasina saklanmamalidir. | Monetization trust | — | Q065 | CONFIRMED |
| BR-049 | Core verified guide, maintenance record ve basic reminder ucretsiz core'dur. | Monetization | — | Q065 | CONFIRMED |
| BR-050 | Kullanici technical ID/code aramaya zorlanmadan observable features/photos ile variant distinction denenmelidir. | Variant identification | Feasibility garantisi degil | Q066-Q067 | CONFIRMED |
| BR-051 | Observable evidence ile variant kesinlesmezse missing distinction shown olmali ve variant-specific application acilmamalidir. | Variant gate | — | Q066-Q067 | CONFIRMED |
| BR-052 | High-voltage application acilmadan risks, prerequisite knowledge/equipment/checks ve motorcycle-specific safety verify edilmelidir. | High voltage | Kategori otomatik dislanmaz | Q068 | CONFIRMED |
| BR-053 | Pressurized/high-temperature/benzeri high-consequence systems'de unverified safety condition atlanarak ilerlenemez. | High-consequence | — | Q069 | CONFIRMED |
| BR-054 | Routine/non-urgent reminders gruplanabilir ve daily spam yerine seyrek summary olabilir. | Notifications | Q070 mevcut user preference | Q070-Q071 | CONFIRMED |
| BR-055 | Riding-safety critical alert diger reminders arasinda kaybolmamalidir. | Notifications | — | Q071 | CONFIRMED |
| BR-056 | Routine notifications kapatilabilir/ertelenebilir; critical safety app icinde ve relevant task oncesi visible kalmalidir. | Notifications | — | Q072 | CONFIRMED |
| BR-057 | History correction old/new value, time ve reason'i korumalidir. | History audit | — | Q073 | CONFIRMED |
| BR-058 | History correction maintenance plan'i degistiriyorsa effect user'a aciklanmalidir. | Maintenance/history | — | Q073 | CONFIRMED |
| BR-059 | User assertion, documented work ve reviewed record ayni evidence level gibi sunulamaz. | Evidence | — | Q074 | CONFIRMED |
| BR-060 | Modified part reliable interval bilinmiyorsa old interval automatic kullanilamaz veya new interval uydurulamaz. | Maintenance uncertainty | — | Q075 | CONFIRMED |
| BR-061 | Verified maintenance exception general plan ile birlikte ve neden gecerli olduguyla gosterilmelidir. | Maintenance exceptions | — | Q076 | CONFIRMED |
| BR-062 | Usage condition bilinmiyorsa missing info gizlenmemeli; valid standard plan varsa gosterilip missing info sorulmalidir. | Maintenance uncertainty | — | Q077 | CONFIRMED |
| BR-063 | Duration exact finish promise yerine experience-dependent range olarak sunulmali; uncertainty visible olmalidir. | Estimate | — | Q078 | CONFIRMED |
| BR-064 | Cost estimate parts/consumables/tools/labor ayirmali; exclusions, price date ve assumptions gorunur olmalidir. | Estimate | — | Q079 | CONFIRMED |
| BR-065 | Personal notes/photos default-private; community sharing explicit choice olmali ve personal info ayiklanmalidir. | Community/privacy | — | Q080 | CONFIRMED |
| BR-066 | Community correction official guide'a direct giremez; source, motorcycle fit ve safety effect review edilmelidir. | Governance | — | Q081 | CONFIRMED |
| BR-067 | Community content source, motorcycle, review status ve date ile official guide'dan ayrilmalidir. | Community provenance | — | Q082 | CONFIRMED |
| BR-068 | Dangerous community content hidden/reviewed olmali; official guide'i etkilerse ilgili adim durdurulup affected users uyarilmalidir. | Moderation/safety | Sayisal SLA degil | Q083 | CONFIRMED |
| BR-069 | Community Q&A/experience official numbered guide steps'e karismamalidir. | Content separation | — | Q084 | CONFIRMED |
| BR-070 | Service/mechanic listing core self-service guide'in yerini almamali; paid ranking technical decision'i etkilememelidir. | Commercial support | — | Q085 | CONFIRMED |
| BR-071 | Purchase options oncesi technical fit criteria gosterilmeli; sponsored offer marked olmali ve payment technical fit'i degistirmemelidir. | Commerce neutrality | — | Q086 | CONFIRMED |
| BR-072 | Motorcycle-specific detailed guide, safety ve basic maintenance tracking free-core expectation'dir. | Monetization | — | Q087 | CONFIRMED |
| BR-073 | Hidden ads, paid product'u technical `best` gostermek, alternatives saklamak veya sales-target guide manipulation trust modeline aykiridir. | Commercial neutrality | — | Q088 | CONFIRMED |
| BR-074 | Roadside experience short/fast olabilir fakat safe-to-ride uncertainty ve critical safety gizlenemez. | Roadside | — | Q090 | CONFIRMED |
| BR-075 | Downloaded guide/visual/safety/progress/history offline accessible kalmali; version/freshness visible olmalidir. | Offline | Application authorization ayri gate olabilir | Q091 | CONFIRMED |
| BR-076 | User kendi motorcycle/record/note/photo data'sini goruntuleme, duzeltme, ekleme ve silme control'una sahip olmalidir. | Data ownership | — | Q092 | CONFIRMED |
| BR-077 | Bir hesabin verisi baska hesapta gorunmemelidir. | Data isolation expectation | Technical implementation karari degil | Q092, Q095 | CONFIRMED |
| BR-078 | User'in own data export'u premium'a baglanmamalidir. | Data portability | Format secilmedi | Q093 | CONFIRMED |
| BR-079 | Delete oncesi scope/irreversibility aciklanmali; delete sonrasinda removed/pending state anlasilir olmalidir. | Data deletion | Retention/sure secilmedi | Q094 | CONFIRMED |
| BR-080 | Fabricated info, hidden risk, cross-account data mix, silent history loss veya ad-influenced guide trust-breaker'dir. | Tum urun | — | Q095 | CONFIRMED |
| BR-081 | Readiness stop'ta missing condition, reason, remediation ve re-check yolu aciklanmalidir. | Readiness UX | — | Q096-Q098 | CONFIRMED |
| BR-082 | User new photo/measurement/alternative check ile re-validation isteyebilmelidir; self-assertion gate'i gecemez. | Readiness re-validation | — | Q096 | CONFIRMED |
| BR-083 | Variant, critical info, equipment, safe environment veya mandatory pre-check eksigi self-declared override ile gecilemez. | Safety gates | — | Q097 | CONFIRMED |
| BR-084 | Teaching content accessible kalabilir; first physical intervention oncesi mandatory conditions verify edilmeli ve new risk/mismatch'te application durmalidir. | Teaching/application | — | Q099 | CONFIRMED |
| BR-085 | Professional escalation kullaniciyi permanent incapable ilan eden dille degil, unverified condition ve retry path ile aciklanmalidir. | Escalation | — | Q100 | CONFIRMED |
| BR-086 | Professional path secilse bile symptom capture, photo, preparation, learning ve result-check support devam etmelidir. | Escalation/support | — | Q101 | CONFIRMED |
| BR-087 | Common aftermarket verified fit varsa guide'a dahil edilebilir; factory/modified differences ayrilmalidir. | Modification coverage | Feasibility garantisi degil | Q102 | CONFIRMED |
| BR-088 | Custom modification'da verified guide yoksa evidence gap aciklanabilir ve teaching-only info kalabilir; risky application kapanir. | Modification fallback | — | Q103-Q104 | CONFIRMED |
| BR-089 | Moderation removal reason somut/saygili olmali; rule/problem shown, correction/re-submit/appeal yolu bulunmalidir. | Community moderation | — | Q105 | CONFIRMED |
| BR-090 | Repeated wrong contribution pre-review'a; intentional/repeated dangerous contribution sharing restriction'a gidebilir. | Community enforcement | Final ban policy degil | Q106, Q108 | CONFIRMED |
| BR-091 | Useful but unverifiable experience `unverified personal experience` olarak context ile sunulabilir; official step olamaz. | Community trust | Risky suggestion review bitmeden publish olmaz | Q107 | CONFIRMED |
| BR-092 | Intentional dangerous contribution hizla hidden olmali, event recorded ve gerekiyorsa exposed users alerted olmalidir. | Moderation/safety | Sayisal SLA degil | Q108 | CONFIRMED |
| BR-093 | Evidence labels user assertion -> documented -> reviewed -> verified distinctions'i anlatmalidir. | Evidence language | Claim semantics context-specific olabilir | Q109 | CONFIRMED |
| BR-094 | `Verified` mutlak garanti degildir; source/applicability/review context gorunur olmalidir. | Evidence language | — | Q110 | CONFIRMED |
| BR-095 | Long-ignored critical topic routine reminders arasinda kaybolmamali; app icinde safety summary ve direct action yolu bulunmalidir. | Critical reminders | — | Q111 | CONFIRMED |
| BR-096 | Multiple critical topics harm/urgency ile siralanmali; why-first, age, next-check gorunmelidir. | Critical priority | — | Q112 | CONFIRMED |
| BR-097 | Long absence'ta notification flood yerine critical safety -> overdue maintenance -> records catch-up summary sunulmalidir. | Re-engagement | — | Q113 | CONFIRMED |
| BR-098 | Safe completion icin required core info ve user's own data portability premium'a baglanmamalidir. | Monetization boundary | — | Q114-Q115 | CONFIRMED |
| BR-099 | Ongoing service cost yaratmayan optional value one-time payment'a uygun olabilir. | Monetization preference | Final package/pricing degil | Q115 | CONFIRMED |
| BR-100 | Core target individual self-service owner'dir; multi-bike/shared/hobby-helper/record-only adjacent contexts olabilir. | User scope | — | Q116-Q117 | CONFIRMED |
| BR-101 | Shared motorcycle owner access + contributor attribution + time/edit trail + revocable permission + private-note isolation gerektirir. | Collaboration | Technical permission model secilmedi | Q118-Q119 | CONFIRMED |
| BR-102 | Ownership transfer selected vehicle-history records aktarabilir; private notes/sensitive photos default-private ve preview'lu olmalidir. | Ownership transfer | Partial completeness ek rules ile rafine | Q120 | CONFIRMED |
| BR-103 | Archive active garage'dan cikarir fakat history'yi korur ve reactivation'a izin verir; delete degildir. | Lifecycle | — | Q121 | CONFIRMED |
| BR-104 | Critical offline guide last-verification gostermeli; freshness limit asildiginda application online re-check'e kadar kapanabilmelidir. | Offline safety | Numeric threshold yok | Q122 | CONFIRMED |
| BR-105 | First-use'ta product value account/notification/long-profile zorunlulugundan once gorulebilmelidir. | Onboarding | Auth karari degil | Q123 | CONFIRMED |
| BR-106 | Turkiye icin clear Turkish, familiar units ve experience-appropriate terminology beklenir. | Localization | Global expansion karari degil | Q124 | CONFIRMED |
| BR-107 | Large readable controls, contrast, non-color warning, image description, captions, voice/easy-touch accessibility needs'dir. | Accessibility | Implementation secilmedi | Q125 | CONFIRMED |
| BR-108 | Blocked readiness'ta professional help'ten once assessment error check + learning/preparation/equipment/self-remediation + re-validation yolu sunulmalidir. | Readiness/escalation | External support tek cikis degil | Q126 | CONFIRMED |
| BR-109 | Safety stop sonrasi same self-service guide'a donus ancak missing condition saglanip equipment, motorcycle fit ve critical checks yeniden verified olursa mumkundur. | Re-entry validation | User assertion yeterli degil | Q127 | CONFIRMED |
| BR-110 | Professional recommendation optional support'tur; unverified critical condition nedeniyle application closure mandatory safety gate'tir. | Escalation semantics | Long duration option olabilir; uncertain technical value gate'tir | Q128 | CONFIRMED |
| BR-111 | Actual motorcycle deletion oncesi linked history/photo/measurement/reminder scope gosterilmeli; confirmed delete user's own copy linked data'sini kaldirmali, independent transferred records'i otomatik silmemelidir. | Data lifecycle | Legal/backup implementation karari degil | Q129 | CONFIRMED |
| BR-112 | Community contribution withdrawal public content/personal info'yu kaldirmali; de-identified safety review trace korunabilir ve withdrawn correction affected guide re-review gerektirebilir. | Community lifecycle | Legal anonymization karari degil | Q130 | CONFIRMED |
| BR-113 | Data export content yaninda source/provenance, evidence level, important corrections ve dates'i standard olarak tasimalidir. | Data portability | Technical format secilmedi | Q131 | CONFIRMED |
| BR-114 | Evidence vocabulary'nin basic logic'i tutarli kalmali fakat `hangi claim review/verify edildi` context'e gore aciklanmalidir. | Evidence semantics | Tek global claim anlami yok | Q132 | CONFIRMED |
| BR-115 | Verified maintenance record islemin yapildigina evidence oldugunu soyler, perfect workmanship guarantee etmez; verified technical guide source + motorcycle fit + application-step suitability claim'ini tasir. | Evidence semantics | — | Q133 | CONFIRMED |
| BR-116 | Safety value, technical value, ownership transfer ve disputed record gibi high-trust baglamlarda label yaninda verified/unverified claim acik cümleyle anlatilmalidir. | Trust communication | Detail depth sonraki discovery'de rafine | Q134 | CONFIRMED |
| BR-117 | Selective transfer explicitly incomplete/owner-selected history olarak isaretlenmeli; covered period ve visible gaps shown olmali, gaps completed maintenance gibi yorumlanmamalidir. | Ownership transfer | Private untransferred content acilmaz | Q135-Q136 | CONFIRMED |
| BR-118 | Transfer sonrasi historical record silent overwrite edilemez; former owner correction proposal attribution/time ile sunulabilir ve prior version/evidence trail korunmalidir. | Ownership history | Current owner review/accept expectation'i var | Q137 | CONFIRMED |
| BR-119 | Initial direct target owner'dir; professional/service owner-invited contributor olabilir ve professional-oriented complexity owner first-use'u domine etmemelidir. | User scope | Ayrı work-management product ileride olabilir | Q138-Q139 | CONFIRMED |
| BR-120 | Hobby help ile paid service ayni record type gibi gorunmemeli; her ikisinde actor/evidence, paid service'te ek service/document info bulunmali; role automatic verified status yaratmaz. | External work trust | — | Q140 | CONFIRMED |
| BR-121 | First product priority beginner+experienced self-service owner'dir; basic record tracking de calismali, advanced shared/work-management later deepen edilebilir. | Product priority | Market-size karari degil | Q141-Q143 | CONFIRMED |
| BR-122 | Required safety visual, completion step, reasonable history veya data export'u premium yapmak indirect paywall sayilir; free user basic task'i bastan sona tamamlayabilmelidir. | Monetization boundary | — | Q145 | CONFIRMED |
| BR-123 | Basic multi-bike separation ve reasonable history core; large media archive, advanced comparative analysis ve extensive collaboration premium candidate olabilir. | Monetization boundary | Numeric quotas/prices yok | Q146 | CONFIRMED |
| BR-124 | Freshness gate ozellikle safety notice, technical value ve changeable procedure order gibi application-critical claims icin anlamlidir; old conceptual teaching tek basina stop reason degildir. | Freshness semantics | Source/last-check yine gorunmeli | Q147 | CONFIRMED |
| BR-125 | Stale critical content teaching/reference olarak kalabilir fakat current application instruction gibi gorunmemeli; application reason ile kapanmali ve current-version check sunulmalidir. | Offline/freshness | Numeric TTL yok | Q148-Q149 | CONFIRMED |
| BR-126 | Active-repair accessibility safety warning, motorcycle fit, technical value, stop condition ve post-operation check'i convenience ugruna atlayamaz. | Accessibility/safety | Alternate modality allowed | Q150, Q152 | CONFIRMED |
| BR-127 | Energy isolation, motorcycle stability, critical connection check ve operation completion gibi decisions misheard voice input'a birakilamaz; explicit/reviewable confirmation gerekir. | Critical confirmation | UI implementation secilmedi | Q151 | CONFIRMED |
| BR-128 | Record-only first-use user rehber aramaya zorlanmadan motorcycle ekleyip latest work record ederek upcoming maintenance value'yu erken gorebilmelidir. | First-use | — | Q153 | CONFIRMED |
| BR-129 | Shared/multi-bike first-use'ta motorcycle separation ve actor attribution erken anlasilmali; persistent shared record/cross-device continuity oncesi ownership kurulmalidir. | First-use/collaboration | `card` specific UI karari degil | Q154 | CONFIRMED |
| BR-130 | First real record'u kalici saklama, cross-device continue veya collaborator invite etme profile gecis icin natural trigger olabilir; profile reason ve existing local data fate onceden aciklanmalidir. | First-use/profile | Technical auth/sync karari degil | Q155 | CONFIRMED |

## Rules needing more discovery

- Basic history vs expanded premium storage value boundary.
- Basic multi-bike vs advanced garage value boundary.
- Transfer correction disagreement ve multiple ownership transfers.
- Withdrawn community evidence'in downstream official-guide/claim etkisi.
- Shared/collaborative deletion ownership edge cases.
- Evidence explanation depth by risk ve information-overload siniri.
- Profile transition sirasinda local-data continuity trust.
- Mid-repair materially changed guide after freshness re-check.
- Active-repair interruption/re-entry confirmations.
- Paid-service evidence ile owner observation dispute semantics.
