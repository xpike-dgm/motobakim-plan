# ADR-013 — Mobile Build, Signing and Split/Hybrid Release Operations

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-015, user-approved under `DEC-0045`) compared four build/release operating-model families
through official research, 64 failure rows, REVIEW-005 remediation and independent REVIEW-006 PASS. Conclusion:
Android release continuity stays active and independent of iOS/macOS readiness; split/hybrid is the reversible
operating shape; iOS/macOS activation stays held until real Mac/Xcode access, Apple signing custody,
provider-neutral provenance, no-owner-debug recovery and clean-room rebuild are proven. This ADR locks that
operating model on top of ADR-007 (supply chain) and ADR-008 (mobile framework). It selects no Mac, hosted-build,
CI, mobile-CI or Xcode Cloud provider or plan, and authorizes no account, purchase, build, signing setup, store
submission or final budget.

## Decision Drivers

- Android-first delivery must never wait for an iOS/Mac path; early macOS spend must be avoidable.
- Borrowed iPhones solve device validation only — never confused with Mac/Xcode build access.
- macOS cost, Xcode lifecycle and provider failures must be contained to the iOS lane, not shared with Android.
- Signing secrets and store authority must stay separable from CI execution, recoverable and owner-controlled.
- The nontechnical owner handles business/identity approvals and plain-language go/no-go only — never terminals,
  logs, Xcode, Gradle, certificates, SSH or CI configuration.

## Options Considered

### Option A — Single unified pipeline for both stores now (rejected)

One provider/lane building Android and iOS together from day one. Rejected: forces macOS commitment before iOS
evidence exists, couples Android continuity to iOS readiness, and maximizes the blast radius of a provider failure.

### Option B — Split/hybrid: independent Android lane, gated iOS lane (chosen)

Android stays on a low-cost, replaceable build/release lane; iOS/macOS capacity activates only when needed and
stays separable. Containment is conditional on shared Flutter dependencies not forcing cross-lane migration.

### Option C — Manual/local builds only (rejected as the model)

Owner-machine builds would drag the nontechnical owner into toolchain repair and destroy reproducibility and
provenance. Local Android lanes may still play a bounded early role, but never as owner-operated release
infrastructure.

## Decision

Kavriva adopts Option B with the following locked rules:

1. **Android continuity is mandatory and independent:** canonical source stays outside build providers; build
   success is never release approval; Android signing/upload-key custody and Google Play authority stay separate
   from CI execution; artifact provenance binds canonical source, build/version identity and digest;
   machine-readable build status with technical recovery ownership; least-privilege secret handling with
   redaction review; spend/quota/billing visibility with safe hold; exportable artifacts/evidence plus a
   provider-exit runbook.
2. **iOS/macOS activation gate (all must be proven separately):** real Kavriva Mac/Xcode execution access; Apple
   certificate/profile/private-key custody with rotation/revocation/recovery and App Store Connect role
   boundaries; provider-neutral artifact provenance; no-owner-debug routine and incident recovery; clean-room
   rebuild and provider replacement without copying opaque provider state. Until then, iOS stays `HELD` rather
   than weakening these gates — no fixed Mac, hosted capacity or paid macOS commitment before the gates require
   and justify it.
3. **Separation of powers:** build execution, signing/provisioning, artifact provenance, release approval, store
   identity/roles, upload transport and physical-device validation stay distinct. A future provider may execute
   build/signing steps but must never become canonical source, release approval, sole signing-secret holder,
   protected audit authority or an exit dependency. Key loss/exposure means revoke/rotate/reissue plus clean
   rebuild — never copying a compromised credential elsewhere.
4. **Capability classification:** mandatory for first Android release — the item list in rule 1. Deferrable until
   iOS activation — real Mac/Xcode path, Apple signing/Connect setup, any Xcode Cloud bootstrap, borrowed-iPhone
   validation, iOS store transport. Optional (each needs separate evidence) — provider-managed signing, long
   retention, extra concurrency, provider AI/debug summaries as helper signals only. Scale-triggered (not current
   recommendations) — paid Xcode Cloud compute above allowance, extra concurrency, annual/unlimited plans,
   dedicated Mac/host capacity, enterprise support/SLA, warm secondary provider.
5. **Cost reading carried forward:** low-volume Linux/Android compute can be inexpensive and some hosted macOS
   fixtures fit near the planning range at low usage — but higher macOS usage, dedicated hardware, support,
   retention, incident/operator labor and exit work can exceed it, and physical-Mac hardware looks acceptable
   only under long amortization with adjunct costs still held. The TRY 2,000–3,000/month non-store figure stays
   planning context, never purchase authority; store fees stay governed separately.

## Rationale

Split/hybrid buys Android momentum without macOS commitment while keeping iOS honest: every iOS dependency
(cost, custody, recovery, rebuild) must prove itself before it can block, bill or break anything. Separation of
powers keeps a build provider a replaceable executor instead of a second release authority.

## Consequences

### Positive

- First release can proceed on Android with minimal fixed cost and no Mac dependency.
- iOS lane failures (price spikes, stack retirements, provider outages) cannot stop Android.
- Signing/store authority stays recoverable and owner-controlled by construction.

### Negative / Trade-offs

- Two-lane thinking (provenance, status, runbooks per lane) is permanent planning overhead.
- iOS stays unavailable until five evidence gates pass — a real calendar cost if Apple-side needs arrive early.
- Shared Flutter upgrades must be watched for cross-lane migration pressure.

## Prohibited / Constrained Alternatives

- Unified both-store pipeline committing macOS spend before iOS gates pass.
- Borrowed-iPhone access counted as build access; provider-managed signing without proven custody/rotation/exit.
- Owner terminal/log/Xcode/Gradle/CI-config/signing/SSH/cache debugging in any form.
- Canonical source, release approval or signing authority moving into a provider.
- Any physical Mac, hosted Mac, general CI, mobile CI or Xcode Cloud provider/plan, account, purchase, build,
  signing setup, store submission, final budget or production activation — none authorized by this ADR.

## Revisit Triggers

- Evidence shows the split boundary cannot hold (shared dependencies force cross-lane migration) or a concrete
  provider passes the full iOS gate package with capped, exportable, no-owner-debug operation — resolved by
  superseding ADR.
- Exact provider, plan fit, failed-payment behavior, stack lifecycle, key backup location, operator identity and
  real tax/FX/egress/support/incident/exit labor remain HELD for later procurement evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0045`, `DEC-0032` (binding directions)
- `05_ADR/RECORDS/ADR-007__SUPPLY_CHAIN_AND_RELEASE_GOVERNANCE.md`
- `05_ADR/RECORDS/ADR-008__CONSUMER_MOBILE_FRAMEWORK.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-015__MOBILE_BUILD_RELEASE_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-015__MANAGER_SYNTHESIS.md`
- `00_CONTROL/DRIVE_ARTIFACT_INDEX.md` (TASK-003 / REVIEW-005 / REVIEW-006 links)
- Downstream: Phase-6 release-task planning; ADR-015 (build task topology)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
