# KAVRIVA SCREEN FAMILY + SPECS — MAIN-MANAGER REVIEW

Status: APPROVED
Date: 2026-09-15
Source package: `PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN FAMILY + SPECS 01`
Uploaded package SHA-256: `97bb6ff594d397ed7ce3c3e8b97ad8aeb805cf5212b379ed5e0298f7e825f285`

## Result

`PASS_WITH_REFINEMENTS — APPROVED WORKING SPECS`

Delegated package approved `SCR-001` — `SCR-038` architecture'i 9 anlamli screen family'ye ayiriyor, tum 38 context icin per-screen specification veriyor ve approved Phase-2 / Phase-3 authority sinirlarini koruyor.

User navigation review sirasinda original 1/2/3 options yerine yeni bir shell refinement onerdi ve acikca onayladi:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

Main-manager bu selection'i approved architecture ve simplicity constraints ile QA ederek kabul etti. Canonical navigation source: `GLOBAL_NAVIGATION.md`.

## What Passed

- Tum `SCR-001` — `SCR-038` context'leri coverage aliyor.
- Her SCR tek bir family'ye atanmis.
- Family yapisi urun mantigiyla uyumlu:
  - FAM-01 First Use / Motorcycle Context
  - FAM-02 Guide Discovery / Fit / Preparation
  - FAM-03 Active Application / Safety / Recovery
  - FAM-04 Diagnosis
  - FAM-05 Maintenance / Reminder
  - FAM-06 History / Evidence / Trust
  - FAM-07 Motorcycle Lifecycle / Entitlement
  - FAM-08 Profile / Collaboration
  - FAM-09 Community
- U04 yalniz `SCR-014` active-guide anchor davranisinda DIRECT tutuluyor; universal app layout'a cevrilmiyor.
- V10 visual DNA olarak kullaniliyor; universal composition veya exact token system yapilmiyor.
- Default-view simplicity her spec'te ana user job uzerinden korunuyor; card-per-semantic/dashboard yaklasimina geri donulmuyor.
- Safety hold, teaching-only, uncertainty, dispute, interruption, guide change, stale content, entitlement, downgrade ve community-authority states korunuyor.
- Generic Settings, dashboard/KPI home, marketplace home, permanent social feed veya pricing screen uydurulmuyor.
- Technology/backend/database/API/auth/sync/framework veya final pricing karari verilmiyor.

## Main-Manager Refinement 01 — Preferences Must Not Depend on Profile

Language/unit preference veya accessibility support:
- profile/account acmaya bagli tasarlanamaz,
- account-light/local use'da kullanilabilir olmalidir,
- profile varsa persistence icin kullanilabilir fakat access prerequisite olamaz.

## User Navigation Decision — Approved Five-Tab Shell

Approved bottom bar:
1. Garaj
2. Bakim
3. AI Usta — center / primary-assistance entry
4. Gecmis
5. Topluluk

### Why this passes QA

Bu shell capability'leri tek bir dashboard'a yigmak yerine uzun omurlu ana product responsibilities'i ayirir.

- Garaj motorcycle context/lifecycle responsibility'sini tasir.
- Bakim maintenance/reminder responsibility'sini tasir.
- AI Usta known-task + symptom-first assistance'in merkezi entry'sidir.
- Gecmis longitudinal history/evidence/trust responsibility'sini tasir.
- Topluluk community Q&A/experience'i official guide authority'sinden ayri tasir.

### AI Usta constraint

`AI Usta` bir UX role/entry label'idir; bu karar LLM/provider/backend architecture secmez.

AI Usta:
- kendi basina technical source-of-truth degildir,
- verified sources/guides yerine gecmez,
- fit/readiness/safety gates'i bypass edemez,
- unsupported technical value veya definitive diagnosis uyduramaz,
- approved `SCR-009` / `SCR-019` ve downstream flows'a kontrollu yonlendirme yapar.

Exact interaction formu sonraki visual-reference work'te rafine edilir.

## Controlled SCR-005 Refinement

5-tab shell sonrasinda `SCR-005` eski broad action-hub rolunde tum capability'leri ayni anda tasimayacak.

Working refinement:
- Garaj = motorcycle context / switching / lifecycle emphasis,
- AI Usta = known task + symptom primary entry,
- Bakim = maintenance primary entry,
- Gecmis = history primary entry,
- Topluluk = community primary entry.

Bu capability silme degil, approved interactions'in daha sade global shell'e dagitilmasidir.

## Surface Recommendations

Delegated package'in ambiguous sheet/full-screen/modal/state-family onerileri **PROPOSED** kalir ve exact production modality sayilmaz.

Ozellikle:
- `SCR-037` permanent paywall route degil contextual gate/state family,
- `SCR-038` permanent social feed degil,
- `SCR-015` recovery normal navigation destination degil,
- `SCR-012` readiness hold dead-end degil.

## Approval Boundary

APPROVED working specs:
- 9-family grouping,
- per-SCR hierarchy/action/trust/safety specifications,
- five-tab global navigation responsibility split,
- language/unit/accessibility profile-independence refinement.

Still open:
- exact ambiguous surface modalities,
- AI Usta structured vs conversational interaction shape,
- active-guide bottom-bar visibility,
- first post-onboarding landing tab,
- final production component/token/iconography,
- technology/pricing.

This review does NOT pass Gate 3 -> 4. Screen-by-screen visual references still require controlled generation + user approval.
