# KAVRIVA SCREEN FAMILY + SPECS — MAIN-MANAGER REVIEW

Status: REVIEW
Date: 2026-09-15
Source package: `PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN FAMILY + SPECS 01`
Uploaded package SHA-256: `97bb6ff594d397ed7ce3c3e8b97ad8aeb805cf5212b379ed5e0298f7e825f285`

## Result

`PASS_WITH_REFINEMENTS — USER NAVIGATION DECISION REQUIRED`

Delegated package approved `SCR-001` — `SCR-038` architecture'i 9 anlamli screen family'ye ayiriyor, tum 38 context icin per-screen specification veriyor ve approved Phase-2 / Phase-3 authority sinirlarini koruyor.

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

Package language/unit ve accessibility modality controls icin hybrid/app-level preference placement onermektedir.

Constraint:
- language/unit preference veya accessibility support, profile/account acmaya bagliymis gibi tasarlanamaz,
- account-light/local use bu temel presentation/accessibility davranislarindan yararlanabilmelidir,
- profile varsa preference persistence icin kullanilabilir; fakat product access prerequisite olamaz.

Bu refinement product requirement eklemez; approved first-value/account-light ve accessibility semantics'ini korur.

## Main-Manager Refinement 02 — Navigation Choice Requires User Preference

Delegated package uc PROPOSED global shell sunuyor:

### Option 1 — Motorcycle-Context-First
Motor merkezde; task, symptom, maintenance ve history motor context icinden acilir.
Risk: `SCR-005` fazla entry toplarsa dashboard/card-stack hissi geri gelebilir.

### Option 2 — Task-First Launcher
Once `ne yapmak istiyorsun?`; motorcycle context header'da.
Risk: launcher zamanla feature menu/dashboard'a donebilir ve maintenance/history ikincil hissedebilir.

### Option 3 — Focused Hybrid Shell
Compact motorcycle context + uc ana alan:
- Yap / Coz
- Bakim
- Gecmis

Lifecycle/profile/collaboration/community contextual kalir.
Delegated recommendation: Option 3.
Main-manager assessment: **Option 3 en guclu candidate**, cunku approved UX simplicity principle'i ve onceki dashboard-clutter feedback'i ile en iyi uyumu gosteriyor.

Option 3 hala APPROVED degildir; explicit user selection gerekir.

## Surface Recommendations

Package'in ambiguous contexts icin sheet/full-screen/modal/state-family onerileri mantikli ve `PROPOSED` kalmalidir. Bu turda exact modality user'a tek tek secim olarak yuklenmeyecek; screen-by-screen visual-reference planning sirasinda consequence ve complexity'ye gore QA edilebilir.

Ozellikle:
- `SCR-037` permanent paywall route degil contextual gate/state family olarak korunmali,
- `SCR-038` permanent social feed'e donusmemeli,
- `SCR-015` recovery normal navigation destination olmamali,
- `SCR-012` readiness hold dead-end olmamali.

## Approval Boundary

Bu review:
- delegated screen-family/spec paketini QA'den gecirir,
- package'i otomatik APPROVED/LOCKED yapmaz,
- global navigation shell'i secmez,
- visual generation'a yetki vermez,
- Gate 3 -> 4'u gecirmez.

User navigation shell secimini yaptiktan sonra main-manager:
1. selected shell'i controlled decision olarak kaydeder,
2. screen-family/spec package'i gerekli refinement'lerle APPROVED working spec seviyesine tasiyabilir,
3. family-based visual-reference planning/generation promptunu hazirlayabilir.
