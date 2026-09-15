# 03 — DESIGN

Amac: Discovery source-of-truth'undan urunun marka kimligini, ekran/state envanterini ve user-approved visual reference sistemini kontrollu sirayla olusturmaktir.

## Current Phase 3 sequence

User'in 2026-09-15 tarihli explicit onayi ile naming tamamlanmis ve current sequence su hale gelmistir:

1. **Brand naming exploration** — approved product truth'tan consumer-facing isim adaylari uret; preliminary collision/domain/app-brand research yap. **DONE**
2. **Brand-name selection + second-pass validation** — user favorite secimi ve deeper preliminary validation. **DONE**
3. **Explicit brand-name approval** — `Kavriva` working consumer-facing brand olarak user tarafindan APPROVED. **DONE**
4. **Logo exploration** — approved `Kavriva` uzerinden form-first logo directions. **CURRENT / READY**
5. **Logo selection / brand visual DNA** — user preference + main-manager QA; logo/reference authority controlled kaydedilir.
6. **Anchor visual exploration — round 2** — selected name/logo/brand DNA ile core anchor screen visual directions yeniden uretilir.
7. **Screen inventory + navigation + state coverage** — approved Phase-2 product truth'tan full screen catalog, transition map ve critical state matrix cikar.
8. **Design principles / screen specs** — brand DNA + product trust/safety rules ile screen-level specs rafine edilir.
9. **Screen-by-screen visual references** — inventory/state coverage uzerinden gerekli reference visuals uretilir ve user approval alinir.
10. **Gate 3 -> 4 readiness review**.

Bu sira screen inventory/state coverage zorunlulugunu kaldirmaz; yalniz UI visual direction'i marka kimligi belirlendikten sonra kalibre eder.

## Approved working brand name

**Kavriva**

Status: `APPROVED WORKING CONSUMER-FACING BRAND NAME`

Canonical source:
- `BRAND_NAME.md`
- DEC-0012

`Motobakim` / `MotoBakim` internal project/repository codename olarak kalabilir.

Known preliminary naming risks user approval ile kabul edilmis fakat cozulmus sayilmamistir:
- `Kavira Software` similarity,
- `Kavira` digital/mobile use,
- close spelling `KAVIVA` trademark activity,
- hear/write confusion possibility.

Naming approval legal trademark clearance degildir. Formal similarity clearance ve priority domain/handle verification later launch-risk validation topics olarak kalir.

## Logo exploration rule

Current prompt:
- **USE NOW:** `PHASE3_LOGO_EXPLORATION_AI_PROMPT.md`

Round 01:
- 10 distinct logo directions,
- 10 separate images,
- form-first / monochrome,
- symbol + wordmark relationship,
- app-icon scale potential,
- no final color palette decision.

Critical wordmark constraint:
- `Kavriva` icindeki `r` ve ikinci `v` okunabilir kalmali; logo `Kavira` / `Kaviva` confusion riskini artirmamali.

Avoid cliche-first dependence on:
- generic motorcycle silhouette,
- wrench + gear,
- shield + checkmark,
- AI sparkle/brain/robot,
- racing flame/speed imagery.

Generated image production-ready vector asset veya trademark-safe mark sayilmaz.

## Naming artifacts

- `BRAND_NAME.md` — APPROVED working brand source.
- `BRAND_NAME_01_HANDOFF.md` — delegated naming package / evidence handoff.
- `BRAND_NAME_REVIEW.md` — main-manager QC.
- `PHASE3_BRAND_NAMING_AI_PROMPT.md` — COMPLETED.

## Previous anchor exploration status

Ilk anchor-screen 10-variant visual exploration denemesi user tarafindan begenilmedi.

- Hicbir varyant APPROVED/LOCKED degildir.
- `REFERENCE_INDEX.md` authority kazanmamistir.
- Deneme yalniz tarihsel design exploration feedback'idir.
- Kavriva logo direction secildikten sonra anchor visual exploration yeniden yapilacaktir.

## Coverage rule

Sadece happy-path ekranlari degil loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade gibi critical states de inventory/state phase'inde kapsanmalidir.

## Current prompts

- `PHASE3_BRAND_NAMING_AI_PROMPT.md` — COMPLETED.
- **`PHASE3_LOGO_EXPLORATION_AI_PROMPT.md` — USE NOW.**
- `PHASE3_ANCHOR_VISUAL_EXPLORATION_AI_PROMPT.md` — DEFERRED; approved/QA-ed logo direction sonrasinda revise edilecek.
- `PHASE3_SCREEN_INVENTORY_AI_PROMPT.md` — DEFERRED; brand/anchor calibration sonrasi.
- Preserved initial inventory prompt: `PHASE3_SCREEN_INVENTORY_AI_PROMPT_DEFERRED_V1.md`.

## Scope restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Naming research veya generated logo legal trademark guarantee veremez.
- User approval olmadan logo/UI artifacts APPROVED/LOCKED ilan edilemez.

Gate 3 -> 4 icin screen catalog, navigation map, important state coverage ve yeterli user-approved visual references yine gereklidir.
