# DEBATE-006 — Final Closure Exercise: React Native + Expo Development Builds
## DOCUMENTARY / NO-CODE / HELD

**Status:** `DOCUMENTARY CLOSURE EXERCISE / NO-CODE / HELD / NO FRAMEWORK SELECTED`  
**Date:** 2026-09-18  
**Candidate:** React Native + Expo development builds + explicit native boundary  
**Decision level:** Phase-4 tie-break evidence only; not an ADR

This document defines the final equal closure exercise requested after the completed
`TASK-SIM-MOB-001` simulation and its audit/judge. It is a documentary acceptance oracle,
not an implementation plan, code change, prototype, benchmark, build, store submission,
purchase authorization or framework recommendation. No application, native project,
lockfile, build artifact or account is created by this exercise.

The exercise is deliberately marked `HELD`: the repository contains documentary evidence
and a closure method, but it contains no real-device, assistive-technology, build,
signing, store, safety-review or provider-capacity result.

## 1. Controlled scenario and decision boundaries

### 1.1 Frozen project context

This exercise inherits the approved common fixture and the RN/Expo dossier without changing
their constants:

- Android and iOS consumer apps remain planned, with a separate browser-based Internal
  Operations surface.
- The publication order is Android first, then iOS. Simultaneous store publication is not
  required.
- The comparison horizon is the first release plus 24 months, with four planned release
  windows per year plus safety/security correction when required.
- The compact selected-motorcycle/task package remains bounded by the common fixture:
  required closure target up to `12 MB`, optional media up to `150 MB`, cache target
  `250 MB`, explicit user choice above `25 MB` on cellular, and no default download of
  the unrelated `2 GB` catalog.
- The owner directly controls an Android phone. iPhones may be borrowed from close
  friends for testing. Borrowed access is useful evidence capacity, not a permanent
  release dependency.
- Mac access is not confirmed. A hosted Mac/build route is a later option only after
  explicit price, cap, credential, export and exit review.
- Approximately `TRY 2,000–3,000/month` is a future non-store planning ceiling, not a
  purchase authorization and not an instruction to spend the full amount.

The fixed device and evidence floor remains the common fixture: constrained Android
10/API 29, main Android 13+, oldest supported iPhone capable of iOS 16.4, and a current
standard iPhone cohort. Actual branded devices, patches, tester availability and test
scheduling remain unresolved until release preparation.

### 1.2 Injected event

The exercise injects two events at the same time:

**Event P — optional photo dependency changes.** The optional photo capability is either:

1. replaced by a maintained, compatible package/adapter; or
2. abandoned and removed from the first release.

The exact package is not silently assumed. The closure record must identify whether the
photo path uses `expo-camera`, `expo-image-picker`, `expo-document-picker`, a different
native-capable package, or an explicitly owned native module. The existing dossier records
the following SDK 57 snapshot entries as candidate references only:
`expo-camera 57.0.5`, `expo-image-picker 57.0.18`, `expo-document-picker 57.0.2` and
`expo-file-system 57.0.7`. Those numbers are not a lockfile, security approval or build
claim.

**Event B — Apple and Google build requirements change.** The change is represented by
symbolic requirement deltas `APPLE-NEXT` and `GOOGLE-NEXT`; no future API, SDK, Xcode or
date is invented. At each release window, the exact current store rules and the Expo/RN
support line must be rechecked. As a current documentary baseline, the official Expo SDK
matrix lists SDK 57 with Android compile/target API 36, iOS 16.4+ and Xcode 26.4+;
Google currently states that new apps and updates must target Android 16/API 36 from
31 August 2026; and Apple currently states that App Store Connect uploads must be built
with Xcode 26 or later using the iOS 26 SDK since 28 April 2026. These are dated external
facts, not permanent project constants.

The two events must be analyzed together. A photo replacement/removal can alter the
native dependency graph and permissions at the same time that store requirements alter
the build toolchain. The exercise must not validate one event and silently omit the other.

### 1.3 Out-of-scope shortcuts

- Expo Go is excluded from production, native-dependency or release evidence. It has a
  fixed native library set and cannot validate an app-specific native closure.
- OTA/runtime JavaScript code delivery is excluded. `expo-updates` is not a recovery or
  release shortcut, and no remotely delivered code may bypass store artifacts,
  provenance, safety review or release controls.
- EAS is not mandatory. EAS Build is one possible hosted or local-with-EAS route only if
  separately approved. Local native builds and another provider remain possible routes
  when they preserve the same closure evidence.
- A JavaScript reload, emulator/simulator result, screenshot or AI assertion is not a
  native rebuild, real-device, assistive-technology, signing or store pass.
- The owner is not asked to code, debug, repair generated projects, fix signing or infer
  an architecture decision from a failed build.

## 2. Baseline closure ledger

The exercise begins by freezing a known-good candidate record before either injected event
is applied. Every item below is a closure input, not an instruction to create it now.

### 2.1 Dependency and tool locks

| Closure class | What must be identified and hashed | Closure meaning |
|---|---|---|
| Direct package manifest | `package.json` (or the selected equivalent), direct dependencies, dev dependencies, scripts, package manager declaration and engine constraints | Defines the requested JS/native surface. A package name alone is insufficient. |
| Package-manager lock | Exactly one authoritative lock format (`package-lock.json`, `yarn.lock`, `pnpm-lock.yaml`, or another explicitly accepted format), all transitive versions, registry URLs, integrity/hashes and optional resolutions/overrides | Makes the dependency graph reproducible. A local `node_modules` directory is not the source of truth. |
| Expo/RN/React line | `expo`, `react-native`, `react`, `@expo/cli`, `expo-dev-client`, `expo-modules-core`, Babel/runtime tooling and their transitive closure | Binds the development-build runtime and the supported native boundary. The evaluated dossier snapshot is SDK 57/RN 0.86.3, not an indefinite latest claim. |
| Capability packages | Photo, filesystem, SQLite, secure storage, notifications, linking and any other native-capable package, with exact version, platform support and config-plugin presence | A capability may affect native files even when its JavaScript call site looks small. |
| Native dependency sub-locks | Android Gradle/Maven resolution and iOS CocoaPods/SPM resolution, including lockfiles where used | Captures platform-specific transitive dependencies that the JS lock does not fully describe. |
| Toolchain lock | Node and package-manager versions; Java/JDK; Android SDK/build-tools/NDK; Gradle/Android Gradle Plugin; Xcode/Apple SDK; CocoaPods/Fastlane/SPM; OS image and relevant environment | A source lock without a toolchain lock cannot explain a build or a generated diff. |
| Build-profile lock | `eas.json` only if EAS is selected; local build profiles, variant/configuration names, environment names, artifact paths and non-secret build inputs | Separates optional provider configuration from the app contract. It must not hide a provider-only dependency. |
| Effective-config snapshot | Resolved app config after dynamic configuration and plugin options, with a digest and the input environment names (never secret values) | Prevents a dynamic config function or environment drift from changing the native app invisibly. |

The exact final versions must be resolved again when the injected requirement event is
processed. A package that was safe in the baseline is not presumed compatible with a new
Xcode, Android API, Expo SDK or OS policy.

### 2.2 App configuration and config-plugin ledger

| Input class | Examples to record | Required closure question |
|---|---|---|
| Core app config | App name/slug, version, runtime compatibility field, scheme, icons/splash, `android.package`, `ios.bundleIdentifier`, build number/version code | Do the identifiers remain continuous across the new artifacts? Are changes intentional and externally approved? |
| Android config | Minimum/target/compile API, package/manifest settings, `android.permissions`, `blockedPermissions`, adaptive icons, intent filters, app links, backup/data-extraction policy and build properties | Did the photo branch or `GOOGLE-NEXT` add/remove permissions, change the target API or alter backup/security behavior? |
| iOS config | Deployment target, `ios.bundleIdentifier`, `ios.infoPlist`, camera/photo usage descriptions, URL schemes, associated domains, capabilities and entitlements | Did the photo branch alter privacy text, capabilities or provisioning requirements? Does `APPLE-NEXT` require a new SDK or deployment target? |
| Plugin inventory | Every package-provided and local config plugin, exact package/source/version, options, order, platform modifiers touched and expected output | Is the plugin named, deterministic, reviewable and owned? An unnamed future plugin is `HELD`. |
| Dynamic-config inputs | Environment/profile values that influence app config, build channel, API endpoint or feature envelope | Can an independent verifier reproduce the effective config without receiving secret credentials? |
| Excluded update inputs | Any `updates`/OTA-related configuration, channels, URLs or runtime assumptions | Confirm that no code-delivery path can be used to bypass the store artifact boundary. |

Expo documents that config plugins are referenced from the app config and run during
prebuild, and that native changes take effect only after rebuilding the native project.
Permissions in standalone/development builds also require native build-time configuration;
runtime JavaScript permission requests are not enough for closure.

### 2.3 Prebuild and generated-project ledger

The generated Android and iOS projects are derived release inputs. The record must include
the generation command/tool version, source config/plugin inputs, generated diff against
the baseline, and whether each change is expected. If Continuous Native Generation is
used, the generated directories may be discarded and regenerated, but the generated
outputs used for each artifact still require an inspectable digest/diff.

**Android generated/native file classes (when present):**

- project settings and included builds (`settings.gradle`/`.kts`, autolinking and module
  inclusion);
- root build files, version catalogs, Gradle properties, wrapper and repository policy;
- app module build files, build types/variants, compile/target/min API values, packaging,
  signing references, R8/ProGuard and native build options;
- `AndroidManifest.xml`, merged manifest and permission/intent-filter output;
- Java/Kotlin application/activity/module registration and lifecycle hooks;
- Expo/RN autolinking and generated module metadata;
- resources: icons, launch/splash, strings, styles, colors, XML and notification assets;
- `google-services.json` or equivalent service references, if a later approved capability
  needs them; no secret service material is committed;
- C/C++/NDK/CMake output, only if a selected dependency introduces it;
- generated intermediates and caches are not authority, but the exact build environment
  that produced the artifact remains provenance evidence.

**iOS generated/native file classes (when present):**

- Xcode project/workspace, project settings, schemes, targets and build configurations;
- `project.pbxproj`, `.xcconfig` and other generated build-setting files;
- `Podfile`, `Podfile.lock`, `Podfile.properties.json`, SPM `Package.resolved` and
  autolinking/module integration;
- `Info.plist`, `PrivacyInfo.xcprivacy` and any generated privacy/usage declarations;
- entitlements, URL schemes, associated domains, app groups and capability declarations;
- AppDelegate/scene lifecycle integration and Swift/Objective-C module registration;
- Assets catalogs, launch/splash resources, localized permission text and other bundled
  resources;
- native extensions/targets only when explicitly approved;
- derived data and build caches are not source truth, but tool/image provenance remains
  part of the artifact record.

**Direct native boundary classes:**

- Expo Modules API Swift/Kotlin modules;
- typed React Native Turbo Native Modules and code-generation/spec inputs;
- platform-specific React Native files and lifecycle adapters;
- native permissions, entitlements, threads/queues, lifecycle callbacks and error paths;
- native library transitive dependencies and their security/EOL owners;
- fallback/manual/read-only path when a native capability is unavailable.

Direct edits to generated output must not silently become the only source of a change. If a
direct edit is unavoidable in a non-CNG path, it must be named, reviewed, reproducibly
reapplied and included in both the generated diff and the exit dossier. In a CNG path,
the change must be represented by app config, a reviewed config plugin, a native module
boundary or an explicitly accepted native source file before regeneration.

## 3. Event P — optional photo replacement or removal

### 3.1 Common semantic invariant

The photo remains optional evidence. It cannot verify a physical state, prove fitment,
replace a warning/readiness gate, create entitlement, publish official technical truth or
convert a restored UI into physical truth. The safety-critical step remains usable without
the photo when the product contract permits; otherwise the affected capability is visibly
`HELD`, not silently weakened.

Existing local photos, pending evidence, provenance and disclosure history are portable
user/data truth. Removing a new-capture dependency must not silently delete or rewrite
those records.

### 3.2 Branch P-Replace — maintained replacement

The following conceptual sequence is required:

1. Freeze the baseline dependency/config/native/artifact manifest and identify every
   package, plugin, permission, entitlement, native module and generated file touched by
   the old photo path.
2. Identify the replacement package or owned adapter, exact version and source, platform
   support, transitive native dependencies, config-plugin behavior, permissions,
   privacy declarations, fallback, EOL/security owner and replacement tests.
3. Resolve the JS/package lock and platform-native locks together. Record removed and
   added packages, integrity hashes, dependency provenance and any license/security
   review. Do not let a transitive native package enter unrecorded.
4. Update app config/plugin inputs through the controlled source. Record camera/photo
   permission text, Android manifest effects, iOS usage/entitlement effects, file URI
   handling, metadata/privacy policy and process-death behavior.
5. Regenerate prebuild output cleanly for each affected platform and inspect the expected
   diff. Unexpected permissions, entitlements, targets, resources or module registration
   are a hold.
6. Build a new development client for each affected platform. The old development client
   is not valid evidence for the new native graph.
7. Run the shared optional-photo negative cases: permission denied, permission later
   granted, capture/import, temporary-file loss, malformed/large file, low storage,
   process termination before checkpoint, duplicate upload, unstable transfer and
   explicit privacy classification.
8. Run separate Android and iOS lifecycle/accessibility evidence, then produce new signed
   release artifacts and provenance. A replacement that works on Android does not close
   iOS.

If the replacement requires a custom native module, the module spec/code-generation input,
Swift/Kotlin ownership, thread/lifecycle/permission/accessibility behavior, fallback,
security response and EOL plan must be reviewed before it can be a candidate. An unnamed
plugin, unreviewed fork or “we can add native code later” is `HELD`.

### 3.3 Branch P-Remove — optional photo abandoned

Removal is not a zero-change event. The closure record must prove:

- the direct photo package(s) and all native-capable transitive packages are removed from
  the manifest and locks, or are retained only for another explicitly documented feature;
- package-provided/local config plugins and plugin options are removed or narrowed;
- Android camera/media permissions, manifest entries, providers, intents, resources and
  native module registration are removed where no other approved capability needs them;
- iOS camera/photo usage descriptions, entitlements, URL schemes, native targets and
  module registration are removed or retained only with an explained independent need;
- generated Android/iOS output is regenerated and reviewed for stale references;
- the task has an accessible manual/no-media path, with the photo absent/pending/failed
  states still truthful for old records;
- previously stored photos/evidence are not deleted, declassified or treated as verified;
- API/content/export contracts and migration records remain compatible with historical
  photo references, or use a reviewed forward migration;
- security/privacy review confirms that removing capture does not expand or silently
  change access to existing private media.

Removal can lower future native surface, but it still changes the dependency closure and
therefore cannot be released from an old native artifact. If removal is incomplete or a
stale permission/native reference remains, the branch is `HELD`.

### 3.4 Photo-branch evidence packet

The packet must contain, separately for Android and iOS:

- baseline and resulting lock/config/plugin manifests with hashes;
- package provenance, license/security/EOL disposition and replacement/removal decision;
- prebuild generation input, tool version and generated native diff;
- effective permission/entitlement/privacy declarations;
- development-build identity and rebuild reason;
- camera/picker/file lifecycle evidence, including denial and process termination;
- temporary-file, classification, metadata, upload-idempotency and disclosure outcomes;
- TalkBack/VoiceOver and largest-text evidence for optional, pending, failed and safe-stop
  states;
- release artifact digest, signing/provenance references and independent review;
- unresolved owner, device, provider and cost triggers.

No photo packet may mark a photo as technical verification. No documentary packet may be
called a real-camera or privacy pass.

## 4. Event B — simultaneous Apple/Google build-requirement change

### 4.1 Re-resolution rule

When `APPLE-NEXT` and `GOOGLE-NEXT` arrive, freeze the last safe compatible artifact and
re-resolve the following as one change set:

- Expo SDK/RN/React compatibility line and supported OS floors;
- Node/package-manager/CLI versions;
- Android compile/target/build tools, Gradle/AGP, Java/JDK and NDK if present;
- Xcode, Apple SDK, Swift/compiler, CocoaPods/SPM and macOS host requirements;
- every native-capable package and config plugin, including photo branch outcome;
- app config build properties, minimum OS settings, permissions, entitlements and
  generated project templates;
- Android/iOS package-manager locks, native sub-locks, SBOM and vulnerability/EOL record;
- signing, provisioning, bundle/package identifiers and store metadata;
- test-device/OS matrix and store submission/test requirements.

The rule is conservative: if a dependency’s native behavior under the new toolchain is
unknown, it is treated as changed and requires affected-platform rebuild/revalidation.
If the current Expo SDK line cannot close the new store requirement, the candidate remains
`HELD` until a supported SDK/toolchain upgrade or an explicitly owned fallback is evidenced.

### 4.2 Android-first sequencing under the simultaneous event

Android may be the first release after the event only when its independent closure is
complete:

- Google’s current target/build requirements are captured at the release date;
- the Android lock, app config, plugin output, generated manifest/build graph and artifact
  digest are bound together;
- the directly controlled Android device and the constrained/main cohorts exercise the
  changed native path, offline package, interruption, camera branch and safe recovery;
- TalkBack, largest text, non-color status and Turkish warning/hold/revalidation paths are
  accepted by an independent accessibility/safety process;
- Android signing, Play account, staged testing and incident-pause evidence are complete;
- the independent release verifier confirms that the artifact exactly matches the reviewed
  source, lock, config, generated output and evidence.

This does not close the iOS branch. If the same shared package/config change affects iOS,
the iOS development and release evidence remains a required future closure even though its
store publication is later.

### 4.3 iOS-later sequencing

iOS remains `HELD` until a real iOS build and evidence route exists. The route may be:

- a locally accessible Mac with the required Xcode/SDK/toolchain and reproducible recipe;
- a later-approved hosted Mac/build provider; or
- another provider-independent macOS environment that can reproduce and export the same
  reviewed artifact/provenance.

Borrowed iPhones provide useful device coverage but do not provide a build host, signing
authority or permanent availability. The iOS packet must separately cover the oldest and
current iPhone cohorts, VoiceOver, Dynamic Type/largest text, scene/lock/call/process
interruption, camera/photo removal or replacement, package reconciliation, signing and
App Store/TestFlight controls.

No iOS result is inferred from Android, from an iOS simulator, or from an Android-first
release.

## 5. Rebuild and invalidation matrix

The following matrix is the core closure oracle. “Affected platforms” means at least those
platforms must receive a new development build and revalidation; a shared input may make
both platforms affected.

| Change class | Minimum invalidation/rebuild action | Required evidence consequence |
|---|---|---|
| TypeScript/JavaScript-only presentation or domain change with proven unchanged native graph | Existing development client may support the bounded inner loop; final Android/iOS release artifacts are still rebuilt from the reviewed release inputs | Automated contract/state evidence may run before device evidence; no JS reload is a store or native pass |
| Add/update/remove package with native code or unknown native behavior | Regenerate affected native projects cleanly; new development build for each affected platform; final artifacts rebuilt | Lock/native sub-lock, SBOM, plugin/config diff, device/AT regression and provenance all reopen |
| Photo package replacement/removal | Treat as native until proven otherwise; rebuild every platform whose graph/permissions/config changed | Photo packet, privacy/permission evidence, old-data compatibility and both-platform parity reopen |
| `app.json`, `app.config.js/ts` or effective app-config change | Clean prebuild and new development builds for affected platforms | Effective config digest, generated diff, permissions/entitlements and signing/provenance reopen |
| Add/remove/update config plugin or plugin options/order | Clean prebuild and new development builds for every platform the plugin can modify | Plugin source/version/options/order, expected mods, generated output and security review are required |
| Prebuild/CNG template, Expo CLI, Expo SDK or RN line change | Clean regenerate Android/iOS outputs and rebuild both when the line is shared | Toolchain lock, all native diffs, compatibility matrix, two-platform device/AT evidence and exit impact reopen |
| Generated Android project, manifest, Gradle, resource, autolinking or native source change | New Android development build and Android release artifact | Android build graph, merged permissions, device/lifecycle/AT, signing and artifact digest reopen |
| Generated iOS project, Info.plist, entitlements, Podfile/SPM, resource, autolinking or native source change | New iOS development build and iOS release artifact | iOS build graph, privacy/capability declarations, device/lifecycle/AT, provisioning and artifact digest reopen |
| Custom Swift/Kotlin/Turbo Native Module spec, codegen, thread/lifecycle or permission change | Rebuild each platform implemented by the module; do not reuse the old client | Module contract, owner/fallback/EOL, native tests, accessibility and independent native review reopen |
| Android target/compile API, Gradle/AGP/JDK/NDK or Play requirement change | New Android generation/build; constrained/main Android and TalkBack evidence rerun | Play policy capture, generated manifest/build settings, signing/provenance and staged test evidence reopen |
| Xcode/Apple SDK/Swift/CocoaPods/macOS or App Store requirement change | New iOS generation/build on macOS or approved hosted Mac route; oldest/current iPhone and VoiceOver evidence rerun | Apple policy capture, project/Pod/entitlement diff, provisioning/signing, TestFlight/App Store evidence reopen |
| `eas.json`, local recipe, build image, environment or artifact path change | Re-run the affected build route; native rebuild if the effective native inputs change | Build recipe/image/environment digest, logs, artifact export and provider exit evidence reopen |
| Signing certificate, keystore/upload key, provisioning profile, team/bundle identity or Play/App Store metadata change | New signed platform artifact and release verification; native rebuild if entitlements/identifier change | Credential custody/rotation, identity continuity, artifact digest and store acceptance evidence reopen |
| Test fixture, safety copy, permission explanation or accessibility semantic change | Re-run automated and platform-specific acceptance; native rebuild if config/native output changes | Product/safety/AT review and parity matrix reopen; no documentary pass survives a changed oracle |

A native change must not be hidden behind “the JavaScript still runs.” Expo’s official
development-build guidance states that adding a native-code library or changing app config
requires rebuilding the development client; the workflow guidance also warns that changing
configuration or native code after the first build requires a rebuild. This exercise uses
that rule as a minimum, with an unknown-native-change default to `HELD`.

## 6. Platform evidence packets

### 6.1 Shared closure packet

The shared packet binds one semantic change to both platforms:

- state/authority contract: offline open, warning/readiness, optional photo, explicit
  durable checkpoint, `unknown/partial`, accessible revalidation, safe-stop/recovery and
  reconnect eligibility;
- package/content compatibility and recall/revocation oracle;
- no-photo and photo-pending meaning, with no technical verification claim;
- migration, privacy classification, export/disclosure and device-trust rules;
- requirement-to-task-to-test/evidence links and the platform parity matrix;
- changed dependency/config/native graph and the rebuild-trigger decision;
- independent product/safety review and separate validator identity.

The shared packet cannot close a missing platform row. Shared React/TypeScript code is not
evidence that Android and iOS behavior is identical.

### 6.2 Android evidence packet (Android first)

The Android packet must identify:

- exact source revision, package lock/native sub-lock, app-config digest, plugin inventory,
  prebuild tool/version and generated Android diff;
- Android toolchain versions and the exact changed target/compile/build requirement;
- development-build identity, final APK/AAB identity and cryptographic digests;
- package/manifest/permission/intent/resource/autolinking/native-module result;
- signing mode, keystore/upload-key or Play App Signing custody reference, package-name
  continuity and rotation/recovery record; raw private keys never enter the repository;
- constrained Android 10/API 29 and main Android 13+ real-device observations;
- TalkBack, largest text, focus/order, non-color status, warning/stop/recovery and Turkish
  copy observations;
- lock/call/background/process-kill/restart, camera denial/capture/removal, low-storage,
  constrained-network, 72-hour offline, package integrity and foreground reconciliation;
- explicit negative results: no auto-continue, no photo verification, no default 2 GB
  download, no push/background correctness dependency, no stale/recall authority;
- independent Android-native review, safety review, accessibility validation and release
  verification;
- Google Play account/test/staged-rollout and incident-pause evidence, when the release
  window actually requires them.

The owner’s Android phone is the directly controlled first path, not a substitute for the
constrained cohort, TalkBack, independent review or store evidence.

### 6.3 iOS evidence packet (later)

The iOS packet must identify:

- the same shared source/lock/config/plugin provenance and the iOS-specific generated diff;
- exact macOS/Xcode/Apple SDK/Swift/CocoaPods/SPM toolchain and the `APPLE-NEXT` rule;
- development-build identity, final IPA/archive identity and cryptographic digests;
- bundle identifier, build number, Info.plist/privacy declarations, entitlements, URL
  schemes, resource/autolinking/module result and capability continuity;
- distribution certificate/provisioning profile/team custody reference, rotation/recovery
  record and raw-secret exclusion;
- oldest iOS 16.4-capable and current standard iPhone real-device observations, using
  borrowed access only as an explicitly scheduled evidence source;
- VoiceOver, Dynamic Type/largest text, focus/order, non-color status, warning/stop/recovery
  and Turkish copy observations;
- lock/call/scene/background/suspension/termination/restart, camera denial/capture/removal,
  protected-data/restore behavior, constrained network, offline package and reconciliation;
- the same negative oracles as Android, with platform-specific failures recorded rather
  than averaged away;
- independent iOS-native review, safety review, accessibility validation and release
  verification;
- Apple Developer/App Store Connect/TestFlight evidence only when the iOS preparation or
  distribution window actually requires it.

No iOS packet can be closed by an Android artifact, a simulator, a borrowed phone without
an identified build/signing path, or a hosted log that cannot be exported and independently
verified.

### 6.4 Signing and provenance packet

For each platform and each candidate artifact, preserve:

- reviewed source revision and repository state;
- JS/package/native lock digests and SBOM;
- effective app-config and config-plugin inventory/options;
- prebuild/CNG tool version, input set and generated native diff;
- build host/provider, OS image, toolchain versions, environment class and build logs;
- artifact digest, format, version/build number and install/update identity;
- Android signing/Play identity or iOS certificate/profile/team identity references, with
  secret material held outside the repository;
- test/AT/device/safety evidence references bound to the exact artifact;
- independent verifier identity, approval, rollout, pause/revocation and recovery context.

Changing the optional photo dependency or a store build requirement changes the artifact
identity even when the store package name and signing key remain unchanged. If entitlements,
identifiers or signing credentials change, the credential/profile continuity and store
review obligations must be re-evaluated; no continuity is inferred.

## 7. Local, hosted and provider-independent recovery

### 7.1 Local Android path

The first preferred evidence path is a local Android toolchain on a host that can reproduce
the locked recipe and install on the owner’s Android phone. It must export the generated
diff, build logs, artifact, digest, SBOM and provenance. An Android local path does not
close iOS and does not eliminate the need for an independent verifier.

If the local Android host fails, retain the last safe artifact, record the exact failure and
re-run from the frozen lock/config/prebuild inputs on another controlled host. Do not repair
the owner’s workstation by guesswork, weaken the target requirement, or call a JavaScript
reload a build recovery.

### 7.2 Local iOS path if a Mac becomes available

If reliable Mac access is later confirmed, the local path must use the exact reviewed
Xcode/Apple SDK/toolchain, regenerate the native project, rebuild, install on scheduled
borrowed/current iPhones and produce exportable signing/provenance evidence. A free Apple
Account can support limited personal device testing according to Apple’s rules; App Store
distribution/TestFlight and store-governed release require the applicable Apple Developer
Program authority. The membership timing remains deferred under the approved project
constraint.

### 7.3 Hosted Mac/build path (optional, later, approval-gated)

EAS Build or another hosted service may be considered when a local iOS path is unavailable,
but the hosted route is not part of the current decision. Before use, the owner must receive
a current official price/limit sheet and a plain-language risk note covering:

- billing period, included capacity, queue/concurrency and build-time limits;
- usage-based charges, overage behavior, hard shutdown or cap controls and spend alerts;
- credential/signing custody, account roles, secret handling and revocation;
- source/config transfer, privacy/data location and log/artifact retention;
- artifact download/export, reproducible recipe and independent verification;
- provider outage, account loss, suspension and migration/exit path;
- whether the route requires an Apple/Google account or provider account before the relevant
  stage; and
- total impact on the future `TRY 2,000–3,000/month` non-store planning ceiling.

Expo’s official documentation describes local builds and hosted EAS builds as different
routes, and documents `eas build --local` as an optional way to run the EAS process on local
macOS/Linux infrastructure. That does not make EAS mandatory, remove the need for a Mac
for a local iOS native toolchain, or authorize a subscription. The current official Expo
pricing/billing pages must be consulted at the approval date; this exercise intentionally
does not transcribe a hosted-service price or treat a free tier as zero-risk.

### 7.4 Provider-independent continuity

The candidate remains recoverable only if the following are portable outside any one Expo,
EAS, CI or Mac provider:

- source and package/native lockfiles;
- effective app config and config-plugin source/options;
- prebuild inputs, generated Android/iOS diff and toolchain recipe;
- SBOM, artifact digests, build logs and acceptance evidence;
- portable API/content/data/migration/recall contracts and user media/provenance;
- signing custody references and documented rotation/recovery, without exporting raw private
  keys into an uncontrolled location;
- device/AT/safety/release oracles and the task graph.

The replacement route must rebuild from these portable inputs and produce a new, independently
verified artifact. A provider-hosted credential or generated file that cannot be exported,
audited or replaced is a material exit risk and keeps the route `HELD`.

### 7.5 Failure, hold and forward recovery

- If the photo replacement is incompatible, hold the optional capability or remove it via
  the reviewed P-Remove branch while retaining existing evidence and a safe manual path.
- If `APPLE-NEXT` or `GOOGLE-NEXT` cannot be met by the current dependency/toolchain line,
  retain the last safe compatible artifact, quarantine the affected release scope and hold
  the affected platform.
- If one platform closes and the other does not, release sequencing may keep Android first,
  but the overall mobile candidate remains `HELD` and iOS cannot be represented as closed.
- If a schema/data migration has already committed new valid data, do not claim that a
  binary downgrade reverses it. Use a tested forward migration/recovery, preserve history,
  revalidate authority and expose a user-visible hold/re-authentication path.
- If a build provider or host fails, switch only through the provider-independent recipe
  and evidence chain. Do not use OTA, Expo Go or a secret manual workstation as a shortcut.

## 8. Cost and approval triggers

This exercise records triggers, not a budget quote. Every amount not already approved by
the project control records remains `UNRESOLVED`.

| Trigger | Classification | Required owner decision/evidence |
|---|---|---|
| Planning/document research | Product-wide baseline | No incremental software spend is assumed. Any paid research/tool subscription needs current price, cap and approval. |
| Android local build with existing tools/device | Preferred low-cost path, not guaranteed free | Confirm host/tool availability and evidence capacity; no device/build purchase is implied. |
| iOS local build | Deferrable until iOS preparation | Confirm reliable Mac/Xcode access. If absent, prepare a priced hosted/alternate route; do not assume one. |
| Hosted Mac, EAS or other hosted build/CI | Optional convenience/external dependency | Current official price, billing, quota, overage, alerts, credential/data handling, artifact export, exit and provider outage plan must be approved before use. |
| Google Play release preparation | Mandatory store cost, deferred | The approved baseline is a one-time USD 25 registration fee, subject to rechecking regional/tax/currency terms at purchase. New personal accounts may also need the applicable closed-test process. |
| Apple iOS distribution/TestFlight | Mandatory store cost, deferred | The approved baseline is USD 99 per Apple Developer Program membership year, subject to rechecking local price/tax/renewal terms at the iOS release window. |
| Borrowed devices/testers | Preferred before purchase, capacity dependency | Confirm actual availability, schedule and evidence quality. Incentives, labs or new devices require separate approval. |
| TalkBack/VoiceOver and qualified safety/content review | Product-wide mandatory evidence | If required authority/capacity is unavailable, the affected release remains `HELD`; a cheaper unqualified substitute is not accepted. |
| Backend/storage/egress/backup/telemetry/security tooling | Product-wide or scale-triggered | Use current provider prices only after provider selection; show caps, overage shutdown, export and migration path. |
| Extra build concurrency, large workers, artifact retention or paid support | Optional/scale-triggered | Compare against the future TRY ceiling and approve a bounded route; do not silently increase a plan. |
| Framework exit or dual-client migration | Contingency/exit cost | Preserve portable contracts and fixtures; do not invent a one-click migration or cost. |

The future `TRY 2,000–3,000/month` value is a planning ceiling for non-store operating
costs only. It does not authorize a hosted build, EAS plan, CI, backend, device, tester,
reviewer, domain or monitoring purchase. Store fees remain separately governed by the
approved store-cost decision unless a later budget sheet explicitly combines them.

## 9. Closure acceptance oracle and HELD semantics

### 9.1 Closure may be marked `PASS` only when

This exercise is not currently at `PASS`. A future evidence owner could close the exercise
only when all of the following are independently evidenced:

1. The photo branch is explicitly selected as replace or remove, with no photo-verification
   semantic leak and with existing photo/evidence continuity preserved.
2. Direct and transitive JS/native locks, native sub-locks, app config, effective config,
   config-plugin inventory, prebuild inputs and generated Android/iOS outputs are exact,
   reviewable and bound to the candidate artifacts.
3. The simultaneous Apple/Google requirement event is rechecked from current official
   sources, and the chosen Expo/RN/toolchain line satisfies the affected platform rules.
4. Every rebuild trigger in Section 5 is applied conservatively; no changed native graph
   reuses an old development client or release artifact.
5. Android evidence closes on the owner-controlled device plus required constrained/main
   cohorts, including TalkBack, interruption, offline/reconciliation, photo branch and
   signing/provenance evidence.
6. iOS evidence closes later on real oldest/current iPhones, with an identified Mac or
   approved hosted route, VoiceOver/Dynamic Type, interruption, photo branch and
   signing/provenance evidence.
7. The build route exports enough source/config/lock/generated/artifact/provenance evidence
   for independent verification and provider replacement.
8. Safety/content, privacy/security, Android/iOS native, accessibility, release and
   incident/recovery authorities remain separate and accountable.
9. Every paid route has a current official price and billing/cap/overage/exit record,
   explicit owner approval and a safe hold when the ceiling or evidence is unavailable.
10. Migration/rollback refusal, forward recovery, recall/compatibility and safe-stop paths
    are exercised without treating a photo, cache, notification or restored UI as physical
    truth.

### 9.2 Conditions that keep the candidate `HELD`

- no reliable iOS build host or approved hosted route;
- borrowed iPhone access without a schedule, artifact identity or independent tester;
- unknown native behavior, unnamed config plugin, stale generated output or missing lock;
- changed Apple/Google rule without a current evidence capture;
- missing Android/iOS real-device or VoiceOver/TalkBack evidence;
- opaque signing custody, missing artifact digest, incomplete SBOM or unverifiable provenance;
- provider cap/overage/export/exit or cost approval not closed;
- no named native/security/EOL/safety/accessibility/release/recovery owner;
- a photo presented as verification, an old client used after a native change, Expo Go or
  OTA proposed as a shortcut, or a binary rollback used to conceal irreversible data change.

`HELD` is an honest release/capability state, not a failure of the owner and not an
invitation to lower the standard. The owner may approve sequencing and spending only after
the affected evidence and costs are made concrete in nontechnical language.

## 10. Current exercise result

**Result:** `OPERABLE WITH MATERIAL CONDITIONS / HELD`

The RN/Expo candidate has a conceptually explicit native-dependency, config-plugin,
prebuild/generated-project, rebuild, platform-evidence and provider-exit boundary. The
exercise also shows how Android-first publication can proceed before iOS when Android’s
independent evidence closes. It does not establish that the boundary is reproducible,
affordable, accessible, safe or releasable.

No framework is selected. No ADR, implementation, EAS account, hosted build, OTA channel,
subscription or store submission is authorized. The tie-break remains `HELD` until the
same closure evidence is produced for the competing finalist under the common fixture.

## 11. Primary and internal sources

### 11.1 Official/primary technical sources consulted 2026-09-18

- [Expo development-build introduction](https://docs.expo.dev/develop/development-builds/introduction/) — development-build choices, local/hosted routes, prebuild and rebuild triggers.
- [Expo development-build FAQ](https://docs.expo.dev/develop/development-builds/faq/) — fixed native library set in Expo Go and app-specific native builds.
- [Use development builds](https://docs.expo.dev/develop/development-builds/use-development-builds/) — native-code dependency changes require rebuilding the development client.
- [Expo workflow overview](https://docs.expo.dev/workflow/overview/) — local versus cloud builds, CNG and rebuild behavior.
- [Continuous Native Generation](https://docs.expo.dev/workflow/continuous-native-generation/) — clean prebuild, generated native projects and package-manager inputs.
- [Config plugins introduction](https://docs.expo.dev/config-plugins/introduction/) and [config-plugin creation/use](https://docs.expo.dev/config-plugins/plugins/) — app-config/plugin/modification boundary and generated native output.
- [Expo permissions guide](https://docs.expo.dev/guides/permissions/) — native build-time permission configuration for development/standalone builds.
- [Expo SDK reference/version matrix](https://docs.expo.dev/versions/latest/) — the dated SDK 57 Android/iOS/toolchain matrix used as the baseline snapshot.
- [Expo local builds](https://docs.expo.dev/build-reference/local-builds/) — local EAS route, prerequisites and limitations; not a requirement to use EAS.
- [Expo app credentials](https://docs.expo.dev/app-signing/app-credentials/) and [local credentials](https://docs.expo.dev/app-signing/local-credentials/) — Android/iOS signing credential classes and custody options.
- [Expo EAS pricing](https://expo.dev/pricing) and [billing plans](https://docs.expo.dev/billing/plans/) — current plan/cap/usage behavior to be rechecked before any hosted approval; no project quote is asserted here.
- [Apple Developer Program membership](https://developer.apple.com/support/compare-memberships/) — USD 99 membership-year baseline and free-account versus distribution distinction.
- [Apple upload-build guidance](https://developer.apple.com/help/app-store-connect/manage-builds/upload-builds) and [upcoming requirements](https://developer.apple.com/news/upcoming-requirements/) — current upload/build SDK requirements and their changeability.
- [Google Play target API requirement](https://developer.android.com/google/play/requirements/target-sdk) — current API 36 requirement and future recheck obligation.
- [Google Play personal-account testing requirements](https://support.google.com/googleplay/android-developer/answer/14151465?hl=en) — closed-testing requirement for applicable new personal accounts.
- [Google Play registration/EEA conditions](https://support.google.com/googleplay/android-developer/answer/14659200?hl=en) — USD 25 one-time registration baseline and identity requirements.
- [React Native platform-specific code](https://reactnative.dev/docs/platform-specific-code), [accessibility](https://reactnative.dev/docs/accessibility) and [AppState](https://reactnative.dev/docs/appstate) — explicit platform/lifecycle/accessibility boundaries; these are affordances, not acceptance passes.

### 11.2 Internal controls and predecessor evidence

- [[00_CONTROL/DECISION_LOG#DEC-0031 — Mobile Evaluation Method and Common Fixture]]
- [[00_CONTROL/DECISION_LOG#DEC-0032 — Android-First Staged Release and Owner Resource Envelope]]
- [[04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS]]
- [[04_TECH_STRATEGY/DEBATES/DEBATE-006__DOSSIER_REACT_NATIVE_EXPO]]
- [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_SPEC]]
- [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_REACT_NATIVE_EXPO]]
- [[04_TECH_STRATEGY/DEBATES/DEBATE-006__TASK_SIM_MOB_001_AUDIT_AND_JUDGE]]
- [[04_TECH_STRATEGY/DEBATES/DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE]]

All external facts in this document are dated and must be rechecked at the actual build or
store window. Internal links describe approved working controls, not an ADR or framework
selection.
