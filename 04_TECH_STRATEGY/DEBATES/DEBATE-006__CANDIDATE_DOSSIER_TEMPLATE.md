# DEBATE-006 — EQUAL MOBILE CANDIDATE DOSSIER TEMPLATE

Status: `CONTROLLED TEMPLATE / NO-CODE / DEC-0031 FIXTURE`
Date: 2026-09-17

## 1. Candidate Identity

- Candidate family:
- Exact evaluated version/snapshot:
- Evidence retrieval date:
- Product-supported Android/iOS floor tested against:
- Framework-supported floor:
- Build-tool/store floor:
- Support/EOL statement:
- Dossier author/reviewer:

Dynamic `latest` claims are not sufficient. Record an exact snapshot and distinguish official evidence, reasoned inference,
dependency-specific evidence and unresolved facts.

## 2. Fixed Inputs

This dossier must use without candidate-specific relaxation:

- `DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md` S1–S15;
- `DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md` approved under `DEC-0031`;
- `DEC-0023`–`DEC-0031` constraints;
- DEBATE-002–005 safety, authorization and release-integrity directions;
- approved Phase-3 design and accessibility truth.

Any required fixture change stops comparison and opens one revision for all five candidates.

## 3. Candidate Architecture Boundary

Document without implementation code:

- UI ownership and platform-specific UI exceptions;
- domain/data logic ownership;
- local persistence, encryption/key, migration and backup boundaries;
- sync/reconciliation and offline-package boundaries;
- camera/file/media, notification/deep-link and background-transfer boundaries;
- accessibility semantics and platform exceptions;
- store build/signing/release boundary;
- Internal Operations/API/content contract boundary;
- portable data and framework-exit boundary.

## 4. Native and Dependency Closure

| Capability | Built-in/framework path | Dependency/plugin | Native code/skill required | Lifecycle/threading constraints | Accessibility impact | Fallback/replacement | EOL/security owner | Status |
|---|---|---|---|---|---|---|---|---|

Every critical capability must be `PASS`, `HELD` or `REJECT`. An unnamed future plugin or owner is `HELD`.

## 5. Equal S1–S15 Scenario Record

Repeat the following record for every scenario:

### Sx — Scenario name

- authoritative starting state:
- allowed transition:
- candidate mechanism:
- official evidence:
- reasoned inference:
- dependency-specific evidence:
- unresolved facts:
- user-visible result:
- failure/hold behavior:
- recovery path:
- shared-system obligation:
- candidate-attributable work:
- accountable AI/external owner:
- required later real-device evidence:
- residual risk:
- result: `PASS / HELD / REJECT`

No aggregate score can override a safety, data-continuity, accessibility, release-integrity or recoverability failure.

## 6. Accessibility Matrix

Apply to Turkish readiness, warning, unexpected-state stop, safe recovery and active-step flows:

| Check | Framework/documented capability | Platform-specific work | Later real-device oracle | Status |
|---|---|---|---|---|
| VoiceOver | | | | |
| TalkBack | | | | |
| Largest text/reflow | | | | |
| Focus and reading order | | | | |
| State announcements | | | | |
| Non-color status/contrast | | | | |
| Reduced motion | | | | |
| Switch/voice control | | | | |
| Reduced dexterity | | | | |

API availability is not a device pass.

## 7. Upgrade and Forced-Event Walkthrough

Walk through:

- one normal planned release window;
- one safety/security emergency correction;
- one forced Apple/Google build/store requirement change;
- abandonment or incompatibility of one critical dependency;
- coexistence of old/new client, API, schema, content and configuration;
- rollback refusal when data migration cannot be safely reversed;
- incident pause, impact identification, correction and recovery.

Record affected toolchains, tasks, evidence, external dependencies, duration/capacity uncertainty and release-hold behavior.

## 8. AI-Operability and Task Isolation

| Question | Evidence/result |
|---|---|
| Can a fresh AI implement one bounded task without whole-project context? | |
| Are platform exceptions visible in the task graph? | |
| Can implementation, review and validation remain separate? | |
| Are builds/tests deterministic enough to produce evidence? | |
| Can dependency changes identify affected contracts/tasks/tests? | |
| Can the project recover without one opaque workstation/provider? | |
| Does the candidate require unavailable human specialist authority? | |

User coding, debugging or build repair is not a mitigation.

## 9. Equal 24-Month TCO Worksheet

Calculate the approved 1,000/10,000/50,000 MAU workload separately. Do not multiply the local-device stress fixture by MAU.

| Cost row | Product-wide unavoidable | Candidate-caused | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---:|---:|---:|---:|---:|---|---|
| Store membership | | | | | | | |
| Mac/hosted build | | | | | | | |
| Android/iPhone access | | | | | | | |
| CI/build artifacts | | | | | | | |
| Backend/database | | | | | | | |
| Storage/backup/CDN/egress | | | | | | | |
| Identity/email/SMS | | | | | | | |
| Crash/telemetry/analytics | | | | | | | |
| Security/SBOM/signing | | | | | | | |
| Accessibility validation | | | | | | | |
| Safety/content review | | | | | | | |
| AI implementation/review | | | | | | | |
| Upgrade/dependency response | | | | | | | |
| Support/incident response | | | | | | | |
| Exit/migration | | | | | | | |

Unknown amounts remain `UNRESOLVED`; they are never entered as zero. A free tier passes only with cap/overage control,
spend alert, export and exit evidence.

## 10. Exit Dossier

State what survives framework replacement:

- content/data schema and history/provenance;
- offline-package and compatibility fixtures;
- media and exports;
- identity/key/account continuity;
- design tokens, copy and accessibility intent;
- tests and acceptance oracles;
- native modules/platform integrations;
- staged replacement release and migration route.

## 11. Candidate Result

- mandatory-gate result:
- S1–S15 result count:
- unresolved critical facts:
- largest low-budget burden:
- largest AI-operability benefit/risk:
- external authorities/capacity required:
- conditions for recommendation:
- disqualifiers triggered:
- overall Phase-4 status: `RECOMMENDABLE / VIABLE WITH CONDITIONS / HELD / REJECTED`

This result is documentary Phase-4 evidence. It cannot claim a build, benchmark, real-device pass or store release.
