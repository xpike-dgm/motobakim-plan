# FEATURE CANDIDATES

Status: DRAFT

Discovery sirasinda ortaya cikan kullanici degeri odakli ozellik adaylari. Bunlar henuz kesin kapsam, technical task veya architecture karari degildir.

| ID | Candidate | User Value | Evidence | Status |
|---|---|---|---|---|
| FC-001 | Motosiklet/varyant tanimlama ve rehber eslesme kontrolu | Yanlis varyant adimlarini engellemek | Q008-Q009, Q026, Q036-Q039 | CANDIDATE |
| FC-002 | Rehber varyant dallari | Yil/versiyon/donanim farklarini dogru adimlarla ele almak | Q009, Q037 | CANDIDATE |
| FC-003 | Kaynak/provenance goruntuleme | Teknik bilginin belge/surum/bolum dayanagini gormek | Q010-Q011, Q041-Q044 | CANDIDATE |
| FC-004 | Kaynak celiskisi gorunumu ve critical hold | Cozulmeyen kritik farkta sahte kesinlikten kacinmak | Q011, Q044 | CANDIDATE |
| FC-005 | Gunluk dille belirti arama + bolge/gorsel bulma | Islem/parca adini bilmeden dogru yolculuga girmek | Q012 | CANDIDATE |
| FC-006 | Islem karar onizlemesi | Baslamadan uygunluk/risk/sure/maliyet/arac-parca bilgisini gormek | Q013 | CANDIDATE |
| FC-007 | Deneyim seviyesine gore rehber gorunumu | Yeni kullaniciya ayrintili, deneyimliye hizli deneyim | Q007, Q014 | CANDIDATE |
| FC-008 | Tek hareket + gorsel + basari kontrolu adim modeli | Her adimda eylem ve dogru sonucu anlamak | Q014-Q015 | CANDIDATE |
| FC-009 | Readiness kontrol listeleri | Eksikleri ise baslamadan fark etmek | Q016-Q017 | CANDIDATE |
| FC-010 | Risk ve stop-gate sistemi | Kritik kosullarda application progression'i durdurmak | Q018-Q021, Q034, Q045-Q053 | CANDIDATE |
| FC-011 | Kanit-temelli teshis akisi | Kesinlik taklidi yapmadan olasiliklari daraltmak | Q022-Q024, Q056-Q058 | CANDIDATE |
| FC-012 | Adim ici yardim katmani | Takilinan adimda detayli yardim almak | Q025 | CANDIDATE |
| FC-013 | Mismatch/modification akisi | Uygun olmayan rehberle devam etmemek | Q026, Q038-Q039 | CANDIDATE |
| FC-014 | Recovery / guvenli geri donus | Hata durumunda motosikleti emniyete alip yardim yoluna gecmek | Q027 | CANDIDATE |
| FC-015 | Devam eden islem oturumu | Yarim isin tum fiziksel/olcum/not baglamini korumak | Q028, Q059 | CANDIDATE |
| FC-016 | Zengin bakım/islem gecmisi | Aylar sonra ne/neden/nasil yapildigini kanitlarla gormek | Q029-Q030 | CANDIDATE |
| FC-017 | Completion + provenance durumlari | Yarim/dogrulanamadi/ertelendi/disarida yapildi ayrimini korumak | Q029, Q033, Q063 | CANDIDATE |
| FC-018 | Uretici tabanli sonraki bakım takibi | Dogrulanmis km/sure ve completion kaydiyla planlamak | Q031, Q033, Q061 | CANDIDATE |
| FC-019 | Aciklanabilir ve ayarlanabilir reminders | Neden bildirim geldigini bilmek ve rutini kontrol etmek | Q032-Q033, Q064 | CANDIDATE |
| FC-020 | Gecmis rehber surumu iliskisi | Hangi surumle islem yapildigini korumak | Q028-Q030, Q059-Q060 | CANDIDATE |
| FC-021 | Kullanici-dostu varyant ayristirma | Teknik kod ezberi olmadan observable ozellik/gorselle eslesmek | Q036-Q039 | CANDIDATE |
| FC-022 | Modifikasyon uygunluk kontrolu | Fabrika rehberini modifiye sisteme yanlis uygulamamak | Q038-Q039 | CANDIDATE |
| FC-023 | Icerik review/re-review/recall yasam dongusu | Guncelleme/hata/celiski durumunda guvenli content davranisi | Q040-Q044 | CANDIDATE |
| FC-024 | Reviewer guven/provenance gostergeleri | Insan incelemesi hakkinda guven sinyali gormek | Q040 | CANDIDATE |
| FC-025 | Kategoriye ozel high-consequence readiness | Kritik sistemlerde ozel on kosul/stop-gate | Q046-Q050 | CANDIDATE |
| FC-026 | Islem-bazli beceri/readiness degerlendirmesi | Oz-beyan yerine goreve ozel hazirligi anlamak | Q051-Q052 | CANDIDATE |
| FC-027 | Ogrenme/hazirlik fallback | Eksik beceriyi kritik application yerine guvenli hazirlikla tamamlamak | Q050-Q052 | CANDIDATE |
| FC-028 | Dogrulanmis gorsel fallback | Tam fotograf yoksa dogrulanmis sema/cizimle ilerlemek | Q054 | CANDIDATE |
| FC-029 | Guvenli esdeger kontrolu | Alternatif arac/malzemenin gercekten uygun oldugunu anlamak | Q053-Q055 | CANDIDATE |
| FC-030 | `Neden dogrulanamadi` + uzman handoff ozeti | Sonucsuz teshisi faydali kanit ozetiyle bitirmek | Q056-Q058 | CANDIDATE |
| FC-031 | Rehber surumu fark karsilastirmasi | Yarim iste kritik yeni degisikligi devamdan once gormek | Q059 | CANDIDATE |
| FC-032 | Rehber geri cekme / yeniden kontrol uyarisi | Gecmis islemde sonradan bulunan hatayi guvenle yonetmek | Q043, Q060 | CANDIDATE |
| FC-033 | Dogrulanmis bakım istisnalari | Yalniz kaynak destekliyorsa kosula gore plan degistirmek | Q061 | CANDIDATE |
| FC-034 | Coklu motosiklet yonetimi | Motor baglamlarini karistirmadan yonetmek | Q062 | CANDIDATE |
| FC-035 | Dis servis/islem kaydi ve guven seviyesi | Dis isi provenance/evidence ile kaydetmek | Q063 | CANDIDATE |
| FC-036 | Gecikmis bakım onceliklendirme | Coklu gecikmis isi safety etkisiyle gerekceli siralamak | Q064 | CANDIDATE |
| FC-037 | Ucretsiz core + premium zenginlestirme siniri | Core guveni korurken ek kolayliklari ucretli deger yapmak | Q065 | CANDIDATE |
| FC-038 | Fotograf/observable evidence tabanli variant finder + unresolved hold | Belge/kod aramadan versiyonu bulmaya calismak; bulunamazsa yanlis adimi acmamak | Q066-Q067 | CANDIDATE |
| FC-039 | Yuksek gerilim / high-consequence learning gate | Risk, ekipman ve kritik kontrolleri ogretip safety dogrulanmadan uygulamaya gecmemek | Q068-Q069 | CANDIDATE |
| FC-040 | Notification grouping + severity separation | Rutinleri ozetlemek, acil safety uyarilarini kaybetmemek | Q070-Q072 | CANDIDATE |
| FC-041 | History edit trail | Yanlis kaydi duzeltirken eski/yeni deger, zaman ve nedeni korumak | Q073 | CANDIDATE |
| FC-042 | Evidence-level labels | Kullanici beyani, belgeli ve incelenmis kayitlari guven seviyeleriyle ayirmak | Q074, Q082 | CANDIDATE |
| FC-043 | Belirsiz bakım takvimi | Modifiye/eksik veride uydurma aralik yerine uncertainty gostermek | Q075-Q077 | CANDIDATE |
| FC-044 | Transparent time/cost estimates | Sureyi aralikla, maliyeti kalem/tarih/varsayimla aciklamak | Q078-Q079 | CANDIDATE |
| FC-045 | Private notes -> explicit community contribution | Kisisel icerigi ozel tutup bilincli secimle topluluga katkida bulunmak | Q080 | CANDIDATE |
| FC-046 | Community contribution review/moderation | Duzeltme/ipuclarini resmi rehberden ayirip incelemek | Q081-Q084 | CANDIDATE |
| FC-047 | Community provenance indicators | Kaynak, motosiklet, review status ve tarihi gormek | Q082 | CANDIDATE |
| FC-048 | Dangerous community content response | Tehlikeli icerigi kaldirip resmi rehber etkisini ve kullanici uyarisini yonetmek | Q083 | CANDIDATE |
| FC-049 | Commercial-neutral service/parts support | Servis veya satin alma yardimini teknik uygunluk kararindan ayri tutmak | Q085-Q088 | CANDIDATE |
| FC-050 | Premium convenience candidates | Gelismis analiz, ek depolama ve benzeri core-disinda ucretli degerleri test etmek | Q087 | CANDIDATE |
| FC-051 | Roadside quick guidance context | Garaj disinda hizli tarama, safety-first ve kisa gorsel adim sunmak | Q090 | CANDIDATE |
| FC-052 | Offline downloaded work context | Rehber/gorsel/safety/progress/history baglamini offline korumak | Q091 | CANDIDATE |
| FC-053 | User data controls | Kendi motosiklet/kayit/not/fotografini goruntuleme, duzeltme ve silme | Q092-Q094 | CANDIDATE |
| FC-054 | Free data portability | Kendi verisini yeniden kullanilabilir export etmek | Q093 | CANDIDATE |
| FC-055 | Transparent deletion state | Silme kapsam/geri alinmazlik ve silinen/bekleyen durumunu aciklamak | Q094 | CANDIDATE |
| FC-056 | Readiness re-validation | Bloklanan readiness'i yeni evidence ile yeniden degerlendirmek | Q096-Q098 | CANDIDATE |
| FC-057 | Block reason + remediation + resume | Eksik kosul/neden/remediation/re-check ve kaldigi yere donusu gostermek | Q097-Q098 | CANDIDATE |
| FC-058 | Teaching-only content layer | Application gate kapali olsa bile guvenilir education/preparation content'i erisilebilir tutmak | Q099-Q104 | CANDIDATE |
| FC-059 | Professional escalation support | Eksik kosula dayali professional option + preparation/result-check sunmak | Q100-Q101 | CANDIDATE |
| FC-060 | Aftermarket adapted guide coverage | Common modification verified ise factory'den farkli adapted guide sunmak | Q102 | CANDIDATE |
| FC-061 | Custom modification evidence-gap fallback | Unique/custom durumda evidence gap + teaching-only + application hold sunmak | Q103-Q104 | CANDIDATE |
| FC-062 | Community appeal / re-submit workflow | Moderation gerekcesi, duzeltme veya appeal yolu | Q105 | CANDIDATE |
| FC-063 | Graduated contributor trust controls | Repeated wrong -> pre-review; intentional danger -> contribution restriction | Q106, Q108 | CANDIDATE |
| FC-064 | Unverified personal-experience status | Faydalı ama unverifiable experience'i official guide'dan ayri tutmak | Q107 | CANDIDATE |
| FC-065 | Evidence semantics view | User assertion/documented/reviewed/verified meaning ve basis'i gormek | Q109-Q110 | CANDIDATE |
| FC-066 | Critical safety catch-up summary | Ignored/accumulated critical topics'i harm/urgency/next-action ile ozetlemek | Q111-Q113 | CANDIDATE |
| FC-067 | Flexible premium packaging candidates | Analysis/storage/personalization ve non-recurring one-time values'i test etmek | Q114-Q115 | CANDIDATE |
| FC-068 | Record-only owner context | Guide kullanmadan history/reminder/document value ve later guide transition | Q117 | CANDIDATE |
| FC-069 | Shared motorcycle collaboration | Owner access, attribution, edit trail, revoke, private-note isolation | Q118-Q119 | CANDIDATE |
| FC-070 | Ownership transfer preview | Selected vehicle history aktarirken personal content'i ayirip preview sunmak | Q120 | CANDIDATE |
| FC-071 | Motorcycle archive lifecycle | Active garage'dan kaldirip history'yi korumak ve reactivate etmek | Q121 | CANDIDATE |
| FC-072 | Critical guide freshness gate | Last verification + stale application hold | Q122 | CANDIDATE |
| FC-073 | Progressive first-use preview | Account/permission/long-profile oncesi product value gostermek | Q123 | CANDIDATE |
| FC-074 | Turkey-first terminology presentation | Clear Turkish, familiar units, experience-based terminology depth | Q124 | CANDIDATE |
| FC-075 | Accessible active-repair guidance | Contrast, non-color warnings, image descriptions, captions, voice/easy-touch | Q125 | CANDIDATE |
| FC-076 | Self-remediation + re-entry path | Blocked readiness'ta learning/preparation/equipment/re-validation ile same guide'a guvenli donus | Q126-Q127 | CANDIDATE |
| FC-077 | Professional recommendation vs mandatory closure states | Optional external support ile mandatory critical gate'i acikca ayirmak | Q128 | CANDIDATE |
| FC-078 | Actual motorcycle deletion scope preview | Linked history/photo/measurement/reminder scope'u delete oncesi gostermek | Q129 | CANDIDATE |
| FC-079 | Independent transferred-record preservation | Source owner deletion'inin previously transferred independent records'i otomatik silmemesi | Q129 | CANDIDATE |
| FC-080 | Community contribution withdrawal | Public content/personal info removal + de-identified review trace + affected-guide re-review | Q130 | CANDIDATE |
| FC-081 | Provenance-rich export | Export'ta source, evidence level, significant corrections ve dates'i korumak | Q131 | CANDIDATE |
| FC-082 | Context-specific evidence explanation | Ortak labels ile birlikte context'e gore `hangi claim verify edildi` aciklamasi | Q132-Q134 | CANDIDATE |
| FC-083 | Partial-history transfer disclosure | Selected/incomplete history, covered period ve gaps'i new owner'a aciklamak | Q135-Q136 | CANDIDATE |
| FC-084 | Post-transfer correction proposal | Former owner'in silent overwrite yerine attributed correction/new-info proposal sunmasi | Q137 | CANDIDATE |
| FC-085 | Owner-first professional collaboration | Professional/hobby contributions'i desteklerken owner-first flow'u sade tutmak | Q138-Q140 | CANDIDATE |
| FC-086 | Segment-aware minimum value | Beginner/experienced/record-only/multi/shared/helper icin farkli minimum product value | Q141-Q143 | CANDIDATE |
| FC-087 | Core-completion paywall guard | Safety visuals, required steps, reasonable history ve export'un premium olmamasini korumak | Q145 | CANDIDATE |
| FC-088 | Basic multi-bike core + advanced garage premium candidate | Basit multi-bike separation'i core, advanced comparison/collaboration'i premium adayi tutmak | Q146 | CANDIDATE |
| FC-089 | Claim-sensitive freshness model | Safety notice/technical value/changeable procedure gibi claims icin freshness gate | Q147-Q149 | CANDIDATE |
| FC-090 | Stale teaching-reference mode | Stale critical guide'i teaching/reference olarak ayri tutup application'i close etmek | Q148-Q149 | CANDIDATE |
| FC-091 | Reviewable critical confirmations | Voice/easy interaction'da energy isolation/stability/critical connection/completion icin explicit confirmation | Q150-Q152 | CANDIDATE |
| FC-092 | Record-only first-use path | Rehber aramadan motorcycle add + latest record + next maintenance value | Q153 | CANDIDATE |
| FC-093 | Shared/multi-bike first-use path | Motorcycle separation ve actor attribution value'yu erken gostermek | Q154 | CANDIDATE |
| FC-094 | Value-triggered profile transition | Persistent record/cross-device/collaboration ihtiyacinda profile istemek ve local-data fate'i aciklamak | Q155 | CANDIDATE |
| FC-095 | Core history preservation guard | Basic longitudinal history fields'i storage pressure nedeniyle kaybetmemek | Q156 | CANDIDATE |
| FC-096 | Expanded evidence archive | Core evidence'in otesinde high-volume photo/video/document archive value sunmak | Q157-Q158 | CANDIDATE |
| FC-097 | Motorcycle isolation invariant | Each motorcycle history/km/reminder/active work state'ini independent tutmak | Q159-Q161 | CANDIDATE |
| FC-098 | Advanced garage workflows | Cross-bike analysis, bulk planning, richer collaboration ve archive search | Q160 | CANDIDATE |
| FC-099 | Disputed historical claims | Accepted record ile rejected correction/disputed claim'i provenance ile ayri tutmak | Q162-Q165 | CANDIDATE |
| FC-100 | Multi-transfer coverage view | Ownership periods, transferred scope ve unknown gaps'i history trust ile gostermek | Q164-Q165 | CANDIDATE |
| FC-101 | Downstream evidence-withdrawal re-review | Withdrawn community evidence'e bagli guide/claim'leri remaining evidence ile yeniden degerlendirmek | Q166-Q168 | CANDIDATE |
| FC-102 | Safety correction reach-back | Withdrawn evidence safety/technical/applied-critical content'i etkilerse affected users'a correction/re-review bilgisi vermek | Q167 | CANDIDATE |
| FC-103 | Shared evidence lifecycle controls | Owner record deletion, contributor evidence withdrawal ve access revoke etkilerini ayri yonetmek | Q169-Q171 | CANDIDATE |
| FC-104 | Risk-adaptive evidence disclosure | Low-risk concise label, high-risk explicit claim/evidence/reviewer/uncertainty explanation | Q172-Q174 | CANDIDATE |
| FC-105 | Trust-preserving local-to-profile migration | Scope preview, no-silent-loss ve user-reviewed conflict handling | Q175-Q177 | CANDIDATE |
| FC-106 | Physical-state remapping | Material guide change veya interrupted repair'da current physical state'i safe guide point'e yeniden eslemek | Q178-Q183 | CANDIDATE |
| FC-107 | Disputed service-completion state | Service document-owner observation conflict'ini unresolved tutup maintenance/future decisions'a certainty aktarmamak | Q184-Q185 | CANDIDATE |

## Important non-commitment

Bu adaylar user need'i temsil eder. MVP/phase priority, screen structure, premium package/price, technical data model, auth/sync, voice stack, offline implementation veya architecture bu asamada kararlastirilmaz.
