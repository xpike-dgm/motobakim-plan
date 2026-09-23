# EPIC CATALOG

Status: APPROVED (owner-approved 2026-09-21 after independent coverage verification; G1–G6 remediations applied)

Row-status legend (clarification 2026-09-23, OUT-3 B-29 — semantics unchanged): row-level PROPOSED = planned-never-executed per Phase-6 convention (same as TASK_INDEX rows); document-level APPROVED = the catalog as planning artifact is closed and verified.

| Epic ID | Name | Outcome | Dependencies | Status |
|---|---|---|---|---|
| E1 | Tüketici mobil uygulaması | 5 sekme ve rehber/tanı/bakım/geçmiş/topluluk akışları Flutter'da çalışır + SCR-030 export | E3, E5, E4 | PROPOSED |
| E2 | Şirket yönetim paneli | Tarayıcıda içerik/operasyon çalışma alanı: inceleme, onay, yayın, ölçüm görünürlüğü + topluluk moderasyon/appeal (SCR-036) | E3, E5 | PROPOSED |
| E3 | Sunucu + veri omurgası | API kapısı, kanonik veri düzeni, platform kurulumu, ortamlar | — (temel) | PROPOSED |
| E4 | Çevrimdışı paket + senkron | Seçili görev paketi iner, kullanıcı işleri defterle gider, CON-005 uyumlu | E3 | PROPOSED |
| E5 | Giriş + yetki + denetim | Hesapsız başlangıç, profiller, hibrit yetkilendirme, denetim kasası, kurtarma yolları | E3 | PROPOSED |
| E6 | Yayın + güvenlik zinciri | Onay → yayın → acil fren, sürüm disiplini, imza emaneti politikası, olay müdahalesi | E3, E5 | PROPOSED |
| E7 | Derleme + mağaza hattı | Android şeridi çalışır, imza/mağaza şerit uygulaması, iOS aktivasyon kapıları tanımlı | E3, E6 | PROPOSED |
| E8 | İçerik + ölçüm | Kaynak/kanıt yönetimi akışı, analitik/gözlem düzlemleri, veri kalite görünürlüğü | E3 | PROPOSED |
| E9 | AI Usta + karar katmanı | Asistan akışı, açıklama soruları, karar katmanı, deterministik son doğrulama | E3, E1 | PROPOSED |
| E10 | Proje grafiği + görev altyapısı | Görev zarfları, graf/şema, kalite kapıları, kapanış takibi çalışır | — (temel) | PROPOSED |

## Cross-cutting notes (no separate epic; enforced in every epic's acceptance)

- Turkish language, units and accessibility behavior in all user-facing work.
- Entitlement/paywall-rule enforcement spans E1 (UI) + E3 (server-side checks) + E5 (policy); final pricing itself
  is not a task (commercial validation open).
- Notifications (reminders, correction reach-back) span E1 (surface) + E3 (scheduling/API) + E6 (incident comms).
- The E1/E9 interface (AI entry routing into guide flows) is flagged for exact resolution in Step 3 dependency work.
- No code, account, purchase or device proof in any epic; HELD evidence becomes acceptance criteria, not tasks.
- Dependency rules fixed per independent verification (2026-09-21): no E1↔E9 cycle (E9 proposes, E1 renders,
  E3 verifies); E4 is consumed by E1, not dependent on it; E7 builds against E3/E6 with E1 output validated in
  acceptance, not as a dependency; E6 owns signing custody policy, E7 owns lane execution; E2 consumes E8 outputs.
|---|---|---|---|---|
