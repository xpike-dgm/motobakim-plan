# FEATURE CANDIDATES

Status: DRAFT

Discovery sirasinda ortaya cikan kullanici degeri odakli ozellik adaylari. Bunlar henuz kesin kapsam, teknik task veya mimari karar degildir.

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
| FC-050 | Premium convenience candidates | Gelismis analiz, ek depolama, coklu garaj gibi core-disinda ucretli degerleri test etmek | Q087 | CANDIDATE |
| FC-051 | Roadside quick guidance context | Garaj disinda hizli tarama, safety-first ve kisa gorsel adim sunmak | Q090 | CANDIDATE |
| FC-052 | Offline downloaded work context | Rehber/gorsel/safety/progress/history baglamini offline korumak | Q091 | CANDIDATE |
| FC-053 | User data controls | Kendi motosiklet/kayit/not/fotografini goruntuleme, duzeltme ve silme | Q092-Q094 | CANDIDATE |
| FC-054 | Free data portability | Kendi motosiklet/gecmis/not/fotograf verisini yeniden kullanilabilir export etmek | Q093 | CANDIDATE |
| FC-055 | Transparent deletion state | Silme kapsam/geri alinmazlik ve silinen/bekleyen durumunu aciklamak | Q094 | CANDIDATE |
| FC-056 | Readiness re-validation | Bloklanan readiness'i yeni fotograf/olcum/alternatif kontrol kanitiyla yeniden degerlendirmek | Q096-Q098 | CANDIDATE |
| FC-057 | Block reason + remediation + resume | Eksik kosulu, nedenini, nasil tamamlanacagini ve sonra kaldigi yere donusu gostermek | Q097-Q098 | CANDIDATE |
| FC-058 | Teaching-only content layer | Application gate kapali olsa bile guvenilir egitim/hazirlik bilgisini erisilebilir tutmak | Q099-Q104 | CANDIDATE |
| FC-059 | Professional escalation support | `Yapamazsin` yerine eksik kosula dayali professional option, preparation ve result-check destegi sunmak | Q100-Q101 | CANDIDATE |
| FC-060 | Aftermarket adapted guide coverage | Yaygin modifikasyonu ayristirip verified ise fabrika duzeninden farkli rehber sunmak | Q102 | CANDIDATE |
| FC-061 | Custom modification evidence-gap fallback | Unique/custom durumda evidence gap + teaching-only bilgi + application hold sunmak | Q103-Q104 | CANDIDATE |
| FC-062 | Community appeal / re-submit workflow | Moderation gerekcesini gormek, katkida duzeltme yapmak veya karara itiraz etmek | Q105 | CANDIDATE |
| FC-063 | Graduated contributor trust controls | Tekrarlanan yanlista pre-review, kasitli tehlikeli tekrarda contribution restriction uygulamak | Q106, Q108 | CANDIDATE |
| FC-064 | Unverified personal-experience status | Faydalı ama dogrulanamamis deneyimi official guide'dan ayri guven statusu ile tutmak | Q107 | CANDIDATE |
| FC-065 | Evidence semantics view | User assertion/documented/reviewed/verified anlam ve dayanaklarini gorunur kilmak | Q109-Q110 | CANDIDATE |
| FC-066 | Critical safety catch-up summary | Uzun sure ertelenmis veya birikmis kritik konulari zarar/aciliyet ve next action ile ozetlemek | Q111-Q113 | CANDIDATE |
| FC-067 | Flexible premium value packaging candidates | Analysis/storage/multi-garage/personalization ve non-recurring one-time degerleri test etmek | Q114-Q115 | CANDIDATE |
| FC-068 | Record-only owner mode/context | Guided repair kullanmadan history/reminder/document value sunmak ve sonradan rehbere gecis saglamak | Q117 | CANDIDATE |
| FC-069 | Shared motorcycle collaboration | Owner-granted access, contributor attribution, edit trail, revoke ve private-note isolation saglamak | Q118-Q119 | CANDIDATE |
| FC-070 | Ownership transfer preview | Secili vehicle history'yi aktarirken personal content'i ayirip transfer oncesi preview sunmak | Q120 | CANDIDATE |
| FC-071 | Motorcycle archive lifecycle | Aktif garajdan kaldirip history'yi korumak ve yeniden active etmek | Q121 | CANDIDATE |
| FC-072 | Critical guide freshness gate | Offline critical guide'da last verification'i gostermek ve stale application'i re-check'e kadar hold etmek | Q122 | CANDIDATE |
| FC-073 | Progressive first-use guide preview | Account/permission/long-profile zorunlulugundan once guide value'yu gostermek | Q123 | CANDIDATE |
| FC-074 | Turkey-first terminology presentation | Acik Turkce, alisilmis olcu birimleri ve deneyime gore terminology depth sunmak | Q124 | CANDIDATE |
| FC-075 | Accessible active-repair guidance | Buyuk controls, contrast, non-color warnings, image descriptions, captions, voice/easy-touch interaction sunmak | Q125 | CANDIDATE |

## Important non-commitment

Bu adaylar kullanici ihtiyacini temsil eder. MVP/sonraki faz, ekran yapisi, premium paket, moderation implementasyonu, offline teknik cozum, veri formati, auth modeli, voice teknolojisi veya mimari bu asamada kararlastirilmaz.
