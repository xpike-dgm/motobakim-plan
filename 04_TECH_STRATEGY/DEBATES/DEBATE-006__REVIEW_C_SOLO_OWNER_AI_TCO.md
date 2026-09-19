# DEBATE-006 — Reviewer C: Solo Owner, AI Operability & 24-Month TCO

Status: INDEPENDENT REVIEW / COMPLETE RESEARCH SYNTHESIS / NO-CODE / NOT ADR / HELD  
Review date: 2026-09-18  
Reviewer: Reviewer C  
Scope: Flutter, React Native + Expo, KMP-native, KMP + Compose Multiplatform, and fully native Android + iOS  
Review boundary: comparative review of the five structurally complete candidate dossiers against the common fixture. This document does not select a framework, create an ADR, assign a Gate result, or promote any candidate from HELD.

## 1. Review purpose and non-negotiable limits

This review answers a narrow question: which candidate leaves the most controllable work surface for a nontechnical solo owner who delegates bounded implementation, review, and validation work to AI, while preserving two-platform parity, safety, accessibility, release, and data-continuity obligations over the first release plus 24 months?

The review uses evidence already captured in the controlled candidate dossiers and the common fixture. It is not an implementation report. No code, prototype, real-device pass, assistive-technology pass, store submission, qualified safety review, or production cost quote is claimed.

The following constraints apply equally to all five candidates:

- Product scope is Android and iOS consumer use plus browser-based internal operations.
- Both stores are planned; store fees are deferred to release preparation.
- The horizon is first release plus 24 months, with four release windows per year plus an unplanned safety-correction window.
- The owner is not assumed to be a developer, debugger, architect, release engineer, safety reviewer, accessibility authority, or store/legal authority.
- AI cannot replace physical-device testing, assistive-technology testing, qualified safety/content review, store authority, legal/privacy authority, or user repair of a broken build.
- Offline, lifecycle, backup/restore, conflict, recall/withdrawal, media, key, notification, deep-link, scoped-transfer, and release obligations are common fixture obligations.
- No unapproved paid subscription, hosted build, contractor, cloud, device purchase, monitoring service, AI provider, or legal/vendor service is silently included.

All five candidate dossiers are documentary research only. Their S1–S15 records remain 0 PASS / 15 HELD / 0 REJECT, and the common rule binds every device-sensitive claim to all four cohorts: constrained Android, main Android, oldest supported iPhone, and current iPhone.

## 2. Evidence basis and control interpretation

Primary control documents read:

- DEC-0028 — machine-verifiable graph, narrow contracts, ownership, validation evidence, and no technology selection by task planning.
- DEC-0029 — nontechnical-owner constraints; bounded AI-operability; deterministic tooling; explicit external authority; no user repair/debug/build repair.
- DEC-0030 — solo-founder economics; mandatory/deferrable/optional/scale costs; explicit free-tier caps, alerts, export, and exit; approved store baseline only.
- DEC-0031 — common five-way fixture, S1–S15 pass/hold/reject rules, four-cohort device coverage, no-code boundary, and no simulator/AI substitution for real-device or qualified authority.
- DEBATE-006 common fixture and operating assumptions — product, workload, device, network, offline, lifecycle, media, safety, privacy, release, and cost constants.
- DEBATE-006 technology evidence and TCO brief — equal candidate boundary, native closure, AI-operability questions, and 15 TCO categories.
- DEBATE-006 candidate dossier template — required S1–S15, accessibility, forced events, AI-operability, TCO, exit, and result fields.
- DEBATE-006 dossier equivalence audit — structural recheck of all five dossiers; no critical finding and no approved candidate ranking.

Candidate evidence reviewed:

- [Flutter dossier](DEBATE-006__DOSSIER_FLUTTER.md)
- [React Native + Expo dossier](DEBATE-006__DOSSIER_REACT_NATIVE_EXPO.md)
- [KMP-native dossier](DEBATE-006__DOSSIER_KMP_NATIVE.md)
- [KMP + Compose Multiplatform dossier](DEBATE-006__DOSSIER_KMP_COMPOSE.md)
- [Fully native dossier](DEBATE-006__DOSSIER_FULL_NATIVE.md)

The dossiers use current official/primary source snapshots, but a snapshot is not a proof of future support. “Current” below means the captured source/date in the dossier, not a promise that the ecosystem will remain unchanged.

## 3. Comparative result at a glance

### 3.1 No unconditional ordering is supported

There is no evidence-supported unconditional winner for the solo-owner problem. The evidence supports two conditional workload groups:

| Conditional group | Candidates | What the group shares | What prevents an internal ordering |
|---|---|---|---|
| Shared application-surface group | Flutter, React Native + Expo, KMP + Compose Multiplatform | A routine UI/application change can potentially be represented once across the two mobile platforms, reducing ordinary parity edits. | Each still has a native host/plugin/module boundary; iOS accessibility, lifecycle, generated-project, dependency-lock, and release evidence is unresolved. RN browser adjacency is only a hypothesis; Compose iOS semantics and Flutter/RN native closure are not implementation-proven. |
| Two-platform ownership group | KMP-native, fully native Android + iOS | Platform behavior is explicit and each platform can use direct APIs; KMP-native shares domain/data while fully native has no cross-platform runtime. | KMP-native adds KMP/Native framework and iOS integration ownership; fully native duplicates the complete product graph, UI, and release correction path. The evidence does not justify trading one burden for the other without owner capacity and toolchain evidence. |

This is a conditional ordering of work-surface shape, not a score, recommendation, or Gate decision. If the decision criterion weights ordinary shared-UI parity work most heavily, the first group has the lower routine duplication surface. If the criterion weights direct platform transparency most heavily, the second group reduces hidden cross-platform runtime behavior but increases explicit two-platform ownership. The common fixture does not provide enough evidence to order candidates inside either group.

### 3.2 Five-way axis matrix

| Candidate | Bounded AI task execution | Deterministic tooling today | Native exception/integration load | Dependency cadence exposure | Browser/internal-ops adjacency | Two-platform parity burden | Mac/device/external authority load | Exit burden |
|---|---|---|---|---|---|---|---|---|
| Flutter | Dart UI/domain tasks can be bounded; plugin/channel and host tasks need separate native context and review. | Frozen Flutter/Dart snapshot is documented; lockfile, generated outputs, native dependency closure, and iOS build evidence remain HELD. | Explicit Flutter plugin and host boundary for camera, files, share, keys, background, lifecycle, notifications, and deep links; selected plugin set is not a closure proof. | Flutter SDK and pub/plugin cadence plus Android/iOS native toolchain cadence; snapshot drift is already visible in the documented release line. | No verified shared browser-ops code path; Dart mobile surface and browser operations remain separate in the dossier. | Lower routine shared-UI duplication, but native boundary can create hidden parity gaps. | Same mandatory Mac/iOS, devices, AT, store, safety, privacy, and release authorities; Flutter/plugin issues add review context. | Flutter renderer/runtime, plugin/channel contracts, native host code, and portable data/contracts must be separated. |
| React Native + Expo | TypeScript/React tasks can be bounded; config-plugin, generated native project, module, and dev-build tasks need distinct context. | Top-level versions and SDK matrix are pinned; transitive lock/hashes, prebuild output, config-plugin output, EAS/CI path, and signing evidence remain HELD. Expo Go is not a production path. | Expo modules, config plugins, prebuild/generated projects, Turbo Native Modules, and direct Android/iOS exceptions; AppState is only a signal, not correctness. | Expo SDK/RN/React/Node and module cadence plus native toolchain; hosted EAS is optional but introduces provider/account/cost/exit questions. | Strongest potential adjacency through TypeScript/React browser operations, but the dossier explicitly marks it as an unverified hypothesis and keeps trust domains separate. | Lower routine shared-UI duplication; generated/native exceptions can reintroduce platform divergence. | Same mandatory external authorities; additionally an unresolved choice between local development builds and hosted EAS/CI. | React Native/Expo runtime, config plugins, generated projects, modules, and any hosted build coupling must be removed or replaced. |
| KMP-native | Kotlin shared domain/data tasks can be bounded; Android and iOS UI/release tasks are separate contexts. | Kotlin/KMP and compatibility ranges are documented; dependency locks, generated iOS framework, Gradle/Xcode integration, and two build graphs remain HELD. | Native UI is first-class rather than an exception, but the KMP/Native generated-framework boundary is an integration surface. | Kotlin/KMP, Gradle/AGP, Xcode/Swift and selected native dependency cadences; two UI toolchains plus generated framework. | Shared Kotlin logic does not establish shared browser UI or browser-ops code; no current proof of that adjacency. | Shared domain/data can reduce invariant duplication; Android/iOS UI and accessibility parity are explicitly duplicated. | Same mandatory external authorities; Mac/Xcode and generated-framework integration are additional owner/reviewer work. | Shared KMP source, generated framework, native UI, and build integration are bound; data schema/fixtures/contracts are portable. |
| KMP + Compose Multiplatform | Kotlin/domain and shared Compose UI tasks can be bounded; iOS host/interop and platform-exception tasks need separate context. | Kotlin 2.4.20, Compose Multiplatform 1.12.0, Compose compiler 2.4.20 and compatibility ranges are captured; locks, generated framework, iOS host, and release proof remain HELD. | Shared Compose UI reduces ordinary duplicate screens, but iOS host/interop, semantics/traversal, high contrast, camera/files/share/keys/background/lifecycle remain native closure work. | Kotlin/KMP, Compose Multiplatform, Compose compiler/Jetpack, Gradle/AGP, Xcode and native dependency cadences interact; iOS accessibility uncertainty is material. | Compose can have other targets, but the fixture is mobile and no browser-ops sharing proof is supplied. Treat as possible, not established. | Lower routine shared-UI duplication; a single shared UI can hide platform semantic/rendering differences unless both platforms are tested. | Same mandatory external authorities; generated iOS framework, Xcode, and AT review are high-value external dependencies. | Kotlin/Native/Compose runtime, shared UI, generated framework, host/interop, and native exceptions are bound; schemas/contracts/fixtures are portable. |
| Fully native | Android/Kotlin and iOS/Swift tasks can each be bounded, but every feature has two implementation/review/validation contexts. | Reference Android and iOS toolchains are explicit; two independent graphs, signing, dependency locks, and real build artifacts remain HELD. | Direct platform APIs reduce hidden cross-platform runtime/plugin behavior; camera/files/keys/background/lifecycle/notifications/deep links are native on each side. | Android SDK/AGP/Gradle/Kotlin and iOS SDK/Xcode/Swift/SPM cadences are independent; no cross-platform framework cadence, but two release timelines. | No shared browser-ops implementation evidence; only portable contracts/data can be shared. | Highest explicit duplication: domain/UI/semantics/tests/release corrections must be kept equivalent across Android and iOS. | Same mandatory external authorities, applied to two full native release paths; no hosted framework is required but Mac remains required for iOS. | Two native graphs/toolchains/signing paths and their parity history must be retained or rewritten; portable data/contracts reduce lock-in but do not remove code burden. |

### 3.3 What this matrix does not claim

- “Lower routine duplication” is not “lower total cost.” Native exceptions, test coverage, dependency churn, and release evidence can reverse the practical burden.
- “Direct platform APIs” is not “automatically safer.” Safety depends on the same acceptance, negative-case, physical-device, AT, and qualified-review evidence for every candidate.
- “Browser adjacency” is not shared code until a boundary, ownership model, build graph, test graph, and security/trust-domain decision are documented.
- “Frozen version” is not reproducibility until lockfiles, transitive artifacts, generated native output, toolchain images, signing, and provenance are captured.

## 4. Solo-owner and AI-operability review

### 4.1 Operating model used for this review

The useful unit is a bounded change packet, not an AI chat turn. A candidate is more operable when one packet can name:

1. one authoritative starting state;
2. one allowed transition and one narrow change surface;
3. explicit contracts, design references, acceptance criteria, negative cases, and rollback;
4. deterministic local validation plus machine-readable evidence;
5. a named human/external authority for anything AI cannot certify;
6. a closure path for generated files, native artifacts, signing, release, and migration.

The owner should be able to approve an outcome and risk decision. The owner should not be asked to diagnose an Android/iOS build, infer a hidden lifecycle race, repair a signing chain, or certify safety/accessibility from a simulator or AI output.

### 4.2 Bounded AI task shape by candidate

| Candidate | Tasks that can be bounded from current evidence | Tasks that cannot be delegated as one bounded packet | Review consequence |
|---|---|---|---|
| Flutter | Shared Dart UI state, domain transformations, fixtures, validation rules, and platform-independent tests, subject to the common contracts. | Flutter plugin registration, platform channels, Android lifecycle/background work, iOS URLSession/BGTask behavior, entitlements, signing, native dependency changes, and physical/AT validation. | Split every feature touching a plugin or lifecycle into Dart packet, Android packet, iOS packet, and external validation packet. |
| React Native + Expo | TypeScript/React UI/state, fixtures, pure logic, and module calls behind documented interfaces; local development-build configuration can be separately bounded. | Expo config plugins, prebuild output, generated native project edits, Turbo Native Modules, background task correctness, EAS/CI, signing, and native package resolution. | The apparent single JS/TS packet is unsafe when it changes generated/native state. Keep generated output reproducible and reviewed. |
| KMP-native | Shared Kotlin domain/data, serialization boundary once selected, repository rules, fixtures, and cross-platform invariants. | Android UI and lifecycle, iOS UI and lifecycle, generated KMP framework integration, Gradle/Xcode linkage, signing, and two-platform acceptance/AT. | Shared core reduces one class of duplicate packet, but every user-visible feature still has two UI packets and two validation paths. |
| KMP + Compose | Shared Kotlin domain/data, shared Compose UI/state, semantics declarations, and common fixtures when the API is common and stable. | iOS host/interop, Compose-to-iOS semantics mapping, high contrast, native media/file/share/key/background behavior, generated framework, signing, and physical/AT validation. | The shared packet must carry platform-specific proof obligations; a visually identical shared screen is not proof of equal semantics. |
| Fully native | Each Android or iOS UI/domain task can be bounded against direct platform contracts; platform-specific tests and fixtures can be explicit. | Parity across the two independent implementations, two release graphs, signing, physical/AT validation, and any cross-platform data/migration invariant. | Every feature doubles the implementation/review/validation packet unless a canonical contract and fixture set are machine-checked on both sides. |

### 4.3 Determinism and reproducibility gates

The following artifacts are decisive for AI-operability but are not present as implementation evidence in the dossiers:

- exact SDK/toolchain manifests and checksums;
- package/dependency lockfiles and transitive artifact provenance;
- generated native project/framework outputs from a clean checkout;
- reproducible debug and release build commands;
- machine-readable test, accessibility, privacy, SBOM, and signing evidence;
- canonical design-system/state references and requirement-to-task-to-test links;
- a bounded rollback path for data schema, cached media, local keys, and staged release;
- spend caps, alerts, export, and shutdown/exit controls for any hosted or cloud path.

Current deterministic-tooling comparison:

- Flutter has a compact Dart/Flutter shared surface, but the dossier still holds lock/native dependency/generation proof.
- RN + Expo has a useful version snapshot, but config-plugin/prebuild/generated-project determinism and hosted/local build choice are unresolved.
- KMP-native and KMP-Compose have captured Kotlin and compatibility ranges, but Gradle/Xcode/generated-framework reproducibility remains unresolved; Compose adds an additional UI/compiler compatibility surface.
- Fully native has the clearest direct platform ownership boundary, but it must reproduce two complete build graphs and preserve parity evidence.

No candidate has passed this gate. “Deterministic today” therefore means “the evidence points to a determinism plan,” not “a reproducible build was observed.”

### 4.4 Native exception and authority load

All five candidates require native closure for at least camera, file selection, export/share, local secure storage/keys, notifications/deep links, lifecycle/process death, foreground reconciliation, and store signing. The difference is where that work appears:

- Flutter and RN + Expo place a meaningful portion behind framework/plugin/module boundaries. This can reduce routine feature code but makes plugin version, generated output, and host behavior part of each affected packet.
- KMP-native makes Android/iOS UI native by design. The burden is visible and duplicated, while KMP/Native framework generation and linkage become a shared-core boundary.
- KMP + Compose makes more UI shared, but native host/interop and iOS semantics are still authority-bearing. The iOS high-contrast and semantic mapping holds are not cosmetic defects.
- Fully native has fewer hidden framework exceptions and direct platform APIs, but it creates two complete owner/reviewer/build/release paths. Directness does not remove the authority load; it distributes it twice.

The following authorities remain outside AI delegation for every candidate: physical-device and network validation, assistive technology, store policy/signing, qualified safety/content review, privacy/legal interpretation, backend/provider operation, and final incident/release accountability.

## 5. Candidate-specific comparative findings

### 5.1 Flutter

The dossier records Flutter 3.47.2 and Dart 3.13.2 with a shared Dart UI/domain surface, explicit Android/Kotlin and iOS/Swift host boundaries, and a captured package snapshot for common media/file paths. This is a reasonable bounded-task shape for pure Dart work.

The solo-owner risk is not the ordinary Dart packet. It is closure: plugin registration and cadence, platform channels, background/lifecycle semantics, iOS entitlements and signing, generated/native dependency state, and the absence of a selected final persistence/serialization/key design. Each such feature must be split into a shared packet, platform packets, and physical/AT/release evidence. The dossier does not prove a real device or clean-build pass.

Flutter offers no documentary proof that the browser Internal Ops surface shares a trustworthy code boundary with the mobile app. Treating the two as one AI workstream would be an unsupported expansion of scope. Exit is plausible at the data/contract/fixture layer, but Flutter renderer/plugin/host code is framework-bound.

### 5.2 React Native + Expo

The dossier records Expo SDK 57.0.22, React Native 0.86.3, React 19.2.3, Expo CLI 57.0.25, Node 22.13.x, and native module snapshots. TypeScript/React work can be bounded, and browser adjacency is the strongest potential among the five because internal browser operations are also described as TypeScript/React. That adjacency is explicitly a hypothesis, not evidence of shared packages, trust domains, release coupling, or parity.

Expo Go is excluded from production. The actual path is a development build with config plugins/prebuild or direct native changes. Therefore the generated Android/iOS projects, native module versions, prebuild output, EAS-versus-local build choice, signing, and clean-build artifacts are part of the candidate closure. AppState and similar JS signals cannot certify background correctness. The apparent low-friction JavaScript packet is not sufficient for a camera/file/key/background/release feature.

RN + Expo can be conditionally attractive only if the browser adjacency is proven and the local/hosted build authority is bounded. An EAS or other hosted path cannot be treated as free or mandatory until current pricing, caps, alerts, export, data retention, and exit are verified. None of those prices are invented here.

### 5.3 KMP-native

The dossier records Kotlin Multiplatform 2.4.20 with shared Kotlin domain/data and separate native Android and iOS UI. This gives AI one shared invariant surface while keeping platform UI and lifecycle behavior explicit. It is materially distinct from KMP + Compose: Compose is not shared here.

The cost is a two-UI parity contract plus KMP/Native generated-framework and Gradle/Xcode integration. A shared core is valuable only if the generated framework, dependency locks, iOS linkage, and cross-platform fixtures are reproducible. UI/accessibility, lifecycle, media, and release corrections still occur twice. The evidence does not establish shared browser-ops code.

For a solo owner, KMP-native sits in the two-platform ownership group: less domain duplication than fully native, but more cross-platform compiler/framework integration than fully native. It cannot be ordered against fully native without knowing whether the owner has reliable Kotlin/Gradle and Swift/Xcode review capacity.

### 5.4 KMP + Compose Multiplatform

The dossier records Kotlin 2.4.20, Compose Multiplatform 1.12.0, Compose compiler 2.4.20, and the associated compatibility range, with shared Kotlin/domain/data and shared Compose UI hosted on Android and iOS. This offers the smallest routine UI parity surface on paper.

The decisive hold is semantic and native closure, not visual reuse. Compose semantics/traversal and their iOS mapping, high contrast behavior, native camera/file/share/key/background functions, lifecycle/process death, generated framework, and Xcode/signing all require platform evidence. An AI-produced common Composable is not evidence that VoiceOver and TalkBack expose equivalent roles, order, actions, focus, and contrast.

Compose Multiplatform may have other targets, but the current fixture provides no browser-ops sharing proof. Treating future web reuse as a present TCO saving is unsupported. Exit remains portable at schemas/contracts/fixtures, while Kotlin/Native/Compose runtime and generated-host code are bound.

### 5.5 Fully native Android + iOS

The dossier records an explicit Android reference toolchain (Android Studio/AGP/Gradle/Kotlin/JDK/SDK/NDK) and iOS reference toolchain (Xcode/Swift/iOS SDK/macOS), with direct platform APIs and no cross-platform framework. The final Android UI choice (Compose/Views) and final iOS UI choice (SwiftUI/UIKit) remain unresolved in the dossier; this is a real decision surface, not a detail to infer.

Direct native APIs make platform exceptions visible and reduce framework-plugin indirection. They also create two complete product graphs: domain/data, UI, lifecycle, accessibility, tests, release, signing, crash evidence, and incident correction. A solo owner must either maintain parity through canonical contracts and machine-checked fixtures or accept repeated AI context and reviewer load.

Fully native belongs in the two-platform ownership group. It may be operationally preferable when direct platform evidence and an existing Android/iOS owner are available; it is not a low-burden default for a nontechnical solo owner. The dossier contains no implementation or device pass.

## 6. 24-month TCO review

### 6.1 Accounting rule

TCO is treated as a control worksheet, not as a guessed total. Shared product obligations are kept separate from candidate-caused work and exposure. Optional convenience is not silently promoted to mandatory spend. Scale-triggered work is shown as a trigger, not as a launch forecast. Every unknown amount is UNRESOLVED and is never treated as zero.

The only approved monetary baseline in this review is the store baseline from DEC-0030/common fixture:

- Google Play Console: USD 25 one time.
- Apple Developer Program: USD 99 per membership year.
- Both stores over a 24-month comparison horizon: USD 124–223 before tax, currency effects, and renewal timing.

The store baseline is a product-wide release obligation, not a candidate advantage. No other numeric price is asserted.

### 6.2 Equal workload quantities

These are capacity quantities from the common fixture, not provider prices and not a retention promise. The local-device photo stress fixture is not multiplied by MAU.

| MAU tier | Required compact transfers/month | Required compact transfers/24 months | Optional media/month | Optional media/24 months | Photo uploads/month | Photo uploads/24 months |
|---:|---:|---:|---:|---:|---:|---:|
| 1,000 | About 24 GB | About 576 GB | About 10 GB | About 240 GB | About 1.5 GB | About 36 GB |
| 10,000 | About 240 GB | About 5.76 TB | About 100 GB | About 2.4 TB | About 15 GB | About 360 GB |
| 50,000 | About 1.2 TB | About 28.8 TB | About 500 GB | About 12 TB | About 75 GB | About 1.8 TB |

The arithmetic assumes two 12 MB compact transfers per MAU per month, optional media for 10% of MAU at a 100 MB average transfer, and 0.5 new 3 MB user photos per MAU per month. Retries, backups, replication, egress copies, moderation, legal retention, and deletion windows remain unresolved.

### 6.3 Shared product-cost envelope

The first column describes obligations that exist regardless of the mobile framework. The second column isolates candidate-caused work or exposure; it is not a price.

| Cost row | Product-wide unavoidable | Candidate-caused delta across the five dossiers | Optional convenience | Scale-triggered | Exit/contingency | Free/capped path | Amount/confidence |
|---|---|---|---|---|---|---|---|
| Store membership | Both planned stores, legal account ownership, signing, policy compliance, and release evidence | No framework-specific fee is evidenced | None pre-approved | Additional testers, staged releases, renewal count | Preserve legal/store identity and artifact history | No free bypass assumed | Approved baseline only: Google USD 25 once; Apple USD 99/year; USD 124–223 over 24 months before tax/currency. High for baseline; recheck at purchase. |
| Mac/hosted build | An Apple build path is required for iOS distribution and validation | Flutter plugin/host build; RN/Expo generated native build and possible EAS; KMP framework/Xcode linkage; fully native second platform graph | Hosted build/CI is convenience unless separately approved | Parallel builds, artifact retention, release windows | Local Xcode recipe and exportable artifacts; provider replacement | Local path only if Mac/account/capacity exists; hosted caps, prices, alerts, export and exit are unresolved | UNRESOLVED; no hosted/Mac price invented. |
| Android/iPhone access | Four-cohort device and AT evidence, replacement access, and network/lifecycle testing | Shared-UI candidates still need both native surfaces; native candidates need two full test paths | Additional lab devices or specialist lab | More OS/device cohorts, locales, releases, and testers | Borrow/replace devices; retain portable test records | Borrowed/local devices where evidence quality holds | UNRESOLVED. |
| CI/build artifacts | Reproducible debug/release evidence, signing, SBOM/provenance, and retention | Flutter SDK/plugin artifacts; RN/Expo prebuild/module artifacts; KMP generated framework; fully native two graphs | Hosted CI, artifact dashboard, or paid cache | More release branches, corrections, artifacts, and retention | Export lockfiles, SBOM, logs, artifacts, and local build recipe | Local/capped CI only with caps, alerts, export, and exit | UNRESOLVED. |
| Backend/database | API authority, sync, audit, migration, conflict, and correction history | Client adapters/offline reconciliation differ; no candidate has selected a final server/database | Managed provider features | MAU, sync/query/conflict/incident volume | Portable schema, API contracts, migration exports | Free/provider tier only after quota, overage, alert, export, shutdown, and exit evidence | UNRESOLVED; no provider or price selected. |
| Storage/backup/CDN/egress | Package media, user photos, backups, outbound transfer, and continuity | Client staging/retry/caching behavior differs; no server price assigned to a candidate | CDN/media optimization, replication, premium backup | Workload quantities above plus retries, copies, and retention | Export originals/manifests/provenance; provider migration and deletion procedure | Capped storage/egress only with retention, overage, alert, export, and exit controls | UNRESOLVED; quantities are not prices. |
| Identity/email/SMS | Account/re-auth, recovery, notification, and entitlement choices | Secure local key/device binding and re-auth surface differ by client boundary | SMS or transactional email convenience | Account/recovery volume and abuse controls | Portable account mapping and manual recovery route | Account-light first value; no SMS provider assumed | UNRESOLVED. |
| Crash/telemetry/analytics | Minimal operational signals, privacy minimization, and incident evidence | Plugin/module/native lifecycle diagnostics vary; full native has two native signal paths | Third-party dashboard or premium retention | Device/version/event volume | Export minimal privacy-filtered evidence and runbooks | Local/self-hosted/capped option only after retention/exit evidence | UNRESOLVED. |
| Security/SBOM/signing | Supply-chain review, key custody, vulnerability response, provenance, and rotation | Flutter package/plugin graph; RN/Expo package/module/config-plugin/generated graph; KMP/Kotlin/Compose/Gradle graph; native Android/iOS graphs | Paid scanning, signing, or security support | More dependencies, releases, advisories, and artifact sets | Portable SBOM, locks, provenance, signing records, and key-rotation evidence | Free tools possible only with verification owner and export | UNRESOLVED. |
| Accessibility validation | Real-device TalkBack/VoiceOver, keyboard/focus where applicable, content/contrast, and qualified AT evidence | Flutter/RN semantics and native bridge; KMP-Compose iOS semantics/high contrast; KMP-native/full-native two UI oracles | External accessibility lab or specialist | More devices, locales, releases, and regressions | Portable accessibility oracle, copy, tokens, and defect evidence | Borrowed devices/external testers only if evidence quality holds | UNRESOLVED. |
| Safety/content review | Qualified content review, correction/withdrawal/recall authority, safe stop, and provenance | Candidate must expose stale/unknown/held states and preserve recovery; no framework removes this | Additional review tooling or specialist capacity | Four planned windows plus emergency safety/security correction | Portable content provenance, acceptance records, and pause procedure | No AI-only or unqualified substitute | UNRESOLVED. |
| AI implementation/review | Controlled implementation, independent review, validation capacity, and task/evidence graph | Shared-UI candidates reduce routine duplicate packet count but add framework/native closure; KMP-native shares core but duplicates UI; full native doubles feature contexts | Extra model/tooling/hosted agent | More platform exceptions, dependency events, and releases | Portable task packs, contracts, fixtures, evidence, and handoff records | Existing AI path only if deterministic, bounded, and independently reviewed | UNRESOLVED; no AI tooling price invented. |
| Upgrade/dependency response | OS/store/security changes require an owner and a safe supported version | Flutter SDK/pub/plugins; RN/Expo/RN modules/config plugins; KMP/Kotlin/Compose/compiler/Gradle/Xcode; native Android/iOS timelines | Paid upgrade support | Four windows plus one safety/security/toolchain event per year | Portable adapters, fallback paths, and replacement plan | Pin only within supported/security policy; no indefinite parking | UNRESOLVED. |
| Support/incident response | User support, pause, correction, rollback/recovery, and truthful status | Candidate-specific version/device/lifecycle diagnostics and parity triage | External support tooling | MAU, device versions, locales, and incident volume | Runbooks, version map, portable evidence, safe hold | Capped tooling after alert/export/exit proof | UNRESOLVED. |
| Exit/migration | Data continuity, export, replacement path, and no silent history loss | Flutter renderer/plugins/host; RN/Expo runtime/modules/config/generated projects; KMP shared source/framework/Compose; fully native two graphs | Migration consultancy/tooling | More users, media, history, and concurrent clients | Portable schemas, contracts, fixtures, manifests, exports, and staged bridge | Open/exportable artifacts; no one-click migration assumed | UNRESOLVED; no rewrite price invented. |

### 6.4 Candidate-caused cost and capacity deltas

These qualitative deltas are the review’s separation of candidate-caused work from shared product cost. They are not scores and do not convert to currency without owner capacity, current quotes, and evidence.

| Candidate | Candidate-caused work most likely to recur over 24 months | What can remain portable | What is most likely to create an unplanned cost or capacity event |
|---|---|---|---|
| Flutter | Flutter SDK/pub/plugin upgrades; plugin/channel registration; Android/iOS host adapters; native lifecycle/background/media/key changes; shared UI parity regression triage. | Product schemas, API contracts, manifests, fixtures, content provenance, acceptance evidence, and platform-independent Dart logic where deliberately isolated. | Plugin or SDK drift that forces native rebuilds; iOS entitlement/signing or background behavior; unresolved final persistence/media dependencies. |
| React Native + Expo | Expo/RN/module upgrades; config-plugin/prebuild/generated-project maintenance; dev-build rebuilds; native module and background task integration; possible EAS/CI account and provider coupling. | Product schemas/contracts/fixtures, TypeScript pure logic, exported media/manifests, and documented native interfaces. | Generated native output mismatch; Expo/RN/Node/module compatibility; hosted build choice; native exception hidden behind a JS surface; no Expo Go production shortcut. |
| KMP-native | Kotlin/KMP/compiler/Gradle integration; generated iOS framework; shared core upgrades; two native UI/accessibility/lifecycle/release implementations; parity fixtures. | Domain/data contracts, schemas, fixtures, content provenance, and selected shared Kotlin logic if no KMP-specific API leaks. | KMP/Native linkage or Xcode/Gradle compatibility; two UI correction paths; need for both platform specialists. |
| KMP + Compose | Kotlin/KMP/Compose/compiler/Jetpack upgrades; shared Compose UI; generated iOS framework/host/interop; iOS semantic/high-contrast validation; native exceptions and two-platform release. | Schemas/contracts/fixtures, content provenance, and platform-independent Kotlin logic with controlled APIs. | Compose/Kotlin/compiler/Gradle/Xcode compatibility; iOS semantics/AT defect requiring platform-specific escape; shared UI change causing two platform regressions. |
| Fully native | Two complete Android/iOS code, dependency, UI, accessibility, lifecycle, test, signing, release, and incident graphs; explicit parity maintenance. | Product schemas/contracts/fixtures, content provenance, API boundaries, and potentially platform-independent algorithms. | Duplicate correction and validation capacity; Android/iOS SDK cadence divergence; two artifact/signing/incident paths; final UI toolkit choice remains open. |

### 6.5 Free, capped, and deferred paths

No path is classified as free merely because its software license is free. A candidate path can be kept in the free/capped column only when the cap, overage behavior, spend alert, export, data retention, shutdown, and replacement route are verified.

| Area | Evidence-supported lower-cash path | Required guard before treating it as viable |
|---|---|---|
| Stores | Buy only when the release/test gate requires it; use the approved store baseline. | Current account, tax/currency, renewal timing, tester/policy requirements, signing custody, and artifact retention. |
| Android builds | Local Android SDK/Gradle/IDE path is possible for every candidate. | Exact supported toolchain, lockfiles, clean-build recipe, cache/artefact retention, and owner/reviewer access. |
| iOS builds | Local Xcode on an available Mac is the direct path for every candidate. | Mac availability/cost, Xcode/SDK support, Apple account, certificates/profiles, physical iPhone, signing custody, and release evidence. |
| Hosted builds/CI | Optional for Flutter, RN/Expo, KMP, and native; local artifacts remain the preferred contingency. | Current price and billing, queue/artifact limits, cap/overage, alerts, data retention, export, outage behavior, and exit. RN/Expo EAS is not assumed. |
| Backend/storage/telemetry | A free or capped provider/self-hosted path may be considered at 1,000 MAU. | Current quota and billing, egress/backup semantics, overage shutdown, privacy, export, restore, and migration. It must be recalculated at 10,000 and 50,000 MAU. |
| Devices/AT/safety | Borrowed or existing devices and qualified reviewers can reduce cash outlay. | Availability, replacement plan, four-cohort coverage, AT evidence, and qualified safety/content authority. AI/simulator evidence is insufficient. |
| AI implementation | Existing approved AI capacity can be used for bounded packets. | Deterministic context pack, independent review, machine validation, usage/cost cap, data handling, and handoff; no unapproved AI subscription is assumed. |

The current record therefore supports a lower-cash research posture, not a zero-cost implementation plan. The owner’s exact monthly cash ceiling and all optional provider/device/authority approvals remain open.

## 7. Conditional ordering and decisive assumptions

### 7.1 Conditional ordering of work-surface groups

The defensible conditional ordering is:

1. Shared application-surface group: Flutter, RN + Expo, and KMP + Compose, tied at the current evidence level for lower routine cross-platform UI duplication but not for total burden.
2. Two-platform ownership group: KMP-native and fully native, tied at the current evidence level for higher explicit parity/release ownership, with different sources of integration burden.

This ordering must not be read as a product recommendation. It is a statement about where repeated work is expected to live under the common fixture. No internal ordering is supported:

- RN + Expo moves upward within the shared group only if TypeScript/React browser adjacency is proven without coupling trust domains, and if local/hosted build authority is bounded.
- KMP + Compose moves downward within the shared group if iOS semantics, high contrast, or generated-framework proof remains unresolved at the decision gate.
- Flutter moves downward if plugin/native closure or SDK/package locking cannot be reproduced.
- KMP-native moves upward relative to fully native if shared domain/data reduces observed invariant drift and the KMP/Native framework path is owned.
- Fully native moves upward relative to KMP-native if direct Android/iOS APIs materially reduce integration incidents and two-platform owner capacity is already available.

### 7.2 Decisive assumptions

1. The owner can obtain or contract the external Mac, Apple account, physical devices, AT, store, privacy, and qualified safety authorities without asking the owner to repair a build.
2. AI work will be executed as narrow task/evidence packets with independent review and machine-readable validation.
3. The monthly cash ceiling is low and exact; unpriced hosted/cloud/CI/device/AI/authority paths cannot be silently assumed.
4. The browser Internal Ops surface is either deliberately separate or a proven shared TypeScript/React boundary is required; the current evidence does not decide this.
5. Four device cohorts, constrained networks, 72-hour offline operation, process death, backup restore, conflict, recall/withdrawal, and accessibility evidence remain mandatory.
6. A final persistence, serialization, secure-key, media, background, notification, and release ownership map is selected before implementation.
7. Dependency locks, generated outputs, SBOM/provenance, clean-build recipes, and rollback/exit artifacts are acceptance evidence, not optional documentation.
8. Any free/capped provider path has verified quota, overage, alert, export, retention, shutdown, and replacement behavior.

## 8. Disqualifiers and hold conditions

### 8.1 Common disqualifiers

Any candidate becomes disqualified for the decision gate if one of the following is true:

- a critical safety, privacy, accessibility, data-continuity, or release path has no named owner and no safe hold/fallback;
- AI output or simulator output is used in place of real-device, AT, store, legal/privacy, or qualified safety evidence;
- the owner is required to diagnose/repair a generated/native build, signing chain, data migration, or incident;
- unbounded provider/hosted/device/AI spend can occur without cap, alert, shutdown, export, and exit;
- canonical authority, history, provenance, private-data separation, or rollback can be silently lost;
- a framework/plugin/native module/toolchain version is unsupported or unpinned in a way that blocks reproducibility;
- a release depends on OTA code/safety behavior, an unreviewed generated project, or an inaccessible external account;
- a candidate cannot provide a portable replacement route for schemas, contracts, fixtures, evidence, and user data.

None of these is asserted as already triggered for a candidate; all candidates remain HELD because documentary evidence does not close them.

### 8.2 Candidate-specific hold triggers

| Candidate | Hold/disqualifier trigger before any recommendation |
|---|---|
| Flutter | Unnamed or unowned plugin/channel for a critical capability; Flutter/pub/native dependency drift without lock/provenance; no iOS host/entitlement/signing owner; shared UI hides divergent native lifecycle or accessibility behavior. |
| React Native + Expo | Expo Go used as a production substitute; config-plugin/prebuild/generated native output not reproducible; critical native module lacks Android/iOS owner; EAS/hosted build chosen without cap/export/exit; OTA relied upon for code or safety. |
| KMP-native | KMP/Native generated-framework linkage lacks an owner; shared-core API leaks prevent portable replacement; native UI/accessibility/release parity has no machine-checked contract; two-platform correction capacity is absent. |
| KMP + Compose | Compose/Kotlin/compiler/Gradle/Xcode compatibility is not locked; iOS semantics, focus/traversal, or high contrast is not proven; shared UI cannot safely escape to native host; generated framework/signing/release path is unowned. |
| Fully native | No capacity for duplicate Android/iOS feature, accessibility, lifecycle, release, and incident correction; final UI toolkit remains unowned; parity contract/fixtures are not machine-checked; one platform is treated as optional evidence. |

## 9. Exact remaining facts required

The following facts are still required for a decision-grade review. They are intentionally not filled with estimates:

1. Owner-approved monthly and 24-month cash ceiling, with tax/currency treatment and approval for each optional category.
2. Current quotes and billing terms for any Mac, hosted build/CI, backend, database, storage/CDN/egress, identity/email/SMS, telemetry, security, AI, support, device, AT, or specialist service.
3. Provider free-tier/cap/overage/alert/shutdown/export/retention/exit evidence for every proposed service.
4. Apple/Google account ownership, signing custody, tester/policy constraints, renewal timing, and release artifact retention.
5. Actual Mac/Xcode availability and reproducible iOS build/signing capacity; Android device/SDK/Gradle availability.
6. Four-cohort physical-device inventory, constrained-network test access, TalkBack/VoiceOver coverage, and qualified accessibility authority.
7. Named Android, iOS, security/privacy, store/release, backend, and qualified safety/content owners or explicit external contracts.
8. Final persistence/database, serialization, key/secure-storage, media, background reconciliation, notification, deep-link, export, and migration choices.
9. Dependency lockfiles, transitive provenance, SBOM format, generated native/framework output, clean-build commands, and artifact retention policy for each candidate.
10. Browser Internal Ops boundary: separate product, shared TypeScript/React package, or another deliberate contract; include trust-domain, release, and test implications.
11. Final Android/iOS UI choices for the fully native candidate and the corresponding accessibility oracle/fixture.
12. Required support/version policy, OS floor, release cadence, safety correction process, recall/withdrawal behavior, and offline package TTL/authority rules.
13. Whether any candidate-specific build/provider account can be operated by an external owner while preserving export and incident access.
14. Exit/migration rehearsal evidence: schemas, manifests, media provenance, local history, keys, pending operations, conflict data, and staged replacement bridge.
15. No real-device, AT, qualified safety, store, or production incident evidence exists yet for any candidate; the future evidence owner and test window must be scheduled.

## 10. Exit dossier

### 10.1 Shared exit invariants

Regardless of candidate, exit must preserve or deliberately migrate:

- canonical server authority and correction/withdrawal/recall history;
- user identity mapping, entitlements, private/shared/community/official data boundaries;
- local history, notes, photos, pending operations, conflict records, and safe recovery state;
- compact-package manifests, digests/signatures, source/provenance, required-versus-optional distinction, and offline validity;
- schemas, API contracts, fixtures, accessibility oracle/copy/tokens, acceptance/negative cases, SBOM, lockfiles, signing/provenance, and incident runbooks;
- staged client coexistence, export, rollback, and a truthful held/unknown state during migration.

### 10.2 Candidate-bound exit surface

| Candidate | Bound-to-candidate surface | Replacement strategy that remains evidence-compatible |
|---|---|---|
| Flutter | Flutter renderer/runtime, Dart UI composition, pub/plugin graph, platform channels, Android/iOS host adapters, and native build integration. | Keep schemas/contracts/fixtures/manifests and portable Dart logic; introduce a replacement client behind the same API/data/fixture boundary; export native artifacts and provenance. |
| React Native + Expo | RN/Expo runtime, JS/TS module surface, config plugins, prebuild/generated projects, Expo modules, native modules, and any EAS/hosted build coupling. | Keep product contracts/fixtures and portable TypeScript logic; replace client behind explicit native/API boundary; export generated projects, locks, SBOM, artifacts, and hosted-provider data. |
| KMP-native | Shared KMP source/API, Kotlin/Native generated iOS framework, Gradle/Xcode linkage, and two native UI clients. | Keep schemas/contracts/fixtures and platform-neutral domain/data behavior; replace generated/native boundary one platform at a time with coexistence and parity evidence. |
| KMP + Compose | Kotlin/Native/Compose runtime, shared Composables/semantics, generated iOS framework, host/interop, and native escape hatches. | Keep portable contracts/fixtures and selected pure Kotlin rules; replace UI/runtime behind the same data/authority boundary; preserve accessibility oracles rather than visual code. |
| Fully native | Two Android/iOS codebases, UI toolkit choices, platform dependencies, signing/build graphs, and parity evidence. | Keep portable schemas/contracts/fixtures/content provenance; replace one platform at a time or introduce a new client; duplicate implementation is already explicit but migration remains a two-client program. |

No candidate has a one-click exit. The cheapest-looking exit can still be the most expensive if source/provenance, local history, pending operations, keys, or accessibility intent were not exported from the beginning.

## 11. Reviewer result

Result: INDEPENDENT REVIEW COMPLETE / STRUCTURALLY ALIGNED / ALL CANDIDATES HELD / NO RECOMMENDATION / NOT ADR

The five dossiers are comparable at the documentary level after the equivalence audit. They all preserve the common S1–S15 fixture and all remain 0 PASS / 15 HELD / 0 REJECT. The current evidence supports only a conditional grouping:

- Flutter, RN + Expo, and KMP + Compose have the lower routine cross-platform UI duplication surface, with materially different native, dependency, iOS-accessibility, generated-output, and browser-adjacency holds.
- KMP-native and fully native make two-platform ownership explicit; KMP-native shares domain/data but adds KMP/Native framework integration, while fully native avoids a cross-platform runtime but duplicates the complete product and release graph.

The review does not turn that grouping into a framework recommendation. A later decision requires the exact remaining facts in Section 9, especially owner capacity, cash ceiling, Mac/device/AT access, browser adjacency boundary, final native/persistence choices, dependency/generated-output provenance, and free/capped provider controls. Until those facts and the common real-device/AT/safety/store evidence exist, the appropriate status for every candidate is HELD.

### Source register

Official/primary source families are recorded in the candidate dossiers and were not reinterpreted as implementation proof:

- Flutter SDK and platform integration documentation; Dart/Flutter release and package documentation cited by the Flutter dossier.
- Expo SDK 57, React Native 0.86, React, Expo Modules, development-build, config-plugin, filesystem, camera, image-picker, notification, secure-store, SQLite, and background-task documentation cited by the RN + Expo dossier.
- Kotlin Multiplatform, Kotlin/Native, Gradle/AGP, Xcode/Swift, and Compose Multiplatform/Compose compiler/Android/iOS compatibility documentation cited by the KMP dossiers.
- Android and Apple official build, lifecycle, storage, accessibility, signing, store, and platform documentation cited by the fully native dossier.
- Google Play Console and Apple Developer Program official membership sources for the approved store baseline.

This register deliberately does not add a new price, provider, implementation claim, real-device claim, accessibility claim, or recommendation beyond the controlled evidence set.
