# DEBATE-006 — TASK-SIM-MOB-001: KMP + COMPOSE MULTIPLATFORM

Status: `STRUCTURALLY COMPLETE NO-CODE TASK SIMULATION / UNREVIEWED / HELD`  
Date: 2026-09-18  
Candidate: KMP + Compose Multiplatform with shared Kotlin domain/data and shared Compose presentation, plus separate Android and iOS hosts  
Authority: DEBATE-006__TASK_SIM_MOB_001_SPEC.md  
Decision level: bounded planning evidence only; not implementation, prototype, estimate, benchmark, device pass, release, ADR or technology selection

Candidate snapshot inherited and pinned for this simulation: Kotlin/KMP `2.4.20`, Kotlin Multiplatform Gradle plugin
`2.4.20`, Compose Multiplatform `1.12.0` and Compose Compiler Gradle plugin `2.4.20`, with the dossier's documented
Gradle/AGP/Xcode compatibility range. This is not a generated project lock or build pass.

The simulation inherits the common frozen quantities unchanged: 12 MB compact package, optional media up to 150 MB,
250 MB content cache, 25 MB cellular confirmation, unrelated 2 GB catalog exclusion, and the approved normal/stress
motorcycle, record, photo, note, pending-operation and conflict fixtures.

## 1. Simulation boundary

This record simulates how a fresh AI would plan one identical Kavriva change from a bounded context pack. It uses the
controlled task specification and the KMP + Compose dossier; it does not read or modify an implementation repository.

The simulated change is one safety-critical active-maintenance step from a valid selected-motorcycle/task offline package.
It shows Turkish objective, warning and readiness state; accepts an optional photo without treating the photo as
verification; commits only an explicit durable checkpoint; survives lock, call, backgrounding and process termination;
restores only the last durable checkpoint as context; marks uncommitted work unknown/partial; requires accessible current
physical-state revalidation; preserves safe-stop/recovery; and produces Android/iOS release evidence without OTA
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:15–25).

The fixed simulation begins with a resolved motorcycle/model-year/variant, one approved package generation within its
offline window, compact closure installed and optional media absent. Camera permission is not granted; constrained
cellular becomes offline after the step opens; the process is terminated after capture but before the next checkpoint;
no new server recall knowledge is available after restart; screen reader and largest text are enabled
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:27–37).

The candidate boundary is not KMP-native. Shared common Kotlin code and shared Compose UI are separate from the Android
Activity host and the iOS native host/ComposeUIViewController. Android and iOS remain separately signed artifacts; iOS
consumes a generated Kotlin/Native framework; native permissions, camera/files, lifecycle, accessibility and release
work remain host responsibilities
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:183–208, 262–297, 378–395).

## 2. Context-pack and work-split map

### 2.1 Minimum bounded context types

The minimum safe plan has twelve packets because the task specification requires twelve distinct evidence-producing work
packets. They can be grouped for navigation, but not collapsed when doing so would hide platform, authority or reviewer
separation:

1. common product/state contract;
2. common Compose UI/presentation;
3. local persistence/checkpoint/migration;
4. camera/photo/temp-file/privacy;
5. Android lifecycle/accessibility host;
6. iOS lifecycle/accessibility host;
7. offline package/reconciliation compatibility;
8. automated common contract/state/negative tests;
9. physical-device human acceptance;
10. build/signing/provenance/release evidence;
11. independent review;
12. exit/rollback-refusal/forward-recovery.

This is a packet minimum, not a staffing count or effort estimate. A fresh AI receives one packet plus its explicitly
linked upstream/downstream context; it does not infer missing work from a repository-wide scan. The required packet
fields and no-code boundary come from the controlled specification
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:44–67).

### 2.2 Common work versus host work

| Area | Shared KMP/Compose responsibility | Android host responsibility | iOS host responsibility |
|---|---|---|---|
| Product/state | Portable task-step state, warning/readiness/safe-stop meaning, photo-pending meaning, checkpoint/revalidation states, unknown/partial outcomes and copy/state identifiers | Render and act on the contract through Android lifecycle and accessibility semantics | Render and act on the contract through iOS lifecycle, VoiceOver semantics and native escape where required |
| Presentation | Compose screens, state vocabulary, Turkish copy keys, semantic intent, progress/size/hold/recovery presentation and shared test identifiers | Activity, Android back behavior, TalkBack/Switch/Voice Access, permission/dialog/notification return behavior | Native application entry point, ComposeUIViewController integration, VoiceOver/Switch Control, Dynamic Type, native dialog/interop return behavior |
| Data/recovery | Portable schema/manifest contracts, idempotency and explicit partial/unknown/conflict meanings; no database or key policy is assumed | Android storage/checkpoint adapter, process/configuration recovery, Keystore/backup policy when selected | iOS storage/checkpoint adapter, scene/process recovery, Keychain/backup policy when selected |
| Camera/files | Intent and evidence-state contracts only; optional photo remains pending evidence | Android camera/Photo Picker/SAF, URI and temporary-file lifecycle | AVFoundation, PhotosUI/PHPicker, UIDocumentPicker, security-scoped resources and temporary-file lifecycle |
| Reconciliation | Package compatibility, integrity and foreground reconciliation contract | Android connectivity/lifecycle trigger and host presentation | iOS connectivity/lifecycle trigger and host presentation |
| Delivery | Common release meaning, capability contract, offline recovery closure and provenance references | Gradle/AGP/JDK/SDK graph, Android artifact and Play evidence | Xcode/Swift/Kotlin/Native/macOS graph, generated framework, iOS artifact and App Store evidence |

The shared layer may own deterministic rules and semantic intent, but it cannot own current entitlement, recall,
publication, native permission, raw keys, process survival or store authority. The KMP + Compose dossier makes those
limits explicit
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:210–237, 239–260, 262–297).

## 3. Required packet records

Each packet below contains every field required by the common task specification:
purpose and user outcome; minimum inputs; allowed scope; forbidden scope; upstream/downstream dependencies;
candidate-specific dependency/generated/native boundary; Android/iOS divergence; acceptance and negative cases; evidence
artifact; implementer/reviewer/validator separation; external human/store/device action; failure and recovery;
unresolved cost/capacity trigger; and Obsidian-compatible links
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:55–67).

### Packet 1 — Shared product/state contract

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Define one portable contract for opening the active step, showing objective/warning/readiness/safe-stop, recording optional photo pending evidence, committing an explicit checkpoint, restoring context, requiring revalidation and producing current/held/unknown/partial outcomes. |
| Minimum input documents/contracts | TASK-SIM-MOB-001 §§2–4; approved KMP + Compose boundary; DEC-0024 offline safety; DEC-0025 approval/suspension/reconciliation; State Matrix; SCR-014/SCR-015/SCR-016 entries in Screen Catalog. |
| Allowed files/modules to change | Conceptual common contract/state nodes only: common Kotlin state vocabulary, transition table, Turkish copy keys, semantic identifiers and fixture references. Exact implementation paths are not selected in this simulation. |
| Forbidden scope | Compose layout, Android/iOS APIs, camera verification, database/key policy, server publication/recall authority, physical torque/fitment/safety values, OTA and store signing. |
| Upstream/downstream dependencies | Upstream: approved package/variant context and task fixture. Downstream: shared Compose UI, persistence, package reconciliation, Android/iOS hosts, tests, review and release evidence. |
| Candidate-specific dependency/generated/native boundary | Shared commonMain KMP logic and portable contracts; shared Compose may consume the state but may not become authority. No generated framework is a source of product truth. |
| Android/iOS divergence | Meaning and allowed transitions are identical. Android and iOS differ in lifecycle callback, focus, permission, native surface and physical-state revalidation expression. |
| Acceptance and negative cases | Offline step opens with required closure; camera denial leaves an optional-photo path usable; photo is never verification; kill before commit yields unknown/partial; restart restores context only; failed/uncertain revalidation holds; successful revalidation permits only the next allowed transition; reconnect rechecks package/release/recall. |
| Evidence artifact | No-code transition table, input/output contract, negative-case matrix, traceability map and unresolved-fact register. |
| Implementer/reviewer/validator separation | AI contract implementer prepares the bounded record; independent domain/safety reviewer checks meaning; separate validator checks every required outcome against the task fixture. |
| External human/store/device action | Qualified safety/content authority confirms task meaning; no store or device action is claimed at this packet. |
| Failure and recovery | Unknown, partial, stale or missing states fail closed; safe-stop/recovery remains available; no automatic continue from restored UI state. |
| Unresolved cost/capacity trigger | Missing safety/domain reviewer, contract owner or validator places the packet HELD. No price, duration or staffing estimate is invented. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/SCREEN_CATALOG]], [[07_AI_ARCHITECTURE/CONTRACTS/README]], [[07_AI_ARCHITECTURE/TASK_EXECUTION_PROTOCOL]], [[06_DELIVERY_PLANNING/TASK_INDEX]] |

KMP-specific boundary evidence: the common core may own readiness, stale/recall/safe-stop meanings, package manifest
rules, provenance relationships, pending operation identity and Turkish semantic identifiers, but remains Kavriva-owned
rather than framework authority
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:239–260).

### Packet 2 — Shared Compose UI and presentation

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Render the active step, objective, warning, readiness, optional-photo status, progress, unknown/partial hold, revalidation and safe-stop/recovery in a shared Compose presentation without changing their meaning. |
| Minimum input documents/contracts | Packet 1; TASK-SIM-MOB-001 required outcomes; SCR-014 active guide step, SCR-015 problem/mismatch/recovery, SCR-016 resume revalidation; approved active-application visual handoff; accessibility matrix. |
| Allowed files/modules to change | Conceptual common Compose screen/state mapping, Turkish copy keys, semantic IDs, focus/action intent, test IDs and visible recovery/readiness vocabulary. |
| Forbidden scope | Android/iOS permission wording, camera/file/share/notification surfaces, Keystore/Keychain, durable checkpoint commit, current authority, store signing, generated-framework manual mutation and OTA. |
| Upstream/downstream dependencies | Upstream: Packet 1. Downstream: Android host Packet 5, iOS host Packet 6, camera Packet 4, automated tests Packet 8, physical acceptance Packet 9. |
| Candidate-specific dependency/generated/native boundary | Compose Multiplatform shared composables and presentation state; Android maps to Jetpack Compose artifacts; iOS uses ComposeUIViewController through the generated Kotlin/Native framework. |
| Android/iOS divergence | Android host owns back behavior, TalkBack semantics, font scale, permission/dialog return and native surfaces. iOS host owns VoiceOver mapping, Dynamic Type, native interop, scene return and native escape. |
| Acceptance and negative cases | Shared screen exposes all required states; optional photo never changes verification state; stale/unknown/held cannot show an active continuation; recovery remains reachable; largest text does not hide stop/recovery; native surfaces return focus to the correct state; unresolved mapping holds the flow. |
| Evidence artifact | No-code screen/state matrix, semantic-ID map, focus and announcement intent, safe-stop/recovery trace and platform-exception list. |
| Implementer/reviewer/validator separation | AI Compose implementer prepares bounded presentation mapping; independent design/accessibility reviewer checks Turkish meaning and hierarchy; separate Android/iOS validator checks host-specific expression. |
| External human/store/device action | Human accessibility and safety reviewers later inspect the design and device behavior; no screenshot or API inspection is a pass. |
| Failure and recovery | If a state cannot be expressed clearly on either platform, keep the flow held with safe-stop/recovery and route to a native host exception only through review. |
| Unresolved cost/capacity trigger | Missing Compose reviewer, Android/iOS accessibility owner, native escape owner or bounded design artifact places the packet HELD. |
| Obsidian-compatible links | [[03_DESIGN/SCREEN_CATALOG]], [[03_DESIGN/SCREEN_FAMILY_SPECS]], [[03_DESIGN/KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_01_HANDOFF]], [[03_DESIGN/DESIGN_PRINCIPLES]], [[03_DESIGN/STATE_MATRIX]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]] |

Compose documentation records semantics, traversal and iOS mapping, but also native interop and non-pixel-perfect
platform behavior. A shared composable is not native accessibility acceptance
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:210–228, 358–376).

### Packet 3 — Local persistence, checkpoint and migration

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Save only explicit durable checkpoints; restore the last durable checkpoint as context; preserve unknown/partial physical progress; prevent auto-continue; support safe forward recovery and data-preserving migration. |
| Minimum input documents/contracts | Packet 1; TASK-SIM-MOB-001 §§3–4; common data/offline fixture; DEC-0024/0025; KMP + Compose persistence boundary; approved history/evidence/trust and active-recovery design. |
| Allowed files/modules to change | Conceptual portable schema, checkpoint/event contract, migration journal and platform storage adapter interfaces. No database technology is selected. |
| Forbidden scope | UI state as durable truth; raw key export; restored cache as entitlement/eligibility; silent overwrite/discard; binary rollback used as data rollback; physical-state proof from a saved confirmation. |
| Upstream/downstream dependencies | Upstream: Packet 1. Downstream: Android/iOS lifecycle hosts, package reconciliation, camera temp recovery, tests, release graph and exit plan. |
| Candidate-specific dependency/generated/native boundary | Shared KMP contract may define durable state categories; actual database, transaction, encryption and key storage remain platform/native implementation boundaries. Compose Multiplatform does not supply them automatically. |
| Android/iOS divergence | Android process/configuration recreation, storage pressure, Keystore and backup rules differ from iOS scene/process behavior, Keychain/Data Protection and backup rules. Both must preserve the same state semantics. |
| Acceptance and negative cases | Commit only after explicit checkpoint; terminate after capture before commit; restart restores last durable context; uncommitted physical progress is unknown/partial; interrupted migration is visible and recoverable; no auto-continue; key/backup mismatch quarantines state. |
| Evidence artifact | No-code checkpoint state machine, data-class/backup matrix, migration compatibility table, restore/clone/key-loss negative cases and durable-write boundary description. |
| Implementer/reviewer/validator separation | AI data/migration implementer prepares contracts; independent data/security reviewer checks loss, replay and key semantics; separate recovery validator checks interruption and forward-migration cases. |
| External human/store/device action | Human data/security authority and later device restore game-day are required; no backup or migration pass is claimed. |
| Failure and recovery | Partial/unknown state stays held; quarantine restored or key-invalid state; re-authenticate or recover from account/portable data; preserve valid new data; forward-migrate after review. |
| Unresolved cost/capacity trigger | No database/key/backup owner, migration reviewer, restore environment or safe fallback means HELD. Amounts, duration and provider choice remain unresolved. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/SCREEN_CATALOG]], [[07_AI_ARCHITECTURE/CONTRACTS/README]], [[90_TEMPLATES/TASK_TEMPLATE]] |

The dossier explicitly leaves database, ORM, serialization, encryption and backup policy unresolved and rejects the
assumption that Compose/KMP provides atomic writes, crash recovery or safe migration
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:299–322).

### Packet 4 — Camera, photo, temporary file and privacy

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Allow an optional photo when permission is available; explain denial accessibly; label captured media as pending evidence; preserve privacy/classification; recover or quarantine temporary data after process loss. |
| Minimum input documents/contracts | Packet 1; TASK-SIM-MOB-001 camera/termination outcomes; privacy and export rules; KMP + Compose native-surface boundary; active-step safety/recovery design. |
| Allowed files/modules to change | Shared capture-requested/photo-pending/temporary/recovery state contracts; Android and iOS adapter specifications for permission, capture, temporary storage and classification. |
| Forbidden scope | Treating a photo as verification or physical truth; making photo mandatory when the task says optional; silent upload/publication; unclassified export; raw URI/key authority; hidden background correctness. |
| Upstream/downstream dependencies | Upstream: Packet 1 and Package Packet 7. Downstream: Compose Packet 2, lifecycle Packets 5–6, persistence Packet 3, tests Packet 8, device acceptance Packet 9. |
| Candidate-specific dependency/generated/native boundary | Android host chooses CameraX/Camera2 and Photo Picker/SAF path; iOS host chooses AVFoundation, PhotosUI/PHPicker and UIDocumentPicker path. Shared Compose only exposes intent/status. |
| Android/iOS divergence | Android permission/URI/process-loss and Photo Picker behavior differ from iOS permission purpose, security-scoped resource, bookmark/temporary-file and capture-session behavior. |
| Acceptance and negative cases | Permission denied leaves the step usable without media; capture succeeds but remains pending; process termination before checkpoint leaves photo/temp work recoverable or quarantined and physical progress unknown/partial; malformed, expired or low-space media never appears verified; privacy label and retry/manual path are visible. |
| Evidence artifact | No-code media state/data-flow diagram, classification and disclosure matrix, temporary-file cleanup/recovery cases, permission/error copy map and dependency boundary inventory. |
| Implementer/reviewer/validator separation | AI shared-state implementer and platform adapter implementers are separate; independent privacy/safety reviewer checks classification and non-verification; validator checks Android/iOS negative cases. |
| External human/store/device action | Human privacy/safety authority, platform permission review and later camera/picker device testing are required; no camera/device pass is claimed. |
| Failure and recovery | Denial uses manual/no-media path; process loss marks pending/unknown and preserves safe-stop; invalid/untrusted media is quarantined; only proven temporary copies may be cleaned. |
| Unresolved cost/capacity trigger | Missing Android/iOS media owner, privacy reviewer, safe manual fallback or device access places the packet HELD. No package price or time estimate is supplied. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[03_DESIGN/SCREEN_CATALOG]], [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/INFORMATION_RULES]], [[07_AI_ARCHITECTURE/CONTRACTS/README]] |

The candidate dossier assigns camera, picker, file, share and native resource lifetimes to the hosts; opening a picker
does not establish correctness, official status or publication authority
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:344–356).

### Packet 5 — Android lifecycle and accessibility host

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Host the shared Compose step on Android through lock, incoming call, backgrounding, process termination and restart; express safe-stop/recovery and current-state revalidation with TalkBack, largest text and native control behavior. |
| Minimum input documents/contracts | Packets 1–4; TASK-SIM-MOB-001 fixed Android path; Android cohort and interruption fixture; approved SCR-014/SCR-016 and accessibility matrix; KMP + Compose Android host boundary. |
| Allowed files/modules to change | Conceptual Android Activity/host lifecycle adapter, Compose host integration, Back/focus/announcement mapping, permission/dialog return mapping and foreground reconciliation trigger. |
| Forbidden scope | Changing common safety meaning; using Activity/UI state as durable truth; granting current authority offline; relying on scheduled background work or push; silently bypassing iOS work; changing release/signing graph without Packet 10. |
| Upstream/downstream dependencies | Upstream: Packets 1–4 and 7. Downstream: common test Packet 8, physical Android acceptance Packet 9, build/release Packet 10 and independent review Packet 11. |
| Candidate-specific dependency/generated/native boundary | Android Activity + shared Compose content; Android lifecycle/process, TalkBack/Switch/Voice Access, runtime permissions, Photo Picker, notification/deep-link return and Android storage/Keystore remain native. |
| Android/iOS divergence | This packet is Android-only: API 29 constrained and Android 13+ main cohorts, Android process/configuration/memory pressure, font scale, Back, TalkBack and Android system surfaces. iOS must be handled by Packet 6. |
| Acceptance and negative cases | Lock/call/background/process kill after photo capture; last durable checkpoint restores; no continue until accessible physical revalidation; denied camera remains optional; failed/uncertain revalidation holds; TalkBack and largest text keep warning, stop and recovery operable. |
| Evidence artifact | No-code Android lifecycle state table, host/Compose semantic mapping, focus/announcement map, process-kill/restart negative-case plan and platform-exception list. |
| Implementer/reviewer/validator separation | AI Android host implementer prepares bounded adapter plan; independent Android/accessibility reviewer checks semantics and lifecycle; separate validator checks interruption and recovery matrix. |
| External human/store/device action | Physical constrained/main Android devices, human TalkBack reviewer and later Android store/build custodian are required; no device result is claimed. |
| Failure and recovery | Any missing callback, stale state, focus loss or unknown physical condition returns to safe-stop/recovery and held status; foreground reopen/reconciliation is the recovery path. |
| Unresolved cost/capacity trigger | No Android native owner, TalkBack reviewer, device cohort or lifecycle evidence path means HELD; no device-lab or labor amount is invented. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[03_DESIGN/SCREEN_CATALOG]], [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_01_HANDOFF]], [[04_TECH_STRATEGY/EVALUATION_PROTOCOL]] |

The Android host owns lifecycle/process integration, Android accessibility, permissions, camera/file surfaces, backup,
background constraints and Android build/release. Shared Compose does not make Android host behavior correct by itself
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:262–277).

### Packet 6 — iOS lifecycle and accessibility host

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Host the shared Compose step through iOS scene/process interruption, lock, call, backgrounding and restart; preserve the last checkpoint as context; provide VoiceOver/largest-text/revalidation and a reviewed native escape where shared semantics or a system surface cannot close the requirement. |
| Minimum input documents/contracts | Packets 1–5 except Android-only evidence; TASK-SIM-MOB-001 iOS path; iOS cohort and interruption fixture; approved active/recovery screens; KMP + Compose iOS boundary and accessibility matrix. |
| Allowed files/modules to change | Conceptual iOS application entry point, ComposeUIViewController integration, scene/process adapter, VoiceOver/focus/announcement mapping, Dynamic Type/reflow, native permission/camera/files/share return and explicit native escape contract. |
| Forbidden scope | Treat Compose iOS mapping as a pass; changing common state meaning; using a generated framework as current authority; ignoring iOS high-contrast/native surface gaps; raw key export; OTA; unreviewed generated-file edits. |
| Upstream/downstream dependencies | Upstream: Packets 1–4 and 7. Downstream: physical iOS acceptance Packet 9, build/framework/release Packet 10, independent review Packet 11 and exit Packet 12. |
| Candidate-specific dependency/generated/native boundary | iOS native host plus ComposeUIViewController consumes a generated Kotlin/Native framework. AVFoundation, PhotosUI/PHPicker, UIDocumentPicker, Keychain, UserNotifications, URLSession/BGTaskScheduler and Xcode/macOS remain host boundaries. |
| Android/iOS divergence | This packet is iOS-only: oldest iOS 16.4-capable and current standard iPhone cohorts, scene/application lifecycle, VoiceOver/Switch Control, Dynamic Type, security-scoped files, permission purpose strings and iOS native escape. |
| Acceptance and negative cases | Capture then terminate before checkpoint; restart shows context only; VoiceOver announces warning/stop/unknown/recovery; largest text preserves all actions; native picker/permission/share return focus safely; unresolved semantics or high-contrast behavior holds continuation; revalidation failure remains held. |
| Evidence artifact | No-code iOS host/lifecycle map, Compose-to-iOS semantic mapping, native-escape decision record, focus/reflow/announcement plan, generated-framework identity dependency and negative-case matrix. |
| Implementer/reviewer/validator separation | AI iOS host implementer prepares the bounded plan; independent iOS/accessibility reviewer checks VoiceOver/native behavior; separate validator checks process and host-return evidence. |
| External human/store/device action | Physical oldest/current iPhone access, human VoiceOver reviewer, Mac/Xcode and App Store release authority are required later; no device or store pass is claimed. |
| Failure and recovery | If generated framework, Compose semantics or native escape is stale/ambiguous, hold the path; preserve last durable context and safe-stop; require revalidation after restart; use foreground reconciliation. |
| Unresolved cost/capacity trigger | Missing Mac/Xcode, iOS native owner, VoiceOver reviewer, native-escape owner or iPhone cohort means HELD; no hosted-build or device cost is estimated. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[03_DESIGN/SCREEN_CATALOG]], [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_01_HANDOFF]], [[04_TECH_STRATEGY/EVALUATION_PROTOCOL]] |

The iOS host owns scene/process behavior, VoiceOver, Dynamic Type, native permissions/pickers/share, Keychain/backup,
background transfer and Xcode/macOS/framework signing. A functioning ComposeUIViewController is not a lifecycle or
VoiceOver pass
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:279–297, 358–376).

### Packet 7 — Offline package and reconciliation compatibility

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Ensure the step uses only the installed valid scoped package, does not download unrelated content, remains safe when cellular becomes offline, and reconciles package/release/recall eligibility in the foreground before authority-sensitive continuation. |
| Minimum input documents/contracts | Packets 1–6; TASK-SIM-MOB-001 fixed package/network state; common offline/package fixture; DEC-0023/0024/0025; KMP + Compose package boundary. |
| Allowed files/modules to change | Conceptual package manifest, compatibility envelope, size/consent/progress states, integrity/atomic-promotion contract, foreground reconciliation adapter and explicit stale/held/recalled outcomes. |
| Forbidden scope | Full catalog or unrelated motorcycle download; silent optional media download; notification/push as recall authority; scheduled background correctness; stale package as current; offline publication or entitlement mutation. |
| Upstream/downstream dependencies | Upstream: Packet 1 and approved installed package. Downstream: Compose Packet 2, persistence Packet 3, lifecycle Packets 5–6, tests Packets 8–9 and release Packet 10. |
| Candidate-specific dependency/generated/native boundary | Shared KMP core and Compose display package state; Android/iOS hosts own file/transfer resources, cancellation, low-storage and scheduler integration. |
| Android/iOS divergence | Android and iOS background scheduling, storage and transfer APIs differ; both use foreground reconciliation as correctness and must expose the same package status meanings. |
| Acceptance and negative cases | Step opens from valid package with compact closure; optional media absent; constrained cellular loss after open leaves step usable; no unrelated download; package corruption/partial/compatibility mismatch holds; reconnect checks current release/recall before further authority. |
| Evidence artifact | No-code manifest/state diagram, data-scope and size decision record, old/new staging/atomicity matrix, compatibility/reconciliation table and over-download negative case. |
| Implementer/reviewer/validator separation | AI package-contract implementer prepares bounded state; independent safety/data reviewer checks scope, integrity and recall; separate validator checks offline/reconnect outcomes. |
| External human/store/device action | Backend/content/recall authority and later network/device validation are external; no package/network pass is claimed. |
| Failure and recovery | Incomplete/corrupt/stale package is held and safe-stop remains; retry from verified checkpoint or re-download after reconciliation; no silent eviction or overwrite. |
| Unresolved cost/capacity trigger | Missing package-integrity owner, foreground reconciliation owner, storage/transfer fallback or offline validation capacity means HELD; no transfer cost or timing estimate. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[00_CONTROL/DECISION_LOG]], [[03_DESIGN/STATE_MATRIX]], [[07_AI_ARCHITECTURE/CONTRACTS/README]] |

The KMP + Compose dossier requires the package lifecycle to end in foreground reconciliation and prohibits a full
catalog, unrelated motorcycle or unused heavy-media download
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:324–342).

### Packet 8 — Automated common contract, state and negative tests

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Define deterministic, no-code test vectors for shared state meaning, package compatibility, checkpoint outcomes, optional-photo classification, revalidation and failure/hold behavior. |
| Minimum input documents/contracts | Packets 1, 3 and 7; TASK-SIM-MOB-001 required outcomes; S1–S15 fixture; State Matrix; controlled dossier template; approved safety/recovery design. |
| Allowed files/modules to change | Conceptual common contract fixtures, transition vectors, negative-case catalog, traceability and expected-status records. |
| Forbidden scope | Claiming physical-device, VoiceOver/TalkBack, store, signing, native-dialog or safety acceptance; treating static Compose semantics or AI review as human evidence; testing only the shared layer while hiding host divergence. |
| Upstream/downstream dependencies | Upstream: shared state, persistence and package contracts. Downstream: Android/iOS host tests, Packet 9 human acceptance, Packet 10 release evidence and Packet 11 independent review. |
| Candidate-specific dependency/generated/native boundary | Common KMP test target/fixture concept may exercise portable rules; Compose UI and generated iOS framework behavior are separate evidence surfaces, not silently covered by common vectors. |
| Android/iOS divergence | Common expected state/result is identical; native lifecycle, permission, semantics, focus, file and background cases route to Packets 5–6 and 9. |
| Acceptance and negative cases | Vectors cover camera denial, photo pending, kill-before-commit, restart/no-auto-continue, revalidation success/failure/uncertainty, stale/recall/unknown package, reconnect, duplicate/partial/corrupt operations and no over-download. |
| Evidence artifact | No-code test-vector catalog, expected transition/outcome table, negative-case traceability and gap report; no execution result is asserted. |
| Implementer/reviewer/validator separation | AI fixture author is separate from contract reviewer; independent validator checks expected results and confirms that native/human evidence is not misclassified as automated. |
| External human/store/device action | Human safety, accessibility and platform validators remain required for anything not observable in common contract vectors. |
| Failure and recovery | Missing vector, contradictory expected outcome or untestable boundary remains HELD; route the case to the appropriate host/device/human packet. |
| Unresolved cost/capacity trigger | No independent test validator or fixture-maintainer capacity means HELD; no automation/tooling price or execution duration is estimated. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE]], [[03_DESIGN/STATE_MATRIX]], [[04_TECH_STRATEGY/EVALUATION_PROTOCOL]], [[07_AI_ARCHITECTURE/TASK_EXECUTION_PROTOCOL]], [[90_TEMPLATES/TASK_TEMPLATE]] |

Automated evidence is useful for shared state and negative cases, but no API or static check substitutes for human
assistive-technology/device evidence
(DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:76–94).

### Packet 9 — Real-device human acceptance

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Obtain the later physical Android/iOS and human accessibility evidence that the simulated state remains safe through interruption, restart, revalidation, optional photo handling and safe-stop/recovery. |
| Minimum input documents/contracts | Packets 1–8; all four DEBATE-006 device cohorts; network/interruption fixture; Turkish accessibility matrix; active/recovery screens; safety/content acceptance rules. |
| Allowed files/modules to change | No-code acceptance runbook, device/cohort matrix, observation fields, evidence-capture and defect/hold record. |
| Forbidden scope | Replacing a physical device/human test with a simulator, documentation, API availability, screenshot, AI statement or owner self-attestation; inventing motorcycle-specific safety values; asking the nontechnical owner to repair builds. |
| Upstream/downstream dependencies | All prior packets. Downstream: release evidence Packet 10, independent review Packet 11 and final hold/reopen decision. |
| Candidate-specific dependency/generated/native boundary | Shared Compose semantics plus Android host and iOS host/native escape are all exercised; generated iOS framework identity must match the reviewed release graph. |
| Android/iOS divergence | Android uses constrained/main cohorts with TalkBack; iOS uses oldest/current cohorts with VoiceOver. Native permission, picker, lifecycle, focus, font-scale/Dynamic Type and high-contrast behavior are platform-specific. |
| Acceptance and negative cases | Screen reader and largest text are active; lock/call/background/termination after photo capture; restart restores context only; revalidation is required; failure/uncertainty holds; safe-stop/recovery remains accessible; no photo becomes verification; reconnect checks current package/recall. |
| Evidence artifact | Later human/device run record with cohort, OS, app/artifact identity, observed state, negative case, reviewer identity and hold/reopen disposition. This simulation does not claim that the record exists or passed. |
| Implementer/reviewer/validator separation | Implementer cannot be sole AT/safety reviewer; independent Android and iOS AT reviewers and a separate validator review the evidence and parity. |
| External human/store/device action | Physical Android/iPhone access, TalkBack/VoiceOver users or qualified testers, and qualified safety/content reviewer are mandatory external actions. Store publication is handled by Packet 10. |
| Failure and recovery | Any failure, missing cohort, inaccessible native surface or ambiguous physical-state result holds the affected path; preserve safe-stop/recovery and repeat after a reviewed correction. |
| Unresolved cost/capacity trigger | No physical devices/testers/AT/safety reviewer or no evidence custody means HELD; no purchase, lab or tester cost is estimated. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[03_DESIGN/SCREEN_CATALOG]], [[03_DESIGN/STATE_MATRIX]], [[04_TECH_STRATEGY/EVALUATION_PROTOCOL]] |

The common fixture requires actual devices for oldest/current cohorts and says simulators do not replace real-device or
real assistive-technology evidence
(DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:48–63; 00_CONTROL/DECISION_LOG.md:825–836).

### Packet 10 — Build, signing, provenance and release evidence

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Bind the reviewed common KMP/Compose source, Android/iOS hosts, generated Kotlin/Native framework, dependencies, toolchains, artifacts, signing and staged release evidence without OTA. |
| Minimum input documents/contracts | Packets 1–9; DEBATE-005 release governance; KMP + Compose release boundary; exact DEBATE-006 snapshot; store/build policy and release-hold rules. |
| Allowed files/modules to change | Conceptual closed release manifest, source/dependency/toolchain inputs, generated-framework identity, SBOM/provenance/attestation records, artifact digests, verification/signing records and staged rollout evidence. |
| Forbidden scope | Rebuilding from unreviewed source at promotion; untracked generated-file edits; OTA/runtime code delivery; signing without independent verification; treating a Compose preview/live edit, source diff or framework availability as release proof; changing content authority through the client. |
| Upstream/downstream dependencies | Upstream: all implementation/evidence packets. Downstream: independent review Packet 11, forward-recovery/exit Packet 12 and store authority. |
| Candidate-specific dependency/generated/native boundary | Kotlin/KMP/Compose/compiler/runtime, Gradle/AGP/JDK, Android Jetpack mapping, Xcode/Swift/Kotlin/Native, macOS, generated iOS framework, native host source and two signed artifacts form one closed graph with platform branches. |
| Android/iOS divergence | Android Gradle/AGP/JDK/SDK/Play graph and artifact differ from iOS Xcode/Swift/Kotlin/Native/macOS/App Store graph. A shared revision must be bound to both host revisions and generated framework identity. |
| Acceptance and negative cases | Missing lock/SBOM/provenance/signer/verifier/compatibility or stale generated framework holds; common-source change triggers both-platform impact review; platform-only change cannot bypass shared contract check; old/new clients remain explicit; no OTA; irreversible migration uses forward recovery. |
| Evidence artifact | Closed release graph/manifest, exact source and dependency records, generated framework digest, SBOM, provenance/attestation, independent verification, signing custody record, staged artifact identities and revocation/suspension context. No artifact or store pass is claimed in this simulation. |
| Implementer/reviewer/validator separation | AI release preparer assembles evidence; independent verifier checks graph, digest and provenance; owner/store custodian performs external signing/publication actions; separate safety/security reviewer confirms impact. |
| External human/store/device action | Legal store identities, signing/key custody, Play/App Store authorities, Mac/Xcode access and staged store actions remain external; the nontechnical owner is not asked to build or repair. |
| Failure and recovery | Hold the affected artifact/capability, retain last accepted artifact, preserve evidence, suspend affected generation if required, correct through authorized path, re-sign/re-stage and reconcile. No binary rollback pretends to undo data migration. |
| Unresolved cost/capacity trigger | Missing Mac/Xcode, CI or recoverable build path, signer, verifier, SBOM/provenance owner, store authority or incident capacity means HELD; no hosted-build price, duration or SLA is invented. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[04_TECH_STRATEGY/DEBATES/DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE]], [[00_CONTROL/DECISION_LOG]], [[04_TECH_STRATEGY/EVALUATION_PROTOCOL]], [[07_AI_ARCHITECTURE/TASK_EXECUTION_PROTOCOL]] |

The KMP + Compose dossier requires two separately signed artifacts and binds shared/host source, toolchain, dependencies,
offline closure, provenance, SBOM, verification, signing and suspension generations. No OTA path is evaluated
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:378–395). DEBATE-005 requires promotion of the exact immutable verified artifact,
not a fresh untracked rebuild
(00_CONTROL/DECISION_LOG.md:680–698).

### Packet 11 — Independent review

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Independently detect incomplete shared/Android/iOS parity, hidden generated/native work, unsafe restore/continue, over-download, inaccessible recovery and release-evidence gaps before any approval. |
| Minimum input documents/contracts | Packets 1–10; TASK-SIM-MOB-001 spec; KMP + Compose dossier; DEC-0024–0029; risk register; controlled dossier/template; approved screens and state matrix. |
| Allowed files/modules to change | Review checklist, traceability links, issue/hold findings, parity matrix, dependency/generated-file inventory and reviewer disposition. |
| Forbidden scope | Self-approval by implementer; AI output as proof; owner coding/debugging/build repair; cached browser/client role state as authority; changing safety or release rules to clear a finding. |
| Upstream/downstream dependencies | Reviews every packet and their links. Downstream: release/exit decision and manager synthesis; no implementation mutation. |
| Candidate-specific dependency/generated/native boundary | Review separately covers common Compose/domain, Android Activity/native surfaces, iOS ComposeUIViewController/native escape, Kotlin/Native generated framework, platform toolchains and closed release graph. |
| Android/iOS divergence | Require paired parity review: Android lifecycle/TalkBack/permissions and iOS lifecycle/VoiceOver/native mapping are distinct review subjects; a common Compose diff does not close either host. |
| Acceptance and negative cases | Missing packet/field/link; optional photo treated as verification; auto-continue; background/push dependency; missing iOS native escape; stale generated framework; missing native fallback; OTA; over-download; no forward recovery; undocumented owner all produce HOLD or rejection under the spec. |
| Evidence artifact | Independent review record with packet-by-packet field completion, parity findings, traceability gaps, dependency/generated boundary findings and explicit hold/reopen disposition. |
| Implementer/reviewer/validator separation | Reviewer is independent of packet implementers; validator independently checks that the review itself covers all twelve packets and no documentary result is called a device/build pass. |
| External human/store/device action | Qualified safety, accessibility, security and release authorities remain independent; reviewer cannot impersonate store identity or physical-device evidence. |
| Failure and recovery | Return incomplete work to the responsible packet with a visible reason; keep candidate HELD; preserve safe-stop/recovery and last accepted artifacts while corrections are reviewed. |
| Unresolved cost/capacity trigger | No independent reviewer, parity validator, safety/AT/security authority or evidence-custody path means HELD; no review capacity or price is estimated. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[04_TECH_STRATEGY/RISK_REGISTER]], [[00_CONTROL/DECISION_LOG]], [[03_DESIGN/SCREEN_COVERAGE_TRACEABILITY]], [[07_AI_ARCHITECTURE/TASK_EXECUTION_PROTOCOL]] |

The approved AI model requires separate implementation, review and validation, and human authorities remain necessary for
safety, accessibility, devices, stores and signing
(00_CONTROL/DECISION_LOG.md:717–769; DEBATE-006__TASK_SIM_MOB_001_SPEC.md:70–83).

### Packet 12 — Exit, rollback refusal and forward recovery

| Required field | Bounded record |
|---|---|
| Purpose and user outcome | Preserve product truth, user history, package manifests, evidence lineage and acceptance fixtures across a framework change; refuse unsafe binary rollback; recover forward without lying about migrated data or physical state. |
| Minimum input documents/contracts | Packets 1, 3, 7, 10 and 11; KMP + Compose exit dossier; DEC-0025/0027; TASK-SIM-MOB-001 automatic failure conditions; portable contract and migration rules. |
| Allowed files/modules to change | Conceptual portable schema/manifest/fixture inventory, migration and coexistence plan, rollback-refusal record, last-accepted-artifact record and forward-recovery contract. |
| Forbidden scope | Silent history rewrite/delete; binary rollback as data rollback; restored UI as physical proof; raw platform-key export; OTA; unreviewed replacement; dropping safe-stop/recovery; claiming portability success without rehearsal. |
| Upstream/downstream dependencies | Upstream: durable data and release graph; downstream: future replacement client, independent review and controlled closure of the old path. |
| Candidate-specific dependency/generated/native boundary | Shared Compose source, Kotlin/Native binaries, Compose compiler/runtime, generated iOS framework, Android host integration, iOS host/native escape and signed artifacts are candidate/toolchain-bound. Portable contracts and fixtures must sit outside them. |
| Android/iOS divergence | Replacement needs Android and iOS host implementations, framework integration, signing and acceptance; a shared Compose source migration does not remove native host or generated-framework parity. |
| Acceptance and negative cases | Interrupted migration remains explicit; no known-good compatible rollback holds the scope; valid new data/history survives; old/new client coexistence is controlled; generated-framework mismatch blocks iOS; physical progress remains unknown until revalidation. |
| Evidence artifact | No-code portable-asset inventory, contract-to-boundary map, forward-migration/coexistence matrix, rollback-refusal scenario, artifact retention and recovery decision record. |
| Implementer/reviewer/validator separation | AI migration planner is separate from data/security/release reviewer; independent validator checks no lossy rollback, no raw-key export and preserved safety/recovery. |
| External human/store/device action | Owner/store authority, data/security reviewer, release signer, safety/accessibility reviewers and later replacement-device evidence are external; no user repair is requested. |
| Failure and recovery | Keep last accepted artifact and portable records; hold affected path; quarantine unsafe state; forward-migrate after review; issue correction/suspension through authorized release graph; revalidate before reopening. |
| Unresolved cost/capacity trigger | Missing portable schema owner, migration/recovery reviewer, replacement capacity or artifact custody means HELD; no migration effort, duration or price is estimated. |
| Obsidian-compatible links | [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_KMP_COMPOSE]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[00_CONTROL/DECISION_LOG]], [[07_AI_ARCHITECTURE/CONTRACTS/README]], [[03_DESIGN/STATE_MATRIX]], [[04_TECH_STRATEGY/EVALUATION_PROTOCOL]] |

The candidate dossier keeps schemas, history, manifests, fixtures, exports, acceptance oracles and release evidence
portable while binding Compose/Kotlin/Native/generated-framework/host assets. It explicitly refuses lossy rollback and
claims no exit pass
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:879–911).

## 4. Simulation questions and evidence boundaries

### How many distinct context types must a fresh AI understand?

Twelve bounded packet types are the minimum record. The common/domain and Compose packets can share a context pack only
when their authority and review fields remain visible. Android and iOS host packets must remain distinct because their
lifecycle, accessibility, native surfaces and toolchains diverge. Build/release, independent review and exit must remain
separate because signing, evidence custody, reviewer independence and migration are different authorities.

### Where does a routine shared change split?

The routine shared change is:

common KMP state contract -> shared Compose screen/semantic intent -> Android host expression + iOS host expression
-> common negative vectors -> physical Android/iOS acceptance -> two-artifact build/release evidence.

The split occurs at Android/iOS lifecycle callbacks, camera/file permissions and resources, focus/announcement semantics,
native escape, storage/keys, generated Kotlin/Native framework integration, build/signing and store release. A shared
Compose change can therefore require both host reviews even when the screen source is common
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:187–208, 262–297, 378–395).

### What generated or native files can change indirectly?

The simulation treats these as review-visible boundaries:

- generated Kotlin/Native iOS framework and its Swift/Objective-C-facing integration;
- Compose compiler/runtime and Android Jetpack artifact mapping;
- Gradle/AGP/JDK/Android SDK inputs;
- Xcode/Swift/Kotlin/Native/macOS inputs;
- Android Activity/permission/Photo Picker/notification/link configuration;
- iOS application entry point, entitlements, permission purpose strings, native picker/share configuration and native
  escape;
- dependency locks, SBOM/provenance, artifact manifests and signing configuration.

No generated or native change is accepted merely because common Kotlin/Compose source is unchanged. The exact graph,
generated output and evidence must be bound to the artifact
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:378–395, 423–440).

### Can a failed candidate dependency be replaced behind a boundary?

In principle, yes, if the capability remains behind an explicit contract and the replacement has a named owner, lifecycle
and threading behavior, accessibility mapping, fallback, EOL/security response, lock/SBOM/provenance and new acceptance
evidence. The shared intent/state contract can survive a camera/file/transfer/native-escape replacement; the replacement
cannot silently change safety meaning or use an unreviewed plugin/module. Without those conditions the capability and
candidate remain HELD
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:344–356, 423–440).

### What must be rebuilt and revalidated?

Any shared KMP/Compose/compiler/runtime or dependency change requires impact review of both hosts, regeneration and
identity check of the iOS framework, Android and iOS builds, dependency/SBOM/provenance verification, relevant common
negative vectors, both host lifecycle/accessibility evidence, signing and staged release evidence. A host-only change
still requires its platform evidence and a common-meaning compatibility review. No OTA path reduces this to a silent
runtime change
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:801–815; 00_CONTROL/DECISION_LOG.md:680–698).

### What can be automated, and what requires devices or humans?

| Evidence class | Simulation treatment |
|---|---|
| Common state/package/compatibility vectors | Can be specified as deterministic fixtures and negative cases; no execution pass is claimed. |
| Compose contract/state mapping | Can be reviewed statically and through a no-code matrix; this does not prove platform accessibility or lifecycle. |
| Android/iOS lifecycle and native surfaces | Requires host-specific evidence and later physical-device execution. |
| VoiceOver/TalkBack, largest text, focus, announcements, reduced motion, switch/voice control and dexterity | Requires actual devices and independent human/qualified AT review. |
| Signing, provenance, generated framework and store artifact | Requires closed build/release graph, independent verification, signer/store authority and staged evidence. |
| Safety meaning, recall/revalidation and physical continuation | Requires qualified safety/content authority and current-state revalidation; photo or UI state cannot substitute. |

The controlled spec explicitly rejects documentary device/build/accessibility claims and requires separate implementer,
reviewer and validator roles
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:69–83).

### How does another AI detect incomplete cross-platform parity?

The next AI receives the packet graph, not a broad repository. It must compare:

- identical state/transition IDs and negative outcomes from Packet 1;
- Compose semantic intent against Android and iOS host mappings;
- Android/iOS lifecycle and native-surface exception inventories;
- generated-framework identity and common-source revision;
- package/dependency lock, SBOM/provenance and artifact graph;
- four-cohort/device and AT evidence fields;
- platform-specific hold/reopen findings and shared release-meaning impact.

Any missing packet, field, platform counterpart, generated identity, native owner, fallback or evidence artifact is a gap
and remains HELD. A common Compose diff is never proof that both hosts are complete.

### Can the task be reverted without lying about data or physical state?

Yes only as a controlled hold/forward-recovery shape:

- restored UI is context, not physical truth;
- uncommitted work is unknown/partial;
- safe-stop/recovery remains available;
- a database/key migration that cannot reverse refuses binary rollback;
- valid new data/history is preserved and forward-migrated;
- current package/release/recall authority is rechecked in the foreground;
- last accepted artifacts are retained and an impact graph identifies affected clients/packages.

This is a policy shape, not evidence that a migration or device interruption has passed
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:299–322, 324–342, 904–911; DEBATE-006__TASK_SIM_MOB_001_SPEC.md:37–42).

### What survives framework replacement?

Portable: product/content/data schemas, history/provenance, correction/withdrawal/recall events, package manifests and
fixtures, Turkish copy/units, accessibility intent, API contracts, exports, acceptance oracles, audit/release
references and migration descriptions.

Bound: shared Compose source and runtime, Kotlin/Native binaries, Compose compiler/runtime, generated iOS framework,
Android/iOS host code, native permission/camera/file/lifecycle/escape adapters, Gradle/Xcode integration, signing and
store artifacts. Replacement requires a new client, explicit coexistence, forward migration, revalidation and new
platform/device/AT/safety/release evidence
(DEBATE-006__DOSSIER_KMP_COMPOSE.md:407–421, 879–911).

## 5. Automatic-failure audit

| Automatic failure condition from common spec | Simulation result |
|---|---|
| Asks owner to code/debug/repair | Not permitted. Every packet assigns AI bounded work and surfaces external technical/human owners; the nontechnical owner is not a repair path. |
| Restores UI as physical proof | Explicitly prevented in Packets 1, 3, 5, 6 and 12. |
| Treats optional photo as verification | Explicitly prevented in Packets 1 and 4. |
| Depends on scheduled background work or push | Explicitly prevented in Packets 5, 6 and 7; foreground reconciliation is correctness. |
| Omits Android or iOS lifecycle/accessibility | Not omitted; Packets 5 and 6 are separate mandatory packets. |
| Plugin/module/generated project bypasses evidence | Not permitted; Packets 4, 6, 10 and 11 require named boundary, owner, provenance and review. |
| Uses OTA code delivery | Excluded in Packet 10 and the KMP + Compose dossier. |
| Downloads unrelated content | Prevented in Packet 7 by the fixed selected-scope package rule. |
| Lacks safe-stop/recovery or forward recovery | Required in Packets 1, 3, 5–7 and 12. |
| Claims documentary device/build/accessibility pass | Explicitly not claimed; Packet 9 is a later evidence plan only. |

The common task specification makes each listed condition an automatic failure, so a future implementation task cannot
clear one by relabeling the packet or hiding it inside shared Compose work
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:69–83).

## 6. Permitted status and conditions

### Candidate simulation status

OPERABLE WITH MATERIAL CONDITIONS / HELD

The no-code task can be decomposed into twelve bounded packets. KMP + Compose provides a plausible shared Kotlin/domain
and shared presentation context while retaining explicit Android and iOS host boundaries. That is sufficient for a
bounded plan, not a product, safety, accessibility, build or release pass.

### Conditions to retain this status

1. Keep common KMP/domain and common Compose packets separate from Android and iOS lifecycle/accessibility packets.
2. Name and review the actual local persistence, checkpoint, key/backup, package-manifest and migration contracts before
   implementation; current dossier leaves these unresolved.
3. Treat Kotlin/Native/generated iOS framework, Compose compiler/runtime, Android artifact mapping and both host toolchains
   as release-graph inputs; regenerate and verify when affected.
4. Require native camera/files/lifecycle/permission/temporary-resource boundaries and an explicit iOS semantic/native
   escape; no unreviewed plugin or generated-file path is a fallback.
5. Preserve selected-scope/offline data efficiency, optional media separation, no over-download, foreground reconciliation,
   no push/background correctness and no OTA.
6. Require independent Android/iOS accessibility, safety, security, build/provenance and release review plus later
   physical-device evidence; none is claimed by this simulation.
7. Require forward recovery and explicit rollback refusal whenever data/key migration cannot safely reverse; retain the
   last accepted artifacts and portable truth.
8. Keep unresolved owners, capacity, external device/store/Mac actions and cost amounts visibly HELD. Do not turn missing
   capacity into an owner repair request or an invented estimate.

This simulation does not select KMP + Compose, authorize code or advance a gate. Two independent critiques and manager
synthesis remain required
(DEBATE-006__TASK_SIM_MOB_001_SPEC.md:84–90; DEBATE-006__DOSSIER_KMP_COMPOSE.md:913–969).
