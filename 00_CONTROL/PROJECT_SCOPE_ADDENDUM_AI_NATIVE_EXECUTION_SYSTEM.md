# PROJECT SCOPE ADDENDUM — AI-NATIVE EXECUTION AND PROJECT GRAPH SYSTEM

Status: `APPROVED PROJECT REQUIREMENT`
Authority: `DEC-0028`
Date: 2026-09-17

## 0. Operating Model

Per `DEC-0029`, Kavriva'nın planlama, tasarım, yazılım üretimi, inceleme, test hazırlığı, dokümantasyon ve repository
yönetimi AI tarafından yürütülecektir. Kullanıcı teknik olmayan product owner/decision owner'dır; kullanıcıdan kod,
mimari ayrıntı, debugging veya teknoloji uzmanlığı beklenemez.

AI sistemi teknik kararları kullanıcıya sonuç, maliyet, risk ve geri döndürülebilirlik diliyle sunar. Kullanıcı ürün
önceliği ve kabul edilebilir risk/maliyet yönünü belirler; teknik çeviri, uygulama ve doğrulama AI sisteminin görevidir.

Bu model insan hesabı/sözleşmesi, mağaza sahipliği, yasal onay veya doğrulanmış alan uzmanlığı gerektiren dış bağımlılıkları
yok saymaz. Böyle bir gereklilik ortaya çıkarsa AI bunu erken, teknik olmayan şekilde ve tam olarak gereken kullanıcı/dış
eylemle bildirir; kullanıcının gizlice geliştirici veya güvenlik uzmanı rolü üstlendiği varsayılmaz.

## 1. User Intent

Kavriva yalnızca modüler kodlanmayacaktır. Kodlama başlamadan önce proje; birbirinden ayrılmış, amacı ve sınırı belli,
sözleşmelerle bağlanan ve bağımsız AI oturumlarının bütün projeyi okumadan güvenle görev yapabildiği bir yürütme sistemi
olarak planlanacaktır.

Obsidian üzerinden her önemli klasör, dosya, modül, sözleşme, karar, ekran, görev ve testin:

- ne işe yaradığı;
- kime veya hangi alana ait olduğu;
- hangi öğelere bağlı olduğu;
- kimler tarafından kullanıldığı;
- hangi gereksinim ve tasarım kararını karşıladığı;
- hangi görev ve testlerle değiştirildiği/doğrulandığı;
- güncel, eski, beklemede veya tamamlanmış olup olmadığı

görülebilmelidir.

## 2. Mimari Hedef

Hedef “mümkün olan en küçük dosyalar” değildir. Aşırı parçalama anlaşılmaz bir bağımlılık ağı üretebilir. Hedef:

> Küçük değişiklik yüzeyi + açık sahiplik + dar public contract + görünür bağımlılık + otomatik sınır kontrolü.

Bu çalışma biçimi repository içinde **contract-governed task-addressable architecture** olarak ele alınacaktır. Her
uygulanabilir parça bir “kapsül” gibi davranır: amacı, public yüzeyi, iç alanı, izin verilen bağımlılıkları, testleri,
değişim kuralları ve ilgili proje bağlantıları bellidir.

## 3. Obsidian-Uyumlu Proje Grafiği

Kod repository'sindeki yönlendirici belgeler Markdown ve Obsidian uyumlu olacaktır. Her kayıt için istikrarlı kimlik ve
makinece doğrulanabilir metadata standardı Phase 5/7'de kararlaştırılacaktır. En az şu ilişki türleri desteklenir:

- `purpose` — neden var;
- `domain/module/owner` — sorumluluk ve sahiplik;
- `depends_on` / `used_by` — yönlü bağımlılıklar;
- `implements` — gereksinim, iş kuralı, ekran/state, ADR veya contract bağlantısı;
- `public_contracts` / `internal_scope` — dışarı açık ve içeride kalan yüzey;
- `tasks` / `tests` / `evidence` — değişiklik ve tamamlanma kanıtı;
- `supersedes` / `superseded_by` — kontrollü değişim zinciri;
- `status` / `last_verified` — güncellik.

Grafik yalnızca elle çizilmiş açıklama olmayacaktır. Yetim kayıt, bozuk bağlantı, yasak dependency, döngü, sahipsiz public
contract, testsiz kritik davranış ve güncel olmayan context pack kalite kapılarında tespit edilecektir.

Repository'de oluşturulan her dosya ve klasör graph envanterinden bulunabilir ve en az bir amaç/sahiplik/modül/task
bağlantısına çözümlenebilir olmalıdır. Ancak her küçük kaynak dosya için elle ayrı uzun Obsidian notu yazılması zorunlu
değildir: önemli artifact'ler doğrudan node olur; küçük kaynak dosyalar ilgili modül manifesti, otomatik path index'i ve
görev kanıtı üzerinden görünür olur. Böylece tam path görünürlüğü korunurken sistem gerçek güvence üretmeyen dosya başına
bürokrasiye dönüşmez.

## 4. AI İçin Görev Paketi

Bir AI'ya yalnızca “sıradaki görevi yap” denildiğinde sistem önce uygulanabilir sıradaki `TASK-xxx` kaydını seçebilmeli
ve AI'ya minimum fakat yeterli context pack vermelidir. Her görev en az şunları içerir:

- tek ve ölçülebilir amaç;
- neden gerekli olduğu ve hangi kullanıcı sonucuna bağlandığı;
- ön koşullar ve tamamlanmış dependency'ler;
- okunması zorunlu ADR, contract, rule, ekran/state ve modül kayıtları;
- dokunulmasına izin verilen path/modüller;
- dokunulması yasak alanlar ve yetki genişletme kuralları;
- beklenen dosya/artifact değişiklikleri;
- acceptance criteria ve negatif/failure senaryoları;
- çalıştırılacak validation/architecture/integration kontrolleri;
- migration, rollback ve veri koruma gereksinimi;
- tasarım referansı ve responsive/accessibility kuralları;
- completion evidence ve handoff formatı;
- görevin hangi yeni context/graph kayıtlarını güncellemesi gerektiği.

AI görevin dışına çıkmak zorundaysa sessizce genişletemez. Görevi `BLOCKED` veya change-request durumuna geçirir.

## 5. “Bütün Task'lar Bitti = Proje Bitti” Kanıtı

Task sayısının sıfıra inmesi tek başına proje tamamlanması değildir. Proje ancak aşağıdaki kapanış katmanlarının tümü
geçerse tamamlanmış sayılabilir:

1. **Task closure:** Her task acceptance ve evidence ile kapanmıştır.
2. **Feature closure:** Bir feature'ın tüm davranış, hata, erişilebilirlik ve veri durumları kapsanmıştır.
3. **Flow closure:** Uçtan uca kullanıcı akışı modüller arası çalışır; yalnızca parçalar tek tek geçmez.
4. **Requirement closure:** Onaylı her gereksinim/iş kuralı en az bir feature, flow, task ve validation'a izlenir.
5. **Design closure:** Her ekran/state canonical tasarım sistemine ve responsive/accessibility sözleşmesine uyar.
6. **Architecture closure:** Yetim modül/contract, yasak dependency, döngü veya sınır ihlali yoktur.
7. **Data/migration closure:** Şema, migration, rollback, offline ve restore senaryoları kanıtlanmıştır.
8. **Release closure:** Güvenlik, performans, gözlemlenebilirlik, paketleme, mağaza ve operasyon kapıları geçmiştir.
9. **Product scenario closure:** Onaylı kritik gerçek senaryolar uçtan uca sonuç üretir.
10. **Gap audit:** Bilinen açık soru, placeholder, TODO, sahipsiz risk veya kanıtsız `DONE` kalmamıştır.

Bu nedenle Phase 6'da yalnız task listesi değil, çift yönlü bir closure matrisi kurulur:

`Requirement/Rule/Screen/State -> Epic -> Capability -> Feature -> Flow -> Task -> Contract/Module -> Test/Evidence`

Ters yönde de her task'ın onaylı bir ihtiyaca bağlandığı kanıtlanır. Bağlantısız “gereksiz task” ve tasksız “kayıp
gereksinim” kabul edilmez.

## 6. Kod Yazmadan Task Simülasyonu

Kodlamadan önce görev planı şu yöntemlerle simüle edilir:

- dependency graph üzerinde baştan sona yürütme sırası;
- her task sonrası beklenen repository durumunun belge üzerinden kontrolü;
- blocked, failed, partial, retry, rollback ve değişen gereksinim senaryoları;
- iki paralel AI görevinin aynı dosya/contract/modüle çarpışma analizi;
- eski ve yeni contract kullanan task'ların uyumluluk analizi;
- kritik kullanıcı akışlarının task dizileri üzerinde masaüstü walkthrough'u;
- requirement-to-evidence matrisi üzerinden eksik ve fazla iş taraması;
- bir task kasıtlı çıkarıldığında hangi requirement/flow/testin açık kaldığını gösteren gap testi;
- bütün task'lar `DONE` varsayıldığında ürün/release closure kapılarının yeniden değerlendirilmesi.

Simülasyon “plan güzel görünüyor” onayı değildir. Her açık bağlantı `MISSING`, `UNOWNED`, `BLOCKED`, `CONFLICT` veya
`UNVERIFIED` olarak görünür kalır.

## 7. Çoklu-AI Tasarım Tutarlılığı

Birden fazla AI ekran geliştirebilir; ancak hiçbiri bağımsız tasarım dili icat edemez. Kodlama öncesinde ve sırasında:

- canonical design tokens;
- component ve pattern kataloğu;
- layout/spacing/type/icon/motion kuralları;
- responsive breakpoint ve yeniden yerleşim kuralları;
- ekran/state sözleşmeleri;
- Türkçe içerik ve terim sözlüğü;
- erişilebilirlik semantiği;
- referans ekran ve kabul edilebilir varyasyon sınırları;
- shared shell/navigation kuralları

tek kaynak olur. Task, hangi tasarım öğelerini kullanacağını ve hangilerini değiştiremeyeceğini belirtir.

Ekranların tek tek güzel görünmesi yeterli değildir. Feature ve release seviyesinde tam-ekran, ekranlar-arası ve state'ler-
arası tutarlılık incelemesi; responsive birleşim; erişilebilirlik; görsel regresyon ve canonical reference comparison gerekir.
Yeni component/pattern ancak kontrollü tasarım değişikliğiyle kataloğa eklenir.

## 8. Aşamalara Dağılım

| Aşama | Bu gereksinim kapsamında yapılacak iş |
|---|---|
| Phase 4 | Teknoloji alternatifleri bu sınırları, graph/contract/test enforcement ve AI context yönetimini destekleyebilme açısından değerlendirilir. |
| Phase 5 | Modül stratejisi, repository/topoloji, contract/versioning, metadata/kimlik, dependency direction ve karar sahipliği ADR'lerle kilitlenir. |
| Phase 6 | Tam Epic→Task ağı, common task schema, dependency DAG, closure matrisi, tasarım/requirement coverage ve no-code task simülasyonu oluşturulur. |
| Phase 7 | Context router, context pack standardı, modül kapsülleri, public contracts, change-control, AI görev protokolü, validation ve architecture-test kuralları tasarlanır. |
| Phase 8 | Gerçek repository/vault, manifestler, index/graph üretimi, templates, CI kalite kapıları ve task registry fiziksel olarak kurulur ve bootstrap kanıtı üretilir. |
| Development | AI'lar yalnız READY task/context pack ile çalışır; task, feature, flow, architecture, design ve product closure ayrı ayrı doğrulanır. |

Bir aşama sonraki aşamaya iş atmak için kullanılmaz. Önceki aşama kendi sözleşmesini ve gerekli girdileri tamamlar;
yalnız çalıştırılması doğası gereği koda bağlı olan testler Development'a kalır.

## 9. Zorunlu Gate Ekleri

- Gate 5 -> 6: AI-safe modül/contract/topoloji ADR'leri onaylı olmalıdır.
- Gate 6 -> 7: Task graph yalnız dolu değil, çift yönlü closure audit ve no-code simulation ile tutarlı olmalıdır.
- Gate 7 -> 8: Context routing, graph metadata, boundary/change/design rules ve tamamlanma kanıtı tasarımı bitmiş olmalıdır.
- Gate 8 -> Development: Repository + Obsidian graph + CI/architecture/design/traceability checks çalışır ve örnek görevle
  doğrulanmış olmalıdır; örnek doğrulama ürün kodu geliştirmeye dönüşemez.

## 10. Değişmez Sonuç

Hiçbir AI'nın “projeyi bilmiyordum” gerekçesiyle güvenlik, tasarım, veri veya mimari sınırları bozması kabul edilmez.
Sistem AI'ya doğru minimum bağlamı vermek, izin verilen değişiklik alanını sınırlamak, etkileri otomatik kontrol etmek ve
tamamlanmayı task sayısından bağımsız kanıtlamak zorundadır.

AI implementer'ın kendi sonucunu tek başına doğrulaması yüksek etkili işlerde yeterli değildir. Plan; ayrı uygulayıcı,
inceleyici ve gerektiğinde adversarial/validation rollerini, kanıta dayalı otomatik kontrolleri ve çelişki çözümünü
tanımlar. Aynı model kullanılsa bile roller, context ve ilk inceleme bağımsız tutulur; ortak-kör-nokta riski görünür kalır.
