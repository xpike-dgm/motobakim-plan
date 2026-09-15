# PHASE 3 — KAVRIVA / FIVE-TAB MAIN-SHELL VISUAL REFERENCES AI PROMPT

Status: ACTIVE — USE NOW

Bu prompt yeni bir AI sohbetine verilmek icindir.

---

Sen Kavriva mobil uygulamasinin **Senior Mobile Product Visual Designer & UX Consistency Specialist** rolundesin.

Bu gorev Phase 3 Design icinde approved screen architecture, working specs, five-tab navigation ve approved AI Usta A1 structure sonrasindaki **main-shell root visual reference** adimidir.

Amacin tum uygulamayi cizmek DEGIL. Once Kavriva'nin 5 ana bottom-tab root surface'ini tek, tutarli visual family olarak gorsellestirip user feedback almak.

## SOURCE OF TRUTH — ONCE OKU

Repository erisimin varsa en az:

1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `00_CONTROL/OPEN_QUESTIONS.md`
6. `03_DESIGN/README.md`
7. `03_DESIGN/BRAND_NAME.md`
8. `03_DESIGN/LOGO_DIRECTION.md`
9. `03_DESIGN/ANCHOR_UX_STRUCTURE.md`
10. `03_DESIGN/ANCHOR_VISUAL_STYLE.md`
11. `03_DESIGN/REFERENCE_INDEX.md`
12. `03_DESIGN/SCREEN_CATALOG.md`
13. `03_DESIGN/NAVIGATION_MAP.md`
14. `03_DESIGN/STATE_MATRIX.md`
15. `03_DESIGN/DESIGN_PRINCIPLES.md`
16. `03_DESIGN/GLOBAL_NAVIGATION.md`
17. `03_DESIGN/SCREEN_FAMILY_SPECS.md`
18. `03_DESIGN/AI_USTA_UX_STRUCTURE.md`
19. `03_DESIGN/KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`
20. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`

oku.

Repository erisimin yoksa product behavior uydurma; gerekli source dosyalarini iste ve DUR.

## REQUIRED VISUAL ATTACHMENTS

Exact visual-direction fidelity icin user bu sohbete su iki approved working reference image'ini ATTACH etmelidir:

1. selected `Kavriva_L05A.png`
2. selected `Kavriva_V10_Signature-Kavriva.png`

Bu iki gorselden biri yoksa exact approved brand/visual fidelity'yi hafizadan reconstruct etme. Eksik attachment'i iste ve DUR.

A1 wireframe attachment zorunlu degildir; canonical hierarchy `AI_USTA_UX_STRUCTURE.md` icindedir.

## APPROVED FIXED GLOBAL NAVIGATION

Bottom bar labels/order degismez:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

- AI Usta center item'dir.
- Her generated root screen'de bottom bar gorunur ve ilgili tab selected olur.
- Exact icon family final production decision degildir; tutarli, restrained working icons kullan.
- AI Usta item slightly more recognizable/central olabilir fakat oversized floating orb / giant hero button olamaz.

## APPROVED VISUAL DNA

Use V10 as working visual DNA, not literal universal layout:
- clean near-white canvas,
- deep graphite/navy text,
- restrained electric-blue accent,
- moderate rounding,
- low decoration,
- strong typography hierarchy,
- restrained L05A brand presence,
- calm technical credibility.

DO NOT:
- copy U04 active-guide layout to all roots,
- mechanically repeat L05A geometry in cards/dividers/buttons,
- use shield/check as generic verified/safe/certified badge,
- invent final HEX/font/token claims,
- create dashboard/KPI/card-stack look.

## THIS ROUND — EXACTLY 5 ROOT VISUALS

Generate exactly **5 separate portrait mobile UI images**, NOT a collage.

All 5 should clearly belong to the same app and same visual system.

### R01 — GARAJ ROOT

Responsibility:
- selected motorcycle context,
- switching / active-inactive management entry,
- motorcycle identity/lifecycle context.

Default visual job:
**Kullanicinin hangi motosiklet baglaminda oldugunu net gostermek.**

Fixture:
- page title: `Garaj`
- selected motorcycle label: `Motosikletim`
- simple status: `Aktif motosiklet`
- compact actions may include: `Motosikleti degistir`, `Motosiklet bilgileri`

Do NOT add:
- maintenance summary cards,
- history summary cards,
- community feed,
- KPI/health score,
- all capabilities on one page.

Garaj dashboard degildir.

### R02 — BAKIM ROOT

Responsibility:
- maintenance plan,
- due/upcoming/uncertain items,
- reminder/catch-up entry.

Default visual job:
**Kullanicinin en onemli bakim ihtiyacini hizla anlamasi.**

Illustrative fixture only — not technical truth:
- page title: `Bakim`
- motorcycle context: `Motosikletim`
- first item: `Fren kontrolu` — `Yaklasiyor`
- second item: `Yag degisimi` — `Planli`
- optional third low-priority item: `Zincir kontrolu`

No invented km/date/interval/value/source names.
No maintenance health score/chart.
Critical safety/correction must not look like ordinary routine reminder.

### R03 — AI USTA ROOT — A1 GUIDED SPLIT

A1 hierarchy is FIXED:
- compact page identity: `AI Usta`
- compact selected motorcycle: `Motosikletim`
- prompt: `Nasil yardimci olayim?`
- choice 1: `Bir is yapmak istiyorum`
- choice 2: `Motorda bir sorun var`
- optional tiny/on-demand `Hangisini secmeliyim?`
- bottom bar: AI Usta selected

Target:
**1 context + 1 question + 2 paths.**

No root free-form chat transcript.
No generated technical answer.
No diagnosis result.
No popular-question grid.
No third equal-weight CTA.
No maintenance/history/community summaries.

The two intents may be large accessible targets but must NOT become bulky nested content cards.

### R04 — GECMIS ROOT

Responsibility:
- longitudinal motorcycle history,
- record/evidence/trust entry.

Default visual job:
**Kullanicinin ne oldugunu kronolojik olarak rahat taramasi.**

Illustrative fixture only:
- page title: `Gecmis`
- motorcycle context: `Motosikletim`
- search/filter affordance restrained
- timeline/list examples:
  - `Fren balatasi kontrolu` — `Kullanici kaydi`
  - `Yag degisimi` — `Servis kaydi`
  - `Zincir bakimi` — `Kullanici kaydi`

No invented verification result.
No analytics/KPI dashboard.
No card-per-semantic inflation; dense readable list/timeline is preferred when appropriate.

### R05 — TOPLULUK ROOT

Responsibility:
- community experiences / Q&A reading,
- explicit contribution/report entry,
- official-guide authority'den separation.

Default visual job:
**Kullanicinin community bilgisini official guidance sanmadan ilgili deneyimi bulmasi.**

Illustrative fixture only:
- page title: `Topluluk`
- simple search/topic entry
- content examples:
  - `Fren sesi deneyimleri`
  - `Bakim sirasinda karsilasilan sorunlar`
- clearly visible community/source status such as `Topluluk deneyimi` or `Kisisel deneyim`
- low-emphasis `Katki yap` action

No follower counts, likes-as-authority, trending feed, infinite-social-feed composition or official-guide numbered-step styling.
No user experience should look verified merely because published.

## COHERENCE RULES ACROSS ALL 5

- Same bottom-bar geometry and label order.
- Same core typography/spacing logic.
- Same restrained V10 color/surface character.
- Selected tab state changes per root; rest stays consistent.
- Motorcycle context presentation should feel related across relevant roots without becoming a huge card.
- Each root has one primary user job.
- Accessibility: full text labels, sufficient tap targets, non-color-only semantic states.

## VISUAL SIMPLICITY QA BEFORE SHOWING USER

For each image ask:
1. Can the user understand the root's main job in ~2 seconds?
2. Is there more than one large semantic block competing for attention?
3. Did the screen become a dashboard or card stack?
4. Is the bottom bar clear without overpowering content?
5. Does AI Usta look like a safe entry/router rather than an all-knowing technical chatbot?
6. Does Topluluk remain semantically separate from official guide authority?

If #2/#3 is YES, simplify before showing.

## IMPORTANT — DO NOT DESIGN THESE YET

This round does NOT generate:
- first-use/onboarding screens,
- detailed known-task selection,
- diagnosis checks,
- active repair steps beyond already approved anchor,
- recovery/safety exception screens,
- profile/collaboration,
- transfer/delete,
- entitlement gates,
- detailed record/provenance,
- pricing/subscription,
- technical AI architecture.

## USER REVIEW STEP

After generating R01–R05, STOP and ask the user to review the five roots.

Ask only for concise feedback:
- `hepsi iyi`,
- or screen IDs that need change, e.g. `R01 ve R05 degissin`,
- plus short description if desired.

Do not automatically generate deeper screens before user feedback.

## AFTER USER APPROVAL / FINAL REVISIONS

When user accepts the root set, output exactly:

# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / FIVE-TAB MAIN SHELL VISUALS 01

A. SOURCE CHECK  
B. ATTACHED REFERENCE CHECK  
C. USER FEEDBACK — VERBATIM  
D. APPROVED-CANDIDATE ROOT SET — R01 TO R05  
E. CROSS-SCREEN VISUAL CONSISTENCY  
F. BOTTOM-BAR TREATMENT  
G. AI USTA A1 VISUAL INTEGRATION  
H. CLUTTER / DASHBOARD QA  
I. TRUST / SAFETY / COMMUNITY SEMANTIC QA  
J. ACCESSIBILITY NOTES  
K. WHAT IS STILL NOT FINAL  
L. RECOMMENDED NEXT VISUAL FAMILY

Then DUR.

- Do not repository write.
- Do not declare APPROVED/LOCKED.
- Do not proceed to remaining 38 screens automatically.
- Do not choose technology/LLM/provider/backend.
- Do not move to Phase 4.
