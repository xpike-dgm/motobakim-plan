# SOURCE OF TRUTH

Bu belge hangi bilginin hangi otorite seviyesinde oldugunu tanimlar.

## Genel Otorite Sirasi

1. Kullanicinin en yeni ve acik talimati
2. `LOCKED` kararlar / ADR'ler / onayli referanslar
3. `APPROVED` source-of-truth belgeleri
4. `00_CONTROL/CURRENT_STATE.md`
5. Diger aktif repository belgeleri
6. Ham kanit / tartisma kayitlari
7. Gecmis sohbetler
8. AI'nin kendi hatirladigi, varsaydigi veya cikarsadigi bilgi

## Global Kontrol Kaynaklari

- `AI_START_HERE.md` — oturum bootstrap protokolu
- `CURRENT_STATE.md` — guncel durum
- `DECISION_LOG.md` — surec/proje karar kaydi
- `OPEN_QUESTIONS.md` — cozulmemis belirsizlikler
- `WORKFLOW_MAP.md` — 8 asama sirasi
- `PHASE_GATES.md` — gecis kosullari
- `DOCUMENT_REGISTRY.md` — kritik belge statuslari
- `CHANGELOG.md` — degisiklik izi
- `HANDOFF.md` — yeni AI devir ozeti
- `PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md` — user-approved internal data/content operations requirement
- `NEW_MANAGER_CHAT_HANDOFF.md` — yeni ana proje-yonetici sohbetine kontrollu devir kilavuzu
- `NEW_MANAGER_CHAT_PROMPT.md` — yeni ana proje-yonetici sohbetine yapistirilacak bootstrap promptu

## Asama Bazli Otorite

### 01 Workspace
`PROJECT_VISION.md`, `CONSTRAINTS.md`, `ASSUMPTIONS.md`, `GLOSSARY.md`. Varsayimlar gercek sayilmaz.

### 02 Discovery
`SESSIONS/` ham kanittir. Phase-2 approved product truth entry point'i `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md` dosyasidir. Working synthesis sonraki kontrollu approval olmadan approved snapshot'i otomatik degistirmez.

### Post-Discovery Approved Scope Addendum

Internal Data & Content Operations capability project scope'una dahildir:
- `00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`
- explicit user confirmation: `bu kesin yapılacak`

Bu requirement:
- motorcycle/technical data research,
- missing/incomplete/stale/conflicting data visibility,
- provenance/source management,
- controlled content/data update,
- review/version/recall needs,
- approved/published data'nin consumer mobile tarafinda kullanilabilmesi,
- data-quality/coverage/operations analytics
kapsamini zorunlu gelecek planlama girdisi yapar.

It does NOT decide web vs desktop vs hybrid, database/CMS/API/sync architecture, exact publishing mechanics, AI provider/model, analytics stack or implementation technology.

### 03 Design — Approved Working Authorities

Brand / logo / anchor:
- `03_DESIGN/BRAND_NAME.md` — Kavriva
- `03_DESIGN/LOGO_DIRECTION.md` — `REF-BRAND-001` / L05A
- `03_DESIGN/ANCHOR_UX_STRUCTURE.md` — `REF-UX-001` / U04
- `03_DESIGN/ANCHOR_VISUAL_STYLE.md` — `REF-VISUAL-001` / V10

Full-app architecture/spec/navigation:
- `03_DESIGN/SCREEN_CATALOG.md`
- `03_DESIGN/NAVIGATION_MAP.md`
- `03_DESIGN/STATE_MATRIX.md`
- `03_DESIGN/DESIGN_PRINCIPLES.md`
- `03_DESIGN/SCREEN_COVERAGE_TRACEABILITY.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-ARCH-001`
- `03_DESIGN/GLOBAL_NAVIGATION.md` -> `REF-NAV-001`
- `03_DESIGN/SCREEN_FAMILY_SPECS.md` -> `REF-SPEC-001`

AI Usta:
- `03_DESIGN/AI_USTA_UX_STRUCTURE.md` -> `REF-AIUSTA-001` / A1 Guided Split

Approved visual families:
- `03_DESIGN/MAIN_SHELL_VISUAL_REFERENCES.md` -> `REF-SHELL-001`
- `03_DESIGN/GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md` -> `REF-GUIDE-001`
- `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md` -> `REF-ACTIVE-001`
- `03_DESIGN/DIAGNOSIS_VISUAL_REFERENCES.md` -> `REF-DIAG-001`
- `03_DESIGN/MAINTENANCE_REMINDER_VISUAL_REFERENCES.md` -> `REF-MAINT-001`
- `03_DESIGN/HISTORY_EVIDENCE_TRUST_VISUAL_REFERENCES.md` -> `REF-HISTORY-001`
- `03_DESIGN/MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUAL_REFERENCES.md` -> `REF-LIFECYCLE-001`
- `03_DESIGN/PROFILE_COLLABORATION_VISUAL_REFERENCES.md` -> `REF-PROFILE-001`
- `03_DESIGN/COMMUNITY_VISUAL_REFERENCES.md` -> `REF-COMMUNITY-001`

Evidence/review layers:
- `KAVRIVA_LOGO_01_HANDOFF.md`, `KAVRIVA_LOGO_REVIEW.md`
- `KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md`, `KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`
- `KAVRIVA_ANCHOR_VISUAL_STYLE_01_HANDOFF.md`, `KAVRIVA_ANCHOR_VISUAL_STYLE_REVIEW.md`
- `SCREEN_INVENTORY_REVIEW.md`
- `SCREEN_FAMILY_SPEC_REVIEW.md`
- `KAVRIVA_AI_USTA_UX_STRUCTURE_01_HANDOFF.md`, `KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`
- `KAVRIVA_MAIN_SHELL_VISUALS_01_HANDOFF.md`, `KAVRIVA_MAIN_SHELL_VISUALS_REVIEW.md`
- `KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_01_HANDOFF.md`, `KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_REVIEW.md`
- `KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_01_HANDOFF.md`, `KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_REVIEW.md`
- `KAVRIVA_DIAGNOSIS_VISUALS_01_HANDOFF.md`, `KAVRIVA_DIAGNOSIS_VISUALS_REVIEW.md`
- `KAVRIVA_MAINTENANCE_REMINDER_VISUALS_01_HANDOFF.md`, `KAVRIVA_MAINTENANCE_REMINDER_VISUALS_REVIEW.md`
- `KAVRIVA_HISTORY_EVIDENCE_TRUST_VISUALS_01_HANDOFF.md`, `KAVRIVA_HISTORY_EVIDENCE_TRUST_VISUALS_REVIEW.md`
- `KAVRIVA_MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUALS_01_HANDOFF.md`, `KAVRIVA_MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUALS_REVIEW.md`
- `KAVRIVA_PROFILE_COLLABORATION_VISUALS_01_HANDOFF.md`, `KAVRIVA_PROFILE_COLLABORATION_VISUALS_REVIEW.md`
- `KAVRIVA_COMMUNITY_VISUALS_01_HANDOFF.md`, `KAVRIVA_COMMUNITY_VISUALS_REVIEW.md`

## Authority Boundaries

- L05A concept/direction authority'dir; production vector/font/palette/trademark clearance degildir.
- U04 active-guide anchor hierarchy authority'dir; universal full-app template degildir.
- V10 visual-DNA authority'dir; exact token/layout specification degildir.
- `SCR-001`–`SCR-038` contexts permanent route count degildir.
- Five-tab navigation: **Garaj · Bakim · AI Usta · Gecmis · Topluluk**.
- AI Usta UX role/entry label'idir; LLM/provider/backend architecture karari degildir.
- A1 root: compact motorcycle context + `Nasil yardimci olayim?` + known-task / symptom split. Unsupported technical-answer chatbot authority vermez.
- `REF-SHELL-001` exact tab icons/tokens/header geometry veya first landing tab'i finalize etmez.
- `REF-GUIDE-001`: task selection != fit; readiness application'dan once; blocked readiness bypass yok; D-series blue K drift logo degildir; generated tool/material examples technical truth degildir.
- `REF-ACTIVE-001`: saved UI progress physical proof degildir; continue-anyway yok; guide-change automatic reversal/guessing yok; partial/unresolved/safe-stop truthful outcomes'dur; reduced navigation PROPOSED ONLY.
- `REF-DIAG-001`: danger-first symptom capture, one discriminating check, supported-vs-unresolved outcomes; no random replacement/fabricated probability; photo contextual evidence'dir; supported result still fit/readiness'tan gecer; reduced navigation PROPOSED ONLY.
- `REF-MAINT-001`: no invented interval/date/mileage; snooze != completion; maintenance-to-guide continuity korunur; catch-up safety/use impact first but not a universal brake-first rule; uncertain timing remains uncertain; critical historical correction routine reminder degildir; deep-flow navigation remains PROPOSED ONLY.
- `REF-HISTORY-001`: current usable record meaning event history'den once gelir; actor/source/evidence/current claim state ayridir; no silent overwrite/fake winner; service role verification degildir; critical correction inactive/entitlement state'te de erisilebilir; basic history/provenance/correction/dispute/export retroactive paywall olamaz.
- `REF-LIFECYCLE-001`: inactive != delete/history lock; archive/inactive != transfer != delete; transfer partial coverage complete/verified gibi sunulamaz; delete independent/shared data sinirlarini korur; J05 v3 relevant new activity'yi gate ederken existing history/trust/safety/recovery access'ini korur; exact price/tier/quota/legal retention/permission implementation final degildir.
- `REF-PROFILE-001`: profile current approved local/core value icin zorunlu degildir; migration no-silent-loss/no-silent-overwrite + conflict review ile ilerler; helper/service role verification authority yaratmaz; revoke historical attribution/evidence'i silmez; private content ayridir. K01 generated absolute security/zero-loss wording ve shield/check art production authority degildir; auth/sync/backend/pricing final degildir.
- `REF-COMMUNITY-001`: community contribution explicit opt-in'dir; private/public scope gorunur kalir; publication/acceptance technical verification veya official-guide authority yaratmaz; photo attachment verification degildir; moderation reason + revise/resubmit/appeal/withdraw path tasir; withdrawal dependent provenance/history'yi sessizce silmez; L02 fixture date ve ornek brand/model/source moderation talepleri universal product rule degildir.
- Generated motorcycle/mechanical imagery identity/fit/diagnosis/maintenance evidence degildir.
- Community wording unsupported authenticity/verification iddiasi yaratamaz.
- Language/unit/accessibility support profile prerequisite olamaz.
- Internal Data/Content Operations requirement exact surface/technology/publishing architecture'i finalize etmez.

Ekran/gorsel otorite `REFERENCE_INDEX.md` icindeki APPROVED/LOCKED references ile kurulur.

### 04 Tech Strategy
Tartisma/oneridir. Tek basina kesin teknoloji karari olamaz. Internal Data/Content Operations da mobil sistemle birlikte bu asamada teknoloji alternatifleri acisindan ele alinmalidir.

### 05 ADR
Teknoloji/mimari kararlarinin gerekceli otoritesidir. APPROVED/LOCKED ADR'ler sonraki planlamayi baglar.

### 06 Delivery Planning
Onayli epic/capability/feature/flow/task ve dependency haritalarinin otoritesidir.

### 07 AI Architecture
Kodlama sirasinda AI davranisi, context routing, modul sinirlari, contract, validation, migration, rollback ve change-control kurallarinin otoritesidir.

### 08 Repository Bootstrap
Kesinlesen mimarinin fiziksel kurulum plani ve completion kanitlarinin otoritesidir.

## No Silent Rewrite

Kabul edilmis bilgi degisiyorsa eski karar iz birakmadan silinmez. Yeni kayit controlled refinement/supersession ile islenir ve changelog'a kaydedilir.
