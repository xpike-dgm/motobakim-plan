# FEATURE CATALOG

Status: CLOSED (all epics recorded + verified 2026-09-21; Gate 6 -> 7 PASSED under DEC-0055; row-level PROPOSED = planned-never-executed per Phase-6 convention, not pending work)

| Feature ID | Capability | Name | Scope | Dependencies | Status |
|---|---|---|---|---|---|
| F3.1.1 | C3.1 | Commit-time authorization enforcement | Effect öncesi tam tuple ile ALLOW/DENY/HELD; önbellek iddialar asla ikame değil | C3.1 | PROPOSED |
| F3.1.2 | C3.1 | Operation identity + idempotency + status lookup | Sabit kimlik/parmak izi; aynı-tekrar-sonuç, farklı-yük-ÇAKIŞMA, kiracı-dışı RED; CONFLICT/REJECTED dahil | C3.1 | PROPOSED |
| F3.1.3 | C3.1 | State dictionary | Birebir durum sözlüğü (ACCEPTED…RECOVERY_REQUIRED) + CONFLICT/REJECTED; izinli/engelli etkiler, tekrar/çözücü | C3.1 | PROPOSED |
| F3.1.4 | C3.1 | Direct-path inventory + negative tests | Açık yüzey envanteri + baypas negatif testleri; AI görev kapsamı; tarihli değişiklik/uyumluluk bekletme | C3.1 | PROPOSED |
| F3.2.1 | C3.2 | Domain authority CRUD + versioning | Alan başına kanonik otorite, kimlik/sürüm sözleşmeleri | C3.2 | PROPOSED |
| F3.2.2 | C3.2 | History/provenance + protected audit planes | Güncel/geçmiş/denetim ayrımı; kolaylık kopyaları asla otorite değil | C3.2 | PROPOSED |
| F3.2.3 | C3.2 | Object/media boundary + quarantine + classification | Nesne sınırı, karantina-öncelikli alım; sınıflandırma tüm türevlere yayılır | C3.2 | PROPOSED |
| F3.3.1 | C3.3 | Supabase-core readiness (hypothesis, no selection) | Geri alınabilirlik önkoşulları, API-sınır ihtiyaçları, BOM girdileri; bölge/plan/hesap seçimi yok, satın alma yok | C3.2 | PROPOSED |
| F3.3.2 | C3.3 | Defense-in-depth + secret custody | RLS/depolama savunma katmanı; service_role sunucuda; emanet/döndürme kuralları | C3.3 | PROPOSED |
| F3.4.1 | C3.4 | Queue/worker infrastructure + job families | Dayanıklı kuyruk/işçi; tam iş ailesi listesi; kira/nabız/kontrol-noktası/DLQ/geri-basınç/iptal/tahliye/uyumluluk/görünür-birikim/çözücü; ürünsüz | C3.1 | PROPOSED |
| F3.5.1 | C3.5 | Negative floors store | Tekdüze zeminler her committe yeniden okunur; yeni/eşit zemin kazanır | C3.5 | PROPOSED |
| F3.5.2 | C3.5 | Epoch propagation | İptal tüm uçlara ulaşır (iş/kuyruk/tanıtıcı/önbellek/paket/anahtar); indirilen kopya dürüstçe geri alınamaz | C3.5 | PROPOSED |
| F3.6.1 | C3.6 | Backup/restore drills + quarantine import | 4-düzlem karantina, bağımsız emanet, manifesto uzlaştırma | C3.3, C3.5 | PROPOSED |
| F3.6.2 | C3.6 | Clean-room exit rehearsal | Sabit kimlikler + normal-hesap-dışı mantıksal dışa aktarma; boşluklar açık | C3.3, C3.5 | PROPOSED |
| F3.7.1 | C3.7 | Cost BOM skeleton | Sınıflı iskelet (zorunlu/ertelenebilir/opsiyonel/ölçek); eşikler HELD; tutamama kuralı | C3.7 | PROPOSED |
| F3.8.1 | C3.8 | Environment separation + promotion plumbing | Ortam kimlik/gizli ayrılığı, ortamlarda yeniden-derleme yok; E6 kontrollerine referans | C3.3 | PROPOSED |
| F10.1.1 | C10.1 | Graph schema + identity standard | Sabit kimlik + denetlenebilir üstveri (birebir liste); 7 kalem kapı tespiti | C10.1 | PROPOSED |
| F10.2.1 | C10.2 | Capsule topology + dependency rules + repo topology | Kapsüller, stabilite-yönlü bağımlılık, sızıntısız sınırlar; plan/kod bağlantısı, yönetilen adresler, yetim-dosya-yok | C10.2 | PROPOSED |
| F10.3.1 | C10.3 | Task-pack schema + registry (manual-carrying compatible) | En-az paket + kayıt durumları; elle taşıma uyumlu, otomatik çalıştırma HELD | C10.3 | PROPOSED |
| F10.4.1 | C10.4 | Closure matrix (10 layers enumerated) | 10 katman + çift yönlü iz; yetim görev/kayıp gereksinim reddedilir | C10.3 | PROPOSED |
| F10.5.1 | C10.5 | Simulation set + excess-work scan | Senaryo tatbikatları + fazla-iş taraması | C10.4 | PROPOSED |
| F10.6.1 | C10.6 | Design gate (full §7) | Tek kaynak tasarım sistemi; kontrollü değişiklik kapısı; tam kanıt seti | — | PROPOSED |
| F10.7.1 | C10.7 | Review protocol + adversarial + DEC-0041 | Rol ayrılığı, ters-görüş, dış-bağımlılık bildirimi, ayrı çıktılar | C10.3 | PROPOSED |
| F4.1.1 | C4.1 | Package composition + safety-media nesting | Doğrulanmış çekirdek + iç içe güvenlik medyası; zorunlu-dışı ayrı (boyut önceden) | C4.1, E3 | PROPOSED |
| F4.1.2 | C4.1 | Nonessential media on-demand | Ayrı/açık/iptal edilebilir/temizlenebilir/yeniden alınabilir; boyut önceden | C4.1 | PROPOSED |
| F4.2.1 | C4.2 | Stage-verify-promote acceptance | Manifesto/özet/bağımlılık/uyumluluk; atomik yükseltme; tam-paket yedeği; zirve alan | C4.2, E3 | PROPOSED |
| F4.3.1 | C4.3 | Automatic transfer CON-005 (required core only) | YALNIZ gerekli çekirdek otomatik; ağ-türü/MB diyaloğu yok; desteklenen yerde tekrar (HELD); tamamlanma≠yetki | C4.3 | PROPOSED |
| F4.4.1 | C4.4 | Adaptive storage + eviction (enumerated) | Sıra: geçici→gereksiz→eski-önbellek→yeniden-üretilebilir; 6-sınıf asla-silme listesi | C4.4 | PROPOSED |
| F4.5.1 | C4.5 | Durable local ledger via E3 API | Yerel kimlikli işlemler + haller; gönderim/sorgu E3 API (F3.1.2) ile; kabul E3'ün | C4.5 | PROPOSED |
| F4.6.1 | C4.6 | Risk-tiered eligibility + cached suspension | Bilinmeyen/eski kritik kapalı; iç-operasyon değişikliği yalnız çevrimiçi-yetkili; E4 önbellek zemin uygular, gerçeklik E3/E6'da | C4.6 | PROPOSED |
| F4.7.1 | C4.7 | No-plaintext enforcement gate (only) | Mekanizma/emanet HELD; düz-metin kapıdan geçemez | C4.7 | PROPOSED |
| F4.8.1 | C4.8 | Numeric-policy HELD skeleton | Aday noktalar TEST NOKTASI; seçim, ölçüm kanıtında kabul kriteri (görev değil) | C4.8 | PROPOSED |
| F4.9.1 | C4.1 | Media classification rule | Necessity-to-understand/prove test (BR-132) + inviolability: core/safety evidence never hidden/deleted (BR-133); Q156 core / Q157 expanded; authority owned E3/E6, E8 derives/checks only | C4.1 | PROPOSED |
| F2.12.1 | C2.3 | Resilience states render | Failed validation/review/publication/rollback/recall shown inspectable + recoverable + resolver (RQ-060..062); unsaved/partial distinguished; four-part explanation; invoke only, E6 decides; additive overlay on C2.3, alters no F2.3.1 decision | C2.3 | PROPOSED |
| F9.1.1 | C9.1 | Assistant conversation flow | Anla→sor→5-aday→6-boyut-doğrula→göster/sor/beklet; E9 önerir, E1 gösterir, E3 doğrular | C9.1 | PROPOSED |
| F9.2.1 | C9.2 | Model routing economy (skeleton) | İlke iskeleti; eşik/seçim HELD; gösterişsiz değerlendirme | C9.2 | PROPOSED |
| F9.3.1 | C9.3 | Provider adapter boundary | Detay adaptörde; sürüm/davranış gözlemlenir; değişim yeniden değerlendirir | C9.3 | PROPOSED |
| F9.4.1 | C9.4 | Least-privilege tools + cost observability | İçerik politika değil; yetki çıktı dışında; sınırlı tekrar + maliyet görünürlüğü; AI-dışı devam | C9.4 | PROPOSED |
| F9.5.1 | C9.5 | Allowed-help (Decision-5 items 1–10 verbatim) | İzinli 10 kalem birebir | C9.5 | PROPOSED |
| F9.6.1 | C9.6 | Never-authority (Decision-6 items 1–15 verbatim) | Yasak 15 kalem birebir; belirsizlikte HOLD | C9.6 | PROPOSED |
| F9.7.1 | C9.7 | Project AI discipline (ref F10.7.1) | Disiplin referansı; DEC-0028/0029; bağımlılık C10.7 | C9.7, C10.7 | PROPOSED |
| F7.1.1 | C7.1 | Android lane continuity (execution-only) | Bağımsız şerit; kaynak dışarıda; derleme≠onay; imza ayrı; E6 politikasının şerit uygulaması; harcama görünürlüğü + çıkış koşu kitabı | C7.1, E6, E3 | PROPOSED |
| F7.2.1 | C7.2 | iOS activation gate package | 5 kanıt ayrı ayrı (gerçek Mac, Apple emaneti+roller, bağımsız geçmiş, sahipsiz-kurtarma, temiz oda); taahhüt yok | C7.2 | PROPOSED |
| F7.3.1 | C7.3 | Separation of powers execution (only) | Güçler ayrı; sağlayıcı çalıştırır sahip olamaz; anahtar-kayıp E6 senaryosu (politika E6'da) | C7.3, E6 | PROPOSED |
| F7.4.1 | C7.4 | Classification lists | Zorunlu/ertelenebilir/opsiyonel/ölçek listeleri güncel | C7.4 | PROPOSED |
| F7.5.1 | C7.5 | Cost reading (read-only) | Bant-değerlendirme TRY bağlamında; mağaza ayrı; tutma E3/E6 referanslı | C7.5, E3 | PROPOSED |
| F8.1.1 | C8.1 | Technical authority enforcement (reference-only) | 8-isim referansı; 6-vektör baypas engeli; yeniden-üretilebilirlik denetimi (sahiplik E3/E6'da) | C8.1, E3, E6 | PROPOSED |
| F8.2.1 | C8.2 | Adjunct evaluation gate | 4-yazarlık sınırı + 5-çıkarılabilirlik kanıtı + ölçülen-yük tetiği; ilk sürümde CMS yok | C8.2 | PROPOSED |
| F8.3.1 | C8.3 | Plane split enforcement | Kayıt-türevi sayaçlar; denetim dışarıda; gözlem ayrı (kayıt E3'te, E8 türetir, E2 gösterir) | C8.3 | PROPOSED |
| F8.4.1 | C8.4 | Analytics discipline (verbatim) | Yasak listesi birebir; sınıf-başı amaç/saklama; kesinti-bağımsızlık + değişim-taşınmazlık | C8.4 | PROPOSED |
| F8.5.1 | C8.5 | Measurement capability lists (9 mandatory) | 8 kalem + kesinti-bağımsızlığı (9.); ertele/opsiyonel/ölçek listeleri | C8.5 | PROPOSED |
| F8.6.1 | C8.6 | Fallback + exit honesty | 5-kapı denetimi; zayıflatmadan taban; 4-HELD taşınabilirlik kanıtı | C8.6 | PROPOSED |
| F1.0.1 | C1.0 | App shell + tabs | 5 sekme + sorumluluklar; aktif-iş korunumu (alt-bar HELD); Türkçe/birim/erişilebilirlik (sunum; gerçeklik dışarıda; kanıt yok) | C1.0 | PROPOSED |
| F1.1.1 | C1.1 | First-value entry + add motorcycle | SCR-001/002 giriş ve motor ekleme (sunum; gerçeklik dışarıda; kanıt yok) | C1.1 | PROPOSED |
| F1.1.2 | C1.1 | Variant resolution + fit states | SCR-003/004 ayrım + uygunluk halleri (sunum; gerçeklik dışarıda; kanıt yok) | C1.1 | PROPOSED |
| F1.2.1 | C1.2 | Guide discovery/fit/preparation | SCR-009..013 hazırlık kapısı, atlama yok (sunum; gerçeklik dışarıda; kanıt yok) | C1.2 | PROPOSED |
| F1.3.1 | C1.3 | Active execution + recovery | SCR-014..018 dürüst sonuçlar, devam-et-yok (sunum; gerçeklik dışarıda; kanıt yok) | C1.3 | PROPOSED |
| F1.4.1 | C1.4 | Diagnosis via E9 | SCR-019..021 tehlike-öncelikli, tek kontrol, E9 yönlendirmeli (sunum; gerçeklik dışarıda; kanıt yok) | C1.4 | PROPOSED |
| F1.5.1 | C1.5 | Maintenance/reminders | SCR-022..024 uydurma-aralık-yok, erteleme≠tamamlama (sunum; gerçeklik dışarıda; kanıt yok) | C1.5 | PROPOSED |
| F1.6.1 | C1.6 | History/evidence + export | SCR-025..030; E1 gösterir, E3 sunar, E5 yetkilendirir (sunum; gerçeklik dışarıda; kanıt yok) | C1.6 | PROPOSED |
| F1.7.1 | C1.7 | Lifecycle + entitlement gates | SCR-008/031..033/037; pasif≠silme; hak sunucuda (sunum; gerçeklik dışarıda; kanıt yok) | C1.7 | PROPOSED |
| F1.8.1 | C1.8 | Profile/collab/migration | SCR-006/007/034; zorlamasız, sessiz-kayıpsız, ayrılabilir (sunum; gerçeklik dışarıda; kanıt yok) | C1.8 | PROPOSED |
| F1.9.1 | C1.9 | Community consumer surface | SCR-035/036/038; karar E2'de, kabul≠doğrulama (sunum; gerçeklik dışarıda; kanıt yok) | C1.9 | PROPOSED |
| F1.10.1 | C1.10 | AI Usta entry A1 | 1+1+2; üçüncü yol/yazışma yok; E9 önerir, E1 gösterir, E3 doğrular (sunum; gerçeklik dışarıda; kanıt yok) | C1.10 | PROPOSED |
| F1.2.2 | C1.2 | Estimate display | Süre-aralığı + maliyet-ayrımı + istisna/tarih; veri-kaynağı HELD, bilinmeyen-bilinmiyor (sunum; gerçeklik dışarıda; kanıt yok) | C1.2 | PROPOSED |
| F1.9.2 | C1.9 | Commerce neutrality | Sponsor işaretli; liste rehberin yerine geçmez; satış-hedefi oyunu engelli; uyum-öncelikli (sunum; gerçeklik dışarıda; kanıt yok) | C1.9 | PROPOSED |
| F1.3.2 | C1.3 | Roadside mode | Kullanıcı-çağrılı kısa/hızlı kip; belirsizlik bandı kalıcı (sunum; gerçeklik dışarıda; kanıt yok) | C1.3 | PROPOSED |
| F1.3.3 | C1.3 | Safe-closure criteria set | Kategori kriter içeriği (yazar: alan-uzmanı + ikinci inceleme; E2 taslak→E6 onay; doğrulama HELD) (sunum; gerçeklik dışarıda; kanıt yok) | C1.3 | PROPOSED |
| F2.1.1 | C2.1 | Workspace shell | Yoğun tarayıcı alanı; erişilebilirlik temeli, duyarlı ertelendi (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.1 | PROPOSED |
| F2.2.1 | C2.2 | Review/approval queues | Kanıtlı paketler; WS-06 + WS-05; bağımsızlık arayüzde (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.2 | PROPOSED |
| F2.3.1 | C2.3 | Publication/recall operations | WS-07 + WS-11 yürütme yüzeyi; karar E6'da (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.3 | PROPOSED |
| F2.4.1 | C2.4 | Source/quarantine view | WS-03; özel karantina özet/soy; API yetkisiyle etkinleşme (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.4 | PROPOSED |
| F2.5.1 | C2.5 | Coverage/quality visibility only | WS-01 + WS-09; kayıt-türevi RQ-052..058; E8'i tüketir, yığın seçmez (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.5 | PROPOSED |
| F2.6.1 | C2.6 | Access administration view | WS-12; kendine-yetki yok (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.6 | PROPOSED |
| F2.7.1 | C2.7 | Moderation internal decisions | Sebepli işlem + denetim izi; SCR-036 arkası (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.7 | PROPOSED |
| F2.8.1 | C2.8 | Authoring draft workspace | Sınırlı taslak RQ-017..024; taslak-asla-canlı (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.8 | PROPOSED |
| F2.9.1 | C2.9 | Variant boundary admin | WS-02 kapsam çiti + matris/çoğaltma/karşılaştırma (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.9 | PROPOSED |
| F2.10.1 | C2.10 | Lineage view | WS-08 zincir + geri-alma-adayı/düzeltme bağı (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.10 | PROPOSED |
| F2.11.1 | C2.11 | Audit trail view | WS-10 RQ-046 alanları + RQ-047 ayrımı; kasa E5'te (tarayıcı; çatı/hesap/kod yok; CMS yetkisiz) | C2.11 | PROPOSED |
| F5.1.1 | C5.1 | Consumer identity + account-light + migration | Yerel-başlangıç, profil, çakışmasız geçiş; Supabase yönü, satın alma yok | C5.1 | PROPOSED |
| F5.2.1 | C5.2 | Hybrid authorization decision (E3 uygulamasına girdi) | Sunucuda tuple kararı + sebep; zemin/kuşak çitiyle E3 F3.1.1'e girdi | C5.2 | PROPOSED |
| F5.2.2 | C5.2 | Separation-of-duties enforcement | Değişim başına uyumsuzluk engeli; küçük ekipte görünür BEKLEME | C5.2 | PROPOSED |
| F5.3.1 | C5.3 | Authentication + sessions + step-up | Oltalamaya dayanıklı giriş, işleme bağlı ikinci doğrulama, sınırlı oturum | C5.3 | PROPOSED |
| F5.3.2 | C5.3 | Identity-plane epoch revocation | Oturum/yetki/kuşak/bekleyen işler; çalıştırma uçları için E3 F3.5.2'yi çağırır; indirilen kopya dürüstçe geri alınamaz | C5.3 | PROPOSED |
| F5.4.1 | C5.4 | Recovery-only flow | İptal + taze giriş, çift kontrol; kurtarma asla onay/yayın/yetki üretmez | C5.4 | PROPOSED |
| F5.5.1 | C5.5 | Audit vault custody (R1/R2/R3/R5/R8) | Olay kapsamı, asgari anlam, etki-öncesi bağ, bütünlük/uyarı, yönetim ayrılığı | C5.5 | PROPOSED |
| F5.5.2 | C5.5 | Investigation chain (E5 okuma) | Nesne-merkezli zincir, korumalı referanslar; zincir mantığı E3'te | C5.5 | PROPOSED |
| F5.5.3 | C5.5 | Retention/legal/admin-separation execution | Saklama/yasal-tutma/redaksiyon denetlenen olaylar; emanet bağımsızlığı yeniden doğrulanır | C5.5 | PROPOSED |
| F5.6.1 | C5.6 | Quarantine pipeline (E5 politika) | Karantina halleri, yalıtılmış önizleme; zorlama E3 F3.2.3'te | C5.6 | PROPOSED |
| F5.6.2 | C5.6 | Export disclosure | Kapsam/amaç önizlemesi, en-azlama, üretim kimliği; kalıntı-kopya uyarısı, bağ-iptali-yalnız-gelecek | C5.6 | PROPOSED |
| F5.6.3 | C5.6 | AI/OCR proposal-only | Girdi/köken bağlantılı öneri; asla onay değil; düşmanca talimat etkisiz | C5.6 | PROPOSED |
| F5.7.1 | C5.7 | Activation gate evaluation (only) | 11 kalem değerlendirme; ikinci-insan emaneti yoksa BEKLEME, açma hükmü yok | C5.7 | PROPOSED |
| F6.1.1 | C6.1 | Authority separation registry | 8 otorite ayrı; çökmeme + personel yoksa görünür BEKLEME | C6.1 | PROPOSED |
| F6.2.1 | C6.2 | Approval binding + publication transition + state model | Mühürlü paket, kapılı geçiş, çit kuralı; tam durum modeli | C6.2 | PROPOSED |
| F6.2.2 | C6.2 | Consumer contract evaluation | İstemcide anlam çözümleme; itme tavsiye, eski reddedilir | C6.2 | PROPOSED |
| F6.3.1 | C6.3 | Emergency plane + drills | Negatif-yetki, iki-kişi/tek-aktör istisnası, süre-sınırlı, kuşak tekdüzeliği, tatbikat | C6.3 | PROPOSED |
| F6.4.1 | C6.4 | Provenance/SBOM/signing + promote-not-rebuild | Yapıt-bağlı köken, bağımsız doğrulama; aynen terfi, dal/etiket yasak, gizliye dokunma yok | C6.4 | PROPOSED |
| F6.5.1 | C6.5 | Config/flag/migration releases | Kapalı-graf listesi + istemci-zarf kontrolü; tipli/sürümlü/denetimli | C6.5 | PROPOSED |
| F6.6.1 | C6.6 | Rollout + rollback + quarantine | Kademeli haller; durdurma düşürmez; geri yüklemede karantina; kuşaklar tekdüze | C6.6 | PROPOSED |
| F6.7.1 | C6.7 | Incident + impact graph | Sınıflandırma, etki grafiği, korumalı kopya; uzlaşmadan kapanış yok | C6.7 | PROPOSED |
| F6.8.1 | C6.8 | OTA denial gate | Varsayılan ret + gerekçe; gelecek listesi tam (yerli-değiştirme/genişletme/birleştirme yok) | C6.8 | PROPOSED |
| F1.11.1 | C1.11 | Account deletion + consent surface | Deletion/withdrawal renders; E1 renders, E3/E5 execute; audit receipt | C1.11 | PROPOSED |
| F3.9.1 | C3.9 | Store-billing gate + consent store | Paid entitlement only with store receipt; server-side check; consent records server-held | C3.9 | PROPOSED |
| F5.8.1 | C5.8 | KVKK rights execution | Deletion/access/objection requests with receipts; cross-border transfer assessed; legal text under expert review | C5.8 | PROPOSED |
| F7.6.1 | C7.6 | Store declaration inventory | Data-Safety + privacy label + age gate inventoried; drift re-checked on store-policy change | C7.6 | PROPOSED |
| F4.9.2 | C4.9 | Measurement corpus + device matrix | Fixed corpus + device matrix; sizes/areas/durations measured as evidence | C4.9 | PROPOSED |
