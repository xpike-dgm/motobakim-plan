# DECISION LOG

Kalici ve kullanici tarafindan onaylanmis surec/proje yonetim kararlari kaydi.

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

---

## DEC-0016 — Screen Inventory / Navigation / Critical-State Architecture Approved
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici, delegated Screen Inventory 01 paketi + main-manager `PASS_WITH_REFINEMENTS` QA sonucundan sonra ekran planina devam edilmesini acikca onayladi (`onayliyorum`).

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

---

## DEC-0017 — Five-Tab Bottom Navigation + Screen-Family Specs Approved
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici screen-family/spec QA sonrasinda global navigation icin yeni bir explicit preference verdi: capability'leri tek bir ana sayfada toplamak yerine 5 bottom-bar destination kullanmak ve ortadaki ana yardim entry'sini `AI Usta` yapmak. Ardindan su shell'i acikca onayladi:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

Bunun sonucunda:
- `03_DESIGN/GLOBAL_NAVIGATION.md` APPROVED global navigation source-of-truth'tur,
- `03_DESIGN/SCREEN_FAMILY_SPECS.md` APPROVED working screen-family/spec source'udur,
- `03_DESIGN/SCREEN_FAMILY_SPEC_REVIEW.md` APPROVED review record'dur,
- 9-family grouping ve per-SCR hierarchy/action/trust/safety specs downstream visual-reference work icin authority olabilir.

### Tab responsibility

- **Garaj:** selected motorcycle context, switching ve lifecycle.
- **Bakim:** maintenance plan/reminders/catch-up.
- **AI Usta:** known-task + symptom-first assistance'in merkezi entry'si.
- **Gecmis:** longitudinal history/evidence/trust/correction/export.
- **Topluluk:** community Q&A/experiences/contribution/moderation; official guide authority'sinden ayri.

### AI Usta authority boundary

`AI Usta` UX role/entry label'idir; bu karar LLM/provider/backend/AI architecture secmez.

AI Usta:
- verified technical source-of-truth yerine gecemez,
- motorcycle fit/readiness/safety gates'i bypass edemez,
- unsupported technical value veya definitive diagnosis uyduramaz,
- approved known-task / diagnosis / guide flows'a controlled entry saglar.

Exact interaction formu — structured assistant, conversational UI, search/prompt veya hybrid — daha sonra controlled design work ile belirlenir.

### Controlled SCR-005 refinement

5-tab shell ile `SCR-005` broad action-hub rolunden Garaj / selected-motorcycle context responsibility'sine daralir. Known-task + symptom primary entry `AI Usta`, maintenance `Bakim`, history `Gecmis`, community `Topluluk` tablarina dagitilir. Bu capability removal degil, previous dashboard/card-stack riskini azaltan navigation refinement'tir.

### Additional QA constraint

Language/unit preference ve accessibility support profile/account prerequisite olamaz; account-light/local use'da da kullanilabilir olmalidir.

### Still not finalized

Bu karar:
- exact icon/font/spacing/animation'i,
- active-repair sirasinda bottom-bar visibility'sini,
- first post-onboarding landing tab'ini,
- exact ambiguous sheet/modal/full-screen mappings'i,
- final component/token system'i,
- pricing veya technology architecture'ini
final yapmaz.

Next authorized Phase-3 task: **five-tab shell uzerinde family-based screen visual references**.

---

## DEC-0018 — A1 Guided Split Approved as Working AI Usta UX Structure
**Date:** 2026-09-15  
**Status:** APPROVED

Kullanici delegated AI Usta UX calibration turunda A1 adayi icin verbatim olarak:

> A1 iyi

secimini yapti. Main-manager portable handoff'u approved navigation/spec/product boundaries ile QA ederek `PASS_WITH_CONSTRAINTS` sonucuyla kabul etti.

Approved working structure:
**A1 — Guided Split**.

### Root hierarchy

AI Usta root surface:
- compact selected motorcycle context,
- `Nasil yardimci olayim?`,
- `Bir is yapmak istiyorum`,
- `Motorda bir sorun var`,
- optional low-prominence help,
- approved five-tab bottom navigation

yapisini kullanir.

Target:
**1 context + 1 prompt + 2 paths.**

### Routing authority

- `Bir is yapmak istiyorum` -> `SCR-009 Known Task Find / Select`.
- `Motorda bir sorun var` -> `SCR-019 Symptom Capture`.

A1 root technical answer surface veya chat-history home degildir. Task declaration fit/readiness authority yaratmaz; symptom declaration direct part-replacement veya unsupported diagnosis uretmez.

### Constraints

- Two intent choices bulky card-stack'e donusturulmez.
- Selected motorcycle context compact kalir; lifecycle/switch authority Garaj'dadir.
- Root free-form composer zorunlu degildir; natural language downstream task/symptom capture'da kullanilabilir.
- AI Usta verified guide/source/provenance yerine gecemez ve safety/fit/readiness gates'i bypass edemez.
- Ambiguous user icin low-prominence `Hangisini secmeliyim?` yardimi olabilir; third equal-weight path degildir.

Canonical sources:
- `03_DESIGN/AI_USTA_UX_STRUCTURE.md`
- `03_DESIGN/KAVRIVA_AI_USTA_UX_STRUCTURE_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-AIUSTA-001`

Bu karar LLM/provider/backend/AI architecture, production tokens/icons, active-repair bottom-bar visibility veya first post-onboarding landing tab'i finalize etmez.

Next authorized Phase-3 task: **five-tab main-shell root visual references**.

---

## DEC-0019 — Active Application / Safety / Recovery Visual Family Approved
**Date:** 2026-09-16
**Status:** APPROVED

User reviewed the E01-E05 active-work visual family, first requested the explicit L05A logo correction, then accepted the refined set with the verbatim feedback:

> genel olarak iyi

Approved working set:
- E01 existing V10 / `SCR-014 Active Guide Step`, unchanged,
- E02 `SCR-015 Problem / Mismatch / Recovery`, refined `v2-L05A`,
- E03 `SCR-016 Resume Revalidation`, refined `v2-L05A`,
- E04 `SCR-017 Material Guide Change / Physical-State Remap`, refined `v2-L05A`,
- E05 `SCR-018 Completion / Safe Closure / Record`, refined `v2-L05A`.

Canonical sources:
- `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`,
- `03_DESIGN/KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_01_HANDOFF.md`,
- `03_DESIGN/KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_REVIEW.md`,
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-ACTIVE-001`.

Required constraints:
- E02-E05 hidden/reduced global navigation remains PROPOSED ONLY,
- saved UI progress is not current physical proof,
- recovery never provides continue-anyway,
- material guide change never auto-reverses or guesses continuation,
- partial/unresolved/safe-stop outcomes remain truthful outcomes,
- safe closure/recovery/revalidation cannot be paywalled,
- exact production copy/components/tokens/accessibility/routing remain non-final.

Next recommended Phase-3 visual family: **FAM-04 Diagnosis (`SCR-019`-`SCR-021`)**.

---

## DEC-0020 — Phase 3 Design Complete and Gate 3 -> 4 Passed
**Date:** 2026-09-17
**Status:** APPROVED

The user approved the final remaining Phase-3 deliverables with the verbatim decision:

> şuan 3 bitti mi onları onaylıyorum

The approval follows presentation of:
- the SCR-004 fit-confirmed and missing-distinction candidate pair,
- the Internal Data & Content Operations requirements, workflow/lifecycle and platform-independent workspace architecture package.

As a result:
- SCR-004 is accepted as a working visual reference,
- FAM-01 is complete under `REF-FIRSTUSE-001`,
- the Internal Data & Content Operations Phase-3 working addendum is APPROVED,
- required Phase-3 screen, navigation, state and reference coverage is sufficient,
- Gate 3 -> 4 is PASSED,
- Phase 4 Technology Strategy is authorized to begin under the user's next explicit task but is not started by this decision alone.

This decision does not select or finalize:
- mobile framework,
- web/desktop/hybrid internal-tool form,
- database/CMS/search/storage,
- backend/API/sync/event architecture,
- authentication or permission implementation,
- AI/LLM/provider,
- analytics stack,
- exact publishing mechanics,
- production UI tokens/components,
- pricing/tier/quota.

Canonical closure records:
- `03_DESIGN/FIRST_USE_MOTORCYCLE_CONTEXT_VISUAL_REFERENCES.md`
- `03_DESIGN/KAVRIVA_FIRST_USE_VISUALS_REVIEW.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REVIEW.md`
- `03_DESIGN/GATE_3_READINESS_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md`

---

## DEC-0021 — Planning Remains No-Code; Internal Operations Is Browser-Based
**Date:** 2026-09-17
**Status:** APPROVED WORKING DIRECTION

User decision, verbatim:

> bu planlama süreci bu süreçte kod yazılmasını istemiyorum istersen başka bir ai a verdiğin bir konu hakkında deepresearch yaptırabilirim ama kod yazmak yok
> şirket içi yönetimininde tarayıcı olarak istiyorum

Decision:

1. This planning process will not create application code, throwaway prototypes, proof-of-concept applications or
   executable technology spikes. Technology comparison remains document/research work.
2. Deep research may be delegated to other AI agents when useful. Independent adversarial AI review remains allowed.
3. Candidate technologies are compared through approved product scenarios, official/primary evidence, architecture
   walkthroughs, failure-mode analysis, decision matrices, operational/TCO analysis and reviewer critique—not by coding.
4. Internal Data & Content Operations will be planned as a browser-based web application.
5. A desktop application or desktop wrapper is outside the current approved direction. Reopening it requires a new
   explicit user decision; it is not an automatic fallback.

This decision does not select the consumer mobile framework; backend/database/cloud/CMS/search/analytics technology;
authentication/RBAC implementation; publication/sync/offline architecture; AI provider; or final web framework.

The browser-based internal form must still meet the approved dense workflow, accessibility, security, audit,
controlled-publication, recall and operational requirements. Phase 5 ADR will later record the technical rationale;
this user direction is binding input to that ADR.

---

## DEC-0022 — Sub-Agent Model Authorization Boundary
**Date:** 2026-09-17
**Status:** SUPERSEDED
**Superseded By:** DEC-0049 (model-choice restriction relaxed; Luna Max default retained as preferred sub-agent)

User instruction, verbatim:

> birde altajan çalıştırırken luna maxi izinsiz istediğin gibi çalıştırabilirsin ama diğer modelleri izinsiz çalıştırma birdaha

Decision:

- Luna Max means `gpt-5.6-luna` with reasoning effort `max`.
- The main manager may use Luna Max as a sub-agent without requesting additional permission when delegation is useful
  and remains inside the active user task.
- Any other sub-agent model—including Astra, Sol, Terra and GPT-5.5—requires explicit user permission before each use.
- Prior authorization does not require a sub-agent to be used and does not expand task scope, permit code during the
  no-code planning process or override phase/change-control rules.
- Running multiple Luna Max agents remains subject to task relevance and available concurrency; adding a different
  model still requires explicit permission.

---

## DEC-0023 — Offline Downloads Must Be Data-Efficient and Task-Scoped
**Date:** 2026-09-17
**Status:** APPROVED WORKING CONSTRAINT

User instruction, verbatim:

> çevrimdışı işlemde fazla veriyi indirmesinler uygulamamızda veri en önemli şeylerden biri aslında

Decision:

- Offline capability must not require downloading the full guide/content library, unrelated motorcycles or unused media.
- The default download unit is the smallest safe package for the selected motorcycle, applicable guide/task and current work.
- The mandatory lightweight core includes fit/version/status metadata, text/steps, critical warnings, required checks
  and task-specific safe-stop/recovery content. Data saving cannot remove these safety essentials.
- High-resolution media, video and nonessential extended material are optional/on-demand and show expected size before download.
- Large automatic background downloads over cellular data are not allowed by default. Network preference and explicit
  user control are required; exact thresholds remain open.
- Reusable assets should not be downloaded repeatedly; later architecture must evaluate deduplication, incremental
  updates, compression, cache limits and user-visible storage cleanup without weakening integrity/version controls.

This decision constrains offline content delivery but does not select a storage, CDN, media, compression or sync technology.

**Supersession note — 2026-09-20 / CON-005:** The older requirement that large cellular/background downloads require
network-based explicit user confirmation is superseded for future product direction. Kavriva must not ask the user for
download confirmation merely because transport is cellular/mobile data or because a byte threshold is crossed. The rest
of DEC-0023 remains binding: downloads stay selected-motorcycle/task scoped and data-efficient; unrelated/full-library
content is not downloaded by default; safety essentials cannot be removed merely to reduce bytes.

---

## DEC-0024 — DEBATE-002 Working Direction Approved
**Date:** 2026-09-17
**Status:** APPROVED WORKING DIRECTION

After the DEBATE-002 direction was explained with the `DEC-0023` data-efficiency constraint incorporated, the user approved it with:

> tamamdrı

Approved working direction:

- offline motorcycle-facing application is risk-tiered and bounded rather than universally online-only or unlimited;
- downloaded guides carry exact release/client compatibility and eligibility context;
- unknown/unclassified or stale critical dependency fails closed and inherits the highest consequence;
- teaching, history, provenance and task-specific safe-stop/recovery remain distinct from normal application eligibility;
- offline start requires a complete compact recovery closure for all reachable physical states;
- restored backup, time anomaly, incompatible old client or mixed package cannot create new positive authority;
- Internal Operations approve/publish/recall/role mutations require an authoritative online result;
- offline packages are selected-motorcycle/task scoped, data-efficient and layered; heavy media is optional/on-demand.

Still unresolved and not approved by this decision:

- numeric freshness/validity windows;
- exact risk taxonomy and which highest-consequence tasks are always-online;
- numeric package-size/cellular/cache limits;
- concrete mobile framework, storage, sync, signing, CDN or backend technology;
- emergency suspension/outage/reach-back implementation;
- old-client support duration and minimum OS/version matrix;
- final offline-draft behavior for Internal Operations.

No ADR is created. This decision is binding input to later Phase-5 ADRs; Gate 4 -> 5 remains closed.

## DEC-0025 — DEBATE-003 Approval, Publication and Emergency Suspension Direction Approved
**Date:** 2026-09-17
**Status:** APPROVED WORKING DIRECTION

After two Luna Max research tracks, two independent Luna Max adversarial reviews and incorporation of all critical
corrections, the user approved the revised DEBATE-003 direction with:

> tamamdır

Approved working direction:

- approval binds the complete immutable consumer-served meaning, including derived artifacts and meaning-changing inputs;
- publication uses a closed release manifest and one authoritative guarded transition;
- normal publication is fenced against the current suspension/revocation generation and cannot clear a newer stop;
- browser timeout or disconnected confirmation becomes explicit `outcome unknown` and is reconciled by the same bound operation identity;
- authoritative-current, delivery-observed and consumer-reconciled remain separate states;
- emergency suspension is a narrow negative authority, operationally independent from the normal publication path to
  the failure-domain level required by later analysis, and cannot create replacement technical truth;
- restore/failover cannot move release or suspension authority backward; restored systems remain quarantined until
  current authority, audit continuity, content integrity and trust context reconcile;
- rollback is a new controlled event to a still-valid known-good release; otherwise the affected scope is suspended;
- protected attributable audit evidence is required for normal and emergency actions, including fallback handling;
- overlapping scope follows dependency-aware, most-restrictive applicable negative authority until explicit reviewed re-entry.

Still unresolved and not approved by this decision:

- numeric suspension, propagation, reconciliation, RTO or RPO targets;
- exact release/suspension scope lattice and independently publishable unit;
- exact role names, staffing, quorum and single-actor emergency exception;
- physical failure-domain topology, emergency credentials, trust roots and audit-buffer implementation;
- database, backend, queue, cache/CDN, signing, identity, cloud or other implementation technology;
- affected-user reach-back channels, acknowledgment rules and service levels;
- final mobile framework and other Phase-4 topics.

No ADR is created. This decision is binding input to later Phase-5 ADRs; Gate 4 -> 5 remains closed.

---

## DEC-0026 — DEBATE-004 Identity, Authorization, Audit and Untrusted Ingestion Direction Approved
**Date:** 2026-09-17
**Status:** APPROVED WORKING DIRECTION

After two Luna Max research tracks, two independent Luna Max adversarial reviews and incorporation of all critical
corrections, the user approved the revised DEBATE-004 direction with:

> onaylandı

Approved working direction:

- understandable base roles provide candidate capabilities, while every sensitive action is authorized server-side
  against current actor/session, action, exact scope, workflow state, classification, consequence and independence;
- deny-by-default applies; browser/UI/cached role state is never authority;
- high-consequence official work cannot be self-approved/self-published; unavailable independent competence places work
  in a visible `HELD` state rather than weakening the rule;
- privileged roles use phishing-resistant authentication, sensitive actions require fresh step-up and privileged recovery
  revokes relying-party sessions, recovery artifacts and pending high-consequence authority through a security epoch;
- authorization policy/access administration is itself a protected versioned object with material author/approve/activate separation;
- delegation is scoped, attributable, time-bounded and cannot copy competence, bridge classification or defeat separation of duties;
- audit evidence is ordered, tamper-evident, separately protected and has explicit fallback/hold behavior during outage;
- files and URL-fetched material enter quarantine-first layered validation; scanning or rendering never establishes
  technical correctness, evidence sufficiency or approval;
- untrusted previews are isolated from operations credentials/authority and original/derived artifacts retain exact lineage;
- unknown/mixed private/shared/community/official classification uses the most restrictive handling and propagates to derivatives;
- export is separately authorized and recorded as a disclosure event that cannot retract already downloaded/copied data;
- AI/OCR/extraction produces attributable proposals only and hostile document instructions have no policy/tool/workflow authority.

Still unresolved and not approved by this decision:

- exact role matrix, low-risk role combinations, reviewer competence issuers and staffing/quorum details;
- numeric session, reauthentication, delegation, access-review, retention, scan or file/resource limits;
- exact identity/recovery, authorization-policy, audit-custody and break-glass implementation;
- permitted file/source classes, encrypted-document policy, URL connectors and quarantine-original access;
- legal/privacy/retention/export destinations, redaction and investigation policy;
- identity provider, policy engine, scanner, renderer, logging, storage, cloud, AI provider or other technology;
- final mobile framework and other Phase-4 topics.

No ADR is created. This decision is binding input to later Phase-5 ADRs; Gate 4 -> 5 remains closed.

---

## DEC-0027 — DEBATE-005 Software, Content Supply Chain and Release Governance Direction Approved
**Date:** 2026-09-17
**Status:** APPROVED WORKING DIRECTION

After two Luna Max research tracks, two independent Luna Max adversarial reviews and incorporation of all critical
corrections, the user approved the revised DEBATE-005 direction with:

> onaylıyorum

Approved working direction:

- consumer app binary, Internal Operations web, backend/API, database migration, technical content, configuration and
  emergency suspension remain distinct release authorities;
- production promotes the exact immutable verified artifact rather than rebuilding from source;
- every release binds reviewed source, declared dependency closure, workflow/builder inputs, exact artifact digest,
  provenance, SBOM, verification, approval, signature, compatibility, rollout and revocation context;
- an independent verifier and explicit trust-root matrix cover repository/workflow policy, builder/bootstrap, toolchain,
  registry/evidence, signer, promoter and deployment target;
- high-consequence human independence is mandatory; unavailable required roles produce a visible `HELD` release;
- artifact authenticity, release approval/provenance and current eligibility/revocation remain separate truths;
- one closed release-meaning graph binds client capability, API/schema, content/derived assets, configuration, migration,
  external resources, task-scoped offline recovery closure and release/suspension generations;
- effective feature/configuration values that can change meaning are controlled release inputs and cannot clear emergency suspension;
- migrations use explicit partial/recovery states and cannot use binary rollback to discard new valid data or revive revoked truth;
- every release/restore domain rechecks the current protected suspension/revocation generation;
- rollout stop does not imply downgrade of already updated clients; installed/offline revocation retains explicit residual risk;
- incident response maintains a protected impact graph across artifacts, deployments, cohorts, offline packages and configuration;
- no OTA/runtime code-update channel is approved by this decision.

Still unresolved and not approved by this decision:

- exact release consequence tiers, staffing/quorum and accountable owners;
- required provenance/SBOM/attestation formats, completeness thresholds and reproducible-build tiers;
- dependency source/license/vulnerability/EOL/exception rules and numeric response targets;
- CI runner, network, secret, builder, registry and evidence-custody implementation;
- signing/key hierarchy, store ownership/recovery, rotation/revocation and emergency ceremony;
- mobile support windows, rollout cohorts, mandatory-update/hold and dormant-client details;
- database destructive-change/data-loss/forward-recovery policy and numeric objectives;
- exact configuration/feature envelope and whether any future OTA channel will ever be allowed;
- source, CI, registry, signing, store, deployment, monitoring or cloud providers;
- final consumer mobile framework and other remaining Phase-4 topics.

No ADR is created. This decision is binding input to later Phase-5 ADRs; Gate 4 -> 5 remains closed.

---

## DEC-0028 — AI-Native Execution and Obsidian Project Graph Requirement
**Date:** 2026-09-17
**Status:** APPROVED PROJECT REQUIREMENT

The user explicitly required a project structure beyond ordinary file-level modularity:

> Her dosya/klasörün amacı ve bağlantıları Obsidian'da görülebilmeli; yeni bir AI bütün projeyi okumadan sıradaki
> `TASK-xxx` görevini projeyi bozmadan yapabilmeli; task planı kod yazılmadan simüle edilmeli; tüm task'lar bittiğinde
> ürün eksiksizliği ve farklı AI'ların tasarım tutarlılığı kanıtlanmalı.

Binding implications:

- project artifacts form an Obsidian-compatible, machine-verifiable relationship graph;
- architecture optimizes for small change surface, explicit ownership, narrow contracts and enforced dependencies,
  not arbitrary file fragmentation;
- every task carries a minimum sufficient context pack, allowed/forbidden scope, contracts, design references,
  acceptance/negative cases, validation and completion evidence;
- requirement-to-task-to-test traceability is bidirectional and orphan/gap detection is mandatory;
- task plans undergo no-code dependency, conflict, failure, rollback and closure simulation before development;
- `all tasks DONE` is insufficient without feature, flow, requirement, design, architecture, data, release, scenario and gap closure;
- multi-AI UI work is governed by one canonical design system and cross-screen/state visual validation;
- Phase 5–8 gates must implement and verify this system before feature development starts.

Canonical requirement:
`00_CONTROL/PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md`.

This decision does not authorize application code, choose a technology or advance a phase gate.

---

## DEC-0029 — AI-Operated Delivery / Nontechnical Product Owner Model
**Date:** 2026-09-17
**Status:** APPROVED PROJECT OPERATING MODEL

The user clarified:

> Tüm projeyi AI yapacak; bunun için planlama yapıyoruz. Benim kod ve teknik bilgilerle ilgim yok.

Binding implications:

- the user is the nontechnical product/decision owner, not a developer, debugger, architect or release engineer;
- planning, design production, code implementation, technical review preparation, testing, documentation and repository
  operation are designed for AI execution;
- technical choices must be translated into product outcome, risk, cost and reversibility rather than delegated to the
  user as unexplained technical decisions;
- framework/TCO evaluation uses AI-operability, deterministic tooling, bounded context/change surface, automatic
  validation, dependency/toolchain churn, observability and external-dependency load—not a fictional existing dev team;
- high-impact AI work requires separate implementer/reviewer/validation roles and evidence; AI output does not self-prove;
- AI cannot impersonate legal identity, store-account ownership, qualified safety/domain attestation or other genuinely
  human/organizational authority. Any unavoidable external action must be surfaced early and nontechnically;
- no task may rely on the user to repair code, resolve build failures or infer architecture.

This refines `DEC-0028` and DEBATE-006 team/TCO inputs. It does not select a framework, authorize code or advance a gate.

---

## DEC-0030 — Solo Ownership and Limited-Budget Constraint
**Date:** 2026-09-17
**Status:** CONFIRMED PROJECT CONSTRAINT

The user clarified that the project is personally owned by one 23-year-old founder with limited financial resources and
that cost decisions cannot be made without first seeing concrete cost categories and current prices.

Binding implications:

- no paid subscription, cloud plan, contractor, device purchase, legal service or recurring vendor cost may be silently assumed;
- every cost proposal separates mandatory, deferrable, optional and scale-triggered spending;
- current official price, billing period, tax/currency uncertainty, free-tier path, hard-cap/overage behavior and exit path
  must be explained in nontechnical language before user approval;
- architecture and framework TCO explicitly value free/local/open-source paths, deterministic spending, spend alerts and
  the ability to defer store/provider fees until needed;
- low initial cost cannot weaken safety, privacy, data continuity, accessibility or release evidence; if a mandatory
  assurance cannot be afforded, the affected release/capability remains `HELD` rather than silently reduced;
- exact monthly/annual spend ceiling remains open until the user receives a concrete staged cost plan.

Cost-card addendum (2026-09-23, OUT-3 B-36 — under DEC-0062 mandate; card facts, not new constraint):
- GitHub Pro (private-repo rulesets + Actions minutes): carded; amount/period per current official pricing at
  purchase time; weekly invoice-reading task T-E3-038 watches it with all other provider spend.

Current verified baseline on 2026-09-17:

- Apple Developer Program: USD 99 per membership year for App Store distribution
  (https://developer.apple.com/support/compare-memberships/);
- Google Play Console: USD 25 one-time registration fee
  (https://support.google.com/googleplay/android-developer/answer/6112435);
- if the app is published on both stores in the same first year, the arithmetic total is USD 124 before local
  tax/currency effects; this is not a joint package or a third membership;
- planning and the main development work can proceed without paying these store fees;
- the fees are deferred to release preparation, not necessarily the literal final publication day: a new Google Play
  personal account currently requires a closed test with at least 12 continuously opted-in testers for 14 days before
  production access, while paid Apple membership is required when App Store Connect/TestFlight distribution is needed;
- optional build/backend/monitoring/AI/device/legal/domain costs depend on later choices and must be separately budgeted.

User approval recorded on 2026-09-17:

- the Apple Developer Program and Google Play Console fees are accepted as mandatory release costs;
- payment remains deferred until each store's release-preparation/testing window requires it;
- this approval does not pre-approve unspecified subscriptions or future recurring costs, which remain subject to the
  staged-cost rule above.

This constraint does not select Android-first/iOS-first, a framework or a provider.

---

## DEC-0031 — Mobile Evaluation Method and Common Fixture
**Date:** 2026-09-17
**Status:** APPROVED PHASE-4 WORKING DIRECTION

The user approved the corrected DEBATE-006 common comparison fixture with:

> onaylıyorum

Binding implications:

- Flutter, React Native + Expo development builds, KMP-native, KMP-Compose and fully native receive the same S1–S15
  no-code scenario conditions and pass/hold/reject rules;
- the common release horizon, device/OS cohorts, network/interruption profiles, data/offline volumes, first-release
  capability boundary, scale workload, privacy, AI-operability and staged-cost fixture are frozen for comparison;
- proposed first-release scope is phone-focused; tablet/foldable optimization is not assumed;
- both stores remain planned without forcing a simultaneous launch;
- real-device, assistive-technology and qualified safety/content evidence cannot be replaced by simulator or AI claims;
- changing a fixture constant requires one recorded revision applied equally to every candidate;
- the common fixture does not approve a framework, provider, hosted build service, other paid subscription, application
  code, ADR or Gate 4 -> 5 transition.

Canonical fixture:
`04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md`.

---

## DEC-0032 — Android-First Staged Release and Owner Resource Envelope
**Date:** 2026-09-18
**Status:** APPROVED PHASE-4 WORKING DIRECTION

The owner confirmed that an Android phone is directly available, iPhones can be borrowed from close friends for testing,
simultaneous Android/iOS publication is not required, and a future non-store operating envelope of approximately
TRY 2,000–3,000 per month may be available when spending actually begins.

The owner authorized the manager to choose the suitable publication order. The selected working direction is:

- publish and stabilize Android first;
- prepare iOS as a later second release rather than forcing a simultaneous two-store launch;
- use the owner's Android device as the directly controlled first real-device path;
- use borrowed iPhones as supplementary real-device test access where practical, without treating informal access as a
  permanent release dependency;
- defer Apple membership and any hosted Mac/build expense until the iOS preparation window actually requires them.

Financial meaning:

- TRY 2,000–3,000/month is a planning ceiling for a later spending phase, not immediate purchase authorization and not a
  requirement to spend the full amount;
- each recurring service still needs its current official price, tax/currency exposure, free/capped route, hard limit,
  credential/data handling and exit path explained before approval;
- store fees remain governed by `DEC-0030` and sit outside this newly stated non-store monthly planning envelope unless a
  later budget sheet explicitly combines them.

Resource limits still open:

- no owned or reliably accessible Mac has yet been confirmed;
- a hosted Mac/build service is only a future option, not an approved provider or subscription;
- borrowed iPhone availability, supported OS/device coverage and test scheduling must be made explicit before iOS release;
- final 12–24 month spend allocation remains subject to a staged cost plan.

Rationale: Android-first minimizes immediate external dependencies and lets the first release cycle use hardware the owner
controls. It does not remove iOS from scope, select Flutter versus React Native/Expo, authorize code, approve a provider or
advance Gate 4 -> 5.

---

## DEC-0033 — Flutter Consumer-Mobile Working Direction
**Date:** 2026-09-18
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After the complete DEBATE-006 no-code comparison, the manager recommended Flutter and the user explicitly approved:

> flutter ı onaylıyorum

Binding direction:

- Flutter is the consumer-mobile framework direction carried into later architecture and delivery planning;
- Android remains the first publication lane and iOS the later second lane under `DEC-0032`;
- React Native + Expo development builds remains the first documented fallback, not an automatically activated second
  implementation;
- KMP-Compose remains an expertise-conditional challenger; KMP-native and full native remain reference baselines;
- portable product, data, safety, provenance and release truth must remain outside framework-bound presentation code;
- Flutter tasks must explicitly close package/plugin, generated registrant, platform-channel, Android Runner/Gradle and
  iOS Runner/Xcode/SwiftPM-or-CocoaPods effects through the AI-native task/evidence graph;
- the owner cannot be required to debug code, native builds, signing or toolchain failures.

Mandatory reversal/review triggers:

- an essential capability requires an unmaintained or unsafe plugin with no controlled native fallback;
- native/generated state cannot be reproduced, attributed, reviewed or exported;
- Android or later iOS requires a non-exportable provider dependency or an uncapped/unapproved recurring cost;
- Flutter cannot satisfy the same real-device lifecycle, offline, recovery, accessibility, safety, signing and store
  evidence gates without weakening approved product requirements;
- implementation would require technical repair by the nontechnical owner;
- RN/Expo or another retained baseline later closes a mandatory requirement that Flutter cannot close safely.

If a trigger occurs, the project records evidence and reopens the framework decision; it does not silently switch stacks.

This approval selects the Phase-4 working framework direction only. It does not authorize application code, create a
Phase-5 ADR, approve a hosted Mac/build provider or subscription, claim build/device/release readiness, enable OTA, or
advance Gate 4 -> 5. Those remain controlled by their later gates and explicit approvals.

---

## DEC-0034 — Data Backbone and Logical Service-Boundary Direction
**Date:** 2026-09-18
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After repository synthesis, official/primary research, controlled intake of the user's external research, two independent
Luna Max reviews and corrected Judge synthesis, the user approved the DEBATE-007 direction:

> onaylıyorum

Binding direction:

- each data domain has a canonical transactional authority and stable identity/version/generation contracts; this does
  not require one physical database or premature microservices;
- Flutter and the browser-based Internal Operations client use server/API-mediated sensitive access and cannot hold
  general canonical database or object-storage authority;
- Internal Operations review, approval, publication, recall/suspension and role/policy actions remain online-authoritative;
- Flutter receives bounded, versioned, integrity-bound motorcycle/task offline packages with complete compact
  safety/application/safe-stop/recovery closure; no full-library default download;
- local user work uses durable identified operations, idempotent submission, visible conflict/hold/unknown results and
  explicit reconciliation; high-consequence data cannot use silent last-write-wins;
- current state, domain history/provenance and protected audit are distinct meanings;
- media/files use a separate logical object boundary with classification, lineage, digest/version, quarantine and
  controlled access; derivation, scan or AI/OCR never grants technical correctness or publication authority;
- projections, search, analytics, cache, notifications and package builders are rebuildable non-authoritative copies;
- restore, failover and migration must use a protected non-restorable release/security/deletion/operation floor so old
  backups cannot resurrect revoked authority, recalled content, deleted private data or accepted operations;
- backup, restore, export and provider exit require cross-plane consistency manifests, quarantine, reconciliation and
  clean-environment import evidence—not merely a successful job or file;
- provider/account/billing/region failure, spending controls and bounded AI operations are first-class states; the owner
  is not required to debug, administer databases, use SSH or repair incidents.

Technology boundary:

- no database engine, BaaS, API runtime, local Flutter storage library, object store, identity service, cloud/provider,
  backup tool, paid plan or numeric RPO/RTO is selected;
- relational/PostgreSQL, managed service, self-hosted/open-source and viable counterfactuals remain later equal-comparison
  candidates against the approved safety, recovery, cost, exit and AI-operability gates;
- the external research report's unsupported percentages, Flutter-Web assumption, fixed thresholds and categorical
  technology/provider conclusions are not project decisions.

This approval is a Phase-5 ADR input. It authorizes no code, prototype, purchase, subscription or Gate 4 -> 5 transition.

---

## DEC-0035 — Supabase-Centered Physical Backend Working Direction
**Date:** 2026-09-18
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After current official research, controlled audit of the user's external backend report, equal finalist dossiers,
comparison-equivalence normalization, two independent Luna Max reviews and manager synthesis, the user approved:

> tamamdır onaylıyorum

Binding direction:

- Kavriva continues Phase-4 planning with a managed Supabase-centered physical backend direction;
- managed Supabase PostgreSQL, Auth and private Storage are the initial core candidates;
- Flutter and browser Internal Operations do not receive general canonical database or object authority;
- sensitive access and every high-consequence mutation remain behind the approved Kavriva server/API authority boundary;
- Supabase Edge Functions or an equivalently bounded server runtime is the initial low-operations API candidate, but the
  exact runtime remains replaceable until the Phase-5 ADR;
- RLS and Storage policies are mandatory defense in depth, never the sole approval, publication, recall, provenance,
  protected-audit or separation-of-duties authority;
- `service_role`/secret keys remain server-only and cannot enter Flutter/browser bundles, repositories, logs or ordinary
  AI task contexts;
- Supabase Studio is provider administration, not the Kavriva browser-based Internal Operations product surface;
- database backup does not cover Storage object bytes; object backup/export, protected audit and the non-restorable
  negative/deletion/accepted-operation floor require sufficiently independent custody and cross-plane recovery evidence;
- bounded offline, anti-resurrection, quarantine, clean-room exit, provider/billing hold and no-owner-debug controls from
  `DEC-0034` remain binding;
- Neon managed PostgreSQL + independent API + Cloudflare R2 remains the first documented fallback, not an automatic
  parallel implementation or approved provider purchase.

Mandatory reversal/review triggers:

- sensitive/high-consequence operations cannot remain behind the API boundary;
- minimum-safe API, independent audit/floor, object backup, monitoring and recovery costs exceed the later approved budget;
- privileged bypass paths cannot be bounded and negatively tested;
- old restore can resurrect recall, revoke, deletion, suspension or accepted operations;
- cross-plane restore or clean-room exit cannot preserve required negative behavior and stable truth;
- outage, billing restriction or incident recovery requires owner SQL, SSH, log diagnosis or technical repair;
- Supabase-specific coupling creates materially worse safe exit than the retained modular fallback.

Financial and implementation boundary:

- the current Supabase Pro headline is a planning signal, not the total safe recurring cost or a purchase approval;
- PITR and every paid adjunct remain unapproved until a current staged bill of materials is presented;
- the owner's TRY 2,000–3,000/month amount remains a later planning ceiling under `DEC-0032`, not immediate spend authority;
- no provider account, region, plan, subscription, purchase, code, prototype, production proof, Phase-5 ADR or Gate 4 -> 5
  transition is authorized by this decision.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-008__MANAGER_SYNTHESIS.md`.

---

## DEC-0036 — Flutter Local Data, Complete Offline Package and Durable Operation Direction
**Date:** 2026-09-18
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After repository requirements synthesis, current official/primary research, mobile-platform failure analysis, equal
Drift/custom and PowerSync dossiers, one equal no-code AI task simulation, equivalence audit, two independent Luna Max
reviews and corrected Judge synthesis, the user approved:

> onaylıyorum

Binding direction:

- SQLite through Drift is the Flutter local-persistence working direction; Drift is not treated as a complete sync,
  encryption, recall, conflict, background or server-acceptance solution;
- the first-release offline-content baseline is one immutable, complete compact package for the selected motorcycle/task,
  with manifest, generation, compatibility, digest and complete safety/application/safe-stop/recovery closure;
- optional high-volume media remains separate, explicit, cancelable and evictable; the unrelated catalog is not downloaded
  by default;
- complex delta sync is deferred until measured data savings justify it and exact-base, ordering, digest, dependency,
  atomic-apply and complete-package fallback evidence exists;
- user history, notes, evidence metadata, pending uploads and account-light work use a separate durable app-owned operation
  ledger with stable identity, payload fingerprint, expected version/generation and explicit pending/submitted/accepted/
  conflict/held/failed/outcome-unknown/reconciling states;
- all server submission and status lookup goes through the Kavriva API boundary; local persistence, HTTP success, queue
  empty, Drift transaction, Realtime event or push receipt never alone means canonical acceptance, freshness or recall;
- Supabase Realtime/push may prompt a foreground/API recheck but is not durable offline sync or negative-authority proof;
- process death, background limits, storage pressure, restore, device clock and migration must preserve the last valid
  package and durable operation truth without depending on lifecycle callbacks;
- restored/device-migrated data enters reconciliation quarantine and cannot resurrect recall, revoke, deletion,
  suspension or an already accepted operation;
- local encryption and key custody remain a separate held decision; plaintext fallback is prohibited;
- PowerSync is the first re-evaluation candidate, not an approved service or automatic fallback.

Comparison fixture:

- 12 MB compact transfer, optional media up to 150 MB, confirmation above 25 MB and 250 MB re-fetchable content cache
  remain equal-evaluation values under `DEC-0031`, not final product/commercial limits;
- required safety/recovery closure cannot be removed merely to fit a fixture number.

Mandatory reversal/review triggers:

- the bounded package/operation protocol cannot be decomposed into independently reviewable AI tasks;
- complete packages cannot remain sufficiently data-efficient under measured workload;
- duplicate, response-loss, conflict, delete, recall, restore or anti-resurrection behavior remains ambiguous;
- Drift migration, encryption/native dependency or later iOS parity requires owner debugging;
- operations require SQL, queue surgery, cursor repair or technical intervention by the owner;
- equal total-cost evidence shows a safer retained alternative within the approved budget;
- clean-room export/import cannot preserve package generations, pending operations, conflicts and tombstones.

Decision boundary:

- no code, schema, database file, library/plugin version, SQLCipher/encryption mechanism, PowerSync account/plan,
  subscription, purchase, production proof, Phase-5 ADR or Gate 4 -> 5 transition is authorized;
- all 36 documentary scenarios remain `HELD` until later implementation/device/restore/accessibility/exit evidence.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-009__JUDGE_SYNTHESIS.md`.

---

## DEC-0037 — Consumer Identity, Account-Light Migration and Privileged Access Activation Direction
**Date:** 2026-09-19
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After repository-derived requirements, current official provider research, 15 identity/session/recovery threat scenarios,
a manager proposal, two independent Luna Max adversarial reviews and the corrected Judge synthesis, the user approved:

> onaylıyorum

Binding direction:

- Supabase Auth is the conditional Phase-4 working direction for consumer profiles because it fits the approved
  Supabase-centered backend and Flutter direction with the fewest initial control planes;
- account-light first value begins with a Kavriva local installation/device principal; a server anonymous account is not
  created by default merely to simulate account-light use;
- local-to-profile migration is a distinct Kavriva product operation with verified source possession, fresh target
  reauthentication, visible scope/classification preview, stable operation identity, conflict hold, immutable mapping,
  target reconciliation and split/rollback; provider identity linking never silently merges product history or ownership;
- provider identity, Kavriva product principal, session, role/grant/delegation, competence/independence, workload/AI
  identity, provider/legal/billing owner and historical audit actor remain distinct;
- authentication never grants product authority by itself. Sensitive access and every high-consequence mutation remain
  behind current server/API authorization over exact actor/session/issuer, security epoch, action, resource/tenant/scope,
  classification, grant, competence, independence, policy, object version/generation and operation identity;
- provider-specific token/session/factor/redirect/linking/logout/key-rotation/recovery behavior remains in an explicit
  adapter boundary; cached claims, `user_metadata`, browser state, provider roles and RLS are not sole authority;
- privileged Internal Operations has no provider winner. One Supabase Auth composition remains the simpler candidate;
  an external internal-only IdP remains a challenger if Supabase cannot meet the privileged activation gate;
- passkey, `aal2`, beta/GA/stable labels or a successful login do not satisfy the activation gate alone. Privileged
  production requires phishing-resistant, user-verified and transaction-bound step-up plus factor-loss, recovery,
  stolen-token, logout-all, browser-origin/PKCE/CSRF, accessibility, outage and key-rotation evidence;
- TOTP, SMS or magic link cannot be substituted for the approved phishing-resistant privileged requirement;
- security-epoch revocation must cover current sessions, grants/policy/competence generations, pending/in-flight
  operations, lost-response retries, private object handles, browser caches and classified local packages. Downloaded
  copies cannot be remotely retracted and must be treated honestly;
- privileged account recovery and emergency negative authority are separate state machines. Recovery cannot approve,
  publish or grant roles; the negative path can only suspend/recall/quarantine/deny and cannot create positive truth;
- a real independent human/organization, support/recovery path and custody are explicit external dependencies. Until
  the solo-owner project can satisfy this and last-admin evidence, high-consequence privileged production remains `HELD`;
- Auth/provider logs do not replace protected Kavriva product audit. Required audit evidence must exist before effect or
  through equivalent transactional assurance; missing normal/fallback custody holds the positive action;
- if two identity issuers are later used, issuer-qualified immutable subject mapping, allowlisted issuer/audience/key
  policy, one Kavriva security epoch and tested cross-issuer revoke/logout are mandatory;
- AI identities remain task-scoped and cannot receive provider owner, billing-root, `service_role`, unrestricted SQL/SSH,
  recovery, approval or publication authority; the nontechnical owner is not the repair/debug mechanism.

Financial and activation boundary:

- no headline provider price is accepted as total safe cost. Before purchase, both candidates require the same normalized
  bill of materials for Auth plan/MAU-MRU, API runtime, SMTP/domain/DNS, optional SMS, protected audit/fallback/logging,
  object backup/restore, monitoring, support, incident recovery, tax/FX and clean-room exit;
- TRY 2,000–3,000/month remains a later planning ceiling, not current purchase authorization;
- if mandatory assurance does not fit the approved budget, the affected privileged capability remains `HELD`; security
  cannot be weakened to make the budget fit;
- Android-first identity/deep-link/recovery evidence does not automatically prove iOS parity; iOS remains a later
  separate evidence gate.

Decision boundary:

- no Supabase/Auth0/Clerk account, project, region, plan, subscription, purchase, SMTP/SMS service, passkey
  implementation, exact factor, session duration, second recovery actor, code, prototype, Phase-5 ADR or Gate 4 -> 5
  transition is authorized;
- both privileged composition candidates remain documentary `0 PASS / 15 HELD / 0 REJECT` until later implementation,
  device/browser, recovery, audit, outage, cost and clean-room-exit evidence.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-010__JUDGE_SYNTHESIS.md`.

---

## DEC-0038 — Kavriva API Runtime, Durable Work and Operations Direction
**Date:** 2026-09-19
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After repository-derived API/runtime requirements, current official-source research, 18 failure/TCO scenarios, a
manager proposal, two independent Luna Max adversarial reviews and the corrected Judge synthesis, the user approved:

> onaylıyorum

Binding direction:

- Flutter, browser Internal Operations and provider consoles do not receive direct high-consequence canonical database,
  object, publication, export or recovery authority; these flows remain behind the provider-neutral Kavriva API;
- API runtimes are replaceable ingress/decision/effect-protocol workers, not the persistent owner of product truth;
- short DB-near command/status/read requests may continue with Supabase Edge Functions as the reversible Phase-4 first
  working hypothesis; this is not a production winner, account, plan or runtime ADR;
- managed container API + bounded worker remains the equal-evidence alternative hypothesis, not an automatic fallback;
  A failing does not make B safe without the same complete evidence package;
- every sensitive effect is reauthorized at commit time over current actor/workload, issuer/session assurance, security
  epoch, action, exact resource/tenant/scope/classification, grant/delegation, competence/independence, policy, object/
  release/schema/config/package generation, current negative floors, operation identity and audit readiness;
- operation identity is bound to actor/tenant/action/resource/scope/classification and immutable payload fingerprint;
  same semantic retry reads the existing result, different payload/scope/actor becomes `CONFLICT/HELD`, and lost response
  stays `OUTCOME_UNKNOWN` until canonical status lookup resolves it;
- the authoritative DB core binds immutable operation acceptance, current authorization/generation fence, canonical DB
  transition, protected audit precondition/receipt reference, deterministic outbox/effect intent and reconciliation state;
  this does not pretend object, queue, notification, scanner or external-provider effects are physically atomic;
- protected audit intent or platform logs alone are insufficient. High-consequence positive effect requires a protected
  audit event/receipt through normal or sufficiently independent fallback custody; otherwise it remains `AUDIT_HELD`;
- known long-job families—package build, object scan/preview/derivative, large export/import, AI/OCR, notification and
  broad reconciliation—are subject to a durable queue/worker capability gate before activation. Background callbacks or
  `waitUntil` do not count as a durable queue;
- long jobs require deterministic effect identity, lease/heartbeat/checkpoint, bounded retry, DLQ/quarantine, poison and
  backpressure handling, deploy drain/message compatibility, owner-visible backlog and canonical reconciliation;
- newer recall/suspension/revoke/delete/object/package/accepted-operation/migration floors take precedence over older or
  in-flight positive effects. Missing/unknown/tied state holds; old restore, runtime, queue message, handle or cache cannot
  clear a newer negative generation;
- security epoch revocation extends through pending/in-flight operations, status retry, worker leases, object handles,
  browser caches/service workers, Flutter packages/ledgers and local key state. Downloaded copies cannot be remotely
  guaranteed to disappear and this limitation is represented honestly;
- privileged account recovery and emergency negative authority remain separate. The negative path can only suspend,
  recall, quarantine or deny; exact technology is open but failure-domain, minimum evidence and anti-resurrection
  semantics are mandatory now;
- all clients and operator surfaces share an explicit state dictionary including `ACCEPTED`, `QUEUED/SUBMITTED`,
  `DENIED`, `HELD`, `OUTCOME_UNKNOWN`, `PARTIAL/RECONCILING`, `AUDIT_HELD`, `BILLING_HELD`, `ACCOUNT_HELD`,
  `DEPLOYMENT_HELD`, `OBJECT_QUARANTINE`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`, `SERVICE_UNAVAILABLE` and
  `RECOVERY_REQUIRED`; HTTP 2xx, green dashboard, worker completion or empty queue does not override product state;
- direct Data API/RPC/view/function/Storage/signed URL/provider-console paths must be inventoried and negatively tested;
  RLS/Storage remain defense in depth and `service_role`, provider owner, billing root or unrestricted SQL/SSH cannot
  enter clients, repositories, logs or ordinary AI task contexts;
- owner/support/account, provider outage, billing/quota stop, no-owner-debug, AI task scope, cross-plane restore,
  anti-resurrection and source-untouched clean-room exit are activation hard gates.

Equal evidence and cost boundary:

- both runtime hypotheses use the same route/workload classes, fault injection, product-state expectations, protected
  audit evidence, recovery owner/next action and cost/exit impact;
- both require a normalized safe-cost BOM covering shared DB/Auth/private Storage, runtime, transaction/network,
  queue/worker, protected audit/floor, observability, object safety/backup, deploy/schema/message compatibility, secrets,
  provider account/support, DNS/TLS/notifications, incident capacity, restore, clean-room exit, external recovery people
  and AI task operations;
- every cost line is classified `mandatory / deferrable / optional / scale-triggered` with current plan/region/unit,
  quota/overage, cap coverage, stop state, tax/FX and incident/restore/exit effects;
- TRY 2,000–3,000/month remains a later planning ceiling, not current purchase authorization. Mandatory assurance that
  does not fit remains `BILLING_HELD/HELD`; the security or recovery standard is not weakened;
- the nontechnical owner gives plain-language approve/hold/stop/payment/legal-support decisions but is not asked to run
  SQL/SSH, diagnose raw logs, repair queues, rotate raw secrets or execute provider-console recovery;
- AI tasks remain narrowly scoped with short-lived credentials, forbidden operations, hard stops, evidence and an
  independent reviewer/validator. AI cannot impersonate the legally/accountably independent recovery, audit or
  emergency-negative human/organization.

Reversal/review triggers:

- Edge memory/CPU/wall-clock/bundle/runtime or transaction-pooler behavior cannot safely carry required short requests;
- required queue/worker/audit/observability adjuncts make Edge materially less safe, operable or affordable than an
  equally evidenced managed-container composition;
- Supabase common failure domain prevents protected audit/floor, emergency-negative, recovery or owner-readable hold;
- deployment, secret rotation, old-revision drain or schema/message compatibility cannot be bounded;
- direct provider bypass, blind duplicate, stale authorization, effect-before-audit, quarantine bypass or restore
  resurrection appears in negative evidence;
- normal + incident + restore + exit BOM exceeds the later approved budget or lacks a safe spend stop;
- clean-room replacement loses principal/policy, operation, queue, object lineage, package, audit/floor or negative state;
- any recovery path requires owner SQL, SSH, queue surgery or unexplained technical repair.

Decision boundary:

- both runtime hypotheses remain documentary `0 PASS / 16 HELD / 0 REJECT` and no production runtime winner exists;
- no runtime language/framework, queue/worker, protected audit product, region, provider plan, account, subscription,
  purchase, code, prototype, deployment, production activation, Phase-5 ADR or Gate 4 -> 5 transition is authorized;
- Cloudflare Workers, Cloud Run and self-managed/reference paths remain challengers/references, not selected services.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-011__JUDGE_SYNTHESIS.md`.

---

## DEC-0039 — Internal Operations Web Frontend and Hosting Direction
**Date:** 2026-09-19
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After framework-neutral requirements, current official-primary research, failure/TCO analysis, an initial manager
proposal, two independent Luna Max adversarial reviews, common no-code task simulation, four-family equivalence audit,
component-ecosystem tie-break, render/hosting tie-break and corrected Judge synthesis, the user approved:

> onaylandı

Binding direction:

- Internal Operations remains a browser-based, desktop-class authenticated workspace;
- public SEO is not a requirement for this internal surface;
- the conditional simplest starting render/hosting direction is CSR-first static artifact/CDN + Kavriva API;
- browser, static host, CDN, framework server, BFF, cache, service worker and provider console are not canonical product
  authority; all sensitive data and effects remain mediated and reauthorized by the Kavriva API;
- same-origin server shell/BFF, managed serverless/edge SSR and managed/portable Node container are need-specific held
  alternatives, not defaults or automatic fallbacks;
- privileged/authenticated offline service-worker behavior is not a default and cannot carry mutation, role, protected
  audit, recalled data or canonical operation-status authority;
- React/Next, Angular, Vue/Nuxt and Svelte/SvelteKit remain equal `HELD` candidates with no Phase-4 winner. Popularity,
  AI familiarity, component count or a framework support label is not selection evidence;
- framework selection requires the same Phase-5 evidence pack: exact dependency/SBOM/license/support closure, dense
  queue/table/diff/graph behavior, real browser/assistive-technology acceptance, session/security and lost-outcome
  fixtures, quarantine, upgrade/release compatibility, AI task/design consistency, normalized TCO and source-untouched
  clean-room exit;
- the Phase-3 workspace architecture, shared state vocabulary, design token/component contract, accessibility oracles,
  task ownership/traceability and visual plus semantic regression evidence must constrain every later AI web task;
- no-owner-debug remains binding: the nontechnical owner is not asked to repair SQL, SSH, raw logs, queues, caches,
  secrets, DNS/TLS or provider consoles.

Decision boundary:

- this is a reversible Phase-4 working direction, not proof that the static pattern or any framework is production-ready;
- if session/CORS/CSRF/XSS/CSP, stale state, outcome reconciliation, quarantine, accessibility, deployment compatibility,
  support/cost or clean-room exit cannot be closed, the affected capability remains `HELD`; another mode/framework does
  not automatically win;
- no framework, exact version, component library, hosting provider, domain, region, plan, account, subscription,
  purchase, code, prototype, deployment, production activation, Phase-5 ADR or Gate 4 -> 5 transition is authorized.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-012__JUDGE_SYNTHESIS.md`.

---

## DEC-0040 — External AI Work Uses Google Drive + GitHub, Not the User's Computer
**Date:** 2026-09-19
**Status:** USER-DIRECTED OPERATING DECISION

The user directed that external AI work replace unnecessary sub-agent usage where practical and clarified:

> ai ların githuba ve drive abağlantısıda olcak ama bilgisayarıma erişim olmıyacak

Binding direction:

- external AI workers use Google Drive for task/context/research/review/decision/handoff artifacts and GitHub for
  repository-native work;
- they do not receive or depend on access to the user's computer, local workspace, desktop, terminal, open applications
  or unshared local files;
- every assignment is a unique `TASK-XXX` execution contract with explicit scope, forbidden scope, minimum context,
  repository/branch/path boundary, deliverables, acceptance checks, evidence, reviewer and block conditions;
- task state is represented by Drive queue folders from READY through CLAIMED, IN_PROGRESS, REVIEW,
  CHANGES_REQUESTED, BLOCKED, DONE and CANCELLED;
- an implementer cannot self-approve. Independent review is required before DONE;
- local-only truth must be migrated to Drive or GitHub before an external task depending on it can become READY;
- missing access, conflicting authority or an unlisted decision produces BLOCKED and an owner-readable question, not
  guessed work;
- merge, release, deployment, account creation, payment, deletion or scope expansion remains separately authorized.

The active Drive workspace and exact links are registered in
`00_CONTROL/EXTERNAL_AI_DRIVE_GITHUB_WORKFLOW.md`.

---

## DEC-0041 — Parallel Independent External-AI Work Is Allowed
**Date:** 2026-09-19
**Status:** USER-DIRECTED OPERATING DECISION

The user clarified:

> aynı şeyi birden fazla ai a göndermen problem değil istediğin kadar ai çalıştırabiliriz ama aynı anda birden fazla ai a prompt atabilirim unutma bunu

Binding direction:

- the same research, critique or review brief may be sent to multiple external AI systems at the same time;
- simultaneous outputs are treated as independent evidence, not as duplicate votes or automatic consensus;
- each worker receives the same canonical task/context version and produces a separately identified output/review;
- external workers must not concurrently overwrite the same Drive document or GitHub path; use distinct reviewer/output
  identifiers and let the manager synthesize differences afterward;
- disagreement, unique findings and shared blind spots are preserved explicitly; majority agreement alone does not
  approve a decision or close a task;
- task closure still requires the stated acceptance checks, review authority and user approval where required.

Boundary:

- this permission applies to external AIs that the user prompts through the Drive/GitHub workflow;
- it does not change `DEC-0022`: Codex sub-agent models other than Luna Max still require explicit user permission.

---

## DEC-0042 — Kavriva-Owned Technical Content Authority / CMS as Optional Authoring Adjunct
**Date:** 2026-09-19
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After TASK-001 research, REVIEW-001 remediation and independent REVIEW-002 PASS, the user approved the manager direction:

> onaylıyorum

Binding direction:

- Kavriva retains source/evidence/claim relationships, applicability, technical truth, human approval, immutable release
  identity, recall/suspension generation, mobile-package eligibility and final publication authority;
- a headless CMS may later be evaluated only as a bounded, replaceable authoring convenience;
- CMS publish, provider console, webhook, direct database action, cache/CDN state or provider restore cannot create
  Kavriva-approved technical live state;
- any CMS candidate must pass provider-bypass, failure/reconciliation, safe TCO, owner-operability and source-untouched
  clean-room replacement evidence;
- no CMS is required for first release merely because it offers editorial convenience.

Decision boundary:

- no CMS product/provider, account, plan, trial, purchase, schema, code, deployment, Phase-5 ADR or Gate 4 -> 5 transition is approved;
- Directus, Strapi, Contentful, Sanity and product-owned workflow remain reference mechanisms, not winners.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-013__MANAGER_SYNTHESIS.md`.

---

## DEC-0043 — GitHub Is the Canonical Cross-Manager Continuity Package
**Date:** 2026-09-19
**Status:** USER-DIRECTED OPERATING DECISION

The user directed that future manager AIs must continue completely from GitHub even when the main chat changes.

Binding direction:

- `xpike-dgm/motobakim-plan` is the persistent planning and manager-memory repository;
- `/AGENTS.md` and `00_CONTROL/MANAGER_START_HERE.md` are the canonical new-manager entrypoints;
- `00_CONTROL/NEXT_ACTION.md` is the single volatile next-work pointer and must be refreshed at every material handoff;
- Drive-only research/review/task evidence is indexed by `00_CONTROL/DRIVE_ARTIFACT_INDEX.md`;
- volatile current state must not be copied into many prompts/handoffs; compatibility files point to the canonical package;
- every material manager cycle ends with memory refresh, consistency checks and an authorized Git checkpoint/push;
- a new manager reconstructs context from GitHub + Drive and does not require access to the owner's computer or old chat.

This decision organizes planning truth; it does not authorize application code or advance Gate 4 -> 5.

---

## DEC-0044 — Analytics / Measurement Split-Boundary Working Direction
**Date:** 2026-09-19
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After TASK-002 official-primary research, REVIEW-003 remediation and independent REVIEW-004 PASS, the user explicitly
approved the DEBATE-014 manager synthesis.

Binding direction:

- measurement remains an observation layer, never technical truth, human approval, proof of repair/safety completion,
  entitlement authority, recall/suspension authority, canonical product state or protected audit evidence;
- Kavriva-owned canonical operational coverage/data-quality metrics derive from canonical records rather than consumer
  telemetry;
- protected privileged-action audit/security evidence remains outside analytics;
- product analytics, when used, stays purpose-limited, minimized, anonymous/account-light by default, non-authoritative
  and replaceable;
- analytics consent denial, SDK/provider outage, quota/billing hold, late upload or telemetry deletion cannot disable
  the safe core path or critical negative-safety/recall behavior;
- reliability/crash/performance observability remains a separate plane and should stay provider-neutral where feasible;
- store/platform vitals remain supporting signals only;
- the split/hybrid boundary is the approved reversible Phase-4 architecture shape: Kavriva-owned operational metrics +
  replaceable product analytics + separable observability;
- if dedicated product analytics cannot meet privacy, owner-operability, safe-TCO, offline and clean-room-exit evidence
  gates, first release falls back to the smaller Kavriva-owned measurement baseline rather than weakening those gates;
- raw export alone is not clean-exit proof. Cross-provider identity/deletion-state fidelity, derived-object fidelity,
  late-arrival handling and mobile-instrumentation portability remain HELD until separately proven.

First-release capability direction:

- mandatory at direction level: plane separation, canonical-record-derived Internal Operations coverage/data-quality
  visibility, minimal purpose-limited product usage measurement where permitted/useful, crash/ANR/performance supporting
  signals, consent/opt-out enforcement, telemetry-health visibility, old-client semantic compatibility,
  retention/delete/export path and outage independence;
- identified analytics profiles, anonymous-to-profile history merge, cross-device identity, advanced funnels/cohorts,
  warehouse streaming and rich segmentation are deferrable;
- session replay, heatmaps, broad autocapture, surveys and detailed device/location enrichment are optional and require
  separate purpose/privacy justification;
- dedicated collector tiers, warehouse/lake export, long raw retention, advanced sampling/cardinality controls,
  multi-region analytics, paid SLA/support and automated spend controls are scale-triggered.

Decision boundary:

- no analytics/product-observability provider winner is selected;
- no provider account, region, plan, trial, purchase, payment or deployment is approved;
- no event schema, SDK integration, code, prototype or executable spike is approved;
- no final KPI target or jurisdiction-specific legal/privacy conclusion is approved;
- no Phase-5 ADR or Gate 4 -> 5 transition is approved.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-014__MANAGER_SYNTHESIS.md`.

---

## DEC-0045 — Android-First Split/Hybrid Mobile Build and Release Working Direction
**Date:** 2026-09-19
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After TASK-003 official-primary research, REVIEW-005 remediation and independent REVIEW-006 PASS, the user explicitly
approved the DEBATE-015 manager synthesis.

Binding direction:

- Android release continuity remains active and independent of iOS/macOS readiness;
- borrowed iPhone access remains physical-device validation only and does not count as Mac/Xcode build access;
- the approved Phase-4 architecture shape is split/hybrid: Android stays on a low-cost, replaceable build/release lane,
  while iOS/macOS capacity is activated only when needed and remains separable from the Android lane;
- iOS activation remains HELD until all of the following are separately proven:
  - real Kavriva Mac/Xcode execution access;
  - Apple signing certificate/profile/private-key custody, rotation/revocation/recovery and App Store Connect role boundaries;
  - provider-neutral artifact provenance bound to canonical source/build/version/digest;
  - no-owner-debug routine and incident recovery;
  - clean-room rebuild/provider replacement without copying opaque provider state;
- canonical source remains outside the build/CI provider;
- build success does not equal release approval;
- Android signing/upload-key custody and Google Play authority remain separate from CI execution;
- future Apple signing/store authority remains separate from CI execution;
- machine-readable build status, technical recovery ownership, spend/quota/billing visibility, safe hold and provider-exit
  evidence are mandatory operating requirements;
- the nontechnical owner handles only explicit business/payment/identity approvals and plain-language go/no-go decisions,
  not terminal/raw-log/Xcode/Gradle/CI-config/signing/SSH/cache debugging;
- fixed Mac, hosted-Mac or paid macOS capacity should not be committed before iOS activation gates require and justify it;
- the TRY 2,000–3,000/month non-store figure remains planning context only and is not purchase authority.

First-release capability direction:

- mandatory for Android: Android continuity independent of iOS, canonical source outside provider, signing/Play authority
  separation, artifact provenance, explicit release approval, machine-readable status and technical recovery ownership,
  least-privilege secret handling, spend/quota/billing safe hold, and exportable artifact/evidence plus exit runbook;
- deferrable until iOS activation: real Mac/Xcode execution, Apple signing/App Store Connect setup, any Xcode Cloud bootstrap,
  borrowed-iPhone validation and iOS-specific store transport;
- provider-managed signing, long provider retention, extra concurrency and provider AI/debug summaries remain optional and
  require separate evidence;
- paid Xcode Cloud compute, extra concurrency, annual/unlimited plans, dedicated Mac/host capacity, enterprise support/SLA
  and a warm secondary provider are scale-triggered rather than current recommendations.

Decision boundary:

- no physical Mac purchase, hosted Mac, general CI, mobile CI or Xcode Cloud provider/plan winner is selected;
- no provider/store account, trial, purchase, payment or store submission is approved;
- no build, signing setup, certificate/profile/key creation, CI configuration, code, prototype or executable spike is approved;
- no final budget commitment is approved;
- no Phase-5 ADR or Gate 4 -> 5 transition is approved.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-015__MANAGER_SYNTHESIS.md`.

---

## DEC-0046 — AI / LLM Assistance, Decision-Layer and Jev Optionality Working Direction
**Date:** 2026-09-20
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After TASK-004 core AI/LLM/provider research, REVIEW-007/008 remediation, REVIEW-009 PASS, the Jev-specific TASK-005
addendum and independent REVIEW-010 PASS, the user explicitly approved the final DEBATE-016 manager synthesis.

Binding direction:

- Kavriva uses AI as bounded assistance, not as canonical technical truth, motorcycle fit/readiness/safety authority,
  publication/recall authority, privileged authorization, protected-audit truth, release/signing/deployment approval,
  legal/privacy authority, billing/purchase authority or high-impact self-review authority;
- the default conversational AI path should use the **cheapest/fastest model that is adequate for the task**;
- the conversational AI may understand free text, ask clarification questions and collect observable evidence;
- a Kavriva-owned, provider/model-neutral decision/routing boundary may propose a route, guide family or other bounded
  candidate from controlled options;
- Kavriva deterministic/canonical systems perform the final eligibility, source/provenance, motorcycle-context,
  readiness/safety and authorization checks before critical results are used;
- ambiguity, insufficient evidence, high-risk inputs or material model/provider divergence safe-hold rather than
  inventing certainty or automatically accepting a fallback answer;
- stronger/more expensive models may be used only when an allowed task actually requires them; model cost alone never
  changes authority or safety boundaries;
- deterministic rules remain preferable where explicit rules solve the problem reliably without probabilistic AI;
- provider/model-specific behavior stays behind a replaceable boundary rather than being spread through product logic;
  provider/model replacement therefore aims to be an adapter/configuration + revalidation exercise rather than a
  product rewrite, while acknowledging that tools, schemas, privacy, context and lifecycle may still differ;
- multi-provider routing/failover, open-weight/local inference, persistent AI memory and autonomous multi-agent behavior
  are not first-release requirements and require separate evidence before activation.

AI Usta direction:

- user free text may be understood by a low-cost/fast conversational model;
- the model may ask controlled clarification questions;
- the bounded decision layer may propose states such as known task, symptom/diagnostic flow, more clarification needed,
  unsupported/unknown or safety hold/escalation;
- the proposed route/guide is not final until Kavriva verifies the correct motorcycle/variant, guide applicability,
  approved/current status, prerequisites, safety/readiness and source/provenance;
- if checks fail or evidence is insufficient, Kavriva asks for more information or holds safely.

Jev-specific direction:

- Jev is **not** adopted for the current/first-release direction;
- Kavriva must remain fully functional without Jev;
- no Jev/TypeSafe account, API key, production schema, data store, code path, contract or recurring dependency is created
  merely to preserve future optionality;
- Jev or a similar bounded decision model may later be evaluated as an optional adapter for low-risk routing,
  classification, triage, scoring or approved-candidate ranking if measured benefit over deterministic rules and the
  existing low-cost LLM path justifies the extra dependency;
- Jev probability/confidence can never override Kavriva deterministic HOLD, safety, eligibility or authorization rules.

Mandatory operating boundaries when AI is enabled:

- canonical/approved-source truth remains outside the model;
- structured output is semantically revalidated;
- correct motorcycle/task context is isolated;
- tool/action authority remains least-privilege and outside model output;
- retrieved/web/community/document/media/tool content is untrusted data, not policy;
- privacy/data minimization is feature/data-class specific;
- provider/model/version identity and behavior changes are observable and re-evaluated;
- retry/outage/cost behavior is bounded and critical journeys retain safe non-AI continuation;
- high-impact project/company AI work cannot self-PASS and requires independent review.

Decision boundary:

- no OpenAI, Anthropic, Google, AWS, Microsoft, TypeSafe/Jev or other provider/model/plan winner is selected;
- no provider account, API key, region, plan, trial, credits, purchase, payment, deployment or integration is approved;
- no production prompt, tool schema, agent workflow, vector DB, fine-tune or executable implementation is approved;
- no final jurisdiction-specific legal/privacy conclusion or final recurring AI budget is approved;
- no Phase-5 ADR and no Gate 4 -> 5 transition is approved.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-016__MANAGER_SYNTHESIS.md`.

---

## DEC-0047 — Production Download, Storage and Automatic Transfer Working Direction
**Date:** 2026-09-21
**Status:** USER-APPROVED PHASE-4 WORKING DIRECTION

After TASK-006 primary research, REVIEW-011 `CHANGES_REQUESTED`, narrow M-1/M-2/m-1 remediation and REVIEW-012
`PASS` with no Critical, Major or Minor findings, the user explicitly approved the final DEBATE-017 manager synthesis.

Binding direction:

- Kavriva prepares one complete, verified offline core for the selected motorcycle/task before offline-start eligibility;
- every visual/video/media byte required for safe understanding, required application or reachable safe-stop/recovery is
  `required safety media` and is a semantic subset of the `required compact core`;
- required safety media is not a separate/additive byte allowance and cannot be moved to the on-demand lane merely to
  satisfy a size target;
- the active-task complete package is exactly one verified required-compact-core generation including the full
  required-safety-media subset;
- safety-nonrequired/nonessential media may remain outside package completeness and may be fetched on demand;
- `CON-005` remains binding: required selected-task content does not ask for download confirmation merely because the
  path is cellular/mobile data, roaming or exceeds a byte/MB threshold;
- storage handling is adaptive: invalid/orphan/temp staging data, nonessential media, old inactive refetchable content
  and other rebuildable projections are removed before active/durable/protected truth;
- active-task complete package, durable user history/notes/photos/evidence, durable pending/accepted operation truth,
  protected audit/authority data and negative floors are not routine disposable cache;
- package transition remains conceptually stage -> verify complete manifest/digest/dependencies/compatibility -> atomic
  promote; partial/corrupt/mixed/stale/incompatible download never becomes actionable;
- download completion alone is not current authorization, recall/suspension state or canonical technical truth;
- background/network facilities are continuity helpers, not correctness authority.

Numeric policy remains intentionally open:

- no exact first-release MB/GB/% production limit is approved;
- 5/12/25/50/100 MB compact points, 25/100/150/300/500 MB safety-media points,
  100/250/500 MB/1 GB/2 GB refetchable-cache points and 20/10/5% free-space bands remain
  `HELD CANDIDATE SENSITIVITY / TEST POINTS`;
- exact compact/media hard caps, cache budgets/ceilings, free-space triggers/reserve, retry/backoff/chunk/partial-retention
  settings and real-device proof require later measured corpus/device evidence;
- Android Auto Backup's researched 25 MB file-based quota is a backup-service constraint only; it is not a Kavriva
  download/cache/core limit and is unrelated to the historical cellular-confirmation fixture.

Decision boundary:

- no CDN/storage provider, provider account, plan, purchase or payment is selected;
- no downloader/storage implementation, schema, deployment or production proof is approved;
- no final commercial budget is approved;
- no Phase-5 ADR is created;
- Gate 4 -> 5 remains closed pending an explicit Phase-4 closure/readiness audit and owner gate approval.

Canonical synthesis:
`04_TECH_STRATEGY/DEBATES/DEBATE-017__MANAGER_SYNTHESIS.md`.

---

## DEC-0048 — Gate 4 -> 5 Passed / Phase 5 ADR Authorized
**Date:** 2026-09-21
**Status:** APPROVED

The owner explicitly approved the Gate 4 -> 5 transition after the fresh-manager Phase-4 closure/readiness audit:

> onaylıyorum

Audit basis:

- `TSQ-001`–`TSQ-018` have direction-level answers with requirements/research/failure-scenario/independent-review/
  manager-synthesis/user-decision evidence;
- Drive `TASK-001`–`TASK-006` are DONE with independent PASS reviews and no open `CHANGES_REQUESTED`;
- remaining HELD items (provider/model winners, exact numeric limits, device/production proof, iOS/macOS and
  privileged-identity activation) classify as legitimate Phase-5 ADR/implementation evidence, not Phase-4 blockers.

Effect:

- Gate 4 -> 5 is PASSED; Phase 4 Technology Strategy is closed at strategy level;
- Phase 5 (ADR — technology/architecture decisions) is authorized to begin;
- no ADR is created by this decision itself; each Phase-5 ADR requires its own explicit owner approval before
  becoming APPROVED/LOCKED, consistent with `DEC-0005`;
- no code, prototype, provider account, purchase, deployment or production proof is authorized by this gate passage.

Canonical audit record:
`00_CONTROL/CHANGELOG.md` — `2026-09-21 / Fresh-Manager Bootstrap / Phase-4 Closure Readiness Audit`.

---

## DEC-0049 — Sub-Agent Model Choice Delegated to Manager
**Date:** 2026-09-21
**Status:** APPROVED OPERATING RULE
**Supersedes:** DEC-0022 (model-choice restriction; Luna Max definition retained as preferred default)

User instruction, verbatim:

> phase 5 e başlayabiliriz altajanlarını istediğin gibi kullanabilirsin

Decision:

- the manager may use any available sub-agent model within the active task scope without requesting per-use
  permission;
- guardrails remain: sub-agent use stays inside the active user task and does not expand scope, permit code
  during no-code planning, or override phase/change-control rules;
- high-impact AI work still requires separate implementer/reviewer roles and independent evidence (`DEC-0028`,
  `DEC-0029`);
- this delegation covers internal sub-agents and does not change the separate external-AI parallelism rule
  (`DEC-0041`).

---

## DEC-0050 — Gate 5 -> 6 Passed / Phase 6 Delivery Planning Authorized
**Date:** 2026-09-21
**Status:** APPROVED

The owner explicitly approved the Gate 5 -> 6 transition with all 15 ADRs APPROVED:

> onaylıyorum

Gate criterion check:

- all required technology/architecture ADR records are APPROVED, including the ADR-015 AI-safe
  module/contract/topology, graph metadata/identity and dependency-direction scope;
- no ADR was skipped, silently advanced or left PROPOSED.

Effect:

- Gate 5 -> 6 is PASSED; Phase 5 is closed;
- Phase 6 (epic -> capability -> feature -> flow -> task, dependencies, acceptance criteria,
  bidirectional traceability, no-code task simulation) is authorized to begin;
- no task execution, prototype, account, purchase or code is authorized by this gate passage
  (code starts only after Gate 8 -> Development).

---

## DEC-0051 — Mixed Execution Model (Path C) as Default for Development
**Date:** 2026-09-21
**Status:** APPROVED OPERATING DIRECTION (takes effect in Development; mechanism design in Phase 7–8)

User context: the owner will develop using existing subscriptions (Claude/Codex/Antigravity/OpenCode),
whichever has quota; asked how chats are controlled, what the control software is, and what full API
automation (Path B) costs. After a staged estimate (mid-tier model orbit: low-hundreds USD total;
cheap tier: tens; flagship: $1,000+; stuck-agent and price-volatility caveats recorded in chat),
the owner chose Path C (`yol c ile devam edelim`).

Decision:

- Default Development execution is mixed: pack generation and quality gates automated (free: templates +
  GitHub automation, built in Phase 7–8); opening chats and carrying pack text stays manual with the owner.
- No paid API automation without a separate current cost sheet and explicit approval (`DEC-0030`); current
  unit prices were surveyed 2026-09-21 and must be re-verified at decision time.
- Subscription quotas rotate across tools; implementer/reviewer separation aligns with quota rotation
  (a different chat reviews).
- Owner never carries technical content; AI-to-AI communication uses structured records (task/reject/evidence
  cards); the owner sees status lines and BLOCKED options only.
- This constrains Phase-7 router/harness design: it must work with manual carrying (copy-paste packs);
  API actuation of chats is an optional later upgrade, never an assumption.

---

## DEC-0052 — Capability Breakdowns Go Through Independent Review, Not Owner Pre-Approval
**Date:** 2026-09-21
**Status:** APPROVED OPERATING RULE

User instruction, verbatim:

> kırılımları yaptıktan sonra bana sormak yerine altajan açıp bağımsız incelet

Decision:

- Phase-6 breakdowns (capability/feature/flow/task drafts) are verified by an independent sub-agent
  against their source ADRs/records BEFORE being written to planning catalogs — instead of asking the
  owner to approve each draft.
- Review verdict `PASS` (no findings) authorizes recording the breakdown as PROPOSED; `CHANGES_REQUESTED`
  requires remediation and re-review of the affected rows only.
- The owner no longer pre-approves every breakdown batch. The owner still: approves phase gates, decides
  BLOCKED/escalation options, approves purchases/accounts/production, and may override or re-review any
  recorded breakdown on request.
- Each review is recorded (reviewer, verdict, findings, remediation) in `CHANGELOG.md`; push of new records
  still requires explicit owner authorization per push.
- First application: E5 + E6 capability draft reviewed `CHANGES_REQUESTED` (2 Critical, 5 Major, 0 invented
  scope); remediation + narrow re-review pending before catalog write.

---

## DEC-0053 — Motorcycle Slot and Guide Entitlement Shape
**Date:** 2026-09-21
**Status:** APPROVED TIER SHAPE (prices, package names and billing periods remain open for commercial validation)

User decision, verbatim:

> 1 motor eklemek bedava üstü ücretli + pro vb bir abonelik alındığında ekleme hakkı 3 e çıkabilir ama rehber
> kılavuz seçtiği 1 motora açılır

Decision:

- 1 motorcycle slot is free; additional slots are paid.
- With a pro-or-similar subscription, total slots rise to 3.
- The full-guide right opens for 1 selected motorcycle at a time; selecting another bike moves the right,
  it does not stack.
- Preserved invariants (unchanged, not negotiable by this decision): existing records are never locked;
  critical safety reach-back and required rechecks continue independent of entitlement; started physical work
  is never stranded mid-repair by an entitlement change; inactive history/evidence/export/correction access
  is preserved; reactivation requires current-context revalidation.
- This resolves the one-active vs multi-bike tension recorded in the Step 5 findings; entitlement tasks
  (T-E1-014b and server-side checks) now have their shape. Exact prices, package names, billing periods,
  selection-switch frequency/anti-abuse rules and trial/wrong-selection handling stay open on the commercial
  validation track and remain HELD gates, not tasks.

---

## DEC-0054 — First Release Ships Complete Planned Scope, Nothing Deferred
**Date:** 2026-09-21
**Status:** APPROVED SCOPE DIRECTION (prices/packages still HELD for commercial validation)

User decision, verbatim:

> önceden planlanmış herşey olsun ilk sürüm eksiksiz olmalı

Decision:

- All 8 Gate 6 -> 7 content gaps become first-release scope, none deferred: estimates UI (BR-063/064),
  commerce neutrality (BR-070/071/073), roadside mode (BR-074), safe-closure acceptance content,
  Q-0066 replacement window, Q-0046 media classification rule, IDCO-RQ-060..062 resilience, CON-004 clarity.
- Each gap gets features/flows/tasks through the normal draft → independent-review → record loop, plus
  E1/E2 validation assignment (review/gate/simulation labels, no code).
- This does not authorize code, accounts, purchases, numeric proofs or device tests; HELD evidence stays HELD.
- Commercial rule from DEC-0053 stands: shape locked, prices/packages HELD.

---

## DEC-0055 — Gate 6 -> 7 Passed / Phase 7 AI Architecture Authorized
**Date:** 2026-09-21
**Status:** APPROVED

The owner explicitly approved the Gate 6 -> 7 transition (`geçir`) after the re-audit verification PASS:

- Phase 6 delivery planning complete: 10 epics, 78 capabilities, 101 features, 110 flows, 199 tasks with
  acyclic dependencies, closed bidirectional traceability, zero orphans, passed no-code simulation.
- Gate 5 -> 6 criterion fully met; all prior BLOCKED items closed and verified.

Effect:

- Gate 6 -> 7 is PASSED; Phase 6 is closed;
- Phase 7 (AI-native architecture: context routing, minimum context packs, Obsidian-compatible graph metadata,
  module boundaries, public contracts, dependency/design/change-control, validation, migration, rollback,
  completion evidence, architecture tests) is authorized to begin;
- no code, task execution, account, purchase, deployment or production proof is authorized by this gate passage
  (code starts only after Gate 8 -> Development).

---

## DEC-0056 — Review Loop Runs Until PASS, No Round Cap
**Date:** 2026-09-21
**Status:** APPROVED OPERATING RULE (extends DEC-0052)

User instruction, verbatim:

> inceleme - düzeltme - inceleme - düzeltme sorun çıkamayana kadar

Decision:

- Every draft → independent-review → remediation cycle repeats (narrow re-review, then micro review if needed)
  until the verdict is PASS with zero open findings. There is no round cap and no "good enough" acceptance.
- Awaiting the owner is never part of the loop: rounds run autonomously; the owner sees only the final PASS
  record plus honest counts (rounds used, findings closed).
- This does not authorize scope expansion during remediation: fixes stay narrow to findings; new scope needs
  its own draft + review.

---

## DEC-0057 — Gate 7 -> 8 Passed / Phase 8 Bootstrap Authorized
**Date:** 2026-09-21
**Status:** APPROVED

The owner explicitly approved the Gate 7 -> 8 transition (`onaylıyorum`) after independent gate verification PASS:

- Phase 7 AI architecture complete: 23 design documents across Groups 1–6, each reviewed PASS with no open findings;
  gate audit BLOCKED items (4) closed and verified; no mechanism/account/key/purchase/code selected.
- Gate 7 -> 8 criterion fully met.

Effect:

- Gate 7 -> 8 is PASSED; Phase 7 is closed;
- Phase 8 (repository bootstrap: physical repository + Obsidian graph + task registry + CI/architecture/design/
  traceability checks, validated by an example task that must not become product-code development) is authorized
  to begin;
- no application code, task execution beyond the bootstrap proof task, account, purchase, deployment or production
  proof is authorized by this gate passage.

---

## DEC-0058 — Phase-8 Bootstrap Plan Approved / Records Push Authorized
**Date:** 2026-09-22
**Status:** APPROVED

The owner explicitly approved (`onaylıyorum`) both:

(a) pushing the pending records batch (DEC-0057 gate records, corrected 07 README, repo link);

(b) the Phase-8 bootstrap work plan, in order with draft → independent review → PASS → setup per step and
  per-step push authorization:

1. directory blueprint draft for `kavriva-app` (approved form installed afterwards);
2. physical module boundaries + public-contract skeleton;
3. validation commands + architecture tests;
4. CI quality gates;
5. task registry + traceability/graph checks;
6. migration/rollback applicability;
7. proof-task validation + fresh-AI-session bootstrap test + Gate 8 readiness audit.

Effect:

- Phase-8 Step 1 (directory blueprint draft) is authorized to begin; no construction beyond the approved plan;
- product feature code and deployment remain unauthorized; the proof task must not become product development;
- implementation repository is owner-created empty at `https://github.com/xpike-dgm/kavriva-app`.

---

## DEC-0060 — Five-AI Closure Protocol (Per-AI Fix-and-Return)
**Date:** 2026-09-23
**Status:** APPROVED (owner-defined workflow)

Five independent AIs stress-test the plan. Operating loop, per AI output brought by the owner:

1. Triage the delivering AI's findings against disk (confirm real vs invalid, no blind fixes).
2. Fix that AI's confirmed issues (review loop intact for content/code changes).
3. Return to the SAME AI session: if it was incomplete, it continues from where it stopped; if it was complete
   with findings, it verifies whether its issues are closed.
4. Completion accepted only when 5 AIs report no problems (agreement still ≠ automatic approval; each closure
   is verified, not assumed).

Effect: OUT-1 (partial, 7 findings) and OUT-5 (EKSİK-TARAMA, 5 findings) findings close per AI; Gate 8 stays
pending until the protocol completes.

---

## DEC-0061 — Push Discipline (Owner Bypass Audited, PR Default)
**Date:** 2026-09-23
**Status:** APPROVED (owner-approved under DEC-0062 mandate)

Ruleset `main-gates` is ACTIVE on both repos (PR + 1 approval + dismiss-stale + required check + no-FF +
no-deletion). Owner-role bypass exists and is used ONLY for manager pushes carrying explicit authorization
(DEC-0059 standing mandate / DEC-0060 per-AI closures / DEC-0062 batch mandate); every bypass push logs the
violations line remotely and lands as a recorded commit. All other changes go via pull request.
Rationale: closes OUT-1 B-01-new and OUT-3 B-12 without breaking the manager loop; bypass without a covering
authorization is a violation.

---

## DEC-0062 — Batch-3 Best-Judgment Mandate (Complete, No Corner-Cutting)
**Date:** 2026-09-23
**Status:** APPROVED (owner instruction: best professional judgment, complete option over convenient one)

The manager decides and approves Batch-3 items by best judgment: sealed-doc edits (B-16/17/18 seam+epic, B-26
acceptance criteria), scope additions (B-09 KVKK/store capabilities, B-25 measurement tasks), governance
(B-12/DEC-0061, B-33 external triggers), new checks (B-07), wikilink conversion (B-06). The review loop
(draft → different-context review → PASS) stays mandatory for every change; honest records continue; Gate 8
passage still needs separate explicit approval.

---

## DEC-0063 — External-Change Trigger Rule
**Date:** 2026-09-23
**Status:** APPROVED (under DEC-0062 mandate)

Binding trigger table lives in `00_CONTROL/EXTERNAL_CHANGE_TRIGGERS.md`: listed external changes (GitHub,
Actions, Supabase, Flutter, stores, Apple, Drive, models) reopen the listed gates/decisions; unlisted changes
open a change-request. Closes OUT-3 B-33.

---

## DEC-0064 — B-01 Per-Repo Enforcement Split + T3 Rule Activated
**Date:** 2026-09-23
**Status:** APPROVED (owner-approved both manager recommendations: per-repo split + T3 on)
**Owner verbatim (2026-09-23):** “önerilerin doğrultusunda kabul ediyorum”

B-01 governance: application repo (`kavriva-app`, future product code, high blast radius) runs with NO bypass —
pull request + green CI + approval required for everyone including the owner. Planning repo (records, low blast
radius) keeps owner-role bypass strictly for authorized manager pushes (DEC-0059/0060/0062), each landing as a
recorded commit with a remote bypass-log line. Rationale: mechanical lock where the asset lives, audited flow
where records live (OUT-3 B-01 closure condition).

T3 rule (from REVIEW_LOG PROPOSED section): ACTIVE as of this decision. T3-class work (money/publish/identity)
additionally requires a non-subagent review leg (owner check or second-model session); sub-agent review alone
is insufficient for T3. Cost accepted by owner: T3 tasks wait for the second eye.

---

## DEC-0059 — Standing Phase-8 Execution Mandate (Best-Judgment + Push)
**Date:** 2026-09-22
**Status:** APPROVED

The owner (`en mantıklı kararları vererek bunları sen uygula ... en iyisi neyse ondan asla vazgeçme`,
`push onayı da verildi`) grants a standing mandate for the remainder of Phase 8:

- the manager decides placement/installation details by best judgment within the approved 7-step plan and
  applies them without asking per micro-decision;
- push to both repositories is authorized per completed step (no per-push re-ask inside Phase 8);
- the review loop (draft → different-context review → narrow remediation → re-review → PASS) is NEVER
  skipped or softened; no PASS, no install — no exceptions;
- honest record-keeping continues ("çalışıyor" boxes only when proven; deferrals written, not hidden);
- this mandate covers Phase 8 only; product code, deployment, account/purchase, and Gate 8 passage still
  require explicit owner approval each.

