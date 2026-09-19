# DEBATE-015 — Mobile Build/Release Access, Hosted Build Cost and AI Operability Requirements Synthesis

Status: `ACTIVE / PRIMARY RESEARCH READY / NO-CODE / NO PROVIDER WINNER`

## Decision Question

Kavriva'nın Android-first / iOS-later Flutter yönü için, teknik olmayan tek owner'ı yerel build-system debugging'e
zorlamadan hangi build/release access işletim modeli Phase 4'te güvenli, bütçesi sınırlı ve geri döndürülebilir çalışma
yönü olarak taşınabilir?

Bu debate bir CI/CD, hosted Mac, cloud-build veya store provider seçmez. Amaç Mac/iOS build erişimi, hosted-build
alternatifleri, signing/key custody, 12–24 aylık safe TCO, failure recovery, provider exit ve AI-operability sınırlarını
eşit kanıtla araştırmaktır.

## Authority and Existing Directions

This topic is selected from the already-recorded unresolved portion of `TSQ-008`.

Existing directions remain unchanged:
- planning is no-code; executable prototype/spike/build is not authorized;
- consumer mobile working direction is Flutter;
- Android is first; iOS follows later;
- direct Android-device access exists;
- a borrowed iPhone can be arranged for later physical-device validation;
- Mac access is not yet confirmed;
- a capped hosted-build route may be considered but is not yet approved;
- the prior TRY 2,000–3,000/month non-store ceiling is planning context only, not purchase authority;
- provider accounts, paid plans, store submission, code signing setup and Phase-5 ADR are not authorized.

Borrowed iPhone access is device-test access only. It must not be treated as proof of Mac/Xcode build access.

## Non-Negotiable Owner / Authority Boundary

The owner is nontechnical and must not be required to:
- install or debug Xcode, CocoaPods, Ruby, Gradle, Java, Flutter SDK or CI agents;
- inspect raw build logs to diagnose dependency/toolchain failures;
- repair signing certificates/profiles or secret stores manually;
- SSH into hosted Macs or self-managed runners;
- edit CI YAML/pipeline code;
- perform runner-image surgery, cache surgery or dependency pin repair;
- operate provider consoles as the normal recovery path.

Owner actions may include explicit business/identity/payment approvals and high-level go/no-go decisions. Technical
recovery belongs to the AI/operator path and must be documented separately.

Build/CI systems must not silently become:
- source-of-truth for product code or canonical project state;
- release approval authority;
- signing authority without explicit custody/rotation/exit rules;
- protected audit authority;
- provider-specific lock-in that cannot be cleanly exited.

## Store / Signing Separation

Research must distinguish:
1. build execution;
2. code-signing material and provisioning;
3. artifact storage/provenance;
4. release approval;
5. store account identity/roles;
6. upload/submission transport;
7. physical-device validation.

A hosted-build provider may perform technical steps, but store/account ownership and release authority must remain
explicit. Provider-managed signing convenience is not automatic acceptance evidence.

## Four Equal Operating-Model Families

Research must compare all four families to the same standard:

A. Dedicated macOS environment under Kavriva control.
   - Examples may include a physical Mac owned/borrowed for build use and a dedicated hosted Mac.
B. General cloud CI with macOS/Linux runners.
   - Examples may include GitHub Actions macOS/Linux and another current general CI with macOS runners.
C. Mobile-specialized managed CI/CD.
   - Examples may include Codemagic and Bitrise.
D. Split/hybrid capped path.
   - Android uses lower-cost Linux/local CI; iOS/macOS is invoked only when needed through a replaceable on-demand path.
   - Examples may combine an Android Linux runner with Xcode Cloud, Codemagic, Bitrise or another current official mechanism.

Each family must have at least two concrete current mechanisms/candidates. Re-use of a candidate in Family D is allowed
only to isolate the architecture/operating-model effect; it must not be counted as fake breadth.

## Required Research Dimensions

For every family/candidate, research at least:

### Build and platform access
- current Flutter support path for Android and iOS;
- macOS/Xcode requirement and current supported toolchain constraints;
- runner images, Xcode versions, Flutter version pinning and update cadence;
- local/dedicated versus ephemeral runner behavior;
- physical iPhone validation boundary;
- Android-first continuity if the iOS path is unavailable.

### Signing and release security
- certificate/profile/key custody;
- bring-your-own versus provider-managed signing;
- exportability, rotation, revocation and recovery;
- secret storage and log-redaction controls;
- least-privilege service identity / store-role model where documented;
- artifact integrity/provenance and reproducibility evidence;
- source-code exposure to provider infrastructure.

### AI-operability
- documented API/CLI/repo-defined workflow support;
- ability to operate routine builds without owner GUI/debugging;
- failure visibility and machine-readable status;
- support/escalation model;
- provider-console-only actions that would create owner dependency;
- exact steps that still require human identity/payment/store authority.

Documentation showing automation capability is mechanism evidence only; do not claim a fully autonomous Kavriva path
without real implementation proof.

### Cost and capacity
- free/capped allowance;
- macOS versus Linux runner/build pricing;
- concurrency;
- build-minute/credit accounting;
- artifact/log/cache retention charges;
- storage/egress;
- signing or distribution adjuncts;
- support/SLA tiers;
- dedicated Mac hardware/rental and maintenance where relevant;
- incident/upgrade/operator labor;
- currency and tax/billing uncertainty.

Separate required store/platform membership fees from the project's non-store operating-cost ceiling.

For normalized comparison, include current official price formulas and sensitivity at:
- 100 macOS build-minutes/month;
- 500 macOS build-minutes/month;
- 1,500 macOS build-minutes/month;
and the analogous Linux/Android build cost where billed separately.

These are synthetic comparison fixtures, not production forecasts.

Where a TRY comparison is useful, use a current official/primary FX source and show it as illustrative only. Do not turn
the TRY 2,000–3,000/month planning ceiling into a purchase commitment.

### Lifecycle and exit
- provider outage/status;
- quota/billing hold;
- runner-image/toolchain deprecation;
- migration of build configuration;
- signing-key/certificate recovery;
- artifact/source-untouched export;
- clean-room provider replacement;
- provider closure/plan removal;
- owner-safe incident escalation.

## Mandatory Failure Scenarios

Apply all four families to all 16 scenarios:

1. Android-first release work continues while no iOS/Mac path is ready.
2. iOS build becomes necessary but no usable Mac access exists.
3. Physical iPhone is temporarily unavailable for validation.
4. macOS runner/build-minute quota is exhausted.
5. Billing/payment hold blocks the hosted build path.
6. CI/build provider outage occurs near a release.
7. Required Xcode/iOS SDK version changes or an old runner image is removed.
8. Flutter/plugin/native dependency requires a newer incompatible toolchain.
9. Signing certificate/provisioning profile expires, is revoked or must rotate.
10. Signing secret/key material is lost, exposed or unavailable.
11. Cache/dependency corruption creates non-reproducible or stale builds.
12. Build artifact provenance/release candidate identity is ambiguous.
13. Provider-specific pipeline/configuration must be replaced cleanly.
14. Source code, secrets or build artifacts face provider/security exposure risk.
15. Build volume/concurrency causes a cost spike above the planning envelope.
16. Nontechnical owner receives a failed build/release incident.

For every scenario/family row, state all eight fields explicitly and substantively:
- expected state;
- safe hold;
- evidence;
- recovery owner;
- next action;
- security/signing impact;
- cost impact;
- exit impact.

Field labels alone are not enough. Unknown or unproven behavior remains `HELD`.

## Required Official / Primary Evidence

Research should prefer:
- Apple Xcode/Xcode Cloud, code-signing/provisioning, App Store Connect/TestFlight and Apple Developer official docs;
- Flutter official Android/iOS build/release docs;
- Android/Google Play official signing/release docs where relevant;
- official pricing, runner-image, limits, security/secrets, artifact retention and support docs for every candidate;
- official status/lifecycle/deprecation docs where available;
- official repository/release documentation for tooling used as evidence.

Time-sensitive pricing, runner-image and platform/toolchain claims must carry an access date.

Marketing phrases such as "zero maintenance", "secure", "fast", "fully managed", "unlimited", "AI-ready" or "one-click"
are not acceptance evidence by themselves.

## Required Deliverable

Drive task:
- `CTX-P4-015 — MOBILE BUILD RELEASE ACCESS AND AI OPERABILITY`
- `TASK-003 — DEBATE-015 MOBILE BUILD RELEASE PRIMARY RESEARCH`

Research output must include:
- nontechnical executive summary;
- requirements trace;
- build/release authority-plane separation;
- equal family/candidate matrix;
- official-primary source ledger;
- signing/key-custody matrix;
- AI-operability / owner-action matrix;
- 16 × 4 = 64 failure rows with all eight mandatory fields;
- 12- and 24-month safe-TCO comparison with current pricing and sensitivity;
- non-store ceiling analysis separate from required store fees;
- provider outage/quota/billing and support analysis;
- toolchain/lifecycle/deprecation analysis;
- clean-room exit analysis;
- unresolved evidence / HELD items;
- recommended next evidence;
- mandatory / deferrable / optional / scale-triggered first-release build/release capabilities.

At most one conditional Phase-4 direction may be proposed. It must remain architecture/operating-model level; no
provider, plan or purchase winner may be selected.

## Boundary

No code, pseudocode, CI configuration, workflow YAML, build, signing setup, certificate/profile creation, secret
generation, account creation, trial, plan selection, purchase, payment, store submission, deployment, final budget
commitment, Phase-5 ADR or Gate 4 -> 5 transition is authorized.

A later research PASS would mean only that the evidence package is sufficient for manager synthesis; it would not be
production proof, a real build pass or owner approval.
