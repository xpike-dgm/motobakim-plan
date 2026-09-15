# DECISION LOG

Kalici ve kullanici tarafindan onaylanmis surec/proje yonetim kararlarinin kaydi.

Status: `PROPOSED`, `APPROVED`, `LOCKED`, `SUPERSEDED`, `DEPRECATED`.

---

## DEC-0001 — Repository as Persistent Project Memory
**Date:** 2026-09-14  
**Status:** LOCKED

Motobakim projesinin kalici baglami `xpike-dgm/motobakim-plan` GitHub repository'sinde tutulacak. Yeni AI oturumlari sohbet hafizasina bagimli olmadan baglami buradan yeniden kuracak.

---

## DEC-0002 — ChatGPT Role
**Date:** 2026-09-14  
**Status:** LOCKED

ChatGPT planlama surecinde proje mimari muhendisi ve yoneticisi rolunu ustlenecek; diger AI'lar uzman, tartisma katilimcisi, reviewer veya implementer olarak kullanilabilecek.

---

## DEC-0003 — Scope Restricted to Memory Management
**Date:** 2026-09-14  
**Status:** SUPERSEDED
**Superseded By:** DEC-0004

Onceki asamada yalnizca AI hafiza sistemi kurulmasi kararlastirilmisti. Hafiza sistemi tamamlandi ve kullanicinin yeni talimatiyla kapsam genisletildi.

---

## DEC-0004 — Eight-Stage Planning Workflow
**Date:** 2026-09-14  
**Status:** LOCKED

Planlama su sirayla yurutulecek:
1. AI calisma sistemi
2. Teknik olmayan urun kesfi
3. Tasarim / ekran referanslari
4. Uzman AI teknoloji stratejisi tartismasi
5. ADR ile teknoloji kararlarinin kaydi
6. Epic -> Capability -> Feature -> User Flow -> Task planlamasi
7. AI-native development architecture
8. Kesinlesen mimarinin repository seviyesinde bootstrap edilmesi

Asamalar `00_CONTROL/PHASE_GATES.md` kosullari saglanmadan atlanmayacak.

---

## DEC-0005 — Evidence, Synthesis and Decision Separation
**Date:** 2026-09-14  
**Status:** LOCKED

Ham kanit, sentez, tartisma ve kesin karar farkli katmanlarda tutulacak. Discovery ham Q&A kayitlari urun gercegi yerine gecmez; tech debate karari kilitlemez; kesin teknoloji/mimari kararlar ADR ile kayda girer.

---

## DEC-0006 — User-Facing Discovery Is Delegated to Other AI Sessions
**Date:** 2026-09-14  
**Status:** LOCKED

ChatGPT proje mimari muhendisi ve yoneticisi olarak discovery sorularini dogrudan kullaniciya sormak yerine, diger AI oturumlarinda kullanilacak kontrollu promptlari hazirlayacak. Kullanici bu promptlari diger AI'lara verecek; alinan cevaplar/sonuclar daha sonra ChatGPT tarafindan repository source-of-truth sistemine islenecek ve kalite/uyumluluk acisindan kontrol edilecek.

Ilk uygulama promptu: `01_WORKSPACE/PHASE1_WORKSPACE_AI_PROMPT.md`.

---

## DEC-0007 — Project-Wide Chat Instructions
**Date:** 2026-09-14  
**Status:** LOCKED

Motobakim projesindeki tum AI sohbetleri ortak bir proje baglami ve davranis kurallariyla calisacak. Bu genel kurallar `00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md` dosyasinda tutulacak.

Her sohbetin ozel gorev promptu rol ve gorevi belirler; genel proje talimati ozel promptun yerine gecmez. Bir AI'ya acikca repository yazma veya karar kilitleme yetkisi verilmedikce AI source-of-truth dosyalarini degistirmeyecek ve kararlarin durumunu LOCKED/APPROVED yapmayacak.

---

## DEC-0008 — Phase 1 Workspace Approved and Gate 1 Passed
**Date:** 2026-09-14  
**Status:** APPROVED

Kullanici, kalite kontrolunden gecirilmis Phase-1 workspace sentezini acikca onayladi.

Bunun sonucunda:
- `01_WORKSPACE/PROJECT_VISION.md` APPROVED
- `01_WORKSPACE/CONSTRAINTS.md` APPROVED
- `01_WORKSPACE/ASSUMPTIONS.md` registry olarak APPROVED; tekil varsayimlar OPEN kalir
- `01_WORKSPACE/GLOSSARY.md` registry olarak APPROVED; PROPOSED terimler nihai/LOCKED sayilmaz
- Gate 1 -> 2 kosullari saglanmis kabul edilir
- Phase 2 teknik olmayan Product Discovery baslatilabilir

Bu karar Phase-1 urun bilgisini `LOCKED` yapmaz; yeni discovery kanitlari kontrollu degisiklik uretebilir.

---

## DEC-0009 — Phase 2 Product Discovery Approved and Gate 2 Passed
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, Q006-Q245 discovery evidence'ina dayanan kalite kontrolunden gecirilmis Phase-2 Product Discovery sentezini acikca onayladi ve Gate 2 -> 3 gecisini kabul etti.

Bunun sonucunda:
- `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md` Phase-2 canonical approval entry point'idir,
- `02_DISCOVERY/GATE_2_REVIEW.md` APPROVED / PASSED durumundadir,
- `02_DISCOVERY` Phase-2 snapshot seviyesinde APPROVED kabul edilir,
- Gate 2 -> 3 tamamlanmistir,
- Phase 3 Design baslatilabilir.

Bu karar:
- Phase-2 product truth'u LOCKED yapmaz,
- raw evidence ile synthesis ayrimini degistirmez,
- `PROPOSED` monetization direction'i final pricing/tier policy'ye donusturmez,
- open feasibility/validation assumptions'i fact yapmaz.

Phase 3 Design approved product snapshot'tan ilerleyecek; teknoloji/backend architecture veya implementation karari vermeyecektir.

---

## DEC-0010 — Phase 3 Begins with Anchor Visual Calibration
**Date:** 2026-09-15  
**Status:** SUPERSEDED
**Superseded By:** DEC-0011

Kullanici, ilk screen-inventory promptunu henuz baska AI'ya gondermeden Phase 3 icindeki sirayi degistirip once anchor visual calibration yapilmasini istemisti.

Bir anchor screen icin 10 visual direction denemesi daha sonra gerceklestirildi; kullanici ortaya cikan gorselleri yeterli bulmadi ve hicbirini reference direction olarak onaylamadi.

Bu nedenle anchor-first sequencing DEC-0011 ile supersede edilmistir. Ilk anchor denemesi tarihsel design exploration olarak kalir; approved reference authority olusturmaz.

---

## DEC-0011 — Phase 3 Brand Identity Before UI Visual Calibration
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici anchor-screen icin uretilen ilk visual denemeleri begenmedigini ve UI gorsellerini yeniden uretmeden once uygulamanin gercek consumer-facing adinin, ardindan logosunun belirlenmesini acikca istedi.

Phase 3 current sequence:
1. Brand naming exploration + preliminary collision research,
2. user brand-name selection + second-pass validation,
3. selected name uzerinden logo exploration,
4. user logo selection / brand visual-DNA calibration,
5. anchor screen visual exploration selected name/logo ile yeniden,
6. full screen inventory + navigation + critical state coverage,
7. design principles / screen specs,
8. screen-by-screen visual references + user approval,
9. Gate 3 -> 4 readiness review.

`Motobakim` adi gercek marka adi secilene kadar internal project codename/placeholder olarak kalir.

Bu karar:
- Phase 2 product truth'u degistirmez,
- naming veya logo adaylarini user selection olmadan APPROVED/LOCKED yapmaz,
- preliminary name research'i hukuki trademark clearance yerine koymaz,
- screen inventory/navigation/state coverage zorunlulugunu kaldirmaz,
- technology/backend architecture veya implementation karari vermez.

Current first prompt:
`03_DESIGN/PHASE3_BRAND_NAMING_AI_PROMPT.md`.
