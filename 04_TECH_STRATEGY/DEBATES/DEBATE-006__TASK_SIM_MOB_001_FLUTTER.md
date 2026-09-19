# DEBATE-006 — TASK-SIM-MOB-001 — Flutter

Status: `STRUCTURALLY COMPLETE NO-CODE TASK SIMULATION / UNREVIEWED / HELD`  
Date: 2026-09-18  
Candidate: Flutter shared Dart UI/application surface with explicit Android/Kotlin and iOS/Swift native boundaries  
Frozen snapshot: Flutter 3.47.2 stable, bundled Dart 3.13.2, official Windows release ref d3b14c876900e553bc736ca19295fc09e3853e8e, artifact digest recorded in the Flutter dossier  
Purpose: simulate how a fresh AI would safely plan one identical Kavriva change without reading the whole project or writing code  
Decision boundary: documentary Phase-4 evidence only; no prototype, estimate, benchmark, code, signed build, store release, real-device pass, assistive-technology pass, or recommendation

This simulation is deliberately bounded to the common TASK-SIM-MOB-001 fixture. It does not select a database,
serialization format, camera implementation, background-transfer implementation, hosted build, CI provider, backend,
identity provider, telemetry provider, AI provider or OTA authority. An unresolved critical item is HELD, never silently
treated as zero risk, zero cost or completed work.

## 1. Simulation purpose and control constraints

The simulated change is one safety-critical active-maintenance step. The goal is to show the minimum context a fresh AI
would need, the exact places where Flutter work splits into shared Dart and native Android/iOS work, and the evidence
that must exist before the owner can accept an outcome.

The nontechnical owner is an outcome and risk approver. The owner is not assumed to code, debug, repair a build,
operate a signing chain, certify accessibility, certify safety, or substitute for a store/device/provider authority.

The simulation carries the following controls without relaxation:

- DEC-0028: narrow contracts, explicit ownership, allowed/forbidden scope, acceptance and negative cases, validation
  evidence, and bidirectional requirement-to-task-to-test traceability.
- DEC-0029: bounded AI task execution, deterministic tooling, visible native exceptions, independent implementation,
  review and validation, and explicit external authority.
- DEC-0030: separate mandatory, deferrable, optional and scale-triggered costs; no unapproved paid service; no invented
  price; free/capped paths require cap, overage, alert, export and exit evidence.
- DEC-0031: one common fixture for all candidates; four device cohorts; real-device, assistive-technology and qualified
  safety evidence cannot be replaced by simulation or AI.
- DEBATE-006 common fixture: scoped offline packages, compact safety/recovery closure, explicit durable checkpoint,
  truthful unknown/partial state, foreground reconciliation, no OTA code authority and no background-correctness claim.

No motorcycle-specific torque, part, fitment or safety value is invented. The task only defines state and evidence
behavior around an approved package.

## 2. Fixed starting state and required outcome

### 2.1 Starting state

- Motorcycle, model year and variant context is resolved.
- One approved task-package generation is installed and within its permitted offline window.
- Compact required closure is locally available; optional heavy media is absent.
- Account-light local history exists.
- Camera permission is not granted.
- The network changes from constrained cellular to offline after the step opens.
- A photo is captured, then the OS terminates the process before the next explicit checkpoint commits.
- After restart, the package remains locally intact and no new server recall knowledge is available.
- Screen reader is enabled and the largest-text path is used.

### 2.2 State truth that the simulation must preserve

| Moment | Required truth and user-visible behavior |
|---|---|
| Step opens | Objective, warning, readiness state and safe-stop/recovery are available offline. |
| Camera denied | The optional-photo path is explained accessibly; the step remains usable without a photo. |
| Photo captured | The photo is pending evidence only. It is not verification, physical truth or a durable checkpoint by itself. |
| Process termination before checkpoint | Temporary/photo work may be recoverable or discarded; physical progress is unknown/partial. |
| Restart | Only the last durable explicit checkpoint restores as context. The app never auto-continues. |
| Revalidation | Current physical observations are explicitly confirmed through accessible controls before continuation. |
| Revalidation fails or is uncertain | The step remains HELD; safe-stop and recovery remain available. |
| Revalidation succeeds | The next permitted transition opens and a new explicit checkpoint may commit. |
| Reconnection | Foreground reconciliation checks package generation, client capability, release/configuration and recall eligibility before further authority. |

### 2.3 Fixed comparison quantities

The required compact package is at most 12 MB and optional media is at most 150 MB. Unrelated 2 GB catalog content is
not downloaded. The offline-content cache target is 250 MB excluding user history/photos; a cellular transfer above
25 MB requires explicit user choice. Device stress uses the common 3/10 motorcycle, 250/2,000 record, 50/500 3 MB
photo, 100/1,000 note, 20/200 pending-change and 3/30 deliberate-conflict fixtures. These are comparison fixtures,
not implementation results or performance promises.

## 3. Flutter boundary used by the simulation

### 3.1 Shared and native ownership

- Shared Dart owns product state contracts, Turkish copy keys, readiness and safe-stop semantics, package-generation
  compatibility, durable-checkpoint intent, conflict outcomes, and shared widget/presentation state.
- Flutter widgets and Semantics express the shared presentation surface. Material/Cupertino and platform adaptations
  are mechanisms, not final Kavriva design tokens or accessibility approval.
- Android/Kotlin owns Android permission, camera/picker, lifecycle, background-transfer adapter, secure storage,
  notification/deep-link and backup behavior.
- iOS/Swift owns iOS permission, camera/picker, lifecycle, background-transfer adapter, Keychain, notification/
  universal-link and backup behavior.
- The Flutter plugin/channel boundary is Kavriva-owned. A plugin is never the product authority and an unnamed
  critical plugin remains HELD.
- Server authority owns current eligibility, recall/withdrawal, publication, authorization, content generation and
  correction meaning. A cached package or restored local state cannot mint current authority.
- Internal Data & Content Operations remains a separate browser trust boundary. No shared Flutter/browser code path is
  assumed by this simulation.

### 3.2 Exact evidence snapshot and known drift

The frozen comparison snapshot is Flutter 3.47.2/Dart 3.13.2. The dossier records that official release metadata also
lists stable 3.47.4, while the documentation snapshot still reflects 3.47.2. This simulation does not silently
replace the frozen snapshot. A later decision must re-pin SDK ref, Dart version, artifact digest, Android toolchain,
macOS/Xcode/SwiftPM and dependency lock together.

The candidate dossier records Flutter team package snapshots camera 0.12.1, image_picker 1.2.3, path_provider 2.1.6,
file_selector 1.1.0 and other platform candidates. These are evidence snapshots, not an approved dependency closure.
No final database, serialization, share, notification, background-transfer or key package is selected.

## 4. Fresh-AI context topology

### 4.1 Minimum distinct context types

A fresh AI cannot safely treat this as one Dart screen task. The minimum context model is fourteen distinct types, with
cross-cutting dependency/provenance and authority fields attached to each packet:

| Context ID | Context type | Why it is distinct in Flutter |
|---|---|---|
| C0 | Governance and fixture | Controls the no-code boundary, common constants, owner limits and failure conditions. |
| C1 | Product authority/state | Defines durable checkpoint, unknown/partial physical state, readiness, safe-stop, recall and revalidation truth. |
| C2 | Design/presentation/accessibility | Defines Turkish copy, roles, focus/order, contrast, largest text, reduced motion and safe recovery presentation. |
| C3 | Dart domain and UI state | Contains shared Flutter widget/state transitions and pure domain behavior, without native authority. |
| C4 | Local persistence/migration | Contains transaction, checkpoint, schema, conflict, restore and forward-migration rules; the final DB is unresolved. |
| C5 | Camera/media/privacy | Contains optional-photo semantics, permission, temporary file, picker, type/size, privacy and upload evidence. |
| C6 | Android native lifecycle/accessibility | Contains Android host/channel behavior, process death, permission/picker, TalkBack and Android backup/lifecycle. |
| C7 | iOS native lifecycle/accessibility | Contains iOS host/channel behavior, process death, permission/picker, VoiceOver and Keychain/backup/lifecycle. |
| C8 | Offline package/reconciliation | Contains scoped content, digest/manifest, generation/capability compatibility, storage and foreground authority. |
| C9 | Automated test/evidence | Converts contracts and negative cases into repeatable reports without claiming physical or qualified evidence. |
| C10 | Real-device and human authority | Covers four cohorts, networks, AT, safety/content, privacy, store and release-custodian evidence. |
| C11 | Build/signing/provenance/release | Covers Flutter/Dart/native locks, generated outputs, Android/iOS artifacts, SBOM, signing and staged release. |
| C12 | Independent review/parity | Checks packet completeness, cross-platform parity, generated/native closure and separation of implementer/reviewer/validator. |
| C13 | Exit and forward recovery | Protects portable data, no-loss migration, rollback refusal, quarantine, replacement and framework exit. |

The twelve required work packets below are deliberately mapped to these contexts. P1 and P2 may share a bounded Dart
context for a small presentation change, but P5, P6, P9, P10 and P11 must not be absorbed into that packet. “One
shared Flutter surface” does not remove the Android/iOS or authority contexts.

### 4.2 Packet dependency shape

The intended dependency shape is:

P1 shared contract -> P2 shared presentation -> P3 persistence -> P4 media/privacy -> P5 Android and P6 iOS ->
P7 offline/reconciliation -> P8 automated evidence -> P9 human/device acceptance -> P10 build/release ->
P11 independent review -> P12 exit/forward recovery.

P1 is the source of state truth. P3/P4/P5/P6/P7 may contribute observations, but none may mint current physical or
server authority. P8 can automate deterministic checks; P9 and qualified human authorities close the physical/AT/safety
parts; P10 packages and proves the exact artifacts; P11 independently challenges the complete graph; P12 prevents
lossy rollback and preserves a replacement route.

## 5. Required no-code work packets

Every packet below uses the same controlled record. File/module names are proposed change surfaces for simulation only;
they are not evidence that the repository or implementation exists.

### P01 — Shared product/state contract

- Purpose and user outcome: Define the active-maintenance step state machine and the user-visible truth. The user can
  open the approved offline step, see objective/warning/readiness/safe-stop, record an explicit durable checkpoint,
  recover after termination, and understand unknown/partial physical progress.
- Minimum input documents/contracts: TASK-SIM-MOB-001 sections 1–4; common fixture; DEC-0028/0029/0031; approved
  Phase-3 safety/readiness, Turkish copy, design and accessibility truth; S1–S15 definitions with S3, S7, S8, S10,
  S12, S13 and S15 as direct scenario dependencies.
- Allowed files/modules to change: Kavriva-owned product state contract, transition table, status/copy-key contract,
  requirement trace rows and fixture records. Exact repository path is UNRESOLVED.
- Forbidden scope: Flutter widgets, camera plugins, native lifecycle code, database selection, server authority,
  physical torque/fitment/safety values, automatic continuation, OTA code delivery and release/signing changes.
- Upstream/downstream dependencies: Upstream C0/C1; downstream P2, P3, P4, P7, P8, P9, P10, P11 and P12.
- Candidate-specific dependency, generated file or native boundary: Pure contract is framework-independent Dart
  intent; no plugin or generated file may enter the authority model. Any Flutter type leakage is a boundary defect.
- Android/iOS divergence: State meanings and Turkish truth are identical; lifecycle/permission observations are
  platform-specific inputs from P5/P6 and cannot change the shared transition policy.
- Acceptance and negative cases: Step opens offline; camera denial leaves optional flow usable; captured photo is
  pending evidence; termination before commit yields unknown/partial; restart restores only last durable checkpoint;
  failed/uncertain revalidation holds; reconnect checks generation/recall. Negative: no photo-as-verification, no
  continue-anyway, no restored-state-as-physical-truth, no unrelated catalog download.
- Evidence artifact: State-transition table, invariant/negative-case register, requirement-to-task-to-test links and
  unresolved-authority register. No executable result is claimed.
- Implementer/reviewer/validator separation: AI drafts the contract; an independent product/safety reviewer challenges
  state truth; an automated schema/trace validator checks completeness; a qualified safety authority owns safety meaning.
- External human/store/device action: Qualified safety/content authority confirms safe-stop/readiness semantics; later
  device/AT and store work is not performed by this packet.
- Failure and recovery: Any contradictory transition or missing safe-stop becomes HELD; retain last accepted contract,
  quarantine ambiguous state and recover forward after review.
- Unresolved cost/capacity trigger: Product-state/safety reviewer capacity, copy authority, task-graph tooling and
  future migration ownership are UNRESOLVED; no hourly rate or service price is inferred.
- Obsidian-compatible links: Existing inputs [[DEBATE-006__TASK_SIM_MOB_001_SPEC#User-Visible Change]],
  [[DEBATE-006__TASK_SIM_MOB_001_SPEC#Required State Outcomes]], [[DEC-0028]], [[DEC-0029]], [[DEC-0031]]; planned
  links [[REQ-MOB-001-step-truth]], [[CON-MOB-001-state-machine]], [[TASK-SIM-MOB-001-P01]],
  [[TEST-MOB-001-contract-negative]].

### P02 — Shared UI and presentation packet

- Purpose and user outcome: Bind P1 truth to one shared Dart presentation surface in Turkish. The user receives
  readable objective, warning, readiness, safe-stop, photo-pending, unknown/partial and revalidation states at
  largest text with deterministic focus and non-color status.
- Minimum input documents/contracts: P1 state contract; Phase-3 design system and critical-flow accessibility
  oracle; Turkish copy/units; Flutter accessibility and testing documentation; S1, S3, S7 and S8 acceptance intent.
- Allowed files/modules to change: Shared Dart widgets/state binding, copy keys, semantics declarations, focus/order
  specification and presentation fixtures. Exact app path is UNRESOLVED.
- Forbidden scope: Android/iOS permission sheets, camera/picker implementation, secure keys, background correctness,
  database schema, server authority, physical verification claims and generated host projects.
- Upstream/downstream dependencies: P1 upstream; P3/P4/P5/P6/P7 provide states; P8 tests semantics/state; P9
  verifies physical AT; P10 packages the result.
- Candidate-specific dependency, generated file or native boundary: Flutter engine/widgets, Semantics,
  Material/Cupertino and platform adaptations are candidate mechanisms. They cannot replace native permission/picker
  or AT evidence; no plugin registration or generated runner change is authorized by this packet.
- Android/iOS divergence: Shared widget/state is common; TalkBack/VoiceOver mappings, system dialogs, switch/voice
  control and focus behavior must be checked separately by P5/P6/P9.
- Acceptance and negative cases: All required states are reachable by explicit transition; focus order and labels
  remain available at largest text; warning/status is not color-only; safe-stop remains reachable. Negative:
  unknown/partial cannot look complete, a restored checkpoint cannot auto-open physical continuation, and a photo
  cannot alter readiness.
- Evidence artifact: Widget/state presentation inventory, semantics oracle, copy key table, bounded visual/state
  fixture and planned Flutter test report. No screenshot or device pass is claimed.
- Implementer/reviewer/validator separation: AI produces the bounded presentation plan; independent design/accessibility
  reviewer checks labels/order/uncertainty; automated widget/semantics validator checks deterministic cases; P9 owns
  AT execution.
- External human/store/device action: Android TalkBack and iOS VoiceOver/Switch/Voice Control reviewers later exercise
  the four cohorts and largest text; no owner repair is permitted.
- Failure and recovery: Missing semantics, clipped warning or inaccessible safe-stop holds the packet; keep the last
  accessible safe-stop presentation and forward-fix copy/tokens before release.
- Unresolved cost/capacity trigger: Independent accessibility reviewer, Turkish critical-flow owner, device access and
  any external AT lab are UNRESOLVED; no lab price is invented.
- Obsidian-compatible links: [[CON-MOB-001-state-machine]], [[DESIGN-MOB-001-active-step]],
  [[A11Y-MOB-001-critical-flow-oracle]], [[TASK-SIM-MOB-001-P02]], [[TEST-MOB-001-widget-semantics]].

### P03 — Local persistence, checkpoint and migration packet

- Purpose and user outcome: Ensure only an explicit durable checkpoint is restored as context. Interrupted photo/temp
  work is recoverable or discardable without claiming physical completion; schema changes move forward without silently
  overwriting history.
- Minimum input documents/contracts: P1 state contract; local-first repository boundary; common offline/history,
  conflict, backup/restore and key-loss rules; S3, S6, S13 and S15; migration and portable-export requirements.
- Allowed files/modules to change: Repository/schema contract, transaction/checkpoint specification, idempotency and
  conflict records, migration fixtures, restore quarantine rules and export manifest. Final database package/path is
  UNRESOLVED.
- Forbidden scope: Selecting an unreviewed database, exporting raw keys, making local data current authority, lossy
  downgrade, silent overwrite/delete, server schema change, or treating process state as durable truth.
- Upstream/downstream dependencies: P1 upstream; P4 photo/temp and P7 reconciliation consume the contract; P8
  exercises crash/migration/negative cases; P9 performs restore game-day evidence; P10 records dependency/provenance;
  P12 owns forward recovery and exit.
- Candidate-specific dependency, generated file or native boundary: A Dart SQL package or owned native SQLite bridge
  may be selected later. Until then, any Flutter database/plugin/native bridge is a dependency closure item, not a
  hidden implementation assumption.
- Android/iOS divergence: Transaction semantics must be common; Android backup/data-extraction and iOS backup/Keychain
  policies differ. Restored/cloned state is untrusted on both platforms and enters quarantine/reconciliation.
- Acceptance and negative cases: Explicit checkpoint survives lock/call/background/process kill when committed;
  kill before commit restores the prior checkpoint and marks current work unknown/partial; repeated commit is
  idempotent; partial migration is not displayed as success; conflict is visible. Negative: no downgrade rollback,
  no copied key, no deletion of independent history.
- Evidence artifact: Schema/transaction contract, crash/interruption matrix, migration fixtures, idempotency table,
  restore/quarantine plan and portable export manifest. No database execution is claimed.
- Implementer/reviewer/validator separation: AI drafts repository/migration boundaries; independent data/security
  reviewer checks loss and key rules; automated contract/migration validator checks fixtures; P9/P12 provide human
  restore and exit evidence.
- External human/store/device action: Android/iOS backup and key specialists, account authority and restore-game-day
  operator are required later; the nontechnical owner is not a migration debugger.
- Failure and recovery: Hold on transaction ambiguity, corruption or unavailable key; preserve last good checkpoint,
  quarantine local state, export what is safely exportable and perform forward migration after review.
- Unresolved cost/capacity trigger: Final database/serialization package, migration owner, backup game-day capacity,
  storage and security review are UNRESOLVED; no package price is assumed.
- Obsidian-compatible links: [[CON-MOB-001-state-machine]], [[DATA-MOB-001-local-truth]],
  [[MIGRATION-MOB-001-forward-only]], [[TASK-SIM-MOB-001-P03]], [[TEST-MOB-001-crash-migration]].

### P04 — Camera, photo, temporary-file and privacy packet

- Purpose and user outcome: Allow an optional photo without making it verification. Permission denial remains usable;
  captured/imported media is classified, temporary work is safely staged, and process death cannot turn a pending file
  into physical truth.
- Minimum input documents/contracts: P1/P3; camera and photo/file privacy rules; common 3 MB photo and unstable
  network fixture; S7, S13 and S15; Flutter package evidence for camera 0.12.1, image_picker 1.2.3 and file_selector
  1.1.0 as non-locked snapshots.
- Allowed files/modules to change: Flutter-facing media adapter contract, temp-file lifecycle, permission/result
  mapping, MIME/size/quarantine policy, privacy classification and explicit pending-evidence record. Native plugin
  configuration may be proposed only as a separately listed closure change.
- Forbidden scope: Photo-as-verification, camera permission bypass, raw-key export, silent upload/authority, unrelated
  media/catalog download, assuming a temporary URI/path survives restart, or silently retaining a private photo.
- Upstream/downstream dependencies: P1 state and P3 durability; P5/P6 native permission/picker/lifecycle; P7 upload/
  reconciliation; P8 adapter/negative tests; P9 camera/AT/process-death evidence; P10 package/SBOM/rebuild.
- Candidate-specific dependency, generated file or native boundary: Flutter team camera/image_picker/file_selector
  plugins and transitive Android CameraX/iOS AVFoundation or picker implementations can change Android/iOS runner
  dependency graphs, permission configuration and generated plugin registration. Exact transitive lock and generated
  outputs are UNRESOLVED.
- Android/iOS divergence: Permission prompts, Photo Picker/PHPicker, URI/path lifetime, temporary-file cleanup,
  process-death recovery, camera controller lifecycle and picker cancellation differ; shared state meaning does not.
- Acceptance and negative cases: Denied camera leaves optional flow usable; later grant works; capture is pending;
  kill before checkpoint marks unknown/partial and recovers/discards temp work truthfully; picker cancel is safe; file
  type/size/privacy errors are visible; unstable upload is idempotent. Negative: no camera requirement, no photo
  verification, no silent retry or disclosure.
- Evidence artifact: Dependency snapshot/lock request, adapter contract, privacy/data-classification table, temp-file
  cleanup matrix, lost-data/process-death cases and planned native device evidence. No capture pass is claimed.
- Implementer/reviewer/validator separation: AI owns adapter/task plan; independent media/privacy/security reviewer
  checks scope and disclosure; automated adapter/idempotency validator checks deterministic cases; P9 human exercises
  native prompts and interruption.
- External human/store/device action: Android/iOS camera/picker and AT reviewers, privacy/security owner and physical
  devices are required; any package publisher/EOL authority remains external.
- Failure and recovery: Quarantine invalid/unknown media, keep safe-stop and last checkpoint, allow manual no-photo
  continuation where product contract permits, and retry only in foreground with explicit state.
- Unresolved cost/capacity trigger: Package security/EOL review, native media owner, device lab/AT, storage/egress and
  privacy review are UNRESOLVED; no plugin or provider cost is invented.
- Obsidian-compatible links: [[CON-MOB-001-state-machine]], [[DATA-MOB-001-private-media]],
  [[PRIV-MOB-001-media-classification]], [[TASK-SIM-MOB-001-P04]], [[TEST-MOB-001-media-interruption]].

### P05 — Android lifecycle and accessibility packet

- Purpose and user outcome: Map Android lock, call, backgrounding and process termination to truthful Flutter states;
  keep the last durable checkpoint and safe-stop; expose the active step to TalkBack and other agreed Android AT.
- Minimum input documents/contracts: P1/P2/P3/P4; Android API 29 constrained and main Android cohorts; Android
  lifecycle, Doze/standby, CameraX/Photo Picker, Keystore, notification and backup evidence; S3, S7, S8, S11, S12,
  S13 and S15.
- Allowed files/modules to change: Android host/native adapter boundary, lifecycle signal mapping, permission/picker
  configuration, secure-storage adapter, foreground reconciliation hooks, Android test fixtures and manifest/Gradle
  closure records. Exact source paths are UNRESOLVED.
- Forbidden scope: iOS files, scheduled background correctness, push as authority, automatic physical continuation,
  OTA code, direct database authority, bypassing TalkBack evidence or asking the owner to repair Gradle/signing.
- Upstream/downstream dependencies: P1–P4; P6 is the parallel iOS packet; P7 consumes lifecycle observations; P8
  automates Android contracts; P9 validates constrained/main devices; P10 rebuilds Android artifact; P11 reviews parity.
- Candidate-specific dependency, generated file or native boundary: Flutter Android runner, generated plugin registration,
  Gradle/AGP/JDK/SDK dependency graph, Kotlin adapter and possible WorkManager/background configuration can change
  indirectly from pub/plugin edits. Every generated/indirect output must be enumerated and locked.
- Android/iOS divergence: Android Activity/process/lifecycle, permission, URI, Doze and backup behavior are not copied
  into iOS assumptions. Shared P1 states receive Android observations; they do not inherit Android timing guarantees.
- Acceptance and negative cases: Lock, call, background, process kill, restart, camera deny/grant, low storage,
  constrained network, TalkBack largest text, focus/order, state announcements, safe-stop and revalidation. Negative:
  skipped AppLifecycleState events cannot be treated as proof of completion; WorkManager timing cannot be correctness;
  restored state cannot mint authority.
- Evidence artifact: Android lifecycle/permission mapping, native adapter contract, Gradle/manifest change inventory,
  instrumentation/semantics test plan and later device/AT session record template. Documentary only at this stage.
- Implementer/reviewer/validator separation: AI drafts Android adapter and evidence plan; independent Android/native
  reviewer checks lifecycle/threading and generated output; automated instrumentation/contract runner checks repeatable
  cases; P9 human owns physical/AT acceptance.
- External human/store/device action: Android owner, constrained/main Android testers, TalkBack reviewer, signing/store
  custodian and safety authority are required later.
- Failure and recovery: On missed lifecycle signal, low storage, permission uncertainty or process loss, restore last
  checkpoint, mark unknown/partial, preserve safe-stop and require foreground revalidation. Hold if native owner or
  device evidence is unavailable.
- Unresolved cost/capacity trigger: Android native skill, exact SDK/AGP/Gradle/JDK, device access, AT and signing/
  artifact capacity remain UNRESOLVED; no CI/device price is invented.
- Obsidian-compatible links: [[CON-MOB-001-state-machine]], [[A11Y-MOB-001-android-oracle]],
  [[NATIVE-MOB-001-android-lifecycle]], [[TASK-SIM-MOB-001-P05]], [[TEST-MOB-001-android-interruption]].

### P06 — iOS lifecycle and accessibility packet

- Purpose and user outcome: Map iOS lock, call, backgrounding and termination to the same truthful shared states;
  preserve last durable checkpoint and safe-stop; expose readiness, warning, unknown/partial and recovery to VoiceOver,
  Switch Control and Voice Control at largest text.
- Minimum input documents/contracts: P1/P2/P3/P4; oldest supported and current iPhone cohorts; Apple lifecycle,
  background-strategy, Keychain, picker, notification, universal-link and accessibility evidence; S3, S7, S8, S11,
  S12, S13 and S15.
- Allowed files/modules to change: iOS Runner/native adapter boundary, lifecycle/scene mapping, entitlements and
  permission configuration, Keychain/picker/media hooks, foreground reconciliation hooks, iOS test fixtures and
  Xcode/SwiftPM closure records. Exact source paths are UNRESOLVED.
- Forbidden scope: Android files, timely background correctness, push as authority, automatic continuation, OTA code,
  raw key export, silent disclosure, and user-operated Xcode/signing repair.
- Upstream/downstream dependencies: P1–P4; P5 is the parallel Android packet; P7 consumes iOS observations; P8
  automates contracts where possible; P9 validates both iPhone cohorts and AT; P10 builds/signs; P11 checks parity.
- Candidate-specific dependency, generated file or native boundary: Flutter iOS Runner, generated plugin registration,
  Xcode build settings, SwiftPM/CocoaPods resolution and native Swift adapters can change indirectly. Flutter 3.44+
  Swift Package Manager guidance and the documented CocoaPods registry event make dependency migration a forced-event
  item; exact generated outputs, Xcode/macOS and signing versions remain UNRESOLVED.
- Android/iOS divergence: iOS scene/lifecycle callbacks, background URLSession/BGTask limits, Keychain/backup,
  PHPicker/document UI, VoiceOver and entitlement behavior are not inferred from Android signals. Shared state truth
  remains common.
- Acceptance and negative cases: Lock/call/background/termination/restart, permission denial/grant, picker cancel,
  temp-file recovery, VoiceOver largest text, focus/order, status announcements, contrast, reduced motion,
  Switch/Voice Control and safe-stop/revalidation. Negative: iOS scheduling cannot be promised timely; old/restored
  authorization cannot become current authority; no visual-sameness pass.
- Evidence artifact: iOS lifecycle/entitlement/permission mapping, Xcode/SwiftPM/native dependency inventory,
  accessibility oracle and later device/AT session template. No signed build or iPhone pass is claimed.
- Implementer/reviewer/validator separation: AI drafts Swift/native boundary and evidence plan; independent iOS/release
  reviewer checks lifecycle, entitlements, generated output and dependency closure; automated host/contract checks cover
  deterministic cases; P9 human owns iPhone/VoiceOver execution.
- External human/store/device action: Mac/Xcode operator, Apple signing/store owner, oldest/current iPhone testers,
  VoiceOver/AT reviewer, privacy/security and qualified safety authority are required.
- Failure and recovery: If an interruption callback is missed, treat work as unknown/partial, restore last checkpoint,
  retain safe-stop and revalidate in foreground. Hold on missing Mac, signing, iOS native owner or AT evidence.
- Unresolved cost/capacity trigger: Mac/Xcode availability, Apple account/certificates, iOS native skill, device/AT
  access, SwiftPM/CocoaPods migration and release capacity are UNRESOLVED; no hosted build or Mac price is invented.
- Obsidian-compatible links: [[CON-MOB-001-state-machine]], [[A11Y-MOB-001-ios-oracle]],
  [[NATIVE-MOB-001-ios-lifecycle]], [[TASK-SIM-MOB-001-P06]], [[TEST-MOB-001-ios-interruption]].

### P07 — Offline package, reconciliation and compatibility packet

- Purpose and user outcome: Keep one selected task package usable offline while preserving compact safety/recovery,
  optional-media boundaries, integrity, generation compatibility and conservative reconnect behavior.
- Minimum input documents/contracts: P1/P3/P4/P5/P6; common 12 MB/150 MB/250 MB/25 MB rules; package manifest,
  digest/signature, client capability, API/schema/content/configuration/revocation generation and foreground
  reconciliation contracts; S2, S3, S4, S5, S9, S10, S12 and S14.
- Allowed files/modules to change: Dart package/reconciliation contract, manifest/compatibility fixtures, scoped
  downloader orchestration, temporary staging/atomic promotion rules, retry/cancel/cleanup state and foreground
  authority check. Exact transport/database package is UNRESOLVED.
- Forbidden scope: Downloading unrelated catalog content, assuming background timing/push, treating cached package as
  current recall authority, OTA code delivery, silent optional-media inclusion, or server/provider selection.
- Upstream/downstream dependencies: P1 state and P3 data; P4 media; P5/P6 lifecycle/storage; P8 tests integrity/
  idempotency; P9 constrained-network/device evidence; P10 release graph; P12 exit and forward recovery.
- Candidate-specific dependency, generated file or native boundary: Dart orchestration may call native Android/iOS
  background adapters; no Flutter downloader plugin is selected. Plugin/channel and OS quota changes are candidate
  closure items and must not alter the package protocol.
- Android/iOS divergence: Background scheduling, storage pressure, process loss and connectivity signals differ. The
  shared protocol allows foreground retry/reconciliation and never promises timely background completion.
- Acceptance and negative cases: Display size before transfer; selected compact closure completes or holds; optional
  media remains separate; cancel/resume/duplicate/corrupt/low-space paths are truthful; offline step opens; reconnect
  checks release/package/recall eligibility; old/unknown capability holds. Negative: no 2 GB catalog, no silent stale
  safety meaning, no “download succeeded” before digest/manifest verification.
- Evidence artifact: Package manifest/capability matrix, state/retry/idempotency table, integrity/atomic-promotion
  test plan, network/interruption fixture and release-generation compatibility register.
- Implementer/reviewer/validator separation: AI drafts Dart orchestration and contract; independent data/safety
  reviewer checks authority and stale-content behavior; automated manifest/hash/idempotency/state validator checks
  deterministic cases; P9/device and qualified safety authority close real behavior.
- External human/store/device action: Backend/content/revocation owner, safety authority, constrained-network testers,
  store/release custodian and device lab are required; no AI-only recall decision.
- Failure and recovery: Hold optional work first, preserve required compact/safe-stop where verified, clean only
  verified temporary data, retry foreground, quarantine corrupt/stale package and re-reconcile before continuation.
- Unresolved cost/capacity trigger: Backend, storage/CDN/egress, retry/backup capacity, content/revocation owner,
  network/device testing and manifest authority are UNRESOLVED; quantities are not prices.
- Obsidian-compatible links: [[CON-MOB-001-state-machine]], [[PKG-MOB-001-scoped-offline]],
  [[RELEASE-MOB-001-generation-graph]], [[TASK-SIM-MOB-001-P07]], [[TEST-MOB-001-package-integrity]].

### P08 — Automated contract, state and negative-test packet

- Purpose and user outcome: Convert P1–P7 contracts into repeatable machine checks so a fresh AI can produce evidence
  without claiming physical, AT, safety or store authority.
- Minimum input documents/contracts: All preceding packet contracts; S1–S15 fixture; state/transition, persistence,
  media/privacy, package compatibility, copy/semantics and release evidence schemas.
- Allowed files/modules to change: Dart unit/property/state/serialization test plans, widget/semantics fixtures,
  adapter mocks/contracts, deterministic fake lifecycle/network/storage inputs, traceability and evidence schemas.
  Native instrumentation paths may be listed but are not executed here.
- Forbidden scope: Simulator or mocked output presented as real-device/AT/safety proof; hiding Android/iOS tests in a
  shared test count; production data, signing secrets, OTA, performance benchmarks or unapproved test provider.
- Upstream/downstream dependencies: P1–P7; downstream P9 human/device, P10 release/provenance and P11 independent
  review. P12 consumes test/fixture portability.
- Candidate-specific dependency, generated file or native boundary: Flutter test/integration_test can cover Dart and
  some app flows; native permission sheets, notification UI, actual process termination, Keychain/Keystore and runner
  behavior require platform instrumentation or P9. Exact native test tooling is UNRESOLVED.
- Android/iOS divergence: Every shared state/negative case is parameterized for both platforms; platform-specific
  lifecycle, picker, permission, AT and backup tests remain separate evidence rows.
- Acceptance and negative cases: All Section 2 outcomes; duplicate/partial/corrupt/low-storage/cancel/retry; kill
  before commit; unknown/partial; revalidation fail/success; offline/reconnect generation; key/restore quarantine;
  parity and no-OTA checks. Negative test absence is a hold, not a passing zero.
- Evidence artifact: Machine-readable test plan/report schema, trace matrix, fixture manifests, expected failures and
  artifact/version identifiers. No tests are run or passed by this document.
- Implementer/reviewer/validator separation: AI writes bounded test cases; independent test reviewer inspects
  oracle completeness; an automated runner later emits reproducible reports; P9/P10/human authorities validate what
  automation cannot.
- External human/store/device action: CI/build custodian, Android/iOS native owners, AT reviewers and qualified safety
  reviewers must accept their respective evidence classes.
- Failure and recovery: Any failed or missing negative test holds the affected transition/release; preserve last
  accepted artifact, fix forward, rerun affected contract set and do not claim a broader pass.
- Unresolved cost/capacity trigger: CI/artifact retention, native test hosts, device access and independent test-review
  capacity are UNRESOLVED; no runner or service price is invented.
- Obsidian-compatible links: [[TEST-MOB-001-contract]], [[TEST-MOB-001-negative-cases]],
  [[TRACE-MOB-001-req-task-test]], [[TASK-SIM-MOB-001-P08]], [[EVIDENCE-MOB-001-automated-report]].

### P09 — Real-device and human acceptance packet

- Purpose and user outcome: Provide the later physical and human evidence that the simulated state model behaves on
  all required Android/iPhone cohorts, networks, lifecycle interruptions and assistive technologies.
- Minimum input documents/contracts: P1–P8; common four-cohort/device/network/offline/lifecycle fixtures; Turkish
  accessibility oracle; qualified safety/content criteria; store/release evidence expectations.
- Allowed files/modules to change: Human test script, device matrix, AT oracle, session/evidence form, defect/hold
  register and recovery/retest records. No application code is changed by this packet.
- Forbidden scope: Simulator-only closure, AI-only signoff, owner repair/debug, invented safety values, store/legal
  impersonation, bypass of a hold or treating screenshots as physical truth.
- Upstream/downstream dependencies: P1–P8; downstream P10 release evidence, P11 independent review and P12 recovery
  record.
- Candidate-specific dependency, generated file or native boundary: Flutter runner/plugin/native permission and
  lifecycle behavior must be observed on real Android/iOS devices; native system UI is not fully represented by shared
  Dart widget automation.
- Android/iOS divergence: Run separate Android API 29/main Android and oldest/current iPhone sessions, including
  TalkBack versus VoiceOver, permission/picker, process termination, storage/network and backup/restore differences.
- Acceptance and negative cases: Step opens offline; denial remains usable; photo is pending; process kill before
  checkpoint yields unknown/partial; restart restores only durable context; revalidation gates continuation; reconnect
  checks recall/generation; safe-stop remains reachable; largest text/AT state announcements and non-color status.
- Evidence artifact: Dated device/session records, OS/build/artifact identifiers, AT observations, network/lifecycle
  logs, defects, retest links and qualified reviewer signoff. This simulation contains none of those results.
- Implementer/reviewer/validator separation: AI may prepare the script; an independent human executes/reviews;
  qualified safety/accessibility/store authorities validate their domains; the owner approves outcome/risk but does
  not perform technical repair.
- External human/store/device action: Physical devices, Mac/iPhone signing access, Android tester, TalkBack/VoiceOver
  user, independent AT reviewer, qualified safety/content reviewer and release custodian are mandatory.
- Failure and recovery: Any cohort or AT failure holds the affected transition/release; preserve safe-stop, retain
  evidence and fix forward. Unknown physical state never becomes a pass through a UI restart.
- Unresolved cost/capacity trigger: Device availability/replacement, AT and qualified safety capacity, tester time,
  Mac access and release-window capacity are UNRESOLVED; no lab, device or human price is invented.
- Obsidian-compatible links: [[A11Y-MOB-001-critical-flow-oracle]], [[DEVICE-MOB-001-four-cohorts]],
  [[SAFETY-MOB-001-review-oracle]], [[TASK-SIM-MOB-001-P09]], [[EVIDENCE-MOB-001-human-session]].

### P10 — Build, signing, provenance and release-evidence packet

- Purpose and user outcome: Produce two exact, reviewable Flutter release artifacts and their evidence without OTA
  code delivery. A release can identify the Flutter/Dart/native/dependency/content/schema/configuration generations.
- Minimum input documents/contracts: P1–P9; frozen Flutter/Dart ref/digest; approved Android/iOS support policy;
  exact Android SDK/AGP/Gradle/JDK and macOS/Xcode/SwiftPM; pubspec lock; SBOM/provenance/signing/store graph;
  DEBATE-005 release/incident and suspension generations.
- Allowed files/modules to change: SDK/dependency manifests and locks, Android/iOS host configuration, generated
  project/framework inventory, build scripts, signing/provenance metadata, SBOM, artifact manifest and staged-release
  evidence records. Exact repository paths and generated outputs are UNRESOLVED.
- Forbidden scope: OTA code/update authority, unreviewed generated-file mutation, unsigned artifact, secret exposure,
  silent build-tool drift, store impersonation, bypassing P9/P11 or changing product state semantics.
- Upstream/downstream dependencies: P1–P9; P11 independently reviews artifacts and parity; P12 records previous
  accepted artifact and replacement/forward path.
- Candidate-specific dependency, generated file or native boundary: Flutter SDK ref/digest, pub lock, Android Gradle
  graph, iOS Runner/Xcode/SwiftPM or CocoaPods resolution, generated plugin registration and platform host outputs
  may change indirectly from a Dart/plugin update. The closure must enumerate, diff and archive them.
- Android/iOS divergence: Separate signed Android and iOS artifacts, toolchains, entitlements/manifest, permissions,
  native test evidence and store submissions; shared Dart source does not collapse release authority.
- Acceptance and negative cases: Clean-checkout rebuild with pinned inputs; artifact checksum/provenance/SBOM; both
  platform test/AT/device evidence linked; capability/schema/content/configuration/revocation compatibility; staged
  pause/correction path. Negative: no OTA code, no unknown generated output, no release with missing native or AT
  evidence.
- Evidence artifact: Reproducible build logs, lockfiles, generated-output manifest/diff, SBOM, signatures, checksums,
  artifact/release graph, store readiness record and incident impact graph. No build or signing pass is claimed.
- Implementer/reviewer/validator separation: AI prepares build/release packet; independent build/security reviewer
  checks graph, provenance and generated output; automated clean-build/manifest/SBOM validators later run; store/
  signing custodian and P9/P11 provide external acceptance.
- External human/store/device action: Mac/Xcode operator, Android build custodian, Apple/Google account/signing owner,
  security/SBOM authority, store policy authority and release incident authority are required.
- Failure and recovery: Hold release on drift, missing signature, generated mismatch, missing cohort evidence or
  incompatible generation; retain last accepted artifact, pause rollout and move forward only after correction.
- Unresolved cost/capacity trigger: Mac/Xcode, Android host, CI/artifact retention, signing, store fees, security
  review and release-owner capacity are UNRESOLVED. Only approved store constants may be used later; no hosted price is
  invented here.
- Obsidian-compatible links: [[RELEASE-MOB-001-generation-graph]], [[SUPPLY-MOB-001-sbom-provenance]],
  [[SIGN-MOB-001-two-platform]], [[TASK-SIM-MOB-001-P10]], [[EVIDENCE-MOB-001-build-artifact]].

### P11 — Independent review and parity packet

- Purpose and user outcome: Ensure the twelve packets are complete, bounded and independently challenged. The reviewer
  detects a shared-Dart change that forgot Android/iOS lifecycle, accessibility, generated-file, release or exit work.
- Minimum input documents/contracts: P1–P10; candidate Flutter dossier; common TASK-SIM spec; equivalence and control
  documents; full S1–S15 mapping; traceability, acceptance, negative-case and unresolved registers.
- Allowed files/modules to change: Review memo, parity matrix, dependency/native/generated-output checklist,
  decision/hold register, trace links and defect/retest records. Reviewer may request packet changes but does not
  implement them.
- Forbidden scope: Approving own implementation, signing/building, changing server authority, waiving device/AT/
  safety evidence, selecting a hidden plugin, changing the common fixture or turning a hold into a score.
- Upstream/downstream dependencies: P1–P10; P12 consumes the independent disposition; manager synthesis remains
  external and no candidate is selected by this packet.
- Candidate-specific dependency, generated file or native boundary: Review must inspect Flutter SDK/pub/plugin graph,
  platform channels, Android/iOS host projects, generated registration/configuration, native fallback and the
  Dart-to-native boundary for every affected packet.
- Android/iOS divergence: Parity means equal state truth and evidence obligations, not identical widget code. Review
  compares Android/iOS lifecycle, permission, picker, key/backup, AT, release and recovery rows independently.
- Acceptance and negative cases: Every required field exists for every packet; all linked requirements/screens/
  contracts/tasks/tests resolve or are marked planned; generated/native effects are named; photo is not verification;
  unknown/partial cannot continue; no background/OTA shortcut; P9/P10 human evidence is still pending.
- Evidence artifact: Independent review memo, packet completeness matrix, shared-versus-native split map, parity
  defect register, unresolved facts and permitted status recommendation to the manager (not a framework decision).
- Implementer/reviewer/validator separation: A different AI/human reviewer than the packet implementer inspects the
  graph; a machine link/schema checker validates references; P9/P10/qualified authorities remain validators of their
  evidence domains.
- External human/store/device action: Manager/decision owner, independent reviewer, safety/accessibility/security
  authorities and release/store custodian receive the packet; no reviewer impersonates them.
- Failure and recovery: Any omitted packet, unowned native capability, broken link, parity divergence or unsupported
  assertion returns the affected packet to HELD; retain prior accepted records and forward-revise.
- Unresolved cost/capacity trigger: Independent review time, manager synthesis, native/security/AT authority and
  evidence tooling are UNRESOLVED; no review subscription or contractor amount is invented.
- Obsidian-compatible links: [[TRACE-MOB-001-req-task-test]], [[PARITY-MOB-001-android-ios]],
  [[REVIEW-MOB-001-independent]], [[TASK-SIM-MOB-001-P11]], [[EVIDENCE-MOB-001-review-memo]].

### P12 — Exit, rollback-refusal and forward-recovery packet

- Purpose and user outcome: Prevent a dishonest rollback after process loss or migration. Preserve the last durable
  checkpoint, label physical work unknown/partial, quarantine untrusted restore, migrate forward without loss and keep
  a route to replace Flutter.
- Minimum input documents/contracts: P1, P3, P7, P10 and P11; exit dossier; schemas/contracts/fixtures/manifests/
  provenance; key/backup/restore and staged old/new client rules; S3, S5, S6, S10, S13, S14 and S15.
- Allowed files/modules to change: Portable schema/export/migration manifests, dual-format/forward bridge plan,
  quarantine and recovery records, artifact-retention/rollback-refusal runbook, framework-exit inventory and
  replacement-release fixture. No downgrade or raw-key export.
- Forbidden scope: Lossy data rollback, restoring process/UI as physical proof, deleting independent history,
  exporting raw keys, silent overwrite, OTA replacement, bypassing server/content authority or claiming migration pass.
- Upstream/downstream dependencies: P1–P11; the packet closes the simulation’s replacement and recovery evidence
  boundary but remains dependent on later implementation/game-day execution.
- Candidate-specific dependency, generated file or native boundary: Flutter widgets/engine, Dart runtime artifacts,
  pub/plugin APIs, Android/iOS runners, platform channels, Gradle/Xcode/SwiftPM and signed binaries are bound. Data,
  manifests, contracts, fixtures, copy/accessibility intent and acceptance oracles must remain portable.
- Android/iOS divergence: Backup transport, Keychain/Keystore, URI/key loss and native restore behavior differ; both
  quarantine into shared unknown/untrusted semantics and require account/current-authority reconciliation.
- Acceptance and negative cases: Kill before checkpoint; restart last durable checkpoint; current physical state
  revalidation; corrupt/partial migration; old/new client/API/schema/content/config coexistence; key loss/rotation;
  framework replacement reads portable data. Negative: no lossy downgrade, no auto-continue, no silent discard,
  no raw-key repair and no current authority from cache.
- Evidence artifact: Export/import manifest, migration fixtures, restore/key-loss game-day plan, artifact/provenance
  archive, forward-recovery runbook, replacement boundary and exit dependency inventory. No migration success is claimed.
- Implementer/reviewer/validator separation: AI drafts forward-recovery and exit records; independent data/security
  reviewer challenges loss/key risks; automated schema/export fixture checker validates structure; human data, security,
  safety and release authorities approve actual migration/recovery later.
- External human/store/device action: Account/data authority, security/key custodian, qualified safety reviewer, Mac/
  store/release owner and physical/AT validators are required for a real migration or replacement.
- Failure and recovery: Quarantine ambiguous state, retain last accepted Flutter artifact and portable export, safe-stop,
  re-authenticate/reconcile, then forward-migrate after review. Refuse unsafe downgrade and explain the hold.
- Unresolved cost/capacity trigger: Backup/storage/egress, migration tooling, key/security review, replacement client,
  incident capacity and external authorities are UNRESOLVED; no exit duration or rewrite price is estimated.
- Obsidian-compatible links: [[EXIT-MOB-001-portable-truth]], [[MIGRATION-MOB-001-forward-only]],
  [[RECOVERY-MOB-001-unknown-partial]], [[TASK-SIM-MOB-001-P12]], [[TEST-MOB-001-exit-fixture]].

## 6. Cross-packet answers to the comparison questions

### 6.1 How many context types must a fresh AI understand?

At least fourteen: governance/fixture, product authority/state, design/accessibility, shared Dart domain/UI,
persistence/migration, media/privacy, Android native, iOS native, offline/reconciliation, automated evidence,
real-device/human authority, build/signing/provenance, independent parity review and exit/forward recovery. A small
shared-Dart change can use a reduced context pack only if P1/P2 remain linked and the packet explicitly declares that
P3–P12 are unchanged and revalidated. Camera, lifecycle, key, background, generated-project, signing or accessibility
changes must expand the context to the affected native and authority packets.

This count is a context inventory, not a score. Fewer visible packets would not be safer if they hide native,
authority or reviewer work.

### 6.2 Where does a routine shared change split?

The routine change starts in P1/P2 as a shared state/presentation change. It splits as soon as it touches:

- permission, camera, picker, temporary URI/file, notification, deep-link, secure key or backup behavior;
- lifecycle/process death, background transfer or foreground reconciliation;
- Android/iOS semantics, system UI, AT or largest-text behavior;
- Flutter plugin/native channel, generated plugin registration, Android Gradle/manifest or iOS Runner/Xcode/
  SwiftPM/CocoaPods configuration;
- signed build, SBOM/provenance, store artifact or incident graph;
- physical-device, AT, qualified safety, privacy, store or external account authority.

The shared Dart packet therefore does not eliminate P5/P6/P9/P10/P11; it gives them a common contract and parity oracle.

### 6.3 What generated/native files can change indirectly?

The affected closure can include Flutter SDK/engine artifacts, pub lock and transitive plugin graph, generated Android
plugin registration, Android Runner/Gradle/manifest/Kotlin adapter and possible background configuration, iOS Runner/
Xcode build settings/entitlements/Swift adapter, SwiftPM or CocoaPods resolution, and signed artifact/provenance
manifests. Exact generated paths are UNRESOLVED until a repository exists. A task is incomplete if a pub/plugin edit
does not enumerate, diff and archive its generated/native consequences.

### 6.4 Can a failed candidate dependency be replaced?

Conditionally. The replacement boundary is a Kavriva-owned adapter for camera/media/picker, transfer, notification,
deep-link, secure storage/key, database and lifecycle observations. Product state, schemas, manifests, contracts and
fixtures must not depend on a plugin-specific object or path. A replacement still requires Android/iOS native skills,
lock/SBOM/provenance, generated-output review, rebuild, device/AT/privacy/security validation and a staged forward
release. If no maintained adapter or safe manual fallback exists, the capability remains HELD.

### 6.5 What must be rebuilt and revalidated?

Any change to Flutter/Dart, pub lock, plugin/module, native channel, Android Gradle/manifest/Kotlin adapter, iOS Runner/
Xcode/entitlement/Swift adapter, database/schema/migration, package manifest/generation, permission, lifecycle,
background, key, notification/deep-link, signing or build toolchain requires a dependency-impact review. The affected
Android and iOS artifacts must be rebuilt from pinned inputs; automated contract/state/negative tests rerun; both
platform device/AT evidence rerun where behavior can differ; SBOM/provenance/signature/artifact graph regenerated; and
release/incident/rollback records updated. A pure copy or isolated Dart change still needs trace, widget/semantics and
parity review; no blanket “shared means no native validation” rule exists.

### 6.6 Which evidence can be automated and which needs people/devices?

Automatable or machine-checkable later:

- state/transition invariants, idempotency, serialization, schema/forward-migration fixtures;
- package manifest/digest/compatibility, scoped-download size, cancel/retry and no-unrelated-content checks;
- Dart/widget/semantics fixtures, traceability/link/schema completeness, dependency locks, SBOM and artifact manifests;
- clean-build reproducibility where the host/toolchain is available, checksums, signatures and generated-output diffs;
- deterministic mocked lifecycle/network/storage negative cases.

Human/physical/external authority required:

- Android API 29/main and oldest/current iPhone lock/call/background/process termination, storage pressure and network;
- TalkBack/VoiceOver/Switch/Voice Control, largest text, focus/order, contrast, reduced motion and dexterity;
- camera/picker/system notification/share/deep-link surfaces and privacy disclosure;
- qualified safety/content/readiness/recall/withdrawal review;
- Apple/Google store, signing, legal/privacy, Mac/Xcode, backend/provider, incident and key custody authority.

No machine result in the first list is a real-device, AT, safety, store or production pass.

### 6.7 How does another AI detect incomplete cross-platform parity?

It should use the parity matrix and trace graph, not compare screenshots only:

1. Find the P1 state/transition and its linked Android and iOS rows.
2. Confirm P5 and P6 each name lifecycle, permission, picker, key/backup, AT, failure and recovery evidence.
3. Compare acceptance and negative cases, including camera denied, photo pending, kill-before-checkpoint,
   unknown/partial, revalidation failure, reconnect recall/generation and safe-stop.
4. Diff Flutter plugin/channel, generated runner, manifest/entitlement, dependency lock, toolchain and signed artifact
   manifests for both platforms.
5. Require separate P9 sessions and P10 artifacts for both platforms; a shared Dart test report cannot close a missing
   native row.
6. Hold if one platform has a different truth, timing assumption, accessibility oracle, fallback, owner or evidence
   status.

### 6.8 Can the task be reverted without lying about migrated data or physical state?

Only by refusal of unsafe rollback and forward recovery. The last explicit durable checkpoint is the only restorable
physical-work context. Work after process termination is unknown/partial until current physical revalidation; the app
does not reconstruct it from UI, photo or process memory. A schema/key/provider migration is not downgraded if that
would lose data or provenance. The client quarantines uncertain state, preserves/export what is safe, retains the last
accepted artifact, and moves forward after reviewed migration/reconciliation. Reconnection checks current package/
release/recall authority before more physical continuation.

### 6.9 What survives framework replacement?

Portable candidates:

- canonical schemas, API/contracts, operation IDs, history/provenance, corrections, publication/revocation generations;
- scoped package manifests/digests, compact safety/recovery closure, optional-media metadata and export formats;
- local history, notes/photos/pending/conflict records when export and key policy allow;
- Turkish copy keys, design tokens/accessibility intent, S1–S15 fixtures, test/acceptance oracles, SBOM/locks/
  provenance and incident runbooks.

Flutter-bound candidates:

- Dart widgets/state composition, Flutter engine/renderer, pub/plugin APIs, channel/runner integration, generated
  Android/iOS projects, platform-specific adapters, Gradle/Xcode/SwiftPM configuration and signed binaries.

Key material is not portable user data. Key loss requires quarantine, re-authentication and re-encryption under the
approved policy; raw-key export is forbidden.

## 7. Accessibility matrix

The following is a documentary plan for Turkish readiness, warning, unexpected-state stop, safe recovery and active
step. It is not an executed accessibility pass.

| Check | Flutter/documented capability | Platform-specific work | Later real-device oracle | Current status |
|---|---|---|---|---|
| VoiceOver | Flutter Semantics, labels, roles, actions and state announcements can be declared. | iOS native permission/picker/notification/share and Swift host surfaces; VoiceOver rotor/focus behavior. | Oldest/current iPhone, VoiceOver enabled, largest text, Turkish step/warning/unknown/partial/recovery and camera denial. | HELD |
| TalkBack | Flutter Semantics and widget/integration test APIs can express labels/roles/actions. | Android native permission/picker/notification/share and Kotlin host surfaces; TalkBack focus/exploration. | Constrained/main Android, TalkBack enabled, largest text, Turkish step/warning/unknown/partial/recovery and camera denial. | HELD |
| Largest text/reflow | Shared layout and text semantics can be inspected in widget tests. | Android/iOS system text settings, native dialogs, truncation and scroll/focus behavior. | Four cohorts, largest agreed text, no clipped warning/readiness/safe-stop/action, photo pending and unknown/partial visible. | HELD |
| Focus and reading order | Flutter focus/semantics tree can be declared and machine-checked in bounded fixtures. | Platform back navigation, modal permission/picker return, native focus restoration and VoiceOver/TalkBack order. | Device session confirms objective -> warning -> readiness -> optional photo -> checkpoint/revalidate -> safe-stop order. | HELD |
| State announcements | Flutter live-region/state semantics can describe pending, paused, unknown/partial, held and revalidation. | Native lifecycle, permission, background interruption and system error announcements may require host mapping. | Human AT reviewer confirms truthful Turkish announcement after denial, capture, kill/restart and failed revalidation. | HELD |
| Non-color status/contrast | Shared widgets can expose text/icon/status semantics and theme contrast. | Native dialogs/sheets, iOS high-contrast settings and Android system UI need separate checks. | Four cohorts at contrast/high-contrast settings; warning, hold, safe-stop, optional and unknown/partial are not color-only. | HELD |
| Reduced motion | Shared Flutter animation choices can respect reduced-motion intent. | Platform transition/permission/picker animation and process-return behavior need native review. | Reduced-motion setting with step open, photo flow, restart and safe-stop; no state depends on animation completion. | HELD |
| Switch/voice control | Flutter semantics/actions can expose activation targets. | Android Switch/Voice Access and iOS Switch/Voice Control system surfaces and labels. | Human AT reviewer performs revalidation and safe-stop without fine dexterity or visual-only gesture. | HELD |
| Reduced dexterity | Large explicit controls and non-time-critical recovery can be designed in shared UI. | Native controls, camera/picker dismissal, back/return and share surfaces differ. | Four cohorts with a controlled dexterity scenario; no accidental commit and no hidden destructive gesture. | HELD |

The shared semantics API is evidence of an available mechanism, not evidence of platform parity. P9 and P11 remain
mandatory.

## 8. Forced-event and toolchain walkthrough

The following walkthroughs are planning records, not executed events. Each event names the affected packets and the
hold/recovery behavior.

| Event | Flutter path in this simulation | Affected packets and evidence | External dependency/capacity | Hold and forward recovery |
|---|---|---|---|---|
| Planned release window | Re-pin Flutter/Dart/ref/digest, review pub lock and generated Android/iOS host graph, run automated contracts, platform device/AT/safety/release evidence, then stage both stores. | P1/P2/P7/P8/P9/P10/P11; lock, SBOM, clean-build, parity and session artifacts. | Android SDK/AGP/Gradle/JDK, Mac/Xcode/SwiftPM, devices, AT, safety/content and release custodians. | Hold if any graph/evidence is missing; retain prior artifact and forward-migrate only after review. |
| Safety/security emergency correction | Prefer reviewed content correction/revocation where code is not required; signed binary correction follows the same release graph. | P1/P7/P9/P10/P11/P12; recall, source/provenance, safe-stop, artifact impact and incident records. | Qualified safety/security reviewer, content authority, store/signing and incident owner. | Pause affected generation/release; safe-stop offline; publish reviewed correction and reconcile. No OTA code shortcut. |
| Apple/Google build/store requirement change | Update pinned host/toolchain or store-facing artifact; rebuild Flutter Android/iOS artifacts and rerun native/AT/migration evidence. | P5/P6/P8/P9/P10/P11; toolchain diff, generated output, signing, SBOM, device/AT records. | Mac/Xcode/signing/store access, Android host owner; exact future requirement and cost UNRESOLVED. | Hold on missing host/custodian; keep provider-independent source, locks and prior artifact. |
| Critical dependency abandonment | Replace camera/media/transfer/security plugin behind Kavriva-owned adapter or move to owned Kotlin/Swift adapter; update lock/SBOM. | P4/P5/P6/P8/P9/P10/P11/P12; replacement contract, native diff, device/AT/security and exit evidence. | Android/iOS native specialist, security review, package provenance/EOL owner and devices. | Quarantine capability, keep safe manual path if safe, fix forward; no silent package substitution. |
| Old/new client/API/schema/content/config coexistence | Use capability/generation matrix, additive/forward serializers and staged signed release; hold unknown safety meaning. | P1/P3/P7/P8/P10/P11/P12; compatibility, migration, manifest, artifact and incident graph. | Backend/content/revocation owner, store custodian, safety and rollback authority. | Reject/hold incompatible record/path; maintain last accepted artifact and migrate forward. |
| Unsafe migration rollback request | Refuse lossy downgrade; preserve export/provenance and use forward migration after data/security review. | P3/P8/P9/P11/P12; crash/restore/migration fixture and key-loss game-day plan. | Data/security reviewer, restore operator, account/key authority. | Quarantine uncertain state, retain last durable checkpoint and accepted artifact; explain the hold. |
| Incident pause and recovery | Identify impacted Flutter/plugin/native/content/client generations from artifact manifest; pause rollout; issue reviewed correction and retest. | P7/P9/P10/P11/P12; impact graph, signed artifact, dependency/SBOM, safe-stop and revalidation records. | Incident commander, security/safety/content/store authorities, support capacity. | No release pass claimed; suspend, preserve evidence, correct forward and rerun affected platform scope. |

### 8.1 Flutter-specific forced toolchain facts

The Flutter dossier records approximately quarterly stable windows, the frozen 3.47.2 snapshot versus official 3.47.4
metadata drift, and Swift Package Manager guidance beginning with Flutter 3.44. It also records the documented
CocoaPods registry event on 2026-12-02. These are maintenance inputs for P6/P10, not evidence of a completed migration.
Exact Xcode/macOS, Android SDK/AGP/Gradle/JDK, SwiftPM/CocoaPods resolution, lockfile, source provenance and release
owner remain UNRESOLVED.

## 9. AI-operability and task isolation

| Question | Simulation result |
|---|---|
| Can a fresh AI implement one bounded task without whole-project context? | Yes for a pure P1/P2 Dart contract/presentation slice only when the controlled inputs, allowed files, forbidden scope, state oracle and links are supplied. A camera/lifecycle/checkpoint/release slice must include its native and authority packet(s); no single shared-screen context is sufficient. |
| Are platform exceptions visible in the task graph? | They are enumerable through P4/P5/P6/P7/P10, but Flutter generated plugin registration, runner changes, transitive packages, Xcode/Gradle resolution and final native inventory remain unresolved. The packet graph must reject hidden effects. |
| Can implementation, review and validation remain separate? | In principle: AI implementation, independent design/native/data/release review, machine checks and human device/AT/safety/store validation are separate packets. No reviewer or validator execution is claimed. |
| Are builds/tests deterministic enough to produce evidence? | A plan exists around Flutter/Dart ref/digest, pub lock, native toolchain pins, generated-output manifest and SBOM. Current lock, host, generated and clean-build evidence is absent, so determinism is HELD. |
| Can dependency changes identify affected contracts/tasks/tests? | Yes if the Kavriva adapter boundary, lock/SBOM, generated-output diff and trace graph are enforced. A package-specific object or unlisted channel would make impact opaque and hold the task. |
| Can the project recover without one opaque workstation/provider? | Portable source/locks/contracts/fixtures/manifests and a local Android path can support replacement. iOS Mac/Xcode/signing, devices, stores and any hosted CI remain external; provider-independent fallback and cost/capacity are unresolved. |
| Does the candidate require unavailable human specialist authority? | It requires Android/iOS native, Mac/Xcode/signing, physical devices, TalkBack/VoiceOver/AT, qualified safety/content, security/privacy, backend, store and incident authorities. AI and the nontechnical owner cannot impersonate them. |

The largest AI-operability benefit is one shared Dart state/presentation surface and a common contract/fixture set. The
largest risk is a visually unified Flutter tree hiding native lifecycle, permission, plugin, generated-project,
accessibility, signing or dependency work. The simulation keeps each risk as an accountable packet.

## 10. Exit and forward-recovery summary

### 10.1 Shared product truth that must survive

- Canonical schemas, history/provenance, corrections, publication/revocation generations, operation IDs and migration
  fixtures.
- Scoped package manifests/digests, required compact safety/recovery closure, optional-media metadata and export
  formats.
- Local history, notes, photos, pending operations and conflicts subject to approved privacy/key policy.
- Turkish copy/design intent, accessibility oracle, S1–S15 fixtures, acceptance/negative tests, SBOM/locks/provenance
  and incident runbooks.

### 10.2 Flutter-bound surface

Flutter widgets/state, engine/renderer, Dart runtime artifacts, pub/plugin APIs, platform channels, generated Android/
iOS runners, Gradle/Xcode/SwiftPM configuration, native adapters and signed binaries are candidate/toolchain-bound.
Android Keystore/iOS Keychain raw keys are never exported as portable data.

### 10.3 Forward-only interruption route

1. Stop or hold the affected step/release when a checkpoint, migration, dependency, authority or evidence condition is
   uncertain.
2. Restore only the last explicit durable checkpoint as context; label post-checkpoint physical work unknown/partial.
3. Quarantine corrupt, stale, restored or key-inaccessible data; preserve safe-stop and user-visible explanation.
4. Export safe portable records/manifests/provenance; retain the last accepted signed artifact.
5. Reconcile account, current package/client capability, release/configuration and recall authority in the foreground.
6. Apply reviewed forward migration or replacement adapter/client; rerun affected automated, native, AT, device,
   safety and release evidence.

No lossy rollback, silent history rewrite, raw-key repair, automatic physical continuation or OTA code update is
permitted by this simulation.

### 10.4 Official evidence anchors inherited from the Flutter dossier

These links are source anchors for the mechanisms named in the packets. They prove that a mechanism exists, not that
Kavriva has implemented or passed it:

- Flutter supported deployment platforms: https://docs.flutter.dev/reference/supported-platforms
- Flutter release archive and release metadata: https://docs.flutter.dev/install/archive and
  https://storage.googleapis.com/flutter_infra_release/releases/releases_windows.json
- Flutter architecture and offline-first guidance: https://docs.flutter.dev/resources/architectural-overview and
  https://docs.flutter.dev/app-architecture/design-patterns/offline-first
- Flutter platform channels and lifecycle: https://docs.flutter.dev/platform-integration/platform-channels and
  https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html
- Flutter accessibility, assistive technology and testing: https://docs.flutter.dev/ui/accessibility,
  https://docs.flutter.dev/ui/accessibility/assistive-technologies,
  https://docs.flutter.dev/ui/accessibility/accessibility-testing and
  https://docs.flutter.dev/testing/integration-tests
- Flutter package/dependency and Swift Package Manager guidance:
  https://docs.flutter.dev/packages-and-plugins/using-packages,
  https://docs.flutter.dev/packages-and-plugins/dependency-management and
  https://docs.flutter.dev/packages-and-plugins/swift-package-manager/for-app-developers
- Flutter camera, image picker, path provider and file selector package evidence:
  https://pub.dev/packages/camera, https://pub.dev/packages/image_picker,
  https://pub.dev/packages/path_provider and https://pub.dev/packages/file_selector
- Android lifecycle/background/backup evidence: https://developer.android.com/training/monitoring-device-state/doze-standby,
  https://developer.android.com/develop/background-work/background-tasks/persistent and
  https://developer.android.com/identity/data/autobackup
- Apple background execution evidence: https://developer.apple.com/documentation/BackgroundTasks/choosing-background-strategies-for-your-app

## 11. Final simulation disposition

Final permitted status: OPERABLE WITH MATERIAL CONDITIONS / HELD

This status is limited to the no-code task simulation. It is conditional on all of the following being closed later:

- P1 state truth and P2 Turkish/accessibility presentation remain narrow, traceable and free of physical-truth claims.
- P3 final persistence/checkpoint/migration/key boundary is selected, transaction-safe, forward-only and exportable.
- P4 critical media capability has an owned, locked, reviewed Android/iOS adapter and safe no-photo fallback.
- P5 and P6 have named Android/iOS owners, explicit lifecycle/permission/backup/key/AT evidence and no background-
  timing correctness dependency.
- P7 package/generation/recall/reconciliation protocol is scoped, integrity-checked, cellular-aware and safe offline.
- P8 deterministic contract/negative tests, dependency impact and parity trace are machine-verifiable.
- P9 four-cohort physical-device, network, process-kill and human AT/safety evidence is obtained; none is claimed here.
- P10 Flutter/Dart/native/toolchain/dependency locks, generated-output inventory, SBOM/provenance, signing, clean
  builds and store evidence are complete; no OTA code authority is introduced.
- P11 is independently reviewed by someone who did not implement the affected packet, with Android/iOS parity and
  native/generated closure explicitly checked.
- P12 preserves portable truth, refuses unsafe rollback, supports forward recovery and documents Flutter replacement.
- Mac/Xcode, devices, AT, qualified safety/content, security/privacy, store, backend and incident authorities are
  available without assigning repair/debug work to the nontechnical owner.
- All optional/hosted/free-tier choices carry current cap, overage, alert, export, retention, shutdown and exit
  evidence; no unresolved price or capacity is treated as zero.

No implementation, benchmark, real-device pass, accessibility pass, safety approval, signed build, store release,
score or framework recommendation is claimed. Two independent critiques and manager synthesis remain required.
