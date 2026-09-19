# DEBATE-006 — Final Tie-Break Manager / Judge Synthesis

Status: `USER-APPROVED FLUTTER WORKING DIRECTION / DOCUMENTARY / NO-CODE / ADR NOT AUTHORIZED`
Date: 2026-09-18

## 1. Decision Question

This record answers which mobile framework should become Kavriva's Phase-4 working direction under the actual owner
envelope: one nontechnical owner, AI-operated delivery, Android first, iOS later, direct Android access, borrowed-iPhone
access, no confirmed Mac and a later TRY 2,000–3,000/month non-store planning ceiling.

It does not claim a build, device, accessibility, signing, store, provider, safety or cost pass. No code, prototype,
subscription, provider or ADR is authorized.

## 2. Evidence Reviewed

- five equal S1–S15 candidate dossiers and their equivalence audit;
- two five-way independent reviews and Judge synthesis;
- equal `TASK-SIM-MOB-001` records, equivalence audit and two further independent reviews;
- Flutter and RN/Expo equal final dependency/rebuild/release closure exercises;
- provider-independent hosted Mac/build control review;
- independent Review G — AI operability, exit and TCO;
- independent Review H — platform, lifecycle and maintenance.

## 3. Reviewer Disagreement

Review G conditionally recommends Flutter because a fresh AI can ordinarily operate through a more concentrated Dart
surface and cross fewer configuration-generation layers before reaching explicit Android/iOS native work. RN/Expo
remains viable but adds effective app configuration, config-plugin ordering, prebuild/CNG, generated-project and
development-client invalidation surfaces.

Review H correctly finds that neither finalist has real build/device/provider evidence and therefore refuses to call
either candidate technically proven. It treats the observed surface difference as an inference rather than measured
maintenance evidence.

These findings are compatible when decision levels are separated:

- Phase 4 may choose a reversible strategic working direction from documentary risk evidence;
- later gates must still prove that direction through exact implementation, build, device, accessibility, signing,
  recovery and cost evidence;
- a strategic recommendation is not a release pass and does not erase any `HELD` evidence gate.

Waiting for code before making any planning recommendation would conflict with the user-approved no-code planning
boundary and would move the technology choice into implementation without an explicit starting direction. Conversely,
treating documentary structure as proof would overstate the evidence. The correct middle position is a conditional,
reversible working recommendation.

## 4. Manager / Judge Recommendation

**Flutter is Kavriva's user-approved consumer-mobile working direction under `DEC-0033`.**

The deciding reason is not popularity, claimed speed or a numerical score. For this project, the central operational
risk is whether a fresh AI can safely change one bounded task without hidden effects and without asking the owner to
debug the result. Both finalists cross native boundaries, but RN/Expo introduces an additional routine transformation
chain:

`application configuration -> config plugins -> prebuild/generated native projects -> native build`

Flutter still requires strict plugin, generated registrant, Runner, Gradle, Xcode, SwiftPM/CocoaPods and platform-channel
closure. Its ordinary shared work is nevertheless concentrated in fewer representations before those explicit native
lanes. Under a solo AI-operated model, the smaller apparent coordination surface is the more conservative planning
default.

Android-first does not itself decide the framework. It supports the recommendation because Flutter can use an
owner-controlled local Android lane while the later iOS lane stays visibly held until a Mac or approved hosted route,
borrowed-device schedule and Apple evidence exist. RN/Expo can do the same and remains the defined fallback.

## 5. Mandatory Conditions and Reversal Triggers

Flutter remains acceptable only if later gated planning and implementation evidence shows:

1. every direct/transitive package, plugin, native implementation, generated output and platform configuration is
   pinned, attributable and linked in the Obsidian-compatible task/evidence graph;
2. a clean provider-independent Android rebuild and recovery path exists;
3. the iOS route can be reproduced through an owned/reliably accessible Mac or an explicitly approved, capped and
   exportable hosted route;
4. signing keys and store credentials remain owner-controlled with least privilege, rotation and recovery;
5. lifecycle, offline, restore, safety and Turkish accessibility behavior is separately proven on required real devices;
6. no failed build, signing or native dependency task is handed to the owner for technical repair;
7. recurring non-store costs remain within an owner-approved staged plan; missing or uncapped cost stays `HELD`;
8. framework-bound code never becomes the canonical home of portable product, data, safety or provenance truth.

The recommendation must return to comparison or switch to RN/Expo if Flutter later requires an unmaintained critical
plugin, unexplained native/generated state, non-exportable hosted dependency, unaffordable mandatory route, owner
debugging or an accessibility/lifecycle compromise while RN/Expo closes the same requirement safely.

RN/Expo is therefore not rejected. It is the first fallback, subject to its own effective-config, config-plugin,
prebuild/generated-project, native lock, development-client and provider-independent recovery controls. KMP-Compose
remains an expertise-conditional challenger; KMP-native and full native remain reference baselines.

## 6. Current Disposition

- Manager recommendation: `FLUTTER — CONDITIONAL WORKING DIRECTION`.
- User approval: `RECEIVED 2026-09-18 / DEC-0033`.
- RN/Expo: `VIABLE FIRST FALLBACK / NOT REJECTED`.
- Hosted Mac/build provider: `NOT SELECTED / HELD UNTIL iOS PREPARATION AND PRICED APPROVAL`.
- Real build/device/accessibility/signing/store/cost evidence: `HELD FOR LATER GATES`.
- Framework ADR: `NOT AUTHORIZED`.
- Code/prototype: `NOT AUTHORIZED`.
- Gate 4 -> 5: `REMAINS CLOSED` pending completion and approval of the rest of Phase 4.

The later ADR must preserve every condition and reversal trigger above; it may not rewrite documentary recommendation
as prior implementation proof.

## 7. Evidence Links

- [[DEBATE-006__FINAL_CLOSURE_FLUTTER]]
- [[DEBATE-006__FINAL_CLOSURE_RN_EXPO]]
- [[DEBATE-006__HOSTED_MAC_BUILD_CONTROL_REVIEW]]
- [[DEBATE-006__FINAL_TIEBREAK_REVIEW_G_AI_TCO]]
- [[DEBATE-006__FINAL_TIEBREAK_REVIEW_H_PLATFORM]]
- [[DEBATE-006__TASK_SIM_MOB_001_AUDIT_AND_JUDGE]]
- [[00_CONTROL/DECISION_LOG#DEC-0032 — Android-First Staged Release and Owner Resource Envelope]]
