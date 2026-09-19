# DEBATE-006 — Candidate Dossier: React Native + Expo Development Builds + Explicit Native Boundary

Status: STRUCTURALLY COMPLETE DRAFT / UNREVIEWED / HELD / NO-CODE  
Date: 2026-09-17  
Candidate: B — React Native + Expo development builds + explicit native boundary

This is a documentary Phase-4 research dossier, not a recommendation, implementation
plan, prototype, benchmark, store submission, or ADR. Sections 1–11 are structurally
present, but the evidence is unreviewed and remains HELD. No build, benchmark, real-device
pass, assistive-technology pass, store submission, or release is claimed.

Evidence labels used below:

- OFFICIAL EVIDENCE: a primary React Native, Expo, Apple, Google, or npm registry source.
- INTERNAL CONTROL: an approved Kavriva control or fixture document.
- REASONED INFERENCE: an explicit implication for Kavriva; it is not a vendor guarantee.
- DEPENDENCY-SPECIFIC: a statement tied to an identified package, plugin, OS, or toolchain.
- UNRESOLVED: a fact that still needs an accountable owner and evidence. It is not a pass and
  it is not a zero-cost assumption.

## 1. Candidate Identity

| Field | Recorded value |
|---|---|
| Candidate family | React Native UI and TypeScript/JavaScript application code, with Expo development builds and an explicit, reviewable Swift/Kotlin/native-module boundary. Expo Go is not the production architecture. |
| Exact evaluated version/snapshot | Expo SDK 57 stable: expo 57.0.22; React Native 0.86.3; React 19.2.3; @expo/cli 57.0.25; expo-dev-client 57.0.19; expo-modules-core 57.0.18; babel-preset-expo 57.0.11. Capability package versions are listed in Section 4. This is a registry snapshot, not a generated lockfile or a build claim. |
| Evidence retrieval date | 2026-09-17, Europe/Istanbul. Dynamic “latest” language is deliberately not used as the evaluated version. |
| Product-supported Android/iOS floor tested against | The equal fixture proposes Android 10 / API 29 (constrained cohort), Android 13+ (main cohort), and iOS 16.4-capable oldest iPhone plus a current generally available iPhone. No branded device has been selected and no real-device test has been run; therefore product-floor evidence is UNRESOLVED. |
| Framework-supported floor | Expo SDK 57 documents Android 7+ and iOS 16.4+. This is a framework floor, not a Kavriva product-support or acceptance pass. Source: [Expo SDK 57 version matrix](https://docs.expo.dev/versions/v57.0.0/). |
| Build-tool/store floor | Expo SDK 57 documents Node 22.13.x, Android compile SDK 36, Android target SDK 36, and Xcode 26.4+. Apple’s current upload guidance requires Xcode 26+ for current distribution work. Google Play’s current requirement at this snapshot is target API 36 for new apps and updates. Exact installed tools, signing custody, and store-account readiness are UNRESOLVED. |
| Support/EOL statement | React Native 0.86 is within the release project’s latest-three-minor support window at the snapshot; React Native 0.87 is a separate active stable line and is not mixed into this Expo SDK 57 candidate. Expo SDK 58 is beta and is excluded. Exact Expo/RN deprecation dates, security-response ownership, and the project’s upgrade SLA are UNRESOLVED. No indefinite support claim is made. |
| Dossier author/reviewer | Codex research agent, using the controlled fixture and primary sources. Independent implementation reviewer, native escalation owner, and acceptance owner are UNRESOLVED. |

### 1.1 Exact snapshot and exclusion boundaries

The candidate is intentionally the stable Expo SDK 57 line, whose documented React Native
line is 0.86. React Native 0.87 was released as a separate stable line, but the evidence
set records Expo’s production path for RN 0.87 as canary at this snapshot [I2]; mixing it into
Expo SDK 57 would invalidate the equality of the comparison. Expo SDK 58 beta, which
advertises an RN 0.88 release candidate, is also excluded from this production snapshot.

The snapshot is exact at package-version level:

| Package/tool | Version recorded | Primary evidence |
|---|---:|---|
| Expo SDK package | expo 57.0.22 | [npm registry: expo 57.0.22](https://registry.npmjs.org/expo/57.0.22) |
| React Native | react-native 0.86.3 | [npm registry: react-native 0.86.3](https://registry.npmjs.org/react-native/0.86.3) |
| React | react 19.2.3 | [npm registry: react 19.2.3](https://registry.npmjs.org/react/19.2.3) |
| Expo CLI | @expo/cli 57.0.25 | [npm registry: @expo/cli 57.0.25](https://registry.npmjs.org/@expo%2fcli/57.0.25) |
| Development build client | expo-dev-client 57.0.19 | [Expo SDK 57 dev-client](https://docs.expo.dev/versions/v57.0.0/sdk/dev-client/) |
| Expo native module core | expo-modules-core 57.0.18 | [npm registry: expo-modules-core 57.0.18](https://registry.npmjs.org/expo-modules-core/57.0.18) |
| Expo Babel preset | babel-preset-expo 57.0.11 | [npm registry: babel-preset-expo 57.0.11](https://registry.npmjs.org/babel-preset-expo/57.0.11) |
| Node.js | 22.13.x | [Expo SDK 57 version matrix](https://docs.expo.dev/versions/v57.0.0/) |
| Android build | compile SDK 36; target SDK 36 | [Expo SDK 57 version matrix](https://docs.expo.dev/versions/v57.0.0/) |
| iOS build | Xcode 26.4+ in the Expo SDK 57 matrix | [Expo SDK 57 version matrix](https://docs.expo.dev/versions/v57.0.0/) |

The Expo SDK 57 [changelog](https://expo.dev/changelog/sdk-57) records the React Native
0.86.3 patch line in the stable SDK 57 maintenance updates. That source does not make
React Native 0.87 part of this candidate.

The final package manager lockfile, all transitive versions and hashes, generated native
projects, config-plugin resolution, SBOM, signing provenance, and reproducible build
evidence are UNRESOLVED. The exact snapshot must not be represented as if those artifacts
already existed.

### 1.2 Primary-source key

The following sources are used in Sections 1–4. External technical claims are restricted
to these official or primary sources:

- O1 — [Expo SDK 57 version matrix](https://docs.expo.dev/versions/v57.0.0/).
- O2 — [Expo development-build introduction](https://docs.expo.dev/develop/development-builds/introduction/).
- O3 — [Expo development-build FAQ](https://docs.expo.dev/develop/development-builds/faq/), [use development builds](https://docs.expo.dev/develop/development-builds/use-development-builds/), [customizing native projects](https://docs.expo.dev/workflow/customizing/), and [Expo workflow overview](https://docs.expo.dev/workflow/overview/).
- O4 — [Expo Camera SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/camera/), [DocumentPicker SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/document-picker/), and [ImagePicker SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/imagepicker/).
- O5 — [Expo SDK 57 FileSystem](https://docs.expo.dev/versions/v57.0.0/sdk/filesystem/).
- O6 — [Expo SDK 57 SecureStore](https://docs.expo.dev/versions/v57.0.0/sdk/securestore/).
- O7 — [Expo SQLite SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/sqlite/).
- O8 — [Expo Notifications SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/notifications/), [BackgroundTask SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/background-task/), and [TaskManager SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/task-manager/).
- O9 — [Expo Sharing SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/sharing/) and [Expo Linking SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/linking/).
- O10 — React Native [Turbo Native Modules](https://reactnative.dev/docs/turbo-native-modules-introduction), [Accessibility](https://reactnative.dev/docs/accessibility), [Platform-specific code](https://reactnative.dev/docs/platform-specific-code), [AppState](https://reactnative.dev/docs/appstate), and [Headless JS for Android](https://reactnative.dev/docs/headless-js-android).
- O11 — React Native [release overview](https://reactnative.dev/releases/), [versioning policy](https://reactnative.dev/docs/versioning-policy), and [0.87 release](https://reactnative.dev/blog/2026/08/11/react-native-0.87).
- O12 — Apple [Developer Program enrollment](https://developer.apple.com/programs/enroll/) and [App Store Connect build upload](https://developer.apple.com/help/app-store-connect/manage-builds/upload-builds).
- O13 — Google Play [registration fee and account requirements](https://support.google.com/googleplay/android-developer/answer/14659200?hl=en) and Android [target API requirements](https://developer.android.com/google/play/requirements/target-sdk).
- O14 — exact package metadata in the [official npm registry](https://registry.npmjs.org/), linked per package above and in Section 4.
- I1 — [DEC-0031](../../00_CONTROL/DECISION_LOG.md) and [DEBATE-006 common fixture and operating assumptions](DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md).
- I2 — [DEBATE-006 mobile technology evidence, team and TCO](DEBATE-006__MOBILE_TECHNOLOGY_EVIDENCE_TEAM_TCO.md).
- I3 — [DEBATE-006 controlled candidate dossier template](DEBATE-006__CANDIDATE_DOSSIER_TEMPLATE.md).
- I4 — [DEBATE-005 software, content, supply-chain and release governance](DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md).

## 2. Fixed Inputs

This candidate uses the approved common comparison fixture without relaxation or
candidate-specific constants. The fixture is controlled by DEC-0031 and I1. A required
change to a constant reopens one revision for all five candidates; it is not changed in
this dossier.

### 2.1 Product, horizon and release cadence

- The product surface is consumer mobile on Android and iOS plus a browser-based Internal
  Operations surface. The mobile candidate does not absorb the browser’s trust domain.
- Both stores are planned, but not necessarily simultaneously. The horizon is first
  release plus 24 months.
- The planned cadence is four release windows per year, with safety correction as needed.
  Store, binary, web, backend, database, content, configuration, and emergency authorities
  remain distinct under I4. No framework OTA mechanism is approved.

### 2.2 Equal MAU workload

The following arithmetic only translates the frozen fixture into monthly transfer volumes;
it is not a price estimate and does not include retries, backup copies, or a legal retention
promise. Storage and outbound are tracked separately.

| MAU tier | Required compact transfers/month | Required transfer ceiling | Optional media/month | User-photo uploads/month |
|---:|---:|---:|---:|---:|
| 1,000 | 2,000 transfers; up to 24,000 MB (about 24 GB decimal) | 12 MB each | 100 users × 100 MB = 10,000 MB (about 10 GB) | 500 × 3 MB = 1,500 MB (about 1.5 GB) |
| 10,000 | 20,000 transfers; up to 240,000 MB (about 240 GB) | 12 MB each | 1,000 × 100 MB = 100,000 MB (about 100 GB) | 5,000 × 3 MB = 15,000 MB (about 15 GB) |
| 50,000 | 100,000 transfers; up to 1,200,000 MB (about 1.2 TB) | 12 MB each | 5,000 × 100 MB = 500,000 MB (about 500 GB) | 25,000 × 3 MB = 75,000 MB (about 75 GB) |

The fixture defines two compact task-package transfers per MAU per month, optional media
for 10% of MAU at 100 MB average transfer, and 0.5 user photos per MAU at 3 MB average
upload. The 24-month horizon is applied to the same workload accounting in later sections;
it must not be converted into provider pricing without current verified price and cap
evidence.

### 2.3 Device, network and interruption cohorts

- Constrained Android: Android 10 / API 29, 64-bit, 4 GB RAM, 64 GB storage, 2 GB free.
- Main Android: Android 13 or newer, 6 GB RAM, 128 GB storage.
- Oldest iPhone cohort: iOS 16.4-capable. Current iPhone cohort: generally available
  current standard non-Pro device.
- Exact branded devices, OS patch levels, purchase/borrow status, and tester population
  are UNRESOLVED. Framework documentation or an emulator is not a device pass.
- Network profiles are stable Wi-Fi at 50 Mbps, cellular at 10 Mbps, and constrained
  network at 1 Mbps / 300 ms / 5% packet loss. Loss may occur during transfer and sync.
- The interruption fixture includes 72 hours offline; background and locked states;
  incoming call; process kill and restart; clock change; and restore before reconnect.

### 2.4 Task package and local stress fixture

- One motorcycle/variant and one active task are in scope.
- Required task content is text, warnings, diagrams, and a complete safe-stop/recovery
  closure. The required compact package has a maximum transfer target of 12 MB.
- Optional high-resolution media is separate and may be up to 150 MB. The UI must show
  size before transfer. An unrelated 2 GB catalog is present to detect default
  over-download and must not be downloaded by default.
- Offline cache target is 250 MB excluding user photos and history. A transfer larger than
  25 MB over cellular requires an explicit user choice.
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
- The mobile client cannot become the authority for safety content, recall state,
  entitlement, identity, or ownership. Those authorities must be represented by explicit
  server/operations contracts and release provenance.
- AI may implement, review, or validate bounded work, but it cannot be the automatic
  authority for safety content. Real devices, assistive technology, qualified safety
  review, store accounts, and legal/tax/payment authorities are external obligations.

### 2.6 Approved cost constants and no-cost assumptions

The following are controlled fixture constants, not a candidate price quote:

- Planning has no incremental spend assumption for the comparison stage.
- Development preparation may use local/free/open-source paths or a capped free tier only
  if caps, alerts, export, and exit are evidenced.
- Google Play Console registration is USD 25 one time. Apple Developer Program membership
  is USD 99 per membership year. The approved 24-month store-only baseline is therefore
  USD 124–223 depending on whether one or two Apple membership payments fall in the
  horizon, before tax and currency conversion.
- Device access is preferably borrowed or otherwise controlled; purchase and hosted-build
  amounts remain UNRESOLVED.
- No unlisted subscription, hosted build, messaging provider, analytics provider, or OTA
  service is pre-approved. A free label never means zero cost; overage, caps, lock-in,
  export, and exit must be evidenced.

Primary evidence for the store constants is Apple O12 and Google O13. Candidate-specific
infrastructure prices are intentionally not invented here.

## 3. Candidate Architecture Boundary

This is a boundary description only. It assigns responsibilities and evidence obligations;
it does not claim that any layer or adapter has been implemented.

### 3.1 Surface and UI ownership

- The consumer mobile UI is React Native with TypeScript/JavaScript application logic
  inside an Expo development build. Expo Go is excluded because its fixed native library
  set cannot validate the native dependencies required by a production app (O2, O3).
- React Native platform-backed components provide the default UI. Platform differences
  are explicit through platform-specific files or Platform selection, not hidden behind
  a claim of visual sameness (O10).
- The browser Internal Operations surface remains a separate client and trust boundary.
  Any shared TypeScript vocabulary is a possible tooling overlap only; it does not merge
  consumer authorization, content publication, or release authority.
- Turkish critical flows, warning, unexpected-state stop, and safe recovery copy/layout
  remain product and accessibility truth from Phase 3. Exact design acceptance artifacts
  are UNRESOLVED.

### 3.2 Domain, data and authority ownership

- Domain state, safety-step state, validation, conflict rules, entitlement decisions,
  content capability checks, recall validity, migration rules, and sync/reconciliation
  are Kavriva application/domain responsibilities. React Native and Expo do not supply
  these semantics.
- A future bounded implementation should keep portable domain contracts and adapters
  separate from React rendering and native APIs. The source of truth for official
  content, correction/withdrawal/recall, profile authority, ownership, and entitlement
  must be an explicit Internal Operations/API contract.
- Local data may support account-light first value, offline work, history, photos, notes,
  and pending operations, but local presence never creates current authority. Server
  revalidation and capability/version checks are required before an authority-sensitive
  step.

### 3.3 Local persistence, encryption, keys, migration and backup

- expo-sqlite 57.0.3 is the candidate local database path. Its documented persistence
  across restarts does not provide Kavriva’s sync, conflict, recall, migration, or
  evidence-provenance semantics. Schema versioning, durable checkpoints, transaction
  boundaries, migration journal, backup policy, and recovery UI are app-owned.
- expo-secure-store 57.0.4 is limited to small protected values such as key references
  or device-binding material. The official documentation describes Android Keystore-backed
  encrypted preferences and iOS Keychain storage, but also documents backup/uninstall,
  biometric invalidation, and restore limitations. It is not a general database or a
  single source of truth.
- The exact at-rest encryption design for database/files, key hierarchy and rotation,
  account re-authentication, Android backup exclusion, iOS restore behavior, key-loss
  recovery, and data retention are UNRESOLVED. This dossier does not imply that
  expo-sqlite encrypts the database.
- A future migration must preserve history and provenance, quarantine restored or
  replayed authority metadata, and give the user a visible recovery path when a protected
  key is unavailable. A one-way data migration cannot be “rolled back” by reverting the
  binary.

### 3.4 Offline package, media and transfer boundary

- expo-file-system 57.0.7 is a file-transfer and local-file primitive. The documented
  modern API supports progress, abort/cancel, idempotent downloads, and local file
  management. It does not implement Kavriva’s package manifest, required-versus-optional
  media policy, hash/signature trust, safe recall state, eviction rules, or atomic
  old/new commit.
- A future package adapter must own a durable manifest containing content identity,
  version/capability, safety status, provenance, integrity result, transfer checkpoint,
  and cleanup decision. Required content cannot be silently evicted or presented as
  current after an integrity, recall, or compatibility failure.
- Temporary space must be reserved for old plus new data and verification. A partial,
  canceled, corrupt, or process-killed transfer must be visible as incomplete and
  recoverable, never as a complete package.
- User photos and evidence media are separate from the compact required package and
  follow their own privacy, upload, retry, and retention rules.

### 3.5 Camera, file import, sharing and media boundary

- Camera capture uses expo-camera 57.0.5; gallery/photo selection may use
  expo-image-picker 57.0.18; system file import uses expo-document-picker 57.0.2.
  Permission configuration is native build/config-plugin work. Camera preview lifecycle,
  temporary-file ownership, metadata stripping/classification, and process-death
  recovery remain app-owned.
- User-visible export/share uses expo-sharing 57.0.20 and the system file/share surface.
  Export classification, disclosure, revocation limits, and whether a file can be
  re-imported are product/privacy rules, not framework guarantees.
- If permission is denied or a platform cannot provide the requested capability, the
  UI must expose a safe manual/no-media path or hold the step; it cannot silently claim
  evidence exists.

### 3.6 Notifications, links and background execution boundary

- expo-notifications 57.0.19 can schedule/present/respond to notifications in a
  development build. Android 13 notification permission/channel work and iOS background
  modes are native configuration. Remote push requires an external delivery/account
  decision that is not selected here. Push is not timely safety authority.
- expo-linking 57.0.10 can handle deep links, but every link must re-check current
  authentication, entitlement, content capability, recall state, and ownership before
  showing an authority-sensitive surface.
- expo-background-task 57.0.18 and expo-task-manager 57.0.18 use OS schedulers and
  document deferrable execution. Foreground reconciliation remains the correctness path.
  A React Native Headless JS task or an Expo background task may optimize refresh, but
  neither is a prerequisite for safe active-work recovery.

### 3.7 Explicit native boundary and build configuration

- Development builds include expo-dev-client and permit native libraries/configuration
  not present in Expo Go. Any native library, permission, config-plugin, SDK, or native
  code change requires a new native build; a JavaScript reload does not close that
  boundary (O2, O3).
- Expo config plugins and prebuild are the intended configuration path. Direct edits to
  generated native projects can be overwritten by prebuild and therefore require
  explicit ownership and regeneration evidence (O3).
- When an Expo package is insufficient, the boundary is an Expo Modules API module
  implemented in Swift/Kotlin or a typed React Native Turbo Native Module. The native
  spec, generated code, thread/lifecycle contract, permission surface, accessibility
  behavior, fallback, maintenance owner, and release provenance must be named before
  that module is accepted. “A future plugin” without those fields is HELD.
- No custom native code is claimed in this partial dossier. The need for native skill or
  escalation is explicit and remains an owner/capacity question.

### 3.8 Accessibility boundary

- React Native documents accessibility labels, hints, roles, state, live-region/focus
  behavior, and VoiceOver/TalkBack integration. Those APIs are implementation affordances,
  not evidence that Kavriva’s Turkish warning, stop, active-step, and recovery flows work.
- Platform-specific focus order, announcement timing, dynamic type/reflow, contrast,
  reduced motion, switch/voice control, and touch target behavior require explicit
  platform work and later execution on real iOS and Android devices with VoiceOver and
  TalkBack. Simulator/API availability is not an acceptance pass.
- Accessibility semantics must stay with the domain state and content classification:
  an announcement must not turn stale, revoked, or unknown content into current authority.

### 3.9 Store signing, release and incident boundary

- Local Android Studio/Gradle and Xcode paths are documented options. Expo also documents
  hosted EAS build paths, but EAS account, quota, billing, artifact retention, host
  availability, and exit evidence are UNRESOLVED and not pre-approved.
- Apple and Google store accounts, legal identity, signing keys, tester populations,
  staged rollout, incident pause, and final publication authority belong to the owner and
  external store authorities. The app team must produce an immutable exact artifact,
  dependency lock, SBOM, provenance, and independent verification before release.
- The release graph keeps binary, web, backend, database, content, configuration, and
  emergency suspension authority distinct. Rollback is allowed only to a still-safe,
  compatible artifact. If schema/data migration cannot be safely reversed, recovery is
  forward migration plus a user-visible hold path.
- OTA/code delivery is excluded. expo-updates is not part of this candidate closure and
  cannot be used to bypass store review, binary provenance, safety correction, or
  DEBATE-005 controls. Expo runtime-version compatibility is only a technical
  compatibility guard, not content provenance or recall authority.

### 3.10 Internal Operations, API and content contract boundary

- Internal Operations owns controlled content intake, safety review, correction/withdrawal/
  recall state, capability metadata, provenance, and publication decisions. The mobile
  client consumes a versioned and classed contract; it does not publish official safety
  truth from local state.
- API/authentication, profile ownership, sync, conflict resolution, entitlement, audit
  history, media storage, deletion, and notification delivery are external/product
  architecture choices. No provider, paid service, or backend schema is selected in this
  partial candidate dossier.
- Private, shared, community, and official classification must be present in the data and
  export contracts. A stale or restored local cache is a candidate input to quarantine
  and reconciliation, never a positive authority.

### 3.11 Portable truth and framework-exit boundary

The following must survive replacement of React Native/Expo:

- content, task, motorcycle, profile, history, note, photo, operation, entitlement,
  correction, withdrawal, recall, and ownership schemas;
- event/history provenance, source attribution, capability/compatibility fixtures, and
  the compact/offline-package acceptance fixtures;
- original media and user-visible exports, with privacy classification and disclosure
  history;
- account identifiers, re-authentication/ownership mapping, and a documented protected
  key recovery policy (not an unportable export of platform key material);
- design tokens, Turkish copy, safety semantics, accessibility intent, and acceptance
  oracles;
- API/content contracts, dependency policy, SBOM/provenance records, and migration
  fixtures.

The following are framework/platform-bound and must be isolated behind adapters:

- React Native component implementation and platform-specific files;
- Expo config plugins, generated Android/iOS projects, and Expo package APIs;
- Swift/Kotlin modules, Turbo Native Module codegen, platform permissions, signing
  configuration, and store packaging.

The intended replacement route is a staged second client against the same portable
contracts: preserve the old client while the replacement reads and verifies the same
schemas/fixtures, transfer user state through an explicit migration, stage both
platform releases, and close the old path only after acceptance evidence. Exact
migration tooling, duration, capacity, and cost are UNRESOLVED and are not a promise.

## 4. Native and Dependency Closure

Every critical row is HELD unless the exact dependency/configuration, native behavior,
owner, fallback, security/EOL handling, and release provenance are all evidenced. Version
numbers below are the exact candidate snapshot; the final lockfile, transitive graph,
native generated files, and device evidence do not yet exist.

| Capability | Built-in/framework path | Dependency/plugin | Native code/skill required | Lifecycle/threading constraints | Accessibility impact | Fallback/replacement | EOL/security owner | Status |
|---|---|---|---|---|---|---|---|---|
| Base mobile UI and platform exceptions | React Native platform-backed components; Platform and .ios/.android file boundaries | react-native 0.86.3; expo 57.0.22; react 19.2.3; @expo/cli 57.0.25; [RN platform-specific code](https://reactnative.dev/docs/platform-specific-code) | TypeScript/React implementation plus Android/iOS review for exceptions; no native code is claimed in this draft | UI thread/render lifecycle; AppState is only a signal and must not be treated as persistence | Labels, hints, roles, state and focus must map to Turkish critical flows | Keep a common safe-stop/read-only path; hold a platform-specific capability with no safe equivalent | RN/Expo support owner and dependency security response are UNRESOLVED; lockfile/SBOM/provenance required | HELD |
| Native module/configuration boundary | Expo development build, config plugins, prebuild, explicit custom module boundary | expo-dev-client 57.0.19; expo-modules-core 57.0.18; [Expo customizing](https://docs.expo.dev/workflow/customizing/) | Swift/Kotlin or typed Turbo Native Module skill when an Expo module is insufficient | Native/config changes require rebuild; generated projects may be overwritten by prebuild | Native controls, permissions, focus, announcements and error states need platform review | Use a maintained Expo/RN module or a safe blocked/manual path; unnamed plugin is not accepted | Named native maintainer, upgrade owner, and security contact UNRESOLVED | HELD |
| Local database and migration | App-owned local schema, checkpoint and migration adapter | expo-sqlite 57.0.3; [Expo SQLite SDK 57](https://docs.expo.dev/versions/v57.0.0/sdk/sqlite/) | Database migration and recovery skill; exact encryption/key design is not supplied by the package | Persistence across restart is documented; schema migration and interrupted transaction recovery are app-owned | Errors, stale/unknown states, conflicts and recovery need accessible announcements | Read-only safe hold and server/profile recovery; no silent reset or overwrite | Database schema/key owner, backup policy, and security review UNRESOLVED | HELD |
| Protected local secrets and device binding | Platform secure storage adapter; never a safety/entitlement authority | expo-secure-store 57.0.4; [Expo SDK 57 SecureStore](https://docs.expo.dev/versions/v57.0.0/sdk/securestore/) | Keychain/Keystore, backup exclusion, biometric invalidation, rotation and re-auth review | Small values only; Android uninstall/restore and iOS persistence behavior require explicit policy; key invalidation can make data unavailable | Key-loss/re-auth/recovery states must be perceivable and actionable | Quarantine local authority metadata; re-authenticate or use account recovery; never mint authority from a clone | Key/account owner and platform security reviewer UNRESOLVED | HELD |
| Camera capture and photo selection | Native permission and camera/gallery surface | expo-camera 57.0.5; expo-image-picker 57.0.18; [Camera](https://docs.expo.dev/versions/v57.0.0/sdk/camera/) and [ImagePicker](https://docs.expo.dev/versions/v57.0.0/sdk/imagepicker/) | Config-plugin permission work and real iOS/Android camera lifecycle review | Permission denial/grant, only-one-preview behavior, app-cache capture, process death and temporary files | Permission prompts, capture state, errors and evidence classification need accessible Turkish output | Manual file import or continue without media with a visible limitation; hold evidence-dependent step | Native media/privacy owner and package security/EOL owner UNRESOLVED | HELD |
| System file import | OS document picker and app-owned copy/classification | expo-document-picker 57.0.2; [DocumentPicker](https://docs.expo.dev/versions/v57.0.0/sdk/document-picker/) | Config-plugin and content-URI/document-permission handling | URI permission, copy failure, process death, duplicate import and temporary cleanup | Picker result, unsupported file, retry and classification must be announced | Retry or manual supported format; do not present an unverified import | File/privacy owner and dependency security owner UNRESOLVED | HELD |
| Scoped package/media transfer | App-owned manifest/checkpoint/integrity layer over local file APIs | expo-file-system 57.0.7; [Expo SDK 57 FileSystem](https://docs.expo.dev/versions/v57.0.0/sdk/filesystem/) | Transfer/recovery implementation plus storage-pressure testing | Modern API documents progress, abort/cancel and idempotent download; resume semantics, hash/signature, atomic commit and eviction rules remain app-owned | Size, progress, pause/cancel, integrity failure and safe hold must be accessible | Retry from verified checkpoint; retain last safe package; block corrupt/stale package | Content/package integrity owner, storage security owner and EOL owner UNRESOLVED | HELD |
| Notifications | Local scheduling/presentation and response surface | expo-notifications 57.0.19; [Notifications](https://docs.expo.dev/versions/v57.0.0/sdk/notifications/) | Android 13 channels/permission and iOS background-mode configuration; remote provider skill if later approved | Remote push is not timely or guaranteed; background notification/task behavior is OS-controlled | Notification permission, content, action, and deep-link destination need AT review | In-app status and foreground reconciliation; never rely on push for safety correctness | Store account, delivery provider, privacy/security and package owner UNRESOLVED | HELD |
| Deep links | Link parse/router plus current authorization recheck | expo-linking 57.0.10; [Linking](https://docs.expo.dev/versions/v57.0.0/sdk/linking/) | Associated-domain/app-link configuration and security review | Link may arrive cold/background; current auth, entitlement, capability and recall must be rechecked | Focus must land on the permitted destination or an accessible hold/re-auth message | Open safe home/read-only state; require re-authentication | Link/identity security owner and store configuration owner UNRESOLVED | HELD |
| Background refresh/reconciliation | Foreground correctness path; OS scheduler only an optimization | expo-background-task 57.0.18; expo-task-manager 57.0.18; [BackgroundTask](https://docs.expo.dev/versions/v57.0.0/sdk/background-task/) and [TaskManager](https://docs.expo.dev/versions/v57.0.0/sdk/task-manager/) | Native scheduler/configuration and lifecycle testing; no continuous correctness claim | WorkManager/BGTaskScheduler are deferrable; task registration/retry and process limits are OS-controlled | Deferred/failed work and stale state need accessible status | Foreground reconciliation on next open; safe stale/unknown hold | Background-task package/OS owner and security reviewer UNRESOLVED | HELD |
| User-visible export/share | Local URI share/system chooser | expo-sharing 57.0.20; [Sharing](https://docs.expo.dev/versions/v57.0.0/sdk/sharing/) | Share-sheet, URI lifetime and disclosure/classification review | Export copy persists outside app and cannot be remotely retracted; process death/cleanup need policy | Share target, classification, warning and completion/failure need AT review | Save a classified local export or hold; no silent disclosure | Privacy/legal owner and package security owner UNRESOLVED | HELD |
| Custom native escape route | Explicit adapter only when platform-backed path cannot close a requirement | Expo Modules API or React Native Turbo Native Modules; exact module and version UNRESOLVED | Named Swift/Kotlin and Android/iOS reviewer are required | Spec/codegen/build integration, main/background thread, lifecycle, permissions and failure semantics must be documented | Native UI/announcement/focus behavior requires platform AT evidence | Replace with maintained module or block the capability; no hidden native dependency | Named maintainer, EOL/upgrade and security owner UNRESOLVED | HELD |
| Build, signing and store release | Local Android Studio/Gradle and Xcode; hosted build is optional | @expo/cli 57.0.25; Node 22.13.x; Expo prebuild/config plugins; exact Gradle/Xcode patch and CI provider UNRESOLVED | Android/iOS build, signing, store and SBOM/provenance skill; owner legal identity required | Any native/config/SDK dependency change requires rebuild; staged rollout and incident pause are external controls | Release evidence must include both-platform AT/device results | Local reproducible path where available; hosted path only after cap/cost/export/exit evidence | Signing custody, store owner, CI/artifact security and upgrade owner UNRESOLVED | HELD |
| OTA/code delivery | Explicitly excluded from candidate | expo-updates is not included or approved | No OTA skill is a mitigation | No JS/native bypass of store artifact, review, provenance or safety correction | No inaccessible emergency path is allowed | Store-delivered compatible binary or approved content/config authority only | Release governance owner; introducing OTA would be rejected under I4 | EXCLUDED / N-A |
| Backend/auth/sync/telemetry boundary | No framework default selected; explicit API/provider contracts required | No provider or paid service selected; exact auth, DB, storage, crash and analytics dependencies UNRESOLVED | Backend, privacy, security, operations and migration skill | Server authority, idempotency, conflict, recall, deletion and audit semantics are outside Expo | Client must expose stale/unknown/conflict/permission states | Foreground retry, read-only safe hold, provider replacement through portable contracts | Product/backend owner, privacy/legal, security and incident owner UNRESOLVED | HELD |

### 4.1 Exact registry references for capability packages

These are immutable version URLs in the official npm registry for the package numbers
shown in the closure table. They are registry evidence only; they do not imply that a
lockfile, native build, or security approval exists:

- [expo-camera 57.0.5](https://registry.npmjs.org/expo-camera/57.0.5)
- [expo-document-picker 57.0.2](https://registry.npmjs.org/expo-document-picker/57.0.2)
- [expo-file-system 57.0.7](https://registry.npmjs.org/expo-file-system/57.0.7)
- [expo-image-picker 57.0.18](https://registry.npmjs.org/expo-image-picker/57.0.18)
- [expo-notifications 57.0.19](https://registry.npmjs.org/expo-notifications/57.0.19)
- [expo-secure-store 57.0.4](https://registry.npmjs.org/expo-secure-store/57.0.4)
- [expo-sqlite 57.0.3](https://registry.npmjs.org/expo-sqlite/57.0.3)
- [expo-sharing 57.0.20](https://registry.npmjs.org/expo-sharing/57.0.20)
- [expo-linking 57.0.10](https://registry.npmjs.org/expo-linking/57.0.10)
- [expo-background-task 57.0.18](https://registry.npmjs.org/expo-background-task/57.0.18)
- [expo-task-manager 57.0.18](https://registry.npmjs.org/expo-task-manager/57.0.18)
- [expo-dev-client 57.0.19](https://registry.npmjs.org/expo-dev-client/57.0.19)
- [expo-modules-core 57.0.18](https://registry.npmjs.org/expo-modules-core/57.0.18)

### 4.2 Closure decision for this dossier

The version snapshot and documented escape routes establish a technically plausible
boundary, but they do not close the candidate. The following are still missing for a
future complete dossier:

- generated lockfile with transitive dependency versions, hashes, native permissions,
  config-plugin output, SBOM, and reproducible artifact provenance;
- named primary and backup owners for every native module, package security response,
  EOL/upgrade decision, and fallback;
- final database/file encryption and key/backup/recovery design;
- API/auth/sync/recall/entitlement/content contracts and provider-independent exit path;
- exact Android/iPhone devices, real-device/assistive-technology acceptance, build/signing
  custody, store-account readiness, and specialist capacity;
- cap/alert/export/exit evidence for any CI, hosted build, storage, messaging, telemetry,
  or other paid service.

Accordingly, Section 4 remains evidentiary closure in a STRUCTURALLY COMPLETE DRAFT /
UNREVIEWED / HELD dossier. It does not authorize a framework choice, an Expo account or
EAS purchase, an OTA service, implementation work, or a release.

## 5. Equal S1–S15 Scenario Record

The records below apply the same approved starting states, transitions, failure injections,
and evidence schema to Candidate B. The framework primitives are not treated as proof of
Kavriva domain correctness. Every unresolved critical cell is HELD, never a zero or a
positive score.

### S1 — First value without an account

- authoritative starting state: A fresh mobile install has no account. The user selects one motorcycle/variant and must see useful local value; this local selection has no current entitlement, ownership, or safety authority.
- allowed transition: Selection may persist through force-close and restart, then optionally migrate into a profile through an explicit, idempotent operation. No local cache may mint authority.
- candidate mechanism: React Native UI; expo-sqlite 57.0.3 for the local selection/history adapter; expo-file-system 57.0.7 for bounded cache; expo-secure-store 57.0.4 only for small protected references.
- official evidence: Expo SQLite documents persistence across restarts; SecureStore documents platform secure storage; RN provides the UI and platform boundary (O6, O7, O10).
- reasoned inference: These primitives can hold a local selection, but ownership, migration, backup, encryption, and authority semantics remain app and server responsibilities.
- dependency-specific evidence: The exact candidate package versions are recorded in Sections 1 and 4; no generated lockfile or native build verifies their combined resolution.
- unresolved facts: Local schema, at-rest protection, backup/exclusion rules, migration conflict policy, account contract, exact devices, and Turkish first-value copy are UNRESOLVED.
- user-visible result: After a normal restart, the selected motorcycle and useful local content remain visible with clear account/authority limits. An authority-sensitive action asks for current verification.
- failure/hold behavior: Database/key/restore ambiguity produces a visible read-only or safe hold state; the UI never silently resets, merges, or claims profile ownership.
- recovery path: Retry the local operation or perform a data-preserving migration; later profile migration uses idempotent operation identifiers and an explicit conflict result.
- shared-system obligation: Product, API, identity, entitlement, privacy, retention, and content authorities must define what accountless value is permitted.
- candidate-attributable work: Build the storage adapter, schema/version tests, restart/restore tests, platform error surfaces, and native-build evidence.
- accountable AI/external owner: AI may implement bounded storage/UI work; an independent reviewer, product owner, privacy/legal authority, and native owner must review it.
- required later real-device evidence: Constrained/main Android and oldest/current iPhone; force-close/restart, restore, key-loss, and Turkish assistive-technology paths.
- residual risk: SecureStore restore/key behavior and an unproven local migration can lose continuity or expose stale state even if the UI renders correctly.
- result: HELD

### S2 — Compact offline task download

- authoritative starting state: One selected motorcycle/variant and one authorized task are available; no compact package is trusted locally yet.
- allowed transition: Show size before transfer; download required text, warnings, diagrams, and complete safe-stop/recovery closure up to the 12 MB target; keep optional high-resolution media separate; allow explicit cellular choice above 25 MB, cancel, retry, and cleanup.
- candidate mechanism: expo-file-system 57.0.7 modern file APIs for progress, abort/cancel, idempotent download, and local files; expo-sqlite 57.0.3 for a durable package manifest and checkpoint adapter.
- official evidence: FileSystem documents progress, abort/cancel, idempotent downloads, and file management; Expo development builds are required for native libraries beyond Expo Go (O2, O3, O5).
- reasoned inference: The APIs can support a transfer workflow, but required-content closure, hash/signature trust, byte-resume policy, atomic old/new commit, storage reservation, eviction, and recall validity are not supplied by Expo.
- dependency-specific evidence: FileSystem 57.0.7 and SQLite 57.0.3 are exact snapshot entries; the package documents do not prove Kavriva manifest semantics or package provenance.
- unresolved facts: Hash/signature format and authority, range-resume behavior, free-space policy, package compatibility matrix, optional-media policy, and server endpoint are UNRESOLVED.
- user-visible result: Size, required/optional distinction, progress, cancellation, incomplete/integrity status, and storage/choice warnings are explicit. An incomplete or stale package is not presented as current.
- failure/hold behavior: Partial, corrupt, canceled, or insufficient-space transfer is marked incomplete and held; required safety content is never silently evicted or replaced with optional media.
- recovery path: Retry from a verified checkpoint or restart the package atomically while retaining the last safe package; revalidate on reconnect.
- shared-system obligation: Content authority, package signing/provenance, recall/withdrawal state, capability metadata, storage policy, and privacy classification are shared obligations.
- candidate-attributable work: Implement manifest/checkpoint/atomic-commit adapters, package-size calculation, cache cleanup, and low-storage/network tests.
- accountable AI/external owner: AI implements bounded transfer tasks; content/safety owner, backend owner, security reviewer, and native Android/iOS owner remain external or independent.
- required later real-device evidence: Android constrained/main and iOS cohorts over Wi-Fi, cellular, 1 Mbps/300 ms/loss, cancellation, process death, low space, corrupt package, and 72-hour offline.
- residual risk: A vendor file primitive may appear reliable while a faulty app-owned manifest or integrity rule presents the wrong safety version.
- result: HELD

### S3 — Interrupted active physical work

- authoritative starting state: The user is part-way through an active physical task, with the last durable checkpoint known; the phone may lock, receive an incoming call, lose process, or restart.
- allowed transition: Resume only from the last durable committed checkpoint, expose uncommitted work as unknown/partial, provide safe stop/recovery, and revalidate current state before the next physical step.
- candidate mechanism: RN AppState signals for active/background/inactive awareness; SQLite checkpoint records; foreground reconciliation; Expo background scheduling only as an optimization.
- official evidence: RN AppState documents active/background/inactive and memory-warning signals; Expo BackgroundTask/TaskManager use deferrable OS schedulers; Headless JS requires native code (O8, O10).
- reasoned inference: AppState can trigger a save attempt but cannot prove a durable commit or preserve physical truth at process-kill time. Background execution cannot be a correctness prerequisite.
- dependency-specific evidence: expo-sqlite 57.0.3, expo-background-task 57.0.18, and expo-task-manager 57.0.18 are the recorded paths; no atomic checkpoint implementation exists.
- unresolved facts: Checkpoint state machine, transaction/journal semantics, physical-step oracle, incoming-call behavior, safe-stop copy, and background retry policy are UNRESOLVED.
- user-visible result: Restart shows the last committed step and labels unknown/partial work; the user can stop safely, recover, or revalidate rather than being advanced to an assumed physical state.
- failure/hold behavior: Ambiguous checkpoint, missing package, stale recall, or key error blocks the next physical step and shows a recovery/hold explanation.
- recovery path: Foreground reconciliation, explicit user confirmation where safe, server/current-content revalidation, and a forward migration of any durable record.
- shared-system obligation: Safety state machine, task guidance, recall authority, audit semantics, and qualified safety review are not framework features.
- candidate-attributable work: Define checkpoint boundaries, crash-safe persistence, AppState handling, accessible unknown/partial UI, and dual-platform interruption tests.
- accountable AI/external owner: AI may prepare bounded adapters; safety owner, domain reviewer, native lifecycle reviewer, and product owner must approve the stop/recovery behavior.
- required later real-device evidence: Lock/unlock, incoming call, background, process kill, low-memory/restart, clock change, and interrupted DB write on both Android cohorts and both iPhone cohorts.
- residual risk: OS scheduling and process death remain nondeterministic; a missing or incorrectly committed checkpoint can mislead physical work.
- result: HELD

### S4 — Recall while offline or dormant

- authoritative starting state: A previously downloaded guide is on device; the device is offline or dormant for up to the fixed 72-hour interval, so it cannot know a newly issued recall.
- allowed transition: Reconnect and revalidate before presenting current safety authority; where policy permits, retain teaching/history and task-specific safe-stop recovery while marking validity conservatively.
- candidate mechanism: Local package manifest and validity state over SQLite/FileSystem; foreground reconciliation; local notification only as a convenience, never as recall authority.
- official evidence: FileSystem supports local file handling; Notifications and BackgroundTask document OS-controlled/deferrable execution and do not guarantee timely delivery (O5, O8).
- reasoned inference: The candidate can represent stale/unknown state, but only the content/release authority can decide whether a guide remains usable after recall or clock/restore changes.
- dependency-specific evidence: expo-notifications 57.0.19, expo-background-task 57.0.18, and expo-task-manager 57.0.18 are exact paths; no remote provider is selected.
- unresolved facts: Recall API and signing, risk-tier validity windows, clock-skew/restore policy, dormant notification policy, and allowed teaching/recovery content are UNRESOLVED.
- user-visible result: The user sees stale, unknown, recalled, or current status with a safe-stop/recovery action; no notification absence is represented as “no recall.”
- failure/hold behavior: Failed revalidation, invalid signature, clock anomaly, or unknown capability holds current-safety presentation and leaves only explicitly permitted recovery/teaching material.
- recovery path: Foreground reconnect, package revalidation, approved replacement package, and audit-preserving content transition.
- shared-system obligation: Recall/correction publication, risk classification, server time/authority, notification policy, and safety review belong to Internal Operations/API.
- candidate-attributable work: Implement validity state, reconnect state machine, accessible stale/recall UI, and offline/restore/clock tests.
- accountable AI/external owner: AI handles bounded client work; safety/content authority, backend owner, privacy owner, and platform notification reviewer are required.
- required later real-device evidence: 72-hour offline simulation, dormant/locked behavior, restore before reconnect, clock changes, denied notifications, and reconnect on constrained networks.
- residual risk: A validly stored package can still be medically/physically unsafe if server recall metadata or client fail-closed rules are wrong.
- result: HELD

### S5 — Old client and changed content meaning

- authoritative starting state: An N-1 or unsupported client receives content, configuration, or a safety-critical field/capability it cannot interpret.
- allowed transition: Capability negotiation may select a compatible representation; unknown safety meaning must fail closed and wait for a compatible client or approved fallback.
- candidate mechanism: Versioned API/content manifests and explicit capability headers in app-owned domain code; runtimeVersion may guard native/update compatibility; OTA remains excluded.
- official evidence: Expo runtime versions constrain native/runtime compatibility and native changes require a new build; RN platform-specific boundaries are documented (O3, O10 and [Expo runtime versions](https://docs.expo.dev/eas-update/runtime-versions/)).
- reasoned inference: A runtime guard can prevent an incompatible binary/update pairing, but it cannot decide the safety meaning of a new content field or replace server capability policy.
- dependency-specific evidence: Expo SDK 57/RN 0.86.3 is the fixed snapshot; no expo-updates package or OTA channel is in the closure.
- unresolved facts: Capability matrix, N-1 support window, content fallback, API negotiation, configuration/schema compatibility, and exact fail-closed copy are UNRESOLVED.
- user-visible result: Supported content displays normally; unknown safety content shows a clear update/hold state and a safe-stop/recovery path rather than a guessed interpretation.
- failure/hold behavior: Unknown field, incompatible config, stale local manifest, or unsupported client blocks the affected action and preserves history.
- recovery path: Store-delivered compatible binary, compatible content representation, or reviewed server-side hold; no JS OTA bypass.
- shared-system obligation: API/content schema, capability publication, store release, recall, and compatibility graph are shared release responsibilities.
- candidate-attributable work: Add capability declarations, versioned adapters, unknown-field tests, platform-specific fallback UI, and provenance checks.
- accountable AI/external owner: AI implements bounded parsing/UI; API/content authority, safety reviewer, store owner, and independent release verifier must approve.
- required later real-device evidence: Old/current binaries on constrained/main Android and iOS, mixed rollout, cached old packages, unknown fields, and offline-to-online reconnect.
- residual risk: Capability drift can be hidden by permissive JavaScript parsing; a runtime-compatible app can still be semantically unsafe.
- result: HELD

### S6 — Local-to-profile migration conflict

- authoritative starting state: Account-light local motorcycle/history data exists while an existing profile contains overlapping or conflicting records.
- allowed transition: The user sees scope and conflicts; cancel/retry is idempotent; neither side is silently overwritten/deleted; partial completion is not shown as full success.
- candidate mechanism: SQLite local records plus app-owned operation identifiers and an explicit API migration adapter; SecureStore may hold a protected account reference only.
- official evidence: SQLite documents local persistence and SecureStore documents protected platform storage; neither defines conflict or merge semantics (O6, O7).
- reasoned inference: React Native/Expo can render a conflict flow, but authoritative merge order, audit history, and idempotency must be designed outside the framework.
- dependency-specific evidence: expo-sqlite 57.0.3 and expo-secure-store 57.0.4 are snapshot packages; no backend or identity provider is chosen.
- unresolved facts: Record identity, merge precedence, tombstones, attachment deduplication, conflict UI, API idempotency, audit schema, and retry budget are UNRESOLVED.
- user-visible result: The user sees local/profile scope, conflicts, pending, completed, and partial states with a reversible choice where possible.
- failure/hold behavior: Network loss, duplicate response, auth expiry, or ambiguous server result leaves records pending/held and never labels all data migrated.
- recovery path: Retry by stable operation ID, reconcile server result, retain both provenance paths, and allow cancel without silent deletion.
- shared-system obligation: Profile authority, identity, audit, deletion, conflict policy, and privacy classification are product/backend obligations.
- candidate-attributable work: Implement adapters, conflict state model, accessible diff/choice UI, offline retry, and process-death tests.
- accountable AI/external owner: AI can implement bounded migration tasks; backend/data owner, privacy/legal reviewer, and independent verifier are required.
- required later real-device evidence: Offline migration, packet loss, process kill, duplicated submission, auth expiry, attachments, and restore on both platforms.
- residual risk: A UI that appears idempotent can still duplicate or erase records if the server operation contract is incomplete.
- result: HELD

### S7 — Camera, file and evidence flow

- authoritative starting state: Permission is denied, later granted, then the user captures a photo or imports a file and attempts upload on an unstable network; evidence has an explicit privacy classification.
- allowed transition: Denial is recoverable; granted capture/import may create a pending local evidence item; upload is retryable/idempotent and process death leaves a visible pending/failed state.
- candidate mechanism: expo-camera 57.0.5, expo-image-picker 57.0.18, expo-document-picker 57.0.2, FileSystem 57.0.7, SQLite 57.0.3, and a future app-owned upload adapter.
- official evidence: Camera, ImagePicker, DocumentPicker, and FileSystem document native permission/configuration, local files, progress, cancel, and picker/camera behavior (O4, O5).
- reasoned inference: These packages provide capture/selection primitives, not metadata minimization, evidence provenance, privacy scope, retry idempotency, durable upload, or deletion semantics.
- dependency-specific evidence: Exact package versions and official SDK pages are recorded in Section 4; remote upload/auth/storage dependencies are not selected.
- unresolved facts: Permission config, URI/content ownership, EXIF policy, accepted formats, encryption, upload API, retention, classification, and post-process-death cleanup are UNRESOLVED.
- user-visible result: Permission state, capture/import result, privacy class, pending/uploaded/failed state, and retry choice are explicit; no failed upload is called evidence-complete.
- failure/hold behavior: Denied permission, malformed file, missing URI, duplicate operation, low space, network loss, or process death holds the evidence item with a recovery action.
- recovery path: Grant/retry, re-import, resume by stable operation ID, quarantine malformed data, or continue without media when the task permits.
- shared-system obligation: Privacy classification, source attribution, backend media authority, deletion, audit, and safety evidence review are shared obligations.
- candidate-attributable work: Implement permission state, temporary-file cleanup, manifest/classification adapter, idempotent upload UI, and dual-platform lifecycle tests.
- accountable AI/external owner: AI may build bounded client adapters; privacy/legal, safety/content, backend/storage, and native camera reviewers must own acceptance.
- required later real-device evidence: Permission denial/grant, camera interruption, gallery/document picker, metadata, low storage, process kill, cellular loss, duplicate upload, and Turkish AT.
- residual risk: A locally captured file may be private or untrusted even when the native picker reports success; external copies cannot be remotely retracted.
- result: HELD

### S8 — Accessibility during a safety-critical step

- authoritative starting state: Turkish readiness, warning, unexpected-state stop, active-step, and safe-recovery screens must be usable with VoiceOver, TalkBack, largest text, non-color status, focus/order, announcements, switch/voice control, and reduced dexterity.
- allowed transition: The user can enter, understand, pause/stop, recover, and continue only when the current state is perceivable and actionable through the selected assistive technology.
- candidate mechanism: React Native accessibilityLabel, hint, role, state, live-region/focus APIs plus explicit iOS/Android platform files and native review.
- official evidence: RN documents accessibility properties and VoiceOver/TalkBack integration, and states that actual devices are needed for meaningful VoiceOver testing (O10).
- reasoned inference: API availability makes an implementation route possible; it does not prove Turkish wording, focus order, announcement timing, contrast, reflow, reduced-motion, or platform convention.
- dependency-specific evidence: RN 0.86.3/Expo SDK 57 are snapshot versions; no native accessibility module or design acceptance artifact has been validated.
- unresolved facts: Final Turkish copy, semantic labels, largest-text layout, contrast tokens, reduced-motion policy, custom control behavior, AT device/tester, and acceptance oracle are UNRESOLVED.
- user-visible result: Each safety state has a non-color, readable, announced action and a safe hold/recovery path; no visual-only success is accepted.
- failure/hold behavior: An inaccessible warning, stop, or recovery state blocks candidate acceptance and release; the user is not instructed to continue physical work through an unverified path.
- recovery path: Return to a verified safe-stop state, correct semantics/layout, rerun both AT paths, and preserve the content state.
- shared-system obligation: Phase-3 design truth, Turkish content, safety review, accessibility specialist, and product acceptance are shared obligations.
- candidate-attributable work: Map domain states to RN semantics, isolate platform exceptions, test large text/focus/announcements, and produce repeatable device evidence.
- accountable AI/external owner: AI can prepare bounded accessibility changes; qualified AT testers, product/safety reviewer, and iOS/Android native reviewers must accept them.
- required later real-device evidence: VoiceOver on oldest/current iPhone and TalkBack on constrained/main Android for all listed Turkish flows, including interruptions and stale/unknown states.
- residual risk: A screenshot or simulator pass can conceal a real-device announcement, focus, gesture, or dynamic-type failure.
- result: HELD

### S9 — Framework/plugin or OS upgrade

- authoritative starting state: The exact Expo SDK 57/RN 0.86.3 candidate is in use while a critical package becomes unsupported or Apple/Google raises a build/OS requirement.
- allowed transition: Propose, lock, review, build, and validate a replacement or SDK/toolchain upgrade on both platforms before staged release; hold when evidence or owner is missing.
- candidate mechanism: Versioned package lock, Expo prebuild/config plugins, development-build native rebuild, RN platform boundary, two-platform test matrix, and explicit fallback.
- official evidence: Expo documents native rebuilds for native dependency/config changes; RN documents a continuing release cadence and versioning policy; SDK 57 specifies its toolchain floors (O1, O2, O3, O11).
- reasoned inference: Development builds reduce configuration friction but do not remove native upgrade, compatibility, signing, device, or specialist work.
- dependency-specific evidence: Current closure pins SDK 57 packages; no EOL dates, backup modules, or generated native diff are available.
- unresolved facts: Upgrade cadence/SLA, exact support end dates, plugin compatibility, Xcode/Gradle/Node patches, owner capacity, fallback module, and cost are UNRESOLVED.
- user-visible result: Users stay on a reviewed compatible release or see a clear hold/update state; unsupported behavior is not silently enabled.
- failure/hold behavior: Build failure, native regression, missing AT evidence, security issue, or absent owner pauses release and retains the last safe compatible artifact.
- recovery path: Pin temporarily within support policy, replace with a maintained module, implement an owned native adapter, or pause the affected capability; no unnamed plugin.
- shared-system obligation: Store requirements, security advisories, signing, rollout, incident pause, and release governance are shared obligations.
- candidate-attributable work: Maintain dependency graph/lockfile/SBOM, native diffs, upgrade task pack, fallback adapters, and dual-platform regression evidence.
- accountable AI/external owner: AI can prepare upgrade tasks; named RN/Expo, Android, iOS, security, AT, and release owners are required.
- required later real-device evidence: Every changed native path on constrained/main Android and oldest/current iPhone, plus AT and interrupted-work checks before release.
- residual risk: RN/Expo and native toolchain cadence can consume more scarce capacity than routine TypeScript overlap suggests.
- result: HELD

### S10 — App, backend, content and configuration mixed rollout

- authoritative starting state: Old and new mobile clients coexist while backend, schema, content, configuration, and capability meaning change.
- allowed transition: Each combination is admitted only through an explicit compatibility graph; unknown or incompatible safety semantics are denied/held. Binary delivery remains store-governed.
- candidate mechanism: Versioned API/content manifests and client capabilities, local package validity state, runtimeVersion as a technical compatibility guard, and no OTA.
- official evidence: Expo runtime-version documentation explains native/update compatibility and that native changes require a new build; DEBATE-005 governs separate release authorities (O4, I4).
- reasoned inference: Runtime matching prevents a class of native incompatibility but cannot prove backend/schema/content safety or replace staged release governance.
- dependency-specific evidence: expo-updates is intentionally absent; Expo SDK 57/RN 0.86.3 remains the only evaluated mobile runtime.
- unresolved facts: Compatibility graph, schema migration policy, content fallback, config signing, server capability negotiation, old-client support window, and provider are UNRESOLVED.
- user-visible result: Compatible content works; unsupported client/content/config combinations show a clear update or safe hold with recovery instructions.
- failure/hold behavior: The client blocks the affected operation, preserves safe local history, and never interprets an unknown field or configuration as a default.
- recovery path: Store-delivered binary, server-approved compatible representation, or forward migration after verification; no JavaScript OTA emergency path.
- shared-system obligation: API/schema/content/config authority, publication, recall, and audit provenance belong to Internal Operations/release governance.
- candidate-attributable work: Create capability headers, compatibility tests, migration adapters, stale-cache handling, and binary/runtime provenance checks.
- accountable AI/external owner: AI implements bounded client changes; backend/content/safety, security, store, and independent release verifier own acceptance.
- required later real-device evidence: Mixed old/new binaries, cached packages, offline interval, store staged delivery, config changes, and process restart on both platforms.
- residual risk: A technically compatible runtime can still display semantically changed or withdrawn content if the shared graph is incomplete.
- result: HELD

### S11 — Low/mid device resource pressure

- authoritative starting state: The fixed 3/10 motorcycle, 250/2,000 history, 50/500 photos, 100/1,000 notes, 20/200 pending changes, and 3/30 conflicts are exercised with one active scoped package.
- allowed transition: Required compact content remains usable within the agreed cache/storage strategy; optional catalog/media is bounded, and resource pressure produces visible choices or safe hold.
- candidate mechanism: SQLite local records, FileSystem package/media storage, bounded/paged app-owned views, explicit optional-media transfer, and no default 2 GB catalog download.
- official evidence: Expo SQLite and FileSystem document persistent local data/file operations; the docs do not provide Kavriva memory, battery, startup, cache, or sync budgets (O5, O7).
- reasoned inference: Native primitives permit bounded storage, but RN render/memory behavior, query strategy, image decoding, battery, and network pressure require measurement.
- dependency-specific evidence: expo-sqlite 57.0.3 and expo-file-system 57.0.7 are pinned; no profiling or benchmark artifact exists.
- unresolved facts: Startup/scroll/memory/battery/network thresholds, image strategy, device thermal behavior, cache eviction, DB indexing, and measured budgets are UNRESOLVED.
- user-visible result: The user sees size/storage warnings, loading/error states, optional-media choices, and safe recovery; unrelated content is not silently downloaded.
- failure/hold behavior: Low space, memory pressure, slow transfer, or query failure holds optional work first and preserves required safe-stop content where verified.
- recovery path: Cancel/cleanup verified temporary data, retry foreground, reduce optional media, or present a safe read-only/stop state.
- shared-system obligation: Fixture thresholds, product performance acceptance, content size policy, backend payloads, and device procurement/testing are shared obligations.
- candidate-attributable work: Profile both platforms, bound lists/images/cache, instrument minimal resource signals, and record repeatable evidence without inventing planning benchmarks.
- accountable AI/external owner: AI can prepare profiling tasks; native performance reviewer, product owner, device/tester owner, and safety reviewer are required.
- required later real-device evidence: Constrained Android10/API29, main Android13+, oldest/current iPhone, all normal/stress fixtures, low storage, background/kill, constrained network, and AT.
- residual risk: Shared React/TypeScript code does not guarantee equal memory or lifecycle behavior across Android and iOS.
- result: HELD

### S12 — Release and incident day

- authoritative starting state: A candidate artifact is proposed for the next planned window or an urgent safety/security correction; no signed release is claimed in this dossier.
- allowed transition: Evidence gate → immutable build/signing → independent verification → staged store rollout → monitoring/pause → safe correction/recovery. Missing specialist evidence holds.
- candidate mechanism: Local Android Studio/Gradle and Xcode or a later-approved hosted build; exact lockfile/SBOM/provenance; staged store release; no OTA.
- official evidence: Expo documents local/EAS development-build paths; Apple documents current Xcode/upload requirements; Google documents registration and target API requirements (O2, O12, O13).
- reasoned inference: The candidate has a documented path to a binary, but signing custody, CI reproducibility, artifact retention, store testing, and incident execution remain operational work.
- dependency-specific evidence: @expo/cli 57.0.25, Node 22.13.x, SDK 57 build floor, and native rebuild rule are recorded; no artifact or signed build exists.
- unresolved facts: Mac/host availability, CI/provider/caps, signing keys, legal identity, closed-test population, artifact retention, monitoring, responders, and duration/capacity are UNRESOLVED.
- user-visible result: Users receive only a staged, verified compatible binary/content state; a paused or affected version shows a safe hold/update path.
- failure/hold behavior: Build/sign/upload/provenance/AT/safety failure pauses release; a prior still-safe compatible artifact is retained and no downgrade is attempted after unsafe migration.
- recovery path: Identify affected artifacts, pause rollout, issue a reviewed compatible binary/content correction, reconcile state, and reopen only after evidence.
- shared-system obligation: Release authority, store accounts, incident command, safety review, security response, backend/content/config compatibility, and legal/tax obligations are shared.
- candidate-attributable work: Maintain build recipe, native diffs, dependency lock/SBOM, evidence manifest, staged-release runbook, and incident impact map.
- accountable AI/external owner: AI can prepare artifacts/checklists; legal store-account holder, release verifier, native build owner, safety reviewer, and incident commander are external/independent.
- required later real-device evidence: Signed builds installed on both platforms, staged update, pause, version identification, fresh install/update/restore, AT, and safe correction.
- residual risk: A working local build is not evidence of reproducible signing, store acceptance, or safe incident recovery.
- result: HELD

### S13 — Privacy, collaboration and device trust

- authoritative starting state: Private notes/photos, shared-motorcycle records, contributor evidence, export, access revocation, and an offline interval occur on a device that may later be restored or cloned.
- allowed transition: Local classification and account/device binding persist only as permitted; revocation removes future authority, preserves attribution/history, and never turns restored cache into positive authority.
- candidate mechanism: SQLite records with privacy context, SecureStore protected references, FileSystem classified exports, and server re-authentication/authorization.
- official evidence: SecureStore documents Android Keystore/iOS Keychain behavior and restore/backup/biometric limitations; Sharing documents local URI sharing (O6, O9).
- reasoned inference: Platform secure storage helps bind secrets, but the candidate cannot infer account authority, revoke exported copies, or define collaboration semantics without the server/privacy model.
- dependency-specific evidence: expo-secure-store 57.0.4 and expo-sharing 57.0.20 are pinned; key hierarchy, remote auth, and export service are not selected.
- unresolved facts: Classification schema, key hierarchy/rotation, device-loss response, export disclosure/retention, access revocation, audit, and legal basis are UNRESOLVED.
- user-visible result: Private/shared/community/official labels and authorization status are explicit; restored/cloned state is quarantined or reauthenticated and exported disclosure is explained.
- failure/hold behavior: Missing key, revoked authority, ambiguous restore, or unclassified export blocks sensitive use and does not erase independent history.
- recovery path: Re-authenticate, reconcile server authority, quarantine local metadata, rotate/recover keys under policy, and re-export only with explicit disclosure.
- shared-system obligation: Identity, authorization, privacy/legal, audit, collaboration, deletion, and source attribution are shared obligations.
- candidate-attributable work: Enforce classification at adapters/UI, implement quarantine states, protect local references, and test restore/clone/offline transitions.
- accountable AI/external owner: AI may implement bounded UI/storage work; privacy/legal, identity/security, backend, and product owners must approve.
- required later real-device evidence: Same/different trust-context restore, device clone, lock/biometric change, offline revocation, export/share, and Turkish AT on both platforms.
- residual risk: Keychain/Keystore behavior differs across uninstall, backup, biometric changes, and OS versions; exported copies remain outside remote control.
- result: HELD

### S14 — Entitlement, evidence and ownership lifecycle

- authoritative starting state: An entitlement/subscription changes during active work; contributor evidence is withdrawn or corrected; ownership transfers with gaps; one owner deletes a copy.
- allowed transition: Already-started physical work retains safe completion/stop/recovery; dependent claims are re-reviewed; provenance/attribution remains; transferred history is partial when coverage is incomplete.
- candidate mechanism: Local task/checkpoint and evidence snapshots in SQLite/FileSystem, with current entitlement/ownership fetched from an external authority; local cache cannot grant access.
- official evidence: SQLite/FileSystem/SecureStore provide storage primitives only; the lifecycle and safety semantics are governed by the fixed fixture and internal controls (O5, O6, O7, I1, I4).
- reasoned inference: RN/Expo can display lifecycle states, but entitlement, evidence withdrawal, ownership gaps, retention, and independent-history rules must be server/domain policy.
- dependency-specific evidence: No entitlement, subscription, ownership, content, or evidence provider is selected; native packages do not close these requirements.
- unresolved facts: Legal entitlement source, grace/revocation rules, transfer schema, evidence retention, delete-one-copy semantics, correction workflow, and server audit are UNRESOLVED.
- user-visible result: The user sees active/expired/held/partial/withdrawn/corrected states and can safely stop or recover; history is not silently rewritten.
- failure/hold behavior: Authority conflict, missing provenance, or incomplete transfer holds affected claims while preserving independent evidence and safe physical recovery.
- recovery path: Reconcile current authority, forward-migrate ownership, re-review dependent claims, and show partial coverage/attribution.
- shared-system obligation: Product safety, entitlement/identity, content moderation, ownership, audit, privacy/legal, and deletion authorities are shared.
- candidate-attributable work: Implement state display, quarantine/partial labels, local cache invalidation, and resilient revalidation flows.
- accountable AI/external owner: AI may prepare bounded client flows; safety reviewer, legal/privacy, backend/identity, content owner, and product owner are required.
- required later real-device evidence: Active work through entitlement change, withdrawal/correction, offline interval, ownership transfer, deletion of one copy, restore, and AT.
- residual risk: A stale local snapshot can look complete unless every dependent claim is linked to current authority and provenance.
- result: HELD

### S15 — Backup, restore, clone and key loss

- authoritative starting state: Android/iOS backup restore is attempted on the same and a different trust context; a device is cloned; keys are lost/rotated; schema changes and local eligibility metadata are replayed.
- allowed transition: Cache/content, history, private notes, profile binding, trust/eligibility, and key material follow separate explicit rules; restored authority is quarantined until reconciled.
- candidate mechanism: SecureStore for protected references, SQLite for local records/migration state, FileSystem for packages/media, and a data-preserving migration/recovery adapter.
- official evidence: SecureStore documents Android backup exclusion needs, uninstall/restore differences, biometric invalidation and small-value limits; SQLite documents persisted local DB (O6, O7).
- reasoned inference: Platform storage behavior can preserve or invalidate pieces differently; no Expo primitive proves a complete backup, clone, encryption, or key-recovery policy.
- dependency-specific evidence: expo-secure-store 57.0.4, expo-sqlite 57.0.3, and expo-file-system 57.0.7 are the exact paths; backup configuration and encryption module are not selected.
- unresolved facts: Data classes and backup rules, database/file encryption, key hierarchy/rotation, same/different trust policy, replay detection, schema migration, and recovery support are UNRESOLVED.
- user-visible result: Restore/clone/key-loss states are explained; unverified eligibility is quarantined; the user receives a data-preserving re-authentication or recovery path.
- failure/hold behavior: Unavailable key, corrupt migration, replayed authority, or trust mismatch blocks sensitive use without silently deleting history or declaring success.
- recovery path: Re-authenticate, reconcile server state, rotate/recover keys under explicit policy, migrate forward with provenance, and export permitted data.
- shared-system obligation: Identity/key authority, backup/legal policy, retention, audit, server recovery, and deletion are shared obligations.
- candidate-attributable work: Define data-class adapters, migration journal, quarantine states, backup exclusion config, and restore/clone tests.
- accountable AI/external owner: AI may implement bounded migration UI; platform security, backend/identity, privacy/legal, native, and product owners must approve.
- required later real-device evidence: Android/iOS same and different trust restore, clone, uninstall, biometric change, key loss/rotation, schema migration, offline eligibility replay, and AT.
- residual risk: Key material and local data may have intentionally different survivability; recovery can be impossible without a separately owned account/key path.
- result: HELD

## 6. Accessibility Matrix

The matrix applies to Turkish readiness, warning, unexpected-state stop, active-step, and
safe-recovery flows. RN API availability is not a device pass. Every row is HELD until
real-device assistive-technology execution and an independent acceptance record exist.

| Check | Framework/documented capability | Platform-specific work | Later real-device oracle | Status |
|---|---|---|---|---|
| VoiceOver | RN accessibility labels, hints, roles, state, focus/announcement affordances; O10 | iOS semantic tree, focus order, rotor/gesture behavior, Turkish announcement timing, native exceptions | Oldest/current iPhone with VoiceOver through readiness, warning, stop, active step, recovery, stale/unknown/error states | HELD |
| TalkBack | RN accessibility labels, roles, state, live-region/focus affordances; O10 | Android API 29 and main Android semantics, traversal, focus return, notification/permission handling | Constrained/main Android with TalkBack through the same critical flows and interruptions | HELD |
| Largest text/reflow | RN text/layout supports app-owned responsive layouts; exact product behavior not proven | Dynamic type/font-scale, Turkish longest strings, diagrams/warnings, scroll/clip/overflow policy | Largest supported settings on both device cohorts; no clipped/hidden stop or recovery action | HELD |
| Focus and reading order | RN accessibility tree and explicit platform-specific boundaries | Modal, error, deep-link, package, and recovery focus placement; native custom controls | Screen-reader traversal on every safety state after async update, restart, and link entry | HELD |
| State announcements | RN state/live-region/announce affordances; O10 | Android/iOS timing, interruption priority, stale/recall/unknown/conflict messages | Verify announcement content and timing for download, recall, partial, hold, recovery, and upload states | HELD |
| Non-color status/contrast | RN styling and text/icon composition; no automatic Kavriva pass | Contrast tokens, warning/recall/partial patterns, dark/light and disabled states | Contrast inspection plus AT/device execution; every status understandable without color | HELD |
| Reduced motion | Platform preference can be observed only through an explicit app policy; exact candidate mapping UNRESOLVED | Disable or reduce transitions/auto-play while preserving focus and safety timing | iOS/Android reduced-motion settings through active/stop/recovery flows | HELD |
| Switch/voice control | Platform assistive input can activate labeled controls; exact custom-control mapping UNRESOLVED | Action names, traversal, permission/picker/share surfaces, no gesture-only safety action | Switch and voice control on both platforms for stop, retry, cancel, recovery, and navigation | HELD |
| Reduced dexterity | RN touch targets/pressable controls are implementation affordances | Target sizing, spacing, alternatives to drag/long-press, glove/one-hand/error states | Real device one-hand/reduced-dexterity exercise with no unsafe accidental advance | HELD |

## 7. Upgrade and Forced-Event Walkthrough

The candidate has a planned cadence of four release windows per year plus safety
correction as needed. Exact duration, staffing, queue time, and cost are UNRESOLVED; no
hours or prices are invented. Every event below has a release-hold path.

### 7.1 Normal planned release window

1. Freeze the exact Expo/RN/package lock, API/content/config compatibility graph, and
   fixture revision. Generate native projects through the owned config-plugin/prebuild
   path and record native diffs.
2. Run independent implementation review, both-platform build, S1–S15 evidence plan,
   accessibility plan, dependency/SBOM/provenance checks, and resource/cost cap checks.
3. Rebuild whenever a native library, config, SDK, or native module changes. A JavaScript
   reload is not a native release.
4. Produce immutable Android/iOS artifacts, verify signing/provenance, then stage through
   the store authorities. Pause if any critical evidence, owner, device, or specialist
   is unavailable.

Affected toolchains include Node, Expo CLI, Gradle/Android SDK, Xcode, CocoaPods/native
modules, package lock and CI/artifact storage. External dependencies include store
accounts, testers, content/safety approval, API compatibility, signing custody, and
device/AT capacity.

### 7.2 Safety/security emergency correction

- Freeze the affected binary/content/configuration and identify users and versions from
  immutable provenance. Pause the staged rollout independently of the normal cadence.
- Keep safe-stop/recovery and already-started-work behavior available where verified.
  Issue a reviewed compatible binary or separately governed content/config correction
  through its authorized channel; do not use OTA to bypass the store/binary boundary.
- Re-run the affected S1–S15/accessibility/security evidence and reopen only after
  independent verification. If safe rollback is impossible after data migration, use a
  forward recovery and visible hold.

Duration, incident staffing, store review timing, and communication capacity remain
UNRESOLVED.

### 7.3 Forced Apple/Google build or store requirement change

- At this snapshot, the Expo SDK 57 matrix records Android compile/target API 36 and
  Xcode 26.4+, while Apple upload guidance requires Xcode 26+ and Google’s current
  target requirement is API 36. A future store/OS rule is a forced event, not a reason
  to relax the fixture.
- Re-resolve the exact Expo SDK/RN/native package set, update config/build properties
  only through a reviewed native change, rebuild both platforms, and repeat real-device,
  AT, signing, and staged-release evidence.
- The official [Expo SDK 57 changelog](https://expo.dev/changelog/sdk-57) records
  ongoing maintenance changes; the exact availability and compatibility of any future
  Xcode/iOS scene requirement is UNRESOLVED. Expo SDK 58 beta/RN 0.88 RC is not silently
  substituted for this stable comparison.

If the build or acceptance path cannot close, release is HELD with the last safe
compatible artifact and an owner decision on upgrade, replacement, or scope hold.

### 7.4 Abandonment or incompatibility of a critical dependency

The dependency owner must pin the affected package, advisory, native surface, OS range,
and affected S1–S15/contracts/tests. The fallback is a maintained compatible Expo/RN
module, an explicitly owned Swift/Kotlin/Turbo Native Module, or a safe blocked/manual
path. An unnamed plugin, unreviewed fork, or Expo Go substitution is not a fallback.

Native module/config changes require new development/store builds, lock/SBOM/provenance,
two-platform device and AT evidence, and security review. If no owner or maintained
fallback exists, the capability and candidate remain HELD.

### 7.5 Old/new client, API, schema, content and configuration coexistence

Publish a capability/version graph before changing API, schema, configuration, or content.
Old clients receive only an explicitly compatible representation; unknown safety meaning
fails closed. RuntimeVersion may guard native compatibility, but it does not authorize
content, recall, entitlement, or safety transitions. Store-delivered binaries remain the
code path; OTA is excluded. Cached packages are revalidated and may be quarantined.

### 7.6 Rollback refusal when data migration cannot be safely reversed

Record migration version, provenance, affected records, and reversible/irreversible
steps before release. If the data migration is not safely reversible, do not roll back
the binary as if the data were unchanged. Hold affected operations, run a tested forward
recovery, preserve history, and provide a user-visible re-authentication/repair path.
The exact migration tooling, support capacity, and recovery duration are UNRESOLVED.

### 7.7 Incident pause, impact identification, correction and recovery

Pause the staged release; map artifact hash, version, runtime, package/content/config
versions, affected device cohorts, and pending local operations; preserve logs without
collecting private content unnecessarily. Separate binary, backend, database, content,
configuration, and emergency-suspension actions. Correct through the authorized release
path, reconcile clients, verify safe-stop/recovery and accessibility, and reopen
gradually. Missing responder, signing authority, safety reviewer, or evidence holds the
recovery.

## 8. AI-Operability and Task Isolation

The candidate’s TypeScript/React adjacency to the browser Operations surface is a
reasoned hypothesis, not evidence that the trust domains or native work can be shared.
The following records the AI-operability gate for this research snapshot.

| Question | Evidence/result |
|---|---|
| Can a fresh AI implement one bounded task without whole-project context? | Conditional route exists: typed React Native UI and explicit adapters can be task-scoped, and development builds expose native dependencies. A real bounded TASK context pack, contracts, fixtures, and acceptance oracle do not yet exist. HELD. |
| Are platform exceptions visible in the task graph? | Platform-specific files, config plugins, native modules, permissions, lifecycle, and rebuild triggers are named in Sections 3–4. No executable dependency/task graph or owner map exists. HELD. |
| Can implementation, review and validation remain separate? | The control model requires separate implementation, review, and validation roles. Reviewer roster, native escalation, safety/AT authority, and evidence workflow are UNRESOLVED. HELD. |
| Are builds/tests deterministic enough to produce evidence? | Exact top-level snapshot and build floors are recorded. Lockfile, transitive hashes, generated native output, signing provenance, test fixtures, and reproducible CI/local path are absent. HELD. |
| Can dependency changes identify affected contracts/tasks/tests? | Closure rows name package/build/rebuild boundaries and affected concerns. A machine-readable impact graph, EOL owner, and fallback tests are absent. HELD. |
| Can the project recover without one opaque workstation/provider? | Expo documents local and hosted build paths, but Mac/Xcode access, EAS account/caps/cost, artifact export, signing custody, and provider exit are UNRESOLVED. HELD. |
| Does the candidate require unavailable human specialist authority? | Yes: Apple/Google account and store authority, iOS/Android native review, real devices and AT, qualified safety/content review, identity/privacy/legal, and incident command. AI or the product owner cannot substitute for those authorities. HELD. |

No user coding, debugging, build repair, or unbounded human availability is treated as a
mitigation. A future task pack must carry the relevant contract, dependency/native
exception, fixture, test oracle, evidence artifact, owner, and recovery path.

## 9. Equal 24-Month TCO Worksheet

### 9.1 Workload calculation used for all three MAU tiers

These figures are arithmetic from the approved fixture, not provider prices. The local
device stress fixture is not multiplied by MAU. Retention, retries, backups, and outbound
copy counts remain separate unresolved assumptions.

| MAU tier | Required compact/month | Required compact/24 months | Optional media/month | Optional media/24 months | Photo uploads/month | Photo uploads/24 months |
|---:|---:|---:|---:|---:|---:|---:|
| 1,000 | 2,000 × 12 MB = about 24 GB | about 576 GB | 100 × 100 MB = about 10 GB | about 240 GB | 500 × 3 MB = about 1.5 GB | about 36 GB |
| 10,000 | 20,000 × 12 MB = about 240 GB | about 5.76 TB | 1,000 × 100 MB = about 100 GB | about 2.4 TB | 5,000 × 3 MB = about 15 GB | about 360 GB |
| 50,000 | 100,000 × 12 MB = about 1.2 TB | about 28.8 TB | 5,000 × 100 MB = about 500 GB | about 12 TB | 25,000 × 3 MB = about 75 GB | about 1.8 TB |

The 24-month columns assume the fixed monthly rates continue only for capacity discussion;
they are not a legal retention promise and are not price quotes.

### 9.2 Equal cost worksheet

Unknown amounts remain UNRESOLVED and are never entered as zero. “Candidate-caused”
identifies work or exposure attributable to this RN/Expo boundary; it is not a price.
Every free/capped path requires cap, overage, alert, export, and exit evidence before
approval.

| Cost row | Product-wide unavoidable | Candidate-caused | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---|---|---|---|---|---|---|
| Store membership | Both planned stores and legal accounts are product-wide release prerequisites | No framework-specific fee isolated | None pre-approved | Apple renewal count and store/testing scope | Retain legal/store identity; no store bypass | No free bypass assumed | Google Play USD 25 one time; Apple Developer Program USD 99/year; approved 24-month store-only baseline USD 124–223 before tax/currency. Official current baseline / high confidence; recheck at purchase. |
| Mac/hosted build | iOS distribution requires an Apple build path | Native Expo/RN iOS rebuilds and generated-project maintenance | Hosted EAS convenience if separately approved | Parallel builds, queue, artifact retention | Local Xcode/native project and portable artifacts | Local path only if Mac/account/capacity exists; hosted caps/prices/exit UNRESOLVED | UNRESOLVED; no hosted price invented. |
| Android/iPhone access | Real devices and AT are mandatory evidence | RN/Expo dual-platform device matrix and native lifecycle checks | Additional lab/test devices | More cohorts/testers at scale | Borrowed/replaceable devices and portable test records | Borrowed devices preferred; availability/cost UNRESOLVED | UNRESOLVED. |
| CI/build artifacts | Reproducible evidence, signing, SBOM, and retention are mandatory | Native rebuilds, package graph, prebuild output, and two-platform artifacts | Hosted CI convenience | More release windows, branches, and artifact retention | Exportable lock/SBOM/artifacts and local recipe | Local/capped CI only with caps/alerts/export/exit | UNRESOLVED. |
| Backend/database | API, authority, sync, audit, and migration exist regardless of UI framework | Native client adapters and offline reconciliation integration | Managed provider features | MAU, conflict, sync, query and incident volume | Portable schemas, API contracts, and migration data | Provider/free tier only after quota/overage/exit evidence | UNRESOLVED; no provider or price selected. |
| Storage/backup/CDN/egress | User photos, package media, backups, and outbound are product-wide | FileSystem/package staging and retry copies affect client behavior; no server price assigned | CDN/media optimization | Workload table: 24/240/1,200 GB compact; 10/100/500 GB optional media; 1.5/15/75 GB photo uploads monthly | Exportable originals, manifests, provenance, and provider migration | Capped storage only with retention/egress alerts and export | UNRESOLVED; arithmetic is not a price. |
| Identity/email/SMS | Identity/re-auth and user communication are product-wide choices | SecureStore/device-binding integration and re-auth UI | SMS or transactional email convenience | Account and recovery volume | Portable account mapping and recovery path | Account-light first value; no SMS provider assumed | UNRESOLVED. |
| Crash/telemetry/analytics | Minimal operational signals and privacy controls are required | RN/Expo native crash/lifecycle signal integration | Third-party dashboards | Device/version/event volume | Exportable, minimal, privacy-filtered events | Local/self-hosted/capped option only with retention/exit evidence | UNRESOLVED. |
| Security/SBOM/signing | Supply-chain, key custody, vulnerability response, and provenance are unavoidable | RN/Expo package/native graph, config plugins, generated projects, and rebuild response | Paid scanning/signing convenience | More dependencies/releases and advisory response | Portable SBOM, lockfile, signing/provenance records; key rotation | Free tools are possible only with verification owner and export | UNRESOLVED. |
| Accessibility validation | AT and real-device acceptance are product-wide safety obligations | RN semantics plus platform-specific exceptions and native rebuild/test surface | External lab or specialist convenience | More devices, locales, releases, and regressions | Portable accessibility oracle/copy/tokens | Borrowed devices/external testers if evidence quality holds | UNRESOLVED. |
| Safety/content review | Qualified review and recall/correction authority are unavoidable | Candidate must surface stale/unknown/held states and preserve safe recovery | Additional review tooling | Four windows/year plus emergency correction | Portable content provenance and acceptance records | No AI-only or unqualified substitute | UNRESOLVED. |
| AI implementation/review | Controlled implementation, independent review, and validation capacity are required | RN/Expo/native boundary task decomposition, rebuilds, and context packs | Extra model/tooling or hosted agents | More platform/dependency exceptions and release windows | Portable task packs, contracts, fixtures, and evidence | Existing AI path only if deterministic and separately reviewed | UNRESOLVED; no AI tooling price invented. |
| Upgrade/dependency response | OS/store/security changes require response for any mobile candidate | Expo SDK/RN/native-module cadence, rebuilds, compatibility and fallback work | Paid upgrade support | Four planned windows plus safety/security events | Portable adapters and replacement native path | Pin only within supported/security policy; no indefinite parking | UNRESOLVED. |
| Support/incident response | User support, pause, correction, and recovery are product-wide | RN/Expo version/device/lifecycle diagnostics add candidate-specific triage | External support tooling | MAU, versions, devices, and incident volume | Runbooks, version map, portable evidence and safe hold | Capped tooling only after alert/export/exit proof | UNRESOLVED. |
| Exit/migration | Data continuity and a replacement route are product-wide obligations | RN/Expo component/native/config rewrite and dual-client bridge work | Migration consultancy/tooling | More users, media, history, and concurrent clients | Portable schemas, contracts, fixtures, exports, and staged replacement | Open/exportable artifacts; no one-click migration assumed | UNRESOLVED; no rewrite price invented. |

The only numeric monetary values in this worksheet are the owner-approved store constants
from Section 2 and the official Apple/Google sources. No Expo/EAS, Mac, CI, backend,
storage, device, messaging, telemetry, security, AI, support, or migration price is
asserted.

## 10. Exit Dossier

The following is the required survival boundary, not a completed migration artifact.

- Content/data schema and history/provenance: motorcycle, task, package, profile, note,
  photo, operation, entitlement, correction, withdrawal, recall, ownership, audit, and
  privacy-classification schemas must be exportable with source attribution and event
  history.
- Offline-package and compatibility fixtures: the 12 MB required package, optional media,
  2 GB unrelated catalog, size/space/interruptions, capability graph, stale/recall, and
  old/new-client fixtures survive as framework-independent acceptance data.
- Media and exports: original user media, package manifests, integrity/provenance records,
  classified exports, disclosure history, and independent evidence copies remain portable.
- Identity/key/account continuity: account identifiers and ownership mapping survive;
  platform Keychain/Keystore material is not blindly exported. Re-authentication, key
  rotation, loss, and recovery are explicit external contracts.
- Design tokens, copy and accessibility intent: Turkish safety copy, warning/stop/recovery
  semantics, tokens, semantic labels, AT oracles, and Phase-3 design truth survive.
- Tests and acceptance oracles: S1–S15 fixtures, device/network/interruption profiles,
  migration/recovery oracles, security checks, AT checks, release/provenance checks, and
  no-silent-discard rules survive.
- Native modules/platform integrations: each Swift/Kotlin module, Turbo Native Module
  spec, permission, lifecycle, thread, fallback, config-plugin input, and generated
  native diff is isolated behind an adapter with ownership and EOL/security history.
- Staged replacement release and migration route: a replacement client reads the same
  portable contracts, runs in parallel with the old client, transfers state through a
  forward data-preserving migration, stages both stores, and closes the old path only
  after real-device/AT/safety/release evidence. A non-reversible data migration is not
  “rolled back” by reverting a binary.

The framework-bound portion is React Native/Expo UI, Expo config plugins and generated
native projects, Expo package APIs, Swift/Kotlin/Turbo Native Module code, platform
permissions, and store packaging. OTA/code delivery remains excluded from both the
current candidate and the exit plan.

## 11. Candidate Result

- mandatory-gate result: HELD — this is a structurally complete, unreviewed, no-code research dossier. The snapshot and explicit native boundary are plausible, but critical closure, device, owner, provider, cost-cap, accessibility, and release evidence are not complete.
- S1–S15 result count: 0 PASS / 15 HELD / 0 REJECT. The excluded OTA path is REJECTED as a path and is not counted as an S scenario.
- unresolved critical facts: final product device models and patch levels; generated lockfile/transitive hashes/SBOM; database/file encryption and key hierarchy; backup/restore/clone policy; API/auth/sync/conflict/recall/entitlement/content contracts; native module owners/fallbacks/EOL/security response; Mac/CI/EAS choice and caps; signing/store identity and tester population; real-device and AT capacity; qualified safety/content reviewer; support/incident capacity; current store/build rules at each release; exact infrastructure and migration amounts.
- largest low-budget burden: Real-device/assistive-technology evidence, iOS build/signing access, native lifecycle review, and recurring Expo/RN/OS/dependency upgrades. Amount is UNRESOLVED.
- largest AI-operability benefit/risk: Benefit is potentially bounded TypeScript/React task work plus explicit native escape routes. Risk is that native rebuilds, platform exceptions, dependency cadence, deterministic evidence, and external safety/store/AT authority overwhelm language/tool overlap. Both remain HELD.
- external authorities/capacity required: Owner legal identity and Apple/Google accounts; store testing/release authorities; Android/iOS native reviewer; real devices and AT testers; qualified safety/content reviewer; backend/identity/privacy/security owner; incident commander; tax/legal/payment authority.
- conditions for recommendation: Complete dependency lock/SBOM/provenance and native closure; name primary/backup owners and fallbacks; close encryption/key/backup and API/sync/recall contracts; run real-device/AT/resource/interruption evidence for all S1–S15; prove reproducible local/hosted build and signing custody; approve cost caps/alerts/export/exit; complete independent review and release runbook.
- disqualifiers triggered: None for the explicitly scoped candidate path. Introducing Expo Go as production proof, depending on OTA for code/safety release, assuming no native skill, or leaving a critical native capability without a maintained/owned fallback would trigger rejection.
- overall Phase-4 status: HELD

This result is documentary evidence only. It is not a framework recommendation, approval to
implement, an ADR, a purchase authorization, a signed build, a benchmark, a real-device
pass, an accessibility pass, or a store release.
