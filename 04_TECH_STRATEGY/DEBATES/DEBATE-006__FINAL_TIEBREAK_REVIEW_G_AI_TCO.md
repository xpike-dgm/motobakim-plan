# DEBATE-006 — FINAL TIEBREAK REVIEW G: AI OPERABILITY, EXIT AND TCO

Status: `INDEPENDENT ADVERSARIAL REVIEW / DOCUMENTARY / NO-CODE / HELD`
Date: 2026-09-18  
Reviewer: Review G — independent adversarial judge  
Candidates: Flutter; React Native + Expo development builds  
Decision level: Phase-4 tie-break evidence only; not an ADR, implementation, purchase, build or release approval

## 1. Review question and evidence discipline

This review asks whether the final Flutter/RN+Expo tie can be broken for Kavriva's actual operating envelope:

- one nontechnical solo owner;
- AI performs the technical work through bounded tasks and separate review/validation roles;
- Android first, iOS later;
- the owner directly controls an Android phone, while iPhones may be borrowed;
- no owned or reliably accessible Mac is confirmed;
- approximately `TRY 2,000–3,000/month` is a future non-store planning ceiling, not current spending authorization;
- no code, prototype, executable spike, provider purchase or framework ADR is authorized.

The evidence reviewed is:

- `00_CONTROL/DECISION_LOG.md` — DEC-0028 through DEC-0032;
- `00_CONTROL/CURRENT_STATE.md`;
- `DEBATE-006__FINAL_CLOSURE_FLUTTER.md`;
- `DEBATE-006__FINAL_CLOSURE_RN_EXPO.md`;
- `DEBATE-006__HOSTED_MAC_BUILD_CONTROL_REVIEW.md`;
- `DEBATE-006__TASK_SIM_MOB_001_AUDIT_AND_JUDGE.md`.

The two final-closure files are documentary acceptance oracles. They report no real build, signed artifact, device,
assistive-technology, safety, store, provider-capacity or price pass. Words such as `edge`, `risk` and `conditional`
below are comparative inferences from the documented change surfaces, never implementation evidence. A missing
fact remains `HELD`; it is not converted into a favorable assumption.

## 2. Verdict

### Conditional recommendation: Flutter, with a narrow and reversible condition

For this specific solo-owner/AI-operated envelope, Flutter is the more defensible conditional default because its
ordinary shared work surface is more concentrated: a fresh AI can usually keep pure UI/domain work in a Dart packet,
then explicitly split plugin/channel, Android runner and iOS runner work when a native boundary is touched. RN+Expo's
ordinary TypeScript/React packet is also bounded, but its app-config, config-plugin, prebuild/CNG, generated-project,
native sub-lock and optional hosted-build surfaces create more ways for a seemingly small task to cross packet
boundaries.

This is a risk-shape preference, not a pass. Flutter is recommended only if the following condition is accepted and
later evidenced:

> Every native, generated, toolchain, signing, artifact and provider-independent recovery edge is made explicit in
> the Flutter task/evidence graph, and no critical capability requires unmanaged native repair by the owner.

Until that condition is proven, the actual disposition of Flutter remains `HELD`. RN+Expo is not rejected and remains
an admissible fallback. If Flutter cannot produce the stated closure, while RN+Expo does produce an equally portable,
deterministic and capped closure, the recommendation must switch to RN+Expo or return to `HELD`; it must not be
rescued by convenience or by an aggregate score.

The recommendation is intentionally conditional because the only candidate-attributable advantage found is a
documentary work-surface inference. Mac access, signing authority, physical/AT/safety evidence, current pricing and
provider exit remain common unresolved gates.

The preceding `TASK-SIM-MOB-001` audit is consistent with this restraint: Reviewer E found no defensible individual
winner, while Reviewer F narrowed the field to `React Native + Expo ≈ Flutter` for a next evidence step. This review
does not turn that approximate ordering into a framework pass; it records a narrow Flutter working default for the
specific solo-AI packet-risk question and keeps the closure status `HELD`.

## 3. Six-axis adversarial comparison

The labels in the final column are comparative dispositions, not points or a numerical score.

| Axis | Flutter | React Native + Expo | Adversarial disposition |
|---|---|---|---|
| AI task isolation | Pure Dart UI/domain/fixture work is a relatively concentrated packet. Plugin registration, platform channels, runner changes, lifecycle, signing and device evidence must still become separate Android/iOS packets. | TypeScript/React UI/state can be bounded, but app config, dynamic config, config-plugin order/options, prebuild/CNG, generated native output, native modules, native sub-locks and development-client rebuilds are separate edges. | **Conditional Flutter edge.** This is an inference about packet crossings, not proof that either AI route has executed successfully. |
| Hidden/generated/native change surface | `pubspec.lock` and transitive package graph do not make a plugin Dart-only. Generated plugin registrants, Flutter framework/Swift-package integration, Runner/Xcode files and CocoaPods fallback remain native/generated surfaces. | JS/package lock is insufficient. Effective config, config-plugin mods, prebuild template, autolinking/codegen, generated Android/iOS projects, native sub-locks and any Expo module/native code must be inspected and hashed. | **Flutter has the smaller apparent layering risk, not a closed surface.** RN's extra config/prebuild layer is a material conditional risk; both hold until clean regeneration and diff evidence exist. |
| Provider independence | Closure plan explicitly permits local Android, later local Mac and a conditional hosted Mac route; Flutter is not tied to a named provider. | EAS is explicitly optional; local native builds and another provider are allowed. The route becomes unsafe only if EAS/hosted state is opaque or mandatory. | **Tie / HELD.** Neither candidate may be penalized for an unselected provider, and neither may claim independence without an export/restore drill. |
| Recovery / exit | Portable product contracts, schemas, fixtures, provenance and old artifacts survive a Flutter replacement; Dart/runtime, pub graph, channels, runners and native build integration do not. | Portable product contracts, schemas, fixtures, provenance and old artifacts survive an RN/Expo replacement; JS/runtime, config plugins, generated projects, modules and any EAS coupling do not. | **Tie / HELD.** Both have a plausible forward-migration boundary; neither has executed restore, replacement or outage recovery. |
| Recurring cost exposure | No Flutter-specific recurring cost is established. Hosted Mac/CI, backend, storage, devices and review are unresolved; store fees are separate approved release costs. | No RN/Expo-specific recurring cost is established. EAS is optional, but selecting it could add provider/account/minute/storage/egress exposure; no current quote or cap is closed. | **Tie / HELD.** No `0 TRY`, `free`, `included`, `uncapped` or budget-safe claim is allowed for either route. |
| Owner-debug risk | Native plugin/channel/runner or toolchain failures remain AI/reviewer work; the owner must not repair Gradle/Xcode, signing or lifecycle behavior. The smaller ordinary packet may reduce handoff confusion. | Prebuild/config-plugin/generated-native failure can surface from a JS-looking change; Expo Go/JS reload/OTA cannot be used as repair or release evidence. The owner must not repair generated projects or signing. | **Conditional Flutter edge, subject to no-owner-debug proof.** Any route that leaves repair to the owner is a `REJECT`, regardless of framework. |

### 3.1 What does not differentiate the candidates

The following are common obligations and therefore cannot be counted as framework advantages:

- Android/iOS product parity, S1–S15 lifecycle/offline/restore/recall truth, safety-stop semantics and photo-as-pending-
  evidence semantics;
- direct Android real-device access, constrained/main Android cohorts, borrowed-iPhone limitations and four-cohort AT
  evidence;
- Apple/Google legal owner, store account, signing, qualified safety/content review, privacy interpretation and
  release approval;
- Android-first sequencing with iOS visibly `HELD` when Mac/build/device evidence is unavailable;
- exact immutable artifact, SBOM, provenance, signing and independent verification obligations;
- no OTA code delivery, no Expo Go production shortcut, no simulator/TestFlight/provider-log substitution;
- migration that preserves history/provenance/media/pending operations and refuses lossy binary rollback.

The hosted-Mac review expressly says that provider absence is not a framework `REJECT`: Android-first may continue,
while iOS and a hosted route remain `HELD`. This prevents an unconfirmed Mac from deciding the framework indirectly.

### 3.2 Injected closure event

The simultaneous-event requirement does not create a hidden shortcut for either candidate:

- **Photo replacement or retirement:** Flutter must re-resolve the pub/plugin graph, plugin registration, native
  implementation, permissions and Runner/package-manager output. RN+Expo must re-resolve the JS lock and native
  sub-locks, app config, config-plugin output, prebuild/autolinking/codegen and native projects. Both must preserve
  pending/old photo evidence, retain the safe no-photo path and rebuild every affected platform. The candidate delta
  is representation count, not different product truth; both remain `HELD` without before/after closure evidence.
- **Apple/Google requirement change:** Flutter re-pins Flutter/Dart plus Android and iOS toolchains; RN+Expo re-pins
  the Expo/RN/React/Node line plus the same platform toolchains and plugin compatibility. Both must retain the last
  accepted artifact, capture the dated official requirement and re-run the affected platform's device/AT/signing/
  store evidence. Neither dated snapshot in the source files proves a future requirement or a build pass.
- **Android-first:** Both candidates can, in principle, close Android separately from iOS if the provider-neutral
  Android recipe and required device/AT/safety/release evidence exist. The directly controlled Android phone does not
  close constrained-cohort or independent evidence obligations. Missing Mac access keeps iOS `HELD` for both.
- **Recovery/exit:** Both must export the exact input graph, generated/native result, artifact, SBOM, provenance and
  acceptance evidence, then recover without the original provider. A plan that merely names Flutter runners or Expo
  prebuild output, without a restore receipt, is not exit evidence.

Thus the event exposes a conditional RN representation risk, but it does not produce a documentary `PASS` for Flutter
or a documentary `REJECT` for RN+Expo.

## 4. Candidate-specific adversarial findings

### 4.1 Flutter — conditional strengths and failure modes

The Flutter closure plan has a clear shared Dart surface and a stable adapter intent for the optional-photo branch.
Its C01–C12 packet split, trigger matrix and separate Android/iOS lanes are suitable for DEC-0028's minimum-sufficient
context model. The plan correctly treats a pub/plugin edit as potentially native, forces both-platform rebuilds when
the impact graph is not proven otherwise, and keeps the old artifact and data truth.

The adversarial concern is that `pubspec.lock` is not the whole closure. A Flutter plugin may bring Kotlin/Java and
Swift/Objective-C code; generated plugin registration, Runner/Xcode integration, SwiftPM/CocoaPods selection,
permissions, entitlements, temporary-file behavior and lifecycle/channel serialization can remain outside a shared
Dart task. If an AI packet says “Dart change” while omitting those edges, the packet is under-scoped and must be
`HELD`.

Flutter's conditional advantage disappears if any of these occur:

- a critical plugin or native channel has no named owner, fallback or EOL/security response;
- generated Runner/registrant or package-manager output differs without a pinned input and clean regeneration record;
- the Android route secretly depends on a hosted service, or the iOS route has no portable local/alternate recovery;
- a failed native/build/signing task is handed to the owner as debugging work;
- the smaller Dart surface is used to waive platform-specific AT, safety, lifecycle or store evidence.

### 4.2 React Native + Expo — conditional strengths and failure modes

The RN+Expo closure plan is explicit about the native boundary. It correctly rejects Expo Go and OTA for production
evidence, requires a new development client after native dependency/config changes, treats unknown native behavior as
changed, and records both the effective app-config digest and the prebuild/generated diff. Local builds, another
provider and EAS are kept as distinct routes rather than silently selecting EAS.

The adversarial concern is the number of coupled representations: JS/package lock, Expo/RN/React compatibility,
Android Gradle/Maven and iOS Pods/SPM locks, dynamic config, plugin inventory/order, prebuild/CNG template, generated
projects, autolinking/codegen and optional EAS profile/environment. A small package or config edit can therefore
alter native output without changing the visible JS call site. The plan names this risk, but naming it is not proof
that every generated output is reproducible or that a fresh AI can safely operate the route.

RN+Expo remains viable only if all of the following are enforced:

- one authoritative package lock plus native sub-locks and effective-config digest;
- plugin source/version/options/order and generated mods are reviewable; no unnamed plugin or opaque dynamic input;
- clean prebuild/CNG output is diffed for both platforms, with direct generated edits either prohibited or reproducibly
  reapplied and included in the exit dossier;
- a native dependency change invalidates the old development client and affected release artifacts;
- EAS/hosted build remains optional and exportable; no Expo Go, JS reload or OTA shortcut enters the closure;
- failure packets go to AI implementer/reviewer/validator owners, never to the nontechnical owner.

If these controls are not attainable, RN's additional representation layers are a critical AI-operability and exit
risk, not a convenience tradeoff.

## 5. Conditional recommendation gate

The Flutter recommendation can be used as a working default only when every gate below is later evidenced. These are
future closure requirements, not claims that they are already satisfied.

### F-G1 — Bounded task graph

Fresh AI receives a minimum-sufficient packet that names the Dart contract, design references, allowed/forbidden files,
dependency/native/generated edges, acceptance and negative cases, reviewer/validator, output evidence and safe
recovery. Any plugin/channel/lifecycle/signing/release change expands the packet to the relevant Android and iOS
contexts.

### F-G2 — Explicit native/generated closure

The exact Flutter/Dart ref and digest, pub lock, direct/transitive package provenance, Android Gradle/toolchain lock,
iOS SwiftPM/Pods lock, plugin registrants, Runner/Xcode outputs, permissions, entitlements, privacy declarations and
generated diffs are all tied to the artifact. An unexplained generated diff is a closure defect.

### F-G3 — Provider-independent Android-first route

Android can be cleanly rebuilt and exported from a provider-neutral recipe, installed on the owner's device and
validated across the required constrained/main cohorts, AT and safety/recovery oracles. A hosted Mac is not a hidden
Android prerequisite. The Android lane may close separately while iOS remains `HELD`.

### F-G4 — Later iOS route without borrowed-device substitution

Before iOS release, reliable local Mac access or an explicitly approved hosted/alternate route must show current price,
cap/overage shutdown, credential custody, retention, export, restore and exit. Borrowed iPhones need a real schedule
and cannot act as build host, signer or sole recovery path.

### F-G5 — Bounded cash and capacity

Every recurring route has an official date-stamped price/period, taxes/FX, quota/parallelism, retry/egress/storage
behavior, hard stop, alerts, retention, export and termination path. The non-store total is compared with the
`TRY 2,000–3,000/month` planning ceiling. Store fees remain separately identified. Missing price or cap is `HELD`,
not zero.

### F-G6 — No owner repair and independent authority

Build failure produces a machine-readable failure packet and AI/technical handoff. Implementer, reviewer, validator,
security/release, accessibility and qualified safety/content authorities remain distinct. The owner supplies product
decisions, external account authority and cost approval only; no code/build/signing repair is delegated to the owner.

### F-G7 — Forward recovery and exit

Photo replacement and retirement preserve old records and provenance; migration is forward-only where required; old
artifacts are retained; source/locks/generated manifests/SBOM/artifacts/evidence are exported and restore-tested; no
cache, backup, notification or OTA path creates current safety/release authority.

Failure of any critical F-G gate keeps Flutter `HELD`. A direct disqualifier (OTA code authority, plaintext key,
unexportable artifact/provenance, unbounded auto-charge, unknown signer, user repair obligation or loss of user truth)
is `REJECT` under the common hosted-control rules.

## 6. Tie-break disposition and next evidence

The documentary evidence supports this narrow decision:

1. **Working default:** Flutter, conditionally, because the ordinary AI task surface is more concentrated and the
   candidate exposes fewer configuration-generation layers before the explicit native boundary.
2. **Viable fallback:** RN+Expo, conditionally, if it closes the effective-config/plugin/prebuild/generated-native
   graph and proves provider-independent local/alternate recovery with the same evidence bar.
3. **Current release status:** both candidates remain `HELD`; neither has build, device, AT, safety, signing, store,
   cost or restore evidence.
4. **No hidden consequence:** Android-first may continue as a working publication direction; it does not close iOS or
   select a provider. Borrowed iPhones do not solve Mac/signing/recovery.
5. **No score substitution:** no aggregate convenience/TCO score may override a critical hold or convert documentary
   plans into passes. The recommendation should be revisited if the first real closure exercise reverses the native,
   recovery or cost findings.

The next authorized action is not coding. It is a controlled evidence closure for the chosen working candidate (or a
fresh equal closure if RN+Expo is retained), followed by independent review. Only after the relevant gates close may a
separate ADR process consider framework selection.

## 7. Source links and authority boundary

Internal sources:

- [[00_CONTROL/DECISION_LOG#DEC-0028 — AI-Native Execution and Obsidian Project Graph Requirement]]
- [[00_CONTROL/DECISION_LOG#DEC-0029 — AI-Operated Delivery / Nontechnical Product Owner Model]]
- [[00_CONTROL/DECISION_LOG#DEC-0030 — Solo Ownership and Limited-Budget Constraint]]
- [[00_CONTROL/DECISION_LOG#DEC-0031 — Mobile Evaluation Method and Common Fixture]]
- [[00_CONTROL/DECISION_LOG#DEC-0032 — Android-First Staged Release and Owner Resource Envelope]]
- [[00_CONTROL/CURRENT_STATE]]
- [[DEBATE-006__FINAL_CLOSURE_FLUTTER]]
- [[DEBATE-006__FINAL_CLOSURE_RN_EXPO]]
- [[DEBATE-006__HOSTED_MAC_BUILD_CONTROL_REVIEW]]
- [[DEBATE-006__TASK_SIM_MOB_001_AUDIT_AND_JUDGE]]

Authority boundary:

- This review does not change `CURRENT_STATE`, DEC-0032, the common fixture or the Android-first direction.
- It does not select Flutter, RN+Expo, EAS, a hosted Mac provider or a subscription.
- It does not authorize code, prototype, build, purchase, ADR or Gate 4 → 5.
- Every framework-specific assertion above is a dated documentary inference or a future acceptance condition; no
  official framework documentation is treated as Kavriva build/device/safety evidence.
