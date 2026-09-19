# DEBATE-006 — EQUAL MOBILE CANDIDATE DOSSIER: FLUTTER

Status: `STRUCTURALLY COMPLETE DRAFT / RESEARCH — NO-CODE / NOT REVIEWED / HELD`
Date: 2026-09-17
Decision level: Phase-4 comparison evidence only; not a recommendation, ADR, approval or Gate 4 -> 5 transition

This dossier evaluates Flutter against the user-approved DEBATE-006 fixture. It is documentary research only. No
application code, prototype, executable spike, signed build, benchmark, store submission or real-device pass is claimed.
The labels used below are:

- `OFFICIAL EVIDENCE`: a statement supported by a Flutter, Android or Apple primary source;
- `REASONED INFERENCE`: a consequence of applying that evidence to the Kavriva fixture;
- `DEPENDENCY-SPECIFIC`: evidence about an identified package/plugin, without implying that it is selected;
- `UNRESOLVED`: a missing product, owner, toolchain, price, capacity or acceptance fact. An unresolved critical item is
  `HELD`, never silently treated as zero risk or zero cost.

## 1. Candidate Identity

| Field | Record |
|---|---|
| Candidate family | Flutter: shared Dart UI/application surface with explicit Android/Kotlin and iOS/Swift native boundaries |
| Exact evaluated version/snapshot | Flutter `3.47.2` stable; bundled Dart `3.13.2`; official Windows release ref `d3b14c876900e553bc736ca19295fc09e3853e8e`, release date `2026-08-27`; Windows artifact SHA-256 `37934f2128a55d77a38baba12fd611157ed23a47bf7d2b7d17e9e84da118409d` ([official release metadata](https://storage.googleapis.com/flutter_infra_release/releases/releases_windows.json)) |
| Evidence retrieval date | 2026-09-17 |
| Product comparison floor | Frozen four-cohort fixture: constrained Android API 29 / 4 GB RAM / 64 GB storage / 2 GB free; main Android 13+ / 6 GB RAM / 128 GB storage; oldest supported-end iPhone capable of iOS 16.4; and a current standard non-Pro iPhone on the current generally available iOS. These are comparison profiles, not a final support promise. |
| Framework-supported floor | At the 3.47.2 documentation snapshot, Android is supported API 24–37 (CI-tested 24–36; x64/Arm32/Arm64) and iOS is supported 15–27 (CI-tested 18 and 26; Arm64). See [supported deployment platforms](https://docs.flutter.dev/reference/supported-platforms). |
| Build-tool/store floor | `UNRESOLVED`: exact Android SDK/AGP/Gradle/JDK, Xcode/macOS, signing and store acceptance matrix must be pinned for the eventual release. A framework floor is not a build or product floor. |
| Support/EOL statement | The official archive recommends the stable channel for production, describes roughly quarterly stable windows and identifies the git ref/Dart version for each release. A fixed Kavriva support/EOL window, upgrade policy and end-of-support response are not yet set. |
| Dossier author/reviewer | Research sub-agent `/root/flutter_dossier`; independent dossier review and manager disposition pending |

Every later reference to comparison devices, device evidence or real-device acceptance means all four frozen cohorts
above. A two-device or oldest-only sample cannot close any scenario or accessibility gate.

### Version drift requiring explicit follow-up

The equal-candidate table in the reviewed DEBATE-006 record uses Flutter `3.47.2`, so that is the frozen comparison
snapshot here. The official release JSON checked on the same date now lists stable `3.47.4` as the current release,
while the Flutter documentation page still states that its content reflects `3.47.2`. This dossier does not silently
replace the frozen fixture. The eventual ADR must re-check and re-pin the SDK, Dart version, ref, artifact digest and
toolchain together. `UNRESOLVED` until that re-pin is authorized.

## 2. Fixed Inputs and Comparison Discipline

This record applies, without candidate-specific relaxation:

- `04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md`, approved under `DEC-0031`;
- the S1–S15 definitions and mandatory gates in `DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md`;
- `DEC-0023`–`DEC-0031`, including scoped/data-efficient offline delivery, conservative recovery, no unapproved OTA,
  federated release integrity, AI-operated delivery and limited-budget staged costing;
- the reviewed DEBATE-002–005 safety, authorization, audit, ingestion, publication, revocation and supply-chain
  directions; and
- approved Phase-3 product/design/accessibility truth, including Turkish-first critical flows, truthful uncertainty,
  no silent overwrite/loss, safe-stop/recovery and protected history/provenance.

The frozen comparison constants are: one selected motorcycle/variant and one active task; required compact guidance and
complete safe-stop/recovery closure up to `12 MB`; optional media up to `150 MB`; unrelated `2 GB` catalog; `250 MB`
offline-content cache; cellular confirmation above `25 MB`; local fixtures of 3/10 motorcycles, 250/2,000 records,
50/500 photos at 3 MB, 100/1,000 private notes, 20/200 pending changes and 3/30 deliberate conflicts; seven network
and interruption profiles; 1,000/10,000/50,000 MAU service workload; four planned release windows per year plus one
annual safety/security correction and one forced platform/toolchain event. These values are comparison fixtures, not final
commercial, retention or support limits.

All scenario results below are `HELD` because this is no-code research and critical inputs (product policy, exact
toolchain, dependency lock, real devices, accessibility execution, owner capacity and service pricing) are not yet
available. This is not evidence that Flutter is inherently rejected; it is the required equal-evidence hold.

## 3. Candidate Architecture Boundary (Documentary, No Implementation)

### UI and platform-specific UI

The proposed Flutter boundary is one shared Dart widget/state presentation surface for the approved Kavriva visual and
state system. Native UI is retained where the operating system owns permission sheets, camera/file pickers, share sheets,
notification surfaces, universal/app links or other accessibility-critical conventions. A shared widget tree is not proof
of platform parity: both Android and iOS require their own semantics, lifecycle and real-device acceptance evidence.

`Material`, `Cupertino`, Flutter `Semantics` and platform adaptations are framework mechanisms, not final Kavriva design
tokens or accessibility approval. Tablet/foldable optimization is outside the first-release fixture; unsupported devices
must receive a clear safe message rather than a partially functional flow.

### Domain and data ownership

Domain rules, state-machine semantics, Turkish copy keys, unit rules, safety/readiness gates, provenance labels,
entitlement rules and conflict outcomes are proposed as portable Dart/domain contracts. They remain Kavriva-owned and are
not delegated to Flutter or a package. A repository boundary is the only permitted mutation path, consistent with
Flutter's offline-first guidance; server-authoritative publication, current eligibility, recall and authorization remain
outside the client framework.

### Local persistence, encryption, migration and backup

The local layer must separate cache/offline packages, account-light core history, private notes/photos, pending operation
log, conflict records, trust/eligibility metadata and key material. A transactional database and schema format are
`UNRESOLVED`; no database package is selected. Writes require durable checkpoints, idempotency keys, crash/interrupted-
write recovery and forward-compatible migrations. Protected fields and keys require Android Keystore and iOS Keychain
ownership through an explicit native boundary; raw keys must not be exported in a backup or portable file.

Android and iOS backup/restore rules are separate platform policies. Restored or cloned state is untrusted until account,
device, key, current release and safety/content generations reconcile. Backup is never a source of current entitlement or
safety authority.

### Sync and scoped offline packages

The offline package service must download only the selected motorcycle/task closure, display size first, keep compact
safety/recovery material complete, treat heavy media as optional, stage into temporary storage, verify digest/manifest and
atomically promote. Cancellation, resume, eviction, low storage, duplicate operation and corrupt-package handling belong to
the Kavriva data protocol. Foreground reconciliation after network return is authoritative; Android/iOS background work
is an optimization and cannot be a correctness prerequisite.

### Native capability boundaries

Camera, file/media import, export/share, notification/deep-link intake, secure storage, background transfer and backup
configuration require native platform knowledge even when reached through a Flutter plugin. Each dependency is wrapped by
a Kavriva-owned interface so that package replacement and independent testing remain possible. An unnamed or ownerless
critical plugin is not accepted; it remains `HELD` until exact version, owner, fallback, EOL/security response and release
evidence are documented.

### Accessibility and release boundary

The Dart UI exposes semantics and platform-adapted behavior, while Android TalkBack/Switch/Voice Access and iOS
VoiceOver/Switch/Voice Control behavior must be proven on actual devices at largest text and Turkish critical states.
Flutter's accessibility APIs and guideline tests are useful evidence but cannot replace that acceptance.

Android and iOS are separate signed store artifacts built from the pinned Flutter/Dart SDK, dependency lock, native
toolchains and release graph. The release graph binds client capability, API/schema, content/configuration, migrations,
offline recovery, derived media, provenance/SBOM, signing and suspension generations. No OTA code/update authority is
assumed or approved.

### Internal Operations and exit boundary

Internal Data & Content Operations remains a separate browser-based client and trust boundary. No shared Flutter/browser
team competency is assumed, and consumer credentials or client-side authority must not cross that boundary.

Portable assets should include canonical content/data schemas, history/provenance/correction events, media exports,
Turkish copy/design intent, S1–S15 fixtures, contracts, migrations and acceptance oracles. Flutter widgets, Dart runtime
artifacts, plugin APIs, Android/iOS runners, Gradle/Xcode configuration and signed binaries are framework/toolchain-bound.
The exact portable schema, key-continuity procedure, migration rehearsal and replacement release plan remain
`UNRESOLVED` and are recorded in the exit dossier below.

## 4. Native and Dependency Closure

The rows below are a closure inventory, not an approved dependency list. Package versions are evidence snapshots observed
on 2026-09-17; only a committed lockfile and source/provenance review can make them release inputs.

| Capability | Flutter/native boundary and exact dependency snapshot | Primary/backup owner and native skill | OS/toolchain floor and lifecycle/threading constraints | Accessibility impact | Fallback/replacement | EOL/security/release evidence | Status |
|---|---|---|---|---|---|---|---|
| Shared UI, state and semantics | Flutter `3.47.2` framework/engine; Dart widgets, `Semantics`, Material/Cupertino; no third-party runtime dependency assumed | AI Flutter implementation + independent reviewer; Android/Kotlin and iOS/Swift escalation for host issues | Framework mobile floor Android API 24/iOS 15 at snapshot; UI work on Flutter main isolate; host channel calls obey platform-main-thread rules | Custom widgets must expose labels, roles, focus order, state changes and non-color status in Turkish; visual parity is not proof | Keep platform-specific widget/host path; replace framework only through exit plan | Pin SDK ref/digest; widget/integration/native tests and release graph required | `HELD` |
| Local database and durable event log | No package selected. Candidate paths are a reviewed Dart SQL package or an owned SQLite/native bridge; exact dependency/version intentionally `TBD` | AI data/migration owner; backup: independent data reviewer; SQLite/transaction/concurrency skill required | Android API 24/iOS 15 comparison floor; serialized writes, transaction boundaries and isolate/host-thread rules must be specified | Conflict/unknown/partial states must be announced and operable without color | Portable schema plus forward migration; hold if no transaction-safe implementation exists | SBOM, lockfile, migration fixtures, crash-recovery evidence and security response needed; no owner/EOL yet | `HELD` |
| Protected fields and keys | Proposed owned Kotlin/Android Keystore and Swift/iOS Keychain adapters through typed platform channel/Pigeon; Pigeon version not selected | AI native-boundary owner with Android/iOS security reviewer; qualified security escalation if key semantics fail | API 24/iOS 15 fixture; channel boundary and platform main-thread rules; key rotation/loss and device binding are explicit states | Lock/key-loss/re-auth/quarantine status needs spoken and text explanation | Quarantine and re-authentication; no plaintext or copied-key fallback | Android Keystore/iOS Keychain policy, key lifecycle tests, signing/SBOM and incident evidence required; exact APIs/config unresolved | `HELD` |
| Camera capture | Flutter team `camera` `0.12.1` evidence snapshot; endorsed `camera_android_camerax`/`camera_avfoundation` implementations are transitive candidates, not locked | AI plugin wrapper owner; backup Android CameraX and iOS AVFoundation owner | Package page documents Android SDK 24+ and iOS 13+; permission prompts, controller initialization/disposal and platform lifecycle; Camera plugin lifecycle handling is app-owned | Permission denial, capture errors and retry/skip paths need accessible status; native camera surface requires AT check | Image/file import; owned platform bridge if plugin fails; unsupported camera must not block non-camera evidence path | Flutter `flutter.dev` publisher, changelog and platform implementation review; exact transitive lock, CameraX/AVFoundation behavior, EOL/security response and both-device evidence unresolved | `HELD` |
| Photo/library and file import | Flutter team `image_picker` `1.2.3` plus Flutter team `file_selector` `1.1.0` evidence snapshots; `retrieveLostData`/native picker behavior must be wrapped | AI media/privacy owner; backup Android Photo Picker and iOS PHPicker/UIDocumentPicker skill | `image_picker` documents Android SDK 24+/iOS 13+; `file_selector` documents Android SDK 21+/iOS 12+; process death, permission changes, temporary files and URI/path lifetime are platform-specific | Native picker and permission UI must be tested with TalkBack/VoiceOver; file type errors cannot rely on color | Owned native picker bridge or safe manual evidence entry; quarantine invalid/untrusted files | Exact package/platform implementation locks, MIME/size scanner, temporary cleanup, security response and native dialog evidence unresolved | `HELD` |
| User-visible export/share | `file_selector` can open/save through native file UI, but its documented mobile save-location support is absent; mobile share sheet requires an owned Android Sharesheet/iOS `UIActivityViewController` boundary or a reviewed plugin (none selected) | AI export owner; backup Android/iOS share and disclosure-review owner | Android API 24/iOS 15 fixture; external share destinations and process return are untrusted/interruptible | Share/export scope, privacy warning and cancellation must be announced and readable | Export to an app-owned file plus user-controlled system share; no silent disclosure | File/export manifests, disclosure audit and plugin/native SBOM; exact mobile share dependency and EOL/security owner unresolved | `HELD` |
| Scoped download, resume and cleanup | Dart orchestration plus owned native adapters; Android WorkManager and iOS background `URLSession`/background-task APIs are platform candidates; no Flutter downloader plugin selected | AI transfer owner; backup Android background-work and iOS URLSession/BackgroundTasks owner | Doze/standby and iOS scheduling are deferred/limited; cancellation/expiration/low storage/process death must leave a recoverable state; channel work must not block UI | Progress, paused/failed/needs-retry and safety closure need accessible announcements | Foreground resumable transfer; user can retry; required compact closure is never silently omitted | Exact adapter/plugin, OS quotas, background modes, EOL/security and device/network evidence unresolved; no timely-background assumption | `HELD` |
| Local/user-visible notifications | Native Android notification APIs and iOS `UNUserNotificationCenter` through owned channel or reviewed plugin (none selected); remote push provider is not chosen | AI notification owner; backup Android/iOS permission and policy owner | Notification permission/authorization, channel/category, user disablement and app process state differ; notification cannot be current safety authority | Notification text/action must be Turkish, non-color, deep-link-safe and usable with AT | In-app foreground reconciliation and visible stale/recall state; no notification dependency for correctness | Exact plugin/provider, privacy/permission review, signing and incident evidence unresolved; OTA/push timing not guaranteed | `HELD` |
| Deep links and external URLs | Flutter Router/default deep-link handler plus Android intent filters and iOS universal-link configuration; plugin not selected | AI navigation/security owner; backup native URL validation owner | App may be cold, resumed or process-restarted; every URL is untrusted input; duplicate/replayed links must be idempotent | Route arrival and error/hold state must be announced; no deep link bypasses readiness/authorization | Safe in-app destination and manual navigation; reject unknown/unsafe routes | Domain association/entitlement, URL allowlist, release config and provenance evidence unresolved | `HELD` |
| Lifecycle/restart/checkpoint | Flutter `AppLifecycleState`/`AppLifecycleListener` plus app-owned durable checkpoint; no lifecycle plugin assumed | AI recovery owner; backup Android Activity and iOS scene/lifecycle owner | Flutter documents skipped lifecycle notifications and sudden termination; only last durable checkpoint may restore; uncommitted physical state is unknown/partial | Resume/revalidation/safe-stop must be announced in Turkish and focusable | Safe-stop/recovery screen and explicit revalidation; never continue-anyway | Lifecycle interruption fixtures, atomic-write evidence and native process-kill results required; no real-device evidence yet | `HELD` |
| Backup, restore, clone and key loss | Android Auto Backup/data-extraction rules plus iOS backup/Keychain policy; Flutter package support is not sufficient; exact include/exclude rules TBD | AI data/security owner; backup Android/iOS backup specialist and account authority | Android backup schedule/transport and iOS key/device behavior are system-controlled; restored URI/key/token may be invalid or stale | Quarantine, re-authentication and partial-restore state need clear AT output | Re-download content, preserve portable records, re-authenticate and quarantine on mismatch | Backup/restore game day, key rotation, clone/replay evidence and protected audit required; iOS policy and exact rules unresolved | `HELD` |
| Accessibility and native UI testing | SDK `flutter_test`/`integration_test` plus semantics/guideline APIs; native permission/notification UI is outside `integration_test` coverage; native XCTest/Espresso or third-party test tool is TBD | AI test owner; independent real-device AT reviewer; external human testers required | Both platform toolchains and physical devices required; tests must cover process death, permission dialogs and largest text | VoiceOver/TalkBack, Switch/Voice Control, Turkish critical flows and non-color state semantics are release gates | No visual/API-only fallback; hold release | Test artifacts, device matrix and independent evidence required; exact test stack/cost/availability unresolved | `HELD` |
| Store build, signing and provenance | Flutter CLI plus Android Gradle/Xcode/SwiftPM host projects; Apple/Google signing accounts and keys are external authorities | AI release owner; owner controls store identity; backup release/security custodian | Exact SDK/toolchain/store floors unknown; iOS requires macOS/Xcode access; both stores can be staged, not necessarily simultaneous | Store error/hold status is operational evidence, not consumer UX proof | Provider-independent local artifacts and recoverable CI; hold if signing/custodian missing | Pin SDK/ref, `pubspec.lock`, SBOM, artifact attestations, signing custody and DEBATE-005 graph; hosted build/CI unapproved | `HELD` |

### Observed package snapshots (not a lockfile)

| Package | Observed version and publisher | Documented platform floor / relevant note | What remains unresolved |
|---|---|---|---|
| `camera` | `0.12.1`, verified publisher `flutter.dev` ([package](https://pub.dev/packages/camera), [source pubspec](https://github.com/flutter/packages/blob/main/packages/camera/camera/pubspec.yaml)) | Android SDK 24+, iOS 13+; CameraX-backed Android implementation is endorsed in the package docs | Final lock, transitive versions, lifecycle handling, device quirks and security/EOL response |
| `image_picker` | `1.2.3`, verified publisher `flutter.dev` ([package](https://pub.dev/packages/image_picker), [source pubspec](https://github.com/flutter/packages/blob/main/packages/image_picker/image_picker/pubspec.yaml)) | Android SDK 24+, iOS 13+; process-loss recovery API is documented | Final lock, permissions/metadata policy, temporary-file/privacy behavior and native-device evidence |
| `path_provider` | `2.1.6`, verified publisher `flutter.dev` ([package](https://pub.dev/packages/path_provider), [source pubspec](https://github.com/flutter/packages/blob/main/packages/path_provider/path_provider/pubspec.yaml)) | Android SDK 24+, iOS 13+; exposes app support/documents/cache paths | It does not provide database, encryption, atomic commit or retention semantics; final lock and owner unresolved |
| `file_selector` | `1.1.0`, verified publisher `flutter.dev` ([package](https://pub.dev/packages/file_selector), [source pubspec](https://github.com/flutter/packages/blob/main/packages/file_selector/file_selector/pubspec.yaml)) | Android SDK 21+, iOS 12+; native file UI; mobile save-location support is not documented as available | Mobile share/export gap, exact lock, disclosure controls and device evidence |
| `integration_test` | SDK-bound package in the pinned Flutter distribution; no separately selected pub version | Flutter documentation says it can run on physical device/emulator but cannot interact with native platform UI | Native dialog/notification test method, device access and independent reviewer capacity |

Flutter's [package dependency management](https://docs.flutter.dev/packages-and-plugins/dependency-management) states that
`pubspec.lock` records exact direct/transitive versions for an application. That lock, provenance, license/SBOM and
platform implementation graph do not exist yet; package pages above are research snapshots only.

## 5. Equal S1-S15 Scenario Record

The following records use the mandatory fields from the common evidence template. A mechanism is a candidate-shaped
design hypothesis, not an implementation claim. Every result is HELD because no code, dependency lock, signed artifact,
physical-device run, accessibility oracle, safety review or accountable delivery capacity has been provided.

### S1 — First value without an account

- Starting state: No account, no server authority and no prior local profile; the user selects one motorcycle/variant and can view the approved local starting surface.
- Allowed transition: Persist the selection durably, show the account-registration/skip choice, and later offer an explicit migration preview; never silently merge or overwrite local history.
- Candidate mechanism: Shared Dart state/repository boundary, app-support storage and a portable profile/event schema; path_provider is only a directory locator and not the database or security layer.
- Official evidence: Flutter offline-first guidance treats repositories as the single source of truth and path_provider documents app support/documents/cache locations: https://docs.flutter.dev/app-architecture/design-patterns/offline-first and https://pub.dev/packages/path_provider.
- Reasoned inference: Flutter can host the local-first presentation and domain contract, but the account bind, database transaction and conflict policy remain Kavriva-owned.
- Dependency-specific evidence: path_provider 2.1.6 is a Flutter-published research snapshot; no database, auth or migration package is selected.
- Unresolved facts: Anonymous identity policy, schema, account bind/idempotency rules, backup handling, deletion and exact local database/key implementation.
- User-visible result: Useful selected-task value without an account, with clear Turkish copy saying what is local, what will migrate and what cannot yet be treated as authoritative.
- Failure/hold behavior: If a local write or migration preview cannot be proven durable, hold the transition and retain the last durable state; never claim successful migration.
- Recovery path: Reopen the last durable checkpoint, revalidate against current authority after sign-in, and quarantine ambiguous records for review.
- Shared-system obligation: Product copy, authorization, history/provenance, deletion and account semantics are shared across all candidates.
- Candidate-attributable work: Dart repository/state wiring, platform storage adapters, semantics and release/test integration around the chosen implementation.
- Accountable AI/external owner: AI data/UI implementer; product/account owner and an independent data reviewer for the migration authority.
- Required later real-device evidence: Fresh install, no-account use, force-close/restart, sign-in migration, duplicate submit, storage pressure and restore/clone on the comparison devices.
- Residual risk: A shared UI can conceal a non-portable local schema or an unsafe account merge.
- Result: HELD.

### S2 — Compact offline teaching package

- Starting state: Online authority has selected one motorcycle/task closure; the required compact package is at most 12 MB, optional media is at most 150 MB, and unrelated 2 GB content is not requested.
- Allowed transition: Show measured size, obtain cellular confirmation above 25 MB, stage a manifest and digest, download resumably, verify, atomically promote, and expose only a complete valid package.
- Candidate mechanism: Dart transfer state machine with app-owned temporary storage and manifest generations; native Android WorkManager and iOS URLSession/background-task adapters are candidates, with a foreground retry path.
- Official evidence: Flutter offline-first architecture; Android persistent background work; Apple's background strategy guidance says scheduling and time are system-controlled: https://docs.flutter.dev/app-architecture/design-patterns/offline-first, https://developer.android.com/develop/background-work/background-tasks/persistent and https://developer.apple.com/documentation/BackgroundTasks/choosing-background-strategies-for-your-app.
- Reasoned inference: Flutter can render the state machine, but network correctness cannot depend on a timely background callback; atomic promotion and resume rules must be implemented and tested per OS.
- Dependency-specific evidence: No downloader plugin is selected. The official package/plugin channel path can carry owned adapters, but plugin versions and native implementation are unknown.
- Unresolved facts: Package schema, digest algorithm, storage reservation, retry/timeout policy, OS quotas, background entitlements, transfer provider, cancellation semantics and exact adapter lock.
- User-visible result: Compact safety/recovery material is available offline; optional media is clearly optional and transfer progress/paused/failed states are Turkish, truthful and accessible.
- Failure/hold behavior: Partial, corrupt, expired or insufficient-space packages are never actionable; the task is held with a recoverable retry message.
- Recovery path: Resume or restart in foreground, clean only verified temporary artifacts, re-check manifest/generation and promote once; do not silently fall back to the 2 GB catalog.
- Shared-system obligation: Scoped delivery, safety closure, content generations, storage limits and no-OTA policy are candidate-neutral.
- Candidate-attributable work: Dart orchestration, channel adapters, progress semantics, background constraints and platform-specific permission/storage handling.
- Accountable AI/external owner: AI transfer implementer; Android background-work and iOS URLSession specialists plus content/release authority.
- Required later real-device evidence: All network profiles, low storage, process kill, lock/call, Doze, iOS expiration, resume, duplicate/corrupt package and 12/150 MB boundary tests.
- Residual risk: A plugin or background API may appear functional while violating atomic safety closure under process death.
- Result: HELD.

### S3 — Interrupted physical work

- Starting state: An active task has a last durable committed checkpoint; the device locks, receives a call, loses process state or is restarted.
- Allowed transition: Restore only the last durable checkpoint, mark in-flight physical state unknown/partial, stop safely and require explicit revalidation before continuation.
- Candidate mechanism: App-owned journal/transaction boundaries and Flutter lifecycle listeners; platform activity/scene callbacks are signals, not proof that termination was observed.
- Official evidence: AppLifecycleState documents lifecycle states and warns that applications may not receive all notifications, including sudden termination: https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html.
- Reasoned inference: Flutter lifecycle APIs help choose a checkpoint, but cannot recover an uncommitted physical action or prove that a kill signal was delivered.
- Dependency-specific evidence: No lifecycle recovery plugin is selected; camera documentation separately requires application lifecycle handling when camera state changes.
- Unresolved facts: Journal schema, atomic commit boundary, hardware/task semantics, recovery copy, native activity/scene behavior and exact kill/restore oracle.
- User-visible result: Turkish safe-stop, unknown/partial and revalidation states are explicit; the app never says continue solely because a screen was restored.
- Failure/hold behavior: Missing or inconsistent checkpoint holds the task; no silent replay, duplicate completion or inferred physical state.
- Recovery path: Reopen last committed state, inspect current physical condition, reconcile with authority when available and record the operator's explicit recovery outcome.
- Shared-system obligation: Conservative recovery, no silent overwrite/loss, audit and safety authority apply equally.
- Candidate-attributable work: Lifecycle bridge, durable journal integration, focus/semantics and native process behavior tests.
- Accountable AI/external owner: AI recovery implementer; qualified safety owner and Android/iOS lifecycle reviewers.
- Required later real-device evidence: Background/lock/call/process kill/restart, low memory, interrupted DB write, camera interruption and clock-change tests on both platforms.
- Residual risk: OS termination can occur without a Flutter callback, leaving the boundary between unknown and committed dependent on durable write design.
- Result: HELD.

### S4 — Offline recall or dormant guidance

- Starting state: A valid compact guide is downloaded and the user is offline; no new server recall or correction is observable.
- Allowed transition: Teach from the last valid content generation, expose its age/scope, and block or downgrade any action whose current validity cannot be established; reconnect and reconcile before treating it as current.
- Candidate mechanism: Versioned content manifest, validity/revocation generation, local provenance and foreground reconciliation; Flutter is only the state presentation.
- Official evidence: Flutter offline-first guidance distinguishes local and remote repositories; Android Doze defers network/jobs and Apple background execution is limited/system-decided: https://docs.flutter.dev/app-architecture/design-patterns/offline-first, https://developer.android.com/training/monitoring-device-state/doze-standby and https://developer.apple.com/documentation/BackgroundTasks/choosing-background-strategies-for-your-app.
- Reasoned inference: Offline use can preserve previously approved teaching, but Flutter cannot manufacture a current recall or safety authority.
- Dependency-specific evidence: No recall/push dependency is selected; native notifications/deep links are explicitly non-authoritative fallbacks.
- Unresolved facts: Recall TTL/priority, offline validity window, clock manipulation policy, correction/withdrawal semantics, notification provider and content-generation API.
- User-visible result: Stale/dormant status, scope and safe-stop/recovery guidance are readable and spoken in Turkish; no current-authority claim is made offline.
- Failure/hold behavior: A withdrawn, expired, incompatible or unknown generation holds the affected action and keeps safe-stop material if verified.
- Recovery path: Reconnect, re-authenticate as required, fetch current generation, reconcile local history and preserve the old record as provenance rather than overwriting it.
- Shared-system obligation: Safety truth, recall, publication/revocation and notification policy are framework-neutral.
- Candidate-attributable work: Generation state, offline banners, accessibility announcements, notification/deep-link adapters and reconciliation tests.
- Accountable AI/external owner: AI content-state implementer; qualified safety/content publisher and authorization owner.
- Required later real-device evidence: Offline 72 hours, clock change, force-close, background restriction, notification denial, cold deep link and correction/withdrawal reconciliation.
- Residual risk: Users may over-trust a polished shared screen if stale state and authority boundaries are not visually, textually and audibly unmistakable.
- Result: HELD.

### S5 — Old client with changed meaning

- Starting state: An older signed client encounters a new content field, changed unit/meaning or server capability it cannot interpret.
- Allowed transition: Negotiate explicit capability and content-generation compatibility; render known safe subsets and fail closed on safety-critical unknown meaning.
- Candidate mechanism: Versioned schemas, capability matrix, feature gates and release graph owned by the product, with Dart adapters kept separate from Flutter widgets.
- Official evidence: Flutter package usage guidance documents that packages bring host code; it provides no automatic product semantic compatibility: https://docs.flutter.dev/packages-and-plugins/using-packages.
- Reasoned inference: Flutter's shared source may reduce duplicated UI, but it does not solve old-client/API/content meaning or store rollout compatibility.
- Dependency-specific evidence: pubspec.lock can pin package versions, but no application lock or release graph exists.
- Unresolved facts: Capability negotiation, schema evolution, server minimum-version policy, content fallback and rollback refusal criteria.
- User-visible result: The user sees a clear compatible/needs-update/held state and never an invented interpretation of a safety field.
- Failure/hold behavior: Unknown critical field or incompatible generation blocks the affected flow; unrelated portable history remains viewable only within its known scope.
- Recovery path: Staged store release, server compatibility window, forward migration after review and explicit update; do not use OTA as an authority.
- Shared-system obligation: API/content versioning, store rollout and safety fail-closed policy are common.
- Candidate-attributable work: Serialization adapters, capability display, widget compatibility tests and native build matrix maintenance.
- Accountable AI/external owner: AI release/data implementer; product API/content owner, safety reviewer and store account custodian.
- Required later real-device evidence: At least one old/new client pair, changed fields, forced update, offline period, rollback refusal and mixed store rollout.
- Residual risk: A single shared Dart repository can make a semantic change look source-compatible while old signed binaries remain incompatible.
- Result: HELD.

### S6 — Local profile and history conflict

- Starting state: Local notes/history and server profile differ because of offline edits, duplicate submission, account migration or restore.
- Allowed transition: Identify operation and record IDs, display a migration/conflict preview, apply deterministic idempotent operations, retain both provenance records where required and request explicit resolution.
- Candidate mechanism: Repository boundary, append-only/pending operation log, conflict records and a reviewed transaction-safe local store; Flutter renders states and forms.
- Official evidence: Flutter offline-first architecture places synchronization responsibility in repository/data layers, not widgets: https://docs.flutter.dev/app-architecture/design-patterns/offline-first.
- Reasoned inference: Flutter can share conflict UX and domain code, but conflict correctness depends on the selected database, server contract and migration rehearsal.
- Dependency-specific evidence: path_provider only exposes directories; no conflict/database/auth package is selected.
- Unresolved facts: Merge precedence, operation IDs, delete/tombstone rules, private-note policy, server conflict API, schema migrations and backup/restore interaction.
- User-visible result: Partial/conflict/needs-review status is explicit, localized and accessible; no silent last-write-wins for protected truth.
- Failure/hold behavior: Ambiguous records are quarantined and the affected action is held; duplicate retries do not create duplicate authoritative outcomes.
- Recovery path: Retry idempotently, resolve through an explicit UI or owner workflow, preserve audit/provenance and reconcile current authority.
- Shared-system obligation: History, audit, conflict, deletion and privacy rules are common candidate gates.
- Candidate-attributable work: Dart operation model, adapters, transactional boundaries, semantics and cross-platform migration tests.
- Accountable AI/external owner: AI data implementer; product/data authority, security/privacy reviewer and safety owner.
- Required later real-device evidence: Offline edit/online merge, duplicate/partial upload, corrupt package, restore/clone, low storage and interrupted write on both OSes.
- Residual risk: A database package or isolate/native bridge could introduce ordering, locking or migration behavior not visible in the shared widget code.
- Result: HELD.

### S7 — Camera, file and evidence capture

- Starting state: Permission is denied or granted; camera capture, photo-library selection or file import is attempted; process may be killed before return or upload.
- Allowed transition: Explain permission, allow retry/skip, validate type/size/content, stage a temporary item, bind an idempotent operation and expose upload/processing uncertainty.
- Candidate mechanism: Flutter camera/image/file wrappers around native CameraX/AVFoundation, Android Photo Picker and iOS PHPicker/UIDocumentPicker; owned export/share boundary remains separate.
- Official evidence: Flutter camera recipe, camera package, image_picker package and file_selector package document native plugin boundaries; image_picker documents process-loss recovery through retrieveLostData: https://docs.flutter.dev/cookbook/plugins/picture-using-camera, https://pub.dev/packages/camera, https://pub.dev/packages/image_picker and https://pub.dev/packages/file_selector.
- Reasoned inference: Endorsed Flutter packages reduce boilerplate but do not close permission, URI lifetime, metadata, native UI accessibility or process-death correctness.
- Dependency-specific evidence: camera 0.12.1, image_picker 1.2.3 and file_selector 1.1.0 are publisher-verified snapshots only; no lock or security scan.
- Unresolved facts: Accepted MIME/size rules, EXIF/privacy policy, temporary cleanup, permission edge cases, CameraX/AVFoundation behavior, share dependency and upload idempotency.
- User-visible result: Capture/import errors and permission denial have clear Turkish retry/skip paths; invalid or untrusted media is quarantined, not silently accepted.
- Failure/hold behavior: Lost, partial, oversized, corrupt or unscanned evidence holds the associated submission while retaining safe local recovery where possible.
- Recovery path: Use retrieve-lost-data/native recovery, retry or manual entry, clean only proven temporary copies and reconcile operation state.
- Shared-system obligation: Privacy, evidence provenance, consent, retention and no-loss policy are shared.
- Candidate-attributable work: Plugin wrappers, native permission/lifecycle bridges, file validation, semantics and process-death tests.
- Accountable AI/external owner: AI media implementer; Android/iOS media specialists, privacy/security reviewer and evidence owner.
- Required later real-device evidence: Permission deny/grant/reset, camera interruption, picker cancellation, process death, URI expiry, 3 MB/50-500 photo fixtures, low storage and TalkBack/VoiceOver native UI.
- Residual risk: Package APIs can make capture appear cross-platform while native permission and process-loss behavior remains OS-specific.
- Result: HELD.

### S8 — Accessible safety/readiness step

- Starting state: A Turkish critical step contains active instruction, readiness, warning, stop and recovery states.
- Allowed transition: Focus and announce the current state, expose all actions/labels/roles, preserve order at large text and non-color contrast, and make stop/recovery operable with assistive technology.
- Candidate mechanism: Flutter Semantics, focus/order APIs and accessibility-aware widgets, plus native permission, picker, notification and share UI where the OS owns the surface.
- Official evidence: Flutter accessibility overview, accessibility testing and assistive technologies document semantics, guideline APIs and TalkBack/VoiceOver/Switch/Voice Control considerations: https://docs.flutter.dev/ui/accessibility, https://docs.flutter.dev/ui/accessibility/accessibility-testing and https://docs.flutter.dev/ui/accessibility/assistive-technologies.
- Reasoned inference: First-class framework semantics are useful but are not a product pass; Turkish wording, dynamic state announcements and native surfaces require independent human/device oracles.
- Dependency-specific evidence: flutter_test/integration_test can exercise Flutter surfaces, while Flutter documents that native platform UI is outside integration_test interaction coverage.
- Unresolved facts: Final Turkish copy, focus order, minimum contrast/size, reduced-motion policy, native dialog announcements, AT device matrix and independent tester capacity.
- User-visible result: The operator can hear/read what is active, unsafe, stopped, unknown and recoverable without relying on color, gesture precision or a visual-only diagram.
- Failure/hold behavior: Any critical path failing AT or largest-text checks is held from release; no accessibility waiver is implied by a widget test.
- Recovery path: Return focus to a safe-stop/recovery control, preserve state and provide an alternate text/manual path.
- Shared-system obligation: Accessibility acceptance and Turkish-first safety copy are candidate-neutral gates.
- Candidate-attributable work: Semantics tree, focus management, platform-adaptive layout, native UI handoff and test instrumentation.
- Accountable AI/external owner: AI UI implementer; independent human AT testers and qualified safety/content reviewer.
- Required later real-device evidence: VoiceOver/TalkBack, Switch/Voice Control, largest text/reflow, dark/high contrast, reduced motion, permission/picker/share/notification native UI and all S1-S15 critical states.
- Residual risk: A framework-level semantics API can pass automated inspection while a real Turkish user cannot perceive or operate a time-critical state.
- Result: HELD.

### S9 — Framework, plugin and toolchain upgrade

- Starting state: Frozen comparison snapshot is Flutter 3.47.2/Dart 3.13.2; a newer stable/hotfix or package/native toolchain event is proposed.
- Allowed transition: Reproduce lockfile and artifact, review changelog and native graph, run scenario/accessibility/release evidence, then stage or refuse the upgrade with rollback criteria.
- Candidate mechanism: Pinned Flutter git ref/digest, pubspec.lock, checked-in Android/iOS host configuration, release graph and migration fixtures.
- Official evidence: Flutter SDK archive recommends stable for production and describes roughly quarterly stable windows; dependency management documents lockfile pinning; Swift Package Manager guidance says SwiftPM is default as of Flutter 3.44 and CocoaPods is in maintenance mode: https://docs.flutter.dev/install/archive, https://docs.flutter.dev/packages-and-plugins/dependency-management and https://docs.flutter.dev/packages-and-plugins/swift-package-manager/for-app-developers.
- Reasoned inference: Upgrade work spans Dart, Flutter engine, plugins, Android/Gradle/JDK, Xcode and SwiftPM; a shared UI does not make the release graph one-dimensional.
- Dependency-specific evidence: Current package snapshots have different minimum Flutter/Dart constraints; final transitive graph and platform implementation locks are absent.
- Unresolved facts: Upgrade cadence, security response SLA, exact toolchain, Mac access, compatibility policy, SwiftPM migration plan, rollback artifact and owner capacity.
- User-visible result: No silent SDK/package change; the user sees a held/staged release outcome and retains the last accepted artifact.
- Failure/hold behavior: Any scenario, migration, native or AT regression holds the upgrade; no production store submission is inferred.
- Recovery path: Keep frozen artifact, revert source/lock/toolchain together where safe, or perform a forward migration after review; do not rely on lossy rollback.
- Shared-system obligation: Version policy, provenance, release windows and safety correction apply to every candidate.
- Candidate-attributable work: Flutter/Dart upgrade testing, plugin migration, host project changes and artifact reproducibility.
- Accountable AI/external owner: AI upgrade implementer; Android/iOS build specialists, security reviewer and store custodian.
- Required later real-device evidence: At least the comparison Android/iPhone, all critical S1-S15 flows, AT matrix, signed staging build, dependency/license/SBOM diff and rollback rehearsal.
- Residual risk: Concentration in framework/plugins can turn a small Dart change into a platform/toolchain release event.
- Result: HELD.

### S10 — Mixed rollout of old/new clients

- Starting state: Old and new signed binaries, content generations, schema versions and server/API capabilities coexist.
- Allowed transition: Use explicit capability/generation negotiation, staged store artifacts and additive/forward migrations; fail closed for unknown safety semantics.
- Candidate mechanism: Release graph, capability table, versioned serializers and server-enforced minimums; no OTA binary replacement is assumed.
- Official evidence: Flutter deep linking requires native URL configuration and treats external URLs as untrusted; package locking only controls a given application build: https://docs.flutter.dev/ui/navigation/deep-linking and https://docs.flutter.dev/packages-and-plugins/dependency-management.
- Reasoned inference: Flutter's common source may reduce duplicate UI, but it cannot coordinate server capability, store rollout, old binaries or data meaning.
- Dependency-specific evidence: Android/iOS runner and signing projects are required; exact Gradle/Xcode/SwiftPM graph is unresolved.
- Unresolved facts: Compatibility window, minimum app version, schema negotiation, rollout pause controls, server contract and no-rollback conditions.
- User-visible result: Compatible work remains available; incompatible work shows a clear update/hold path and no fabricated status.
- Failure/hold behavior: Unknown or non-additive state is held per task/record; a rollout can be paused without erasing portable history.
- Recovery path: Keep old/new artifacts, reconcile once compatible, forward-migrate with backup and retain provenance; replace only through approved stores.
- Shared-system obligation: Mixed rollout and release integrity are candidate-neutral.
- Candidate-attributable work: Dart serialization/capability adapters, Flutter route/state compatibility and native build matrix updates.
- Accountable AI/external owner: AI release/data implementer; backend/content owner, store custodian and safety reviewer.
- Required later real-device evidence: Old/new installs, upgrade/downgrade refusal, offline queue replay, content generation mismatch, deep link cold start and store staged rollout.
- Residual risk: A plugin/native ABI change can break one platform despite source-level compatibility.
- Result: HELD.

### S11 — Low/mid-device and storage pressure

- Starting state: Fixture device is Android API 29, 64-bit, 4 GB RAM, 64 GB storage with 2 GB free; local stress includes 3/10 motorcycles, 250/2,000 records, 50/500 3 MB photos, 100/1,000 notes, 20/200 pending and 3/30 conflicts.
- Allowed transition: Load only selected compact content, paginate/stream heavy media, report space/memory pressure, evict cache only, and preserve user records/pending truth.
- Candidate mechanism: Flutter list/rendering and Dart repository with path_provider cache/support separation; database, image decode and native memory policy remain unselected.
- Official evidence: path_provider documents separate support/documents/cache locations; Flutter's architecture overview describes framework rendering and native embedders, but no Kavriva benchmark: https://pub.dev/packages/path_provider and https://docs.flutter.dev/resources/architectural-overview.
- Reasoned inference: Shared Flutter UI may reduce duplicated presentation work, but memory, image decoding, database locking and startup behavior must be measured on the specified devices.
- Dependency-specific evidence: path_provider 2.1.6 supplies paths only; camera/image_picker/file_selector do not prove large fixture performance.
- Unresolved facts: Peak memory, startup, scroll/render budget, image/downsample policy, database choice/indexes, cache eviction, thermal/battery impact and low-storage OS behavior.
- User-visible result: The user sees selected content, honest progress and a clear low-space/limited-media message; private notes and pending truth are not silently deleted.
- Failure/hold behavior: Exceeding a safety or integrity threshold holds optional work or the release; cache eviction cannot discard pending/authoritative records.
- Recovery path: Evict verified cache, reduce optional media, retry in foreground and reconcile; preserve/export portable records before any destructive migration.
- Shared-system obligation: Fixture limits, retention/privacy, no-loss and safe degradation are common.
- Candidate-attributable work: Rendering/data pagination, image pipeline, native memory profiling and low-storage instrumentation.
- Accountable AI/external owner: AI performance implementer; Android/iOS performance specialists, data/security owner.
- Required later real-device evidence: Cold/warm startup, all local stress fixtures, low storage, thermal/rotation/background, image decode, DB recovery and accessibility at largest text.
- Residual risk: A cross-platform renderer can conceal device-specific jank or memory pressure until the acceptance run.
- Result: HELD.

### S12 — Release, incident and pause

- Starting state: A staged Android/iOS artifact is proposed; a dependency, safety correction, store review or incident requires pause, impact assessment or recovery.
- Allowed transition: Verify source/ref/lock/SBOM/signature/provenance, stage both stores independently, pause rollout, identify affected generations and preserve provider-independent artifacts.
- Candidate mechanism: Flutter CLI plus Android Gradle and Xcode/SwiftPM host projects, reproducible artifact manifest and explicit release graph; no store submission is claimed.
- Official evidence: Flutter archive records release refs/Dart versions; package dependency guidance requires lockfile discipline; Android and Apple native build/signing remain platform responsibilities: https://docs.flutter.dev/install/archive and https://docs.flutter.dev/packages-and-plugins/dependency-management.
- Reasoned inference: Flutter provides a common build entry point, but signing identities, Mac/Xcode, store policy, native plugins and incident response remain external or platform-specific.
- Dependency-specific evidence: No CI, Mac host, signing account, plugin lock, SBOM or attestation is present in this dossier.
- Unresolved facts: CI/build provider, Mac availability, Xcode/Gradle/JDK versions, signing custody, store review timing, artifact retention, incident authority and cost.
- User-visible result: Release/hold state is truthful; affected content or app paths show safe pause/recovery rather than an optimistic updated claim.
- Failure/hold behavior: Missing provenance, failed AT/device/safety evidence, signature issue or critical incident blocks the store release and can pause a staged rollout.
- Recovery path: Retain last accepted artifact, revoke/limit affected content by authority, issue reviewed correction and restore only after evidence; no unapproved OTA binary path.
- Shared-system obligation: Release integrity, safety correction, audit and pause controls are common.
- Candidate-attributable work: Host-project configuration, Flutter artifact reproducibility and plugin/native release coordination.
- Accountable AI/external owner: AI release implementer; owner/store accounts, security custodian, qualified safety reviewer and native build operators.
- Required later real-device evidence: Signed staging artifacts on both stores/platforms, clean install/upgrade, pause and rollback/forward-migration drill, provenance verification and incident communication.
- Residual risk: A single cross-platform command can create false confidence while one store or native host remains unverified.
- Result: HELD.

### S13 — Privacy, collaboration and device trust

- Starting state: Private notes/photos, shared/community material and official/safety material exist in distinct scopes; device may be restored, cloned, lost or shared.
- Allowed transition: Enforce scope and authorization, protect keys, label provenance, re-authenticate after restore/key mismatch and quarantine untrusted state.
- Candidate mechanism: Portable records plus owned Android Keystore/iOS Keychain adapters; Flutter stores no raw key authority and does not decide current entitlement.
- Official evidence: Flutter plugins bring host code; Android Auto Backup includes app data by default with cache exclusions and a 25 MB cloud quota, while backup timing/restore conditions are system-controlled: https://docs.flutter.dev/packages-and-plugins/using-packages and https://developer.android.com/identity/data/autobackup.
- Reasoned inference: A Flutter data model can separate scopes, but key protection, backup exclusion and authorization are native/account boundaries.
- Dependency-specific evidence: No encryption/auth package or key adapter is selected; path_provider is not a security primitive.
- Unresolved facts: Key hierarchy/rotation, iOS backup/Keychain semantics, Android include/exclude rules, clone detection, shared-content ACLs, deletion/export policy and re-auth flow.
- User-visible result: Private/shared/official labels, lock/re-auth/quarantine and disclosure warnings are explicit and accessible; a restored item is not silently trusted.
- Failure/hold behavior: Key/authority mismatch holds protected action and preserves safe portable metadata without exposing plaintext.
- Recovery path: Re-authenticate, re-download/re-encrypt under current authority, preserve audit/provenance and revoke invalid device/session authority.
- Shared-system obligation: Privacy, authorization, key loss, backup and deletion rules are product-wide.
- Candidate-attributable work: Typed native security boundary, scope-aware state/semantics and restore/clone test harness.
- Accountable AI/external owner: AI security/data implementer; qualified security/privacy reviewer, account authority and Android/iOS key specialists.
- Required later real-device evidence: Backup/restore, device-to-device transfer, app clone, key rotation/loss, uninstall/reinstall, permission reset and AT for private/shared labels.
- Residual risk: OS backup can preserve stale data or omit key material; incorrect reconciliation may disclose or lose private truth.
- Result: HELD.

### S14 — Entitlement, evidence and lifecycle change

- Starting state: Entitlement, publication, correction, withdrawal, transfer or delete authority changes while a task is active or offline.
- Allowed transition: Preserve the last durable safe checkpoint, evaluate current authority when available, block withdrawn/ineligible actions and retain audit/provenance; never erase history to hide a correction.
- Candidate mechanism: Domain state machine and repository reconciliation independent of widgets, with lifecycle signals and native notification/deep-link hints only as accelerators.
- Official evidence: Flutter lifecycle documentation warns that notifications may be skipped; offline-first guidance requires local/remote repository responsibility. Neither framework API defines Kavriva entitlement or safety semantics: https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html and https://docs.flutter.dev/app-architecture/design-patterns/offline-first.
- Reasoned inference: Flutter can present a deterministic state machine, but authority and lifecycle correctness are backend/product/native concerns.
- Dependency-specific evidence: No entitlement, remote push or subscription plugin/provider is selected; notification permission and scheduling are platform-dependent.
- Unresolved facts: Entitlement source/TTL, offline grace, withdrawal timing, transfer/delete policy, active-task safety semantics and server reconciliation contract.
- User-visible result: The user sees active/held/withdrawn/transferred/needs-review states with a safe-stop path and clear Turkish explanation.
- Failure/hold behavior: Authority uncertainty or withdrawal blocks the affected action; an in-flight operation is unknown/partial until reconciled, not marked complete.
- Recovery path: Reconnect/re-authenticate, reconcile idempotently, preserve prior evidence and apply reviewed correction/transfer/delete rules.
- Shared-system obligation: Authorization, publication, audit, safety and retention are framework-neutral.
- Candidate-attributable work: State presentation, reconciliation adapters, lifecycle persistence and native notification/deep-link plumbing.
- Accountable AI/external owner: AI state implementer; product/authorization owner, qualified safety reviewer and privacy/legal authority.
- Required later real-device evidence: Entitlement changes during foreground/background, notification denied, cold deep-link, process kill, offline grace expiry and correction/withdrawal.
- Residual risk: A smooth shared UI may hide a server-authority race or leave a native notification as an accidental source of truth.
- Result: HELD.

### S15 — Backup, restore, clone and key loss

- Starting state: App backup/restore, device-to-device clone, reinstall or protected-key loss occurs with local packages, history, pending operations and private media present.
- Allowed transition: Classify restored data, validate account/device/key/content generations, quarantine mismatches, re-authenticate and re-download non-portable material; restore only the last durable committed checkpoint.
- Candidate mechanism: Portable schema and manifests plus native backup rules, key adapters and explicit restore reconciliation; Flutter does not treat backup as current authority.
- Official evidence: Android Auto Backup covers API 23+, normally includes databases/files, excludes cache, has a 25 MB per-app cloud quota and does not guarantee schedule; restored URI/tokens can be stale or device-specific. Apple backup/Keychain policy remains a separate native review: https://developer.android.com/identity/data/autobackup.
- Reasoned inference: Flutter can share restore status and migration UI, but OS backup/key behavior and key continuity cannot be inferred from Dart code.
- Dependency-specific evidence: No backup/encryption package is selected; path_provider and Flutter offline-first guidance do not establish restore semantics.
- Unresolved facts: iOS backup/key behavior, Android include/exclude configuration, key hierarchy, clone detection, pending operation replay, media retention, quota impact and recovery authority.
- User-visible result: Restored/partial/quarantined/re-auth states are explicit; the user is not told that a stale restored entitlement or token is current.
- Failure/hold behavior: Key loss, generation mismatch, corrupt database or replay ambiguity holds protected actions and preserves safe export/portable records where permitted.
- Recovery path: Re-authenticate, forward-migrate after validation, re-download compact content, re-encrypt under current keys and retain audit; do not fabricate recovery or silently discard history.
- Shared-system obligation: Data continuity, backup, privacy, deletion and authority reconciliation are common.
- Candidate-attributable work: Restore state machine, native key/backup adapters, migration fixtures and accessible quarantine/recovery UX.
- Accountable AI/external owner: AI data/security implementer; Android/iOS backup specialists, security reviewer, account authority and privacy/legal owner.
- Required later real-device evidence: API 29/current Android and comparison iPhone backup/restore, clone, reinstall, key rotation/loss, corrupted DB, pending replay, media and largest-text/AT scenarios.
- Residual risk: A successful OS restore can still be a semantically stale or cryptographically unusable state; the user-facing recovery must remain conservative.
- Result: HELD.

## 6. Accessibility Matrix

This is a capability-and-evidence matrix, not an accessibility approval. Flutter documents framework semantics and
testing APIs, but native dialogs and real assistive technologies still require independent device acceptance.

| Surface/oracle | Framework/documented capability | Platform-specific work | Later real-device oracle | Status |
|---|---|---|---|---|
| VoiceOver | Semantics, labels, roles, focus and state announcements are framework mechanisms | iOS native picker, permission, notification, share and universal-link surfaces | VoiceOver through active, warning, stop, recovery, conflict and restore states | HELD |
| TalkBack | Semantics and accessibility guideline APIs are documented | Android permission, Photo Picker, notification, share and intent surfaces | TalkBack through the same critical states and process interruptions | HELD |
| Largest text/reflow | Flutter layout/text widgets can adapt; no product layout pass exists | iOS Dynamic Type and Android font-scale/large-display behavior | Largest supported text, clipping, truncation, scroll and diagram alternatives | HELD |
| Focus and reading order | Semantics tree and focus/order APIs are available | Native surface return focus and back navigation must be specified | Keyboard/switch/AT focus across every safety transition | HELD |
| State announcements | Flutter can expose live/state semantics | Platform notification/deep-link arrival and permission result need native checks | Turkish active/readiness/warning/unknown/stop/recovery announcements | HELD |
| Non-color status and contrast | Framework widgets can provide text/semantics and color-independent states | Native controls and system contrast settings | Contrast, dark/high-contrast, color-blind and diagram/text alternatives | HELD |
| Reduced motion | Flutter animation policy can be controlled by product code | OS reduce-motion signal and native transitions need integration | Reduced-motion mode during warnings, stop, navigation and media | HELD |
| Switch/Voice Control | Flutter semantics exposes controls to platform AT | Native camera/file/share/permission controls need platform verification | Switch scanning, Voice Control labels, no gesture-only critical action | HELD |
| Reduced dexterity / touch | Larger controls and alternate paths are framework design work | System back, interruption, picker cancellation and share return | One-hand/touch target, timeout, cancel/retry and safe-stop operation | HELD |

No row is PASS. Automated widget/integration evidence cannot substitute for independent human AT review, especially
because Flutter documents that native platform UI is not interactable through integration_test.

## 7. Upgrade and Forced-Event Walkthrough

| Event | Flutter path under the fixture | Evidence and affected contracts | External dependency/capacity | Hold/recovery |
|---|---|---|---|---|
| Planned quarterly release | Re-pin SDK/Dart/ref/digest, review pub lock and native host graph, run S1-S15/AT/device/release evidence, then stage stores | Archive describes stable production channel and roughly quarterly windows; Flutter 3.47.2 is frozen despite current JSON drift to 3.47.4 | Android SDK/AGP/Gradle/JDK, macOS/Xcode, SwiftPM, devices, AT/safety reviewer and release custodian | HOLD until graph and evidence exist; retain prior artifact and forward-migrate only after review |
| Safety/security correction | Prefer content revocation/authority correction through approved server/store paths; binary correction follows the same signed release graph | Offline generation, recall, audit, signing and no-OTA rules are affected; notifications are not current authority | Qualified safety reviewer, security custodian, store accounts and incident authority | Pause affected generation/release, safe-stop offline, publish reviewed correction and reconcile |
| Forced Apple/Google build/store requirement | Update host project/toolchain and rebuild Flutter artifact; re-run native/AT/migration evidence | Store target/build rules are external; iOS requires macOS/Xcode access; Android native graph can change | Mac/Xcode/signing and store access; exact current requirements and cost are UNRESOLVED | HOLD on missing host/custodian; keep provider-independent source/lock/artifacts |
| Critical dependency abandonment | Replace camera/media/transfer/security plugin or move boundary into owned Kotlin/Swift adapter; update lock/SBOM | Plugin host code and platform APIs are part of release closure; package pages do not establish EOL response | Native specialists, security review, package maintenance/provenance and device lab | Quarantine affected capability, keep manual safe path if safe, migrate forward; no silent substitution |
| Old/new client/API/schema/content/config coexistence | Use capability/generation matrix, additive/forward serializers and staged store rollout; reject unknown safety meaning | Lockfile pins one build only; old signed binaries remain; deep links/notifications are untrusted accelerators | Backend/content owner, store custodian, safety reviewer and rollback authority | Hold incompatible record/path; maintain last accepted artifact and migrate forward |
| Migration rollback refusal | Refuse lossy downgrade; preserve backup/provenance and use forward migration after review | Local DB/key/schema behavior is not selected; no rollback claim can be made | Data/security reviewer and restore game-day capacity | HOLD if downgrade is required; quarantine and recover from last durable checkpoint |
| Incident pause, impact and recovery | Use artifact manifest/release graph to identify platform/package/content generations; pause rollout and communicate | Provenance/SBOM/signing, platform release and safety correction contracts converge | Incident commander, security/safety/content/store authorities | No production pass; suspend, preserve evidence, issue reviewed correction and re-test |

Flutter's official Swift Package Manager guidance records that SwiftPM became the default as of Flutter 3.44 and that
the CocoaPods registry becomes read-only on 2026-12-02: https://docs.flutter.dev/packages-and-plugins/swift-package-manager/for-app-developers.
The consequence is a real forced-event candidate, not a numeric cost estimate: exact migration timing, toolchain
versions, ownership and price remain UNRESOLVED. No OTA binary authority is assumed.

## 8. AI-Operability and Task Isolation

| Operating requirement | Flutter evidence-shaped path | Missing proof / boundary | Status |
|---|---|---|---|
| Bounded task context | Separate Dart UI/domain/data contracts and the native closure table can make TASK work units explicit | No implementation repository, task graph, contract tests or reviewer run exists | HELD |
| Exceptions visible | Platform channels and host projects make Kotlin/Swift exceptions enumerable in principle | Final plugin/native inventory, owner, fallback and source review are absent | HELD |
| Separate implementation, review and validation | Flutter test layers plus independent native/AT/device/safety review can be separated | No task ownership, reviewer capacity, real-device oracle or signed evidence exists | HELD |
| Deterministic build | SDK git ref/digest, Dart version and pubspec.lock can pin a build; native host versions must also be pinned | Lockfile, Android/iOS host projects, Gradle/JDK/SwiftPM/CI pins do not yet exist | HELD |
| Dependency impact visible | Pub lock, SBOM and platform implementation graph can be attached to each task/release | Package transitive graph, licenses, EOL and provenance are unresolved | HELD |
| Recovery without opaque workstation/provider | Android artifacts can be produced from a controlled environment; source/lock/manifests can be portable | iOS macOS/Xcode/signing and store authority are external; backup host and cost are unknown | HELD |
| Nontechnical owner protected | AI can produce bounded artifacts and explanations; owner need not code or debug | Someone still must own store identity, signing, devices, AT, safety, security and incident decisions | HELD |
| No hidden mutation | No-code Phase 4 keeps dossier/documentary work separate from app mutation | There is no executed build or prototype to prove isolation | HELD |

The largest AI-operability benefit is one shared Dart presentation/domain surface and portable scenario contracts.
The largest risk is that a visually unified surface hides native lifecycle, permission, signing, accessibility or
dependency exceptions. Every such exception remains a separate accountable work item. The nontechnical owner is not
assumed to code, debug or repair a build.

## 9. Equal 24-Month TCO Worksheet

### 9.1 Workload quantities (not prices)

The following are fixture quantities for equal comparison only. They are not forecasts, retention commitments or
provider quotes. At the illustrative per-MAU/month workload of two 12 MB compact transfers, optional media for 10% of
MAU at 100 MB, and 0.5 photos at 3 MB:

| MAU tier | Compact transfer bytes/month | Optional media bytes/month | Photo upload bytes/month | Retained photo bytes over 24 months if never evicted |
|---:|---:|---:|---:|---:|
| 1,000 | 24 GB | 10 GB | 1.5 GB | 36 GB |
| 10,000 | 240 GB | 100 GB | 15 GB | 360 GB |
| 50,000 | 1.2 TB | 500 GB | 75 GB | 1.8 TB |

These quantities exclude protocol overhead, retries, thumbnails, backups, regional replication, egress, logs and
provider-specific billing units. Local-device stress fixtures are not multiplied by MAU. A retention policy is
UNRESOLVED; the retained-photo column is a scenario quantity, not a promise.

### 9.2 Cost categories

Unknown amount means UNRESOLVED, never zero. No provider, plan, currency conversion, tax, discount or human hourly
rate is invented here.

| Cost row | Product-wide unavoidable | Candidate-caused | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---|---|---|---|---|---|---|
| Store membership | Both planned stores | None specific to Flutter | None | Apple renewal/tax/currency | Preserve accounts/artifact history | Buy only when test/release gate requires | Google USD 25 once + Apple USD 99/year; 24-month store-only USD 124–223 before tax/currency/renewal timing / High for frozen fixture |
| Mac/hosted iOS build | iOS release requires Mac/Xcode path | Flutter iOS host/plugin build closure | Hosted build convenience | More builds and forced events | Backup Mac/host path | Existing/borrowed local Mac preferred | UNRESOLVED / Low |
| Android/iPhone access | Four-cohort real-device/AT evidence | Flutter/plugin/native integration coverage | Device lab | Release/device breadth | Borrowed/replacement devices | Existing/borrowed devices/testers | UNRESOLVED / Low |
| CI/build artifacts | Reproducible signed evidence | Flutter SDK + Android/iOS host graph | Hosted CI/cache | Build frequency/storage | Portable rebuild/archive | Local/provider-independent artifacts | UNRESOLVED / Low |
| Backend/database | Product-wide authority/history | No Flutter provider selected | Managed convenience | MAU/operations | Export/rebuild | Capped tier with alerts/shutdown/export | UNRESOLVED / Low |
| Storage/backup/CDN/egress | Product-wide continuity/delivery | No Flutter-specific provider | CDN/replication convenience | Frozen MAU/media workload | Export/eviction/migration | Compact scope, quotas and alerts | UNRESOLVED / Low |
| Identity/email/SMS | Product-wide account/recovery | Flutter bindings/client states | SMS/provider convenience | MAU/recovery rate | Manual/exported recovery | Approved email/manual path with caps | UNRESOLVED / Low |
| Crash/telemetry/analytics | Privacy-safe diagnostics if approved | Flutter/native exception visibility | Hosted dashboards | Events/retention | Export/provider replacement | Disabled or capped/free path | UNRESOLVED / Low |
| Security/SBOM/signing | Product-wide assurance | Flutter SDK/plugin/host provenance | Paid scanning convenience | Dependency/build cadence | Key recovery/replacement plugin | Owned lock/SBOM/attestation | UNRESOLVED / Low |
| Accessibility validation | Human four-cohort AT evidence | Flutter semantics plus native surfaces | Device lab | Each release/forced event | Alternate accessible safe path | Organized testers/borrowed devices | UNRESOLVED / Low |
| Safety/content review | Qualified product-wide authority | None specific to Flutter | External review capacity | Releases/corrections | Hold/recall/re-review | No AI-only substitute | UNRESOLVED / Low |
| AI implementation/review | Separate implement/review/validate capacity | Dart/Flutter plus native-boundary contexts | Paid model/tool convenience | Task/release volume | Alternate agent/tooling | Bounded tasks and current approved plans | UNRESOLVED / Low |
| Upgrade/dependency response | Store/OS changes affect all | Flutter/Dart/plugin and host alignment | Specialist support | Quarterly/forced events | Pin/replace/owned native path | Stable pin plus portable evidence | UNRESOLVED / Low |
| Support/incident response | Product-wide support/authority | Flutter/native/plugin diagnosis surface | Contracted support | Users/releases/incidents | Pause/recovery/provider exit | Staged rollout and owned evidence | UNRESOLVED / Low |
| Exit/migration | Preserve product truth | Flutter widgets/runtime/plugins/hosts replacement | Migration assistance | Data/users at exit | Forward migration and replacement release | Portable schemas/manifests/tests | UNRESOLVED / Low |

Flutter-specific TCO is therefore not a price claim. Shared Dart UI/domain work may reduce routine parity effort,
while plugin/native closure, Android/iOS device acceptance, Mac/Xcode/signing and upgrade coverage remain real capacity
burdens. Any unapproved OTA line is disabled and remains UNRESOLVED, not zero.

## 10. Exit Dossier

### Portable or replaceable assets

- Canonical schemas, history/provenance records, corrections, publication/revocation generations, operation IDs and
  migration fixtures should be framework-neutral.
- Content manifests, digests, compact-package boundaries, safety/recovery closure and optional-media metadata should be
  consumable by another client.
- User-controlled export/share formats, Turkish copy keys, design/accessibility intent, S1-S15 fixtures and acceptance
  oracles should survive a renderer change.
- Forward migrations must be explicit, versioned and rehearsed; an old signed client remains contained by the server
  capability/content graph.

### Framework-, plugin- or toolchain-bound assets

- Dart widgets/state runtime, Flutter engine/rendering, Flutter plugin APIs, Android/iOS runner projects, Gradle/JDK,
  Xcode/SwiftPM configuration and signed binaries are bound to the candidate or its host toolchain.
- Camera, file picker, notification, deep link, share, lifecycle, secure key and background-transfer adapters are
  native/plugin boundaries, not portable business truth.
- Android Keystore/iOS Keychain keys are not portable user data. Key loss requires quarantine, re-authentication and
  re-encryption; it must not be fixed by exporting raw keys.

### Migration, interruption and cost

- A replacement candidate can consume the canonical data/manifests through a dual-format or forward migration path;
  no lossy rollback or silent history rewrite is allowed.
- The interruption plan is to retain the last accepted Flutter artifact, keep portable records/export, pause affected
  content/release, and reconcile only after the replacement is reviewed and signed.
- Exact exit effort, interruption duration, migration tooling, replacement support and cost are UNRESOLVED. No exit
  success or portability pass is claimed.

## 11. Candidate Result (Phase-4 Research)

| Mandatory gate | Flutter record | Status |
|---|---|---|
| Safety/readiness and truthful uncertainty | State-machine shape is expressible; no implementation or qualified safety evidence | HELD |
| Offline scoped delivery and 72-hour behavior | Official offline-first/background evidence exists; package/atomic/resume proof is absent | HELD |
| Native closure and lifecycle/restart | Platform channels and lifecycle APIs are documented; native adapters and kill/restart proof are absent | HELD |
| Accessibility and Turkish critical flow | Semantics/AT guidance exists; independent real-device/human oracle is absent | HELD |
| Release, signing, provenance and forced events | SDK snapshot/archive evidence exists; lock/host/signing/store graph is absent | HELD |
| Data continuity, backup/restore and key loss | Android backup facts are documented; iOS/key/schema game-day evidence is absent | HELD |
| AI-operability and task isolation | Boundaries can be specified; no executable task/review/build evidence exists | HELD |
| 24-month TCO and owner capacity | Store baseline is approved; all other prices/capacity/provider selections are unresolved | HELD |
| Exit/migration and replacement continuity | Portable-asset plan is defined; migration rehearsal and replacement evidence are absent | HELD |

Scenario count: 0 PASS / 15 HELD / 0 REJECT. No real-device pass, store pass, accessibility pass, benchmark,
security pass or safety approval is claimed.

### Critical unresolved facts

- Product support policy, exact minimum OS/build floors, lifecycle/recovery semantics and offline recall validity.
- Final Flutter/Dart/toolchain ref, artifact digest, Android SDK/AGP/Gradle/JDK, macOS/Xcode/SwiftPM and store matrix.
- Committed direct/transitive dependency lock, native implementation graph, provenance/license/SBOM, EOL/security
  response and owned fallback for camera, media, transfer, share, notification, key and lifecycle boundaries.
- Transactional local database, schema/migration, account/entitlement/conflict contract, backup/restore/key semantics
  and portable export format.
- Physical Android/iPhone access, VoiceOver/TalkBack and other AT reviewers, independent safety/content reviewer,
  release/signing/store custodian, Mac access and incident authority.
- AI task/review capacity, cash ceiling, optional service approvals and current provider quotes; no numeric amount is
  assumed for these unresolved lines.
- Mixed old/new client/API/content/config release graph, pause/rollback refusal and correction/withdrawal protocol.

### Conditional interpretation

The largest low-budget burden is qualitatively the iOS macOS/Xcode/signing path together with physical-device,
accessibility, safety review and native/plugin upgrade coverage. The largest AI benefit is shared Dart UI/domain
surface and portable contracts; the largest AI risk is hidden native lifecycle/plugin/toolchain exception work.

External authorities remain required for Apple/Google legal identity and store accounts, Mac/Xcode/signing, physical
devices/testers/AT, qualified safety/content review, security/privacy, tax/legal/payment and any selected service
provider. No framework recommendation is made. A later recommendation would require complete native closure, pinned
toolchain/dependency/provenance, evidence for all S1-S15, AT/device/safety/release oracles, owner/capacity/TCO approval
and independent review. A rejection would be triggered by an ownerless critical path, unsafe bypass, unbounded
unapproved cost, lost canonical truth or unsupported capability without a safe fallback; none is asserted as an
intrinsic Flutter rejection here, but all gates remain HELD.

Overall Phase-4 disposition: DRAFT / RESEARCH / HELD.

## Source Register

Official/primary sources consulted for this dossier (retrieved 2026-09-17):

- Flutter supported deployment platforms: https://docs.flutter.dev/reference/supported-platforms
- Flutter SDK archive and release cadence: https://docs.flutter.dev/install/archive
- Flutter release metadata: https://storage.googleapis.com/flutter_infra_release/releases/releases_windows.json
- Flutter architectural overview: https://docs.flutter.dev/resources/architectural-overview
- Flutter offline-first architecture: https://docs.flutter.dev/app-architecture/design-patterns/offline-first
- Flutter platform channels: https://docs.flutter.dev/platform-integration/platform-channels
- Flutter AppLifecycleState: https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html
- Flutter accessibility: https://docs.flutter.dev/ui/accessibility
- Flutter accessibility testing: https://docs.flutter.dev/ui/accessibility/accessibility-testing
- Flutter assistive technologies: https://docs.flutter.dev/ui/accessibility/assistive-technologies
- Flutter integration testing: https://docs.flutter.dev/testing/integration-tests
- Flutter testing overview and plugin testing: https://docs.flutter.dev/testing/overview and https://docs.flutter.dev/testing/plugins-in-tests
- Flutter deep linking: https://docs.flutter.dev/ui/navigation/deep-linking
- Flutter camera recipe: https://docs.flutter.dev/cookbook/plugins/picture-using-camera
- Flutter package usage/dependency management: https://docs.flutter.dev/packages-and-plugins/using-packages and https://docs.flutter.dev/packages-and-plugins/dependency-management
- Flutter Swift Package Manager for app developers: https://docs.flutter.dev/packages-and-plugins/swift-package-manager/for-app-developers
- Flutter camera, image_picker, path_provider and file_selector package pages: https://pub.dev/packages/camera, https://pub.dev/packages/image_picker, https://pub.dev/packages/path_provider and https://pub.dev/packages/file_selector
- Flutter package source manifests: https://github.com/flutter/packages/blob/main/packages/camera/camera/pubspec.yaml, https://github.com/flutter/packages/blob/main/packages/image_picker/image_picker/pubspec.yaml, https://github.com/flutter/packages/blob/main/packages/path_provider/path_provider/pubspec.yaml and https://github.com/flutter/packages/blob/main/packages/file_selector/file_selector/pubspec.yaml
- Android Doze/standby: https://developer.android.com/training/monitoring-device-state/doze-standby
- Android persistent background work: https://developer.android.com/develop/background-work/background-tasks/persistent
- Android Auto Backup: https://developer.android.com/identity/data/autobackup
- Apple background strategies: https://developer.apple.com/documentation/BackgroundTasks/choosing-background-strategies-for-your-app
- Internal controls: AI_START_HERE, CURRENT_STATE, SOURCE_OF_TRUTH, PROJECT_CHAT_INSTRUCTIONS, DECISION_LOG/DEC-0031,
  the approved common fixture, MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO and CANDIDATE_DOSSIER_TEMPLATE.
