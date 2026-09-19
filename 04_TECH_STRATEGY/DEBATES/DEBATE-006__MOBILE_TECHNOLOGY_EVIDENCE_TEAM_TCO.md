# DEBATE-006 — MOBILE TECHNOLOGY EVIDENCE, TEAM AND TCO

Status: `REVIEW COMPLETE — USER WORKING-DIRECTION DECISION PENDING / NO-CODE / FRAMEWORK HELD`
Date: 2026-09-17
Decision level: Phase-4 recommendation only; not an ADR and not approved/locked

## 1. Decision Question

Which mobile implementation family should Kavriva carry toward Phase 5 after comparing the same real product
and failure scenarios without writing an application prototype?

The options are:

1. Flutter;
2. React Native with Expo development builds and an explicit native boundary;
3. Kotlin Multiplatform shared domain/data logic with native Android and iOS UIs (`KMP-native`);
4. Kotlin Multiplatform with Compose Multiplatform shared UI (`KMP-Compose`), kept separate from option 3;
5. fully native Swift/iOS plus Kotlin/Android as the reference baseline.

This debate does not select a backend, database, cloud provider, analytics service, identity provider or OTA
update channel. It does not authorize code, a prototype, a proof of concept or an executable technology spike.

## 2. What “Real Scenario Comparison” Means

The options are not compared through marketing feature lists or a generic demo. Each option must explain how the
same Kavriva situation would be designed, maintained, released and recovered. The evidence is documentary:

- official platform/framework documentation;
- an architecture and state walkthrough using the same approved product fixtures;
- a dependency and native-exception inventory;
- an accessibility, lifecycle, upgrade and failure matrix;
- a team-capability inventory and a 12–24 month cost worksheet;
- two independent adversarial reviews.

During Phase 4, words such as `test`, `exercise` and `simulate` mean a documented state/failure walkthrough against
official constraints. They do not mean running a candidate application, signing a store build or claiming a real-device
pass. The dossier records those later acceptance activities and their expected evidence; execution remains unauthorized
until the applicable Phase-5/implementation decision.

For example, “the user downloaded one maintenance guide, lost the network, the operating system terminated the
app, the guide was later recalled, and the installed client is old” is one common scenario. Each candidate must
show where the downloaded data lives, what survives termination, what can still be displayed, what becomes blocked,
how recovery remains available and what happens at the next connection. The scenario is real even though no code is
written: the required states, platform limits, dependencies, owners and acceptance evidence are concrete.

Official documentation proves that a mechanism exists. It does not prove that Kavriva's design is correct, that the
team can maintain it or that it will behave correctly on every device. Those remain explicit evidence gaps.

## 3. Approved Constraints Carried Forward

The comparison inherits `DEC-0021`–`DEC-0030` and DEBATE-001–005:

1. The consumer product is Android/iOS; Internal Data & Content Operations remains browser-based.
2. Planning is no-code. No candidate earns points from an unapproved prototype.
3. Offline content is selected-motorcycle/task scoped. Compact safety/recovery content is mandatory; heavy media is
   optional and must not cause excessive downloads.
4. Offline eligibility is risk-tiered and bounded. Background execution or push delivery is never assumed timely.
5. Active physical work resumes only after required current-state and safety revalidation.
6. Local-first value and later profile migration must not silently lose or overwrite data.
7. Content, client capability, configuration and revocation must form a compatible release meaning.
8. Exact immutable artifacts are promoted; dependency/build/signing evidence and a protected incident graph are required.
9. No OTA code/update channel is approved. A framework's OTA capability is neither a benefit nor an authorization.
10. Accessibility, Turkish-first copy/units and truthful uncertainty are release requirements, not optional polish.

## 4. Current Official Evidence

Primary documentation checked on 2026-09-17:

- Flutter supported platforms: https://docs.flutter.dev/reference/supported-platforms
- Flutter platform integration/channels: https://docs.flutter.dev/platform-integration/platform-channels
- Flutter offline-first architecture: https://docs.flutter.dev/app-architecture/design-patterns/offline-first
- Flutter accessibility and testing: https://docs.flutter.dev/ui/accessibility
- React Native native modules: https://reactnative.dev/docs/turbo-native-modules-introduction
- React Native accessibility: https://reactnative.dev/docs/accessibility
- React Native releases and support: https://reactnative.dev/releases/
- React Native versioning policy: https://reactnative.dev/releases/versioning-policy
- React Native 0.87 release: https://reactnative.dev/blog/2026/08/11/react-native-0.87
- Expo development builds: https://docs.expo.dev/develop/development-builds/introduction/
- Expo SDK 57 matrix: https://docs.expo.dev/versions/v57.0.0/
- Expo runtime compatibility: https://docs.expo.dev/eas-update/runtime-versions/
- Kotlin Multiplatform platform stability: https://kotlinlang.org/docs/multiplatform/supported-platforms.html
- Kotlin Multiplatform overview: https://kotlinlang.org/docs/multiplatform/kmp-overview.html
- Kotlin/iOS integration: https://kotlinlang.org/docs/multiplatform-ios-integration-overview.html
- Kotlin Multiplatform compatibility: https://kotlinlang.org/docs/multiplatform/multiplatform-compatibility-guide.html
- Compose Multiplatform platform behavior: https://kotlinlang.org/docs/multiplatform/compose-platform-specifics.html
- Compose Multiplatform compatibility/versioning: https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html
- Compose Multiplatform Android-only/device API boundary: https://kotlinlang.org/docs/multiplatform/compose-android-only-components.html
- Apple background execution evidence and Android background/backup evidence remain recorded in DEBATE-002.

Evidence-level observations:

- Flutter officially supports current Android/iOS deployment and exposes platform channels/plugins. Its official
  architecture material discusses offline-first repositories. Kavriva still owns sync, recall and migration semantics.
- React Native exposes typed native modules/components and platform-specific code. Its official release policy has a
  regular cadence and a limited active-support window, so upgrades are a recurring operating cost.
- Expo Go is not a production boundary for Kavriva. Expo's own guidance positions development builds as the route for
  arbitrary native libraries/configuration; native changes require rebuilding the native app.
- Expo runtime versions express native/update compatibility, but DEBATE-005 has not approved EAS Update or any OTA
  authority. Runtime compatibility is not proof of content safety, provenance, current eligibility or recall.
- Core Kotlin Multiplatform and Compose Multiplatform for Android/iOS are documented as stable. This removes an old
  maturity objection but does not prove Kavriva accessibility, lifecycle fit, staffing or lower total cost.
- Fully native implementation has the most direct platform surface but duplicates much of the product delivery and
  parity burden. It is a control/reference, not automatically the safest whole-system outcome.

Version snapshot, used only to expose maintenance and device-floor consequences:

| Family | Exact framework snapshot | Framework floor / architecture evidence | Toolchain, CI and cadence evidence | Product decision |
|---|---|---|---|---|
| Flutter | 3.47.2, retrieved 2026-09-17 | Official table distinguishes supported, CI-tested and unsupported combinations; mobile support lists Android API 24+ and iOS 15+ for the documented architectures | Flutter/Dart, Xcode/Gradle and plugin upgrades remain recurring work | `HELD`: Kavriva device/OS floor unknown |
| React Native | 0.87 stable | Framework release, not a Kavriva OS-floor decision | Node 22.13+, Kotlin 2.0+, AGP 9 and compile SDK 37 in the 0.87 release; current releases page states a latest-three-minor maintenance commitment | `HELD`: product floor and upgrade capacity unknown |
| Expo stable line | SDK 57 / RN 0.86 | Android 7+, iOS 16.4+ in the version-pinned SDK 57 table | SDK/RN/native-module/Xcode alignment; SDK 58 is beta at review time and is excluded from the production comparison | `HELD`: target users and upgrade capacity unknown |
| KMP core | Current stability table, retrieved 2026-09-17 | Android/iOS code sharing documented stable | Kotlin/KMP Gradle plugin, Gradle, AGP, Xcode and Swift integration matrix | `HELD`: product floor and team/toolchain capacity unknown |
| Compose Multiplatform | 1.12.0 | Android API 21+, iOS 14+, 64-bit only; UI stability does not cover device APIs | Kotlin/K2, Compose compiler/plugin, Gradle, AGP, JDK, Xcode and third-party library alignment | `HELD`: product floor, libraries and iOS evidence unknown |
| Full native | Platform SDK/project settings | Product selects deployment targets subject to API/library/store requirements | Two native toolchains, CI/signing and release paths | `HELD`: product floor and dual-team capacity unknown |

These numbers will change. The final ADR must bind an approved OS/device support policy and a framework/toolchain
upgrade window instead of copying this research snapshot as a permanent product promise.

Terminology is not interchangeable: `product-supported` is Kavriva's approved device promise; `framework-supported`
is a vendor/framework statement; `CI-tested` is the subset exercised by that framework's automation; `build-tool
minimum` is required to compile; `store-accepted` is the current Apple/Google submission rule; `team-maintained` means
Kavriva has accountable capacity to patch and upgrade. A candidate passes only against the product-supported policy,
and that policy is still open.

## 5. Mandatory Gates

A candidate is ineligible even if attractive elsewhere when it cannot provide credible no-code evidence for all gates:

| Gate | Required evidence |
|---|---|
| Product safety semantics | Exact states for uncertainty, readiness, interruption, recall, incompatibility and safe recovery; no continue-anyway bypass. |
| Offline correctness | Versioned scoped package, local records, atomic/interrupted-write recovery, bounded eligibility, storage/data controls and foreground reconciliation. |
| Native/lifecycle reach | Maintained route to camera, files/media, notification/deep link, secure local state, background transfer and OS lifecycle handling. |
| Accessibility | Phase-4 matrix for VoiceOver/TalkBack, large text, contrast, reduced motion, focus/order, state announcements, switch/voice control, dexterity and Turkish copy on critical readiness/warning/stop/recovery flows; later real-device evidence is mandatory before implementation acceptance. Framework API availability alone cannot pass the gate. |
| Release compatibility and evidence | Supported OS/client policy; store build/signing path; dependency/native-exception inventory; the complete DEBATE-005 graph binding client/API/schema/content/derived assets/configuration/migration/external resources/offline recovery/release and suspension generations; independent verifier/trust-root matrix; protected incident impact graph. Unknown or partial critical closure is `HELD`. |
| Data continuity | Non-destructive local-to-profile migration, conflict review, schema recovery, backup/restore distrust and preserved core history. |
| Team operability | Named skills/owners for both platforms, native exceptions, CI/signing, upgrades, incidents and accessibility; no responsibility assigned to a nonexistent role. |
| Exit path | Native escape and framework replacement boundaries are understood; no critical truth is trapped in an opaque vendor-only format. |

The gate evaluates the proposed architecture around the framework, not a claim that the framework supplies these
properties automatically.

## 6. Common Kavriva Scenario Dossier

Every candidate receives the same fixture, device/network assumptions and questions. Each answer is labelled
`OFFICIAL EVIDENCE`, `REASONED INFERENCE`, `DEPENDENCY-SPECIFIC` or `UNRESOLVED`.

Every scenario/option cell also records: authoritative starting state; allowed transition; `PASS`, `HELD` or `REJECT`
outcome; user-visible result; required evidence artifact; shared-system obligation versus framework-attributable work;
accountable owner; recovery; residual risk; and later real-device acceptance plan. An unresolved critical cell is
`HELD`, never a zero-cost assumption or a positive score.

The conceptual fixture is fixed now: one selected motorcycle/variant, one active task, compact required guidance plus
complete task-specific recovery, optional heavy media, unrelated catalog content to detect over-download, local
account-light history/photos/private notes, an intentionally conflicting profile dataset, interrupted active work,
current/old/capability-missing clients, and source correction/withdrawal/recall events. Numeric media/history volumes,
OS/device cohorts, storage pressure, network profiles, interruption points and release cadence must be filled once from
the user/business inputs in section 13 and then reused unchanged for all candidates. Until that fixture is frozen, all
comparative outcomes remain `HELD`.

### S1 — First value without an account

The user selects a motorcycle and sees useful local value before creating a profile. Force-close and restart must not
erase the selection. The candidate identifies local storage ownership, protected/sensitive fields, backup behavior and
later migration boundaries.

### S2 — Compact offline task download

The user downloads one task for one motorcycle. Size is shown before transfer; required text/diagrams/warnings and the
complete safe-stop/recovery closure are mandatory, while video/high-resolution media is optional. Test duplicate assets,
cellular preference, partial transfer, cancellation, resume, integrity failure, low storage, eviction and cleanup.

### S3 — Interrupted active physical work

During a maintenance task the user locks the phone, receives a call and later the OS terminates the process. Restart
may restore only the **last durable committed checkpoint**, never the process-kill moment or physical truth. Uncommitted
work is `unknown/partial`; the walkthrough requires atomic checkpoint rules, crash recovery, safe-stop availability and
current-state revalidation before the next physical step. Background execution is an optimization, never a correctness
prerequisite.

### S4 — Recall while offline or dormant

A downloaded guide is suspended after the device went offline. The client cannot know the new recall until it reconnects.
Risk-tiered validity and conservative time/restore rules prevent old data from being silently presented as current;
teaching, history and task-specific safe recovery remain available where allowed.

### S5 — Old client and changed content meaning

An N-1 or unsupported client receives an unknown safety-critical field, configuration or guide capability. It must not
guess. The candidate maps store updates, server/client capability checks, local cached state and safe failure behavior.

### S6 — Local-to-profile migration conflict

Local motorcycle/history data conflicts with an existing profile. The user sees scope and conflicts; cancel/retry is
idempotent; neither side is silently overwritten or deleted; partial success is not displayed as full success.

### S7 — Camera, file and evidence flow

The user denies permission, later grants it, captures a photo, imports a file and uploads on an unstable network. The
candidate identifies native/plugin dependencies, temporary-file cleanup, privacy classification, retry/idempotency and
what happens after process death.

### S8 — Accessibility during a safety-critical step

The Phase-4 matrix covers VoiceOver/TalkBack, largest text, contrast/non-color status, reduced motion, focus/order,
state announcements, switch/voice control and reduced dexterity for an active step, readiness check, warning,
unexpected-state stop and recovery in Turkish. Visual sameness or framework APIs are not accepted as proof. Actual
assistive-technology/device execution is a mandatory later acceptance test and is not claimed during no-code planning.

### S9 — Framework/plugin or OS upgrade

A critical camera/storage/background dependency becomes unsupported while Apple/Google raises an OS or build requirement.
The candidate shows dependency owner, native replacement route, supported-version window, upgrade workload, dual-platform
test scope and release hold/fallback.

### S10 — App, backend, content and configuration mixed rollout

Old and new clients coexist while backend, content, configuration and schema change. Candidate documentation must show
how incompatible combinations are denied/held, how already-downloaded data is treated and why an OTA mechanism, if the
framework has one, remains disabled unless separately approved.

### S11 — Low/mid device resource pressure

Large history, images and an active scoped package are used on agreed low/mid Android and supported iPhone profiles.
The dossier identifies startup/scroll/storage/memory/battery/network risks, media strategy and measurable future
acceptance evidence without inventing benchmark results during planning.

### S12 — Release and incident day

The Phase-4 walkthrough follows the future team through both store build/signing paths, dependency/provenance evidence,
staged release, anomaly pause, affected-version identification and safe correction. It names required people, tools,
future evidence, recurring ceremonies and the hold behavior when a specialist is unavailable; it does not perform or
claim a signed release.

### S13 — Privacy, collaboration and device trust

Private notes, shared-motorcycle records, contributor evidence, ownership transfer, export and access revocation are
walked through before and after an offline interval. Local cache or a restored device must not create new positive
authority. Private, community and official contexts stay distinct; revocation changes future authority without erasing
attribution/history; exported copies are treated as disclosure that cannot be remotely retracted. The candidate names
local classification, key/account binding, device-loss handling and platform-specific secure-storage ownership.

### S14 — Entitlement, evidence and ownership lifecycle

Walk through a subscription/entitlement change during active physical work, contributor/source evidence withdrawal,
community correction/hold, selective motorcycle ownership transfer with known gaps and deletion of one owner's copy.
The required result preserves safe completion/stop/recovery for already-started physical work; re-reviews dependent
claims without silently rewriting history; retains attribution/correction provenance; keeps private notes isolated;
labels transferred history as partial when coverage is incomplete; and never deletes independent evidence merely because
one copy or contributor access is removed.

### S15 — Backup, restore, clone and key loss

Walk through Android/iOS backup restore onto the same and a different trust context, device cloning, key loss/rotation,
schema change and replayed local eligibility metadata. Cache/content, core history, private notes, profile-binding data,
trust/eligibility metadata and key material receive explicit and potentially different backup/exclusion rules. Restored
content or prior authorization enters quarantine/reconciliation and cannot create current positive authority. The dossier
requires data-preserving migration and a user-visible recovery path when protected keys are unavailable.

## 7. Option Comparison

### A — Flutter

**What it simplifies**

- one shared Dart UI implementation can express Kavriva's custom visual/state system consistently;
- official offline-first and architecture guidance provides a coherent starting vocabulary;
- supported platform channels/plugins provide a native escape route;
- one UI stack can reduce routine screen-parity work.

**What remains expensive or risky**

- Dart/Flutter is a distinct team competency and does not share the internal browser UI;
- plugin/native lifecycle exceptions still require Android/iOS knowledge and ownership;
- custom rendering/widgets do not prove native accessibility or convention fit;
- common UI can hide platform-specific failures unless both platforms retain explicit tests;
- framework and plugin upgrades, Xcode/Gradle/store changes and native signing still remain.

**Conditional hypothesis — unproven**

This may fit when AI tasks can keep Dart/Flutter plus bounded Swift/Kotlin exceptions deterministic, Kavriva's custom
cross-platform visual consistency is valuable, and the dependency inventory shows critical native capabilities have
maintained or explicitly escalated routes. That AI-operability evidence is not yet complete.

**Disqualifier**

Do not choose if there is no accountable Dart/Flutter ownership, critical native/plugin gaps have no maintained fallback,
or critical accessibility/lifecycle scenarios can only be asserted rather than evidenced.

### B — React Native + Expo development builds + explicit native boundary

**What it simplifies**

- React/TypeScript skills may overlap with the browser operations team and shared tooling;
- React Native uses platform-backed components and exposes typed native modules/components;
- Expo development builds can simplify standard development/build configuration while allowing native libraries;
- platform-specific files and native modules provide escape routes when one-platform behavior differs.

**What remains expensive or risky**

- language overlap does not make consumer and operator trust domains shareable;
- Expo Go is insufficient as the production architecture; development builds/native rebuilds are part of the real cost;
- React Native, Expo SDK and native-module compatibility create an upgrade/dependency coordination surface;
- the official support cadence requires regular upgrades rather than indefinite version parking;
- local storage, sync, recall and migration remain Kavriva architecture, not React Native/Expo features;
- an available OTA/update service is unapproved and cannot bypass DEBATE-005.

**Conditional hypothesis — unproven**

This may fit when the AI task/tooling path for React/TypeScript is deterministic, scheduled framework/SDK upgrades are
manageable, and critical Swift/Kotlin paths have explicit validation/escalation without collapsing the mobile release
boundary into the web client. Language adjacency is not yet a proven benefit.

**Disqualifier**

Do not choose if the plan depends on Expo Go, assumes no native code/skills will ever be needed, treats OTA as ordinary
deployment authority, or critical modules do not have maintained New-Architecture-compatible/owned alternatives.

### C — KMP shared domain/data logic + native UI

**What it simplifies**

- safety rules, validation, sync/domain logic and selected persistence behavior can be shared while native UI/lifecycle
  remain directly owned per platform;
- sharing can be selective, so an unsuitable platform concern need not be forced into common code;
- native UI gives the strongest direct path to platform convention and accessibility behavior short of full duplication.

**What remains expensive or risky**

- two UI implementations and two platform delivery paths remain;
- Kotlin/Gradle plus Swift/Xcode interoperability, debugging and CI require broader expertise;
- a shared core can become a difficult boundary if platform data/lifecycle semantics are forced into it;
- it does not share the internal browser frontend competency.

**Conditional hypothesis — unproven**

This may fit when the AI execution system can reliably operate both native Android/iOS surfaces, direct platform behavior
is more important than one UI implementation, and shared domain invariants materially outweigh interoperability and
two-UI context/toolchain cost. Current evidence does not establish those conditions.

**Disqualifier**

Do not choose to compensate for missing iOS expertise: native iOS UI, lifecycle, release and accessibility ownership are
still required. Do not choose without a clear rule for what may and may not enter the shared core.

### D — KMP + Compose Multiplatform shared UI

**What it simplifies**

- Kotlin can share domain logic and much of the UI across Android/iOS;
- official documentation now describes Android/iOS Compose targets as stable;
- native interop and embedded native views remain possible.

**What remains expensive or risky**

- stable status is not proof of Kavriva-specific iOS accessibility, native convention or lifecycle behavior;
- the team needs Kotlin/Compose plus iOS/Xcode/native-integration capability;
- permissions, camera/device, file/database and other non-UI capabilities remain outside the shared Compose UI promise
  and need separate multiplatform libraries or platform-specific implementations;
- library availability and platform exceptions require a distinct inventory from KMP-native;
- a shared UI can reproduce the same hidden-divergence risk as other cross-platform UI approaches while offering less
  skill overlap with the browser operations client.

**Current disposition**

Equal dossier candidate, kept separate from KMP-native. Its result is `HELD` pending AI-operability, iOS scenario,
accessibility and dependency evidence. Stability alone does not rank it above or below another option.

### E — Fully native Swift/iOS + Kotlin/Android baseline

**What it simplifies**

- most direct access to platform lifecycle, accessibility, storage, background transfer and new OS APIs;
- lowest framework-abstraction risk and clearest platform-vendor documentation path.

**What remains expensive or risky**

- two complete presentation/application implementations, parity tracking and duplicated tests;
- broader staffing/on-call/CI/signing needs;
- business rules can diverge unless contracts and shared fixtures are unusually disciplined;
- direct native access does not automatically solve offline truth, recall, sync, migration or release governance.

**Current disposition**

Equal dossier candidate and native-behavior/cost reference. Its result is `HELD` pending the same scenario and
AI-operability/TCO evidence; direct platform access is not treated as automatic whole-system safety.

## 8. Evidence Matrix — No Invented Scores

| Option | Strongest documented tendency | Largest Kavriva-specific uncertainty | Current Phase-4 disposition |
|---|---|---|---|
| Flutter | One custom UI stack, official platform integration and offline-first guidance | Team ownership, plugin/native exception load, platform accessibility/lifecycle evidence | `HELD` — equal dossier candidate |
| RN + Expo dev builds | Platform-backed UI, typed native escape and managed tooling options; any React/TS team adjacency is unresolved | Upgrade/module compatibility, native ownership and explicit Expo/OTA boundary | `HELD` — equal dossier candidate |
| KMP-native | Shared invariants with direct native UI/lifecycle | Two UI teams, Swift/Kotlin/Gradle/Xcode operating cost | `HELD` — equal dossier candidate |
| KMP-Compose | Stable Android/iOS shared Kotlin UI with native interop | iOS evidence, team fit, dependency/native exception load | `HELD` — equal dossier candidate, separate from KMP-native |
| Fully native | Direct platform surface and reference ceiling | Duplicate delivery/parity and staffing cost | `HELD` — equal dossier candidate and reference |

No numeric score is assigned because AI-operability/external-dependency capacity, release cadence, target device/OS floor, expected media volume,
native integration inventory and budget are not yet known. Unknown values cannot be converted into a confident ranking.

### Required native/dependency closure

Native reach is baseline work, not a future exception. For camera, files/media, background transfer, notification,
deep link, local database, secure storage/key handling, backup/restore, accessibility and lifecycle, every candidate
must record:

`capability → framework/native boundary → exact dependency/plugin or owned code → accountable primary/backup → OS and
toolchain floor → threading/lifecycle limits → accessibility impact → fallback/replacement → maintainer/support/EOL →
security-response path → release/provenance evidence`.

An unnamed, unsupported or ownerless critical capability is `REJECT`; incomplete noncritical evidence is `HELD`.

### Required exit dossier

“Native escape” is not a framework exit plan. Each option must identify which content/schema/history/provenance/media,
state fixtures, local-storage format, identity/key continuity and platform integrations remain portable; which UI/runtime
artifacts are framework-bound; how data is migrated without loss; how an old client is contained; and what replacement
release/evidence path exists. Exit effort and service interruption belong in TCO.

## 9. Team Capability Gate

`DEC-0029` answers the delivery model: there is no pre-existing human development team. A nontechnical product owner
directs an AI-operated project. Therefore hiring popularity or assumed staff familiarity cannot be used as a framework
advantage. The capability gate becomes an **AI-operability and external-dependency map**:

| Capability | Evidence requested |
|---|---|
| Product/decision owner | User supplies product priorities and risk/cost decisions in nontechnical language; no coding/debugging duty. |
| AI architecture manager | Maintains source of truth, decomposes decisions/tasks, routes context and prevents silent scope expansion. |
| Primary implementation agents | Demonstrated ability to use the chosen official toolchain, contracts, tests and task protocol reproducibly. |
| Independent review agents | Separate first-pass implementation/review contexts and adversarial validation for high-impact work. |
| Native exception ownership | AI route plus explicit external escalation/fallback for camera/files/background/storage/accessibility defects on each platform. |
| Local data/sync | Who owns migrations, conflict rules, backup/restore and interrupted-write recovery. |
| Accessibility | Who tests critical flows with VoiceOver/TalkBack and large text on real devices. |
| Build/release | Who owns Xcode/Gradle, certificates/keys, store accounts, dependency upgrades and incident releases. |
| Test/operations | Device/OS matrix, telemetry/privacy ownership, on-call expectations and release cadence. |
| External dependency | Human-owned accounts, legal/safety/domain attestations, paid services or exceptional specialists that AI cannot legitimately replace. |

AI execution does not turn generated output into evidence. Passing tests, protected release records, device/accessibility
results and independent review remain required. AI also cannot impersonate legal identity, store-account ownership,
qualified domain attestation or another authority that requires a real person/organization.

## 10. 12–24 Month TCO Worksheet

TCO is compared by workload category, not invented currency totals. Each candidate must estimate the same release scope
using local salary/vendor rates and explicitly mark confidence:

1. initial architecture and product delivery;
2. duplicated versus shared screen/state work;
3. local database, sync, migration, recall and recovery design;
4. platform-native exceptions and plugin/module replacement;
5. accessibility and real-device matrix;
6. CI, signing, store submission and staged release;
7. scheduled framework/SDK/Xcode/Gradle/OS upgrades;
   for KMP/Compose this explicitly tracks Kotlin, KMP plugin, Compose/compiler, Gradle, AGP, JDK, Xcode, Swift and
   third-party library compatibility plus rehearsed upgrades and EOL response;
8. security/dependency response and emergency correction;
9. observability, privacy and support/on-call;
10. recruitment, onboarding, training, vendor and knowledge-concentration cost;
11. macOS/build machines, Apple/Google accounts, CI/hosted builds, device lab/farm and test hardware;
12. vendor outage/recovery, safety/content review and release-custodian coverage;
13. paid tooling/service use, including an explicit zero/disabled line for unapproved OTA;
14. migration/exit cost if a critical framework or dependency becomes unsuitable;
15. delay/hold cost when native, accessibility, safety or release expertise is unavailable.

For the approved AI-operated model, line 10 is interpreted as agent/tooling/context-system setup, independent-review
capacity and any unavoidable external specialist/vendor onboarding—not a presumed permanent developer team.

For each line record `owner`, `one-time effort`, `recurring effort`, `external cash cost`, `schedule risk`, `single-person
risk`, `evidence source` and `confidence`. Use low/expected/high ranges only after product budget/capacity and external
service cost inputs exist. A one-codebase claim does not erase native testing, store, accessibility or incident work.

## 11. Decision Hold and Evidence Order

Current evidence does **not** establish a finalist or winner. DEBATE-001's earlier Flutter/RN-first research order is
not a ranking and is superseded here by an equal S1–S15 dossier requirement for all five options. Framework-attributable
work must be separated from offline/domain/backend/content/release work that every option shares.

After the common fixture and AI-operability/TCO inputs are frozen, conditional interpretations may become valid. RN/Expo
may benefit if its complete toolchain, dependency envelope and native exceptions are more deterministic for bounded AI
tasks; Flutter may benefit if one UI system and bounded platform channels produce the smaller verified change surface;
KMP-native/full native may benefit if direct platform behavior outweighs their larger dual-toolchain/context burden;
KMP-Compose may benefit if its Kotlin-centered graph passes iOS/accessibility/dependency evidence. None is proven yet.

The next honest decision is therefore to complete the equal scenario matrices and AI-operability/TCO inputs, then select
the lowest-risk option that passes every mandatory gate. The result must minimize what the nontechnical owner is asked
to debug or decide while preserving independent evidence; framework popularity or human hiring familiarity cannot choose it.

## 12. Rejection Rules

Reject or hold a candidate when any of these occurs:

- a critical Kavriva state is delegated to an unnamed future library or service;
- correctness depends on guaranteed background execution or timely push;
- native platform work is described as unnecessary despite required capabilities;
- accessibility evidence is inferred from visual similarity or generic framework claims;
- an unsupported client guesses unknown safety meaning;
- local/profile migration has no non-destructive conflict and retry model;
- excessive catalog/media download is required for one selected task;
- the candidate requires an OTA authority that has not been separately approved;
- a framework/plugin upgrade can no longer meet store/OS/security requirements and has no owned fallback;
- the required skills, release owner or 12–24 month operating capacity do not exist and no funded acquisition plan exists.

## 13. Remaining User/Business Inputs

Framework selection cannot close until these factual inputs exist:

1. `ANSWERED — DEC-0029`: AI will build and maintain the project under a nontechnical product owner; no existing human development team is assumed.
2. `ANSWERED — DEC-0029`: delivery planning must be optimized for AI task execution, independent AI review and automatic evidence.
3. What delivery horizon and release cadence are expected?
4. What budget/capacity range is available for 12–24 months, including maintenance after first release?
5. Which lowest Android/iOS versions and representative devices must be supported?
6. Which native capabilities are required for the first release versus later?
7. Is dependence on hosted build tooling acceptable if local/provider-independent recovery remains documented?
8. What user, history, image/video and offline-package scale should the cost model use?
9. What privacy, retention, device-loss and collaboration obligations apply to locally held data?
10. What accessibility validation depth and safety/content reviewer availability can the operating team sustain?
11. `CONSTRAINT — DEC-0030`: one young solo owner has limited funds; every cost must be staged as mandatory,
    deferrable, optional or scale-triggered with a free/capped alternative before approval.

The remaining items are not technical trivia. Different answers can legitimately change the recommended framework.

## 14. Independent Review and Judge Result

- Reviewer A — Product Delivery, Scenario Fairness, Team & TCO: `PASS_WITH_CHANGES / NOT ADR-READY`.
- Reviewer B — Mobile Platform, Accessibility, Dependency & Maintenance: `PASS_WITH_CHANGES AS DIRECTION / REJECT AS ADR`.
- Canonical records:
  - `DEBATE-006__REVIEW_A_PRODUCT_DELIVERY_TCO.md`
  - `DEBATE-006__REVIEW_B_MOBILE_PLATFORM_MAINTENANCE.md`

All critical findings were accepted:

1. premature finalist ranking was removed; all five options require equal S1–S15 matrices;
2. Phase-4 scenario work is documentary and cannot claim real-device/build results;
3. restart means last durable committed checkpoint, never exact physical/process state;
4. accessibility APIs/stability do not pass the product gate; a later real-device matrix remains mandatory;
5. native capabilities require exact dependency/owner/toolchain/fallback/EOL/security closure;
6. complete DEBATE-005 release/trust/impact evidence is a mandatory gate;
7. backup/restore/key loss and entitlement/evidence/ownership lifecycle scenarios were added;
8. support terminology, KMP/Compose toolchain TCO and framework exit evidence were strengthened.

### Judge determination

`PASS_WITH_CHANGES — CHANGES INCORPORATED FOR USER WORKING-DIRECTION DECISION; FRAMEWORK SELECTION HELD; NOT ADR-READY`.

The no-code scenario/TCO method is coherent. It does not identify a winning framework because common numeric fixtures,
product device/OS policy, AI-operability/external-dependency capacity and cost inputs do not exist. User approval would approve the evaluation
direction and decision hold, not a framework. Gate 4 -> 5 remains closed.
