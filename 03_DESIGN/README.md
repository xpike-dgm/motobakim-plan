# 03 — DESIGN

Amac: Discovery source-of-truth'undan urunun marka kimligini, ekran/state envanterini ve user-approved visual reference sistemini kontrollu sirayla olusturmaktir.

## Current Phase 3 sequence

User'in 2026-09-15 tarihli latest explicit talimatiyla Phase 3 sirasi su sekilde rafine edilmistir:

1. **Brand naming exploration** — approved product truth'tan consumer-facing isim adaylari uret; preliminary collision/domain/app-brand research yap. **DONE**
2. **Brand-name selection + second-pass validation** — user favorite secimi ve deeper preliminary validation. **DONE**
3. **Explicit brand-name approval / reopen naming** — user favorite'i risk-aware bicimde working brand olarak onaylar veya naming'i yeniden acar. **CURRENT**
4. **Logo exploration** — yalniz approved working name uzerinden logo directions uretilir.
5. **Logo selection / brand visual DNA** — user preference QA edilir; logo/reference authority controlled kaydedilir.
6. **Anchor visual exploration — round 2** — selected name/logo/brand DNA ile core anchor screen visual directions yeniden uretilir.
7. **Screen inventory + navigation + state coverage** — approved Phase-2 product truth'tan full screen catalog, transition map ve critical state matrix cikar.
8. **Design principles / screen specs** — brand DNA + product trust/safety rules ile screen-level specs rafine edilir.
9. **Screen-by-screen visual references** — inventory/state coverage uzerinden gerekli reference visuals uretilir ve user approval alinir.
10. **Gate 3 -> 4 readiness review**.

Bu sira screen inventory/state coverage zorunlulugunu kaldirmaz; yalniz UI visual direction'i marka kimligi belirlendikten sonra kalibre eder.

## Current naming result

Current user favorite:
- `Kavriva`

Status:
- `PROPOSED_CONDITIONAL — USER FAVORITE / COLLISION RISK`

Artifacts:
- `BRAND_NAME_01_HANDOFF.md` — delegated second-pass portable package / raw handoff.
- `BRAND_NAME_REVIEW.md` — main-manager QA.

Known preliminary risk signals:
- active `Kavira Software` brand in Turkey/software context,
- `Kavira` mobile/digital brand use,
- close `KAVIVA` trademark activity,
- plausible spelling/hearing confusion.

These are not legal trademark-clearance conclusions.

Explicit user approval is required before logo exploration.

## Naming rules

- `Motobakim` / `MotoBakim` remains internal project codename until brand-name approval.
- User favorite != APPROVED name.
- Preliminary web/domain/app collision research != legal trademark clearance.
- Availability research yapilmadan bir isim `available` diye ilan edilemez.
- User approval olmadan isim APPROVED/LOCKED sayilmaz.
- Naming urunu yalniz maintenance-reminder gibi dar gostermemelidir.

## Previous anchor exploration status

Ilk anchor-screen 10-variant visual exploration denemesi user tarafindan begenilmedi.

- Hicbir varyant APPROVED/LOCKED degildir.
- `REFERENCE_INDEX.md` authority kazanmamistir.
- Deneme yalniz tarihsel design exploration feedback'idir.
- Approved working brand name ve logo sonrasinda anchor visual exploration yeniden yapilacaktir.

## Coverage rule

Sadece happy-path ekranlari degil loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade gibi critical states de inventory/state phase'inde kapsanmalidir.

## Current prompts

- `PHASE3_BRAND_NAMING_AI_PROMPT.md` — COMPLETED.
- Logo prompt — NOT CREATED; explicit name approval bekleniyor.
- `PHASE3_ANCHOR_VISUAL_EXPLORATION_AI_PROMPT.md` — DEFERRED; selected name + logo sonrasinda revise edilecek.
- `PHASE3_SCREEN_INVENTORY_AI_PROMPT.md` — DEFERRED; brand/anchor calibration sonrasi.
- Preserved initial inventory prompt: `PHASE3_SCREEN_INVENTORY_AI_PROMPT_DEFERRED_V1.md`.

## Scope restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Naming research hukuki marka tescil garantisi veremez.
- User approval olmadan name/logo/design artifact'larini APPROVED/LOCKED ilan edemez.

Gate 3 -> 4 icin screen catalog, navigation map, important state coverage ve yeterli user-approved visual references yine gereklidir.
