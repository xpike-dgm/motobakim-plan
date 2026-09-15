# 03 — DESIGN

Amac: Discovery source-of-truth'undan eksiksiz ekran/state envanteri cikarmak, kullanici tarafindan onaylanabilecek visual direction belirlemek ve daha sonra bu direction'i screen-by-screen tutarli bicimde yaymaktir.

## Current Phase 3 sequence

User'in 2026-09-15 tarihli explicit talimatiyla ilk kalibrasyon adimi guncellenmistir:

1. **Anchor visual exploration** — Motobakim'in core degerini temsil eden tek bir anchor screen icin ayni content/state ile 10 ayri visual direction uret.
2. **User visual-direction selection** — kullanici 1-3 favori veya hybrid visual DNA secer; bu secim QA edilmeden APPROVED/LOCKED sayilmaz.
3. **Screen inventory + navigation + state coverage** — approved Phase-2 product truth'tan full screen catalog, transition map ve critical state matrix cikar.
4. **Design principles / screen specs** — secilen visual DNA + product trust/safety rules ile screen-level specs'i rafine et.
5. **Screen-by-screen visual references** — inventory/state coverage uzerinden gerekli reference visuals'i uret ve user approval al.

Bu sira, screen inventory'nin Gate 3 icin zorunlulugunu kaldirmaz; yalniz visual direction'i erken kalibre ederek sonradan genis capli rework riskini azaltir.

## Anchor visual calibration rule

- Ilk anchor: `Aktif Islem / Adim Adim Uygulama Rehberi — normal application-ready state`.
- 10 visual direction ayni information/content semantics ile karsilastirilir; yalniz style/hierarchy/density/image treatment/shape language gibi visual variables degisir.
- Safety, trust/provenance, recovery path ve success-check variation ugruna kaldirilamaz.
- Anchor exploration full screen catalog karari degildir.
- User selection olmadan visual direction authority kazanmaz.

## Coverage rule

Sadece happy-path ekranlari degil loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade gibi critical states de inventory/state phase'inde kapsanmalidir.

## Current prompts

- **Current first prompt:** `PHASE3_ANCHOR_VISUAL_EXPLORATION_AI_PROMPT.md`
- `PHASE3_SCREEN_INVENTORY_AI_PROMPT.md` su anda DEFERRED pointer'dir.
- Ilk inventory promptunun korunmus kopyasi: `PHASE3_SCREEN_INVENTORY_AI_PROMPT_DEFERRED_V1.md`.

## Scope restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- User approval olmadan design artifact'larini APPROVED/LOCKED ilan edemez.

Gate 3 -> 4 icin screen catalog, navigation map, important state coverage ve yeterli user-approved visual references yine gereklidir.
