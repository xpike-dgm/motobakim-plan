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

---

## DEC-0012 — Kavriva Approved as Working Consumer-Facing Brand Name
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, delegated naming exploration + second-pass validation + main-manager QA sonrasinda `Kavriva` adini acikca onayladi.

Bilinen preliminary riskler user approval oncesinde aciklandi ve korunuyor:
- `Kavira Software` benzerligi,
- `Kavira` digital/mobile brand kullanimi,
- close spelling `KAVIVA` trademark activity,
- `Kavriva -> Kavira / Kaviva` hear/write confusion ihtimali.

Buna ragmen kullanici `Kavriva`yi Phase-3 design calismalari icin working consumer-facing brand name olarak kabul etti.

Bunun sonucunda:
- `03_DESIGN/BRAND_NAME.md` APPROVED brand-name source-of-truth'tur,
- logo exploration `Kavriva` uzerinden baslatilabilir,
- `Motobakim` / `MotoBakim` internal project/repository codename olarak kalabilir,
- brand name LOCKED degildir; daha yeni explicit user karari controlled supersession yapabilir.

Bu karar legal trademark clearance, registrability/infringement sonucu veya domain/handle availability garantisi degildir.

---

## DEC-0013 — L05A Approved as Working Kavriva Logo Direction
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, controlled Kavriva logo exploration Round 01 + Round 02 sonrasinda `L05A — The Precision Fit` refinement'ini final selection olarak secti. Main-manager, supplied L05A visual ve delegated handoff'u QA ederek direction'i `PASS_WITH_CONSTRAINTS` sonucuyla kabul etti.

Bunun sonucunda:
- `03_DESIGN/LOGO_DIRECTION.md` approved working logo-direction source'udur,
- `03_DESIGN/KAVRIVA_LOGO_01_HANDOFF.md` delegated evidence/handoff katmanidir,
- `03_DESIGN/KAVRIVA_LOGO_REVIEW.md` main-manager QA kaydidir,
- `03_DESIGN/REFERENCE_INDEX.md` icinde `REF-BRAND-001` L05A working direction'i APPROVED referans olarak kaydeder.

Approval scope concept/direction seviyesindedir. Generated PNG production-ready vector asset, exact paths/proportions, final wordmark typography, final palette, launcher-icon spec veya trademark/legal clearance degildir.

Future refinement speed/racing treatment eklememeli, rewind/back-arrow ambiguity'sini artirmamali, small-size negative-space separation'i korumali ve `Kavriva` wordmark'inda `r` ile iki `v` acik kalmalidir.

---

## DEC-0014 — U04 Approved as Working Kavriva Anchor UX Structure
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, repeated anchor-screen UX clutter feedback'i sonrasinda yapilan controlled UX Structure Calibration turunda `U04 — Progressive Detail` yapisini acikca secti (`U04`). Main-manager delegated handoff'u QA ederek structure'i `PASS_WITH_CONSTRAINTS` sonucuyla kabul etti.

Bunun sonucunda:
- `03_DESIGN/ANCHOR_UX_STRUCTURE.md` approved working anchor-UX source'udur,
- `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md` delegated evidence/handoff katmanidir,
- `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md` main-manager QA kaydidir,
- `03_DESIGN/REFERENCE_INDEX.md` icinde U04 working anchor hierarchy APPROVED reference olarak kaydedilebilir,
- sonraki visual-style exploration U04 hierarchy'sini sabit tutmak zorundadir.

Approved U04 principle:
**Accessible does not mean simultaneously prominent.**

Working hierarchy task-first'tur: compact context/progress -> step title -> quiet trust label -> dominant visual + one annotation -> concise instruction -> integrated critical safety -> collapsed detail affordance -> one dominant completion CTA -> lower-emphasis visible recovery path.

Approval scope bilincli olarak dardir. Bu karar:
- U04'u tum Kavriva ekranlari icin universal template yapmaz,
- final screen catalog/navigation/state architecture karari degildir,
- final component system, font, palette, exact spacing veya implementation karari degildir.

Visual-style exploration hierarchy order'ini, visible-vs-on-demand semantics'i, CTA placement logic'ini, critical-safety visibility'ni, trust visibility'ni, recovery emphasis'ini veya progressive-disclosure behavior'ini degistiremez.

---

## DEC-0015 — V10 Approved as Working Kavriva Anchor Visual Direction
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici visual-style exploration sonucunda `V10 — Signature Kavriva` yonunu ana gorsel yon olarak secti. Main-manager user-supplied V10 image ve handoff paketini QA ederek direction'i `PASS_WITH_CONSTRAINTS` sonucuyla kabul etti.

Bunun sonucunda:
- `03_DESIGN/ANCHOR_VISUAL_STYLE.md` approved working anchor visual-direction source'udur,
- `03_DESIGN/KAVRIVA_ANCHOR_VISUAL_STYLE_01_HANDOFF.md` delegated evidence/handoff katmanidir,
- `03_DESIGN/KAVRIVA_ANCHOR_VISUAL_STYLE_REVIEW.md` main-manager QA kaydidir,
- `03_DESIGN/REFERENCE_INDEX.md` icinde `REF-VISUAL-001` V10 working visual direction'i APPROVED referans olarak kaydedilebilir,
- Phase 3 full screen inventory + navigation + critical state coverage adimina gecilebilir.

Approved V10 direction signals:
- clean near-white canvas,
- deep graphite/navy text character,
- restrained electric-blue accent,
- realistic inspection-focused imagery,
- moderate rounding,
- low decoration,
- strong typographic hierarchy,
- restrained L05A brand presence,
- calm technical credibility.

Approval scope bilincli olarak dardir. Bu karar:
- handoff'taki exact HEX degerlerini final production token yapmaz,
- generated screenshot'u exact spacing/type/component specification yapmaz,
- generated motorcycle image'ini verified motorcycle-specific evidence yapmaz,
- shield/check iconography'yi final trust/safety component semantics'i olarak onaylamaz,
- U04'u tum ekranlara universal template yapmaz.

Required refinement constraints:
- trust/provenance iconography official safety certification veya guaranteed correctness izlenimi vermemeli,
- trust ile safety icon semantics'i ayristirilmali,
- final colors/accessibility/dark-mode behavior daha sonra validate edilmeli,
- responsive header behavior daha sonra screen/spec asamasinda ele alinmali.
