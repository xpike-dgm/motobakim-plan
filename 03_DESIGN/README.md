# 03 — DESIGN

Amac: Discovery source-of-truth'undan urunun marka kimligini, ekran/state envanterini ve user-approved visual reference sistemini kontrollu sirayla olusturmaktir.

## Current Phase 3 sequence

User'in 2026-09-15 tarihli latest explicit talimatiyla Phase 3 sirasi su sekilde rafine edilmistir:

1. **Brand naming exploration** — approved product truth'tan gercek consumer-facing isim adaylari uret; preliminary collision/domain/app-brand research yap.
2. **Brand-name selection + second-pass validation** — kullanici favorileri secer; finalist isimler daha derin kontrol edilir. Isim user approval olmadan authority kazanmaz.
3. **Logo exploration** — secilen isim uzerinden logo directions uretilir.
4. **Logo selection / brand visual DNA** — user preference QA edilir; logo/reference authority controlled kaydedilir.
5. **Anchor visual exploration — round 2** — selected name/logo/brand DNA ile core anchor screen icin visual directions yeniden uretilir.
6. **Screen inventory + navigation + state coverage** — approved Phase-2 product truth'tan full screen catalog, transition map ve critical state matrix cikar.
7. **Design principles / screen specs** — brand DNA + product trust/safety rules ile screen-level specs rafine edilir.
8. **Screen-by-screen visual references** — inventory/state coverage uzerinden gerekli reference visuals uretilir ve user approval alinir.
9. **Gate 3 -> 4 readiness review**.

Bu sira screen inventory/state coverage zorunlulugunu kaldirmaz; yalniz UI visual direction'i marka kimligi belirlendikten sonra kalibre eder.

## Current naming rule

- `Motobakim` / `MotoBakim` su anda **internal project codename / placeholder** olarak kalir.
- Naming AI approved product truth'a dayanmalidir; urunu yalniz maintenance-reminder gibi dar gosteren isimlerden kacinmalidir.
- Preliminary web/domain/app collision research hukuki trademark clearance degildir.
- Availability research yapilmadan bir isim `available` diye ilan edilemez.
- User secimi olmadan isim APPROVED/LOCKED sayilmaz.

## Previous anchor exploration status

Ilk anchor-screen 10-variant visual exploration denemesi user tarafindan begenilmedi.

- Hicbir varyant APPROVED/LOCKED degildir.
- `REFERENCE_INDEX.md` authority kazanmamistir.
- Deneme yalniz tarihsel design exploration feedback'idir.
- Selected brand name ve logo sonrasinda anchor visual exploration yeniden yapilacaktir.

## Coverage rule

Sadece happy-path ekranlari degil loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade gibi critical states de inventory/state phase'inde kapsanmalidir.

## Current prompts

- **USE NOW:** `PHASE3_BRAND_NAMING_AI_PROMPT.md`
- **DEFERRED:** `PHASE3_ANCHOR_VISUAL_EXPLORATION_AI_PROMPT.md` — selected name + logo sonrasinda yeniden kullanilacak/revise edilecek.
- **DEFERRED:** `PHASE3_SCREEN_INVENTORY_AI_PROMPT.md` — brand/anchor calibration sonrasi.
- Preserved initial inventory prompt: `PHASE3_SCREEN_INVENTORY_AI_PROMPT_DEFERRED_V1.md`.

## Scope restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Naming research hukuki marka tescil garantisi veremez.
- User approval olmadan name/logo/design artifact'larini APPROVED/LOCKED ilan edemez.

Gate 3 -> 4 icin screen catalog, navigation map, important state coverage ve yeterli user-approved visual references yine gereklidir.
