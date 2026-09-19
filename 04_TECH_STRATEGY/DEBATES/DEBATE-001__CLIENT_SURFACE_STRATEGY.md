# DEBATE-001 — CLIENT SURFACE STRATEGY

Status: `USER DIRECTION RECORDED — INTERNAL WEB APPROVED / MOBILE FRAMEWORK OPEN / NO-CODE`
Date: 2026-09-17
Decision level: Phase-4 recommendation only; not an ADR and not approved/locked

## 1. Decision Question

Which client-surface topology best fits Kavriva's approved product requirements?

1. Which implementation family should lead consumer Android/iOS delivery?
2. Should Internal Data & Content Operations begin as web, desktop or hybrid?
3. What boundary must separate both clients from shared product data and controlled publication?

This debate does not select the final backend, database, CMS, identity, analytics, cloud or AI provider.

## 2. Approved Inputs

- `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`
- `02_DISCOVERY/SYNTHESIS/BUSINESS_RULES.md`
- `03_DESIGN/NAVIGATION_MAP.md`
- `03_DESIGN/STATE_MATRIX.md`
- `03_DESIGN/SCREEN_FAMILY_SPECS.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md`
- `04_TECH_STRATEGY/EVALUATION_CRITERIA.md`

Product facts driving the comparison:

- consumer delivery is Android/iOS mobile with a strong visual/state system;
- offline guide, safety, progress and history continuity is baseline;
- stale or recalled critical content must not be treated as safe/current merely because it is cached;
- local-first value precedes mandatory profile creation, and later migration is non-destructive;
- camera/media, notifications, files, secure local state and platform lifecycle integration are expected;
- Internal Operations is a dense, permissioned, auditable research/review/release workflow;
- editing never equals approval, and approval never equals publication.

## 3. Technical Evidence Reviewed

Primary documentation consulted on 2026-09-17:

- Flutter supported platforms: https://docs.flutter.dev/reference/supported-platforms
- Flutter platform integration: https://docs.flutter.dev/platform-integration
- Flutter offline-first guidance: https://docs.flutter.dev/app-architecture/design-patterns/offline-first
- Flutter application architecture: https://docs.flutter.dev/app-architecture
- React Native architecture: https://reactnative.dev/architecture/overview
- React Native New Architecture: https://reactnative.dev/blog/2024/10/23/the-new-architecture-is-here
- React Native environment setup: https://reactnative.dev/docs/set-up-your-environment
- Expo SQLite: https://docs.expo.dev/versions/latest/sdk/sqlite/
- Kotlin Multiplatform overview: https://kotlinlang.org/docs/multiplatform/kmp-overview.html
- Kotlin Multiplatform iOS integration: https://kotlinlang.org/docs/multiplatform-ios-integration-overview.html
- PWA offline/background operations: https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Offline_and_background_operation
- Electron process model: https://www.electronjs.org/docs/latest/tutorial/process-model
- Electron security: https://www.electronjs.org/docs/latest/tutorial/security
- Tauri architecture: https://v2.tauri.app/concept/architecture/
- Tauri security: https://v2.tauri.app/security/
- Apple background download behavior: https://developer.apple.com/documentation/foundation/downloading-files-in-the-background
- Apple background task behavior: https://developer.apple.com/documentation/uikit/using-background-tasks-to-update-your-app

Evidence interpretation:

- All three mobile families can reach native platform APIs. Framework choice does not solve sync,
  migration, recall or safety semantics; those require a deliberately designed local data layer.
- iOS background work remains OS-scheduled and constrained regardless of cross-platform framework.
  Correctness cannot depend on a background job running at an exact time.
- React Native's New Architecture removes the old bridge as the central interaction mechanism and
  improves native interop, but offline architecture remains an application/framework-ecosystem choice.
- Kotlin Multiplatform can share selected logic while retaining native UI and APIs; its flexibility also
  creates more possible team/toolchain shapes that must be governed.
- Web/PWA supports offline caching and local persistence, but background and browser-storage behavior
  is not a substitute for mobile-native lifecycle guarantees.
- Electron and Tauri both add a privileged desktop trust boundary. Tauri exposes capabilities around a
  Rust core/system WebView; Electron embeds Chromium and a Node-capable main process. Either wrapper
  adds packaging, update and security work that a browser-only internal tool does not inherently need.

## 4. Options — Consumer Mobile

### M1 — Flutter application

**Strengths**

- One UI implementation can closely reproduce Kavriva's approved custom visual system on Android/iOS.
- Official architecture guidance explicitly supports repository-based offline-first designs combining
  local and remote sources of truth.
- Native plugins and platform channels provide escape hatches for background transfer, secure storage,
  notifications, camera/media and OS-specific behavior.
- A consistent rendering/component model can reduce cross-platform visual drift.

**Risks / costs**

- Dart/Flutter is a dedicated competency; it does not directly share the Internal Operations web UI.
- Plugin maturity, native build failures and OS-release lag must be actively managed; platform-specific
  code is still required for lifecycle edge cases.
- Custom rendering does not automatically produce correct native accessibility or platform conventions.
- A single codebase can hide platform-specific defects unless real-device test matrices remain explicit.

### M2 — React Native with an explicit framework/native-module envelope

**Strengths**

- TypeScript/React competency can overlap with Internal Operations web staffing and tooling.
- Native components and the current architecture provide direct native interop and strong ecosystem reach.
- SQLite/local persistence and native modules are available; a framework layer such as Expo can simplify
  builds, signing and standard device capabilities only within a separately governed native-module and
  application-release envelope. OTA delivery, if considered, is a distinct release authority and cannot
  bypass app/content approval controls.
- Large ecosystem and familiar web-adjacent development model may lower staffing friction.

**Risks / costs**

- Offline sync, version/recall enforcement and migration correctness are not supplied by React Native;
  they remain custom architecture and testing responsibilities.
- Framework/native module compatibility and upgrade coordination can create dependency coupling.
- Cross-platform UI and native-module behavior may diverge, especially around complex lifecycle/background cases.
- Sharing a language with web can tempt inappropriate sharing of UI or business state that has different
  trust and lifecycle semantics.

### M3 — Kotlin Multiplatform shared core with native Android/iOS UIs

**Strengths**

- Can share domain, validation, persistence and sync logic while retaining native APIs and native UI behavior.
- Strong option when native fidelity, platform-specific lifecycle control and shared business invariants
  are more important than a single cross-platform UI layer.
- Sharing can be incremental rather than all-or-nothing.

**Risks / costs**

- Native UI means two presentation implementations.
- Kotlin/Gradle/Xcode/Swift integration and CI increase operational and debugging complexity.
- Higher initial architecture/team burden is difficult to justify before staffing and platform divergence
  demand it.
- Internal Operations web remains a separate frontend competency.

### M4 — Kotlin Multiplatform with shared Compose Multiplatform UI

This is not scored together with M3. It may share more UI and domain code than M3, but it needs separate
validation for iOS accessibility, platform convention, toolchain, debugging and team capability. It remains
an investigation option, not an inferred substitute for native UI.

### M5 — Fully native Android and iOS reference baseline

A fully native pair is retained as a comparison baseline for lifecycle control, accessibility and native API
fit. It is not currently shortlisted for duplicate product implementation because repo evidence does not yet
justify two complete UI stacks, but the other candidates must be compared against its native-behavior ceiling.

## 5. Evidence-Limited Mobile Comparison

The first draft's numerical table was removed after both independent reviewers found that it quantified unknown
team capability, performance and implementation quality in conflict with the scoring discipline. The table below
records only option-attributable tendencies; every Kavriva-specific result remains unproven until a comparable test.

| Option | Demonstrated from official docs | Kavriva-specific unknowns | Current disposition |
|---|---|---|---|
| Flutter | Android/iOS support, one UI toolkit, native integration, official offline-first architecture guidance | accessibility fidelity, plugin/native exception load, team capability, device behavior, full sync/recall design | Leading no-code evidence candidate |
| React Native + defined envelope | Native interop, current architecture, React/TypeScript ecosystem, SQLite/native modules via selected framework/libraries | exact Expo/native boundary, dependency/upgrade load, team capability, lifecycle divergence, full sync/recall design | Leading no-code evidence candidate |
| KMP shared core + native UI | Incremental domain sharing with native APIs/UI | two-UI delivery cost, Swift/Kotlin staffing, CI/debugging burden, shared persistence/sync behavior | Escalation candidate and reference |
| KMP + shared Compose UI | Shared Kotlin domain and UI is technically available | iOS UX/accessibility, maturity for this team, native exception load and delivery cost | Separate investigation option |
| Fully native pair | Direct platform APIs and platform-native UI/accessibility ceiling | duplicate delivery cost, parity/governance and staffing | Reference baseline, not shortlisted yet |

Controlled refinement from DEBATE-006: the `Leading no-code evidence candidate` and shortlist labels above now describe
the historical research order only. Independent DEBATE-006 review rejected finalist ranking before equivalent scenario,
team and TCO evidence. Flutter, RN/Expo, KMP-native, KMP-Compose and full native are currently equal `HELD` dossier
candidates; DEBATE-006 governs the current comparison status.

The weighted criteria remain useful after identical fixtures, team/staffing evidence and measured outcomes exist.

## 6. Options — Internal Data & Content Operations

### I1 — Responsive browser web application

**Strengths**

- Best natural fit for dense tables, diffs, provenance, multi-pane review, keyboard use and centrally
  deployed role/permission changes.
- One controlled server release reduces client version drift during urgent recall/publishing operations.
- Browser security boundary avoids granting local filesystem/shell powers unless separately required.
- Can later gain installability/offline assistance selectively without making background behavior a safety assumption.

**Risks / costs**

- Browser storage/offline semantics are not sufficient for an always-offline authoritative publishing console.
- Large file ingestion, local tooling or device integration may require explicit browser APIs, upload agents
  or later desktop packaging.
- Responsive scope must prioritize desktop operator workflows without pretending every dense workspace is
  equally useful on a phone.

### I2 — Electron desktop application

**Strengths:** mature cross-platform desktop packaging, Chromium consistency, Node ecosystem and local integration.

**Risks:** privileged main/renderer/IPC boundary, bundled runtime/update burden, larger attack surface and no
currently approved requirement that needs desktop-native authority.

### I3 — Tauri desktop application

**Strengths:** system WebView, small compiled core, explicit capability model and fine-grained IPC permissions.

**Risks:** Rust plus frontend toolchain, OS-WebView variation, capability/configuration mistakes, desktop
distribution/update work and no currently approved desktop-only need.

### Historical extension idea — parked by user decision

The first draft considered a later shell. `DEC-0021` supersedes that default: the internal client is browser-based,
and no Electron/Tauri shell or companion desktop application may be introduced automatically. If a later no-code
scenario finds a browser-insufficient need, it is reported as an unresolved gap and returned to the user.

## 7. Evidence-Limited Internal-Surface Comparison

| Option | Option-attributable advantage | Unproven / added burden | Current disposition |
|---|---|---|---|
| Browser web | Natural dense-workflow UI, central deployment, no default local shell/filesystem authority | XSS/session/API authorization, stale tabs/caches, hostile ingestion, constrained-network and large-file behavior | **User-approved client form** |
| Electron | Chromium consistency, Node/local integration | privileged IPC/main process, bundled-runtime security/update/distribution burden | Outside current direction |
| Tauri | system WebView, Rust core, capability/IPC model, small package potential | Rust+frontend competency, OS-WebView variation, capability mistakes, update/distribution burden | Outside current direction |

RBAC, audit, controlled publication and disaster recovery are service/security architecture obligations; client
packaging does not earn those properties. Cost/TCO remains unknown pending staffing and operational modelling.

## 8. Leading Logical Boundary — Shared Services, Separate Client Authorities

Regardless of client framework, the current proposal requires this boundary:

```text
Consumer Mobile -> Consumer contract -> application-eligible versioned content + user services
                                             ^
                                             | controlled publication transition
                                             |
Internal Web -> Operations contract -> draft/review/version/audit models
```

Rules:

- The clients may share schemas, design tokens and generated API contracts; they do not share authority.
- Internal UI never directly changes consumer application eligibility.
- Server-side policy enforces role, review, exact approved version and publication eligibility; hiding a button
  is not authorization.
- Mobile caches version-addressed content plus eligibility/freshness metadata. An offline device cannot learn a
  new recall instantly; risk-tiered offline validity, time-tamper behavior, foreground reconciliation and a
  separately preserved safe-stop/recovery package require their own policy/architecture decision.
- User-local history/progress and editorial source data are different bounded domains even if one backend
  platform eventually hosts both.
- Shared UI code is optional and low priority. Shared domain vocabulary and tested contracts are high priority.

This is a logical trust boundary, not a premature physical data topology. A transactionally controlled version/
eligibility model and a separate publication projection/read store are both still valid alternatives. Separate
contracts do not require separate deployments or databases. Physical publication, atomicity, lag, retry, replay/
downgrade protection and recall ordering move to a dedicated debate.

## 9. Revised Manager Proposal After Independent Review

1. **Consumer mobile:** compare **Flutter and React Native with an explicitly defined framework/native envelope**
   first through no-code evidence dossiers. Keep KMP-native as escalation/reference if official evidence shows that
   native lifecycle/accessibility needs outweigh single-UI delivery efficiency. No prototype will be written.
2. **Internal Operations:** the user selected a **browser-based, desktop-class responsive web application**.
   Desktop applications/wrappers are outside the current direction and require a new explicit user decision to reopen.
3. **System boundary:** carry **separate client authorities + server-enforced contracts + controlled publication
   transition** as the leading logical topology; do not yet choose a physical projection/read-store design.
4. **Validation:** all remaining comparison is no-code: official/primary documentation, identical product-scenario
   walkthroughs, failure/compatibility tables, maintenance/TCO evidence and independent AI critique.

## 10. Required No-Code Evidence Scenarios

### Mobile architecture walkthrough scenarios

1. Download a versioned guide/media bundle; kill/restart offline; restore exact saved context but keep physical/
   safety checks unconfirmed and progression closed until required revalidation succeeds.
2. Stay offline beyond a synthetic critical validity boundary without receiving a server event; close new
   application while preserving teaching/history and safe stop/recovery. Test airplane mode, untrusted/changed
   device time, old backup restore, missed push and long-dormant/old client behavior. Synthetic thresholds test
   mechanics and do not become approved product policy.
3. Create local account-light motorcycle/history data; migrate to a conflicting profile dataset without loss or
   silent overwrite; cancel and retry safely.
4. Exercise camera/file/notification/background download and deep-link flows on real low/mid Android and iOS devices.
5. Run VoiceOver/TalkBack, large text, Turkish copy and non-color state checks on representative approved screens.
6. Simulate interrupted writes, repeated sync requests, partial download and schema migration rollback/recovery.
7. Test a material guide change during active work: preserve historical version/action context and require safe
   current-state mapping before continuation.
8. Test N/N-1/unsupported clients and unknown safety-critical fields; unsupported application fails closed while
   required history and recovery remain available.

### Internal web architecture walkthrough scenarios

1. Navigate keyboard-only through a dense review packet, diff, provenance and decision flow.
2. Enforce strict proposer/reviewer/publisher separation for a high-consequence fixture, scope-aware authorization,
   stale/revoked-role rejection and direct-API bypass resistance; leave lower-risk staffing policy open.
3. Bind approval to an immutable/content-addressed snapshot and release manifest; prove sole-writer publication,
   replay/downgrade protection, atomic current-version change, idempotent retry and partial-failure recovery.
4. Trace a source withdrawal to dependent claims/guides and open a recall without deleting history.
5. Walk through hostile and realistic documents/media/URLs with sandboxed preview, type validation, malware/archive
   defenses, SSRF protection and derived-copy withdrawal; record any browser-insufficient gap for user decision.
6. Race edit/evidence withdrawal/recall against pending publication and delayed messages; no stale release may
   silently regain eligibility.
7. Exercise emergency suspension while normal publishing or identity service is unavailable; test step-up/break-glass
   control, audit, cache/CDN propagation evidence, RTO/RPO and restoration.
8. Open an old operations tab/session against changed policy/data; stale approval and publish attempts must fail.

### Comparable evidence contract

Each candidate dossier must use identical conceptual fixtures, guide/media envelopes, local-record scale assumptions,
device/OS profiles, network/interruption conditions and pass/fail questions. Each claim must be marked official evidence,
reasoned inference, unresolved or dependency-specific. Native-code exceptions, team competency, 12–24 month TCO,
CI/signing, HA/DR, observability, retention and on-call cost are explicit evidence inputs. No executable test is produced.

## 11. Key Risks

- Framework scoring may be dominated by unknown team skill rather than product fit.
- A local database library may be mistaken for a complete sync/conflict/recall architecture.
- Background refresh may be treated as timely or guaranteed even though mobile OS scheduling is constrained.
- Cross-platform abstraction may hide iOS/Android differences until late real-device testing.
- “Shared TypeScript” or “one codebase” may become a goal that collapses distinct trust domains.
- Web-first may under-estimate bulk document/media ingestion or constrained-network operational needs.
- A desktop wrapper may be adopted for convenience and create unnecessary privileged attack/update surface.
- Published read-model projection and recall propagation are not yet designed; they remain a later debate/ADR.
- Approval-to-publish snapshot integrity, emergency suspension and client/content compatibility are not yet designed.
- Hostile source ingestion, audit tamper-resistance, account/device key boundaries and supply-chain release authority
  remain unresolved security work.

## 12. Independent Review Result

- Reviewer A — Architecture, Mobile & Scale: `PASS_WITH_CHANGES`.
- Reviewer B — Security, Operations, Failure Modes & Cost: `PASS_WITH_CHANGES`.
- Critical findings were accepted; no critical finding was dismissed.
- Canonical records:
  - `DEBATE-001__REVIEW_A_ARCHITECTURE.md`
  - `DEBATE-001__REVIEW_B_SECURITY_OPERATIONS.md`

Both reviewers preserve the main direction but reject framework selection and physical publication topology as
premature. Their corrections are incorporated above.

## 13. ADR Candidates — Not Yet Authorized

- ADR candidate: consumer mobile framework selection, after no-code evidence and staffing/TCO review.
- ADR candidate: Internal Operations browser-based client form (`USER-APPROVED DIRECTION`; Phase 5 record still pending).
- ADR candidate: separate client authorities and server-enforced logical contracts.
- No desktop-wrapper ADR candidate exists under `DEC-0021`; only a new explicit user decision may reopen it.

Separate Phase-4 debates required before architecture ADRs:

- offline safety validity, recall and client/content compatibility contract;
- approval snapshot, publication topology, emergency suspension and disaster recovery;
- identity/RBAC/audit and hostile evidence ingestion boundary;
- supply-chain, application/content release authority and update governance.

No ADR candidate above is approved by this document.
