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

---

## DEC-0007 — Project-Wide Chat Instructions
**Date:** 2026-09-14  
**Status:** LOCKED

Motobakim projesindeki tum AI sohbetleri ortak bir proje baglami ve davranis kurallariyla calisacak. Bu genel kurallar `00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md` dosyasinda tutulacak.

---

## DEC-0008 — Phase 1 Workspace Approved and Gate 1 Passed
**Date:** 2026-09-14  
**Status:** APPROVED

Kullanici, kalite kontrolunden gecirilmis Phase-1 workspace sentezini acikca onayladi. Gate 1 -> 2 tamamlandi. Bu karar Phase-1 urun bilgisini LOCKED yapmaz.

---

## DEC-0009 — Phase 2 Product Discovery Approved and Gate 2 Passed
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, Q006-Q245 discovery evidence'ina dayanan kalite kontrolunden gecirilmis Phase-2 Product Discovery sentezini acikca onayladi ve Gate 2 -> 3 gecisini kabul etti.

Bunun sonucunda:
- `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md` Phase-2 canonical approval entry point'idir,
- `02_DISCOVERY/GATE_2_REVIEW.md` APPROVED / PASSED durumundadir,
- Phase 3 Design baslatilabilir.

Bu karar PROPOSED monetization direction'i final pricing/tier policy'ye donusturmez ve feasibility assumptions'i fact yapmaz.

---

## DEC-0010 — Phase 3 Begins with Anchor Visual Calibration
**Date:** 2026-09-15  
**Status:** SUPERSEDED
**Superseded By:** DEC-0011

Kullanici ilk screen-inventory promptunu gondermeden Phase-3 siralamasini once anchor visual calibration yapacak sekilde degistirdi. Ilk anchor visual denemesi daha sonra kullanici tarafindan yeterli bulunmadi.

---

## DEC-0011 — Phase 3 Brand Identity Before UI Visual Calibration
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici UI gorsellerini yeniden uretmeden once gercek consumer-facing ismin, ardindan logonun belirlenmesini istedi. Screen inventory/navigation/state coverage zorunlulugu korunmustur.

---

## DEC-0012 — Kavriva Approved as Working Consumer-Facing Brand Name
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici preliminary Kavira/Kaviva collision/confusion riskleri aciklandiktan sonra `Kavriva` adini Phase-3 working consumer-facing brand name olarak acikca onayladi.

Bu karar legal trademark clearance veya registrability/infringement sonucu degildir.

---

## DEC-0013 — L05A Approved as Working Kavriva Logo Direction
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici `L05A — The Precision Fit` refinement'ini secti. Main-manager direction'i `PASS_WITH_CONSTRAINTS` sonucuyla kabul etti.

Approval concept/direction seviyesindedir; production vector, exact paths/proportions, final wordmark typography, final palette, launcher-icon spec veya trademark/legal clearance degildir.

---

## DEC-0014 — U04 Approved as Working Kavriva Anchor UX Structure
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici controlled UX Structure Calibration turunda `U04 — Progressive Detail` yapisini secti. Main-manager `PASS_WITH_CONSTRAINTS` sonucu verdi.

Approved principle: **Accessible does not mean simultaneously prominent.**

Approval anchor calibration scope'undadir; universal full-app template veya final screen catalog/navigation/state architecture degildir.

---

## DEC-0015 — V10 Approved as Working Kavriva Anchor Visual Direction
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici visual-style exploration sonucunda `V10 — Signature Kavriva` yonunu secti. Main-manager `PASS_WITH_CONSTRAINTS` sonucu verdi.

Working signals:
- clean near-white canvas,
- deep graphite/navy text,
- restrained electric-blue accent,
- realistic inspection-focused imagery,
- moderate rounding,
- low decoration,
- strong hierarchy,
- restrained L05A presence,
- calm technical credibility.

Exact HEX/font/spacing/icon family/dark theme/responsive behavior final degildir. Shield/check generic canonical trust/safety badge degildir.

---

## DEC-0016 — Screen Inventory / Navigation / Critical-State Architecture Approved
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, delegated Screen Inventory 01 paketi + main-manager `PASS_WITH_REFINEMENTS` QA sonucundan sonra ekran planina devam edilmesini acikca onayladi (`onaylıyorum`).

Bunun sonucunda Phase-3 working architecture olarak sunlar APPROVED:
- `03_DESIGN/SCREEN_CATALOG.md` — `SCR-001` — `SCR-038` product interaction contexts,
- `03_DESIGN/NAVIGATION_MAP.md` — product-level transition architecture,
- `03_DESIGN/STATE_MATRIX.md` — critical-state architecture,
- `03_DESIGN/DESIGN_PRINCIPLES.md` — working screen-level design principles,
- `03_DESIGN/SCREEN_COVERAGE_TRACEABILITY.md` — journey/rule coverage,
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-ARCH-001`.

Main-manager refinement `SCR-038 — Community Experiences / Q&A` approval kapsamindadir.

Approval semantics bilincli olarak working-architecture seviyesindedir. Bu karar:
- 38 permanent implementation route gerektirmez,
- full-screen/sheet/modal/inline kararlarini source olmayan yerde kilitlemez,
- final global navigation shell veya bottom-tab yapisini secmez,
- final MVP scope/prioritization karari degildir,
- final component library/tokens/visual specs degildir,
- technology/backend/database/API/auth/sync/framework karari degildir,
- Gate 3 -> 4'u otomatik gecirmez.

Next authorized Phase-3 task: **Screen-Family Principles + Screen Specifications**.
