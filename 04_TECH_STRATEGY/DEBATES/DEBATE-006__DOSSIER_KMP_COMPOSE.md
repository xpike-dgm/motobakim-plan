# DEBATE-006 — EQUAL MOBILE CANDIDATE DOSSIER: KMP + COMPOSE MULTIPLATFORM

Status: STRUCTURALLY COMPLETE DRAFT / UNREVIEWED — NO-CODE / HELD
Date: 2026-09-17
Decision level: Phase-4 comparison evidence only; not a recommendation, ADR, approval or Gate 4 → 5 transition

Completion warning: Sections 1–11 of the controlled candidate template are now structurally present as documentary
research. They are unreviewed and held. No KMP + Compose scenario, accessibility check, build, benchmark, store release
or real-device pass has passed or is claimed.

This dossier evaluates KMP + Compose Multiplatform: shared Kotlin Multiplatform domain/data logic and shared Compose
Multiplatform UI, with native Android and iOS application hosts and explicit native exceptions. It does not evaluate
KMP-native, which keeps Android and iOS presentation native while sharing Kotlin logic only. Findings from the KMP-native
dossier cannot be inherited by this shared-UI candidate, and this file does not alter the KMP-native boundary.

This is documentary research only. No application code, prototype, executable spike, signed build, benchmark, store
submission or real-device pass is claimed.

Evidence labels used below:

- OFFICIAL EVIDENCE: claim supported by an official Kotlin, JetBrains Compose, Android or Apple primary source linked in
  this file;
- REASONED INFERENCE: a provider-neutral consequence of applying that evidence to the approved Kavriva fixture;
- DEPENDENCY-SPECIFIC: evidence about a named official or candidate package/library, without implying selection;
- UNRESOLVED: a product, dependency, owner, toolchain, capacity, cost or later acceptance fact not established;
- HELD: the candidate closure is incomplete, so no positive candidate result is asserted.

## 1. Candidate Identity

| Field | Record |
|---|---|
| Candidate family | KMP + Compose Multiplatform: shared Kotlin common/domain/data contracts and shared Compose UI/presentation, with Android and iOS native application hosts and explicit platform-specific source sets |
| Exact evaluated version/snapshot | Kotlin 2.4.20 and Kotlin Multiplatform Gradle plugin 2.4.20; Compose Multiplatform 1.12.0 release tag v1.12.0, published 2026-08-25, release commit shown as d67175a; Compose Compiler Gradle plugin 2.4.20; Android Jetpack Compose artifact mapping 1.12.0. These are comparison snapshots, not final Kavriva pins |
| Kotlin release evidence | Official Kotlin 2.4.20 release tag, published 2026-09-07, release commit shown as 890ac1d |
| Evidence retrieval date | 2026-09-17 |
| Product comparison floor | Frozen four-cohort fixture: constrained Android API 29 / 4 GB RAM / 64 GB storage / 2 GB free; main Android 13+ / 6 GB RAM / 128 GB storage; oldest supported-end iPhone capable of iOS 16.4; and a current standard non-Pro iPhone on the current generally available iOS. These are comparison profiles, not a final support promise |
| Compose Multiplatform framework floor | Compose Multiplatform 1.12.0 documentation lists Android 5.0/API 21 and iOS 14 as minimums and supports only 64-bit platforms. The Kavriva fixture is narrower and remains the comparison floor |
| Core KMP stability | Official Kotlin Multiplatform documentation identifies the core Android/iOS targets as stable; Compose Multiplatform is documented as stable for Android and iOS, but stability is not product, accessibility, lifecycle, safety or team acceptance |
| Toolchain compatibility snapshot | Official Kotlin 2.4.20 compatibility row: Gradle 7.6.3–9.7.0, Android Gradle Plugin 8.5.2–9.3.1 and Xcode 26.4. This is a compatibility range, not an exact project pin |
| Build-tool/store floor | UNRESOLVED: exact JDK/Java, Gradle, AGP, Android SDK, Xcode/macOS, Swift integration, Kotlin/Native targets, signing, store and CI matrix must be pinned together |
| Support/EOL statement | Official sources publish release and compatibility guidance, but a Kavriva support floor, Compose/KMP upgrade policy, library EOL response, OS window and emergency capacity are not set |
| Dossier author/reviewer | Research sub-agent /root/flutter_dossier; independent dossier review pending |

Every later reference to comparison devices, both-platform evidence or real-device acceptance means all four frozen
cohorts above. A two-device or oldest-only sample cannot close a scenario or accessibility gate.

### 1.1 Official primary sources

The external technical evidence used for this bounded draft is limited to official Kotlin, JetBrains, Android and Apple
sources:

- Compose Multiplatform compatibility and versions: https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html
- Compose Multiplatform 1.12.0 release: https://github.com/JetBrains/compose-multiplatform/releases/tag/v1.12.0
- Kotlin 2.4.20 release: https://github.com/JetBrains/kotlin/releases/tag/v2.4.20
- Kotlin Multiplatform compatibility guide: https://kotlinlang.org/docs/multiplatform/multiplatform-compatibility-guide.html
- Compose Multiplatform and Jetpack Compose relationship: https://kotlinlang.org/docs/multiplatform/compose-multiplatform-and-jetpack-compose.html
- Platform-specific Compose behavior and entry points: https://kotlinlang.org/docs/multiplatform/compose-platform-specifics.html
- Kotlin platform APIs and expect/actual boundaries: https://kotlinlang.org/docs/multiplatform/multiplatform-connect-to-apis.html
- KMP hierarchical source sets: https://kotlinlang.org/docs/multiplatform/multiplatform-hierarchy.html
- Compose accessibility: https://kotlinlang.org/docs/multiplatform/compose-accessibility.html
- Compose iOS accessibility: https://kotlinlang.org/docs/multiplatform/compose-ios-accessibility.html
- Compose lifecycle: https://kotlinlang.org/docs/multiplatform/compose-lifecycle.html
- Compose navigation/deep links: https://kotlinlang.org/docs/multiplatform/compose-navigation-deep-links.html
- Compose resources: https://kotlinlang.org/docs/multiplatform/compose-multiplatform-resources.html
- First Compose Multiplatform app and iOS/Xcode host: https://kotlinlang.org/docs/multiplatform/compose-multiplatform-create-first-app.html
- Android Keystore: https://developer.android.com/privacy-and-security/keystore
- Android persistent background work: https://developer.android.com/develop/background-work/background-tasks/persistent
- Android Photo Picker and documents/files: https://developer.android.com/training/data-storage/shared/photopicker and https://developer.android.com/training/data-storage/shared/documents-files
- Android notification permission: https://developer.android.com/develop/ui/views/notifications/notification-permission
- Android accessibility: https://developer.android.com/guide/topics/ui/accessibility/apps
- Android Auto Backup: https://developer.android.com/identity/data/autobackup
- Apple Keychain Services: https://developer.apple.com/documentation/security/keychain_services
- Apple background tasks and background URLSession: https://developer.apple.com/documentation/backgroundtasks and https://developer.apple.com/documentation/foundation/url_loading_system/downloading_files_in_the_background
- Apple PHPicker and document picker: https://developer.apple.com/documentation/photokit/phpickerviewcontroller and https://developer.apple.com/documentation/uikit/uidocumentpickerviewcontroller
- Apple UserNotifications and accessibility: https://developer.apple.com/documentation/usernotifications and https://developer.apple.com/documentation/accessibility

Kavriva product and comparison authority is separate from these external technical sources and is recorded in Section 2.

### 1.2 Snapshot interpretation and limits

OFFICIAL EVIDENCE: Compose Multiplatform releases are separate from Kotlin and Jetpack Compose releases. The official
compatibility page identifies Compose Multiplatform 1.12.0, maps it to Jetpack Compose 1.12.0 for Android, requires the
Compose Compiler Gradle plugin with the same version as the Kotlin Multiplatform plugin, and states that current release
compatibility is affected by Kotlin, Gradle, Android Gradle Plugin and Xcode.

OFFICIAL EVIDENCE: The Compose 1.12.0 release page shows the v1.12.0 tag, release date and signed release commit
d67175a. The Kotlin 2.4.20 release page shows the v2.4.20 tag, release date and signed release commit 890ac1d. The
full source/archive digest, Gradle wrapper, repository lock, native host revision and artifact attestation are not
captured here.

REASONED INFERENCE: The exact comparison snapshot is versioned enough for documentary comparison, but not reproducible
enough for a release. The eventual ADR must re-check and bind Kotlin/compiler, KMP plugin, Compose plugin/compiler,
Gradle, AGP, JDK, Android SDK, Xcode/macOS, Swift integration, dependency graph, target architectures, artifact digest
and store requirements as one authorized snapshot. Dynamic latest claims are not sufficient.

OFFICIAL EVIDENCE: Compose 1.12.0 documents iOS accessibility improvements including live-region semantics and VoiceOver
text attributes; the separate accessibility guide documents semantics mapping to native iOS accessibility objects and
XCTest audit access. REASONED INFERENCE: these are framework capabilities, not a Kavriva Turkish critical-flow pass.

The snapshot does not prove:

- the correctness of Kavriva's offline package, recall, migration, conflict, physical-state or safety state machine;
- native permission, camera, file, share, notification, deep-link, background, backup, key or signing behavior;
- VoiceOver/TalkBack behavior on active, warning, stop, unknown, held and recovery states;
- performance or memory behavior on the 4 GB/2 GB-free comparison device;
- availability of accountable Compose/KMP, Android, iOS, security, release, accessibility or safety owners;
- lower 12–24 month cost, free-tier suitability or provider-independent exit;
- approval for any OTA/runtime code delivery mechanism.

## 2. Fixed Inputs and Comparison Discipline

This record applies without KMP + Compose-specific relaxation:

- 04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md, approved under DEC-0031;
- the equal S1–S15 definitions and pass/hold/reject rules in DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md;
- DEC-0023 through DEC-0031, including data-efficient task-scoped offline delivery, conservative recovery,
  AI-operated delivery, limited-budget costing and no approved OTA;
- approved DEBATE-001 through DEBATE-005 directions: separate client authority, bounded offline eligibility, immutable
  publication meaning, scoped authorization/audit, federated release integrity and the closed cross-domain release graph;
- approved Phase-2/Phase-3 product, design and accessibility truth: fit-before-application, evidence/provenance,
  uncertainty, non-destructive history, current physical-state revalidation, safe-stop/recovery, Turkish-first critical
  flows, private/community/official separation and no silent overwrite/loss.

Any required fixture change stops this dossier and must be applied once to all five candidates. This file does not alter
the common fixture.

### 2.1 Frozen comparison fixture carried into this candidate

The following are comparison inputs, not final commercial, support, retention or SLA commitments:

- one selected motorcycle/variant and one active maintenance task;
- required compact guidance and complete safe-stop/recovery closure up to 12 MB transfer;
- optional high-resolution media/video up to 150 MB, never silently selected;
- unrelated 2 GB catalog used to prove that the candidate does not download it by default;
- default offline-content cache budget 250 MB, excluding user-created history/photos;
- cellular confirmation above 25 MB;
- local fixture of 3/10 motorcycles, 250/2,000 history/evidence records, 50/500 photos at 3 MB average,
  100/1,000 private notes, 20/200 pending changes and 3/30 deliberate local/profile conflicts;
- one duplicate operation, one partial upload, one corrupt package, one interrupted database change, one source
  correction, one content withdrawal and one safety recall;
- constrained network, connection loss, 72-hour offline, process termination, device-clock change and backup-restore
  profiles;
- phone-focused four-cohort comparison: constrained Android API 29, main Android 13+, oldest supported-end iPhone
  capable of iOS 16.4 and a current standard non-Pro iPhone on current generally available iOS;
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

Shared Compose UI cannot become authority. The shared KMP core and composables may represent the consumer contract and
local state, but server-authoritative eligibility, publication, recall, current release and authorization remain outside
the framework. The mobile client receives only the eligible versioned content permitted by the consumer contract.

The local package must be the smallest safe closure for the selected motorcycle/task. It must retain mandatory text,
warnings, checks and safe-stop/recovery while keeping heavy media optional. A restored, cloned, stale, mixed or partially
verified package cannot create positive safety or entitlement authority.

The KMP + Compose boundary must preserve these distinctions:

    Compose shared UI/presentation  ≠  Android native host/exceptions  ≠  iOS native host/exceptions
    KMP common domain/data contract ≠ Internal Operations authority
    local cache/history context    ≠  current server eligibility
    artifact authenticity          ≠  approval/provenance ≠ current revocation state

Shared composables may share product vocabulary, state contracts, theme and accessibility intent, but they must not
silently share operator credentials, private data scope or server mutation authority with Internal Operations.

### 2.3 Evidence status for this bounded draft

All capability outcomes remain HELD. Official documentation establishes that Kotlin Multiplatform and Compose
Multiplatform mechanisms exist and identifies their compatibility relationships; it does not establish a complete
Kavriva implementation, dependency lock, owner/capacity plan, real-device result or release-ready closure. The S1–S15
records and later sections below remain documentary and held.

## 3. Candidate Architecture Boundary (Documentary, No Implementation)

### 3.1 Boundary statement

The candidate is a shared Kotlin Multiplatform core and shared Compose Multiplatform presentation surface with two
separately signed mobile hosts:

    Consumer contract / server authority
                    |
        +-----------+-----------+
        |                       |
    Android host            iOS host
    Activity + Compose      @main + ComposeUIViewController
        |                       |
        +-----------+-----------+
                    |
       KMP common domain/data contracts
       commonMain plus platform source sets

OFFICIAL EVIDENCE: Compose Multiplatform platform guidance describes a dedicated entry point for each target, including
an Android Activity and an iOS main class/structure, and documents native interop for platform-specific APIs. This is a
logical boundary only; no repository/module layout or implementation is selected.

This is not KMP-native. In KMP-native, Android and iOS presentation code stays native and only Kotlin logic/data is
shared. In this candidate, Compose UI, presentation state, navigation patterns and semantic intent are shared where the
framework supports both mobile targets, while each host retains explicit native exceptions and ownership.

### 3.2 Shared Compose UI and presentation ownership

REASONED INFERENCE: shared commonMain Compose code may own the portable presentation contract:

- visual/state vocabulary, theme tokens, Turkish copy keys, units and content-generation labels;
- readiness, active instruction, warning, safe-stop, unknown, partial, held, recovery and conflict presentation;
- composable screens, reusable controls, focus/action intent, state announcements and navigation state;
- selected-task/offline-package status and user-visible size/consent/progress messages;
- non-authoritative local history/evidence views and explicit scope/provenance labels;
- shared test identifiers and semantic state identifiers where platform mapping remains valid.

OFFICIAL EVIDENCE: Compose Multiplatform extends Compose APIs to common Kotlin code and uses Android Jetpack Compose
artifacts for Android while JetBrains multiplatform artifacts serve other targets. The platform-specific behavior guide
states that common UI elements may not be covered, native pop-ups differ, text is not pixel-perfect across platforms and
native interop is required for platform-specific views.

REASONED INFERENCE: a shared composable is not a native UI pass. Android and iOS must each verify layout, text scale,
focus, semantics, input, back behavior, interruption and native surface return. The shared UI cannot weaken the safety
state machine or reclassify server state.

The shared Compose surface must not own:

- Android/iOS permission prompt wording or system authorization;
- camera, photo picker, document picker, share sheet or notification system surfaces;
- Android Keystore or iOS Keychain authority;
- current entitlement, recall, publication, release or Internal Operations credentials;
- OS scheduling, background execution, process survival or store signing;
- raw native handles, security-scoped resources or platform-only lifecycle assumptions.

### 3.3 Shared domain and data ownership

REASONED INFERENCE: the KMP common core should own portable deterministic rules with one meaning on both platforms:

- motorcycle/variant applicability and fit-result semantics;
- content/release/client-capability envelope parsing;
- risk, readiness, freshness, stale, recall and safe-stop state meanings;
- current physical-state revalidation after interruption;
- task-scoped package manifest and integrity/closure rules;
- local record/history/provenance/correction/withdrawal relationships;
- pending operation identity, idempotency and explicit partial/unknown/conflict outcomes;
- local-to-profile migration intent and conflict categories;
- Turkish copy keys, unit semantics and accessibility-state contract identifiers;
- portable consumer API/data contracts and release-compatibility declarations.

These rules remain Kavriva-owned. Kotlin, Compose, Android services and iOS services do not become truth authorities
merely because common code calls them. Domain/data code must not directly depend on composable lifecycle, Activity/
ViewController instances, notification presentation, camera surfaces or store identities.

OFFICIAL EVIDENCE: Kotlin documentation describes common and platform-specific source sets, expect/actual declarations
and interfaces for platform APIs. The compiler enforces corresponding actual declarations for targeted platforms, and
hierarchical source sets expose only APIs available for all targets in that source set.

### 3.4 Android host and native exception boundary

The Android host owns:

- the application Activity and Android lifecycle/process integration around the shared Compose content;
- Android back behavior, configuration changes, memory/storage pressure and UI/threading policy;
- TalkBack, Switch/Voice Access, Android focus/order and native accessibility services;
- runtime permissions, notification channels/permission, Android intents/app links and system dialogs;
- camera, CameraX/Camera2 choice, Photo Picker/Storage Access Framework and URI/path lifetimes;
- Android Keystore, backup/data-extraction configuration, device binding and restore reconciliation;
- Android WorkManager/background constraints, foreground transfer fallback and low-storage behavior;
- Android build, Gradle/AGP/JDK/SDK, signing, Play submission and installed-client rollout artifact.

The shared Compose UI may be rendered inside this host, but it cannot turn stale, recalled, unknown, held, safe-stop,
teaching-only or not-applicable state into a physically eligible action. Android-native UI availability is not evidence
that the shared data or safety behavior is correct.

### 3.5 iOS host and native exception boundary

The iOS host owns:

- the Swift/Objective-C application entry point and ComposeUIViewController integration;
- iOS scene/application lifecycle, process/background behavior and resource interruption;
- VoiceOver, Switch Control, focus/order, Dynamic Type and iOS accessibility services;
- permission sheets, camera, PHPicker, UIDocumentPicker, security-scoped resource and share-sheet behavior;
- iOS Keychain, device binding, backup/restore and key-loss treatment;
- UserNotifications, universal links, URL validation and foreground reconciliation;
- URLSession/background-transfer or BGTaskScheduler integration and cancellation/expiration;
- Xcode/macOS/Swift/Kotlin/Native framework integration, signing, App Store submission and rollout artifact.

OFFICIAL EVIDENCE: the Compose iOS documentation describes a generated/native iOS host and mapping of Compose semantics
to native iOS accessibility objects; the KMP quickstart states that a macOS host and Xcode are needed to build iOS.

REASONED INFERENCE: the shared Compose renderer reduces presentation duplication, but native iOS resource ownership,
scene/process behavior, permission UI, signing and acceptance remain iOS-specific. A functioning
ComposeUIViewController is not a VoiceOver, lifecycle, backup or store pass.

### 3.6 Local persistence, encryption, migration and backup boundary

The logical local data boundary separates at least:

- scoped offline content packages and their release/client eligibility context;
- account-light motorcycle/history records;
- private notes and user photos;
- pending operations and durable checkpoints;
- conflict/partial/unknown records;
- provenance, correction and withdrawal history;
- trust/eligibility metadata and release/revocation observations;
- protected fields, device binding and key references.

UNRESOLVED: no local database, ORM, serialization library, schema format, encryption wrapper, key derivation policy or
backup include/exclude policy is selected. Compose Multiplatform or a KMP library does not automatically provide atomic
writes, crash recovery, conflict resolution, recall ordering, encryption, retention or safe migration.

REASONED INFERENCE: Android Keystore and iOS Keychain remain platform-owned protected-key boundaries. Raw keys must not be
exported in user files or ordinary backup data. Restored or cloned local state remains untrusted until account/device
binding, key state, current release, suspension/revocation generation and content integrity reconcile.

Migration must preserve valid new data and history. A binary rollback cannot be used as a data rollback when schema/data
compatibility is unknown. Failed or interrupted migration remains explicit and recoverable/quarantined rather than being
reported as completed.

### 3.7 Sync, reconciliation and scoped offline package boundary

REASONED INFERENCE: the shared KMP core may coordinate local state, package verification and pending-operation
reconciliation, while shared Compose displays state and user choices. It cannot make offline state authoritative.
Foreground reconciliation after connectivity returns is decisive for current eligibility, recall, release generations and
server mutations.

The package lifecycle must conceptually be:

    requested scope → staged transfer → integrity/manifest verification
                     → complete package promotion → bounded offline use
                     → foreground reconciliation → current/held/recalled result

The shared core must represent cancellation, interruption, duplicate request, corruption, low storage, partial transfer,
stale release, incompatible client, recall and unknown reconciliation outcomes. Android/iOS background scheduling may
optimize transfer, but correctness cannot depend on a scheduled task running at a particular time.

No full catalog, unrelated motorcycle or unused heavy media download is permitted by the fixed input. Shared Compose
must not hide an over-download behind a platform cache or resource mechanism.

### 3.8 Camera, file/media, notification, deep-link and background boundaries

The shared core and Compose UI may own portable intent/state contracts such as capture requested, file selected,
transfer partial, notification advisory, deep link pending and reconciliation required. Native hosts own actual
platform surfaces, permissions, resource lifetimes, cancellation and failure behavior.

External files, URLs and derived media remain untrusted until the approved ingestion and provenance process establishes
the required status. Opening a native viewer, picker or share destination does not establish technical correctness,
official status or publication authority.

Notifications and push are advisory. A notification cannot be the sole recall authority, and a missing notification
cannot silently preserve physical application eligibility. Deep links cannot bypass fit, readiness, authorization,
release or recall checks.

### 3.9 Accessibility and state-semantics boundary

The shared Compose layer owns stable semantic state identifiers and required meaning; Android and iOS hosts own the
accessible expression and native surfaces. Compose documentation describes semantic properties, traversal order,
screen-reader support and iOS mapping to native accessibility services. The iOS documentation also records that
Material3 ColorScheme does not currently provide out-of-the-box high-contrast colors.

Both platforms must later prove, on actual devices and with assistive technologies, the critical Turkish flows:

- readiness and required checks;
- warning and stop states;
- stale/recall/unknown/held outcomes;
- safe-stop/recovery and active physical work;
- evidence/provenance and uncertainty;
- largest text/reflow, focus/order, non-color status, contrast and reduced motion;
- native permission, picker, notification, share and link surfaces.

KMP/Compose version stability or semantic API availability does not count as a real-device VoiceOver/TalkBack pass.
No accessibility result is claimed in this partial dossier.

### 3.10 Store, build, signing and release boundary

KMP common code and Compose shared UI are inputs to two separately signed consumer application artifacts. Android uses
the Jetpack Compose artifacts mapped by Compose Multiplatform; iOS consumes the generated shared framework through its
native host. They are not one interchangeable binary.

The release graph must bind, at minimum:

- exact KMP/shared and Android/iOS host source revisions;
- Kotlin/compiler/KMP/Compose plugin, Gradle, AGP, JDK, Android SDK, Xcode, Swift and macOS closure;
- direct/transitive dependency resolution and native implementation inputs;
- shared UI capability, Android/iOS host exception and accessibility declarations;
- client capability, API/schema, content/derived assets, configuration, migration and offline recovery closure;
- provenance/SBOM/verification/signing evidence and suspension/revocation generations.

No KMP/Compose framework feature, shared UI path or future runtime delivery mechanism can approve technical content,
change current eligibility, bypass Internal Operations publication or create an OTA authority. No OTA path is evaluated
here.

### 3.11 Internal Operations/API/content contract boundary

Internal Data & Content Operations remains a separate browser-based trust boundary. The mobile apps consume the approved
consumer contract; they do not share operator credentials, role state, publication authority or private editorial data.

The shared KMP module may contain generated/portable consumer contract types only if contract governance permits that
shape. Compose UI may display status but must not directly mutate editorial truth, current-release pointers, roles,
publication status or audit evidence. Server policy remains authoritative for authorization, publication, recall and
current eligibility.

### 3.12 Portable data and framework-exit boundary

Portable assets should include, independently of KMP + Compose:

- canonical product/content/data schemas and migration descriptions;
- history, provenance, correction, withdrawal and conflict events;
- offline-package fixtures and compatibility envelopes;
- user export and media lineage;
- Turkish copy, units, design tokens and accessibility intent;
- S1–S15 scenario fixtures and acceptance oracles;
- release/rollback/revocation evidence and audit references.

Shared Compose source, Kotlin/Native binaries, generated iOS frameworks, Gradle/Xcode integration, Android host
artifacts and signed platform binaries remain implementation-bound. The exact portable format, framework replacement
migration, key continuity and two-platform parity strategy are UNRESOLVED and intentionally deferred to later sections.

## 4. Native and Dependency Closure

### 4.1 Closure rule

The rows below are a capability closure inventory, not an approved dependency list. No third-party library, provider,
hosted build service, CI runner, database, serialization format, identity service or OTA mechanism is selected. The
Kotlin 2.4.20 plus Compose Multiplatform 1.12.0 row and official native platform APIs are evidence snapshots only.

Every critical capability must eventually reach PASS, HELD or REJECT with an exact source/version, primary and backup
owner, native skill, lifecycle constraint, fallback, EOL/security response and later acceptance evidence. An unnamed
dependency, native exception, build input or owner is HELD.

### 4.2 Native/dependency closure matrix

| Capability | Built-in/framework path | Dependency/plugin | Native code/skill required | Lifecycle/threading constraints | Accessibility impact | Fallback/replacement | EOL/security owner | Status |
|---|---|---|---|---|---|---|---|---|
| Shared Compose UI, presentation and semantics | Compose Multiplatform 1.12.0 common UI; Android maps to Jetpack Compose 1.12.0; semantics/traversal APIs documented | Compose plugin is official snapshot only; no add-on UI library selected | Shared Compose/Kotlin owner plus Android and iOS UI reviewers | Each host has a dedicated entry point; native interop, platform input and lifecycle remain host-owned | Shared semantics must map correctly to TalkBack/VoiceOver; iOS high-contrast Material3 gap is explicit | Native screen/host exception behind the same state contract; hold if semantics cannot be expressed | JetBrains/Google release and security evidence; product owner and dependency lock unresolved | HELD |
| Kotlin/KMP/Compose compiler snapshot | Kotlin 2.4.20, KMP Gradle plugin 2.4.20, Compose Multiplatform plugin 1.12.0, Compose compiler plugin 2.4.20 | No additional compiler plugin selected | Kotlin/Gradle/Native release owner and independent verifier | Compose compiler plugin must match Kotlin/KMP plugin; KMP compatibility matrix binds Gradle/AGP/Xcode | Compiler changes can alter generated semantics/interfaces; revalidation required | Previous pinned snapshot and controlled migration event | Toolchain provenance, lock, SBOM, CVE/EOL and rollback owner unresolved | HELD |
| Android host and shared Compose integration | Android Activity host plus official Jetpack Compose artifact mapping | No Android UI add-on selected | Android Kotlin/native UI owner, Android lifecycle and accessibility skill | Activity/process/configuration changes, UI thread, memory/storage pressure require explicit policy | TalkBack, Switch/Voice Access, focus/order and native dialogs require device evidence | Android native screen/adapter behind portable state; hold incompatible shared UI | Android SDK/AGP/Gradle/JDK/store support and dependency closure unresolved | HELD |
| iOS host and shared Compose integration | iOS application entry point plus ComposeUIViewController/shared framework | No Swift UI/add-on selected | Swift/iOS, UIKit/SwiftUI interop, Kotlin/Native and Xcode skill | Scene/process/background behavior, framework generation/cache and Swift/Kotlin boundary require explicit policy | VoiceOver/Switch Control, Dynamic Type and native surfaces require device evidence | Native iOS screen/adapter behind portable state; hold if Compose surface fails | iOS/Xcode/Swift/store support and framework artifact provenance unresolved | HELD |
| Platform-specific APIs and source sets | KMP common/platform source sets and expect/actual or interfaces are official mechanisms | No DI or platform abstraction package selected | Android and iOS native implementers for every actual/host exception | Source-set API availability, target architecture and dispatcher/actor boundaries must be explicit | Platform implementations must preserve shared semantic state and labels | Owned adapters or native host implementation; no future unnamed plugin | Shared-core and native owners, provenance and EOL response unresolved | HELD |
| Shared domain/state machine | KMP commonMain portable Kotlin contracts; Compose observes state but is not authority | No domain/state library selected | Kotlin domain/data owner with Android/iOS boundary review | No direct UI/Activity/ViewController/scheduler dependency; idempotency and error model unresolved | Native UIs must express active, warning, stop, unknown, held and recovery states | Portable contracts and platform-specific renderers | Shared-core owner, schema/provenance and security review unresolved | HELD |
| Serialization and consumer contract | KMP common code may hold versioned contract types | No serialization/wire library selected; no unnamed future dependency accepted | API/schema compatibility owner, Kotlin/Swift interop review | Unknown safety fields fail closed; old/new clients need explicit capability graph | Stable state codes and copy keys must not be inferred from visual text | Versioned portable contract and server compatibility hold | Library/license/security owner and migration authority unresolved | HELD |
| Local database/history/event log | No built-in Compose/KMP database claim | No database/ORM selected | Data/migration owner with Android/iOS storage skill | Durable checkpoints, atomicity, crash recovery, concurrency and forward migration unresolved | Partial/conflict/unknown states require accessible explanation | Portable schema plus forward/corrective migration; quarantine if unsafe | DB/library owner, EOL/security and restore evidence unresolved | HELD |
| Protected fields, key references and device binding | Android Keystore and Apple Keychain are native protected-key boundaries | No crypto/key wrapper selected | Android security and Swift/iOS security owner; independent security reviewer | Key loss, rotation, restore/clone and device binding are explicit failures; raw keys never export | Re-auth/quarantine/key-loss states must be readable/announced in shared UI and native surfaces | Re-authentication and quarantine; no plaintext/copy-key fallback | Key lifecycle, incident/revocation and backup owner unresolved | HELD |
| Scoped package download/resume/cleanup | Shared state machine plus native Android/iOS transfer APIs | No downloader/cache package selected | Shared transfer owner, Android background-work and iOS URLSession/BGTask owner | Process death, cancellation, low storage, expiration and partial transfer cannot lose mandatory closure; background not correctness | Progress, paused/failed/unknown/retry states must be announced | Foreground resumable transfer; hold if complete closure cannot verify | Transfer/package owner, integrity verifier and dependency response unresolved | HELD |
| Android camera/media/file input | Native Android camera, Photo Picker and documents/files APIs are available | No CameraX/camera/file package selected | Android camera, permission, Photo Picker/SAF and URI/storage skill | Permission denial, URI lifetime, process death, temporary files and low storage require explicit handling | Native picker/camera/denial/error states require TalkBack evidence | Manual evidence entry or owned adapter; quarantine untrusted input | Native adapter, scanner/parser and security owner unresolved | HELD |
| iOS camera/media/file input | Native iOS camera, PHPicker and UIDocumentPicker APIs are available | No Swift media package selected | Swift/iOS Photos, document, camera and security-scoped resource skill | Permission changes, process loss, temporary-file cleanup and resource release require explicit handling | Native picker/camera/denial/error states require VoiceOver evidence | Manual evidence entry or owned adapter; quarantine untrusted input | Native adapter, scanner/parser and security owner unresolved | HELD |
| Android/iOS export and share | Native Android Sharesheet and iOS share sheet are platform surfaces | No sharing/export package selected | Android/iOS share and disclosure-review skill | Destination is untrusted and operation interruptible; exported copy cannot be remotely retracted | Scope, recipient, privacy and cancellation need accessible confirmation | App-owned export plus user-controlled native share | Export/disclosure owner and audit linkage unresolved | HELD |
| Notifications/advisory recall notice | Android notification API/permission and Apple UserNotifications are native surfaces | Push provider and notification package not selected | Android notification-channel and iOS notification-category skill | User disablement, authorization, process state and delivery delay are expected; notification not authority | Turkish text/action and stop/recovery meaning need AT evidence | Foreground reconciliation and in-app state; no notification-dependent safety | Notification owner, privacy, provider and incident response unresolved | HELD |
| Navigation/deep links | Compose navigation patterns plus Android intents/app links and iOS universal links | No routing/deep-link package selected; official multiplatform Navigation is research evidence only | Android intent and Swift/iOS link-validation skill | Cold start, replay, duplicate link and untrusted URL require idempotent validation | Link arrival/error/hold must be announced; no readiness/auth bypass | Safe in-app destination or manual navigation | Domain association/configuration owner and security evidence unresolved | HELD |
| Lifecycle/checkpoint | Compose Multiplatform lifecycle guidance can expose common lifecycle state; host lifecycle remains native | Optional lifecycle-runtime-compose version shown in official docs, not selected | Android Activity and iOS scene/process/lifecycle skill | Lifecycle signals may be skipped; only last durable checkpoint restores; no uncommitted physical state replay | Resume/revalidation/safe-stop must be shared and native-accessible | Safe-stop/recovery screen and explicit revalidation | Lifecycle owner, atomic-write evidence and native kill tests unresolved | HELD |
| Background execution/reconciliation trigger | Android persistent background work and Apple background-task/URLSession APIs are platform services | No scheduler/work package selected | Android WorkManager and iOS background-transfer skill | Scheduling is opportunistic; correctness uses durable state and foreground reconcile | Deferred/paused/expired work needs accessible explanation | Foreground retry/reconcile; no exact-time guarantee | OS policy owner and change-response capacity unresolved | HELD |
| Backup/restore/clone behavior | Android and Apple backup systems are platform policies; exact inclusion/exclusion is not selected | No backup package selected | Android backup and iOS backup/Keychain expertise | Restored/cloned positive state untrusted until account/device/key/release/revocation reconciliation | Quarantine, re-auth and partial restore visible in shared UI/native AT | Re-download scoped content; preserve portable records; quarantine mismatch | Backup/key/restore owner and game-day evidence unresolved | HELD |
| Accessibility semantics and native critical flows | Compose semantics/traversal support, iOS native semantics mapping and platform accessibility APIs documented | No accessibility package selected | Independent TalkBack/Voice Access and VoiceOver/Switch Control reviewers | Largest text, reduced motion, focus, process interruption and permission surfaces require physical-device review | Critical gate; API availability is not a pass; high contrast requires explicit design | Hold release until real-device evidence; native UI replacement | Accessibility owner and qualified testers unresolved | HELD |
| Test and validation boundary | Compose UI test/semantics and native Android/iOS test frameworks are possible | No test/telemetry package selected | Android/iOS real-device, migration, accessibility and safety reviewers | Deterministic state fixtures, process kill, schema migration and native dialogs require separate evidence | AT evidence cannot be replaced by simulator or AI claim | Hold release; record missing evidence and owner | Independent validation owner/capacity unresolved | HELD |
| Shared resources/localization | Compose Multiplatform resources plugin supports common resources and language/theme inputs | Official resources library is a versioned snapshot only; no final resource package selected | Android/iOS resource, font, Dynamic Type and locale skill | Resource packaging, font fallback and platform locale behavior require release checks | Turkish labels, warnings and announcements must survive reflow/AT | Portable copy keys and native resource fallback; hold missing critical copy | Resource owner, license/font provenance and EOL unresolved | HELD |
| Android/iOS build, signing and store artifacts | Gradle shared module plus Android host and Xcode iOS host produce separate artifacts | No CI, registry or signing provider selected | Android/Gradle and Xcode/Swift build/signing owners; store authority | Exact source/dependency/toolchain/artifact digest and DEBATE-005 graph must bind | Store/build errors are operational evidence, not product safety status | Reproducible/provider-independent artifact path; hold custody gap | Release/security owner, key custody and incident response unresolved | HELD |
| Provenance/SBOM/trust-root closure | DEBATE-005 requires artifact-bound provenance/SBOM and independent verification | No SBOM/attestation tool or format selected | Release-security owner and independent verifier | Shared/core/native/dependency/toolchain/base-image inputs bind to each artifact | Evidence/hold/revocation remains user-visible where relevant | Quarantine/rebuild from known inputs | Trust-root, verifier and evidence-custody owners unresolved | HELD |

### 4.3 Toolchain and dependency closure observations

OFFICIAL EVIDENCE: the Compose compatibility guide states that Compose Multiplatform is affected by the Kotlin
Multiplatform Gradle plugin, Gradle, Android Gradle Plugin and Xcode matrix. For Kotlin 2.4.20 it records Gradle
7.6.3–9.7.0, AGP 8.5.2–9.3.1 and Xcode 26.4. These are supported ranges, not permission to mix arbitrary latest tools.

OFFICIAL EVIDENCE: Compose Multiplatform 1.12.0 requires the Compose Compiler Gradle plugin with the same version as
the Kotlin Multiplatform plugin; the Android target consumes Jetpack Compose artifact version 1.12.0 according to the
official mapping. The Kotlin/Native and generated iOS framework path adds a separate native build/release boundary.

The future build plan must record:

- exact Kotlin compiler, KMP Gradle plugin, Compose plugin/compiler and release source identity;
- exact Gradle, AGP, JDK, Android SDK, Xcode, macOS, Swift integration and host project identity;
- Android/iOS target architectures, simulator/device coverage and iOS framework integration mode;
- Compose common/platform source-set hierarchy and every platform-specific actual/host exception;
- direct/transitive dependency lock, repository provenance, license/SBOM and vulnerability response;
- native API/permission/background/backup declarations and resource/localization inputs;
- primary/backup owner, EOL/security response and replacement path for each critical capability;
- migration and rollback evidence for each toolchain, Compose, Kotlin or native dependency upgrade.

UNRESOLVED: the repository has no KMP + Compose project, lockfile, dependency graph, generated iOS framework, CI
pipeline, signing configuration or named native owner. Every row remains HELD until those facts are supplied through
later authorized work. This bounded dossier intentionally does not select a database, media/transfer library, test
framework, DI/navigation provider, CI system, store service, KMP-native UI path or OTA channel.

## 5. Equal S1-S15 Scenario Record

The records below use the controlled template fields. A mechanism is an evidence-shaped design hypothesis, not an
implementation claim. All results are HELD: no KMP + Compose code, dependency lock, signed artifact, physical-device
run, independent accessibility oracle, safety review or accountable delivery capacity exists in this Phase-4 dossier.

### S1 — First value without an account

- Authoritative starting state: No account, server authority or prior local profile; the user selects one motorcycle/variant and can view the approved local starting surface.
- Allowed transition: Persist the selection durably, show account-registration/skip choice, and later offer an explicit migration preview; never silently merge or overwrite local history.
- Candidate mechanism: Shared Kotlin state/repository contract and shared Compose presentation, with platform storage adapters and a portable profile/event schema.
- Official evidence: KMP common/platform source sets and interfaces are documented at https://kotlinlang.org/docs/multiplatform/multiplatform-connect-to-apis.html; Compose common UI and native entry points are documented at https://kotlinlang.org/docs/multiplatform/compose-platform-specifics.html.
- Reasoned inference: Shared Kotlin/Compose can present local-first value consistently, but account bind, transaction, migration and conflict authority remain Kavriva-owned.
- Dependency-specific evidence: No database, auth, migration or local-storage library is selected; Compose resources/lifecycle documentation does not provide those semantics.
- Unresolved facts: Anonymous identity policy, schema, account bind/idempotency rules, backup handling, deletion and exact local database/key implementation.
- User-visible result: Useful selected-task value without an account, with Turkish copy stating what is local, what will migrate and what is not authoritative.
- Failure/hold behavior: If local write or migration preview cannot be proven durable, hold the transition and retain the last durable state; never claim successful migration.
- Recovery path: Reopen the last durable checkpoint, revalidate against current authority after sign-in and quarantine ambiguous records for review.
- Shared-system obligation: Product copy, authorization, history/provenance, deletion and account semantics are shared across candidates.
- Candidate-attributable work: Common Kotlin repository/state contract, Compose state rendering, Android/iOS storage adapters and semantics/release tests.
- Accountable AI/external owner: AI data/UI implementer; product/account owner and independent data reviewer for migration authority.
- Required later real-device evidence: Fresh install, no-account use, force-close/restart, sign-in migration, duplicate submit, storage pressure and restore/clone on both comparison devices.
- Residual risk: Shared composables can conceal a non-portable local schema or an unsafe account merge.
- Result: HELD.

### S2 — Compact offline teaching package

- Authoritative starting state: Online authority selected one motorcycle/task closure; required compact package is at most 12 MB, optional media at most 150 MB and unrelated 2 GB content is not requested.
- Allowed transition: Show measured size, obtain cellular confirmation above 25 MB, stage manifest/digest, download resumably, verify, atomically promote and expose only a complete valid package.
- Candidate mechanism: Common Kotlin transfer state machine and Compose progress/hold states, with native Android WorkManager and iOS URLSession/background-task adapters as candidates plus foreground retry.
- Official evidence: Android persistent background work is documented at https://developer.android.com/develop/background-work/background-tasks/persistent; Apple background strategy is system-controlled at https://developer.apple.com/documentation/backgroundtasks.
- Reasoned inference: Compose can share the state presentation, but transfer correctness cannot depend on timely scheduling; atomic promotion and resume must be implemented per host.
- Dependency-specific evidence: No downloader/cache package is selected; exact native adapter and transfer implementation are unresolved.
- Unresolved facts: Package schema, digest, storage reservation, retry/timeout, OS quotas, background entitlements, provider, cancellation and adapter lock.
- User-visible result: Compact safety/recovery material is available offline; optional media is clearly optional and progress/paused/failed states are Turkish and accessible.
- Failure/hold behavior: Partial, corrupt, expired or insufficient-space packages are never actionable; affected task is held with recoverable retry.
- Recovery path: Resume/restart in foreground, clean only verified temporary artifacts, recheck generation and promote once; never fall back silently to the 2 GB catalog.
- Shared-system obligation: Scoped delivery, safety closure, content generations, storage limits and no-OTA policy are candidate-neutral.
- Candidate-attributable work: Common Kotlin transfer orchestration, Compose progress semantics, native adapters and platform permission/storage handling.
- Accountable AI/external owner: AI transfer implementer; Android background and iOS URLSession specialists plus content/release authority.
- Required later real-device evidence: All network profiles, low storage, process kill, lock/call, Doze, iOS expiration, resume, duplicate/corrupt package and 12/150 MB boundaries.
- Residual risk: A shared progress screen may look complete while one platform has not atomically committed the safety closure.
- Result: HELD.

### S3 — Interrupted physical work

- Authoritative starting state: Active task has a last durable committed checkpoint; device locks, receives a call, loses process state or restarts.
- Allowed transition: Restore only the last durable checkpoint, mark in-flight physical state unknown/partial, stop safely and require explicit revalidation before continuation.
- Candidate mechanism: Common Kotlin journal/transaction contract and Compose recovery state, with Android Activity and iOS scene/process lifecycle adapters.
- Official evidence: Compose Multiplatform lifecycle maps native events to common lifecycle states at https://kotlinlang.org/docs/multiplatform/compose-lifecycle.html; iOS/Android host entry points remain platform-specific.
- Reasoned inference: Common lifecycle state helps presentation but cannot recover an uncommitted physical action or prove a kill signal was delivered.
- Dependency-specific evidence: Optional lifecycle-runtime-compose shown in official documentation is not selected; no journal/recovery library is selected.
- Unresolved facts: Journal schema, atomic commit boundary, physical/task semantics, recovery copy, native lifecycle behavior and kill/restore oracle.
- User-visible result: Turkish safe-stop, unknown/partial and revalidation states are explicit; restored screen never implies safe continuation.
- Failure/hold behavior: Missing/inconsistent checkpoint holds the task; no silent replay, duplicate completion or inferred physical state.
- Recovery path: Reopen last committed state, inspect current physical condition, reconcile authority when available and record explicit recovery outcome.
- Shared-system obligation: Conservative recovery, no silent overwrite/loss, audit and safety authority apply equally.
- Candidate-attributable work: Common checkpoint model, Compose recovery UX, Android/iOS lifecycle bridges and native process tests.
- Accountable AI/external owner: AI recovery implementer; qualified safety owner and Android/iOS lifecycle reviewers.
- Required later real-device evidence: Background/lock/call/process kill/restart, low memory, interrupted database write, Compose host recreation and clock-change tests.
- Residual risk: Common lifecycle abstractions can obscure different process and scene termination paths.
- Result: HELD.

### S4 — Offline recall or dormant guidance

- Authoritative starting state: Valid compact guide is downloaded and the user is offline; no new server recall or correction is observable.
- Allowed transition: Teach from last valid content generation, expose age/scope, and block/downgrade actions whose current validity cannot be established; reconnect and reconcile first.
- Candidate mechanism: Common Kotlin manifest/validity/revocation generation and Compose stale/hold state; native background and foreground triggers are advisory.
- Official evidence: Compose lifecycle/background behavior is documented at https://kotlinlang.org/docs/multiplatform/compose-lifecycle.html; Android Doze defers work at https://developer.android.com/training/monitoring-device-state/doze-standby.
- Reasoned inference: Offline Compose presentation can preserve previously approved teaching, but neither framework can manufacture current recall or safety authority.
- Dependency-specific evidence: No recall/push provider is selected; Compose navigation/notification integration is not current authority.
- Unresolved facts: Recall TTL/priority, offline validity window, clock manipulation, correction/withdrawal semantics, notification provider and generation API.
- User-visible result: Stale/dormant status, scope and safe-stop/recovery guidance are readable/spoken in Turkish; no current-authority claim offline.
- Failure/hold behavior: Withdrawn, expired, incompatible or unknown generation holds affected action while retaining verified safe-stop material.
- Recovery path: Reconnect/re-authenticate, fetch current generation, reconcile history and preserve old record as provenance rather than overwrite.
- Shared-system obligation: Safety truth, recall, publication/revocation and notification policy are framework-neutral.
- Candidate-attributable work: Common generation state, Compose banners/announcements and native notification/deep-link adapters.
- Accountable AI/external owner: AI content-state implementer; qualified safety/content publisher and authorization owner.
- Required later real-device evidence: Offline 72 hours, clock change, force-close, background restriction, notification denial, cold deep link and correction/withdrawal.
- Residual risk: A polished shared screen may cause over-trust if stale/authority boundaries are not unmistakable.
- Result: HELD.

### S5 — Old client with changed meaning

- Authoritative starting state: Older signed client encounters new content field, changed unit/meaning or server capability it cannot interpret.
- Allowed transition: Negotiate capability/content-generation compatibility; render known safe subsets and fail closed on safety-critical unknown meaning.
- Candidate mechanism: Common Kotlin versioned schemas/capability matrix and shared Compose compatibility state; native hosts maintain release artifacts.
- Official evidence: KMP hierarchical source sets constrain APIs per target at https://kotlinlang.org/docs/multiplatform/multiplatform-hierarchy.html; Compose version compatibility is documented at https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html.
- Reasoned inference: Shared source reduces presentation duplication but does not solve old signed binary, API, content meaning or store rollout compatibility.
- Dependency-specific evidence: Compose and KMP versions can be pinned, but no application lock or release graph exists.
- Unresolved facts: Capability negotiation, schema evolution, minimum-version policy, content fallback and rollback refusal criteria.
- User-visible result: Clear compatible/needs-update/held state; never invent interpretation of an unknown safety field.
- Failure/hold behavior: Unknown critical field or incompatible generation blocks affected flow; known portable history remains scoped.
- Recovery path: Staged store release, compatibility window, forward migration after review and explicit update; no OTA authority.
- Shared-system obligation: API/content versioning, store rollout and fail-closed safety policy are common.
- Candidate-attributable work: Common serializers/capability models, Compose state display and Android/iOS build matrix maintenance.
- Accountable AI/external owner: AI release/data implementer; API/content owner, safety reviewer and store custodian.
- Required later real-device evidence: Old/new client pair, changed fields, forced update, offline period, rollback refusal and mixed rollout.
- Residual risk: Common composables can appear source-compatible while old signed clients remain semantically incompatible.
- Result: HELD.

### S6 — Local profile and history conflict

- Authoritative starting state: Local notes/history and server profile differ because of offline edits, duplicate submission, account migration or restore.
- Allowed transition: Identify operation/record IDs, show migration/conflict preview, apply deterministic idempotent operations, retain provenance and request explicit resolution.
- Candidate mechanism: Common Kotlin pending-operation/conflict model and Compose resolution states with a transaction-safe local store behind an interface.
- Official evidence: KMP interfaces and platform implementations are documented at https://kotlinlang.org/docs/multiplatform/multiplatform-connect-to-apis.html.
- Reasoned inference: Common conflict UX/rules can be shared, but correctness depends on selected database, server contract and migration rehearsal.
- Dependency-specific evidence: No conflict, database or auth package is selected.
- Unresolved facts: Merge precedence, operation IDs, delete/tombstone rules, private-note policy, server conflict API, schema migration and backup interaction.
- User-visible result: Partial/conflict/needs-review is explicit, localized and accessible; no silent last-write-wins for protected truth.
- Failure/hold behavior: Ambiguous records are quarantined and affected action held; duplicate retries do not create duplicate authoritative outcomes.
- Recovery path: Retry idempotently, resolve through explicit UI/owner workflow, preserve audit/provenance and reconcile authority.
- Shared-system obligation: History, audit, conflict, deletion and privacy rules are common gates.
- Candidate-attributable work: Common operation model, Compose conflict UI, platform storage adapters and migration tests.
- Accountable AI/external owner: AI data implementer; product/data authority, security/privacy reviewer and safety owner.
- Required later real-device evidence: Offline edit/online merge, duplicate/partial upload, corrupt package, restore/clone, low storage and interrupted write on both platforms.
- Residual risk: KMP common code may hide platform database locking, ordering or migration differences.
- Result: HELD.

### S7 — Camera, file and evidence capture

- Authoritative starting state: Permission denied/granted; camera capture, photo-library selection or file import is attempted; process may die before return/upload.
- Allowed transition: Explain permission, allow retry/skip, validate type/size/content, stage temporary item, bind idempotent operation and expose upload uncertainty.
- Candidate mechanism: Shared Compose request/result state with native Android camera/Photo Picker/SAF and iOS camera/PHPicker/UIDocumentPicker hosts.
- Official evidence: Android Photo Picker and documents/files APIs are documented at https://developer.android.com/training/data-storage/shared/photopicker and https://developer.android.com/training/data-storage/shared/documents-files; Apple picker APIs are documented at https://developer.apple.com/documentation/photokit/phpickerviewcontroller and https://developer.apple.com/documentation/uikit/uidocumentpickerviewcontroller.
- Reasoned inference: Shared Compose wrappers can reduce form duplication but do not close permissions, URI/security-scoped lifetime, metadata, native accessibility or process-death correctness.
- Dependency-specific evidence: No camera, media, picker or upload package is selected; exact Android/iOS APIs and wrapper contracts are unresolved.
- Unresolved facts: MIME/size rules, EXIF/privacy, cleanup, permission edge cases, camera implementation, upload idempotency and host return behavior.
- User-visible result: Capture/import errors and denial have Turkish retry/skip paths; invalid/untrusted media is quarantined.
- Failure/hold behavior: Lost, partial, oversized, corrupt or unscanned evidence holds associated submission while retaining safe local recovery.
- Recovery path: Use host recovery, retry/manual entry, clean only proven temporary copies and reconcile operation state.
- Shared-system obligation: Privacy, evidence provenance, consent, retention and no-loss policy are shared.
- Candidate-attributable work: Compose wrappers/state, native permission and resource bridges, validation and process-death tests.
- Accountable AI/external owner: AI media implementer; Android/iOS media specialists, privacy/security reviewer and evidence owner.
- Required later real-device evidence: Permission deny/grant/reset, picker cancellation, camera interruption, process death, URI expiry, 3 MB/50-500 photo fixtures, low storage and native AT.
- Residual risk: A unified Compose form may mask different native URI, security-scope and process-loss behavior.
- Result: HELD.

### S8 — Accessible safety/readiness step

- Authoritative starting state: Turkish critical step contains active instruction, readiness, warning, stop and recovery states.
- Allowed transition: Focus/announce current state, expose labels/roles/actions, preserve order at largest text and non-color contrast, and make stop/recovery operable with AT.
- Candidate mechanism: Shared Compose semantics/traversal and state identifiers with Android/iOS native accessibility mapping and native surface checks.
- Official evidence: Compose semantics/accessibility is documented at https://kotlinlang.org/docs/multiplatform/compose-accessibility.html; iOS mapping and XCTest audit are documented at https://kotlinlang.org/docs/multiplatform/compose-ios-accessibility.html.
- Reasoned inference: Compose semantics can provide a shared base, but iOS synchronization, live-region behavior, VoiceOver wording, high contrast and native dialogs need independent human/device oracles.
- Dependency-specific evidence: Compose 1.12.0 release notes document iOS live-region and VoiceOver text-attribute support; Material3 high-contrast colors remain an explicit gap in the iOS accessibility guidance.
- Unresolved facts: Final Turkish copy, semantic grouping/traversal, high-contrast palette, Dynamic Type/reflow, reduced motion, native dialog announcements and AT capacity.
- User-visible result: Operator can hear/read active, unsafe, stopped, unknown and recoverable states without relying on color, gesture precision or visual-only diagrams.
- Failure/hold behavior: Any critical path failing AT/largest-text checks is held; semantic API availability is not a waiver.
- Recovery path: Return focus to safe-stop/recovery control, preserve state and provide text/manual alternative.
- Shared-system obligation: Accessibility acceptance and Turkish-first safety copy are candidate-neutral gates.
- Candidate-attributable work: Compose semantics tree, focus/traversal, platform mapping, native UI handoff and accessibility instrumentation.
- Accountable AI/external owner: AI UI implementer; independent human AT testers and qualified safety/content reviewer.
- Required later real-device evidence: VoiceOver/TalkBack, Switch/Voice Control, largest text/reflow, contrast/dark mode, reduced motion, native permission/picker/share/notification and all critical states.
- Residual risk: A shared semantic tree can pass API-level inspection while a real Turkish user cannot operate a time-critical state.
- Result: HELD.

### S9 — Framework, plugin and toolchain upgrade

- Authoritative starting state: Frozen comparison is Kotlin/KMP 2.4.20 plus Compose Multiplatform 1.12.0; a newer stable/hotfix, Compose compiler or native toolchain event is proposed.
- Allowed transition: Reproduce lock/artifact, review Kotlin/Compose/Jetpack and native graph, run scenario/AT/device/release evidence, then stage or refuse upgrade with rollback criteria.
- Candidate mechanism: Pinned Kotlin/KMP/Compose refs, Gradle lock/wrapper, native host configuration, release graph and migration fixtures.
- Official evidence: Compose compatibility and release cycles are documented at https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html; KMP compatibility and deprecations at https://kotlinlang.org/docs/multiplatform/multiplatform-compatibility-guide.html.
- Reasoned inference: Upgrade spans Kotlin compiler/Native, Compose compiler/runtime, Jetpack Compose Android artifacts, Gradle/AGP/JDK, Xcode and Swift framework integration.
- Dependency-specific evidence: Official lifecycle/navigation/resources versions shown in docs are not selected application dependencies; final transitive graph is absent.
- Unresolved facts: Upgrade cadence, security SLA, exact toolchain, Mac access, Compose iOS compatibility, migration/rollback artifact and owner capacity.
- User-visible result: No silent framework change; held/staged outcome retains last accepted artifact.
- Failure/hold behavior: Scenario, migration, native, AT or release regression holds upgrade; no store submission inferred.
- Recovery path: Keep frozen artifact, revert source/lock/toolchain together where safe, or perform reviewed forward migration; no lossy rollback.
- Shared-system obligation: Version policy, provenance, release windows and safety corrections are common.
- Candidate-attributable work: Compose/Kotlin upgrade tests, plugin/host migration, generated iOS framework verification and artifact reproducibility.
- Accountable AI/external owner: AI upgrade implementer; Android/iOS build specialists, security reviewer and store custodian.
- Required later real-device evidence: Comparison Android/iPhone, all critical flows, AT matrix, signed staging build, dependency/SBOM diff and rollback rehearsal.
- Residual risk: Shared UI can make a renderer change look small while Kotlin/Native or iOS framework integration changes the release graph.
- Result: HELD.

### S10 — Mixed rollout of old/new clients

- Authoritative starting state: Old/new signed binaries, Compose/KMP schemas, content generations and server capabilities coexist.
- Allowed transition: Capability/generation negotiation, staged store artifacts and additive/forward migrations; fail closed on unknown safety semantics.
- Candidate mechanism: Common Kotlin release/capability model and Compose compatibility state; separate Android/iOS artifacts and server graph.
- Official evidence: Compose releases map separately to Jetpack Compose and KMP/Gradle/AGP/Xcode compatibility at https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html.
- Reasoned inference: Common UI may reduce duplicated presentation, but cannot coordinate server capability, old binaries, store rollout or data meaning.
- Dependency-specific evidence: No application lock or native framework artifact graph exists.
- Unresolved facts: Compatibility window, minimum app version, schema negotiation, rollout pause, server contract and no-rollback conditions.
- User-visible result: Compatible work remains available; incompatible work has explicit update/hold path.
- Failure/hold behavior: Unknown/non-additive state held per task/record; rollout can pause without erasing portable history.
- Recovery path: Keep old/new artifacts, reconcile after compatibility, forward-migrate with backup and retain provenance; approved stores only.
- Shared-system obligation: Mixed rollout and release integrity are candidate-neutral.
- Candidate-attributable work: Common serializers/capability adapters, Compose route/state compatibility and host build matrix updates.
- Accountable AI/external owner: AI release/data implementer; backend/content owner, store custodian and safety reviewer.
- Required later real-device evidence: Old/new installs, upgrade/downgrade refusal, offline queue replay, generation mismatch, deep-link cold start and staged rollout.
- Residual risk: Kotlin/Native ABI, Compose runtime or host framework changes may break one platform despite common source compatibility.
- Result: HELD.

### S11 — Low/mid-device and storage pressure

- Authoritative starting state: Android API 29, 64-bit, 4 GB RAM, 64 GB storage and 2 GB free; local stress includes 3/10 motorcycles, 250/2,000 records, 50/500 3 MB photos, 100/1,000 notes, 20/200 pending and 3/30 conflicts.
- Allowed transition: Load only selected compact content, paginate/stream heavy media, report pressure, evict cache only and preserve records/pending truth.
- Candidate mechanism: Shared Compose lists/state and common Kotlin repository; image decoding, database and host memory policy remain open.
- Official evidence: Compose platform guidance documents platform-specific behavior and non-pixel-perfect text at https://kotlinlang.org/docs/multiplatform/compose-platform-specifics.html.
- Reasoned inference: Shared composables may reduce parity effort, but memory, image decode, database locking, startup and scrolling must be measured separately.
- Dependency-specific evidence: No image/database/cache dependency is selected; Compose resource support is not a performance guarantee.
- Unresolved facts: Peak memory, startup, render/scroll budget, image policy, database/indexes, cache eviction, thermal/battery and low-storage behavior.
- User-visible result: Honest progress and low-space/limited-media message; private notes/pending truth never silently deleted.
- Failure/hold behavior: Threshold breach holds optional work or release; cache eviction cannot discard pending/authoritative records.
- Recovery path: Evict verified cache, reduce optional media, retry foreground and reconcile; preserve/export records before destructive migration.
- Shared-system obligation: Fixture limits, retention/privacy, no-loss and safe degradation are common.
- Candidate-attributable work: Compose rendering/pagination, shared image-state model and Android/iOS profiling.
- Accountable AI/external owner: AI performance implementer; Android/iOS performance specialists and data/security owner.
- Required later real-device evidence: Cold/warm startup, local stress fixtures, low storage, thermal/rotation/background, image decode, DB recovery and largest-text accessibility.
- Residual risk: Compose visual consistency can hide platform-specific jank, memory pressure or input behavior.
- Result: HELD.

### S12 — Release, incident and pause

- Authoritative starting state: Staged Android and iOS artifacts are proposed; dependency, safety correction, store review or incident requires pause, impact assessment or recovery.
- Allowed transition: Verify source/ref/lock/SBOM/signature/provenance, stage stores independently, pause rollout, identify affected generations and preserve provider-independent artifacts.
- Candidate mechanism: Gradle KMP/Compose build plus Android host and Xcode iOS host, artifact manifest and explicit release graph.
- Official evidence: Compose first-app guidance documents separate Android and iOS project/build paths and macOS/Xcode need at https://kotlinlang.org/docs/multiplatform/compose-multiplatform-create-first-app.html.
- Reasoned inference: Shared Compose source provides a common build input, but signing identities, Mac/Xcode, store policy, iOS framework cache and incident response remain external/platform-specific.
- Dependency-specific evidence: No CI, Mac host, signing account, dependency lock, SBOM or attestation is present.
- Unresolved facts: CI/build provider, Mac availability, tool versions, signing custody, store review, artifact retention, incident authority and cost.
- User-visible result: Release/hold state is truthful; affected content/app path shows safe pause/recovery, not optimistic update.
- Failure/hold behavior: Missing provenance, failed AT/device/safety evidence, signature issue or incident blocks release and can pause rollout.
- Recovery path: Retain last accepted artifact, revoke/limit affected content by authority, issue reviewed correction and restore only after evidence; no OTA binary path.
- Shared-system obligation: Release integrity, safety correction, audit and pause controls are common.
- Candidate-attributable work: Gradle/Compose artifact reproducibility, generated iOS framework binding, host configuration and plugin/native coordination.
- Accountable AI/external owner: AI release implementer; store accounts, security custodian, qualified safety reviewer and native build operators.
- Required later real-device evidence: Signed staging artifacts on both stores, clean install/upgrade, pause and forward-migration drill, provenance verification and incident communication.
- Residual risk: One shared Gradle invocation can create false confidence while one host or store remains unverified.
- Result: HELD.

### S13 — Privacy, collaboration and device trust

- Authoritative starting state: Private notes/photos, shared/community material and official/safety material have distinct scopes; device may be restored, cloned, lost or shared.
- Allowed transition: Enforce scope/authorization, protect keys, label provenance, re-authenticate after restore/key mismatch and quarantine untrusted state.
- Candidate mechanism: Common Kotlin scope/provenance model and Compose labels, with Android Keystore/iOS Keychain native adapters.
- Official evidence: Android Auto Backup behavior is documented at https://developer.android.com/identity/data/autobackup; native key boundary is Android Keystore and Apple Keychain.
- Reasoned inference: Shared data/state can separate scopes, but key protection, backup exclusion and current authorization are native/account boundaries.
- Dependency-specific evidence: No crypto/auth/key package is selected; Compose resources or UI semantics are not security primitives.
- Unresolved facts: Key hierarchy/rotation, iOS backup/Keychain semantics, Android include/exclude, clone detection, ACLs, deletion/export and re-auth.
- User-visible result: Private/shared/official labels, lock/re-auth/quarantine and disclosure warnings explicit and accessible.
- Failure/hold behavior: Key/authority mismatch holds protected action and preserves safe metadata without plaintext exposure.
- Recovery path: Re-authenticate, re-download/re-encrypt under current authority, preserve audit/provenance and revoke invalid device/session authority.
- Shared-system obligation: Privacy, authorization, key loss, backup and deletion rules are product-wide.
- Candidate-attributable work: Common scope state, Compose semantics, typed native security boundary and restore/clone harness.
- Accountable AI/external owner: AI security/data implementer; security/privacy reviewer, account authority and Android/iOS key specialists.
- Required later real-device evidence: Backup/restore, device-to-device transfer, clone, key rotation/loss, uninstall/reinstall, permission reset and AT for scope labels.
- Residual risk: Shared state presentation may conceal OS backup of stale data or omission of key material.
- Result: HELD.

### S14 — Entitlement, evidence and lifecycle change

- Authoritative starting state: Entitlement, publication, correction, withdrawal, transfer or delete authority changes while task is active or offline.
- Allowed transition: Preserve last durable safe checkpoint, evaluate current authority when available, block withdrawn/ineligible actions and retain audit/provenance.
- Candidate mechanism: Common Kotlin state machine/reconciliation and Compose status, with lifecycle/notification/deep-link signals only as accelerators.
- Official evidence: Compose lifecycle mappings are documented at https://kotlinlang.org/docs/multiplatform/compose-lifecycle.html; they do not define Kavriva entitlement or safety semantics.
- Reasoned inference: Shared Compose can present deterministic state, but authority and lifecycle correctness are backend/product/native concerns.
- Dependency-specific evidence: No entitlement, push or subscription provider/package is selected.
- Unresolved facts: Entitlement source/TTL, offline grace, withdrawal timing, transfer/delete policy, active-task semantics and reconciliation contract.
- User-visible result: Active/held/withdrawn/transferred/needs-review state with safe-stop and Turkish explanation.
- Failure/hold behavior: Authority uncertainty or withdrawal blocks affected action; in-flight operation remains unknown/partial until reconcile.
- Recovery path: Reconnect/re-authenticate, reconcile idempotently, preserve evidence and apply reviewed correction/transfer/delete.
- Shared-system obligation: Authorization, publication, audit, safety and retention are framework-neutral.
- Candidate-attributable work: Common state/reconciliation, Compose presentation and native notification/deep-link/lifecycle plumbing.
- Accountable AI/external owner: AI state implementer; product/authorization owner, qualified safety reviewer and privacy/legal authority.
- Required later real-device evidence: Entitlement changes foreground/background, notification denied, cold deep-link, process kill, offline grace expiry and correction/withdrawal.
- Residual risk: Common UI may hide a server-authority race or accidental notification authority.
- Result: HELD.

### S15 — Backup, restore, clone and key loss

- Authoritative starting state: Backup/restore, device clone, reinstall or protected-key loss occurs with local packages, history, pending operations and private media.
- Allowed transition: Classify restored data, validate account/device/key/content generations, quarantine mismatch, re-authenticate and re-download non-portable material; restore only last durable checkpoint.
- Candidate mechanism: Common Kotlin portable schema/manifests and Compose recovery state with native backup/key adapters.
- Official evidence: Android Auto Backup covers API 23+, normally includes databases/files, excludes cache, has a 25 MB per-app cloud quota and can restore stale/device-specific values: https://developer.android.com/identity/data/autobackup.
- Reasoned inference: Shared Compose can present restore status, but OS backup/key behavior and key continuity cannot be inferred from common code.
- Dependency-specific evidence: No backup/encryption package is selected; Compose resources and KMP source sets do not establish restore semantics.
- Unresolved facts: iOS backup/key behavior, Android rules, key hierarchy, clone detection, operation replay, media retention, quota and recovery authority.
- User-visible result: Restored/partial/quarantined/re-auth states explicit; stale entitlement/token never presented as current.
- Failure/hold behavior: Key loss, generation mismatch, corrupt database or replay ambiguity holds protected actions and preserves permitted portable records.
- Recovery path: Re-authenticate, validate/forward-migrate, re-download compact content, re-encrypt under current keys and retain audit; no silent discard.
- Shared-system obligation: Data continuity, backup, privacy, deletion and authority reconciliation are common.
- Candidate-attributable work: Common restore state, Compose quarantine UX, native key/backup adapters and migration fixtures.
- Accountable AI/external owner: AI data/security implementer; Android/iOS backup specialists, security reviewer, account authority and privacy/legal owner.
- Required later real-device evidence: Android API 29/current and comparison iPhone backup/restore, clone, reinstall, key loss, corrupt DB, pending replay, media and largest-text AT scenarios.
- Residual risk: Successful OS restore may remain semantically stale or cryptographically unusable.
- Result: HELD.

## 6. Accessibility Matrix

This matrix is capability evidence, not approval. Compose Multiplatform documents semantic properties, traversal and iOS
mapping to native accessibility objects, but the iOS high-contrast Material3 gap, host-owned surfaces and real Turkish
critical-flow behavior remain unresolved.

| Check | Framework/documented capability | Platform-specific work | Later real-device oracle | Status |
|---|---|---|---|---|
| VoiceOver | Compose semantics map to iOS accessibility objects; Compose 1.12.0 release notes include live-region and VoiceOver text-attribute changes | Validate Compose tree synchronization, UIKit/SwiftUI/native picker/permission/share/notification surfaces | VoiceOver through active, warning, stop, unknown, recovery, conflict and restore states | HELD |
| TalkBack | Compose semantics/traversal properties provide a common base | Android semantics, native dialogs, Photo Picker, notifications and back behavior | TalkBack through critical states and process interruptions | HELD |
| Largest text/reflow | Compose text/layout can adapt; no Kavriva layout pass exists | Android font scale, iOS Dynamic Type, native dialog and diagram behavior | Largest supported size, clipping/truncation, scroll and text alternative | HELD |
| Focus and reading order | Compose traversal semantics and focus APIs are documented | Host return focus, back navigation, interop view order and keyboard/switch behavior | Focus order across every safety transition and native surface | HELD |
| State announcements | Shared semantics can expose active/held/warning/recovery state | iOS live-region synchronization and Android announcement timing require validation | Turkish active/readiness/warning/unknown/stop/recovery announcements | HELD |
| Non-color status/contrast | Semantics/text can avoid color-only meaning; iOS Material3 high-contrast colors not automatic | Theme/tokens, native controls and OS contrast settings | Contrast, dark/high-contrast, color-blind and diagram/text alternatives | HELD |
| Reduced motion | Compose animation policy can be designed | Android/iOS reduce-motion signals and native transitions need integration | Reduced motion during warning, stop, navigation and media | HELD |
| Switch/voice control | Compose semantics can expose controls | Android Switch/Voice Access and iOS Switch Control/Voice Control for native and interop surfaces | Switch scanning, labels and no gesture-only critical action | HELD |
| Reduced dexterity | Compose controls can be sized and alternative paths designed | System back, picker cancel, interruption, share return and touch-target behavior | One-hand/touch target, cancel/retry and safe-stop operation | HELD |

No row is PASS. Framework semantics, Compose 1.12.0 release notes or XCTest audit access cannot substitute for
independent human AT review on physical devices.

## 7. Upgrade and Forced-Event Walkthrough

| Event | KMP + Compose path under the fixture | Evidence and affected contracts | External dependency/capacity | Hold/recovery |
|---|---|---|---|---|
| Planned quarterly release | Re-pin Kotlin/KMP/Compose/compiler, Gradle/AGP/JDK/Xcode, dependency locks and generated iOS framework; run critical-flow/AT/device/release evidence, then stage stores | Compose releases are separate from Kotlin/Jetpack and typically align with Jetpack with a 1–3 month gap; compatibility matrix is official | Android/iOS specialists, Mac/Xcode, devices, AT/safety/release custodians | HOLD until graph/evidence exist; retain prior artifacts and forward-migrate only after review |
| Safety/security correction | Apply approved content revocation/authority correction; binary correction follows two signed host artifacts | Shared UI cannot be current recall authority; generation, audit, signing and no-OTA rules affected | Qualified safety reviewer, security custodian, stores and incident authority | Pause affected generation/release, safe-stop offline, publish reviewed correction and reconcile |
| Forced Apple/Google build/store requirement | Update native host/toolchain and shared framework integration, rebuild both artifacts, repeat evidence | KMP compatibility binds Kotlin/Gradle/AGP/Xcode; iOS macOS/Xcode is required by official quickstart | Mac/Xcode/signing/store access; exact current requirements and cost UNRESOLVED | HOLD missing host/custodian; preserve source/lock/artifact |
| Critical dependency abandonment | Replace local DB/media/transfer/key/navigation/resource dependency or move boundary to owned native adapter; update lock/SBOM and Compose/KMP compatibility | No package is selected; common UI may still depend on native API and compiler/runtime compatibility | KMP/Compose/Android/iOS specialists, security review, device lab | Quarantine capability, retain manual safe path if safe, forward-migrate; no silent substitution |
| Old/new client/API/schema/content/config coexistence | Common capability/generation graph, additive/forward serializers, staged separate stores and fail-closed unknown safety meaning | Lockfile only controls one artifact; old signed Android/iOS binaries remain | Backend/content owner, store custodian and safety reviewer | Hold incompatible path; maintain accepted artifacts and migrate forward |
| Migration rollback refusal | Refuse lossy downgrade, preserve backup/provenance and use reviewed forward migration | Database/key/schema implementation not selected; generated iOS framework rollback is separate from data rollback | Data/security reviewer and restore game-day capacity | HOLD downgrade if unsafe; quarantine and recover last durable checkpoint |
| Incident pause, impact and recovery | Use source/lock/framework/artifact/content manifest to identify affected platform and generation, pause rollout and communicate | DEBATE-005 provenance/SBOM and release graph bind shared and host artifacts | Incident, security, safety, content, native and store authorities | Suspend, preserve evidence, issue correction and re-test; no production pass claimed |

The exact toolchain is not frozen by the supported range. In particular, a Kotlin/Compose upgrade can affect Kotlin/Native
framework generation, Compose compiler/runtime, Android Jetpack artifact mapping, Gradle/AGP and Xcode/Swift integration
at once. No OTA binary authority is assumed.

## 8. AI-Operability and Task Isolation

| Question | Evidence/result |
|---|---|
| Can a fresh AI implement one bounded task without whole-project context? | Potentially: common Kotlin contracts, shared Compose state and explicit Android/iOS host boundaries can define bounded tasks. No repository, task graph or contract-test evidence exists; HELD. |
| Are platform exceptions visible in the task graph? | They can be enumerated through common/platform source sets, expect/actual interfaces and host modules. Final native exception/dependency inventory, owner and fallback are absent; HELD. |
| Can implementation, review and validation remain separate? | Shared Compose UI can have common tests, while native, AT, safety, migration and signed-artifact review remain separate. No reviewer capacity, device oracle or signed evidence exists; HELD. |
| Are builds/tests deterministic enough to produce evidence? | Kotlin/KMP/Compose versions and a compatibility range are recorded; exact Gradle wrapper, AGP, JDK, Xcode, locks, generated framework and CI are not pinned; HELD. |
| Can dependency changes identify affected contracts/tasks/tests? | Pub/Maven/Gradle locks, SBOM and platform graph could map impact, but no application graph or provenance manifest exists; HELD. |
| Can the project recover without one opaque workstation/provider? | Shared source, manifests and portable contracts can be kept provider-independent; iOS requires macOS/Xcode and signing authority, and backup host/cost are unknown; HELD. |
| Does the candidate require unavailable human specialist authority? | Yes, likely: Android/iOS native, Kotlin/Native/Gradle, Xcode/Swift, security/key, accessibility, safety, store and incident owners. The nontechnical owner is not a coding/debugging/build-repair mitigation; HELD. |

The principal AI benefit is a common Kotlin domain/presentation contract and Compose UI surface. The principal risk is
that shared composables make native lifecycle, semantics mapping, compiler/runtime, generated-framework, signing and
platform dependency work appear smaller than it is. Every exception remains a separately owned task.

## 9. Equal 24-Month TCO Worksheet

### 9.1 Workload quantities (not prices)

These are the approved fixture quantities for equal comparison, not forecasts, retention commitments or provider quotes.
Using two 12 MB compact transfers per MAU/month, optional media for 10 percent of MAU at 100 MB, and 0.5 photos at
3 MB:

| MAU tier | Compact transfer bytes/month | Optional media bytes/month | Photo upload bytes/month | Retained photo bytes over 24 months if never evicted |
|---:|---:|---:|---:|---:|
| 1,000 | 24 GB | 10 GB | 1.5 GB | 36 GB |
| 10,000 | 240 GB | 100 GB | 15 GB | 360 GB |
| 50,000 | 1.2 TB | 500 GB | 75 GB | 1.8 TB |

These quantities exclude protocol overhead, retries, thumbnails, backups, replication, egress, logs and provider billing
units. Local-device stress is not multiplied by MAU. Retention is UNRESOLVED; the retained-photo column is a scenario
quantity, not a promise.

### 9.2 Controlled category table

Unknown amounts remain UNRESOLVED, never zero. No provider plan, tax, currency conversion, discount, human hourly rate
or optional service price is invented.

| Cost row | Product-wide unavoidable | Candidate-caused | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---|---|---|---|---|---|---|
| Store membership | Yes | No | No | No | No | No free production-store substitute; defer purchase | Approved fixture: Google Play Console USD 25 one-time + Apple Developer USD 99/year; 24-month store-only USD 124-223 before tax/currency and renewal timing; high/recheck |
| Mac/hosted build | Yes for iOS release | KMP/Compose adds generated-framework integration and host graph | Hosted build optional | Access/build frequency | Borrow/local Mac or provider switch | Local/borrowed Mac preferred | UNRESOLVED; low |
| Android/iPhone access | Yes | Shared Compose requires both host/device acceptance | Lab/borrowed devices optional | More cohorts/releases | Replace lab/borrower | Borrow/tester/device lab | UNRESOLVED; low |
| CI/build artifacts | Yes for reproducible release evidence | Kotlin/Gradle/Compose/iOS framework graph | Hosted CI optional | Build/release volume | Provider-independent artifact path | Local controlled build with exportable manifests | UNRESOLVED; low |
| Backend/database | Yes | No provider selected; KMP shared data contracts need an implementation | Managed convenience optional | MAU/workload/retention | Export/replace provider | Free tier only with cap, overage shutdown, alert, export and exit | UNRESOLVED; low |
| Storage/backup/CDN/egress | Yes | Shared package/state model must enforce scope but does not set provider price | CDN/replication convenience optional | MAU, media, retries and retention | Compact scope, optional media and export | Cache eviction and capped tiers | UNRESOLVED; no price inferred from quantities; low |
| Identity/email/SMS | Yes if account flows require it | No KMP identity provider selected | SMS/premium recovery optional | MAU and recovery use | Manual/export recovery where approved | Email/manual first if approved; cap SMS | UNRESOLVED; low |
| Crash/telemetry/analytics | No until approved | Compose/KMP/native boundary may increase observability scope | Optional | MAU/events | Disable/export logs | Disable or capped/free path with privacy and spend approval | UNRESOLVED, not zero; low |
| Security/SBOM/signing | Yes | Kotlin/Native/Compose/Gradle/Maven/Xcode dependency closure adds inputs | Paid scanner/host optional | Release/dependency cadence | Owned lock/SBOM/attestation | Reviewable open tooling if capacity exists | UNRESOLVED; low |
| Accessibility validation | Yes | Shared Compose semantics/iOS mapping and two host surfaces need validation | External lab optional but independent human evidence required | Every release/forced event | Hold/rework/native fallback | Borrowed AT testers/devices | UNRESOLVED; low |
| Safety/content review | Yes | Shared state presentation cannot replace qualified review | No AI-only substitute | Content/release/correction | Safe-stop and release pause | Qualified owner required | UNRESOLVED; low |
| AI implementation/review | Capacity-dependent | Common Kotlin/Compose surface may reduce duplicate routine UI work; native exceptions remain | Optional paid AI/service capacity unapproved | Task/review volume | Portable artifacts and reassignment | Bounded tasks only if approved capacity and spend controls exist | UNRESOLVED; low |
| Upgrade/dependency response | Yes | Kotlin/KMP/Compose compiler/runtime, Jetpack mapping and generated iOS framework are candidate-specific | Hosted migration support optional | Quarterly/forced events | Pin, retain prior artifact, replace dependency/native adapter | Local lock and staged migration | UNRESOLVED; low |
| Support/incident response | Yes | Shared UI plus two native hosts create cross-platform release surface | Contracted/on-call convenience optional | MAU/platform/release scope | Pause/stage/provider-independent evidence | Explicit incident owner and capped operations | UNRESOLVED; low |
| Exit/migration | Yes | Compose source, Kotlin/Native framework and Gradle/Xcode integration are candidate-bound | Replacement candidate work optional | Triggered by forced event/exit | Portable schemas/manifests/export and forward migration | No lossy rollback; retain accepted artifacts | UNRESOLVED; low |

KMP + Compose-specific cost is therefore a capacity statement, not a price claim. Shared Kotlin/Compose UI may reduce
routine Android/iOS presentation duplication, while two host artifacts, iOS macOS/Xcode/framework integration, native
accessibility, dependency/compiler upgrades, security closure and physical-device acceptance remain real burdens. Any
unapproved OTA line is disabled and remains UNRESOLVED, not zero.

## 10. Exit Dossier

### Portable or replaceable assets

- Canonical product/content/data schemas, history/provenance records, corrections, withdrawal events, operation IDs
  and migration fixtures should be framework-neutral.
- Content manifests, digests, compact-package boundaries, safety/recovery closure and optional-media metadata should be
  consumable by a replacement client.
- User-controlled export/share formats, Turkish copy keys, unit rules, design tokens, semantic state identifiers and
  accessibility intent should survive a renderer change.
- S1-S15 fixtures, acceptance oracles, release/rollback/revocation evidence and audit references should remain outside
  Compose/Kotlin implementation details.
- Forward migrations must be explicit, versioned and rehearsed; old signed clients remain contained by server
  capability/content policy.

### Candidate-bound assets

- Common Kotlin source, Compose composables/state/runtime, Compose compiler/runtime artifacts, Kotlin/Native binaries,
  generated iOS frameworks, Android Compose/host integration, Gradle configuration and signed binaries are bound to this
  candidate or its toolchain.
- Camera, file picker, notification, deep link, share, lifecycle, secure-key and background-transfer adapters remain
  native/platform boundaries even when invoked by a shared composable.
- Android Keystore and iOS Keychain keys are not portable user data. Key loss requires quarantine, re-authentication and
  re-encryption; it must not be fixed by exporting raw keys.

### Migration, interruption and cost

- A replacement candidate may consume canonical data/manifests through a dual-format or forward migration path; no
  lossy rollback or silent history rewrite is allowed.
- Interruption plan: retain last accepted Android/iOS artifacts, preserve portable records/export, pause affected
  content/release, and reconcile only after the replacement is reviewed, built and signed.
- Exact exit effort, interruption duration, generated-framework replacement, migration tooling, replacement support and
  cost are UNRESOLVED. No exit success or portability pass is claimed.

## 11. Candidate Result (Phase-4 Research)

### Mandatory-gate result

All mandatory gates remain HELD:

- Safety/readiness and truthful uncertainty: common state semantics are expressible; no implementation or qualified
  safety evidence exists.
- Offline scoped delivery and 72-hour behavior: common state/Compose UI path is plausible; atomic package/resume and
  platform background proof is absent.
- Native closure and lifecycle/restart: host boundaries and lifecycle documentation exist; Android/iOS adapters and
  kill/restart evidence are absent.
- Accessibility and Turkish critical flow: Compose semantics/iOS mapping are documented; independent VoiceOver/TalkBack,
  high-contrast, largest-text and native-surface oracles are absent.
- Release, signing, provenance and forced events: version/compatibility evidence exists; lock, generated framework,
  host, signing, store and SBOM graph is absent.
- Data continuity, backup/restore and key loss: portable boundary is described; database/schema/iOS key/restore game day
  is absent.
- AI-operability and task isolation: bounded task structure is possible; executable task/review/build evidence is absent.
- 24-month TCO and owner capacity: store baseline is approved; all other prices, providers and capacity are unresolved.
- Exit/migration and replacement continuity: portable-asset plan is described; migration rehearsal is absent.

S1-S15 result count: 0 PASS / 15 HELD / 0 REJECT. No real-device pass, store pass, benchmark, security pass or
safety approval is claimed.

### Unresolved critical facts

- Product support policy, exact OS/build floors, Compose iOS accessibility synchronization/high-contrast behavior,
  lifecycle/recovery semantics and offline recall validity.
- Final Kotlin/KMP/Compose/compiler/toolchain ref, full source/archive digest, Gradle/AGP/JDK/Android SDK,
  macOS/Xcode/Swift integration and store matrix.
- Committed direct/transitive Gradle/Maven dependency lock, Compose/Jetpack mapping, generated iOS framework provenance,
  native implementation graph, SBOM/license/EOL/security response and owned fallbacks.
- Transactional local database, schema/migration, account/entitlement/conflict contract, backup/restore/key semantics
  and portable export format.
- Android/iPhone devices, VoiceOver/TalkBack/other AT reviewers, independent safety/content reviewer, release/signing/
  store custodian, Mac access and incident authority.
- AI task/review capacity, cash ceiling, optional-service approvals and current provider quotes; no numeric amount is
  assumed for unresolved lines.
- Mixed old/new client/API/content/config release graph, pause/rollback refusal and correction/withdrawal protocol.

### Conditional interpretation

The largest low-budget burden is qualitatively the iOS macOS/Xcode/generated-framework/signing path together with
physical-device, accessibility, safety review and Kotlin/Compose/native dependency upgrade coverage. The largest
AI-operability benefit is one Kotlin domain/state and Compose presentation surface; the largest risk is hidden host,
compiler/runtime, semantics-mapping and platform-service exception work.

External authorities remain required for Apple/Google legal identity and store accounts, Mac/Xcode/signing, physical
devices/testers/AT, qualified safety/content review, security/privacy, tax/legal/payment and any selected provider. No
framework recommendation is made. A later recommendation would require complete native closure, pinned toolchain/
dependency/provenance, evidence for all S1-S15, AT/device/safety/release oracles, owner/capacity/TCO approval and
independent review. A rejection would be triggered by an ownerless critical path, unsafe bypass, unbounded
unapproved cost, lost canonical truth or unsupported capability without a safe fallback; none is asserted as an
intrinsic KMP + Compose rejection here, but all gates remain HELD.

Overall Phase-4 status: STRUCTURALLY COMPLETE DRAFT / UNREVIEWED / HELD.

## Source Register

Official/primary external sources consulted for this dossier (retrieved 2026-09-17):

- Compose Multiplatform compatibility and versions: https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html
- Compose Multiplatform 1.12.0 release: https://github.com/JetBrains/compose-multiplatform/releases/tag/v1.12.0
- Kotlin 2.4.20 release: https://github.com/JetBrains/kotlin/releases/tag/v2.4.20
- Kotlin Multiplatform compatibility guide: https://kotlinlang.org/docs/multiplatform/multiplatform-compatibility-guide.html
- Compose Multiplatform and Jetpack Compose relationship: https://kotlinlang.org/docs/multiplatform/compose-multiplatform-and-jetpack-compose.html
- Platform-specific Compose behavior and entry points: https://kotlinlang.org/docs/multiplatform/compose-platform-specifics.html
- Kotlin platform APIs and expect/actual boundaries: https://kotlinlang.org/docs/multiplatform/multiplatform-connect-to-apis.html
- KMP hierarchical source sets: https://kotlinlang.org/docs/multiplatform/multiplatform-hierarchy.html
- Compose accessibility and iOS accessibility: https://kotlinlang.org/docs/multiplatform/compose-accessibility.html and https://kotlinlang.org/docs/multiplatform/compose-ios-accessibility.html
- Compose lifecycle and navigation/deep links: https://kotlinlang.org/docs/multiplatform/compose-lifecycle.html and https://kotlinlang.org/docs/multiplatform/compose-navigation-deep-links.html
- Compose resources and first-app/iOS host: https://kotlinlang.org/docs/multiplatform/compose-multiplatform-resources.html and https://kotlinlang.org/docs/multiplatform/compose-multiplatform-create-first-app.html
- Android Keystore, background work, media/files, notifications, accessibility and backup: https://developer.android.com/privacy-and-security/keystore, https://developer.android.com/develop/background-work/background-tasks/persistent, https://developer.android.com/training/data-storage/shared/photopicker, https://developer.android.com/training/data-storage/shared/documents-files, https://developer.android.com/develop/ui/views/notifications/notification-permission, https://developer.android.com/guide/topics/ui/accessibility/apps and https://developer.android.com/identity/data/autobackup
- Apple Keychain, background tasks/transfers, media/file pickers, notifications and accessibility: https://developer.apple.com/documentation/security/keychain_services, https://developer.apple.com/documentation/backgroundtasks, https://developer.apple.com/documentation/foundation/url_loading_system/downloading_files_in_the_background, https://developer.apple.com/documentation/photokit/phpickerviewcontroller, https://developer.apple.com/documentation/uikit/uidocumentpickerviewcontroller, https://developer.apple.com/documentation/usernotifications and https://developer.apple.com/documentation/accessibility
- Internal controls: AI_START_HERE, CURRENT_STATE, SOURCE_OF_TRUTH, PROJECT_CHAT_INSTRUCTIONS, DECISION_LOG/DEC-0031,
  the approved common fixture, MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO and CANDIDATE_DOSSIER_TEMPLATE.
