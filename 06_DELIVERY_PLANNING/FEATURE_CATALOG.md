# FEATURE CATALOG

Status: PROPOSED (E3 recorded 2026-09-21 after independent review PASS; rest pending)

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
|---|---|---|---|---|---|
