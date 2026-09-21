# PHASE GATES

Her asama icin giris, cikis ve onay kapisi vardir. Bir AI sonraki asamaya kendiliginden gecemez.

## Gate 1 -> 2
Calisma sistemi, source-of-truth, karar/varsayim/kisit/glossary mekanizmalari hazir ve tutarli olmali.

## Gate 2 -> 3
Urun kesfi yeterli kapsama ulasmali; ana urun ozeti, kullanici tipleri, yolculuklar, is kurallari ve non-goals sentezlenmis olmali.

## Gate 3 -> 4
Ekran katalogu, navigasyon haritasi, onemli state'ler ve onayli referans indeksleri yeterli kapsama ulasmali. Approved project-scope addendum geregi Internal Data & Content Operations icin product requirements, workflow/lifecycle ve platform-independent screen/workspace architecture kapsami da teknoloji secmeden tamamlanmis olmali.

## Gate 4 -> 5
Uzman AI gorusleri ve judge sentezi tamamlanmali; teknoloji alternatifleri, riskler ve trade-off'lar acik olmali.

## Gate 5 -> 6
Gerekli teknoloji kararlarinin ADR kayitlari APPROVED/LOCKED durumda olmali. AI-safe modul/contract/repository
topolojisi, graph metadata/kimlik ve dependency yonu kararlarini gerektiren ADR kapsami belirlenmis olmali.

## Gate 6 -> 7
Epic, capability, feature, user flow ve atomik task haritasi ile bagimliliklar ve acceptance criteria yeterli olmali.
Requirement-to-task-to-test izlenebilirligi iki yonlu kapanmali; yetim/gap/conflict taramasi ve no-code task/dependency/
failure/rollback/closure simulasyonu gecmis olmali.

## Gate 7 -> 8
AI-native mimari; context routing, minimum context pack, Obsidian-compatible graph metadata, modul sinirlari, public
contract, dependency/design/change-control, validation, migration, rollback, completion evidence ve architecture-test
kurallariyla tamamlanmis olmali.

## Gate 8 -> Development
Bootstrap checklist tamamlanmali; repository + Obsidian graph + task registry + CI/architecture/design/traceability
kontrolleri kurulup ornek gorevle dogrulanmali. Gercek kodlama ancak bundan sonra baslar.
## Current Gate Status — 2026-09-21

- Gate 3 -> 4: PASSED.
- Phase 4 Technology Strategy: working-direction question set `TSQ-001`–`TSQ-018` completed at direction level.
- Gate 4 -> 5: **PASSED under `DEC-0048` on 2026-09-21** after the fresh-manager closure/readiness audit and explicit owner approval.
- Phase 5 (ADR) is authorized to begin. No ADR is created by the gate passage itself; each ADR requires its own explicit owner approval.
- HELD provider/numeric/device/implementation/production evidence was classified during the audit as legitimate later-phase evidence, not Phase-4 blockers; it must still not be silently forced into premature provider/implementation decisions.

