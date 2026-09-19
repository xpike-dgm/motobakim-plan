# DEBATE-006 — Candidate Dossier: Fully Native Kotlin/Android + Swift/iOS Baseline

Status: STRUCTURALLY COMPLETE DRAFT / UNREVIEWED / HELD / NO-CODE  
Date: 2026-09-17  
Candidate: E — Fully native Kotlin/Android plus Swift/iOS reference baseline

This is a documentary Phase-4 research dossier, not a recommendation, implementation
plan, prototype, benchmark, store submission, or ADR. Sections 1–11 are structurally
present but unreviewed and held. No scenario, accessibility acceptance, build, benchmark,
store submission or real-device pass is claimed.

Evidence labels used below:

- OFFICIAL EVIDENCE: a primary Android Developers, Apple Developer, or other platform
  vendor source.
- INTERNAL CONTROL: an approved Kavriva control or fixture document.
- REASONED INFERENCE: an explicit implication for Kavriva; it is not a vendor guarantee.
- DEPENDENCY-SPECIFIC: a statement tied to an identified library, OS, or toolchain.
- UNRESOLVED: a fact that still needs an accountable owner and evidence. It is not a pass
  and it is not a zero-cost assumption.

## 1. Candidate Identity

| Field | Recorded value |
|---|---|
| Candidate family | Two complete native mobile application and UI paths: Kotlin/Android and Swift/iOS. Android and iOS have separate lifecycle, storage, accessibility, build, signing, test, and release ownership. No shared mobile UI runtime is assumed. |
| Exact evaluated version/snapshot | Android reference toolchain: Android Studio Quail 4 2026.1.4 stable; Android Gradle Plugin 9.0.1; Gradle 9.1.0; built-in Kotlin Gradle Plugin runtime dependency 2.2.10; JDK 17; Android SDK Platform 36 revision 1; SDK Build Tools 36.0.0; NDK 28.2.13676358. iOS reference toolchain: Xcode 26.4; Swift 6.3; iOS 26.4 SDK; macOS Tahoe 26.2. These are exact vendor-documented snapshots where available, not a generated project lockfile. |
| Evidence retrieval date | 2026-09-17, Europe/Istanbul. Dynamic latest claims are not used as the evaluated snapshot. |
| Product-supported Android/iOS floor tested against | The equal fixture proposes Android 10 / API 29 constrained devices, Android 13+ main devices, iOS 16.4-capable oldest iPhone, and a current generally available standard non-Pro iPhone. No branded device, patch level, or real-device pass has been selected; product-floor evidence is UNRESOLVED. |
| Framework-supported floor | There is no cross-platform framework floor. Android platform APIs used by the reference path must be checked against proposed minSdk/API 29; iOS platform APIs must be checked against proposed iOS 16.4 deployment target. API availability is not a product acceptance pass. |
| Build-tool/store floor | Android toolchain snapshot is documented below. Apple upload guidance currently identifies Xcode 26 or later for iOS app builds; Google’s current target API requirement is time-sensitive. Store, target API, Xcode upload, notarization/signing, and future OS/build floors must be rechecked at each release and are therefore dynamic/UNRESOLVED. |
| Support/EOL statement | Android SDK/Jetpack, Kotlin, Gradle/AGP, JDK, NDK, Xcode, Swift, Swift Package Manager, and third-party libraries each have different support and security lifecycles. Direct platform access does not create a combined support contract. Exact EOL/security-response dates, upgrade SLA, and primary/backup owners are UNRESOLVED. |
| Dossier author/reviewer | Codex research agent using the controlled fixture and official platform sources. Independent Android/iOS reviewers, accessibility testers, safety reviewer, and release owner are UNRESOLVED. |

Every later reference to comparison devices, both devices, both platforms, platform evidence or real-device acceptance
means all four frozen cohorts above. A two-device, one-device-per-platform or oldest-only sample cannot close a scenario
or accessibility gate.

### 1.1 Defensible toolchain snapshot

Android Developers documents Android Studio Quail 4 version 2026.1.4 as a stable
release at retrieval. Android Gradle Plugin 9.0.1 documents Gradle 9.1.0, SDK Build Tools
36.0.0, JDK 17, NDK 28.2.13676358, maximum API 36.1, and built-in Kotlin support with
Kotlin Gradle Plugin runtime dependency 2.2.10. Android SDK Platform release notes document
Android 16 / API 36 revision 1. These exact values are recorded as a build reference, not
as a claim that the workspace already contains them.

Apple’s Xcode 26.4 release notes document Swift 6.3, iOS 26.4 SDKs, and a macOS Tahoe
26.2 requirement. Apple’s App Store Connect guidance currently identifies Xcode 26 or
later for building iOS apps for upload. The Xcode/SDK and App Store Connect rules are
release-time dependencies; future floors are UNRESOLVED. Xcode’s ability to debug an older
device is not the same as an app deployment-target or store-acceptance guarantee.

### 1.2 Primary-source key

External technical claims in this dossier use only the following official or primary
sources, retrieved or checked on 2026-09-17:

- A1 — [Android Studio releases](https://developer.android.com/studio/releases).
- A2 — [Android Gradle Plugin 9.0.1 release notes](https://developer.android.com/build/releases/agp-9-0-0-release-notes).
- A3 — [Android SDK Platform release notes](https://developer.android.com/tools/releases/platforms).
- A4 — [Set up the Android 16 SDK](https://developer.android.com/about/versions/16/setup-sdk).
- A5 — [Android app architecture](https://developer.android.com/topic/architecture).
- A6 — [Android processes and app lifecycle](https://developer.android.com/guide/components/activities/process-lifecycle) and [Activity lifecycle](https://developer.android.com/topic/libraries/architecture/views/activity-lifecycle-views).
- A7 — [WorkManager task scheduling](https://developer.android.com/develop/background-work/background-tasks/persistent) and [WorkManager getting started](https://developer.android.com/develop/background-work/background-tasks/persistent/getting-started).
- A8 — [Android Keystore system](https://developer.android.com/privacy-and-security/keystore).
- A9 — [Android data backup overview](https://developer.android.com/identity/data/backup) and [Auto Backup](https://developer.android.com/identity/data/autobackup).
- A10 — Android [Room persistence](https://developer.android.com/training/data-storage/room), [Photo Picker](https://developer.android.com/training/data-storage/shared/photo-picker), and [Storage Access Framework](https://developer.android.com/training/data-storage/shared/documents-files).
- A11 — [Jetpack Compose accessibility](https://developer.android.com/develop/ui/compose/accessibility) and [Compose semantics](https://developer.android.com/develop/ui/compose/accessibility/semantics).
- A12 — [Android App Links](https://developer.android.com/training/app-links/about) and [deep links](https://developer.android.com/training/app-links).
- A13 — Android [camera permission guidance](https://developer.android.com/training/permissions/requesting) and [CameraX permission example](https://developer.android.com/codelabs/camerax-getting-started).
- P1 — [Xcode 26.4 release notes](https://developer.apple.com/documentation/xcode-release-notes/xcode-26_4-release-notes).
- P2 — Apple [App Store Connect upload-build guidance](https://developer.apple.com/help/app-store-connect/manage-builds/upload-builds) and [App Store Connect workflow](https://developer.apple.com/help/app-store-connect/get-started/app-store-connect-workflow).
- P3 — Apple [UIKit app lifecycle](https://developer.apple.com/documentation/uikit/managing-your-app-s-life-cycle), [background execution](https://developer.apple.com/documentation/uikit/about-the-background-execution-sequence), and [scene lifecycle migration](https://developer.apple.com/documentation/uikit/transitioning-to-the-uikit-scene-based-life-cycle).
- P4 — Apple [background URLSession downloads](https://developer.apple.com/documentation/foundation/downloading-files-in-the-background) and [URLSession](https://developer.apple.com/documentation/foundation/urlsession).
- P5 — Apple [Keychain Services](https://developer.apple.com/documentation/security/keychain-services) and [using the Keychain for secrets](https://developer.apple.com/documentation/security/using-the-keychain-to-manage-user-secrets).
- P6 — Apple [data protection for app files](https://developer.apple.com/documentation/uikit/encrypting-your-apps-files) and [App Sandbox](https://developer.apple.com/documentation/security/protecting-user-data-with-app-sandbox).
- P7 — Apple [Core Data](https://developer.apple.com/documentation/coredata/) and [Core Data migrations](https://developer.apple.com/documentation/coredata/staged-migrations).
- P8 — Apple [AVFoundation camera authorization](https://developer.apple.com/documentation/avfoundation/requesting-authorization-to-capture-and-save-media) and [capture session](https://developer.apple.com/documentation/avfoundation/setting-up-a-capture-session).
- P9 — Apple [SwiftUI accessibility fundamentals](https://developer.apple.com/documentation/swiftui/accessibility-fundamentals).
- P10 — Apple [User Notifications](https://developer.apple.com/documentation/usernotifications) and [local notification scheduling](https://developer.apple.com/documentation/usernotifications/scheduling-a-notification-locally-from-your-app).
- P11 — Apple [associated domains](https://developer.apple.com/documentation/xcode/supporting-associated-domains) and [universal links](https://developer.apple.com/documentation/xcode/allowing-apps-and-websites-to-link-to-your-content).
- I1 — [DEC-0031 and the common fixture](../../00_CONTROL/DECISION_LOG.md) and [DEBATE-006 common fixture and operating assumptions](DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md).
- I2 — [DEBATE-006 mobile technology evidence, team and TCO](DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md).
- I3 — [DEBATE-006 controlled candidate dossier template](DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md).
- I4 — [DEBATE-005 software, content, supply-chain and release governance](DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md).

## 2. Fixed Inputs

This candidate uses the approved common comparison fixture without relaxation or
candidate-specific constants. The fixture is controlled by DEC-0031 and I1. Any change to
a shared constant reopens one revision for all five candidates. Scenario records S1–S15
below use the same controlled record schema and remain held.

### 2.1 Product, horizon and release cadence

- The product surface is consumer mobile on Android and iOS plus a browser-based Internal
  Operations surface. The two native mobile paths do not absorb the browser trust domain.
- Both stores are planned, but not necessarily simultaneously. The horizon is first
  release plus 24 months.
- The planned cadence is four release windows per year, with safety correction as needed.
  Binary, web, backend, database, content, configuration, and emergency authorities stay
  distinct under I4. No OTA/code delivery mechanism is approved.

### 2.2 Equal MAU workload

The following arithmetic translates the frozen fixture into monthly volumes. It is not a
price estimate and does not include retries, backup copies, or a legal retention promise.
Storage and outbound are tracked separately.

| MAU tier | Required compact transfers/month | Required transfer ceiling | Optional media/month | User-photo uploads/month |
|---:|---:|---:|---:|---:|
| 1,000 | 2,000 transfers; up to 24,000 MB (about 24 GB decimal) | 12 MB each | 100 users × 100 MB = 10,000 MB (about 10 GB) | 500 × 3 MB = 1,500 MB (about 1.5 GB) |
| 10,000 | 20,000 transfers; up to 240,000 MB (about 240 GB) | 12 MB each | 1,000 × 100 MB = 100,000 MB (about 100 GB) | 5,000 × 3 MB = 15,000 MB (about 15 GB) |
| 50,000 | 100,000 transfers; up to 1,200,000 MB (about 1.2 TB) | 12 MB each | 5,000 × 100 MB = 500,000 MB (about 500 GB) | 25,000 × 3 MB = 75,000 MB (about 75 GB) |

Each MAU has two compact task-package transfers per month. Optional media is 10% of
MAU at 100 MB average transfer. User photos are 0.5 per MAU per month at 3 MB average upload; the worksheet observes
the resulting storage-cost horizon for 24 months without making a legal retention promise. These workload constants are
identical for every candidate.

### 2.3 Device, network and interruption cohorts

- Constrained Android: Android 10 / API 29, 64-bit, 4 GB RAM, 64 GB storage, 2 GB free.
- Main Android: Android 13 or newer, 6 GB RAM, 128 GB storage.
- Oldest iPhone cohort: iOS 16.4-capable. Current iPhone cohort: generally available
  current standard non-Pro device.
- Exact branded devices, OS patch levels, procurement/borrow status, and tester
  population are UNRESOLVED. The Android API 29 and iOS 16.4 values are fixture floors,
  not completed product-support evidence.
- Network profiles are stable Wi-Fi at 50 Mbps, cellular at 10 Mbps, and constrained
  network at 1 Mbps / 300 ms / 5% packet loss. Loss may occur during transfer and sync.
- The interruption fixture includes 72 hours offline; background and locked states;
  incoming call; process kill and restart; clock change; and restore before reconnect.

### 2.4 Task package and local stress fixture

- One motorcycle/variant and one active task are in scope.
- Required task content is text, warnings, diagrams, and complete safe-stop/recovery
  closure. The required compact package has a maximum transfer target of 12 MB.
- Optional high-resolution media is separate and may be up to 150 MB. Size is shown before
  transfer. An unrelated 2 GB catalog must not download by default.
- Offline cache target is 250 MB excluding user photos and history. A transfer larger than
  25 MB over cellular requires explicit user choice.
- Temporary space must account for old and new package copies and atomic verification.
- Normal/stress local fixtures are 3/10 motorcycles, 250/2,000 history records,
  50/500 user photos at 3 MB each, 100/1,000 notes, 20/200 pending offline changes,
  and 3/30 conflicts.
- Failure injections include duplicate operation, partial upload, corrupt package,
  interrupted database change, source correction, content withdrawal, and safety recall.
  No silent discard, overwrite, or display of partial success is allowed.

### 2.5 Privacy, authority and evidence controls

- Private notes and photos stay private. Private, shared, community, and official
  contexts remain distinct.
- Analytics are minimal. A restored or cloned cache cannot create authority, entitlement,
  or safety eligibility. Export is a disclosure that cannot be remotely retracted.
- Deleting one copy does not erase independent evidence or history. Exact retention and
  deletion periods are UNRESOLVED.
- The mobile clients cannot become the authority for safety content, recall state,
  entitlement, identity, or ownership. Those authorities require explicit API/operations
  contracts and release provenance.
- AI may implement, review, or validate bounded work, but cannot be the automatic
  authority for safety content. Real devices, assistive technology, qualified safety
  review, store accounts, and legal/tax/payment authorities are external obligations.

### 2.6 Approved cost constants and no-cost assumptions

These are controlled fixture constants, not a native-candidate price quote:

- Planning has no incremental spend assumption for the comparison stage.
- Development preparation may use local/free/open-source paths or a capped free tier only
  when caps, alerts, export, and exit are evidenced.
- Google Play Console registration is USD 25 one time. Apple Developer Program membership
  is USD 99 per membership year. The approved 24-month store-only baseline is
  USD 124–223 depending on whether one or two Apple membership payments fall in the
  horizon, before tax and currency conversion.
- Device access is preferably borrowed or otherwise controlled. Mac, CI, native toolchain,
  hosted build, lab, and specialist amounts are UNRESOLVED.
- No unlisted subscription, hosted service, messaging provider, analytics provider, or
  OTA service is pre-approved. A free label never means zero cost.

## 3. Candidate Architecture Boundary

This is a responsibility and evidence boundary only. It contains no implementation code
and does not claim that either native path or any adapter exists.

### 3.1 Two native UI/application delivery paths

The candidate deliberately has two independent mobile delivery paths:

| Path | UI reference | Application/domain path | Native authority |
|---|---|---|---|
| Android | Kotlin Android application. Jetpack Compose is the reference UI candidate, with Android Views as a platform-native fallback/interop path; exact Compose library/compiler versions are UNRESOLVED. | Kotlin modules for domain state, validation, persistence adapters, task/checkpoint logic, network/reconciliation adapters, and platform lifecycle. Android components are not allowed to be the source of durable domain state. | Android SDK, Android lifecycle, storage, permissions, accessibility, signing, Gradle/AGP, and Play release authority. |
| iOS | Swift application. SwiftUI is the reference UI candidate, with UIKit/UIViewController interoperability for platform-specific controls; exact UI toolkit choice and deployment settings are UNRESOLVED. | Swift modules for domain state, validation, persistence adapters, task/checkpoint logic, network/reconciliation adapters, and scene/app lifecycle. SwiftUI/UIKit view state is not the source of durable domain truth. | Apple SDKs, UIKit/SwiftUI, Foundation, privacy permissions, accessibility, signing, Xcode/SPM, and App Store/TestFlight release authority. |

The UI choices above are reference directions, not a hidden third shared framework.
Their package/toolchain resolution, native accessibility behavior, and parity evidence
must be closed before either path is accepted. The two paths require duplicated screen,
state, lifecycle, test, accessibility, and release work unless a portable contract or
fixture is explicitly shared.

### 3.2 Portable domain contracts and authority

- Portable data schemas, content manifests, safety-state vocabulary, acceptance fixtures,
  provenance records, and API contracts may be shared as files or generated artifacts.
  No Kotlin Multiplatform core, generated cross-platform business logic, or shared mobile
  UI is assumed in this fully native reference.
- Android and iOS each implement the same domain/state contract locally. Safety-step
  state, validation, conflict rules, entitlement, content capability, recall validity,
  migration, and synchronization remain Kavriva application/domain responsibilities.
- Internal Operations owns controlled content intake, review, correction/withdrawal/recall,
  capability metadata, provenance, and publication decisions. Mobile clients consume a
  versioned/classed contract and never publish official safety truth from local state.
- API/authentication, profile ownership, sync, conflict resolution, entitlement, audit,
  media storage, deletion, and notification delivery are external/product architecture
  choices. No provider or backend schema is selected here.

### 3.3 Local persistence, encryption, migration and backup

- Android reference: Room over SQLite is the preferred structured-data direction;
  Android’s official page currently documents Room3 3.0.3 examples. The exact Room/SQLite
  dependency graph, version, driver, schema export, encryption, and migration plan remain
  UNRESOLVED. Android app components and processes can be recreated or killed, so durable
  state must be outside Activity/UI objects (A5, A6, A10).
- iOS reference: Core Data over an app-private persistent store is the proposed iOS16.4
  compatible direction. Apple documents model versioning and migration, but the exact
  model, store configuration, encryption, migration stages, and backup policy are
  UNRESOLVED. SwiftData is not assumed for the iOS16.4 fixture floor.
- Android Keystore and iOS Keychain hold protected keys/references, not arbitrary history
  or current entitlement. Android Auto Backup includes app data by default with documented
  inclusion/exclusion and quota behavior; iOS Data Protection and App Sandbox govern
  protected files. Data-class-specific backup/exclusion, clone, restore, key rotation,
  key loss, account re-authentication, and retention policies remain app/authority work
  (A8, A9, P5, P6).
- Neither platform primitive is treated as the sole source of truth. A future design must
  separate cache/content, core history, private notes, profile binding, trust/eligibility,
  and key material; quarantine restored/replayed authority metadata; preserve provenance;
  and provide visible recovery when a key is unavailable.

### 3.4 Offline package, media and transfer boundary

- Android uses app-private files, scoped storage, Storage Access Framework/Photo Picker,
  and optionally WorkManager for non-urgent durable work. iOS uses app sandbox/FileManager,
  UIDocumentPicker/PhotosUI, and URLSession background transfers where appropriate.
- Both paths require an app-owned package manifest with content identity, version,
  capability, safety status, provenance, integrity result, transfer checkpoint, and
  cleanup decision. Platform file APIs do not supply Kavriva’s required/optional media,
  recall, signature, atomic old/new commit, or eviction semantics.
- Required compact text/warnings/diagrams/recovery is separate from optional high-resolution
  media and user evidence. A partial, canceled, corrupt, or process-killed transfer stays
  visibly incomplete and cannot be displayed as current.
- Foreground reconciliation is the correctness path. Android WorkManager and iOS
  URLSession/BGTaskScheduler may optimize transfer/refresh, but OS scheduling, termination,
  network policy, battery constraints, and delivery timing are not guaranteed.

### 3.5 Camera, file, share and media boundary

- Android native capture is Camera2/permission-controlled capture, with Photo Picker or
  Storage Access Framework for user-selected media and FileProvider/Content URI rules for
  user-visible sharing. iOS native capture is AVFoundation; PhotosUI/Photos and
  UIDocumentPicker provide selection/import; system share/export uses Apple UI/document
  APIs.
- Permission prompts, purpose strings, metadata minimization, temporary-file cleanup,
  evidence classification, URI/bookmark lifetime, process-death recovery, upload
  idempotency, and deletion are app/privacy/safety responsibilities.
- Denial, missing hardware, malformed file, low storage, or failed upload must produce a
  visible manual/no-media or safe-hold path. A native permission grant is not proof that
  evidence is trusted or uploaded.

### 3.6 Notifications, deep links and background execution

- Android uses NotificationManager/channels and App Links/Intents; remote FCM delivery is
  not selected. iOS uses UserNotifications/APNs and Universal Links/Associated Domains;
  a remote provider is not selected. Local or remote notification delivery is not timely
  safety authority.
- A deep link must re-check current authentication, entitlement, content capability,
  recall, ownership, and privacy before opening an authority-sensitive screen.
- Android WorkManager 2.11.2 is the documented current official example for persistent
  scheduled work; iOS URLSession background configuration and BGTaskScheduler are native
  routes. Exact dependency resolution and workload policy are UNRESOLVED.
- Incoming call, lock, background, process kill, suspension, scene disconnect, and OS
  termination require durable checkpoint/recovery behavior. Background work is an
  optimization, never a correctness prerequisite.

### 3.7 Accessibility semantics and platform exceptions

- Android Compose semantics/roles/state/traversal or native View accessibility APIs and
  iOS SwiftUI accessibility modifiers/UIKit UIAccessibility are the direct platform
  affordances. They allow explicit labels, state, focus, actions, and announcements.
- Turkish warning, unexpected-state stop, active-step, readiness, and safe-recovery
  semantics remain Phase-3 product/safety truth. Largest text/reflow, contrast/non-color
  status, reduced motion, switch/voice control, reduced dexterity, focus order, and
  announcement timing require platform-specific work.
- Device/API availability, Compose semantics inspection, or SwiftUI defaults is not a
  VoiceOver/TalkBack acceptance pass. Real iOS and Android devices with actual assistive
  technology are mandatory later evidence.

### 3.8 Build, signing, release and incident boundary

- Android and iOS have independent source trees, build graphs, signing identities,
  artifact provenance, CI/host paths, test matrices, staged store releases, and incident
  pause controls. A shared fixture/schema does not make their artifacts interchangeable.
- Android reference uses Gradle/AGP/Android Studio/JDK/SDK/NDK as snapshot in Section 1.
  iOS reference uses Xcode/Swift/SDK/macOS as snapshot in Section 1. Exact project
  configuration, SPM/Gradle dependencies, certificates, keys, CI, and artifact retention
  are UNRESOLVED.
- Store authorities own legal identity, account roles, tester populations, signing,
  staged release, submission, and emergency controls. The app team must produce an
  immutable exact artifact, dependency lock, SBOM, provenance, and independent verification
  for each platform.
- Binary, web, backend, database, content, configuration, and emergency suspension
  authorities remain separate. A safe compatible artifact is the only rollback target;
  an irreversible data migration requires forward recovery rather than a pretend binary
  rollback.
- OTA/code delivery is excluded. No remote JavaScript, Swift, Kotlin, or native update
  path may bypass store review, binary provenance, safety correction, or DEBATE-005.

### 3.9 Portable truth and framework-exit boundary

Portable artifacts are content/data/history/provenance schemas, media and classified
exports, acceptance fixtures and oracles, API contracts, identity/ownership mapping,
design tokens, Turkish copy, accessibility intent, migration records, SBOM/provenance
records, and the evidence/release history.

Platform-bound artifacts are Android Kotlin/Compose/View code, Gradle/AGP/SDK/NDK
configuration, Android permissions/Keystore/WorkManager/App Links, Swift/SwiftUI/UIKit
code, Xcode/Swift Package Manager configuration, iOS entitlements/Keychain/URLSession/
Universal Links, signing keys, and store packaging.

An exit route therefore requires a second Android and/or iOS implementation against the
same portable contracts and fixtures, explicit data migration, coexistence with the old
client, revalidation of current authority, staged store delivery, and closure only after
real-device/AT/safety/release evidence. Direct native access is not an exit plan.

## 4. Native, Dependency and Toolchain Closure

Native reach is baseline work for this candidate, not an exception. Every row must have an
exact dependency or platform API, primary/backup owner, OS/toolchain floor, threading and
lifecycle limits, accessibility impact, fallback, EOL/security response, and release
provenance. A package or platform API being available does not make the row PASS.

| Capability | Built-in/framework path | Dependency/plugin/toolchain snapshot | Native code/skill required | Lifecycle/threading constraints | Accessibility impact | Fallback/replacement | EOL/security owner | Status |
|---|---|---|---|---|---|---|---|---|
| Android application shell/UI | Kotlin Android app; Compose reference with Views interop/fallback | Android SDK API 36; Android Studio Quail 4 2026.1.4; AGP 9.0.1; Gradle 9.1.0; KGP runtime 2.2.10; JDK 17; [A1, A2, A4](https://developer.android.com/studio/releases) | Android/Kotlin and Compose/Views expertise; direct native implementation | Activity/process can be recreated or killed; durable state must not live only in UI components | Compose semantics or View accessibility tree, traversal, state and focus require explicit mapping | Use the other native UI toolkit within Android; hold unsafe/inaccessible surface | Android/Kotlin/Compose owners and security response UNRESOLVED | HELD |
| iOS application shell/UI | Swift iOS app; SwiftUI reference with UIKit interoperability/fallback | Xcode 26.4; Swift 6.3; iOS 26.4 SDK; macOS Tahoe 26.2; [P1](https://developer.apple.com/documentation/xcode-release-notes/xcode-26_4-release-notes) | Swift/UIKit/SwiftUI and scene lifecycle expertise; direct native implementation | Scene/app lifecycle, suspension, disconnection, memory pressure and OS termination | SwiftUI accessibility modifiers/UIKit UIAccessibility; real VoiceOver evidence required | Use the other native UI toolkit within iOS; hold unsafe/inaccessible surface | Apple/Swift/Xcode/SPM owners and security response UNRESOLVED | HELD |
| Portable domain/data contract | Language-neutral schemas, manifests, fixtures and API contracts | No shared executable mobile library selected; exact schema format/version UNRESOLVED | Contract/domain review on both paths; no KMP assumption | Each client owns lifecycle adapter while preserving shared state semantics | Error/unknown/conflict/safe-hold vocabulary must be identical and accessible | Portable contract is the replacement path; no silent platform divergence | Product/domain owner, safety/content owner, schema/security owner UNRESOLVED | HELD |
| Android structured local data | Room over Android SQLite; app-owned schema/checkpoints/migrations | Official Android docs currently show Room3 3.0.3 examples; exact Room/SQLite driver/version/SBOM UNRESOLVED; [A5, A10](https://developer.android.com/training/data-storage/room) | Kotlin database/migration and recovery skill | Database work off main thread; Activity/process may die; migration must be durable and data-preserving | Accessible migration, conflict, stale, unknown and failure states | Read-only safe hold; server/profile recovery; replacement local schema with forward migration | Database schema/key owner and Android security reviewer UNRESOLVED | HELD |
| iOS structured local data | Core Data persistent store; Swift model adapters | Core Data is Apple SDK; exact model/store options/version/migration graph UNRESOLVED; [P7](https://developer.apple.com/documentation/coredata/) | Swift/Core Data migration and recovery skill | Context/queue confinement, scene lifecycle, background import, process termination | Accessible migration/conflict/stale/unknown states; UIKit/SwiftUI bridge review | Read-only safe hold; forward migration; export/replacement store | iOS data owner and Apple security reviewer UNRESOLVED | HELD |
| Android key and secret storage | Android Keystore, non-exportable key material and authenticated use | Android platform API; exact key algorithm, alias, attestation, backup exclusion and rotation UNRESOLVED; [A8](https://developer.android.com/privacy-and-security/keystore) | Android security/Keystore expertise | Key availability varies with lock/auth/device state; never use as general database | Visible re-auth/key-loss/recovery states | Quarantine authority metadata and re-authenticate; no cache-created authority | Android security/identity owner UNRESOLVED | HELD |
| iOS key and secret storage | Keychain Services plus file Data Protection | Apple Security/UIKit APIs; exact accessibility class, access group, sync/rotation and file protection UNRESOLVED; [P5, P6](https://developer.apple.com/documentation/security/keychain-services) | iOS security/Keychain/Data Protection expertise | Keychain/file access differs with lock, backup, uninstall and trust context | Accessible key-loss/re-auth/recovery and protected-data states | Quarantine and re-authenticate; no exported platform key assumption | iOS security/identity owner UNRESOLVED | HELD |
| Android camera/photo | Camera2 and runtime permissions; Photo Picker/MediaStore for selection | Android platform APIs; CameraX is not assumed; exact permission/manifest and media policy UNRESOLVED; [A10, A13](https://developer.android.com/training/permissions/requesting) | Android camera/permission/media skill | Camera/session lifecycle, permission denial, process death, URI grants | Permission, capture, error, classification and retry announcements | Manual SAF import/no-media path; hold evidence-dependent step | Android media/privacy owner and security response UNRESOLVED | HELD |
| iOS camera/photo | AVFoundation capture; PhotosUI/Photos selection | Apple SDK APIs; exact capture/session/photo-library policy UNRESOLVED; [P8](https://developer.apple.com/documentation/avfoundation/requesting-authorization-to-capture-and-save-media) | Swift AVFoundation/PhotosUI and permission skill | Capture session must stop/release on lifecycle/interruption; process death and permission changes | Permission purpose, capture state, error and classification need VoiceOver review | UIDocumentPicker/manual import/no-media path; hold evidence-dependent step | iOS media/privacy owner and security response UNRESOLVED | HELD |
| Android file import/export/share | Storage Access Framework, content URIs, FileProvider, system chooser | Android platform APIs; exact URI grant, format, provider and export policy UNRESOLVED; [A10](https://developer.android.com/training/data-storage/shared/documents-files) | Android URI/file-provider/privacy skill | URI may expire; process death/copy failure/cleanup; never trust unvalidated path | Accessible picker, unsupported-file, disclosure and share completion states | Retry/manual supported format; classified local export; hold unverified import | Android file/privacy owner UNRESOLVED | HELD |
| iOS file import/export/share | UIDocumentPicker, FileManager, sandbox and system share/document APIs | Apple SDK APIs; exact bookmark/file-protection/share policy UNRESOLVED; [P6](https://developer.apple.com/documentation/security/protecting-user-data-with-app-sandbox) | Swift file/document/share/privacy skill | Sandbox paths, security-scoped URLs, process death, disclosure outside app | Accessible picker, disclosure warning and share completion states | Retry/manual supported format; classified export; hold unverified import | iOS file/privacy owner UNRESOLVED | HELD |
| Scoped package/download/upload | Android WorkManager/user-initiated transfer plus files; iOS URLSession background transfers | Android WorkManager 2.11.2 documented example; iOS URLSession/BGTaskScheduler APIs; exact package manifest/hash/signature/resume policy UNRESOLVED; [A7](https://developer.android.com/develop/background-work/background-tasks/persistent), [P4](https://developer.apple.com/documentation/foundation/downloading-files-in-the-background) | Both native background-transfer and app-owned integrity/recovery skill | Work is deferrable/interruptible; foreground reconciliation and durable checkpoints are required | Size, progress, pause/cancel, incomplete/integrity/hold state must be announced | Retry verified checkpoint; retain last safe package; block corrupt/stale package | Content/package integrity, Android/iOS background, security owners UNRESOLVED | HELD |
| Android notifications/deep links | NotificationManager/channels; App Links/Intents | Android platform APIs; FCM/provider not selected; exact link association/config UNRESOLVED; [A12](https://developer.android.com/training/app-links/about) | Android notification/link/security skill | Delivery not guaranteed; cold/background link must revalidate authority | Permission/channel, destination focus and stale/hold messages | In-app foreground status; safe home/read-only route | Android store/privacy/identity owner UNRESOLVED | HELD |
| iOS notifications/deep links | UserNotifications/APNs; Universal Links/Associated Domains | Apple platform APIs; APNs provider and exact entitlements/domain association UNRESOLVED; [P10, P11](https://developer.apple.com/documentation/usernotifications) | iOS notification/link/security skill | Delivery not guaranteed; scene may connect in background; link must revalidate authority | Notification permission, content, focus and stale/hold states | In-app foreground status; safe home/re-auth route | iOS store/privacy/identity owner UNRESOLVED | HELD |
| Android background reconciliation | WorkManager/JobScheduler boundary; foreground remains correctness path | androidx.work work-runtime-ktx 2.11.2 documented example; exact constraints/retry policy UNRESOLVED; [A7](https://developer.android.com/develop/background-work/background-tasks/persistent/getting-started) | Android scheduler/lifecycle skill | OS, vendor, battery and process restrictions; retry result and idempotency app-owned | Deferred/failed/stale state accessible | Foreground reconciliation and safe hold | Android lifecycle/security owner UNRESOLVED | HELD |
| iOS background reconciliation | URLSession background sessions/BGTaskScheduler; foreground remains correctness path | Apple SDK APIs; exact background modes, session ID, retry and task policy UNRESOLVED; [P3, P4](https://developer.apple.com/documentation/foundation/urlsession) | iOS scene/background/network skill | Suspension/termination and discretionary scheduling; completion/retry app-owned | Deferred/failed/stale state accessible | Foreground reconciliation and safe hold | iOS lifecycle/security owner UNRESOLVED | HELD |
| Android accessibility | Compose semantics or Android View accessibility services | Compose/Views choice and exact dependency graph UNRESOLVED; [A11](https://developer.android.com/develop/ui/compose/accessibility) | Android accessibility and TalkBack testing skill | Custom semantics/focus/traversal may diverge from visual tree | Labels, roles, state, actions, large text, focus, non-color status | Native standard control or safe hold; no visual-only proof | Qualified AT tester and Android reviewer UNRESOLVED | HELD |
| iOS accessibility | SwiftUI accessibility modifiers and UIKit UIAccessibility | SwiftUI/UIKit choice and exact semantic mapping UNRESOLVED; [P9](https://developer.apple.com/documentation/swiftui/accessibility-fundamentals) | iOS accessibility and VoiceOver testing skill | Scene/focus transitions and custom controls need explicit handling | Labels, values, traits, focus, large text, non-color status | Native standard control or safe hold; no visual-only proof | Qualified AT tester and iOS reviewer UNRESOLVED | HELD |
| Build and artifact provenance | Two independent native Gradle and Xcode build graphs | Android Studio/AGP/Gradle/JDK/SDK/NDK and Xcode/Swift/macOS snapshots above; exact lockfiles/SPM/Gradle graph/SBOM UNRESOLVED | Android and iOS build/signing/release expertise | Native dependency/config/OS change requires platform rebuild and two-platform evidence | Release evidence must include AT/device results | Local reproducible path; hosted CI only after cap/export/exit evidence | Signing custody, CI/artifact security, upgrade owner UNRESOLVED | HELD |
| Store submission and staged release | Play Console and App Store Connect; separate account roles | Current store/build rules are dynamic; Android target API and Apple upload floor must be rechecked; [P2](https://developer.apple.com/help/app-store-connect/manage-builds/upload-builds) | Store/legal identity, signing, tester, staged rollout, incident skill | App Store/Play processing/review and staged rollout are external; no downgrade after unsafe migration | Device/AT evidence attached to each platform artifact | Hold release, retain safe artifact, forward-correct | Legal owner, store account holder, release verifier UNRESOLVED | HELD |
| OTA/code delivery | Explicitly excluded | No OTA package/service selected or approved | No OTA skill is a mitigation | No remote code/config path bypasses release authority | No emergency path may bypass safety/accessibility evidence | Store-delivered compatible binary or separately governed content/config only | Release governance owner; introducing OTA would be rejected under I4 | EXCLUDED / N-A |
| Backend/auth/sync/telemetry | No native default; explicit API/provider contracts | No provider or paid service selected; exact auth, DB, storage, crash and analytics dependencies UNRESOLVED | Backend, privacy, security, operations and migration skills on both paths | Server authority, idempotency, conflict, recall, deletion and audit are outside native SDKs | Client exposes stale/unknown/conflict/permission states | Foreground retry, read-only hold, provider replacement through portable contracts | Product/backend/privacy/security owners UNRESOLVED | HELD |

### 4.1 Closure decision for this partial draft

The native baseline has the clearest direct platform API path, but it also has two complete
application/UI/toolchain/release surfaces. The snapshot and official platform affordances do
not close the candidate. The following remain missing:

- exact Android and iOS project dependency graphs, lockfiles, SPM/Gradle versions, hashes,
  SBOM, generated artifacts, signing provenance, and reproducible build evidence;
- final Compose/Views and SwiftUI/UIKit UI choices, parity contracts, and independent
  Android/iOS owners;
- database/file encryption, key hierarchy, backup/restore/clone, migration, and recovery
  policy on each platform;
- package integrity/recall, API/auth/sync/conflict/entitlement/content contracts, and
  provider-independent exit path;
- exact device/OS patch cohorts, real-device and assistive-technology capacity, Mac/CI
  access, store/legal identity, signing custody, tester population, and safety reviewer;
- dynamic Apple/Google build/store floors at each release, security/EOL response, support
  capacity, and all candidate-caused external cash amounts.

Accordingly, Section 4 is PARTIAL DRAFT / INCOMPLETE / HELD. It does not authorize a
framework choice, native implementation, device purchase, CI/hosted build, store release,
or OTA service.

## 5. Equal S1-S15 Scenario Record

The records below use the controlled template fields. Fully native means every critical
presentation, lifecycle, platform-service adapter, test and release path is implemented
separately for Android and iOS. Portable schemas and fixtures do not remove that duplicated
parity burden. All results are HELD: no code, lockfile, signed artifact, physical-device
run, independent accessibility oracle, safety review or accountable delivery capacity is
present in this dossier.

### S1 — First value without an account

- authoritative starting state: No account, server authority or prior local profile; the user selects one motorcycle/variant and can view the approved local starting surface.
- allowed transition: Persist the selection durably, show account-registration/skip choice, and later offer an explicit migration preview; neither native path may silently merge or overwrite history.
- candidate mechanism: Android Kotlin state/repository and iOS Swift state/repository implement the same portable contract and Turkish copy keys; UI state is not durable truth.
- official evidence: Android architecture/lifecycle guidance A5/A6 and Apple lifecycle guidance P3 separate app/lifecycle responsibilities; internal authority remains I1/I2.
- reasoned inference: Fully native paths can optimize each platform's first-use UX, but duplicate account/migration implementations create parity and drift work.
- dependency-specific evidence: Android Room and iOS Core Data are only reference directions; no auth, database or migration dependency is locked.
- unresolved facts: Anonymous identity, schema, account bind/idempotency, backup, deletion, migration conflict policy and both platform storage implementations.
- user-visible result: Useful selected-task value without an account, with identical Turkish meaning and platform-appropriate presentation of local versus authoritative data.
- failure/hold behavior: If either platform cannot prove durable write or migration preview, hold that transition and retain the last durable state.
- recovery path: Reopen last durable checkpoint, revalidate authority after sign-in and quarantine ambiguous records; do not let one platform claim success when the other is unresolved.
- shared-system obligation: Product copy, authorization, history/provenance, deletion and account semantics are common.
- candidate-attributable work: Two native state/repository implementations, two migration UIs, parity fixtures and cross-platform contract review.
- accountable AI/external owner: AI Android and iOS implementers; product/account owner and independent data reviewer.
- required later real-device evidence: Fresh install, no-account use, force-close/restart, sign-in migration, duplicate submit, storage pressure and restore/clone on both devices.
- residual risk: Separate native code can produce inconsistent migration or privacy wording even when schemas match.
- result: HELD.

### S2 — Compact offline teaching package

- authoritative starting state: Online authority selected one motorcycle/task closure; required compact package is at most 12 MB, optional media at most 150 MB, unrelated 2 GB content is not requested.
- allowed transition: Show size, confirm cellular transfer above 25 MB, stage manifest/digest, resume, verify and atomically promote only a complete package.
- candidate mechanism: Android Kotlin package state plus WorkManager/files; iOS Swift package state plus URLSession/FileManager; each native UI renders the same package contract.
- official evidence: Android persistent work A7 and Apple background URLSession P4 document platform-specific scheduling/transfer behavior.
- reasoned inference: Native APIs provide direct reach, but two independent transfer state machines, integrity checks and retry paths must remain behaviorally identical.
- dependency-specific evidence: WorkManager 2.11.2 is an official documented example; exact Android/iOS dependencies, hash/signature and transfer provider are not selected.
- unresolved facts: Package schema, digest/signature, storage reservation, retries, quotas, background modes, cancellation, atomic promotion and lockfiles.
- user-visible result: Required safety/recovery material is offline; optional media is visibly optional and progress/paused/failed states are truthful and accessible on each platform.
- failure/hold behavior: Partial, corrupt, expired or low-space package is never actionable; the affected native path holds and explains recovery.
- recovery path: Resume/restart foreground, clean verified temporary artifacts, recheck generation and promote once; never silently download the full catalog.
- shared-system obligation: Scoped delivery, safety closure, content generations, storage limits and no OTA are common.
- candidate-attributable work: Duplicate Android/iOS transfer orchestration, integrity code, storage handling, progress UI and native background constraints.
- accountable AI/external owner: AI transfer implementers for both paths; Android background, iOS URLSession, content and release owners.
- required later real-device evidence: All network profiles, Doze, iOS expiration, low storage, process kill, lock/call, resume, duplicate/corrupt package and 12/150 MB boundaries.
- residual risk: Native parity drift can make one platform expose an incomplete package while the other reports completion.
- result: HELD.

### S3 — Interrupted physical work

- authoritative starting state: Active task has a last durable committed checkpoint; lock, incoming call, process kill or restart interrupts the work.
- allowed transition: Restore only the last durable checkpoint, mark in-flight physical state unknown/partial, stop safely and require explicit revalidation.
- candidate mechanism: Android journal/checkpoint and Activity/process adapters; iOS journal/checkpoint and scene/app adapters; both consume the same recovery contract.
- official evidence: Android process lifecycle A6 and Apple app/scene lifecycle P3 show different lifecycle boundaries and termination behavior.
- reasoned inference: Fully native code can use each OS's correct callbacks, but neither callback proves an uncommitted physical action was completed.
- dependency-specific evidence: Room/Core Data remain unlocked reference directions; no recovery journal or transaction library is selected.
- unresolved facts: Durable journal schema, commit boundary, physical semantics, native termination behavior, recovery copy and kill oracle.
- user-visible result: Turkish safe-stop, unknown/partial and revalidation states are explicit on Android and iOS; a restored screen never implies safe continuation.
- failure/hold behavior: Missing/inconsistent checkpoint holds the task; no silent replay, duplicate completion or inferred physical state.
- recovery path: Reopen last committed state, inspect current physical condition, reconcile authority and record explicit recovery outcome independently on each platform.
- shared-system obligation: Conservative recovery, no silent overwrite/loss, audit and safety authority apply equally.
- candidate-attributable work: Two checkpoint/lifecycle integrations, two recovery UIs and two native process/interruption test suites.
- accountable AI/external owner: AI recovery implementers; qualified safety owner and Android/iOS lifecycle reviewers.
- required later real-device evidence: Lock/call/background/process kill/restart, low memory, interrupted database write, camera interruption and clock-change tests on both platforms.
- residual risk: Separate lifecycle and journal code can disagree on the last committed point.
- result: HELD.

### S4 — Offline recall or dormant guidance

- authoritative starting state: Valid compact guide is downloaded and the user is offline; no new server recall or correction is observable.
- allowed transition: Teach from last valid generation, show age/scope and hold actions whose current validity is unknown; reconnect before treating content as current.
- candidate mechanism: Android and iOS each implement versioned manifest/recall state, local provenance and foreground reconciliation using the same contract.
- official evidence: Android Doze A7 defers network/jobs; Apple background execution P3/P4 is limited/system-controlled. Notifications are not a guaranteed authority.
- reasoned inference: Fully native notifications can follow platform conventions, but neither platform can create current recall authority offline.
- dependency-specific evidence: FCM/APNs providers are not selected; local notification APIs are platform surfaces only.
- unresolved facts: Recall TTL/priority, offline validity, clock policy, correction/withdrawal semantics, notification provider and generation API.
- user-visible result: Stale/dormant status, scope, warning and safe-stop/recovery guidance are clear Turkish content on both native paths.
- failure/hold behavior: Withdrawn, expired, incompatible or unknown generation holds the affected action and preserves verified safe-stop material.
- recovery path: Reconnect/re-authenticate, fetch current generation, reconcile history and preserve old record as provenance.
- shared-system obligation: Safety truth, recall, publication/revocation and notification policy are framework-neutral.
- candidate-attributable work: Duplicate generation state, stale UI, notification/deep-link reconciliation and platform-specific accessibility announcements.
- accountable AI/external owner: AI content-state implementers; qualified safety/content publisher and authorization owner.
- required later real-device evidence: 72-hour offline, clock change, force-close, background restriction, notification denial, cold links and correction/withdrawal.
- residual risk: Android and iOS may show different stale wording or timing while sharing a version number.
- result: HELD.

### S5 — Old client with changed meaning

- authoritative starting state: An older Android or iOS signed client encounters a new field, changed unit/meaning or unsupported server capability.
- allowed transition: Negotiate capability/content generation, render only known safe meaning and fail closed on unknown safety-critical meaning.
- candidate mechanism: Portable schemas/capability table plus separate Kotlin and Swift adapters and native compatibility UI.
- official evidence: Android/iOS store artifacts and platform SDKs have independent release paths; A1-A4 and P1-P2 establish toolchain/store boundaries.
- reasoned inference: Separate native code allows platform-specific compatibility behavior but doubles the old/new test and rollout matrix.
- dependency-specific evidence: Android and iOS dependency locks/build graphs are not present; no automatic cross-platform compatibility is provided by native SDKs.
- unresolved facts: Capability negotiation, schema evolution, minimum-version policy, fallback, rollout pause and rollback refusal.
- user-visible result: Compatible/needs-update/held state is explicit and never invents interpretation of a safety field.
- failure/hold behavior: Unknown critical field or incompatible generation blocks the affected path; known portable history remains scoped.
- recovery path: Staged platform releases, server compatibility window, forward migration and explicit update; no OTA binary.
- shared-system obligation: API/content versioning, store rollout and fail-closed safety are common.
- candidate-attributable work: Duplicate Kotlin/Swift serializers, capability UI, parity fixtures and two release matrices.
- accountable AI/external owner: AI release/data implementers; API/content owner, safety reviewer and Android/Apple store custodians.
- required later real-device evidence: Old/new client pair on both stores, changed fields, forced update, offline queue, rollback refusal and staged rollout.
- residual risk: One platform may accept a field the other holds, causing unsafe cross-platform meaning drift.
- result: HELD.

### S6 — Local profile and history conflict

- authoritative starting state: Local notes/history and server profile differ after offline edits, duplicate submission, account migration or restore.
- allowed transition: Show record/operation IDs and conflict preview, apply deterministic idempotent operations, retain provenance and request explicit resolution.
- candidate mechanism: Android Room/SQLite direction and iOS Core Data direction behind identical portable conflict contract; native UI resolves without silent overwrite.
- official evidence: Android Room A10 and Apple Core Data P7 document platform persistence/migration primitives, not Kavriva merge semantics.
- reasoned inference: Each platform can use its native database strengths, but schema/migration/concurrency parity becomes duplicated acceptance work.
- dependency-specific evidence: Room3 3.0.3 and Core Data are reference documentation snapshots only; exact versions, drivers and schema export are unresolved.
- unresolved facts: Merge precedence, operation IDs, tombstones, private-note policy, server conflict API, migration and restore interaction.
- user-visible result: Partial/conflict/needs-review is explicit, localized and accessible; no protected last-write-wins.
- failure/hold behavior: Ambiguous records quarantined and affected action held; duplicate retries do not create duplicate authority.
- recovery path: Retry idempotently, resolve explicitly, preserve audit/provenance and reconcile current authority.
- shared-system obligation: History, audit, conflict, deletion and privacy rules are common.
- candidate-attributable work: Two transaction/migration implementations, two conflict UIs, parity tests and backup/restore fixtures.
- accountable AI/external owner: AI data implementers; data authority, security/privacy reviewer and safety owner.
- required later real-device evidence: Offline edit/online merge, duplicate/partial upload, corrupt package, restore/clone, low storage and interrupted write on both OSes.
- residual risk: Separate native persistence engines can diverge in ordering, locking, migration or date behavior.
- result: HELD.

### S7 — Camera, file and evidence capture

- authoritative starting state: Permission denied/granted; native camera, photo-library picker or file import is attempted; process may die before return/upload.
- allowed transition: Explain permission, allow retry/skip, validate type/size/content, stage temporary item, bind idempotent operation and expose upload uncertainty.
- candidate mechanism: Android Camera2/Photo Picker/SAF and iOS AVFoundation/PhotosUI/UIDocumentPicker, each with its own native lifecycle and privacy handling.
- official evidence: Android camera permission/CameraX A13 and media APIs A10; Apple AVFoundation P8 and picker APIs document native boundaries.
- reasoned inference: Direct APIs avoid a cross-platform plugin, but duplicate permission, URI/bookmark, metadata and process-loss logic increases parity burden.
- dependency-specific evidence: CameraX is not selected; exact Android/iOS framework API configurations, scanners and upload libraries are unresolved.
- unresolved facts: MIME/size, EXIF/privacy, cleanup, permission edge cases, camera session behavior, security-scoped resources and upload idempotency.
- user-visible result: Capture/import denial/errors have Turkish retry/skip paths; invalid or untrusted media is quarantined on both paths.
- failure/hold behavior: Lost, partial, oversized, corrupt or unscanned evidence holds submission while retaining safe local recovery.
- recovery path: Native lost-data/resource recovery, retry/manual entry, clean only proven temporary copies and reconcile operation state.
- shared-system obligation: Privacy, evidence provenance, consent, retention and no-loss policy are common.
- candidate-attributable work: Separate Android/iOS capture/picker/privacy adapters, forms, permission states and process-death tests.
- accountable AI/external owner: AI media implementers; Android/iOS media specialists, privacy/security reviewer and evidence owner.
- required later real-device evidence: Permission deny/grant/reset, capture interruption, picker cancellation, process death, URI/bookmark expiry, 3 MB/50-500 photo fixtures, low storage and native AT.
- residual risk: Platform-native code reduces abstraction risk but makes parity and simultaneous correction more expensive.
- result: HELD.

### S8 — Accessible safety/readiness step

- authoritative starting state: Turkish critical step contains active instruction, readiness, warning, stop and recovery states.
- allowed transition: Focus/announce current state, expose labels/roles/actions, preserve order at largest text/non-color contrast and make stop/recovery operable with AT.
- candidate mechanism: Android Compose semantics or View accessibility; iOS SwiftUI accessibility or UIKit UIAccessibility; shared copy/state identifiers only.
- official evidence: Android Compose semantics A11 and Apple SwiftUI accessibility P9 document platform-specific accessibility mechanisms.
- reasoned inference: Fully native controls may maximize platform convention, but two semantic trees and two Turkish copy/layout implementations can diverge.
- dependency-specific evidence: Exact Android Compose/Views and iOS SwiftUI/UIKit choices are unresolved; defaults are not acceptance evidence.
- unresolved facts: Final toolkit, semantic grouping/traversal, Turkish wording, contrast, Dynamic Type/font scale, reduced motion and native-dialog behavior.
- user-visible result: Operator can perceive active, unsafe, stopped, unknown and recoverable states without color/gesture-only reliance on both platforms.
- failure/hold behavior: Any critical Android or iOS AT/largest-text failure holds release; no platform waiver.
- recovery path: Return focus to safe-stop/recovery, preserve state and provide text/manual alternative independently on each platform.
- shared-system obligation: Accessibility acceptance and Turkish-first safety copy are candidate-neutral.
- candidate-attributable work: Two semantics/focus implementations, two native surface handoffs and two AT test suites.
- accountable AI/external owner: AI Android/iOS UI implementers; independent human AT testers and qualified safety/content reviewer.
- required later real-device evidence: TalkBack/Voice Access and VoiceOver/Switch Control, largest text, contrast, reduced motion and all critical states.
- residual risk: Native parity may be safer per platform but increases duplicate defect surface and release coordination.
- result: HELD.

### S9 — Framework, library and toolchain upgrade

- authoritative starting state: Android reference and iOS reference snapshots in Section 1 are frozen; a new SDK, Compose/Views, SwiftUI/UIKit, library or store toolchain event is proposed.
- allowed transition: Reproduce lock/artifacts, review both dependency graphs, run scenarios/AT/device/release evidence, then stage or refuse upgrade with rollback criteria.
- candidate mechanism: Independent Android Gradle/SDK/NDK and iOS Xcode/Swift/SPM graphs with common portable fixtures and release checklist.
- official evidence: Android AGP/A1-A4 and Apple Xcode/App Store P1-P2 define independent version/build relationships.
- reasoned inference: Fully native avoids a cross-platform framework upgrade, but requires two upgrade streams and duplicated parity review.
- dependency-specific evidence: Android Room/WorkManager/Compose and iOS Core Data/URLSession/SwiftUI dependencies are not fully locked.
- unresolved facts: Upgrade cadence, security SLA, exact project locks, Mac/CI access, SDK deprecations, rollback artifacts and owner capacity.
- user-visible result: No silent native SDK/library change; staged/held outcome retains last accepted platform artifacts.
- failure/hold behavior: Any Android or iOS regression in safety, migration, AT, native service or release evidence holds that release.
- recovery path: Retain each accepted artifact, revert source/lock/toolchain together where safe or perform reviewed forward migration; no lossy binary rollback.
- shared-system obligation: Version policy, provenance, release cadence and safety correction are common.
- candidate-attributable work: Two upgrade plans, two dependency/SBOM diffs, two test matrices and parity reconciliation.
- accountable AI/external owner: AI Android/iOS upgrade implementers; native build specialists, security reviewer and store custodians.
- required later real-device evidence: Both comparison devices, critical flows, AT, signed staging artifacts, dependency/license/SBOM diff and migration/rollback rehearsal.
- residual risk: Independent native upgrades can leave Android and iOS on different semantic or security baselines.
- result: HELD.

### S10 — Mixed rollout of old/new clients

- authoritative starting state: Old/new Android and iOS signed binaries, schemas, content generations and server capabilities coexist.
- allowed transition: Capability negotiation, additive/forward migration and staged per-store artifacts; fail closed on unknown safety meaning.
- candidate mechanism: Common contract plus separate Android/iOS release graphs, serializers, migrations and native configuration.
- official evidence: App Store Connect and Google/Android release paths are separate (P2 and A1-A4); native SDKs do not coordinate server rollout.
- reasoned inference: Two native artifacts permit platform-specific rollout control but multiply compatibility, pause and rollback matrices.
- dependency-specific evidence: No complete Android/iOS lock, artifact graph or server capability manifest exists.
- unresolved facts: Compatibility window, minimum app version, schema negotiation, rollout pause, server contract and no-rollback conditions.
- user-visible result: Compatible work remains available; incompatible work shows update/hold path with no fabricated status.
- failure/hold behavior: Unknown/non-additive state held per task/record; one store can pause without erasing portable history.
- recovery path: Keep accepted artifacts, reconcile when compatible, forward-migrate with backup/provenance and release through approved stores.
- shared-system obligation: Mixed rollout and release integrity are candidate-neutral.
- candidate-attributable work: Duplicate serializer/capability adapters, two store rollout matrices, migration and parity checks.
- accountable AI/external owner: AI release/data implementers; backend/content owner, store custodians and safety reviewer.
- required later real-device evidence: Old/new installs on both stores, upgrade/downgrade refusal, offline queue, generation mismatch, cold links and staged rollout.
- residual risk: Android and iOS may expose different capability windows or migration errors.
- result: HELD.

### S11 — Low/mid-device and storage pressure

- authoritative starting state: Android API 29, 64-bit, 4 GB RAM, 64 GB storage and 2 GB free; local stress is 3/10 motorcycles, 250/2,000 records, 50/500 3 MB photos, 100/1,000 notes, 20/200 pending and 3/30 conflicts.
- allowed transition: Load selected compact content only, paginate/stream media, report pressure, evict cache only and preserve records/pending truth.
- candidate mechanism: Android and iOS each tune native lists/renderers, image decode, database and storage while honoring same fixture/contract.
- official evidence: Android architecture/performance boundaries A5 and Apple app lifecycle/background guidance P3 identify platform-specific runtime conditions.
- reasoned inference: Direct native controls may optimize each cohort, but measuring and maintaining two tuned implementations costs more parity effort.
- dependency-specific evidence: Android Compose/Views and iOS SwiftUI/UIKit choices, image/database packages and memory policy are unresolved.
- unresolved facts: Peak memory, startup, render/scroll budget, image policy, database indexes, cache eviction, thermal/battery and low-storage behavior.
- user-visible result: Honest progress and low-space/limited-media message; private notes/pending truth are never silently deleted.
- failure/hold behavior: Threshold breach holds optional work/release; cache eviction cannot discard pending or authoritative records.
- recovery path: Evict verified cache, reduce optional media, retry foreground and reconcile; preserve/export records before destructive migration.
- shared-system obligation: Fixture limits, privacy, retention, no-loss and safe degradation are common.
- candidate-attributable work: Separate Android/iOS performance implementations, image/data pagination, low-storage instrumentation and parity tests.
- accountable AI/external owner: AI performance implementers; Android/iOS specialists and data/security owner.
- required later real-device evidence: Cold/warm start, all local fixtures, low storage, thermal/rotation/background, image decode, DB recovery and largest-text accessibility.
- residual risk: Native optimization can produce platform-specific performance envelopes and inconsistent user guidance.
- result: HELD.

### S12 — Release, incident and pause

- authoritative starting state: Android and iOS staged artifacts are proposed; dependency, safety correction, store review or incident requires pause and impact assessment.
- allowed transition: Verify each source/lock/SBOM/signature/provenance, stage stores independently, pause rollout, identify affected generations and preserve artifacts.
- candidate mechanism: Two independent Gradle and Xcode release graphs, artifact manifests and a shared release-integrity checklist.
- official evidence: Android build/store A1-A4 and Apple Xcode/App Store P1-P2 require platform-specific build/signing/upload flows.
- reasoned inference: Fully native gives direct incident control per platform, but every correction, reviewer and signature must be coordinated twice.
- dependency-specific evidence: No CI, signing custody, platform lock, SBOM, attestation or artifact retention evidence is present.
- unresolved facts: CI/build provider, Mac access, certificates/keys, store review, artifact retention, incident authority and cost.
- user-visible result: Release/hold and affected content state are truthful on each platform; no optimistic updated claim.
- failure/hold behavior: Missing provenance, failed AT/device/safety evidence, signature issue or incident blocks the corresponding store release.
- recovery path: Retain last accepted artifact, revoke/limit affected content, issue reviewed correction and re-test both paths; no OTA binary path.
- shared-system obligation: Release integrity, safety correction, audit and pause controls are common.
- candidate-attributable work: Duplicate build/signing/release evidence, parity checklist, incident impact map and platform store operations.
- accountable AI/external owner: AI release implementers; Android/iOS build operators, security/safety reviewers and store authorities.
- required later real-device evidence: Signed staging artifacts on both stores, clean install/upgrade, pause/forward migration, provenance verification and incident communication.
- residual risk: The native baseline avoids one framework build failure but has two independent opportunities for missed correction.
- result: HELD.

### S13 — Privacy, collaboration and device trust

- authoritative starting state: Private notes/photos, shared/community and official/safety material have distinct scopes; device may be restored, cloned, lost or shared.
- allowed transition: Enforce scope/authorization, protect keys, label provenance, re-authenticate after restore/key mismatch and quarantine untrusted state.
- candidate mechanism: Android Keystore/files and iOS Keychain/Data Protection each implement the same portable scope/audit contract.
- official evidence: Android Keystore/backup A8-A9 and Apple Keychain/Data Protection P5-P6 define separate protected-data boundaries.
- reasoned inference: Native security APIs provide direct control, but two key hierarchies, backup exclusions and restore paths must remain aligned.
- dependency-specific evidence: No crypto/auth package or key wrapper is selected; exact key algorithms, access classes and backup rules are unresolved.
- unresolved facts: Key hierarchy/rotation, iOS/Android backup semantics, clone detection, ACLs, deletion/export and re-authentication.
- user-visible result: Private/shared/official labels, lock/re-auth/quarantine and disclosure warnings are explicit and accessible.
- failure/hold behavior: Key/authority mismatch holds protected action and preserves permitted safe metadata without plaintext exposure.
- recovery path: Re-authenticate, re-download/re-encrypt under current authority, preserve audit and revoke invalid device/session authority.
- shared-system obligation: Privacy, authorization, key loss, backup and deletion rules are product-wide.
- candidate-attributable work: Two native key/backup implementations, two scope UIs, restore/clone tests and parity review.
- accountable AI/external owner: AI security/data implementers; security/privacy reviewer, account authority and Android/iOS key specialists.
- required later real-device evidence: Backup/restore, clone, device transfer, key rotation/loss, uninstall/reinstall, permission reset and AT for scope labels.
- residual risk: Direct native access does not prevent divergent key/backup choices or stale restored authority.
- result: HELD.

### S14 — Entitlement, evidence and lifecycle change

- authoritative starting state: Entitlement, publication, correction, withdrawal, transfer or delete authority changes while an active task is foreground/background/offline.
- allowed transition: Preserve last durable safe checkpoint, evaluate current authority, block withdrawn/ineligible action and retain audit/provenance.
- candidate mechanism: Android Kotlin and iOS Swift state machines implement the same authority/reconciliation contract; native notifications are accelerators only.
- official evidence: Android lifecycle A6, Apple lifecycle P3 and notification APIs A12/P10 do not define Kavriva entitlement or safety semantics.
- reasoned inference: Two native clients can integrate platform timing, but they can race or disagree on authority without shared contract tests.
- dependency-specific evidence: No entitlement, push, subscription or backend provider is selected.
- unresolved facts: Entitlement source/TTL, offline grace, withdrawal timing, transfer/delete policy, active-task semantics and reconciliation contract.
- user-visible result: Active/held/withdrawn/transferred/needs-review state with safe-stop and Turkish explanation on both paths.
- failure/hold behavior: Authority uncertainty or withdrawal blocks affected action; in-flight work remains unknown/partial until reconciliation.
- recovery path: Reconnect/re-authenticate, reconcile idempotently, preserve evidence and apply reviewed correction/transfer/delete.
- shared-system obligation: Authorization, publication, audit, safety and retention are framework-neutral.
- candidate-attributable work: Duplicate authority state, lifecycle persistence, native notification/link handling and parity tests.
- accountable AI/external owner: AI state implementers; authorization owner, safety reviewer and privacy/legal authority.
- required later real-device evidence: Entitlement changes foreground/background, notification denial, cold link, process kill, offline grace and correction/withdrawal.
- residual risk: Independent timing and notification code can create inconsistent authority messaging between stores.
- result: HELD.

### S15 — Backup, restore, clone and key loss

- authoritative starting state: Backup/restore, device clone, reinstall or protected-key loss occurs with packages, history, pending operations and private media present.
- allowed transition: Classify restored data, validate account/device/key/content generations, quarantine mismatch, re-authenticate and re-download non-portable material; restore only last durable checkpoint.
- candidate mechanism: Android and iOS each implement native backup/key reconciliation behind the same portable data and recovery contract.
- official evidence: Android Auto Backup A9 documents API 23+, app-data inclusion/cache exclusion, 25 MB cloud quota and stale/device-specific restored values; Apple P5/P6 require separate review.
- reasoned inference: Native APIs expose platform-specific controls, but two restore/key-loss implementations and test games are required.
- dependency-specific evidence: Room/Core Data, key wrappers and backup configuration are not locked; iOS backup/key behavior remains unresolved.
- unresolved facts: iOS/Android backup rules, key hierarchy, clone detection, operation replay, media retention, quota and recovery authority.
- user-visible result: Restored/partial/quarantined/re-auth states explicit; stale entitlement/token is never current.
- failure/hold behavior: Key loss, generation mismatch, corrupt database or replay ambiguity holds protected actions and preserves permitted portable records.
- recovery path: Re-authenticate, validate/forward-migrate, re-download compact content, re-encrypt and retain audit; no silent discard.
- shared-system obligation: Data continuity, backup, privacy, deletion and authority reconciliation are common.
- candidate-attributable work: Two restore state machines, native key/backup adapters, migration fixtures and accessible quarantine UX.
- accountable AI/external owner: AI data/security implementers; platform backup specialists, security reviewer, account authority and privacy/legal owner.
- required later real-device evidence: Android API 29/current and comparison iPhone backup/restore, clone, reinstall, key loss, corrupt DB, pending replay, media and largest-text AT.
- residual risk: A successful platform restore can remain semantically stale or cryptographically unusable, with different failure modes per OS.
- result: HELD.

## 6. Accessibility Matrix

This is capability evidence, not approval. Fully native allows each OS's accessibility
services and standard controls, but the final Android UI toolkit and final iOS UI toolkit
are unresolved. Shared Turkish state/copy intent does not prove parity. The Android and iOS
oracles must be run independently on physical devices.

The candidate-specific `Android path` and `iOS path` columns jointly map to the controlled template's documented
capability plus platform-specific-work fields; `Later real-device oracle` and `Status` retain their controlled meaning.

| Check | Android path | iOS path | Later real-device oracle | Status |
|---|---|---|---|---|
| VoiceOver | Not applicable to Android; Android result must not be inferred from this column | SwiftUI accessibility modifiers or UIKit UIAccessibility; exact toolkit unresolved | VoiceOver through active, warning, stop, unknown, recovery, conflict and restore states | HELD |
| TalkBack | Compose semantics or View accessibility tree; roles, state, focus and traversal require explicit mapping | Not applicable to iOS; iOS result must not be inferred from this column | TalkBack through the same critical states and process interruptions | HELD |
| Largest text/reflow | Compose/Views layout, Android font scale, clipping and diagram alternative | SwiftUI/UIKit Dynamic Type, clipping and diagram alternative | Android largest font scale and iOS largest Dynamic Type; no truncation of safety text | HELD |
| Focus and reading order | Compose semantics/traversal or View order, keyboard/switch focus and back navigation | SwiftUI accessibility order or UIKit accessibilityElements, focus and back navigation | Independent focus order through every safety transition and native surface | HELD |
| State announcements | Android accessibility events/live regions and native permission/notification results | SwiftUI/UIKit announcements, VoiceOver focus and native permission/notification results | Turkish active/readiness/warning/unknown/stop/recovery announcements on each OS | HELD |
| Non-color status/contrast | Android theme, Compose/View semantics and system contrast settings | SwiftUI/UIKit theme, traits and system contrast settings; high-contrast implementation unresolved | Contrast, dark/high-contrast, color-blind and diagram/text alternatives | HELD |
| Reduced motion | Android animation scale and app-specific transition policy | iOS Reduce Motion and app-specific transition policy | Reduced motion during warning, stop, navigation and media on both devices | HELD |
| Switch/voice control | Switch Access/Voice Access and native controls | Switch Control/Voice Control and native controls | Switch scanning, spoken labels and no gesture-only critical action | HELD |
| Reduced dexterity | Android touch targets, timeout/cancel/retry and system back | iOS touch targets, timeout/cancel/retry and system back | One-hand/touch operation of safe-stop, recovery, picker and share return | HELD |

No row is PASS. Android Compose/View availability, SwiftUI/UIKit defaults or static
accessibility inspection cannot substitute for independent TalkBack/VoiceOver and human
review. The duplicate native paths add an explicit parity obligation: a fix in one path is
not evidence that the other path is fixed.

## 7. Upgrade and Forced-Event Walkthrough

| Event | Android path | iOS path | Affected contracts/evidence | External dependency/capacity | Hold/recovery |
|---|---|---|---|---|---|
| Planned release window | Re-pin Android Studio/AGP/Gradle/JDK/SDK/NDK and app dependencies; run Android fixtures, AT and signed staging | Re-pin Xcode/Swift/SDK/macOS/SPM and app dependencies; run iOS fixtures, AT and signed staging | Common API/schema/content/config/release graph plus two native graphs and two artifacts | Android/iOS owners, Mac/Xcode, devices, AT/safety/release custodians | HOLD until both paths pass; retain each prior artifact and forward-migrate only after review |
| Safety/security emergency correction | Apply approved content correction or signed Android binary; re-run Android impact evidence | Apply approved content correction or signed iOS binary; re-run iOS impact evidence | Recall/revocation, audit, provenance, signing and no-OTA controls | Qualified safety reviewer, security custodian, store accounts and incident authority | Pause affected generation/release on either store; safe-stop offline; reconcile after reviewed correction |
| Forced Google build/store requirement | Update target API/AGP/SDK/Gradle/JDK as required, rebuild and repeat Android tests | Unaffected only if Apple requirements unchanged; still recheck shared contract and rollout | Store target/build rules are dynamic; Android build graph may diverge from iOS | Android build/release owner and Google store authority; exact current rule/cost unresolved | Hold Android release, retain prior artifact, stage only after evidence; do not assume cross-platform symmetry |
| Forced Apple build/store requirement | Android artifact may remain valid, but shared contract/release graph must be reviewed | Update Xcode/SDK/Swift/macOS/signing and rebuild iOS; repeat iOS/native/AT evidence | App Store upload floor and iOS host graph are external and may force shared data/config checks | Mac/Xcode/signing and Apple store access; exact current rule/cost unresolved | Hold iOS release; retain prior iOS artifact and communicate platform-specific availability |
| Critical dependency abandonment | Replace Room/WorkManager/Compose/Views/media or security dependency and update Gradle/SBOM | Replace Core Data/SwiftUI/UIKit/SPM/media or security dependency and update SPM/SBOM | Native API, schema, migration, permissions, AT and provenance closure | Two native specialists, security review, dependency maintenance and device lab | Quarantine capability, keep safe manual path if valid, forward-migrate; no silent substitution |
| Old/new client/API/schema/content/config coexistence | Maintain old/new Android artifact and capability graph | Maintain old/new iOS artifact and capability graph | Server compatibility, content generations, migration and store rollout are shared but artifacts differ | Backend/content owner, two store custodians and safety reviewer | Hold incompatible task/path; keep accepted artifacts and migrate forward |
| Migration rollback refusal | Refuse unsafe Room/SQLite or file/schema downgrade; use forward migration | Refuse unsafe Core Data/file/schema downgrade; use forward migration | Binary rollback cannot undo a lossy data migration | Data/security reviewers and restore game-day capacity | HOLD if downgrade is required; quarantine and recover last durable checkpoint |
| Incident pause, impact and recovery | Identify Android version/dependency/config/content impact, pause Play rollout | Identify iOS version/dependency/config/content impact, pause App Store rollout | Provenance/SBOM/signing, platform release and safety correction converge | Incident commander, Android/iOS, security/safety/content/store authorities | Suspend, preserve evidence, issue reviewed correction and re-test both paths |

The fully native candidate avoids a single cross-platform framework upgrade, but it
explicitly owns two native upgrade streams. A shared fixture or schema does not reduce the
number of host/toolchain, accessibility, signing and store events that must be closed.
Exact duration, labor/capacity, hosted build and emergency costs are UNRESOLVED. No OTA
binary authority is assumed.

## 8. AI-Operability and Task Isolation

| Question | Evidence/result |
|---|---|
| Can a fresh AI implement one bounded task without whole-project context? | Portable contracts and fixtures can bound a task, but Android Kotlin and iOS Swift each need their own implementation context, native API and test path. No task graph or implementation evidence exists; HELD. |
| Are platform exceptions visible in the task graph? | Yes in principle because all platform code is explicit, but the final Android/iOS dependency, permission, lifecycle, backup and signing inventory is absent; HELD. |
| Can implementation, review and validation remain separate? | Separate Android and iOS work can be reviewed independently, with common fixture/parity review. No named owners, reviewer capacity, physical devices, AT oracle or safety evidence exists; HELD. |
| Are builds/tests deterministic enough to produce evidence? | Exact reference snapshots are recorded, but project lockfiles, Gradle/SPM resolution, CI, certificates, artifacts and test matrices are not pinned; HELD. |
| Can dependency changes identify affected contracts/tasks/tests? | Per-platform Gradle/SPM locks, SBOM and artifact manifests could map impact, but no application graph exists; HELD. |
| Can the project recover without one opaque workstation/provider? | Android source/artifacts can be portable in principle; iOS requires macOS/Xcode/signing access. Backup host, CI and artifact custody are unknown; HELD. |
| Does the candidate require unavailable human specialist authority? | Yes, likely: Android/Kotlin, iOS/Swift, Gradle/SPM/Xcode, security/key, accessibility, safety, store and incident owners. The nontechnical owner is not a coding/debugging/build-repair mitigation; HELD. |

The main AI benefit is explicit native boundaries and directly documented platform APIs.
The main AI risk is duplicated parity: a completed Android task does not complete its iOS
counterpart, and a native fix can require two independent reviews, test matrices, signed
artifacts and release decisions.

## 9. Equal 24-Month TCO Worksheet

### 9.1 Workload quantities

The approved workload is already fixed in Section 2. For auditability, its monthly
quantities are 24 GB / 240 GB / 1.2 TB required compact transfer, 10 GB / 100 GB /
500 GB optional media, and 1.5 GB / 15 GB / 75 GB user-photo upload for 1,000 / 10,000 /
50,000 MAU respectively. These are workload quantities, not provider prices, and exclude
retries, backups, replication, egress, logs and retention commitments. Local-device stress
is not multiplied by MAU.

### 9.2 Controlled category table

Unknown amounts remain UNRESOLVED, never zero. No provider plan, tax, currency conversion,
discount, human hourly rate or optional service price is invented.

| Cost row | Product-wide unavoidable | Candidate-caused | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---|---|---|---|---|---|---|
| Store membership | Yes | No | No | No | No | No free production-store substitute; defer purchase | Approved fixture: Google Play Console USD 25 one-time + Apple Developer USD 99/year; 24-month store-only USD 124-223 before tax/currency and renewal timing; high/recheck |
| Mac/hosted build | Yes for iOS release | Separate native Xcode/Swift path and signing | Hosted build optional | Build/release frequency | Borrow/local Mac or provider switch | Local/borrowed Mac preferred | UNRESOLVED; low |
| Android/iPhone access | Yes for acceptance | Two independent native UI/device matrices | Lab/borrowed devices optional | Cohorts/releases | Replace lab/borrower | Borrow/tester/device lab | UNRESOLVED; low |
| CI/build artifacts | Yes for reproducible evidence | Two build graphs, Gradle and SPM/Xcode | Hosted CI optional | Build/release volume | Provider-independent artifacts | Local controlled builds with exportable manifests | UNRESOLVED; low |
| Backend/database | Yes | No provider selected; Android/iOS persistence choices need separate implementation | Managed convenience optional | MAU/workload/retention | Export/replace provider | Free tier only with cap, overage shutdown, alert, export and exit | UNRESOLVED; low |
| Storage/backup/CDN/egress | Yes | Native storage/backup rules and two package paths | CDN/replication convenience optional | MAU, media, retries and retention | Compact scope, optional media and export | Cache eviction and capped tiers | UNRESOLVED; no price inferred from quantities; low |
| Identity/email/SMS | Yes if accounts require it | Two native key/permission/session integrations | SMS/premium recovery optional | MAU/recovery use | Manual/export recovery where approved | Email/manual first if approved; cap SMS | UNRESOLVED; low |
| Crash/telemetry/analytics | No until approved | Two native crash/observability integrations if selected | Optional | MAU/events | Disable/export logs | Disable or capped/free path with privacy/spend approval | UNRESOLVED, not zero; low |
| Security/SBOM/signing | Yes | Two signing/provenance/dependency closures | Paid scanner/host optional | Release/dependency cadence | Owned lock/SBOM/attestation | Reviewable open tooling if capacity exists | UNRESOLVED; low |
| Accessibility validation | Yes | Two UI/toolkit paths and native surfaces require separate evidence | External lab optional but independent human evidence required | Every release/forced event | Hold/rework/native fallback | Borrowed AT testers/devices | UNRESOLVED; low |
| Safety/content review | Yes | Two native renderings must preserve one safety meaning | No AI-only substitute | Content/release/correction | Safe-stop and release pause | Qualified owner required | UNRESOLVED; low |
| AI implementation/review | Capacity-dependent | Duplicate Android/iOS implementation, review and parity work | Optional paid AI/service capacity unapproved | Task/review volume | Portable contracts and reassignment | Bounded tasks only with approved capacity/spend controls | UNRESOLVED; low |
| Upgrade/dependency response | Yes | Two independent Android and iOS SDK/library/toolchain streams | Hosted migration support optional | Quarterly/forced events | Pin, retain each artifact, replace dependency | Local lock and staged migration | UNRESOLVED; low |
| Support/incident response | Yes | Two platform incident/release surfaces | Contracted/on-call convenience optional | MAU/platform/release scope | Pause/stage/provider-independent evidence | Explicit incident owner and capped operations | UNRESOLVED; low |
| Exit/migration | Yes | Platform-specific code, stores, schema adapters and signing paths | Replacement candidate work optional | Forced event/exit | Portable schemas/manifests/export and forward migration | No lossy rollback; retain accepted artifacts | UNRESOLVED; low |

The fully native cost burden is qualitative and explicit: two UI implementations, two
accessibility oracles, two lifecycle/storage/media paths, two dependency graphs, two
toolchain upgrades, two signed artifacts and two store release decisions. Native direct
access may reduce framework/plugin indirection, but it does not make this duplicated work
free. Any unapproved OTA line is disabled and remains UNRESOLVED, not zero.

## 10. Exit Dossier

### Portable or replaceable assets

- Canonical product/content/data schemas, history/provenance records, corrections,
  withdrawals, operation IDs and migration fixtures should remain framework-neutral.
- Content manifests, digests, compact-package boundaries, safety/recovery closure and
  optional-media metadata should be consumable by a replacement client.
- User-controlled export/share formats, Turkish copy keys, unit rules, design tokens,
  accessibility intent and semantic state identifiers should survive a UI/toolkit change.
- S1-S15 fixtures, acceptance oracles, release/rollback/revocation evidence and audit
  references should remain outside Android/iOS implementation details.
- Forward migrations must be explicit, versioned and rehearsed; old signed clients remain
  contained by the server capability/content policy.

### Platform-bound assets

- Android Kotlin/Compose/View code, Gradle/AGP/SDK/NDK configuration, Android permissions,
  Keystore, WorkManager, App Links and Play packaging are Android-bound.
- Swift/SwiftUI/UIKit code, Xcode/Swift/SPM configuration, iOS entitlements, Keychain,
  URLSession, Universal Links and App Store packaging are iOS-bound.
- Camera, picker, notification, share, lifecycle, background, key and backup adapters
  are platform-specific even when they implement the same portable contract.
- Android Keystore/iOS Keychain keys are not portable user data. Key loss requires
  quarantine, re-authentication and re-encryption; raw keys must not be exported.

### Migration, interruption and cost

- A replacement candidate must implement Android and iOS against the portable schemas,
  manifests and fixtures, support coexistence with old signed clients, revalidate current
  authority and deliver staged store artifacts.
- Interruption plan: retain the last accepted artifact on each platform, preserve portable
  records/export, pause affected content/release and reconcile only after replacement
  evidence and signing. A binary rollback is not a data rollback.
- Exact exit effort, duration, parity migration, replacement support and cost are
  UNRESOLVED. Direct native access is not an exit pass.

## 11. Candidate Result (Phase-4 Research)

### Mandatory-gate result

All mandatory gates remain HELD:

- Safety/readiness and truthful uncertainty: native APIs can express the contract; no
  Android/iOS implementation or qualified safety evidence exists.
- Offline scoped delivery and 72-hour behavior: direct platform transfer paths exist;
  package integrity, atomicity, resume and parity proof are absent.
- Native closure and lifecycle/restart: native reach is broad; durable checkpoint and
  Android/iOS interruption evidence are absent.
- Accessibility and Turkish critical flow: direct platform services exist; independent
  TalkBack/VoiceOver, largest-text, contrast, reduced-motion and native-surface oracles
  are absent.
- Release, signing, provenance and forced events: reference snapshots exist; two complete
  locks, SBOMs, signing chains, CI paths and store graph are absent.
- Data continuity, backup/restore and key loss: platform primitives are documented;
  schema, migration, restore/clone and key-loss game-day evidence are absent.
- AI-operability and task isolation: boundaries are visible, but two-path task/review/build
  capacity and deterministic evidence are absent.
- 24-month TCO and owner capacity: store baseline is approved; all other prices, providers
  and capacity are unresolved.
- Exit/migration and replacement continuity: portable boundary is stated; replacement
  rehearsal and simultaneous platform migration evidence are absent.

S1-S15 result count: 0 PASS / 15 HELD / 0 REJECT. No real-device pass, store pass,
benchmark, security pass or safety approval is claimed.

### Unresolved critical facts

- Product support policy, exact Android/iOS deployment floors, final Android UI and iOS UI
  toolkit, lifecycle/recovery semantics and offline recall validity.
- Android Studio/AGP/Gradle/JDK/SDK/NDK and Xcode/Swift/SPM/macOS exact project locks,
  certificates, artifact digests, store target requirements and CI availability.
- Database/schema/migration, account/entitlement/conflict contract, media/file rules,
  backup/restore/key semantics and portable export format on both paths.
- Native dependency and platform API closure, direct/transitive locks, SBOM/license/EOL/
  security response and owned fallbacks for transfer, camera, files, share, notifications,
  deep links and secure storage.
- Android/iPhone devices, TalkBack/VoiceOver and other AT reviewers, independent safety/
  content reviewer, release/signing/store custodians, Mac access and incident authority.
- AI task/review capacity, cash ceiling, optional-service approvals and current provider
  quotes; no numeric amount is assumed for unresolved lines.
- Mixed old/new client/API/content/config release graph, pause/rollback refusal and
  correction/withdrawal protocol.

### Conditional interpretation

The largest low-budget burden is explicit duplication: two native UI/state implementations,
two accessibility and device matrices, two lifecycle/storage/media paths, two dependency
graphs, two toolchain upgrade streams and two signed store releases. The largest
AI-operability benefit is direct, visible native boundaries; the largest risk is parity
drift and twice the context/reviewer capacity.

External authorities remain required for Apple/Google legal identity and store accounts,
Mac/Xcode/signing, physical devices/testers/AT, qualified safety/content review,
security/privacy, tax/legal/payment and any selected provider. No framework recommendation
is made. A later recommendation would require complete native closure, pinned toolchains/
dependencies/provenance, all S1-S15 evidence, independent AT/device/safety/release
oracles, owner/capacity/TCO approval and review. A rejection would be triggered by an
ownerless critical path, unsafe bypass, unbounded unapproved cost, lost canonical truth or
unsupported capability without a safe fallback; no intrinsic fully-native rejection is
asserted here, but all gates remain HELD.

Overall Phase-4 status: STRUCTURALLY COMPLETE DRAFT / UNREVIEWED / HELD.

## Source Register

Official/primary external sources are listed in Section 1.1. Internal control sources
used for the fixture and decision status are:

- DEC-0031 and common fixture: ../../00_CONTROL/DECISION_LOG.md and
  DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md
- DEBATE-006 mobile technology evidence, team and TCO:
  DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md
- Controlled candidate dossier template: DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md
- DEBATE-005 software/content/supply-chain/release governance:
  DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md
