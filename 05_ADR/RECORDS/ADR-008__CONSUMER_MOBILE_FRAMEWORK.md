# ADR-008 — Consumer Mobile Framework and Portable-Truth Separation

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-006, user-approved under `DEC-0033` on the corrected common fixture `DEC-0031` and
Android-first sequencing `DEC-0032`) compared Flutter, React Native + Expo development builds, KMP-native,
KMP-Compose and full native through identical no-code S1–S15 scenario dossiers, equivalence audits, task
simulations, dependency/rebuild/release closure exercises, a hosted-build control review and two independent final
critiques. Flutter became the conditional, reversible working direction with React Native + Expo as first fallback.
This ADR converts that recommendation into a binding framework decision. It authorizes no code, build, device test,
provider, OTA channel, subscription or store submission, and claims no build/device/release readiness.

## Decision Drivers

- The central operational risk for this project is whether a fresh AI can safely change one bounded task without
  hidden effects and without asking the nontechnical owner to debug the result.
- Android-first must use hardware the owner controls today (direct Android access; borrowed iPhones only for later
  test access), with iOS as a later second lane — no simultaneous-launch forcing.
- Later TRY 2,000–3,000/month non-store planning ceiling is context for staged cost evidence, not spend authority.
- Portable product, data, safety, provenance and release truth must never live inside framework-bound presentation
  code, whichever framework wins later.

## Options Considered

### Option A — Flutter as the working direction (chosen, conditional)

Deciding reason (Review G, accepted by Judge): ordinary shared AI work stays concentrated in a narrower surface
(Dart) and crosses fewer configuration-generation representations before reaching explicit native lanes than the
RN/Expo chain of application configuration → config plugins → prebuild/generated projects → native build. Under a
solo AI-operated model, the smaller apparent coordination surface is the more conservative planning default — not a
popularity, speed or scoring verdict (Review H correctly notes neither finalist has real build/device evidence, so
this remains a documentary recommendation, not a technical proof).

### Option B — React Native + Expo development builds (first fallback, not rejected)

Viable and held ready: subject to its own effective-config, config-plugin, prebuild/generated-project, native-lock,
development-client and provider-independent recovery controls. Activates only through the reversal triggers below,
never silently or in parallel.

### Option C — KMP-Compose (expertise-conditional challenger)

Kept as challenger: viable only if the project later fields the specific Kotlin-multiplatform expertise and proves
the same closure gates; not a default.

### Option D — KMP-native / full native baselines (reference only)

Reference points for comparison, not implementation candidates for a solo AI-operated project.

## Decision

Kavriva adopts Flutter as the consumer-mobile framework direction, **conditionally and reversibly**, with the
following locked conditions (all must hold; any failure reopens the decision instead of silently switching stacks):

1. Every direct/transitive package, plugin, native implementation, generated output (including registrants) and
   platform configuration (Android Runner/Gradle, iOS Runner/Xcode, SwiftPM-or-CocoaPods) is pinned, attributable
   and linked through the AI-native task/evidence graph.
2. Portable product, data, safety, provenance and release truth remain outside framework-bound presentation code.
3. A clean provider-independent Android rebuild and recovery path exists; Android stays the first publication lane
   on the owner-controlled device.
4. The iOS lane opens only with real Mac/Xcode execution access (or an explicitly approved, capped, exportable
   hosted route), borrowed-iPhone test scheduling, signing custody and Apple evidence (detailed in ADR-013).
5. Signing keys and store credentials stay owner-controlled with least privilege, rotation and recovery; the owner
   is never asked to debug code, native builds, signing or toolchain failures.
6. Lifecycle, offline, restore, safety and Turkish accessibility behavior are proven separately on required real
   devices — simulators and AI claims never substitute.
7. Recurring non-store costs stay inside an owner-approved staged plan; missing or uncapped cost stays `HELD`.
8. No provider, OTA channel, hosted Mac/build subscription or implementation is approved by this decision.

Mandatory reversal/review triggers (any one reopens the framework decision with evidence): an essential capability
needs an unmaintained or unsafe plugin with no controlled native fallback; native/generated state cannot be
reproduced, attributed, reviewed or exported; Android or later iOS demands a non-exportable provider dependency or
an uncapped/unapproved recurring cost; Flutter cannot close a mandatory real-device lifecycle/offline/recovery/
accessibility/safety/signing/store gate without weakening product requirements; implementation would require owner
technical repair; RN/Expo provably closes a mandatory requirement Flutter cannot close safely.

## Rationale

The choice optimizes for the project's actual bottleneck — safe bounded AI change without owner debugging — rather
than ecosystem popularity or benchmark speed, while Android-first sequencing lets the first release cycle run on
hardware the owner already controls. Keeping RN/Expo as a defined fallback (instead of rejecting it) preserves a
reviewed escape path with known activation conditions.

## Consequences

### Positive

- One explicit framework lane for all later mobile tasks, with closure obligations (plugin, registrant,
  platform-channel, Runner/Gradle/Xcode effects) defined up front instead of discovered during incidents.
- iOS cost and complexity stay deferred and fenced until their own evidence gates pass.
- Fallback conditions are written down now, so a future switch (if ever needed) follows evidence, not panic.

### Negative / Trade-offs

- Flutter is a recommendation, not a proof: every build/device/accessibility/signing/store gate is still `HELD`
  for later real evidence — planning cannot skip them.
- Dart/Flutter plugin and native-layer closures become mandatory AI-task overhead from the first mobile task.
- If Flutter trips a reversal trigger late, the project pays a framework-revisit cost; the fallback definition
  bounds but does not remove it.

## Prohibited / Constrained Alternatives

- Treating this ADR as build/device/release readiness, or starting implementation, builds, signing or store
  submission under it.
- Framework-bound presentation code owning portable product/data/safety/provenance/release truth.
- Simultaneous two-store launch forcing; iOS lane opening without its evidence gates.
- Silent framework switching on trigger events — triggers reopen the decision with recorded evidence.
- Any hosted Mac/build provider, subscription, OTA channel, code or implementation — none authorized by this ADR.

## Revisit Triggers

See the mandatory trigger list in Decision above. Additionally: exact Flutter/Dart channels and versions, plugin
allowlist, and real-device/OS coverage matrices remain HELD for later implementation evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0031`, `DEC-0032`, `DEC-0033` (binding directions)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-007__SUPPLY_CHAIN_AND_RELEASE_GOVERNANCE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__FINAL_TIEBREAK_JUDGE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__FINAL_CLOSURE_FLUTTER.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__FINAL_CLOSURE_RN_EXPO.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-006__HOSTED_MAC_BUILD_CONTROL_REVIEW.md`
- Downstream: ADR-009 (offline package/ledger), ADR-013 (build/release operations)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
