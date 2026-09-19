# DEBATE-006 — TASK-SIM-MOB-001 Candidate Simulation: React Native + Expo Development Builds

Status: `STRUCTURALLY COMPLETE NO-CODE TASK SIMULATION / UNREVIEWED / HELD`  
Date: 2026-09-18  
Candidate: B — React Native + Expo development builds + explicit native boundary  
Audience: nontechnical owner; this record is intended to support routing and hold/release decisions, not coding or build repair.

This is a bounded task simulation against the controlled [TASK-SIM-MOB-001 common
spec](DEBATE-006__TASK_SIM_MOB_001_SPEC.md) and the [React Native + Expo candidate
dossier](DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md). It describes the minimum context a
fresh AI and the separate human authorities would need to plan one safety-critical change.
It is not a prototype, implementation plan, benchmark, effort or time estimate, score,
device/build/accessibility pass, store submission, recommendation, or ADR. No code is
written here. No score is computed. The only permitted output of this simulation is a
bounded task/context record and its evidence conditions.

It inherits the common frozen quantities unchanged: 12 MB compact package, separate optional media up to 150 MB,
250 MB content cache, 25 MB cellular confirmation, unrelated 2 GB catalog exclusion, and the approved normal/stress
motorcycle, record, photo, note, pending-operation and conflict fixtures.

## 1. Task and fixed truth

### 1.1 User-visible change

The simulated change adds one safety-critical active-maintenance step to a valid selected-
motorcycle/task offline package. The step:

- shows objective, warning, readiness and safe-stop/recovery information in Turkish;
- accepts an optional photo without treating the photo as verification;
- saves only an explicit durable checkpoint;
- survives lock, incoming call, backgrounding and process termination;
- restores the last durable checkpoint as context, never as physical truth;
- marks work that was not committed as `unknown/partial`;
- requires accessible physical-state revalidation before continuation;
- keeps safe-stop/recovery available on every failed or uncertain path; and
- produces Android and iOS test/release evidence without OTA code delivery.

No motorcycle-specific torque, part, fitment, measurement or other safety value is invented.

### 1.2 Fixed starting state and required outcomes

The starting state is taken verbatim from the common spec: the motorcycle/model-year/
variant is resolved; one approved task-package generation is installed and within its
allowed offline window; compact required closure is available; optional heavy media is
absent; local account-light history exists; camera permission is not granted; the network
goes from constrained cellular to offline after the step opens; the OS terminates the
process after a photo is captured but before the next checkpoint commits; after restart
the package remains intact and no new server recall knowledge is available; and a screen
reader is enabled with largest text.

| Event | Required truth for this simulation |
|---|---|
| Step opens | Objective, warning, readiness and safe-stop/recovery are available offline. |
| Camera denied | The step remains usable where the photo is optional; denial is explained accessibly. |
| Photo captured | The photo is pending evidence only, not verification or committed physical truth. |
| Process terminates before checkpoint | Temporary/photo work may require recovery; physical progress is `unknown/partial`. |
| Restart | The last durable checkpoint restores as context; continuation is never automatic. |
| Revalidation | The user confirms current physical observations through accessible controls. |
| Revalidation fails or is uncertain | The application remains held and safe-stop/recovery remains available. |
| Revalidation succeeds | The next allowed transition opens and a new explicit checkpoint may commit. |
| Reconnection | Foreground reconciliation checks package, release and recall eligibility before any authority-sensitive continuation. |

### 1.3 Candidate snapshot used by the simulation

The simulation does not refresh or silently change the dossier snapshot. The exact
candidate context is the dossier’s recorded registry/tool snapshot: Expo SDK 57.0.22,
React Native 0.86.3, React 19.2.3, `@expo/cli` 57.0.25, `expo-dev-client` 57.0.19,
`expo-modules-core` 57.0.18, Node 22.13.x, Android compile/target SDK 36, and Xcode
26.4+ / iOS 16.4+ framework floor as recorded there. Capability package versions,
lockfile/transitive hashes, generated native output, signing provenance and installed
tool patch levels remain unresolved. This is a package snapshot, not a build claim.

Official primary anchors used by the dossier and this simulation are [Expo development
builds](https://docs.expo.dev/develop/development-builds/introduction/), [development
build FAQ](https://docs.expo.dev/develop/development-builds/faq/), [customizing native
projects and prebuild](https://docs.expo.dev/workflow/customizing/), [React Native
platform-specific code](https://reactnative.dev/docs/platform-specific-code), [React
Native accessibility](https://reactnative.dev/docs/accessibility), and [React Native
Turbo Native Modules](https://reactnative.dev/docs/turbo-native-modules-introduction).
Package-specific primary links remain in the candidate dossier’s Sections 1 and 4.

## 2. Non-negotiable candidate boundary controls

These controls apply to every packet. A packet cannot declare itself complete by relying
on another packet to hide a platform, authority, reviewer or generated-file obligation.

| Control | Simulation rule |
|---|---|
| Expo Go | Excluded from production evidence. Its fixed native library set cannot validate this task’s explicit native boundary. |
| Expo development build | The task’s runtime context is an Expo development build containing the resolved native library/configuration set. A JavaScript reload is not a native-build proof. |
| Config plugins | Every config plugin that changes permissions, entitlements, manifests, build properties, native modules or resources must be named, versioned, reviewed and included in the dependency/provenance record. An unnamed future plugin is `HELD`. |
| Prebuild and generated native projects | Android and iOS projects produced by prebuild are derived release inputs. Their generation inputs, diff and tool version must be recorded. A direct edit to generated output may be overwritten by prebuild and cannot silently bypass the config-plugin/native review boundary. |
| Native modules | An Expo Modules API module or typed React Native Turbo Native Module is allowed only with a named Swift/Kotlin implementation boundary, spec/code-generation inputs, thread/lifecycle/permission/accessibility contract, fallback, owner and security/EOL record. No hidden native module is assumed. |
| Development-build rebuild trigger | Any native module, config plugin, permission, entitlement, SDK/build-property, Expo package with native code, generated-project input or native dependency change requires a fresh development build and affected-platform revalidation. JavaScript-only changes may use an existing development build for the bounded inner loop, but final evidence still needs a release/test artifact. |
| Build route | Local Android/Apple builds and a hosted build route are both documented possibilities. Neither route is selected here. EAS account, host, quota, billing, artifact export, signing custody and exit are `UNRESOLVED`; a nontechnical owner is not asked to choose by inference. |
| OTA/code delivery | Explicitly excluded. `expo-updates` is not part of this simulation and no remote JavaScript/native code may bypass store review, binary provenance or safety correction. |
| Background and push | OS-scheduled background work and push may optimize refresh, but neither is a correctness prerequisite for checkpoint, safe-stop, revalidation or recovery. |
| Optional photo | A captured photo is pending evidence only. It never verifies a physical state, closes a safety step, creates entitlement or supplies official content truth. |
| Device/build claims | Documentary planning is not a real-device, screen-reader, build, signing, store or accessibility pass. Any missing execution is `UNRESOLVED`/`HELD`. |
| Owner role | The nontechnical owner may route the bounded work, provide or appoint authorities, and hold/release on evidence. The owner is never instructed to code, debug, repair a build, review safety truth alone or substitute for a device/AT/store authority. |

## 3. Minimum fresh-AI context model

The task is intentionally split into twelve bounded packets. Shared contracts and fixtures
may be reused, but Android and iOS lifecycle/accessibility/build obligations remain
separate. The packets are an inventory of context types, not a score or a claim that a
packet count predicts cost.

The common links used below are Obsidian-compatible wiki links. They point to requirements,
screens/state, contracts, delivery tasks and tests without claiming that those artifacts
already exist for this simulated task:

- Requirements: [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]], [[02_DISCOVERY/SYNTHESIS/BUSINESS_RULES]], [[03_DESIGN/SCREEN_COVERAGE_TRACEABILITY]]
- Screens/state: [[03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES]], [[03_DESIGN/SCREEN_CATALOG]], [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E01-SCR-014-Active-Guide-Step.png]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E03-SCR-016-Resume-Revalidation-v2-L05A.png]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E05-SCR-018-Completion-Safe-Closure-Record-v2-L05A.png]]
- Contracts: [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]], [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]], [[07_AI_ARCHITECTURE/MIGRATION_POLICY]], [[07_AI_ARCHITECTURE/ROLLBACK_STRATEGY]]
- Tasks: [[06_DELIVERY_PLANNING/TASK_INDEX]], [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]], [[06_DELIVERY_PLANNING/TASKS/README]]
- Tests/evidence: [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]], [[08_REPOSITORY_BOOTSTRAP/QUALITY_GATES]]

## 4. Required no-code work packets

### Packet 01 — Shared product/state contract

- Purpose and user outcome: Define the single state vocabulary and allowed transitions for the new active-maintenance step: offline open, readiness, optional-photo-pending, explicit checkpoint, `unknown/partial`, accessible revalidation, safe-stop/recovery, and reconnect eligibility. The user must never be told that restored UI or a photo proves current physical state.
- Minimum input documents/contracts: TASK-SIM-MOB-001 Sections 1–4; the RN/Expo dossier Sections 2–4 and 5–7; approved Phase-3 state/design truth; the offline safety/recall compatibility, authorization, and release-governance controls; portable/public contract and migration rules.
- Allowed files/modules to change: Only the task’s shared domain/state contract, state-transition fixture, validation vocabulary and traceability record, if implementation is later authorized. No file change is authorized by this simulation.
- Forbidden scope: No React screen, native module, camera permission, provider/backend schema, new safety value, entitlement rule, content publication rule, OTA path, or unrelated catalog/media behavior.
- Upstream/downstream dependencies: Upstream is the approved product/safety/state truth. Downstream packets are 02 presentation, 03 persistence, 07 reconciliation, 08 automated tests, 09 human acceptance and 12 forward recovery. Packet 01 is the semantic source for both platforms.
- Candidate-specific dependency, generated file or native boundary: TypeScript/JavaScript contract and serialization boundary only; no native dependency is needed for the semantic record. If a native module is later needed for serialization, it is routed through the explicit module rule and triggers a development-build rebuild.
- Android/iOS divergence: State names, transition guards and user-visible truth must be identical. Android process/activity and iOS scene/app interruptions are separate adapters in Packets 05–06; platform lifecycle events may differ, but they cannot create different safety meanings.
- Acceptance and negative cases: Accept only if the fixed starting state opens offline; objective/warning/readiness/safe-stop are present; optional photo remains pending; only explicit checkpoint commits; pre-commit termination becomes `unknown/partial`; restart restores context without auto-continue; accessible revalidation gates the next transition; reconnect rechecks current eligibility. Reject/hold if a cached UI is authority, a photo verifies state, a background task is required, a 2 GB catalog downloads, an unknown transition is silently accepted, or a torque/fitment fact is invented.
- Evidence artifact: Versioned state-transition table, authoritative-state map, fixture inputs/outputs, negative-case catalogue and requirement-to-state traceability. This simulation creates no executed result.
- Implementer/reviewer/validator separation: A bounded AI or implementer may draft the contract; an independent product/safety reviewer must review semantics; a separate validator checks transition fixtures and traceability. No single person or model may approve official safety truth.
- External human/store/device action: Product/safety authority must approve the state vocabulary and Turkish safety meaning. No store or device action is sufficient to close this packet.
- Failure and recovery: Ambiguous, stale, recalled, migrated or unknown state enters visible hold with safe-stop/recovery. Recovery is a forward, data-preserving transition after current eligibility and physical revalidation; no silent reset or binary-only rollback.
- Unresolved cost/capacity trigger: Named product/safety owner, contract reviewer, translation/content review and conflict/migration capacity are unresolved. No numeric price is entered.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#2. User-Visible Change]], [[02_DISCOVERY/SYNTHESIS/BUSINESS_RULES]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES]]; contracts [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]], [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]]; tasks [[06_DELIVERY_PLANNING/TASK_INDEX]], [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]]; tests [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]].

### Packet 02 — Shared UI/presentation and Turkish safety semantics

- Purpose and user outcome: Map the Packet 01 states to the active-step, warning, readiness, optional-photo, revalidation and safe-closure surfaces in Turkish. The user can understand what is known, what is pending, what is unsafe to continue, and what must be physically revalidated.
- Minimum input documents/contracts: Packet 01 contract; Phase-3 active-application/recovery screens and state matrix; Turkish copy and design tokens; screen coverage traceability; RN accessibility and platform-specific-code evidence; product safety and accessibility review directions.
- Allowed files/modules to change: Only the bounded React Native presentation/screen surface, semantic labels/roles/state mapping, Turkish copy references and platform-specific presentation exception records, if authorized. No generated Android/iOS project edits are allowed in this packet.
- Forbidden scope: No domain transition logic hidden in a component, visual state treated as truth, photo treated as verification, inaccessible custom control, new navigation authority, OTA update, unrelated catalog download, or platform-specific safety copy that changes the shared meaning.
- Upstream/downstream dependencies: Packet 01 supplies state truth. Packets 03–07 supply persistence, media, lifecycle and reconciliation status. Packets 08–09 validate automated semantics and human AT/physical behavior; Packet 10 packages the resulting native/runtime evidence.
- Candidate-specific dependency, generated file or native boundary: React Native 0.86.3, React 19.2.3 and Expo SDK 57.0.22 are the recorded UI snapshot. `.android`/`.ios` presentation exceptions are explicit boundaries. A config plugin or native module is not assumed for ordinary presentation; if introduced, it follows the global naming/review/rebuild control.
- Android/iOS divergence: TalkBack focus/reading order, Android roles/state announcements, largest-text layout and back/lifecycle behavior need Android-specific review. VoiceOver focus/announcement timing, Dynamic Type/reflow and scene transitions need iOS-specific review. Shared state semantics and safe-stop wording must not diverge.
- Acceptance and negative cases: Accept only if objective, warning, readiness, pending-photo, `unknown/partial`, revalidation, safe-stop and recovery states remain legible at largest text, non-color-coded and screen-reader perceivable. Hold if focus skips the warning/hold, state is conveyed only by color, a stale package is announced as current, a screen reader cannot reach safe-stop, or the UI auto-continues after restart.
- Evidence artifact: Screen/state traceability, semantic inventory, Turkish copy review record, platform-exception list, and accessibility test oracle. Static or documentary evidence here is not a device/VoiceOver/TalkBack pass.
- Implementer/reviewer/validator separation: Implementer/AI may prepare the bounded mapping; an independent design/product reviewer checks parity and safety language; a qualified accessibility validator checks semantic and interaction oracles separately.
- External human/store/device action: Turkish content/safety reviewer and Android/iOS TalkBack/VoiceOver testers are required later. A nontechnical owner may arrange them, not replace them.
- Failure and recovery: Any inaccessible warning, stop or recovery state holds the task and keeps a plain safe-stop/read-only route. Return to the last durable context; never instruct physical continuation through an unverified presentation.
- Unresolved cost/capacity trigger: Final copy, semantic labels, screen-reader testers, large-text device access, and platform-specific UI ownership are unresolved; no external-lab or tooling amount is invented.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#2. User-Visible Change]], [[03_DESIGN/SCREEN_COVERAGE_TRACEABILITY]]; screens [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E01-SCR-014-Active-Guide-Step.png]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E03-SCR-016-Resume-Revalidation-v2-L05A.png]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E05-SCR-018-Completion-Safe-Closure-Record-v2-L05A.png]]; contracts [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]], [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]]; tasks [[06_DELIVERY_PLANNING/TASK_INDEX]], [[06_DELIVERY_PLANNING/TASKS/README]]; tests [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]].

### Packet 03 — Local persistence, durable checkpoint and migration

- Purpose and user outcome: Persist only explicit checkpoints; restore the last durable checkpoint as context after process termination; preserve `unknown/partial` when the photo or physical transition was not committed; and migrate local data without losing history or pretending that a binary rollback reverses data.
- Minimum input documents/contracts: Packets 01–02; task fixed starting state and outcomes; RN dossier local persistence/security boundary and `expo-sqlite`/`expo-secure-store` evidence; public contracts; migration policy; rollback strategy; privacy and backup controls.
- Allowed files/modules to change: A bounded local schema/checkpoint repository, migration journal, serializer and recovery-state adapter, plus their fixtures, if authorized. Native storage configuration may change only through the explicit config-plugin/native boundary and is not edited directly in generated output.
- Forbidden scope: No UI state as source of truth, no assumption that Expo SQLite encrypts data, no local authority for entitlement/recall/physical truth, no silent reset/overwrite, no destructive database drop, no blind backup restore, and no irreversible migration without forward recovery.
- Upstream/downstream dependencies: Packet 01 defines state; Packet 02 renders it. Packet 04 contributes photo/temp-file status. Packets 05–07 supply interruption/reconciliation events; Packet 08 tests transactions; Packet 10 rebuilds if storage/native inputs change; Packet 12 owns migration/rollback refusal.
- Candidate-specific dependency, generated file or native boundary: `expo-sqlite` 57.0.3 is the recorded database direction and `expo-secure-store` 57.0.4 is only for small protected references. Database encryption, key hierarchy, backup exclusion and native module need are unresolved. Any native storage/config-plugin change requires a new development build for affected platforms.
- Android/iOS divergence: Android backup, process death, Keystore availability and filesystem behavior require Android-specific policy. iOS Keychain/Data Protection, protected-data availability, restore/uninstall behavior and scene termination require iOS-specific policy. The checkpoint schema and authority quarantine rules remain shared.
- Acceptance and negative cases: Accept explicit checkpoint commit, restart restoration, interrupted transaction recovery, duplicate-operation idempotency, preserved history/provenance, and visible key-loss/restore hold. Hold/reject if a pre-commit photo becomes committed, process termination silently advances physical progress, restore grants entitlement, backup/clone creates authority, a schema migration discards history, or a binary downgrade is described as data rollback.
- Evidence artifact: Versioned schema/migration manifest, checkpoint journal, data-class/backup map, transaction/recovery fixture and forward-recovery record. No migration or restart execution is claimed in this simulation.
- Implementer/reviewer/validator separation: Implementer prepares the bounded storage change; an independent data/security reviewer checks encryption, backup, migration and authority quarantine; a separate validator runs fixture and recovery checks. The AI cannot approve key policy.
- External human/store/device action: Data-security/privacy owner, backend/account owner and platform storage reviewers must approve the policy. Device execution is later required for process/lock/restore behavior; no pass is claimed.
- Failure and recovery: If commit status is ambiguous, mark `unknown/partial`, keep safe-stop and reopen only after revalidation. If migration is irreversible or key material is unavailable, refuse binary rollback, quarantine affected authority metadata and use tested forward recovery/re-authentication.
- Unresolved cost/capacity trigger: Exact lockfile/transitive graph, encryption implementation, key/backup policy, migration owner, restore test devices, and specialist review are unresolved. No storage or security price is entered.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#3. Fixed Starting State]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_REACT_NATIVE_EXPO#3.3 Local persistence, encryption, keys, migration and backup]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E03-SCR-016-Resume-Revalidation-v2-L05A.png]]; contracts [[07_AI_ARCHITECTURE/MIGRATION_POLICY]], [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]]; tasks [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]], [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]].

### Packet 04 — Camera, photo, temporary file and privacy

- Purpose and user outcome: Allow an optional photo when permission is denied or media is unavailable; retain a captured photo as pending evidence only; prevent temporary-file loss or accidental disclosure; and keep physical-state verification and safe-stop independent of the photo.
- Minimum input documents/contracts: Packets 01–03; task camera starting state and required outcomes; RN/Expo camera, image-picker, document-picker, file-system and sharing boundaries; privacy/data-classification rules; media retention/deletion and export controls.
- Allowed files/modules to change: Camera/photo adapter, permission-state presentation, temporary-file ownership/cleanup record, evidence classification and upload-intent adapter, if later authorized. Permission manifests, entitlements and config-plugin inputs may be declared only as named native configuration; generated native output is derived and not hand-edited here.
- Forbidden scope: No photo verification, automatic physical-state transition, metadata-as-truth, background camera, broad media permission, silent upload, unrelated catalog/media download, irreversible export, or native module added without the module contract.
- Upstream/downstream dependencies: Packet 01 controls evidence/state meaning; Packet 02 renders permission and pending states; Packet 03 persists checkpoint/temp status. Packets 05–07 handle lifecycle and package/reconciliation; Packets 08–09 test negative cases and humans; Packet 10 rebuilds native permission/config changes.
- Candidate-specific dependency, generated file or native boundary: Recorded candidates are `expo-camera` 57.0.5, `expo-image-picker` 57.0.18, `expo-document-picker` 57.0.2 and `expo-file-system` 57.0.7. Their permission/config-plugin/native behavior must be locked and reviewed. A custom Expo Modules/Turbo Native Module is a last-resort explicit boundary. Any package/config/permission/native change triggers a development-build rebuild.
- Android/iOS divergence: Android camera/runtime permission, URI grants, picker/provider and cache behavior require Android review. iOS AV/camera permission, limited photo-library behavior, sandbox/security-scoped URLs and capture-session interruption require iOS review. The pending-evidence and no-verification rule is identical.
- Acceptance and negative cases: Accept camera denial with accessible optional/no-media route; capture as pending evidence; process termination before checkpoint as `unknown/partial`; malformed/low-storage/permission-change handling; temp cleanup; idempotent retry; and no authority from media. Hold if denial blocks an optional step, a photo closes readiness, capture is trusted without classification, a temp file is displayed as committed, or private media crosses a disclosure boundary silently.
- Evidence artifact: Permission/config matrix, temporary-file state diagram, evidence-classification contract, package/lock/SBOM/config-plugin diff and manual acceptance script. Documentary artifacts are not a camera or privacy pass.
- Implementer/reviewer/validator separation: Implementer prepares the adapter; privacy/media and safety reviewers independently inspect classification and physical-truth boundaries; validator checks denial, interruption and cleanup oracles. Native camera expertise is separate from product approval.
- External human/store/device action: Camera-capable Android/iOS devices, privacy reviewer and later human acceptance are required. Store permission declarations and legal privacy copy require owner authority; no device result is claimed.
- Failure and recovery: Denial or unavailable camera exposes safe manual/no-media continuation when allowed. Capture/process loss remains pending or `unknown/partial`; malformed/low-storage media is quarantined or held; a failed upload retries idempotently without converting the local file into official evidence.
- Unresolved cost/capacity trigger: Real camera devices, AT testers, storage/egress policy, native permission owner, privacy/legal review and any custom module capacity are unresolved. No provider or storage price is invented.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#2. User-Visible Change]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#4. Required State Outcomes]]; screens [[03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E01-SCR-014-Active-Guide-Step.png]]; contracts [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]], [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]]; tasks [[06_DELIVERY_PLANNING/TASK_INDEX]], [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]]; tests [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]].

### Packet 05 — Android lifecycle and accessibility

- Purpose and user outcome: Keep the step safe across Android lock, incoming call, backgrounding, process kill and restart, while TalkBack, largest text, focus order, state announcements and non-color status expose the same truth.
- Minimum input documents/contracts: Packets 01–04; fixed interruption fixture; RN AppState/platform-specific/accessibility evidence; Android lifecycle and process limits; Phase-3 accessibility intent; acceptance matrix and negative-state oracle.
- Allowed files/modules to change: Android-specific React Native presentation/lifecycle adapter, accessibility semantics and test fixtures; Android manifest/config-plugin inputs only when explicitly named. Generated Android project output may be regenerated and reviewed but not silently edited.
- Forbidden scope: No scheduled task or push dependency for correctness, no automatic resume, no visual-only accessibility claim, no Android-specific semantic change to shared safety truth, no Expo Go proof and no OTA.
- Upstream/downstream dependencies: Packets 01–04 supply state/UI/persistence/media. Packet 07 supplies reconciliation status; Packet 08 supplies automated lifecycle contracts; Packet 09 supplies TalkBack/device evidence; Packet 10 supplies development/release build provenance; Packet 12 supplies forward recovery.
- Candidate-specific dependency, generated file or native boundary: React Native `AppState` and Android platform-specific files are the default boundary. Headless JS/background task may be an optimization only. Any native module, permission or config-plugin change requires a fresh Android development build and affected-platform revalidation.
- Android/iOS divergence: Android activity/process recreation, vendor battery policy, URI/camera interruption, TalkBack focus and Android 13 permission behavior are Android obligations. iOS scene/suspension/VoiceOver obligations are Packet 06. The durable checkpoint and safe-stop contract stays shared.
- Acceptance and negative cases: Accept step open offline, lock/call/background, process termination after photo/pre-checkpoint, restart to last durable context, no auto-continue, accessible revalidation, safe-stop and visible `unknown/partial`. Hold if Activity/UI memory is treated as durable, Android scheduler/push is required, TalkBack skips the hold or warning, largest text clips a safety instruction, or a simulator/API result is called a device pass.
- Evidence artifact: Android lifecycle event matrix, TalkBack semantics/focus oracle, interruption test plan, native/config diff and structured evidence record. No Android device or accessibility execution is claimed here.
- Implementer/reviewer/validator separation: Implementer/AI handles bounded Android presentation/adapter work; independent Android-native reviewer checks lifecycle and configuration; qualified TalkBack validator and safety reviewer separately validate user outcomes.
- External human/store/device action: Android 10/API 29 constrained and Android 13+ main devices, TalkBack user/tester, camera/phone-call/lock/process controls and Android release authority are required later. No pass is asserted.
- Failure and recovery: On any lifecycle ambiguity, restore durable checkpoint as context, mark physical progress `unknown/partial`, keep safe-stop, and require foreground revalidation. A failed accessibility path holds release rather than bypassing the control.
- Unresolved cost/capacity trigger: Branded device/patch matrix, Android native maintainer, TalkBack tester, build host, signing custody and interruption lab capacity are unresolved. No device/lab amount is entered.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#3. Fixed Starting State]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#4. Required State Outcomes]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E03-SCR-016-Resume-Revalidation-v2-L05A.png]]; contracts [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]]; tasks [[06_DELIVERY_PLANNING/TASK_INDEX]], [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]]; tests [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]], [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]].

### Packet 06 — iOS lifecycle and accessibility

- Purpose and user outcome: Keep the step safe across iOS lock, call/interruption, backgrounding, scene disconnection, suspension, termination and restart, while VoiceOver, Dynamic Type/largest text, focus order, announcements and non-color status expose the same truth.
- Minimum input documents/contracts: Packets 01–04; fixed interruption fixture; RN AppState/platform-specific/accessibility evidence; Apple lifecycle/background and accessibility directions; Phase-3 active/recovery screens; acceptance matrix and negative-state oracle.
- Allowed files/modules to change: iOS-specific React Native presentation/lifecycle adapter, accessibility semantics and test fixtures; iOS permission/entitlement/config-plugin inputs only when named. Generated iOS project output may be regenerated and reviewed, not silently hand-edited.
- Forbidden scope: No background task, push, scene callback or notification dependency for correctness; no automatic resume; no visual-only VoiceOver claim; no semantic divergence from Android; no Expo Go, OTA or unreviewed native module.
- Upstream/downstream dependencies: Packets 01–04 supply state/UI/persistence/media. Packet 07 supplies reconciliation; Packet 08 supplies contract tests; Packet 09 supplies VoiceOver/device evidence; Packet 10 supplies development/release build provenance; Packet 12 supplies forward recovery.
- Candidate-specific dependency, generated file or native boundary: React Native `AppState` and explicit `.ios` files are the default boundary. A Swift Expo module or Turbo Native Module is allowed only under the global native contract. Any native/config/permission/entitlement change requires a fresh iOS development build and affected-platform revalidation.
- Android/iOS divergence: iOS scene lifecycle, protected-data availability, camera interruption, VoiceOver focus/announcement and Dynamic Type behavior are iOS obligations. Android activity/process/TalkBack behavior is Packet 05. Neither platform may infer physical truth from its restored view hierarchy.
- Acceptance and negative cases: Accept the same offline open, optional-camera denial, pre-checkpoint process termination, restart-as-context, no auto-continue, accessible physical revalidation, safe-stop and foreground eligibility check. Hold if a scene callback silently commits, VoiceOver misses warning/recovery, Dynamic Type truncates a safety meaning, background scheduling is required, or simulator output is called a device pass.
- Evidence artifact: iOS scene/lifecycle matrix, VoiceOver/Dynamic Type semantics oracle, interruption test plan, native/config diff and structured evidence record. No iOS device or accessibility execution is claimed.
- Implementer/reviewer/validator separation: Implementer/AI handles bounded iOS presentation/adapter work; independent iOS-native reviewer checks lifecycle/configuration; qualified VoiceOver validator and safety reviewer separately validate user outcomes.
- External human/store/device action: An iOS 16.4-capable oldest cohort, current standard iPhone cohort, VoiceOver tester, camera/call/lock/termination controls, Mac/Xcode path and Apple release authority are required later. No pass is asserted.
- Failure and recovery: On interruption or scene ambiguity, restore the last durable context, mark `unknown/partial`, expose safe-stop and require foreground revalidation. Any accessibility or lifecycle uncertainty holds the release.
- Unresolved cost/capacity trigger: Exact iPhone models/patches, Mac/Xcode access, Apple signing/store account, VoiceOver tester, native maintainer and interruption-lab capacity are unresolved. No Mac, CI or device price is invented.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#3. Fixed Starting State]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#4. Required State Outcomes]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E03-SCR-016-Resume-Revalidation-v2-L05A.png]]; contracts [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]]; tasks [[06_DELIVERY_PLANNING/TASK_INDEX]], [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]]; tests [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]], [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]].

### Packet 07 — Offline package and reconciliation compatibility

- Purpose and user outcome: Open only the selected approved package offline; keep required compact closure available; do not download the unrelated catalog or optional heavy media by default; and, on foreground reconnection, re-check package/version/release/recall eligibility before authority-sensitive continuation.
- Minimum input documents/contracts: Packets 01–06; common fixture workload/device/network/interruption rules; task package/recovery specification; RN/Expo FileSystem/background-task/task-manager evidence; DEBATE-002 offline safety/recall compatibility; Internal Operations/content/API contracts.
- Allowed files/modules to change: Package manifest/checkpoint/integrity adapter, bounded cache policy, compatibility/reconciliation state and fixtures, if authorized. No backend/provider schema, content authority, store configuration or OTA service is changed.
- Forbidden scope: No 2 GB unrelated catalog download, no required-content eviction, no cache as recall/entitlement authority, no scheduled work or push as correctness, no silent partial/corrupt package, no optional-media auto-download and no OTA code.
- Upstream/downstream dependencies: Packet 01 state and Packet 03 persistence define commit/recovery. Packet 04 separates user media. Packets 05–06 handle interruption; Packet 08 tests compatibility; Packet 09 observes network/device behavior; Packet 10 packages provenance; Packet 12 handles old/new clients and recovery.
- Candidate-specific dependency, generated file or native boundary: `expo-file-system` 57.0.7 is the local-transfer primitive; `expo-background-task` 57.0.18 and `expo-task-manager` 57.0.18 may optimize deferrable refresh only. Manifest, hash/signature, atomic old/new commit, recall and eviction semantics are app-owned. Background capability/config-plugin/native changes require a new development build.
- Android/iOS divergence: Android content URIs, storage pressure, WorkManager/vendor policies and process limits differ from iOS sandbox, URLSession/background scheduling, protected files and scene termination. The package manifest, integrity, compatibility and safe-hold semantics are shared.
- Acceptance and negative cases: Accept valid offline package open, required content within scope, no unrelated catalog download, explicit optional-media choice, constrained-network interruption, partial/corrupt detection, and foreground revalidation after reconnect. Hold if a stale/recalled package appears current, background work is required, a transfer is shown complete before integrity/atomic commit, or a cache creates entitlement/authority.
- Evidence artifact: Framework-independent package manifest fixture, compatibility/capability matrix, transfer/checkpoint state table, storage/size policy, recall/reconnect oracle and provenance record. No network or device pass is claimed.
- Implementer/reviewer/validator separation: Implementer/AI prepares adapters and fixture changes; content/safety and backend/security reviewers independently inspect authority and integrity; validator checks negative/recovery behavior separately.
- External human/store/device action: Internal Operations/content authority, backend/sync/security owner, constrained-network test capacity and both platform device cohorts are required later. Store action is not a substitute for recall/compatibility evidence.
- Failure and recovery: Keep the last verified package when transfer/integrity/recall is uncertain; mark pending work incomplete; expose safe-stop/read-only hold; reconcile in foreground with idempotent operations. Never silently discard or overwrite a package or claim rollback after an irreversible migration.
- Unresolved cost/capacity trigger: Backend contract, storage/egress/retention, network lab, package-signing owner, device coverage and background-policy expertise are unresolved. Arithmetic workload is not converted to a price.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#3. Fixed Starting State]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#4. Required State Outcomes]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES]]; contracts [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]], [[07_AI_ARCHITECTURE/MIGRATION_POLICY]]; tasks [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]].

### Packet 08 — Automated contract, state and negative tests

- Purpose and user outcome: Provide deterministic, repeatable checks for the shared state contract and negative transitions without pretending that automation proves physical state, human accessibility, store acceptance or real-device lifecycle behavior.
- Minimum input documents/contracts: Packets 01–07; TASK-SIM-MOB-001 required outcomes; state/acceptance matrices; public contracts; architecture tests; validation strategy; dependency rules; migration/rollback rules; RN/Expo snapshot and native-boundary controls.
- Allowed files/modules to change: Test fixtures, state/property/contract oracles, negative-case records, test configuration and evidence schemas, if implementation is later authorized. Production code, generated native projects and signing configuration are outside this packet.
- Forbidden scope: No mock, emulator, JavaScript reload or unit result may be called a device/AT/build/store pass; no test bypasses native rebuild, config-plugin review, safety review or human acceptance; no test invents motorcycle values or relies on push/background timing.
- Upstream/downstream dependencies: Packet 01 is the contract source; Packets 02–07 provide presentation, persistence, media, lifecycle and package states. Packet 09 covers physical/human oracles; Packet 10 covers artifact/release evidence; Packet 11 independently reviews test completeness; Packet 12 validates recovery fixtures.
- Candidate-specific dependency, generated file or native boundary: The exact JS/RN test runner and testing-library versions are not selected in the dossier. Native module/config-plugin/prebuild changes require integration tests against a new development build; pure contract fixtures must remain runnable without Expo Go assumptions.
- Android/iOS divergence: Contract/state tests are shared where possible. Android lifecycle/permission/accessibility integration tests and iOS scene/permission/accessibility integration tests remain separate suites with separate evidence; a shared test result cannot close either platform’s divergence.
- Acceptance and negative cases: Required cases include offline step open, camera denial, pending photo, pre-checkpoint termination, restart-as-context, no auto-continue, successful/failed/uncertain revalidation, safe-stop, reconnect/recall check, corrupt/partial package, duplicate operation, migration/rollback refusal, unknown fields, no default catalog download and no background/push correctness dependency. A missing or flaky oracle is `HELD`, not skipped.
- Evidence artifact: Test inventory and traceability, deterministic fixture vectors, machine-readable result schema, negative-case logs, dependency/configuration manifest and reproducibility instructions. No test has been executed or passed by this simulation.
- Implementer/reviewer/validator separation: A test implementer may author fixtures; an independent contract/safety reviewer checks expected truth; a separate validator verifies deterministic execution and evidence integrity. Native and AT reviewers remain outside automated-test approval.
- External human/store/device action: CI or a controlled local runner is needed for execution; real devices, screen readers and store accounts are not replaced by this packet and remain Packet 09/10 obligations.
- Failure and recovery: A failed, nondeterministic or environment-dependent test holds the affected task/release. Restore the last known fixture, isolate the change, update the contract/fixture through review and rerun; never delete a failing test to obtain green evidence.
- Unresolved cost/capacity trigger: Test-runner selection, CI/local/hosted path, artifact retention, native integration capacity and independent validator availability are unresolved. No CI or tooling price is invented.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#5. Required No-Code Work Packets]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#8. Automatic Failure Conditions]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/SCREEN_COVERAGE_TRACEABILITY]]; contracts [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]], [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]]; tasks [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[08_REPOSITORY_BOOTSTRAP/QUALITY_GATES]].

### Packet 09 — Real-device and human acceptance

- Purpose and user outcome: Verify on actual Android and iOS devices, with TalkBack/VoiceOver and largest text, that the user can understand the Turkish warning/readiness/hold, handle camera denial/optional capture, observe `unknown/partial`, physically revalidate, stop safely and recover after interruption.
- Minimum input documents/contracts: Packets 01–08; fixed device/network/interruption cohorts; Phase-3 screens and accessibility intent; acceptance matrix; device/AT evidence protocol; privacy/safety review conditions; no invented motorcycle-specific safety values.
- Allowed files/modules to change: Human acceptance script, device matrix, evidence forms, defect/hold records and traceability only, if authorized. This packet does not authorize production-code edits, generated native edits or build repair by the owner.
- Forbidden scope: No emulator/simulator/API availability as device proof; no AI, owner or developer substitute for physical observation; no photo as verification; no automatic continuation; no store publication; no OTA; no aggregate score or “mostly passed” claim.
- Upstream/downstream dependencies: Packets 01–07 define expected truth and platform behavior; Packet 08 supplies automated baseline; Packet 10 supplies an identifiable development/release artifact; Packet 11 independently reviews evidence; Packet 12 supplies recovery/rollback handling.
- Candidate-specific dependency, generated file or native boundary: Acceptance must install the resolved Expo development/test build containing the same config-plugin/prebuild/native-module set intended for evidence. Any native/config/package change invalidates the artifact and requires a fresh affected-platform development build before revalidation. Local/hosted route remains undecided.
- Android/iOS divergence: Android 10/API 29 constrained and Android 13+ main cohorts use TalkBack, Android lifecycle and permission controls. iOS 16.4-capable oldest and current standard cohorts use VoiceOver, Dynamic Type and scene/camera controls. Evidence is recorded per platform; one platform cannot stand in for the other.
- Acceptance and negative cases: Exercise offline open, constrained cellular to offline, lock, call/interruption, background, process kill after photo before checkpoint, restart, denial, pending photo, revalidation success/failure/uncertainty, safe-stop, reconnect/eligibility and stale/recall hold. Any inaccessible warning/stop/recovery, auto-continue, displayed partial success, physical-state inference, or unverified build is a hold.
- Evidence artifact: Device/OS/build identity, screen-reader interaction record, largest-text/reflow record, interruption/restart record, camera/privacy record, observed expected/negative outcomes, defects and reviewer sign-off. This simulation produces no device record and claims no pass.
- Implementer/reviewer/validator separation: A human facilitator or tester performs the interaction; an independent safety/accessibility reviewer evaluates the observation; a separate validator checks completeness, artifact identity and reproducibility. The implementer cannot self-accept.
- External human/store/device action: Real Android/iOS devices, TalkBack/VoiceOver users or qualified testers, phone/camera/lock/process controls, and safety/accessibility authority are mandatory. Store accounts are needed only when a distribution channel is selected; neither is available by assumption.
- Failure and recovery: Stop the physical task, preserve the last safe durable package/checkpoint, record `unknown/partial`, and route to safe-stop/revalidation. A failure blocks the affected release/build and returns to the responsible packet; it is never “worked around” by asking the owner to debug.
- Unresolved cost/capacity trigger: Device procurement/borrowing, AT tester availability, Mac/Xcode access, Android signing/build access, test-facilitator capacity and evidence storage are unresolved. No lab or device amount is entered.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#3. Fixed Starting State]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#4. Required State Outcomes]]; screens [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E01-SCR-014-Active-Guide-Step.png]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E03-SCR-016-Resume-Revalidation-v2-L05A.png]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E05-SCR-018-Completion-Safe-Closure-Record-v2-L05A.png]]; contracts [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]]; tasks [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[08_REPOSITORY_BOOTSTRAP/EVIDENCE/README]].

### Packet 10 — Build, signing, provenance and release evidence

- Purpose and user outcome: Produce separately identifiable Android and iOS test/release artifacts whose native inputs, package graph, generated output, signing custody, evidence and release authority can be inspected; deliver the change through store-governed binaries, never OTA code.
- Minimum input documents/contracts: RN/Expo dossier Sections 1, 3.7, 3.9 and 4; Packets 01–09; DEBATE-005 release/supply-chain governance; dependency rules; quality gates; store/build-floor controls; lockfile/SBOM/provenance requirements.
- Allowed files/modules to change: Reviewed package manifests/lockfiles, app configuration, config-plugin inputs, build properties, generated Android/iOS project outputs, build recipes, signing references (never raw private keys), SBOM/provenance manifests and release-evidence records, if authorized. The simulation itself changes none of them.
- Forbidden scope: No direct generated-project edit that bypasses its source/config plugin, no unnamed native dependency, no Expo Go evidence, no unreviewed hosted build, no OTA, no store submission, no owner-directed build repair and no claim that a successful local build is a release pass.
- Upstream/downstream dependencies: All implementation/evidence packets feed this packet. Packet 11 independently verifies provenance and parity; Packet 12 verifies migration/recovery release behavior. Store/legal/signing and host/device authorities remain external.
- Candidate-specific dependency, generated file or native boundary: Expo prebuild/config plugins, `expo-dev-client`, native modules and native-capable Expo packages define the explicit boundary. Any change to them, permissions, entitlements, SDK/build properties or generated project requires fresh development builds for affected platforms and revalidation; a final store artifact is also required before release evidence closes.
- Android/iOS divergence: Android Gradle/SDK/signing/Play artifact and iOS Xcode/SDK/SPM/signing/App Store artifact have independent build graphs and release evidence. Current store/build floors are dynamic and must be rechecked at release; no platform floor is inferred from the other.
- Acceptance and negative cases: Accept only with exact artifact identity, resolved lockfile/transitive hashes, SBOM, config-plugin/prebuild inputs and diff, signing/provenance record, independent verification, platform-specific tests and controlled staged-release/incident hold route. Hold if generated files differ without explanation, native changes use an old dev build, signing custody is opaque, hosted caps/export/exit are unknown, OTA is proposed, or store/device evidence is missing.
- Evidence artifact: Build manifest, package lock and hash record, SBOM, config-plugin inventory, prebuild/generated-native diff, artifact hashes, signing/provenance chain, test/AT/device evidence references and release/incident checklist. This simulation records the required artifact shape only; no build is produced.
- Implementer/reviewer/validator separation: Build/release implementer prepares artifacts; independent supply-chain/release verifier checks hashes, generated output, signing and store controls; separate product/safety/AT validator checks that the artifact corresponds to accepted behavior. The owner does not repair a failed build.
- External human/store/device action: Apple/Google account and legal identity, signing custody, Mac/Xcode, Android build host, local or hosted build owner, tester distribution and store authorities are required. Local versus hosted remains undecided pending evidence; no account or purchase is approved here.
- Failure and recovery: Hold publication and retain the last safe compatible artifact. If a native/config/dependency change invalidates the build, rebuild and revalidate. If data migration is not reversible, refuse binary rollback and route to Packet 12 forward recovery. OTA is never a recovery shortcut.
- Unresolved cost/capacity trigger: Mac/hosted build choice, CI capacity, EAS account/quota/billing/export/exit, artifact retention, signing keys, store enrollment, dynamic tool/store floors and release verifier availability are unresolved. No numeric price is invented.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#2. User-Visible Change]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_REACT_NATIVE_EXPO#3.7 Explicit native boundary and build configuration]]; screens [[03_DESIGN/SCREEN_COVERAGE_TRACEABILITY]], [[03_DESIGN/STATE_MATRIX]]; contracts [[07_AI_ARCHITECTURE/DEPENDENCY_RULES]], [[07_AI_ARCHITECTURE/ROLLBACK_STRATEGY]]; tasks [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[08_REPOSITORY_BOOTSTRAP/QUALITY_GATES]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]].

### Packet 11 — Independent review and cross-platform parity

- Purpose and user outcome: Have an independent reviewer expose missing context, hidden native/configuration work, Android/iOS parity gaps, unsafe state interpretation, evidence substitution and release-integrity holes before any owner decision.
- Minimum input documents/contracts: TASK-SIM-MOB-001 spec; RN/Expo dossier; Packets 01–10 and their evidence shapes; DEBATE-002–005 controls; Phase-3 screens/state/accessibility truth; task/dependency graph; validation and quality gates.
- Allowed files/modules to change: Review report, parity matrix, issue/hold register, requirement traceability and requested-context list only. Reviewers may not directly implement, rewrite generated native projects, approve their own change or turn a hold into a pass.
- Forbidden scope: No aggregate score, recommendation, device/build/accessibility pass from documents, owner coding/debug request, self-review, hidden plugin/module, OTA, scheduled-correctness claim, photo verification or platform substitution.
- Upstream/downstream dependencies: Consumes every packet. Sends findings back to the responsible packet, Packet 10 release gate and Packet 12 recovery path. Manager synthesis and two independent critiques remain outside this candidate simulation.
- Candidate-specific dependency, generated file or native boundary: The reviewer must inspect the config-plugin inventory, prebuild inputs/generated Android/iOS diffs, native-module specs/codegen, development-build rebuild triggers, package lock/SBOM and unresolved local/hosted route. Missing provenance is a hold, not an inferred default.
- Android/iOS divergence: Review parity per platform for lifecycle, permissions, storage, camera, accessibility, build/signing and store evidence. Shared React/TypeScript context cannot close a missing Android or iOS native obligation.
- Acceptance and negative cases: Review is structurally complete only when all twelve packets expose every required field, every requirement maps to both platforms where applicable, negative cases have holds/recovery, optional photo is not verification, no background/push/OTA correctness leak exists, generated/native changes have owners/rebuild evidence, and no documentary pass is claimed. Any omission reopens the packet.
- Evidence artifact: Independent critique, Android/iOS parity matrix, missing-context list, native/config/generated-file audit, reviewer identity and hold disposition. It is not a score or a recommendation.
- Implementer/reviewer/validator separation: One person or AI may implement; an independent native/product/supply-chain reviewer critiques; a separate validator checks evidence completeness and release/safety conditions. Accessibility and safety authorities remain independent of code review.
- External human/store/device action: Qualified Android/iOS reviewers, accessibility and safety reviewers, and a release/provenance verifier are required. Store/device evidence may be referenced only when separately produced; this simulation has none.
- Failure and recovery: Return incomplete packets to their owners with explicit missing fields; preserve the last accepted context and hold release. Do not silently fill unknown facts, change the fixture, or ask the nontechnical owner to fix technical gaps.
- Unresolved cost/capacity trigger: Independent native reviewers, safety/AT authorities, release verifier, manager synthesis capacity and review artifact retention are unresolved. No review or consultant amount is invented.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#6. Required Record Per Packet]], [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#8. Automatic Failure Conditions]]; screens [[03_DESIGN/SCREEN_COVERAGE_TRACEABILITY]], [[03_DESIGN/STATE_MATRIX]]; contracts [[07_AI_ARCHITECTURE/MODULE_BOUNDARIES]], [[07_AI_ARCHITECTURE/DEPENDENCY_RULES]]; tasks [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[07_AI_ARCHITECTURE/ARCHITECTURE_TESTS]], [[08_REPOSITORY_BOOTSTRAP/QUALITY_GATES]].

### Packet 12 — Exit, rollback refusal and forward recovery

- Purpose and user outcome: Preserve user history, provenance, package integrity and safe physical-state truth when the task, dependency, schema, native boundary or framework must be replaced; refuse a dishonest binary rollback after irreversible data migration; and provide a visible forward-recovery/hold path.
- Minimum input documents/contracts: Packets 01, 03, 07, 10 and 11; task outcomes; portable/public contracts; migration policy; rollback strategy; DEBATE-002 offline/recall compatibility; DEBATE-003 approval/emergency suspension; DEBATE-005 release governance; RN/Expo dossier Section 3.11.
- Allowed files/modules to change: Portable schema/fixture/export contracts, migration journal, forward-recovery runbook, compatibility headers, rollback-refusal record, incident evidence and adapter-boundary inventory, if authorized. No destructive erase, binary rollback, OTA or generated-native bypass is authorized.
- Forbidden scope: No UI restoration as physical truth, no reset/drop that deletes independent evidence, no binary downgrade presented as data rollback, no cache-created authority, no deletion of private/shared/official provenance, no Expo Go replacement, no OTA recovery code.
- Upstream/downstream dependencies: Packet 01 supplies portable state truth; Packet 03 supplies migration/checkpoint behavior; Packet 07 supplies package compatibility; Packet 10 supplies artifact/release provenance; Packet 11 verifies the recovery evidence. A replacement framework/client must consume portable contracts rather than the RN/Expo runtime.
- Candidate-specific dependency, generated file or native boundary: React Native/Expo UI, Expo package APIs, config plugins, prebuild-generated projects, Swift/Kotlin/Turbo Native Modules, permissions, signing configuration and store packaging are framework/platform-bound inventory. Replacement requires an explicit second client and new native/build evidence; any native/config change triggers development-build rebuild.
- Android/iOS divergence: Android backup/Keystore/process and Play coexistence differ from iOS Keychain/Data Protection/scene and App Store coexistence. Both platforms require old/new client compatibility, data-preserving migration and independent staged evidence; neither can erase the other’s proof.
- Acceptance and negative cases: Accept portable schemas, history/provenance, package fixtures, classified media/exports, accessibility intent and test oracles; old/new client coexistence; explicit migration version/provenance; safe rollback only when data is reversible; forward recovery and visible hold when it is not. Hold if any path claims rollback after irreversible migration, reuses stale physical progress, loses evidence, relies on OTA, or has no replacement/fallback boundary.
- Evidence artifact: Portable data/contract inventory, migration and rollback-refusal record, forward-recovery fixture, old/new compatibility matrix, artifact provenance and staged-replacement runbook. This simulation does not execute migration or claim recovery success.
- Implementer/reviewer/validator separation: Migration implementer prepares the route; independent data/security/safety reviewer checks continuity and physical-truth boundaries; release/acceptance validator checks staged evidence. The nontechnical owner decides only after those authorities report.
- External human/store/device action: Backend/API/content authority, incident commander, support/recovery owner, Apple/Google release authority, device/AT testers and replacement-client owners are required. No store or device action is available from this document.
- Failure and recovery: Freeze affected release/content/configuration, identify artifact/package/schema/version impact, preserve the last safe compatible client, hold unsafe operations, re-authenticate/quarantine as needed, and execute tested forward recovery. Never conceal data migration or ask an owner to erase/reinstall as a safety fix.
- Unresolved cost/capacity trigger: Dual-client support, migration engineering, backend compatibility, incident response, exports/storage, store review, device/AT evidence and replacement-platform capacity are unresolved. No migration or support price is entered.
- Obsidian links (requirements/screens/contracts/tasks/tests): Requirements [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC#7. Comparison Questions]], [[04_TECH_STRATEGY/DEBATE-006__TASK_SIM_MOB_001_SPEC#8. Automatic Failure Conditions]]; screens [[03_DESIGN/STATE_MATRIX]], [[03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/E05-SCR-018-Completion-Safe-Closure-Record-v2-L05A.png]]; contracts [[07_AI_ARCHITECTURE/MIGRATION_POLICY]], [[07_AI_ARCHITECTURE/ROLLBACK_STRATEGY]], [[07_AI_ARCHITECTURE/PUBLIC_CONTRACTS]]; tasks [[06_DELIVERY_PLANNING/DEPENDENCY_GRAPH]], [[06_DELIVERY_PLANNING/TASK_INDEX]]; tests [[06_DELIVERY_PLANNING/ACCEPTANCE_MATRIX]], [[07_AI_ARCHITECTURE/VALIDATION_STRATEGY]], [[08_REPOSITORY_BOOTSTRAP/QUALITY_GATES]].

## 5. Simulation answers without scoring

### 5.1 Distinct context types a fresh AI must understand

The minimum context is not one generic React task. It includes the shared product/safety
state contract; Turkish screen and accessibility semantics; durable local data and
migration; camera/media/privacy; Android lifecycle/accessibility; iOS lifecycle/
accessibility; offline package and reconciliation authority; automated negative tests;
real-device human acceptance; native/config-plugin/prebuild/build/signing/provenance;
independent review; and exit/forward recovery. The distinction matters because a shared
TypeScript vocabulary does not remove native lifecycle, accessibility, signing, device,
store, safety or reviewer authority.

### 5.2 Where a routine shared change splits

The product/state contract and most fixture/oracle vocabulary can be shared. The work
splits at Android versus iOS lifecycle and accessibility, permission/camera/file behavior,
background transfer policy, generated native project/configuration, signing, artifact
provenance, store evidence and real-device acceptance. A React Native screen can reduce
surface duplication, but it cannot erase those platform-specific obligations.

### 5.3 Indirect native/generated changes

The change can affect native behavior indirectly through an Expo package with native code,
config plugin, permission or entitlement, build property, native module, prebuild input,
generated Android/iOS project, package lock or SDK/toolchain. Each such change must be
named in the task graph, reviewed, regenerated/diffed where applicable, included in SBOM
and provenance, and followed by a fresh development build plus affected-platform
revalidation. Direct generated-file edits cannot serve as an invisible shortcut.

### 5.4 Dependency replacement behind a boundary

A failed Expo/RN dependency can be replaced only when the capability has a named adapter,
portable contract, maintained replacement or explicit Swift/Kotlin/Turbo Native Module
fallback, lifecycle/thread/permission/accessibility behavior, owner, security/EOL record,
and negative/recovery tests. If replacement changes native/configuration inputs, both the
development build and final affected-platform artifact must be rebuilt and revalidated.
An unnamed plugin, unreviewed fork, Expo Go substitution or owner-led build repair is not
a replacement plan.

### 5.5 What must be rebuilt and revalidated

JavaScript-only presentation work may be inspected against an existing development build
for a bounded inner loop. A native module, config plugin, permission/entitlement, Expo
package with native code, SDK/build property, native dependency, prebuild input or
generated-project change invalidates that build context and requires a new affected-
platform development build. Release evidence additionally requires the exact lockfile,
SBOM, generated diff, signing/provenance, automated evidence, real-device/AT evidence and
store-governed artifact. OTA is excluded from this chain.

### 5.6 Automated versus physical/human evidence

Automated evidence can cover contract/state transitions, serialization, negative fixtures,
idempotency, migration journals, package compatibility and architecture/dependency rules.
Only real devices and humans can close physical interruption behavior, camera/permission
interaction, TalkBack/VoiceOver, largest text/focus/announcement behavior, safe-stop
comprehension and physical-state revalidation. Store/build/signing evidence requires its
own release authority. No simulation artifact substitutes for those authorities.

### 5.7 Detecting incomplete Android/iOS parity

A fresh AI should use a requirement-by-platform matrix with one row for each state,
negative case, lifecycle event, accessibility check, native/config input, build artifact
and recovery path. Every row must identify Android evidence, iOS evidence, shared contract,
reviewer and validator. Missing platform row, unexplained generated diff, different safety
meaning, missing dev-build rebuild, or a device/AT placeholder presented as complete is a
hold. Shared React/TypeScript files do not count as evidence for both platforms.

### 5.8 Revert without lying about data or physical state

If no durable checkpoint committed, the only truthful result is `unknown/partial` with
safe-stop and recovery. After a durable schema/data migration, binary rollback is not
assumed to reverse data. The release must refuse unsafe rollback, preserve provenance,
coexist with compatible old/new clients where possible, and use a tested forward recovery
with visible hold/re-authentication. A restored UI, cache, photo or notification never
proves current physical state.

### 5.9 What survives framework replacement

Portable state/data/content schemas, package manifests and compatibility fixtures,
history/provenance, classified media/exports, identity mapping/re-auth contracts, design
tokens/Turkish copy/accessibility intent, test oracles, API/content contracts, migration
records, SBOM/provenance and incident history survive. React Native/Expo UI and package
APIs, config plugins, generated native projects, Swift/Kotlin/Turbo Native Modules,
permissions, signing and store packaging are isolated framework/platform artifacts and
must be replaced behind the portable boundary.

## 6. Permitted status and conditions for a nontechnical owner

### 6.1 Permitted status

`OPERABLE WITH MATERIAL CONDITIONS / HELD`

This means the task can be described in bounded packets under the current model, but no
implementation, build, device result, accessibility result, store result, safety approval
or cost commitment has been established. It is not a recommendation or authorization.

### 6.2 Conditions before any implementation or release routing

- Freeze and approve the Packet 01 state/authority contract and Packet 02 Turkish/accessibility mapping against the Phase-3 truth.
- Assign separate implementer, Android reviewer, iOS reviewer, safety/content reviewer, accessibility validator, release/provenance verifier and incident/recovery owner.
- Name every Expo package/config plugin/native module, its version, generated-project inputs/diff, fallback, owner, lifecycle/thread/permission/accessibility behavior and EOL/security response.
- Resolve the local-versus-hosted build route only with signing custody, cap/alert/export/exit evidence; neither route is selected by this simulation.
- Rebuild the affected development build whenever native/configuration inputs change, then rebuild and revalidate the final platform artifact. Do not use Expo Go or OTA code delivery.
- Complete automated contract/negative evidence and separate real Android/iOS TalkBack/VoiceOver, largest-text, interruption, camera and physical revalidation evidence. No device or accessibility pass is claimed here.
- Produce lockfile/transitive hashes, SBOM, config-plugin/prebuild/generated-native provenance, artifact hashes, signing evidence and store-governed release controls.
- Prove safe-stop, `unknown/partial`, package/recall reconciliation, migration/rollback refusal and forward recovery without treating a photo or restored UI as physical truth.
- Keep all unknown prices, device/host availability, reviewer capacity, provider limits, store/tool floors and migration/support capacity `UNRESOLVED`; do not convert them to zero or invent a quote.

The nontechnical owner may hold the task until these conditions have accountable evidence.
The owner is not asked to code, debug, repair a build, approve safety content alone, or
accept a documentary simulation as a device/build/store pass. Manager synthesis and the
two independent critiques required by the common spec remain outstanding.
