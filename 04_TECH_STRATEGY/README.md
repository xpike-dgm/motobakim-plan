# 04 — TECHNOLOGY STRATEGY

Amac: Kesin teknoloji karari vermeden once alternatifleri uzman rolleriyle tartismak.

Girdiler: onayli urun sentezi + tasarim envanteri/referanslari + kisitlar.
Cikti: karsilastirmali oneriler, riskler, trade-off'lar ve Architect/Judge sentezi.
Kod yazilmaz. Bu yasak throwaway prototype, proof-of-concept, executable spike ve deneme uygulamasini da kapsar.
Karsilastirma; resmi/birincil kaynak arastirmasi, urun senaryosu uzerinden mimari walkthrough, failure-mode analizi,
TCO/operasyon incelemesi ve bagimsiz AI elestirisi ile yapilir.

## Status

`ACTIVE — NO-CODE / INTERNAL WEB DIRECTION APPROVED / FLUTTER WORKING DIRECTION APPROVED`

Phase 4, 2026-09-17 tarihinde kullanicinin acik `tamamdir baslayalim` talimatiyla baslatildi.
Internal Operations browser-based client formu `DEC-0021` ile user-approved working direction'dir. Bunun disindaki
implementation platform/framework/service/provider onerileri Phase 5 ADR olmadan `APPROVED/LOCKED` sayilmaz.

## Active Topic

- `DEBATE-014 — Analytics and Measurement Strategy`
  - opened from the existing unresolved analytics/measurement scope by explicit user direction,
  - requirements synthesis is complete at research-contract level,
  - Drive `CTX-P4-014` is published; primary research and HANDOFF-TASK-002 are complete and TASK-002 is DONE,
  - manager intake verified four equal families, two mechanisms per family, a 30-row official-primary source ledger and 16 × 4 = 64 failure rows with all eight required fields,
  - independent `REVIEW-003` returned `CHANGES_REQUESTED`: no Critical/Minor findings and one Major M-1 limited to S15 clean-room replacement / Family D field substance; required official-source spot-checks found no material contradiction,
  - the scoped S15-D remediation is complete; REVIEW-004 returned PASS with no findings and TASK-002 is in Drive `06_DONE`,
  - research separates product analytics, operational analytics, observability and protected audit; manager synthesis is ready for explicit user decision and missing evidence remains HELD,
  - no provider/account/plan/code/SDK integration/final KPI/ADR or Gate 4 -> 5 transition.

## Most Recently Completed Topic

- `DEBATE-013 — CMS and Controlled Publishing Mechanics`
  - selected from the existing unresolved CMS/publishing scope,
  - compares Kavriva-owned workflow, open-source headless CMS, managed headless CMS and a controlled hybrid,
  - Drive research and handoff delivered; independent REVIEW-001 returned `CHANGES_REQUESTED`,
  - Major M1 remediation now supplies 12 scenarios × four families = 48 rows, each with all seven required fields,
  - independent REVIEW-002 returned PASS with no Critical/Major/Minor findings; TASK-001 is DONE,
  - manager direction is user-approved under `DEC-0042`: Kavriva owns technical authority and CMS remains an optional,
    replaceable authoring adjunct,
  - no code, provider account, trial, purchase, deployment or ADR.

Earlier completed topics:

- `DEBATE-012 — Internal Operations Web Frontend and Hosting`
  - opened after the user explicitly asked to continue with the next existing Phase-4 area,
  - requirements, official research, failure/TCO work, two independent reviews, task/equivalence audit, component and
    render/hosting tie-breaks are complete,
  - the initial React conditional-leader language was withdrawn; React/Next, Angular, Vue/Nuxt and Svelte/SvelteKit are
    equal `HELD` with no winner,
  - corrected Judge proposes CSR-first static artifact/CDN + Kavriva API as a conditional starting direction; BFF,
    SSR/edge, container and privileged service worker require separate evidence,
  - corrected direction is user-approved under `DEC-0039`; no framework/provider/account/plan/code/ADR.

- `DEBATE-011 — Kavriva API Runtime, Boundary Enforcement and Operations`
  - repository requirements, current official runtime research and 18 failure/TCO scenarios complete,
  - Supabase Edge, managed container, Cloudflare Workers, Cloud Run and self-managed/reference paths compared,
  - manager proposal and two independent Luna Max adversarial reviews complete; both finalists remain held,
  - corrected Judge keeps short DB-near Supabase Edge as a reversible working hypothesis and managed container + worker
    as an equal-evidence alternative, with no runtime winner,
  - protected audit receipt/precondition, long-job queue/worker gate, monotonic negative floors, no-owner-debug,
    normalized safe cost, restore/anti-resurrection and clean-room exit are mandatory,
  - corrected direction is user-approved under `DEC-0038`; no production runtime winner,
  - no runtime/provider/plan/queue/account/code/ADR.

- `DEBATE-010 — Identity, Session, Account Recovery and Privileged Access`
  - repository requirements, current official provider research and 15 failure/threat scenarios complete,
  - two independent Luna Max adversarial reviews complete; both candidates are held and there is no privileged winner,
  - corrected Judge keeps consumer Supabase Auth + local-first account-light as the conditional proposal,
  - privileged production requires end-to-end revoke, protected audit-before-effect, separate recovery/negative authority,
    phishing-resistant transaction-bound fixtures, last-admin, normalized cost and exit closure,
  - corrected direction is user-approved under `DEC-0037`; no privileged provider winner,
  - no IdP account/plan/factor/purchase/code/ADR.

- `DEBATE-009 — Flutter Offline Data, Package and Sync Strategy`
  - research, equal Drift/PowerSync dossiers, task simulation, equivalence audit and two reviews complete,
  - corrected Judge recommends Drift local persistence + complete compact selected-task packages + durable operation API,
  - complex delta is deferred; PowerSync remains first re-evaluation candidate and Realtime/cache is hint only,
  - corrected direction is user-approved under `DEC-0036`,
  - no code, prototype, local database/sync provider approval, subscription or ADR.

- `DEBATE-008 — Physical Data/Backend Stack and Provider Candidates`
  - current official research, controlled external-report audit and equal finalist dossiers complete,
  - equivalence normalization and two independent Luna Max reviews complete,
  - reviewers split between Supabase-centered solo-owner operability and Neon+Render+R2 recovery/exit explicitness,
  - managed Supabase-centered behind the mandatory Kavriva API boundary is user-approved under `DEC-0035` as the
    reversible Phase-4 working direction; modular managed remains first fallback,
  - no provider account, subscription, purchase, code, production proof or ADR.

- `DEBATE-007 — Data Backbone and Logical Service Boundaries`
  - internal requirements, official/primary research and controlled external-report intake complete,
  - manager draft, two independent reviews and corrected Judge synthesis complete,
  - provider-neutral direction is user-approved under `DEC-0034`,
  - no engine, provider, physical architecture, paid service, code or ADR selected.

- `DEBATE-006 — Mobile Technology Evidence, Team & TCO`
  - two Luna Max research tracks and two independent Luna Max reviews complete,
  - both reviews allow continued Phase-4 work but reject ADR readiness; critical changes incorporated,
  - the equal five-candidate dossier and final tie-break stages are complete,
  - common fixture/evaluation direction is user-approved under `DEC-0031`,
  - five equal dossiers, equivalence audit, two independent critiques and Judge synthesis are complete,
  - equal task simulation and final Flutter/RN dependency/rebuild/release tie-break work are complete,
  - Flutter is the user-approved conditional working direction under `DEC-0033`; RN/Expo remains first fallback,
  - no framework ADR, provider, OTA channel, implementation or real build/device pass exists.

Prior reviewed topic:

- `DEBATE-005 — Software, Content Supply Chain & Release Governance`
  - user-approved working direction under `DEC-0027`.
- `DEBATE-004 — Identity, Scoped Authorization, Audit & Untrusted Ingestion`
  - user-approved working direction under `DEC-0026`.
- `DEBATE-003 — Approval, Publication & Emergency Suspension Integrity`
  - user-approved working direction under `DEC-0025`.
- `DEBATE-002 — Offline Safety, Recall & Client Compatibility`
  - user-approved working direction under `DEC-0024`.
- `DEBATE-001 — Client Surface Strategy`
  - Internal Operations browser direction approved,
  - consumer mobile technology remains open.

## Operating Rule

Her konu icin once urun kaynaklarindan kriterler turetilir, sonra birincil teknik kaynaklarla
alternatifler arastirilir. Manager taslagi iki bagimsiz AI elestirmenine verir; elestiriler ve
Architect/Judge sentezi kayda gecmeden konu ADR adayi olarak kapanmaz.
