# DEBATE-006 — COMMON FIXTURE AND OPERATING ASSUMPTIONS

Status: `APPROVED COMMON COMPARISON FIXTURE / NO-CODE / NO FRAMEWORK SELECTED`
Date: 2026-09-17
Decision level: Phase-4 comparison input only; not an ADR

## 1. Plain-Language Purpose

This document gives every mobile technology candidate the same Kavriva examination. It prevents one option from being
shown on an easy demo while another is judged against the difficult real product. No application, prototype or executable
test is authorized here.

The numbers below are conservative planning fixtures, not promises about final product limits. Once approved, they stay
unchanged across Flutter, React Native + Expo development builds, KMP-native, KMP-Compose and fully native dossiers.

## 2. Proposed Product and Release Baseline

| Item | Common fixture | Why this is proposed |
|---|---|---|
| Product surfaces | Android and iOS consumer apps; browser-based Internal Operations | Already-approved product direction |
| Publication order | Both stores remain planned; simultaneous release is not assumed | Avoids forcing duplicate launch pressure onto one low-budget owner |
| Evaluation horizon | First release plus 24 months of maintenance | Exposes upgrade and recurring-cost consequences |
| Planning release rhythm | Four planned release windows per year plus safety-critical correction when required | Enough to test maintenance burden without inventing a high-frequency team |
| First public scale | 1,000 monthly active users | Small but real launch baseline |
| Growth check | 10,000 monthly active users | Shows which costs appear after free tiers |
| Stress check | 50,000 monthly active users | Scale-triggered estimate only; not a launch forecast |

Release timing is evidence-gated, not calendar-promised. A failed safety, data-continuity, accessibility or store-readiness
gate delays the affected release instead of lowering the standard.

User count alone is not a cost model. For comparison only, every scale tier also uses the following monthly workload:

- two compact task-package transfers per monthly active user;
- optional-media use by 10% of monthly active users, using a `100 MB` average transfer in the cost worksheet;
- `0.5` new user photos per monthly active user at a `3 MB` average upload;
- a 24-month storage-cost horizon, without turning 24 months into a final legal retention promise;
- the same workload calculated at 1,000, 10,000 and 50,000 MAU, with storage and outbound transfer shown separately.

The local-device photo stress fixture in section 5 is not multiplied by MAU. It tests device behavior; the monthly workload
above tests service cost. The maintenance capacity fixture also includes one unplanned safety/security correction and one
forced store/platform/toolchain compatibility event per year. These are stress events, not a release promise.

## 3. Proposed Device and Operating-System Policy

The product policy is deliberately narrower than every technically possible device. Supporting very old devices increases
testing, failure and maintenance load for a solo owner.

| Cohort | Proposed comparison floor | Documentary pressure condition |
|---|---|---|
| Constrained Android | Android 10 / API 29, 64-bit, 4 GB RAM, 64 GB storage, 2 GB free | Process termination, storage pressure, battery saver and unreliable network |
| Main Android | Android 13 or newer, 6 GB RAM, 128 GB storage | Normal daily-use reference |
| Oldest supported iPhone | iOS 16.4-capable device at the oldest supported end | Process termination, low free storage and accessibility checks |
| Current iPhone | Current generally available iOS on a standard non-Pro device | Current platform behavior reference |

The exact branded test devices are intentionally not selected during no-code planning. Before ADR approval, current
framework and store floors must be rechecked. Before release, actual devices—not simulators alone—must cover the oldest
supported and current cohorts. Device borrowing/test access is preferred before any purchase is proposed.

The RAM/storage values are test profiles, not a promise that every device with those numbers is supported. `Current iPhone`
and current operating-system values are re-frozen at each release window. The proposed first-release scope is phone-only:
tablets and foldables must remain safe and non-corrupting but do not receive optimized layouts until separately approved.
An explicitly unsupported device receives a clear store/client message and never an unsafe partial experience. Simulators
do not replace real-device or real assistive-technology evidence.

## 4. Fixed Network and Interruption Profiles

Every option walks through all profiles:

1. stable Wi-Fi: 50 Mbps download, ordinary latency;
2. ordinary cellular: 10 Mbps download;
3. constrained cellular: 1 Mbps, 300 ms latency and 5% packet loss;
4. connection loss during transfer and during synchronization;
5. fully offline for 72 hours;
6. app backgrounded, phone locked, incoming call, operating-system process termination and later restart;
7. device clock changed and app restored from backup before reconnection.

These are documentary comparison conditions. Phase 4 does not claim that a real device passed them.

## 5. Fixed Data and Offline-Package Fixture

### 5.1 Selected task package

- one selected motorcycle, model year and resolved variant;
- one active maintenance task;
- required text, warnings, diagrams and complete safe-stop/recovery material: target maximum `12 MB` network-transfer size;
- optional high-resolution images/video: separate, up to `150 MB`, never selected silently;
- size shown before download;
- required compact package remains complete without optional media;
- an unrelated `2 GB` catalog exists in the fixture solely to prove that the client does not download it by default;
- default offline-content cache budget: `250 MB`, excluding user-created history/photos;
- downloads above `25 MB` on cellular require an explicit user choice; required compact safety/recovery material must not
  be split merely to evade this threshold.

The installed/indexed size is measured separately from the `12 MB` transfer. Every candidate must budget at least enough
temporary space for the old package plus the new package and atomic verification; it cannot present `12 MB` as the total
on-device peak. The `12 MB`, `150 MB`, `2 GB`, `250 MB` and `25 MB` values are proposed comparison constants, not final
commercial limits.

### 5.2 Local records and media

| Dataset | Normal fixture | Stress fixture |
|---|---:|---:|
| Motorcycles | 3 | 10 |
| History/evidence records | 250 | 2,000 |
| User photos | 50 at 3 MB average | 500 at 3 MB average |
| Private notes | 100 | 1,000 |
| Pending offline changes | 20 | 200 |
| Deliberate local/profile conflicts | 3 | 30 |

The fixture contains one duplicate operation, one partial upload, one corrupt package, one interrupted database change,
one source correction, one content withdrawal and one safety recall. No candidate may discard or overwrite these cases
silently.

## 6. First-Release Native Capability Boundary

Required in the comparison:

- camera capture and photo/file import;
- user-visible file export/share;
- notifications and deep links;
- secure local storage for protected fields and keys;
- scoped offline download, cancellation, resume, integrity validation and cleanup;
- foreground reconciliation after network return;
- accessible Turkish critical flows using VoiceOver and TalkBack;
- store signing, staged release and incident pause for both platforms.

Not assumed for the first release unless later product evidence reopens them:

- Bluetooth device integration;
- NFC;
- continuous GPS/background location;
- direct motorcycle sensor/diagnostic-hardware connection;
- background execution as a correctness requirement;
- framework-provided OTA code delivery;
- automatic AI authority over safety-critical content publication.

Removing these assumptions reduces unnecessary permission, dependency, battery and maintenance cost. It does not prevent
a later controlled capability decision.

## 7. Privacy, Retention and Device-Loss Assumptions

- private notes and user photos are private by default;
- private, shared/community and officially approved technical content remain distinct;
- analytics must work with the minimum necessary event data and must not ingest private note/photo content by default;
- a restored/cloned device or replayed cache cannot create current authorization, entitlement or safety eligibility;
- export is treated as a disclosure that cannot be remotely withdrawn from an already exported copy;
- deletion of one copy does not silently erase independent evidence, provenance or required correction history;
- exact retention durations remain a legal/product-policy question and are not invented by a framework dossier.

## 8. AI-Operability Fixture

There is no assumed human development team. Each candidate must show how the approved AI-operated model can maintain it:

1. a fresh implementation AI receives a bounded `TASK-xxx` context pack without reading the whole project;
2. consumer UI, domain/data rules, native/platform exceptions and release configuration have explicit contracts;
3. implementation, review and validation are separate evidence-producing tasks;
4. an upgrade must expose changed dependencies, native exceptions, affected contracts and required revalidation;
5. both platform release paths must be reproducible and recoverable without one opaque personal workstation;
6. critical product truth uses portable formats and has a documented framework-exit boundary;
7. failure to obtain trustworthy AI evidence is `HELD`, not assumed correct.

AI does not replace these external authorities:

- the owner's legal identity and Apple/Google store-account actions;
- access to real Android and iPhone devices and human testers;
- the Google Play closed-test population and waiting period applicable at release time;
- real assistive-technology validation;
- qualified review of safety-critical motorcycle guidance and source claims;
- tax, legal or payment-account actions if monetization requires them.

## 9. Staged Cost Fixture

The cost worksheet uses ranges and trigger points rather than pretending every future invoice is known.

| Stage | Mandatory baseline | Preferred low-cost path | Hold/approval trigger |
|---|---|---|---|
| Planning | `USD 0` incremental software spend | Local documents, official sources and approved AI tools | Any proposed paid research/tool subscription |
| Development preparation | No provider assumed | Free/local/open-source tooling and capped free tiers | Paid build service, backend, analytics or AI dependency |
| Device validation | Real Android and iPhone access is mandatory | Existing/borrowed devices and organized testers | Device purchase or paid device-lab plan |
| Android release preparation | Google Play Console `USD 25` one-time, owner-approved | Buy only before account/test window requires it | Material tax/currency change or extra service |
| iOS release preparation | Apple Developer Program `USD 99/year`, owner-approved | Buy only before TestFlight/App Store distribution requires it | Mac/hosted-build/device cost not already available |
| Initial operations | Aim for capped/free infrastructure where safe | Spend alerts, quotas, export and provider-exit path | Any recurring charge or uncapped usage billing |
| Growth | Scale-triggered only | Recalculate at 10,000 and 50,000 MAU fixtures | User approval before raising a cap or tier |

Store prices are the verified baseline on 2026-09-17 and must be rechecked before purchase. Taxes and currency conversion
are not included. Store-fee approval is not blanket approval for hosting, build, device, domain, expert or legal costs.
Depending on the Apple purchase/renewal dates, a 24-month comparison contains one or two `USD 99` Apple membership
payments; together with Google, the store-only 24-month baseline is therefore `USD 124–223` before tax/currency effects.

Every option's 24-month worksheet also carries explicit, separately approved rows for:

- Mac/Xcode access or hosted macOS/build service;
- real Android/iPhone access, closed-test coordination and any tester incentive;
- VoiceOver/TalkBack validation and qualified motorcycle safety/content review;
- backend/database, storage, backup, CDN and outbound data transfer;
- identity, email/SMS, crash reporting, telemetry and analytics;
- build artifacts, SBOM/provenance, signing and security scanning;
- domain plus required privacy/support pages;
- source/content licensing, legal/tax/insurance needs if applicable;
- user support, incident response, emergency reach-back and independent AI review capacity.

A free tier is accepted as low-risk only when it has a usable cap or overage shutdown, spend alerts, data export and a
documented provider-exit path. Otherwise the affected capability remains `HELD` until its financial exposure is approved.

Every technology dossier must separate:

- unavoidable product-wide cost;
- cost caused by that technology choice;
- optional convenience cost;
- scale-triggered cost;
- exit/migration cost;
- an unresolved amount that cannot honestly be priced yet.

## 10. Equal Pass/Hold/Reject Rule

A candidate may proceed only when every S1–S15 scenario has the same fixture and evidence schema. No weighted score may
cancel a failure in safety, data continuity, accessibility, release integrity or recoverability.

- `PASS`: credible official evidence plus a complete Kavriva walkthrough and later acceptance plan;
- `HELD`: critical evidence, owner/capacity, numeric price or real-device validation is still missing;
- `REJECT`: the proposed architecture requires an unsafe bypass, unbounded cost/dependency, lost user truth or an
  unsupported critical path with no owned fallback.

Framework convenience, popularity or AI familiarity is evidence only for the work it actually reduces. It does not earn
credit for shared backend/content obligations that every option must implement.

## 11. Owner Approval

The recommended defaults above ask the owner to approve only product outcomes, not technical implementation:

1. support a bounded recent-device range instead of every old phone;
2. plan for both stores without requiring simultaneous launch;
3. use the proposed compact/offline data limits as fair comparison numbers;
4. compare first release plus 24 months and four planned release windows per year;
5. treat real-device, accessibility, store-account and qualified safety/content review as unavoidable external evidence;
6. keep every unlisted paid subscription subject to separate price disclosure and approval.

Before the final technology recommendation, the owner must also confirm what resources already exist (Mac access,
Android/iPhone access, domain and current AI plan), the actual 12–24 month cash ceiling, whether both stores must launch
within that horizon, and whether hosted build/CI is acceptable if a free/local recoverable path is documented. Tester,
accessibility and qualified safety/content-review access may use organized or borrowed capacity, but inability to obtain
required evidence holds release; it does not lower the safety bar.

The owner approved this common fixture on 2026-09-17 with:

> onaylıyorum

The listed comparison constants are now frozen for equal Phase-4 candidate dossiers. Changing one requires a recorded
fixture revision applied to all five candidates. This approval does not select a framework, authorize code, approve an
unlisted paid service or pass Gate 4 -> 5.
