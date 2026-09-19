# DEBATE-006 — REVIEW D: MOBILE PLATFORM, ACCESSIBILITY & MAINTENANCE

Status: COMPLETE — CONDITIONAL FIVE-WAY CRITIQUE / NOT ADR-READY  
Date: 2026-09-18  
Reviewer: independent Luna Max read-only review track  
Scope: Flutter; React Native + Expo development builds with explicit native boundary; KMP-native; KMP + Compose Multiplatform; fully native Kotlin/Android + Swift/iOS

## 1. Disposition

This review is suitable for Phase-4 judge synthesis with conditions. It is not a framework recommendation, ADR,
implementation authorization or Gate 4 -> 5 approval.

- The corrected dossiers are equivalent enough to enter independent five-way critique. The equivalence audit reports no
  remaining blocking drift in the five-way fixture, S1–S15 structure, accessibility fields, TCO schema, pricing treatment
  or the KMP-native/KMP-Compose distinction
  (04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_EQUIVALENCE_AUDIT_01.md:33–49).
- Every candidate remains documentary, unselected and HELD. Each records 0 PASS / 15 HELD / 0 REJECT and makes no
  real-device, assistive-technology, safety, security, benchmark, store or release claim
  (DEC-0031, 00_CONTROL/DECISION_LOG.md:825–836; representative result records:
  DEBATE-006__DOSSIER_FLUTTER.md:594–609, DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:952–966,
  DEBATE-006__DOSSIER_KMP_NATIVE.md:862–888, DEBATE-006__DOSSIER_KMP_COMPOSE.md:913–969,
  DEBATE-006__DOSSIER_FULL_NATIVE.md:826–891).
- The conditional orderings in Section 9 are dimension-specific hypotheses, not scores and not a final selection.
  Documentary convenience cannot override a safety, data-continuity, accessibility, release-integrity or recovery hold.

## 2. Binding controls applied equally

| Control | Review interpretation | Repository authority |
|---|---|---|
| Data-efficient offline | Download only the smallest safe selected-motorcycle/task closure. Required safety/recovery material stays complete; heavy media is optional and visible before download; unrelated library content is not a default. | 00_CONTROL/DECISION_LOG.md:536–556; DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:79–97 |
| Bounded offline and restore | Eligibility, recall and authority are not created by cached, stale, restored, cloned, time-anomalous or incompatible state. Foreground reconciliation is the decisive path. | 00_CONTROL/DECISION_LOG.md:568–589; DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:65–77, 140–148 |
| Release meaning | Approval binds immutable consumer meaning. Current authority, delivery observation and consumer reconciliation remain separate; suspension is negative authority; rollback cannot erase new data or revive revoked truth. | 00_CONTROL/DECISION_LOG.md:591–625 |
| Supply chain and OTA | Binary, web, API, database migration, content, configuration and emergency suspension are distinct authorities. The exact verified artifact, dependency closure, provenance, SBOM, verification, signature, compatibility and revocation context are release inputs. No OTA/runtime code channel is approved. | 00_CONTROL/DECISION_LOG.md:671–713 |
| Accessibility evidence | All nine accessibility checks are required; API availability is not a device pass. Actual Android/iPhone assistive-technology evidence and qualified human review cannot be replaced by simulator or AI claims. | DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:78–94; 00_CONTROL/DECISION_LOG.md:817–836 |
| Equal evidence and cost | All candidates use the same S1–S15 schema, four device cohorts, network/interruption/data fixture, exact TCO columns and PASS/HELD/REJECT rule. Unknown cost is unresolved, never zero. | DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:53–76, 96–147; DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:214–225 |

## 3. Framework capability versus Kavriva-owned system work

The following are product, service, safety or governance obligations. They are not framework benefits and must not be
credited to one candidate merely because a framework can render a screen or call an OS API.

| System obligation | Candidate-neutral requirement | Candidate-attributable surface |
|---|---|---|
| Official truth and safety | Internal Operations/API owns classification, provenance, approval, publication, correction, withdrawal, recall, current eligibility, audit and authorization. A mobile cache, UI or notification is never the authority. | The candidate must consume the versioned/classed contract, expose stale/unknown/held/safe-stop states and preserve a clear boundary from browser operations. See Flutter:70–85, 126–135; RN/Expo:211–224, 338–350; KMP-native:350–358; KMP-Compose:397–405; full native:204–218. |
| Scoped package and continuity | Package identity, required-versus-optional media, size/space consent, integrity, atomic promotion, cancellation, resume, eviction, reconciliation, conflict, recall and no-silent-discard semantics are app/service work. | The framework or native APIs provide file, transfer, lifecycle and UI primitives. The implementation must add the same manifest/checkpoint/state contract for every candidate. The fixed package and local data fixture are common: DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:79–112. |
| Protected data and restore | Data classes, backup inclusion/exclusion, key hierarchy, re-authentication, clone detection, migration, export disclosure and recovery are product/security policy. Restored authority remains quarantined. | OS secure storage, backup and database APIs differ by candidate; none of the dossiers closes the policy or game-day evidence. |
| Accessibility and Turkish safety meaning | Turkish readiness, warning, stop, active-step, uncertainty and recovery meaning must remain identical and independently accepted on both platforms. | Semantics APIs, widgets, Compose mappings, native controls and test tools are evidence affordances only. Native permission/picker/share/notification surfaces and actual AT behavior remain candidate work. |
| Release and incident integrity | Artifact identity, closed release graph, independent verification, signing custody, suspension generation, partial/unknown outcome, impact graph, recall, forward recovery and reach-back are shared governance work. | Candidate-specific build graphs, generated projects/frameworks, dependencies, stores, platform rollout and duplicate parity reviews create different maintenance surfaces. |

## 4. Lifecycle, offline and restore comparison

### Common result

The fixture requires the same 72-hour offline, transfer loss, background/lock/call/process-kill/restart, clock-change and
backup-restore conditions for every candidate
(DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:65–77). The selected package is a required compact closure
with optional media separated, a size-before-download decision, temporary old-plus-new verification space and no
unrelated catalog download
(DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:79–97). Duplicate, partial, corrupt, interrupted,
corrected, withdrawn and recalled records may not be silently discarded or overwritten
(DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:99–112).

No candidate can claim that a framework’s offline-first, database, file-transfer or background API closes these obligations.
The safe conceptual state sequence remains:

requested scope -> staged transfer -> integrity/manifest verification -> complete promotion
-> bounded offline use -> foreground reconciliation -> current/held/recalled result

### Candidate pressure points

- Flutter puts the manifest, integrity, atomic promotion, cleanup and durable checkpoint above Dart/native adapters;
  Android/iOS background work is an optimization and restore/clone state is untrusted
  (DEBATE-006__DOSSIER_FLUTTER.md:87–105). This gives one visible application state surface, but plugin/channel and
  host lifecycle behavior remain open.
- RN + Expo explicitly treats expo-sqlite and expo-file-system as primitives, not sync, authority or atomic package
  semantics. Development-build native changes require a rebuild, and background tasks are deferrable; foreground
  reconciliation remains correctness
  (DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:226–261, 277–306). The main maintenance risk is a JavaScript-level
  change being mistaken for closure of a native/lifecycle change.
- KMP-native can place deterministic package, pending-operation and reconciliation meanings in shared Kotlin code while
  native Android/iOS applications own lifecycle and system surfaces. It still needs two native lifecycle/storage/media
  paths and a generated iOS framework; foreground reconciliation, not KMP or a scheduler, establishes current state
  (DEBATE-006__DOSSIER_KMP_NATIVE.md:282–301, 303–315).
- KMP + Compose can share core state and presentation of partial, unknown, held and recovery results, but the hosts still
  own process, permission, storage, background and native-surface behavior. Compose must not hide over-download or turn
  offline state into authority
  (DEBATE-006__DOSSIER_KMP_COMPOSE.md:324–356).
- Full native has the most direct access to Android/iOS lifecycle and transfer primitives, but owns two package,
  checkpoint, persistence, migration and recovery implementations whose parity is an explicit obligation
  (DEBATE-006__DOSSIER_FULL_NATIVE.md:220–256).

### Reviewer conclusion on lifecycle

Direct native access reduces abstraction distance, not product risk by itself. KMP-native and full native make platform
callbacks and failure paths most explicit; Flutter and RN/Expo can centralize routine state/presentation but retain
plugin/bridge exceptions; KMP-Compose centralizes more presentation while adding shared-renderer/host mapping risk.
None has lifecycle or restore evidence beyond a documentary plan.

## 5. Accessibility comparison

The controlled matrix requires VoiceOver, TalkBack, largest text/reflow, focus/order, state announcements, non-color
status/contrast, reduced motion, switch/voice control and reduced dexterity. The matrix is an evidence plan, not approval
(DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:78–94).

| Candidate | Documentary accessibility shape | Maintenance/accessibility risk | Current result |
|---|---|---|---|
| Flutter | Shared Dart semantics and focus/state intent, with native permission, picker, share, notification and link surfaces. | A unified widget tree can hide platform-specific semantics, process return and native dialog behavior; Flutter integration tests do not replace native UI AT review. | All rows HELD; no row PASS (DEBATE-006__DOSSIER_FLUTTER.md:463–481). |
| RN + Expo | RN labels, roles, state/live-region/focus affordances inside an Expo development build; platform-specific work is explicit. | Config plugins, native modules, rebuilds, async announcement timing and native surfaces need separate iOS/Android evidence; API presence is not acceptance. | All rows HELD (DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:740–756). |
| KMP-native | Shared stable state/copy identifiers feed two native semantic trees; no shared renderer is assumed. | Native expression, focus restoration, Dynamic Type/font scale and native surfaces are duplicated and can drift; two AT matrices are required. | All rows HELD (DEBATE-006__DOSSIER_KMP_NATIVE.md:735–751). |
| KMP + Compose | Shared Compose semantics/traversal and iOS mapping provide a common presentation base; hosts own native surfaces. | iOS synchronization/mapping, native interop and the documented Material3 high-contrast gap add a specific uncertainty; a shared composable is not native AT proof. | All rows HELD; no row PASS (DEBATE-006__DOSSIER_KMP_COMPOSE.md:780–799). |
| Full native | Android Compose/View and iOS SwiftUI/UIKit provide direct OS accessibility affordances and independent native control. | Two semantic trees, two Turkish copy/layout implementations, two native-surface handoffs and two AT suites must stay equivalent. A fix on one platform is not evidence for the other. | All rows HELD; no row PASS (DEBATE-006__DOSSIER_FULL_NATIVE.md:686–711). |

### Reviewer conclusion on accessibility

For direct control of OS-native semantics and lifecycle, full native and KMP-native have the clearest boundary. That is a
capacity and evidence advantage only if independent Android/iOS accessibility owners and devices exist. Flutter and RN/Expo
offer shared semantic implementation surfaces but still require native exceptions. KMP-Compose may reduce duplicated
presentation semantics, yet its cross-platform semantic mapping and iOS high-contrast caveat are explicit unresolved
items. No candidate has an accessibility pass.

## 6. Native capability, dependency and maintenance closure

The controlled closure requires, for each critical capability, an exact path/version, dependency, native skill,
lifecycle/threading constraint, accessibility impact, fallback and EOL/security owner; an unnamed plugin or owner is HELD
(DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:46–51).

| Candidate | Closure shape | Upgrade/security consequence |
|---|---|---|
| Flutter | Shared Dart surface plus platform channels and Flutter-team/plugin snapshots. Camera, file, share, key, transfer, lifecycle and signing rows remain owned/native or package boundaries. | One shared routine UI path can reduce parity edits, but Flutter/Dart/engine, plugin transitive graph, Android host and iOS host must move as one verified graph. The dossier leaves exact locks, owners, fallbacks and EOL/security responses HELD (DEBATE-006__DOSSIER_FLUTTER.md:107–156). |
| RN + Expo | Expo development build, config-plugin/prebuild path, React Native platform files, Expo packages and explicit Swift/Kotlin/Turbo Native Module escape. Expo Go is excluded. | Any native/config/SDK/module change requires a new native build; generated projects and prebuild ownership must be controlled. The exact lock, generated diff, SBOM, owner, fallback and security response remain HELD (DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:291–306, 382–405). |
| KMP-native | Shared Kotlin domain/data boundary, two native UI/host paths, generated iOS framework and native platform adapters. | Reduces duplicated domain semantics, but Kotlin/KMP/Gradle/AGP/JDK/Xcode/Swift integration and two native closure/review paths must be versioned together (DEBATE-006__DOSSIER_KMP_NATIVE.md:332–348, 384–411). |
| KMP + Compose | Shared Kotlin core and Compose UI, two native hosts and explicit interop/native exceptions. | The widest shared toolchain coupling: Kotlin/KMP/Compose/compiler/runtime, Jetpack mapping, Gradle/AGP/JDK, generated iOS framework, Xcode/Swift and native packages. A Compose or compiler update can change more than the shared screen source (DEBATE-006__DOSSIER_KMP_COMPOSE.md:378–395, 423–440). |
| Full native | No cross-platform framework runtime is assumed; Android and iOS each use native APIs, storage, UI, build, signing and store paths. | Removes cross-platform plugin/renderer indirection but creates two complete dependency, toolchain, SBOM, signing and security-response graphs. Native API availability does not close ownership, fallback or device evidence (DEBATE-006__DOSSIER_FULL_NATIVE.md:300–318, 337–356). |

### Reviewer conclusion on closure and security response

The main trade is not “framework versus no framework”; it is where unresolved native and dependency ownership is made
visible. RN/Expo and Flutter have more explicit plugin/configuration edges. KMP-Compose has a shared UI/runtime/compiler
coupling that can obscure host impact. KMP-native and full native expose more direct platform work, but their apparent
simplicity would be misleading if two native owners, locks, SBOMs, fallbacks and security-response paths are not funded and
reviewed. All five remain HELD until exact closure is evidenced.

## 7. OS/store/toolchain upgrades, release parity and incident handling

The template requires a normal release, emergency correction, forced Apple/Google change, dependency abandonment,
old/new coexistence, migration rollback refusal and incident pause/recovery
(DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:96–108). DEBATE-005 requires immutable verified artifacts, a closed
meaning graph, separate authorities, protected impact mapping and no OTA
(00_CONTROL/DECISION_LOG.md:680–713).

| Candidate | Release-parity surface | Failure/upgrade behavior documented |
|---|---|---|
| Flutter | Two signed artifacts; shared Dart/Flutter plus native host/plugin graph. | Re-pin SDK/Dart/ref/digest, pub lock and host graph; hold on native/AT/migration failure; retain prior artifact; use forward migration. Swift Package Manager/CocoaPods change is a concrete forced-event candidate, not a pass (DEBATE-006__DOSSIER_FLUTTER.md:483–498). |
| RN + Expo | Two store artifacts; JS/React surface, development-build native graph, config/prebuild output and native modules. | Rebuild for native changes; Expo runtime-version is only a technical compatibility guard; OTA is excluded. Pause rollout, map artifact/runtime/package/content/config impact and reopen only after independent evidence (DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:764–848). |
| KMP-native | One reviewed shared-core revision bound to two native UI revisions and two signed artifacts. | Re-pin KMP/toolchain and regenerate the iOS framework; hold if either platform cannot be rebuilt or verified; retain accepted artifacts and reconcile foreground. Rollback refusal is explicit when data/schema/key migration is unsafe (DEBATE-006__DOSSIER_KMP_NATIVE.md:753–766). |
| KMP + Compose | Shared KMP/Compose source and generated framework bound to two host artifacts. | Kotlin/Compose/compiler/Jetpack/Gradle/AGP/Xcode changes can affect both shared and host graphs. Hold until both artifacts and native/AT/release evidence are rechecked; no OTA (DEBATE-006__DOSSIER_KMP_COMPOSE.md:801–815). |
| Full native | Two independent Android/iOS source, toolchain, signing, artifact, rollout and incident graphs. | Android-only or iOS-only forced requirements can be handled separately only if common contract/release meaning remains safe. Every correction, reviewer, signature and parity check must be coordinated per platform (DEBATE-006__DOSSIER_FULL_NATIVE.md:300–318, 713–730). |

### Release policy inferred for all five

1. An unavailable identity, signer, verifier, safety reviewer, accessibility oracle, device cohort, dependency owner or
   recovery path produces a visible HOLD; it never produces a silent downgrade.
2. A platform-specific artifact may be held while another platform proceeds only after the protected release graph proves
   that shared API/schema/content/configuration/offline meaning and current suspension generation remain safe. The exact
   independently publishable scope is still unresolved in DEC-0025
   (00_CONTROL/DECISION_LOG.md:615–623). If that proof is unavailable, hold the affected shared meaning and both
   dependent paths.
3. A browser timeout or disconnected confirmation is outcome unknown, not success or failure. Reconcile by the same bound
   operation identity; preserve authoritative-current, delivery-observed and consumer-reconciled states separately
   (00_CONTROL/DECISION_LOG.md:602–613).
4. Emergency suspension is a narrow negative authority independent of normal publication. It may stop exposure or active
   eligibility, but cannot create replacement technical truth. Restore/failover is quarantined until current authority,
   audit continuity, integrity and trust context reconcile.
5. Rollback is a new controlled event to a still-valid known-good artifact. If data migration cannot be reversed safely,
   refuse binary rollback, preserve valid new data, use reviewed forward recovery and keep the affected scope held.
6. Stop, recall and correction retain residual risk for already installed/offline clients; rollout stop is not a downgrade
   of those clients. The impact graph must include artifacts, deployments, cohorts, offline packages and configuration
   (00_CONTROL/DECISION_LOG.md:691–697).

## 8. Exit and AI-maintenance comparison

All dossiers preserve the same portable core: schemas, history/provenance, package fixtures, exports, Turkish copy/design
and accessibility intent, acceptance oracles, release evidence and migration records. Framework/runtime, native adapters,
generated projects/frameworks, signing and store packaging remain bound. This is a required boundary, not an exit pass.

- Flutter keeps Dart widgets/runtime, plugin APIs and host projects bound; a replacement consumes portable schemas,
  manifests, fixtures and forward migrations
  (DEBATE-006__DOSSIER_FLUTTER.md:563–592).
- RN/Expo isolates React Native/Expo UI, config plugins, generated projects, Expo APIs and Turbo Native Modules; its
  proposed replacement is a staged second client against the same portable contracts
  (DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:917–950).
- KMP-native keeps common KMP source/framework binaries, generated iOS frameworks, native UI and host toolchains bound,
  while preserving a shared domain/data contract for replacement
  (DEBATE-006__DOSSIER_KMP_NATIVE.md:836–860).
- KMP-Compose additionally binds shared Compose source, compiler/runtime and generated iOS framework; a renderer replacement
  must revalidate common semantic intent and both hosts
  (DEBATE-006__DOSSIER_KMP_COMPOSE.md:879–911).
- Full native binds two complete platform implementations and toolchains. A replacement still needs two platform
  implementations, coexistence, migration and independent evidence; direct native access is not an exit plan
  (DEBATE-006__DOSSIER_FULL_NATIVE.md:789–824).

For the approved AI-operated model, a bounded TASK, separate implementation/review/validation and portable evidence are
mandatory. The user is not a coding, debugging or build-repair mitigation
(00_CONTROL/DECISION_LOG.md:717–769; DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:150–169).

- Flutter and RN/Expo offer one routine shared presentation/application context, but native plugins/configuration,
  lifecycle, signing, AT and release exceptions must remain visible.
- KMP-native offers one shared domain/data context plus two native UI contexts; the split is conceptually clear but
  increases native reviewer and parity tasks.
- KMP-Compose offers one shared domain/presentation context, but compiler/runtime/generated-framework and host exceptions
  make upgrade impact easy to underestimate.
- Full native makes every platform exception explicit, but one completed Android task never completes its iOS counterpart.

No candidate has a proven AI-maintenance advantage; these are task-shape hypotheses until deterministic task graphs,
reviewer capacity, build recovery and acceptance evidence exist.

## 9. Conditional ordering and ties (not a recommendation)

The following are the only defensible orderings from the no-code evidence. They are conditional, dimension-specific and
must not be converted into an aggregate score.

| Decision objective and required assumption | Conditional relation | Why it can flip / current blocker |
|---|---|---|
| Reduce routine shared presentation and bounded AI UI task duplication, while native specialists are scarce | Flutter ≈ RN + Expo ≈ KMP + Compose on shared-UI surface; KMP-native and full native are lower on this dimension | The three shared-UI candidates still differ materially: RN/Expo rebuild/config-plugin edges, Flutter plugin/host edges, and KMP-Compose compiler/runtime/iOS mapping. No productivity evidence exists to break the tie. |
| Maximize direct OS semantics, lifecycle and native-surface control, with two-platform native reviewers and devices available | Full native ≈ KMP-native on direct-control surface; both are ahead of shared-renderer options on boundary explicitness | Native control does not close the duplicate AT/recovery/release work. KMP-native adds KMP/generated-framework integration; full native adds more duplicated domain/data/UI work. All are HELD. |
| Minimize duplicated executable domain/data semantics without adopting shared UI | KMP-native > full native on this narrow objective | This assumes KMP compatibility, Kotlin/Native-to-Swift integration and shared-core ownership are acceptable. The dossier has no implementation or migration proof. |
| Minimize cross-platform renderer/compiler coupling | Full native is the clearest baseline; KMP-native is next on this narrow axis; no defensible order exists among Flutter, RN/Expo and KMP-Compose from current evidence | Full native still has two toolchain graphs. KMP-native retains KMP integration. Flutter/RN/Expo/Compose each retain different framework/runtime/plugin/renderer coupling; exact locks and maintenance capacity are unresolved. |
| Minimize duplicated presentation source | KMP-Compose ≈ Flutter ≈ RN + Expo > KMP-native ≈ full native | This measures source-surface shape only, not accessibility, lifecycle, security or release quality. Native exceptions and host artifacts remain in every candidate. |

There is no justified total ordering across all objectives. In particular, the evidence cannot presently decide Flutter
versus RN/Expo, KMP-native versus full native, or whether KMP-Compose’s shared UI benefit outweighs its compiler/interop and
accessibility mapping risk.

## 10. Failure and abuse scenarios that remain decisive

| Scenario | Required system outcome | Candidate-specific pressure |
|---|---|---|
| Client silently downloads the unrelated catalog or optional media | Block the over-download; show scope/size/consent; preserve required compact safety/recovery closure. | Every framework can accidentally hide work in a cache/resource/plugin. Package manifest and transfer evidence are app-owned. |
| Process kill, cancellation or low storage during package/database commit | Mark partial/unknown, preserve last durable checkpoint, never present as current; retry or foreground reconcile. | Flutter/RN need explicit adapter state; KMP candidates need common/native parity; full native needs two equivalent implementations. |
| Restored or cloned cache appears eligible | Quarantine, re-authenticate and reconcile current release/suspension/content authority; never mint positive authority locally. | Secure-storage and backup primitives differ; no dossier closes key/backup/game-day policy. |
| Permission, picker, share, notification or native module is denied/removed | Use a visible safe manual/no-media or hold path; never claim evidence or current safety truth. | Shared-renderer candidates need native escape ownership; native candidates need two platform fallbacks. |
| Framework API/static semantics check appears to pass while TalkBack/VoiceOver fails | Hold release and preserve accessible safe-stop/recovery; require independent human real-device evidence. | KMP-Compose has explicit iOS mapping/high-contrast uncertainty; all others have native-surface/parity uncertainty. |
| Critical dependency CVE, abandonment or incompatible OS/store requirement | Freeze affected artifact/capability; identify impact from lock/SBOM/provenance; replace only through reviewed graph and re-test. | RN/Expo native rebuild/prebuild, Flutter plugin/host, KMP/Compose compiler/framework, and two native graphs have different blast radii. |
| One platform is corrected while the other remains stale | Keep platform-specific state visible; release only if the common meaning graph and suspension generation prove safe; otherwise hold both dependent paths. | Full native and KMP-native have obvious parity duplication; shared UI reduces source duplication but not two signed artifacts. |
| Migration cannot be reversed or release confirmation is lost | Treat outcome as unknown or rollback refusal; preserve valid new data; forward-recover and reconcile by operation identity. | No candidate may use binary rollback as data rollback. |

## 11. Decisive assumptions and open user decisions

The following must remain user/product decisions or explicitly assigned external authority; this review does not choose
them:

1. Final Android/iPhone models, patch floors, oldest/current support policy and actual access to four device cohorts,
   VoiceOver/TalkBack and human accessibility testers.
2. Whether the owner can obtain/borrow native Android, iOS, Mac/Xcode, signing and store capacity; whether a platform can
   be held while another launches; and the required reach-back/incident authority.
3. Native UI toolkit and reviewer ownership for KMP-native and full native; native escape boundary for Flutter/RN/Expo;
   Compose/native exception policy for KMP-Compose.
4. Exact database, schema, encryption, key hierarchy, backup/restore, clone, migration, conflict, reconciliation and
   package-integrity implementation, with primary/backup owners and safe fallbacks.
5. Exact dependency locks, generated artifacts/frameworks, SBOM/provenance, vulnerability/EOL response, signing/key
   custody, CI/host path and store compatibility matrix.
6. Emergency suspension scope, partial publication policy, unknown-outcome reconciliation, old-client coexistence,
   rollback refusal, offline recall residual risk and affected-user communication.
7. AI task/review/validation capacity and independent safety, security, accessibility and release authorities. AI cannot
   impersonate the owner’s legal/store identity or qualified human review
   (00_CONTROL/DECISION_LOG.md:638–665; 717–769).
8. Actual 12–24 month cash ceiling, current resources and whether any hosted build, provider, device, tester or specialist
   path is acceptable. The controlled worksheet must preserve unresolved amounts rather than inventing prices
   (00_CONTROL/DECISION_LOG.md:773–813; DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md:124–147).

## 12. Remaining blockers and proceed decision

### No new equivalence blocker

The equivalence audit’s corrections are present for all five: four cohorts are bound globally, workload arithmetic and TCO
columns are controlled, RN/Expo OTA is excluded rather than counted as an S scenario, and KMP-native is not conflated with
KMP-Compose. The five drafts may proceed to independent judge synthesis
(DEBATE-006__DOSSIER_EQUIVALENCE_AUDIT_01.md:25–49).

### Blocking evidence for any final recommendation

- No actual four-cohort device, interruption, accessibility or safety evidence.
- No complete native/dependency closure with committed locks, generated output, SBOM, provenance, EOL/security owner,
  fallback and independent verification.
- No durable database/package/restore/key/migration/reconciliation game-day evidence.
- No completed two-platform release graph, signing custody, store acceptance, emergency suspension or incident rehearsal.
- No confirmed owner/capacity plan for native review, AT, safety/content, security, release, Mac/build and reach-back.
- No approved exit/migration rehearsal or replacement-client evidence.

These are common blockers, not an intrinsic rejection of any one candidate. They are consistent with the candidate result
sections and the approved rule that missing critical evidence remains HELD
(DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md:214–225; representative unresolved result records:
DEBATE-006__DOSSIER_FLUTTER.md:611–637, DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md:952–961,
DEBATE-006__DOSSIER_KMP_NATIVE.md:876–884, DEBATE-006__DOSSIER_KMP_COMPOSE.md:938–967,
DEBATE-006__DOSSIER_FULL_NATIVE.md:855–889).

| Decision surface | Reviewer disposition |
|---|---|
| Equal-fixture/equivalence readiness | PASS_WITH_CONDITIONS — proceed to five-way critique; preserve the frozen fixture and do not use dossier length as evidence. |
| Platform/accessibility/maintenance comparative research | PASS_WITH_CONDITIONS — use the conditional ties and failure rules in this report. |
| Technology recommendation or weighted score | HELD — no defensible aggregate ordering or score exists. |
| ADR, implementation or Gate 4 -> 5 | NOT READY / HELD — requires the missing evidence, owners and user decisions above. |

Final reviewer position: proceed to judge synthesis, but preserve the distinction between framework capability and
Kavriva-owned system work, keep every unproven gate HELD, and do not turn these conditional tiers into a technology
selection.
