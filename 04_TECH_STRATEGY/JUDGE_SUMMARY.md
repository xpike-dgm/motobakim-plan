# ARCHITECT / JUDGE SUMMARY

Status: `DEBATE-001–007 REVIEWED / PHASE-4 ACTIVE / DEBATE-007 USER-APPROVED DIRECTION`

## DEBATE-001 — Client Surface Strategy

### Inputs

- manager research and proposal,
- Reviewer A: Architecture, Mobile & Scale — `PASS_WITH_CHANGES`,
- Reviewer B: Security, Operations, Failure Modes & Cost — `PASS_WITH_CHANGES`,
- revised canonical debate.

### Areas of Agreement

1. At the DEBATE-001 review point, no consumer mobile framework could be selected responsibly from the then-current evidence.
2. Flutter and React Native with a defined framework/native boundary are reasonable first no-code evidence candidates.
3. KMP-native remains an escalation/reference candidate; KMP+Compose is a separate option, not the same score.
4. Review evidence favored browser web; the user subsequently selected it. Desktop packaging is outside the current
   direction and can return only through a new explicit user decision.
5. Consumer and operator surfaces must not share authority. Server-side policy, review and publication control
   cannot be replaced by UI restrictions.
6. Offline storage is not offline correctness; background execution is opportunistic; fully offline recall has a
   physical limit that requires product/architecture policy.
7. Physical publication storage/projection, emergency suspension, compatibility, RBAC/audit and release governance
   are separate decisions.

### Corrections Accepted by Manager

- unsupported numerical scores removed;
- KMP/native and KMP/Compose split; fully native reference baseline added;
- web optional shell changed from a scored alternative to an extension policy;
- “required read-model projection” reduced to a logical trust boundary;
- resume test now restores context but requires safety/physical-state revalidation;
- fully offline expiry, old client, race, immutable snapshot, hostile ingestion, stale tab and emergency suspension
  scenarios added;
- Phase 4 comparison is no-code and specifies scenario/evidence walkthroughs only;
- risk register expanded toward owner/signal/trigger/contingency/residual-risk tracking.

### Judge Determination

`PASS_WITH_CHANGES — CHANGES INCORPORATED FOR DEBATE CONTINUATION`.

At review time this meant the client-surface direction was ready to present. Before the later user decision it did
**not** mean:

- Flutter or React Native is selected;
- web was not yet approved as the Internal Operations form (the user subsequently approved browser-based form);
- a publication projection/read store is selected;
- offline recall, emergency suspension or old-client safety is solved;
- Gate 4 -> 5 is passed.

### User Decision Received

The user explicitly decided:

1. no application code, prototype or executable spike will be written during planning;
2. deep research and independent AI critique may be used;
3. Internal Operations will be browser-based.

This historical DEBATE-001 hold was later narrowed by DEBATE-006. The logical service boundary remains open. Work was split into:
   - offline safety/recall/compatibility,
   - approval/publishing/emergency suspension,
   - identity/RBAC/audit/hostile ingestion,
   - supply-chain/release governance,
   - staffing/TCO and comparable no-code evidence specification.

### ADR Readiness

The browser-based Internal Operations form is binding user direction and a Phase-5 ADR input. No Phase-5 ADR is
created yet. Flutter is now the user-approved DEBATE-006 working direction under `DEC-0033`; Gate 4 -> 5 remains closed.

---

## DEBATE-002 — Offline Safety, Recall & Client Compatibility

Status: `REVIEW COMPLETE — USER APPROVED WORKING DIRECTION / ADR PENDING`

### Inputs

- repository product-policy synthesis by Luna Max,
- official iOS/Android/Firebase evidence research by Luna Max,
- manager C+D policy draft,
- independent Product Safety/User Trust review — `PASS_WITH_CHANGES`,
- independent Mobile Platform/Security/Operations review — `PASS_WITH_CHANGES`.

### Areas of Agreement

1. A fully offline device cannot learn a new recall immediately; the product must bound this risk, not deny it.
2. Push/background work is advisory, never recall authority.
3. Unlimited cached physical application is incompatible with approved freshness/recall rules.
4. Always-online application is safest but unnecessarily destroys approved offline value for every category.
5. Risk-tiered bounded eligibility plus release-bound context is the strongest balanced direction.
6. Unknown/unclassified or stale dependent risk holds application and inherits the highest consequence.
7. Offline start requires complete task-specific safe-stop/recovery coverage for every reachable physical state.
8. Restored backup, old client, time anomaly or mixed release cannot create new positive authority.
9. Browser authoritative actions stay online; network timeout may be `outcome unknown`, not assumed failure/success.

### Critical Corrections Accepted

- release identity was strengthened into required integrity/capability/anti-rollback properties without choosing technology;
- risk dependency propagation and safe unknown defaults added;
- recovery coverage made an offline-start prerequisite;
- recall-after-check residual race recorded rather than claimed solved;
- server/client/last-reconciled recall knowledge separated;
- old-client base envelope/pre-use capability negotiation added;
- browser stale-session/idempotent unknown-result reconciliation added;
- perfect recovery after unexpected device/storage loss is no longer promised.

### Judge Determination

`PASS_WITH_CHANGES — SUFFICIENT FOR USER WORKING-DIRECTION DECISION, NOT ADR`.

### User Decision

The user approved these principles under `DEC-0024`, not numeric limits or implementation:

1. risk-tiered limited offline physical application;
2. exact release/client compatibility context for downloaded guides;
3. critical uncertainty closes normal application but preserves teaching/history/task-specific safe recovery;
4. Internal Operations approval/publish/recall actions require an online authoritative result.

### Still Open

- highest-consequence always-online boundary;
- numeric validity windows and accountable approval roles;
- exact emergency suspension/outage/reach-back design;
- long-dormant client support window;
- backup/data classification mechanics;
- mobile framework and all physical implementation choices.

No ADR is ready and Gate 4 -> 5 remains closed.

---

## DEBATE-003 — Approval, Publication and Emergency Suspension Integrity

Status: `REVIEW COMPLETE — USER APPROVED WORKING DIRECTION / ADR PENDING`

### Inputs

- approved Internal Data & Content Operations requirements/lifecycle;
- DEBATE-002 online-authority and recall constraints;
- Luna Max repository-policy synthesis;
- Luna Max primary standards/security research;
- independent Process Safety/User Trust review — `PASS_WITH_CHANGES`;
- independent Security/Resilience review — `PASS_WITH_CHANGES`.

### Areas of Agreement

1. Approval must bind the complete immutable served meaning, not a mutable record or only the authoring fields.
2. Publication requires one guarded transition over exact release, approval/dependency, current-release and suspension generations.
3. Browser timeout is an explicit `outcome unknown`; retries reconcile the same bound operation identity.
4. Authoritative-current, delivery-observed and consumer-reconciled are different states.
5. Emergency suspension is a narrow negative authority and cannot create replacement technical truth.
6. Normal publication cannot clear or outrun a newer suspension; unknown critical authority fails closed.
7. Restore enters quarantine until release/suspension floors, audit continuity, content integrity and key trust reconcile.
8. Break-glass action still requires durable protected evidence and later reconciliation.
9. Rollback is a new event to a still-valid known-good release; otherwise suspend rather than guess.

### Critical Corrections Accepted

- derived artifacts/localization/templates/media/configuration added to approval closure;
- release and suspension authorities fenced with monotonic generations;
- partial propagation now has consequence-tiered known-safe/reference-only/hold behavior;
- emergency operations gained idempotent identity, unknown-outcome and status reconciliation;
- overlapping scope uses dependency-aware most-restrictive negative precedence;
- infrastructure outage, known suspension and unknown suspension are distinct states;
- audit-outage fallback requires independent tamper-detectable evidence;
- emergency common-mode dependencies require a matrix and actual drills.

### Judge Determination

`PASS_WITH_CHANGES — CHANGES INCORPORATED FOR USER WORKING-DIRECTION DECISION; NOT ADR-READY`.

The recommended B+C direction is coherent: controlled immutable release plus independent narrow emergency suspension.
The user approved it under `DEC-0025`. Numeric targets, exact scope/role/quorum policy, failure-domain topology and
technology remain open. Gate 4 -> 5 remains closed.

---

## DEBATE-004 — Identity, Scoped Authorization, Audit and Untrusted Ingestion

Status: `REVIEW COMPLETE — USER APPROVED WORKING DIRECTION / ADR PENDING`

### Inputs

- approved IDCO role/audit/source/provenance requirements;
- DEBATE-003 publication, emergency and protected-audit direction;
- Luna Max governance/capability synthesis;
- Luna Max primary identity/AppSec research;
- independent Governance/Privacy/Operations review — `PASS_WITH_CHANGES`;
- independent Identity/AppSec/Ingestion review — `PASS_WITH_CHANGES AS DIRECTION / REJECT AS ADR`.

### Areas of Agreement

1. Role labels and browser UI are not authority; every sensitive request is server-authorized against current context.
2. Hybrid base roles plus scope/state/consequence/independence policy is clearer and safer than flat roles or opaque rules alone.
3. High-consequence self-approval/self-publication is prohibited; unavailable independence holds work rather than weakening policy.
4. Privileged recovery must invalidate relying-party sessions and pending high-consequence authorizations, not only reset an authenticator.
5. Authorization policy and access administration are controlled high-consequence objects, not an unrestricted admin shortcut.
6. Audit requires protected ordered evidence, independent custody and explicit outage/restore behavior.
7. Uploads and fetched URLs remain quarantined/untrusted through layered checks; scanning/preview never proves technical correctness.
8. Unknown/mixed classification uses the most restrictive handling and propagates to derivatives and exports.
9. Export is a disclosure event; link revocation cannot retract an already copied/downloaded result.
10. AI/OCR output is attributable proposal-only and hostile document instructions have no tool/policy/workflow authority.

### Critical Corrections Accepted

- account/session security epoch and complete privileged compromise/recovery transition;
- versioned authorization-policy author/approve/activate separation plus non-retroactive semantics;
- normative minimum audit evidence, integrity/order/fork detection and protected fallback;
- small-team `HELD` state instead of self-approval;
- delegation/competence/alias/service-account accumulation checks;
- `SAFE_FOR_HUMAN_REVIEW` replaces misleading evidence-eligibility wording;
- isolated-origin preview with no ambient authority/native-viewer shortcut;
- stricter URL connection/redirect/address validation;
- classification propagation, export field preview and residual-copy warning;
- explicit result oracles for all acceptance scenarios.

### Judge Determination

`PASS_WITH_CHANGES — CHANGES INCORPORATED FOR USER WORKING-DIRECTION DECISION; NOT ADR-READY`.

The corrected hybrid direction is coherent and vendor-neutral. The user approved it under `DEC-0026`. Numeric values,
exact role matrix, competence/governance owners, file/source classes, retention/legal policy and physical implementation
remain open. Gate 4 -> 5 remains closed.

---

## DEBATE-005 — Software, Content Supply Chain and Release Governance

Status: `REVIEW COMPLETE — USER APPROVED WORKING DIRECTION / ADR PENDING`

### Inputs

- approved DEBATE-002/003/004 compatibility, publication, emergency, authorization and audit directions;
- Luna Max release-authority/repository synthesis;
- Luna Max primary supply-chain/build/signing evidence research;
- independent Release Governance/Operations review — `PASS_WITH_CHANGES`;
- independent Supply-Chain Security review — `PASS_WITH_CHANGES AS DIRECTION / REJECT AS ADR`.

### Areas of Agreement

1. Mobile binary, internal web, backend/data, technical content, configuration and emergency controls are distinct authorities.
2. Production promotes the exact verified immutable artifact and does not rebuild it.
3. Provenance, SBOM, signature and transparency evidence bind exact digests but never prove software is safe/correct.
4. Trust includes repository/workflow policy, builder bootstrap, toolchain/cache, verifier, signer, promoter and deployment target.
5. One closed compatibility graph binds client/API/schema/content/config/migration/offline recovery and revocation generations.
6. Current eligibility/revocation is distinct from artifact authenticity and prior approval.
7. Every release/restore domain is fenced by the current emergency suspension/revocation generation.
8. Migration/data recovery differs from binary rollback and must preserve new valid data plus audit/revocation truth.
9. Stopping rollout does not downgrade updated clients; offline/dormant clients retain an explicit residual revocation race.
10. No OTA channel is approved; any future proposal needs its own root/threshold/expiry/anti-rollback envelope.

### Critical Corrections Accepted

- independent verifier and trust-root matrix;
- policy-bound dependency-closure states and hardened/reproducible builder assurance;
- monotonic artifact revocation impact and store/account recovery semantics;
- cross-domain release-meaning graph and runtime verification;
- exact effective configuration closure and non-scriptable envelope;
- explicit migration and rollout state machines;
- high-consequence human independence with small-team `HELD` fallback;
- offline task-package/data-efficiency and classification closure;
- protected impact graph outside compromised delivery planes;
- acceptance tests require authoritative outcomes and residual risk.

### Judge Determination

`PASS_WITH_CHANGES — CHANGES INCORPORATED FOR USER WORKING-DIRECTION DECISION; NOT ADR-READY`.

The corrected federated/provenance-bound direction is coherent and vendor-neutral. The user approved it under `DEC-0027`.
Exact assurance tiers, formats, staffing, keys, support windows, numeric controls and implementation remain open.
Gate 4 -> 5 remains closed.

---

## DEBATE-006 — Mobile Technology Evidence, Team and TCO

Status: `FINAL NO-CODE TIE-BREAK COMPLETE / FLUTTER USER-APPROVED WORKING DIRECTION / ADR PENDING`

### Inputs

- approved product/design truth and DEBATE-001–005 constraints;
- Luna Max common-scenario/team/TCO evidence synthesis;
- Luna Max current official Flutter, React Native/Expo, KMP/Compose and native-platform research;
- independent Product Delivery/Scenario Fairness/Team/TCO review — `PASS_WITH_CHANGES`;
- independent Mobile Platform/Accessibility/Dependency/Maintenance review — `PASS_WITH_CHANGES AS DIRECTION / REJECT AS ADR`.

### Areas of Agreement

1. Framework choice does not solve offline truth, recall, sync, migration, release compatibility or physical-state safety.
2. All five options need the same Kavriva fixtures, states, evidence schema and rejection rules.
3. Background execution and push are optimizations, never correctness or recall authority.
4. Restart restores at most the last durable checkpoint; current physical truth must be re-established.
5. Accessibility APIs or stable status do not prove critical Turkish flows on actual assistive technologies/devices.
6. Camera/files/background/storage/security capabilities make native ownership baseline work for every option.
7. Product-supported, framework-supported, CI-tested, build-tool and store requirements are different policies.
8. OTA remains disabled/unapproved and cannot be counted as a delivery benefit.
9. Team capability, backup coverage and 12–24 month operating capacity can legitimately change the best option.
10. Native escape is not an exit plan; portable data/trust continuity and replacement release must be explicit.

### Critical Corrections Accepted

- finalist/escalation ranking removed; all candidates are `HELD` pending equivalent evidence;
- S1–S15 common scenario set and per-cell pass/hold/reject evidence schema;
- documentary-only Phase-4 walkthrough language;
- durable-checkpoint/crash recovery and restore/key-loss quarantine;
- critical-flow accessibility matrix plus mandatory later device acceptance;
- capability/dependency/owner/toolchain/fallback/EOL/security closure;
- complete DEBATE-005 release graph, trust-root/verifier and incident-impact gate;
- expanded staffing/TCO, toolchain upgrade and exit dossiers.

### Judge Determination

`PASS_WITH_CHANGES — CHANGES INCORPORATED FOR USER WORKING-DIRECTION DECISION; FRAMEWORK SELECTION HELD; NOT ADR-READY`.

The evaluation method is coherent and no-code. Five equal dossiers, equal Group-A task simulation, owner resource facts,
equal Flutter/RN final closure exercises, hosted-build controls and two final independent critiques are now complete.
The final reviewers disagree: one conditionally prefers Flutter's narrower configuration-generation surface; the other
keeps both technically held without real implementation evidence. Manager/Judge separates a reversible Phase-4 strategy
recommendation from later proof and recommended Flutter as the conditional working direction, with RN/Expo as first
fallback and explicit reversal triggers. The user approved Flutter under `DEC-0033`. No framework ADR, provider, code or
real evidence pass exists; Gate 4 -> 5 remains closed.

---

## DEBATE-007 — Data Backbone and Logical Service Boundaries

Status: `PASS_WITH_CHANGES — CORRECTIONS INCORPORATED / USER APPROVED DEC-0034 / ADR NOT READY`

Repository synthesis, official/primary research, controlled external-report intake and two independent reviews support a
provider-neutral working shape: canonical transactional authority per domain; server/API-mediated sensitive access;
online-authoritative Internal Operations; bounded closed mobile offline packages; durable user-operation reconciliation;
separate current/history/protected-audit and object/media planes; rebuildable projections; and cross-plane tested backup,
restore, export and exit.

Critical corrections for restore resurrection, physical-action recall races, package dependency closure, classification
propagation, privileged bypass paths, protected audit, cross-plane consistency, provider/account/cost failure and bounded
AI operations are incorporated. PostgreSQL, managed service and every physical technology/provider remain comparison
candidates—not decisions. The user approved the direction under `DEC-0034`; no ADR/code/purchase or Gate 4 -> 5
transition is authorized.

---

## DEBATE-012 — Internal Operations Web Frontend and Hosting

Status: `USER-APPROVED WORKING DIRECTION DEC-0039 / 4 FRAMEWORKS HELD / NO WINNER / ADR NOT READY`

Framework-neutral requirements, current official research, failure/TCO analysis, an initial manager proposal, two
independent Luna Max adversarial reviews, common no-code task simulation, four-way equivalence audit, component-
ecosystem tie-break and render/hosting tie-break are complete.

Both reviews rejected the initial React conditional-leader and fallback ordering. React/Next, Angular, Vue/Nuxt and
Svelte/SvelteKit remain equal `HELD`; popularity and AI familiarity are not capability evidence. The corrected Judge
identifies CSR-first static artifact/CDN + Kavriva API as the simplest conditional starting direction because the
internal authenticated application has no public SEO requirement and this shape begins with the smallest web-runtime
authority surface. Same-origin BFF, SSR/edge, container and privileged service worker remain need-specific and held.

API commit authority, session/CSRF/XSS/CSP, stale tab and lost outcome, quarantine, accessibility, dense workspace,
multi-AI design/task consistency, immutable release compatibility, no-owner-debug, bounded TCO and clean-room exit are
hard gates. The user approved the corrected working direction under `DEC-0039`. No framework, component library,
hosting provider, account, plan, code, deployment, ADR or Gate 4 -> 5 transition is authorized.
