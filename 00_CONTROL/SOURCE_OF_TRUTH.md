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

- `/AGENTS.md` — repository-wide AI manager contract
- `MANAGER_START_HERE.md` — canonical new-manager bootstrap
- `NEXT_ACTION.md` — single current work pointer
- `AI_START_HERE.md` — oturum bootstrap protokolu
- `CURRENT_STATE.md` — guncel durum
- `DECISION_LOG.md` — surec/proje karar kaydi
- `OPEN_QUESTIONS.md` — cozulmemis belirsizlikler
- `WORKFLOW_MAP.md` — 8 asama sirasi
- `PHASE_GATES.md` — gecis kosullari
- `DOCUMENT_REGISTRY.md` — kritik belge statuslari
- `CHANGELOG.md` — degisiklik izi
- `HANDOFF.md` — yeni AI devir ozeti
- `DRIVE_ARTIFACT_INDEX.md` — Drive-only task/research/review evidence links
- `PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md` — user-approved internal data/content operations requirement
- `PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md` — user-approved AI-safe task execution, Obsidian graph and completion-proof requirement
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

This requirement document did NOT itself decide web vs desktop vs hybrid, database/CMS/API/sync architecture, exact
publishing mechanics, AI provider/model, analytics stack or implementation technology. Later decisions now control the
live state: browser-based Internal Operations (`DEC-0021`) and the bounded Phase-4 directions indexed in
`CURRENT_STATE.md`. The original addendum remains requirement authority, not current technology-status authority.

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
- `03_DESIGN/FIRST_USE_MOTORCYCLE_CONTEXT_VISUAL_REFERENCES.md` -> `REF-FIRSTUSE-001`

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

Phase-3 user-approved working addendum for Internal Data & Content Operations:
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REVIEW.md`

SCR-004 accepted evidence:
- `03_DESIGN/KAVRIVA_FIRST_USE_SCR004_CANDIDATE_01.md`

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

Active reviewed strategy package:
- `04_TECH_STRATEGY/EVALUATION_CRITERIA.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-001__CLIENT_SURFACE_STRATEGY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-001__REVIEW_A_ARCHITECTURE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-001__REVIEW_B_SECURITY_OPERATIONS.md`
- `04_TECH_STRATEGY/JUDGE_SUMMARY.md`
- `04_TECH_STRATEGY/RISK_REGISTER.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-002__OFFLINE_SAFETY_RECALL_CLIENT_COMPATIBILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-002__REVIEW_A_PRODUCT_SAFETY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-002__REVIEW_B_PLATFORM_SECURITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-003__REVIEW_A_PROCESS_SAFETY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-003__REVIEW_B_SECURITY_RESILIENCE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__REVIEW_A_GOVERNANCE_PRIVACY_OPERATIONS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__REVIEW_B_IDENTITY_APPSEC_INGESTION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-005__REVIEW_A_RELEASE_GOVERNANCE_OPERATIONS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-005__REVIEW_B_SUPPLY_CHAIN_SECURITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__REVIEW_A_PRODUCT_DELIVERY_TCO.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__REVIEW_B_MOBILE_PLATFORM_MAINTENANCE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__REVIEW_A_ARCHITECTURE_ACCESSIBILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__REVIEW_B_SECURITY_OPERABILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__FOUR_WAY_EQUIVALENCE_AUDIT.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__RENDER_HOSTING_TIEBREAK.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__JUDGE_SYNTHESIS.md`

These documents authorize no framework/platform/provider. Their current authority is the compared alternatives,
reviewed risks, required evidence and next-debate boundaries only.

`DEC-0021` adds two binding working directions:
- planning produces no application code, prototype, proof-of-concept or executable spike;
- Internal Data & Content Operations is a browser-based web application.

This fixes the internal client form, not its frontend framework, backend, data, identity or deployment technology.

`DEC-0022` controls sub-agent model authorization: Luna Max (`gpt-5.6-luna`, `max`) is pre-authorized; every other
sub-agent model requires explicit user permission before use.

`DEC-0023` makes offline delivery data-efficient: packages are selected-motorcycle/task scoped, not full-library
downloads. Compact safety/application/recovery completeness is mandatory; heavy media is optional/on-demand.

`DEC-0024` approves the DEBATE-002 working direction: risk-tiered bounded offline eligibility, release/client
compatibility context, fail-closed critical uncertainty, preserved task-specific safe recovery and online-authoritative
Internal Operations mutations. Numeric limits and implementation technology remain open.

`DEC-0025` approves the independently reviewed DEBATE-003 working direction: complete immutable approval/release
meaning, fenced publication/suspension ordering, explicit unknown/partial states, independent narrow emergency negative
authority, restore quarantine and protected audit. Numeric targets, detailed governance and implementation technology
remain open.

`DEC-0026` approves the independently reviewed DEBATE-004 working direction: hybrid scoped/contextual authorization,
privileged account/session recovery, controlled policy administration, protected audit and quarantine-first layered
file/URL ingestion. Numeric policies, detailed governance and implementation/provider technology remain open.

`DEC-0027` approves the independently reviewed DEBATE-005 working direction: federated release authorities, exact
immutable artifact promotion, trust-root/verifier independence, artifact-bound provenance/SBOM, scoped signing/deployment
and a cross-domain compatibility/revocation graph. It does not approve an OTA channel or select a provider.

`DEC-0031` approves the DEBATE-006 equal S1–S15 no-code method and corrected common device/data/scale/cost fixture.
The fixture is comparison authority, not a final product limit.

`DEC-0032` approves Android-first/iOS-later publication sequencing and records direct Android access, borrowed-iPhone
access and the later TRY 2,000–3,000/month non-store planning ceiling.

`DEC-0033` approves Flutter as the consumer-mobile working direction after the complete equal no-code comparison.
RN/Expo is the first fallback. The decision is a Phase-5 ADR input, not code/build/device/release evidence or provider approval.

`DEC-0034` approves the provider-neutral data-backbone direction: canonical authority per domain, server/API-mediated
sensitive access, online-authoritative Internal Operations, bounded closed mobile packages, durable reconciliation,
separate current/history/protected-audit and object/media meanings, and cross-plane anti-resurrection recovery/exit.
It selects no engine, PostgreSQL/provider, BaaS, paid plan or physical architecture.

`DEC-0035` approves managed Supabase-centered as the reversible Phase-4 physical backend working direction, always behind
the Kavriva server/API authority boundary. RLS/Storage policies are defense in depth, Supabase Studio is not Internal
Operations, and database backup does not cover object/audit/floor recovery. Neon + independent API + R2 remains first
fallback. No account, region, plan, purchase, code, production proof or Phase-5 ADR is approved.

`DEC-0036` approves SQLite/Drift as the Flutter local-persistence working direction, complete compact selected-task
packages as the first-release offline baseline and a separate durable user-operation ledger through the Kavriva API.
Complex delta is deferred; PowerSync is first re-evaluation candidate and Realtime/push is hint only. Encryption/key
custody, versions, final limits and real evidence remain open; no code, service purchase or ADR is approved.

`DEC-0037` approves consumer Supabase Auth and local-first account-light as the reversible Phase-4 identity working
direction. Provider-qualified Kavriva principals, API authorization, security epoch, protected audit-before-effect,
end-to-end revoke, separate privileged recovery/emergency-negative authority, last-admin, owner-cost and exit gates are
binding. Privileged Internal Operations has no provider winner and remains held. No account, plan, factor, purchase,
implementation, second recovery actor or Phase-5 ADR is approved.

`DEC-0038` approves the corrected Kavriva API runtime working direction. Short DB-near Supabase Edge is a reversible
working hypothesis; managed container + worker is the equal-evidence alternative; both remain `HELD` with no production
runtime winner. Protected audit receipt/precondition, durable long-job semantics, complete commit-time authorization,
monotonic negative floors, end-to-end epoch, owner/support, normalized cost, restore/anti-resurrection and clean-room
exit are binding. No runtime/provider/plan/queue/account/code/deployment or Phase-5 ADR is approved.

`DEC-0039` approves the corrected DEBATE-012 working direction. React/Next, Angular, Vue/Nuxt and Svelte/SvelteKit
remain equal `HELD` with no framework winner. CSR-first static artifact/CDN + Kavriva API is the conditional Internal
Operations render/hosting starting direction; BFF, SSR/edge, container and privileged service worker remain need-
specific. This does not approve a framework, component library, host, provider, account, plan, code, deployment, ADR or
Gate 4 -> 5 transition.

`DEC-0040` establishes the external-AI operating boundary: Google Drive carries task/context/research/review/decision/
handoff artifacts and GitHub carries repository-native work. External AIs do not receive or depend on the user's
computer. Every job requires a task-addressed minimum context pack, explicit GitHub scope, acceptance evidence and
independent review. Exact Drive links and queue structure are registered in
`00_CONTROL/EXTERNAL_AI_DRIVE_GITHUB_WORKFLOW.md`.

`DEC-0043` establishes the GitHub cross-manager continuity package. `/AGENTS.md` defines repository-wide AI behavior;
`00_CONTROL/MANAGER_START_HERE.md` is the canonical bootstrap; `00_CONTROL/NEXT_ACTION.md` is the single volatile work
pointer; `00_CONTROL/DRIVE_ARTIFACT_INDEX.md` links Drive-only evidence. Compatibility prompts/handoffs may point to
these authorities but must not maintain a competing current-state copy.

`DEBATE-013 — CMS and Controlled Publishing Mechanics` is a completed, user-approved Phase-4 working direction. Its Drive context pack
`CTX-P4-013` and `TASK-001` route external research but do not themselves create decision authority. TASK-001 research
and handoff were delivered, and `REVIEW-001` returned `CHANGES_REQUESTED`. Major M1 was remediated: manager readback
verified S1–S12, 48 A–D rows and all seven required field labels per row. Independent REVIEW-002 then returned PASS
with no Critical, Major or Minor findings. TASK-001 is DONE. The user then approved the manager synthesis under
`DEC-0042`. No CMS architecture family/product/provider, account, plan, purchase, code or ADR is approved.

`DEC-0042` approves the DEBATE-013 working direction: Kavriva owns technical truth, applicability, approval, immutable
release, recall/suspension, package eligibility and final publication authority. A CMS may be evaluated later only as a
bounded, replaceable authoring adjunct. No CMS/provider/product/account/plan/purchase/code/deployment or Phase-5 ADR is approved.

`DEC-0044` approves the DEBATE-014 analytics/measurement working direction. Canonical operational coverage/data-quality
metrics and protected evidence remain Kavriva-owned; product analytics remains optional, minimized, non-authoritative
and replaceable; reliability/observability remains separate and provider-neutral where feasible; split/hybrid is the
reversible Phase-4 architecture shape and a smaller Kavriva-owned measurement baseline is the fallback when evidence
gates are not met. No analytics/observability provider, account/plan, SDK integration, final KPI, legal conclusion or
Phase-5 ADR is approved.

`DEC-0045` approves the DEBATE-015 mobile build/release working direction. Android release continuity remains active and
independent of iOS/macOS readiness; split/hybrid is the reversible Phase-4 operating shape; iOS/macOS activation remains
HELD until real Mac/Xcode access, Apple signing custody, provider-neutral provenance, no-owner-debug recovery and
clean-room rebuild are proven. No physical Mac/hosted-Mac/CI/mobile-CI/Xcode-Cloud provider or plan, account, purchase,
build, signing setup, final budget or Phase-5 ADR is approved.

`DEC-0028` establishes the project-wide AI-native execution requirement: Obsidian-compatible relationship graph,
contract-governed task-addressable modules, minimum sufficient task context packs, bidirectional requirement/task/test
closure, no-code task simulation, canonical multi-AI design rules and completion proof beyond `all tasks DONE`.

`DEC-0029` establishes the operating model: a nontechnical product owner directs an AI-operated project. The user is not
a developer/debugger; technical work and translation belong to the AI system, with independent evidence and explicit
external dependencies where legal identity, store ownership or qualified human/organizational authority is unavoidable.

`DEC-0030` establishes solo ownership and limited budget as a project constraint. Paid services, devices or experts may
not be assumed; staged current pricing, free path, billing/overage and deferral must be shown before approval. Exact spend
ceiling remains open and unaffordable mandatory assurance produces `HELD`, not a weaker hidden standard.

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
