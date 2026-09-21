# ADR-007 — Software, Content Supply Chain and Release Governance

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-005, user-approved under `DEC-0027`) defined how Kavriva proves what source, dependencies,
approvals and controlled build produced every deployable artifact, separates release authorities, and promotes,
stops, rolls back or recovers releases without letting a compromised dependency, pipeline, key, store account or
administrator silently change consumer meaning. This ADR converts that direction into binding governance on top of
ADR-001–ADR-004 (boundaries, platform, publication, identity). It selects no source host, CI/CD provider, registry,
cloud, signing service, store-account design, SBOM format, feature-flag product or deployment technology, and
approves no OTA channel.

## Decision Drivers

- The complete high-consequence path (source → dependency → build → provenance → sign → promote → deploy →
  consumer) must have no single silent point of control.
- Promotion must move the exact verified artifact, never a rebuild that merely claims the same source.
- Configuration, flags, migrations and transforms that can change safety meaning are releases, not informal edits.
- Old, offline and partially updated clients stay inside the threat model; stopping a rollout never downgrades them.
- Small-team staffing gaps must hold releases visibly rather than collapse independence.

## Options Considered

### Option A — Developer-driven release with shared credentials (rejected)

Fast initially, but one workstation/account can alter source, build, sign and ship; evidence and recovery are weak.

### Option B — Automated pipeline with review gates but mutable/opaque builders (insufficient alone)

Better repeatability, but a compromised build environment or action can substitute output, and promotion evidence may
not prove the artifact corresponds to reviewed source.

### Option C — Provenance-bound controlled promotion (chosen)

Reviewed immutable inputs enter an isolated build; the resulting immutable artifact carries verifiable
provenance/SBOM, is independently verified, signed and promoted by scoped identities, and deployed unchanged through
environments.

### Option D — Fully manual/offline ceremony for every release (reserved, not the pipeline)

Protects a small set of root/recovery keys, but routine manual copying/signing is slow, inconsistent and
error-prone. Reserved for root/recovery operations only.

## Decision

Kavriva adopts Option C (with Option D reserved for root/recovery keys) with the following locked rules:

1. **Distinct release authorities:** consumer app binary, internal web deployment, backend/API/service release,
   database/schema/data migration, technical content release, configuration/feature policy, emergency suspension and
   (explicitly unapproved) future OTA remain separate actions, credentials, audit events and consequence checks.
   No shared "release admin" superpower; holding several operational responsibilities never merges their authorities.
2. **Immutable traceable artifacts:** every production artifact is immutable, uniquely identified and traceable to
   exact reviewed source, dependency lock, build instructions/environment, builder identity, approvals, verification
   results and digest. Provenance/SBOM/signature must bind the exact artifact digest — a valid document about
   another artifact is failure.
3. **Promote, don't rebuild:** production receives the exact verified artifact; per-environment rebuilds are
   forbidden. Dependencies and pipeline components pin to immutable verified identities; mutable branches/tags are
   never release authority; untrusted change/build contexts never touch production secrets, signing keys or
   deployment authority.
4. **Independent verification:** the verifier is independent of the build worker and checks subject digest,
   builder/signer identity, policy version, attestation chain, declared input closure and revocation state; the
   trust-root inventory (repository, workflow, builder, runner, toolchain, registry, verifier, signer, promoter,
   target) is explicit; unknown or inconsistent trust state holds promotion. Known-good and incident copies keep
   independent protected retention.
5. **Scoped custody:** signing/deployment keys separate by release domain and environment, protected from routine
   export, revocable, dual-controlled across creation/use/rotation/revocation/recovery/destruction; routine CI
   cannot reach root/recovery material. Store/platform account ownership is organizational, never one personal account.
6. **Consequence-proportionate independence:** incompatible author/reviewer/verifier/signer/promoter roles cannot
   collapse onto one human via aliases, service accounts or emergency access; unavailable independent staffing holds
   the release visibly with owner and escalation.
7. **Everything meaning-changing is a release:** configuration, flags, templates, migrations and transforms are
   typed, versioned, reviewed, attributable, consequence-classified releases inside the closed release-meaning graph
   (binary, API/contract window, content manifest, effective config, schema/migration state, external model
   identities, offline package closure, release/suspension generations). A flag/config can never introduce semantics
   outside the current client capability envelope and can never clear emergency suspension.
8. **Safe rollout and rollback:** staged rollout declares population, observation, pause/stop, escalation and
   completion; stopping never claims to downgrade updated clients. Rollback is a new controlled promotion to a
   still-trusted, compatible, non-revoked artifact — signing alone is insufficient. Migration uses explicit
   planned/started/partial/reconciling/reconciled states; rollback never silently discards new valid data or
   reactivates revoked authority; generations never move backward through restore, failover or rollback.
9. **Incident discipline:** every incident builds an auditable impact graph from compromised source/dependency/
   workflow/builder/key to affected artifacts, environments, cohorts, offline packages, content/config states and
   rollout — with a protected copy outside the possibly compromised plane. Rotation, rebuild or rollback does not
   close the incident until the graph reconciles and artifacts re-verify or revoke/suspend.
10. **OTA denied by default:** no over-the-air/runtime code-update channel is approved. Any future OTA needs its own
    release authority, explicit mutable envelope, signing/versioning, provenance, compatibility, anti-rollback,
    staged rollout, revocation and platform-policy review — and may never silently replace native/security-critical
    code, widen permissions or merge content approval into software publication.

## Rationale

Only provenance-bound promotion closes the substitution gap between reviewed source and running artifact; only
separated authorities and scoped custody stop one compromise from owning the whole path; only graph-closed releases
stop configuration and migration from becoming shadow publication channels. Denying OTA by default removes the
highest-risk silent-update class until it earns its own authority.

## Consequences

### Positive

- Every shipped byte is attributable to reviewed inputs through an independently checked chain.
- Compromised dependencies, runners, registries, keys and accounts produce bounded, traversable impact instead of
  silent consumer harm.
- Rollout, migration and incident behavior stay explicit across online, old, dormant and offline clients.

### Negative / Trade-offs

- Build isolation, pinning, attestation, verification and custody are permanent pipeline cost and complexity.
- Strict independence slows high-consequence releases and visibly holds them when staffing is missing.
- The 28-acceptance-scenario suite (moved tags, malicious actions, substituted artifacts, stopped rollouts,
  region-split migrations, flag-driven safety changes and others) must be walked for every candidate architecture.

## Prohibited / Constrained Alternatives

- Developer workstations or shared credentials as release authority; mutable tags/branches as release identity.
- Per-environment rebuilds; `latest` pointers, filenames or registry locations as artifact identity.
- Signing alone as rollback justification or revocation override; key rotation presented as incident closure.
- Configuration/flag/migration changes outside release control; normal config clearing emergency suspension.
- Unapproved OTA/runtime code-update channels of any kind.
- Any source host, CI/CD provider, registry, cloud, signing service, SBOM format, flag product, deployment
  technology, account, purchase or production deployment — none authorized by this ADR.

## Revisit Triggers

- Evidence shows the provenance/verification bar cannot be operated within bounded AI workflows, or a concrete tool
  chain passes the full contract including independent rebuild comparison — resolved by superseding ADR.
- Consequence tiers, quorum matrix, required SBOM/attestation formats, dependency/license/EOL policies, runner
  isolation bounds, key hierarchy details, rollout populations, support windows, migration acceptance criteria,
  retention policy and all physical providers remain HELD for later evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0027` (binding working direction)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `05_ADR/RECORDS/ADR-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md`
- `05_ADR/RECORDS/ADR-004__IDENTITY_AUTHORIZATION_SESSION_RECOVERY_AND_PRIVILEGED_ACTIVATION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-005__REVIEW_A_RELEASE_GOVERNANCE_OPERATIONS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-005__REVIEW_B_SUPPLY_CHAIN_SECURITY.md`
- Downstream: ADR-008 (mobile binary provenance), ADR-010 (web deployment), ADR-013 (build/release operations)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
