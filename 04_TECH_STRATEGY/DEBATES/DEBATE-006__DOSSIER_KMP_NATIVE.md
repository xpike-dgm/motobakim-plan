# DEBATE-006 — EQUAL MOBILE CANDIDATE DOSSIER: KMP-NATIVE

Status: STRUCTURALLY COMPLETE DRAFT / RESEARCH — NO-CODE / NOT REVIEWED / HELD
Date: 2026-09-17
Decision level: Phase-4 comparison evidence only; not a recommendation, ADR, approval or Gate 4 → 5 transition

Completion warning: Sections 1–11 of the controlled candidate template are now structurally present. The S1–S15,
accessibility, forced-event, AI-operability, TCO and exit records are documentary evidence plans and holds only; they are
not implementation, device, store or safety passes. No KMP-native scenario has passed and no recommendation is made.

This dossier evaluates **KMP-native**: shared Kotlin Multiplatform domain/data logic with separate native Android and
iOS user interfaces. It does **not** evaluate or adopt Compose Multiplatform shared UI. Any shared-UI candidate belongs
to the separate KMP-Compose dossier and cannot inherit this boundary or result.

This is documentary research only. No application code, prototype, executable spike, signed build, benchmark, store
submission or real-device pass is claimed.

Evidence labels used below:

- `OFFICIAL EVIDENCE`: claim supported by an official Kotlin, Android or Apple primary source linked in this file;
- `REASONED INFERENCE`: a provider-neutral consequence of applying the approved Kavriva boundary to that evidence;
- `UNRESOLVED`: a product, dependency, owner, toolchain, capacity, cost or later acceptance fact not established;
- `HELD`: the candidate closure is incomplete, so no positive candidate result is asserted.

## 1. Candidate Identity

| Field | Record |
|---|---|
| Candidate family | KMP-native: shared Kotlin Multiplatform domain/data modules; native Android UI; native iOS UI. No shared Compose UI. |
| Exact evaluated version/snapshot | Kotlin `2.4.20` and Kotlin Multiplatform Gradle plugin `2.4.20`, the current stable Kotlin version and matching KMP plugin row in the official compatibility guide retrieved 2026-09-17. This is an evidence snapshot, not a final Kavriva pin. |
| Official platform-stability snapshot | Core Kotlin Multiplatform lists Android and iOS as `Stable` in the official stability table retrieved 2026-09-17. Stability of code sharing is not proof of Kavriva product, accessibility, lifecycle or team fit. |
| Evidence retrieval date | 2026-09-17 |
| Product comparison floor | Frozen four-cohort fixture: constrained Android API 29 / 4 GB RAM / 64 GB storage / 2 GB free; main Android 13+ / 6 GB RAM / 128 GB storage; oldest supported-end iPhone capable of iOS 16.4; and a current standard non-Pro iPhone on the current generally available iOS. These are comparison profiles, not a final support promise. |
| Framework/toolchain compatibility snapshot | Official Kotlin 2.4.20 compatibility row: Gradle `7.6.3–9.7.0`, Android Gradle Plugin `8.5.2–9.3.1`, Xcode `26.4`. These are a compatibility range and are not selected project versions. |
| Build-tool/store floor | `UNRESOLVED`: exact JDK, Gradle, AGP, Xcode, Swift, SDK, signing, store and CI policy must be re-pinned together before an implementation decision. KMP compatibility is not a store or product-support guarantee. |
| Support/EOL statement | `OFFICIAL EVIDENCE`: Kotlin documentation defines `Stable` as suitable for conservative use under its backward-compatibility rules. `UNRESOLVED`: Kavriva product support floor, KMP upgrade cadence, library EOL policy, OS support window and emergency response are not set. |
| Dossier author/reviewer | Research sub-agent `/root/publish_policy`; independent dossier review pending |

Every later reference to comparison devices, both-platform evidence or real-device acceptance means all four frozen
cohorts above. A two-device or oldest-only sample cannot close a scenario or accessibility gate.

### 1.1 Official primary sources

The following are the only external technical sources used for this bounded draft:

- [What is Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform/kmp-overview.html) — shared logic, native UI choices,
  Kotlin/Native and platform integration overview.
- [Stability of supported platforms](https://kotlinlang.org/docs/multiplatform/supported-platforms.html) — core KMP Android/iOS
  stability levels and the meaning of `Stable`.
- [iOS integration methods](https://kotlinlang.org/docs/multiplatform-ios-integration-overview.html) — generated iOS
  framework and local/remote integration choices.
- [Compatibility guide for Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform/multiplatform-compatibility-guide.html) —
  exact Kotlin/KMP, Gradle, AGP and Xcode compatibility table and migration/deprecation notices.
- [Kotlin/Native overview](https://kotlinlang.org/docs/native-overview.html) — native targets and platform API access.
- [Android app architecture](https://developer.android.com/topic/architecture) — Android application/lifecycle architecture
  guidance; it does not define Kavriva's offline or safety truth.
- [Android Keystore system](https://developer.android.com/privacy-and-security/keystore) — protected Android key boundary.
- [Android background work overview](https://developer.android.com/develop/background-work/background-tasks) — Android
  background-execution constraints.
- [Android Photo Picker](https://developer.android.com/training/data-storage/shared/photopicker) and [documents/files](https://developer.android.com/training/data-storage/shared/documents-files) —
  native media/file boundaries.
- [Android notification runtime permission](https://developer.android.com/develop/ui/views/notifications/notification-permission) —
  notification permission behavior.
- [Android accessibility](https://developer.android.com/guide/topics/ui/accessibility/apps) — native accessibility obligations.
- [Apple background tasks](https://developer.apple.com/documentation/backgroundtasks) and [background URLSession transfers](https://developer.apple.com/documentation/foundation/url_loading_system/downloading_files_in_the_background) —
  iOS background work/transfer boundaries.
- [Apple Keychain Services](https://developer.apple.com/documentation/security/keychain_services) — protected iOS key boundary.
- [PHPickerViewController](https://developer.apple.com/documentation/photokit/phpickerviewcontroller) and [UIDocumentPickerViewController](https://developer.apple.com/documentation/uikit/uidocumentpickerviewcontroller) —
  native media/file boundaries.
- [UserNotifications](https://developer.apple.com/documentation/usernotifications) and [Apple accessibility](https://developer.apple.com/documentation/accessibility) —
  native notification and accessibility boundaries.

Kavriva product and comparison authority is separate from these external technical sources and is recorded in Section 2.

### 1.2 Snapshot interpretation and limits

`Kotlin 2.4.20` is recorded because the official compatibility guide names it as the current stable Kotlin version and
shows the matching KMP plugin/toolchain compatibility row. It is not a permanent framework pin. The eventual ADR must
re-check and bind the language/compiler, KMP plugin, Gradle, AGP, JDK, Xcode, Swift integration, dependency graph and
store requirements as one exact release snapshot.

The official KMP stability table is evidence that the core Android/iOS code-sharing targets are stable. It does not prove:

- any particular local database, serialization, networking, media, background or secure-storage library;
- the correctness of Kavriva's offline package, recall, migration, conflict or safety state machine;
- VoiceOver/TalkBack behavior on Kavriva's critical Turkish flows;
- product support for every OS/device covered by the framework;
- availability of an accountable KMP, Android, iOS, security, release or accessibility owner;
- lower 12–24 month cost;
- approval for shared Compose UI or any OTA/runtime code channel.

Official KMP documentation also describes compatibility and migration concerns around Android target plugin configuration,
deprecated target shortcuts, legacy multiplatform libraries and Gradle integration. These are toolchain-closure inputs,
not reasons to silently choose a migration path here.

## 2. Fixed Inputs and Comparison Discipline

This record applies without KMP-specific relaxation:

- `04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md`, approved under `DEC-0031`;
- the equal S1–S15 definitions and pass/hold/reject rules in
  `04_TECH_STRATEGY/DEBATES/DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md`;
- `DEC-0023` through `DEC-0031`, including data-efficient task-scoped offline delivery, conservative recovery,
  AI-operated delivery, limited-budget costing and no approved OTA;
- approved DEBATE-001 through DEBATE-005 directions: separate client authority, bounded offline eligibility, immutable
  publication meaning, scoped authorization/audit, federated release integrity and the closed cross-domain release graph;
- approved Phase-2/Phase-3 product, design and accessibility truth: fit-before-application, evidence/provenance,
  uncertainty, non-destructive history, current physical-state revalidation, safe-stop/recovery, Turkish-first critical
  flows, private/community/official separation and no silent overwrite/loss.

Any required fixture change stops this dossier and must be applied once to all five candidates. This file does not alter the
common fixture.

### 2.1 Frozen comparison fixture carried into this candidate

The following are comparison inputs, not final commercial, support, retention or SLA commitments:

- one selected motorcycle/variant and one active maintenance task;
- required compact guidance and complete safe-stop/recovery closure up to `12 MB` transfer;
- optional high-resolution media/video up to `150 MB`, never silently selected;
- unrelated `2 GB` catalog used to prove that the candidate does not download it by default;
- default offline-content cache budget `250 MB`, excluding user-created history/photos;
- cellular confirmation above `25 MB`;
- local fixture of 3/10 motorcycles, 250/2,000 history/evidence records, 50/500 photos at 3 MB average,
  100/1,000 private notes, 20/200 pending changes and 3/30 deliberate local/profile conflicts;
- one duplicate operation, one partial upload, one corrupt package, one interrupted database change, one source
  correction, one content withdrawal and one safety recall;
- constrained network, connection loss, 72-hour offline, process termination, device-clock change and backup-restore
  profiles;
- phone-focused comparison: constrained Android API 29 cohort and oldest-comparison iPhone capable of iOS 16.4;
- first-release native capability boundary: camera, photo/file import, user-visible export/share, notifications,
  deep links, secure local storage, scoped download/cancel/resume/integrity/cleanup, foreground reconciliation,
  VoiceOver/TalkBack critical flows and store signing/staged release/incident pause;
- no first-release assumption of Bluetooth, NFC, continuous GPS/background location, motorcycle hardware integration,
  background execution as correctness, framework OTA code delivery or AI authority over safety publication;
- 1,000/10,000/50,000 MAU service-cost workload, first release plus 24 months, four planned release windows per year,
  one annual safety/security correction and one annual forced platform/toolchain event.

The exact fixture is defined once in the common document; the values above are repeated only to make this candidate's
boundary auditable.

### 2.2 Fixed product and release rules

KMP-native cannot turn shared code into authority. The shared module may represent the consumer contract and local state,
but server-authoritative eligibility, publication, recall, current release and authorization remain outside the framework.
The mobile client receives only the eligible versioned content permitted by the consumer contract.

The local package must be the smallest safe closure for the selected motorcycle/task. It must retain mandatory text,
warnings, checks and safe-stop/recovery while keeping heavy media optional. A restored, cloned, stale, mixed or partially
verified package cannot create positive safety or entitlement authority.

The KMP-native dossier must preserve the following distinctions:

```text
KMP shared domain/data logic  ≠  Android native UI  ≠  iOS native UI
mobile consumer authority     ≠  Internal Operations authority
local cache/history context   ≠  current server eligibility
artifact authenticity         ≠  approval/provenance   ≠  current revocation state
```

The native UIs may share product vocabulary, state contracts and accessibility intent, but they must not silently share
authority, private data scope or server mutation credentials with Internal Operations.

### 2.3 Evidence status for this bounded draft

All capability outcomes remain `HELD`. Official documentation establishes that KMP and native platform mechanisms exist;
it does not establish a complete Kavriva implementation, dependency lock, owner/capacity plan, real-device result or
release-ready closure. S1–S15 are intentionally deferred to the next bounded task.

## 3. Candidate Architecture Boundary (Documentary, No Implementation)

### 3.1 Boundary statement

The candidate is a shared Kotlin Multiplatform core with two separately owned native presentation applications:

```text
                    Consumer contract / server authority
                                  │
                ┌─────────────────┴─────────────────┐
                │                                   │
     Android native application             iOS native application
       Kotlin + native UI                    Swift + native UI
                │                                   │
                └────────── KMP shared domain/data ─┘
                    Kotlin common contracts and rules
```

This is a logical boundary, not a selected repository/module layout. The final Android UI toolkit and final iOS UI toolkit
remain open. “Native UI” means each platform owns its presentation, accessibility, lifecycle and platform conventions;
it does not imply a specific Android widget framework or a specific iOS declarative/imperative UI choice.

The separate KMP-Compose shared-UI option is deliberately excluded. No shared Compose screen, Compose renderer, Compose
accessibility claim or Compose-specific dependency is part of this candidate.

### 3.2 Shared domain and data ownership

`REASONED INFERENCE`: the KMP shared core is the proposed owner of portable, deterministic product rules that must have one
meaning on both platforms:

- motorcycle/variant applicability and fit-result semantics;
- content/release/client-capability envelope parsing;
- risk, readiness, freshness, stale, recall and safe-stop state meanings;
- current-physical-state revalidation requirements after interruption;
- task-scoped package manifest and dependency-closure rules;
- local record/history/provenance/correction/withdrawal relationships;
- pending operation identity, idempotency and explicit partial/unknown/conflict outcomes;
- local-to-profile migration intent and conflict categories;
- entitlement-independent history/recovery availability rules;
- Turkish copy keys, unit semantics and accessibility-state contract identifiers;
- portable consumer API/data contracts and release compatibility declarations.

These rules remain Kavriva-owned. KMP, Kotlin libraries, Android services and iOS services do not become truth authorities
merely because the shared module calls them.

`REASONED INFERENCE`: the shared core should expose interfaces/contracts for platform services rather than make common
domain code depend directly on UI, Activity/ViewController, notification presentation, camera surfaces, file pickers,
OS schedulers or store identities. The exact interface shape is not designed in this partial dossier.

### 3.3 Native Android UI boundary

The Android application owns:

- native navigation, screens, focus/order, text layout and platform conventions;
- TalkBack, Switch/Voice Access and Android accessibility behavior;
- Android permission surfaces and user-visible system dialogs;
- camera/media/file picker integration and Android URI/path lifecycle;
- Android secure key storage and device-binding policy;
- Android lifecycle, process termination, background-work and notification behavior;
- Android deep-link/intents/app-link entry and validation;
- Android backup/data-extraction configuration and restore handling;
- Android-specific performance, memory, storage, battery and OS-version behavior;
- Android build, signing, store submission and installed-client rollout artifact.

The Android UI may render state supplied by the shared core, but it cannot reclassify `stale`, `recalled`, `unknown`,
`held`, `safe-stop`, `teaching-only` or `not applicable` into an eligible physical application state. UI restrictions are
not server authorization.

### 3.4 Native iOS UI boundary

The iOS application owns:

- native navigation, screens, focus/order, text layout and iOS platform conventions;
- VoiceOver, Switch Control and iOS accessibility behavior;
- iOS permission surfaces and user-visible system dialogs;
- camera/media/file picker integration and security-scoped/resource lifecycle;
- iOS Keychain and device-binding policy;
- iOS scene/application lifecycle, background-transfer and notification behavior;
- iOS universal-link entry and validation;
- iOS backup/restore and key/data treatment;
- iOS-specific performance, memory, storage, battery and OS-version behavior;
- iOS build, signing, store submission and installed-client rollout artifact.

The iOS UI must consume the same domain/state contracts as Android without assuming visual, lifecycle, accessibility,
threading or platform-service parity. A native iOS surface is not evidence that the shared domain/data behavior is safe or
that the critical Turkish flows work on real devices.

### 3.5 Local persistence, encryption, migration and backup boundary

The logical local data boundary separates at least:

- scoped offline content packages and their release/client eligibility context;
- account-light motorcycle/history records;
- private notes and user photos;
- pending operations and durable checkpoints;
- conflict/partial/unknown records;
- provenance, correction and withdrawal history;
- trust/eligibility metadata and release/revocation observations;
- protected fields, device binding and key references.

`UNRESOLVED`: no local database, serialization library, encryption wrapper, schema format, key derivation policy or backup
include/exclude policy is selected. KMP-native must not claim that a multiplatform database library automatically provides
atomic writes, crash recovery, conflict resolution, recall ordering, encryption, retention or safe migration.

`REASONED INFERENCE`: Android Keystore and iOS Keychain remain platform-owned protected-key boundaries. Raw keys must not
be exported in user files or ordinary backup data. A restored or cloned local state remains untrusted until account/device
binding, key state, current release, suspension/revocation generation and content integrity reconcile.

Migration must preserve valid new data and history. A binary rollback cannot be used as a data rollback when schema/data
compatibility is unknown. Failed or interrupted migration remains explicit and recoverable/quarantined rather than being
reported as completed.

### 3.6 Sync, reconciliation and scoped offline package boundary

`REASONED INFERENCE`: KMP shared data logic may coordinate local state, package verification and pending-operation
reconciliation, but it cannot make offline state authoritative. Foreground reconciliation after connectivity returns is
the decisive path for current eligibility, recall, release generations and server mutations.

The package lifecycle must conceptually be:

```text
requested scope → staged transfer → integrity/manifest verification
                 → complete package promotion → offline bounded use
                 → foreground reconciliation → current/held/recalled result
```

The shared core must represent cancellation, interruption, duplicate request, corruption, low storage, partial transfer,
stale release, incompatible client, recall and unknown reconciliation outcomes. Android/iOS background scheduling may
optimize transfer, but correctness cannot depend on a scheduled background task running at a particular time.

No full catalog, unrelated motorcycle or unused heavy media download is permitted by this candidate's fixed input. The
common core must not hide an over-download behind a platform cache or package manager.

### 3.7 Camera, file/media, notification, deep-link and background boundaries

The shared core may own portable intent/state contracts such as `capture requested`, `file selected`, `transfer partial`,
`notification advisory`, `deep link pending` and `reconciliation required`. Native applications own the actual platform
surfaces, permissions, resource lifetimes, cancellation and failure behavior.

External files, URLs and derived media remain untrusted until the approved ingestion and provenance process establishes the
required status. Opening a native viewer, picker or share destination does not establish technical correctness, official
status or publication authority.

Notifications and push are advisory. A notification cannot be the sole recall authority, and a missing notification cannot
silently preserve physical application eligibility. Deep links cannot bypass fit, readiness, authorization, release or
recall checks.

### 3.8 Accessibility and state-semantics boundary

The shared core owns stable semantic state identifiers and required meaning; Android and iOS native UIs own the accessible
expression of those states. Both must later prove, on actual devices and assistive technologies, the critical Turkish flows:

- readiness and required checks;
- warning and stop states;
- stale/recall/unknown/held outcomes;
- safe-stop/recovery and active physical work;
- evidence/provenance and uncertainty;
- large text, focus/order, non-color status and reduced-motion behavior.

KMP stability or native UI access does not count as a real-device VoiceOver/TalkBack pass. No accessibility result is claimed
in this partial dossier.

### 3.9 Store, build, signing and release boundary

KMP shared code is an input to two separately signed consumer application artifacts. Android and iOS builds must bind the
same reviewed shared-domain revision to their platform-specific UI, native adapters, configuration, dependency closure and
release metadata. They are not one interchangeable binary.

The release graph must bind, at minimum:

- exact KMP/shared source revision and native application revisions;
- Kotlin/KMP/Gradle/AGP/JDK/Xcode/Swift/toolchain closure;
- direct/transitive dependency resolution and native implementation inputs;
- Android and iOS UI/capability declarations;
- client capability, API/schema, content/derived assets, configuration, migration and offline recovery closure;
- provenance/SBOM/verification/signing evidence and suspension/revocation generations.

No KMP framework feature, shared code path or future runtime delivery mechanism can approve technical content, change
current eligibility, bypass Internal Operations publication or create an OTA authority. No OTA path is evaluated here.

### 3.10 Internal Operations/API/content contract boundary

Internal Data & Content Operations remains a separate browser-based trust boundary. The mobile apps consume the approved
consumer contract; they do not share operator credentials, role state, publication authority or private editorial data.

The shared KMP module may contain generated/portable consumer contract types only if the eventual contract governance allows
that shape. It must not contain a shortcut that directly mutates editorial truth, current-release pointers, roles,
publication status or audit evidence. Server policy remains authoritative for authorization, publication, recall and current
eligibility.

### 3.11 Portable data and framework-exit boundary

Portable assets should include, independently of KMP:

- canonical product/content/data schemas and migration descriptions;
- history, provenance, correction, withdrawal and conflict events;
- offline-package fixtures and compatibility envelopes;
- user export and media lineage;
- Turkish copy, units and accessibility intent;
- S1–S15 scenario fixtures and acceptance oracles;
- release/rollback/revocation evidence and audit references.

KMP shared source, Kotlin/Native binaries, generated iOS frameworks, Gradle/Xcode integration and platform-specific UI
remain implementation-bound. The exact portable format, framework replacement migration, key continuity and two-platform
parity strategy are `UNRESOLVED` and intentionally deferred to the exit dossier.

## 4. Native and Dependency Closure

### 4.1 Closure rule

The rows below are a capability closure inventory, not an approved dependency list. No third-party library, package,
provider, hosted build service, CI runner, database, serialization format, identity service or OTA mechanism is selected.
The KMP `2.4.20` row and official native platform APIs are evidence snapshots only.

Every critical capability must eventually reach `PASS`, `HELD` or `REJECT` with an exact source/version, primary and backup
owner, native skill, lifecycle constraint, fallback, EOL/security response and later acceptance evidence. An unnamed
dependency, native exception or owner is `HELD`.

### 4.2 Native/dependency closure matrix

| Capability | Built-in/framework path | Dependency/plugin | Native code/skill required | Lifecycle/threading constraints | Accessibility impact | Fallback/replacement | EOL/security owner | Status |
|---|---|---|---|---|---|---|---|---|
| Shared domain/state contracts | `OFFICIAL`: KMP common code/source-set model and Kotlin/Native targets; candidate uses shared Kotlin domain/data logic only | No package selected | Kotlin/KMP shared-code owner; Android and iOS reviewers for boundary changes | `REASONED`: common code must not call UI or assume a platform scheduler; dispatcher/actor/error boundary is unresolved | Native UIs must expose the same state meaning and focus/action semantics | Portable contract/data schema and platform-specific adapters | Named shared-core owner, backup and source/provenance evidence unresolved | `HELD` |
| KMP compiler/plugin snapshot | `OFFICIAL`: Kotlin `2.4.20`; matching KMP Gradle plugin row | No additional plugin selected beyond official KMP plugin | Kotlin/Gradle release owner; independent verifier | Official compatibility row must be rechecked as one Kotlin/Gradle/AGP/Xcode set; no floating `latest` | Toolchain changes may affect generated interfaces; revalidation required | Previous pinned snapshot and controlled migration event | Toolchain provenance, lock, SBOM, CVE/EOL and rollback owner unresolved | `HELD` |
| Android native application host/UI | `OFFICIAL`: Android application can consume the shared KMP module as an Android library; UI toolkit not selected | No UI library selected | Android Kotlin/native UI owner; backup Android reviewer | Android lifecycle, process death, configuration/storage pressure and UI-thread rules require explicit policy | TalkBack, Switch/Voice Access, focus/order and non-color critical states | Native UI replacement behind portable state contracts | Android owner, SDK/store support and dependency closure unresolved | `HELD` |
| iOS native application host/UI | `OFFICIAL`: KMP generates an iOS framework consumed by an iOS application; native UI choice remains open | No Swift package/UI library selected | Swift/iOS/native UI owner; backup iOS reviewer | iOS scene/process/background behavior, Swift/Kotlin boundary and framework integration require explicit policy | VoiceOver, Switch Control, focus/order and non-color critical states | Alternate native UI implementation behind the same shared contracts | iOS owner, Xcode/Swift/store support and dependency closure unresolved | `HELD` |
| iOS KMP framework integration | `OFFICIAL`: local direct integration or remote framework integration are documented; no option selected | Direct integration, SwiftPM or CocoaPods are documented choices, not selected dependencies | Kotlin/Native + Xcode/Swift integration skill | Generated framework must match the exact shared revision; stale framework/cache after upgrade must be detected | Integration errors cannot hide state or accessibility failures | Controlled local/remote integration migration with exact artifact identity | Integration owner, framework artifact provenance and recovery path unresolved | `HELD` |
| Shared serialization and consumer contract | No KMP serialization library or wire format selected | Any future library must be version-pinned and reviewed; no unnamed package accepted | Contract/compatibility owner; Kotlin and Swift interop review | Unknown fields and incompatible safety semantics fail closed; schema evolution must be explicit | Native UIs need stable labels/state codes, not inferred text | Versioned portable contract and server compatibility hold | Dependency/source/license/security owner unresolved | `HELD` |
| Local database/history/event log | No database or ORM selected | No package selected; framework presence is not database proof | Data/migration owner with Android/iOS storage skill | Durable checkpoints, atomicity, crash recovery, concurrency and forward migration are unresolved | Partial/conflict/unknown states require accessible explanation | Portable schema plus forward/corrective migration; quarantine if unsafe | DB/library owner, EOL/security and restore evidence unresolved | `HELD` |
| Protected fields, key references and device binding | `OFFICIAL`: Android Keystore and Apple Keychain are native protected-key boundaries | No key wrapper/crypto package selected | Android security + Swift/iOS security owner; independent security reviewer | Key loss, rotation, restore/clone and device binding are explicit failure states; raw keys must not enter export/ordinary backup | Re-auth/quarantine/key-loss states must be readable and announced | Re-authentication and quarantine; no plaintext/copy-key fallback | Key lifecycle, incident/revocation and backup owner unresolved | `HELD` |
| Scoped package download/resume/cleanup | `OFFICIAL`: Android and iOS expose platform transfer/background mechanisms; exact orchestration remains Kavriva-owned | No downloader/cache package selected | Shared transfer-state owner plus Android/iOS background-transfer owners | Process death, cancellation, low storage, expiration and partial transfer cannot lose mandatory recovery closure; background is not correctness | Progress, paused/failed/unknown/retry states must be announced | Foreground resumable transfer; hold if complete closure cannot be verified | Transfer/package owner, integrity verifier, dependency/EOL response unresolved | `HELD` |
| Android camera/media/file input | `OFFICIAL`: Android media/file picker and document APIs are available; exact camera/path not selected | No camera/file package selected | Android camera, Photo Picker/SAF and storage-permission skill | Permission denial, URI lifetime, process death, temporary files and low storage require explicit handling | Native picker, denial and invalid-file states require TalkBack evidence | Manual evidence entry or owned native adapter; quarantine untrusted input | Native adapter owner, parser/scanner and security response unresolved | `HELD` |
| iOS camera/media/file input | `OFFICIAL`: Apple PHPicker, UIDocumentPicker and native camera/media APIs are available; exact path not selected | No Swift package selected | Swift/iOS Photos, document and camera skill | Permission changes, security-scoped resources, process loss and temporary-file cleanup require explicit handling | Native picker/camera and denial/error states require VoiceOver evidence | Manual evidence entry or owned native adapter; quarantine untrusted input | Native adapter owner, parser/scanner and security response unresolved | `HELD` |
| Android/iOS export and share | Native Android/iOS share surfaces are platform-owned; exact export contract is Kavriva-owned | No sharing package selected | Android Sharesheet and iOS share-sheet skill; privacy/export review | Destination is untrusted and operation is interruptible; exported copy cannot be remotely retracted | Scope, recipient, privacy and cancellation need accessible confirmation | App-owned export file plus user-controlled native share | Export/disclosure owner and audit linkage unresolved | `HELD` |
| Notifications and advisory recall notice | `OFFICIAL`: Android notification permission/API and Apple UserNotifications are platform surfaces | Push provider and notification package not selected | Android notification-channel and iOS notification-category skills | User disablement, authorization, process state and delivery delay are expected; notification is not recall authority | Turkish text/action and stop/recovery meaning need AT evidence | Foreground reconciliation and in-app state; no notification-dependent safety | Notification owner, privacy, provider and incident response unresolved | `HELD` |
| Deep links/intents/universal links | Android intents/app links and Apple universal links are native entry boundaries | No routing/deep-link package selected | Android intent and Swift/iOS link-validation skill | Cold start, replay, duplicate link and untrusted URL require idempotent validation | Link arrival/error/hold must be announced; no readiness/auth bypass | Safe in-app destination or manual navigation | Domain association/configuration owner and security evidence unresolved | `HELD` |
| Background execution and reconciliation trigger | `OFFICIAL`: Android background work and Apple background-task/transfer systems are constrained platform services | No scheduler/work package selected | Android background-work + iOS background-task/URLSession skill | Scheduling is opportunistic; correctness uses durable state and foreground reconciliation | Paused/deferred/expired work needs accessible explanation | Foreground retry/reconcile; no exact-time guarantee | Background policy owner and OS-change response unresolved | `HELD` |
| Backup/restore/clone behavior | Android and Apple backup systems are platform policies; exact inclusion/exclusion is not selected | No backup package selected | Android backup and iOS backup/Keychain expertise | Restored/cloned positive state is untrusted until account/device/key/release/revocation reconciliation | Quarantine, re-auth and partial restore must be visible to AT | Re-download scoped content; preserve portable records; quarantine mismatch | Backup/key/restore owner and game-day evidence unresolved | `HELD` |
| Accessibility semantics and native critical flows | Native Android/iOS accessibility APIs plus KMP shared semantic contract | No accessibility package selected | Independent TalkBack/Voice Access and VoiceOver/Switch Control reviewers | Largest text, reduced motion, focus, process interruption and permission surfaces require physical-device review | Critical gate; framework/API availability is not a pass | Hold release until real-device evidence exists | Accessibility owner and qualified testers unresolved | `HELD` |
| Test and validation boundary | Platform test frameworks are possible; exact test stack is not selected | No test/telemetry package selected | Android/iOS real-device, migration, accessibility and safety reviewers | Deterministic state fixtures, process kill, schema migration and native dialog coverage required | AT evidence cannot be replaced by simulator or AI claim | Hold release; record missing evidence and owner | Independent validation owner/capacity unresolved | `HELD` |
| Android/iOS build, signing and store artifacts | KMP shared module plus native host projects produce separate platform artifacts; exact release tools not selected | No CI, registry or signing provider selected | Android/Gradle and Xcode/Swift build/signing owners; organizational store authority | Exact source/dependency/toolchain/artifact digest and DEBATE-005 graph must bind; store rollout is partial/observable | Store/build errors must not be misrepresented as product safety status | Reproducible/recoverable provider-independent artifact path; hold if custody missing | Release/security owner, key custody and incident response unresolved | `HELD` |
| Provenance/SBOM/trust-root closure | DEBATE-005 requires artifact-bound provenance/SBOM and independent verification; no implementation selected | No SBOM/attestation tool or format selected | Release-security owner and independent verifier | Shared/core/native/dependency/toolchain/base-image inputs must be bound to each artifact | Evidence/hold/revocation must remain user-visible where relevant | Quarantine/rebuild from known inputs | Trust-root, verifier and evidence-custody owners unresolved | `HELD` |

### 4.3 Toolchain and dependency closure observations

`OFFICIAL EVIDENCE`: the Kotlin Multiplatform compatibility guide makes the Kotlin/KMP plugin version part of a matrix with
Gradle, Android Gradle Plugin and Xcode. The exact `2.4.20` row is therefore recorded as a single compatibility snapshot,
not as permission to mix arbitrary “latest” tools.

The official guide also records migration/deprecation pressure affecting KMP projects, including Android target plugin
configuration, deprecated target shortcuts, legacy multiplatform libraries and Gradle integration. The future build plan
must therefore record:

- exact Kotlin compiler and KMP plugin identity;
- exact Gradle, AGP, JDK, Xcode and Swift integration identity;
- target architectures and simulator/device coverage;
- generated iOS framework integration mode and artifact identity;
- source-set hierarchy and platform-specific dependency closure;
- direct/transitive lock and integrity evidence;
- compiler/toolchain/base-image/cache provenance;
- native API and permission declarations;
- primary/backup owner, EOL/security response and replacement path for every critical native dependency;
- migration and rollback evidence for each toolchain upgrade.

`UNRESOLVED`: the repository has no KMP project, lockfile, dependency graph, generated framework, CI pipeline, signing
configuration or named native owner. Every row remains `HELD` until those facts are supplied through later authorized
work. This dossier intentionally does not select a package, provider, UI toolkit, database, test framework, CI
system, store service, Compose UI path or OTA channel.

## 5. Equal S1–S15 Scenario Record

These records apply the frozen fixture and the controlled record in
04_TECH_STRATEGY/DEBATES/DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md §5. They are KMP-native design hypotheses, not
implementation claims. The candidate is shared KMP domain/data logic with separate native Android and iOS UI; no shared
Compose UI is included. Every result is HELD because no code, lockfile, signed artifact, physical-device run,
accessibility oracle, qualified safety review or accountable delivery capacity exists.

### S1 — First value without an account

- authoritative starting state: No account, server authority or prior local profile; the user selects one motorcycle/variant.
- allowed transition: Persist the selection, show account/skip choice and later an explicit migration preview; never silently merge or overwrite history.
- candidate mechanism: Shared KMP state/repository contract with platform persistence adapters; no database or auth path is selected.
- official evidence: KMP documents shared logic with native UI; Android architecture and native storage/security boundaries remain platform-owned (see §1.1).
- reasoned inference: KMP can share the state transition, but durability, anonymous identity and account binding remain Kavriva-owned.
- dependency-specific evidence: No database, serialization, authentication or migration dependency is selected; see §4.2.
- unresolved facts: Anonymous-profile policy, schema, idempotent bind, deletion, backup and key behavior.
- user-visible result: Useful selected-task value before sign-in, with Turkish copy distinguishing local, migrated and authoritative data.
- failure/hold behavior: An unproven local write or migration holds the transition and preserves the last durable state.
- recovery path: Reopen the durable checkpoint, revalidate after sign-in and quarantine ambiguous records for review.
- shared-system obligation: Account, history, provenance, deletion and privacy semantics are candidate-neutral.
- candidate-attributable work: KMP state contracts, native persistence adapters, migration UI and two-platform tests.
- accountable AI/external owner: AI data/UI implementer; product/account owner and independent data reviewer.
- required later real-device evidence: Fresh install, no-account use, force-close/restart, sign-in migration, duplicate submit and restore/clone on both fixtures.
- residual risk: Shared domain logic may hide a non-portable schema or unsafe account merge across native adapters.
- result: HELD.

### S2 — Compact offline task download

- authoritative starting state: Online authority selects one motorcycle/task closure; required compact guidance is at most 12 MB, optional media is separate and unrelated 2 GB content is out of scope.
- allowed transition: Show measured size, request explicit cellular confirmation above 25 MB, stage manifest/digest, resume, verify and atomically promote only a complete package.
- candidate mechanism: Shared KMP package-state and manifest contracts with native Android/iOS transfer and storage adapters.
- official evidence: KMP supports shared logic/native UI; Android background-work, Apple background-task and background-transfer docs describe constrained platform mechanisms (see §1.1).
- reasoned inference: KMP can share package semantics, but timely background execution, atomic promotion and low-storage behavior require native implementation and evidence.
- dependency-specific evidence: No downloader, cache, database or checksum dependency is selected; §4.2 remains HELD.
- unresolved facts: Package schema/digest, reservation, retry/cancel/resume, OS quotas, cache eviction and integrity policy.
- user-visible result: Only the selected compact package is offered offline; optional media and progress/paused/failed states are explicit in Turkish.
- failure/hold behavior: Partial, corrupt, expired or insufficient-space packages are non-actionable and retain a recoverable retry/stop path.
- recovery path: Foreground resume/restart, remove only verified temporary artifacts, recheck generation and promote once.
- shared-system obligation: Scoped delivery, safety closure, cache limit and no full-catalog fallback apply to every candidate.
- candidate-attributable work: Shared transfer state, native adapters, progress semantics, permission/storage handling and interruption tests.
- accountable AI/external owner: AI transfer implementer; Android background-transfer and iOS URLSession/background specialists plus content/release authority.
- required later real-device evidence: 1 Mbps/300 ms/5% loss, loss/restart, low storage, Doze/iOS expiration, cancellation, duplicate/corrupt package and 12/150 MB boundaries.
- residual risk: A shared state machine can appear correct while a native transfer or promotion path loses safety closure at process death.
- result: HELD.

### S3 — Interrupted active physical work

- authoritative starting state: An active task has a last durable committed checkpoint; lock, call, process termination or restart occurs.
- allowed transition: Restore only the last durable checkpoint, label in-flight physical state unknown/partial, safe-stop and require explicit revalidation.
- candidate mechanism: Shared typed checkpoint/recovery contract with native lifecycle, journal and persistence adapters.
- official evidence: KMP’s shared-logic/native-UI boundary and Android/Apple lifecycle/background guidance establish platform integration surfaces; they do not observe every termination (see §1.1).
- reasoned inference: Lifecycle callbacks are signals, not proof; physical truth cannot be reconstructed from a restored screen.
- dependency-specific evidence: No journal, database, lifecycle or concurrency dependency is selected.
- unresolved facts: Atomic commit boundary, journal schema, process-kill behavior, recovery copy and physical-task semantics.
- user-visible result: Turkish safe-stop, unknown/partial and revalidation states are explicit; no automatic continuation is shown.
- failure/hold behavior: Missing or inconsistent checkpoint holds the task; no silent replay, duplicate completion or inferred physical state.
- recovery path: Reopen last committed state, inspect the physical condition, reconcile authority and record the explicit recovery outcome.
- shared-system obligation: Conservative recovery, no silent loss/overwrite, audit and safety authority are framework-neutral.
- candidate-attributable work: Native lifecycle bridges, durable journal integration, KMP transition contracts and kill/restart tests.
- accountable AI/external owner: AI recovery implementer; qualified safety owner and Android/iOS lifecycle reviewers.
- required later real-device evidence: Lock/call/process kill/restart, low memory, interrupted write, camera interruption and clock-change tests on both platforms.
- residual risk: Common code may assume a dispatcher or callback that the OS never guarantees, especially across Kotlin/Swift boundaries.
- result: HELD.

### S4 — Recall while offline or dormant

- authoritative starting state: A verified compact guide is cached while the device is offline; a newer recall/correction is not observable.
- allowed transition: Teach only the last valid generation within declared scope/age; block or downgrade current-authority actions until reconciliation.
- candidate mechanism: Shared content-generation, validity, stale, recall and safe-stop state with native foreground/background reconciliation.
- official evidence: KMP shared logic/native UI plus Android and Apple constrained background mechanisms are documented in §1.1; notifications are platform surfaces, not authority.
- reasoned inference: Offline KMP code cannot manufacture a current recall and a notification/deep link cannot replace server reconciliation.
- dependency-specific evidence: No push, notification, clock, recall or OTA dependency is selected.
- unresolved facts: Recall TTL/priority, offline validity window, clock manipulation, withdrawal/correction API and notification provider.
- user-visible result: Stale/dormant status, scope, age and safe-stop/recovery guidance are visible and accessible in Turkish.
- failure/hold behavior: Withdrawn, expired, incompatible or unknown generations hold affected actions while verified recovery content remains available where allowed.
- recovery path: Reconnect, re-authenticate if needed, fetch current generation, reconcile local history and retain the old record as provenance.
- shared-system obligation: Publication, recall, current eligibility, notification policy and safety wording are shared-system truth.
- candidate-attributable work: Generation state mapping, native notification/deep-link adapters, foreground reconciliation and accessibility announcements.
- accountable AI/external owner: AI content-state implementer; qualified safety/content publisher and authorization owner.
- required later real-device evidence: 72-hour offline, clock change, notification denial, background restriction, cold link and correction/withdrawal reconciliation.
- residual risk: Native UIs can make stale material look authoritative unless state semantics are unambiguous across both platforms.
- result: HELD.

### S5 — Old client and changed content meaning

- authoritative starting state: An older signed client sees a new safety-critical field, unit, meaning, configuration or content capability.
- allowed transition: Negotiate explicit client/content capability; render only known safe subsets and fail closed on unknown safety meaning.
- candidate mechanism: Versioned shared consumer contracts, capability matrix, content envelope and separate native release artifacts.
- official evidence: KMP compatibility and iOS framework integration sources in §1.1 show toolchain/framework coupling; they do not provide product semantic negotiation.
- reasoned inference: One shared Kotlin revision does not change already-signed binaries or solve old API/schema/content compatibility.
- dependency-specific evidence: No serializer, schema, API client or capability library is selected; generated framework identity is unresolved.
- unresolved facts: Compatibility window, unknown-field policy, minimum-version enforcement, content fallback and rollback refusal.
- user-visible result: Clear compatible/needs-update/held status; never an invented interpretation of a new safety field.
- failure/hold behavior: Unknown critical meaning blocks the affected flow; known portable history remains scoped and labelled.
- recovery path: Staged store release, server capability gate and reviewed forward migration; no OTA binary authority.
- shared-system obligation: API/content versioning, release graph and fail-closed safety policy are common.
- candidate-attributable work: Kotlin contract adapters, Swift/Android bindings, capability display and mixed-client test matrix.
- accountable AI/external owner: AI release/data implementer; API/content owner, safety reviewer and store custodian.
- required later real-device evidence: Old/new client pair, changed fields, forced update, offline period, rollback refusal and mixed rollout.
- residual risk: Common source may look source-compatible while Swift framework ABI/API and old signed clients remain incompatible.
- result: HELD.

### S6 — Local-to-profile migration conflict

- authoritative starting state: Local notes/history and a server profile differ after offline edits, duplicate submit, account bind or restore.
- allowed transition: Display scope and conflict preview, use operation IDs/idempotency, retain provenance and request explicit resolution.
- candidate mechanism: Shared conflict/operation state contracts with platform database, transaction and account adapters.
- official evidence: KMP supports selective shared logic/native platform code; official documentation does not define Kavriva merge or transaction semantics (see §1.1).
- reasoned inference: KMP can reduce duplicated conflict rules only if the native stores and Kotlin/Swift interop preserve identical semantics.
- dependency-specific evidence: No database, ORM, serializer, auth or conflict package is selected.
- unresolved facts: Merge precedence, tombstones/deletion, private-note rules, server conflict API, migrations and restore interaction.
- user-visible result: Partial/conflict/needs-review status is explicit, localized and accessible; no silent last-write-wins for protected truth.
- failure/hold behavior: Ambiguous records are quarantined and affected authority is held; duplicate retries do not duplicate outcomes.
- recovery path: Retry idempotently, resolve explicitly, preserve audit/provenance and reconcile current authority.
- shared-system obligation: History, audit, conflict, deletion and privacy policy are candidate-neutral.
- candidate-attributable work: Shared operation model, native transaction adapters, migration UI and parity tests.
- accountable AI/external owner: AI data implementer; data authority, security/privacy reviewer and safety owner.
- required later real-device evidence: Offline edits, duplicate submit, process kill during migration, storage pressure, restore/clone and conflict resolution.
- residual risk: Divergent Kotlin/Swift value mapping or transaction behavior can produce asymmetric history without a common executable oracle.
- result: HELD.

### S7 — Camera, file and evidence flow

- authoritative starting state: The user denies then grants permission, captures/imports evidence and uploads over an unstable network.
- allowed transition: Use native permission/picker/camera surfaces, classify input as untrusted, stage metadata and upload idempotently; never silently discard evidence.
- candidate mechanism: Native Android Photo Picker/documents/camera and iOS PHPicker/UIDocumentPicker/camera; shared KMP media metadata and operation states only.
- official evidence: Android Photo Picker/documents/files and Apple PHPicker/UIDocumentPicker are the platform boundaries linked in §1.1.
- reasoned inference: KMP should not own OS permission, URI/security-scoped lifetime or platform picker UI; no Compose shared UI is implied.
- dependency-specific evidence: No camera, file, image parser or upload package is selected; §4.2 rows are HELD.
- unresolved facts: MIME/size scan, temporary cleanup, URI lifetime, metadata/privacy classification, upload retry and key handling.
- user-visible result: Permission, file-type, upload-progress, paused/failed and privacy states are Turkish, explicit and accessible.
- failure/hold behavior: Invalid, partial, untrusted or interrupted evidence is quarantined; the app never reports full upload on partial success.
- recovery path: Reacquire permission, restore staged file if valid, resume idempotently or offer manual evidence entry with provenance.
- shared-system obligation: Evidence ownership, privacy, audit, disclosure and source lineage are product-wide.
- candidate-attributable work: Two native adapters, Swift/Kotlin interop, shared metadata schema and process-death tests.
- accountable AI/external owner: AI media implementer; Android/iOS media specialists, privacy/security reviewer and evidence owner.
- required later real-device evidence: Denial/grant, picker cancellation, low storage, process kill, large files, unstable network, duplicate retry and AT on native surfaces.
- residual risk: Native file/security-scoped-resource differences can create data loss or privacy leakage despite identical shared metadata.
- result: HELD.

### S8 — Accessibility during a safety-critical step

- authoritative starting state: Turkish readiness, warning, unexpected-state stop, safe recovery and active-step screens run on both native UIs.
- allowed transition: Expose the same state meaning with readable text, roles, focus/order, announcements and non-gesture alternatives; never infer safety from visual similarity.
- candidate mechanism: Shared semantic/state IDs and Turkish copy contract; native Android accessibility and iOS accessibility implementations.
- official evidence: Android accessibility and Apple accessibility guidance are linked in §1.1; KMP docs only establish the shared/native boundary.
- reasoned inference: Native UI gives a direct platform path, but API availability and shared semantics are not device acceptance.
- dependency-specific evidence: No accessibility wrapper or UI toolkit is selected; no Compose accessibility result is inherited.
- unresolved facts: Exact UI toolkit choices, labels/roles, dynamic type/font scale, reduced motion, switch/voice control and reviewer capacity.
- user-visible result: The user can understand readiness, uncertainty, stop and recovery in Turkish through VoiceOver/TalkBack and alternative controls.
- failure/hold behavior: Any critical AT, largest-text, focus or non-color failure holds the release and affected flow.
- recovery path: Accessible safe-stop/retry path, preserve last durable state and obtain human review before resuming.
- shared-system obligation: Turkish wording, safety semantics and acceptance oracle are common to all candidates.
- candidate-attributable work: Two native UI implementations, semantic mapping, focus restoration and platform dialog coverage.
- accountable AI/external owner: AI UI implementer; independent VoiceOver/TalkBack reviewers and qualified safety/content reviewer.
- required later real-device evidence: VoiceOver/TalkBack, Switch/Voice Control, largest text/reflow, contrast, reduced motion and native permission/picker/share/notification surfaces.
- residual risk: Two native implementations can drift in focus, announcement or uncertainty meaning even when KMP state codes match.
- result: HELD.

### S9 — Framework/plugin or OS/toolchain upgrade

- authoritative starting state: A planned release or forced Apple/Google requirement change affects Kotlin/KMP, Gradle/AGP, Xcode/Swift or a critical native dependency.
- allowed transition: Re-pin one compatibility graph, review changes, regenerate framework, run evidence and stage only after acceptance; retain the previous artifact.
- candidate mechanism: Kotlin 2.4.20/KMP plugin snapshot with native host projects and generated iOS framework; no upgrade path is selected.
- official evidence: The official KMP compatibility guide records Kotlin/KMP, Gradle, AGP and Xcode compatibility plus migration/deprecation considerations (see §1.1).
- reasoned inference: Shared domain code can reduce duplicate rule edits, while KMP/Gradle/Swift/Xcode integration adds a cross-toolchain closure to review.
- dependency-specific evidence: No third-party critical dependency is selected, so no EOL or replacement evidence exists.
- unresolved facts: Exact JDK/SDK/architectures, source/dependency locks, generated-framework identity, supported-version policy and rollback test.
- user-visible result: Upgrade status is explicit; affected content/build remains held rather than silently changing behavior.
- failure/hold behavior: Incompatible build, generated interface, migration or AT result blocks staging; no floating-latest or emergency bypass.
- recovery path: Restore the prior signed artifact, quarantine incompatible data/path, then forward-migrate only after reviewed evidence.
- shared-system obligation: Release integrity, support floor, dependency provenance, safety correction and store compatibility are common.
- candidate-attributable work: Kotlin/Gradle/Xcode graph maintenance, Swift/Kotlin API review, native UI regression and two-store staging.
- accountable AI/external owner: AI upgrade implementer; Kotlin/Gradle, Android, iOS/Xcode, security and store custodians.
- required later real-device evidence: Both comparison devices, all critical S1–S15 flows, AT matrix, signed staging, dependency/SBOM diff and rollback rehearsal.
- residual risk: A KMP update can alter generated iOS APIs or compiler behavior without changing common source appearance.
- result: HELD.

### S10 — App, backend, content and configuration mixed rollout

- authoritative starting state: Old/new Android and iOS clients coexist while API, schema, content, configuration and derived assets change.
- allowed transition: Bind each signed artifact to shared revision, capability table, API/schema/content/config generations and migration state; deny unknown safety combinations.
- candidate mechanism: Two native store artifacts consuming a versioned KMP shared module; server remains authoritative; no OTA binary channel.
- official evidence: KMP iOS framework integration and compatibility sources in §1.1 establish artifact/toolchain identity requirements, not rollout policy.
- reasoned inference: Shared Kotlin revision helps identify core provenance but cannot authorize a mixed client or make a partial publication whole.
- dependency-specific evidence: No OTA, configuration, release SDK or rollout provider is selected.
- unresolved facts: Minimum versions, compatibility matrix, server gating, config signing, content fallback and mixed-store observation.
- user-visible result: Compatible/current, stale, needs-update, held and safe-stop states are distinct and truthful.
- failure/hold behavior: Unknown or mixed safety semantics are held; already-downloaded valid content stays scoped and labelled.
- recovery path: Pause affected generation, retain old artifact, publish reviewed correction/update and reconcile on foreground.
- shared-system obligation: API/content/release authority, recall, configuration and publication semantics are candidate-neutral.
- candidate-attributable work: Shared capability contracts, native update prompts, framework artifact binding and dual-platform release tests.
- accountable AI/external owner: AI release implementer; backend/content owner, safety reviewer, release/security and store authorities.
- required later real-device evidence: Staged Android/iOS rollout, old/new matrix, offline cache, changed config/content, pause and recovery.
- residual risk: Separate native artifact versions and generated framework changes increase the number of mixed states requiring evidence.
- result: HELD.

### S11 — Low/mid device resource pressure

- authoritative starting state: Constrained Android API 29/4 GB/2 GB free and oldest comparison iPhone exercise history, photos and one scoped package.
- allowed transition: Keep cache at 250 MB, request only selected compact data, separate optional media and preserve a recoverable state under pressure.
- candidate mechanism: Shared data-size/eviction/state contracts; native lists, image/file handling, storage and lifecycle behavior per platform.
- official evidence: KMP documents selective shared logic/native platform access; Android architecture and native file/storage sources are linked in §1.1.
- reasoned inference: KMP domain/data sharing does not provide a memory, image-decoding, database or battery budget.
- dependency-specific evidence: No image, database, cache, telemetry or performance package is selected.
- unresolved facts: Media format/resize, paging, DB engine, eviction/retention, startup budget, thermal policy and device access.
- user-visible result: Progress, storage warning, paused/failed, cache-scope and safe-stop states remain explicit; unrelated catalog is not downloaded.
- failure/hold behavior: Insufficient storage/memory or incomplete package holds the affected operation without silent deletion of evidence/history.
- recovery path: Clean only disposable verified cache/temp data, reduce optional media, resume in foreground and reconcile.
- shared-system obligation: Data minimization, cache policy, retention, offline scope and no silent history deletion are common.
- candidate-attributable work: Two native rendering/storage paths, KMP size/eviction contracts, profiling and interruption evidence.
- accountable AI/external owner: AI performance/data implementer; Android/iOS performance owners and data/security reviewer.
- required later real-device evidence: Cold/warm startup, local stress fixtures, 2 GB free boundary, low storage, thermal/background, image decode, DB recovery and AT.
- residual risk: Two native UI/runtime implementations can expose different memory and low-storage failure behavior.
- result: HELD.

### S12 — Release and incident day

- authoritative starting state: A planned or emergency release has KMP shared revision, two native artifacts and API/content/config generations.
- allowed transition: Verify provenance/SBOM, signing and independent review, stage stores, observe, pause affected rollout and issue a reviewed correction.
- candidate mechanism: DEBATE-005 release graph bound to KMP module, generated framework, native hosts, migration and content; no OTA.
- official evidence: KMP compatibility/iOS integration and Android/Apple platform release boundaries are linked in §1.1; no store result is claimed.
- reasoned inference: KMP-native needs one shared-core proof plus two UI/build/signing proofs; either platform can hold the release.
- dependency-specific evidence: CI, signing, SBOM/attestation and store providers are not selected; §4.2 is HELD.
- unresolved facts: Artifact custody, trust roots, release roles, incident reach-back, store account access and correction workflow.
- user-visible result: Current/held/recalled/safe-stop status is truthful; release or incident state is never represented as an app safety pass.
- failure/hold behavior: Missing reviewer, signing evidence, platform artifact or impact map pauses publication and preserves the last accepted artifact.
- recovery path: Identify affected shared/native/content generations, suspend, correct, re-test, re-sign and reconcile.
- shared-system obligation: Publication, recall, audit, rollback/recall and emergency suspension rules are framework-neutral.
- candidate-attributable work: Dual-platform build graph, generated-framework attestation, native UI release tasks and platform incident fixes.
- accountable AI/external owner: AI release implementer; store-account owner, security custodian, qualified safety reviewer and Android/iOS operators.
- required later real-device evidence: Staged signed artifacts, pause/release drill, impact query, offline recall, rollback refusal and recovery.
- residual risk: Kotlin/Native framework identity and native artifacts can diverge from the shared source unless attestation is enforced.
- result: HELD.

### S13 — Privacy, collaboration and device trust

- authoritative starting state: Private notes/photos, shared/community/official records, ownership transfer or revocation occur before/after offline use or restore.
- allowed transition: Preserve classification/provenance, bind protected state to account/device/key context, revoke future authority and treat exports as non-retractable.
- candidate mechanism: Shared privacy/trust/provenance state contracts with Android Keystore and Apple Keychain boundaries.
- official evidence: Android Keystore, Apple Keychain and KMP native-integration sources are linked in §1.1.
- reasoned inference: KMP can share labels and transitions, but key storage, device binding, backup and OS access remain native.
- dependency-specific evidence: No auth, crypto, key wrapper, backup or sharing dependency is selected.
- unresolved facts: Role/entitlement contract, key rotation/loss, backup inclusion, export format, revocation and deletion semantics.
- user-visible result: Private/shared/community/official labels, lock/re-auth/quarantine and disclosure warnings are accessible and explicit.
- failure/hold behavior: Restored/cloned cache cannot create authority; key mismatch or revoked access quarantines affected state.
- recovery path: Re-authenticate/reconcile, preserve history and attribution, re-download scoped content and retain export provenance.
- shared-system obligation: Privacy, ownership, revocation, history retention and export disclosure are product-wide.
- candidate-attributable work: Native secure-storage adapters, shared trust states, share/export UI and device-loss tests.
- accountable AI/external owner: AI security/data implementer; security/privacy reviewer, account authority and platform key specialists.
- required later real-device evidence: Same/different trust context restore, clone, key loss/rotation, revocation, export and AT.
- residual risk: Platform key/backup differences can invalidate otherwise identical KMP trust-state transitions.
- result: HELD.

### S14 — Entitlement, evidence and ownership lifecycle

- authoritative starting state: Entitlement changes, source withdrawal, community correction/hold, selective motorcycle transfer or deletion occur during/after physical work.
- allowed transition: Preserve safe completion/stop/recovery, re-review dependent claims, retain attribution/correction provenance and mark transferred history partial where needed.
- candidate mechanism: Shared eligibility, provenance, correction, withdrawal and ownership-event contracts; native UI only presents the resulting states.
- official evidence: KMP shared-logic/native-UI boundary is documented in §1.1; authorization and publication are not framework capabilities.
- reasoned inference: KMP cannot decide entitlement, source trust, deletion or current eligibility; it can only carry explicit server-owned outcomes.
- dependency-specific evidence: No identity, subscription, authorization, audit or content client is selected.
- unresolved facts: Entitlement provider, effective-time rules, source withdrawal, transfer gaps, deletion/retention and audit authority.
- user-visible result: Active work can safe-stop/recover; current eligibility, partial ownership and withdrawn evidence are clearly labelled.
- failure/hold behavior: Unknown entitlement or authority holds affected actions; no silent history rewrite or deletion of independent evidence.
- recovery path: Reconcile current authority, re-review dependent claims, preserve records and complete safe recovery with explicit user action.
- shared-system obligation: Safety, authorization, content publication, evidence lineage and retention are candidate-neutral.
- candidate-attributable work: Shared event/state adapters, native re-auth/hold screens, migration and parity tests.
- accountable AI/external owner: AI lifecycle/state implementer; authorization owner, safety reviewer and privacy/legal authority.
- required later real-device evidence: Offline entitlement change, source withdrawal, ownership transfer with gaps, deletion of one copy and active-task recovery.
- residual risk: Shared event models can be mistaken for authority if native clients accept local eligibility without reconciliation.
- result: HELD.

### S15 — Backup, restore, clone and key loss

- authoritative starting state: Android/iOS backup restore occurs in same/different trust context; clone, key loss/rotation, schema change or replayed eligibility metadata is present.
- allowed transition: Quarantine restored positive state, reconcile account/device/key/release/revocation, preserve portable data and never export raw keys.
- candidate mechanism: Shared migration/trust/quarantine contracts with native backup, Keystore/Keychain and secure-storage adapters.
- official evidence: Android Keystore and Apple Keychain sources in §1.1 establish protected-key boundaries; KMP integration does not define backup policy.
- reasoned inference: A generated iOS framework or shared KMP model cannot make restored cache, keys or eligibility authoritative.
- dependency-specific evidence: No database, encryption, backup, auth or migration package is selected.
- unresolved facts: Backup inclusion/exclusion, schema format, key rotation/loss, clone detection, account bind, retention and migration.
- user-visible result: Quarantine, re-auth, partial restore and recovery choices are visible, localized and accessible.
- failure/hold behavior: Key loss, mismatched trust or unsafe migration holds positive actions; no plaintext/key-copy fallback.
- recovery path: Re-authenticate, re-download scoped content, preserve history/export, forward-migrate and record the recovery outcome.
- shared-system obligation: Data continuity, key custody, privacy, restore/clone trust and no silent deletion apply to every candidate.
- candidate-attributable work: Shared migration state, native key/backup adapters, quarantine UI and restore game-day evidence.
- accountable AI/external owner: AI data/security implementer; Android/iOS backup specialists, security reviewer and account authority.
- required later real-device evidence: Same/different device restore, clone, key loss/rotation, schema migration, replayed eligibility and AT.
- residual risk: Divergent platform backup/key semantics can break data continuity even with identical shared contracts.
- result: HELD.

No aggregate or convenience score can override a safety, data-continuity, accessibility, release-integrity or
recoverability hold.

## 6. Accessibility Matrix

This is a native Android/iOS capability-and-evidence matrix, not an accessibility approval. The KMP module may expose
stable state codes, semantic identifiers and Turkish copy contracts; it does not render shared Compose UI. Native system
surfaces remain platform-owned. Official API availability is not a real-device pass, and every row remains HELD.

| Check | Framework/documented capability | Platform-specific work | Later real-device oracle | Status |
|---|---|---|---|---|
| VoiceOver | Shared KMP state/semantic IDs can feed native labels, roles and state transitions; no shared renderer | Native iOS UI, Dynamic Type, picker, permission, notification, share and universal-link surfaces | VoiceOver through readiness, warning, stop, recovery, conflict, restore and offline states in Turkish | HELD |
| TalkBack | Same shared state meanings and copy IDs can feed native Android semantics; no automatic parity | Native Android UI, font scale, Photo Picker, permission, notification, share and intent surfaces | TalkBack through the same critical states, process interruption and low-storage paths | HELD |
| Largest text/reflow | KMP can carry text/state meaning; native layout and text measurement remain separate | Android font scale/large display and iOS Dynamic Type; no UI toolkit selected | No clipping/truncation/overlap, actionable scroll/reflow and diagram/text alternatives on both devices | HELD |
| Focus and reading order | Shared transitions can identify the next semantic state, not platform focus behavior | Native navigation, focus restoration, back/cancel and return from system surfaces | Keyboard/switch/AT focus across every safety transition and interruption | HELD |
| State announcements | Shared stable status codes and Turkish copy contract | Native live-region/announcement, alert, permission, notification and deep-link behavior | Active/readiness/warning/unknown/stop/recovery/conflict/recall announcements | HELD |
| Non-color status/contrast | Shared state model can require text/icon/semantic status; no visual proof | Native contrast, dark/high-contrast settings and system controls | Contrast/color-blind checks, text/icon alternatives and no color-only safety status | HELD |
| Reduced motion | Shared contract can declare reduced-motion-sensitive transitions | Native Android/iOS animation policy and OS preference integration | Warnings, stop, navigation and media remain comprehensible with reduced motion | HELD |
| Switch/voice control | Native semantics can expose controls from shared action IDs | Android Switch/Voice Access and iOS Switch Control/Voice Control labels and actions | No gesture-only critical action; scanning, voice labels and cancellation on both platforms | HELD |
| Reduced dexterity | Shared action model can define cancel/retry/safe-stop alternatives | Native touch targets, timeout, picker cancellation, system back and share return | One-hand operation, target size, no time trap and safe-stop/retry under interruption | HELD |

## 7. Upgrade and Forced-Event Walkthrough

The walkthrough uses four planned release windows per year plus the approved annual safety/security and forced
platform/toolchain stress events. No duration or SLA is invented; duration, staffing and cost remain UNRESOLVED.

| Event | KMP-native path under the fixture | Affected contracts/evidence | External dependency/capacity | Hold/recovery |
|---|---|---|---|---|
| Normal planned release window | Re-pin Kotlin/KMP, Gradle/AGP/JDK, Xcode/Swift and native UI revisions as one graph; regenerate iOS framework; build two artifacts; run S1–S15, AT, migration and release evidence; stage stores | Shared source/framework identity, native UI, schema/content/config, offline packages, provenance/SBOM/signing | Kotlin/Gradle, Android, iOS/Xcode, Mac, devices, AT/safety reviewers, store custodian | Hold on any missing graph/evidence; retain prior signed artifacts; forward migration only after review |
| Safety/security emergency correction | Prefer reviewed server/content revocation or correction; binary correction uses the same two-artifact signed graph; no OTA authority | Recall/withdrawal generations, offline safe-stop, audit, API/content compatibility and artifact impact map | Qualified safety/security reviewer, incident authority, store accounts and native operators | Pause affected generation/release, preserve evidence, publish reviewed correction and reconcile; no calendar promise |
| Forced Apple/Google build/store requirement | Update native host/toolchain and KMP compatibility row, regenerate framework, rebuild/sign both platforms and rerun critical evidence | Kotlin/KMP/Gradle/AGP/Xcode/SDK, store target rules, generated Swift interface, permissions and AT | Apple/Google account access, Mac/Xcode, Android build owner, signing, devices and review capacity | Hold if any platform cannot be rebuilt or verified; preserve last accepted artifact and portable data |
| Critical dependency abandonment/incompatibility | Since no dependency is selected, future event requires inventory, replacement with native/owned adapter or removal of affected capability, then lock/SBOM/evidence update | Platform API, key/storage, DB/serialization, camera/media/transfer/background contracts | Native Android/iOS specialists, security/data reviewer, replacement capacity and source provenance | Quarantine affected capability; keep safe manual path if valid; forward-migrate only after replacement evidence |
| Old/new client, API, schema, content/config coexistence | Bind shared revision, generated framework, native revisions and server generations; use capability/minimum-version gates; no OTA | Mixed-client release graph, unknown-field behavior, local cache, migration, recall and config signing | Backend/content owner, store custodian, safety/release reviewer | Hold incompatible combinations; retain known-safe artifact and reconcile on foreground |
| Rollback refusal after unsafe migration | Refuse binary rollback when data/schema/key migration cannot safely reverse; do not erase or downgrade user truth | Local schema/history, keys, content generations, old-client capability and restore path | Data/security reviewer, release authority and recovery-game-day capacity | Hold affected release; quarantine/forward-migrate from durable state; rollback refusal is explicit, not hidden failure |
| Incident pause, impact and recovery | Use release graph to identify shared KMP revision, generated framework, native artifacts, API/content/config generations and affected offline packages; pause and re-test | Provenance/SBOM, audit, recall, suspension, signing and correction contracts | Incident commander, security/safety/content/store authorities and independent verifier | Suspend, preserve logs/artifacts, issue reviewed correction, re-sign/re-stage and reconcile; duration remains UNRESOLVED |

## 8. AI-Operability and Task Isolation

The approved AI-operated model requires bounded tasks, separated implementation/review/validation and portable
evidence. KMP-native may create explicit shared-core and two-native-UI work units, but no executable task graph or
deterministic build evidence exists yet.

| Question | Evidence/result |
|---|---|
| Can a fresh AI implement one bounded task without whole-project context? | Candidate-shaped split is possible: shared contract, Android adapter, iOS adapter or evidence task. No KMP project, TASK graph or contract fixtures exist; HELD. |
| Are platform exceptions visible in the task graph? | Native UI, lifecycle, storage, media, background, signing and generated-framework boundaries are named in §§3–4; exact tasks/owners are absent; HELD. |
| Can implementation, review and validation remain separate? | Shared-core review plus independent Android/iOS, accessibility, safety, security and release validation can be specified; no run or reviewer capacity exists; HELD. |
| Are builds/tests deterministic enough to produce evidence? | Exact Kotlin/KMP 2.4.20 snapshot is recorded, but project locks, generated framework, host toolchains, CI and devices do not exist; HELD. |
| Can dependency changes identify affected contracts/tasks/tests? | §4 closure requires source/version, native exception, owner, EOL, fallback and evidence; no dependency graph/SBOM/impact automation exists; HELD. |
| Can the project recover without one opaque workstation/provider? | Portable source/contracts/artifacts are intended; iOS Mac/Xcode, signing custody, devices and store accounts remain external and unresolved; HELD. |
| Does the candidate require unavailable human specialist authority? | Yes, native Android/iOS lifecycle and release, VoiceOver/TalkBack, qualified safety/content, security/privacy, signing/store and incident authority are required; availability is unresolved; HELD. |

AI output, a generated KMP framework or a passing static check cannot impersonate a store account, signing key,
qualified safety decision, assistive-technology oracle or real-device result. User coding, debugging or build repair is
not a mitigation.

## 9. Equal 24-Month TCO Worksheet

TCO is recorded by equal workload category, not invented currency totals. The common fixture freezes both the MAU tiers
and monthly transfer/upload rates. Provider prices, legal retention policy, tester compensation and human rates remain
unresolved. The local-device stress fixture is never multiplied by MAU.

### 9.1 Workload quantities (not prices)

| MAU tier | Compact transfer bytes/month | Optional media bytes/month | Photo upload bytes/month | Retained photo bytes over 24 months if never evicted |
|---:|---:|---:|---:|---:|
| 1,000 | 24 GB | 10 GB | 1.5 GB | 36 GB |
| 10,000 | 240 GB | 100 GB | 15 GB | 360 GB |
| 50,000 | 1.2 TB | 500 GB | 75 GB | 1.8 TB |

The local fixtures remain 3/10 motorcycles, 250/2,000 history records, 50/500 photos at 3 MB, 100/1,000 notes,
20/200 pending operations and 3/30 conflicts. These are device stress inputs, not MAU volume forecasts. The arithmetic
uses two compact 12 MB transfers per MAU/month, optional 100 MB media for 10% of MAU and 0.5 photos at 3 MB per MAU/month.
Protocol overhead, retries, backup/replication, egress pricing, legal retention and support volume remain unresolved;
the retained-photo column is a comparison quantity, not a retention promise.

### 9.2 Cost categories

Unknown amount means UNRESOLVED, never zero. The only numeric baseline carried here is the owner-approved store
fixture in 04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md §9; it must be rechecked
before purchase. No provider, plan, currency conversion, tax, discount or human hourly rate is selected.

| Cost row | Product-wide unavoidable | Candidate-caused | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---|---|---|---|---|---|---|
| Store membership | Both planned stores | None specific to KMP | None | Renewal/tax/currency | Keep accounts/artifact history | Buy only when release/test gate requires | Google Play USD 25 one-time + Apple USD 99/year; 24-month store-only USD 124–223 before tax/currency/renewal timing; approved fixture / High |
| Mac/hosted iOS build | Required for iOS release path | KMP adds Swift/Kotlin framework integration to the native host | Hosted convenience | More builds/forced events | Backup Mac/host path | Local/borrowed Mac where recoverable | UNRESOLVED / Low |
| Android/iPhone access | Mandatory real-device evidence | Two native UI paths require both platform fixtures | Device lab/convenience | MAU does not multiply device fixture; release breadth may | Replacement/borrowed devices | Existing/borrowed devices and organized testers | UNRESOLVED / Low |
| CI/build artifacts | Reproducible evidence and signed artifacts | KMP + two hosts + generated iOS framework graph | Hosted CI/cache | Four windows and forced events | Portable local rebuild/archive | Local controlled build if recoverable | UNRESOLVED / Low |
| Backend/database | Product-wide authority, content and history | No KMP-specific provider selected | Managed convenience | MAU, media, retention and egress | Export/exit/rebuild | Capped/free tier with shutdown/export | UNRESOLVED / Low |
| Storage/backup/CDN/egress | Product-wide data delivery and continuity | KMP does not remove server/native backup obligations | CDN/replication convenience | MAU, retries, optional media and retention | Export, eviction and migration | Compact scope, optional media, quotas and alerts | UNRESOLVED / Low |
| Identity/email/SMS | Product-wide account/recovery | Kotlin/Swift bindings and key/re-auth states | SMS/convenience provider | MAU and recovery rate | Manual/exported recovery path | Approved email/manual path with caps | UNRESOLVED / Low |
| Crash/telemetry/analytics | Optional product operations | Two native runtimes and KMP boundary add observability surfaces | Analytics convenience | MAU/event volume | Export/disable path | Disabled or capped path pending privacy approval | UNRESOLVED / Low |
| Security/SBOM/signing | Product-wide trust and release integrity | KMP compiler/plugin, generated framework and dual native graphs | Paid scanner/host convenience | Each release/forced event | Reproducible archive and key rotation | Owned manifest/SBOM/attestation path if approved | UNRESOLVED / Low |
| Accessibility validation | Mandatory external acceptance | Two native UI implementations and native system surfaces | Paid lab/convenience | Every release/forced event | Alternate testers/device access | Organized/borrowed human AT capacity | UNRESOLVED / Low |
| Safety/content review | Mandatory product authority | Shared state mapping must preserve review semantics in both UIs | Expert/convenience capacity | Corrections, recalls and release events | Reach-back/incident coverage | Qualified owner or organized review | UNRESOLVED / Low |
| AI implementation/review | Capacity-dependent under approved model | KMP shared core plus two native UI/toolchain contexts | Extra AI/context tooling | Task/review volume and upgrades | Portable task artifacts and independent review | Approved AI plan with bounded context | UNRESOLVED / Low |
| Upgrade/dependency response | Product-wide platform changes | Kotlin/KMP/Gradle/AGP/Xcode/Swift plus dual native UI | Hosted upgrade tooling | Planned windows plus forced events | Previous artifact, owned/native replacement | Stable pin and controlled migration | UNRESOLVED / Low |
| Support/incident response | Product-wide emergency reach-back | KMP/native shared-core and two-store impact analysis | Contracted on-call | MAU, release and incident volume | Pause, recall, rollback refusal and replacement | Staged rollout and documented manual response | UNRESOLVED / Low |
| Exit/migration | Product-wide continuity obligation | KMP source/framework/native UI replacement and data adapters | Migration convenience | Triggered by unsuitability or platform change | Portable schema, exports and forward migration | Owned portable fixtures and dual-read period | UNRESOLVED / Low |

KMP-native has no numeric TCO result in this draft. Two native UIs, Kotlin/Gradle plus Swift/Xcode integration, generated
framework verification and dual-platform accessibility/release evidence are explicit workload categories, not claimed
savings or disqualifiers.

## 10. Exit Dossier

### Portable or replaceable assets

- Canonical content/data schemas, history/provenance, correction/withdrawal events, operation IDs, capability envelopes and migration descriptions.
- Offline-package manifests, digests, compact/safe-stop closure, compatibility fixtures and acceptance oracles.
- User-controlled exports, media lineage, Turkish copy/units, design tokens and accessibility intent.
- Native-boundary contracts for camera/files, notifications, deep links, secure storage, background triggers, lifecycle and sharing.
- Release graph references, audit evidence, SBOM/provenance records and last accepted artifact identity.

### Framework-, native- and toolchain-bound assets

- Shared KMP source sets, Kotlin/Native binaries, generated iOS frameworks, Gradle/KMP/AGP/JDK integration and Xcode/Swift host configuration.
- Android and iOS native UI implementation, navigation/focus code, platform permission/picker/share/background adapters and signed store artifacts.
- Android Keystore and Apple Keychain key material are not portable user data; raw keys cannot be exported as an exit shortcut.

### Identity, data continuity and replacement route

- Account/server identifiers, history/provenance and user exports must survive a renderer/framework replacement; local cache may be re-downloaded from scoped manifests.
- Replacement consumes the portable contracts through forward migration or a controlled dual-read/compatibility period; it may not silently rewrite history or delete evidence.
- If a schema/key migration cannot safely reverse, binary rollback is refused, the affected path is held and recovery proceeds from the last durable state or reviewed forward migration.
- A staged replacement requires a new independent release graph, native-device/accessibility/safety evidence, signing and store publication; no OTA binary authority is assumed.

Exact migration tooling, key continuity, interruption duration, replacement candidate, parity evidence and exit cost are
UNRESOLVED. No portability or exit success is claimed.

## 11. Candidate Result (Phase-4 Research)

| Mandatory gate | KMP-native record | Status |
|---|---|---|
| Safety/readiness and truthful uncertainty | Shared state contracts can describe conservative transitions; no implementation or qualified safety evidence exists | HELD |
| Offline scoped delivery and 72-hour behavior | Native transfer/background mechanisms are documented; package schema, atomic promotion, resume and recall proof are absent | HELD |
| Native closure and lifecycle/restart | Separate Android/iOS UI and lifecycle boundaries are explicit; no native adapters or kill/restart evidence exists | HELD |
| Accessibility and Turkish critical flow | Native API paths and shared semantic contract are named; independent VoiceOver/TalkBack real-device evidence is absent | HELD |
| Release, signing, provenance and forced events | KMP compatibility snapshot and release graph requirement are recorded; project locks, signing custody and store evidence are absent | HELD |
| Data continuity, backup/restore and key loss | Keystore/Keychain boundaries are documented; database/schema/backup/key-loss game-day evidence is absent | HELD |
| AI-operability and task isolation | Shared-core/two-native task split is describable; no executable task graph, deterministic build or independent review run exists | HELD |
| 24-month TCO and owner capacity | Equal worksheet and approved store baseline are recorded; capacity, usage, service and remaining price inputs are unresolved | HELD |
| Exit/migration and replacement continuity | Portable asset/forward-migration boundary is defined; migration rehearsal and replacement evidence are absent | HELD |

- mandatory-gate result: HELD; no gate is passed.
- S1–S15 result count: 0 PASS / 15 HELD / 0 REJECT.
- unresolved critical facts: Exact product OS/support floor; KMP/native project and locks; DB/serialization/network/key/backup implementation; generated framework integration; native UI toolkit; CI/signing/store custody; SBOM/trust roots; device/AT/safety capacity; release roles; API/content/config compatibility; workload/retention/provider costs; migration/exit rehearsal.
- largest low-budget burden: Qualitatively, two native UI/release paths plus iOS Mac/Xcode/signing and real-device/AT/safety access; no price or staffing quantity is asserted.
- largest AI-operability benefit/risk: Benefit is one shared domain/data invariant surface; risk is hidden Kotlin/Native–Swift/Gradle/Xcode interop and two native UI/lifecycle contexts.
- external authorities/capacity required: Apple/Google legal/store identities, signing custody, Mac/Xcode, Android/iPhone devices, VoiceOver/TalkBack reviewers, qualified safety/content, security/privacy, backend/content/API, incident and independent release verification.
- conditions for recommendation: No recommendation is made. A later decision record would require complete §4 closure, all S1–S15 evidence, native AT/device/safety/release oracles, owner/capacity/TCO approval, dependency/provenance evidence and independent review.
- disqualifiers triggered: None asserted as an intrinsic KMP-native rejection in this no-code draft; any ownerless critical path, unsafe bypass, lost canonical truth, unbounded unapproved cost or unsupported critical capability without fallback would be a rejection under the common rule.
- overall Phase-4 status: HELD.

This result is documentary Phase-4 evidence only. It claims no build, benchmark, real-device pass, accessibility pass,
security pass, safety approval or store release. Compose Multiplatform shared UI remains a separate candidate and is not
evaluated or inherited here.

### 11.1 Repository citation register

- 04_TECH_STRATEGY/DEBATES/DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md §§5–11 — controlled scenario, accessibility, forced-event, AI, TCO, exit and result fields.
- 04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md §§2–10 — frozen release/device/network/data/offline/privacy/AI/cost/pass-hold rules.
- 04_TECH_STRATEGY/DEBATES/DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md §§5–11 — mandatory gates, equal S1–S15 definitions, KMP-native boundary, AI-operability and TCO method.
- 00_CONTROL/DECISION_LOG.md DEC-0023–DEC-0031 — approved product/release/data/AI-operated/common-fixture decisions carried by Section 2.
- 04_TECH_STRATEGY/JUDGE_SUMMARY.md DEBATE-006 judgment — equal candidate dossiers, no framework selection and no ADR readiness.
- 04_TECH_STRATEGY/DEBATE_LOG.md DEBATE-006 entry — common fixture and evidence-gated comparison status.
- Official technical sources are limited to the Kotlin, Android and Apple links listed in §1.1; no vendor/provider or package has been selected.
