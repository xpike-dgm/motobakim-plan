# DEBATE-015 — Mobile Build/Release Access, Hosted Build Cost and AI Operability Manager Synthesis

Status: `USER-APPROVED PHASE-4 WORKING DIRECTION / DEC-0045 / NO PROVIDER WINNER`

## Nontechnical Decision

Kavriva should preserve Android-first delivery as the active release path and keep iOS activation HELD until a real
Mac/Xcode access path, signing custody, artifact provenance, no-owner-debug recovery and clean-room exit are proven.

The approved working direction is a split/hybrid operating boundary:
- Android build/release continuity remains independent of iOS/macOS readiness;
- Android should use a low-cost, replaceable Linux-capable build path when implementation is later authorized;
- iOS/macOS capacity should be activated only when needed and only through a path that can be replaced without moving
  canonical source, release approval or signing authority into the provider;
- if the iOS lane cannot meet owner-operability, signing/security, safe-TCO and clean-exit gates, iOS remains HELD rather
  than weakening those gates.

This is an operating-model direction, not a provider, plan, hardware or purchase recommendation.

## Why This Direction

The research and reviews support four core conclusions:

1. Borrowed iPhone access solves only later physical-device validation; it is not Mac/Xcode build access.
2. Android does not need to wait for an iOS/Mac path, so early macOS spend can be avoided.
3. Dedicated Mac, general cloud CI and mobile-specialized CI all remain usable families, but none has Kavriva-specific
   proof of no-owner-debug operation or clean-room replacement.
4. Split/hybrid contains macOS cost, Xcode lifecycle and provider failures to the iOS lane while preserving Android
   continuity, provided shared Flutter dependencies do not force cross-lane migration.

## Binding Phase-4 Working Direction

If the owner approves this proposal, the Phase-4 working direction should be:

- Android-first release continuity is mandatory and independent of iOS Mac availability.
- Canonical source remains outside build providers.
- Build success is not release approval.
- Android signing/upload-key custody and Google Play authority remain separate from CI execution.
- Future Apple certificate/profile/private-key custody and App Store Connect authority remain separate from CI execution.
- Artifact provenance must bind canonical source, build/version identity and artifact digest.
- Machine-readable build status and technical recovery ownership are mandatory; the nontechnical owner receives
  plain-language escalation and business/identity approval requests only.
- Spend/quota/billing visibility and a safe hold are mandatory.
- Exportable artifacts/evidence and a provider-exit runbook are mandatory.
- iOS activation remains HELD until real Mac/Xcode execution, Apple signing custody, provider-neutral provenance,
  no-owner-debug recovery and clean-room rebuild are separately proven.

## First-Release Capability Classification

Mandatory for first Android release:
- Android build continuity independent of iOS;
- canonical source outside the build provider;
- Android signing/upload-key custody and Play authority separation;
- artifact provenance tied to canonical source and digest;
- explicit release approval separate from build success;
- machine-readable build status and technical recovery ownership;
- secret least-privilege/redaction review;
- spend/quota/billing visibility and safe hold;
- exportable release artifact/evidence and provider-exit runbook.

Deferrable until iOS activation:
- real Mac/Xcode execution path;
- Apple certificate/profile/signing custody and App Store Connect role/API setup;
- Xcode Cloud bootstrap, if ever evaluated;
- borrowed-iPhone physical validation;
- iOS-specific artifact/store transport.

Optional convenience:
- provider-managed signing only if custody/rotation/exit are proven;
- long provider artifact retention beyond the independent evidence need;
- extra concurrency before queue pressure is observed;
- provider AI/debug summaries as helper signals only.

Scale-triggered:
- paid Xcode Cloud compute above included allowance;
- additional CI concurrency;
- annual/unlimited plans;
- dedicated Mac/host capacity;
- enterprise support/SLA;
- warm secondary provider.

## Cost / Budget Interpretation

The prior TRY 2,000–3,000/month non-store figure remains planning context only.

Research indicates:
- low-volume Linux/Android build compute can be inexpensive;
- some macOS hosted-build fixtures can fit near the planning range at lower usage;
- higher macOS usage, dedicated hardware, support, retention, incident/operator labor and clean-exit work can exceed it;
- physical-Mac hardware may appear acceptable only under longer amortization while mandatory adjunct costs remain HELD.

Therefore the working direction should minimize fixed macOS commitment until iOS activation evidence exists. No current
price fixture is sufficient to select a provider or approve spend.

Store/platform fees remain separate from the non-store operating-cost context.

## Signing / Security Boundary

Build execution, signing/provisioning, artifact provenance, release approval, store identity/roles, upload transport and
physical-device validation stay separate.

A future hosted-build provider may technically handle build/signing steps, but it must not become:
- canonical source authority;
- release approval authority;
- the only holder of signing secrets without independent reissue/rotation/recovery;
- protected audit authority;
- an exit dependency that requires copying opaque provider state.

Key loss/exposure requires revoke/rotate/reissue and clean rebuild, not copying a compromised credential to another
provider.

## AI-Operability / Owner Boundary

The nontechnical owner must not be required to:
- inspect raw logs;
- debug Xcode, Gradle, CocoaPods, Ruby, Java, Flutter or runner images;
- repair certificates/profiles;
- SSH into a Mac/runner;
- edit CI configuration;
- perform cache/dependency surgery.

The technical recovery path belongs to the AI/operator role, with provider support or Apple/Google account-role action
used where required. The owner handles only explicit business, payment, identity and plain-language go/no-go decisions.

Documented APIs/CLIs are mechanism evidence only. They do not prove Kavriva-specific autonomous recovery.

## HELD Evidence After Research

The following remain HELD:
- a currently verified Kavriva Mac/Xcode execution path;
- live build/signing/provider/store account proof;
- Kavriva-specific no-owner-debug incident walkthrough;
- provider-neutral provenance implementation;
- clean-room cross-provider rebuild;
- exact AWS Mac TCO without an authorized region/instance fixture;
- Xcode Cloud build-minute-to-compute-hour normalization;
- exact Bitrise product/plan fit;
- exact Azure/Bitrise failed-payment behavior where not equally evidenced;
- eventual Bitrise Xcode-stack lifecycle;
- Kavriva-specific secure key backup/recovery location, operator identity and support contacts;
- actual tax/FX/storage/egress/support/incident/operator/exit labor.

These HELD items are not failures of the working direction. They are gates that must be proven before the corresponding
capability is activated or purchased.

## Evidence and Review History

- TASK-003 compared four equal operating-model families with at least two mechanisms/reference candidates per family.
- The failure walkthrough contains 16 mandatory scenarios × four families = 64 rows with eight required fields.
- REVIEW-005 returned CHANGES_REQUESTED with one Major M-1 across all 64 Recovery owner fields and two Minor findings.
- The remediation changed all 64 Recovery owner fields to scenario/family-specific values while leaving the other seven
  mandatory fields unchanged; both Minor findings were corrected.
- REVIEW-006 returned PASS with no Critical, Major or Minor findings and verified no remediation regression.
- TASK-003 is DONE after manager readback.

## User Approval

The user explicitly approved this Phase-4 working direction under `DEC-0045`.

## Boundary

This proposal does not approve a Mac purchase, hosted Mac, CI/CD provider, mobile CI provider, Xcode Cloud use, account,
plan, trial, signing setup, certificate/profile/key creation, build, code, store submission, final budget, Phase-5 ADR
or Gate 4 -> 5 transition.
