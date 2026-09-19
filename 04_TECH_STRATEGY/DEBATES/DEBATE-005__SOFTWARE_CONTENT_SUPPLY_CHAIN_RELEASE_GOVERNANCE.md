# DEBATE-005 — Software, Content Supply Chain and Release Governance

Status: `APPROVED WORKING DIRECTION — DEC-0027 / ADR PENDING`
Date: 2026-09-17
Scope: Consumer mobile, browser Internal Operations, backend/data, technical content and emergency controls
Planning constraint: No application code, prototype or executable spike

## 1. Decision question

How should Kavriva prove what source, dependencies, approvals and controlled build produced every deployable artifact;
separate the authorities for software, content, configuration, data and emergency actions; and safely promote, stop,
roll back or recover releases without letting a compromised dependency, pipeline, key, store account or administrator
silently change consumer meaning?

This debate defines governance and security properties. It does not select a source host, CI/CD provider, package registry,
cloud, signing service, app-store account design, SBOM format, feature-flag product or deployment technology.

## 2. Existing authority

- `DEC-0021`: planning is no-code; Internal Operations is browser-based.
- `DEC-0024`: old/incompatible clients and mixed packages cannot gain positive application authority.
- `DEC-0025`: complete approved meaning, fenced publication/suspension generations, restore quarantine and protected audit.
- `DEC-0026`: scoped server authorization, privileged recovery, controlled policy changes and protected audit.
- `TSR-010`: ecosystem/plugin abandonment and OS compliance risk.
- `TSR-011`: reviewed/published mismatch and replay/downgrade risk.
- `TSR-013`: old clients may not understand safety semantics.
- `TSR-017`: dependency, CI, signing key or OTA compromise risk.
- `TSR-024`: transforms/configuration can change approved consumer meaning.
- `TSR-025`–`028`: publication/suspension races, common-mode emergency failure and restore/audit risks.

## 3. Release authorities that must remain distinct

| Authority | Changes | Must not automatically grant |
|---|---|---|
| Consumer app binary release | Native/app code, bundled resources, capability envelope. | Technical-content approval, backend data mutation or emergency suspension. |
| Internal web deployment | Operator UI and web application behavior. | Server authorization-policy bypass, content approval or audit alteration. |
| Backend/API/service release | Server behavior, contracts and policy enforcement. | Database destructive change or positive content publication by itself. |
| Database/schema/data migration | Stored structure or controlled data transformation. | Truth correction without IDCO review, audit erasure or silent rollback. |
| Technical content release | Approved claims/guides/media and eligibility context. | Executable software update or mobile-store authority. |
| Configuration/feature policy | Runtime behavior inside a pre-approved capability envelope. | New executable authority, review bypass or safety semantics unknown to the client. |
| Emergency suspension | Narrow negative eligibility/control action. | Replacement content, ordinary publication or software deployment. |
| Future OTA/runtime update | Only the explicitly authorized mutable software/resource envelope. | Native/security boundary bypass, store-policy evasion or arbitrary content authority. |

One person may hold multiple operational responsibilities where later policy permits, but these are separate actions,
credentials, audit events and consequence checks. A shared “release admin” superpower is not the target model.

## 4. Threat and failure model

The policy must remain safe when:

- a direct or transitive dependency, package registry or maintainer account is compromised;
- a mutable tag/branch/action changes without the reviewed repository change;
- an untrusted pull request or build script attempts to steal CI secrets;
- a build runner, artifact registry, deployment identity or release account is compromised;
- source review passes but the production artifact is rebuilt differently;
- an SBOM/provenance file describes a different artifact than the one shipped;
- a signing key, upload key, store account or emergency credential is lost/compromised;
- a feature flag or remote configuration silently changes safety meaning;
- a database migration succeeds partially, destroys information or becomes incompatible with old servers/clients;
- a staged rollout is stopped after some devices/environments already updated;
- rollback selects an artifact that is signed but now vulnerable, incompatible or recalled;
- an app store review/update delay leaves old clients active;
- a compromised release exists on offline/dormant devices;
- restore/failover returns an old deployment, policy, key or revocation state;
- release evidence/audit is unavailable, inconsistent or under the same administrator’s control.

## 5. Non-negotiable invariants

1. Source review, build, signing, promotion, deployment and consumer eligibility are separate transitions.
2. Every production artifact is immutable, uniquely identified and traceable to exact reviewed source, dependency lock,
   build instructions/environment, builder identity, approvals, verification results and resulting digest.
3. Production promotion uses the exact verified artifact; it is not rebuilt from source for each environment.
4. Provenance/SBOM/signature must bind the exact artifact digest. A valid document describing another artifact is failure.
5. Dependencies and pipeline components are pinned to immutable verified identities; mutable branches/tags are not release authority.
6. Untrusted change/build contexts cannot access production secrets, signing keys or deployment authority.
7. Signing and deployment credentials are scoped by release domain/environment, protected from routine export/use and revocable.
8. No single compromised developer, reviewer, CI worker, package maintainer, signer or publisher should silently control the
   complete high-consequence path.
9. Configuration, flags, templates, migrations and transforms that can change meaning are governed release artifacts.
10. Technical content continues through DEBATE-003; software CI success cannot approve technical truth.
11. Emergency suspension remains independent negative authority and cannot be overwritten by software/config deployment.
12. Rollback is a new controlled promotion to a still-trusted, compatible and non-revoked artifact; signing alone is insufficient.
13. Release/revocation generations cannot move backward through restore, failover or rollback.
14. A staged rollout does not imply full delivery, and stopping it does not downgrade already updated clients.
15. Old clients and old backend versions remain in the compatibility/threat model until authoritative support policy removes them.
16. If provenance, required approval, artifact identity, revocation status or protected audit is unknown, high-consequence
    promotion is held; missing evidence never becomes permission.
17. Artifact authenticity, release approval/provenance and current eligibility/revocation are separate truths. A formerly
    valid signature cannot override a newer revocation/suspension or unknown critical eligibility.
18. Every release domain and restore operation is fenced against the current protected suspension/revocation generation;
    an older/in-flight binary, web, backend, migration or configuration action cannot indirectly clear a hold.
19. High-consequence human independence is mandatory, not achieved merely by separate credentials. If required staffing
    or an independent verifier/custodian is unavailable, the release remains visibly `HELD`.
20. Private/shared/community/official classification and disclosure scope remain part of release closure and propagate
    to bundled/generated artifacts, provenance, SBOM access and exports.

## 6. Governance alternatives

### Option A — Developer-driven release with shared credentials

Fast initially, but one workstation/account can alter source, build, sign and ship; evidence and recovery are weak.

Result: `REJECT`.

### Option B — Automated pipeline with review gates but mutable/opaque builders

Better repeatability, but a compromised build environment/action can substitute output; promotion evidence may not prove
the artifact corresponds to reviewed source.

Result: `INSUFFICIENT ALONE`.

### Option C — Provenance-bound controlled promotion

Reviewed immutable inputs enter an isolated build; the resulting immutable artifact carries verifiable provenance/SBOM,
is independently authorized, signed/promoted by scoped identities and deployed unchanged through environments.

Result: `RECOMMENDED BASELINE`.

### Option D — Fully manual/offline ceremony for every release

Can protect a small set of root/recovery keys, but routine manual copying/signing is slow, inconsistent and error-prone.

Result: `RESERVE FOR ROOT/RECOVERY OPERATIONS, NOT THE WHOLE PIPELINE`.

## 7. Recommended release chain

### 7.1 Source and change control

- protected canonical source and policy repositories;
- attributable change proposal and review; high-impact pipeline/policy changes receive security/release review;
- immutable source revision for every candidate;
- branch/rule changes, release workflow changes and reviewer policy are themselves controlled/audited;
- generated code/assets and external inputs record generator/source/version and are reviewed as release inputs;
- secrets never live in source, build logs, artifacts or untrusted change contexts;
- history rewrite or direct production branch/tag mutation is detected and denied for release authority.
- reviewed commit, merge identity, workflow digest, branch/review-policy version and rule changes bind to the candidate;
- repository administrators cannot silently weaken review/workflow rules and use the weakened rule in the same
  high-consequence release path; material policy author/approve/activate separation follows DEBATE-004.

Human independence is consequence-tiered. For high-consequence release, incompatible author/reviewer/verifier/signer/
promoter roles cannot be collapsed onto the same human through aliases, service accounts or emergency access. When the
required independent operator is unavailable, release stays `HELD` with owner/escalation. Pre-authorized backup/external
reviewers and key custodians require documented scope, competence, independence and expiry.

### 7.2 Dependency control

- declared dependency closure per artifact and environment, with explicit `KNOWN_COMPLETE`, `BEST_EFFORT` or `UNKNOWN` status;
- exact immutable resolution/lock with integrity verification; no floating release dependencies;
- approved source/registry and namespace ownership policy;
- dependency additions/updates are change proposals, not automatic truth;
- automated vulnerability, integrity, license and maintenance signals support review but do not auto-approve;
- unused dependencies are removed; build/test/dev dependencies remain in exposure inventory;
- exception records have reason, owner, scope, expiry, compensating control and re-review;
- compromise/removal/unavailability triggers impact traversal across built and deployed artifacts.
- every component has accountable owner, canonical source/registry, supplier/maintainer/support status, security contact,
  license decision, end-of-life/replacement trigger and incident containment path appropriate to its consequence;

The closure policy names runtime packages, build tools, compiler/toolchain, base/OS images, native/optional components,
generated assets/fonts, downloaded installers, dynamic fetches and build caches as applicable. High-consequence release
holds on `UNKNOWN`; `BEST_EFFORT` requires an attributable bounded exception and compensating evidence.

### 7.3 Controlled build

- clean, isolated, short-lived build environment from declared inputs;
- network/secret access denied by default and allowed only by named build-tier policy; every exception is scoped,
  attributable, time-bounded and included in provenance;
- untrusted pull requests/forks cannot access privileged runners, signing or deployment credentials;
- pipeline actions/plugins/tools are pinned and verified like dependencies;
- build instructions, builder identity, input digests and output digests are recorded in attested provenance;
- the required assurance per consequence tier is explicit: reproducible independent rebuild where supported, otherwise
  a separately justified hardened-builder/independent-verification control with owner, expiry and compensating evidence;
- test/security/quality results are linked to the exact candidate digest, not merely a branch name;
- build workers cannot independently grant final promotion authority.

### 7.3.1 Trust-root and verifier independence

The trusted computing/policy boundary is explicitly inventoried across repository administration, review rules, workflow
policy/actions, builder control plane, runner host/image/cache, toolchain/compiler/base image, dependency registry,
artifact/evidence registry, provenance verifier, signer, promoter and deployment target.

- the verifier is independent of the build worker and checks subject digest, builder/signer identity, policy version,
  attestation chain, declared input closure and revocation state;
- builder bootstrap, runner image, cache, toolchain and base image are verified/bound inputs;
- provenance acceptance policy is versioned, independently approved and included in verification evidence;
- unknown or inconsistent trust-root/input state holds promotion;
- artifacts/evidence/known-good and incident copies have independent protected retention so one compromised registry or
  CI account cannot rewrite the complete history.

### 7.4 Artifact and evidence package

Each candidate release package includes or links:

- release/domain/version and exact artifact digest;
- canonical source revision and reviewed change set;
- builder/workflow identity and build invocation/environment;
- dependency lock and SBOM bound to the artifact;
- provenance/attestation and verification result;
- required tests/scans and known accepted exceptions;
- signing identity/key version and signature status;
- API/schema/content/capability compatibility declaration;
- migrations, configuration/flags and rollback/recovery plan;
- approval/promotion/audit operation identities;
- known deployment/rollout state and revocation/suspension generation.
- classification/disclosure scope and derivative-propagation status;
- task/motorcycle-scoped offline package manifest where applicable, including complete safe-stop/recovery closure,
  optional-media boundary, active-work pinning and package integrity/size class.

An SBOM is an inventory, not proof that components are safe, reviewed, licensed correctly or actually used. Provenance is
evidence about production; it is not proof that source or builder was benevolent.

### 7.4.1 Cross-domain release-meaning graph

Before positive promotion, one closed compatibility graph binds the applicable:

- mobile/web/backend artifact and capability envelope;
- API/contract and supported client window;
- content manifest, derived/localized/rendered assets and provenance/classification;
- effective configuration values, defaults, audience/scope, templates/transforms and expiry;
- schema and data-migration version/state;
- external model/resource identities where they can alter meaning;
- offline task package plus complete reachable-state safe recovery;
- release and suspension/revocation generations.

The graph is verified at promotion and again at authoritative runtime consumption where values are selected dynamically.
An old/dormant client that cannot represent a safety-critical semantic gets no positive application authority; only its
supported teaching/history/task-safe-recovery paths remain. Content/configuration activation is held until its required
capability window and dependency closure are satisfied. Unknown/mixed classification receives most-restrictive handling.

### 7.5 Signing, key and account custody

- separate identities/keys for app binary, internal web/backend deployment, content integrity, emergency suspension and
  other release domains; development/test keys cannot authorize production;
- least-privilege, non-exportable or equivalently protected keys according to a named release-tier rule; any exception
  has owner, reason, expiry, compensating control and protected audit;
- signing requests bind exact artifact digest, release domain, environment, provenance and authorization;
- routine CI cannot silently retrieve root/recovery key material;
- key creation, access, use, rotation, revocation, recovery and destruction are dual-controlled/protected-audit events;
- emergency/recovery keys are narrow, offline or independently protected as appropriate and regularly exercised;
- store/platform account recovery and ownership are organizational, not tied to one personal account;
- compromise playbooks identify affected artifacts, stop promotion, revoke/rotate, suspend affected capability and rebuild
  trust from known inputs; key rotation alone does not make previously malicious artifacts safe.

Authenticity, approval/provenance and current eligibility are evaluated separately. Key/store compromise creates an
artifact impact set and a new monotonic revocation/suspension state; it does not magically retract installed, cached,
dormant or offline artifacts. Online containment, store/platform action, organization-owned account recovery, client
reconciliation and explicit offline residual risk are all recorded. A future OTA trust root would require threshold/root
rotation, expiry, rollback/freeze/mix-and-match defenses before that channel could be approved.

### 7.6 Environment and promotion control

- development/test/staging/production have separate identities, secrets and mutation authority;
- production data/secrets do not silently flow to lower environments;
- promotion advances the exact immutable verified artifact; environment configuration is separately versioned and bound;
- production authorization rechecks provenance, signature, compatibility, revocation and policy at promotion time;
- artifact retrieval and deploy boundaries re-verify the exact digest; filename, tag, `latest` pointer or registry location
  is never identity by itself;
- verification produces a promotion/deployment attestation bound to artifact, verifier, policy version, approval,
  environment configuration, migration version and rollout state;
- staged/canary rollout has declared population, observation, pause/stop, escalation and completion criteria;
- deployment result is authoritative, partial, failed or outcome-unknown; retries reconcile the same operation identity;
- direct/manual production mutation is denied or enters an explicit emergency path with protected evidence and reconciliation;
- registry/deployment retention preserves known-good and incident artifacts according to later policy.

Rollout has durable authoritative states:

`PREPARED → CANARY → PAUSED/STOPPED/PARTIAL → COMPLETED → SUPERSEDED/RECALLED`

with `FAILED` and `OUTCOME_UNKNOWN` branches. Cohort identity, metric/evidence integrity, observation owner, escalation,
completion and stop criteria are bound to the rollout operation. Stopping prevents further promotion; it never claims to
downgrade already updated clients.

## 8. Release-type-specific policy

### 8.1 Consumer mobile binary

- official platform signing/distribution is one layer, not the complete Kavriva approval/provenance chain;
- store upload/release accounts are scoped and separated from development identity where platform permits;
- staged rollout cannot assume all devices update or that stopping rollout downgrades updated devices;
- backend/content compatibility supports old and dormant clients according to DEBATE-002;
- minimum supported capability and forced-hold behavior are declared before rollout;
- compromised or unsafe binary response includes server-side containment, store action, key/account recovery and user reach-back;
- store policy and OS distribution constraints are evidence inputs, not guarantees of immediate recall.

### 8.2 Browser Internal Operations

- centralized deployment reduces client-version drift but increases blast radius of a bad deployment;
- operator frontend artifact and backend authorization policy remain distinct release authorities;
- browser cache/service-worker state cannot authorize mutation or preserve a revoked privilege;
- private/mutation responses and release status follow DEBATE-003/004 network-authoritative cache rules;
- rollout, rollback and browser compatibility are observed rather than assumed.
- private/mutation/status responses are network-authoritative and non-cacheable; no offline mutation queue or service-worker authority;
- stale/mixed frontend assets or incompatible code become read-only until current server version/policy is reconciled;
- cache poisoning and old/new asset mixtures are release incidents, not local success states.

### 8.3 Backend/API/service and database migration

- contracts declare compatible version windows and unknown safety semantics fail closed;
- schema/data migration is reviewed, tested and promoted as a release artifact with exact input/output expectations;
- prefer backward/forward compatible sequencing where possible; destructive/irreversible change requires explicit higher assurance;
- backup existence is not rollback proof; restoration, reprocessing and audit/revocation reconciliation are tested;
- application deploy and migration ordering is explicit; partial/mixed version states have defined behavior;
- rollback never silently discards new valid data or reactivates revoked content/authority.

Migration uses explicit `PLANNED → STARTED → PARTIAL/FAILED → RECONCILING → RECONCILED` states with owner, checkpoint,
affected region/data scope and next action. Binary rollback and data/schema recovery are different decisions. Migration
design declares old/new reader-writer compatibility, concurrent-write behavior, idempotence/retry boundaries, partial-region
operation, data-loss risk and compensating/forward correction. If new valid data or revocation/history truth cannot be
preserved, the affected capability remains held rather than automatically restoring an older artifact/backup.

### 8.4 Technical content

Content authoring/approval/publication remains under DEBATE-003 and IDCO. Software release tooling may package or
transport an exact approved manifest but cannot create approval, reinterpret provenance or bypass emergency suspension.

### 8.5 Configuration, feature flags and transforms

- typed/schema-validated, versioned, reviewed and attributable;
- classified by maximum possible consequence, not by “no code” label;
- scope, default, expiry/owner and fail-safe state are explicit;
- high-consequence changes require controlled approval and staged observation;
- a flag/config cannot introduce semantics unsupported by the current client capability envelope;
- emergency kill/hold action remains negative and independently ordered; normal configuration cannot clear it;
- stale, unknown or invalid critical configuration fails closed without erasing safe recovery/history.

The exact effective value, default, audience/scope, expiry, template/transform/resource input and configuration digest are
part of the closed release-meaning graph. Any change that can alter technical/safety meaning requires the corresponding
content/software review and a new controlled activation. Configuration is non-scriptable within its declared envelope;
runtime selection rechecks capability compatibility and the current suspension/revocation generation.

### 8.6 Future OTA/runtime update channel

No OTA mechanism is approved. If later considered, it is a separate release authority with an explicit allowed envelope,
signed/versioned artifacts, provenance, compatibility, anti-rollback, staged rollout, revocation and platform-policy review.
It may not silently replace native/security-critical code, widen permissions, bypass store review expectations or merge
technical-content approval into software publication.

## 9. Incident and revocation policy

Release incident response distinguishes:

- vulnerable but uncompromised dependency;
- confirmed malicious dependency/artifact;
- source/reviewer account compromise;
- builder/CI/action compromise;
- registry/deployment account compromise;
- signing/store/recovery key compromise;
- configuration/flag abuse;
- database migration/data corruption;
- provenance/SBOM/audit inconsistency.

Response can hold promotion, freeze affected credentials, quarantine artifacts, identify every affected build/deployment,
activate independent negative controls, revoke or supersede trust, rebuild from known inputs, issue compatible correction,
perform reach-back and preserve incident evidence. “Roll back” is not universal: if no still-safe compatible artifact
exists, the affected function remains held or safely degraded.

Every incident builds an auditable impact graph from compromised source/dependency/workflow/builder/key to affected
artifacts, evidence packages, environments, regions, client cohorts, offline packages, active work, content/configuration
states and current rollout. A protected copy exists outside the potentially compromised CI/registry/deployment plane.
Key rotation, rebuild or rollback does not close the incident until this graph is reconciled and affected artifacts are
re-verified or explicitly revoked/suspended.

All binary, web, backend, migration, configuration, content and restore promotions bind the current protected
suspension/revocation generation. Older/in-flight operations are rejected. A security-patch/containment release while a
suspension is active may reduce harm but cannot clear the suspension; re-entry requires the normal explicit reviewed event.

## 10. No-code acceptance scenarios

Every candidate architecture must state expected allow/deny/hold, side effects, authoritative evidence and recovery for:

1. A dependency tag is moved after review.
2. A transitive package is removed or its maintainer account is compromised.
3. A CI action/plugin referenced by a mutable tag becomes malicious.
4. An untrusted pull request attempts to read signing/deployment secrets.
5. A compromised runner substitutes an artifact after tests.
6. Provenance and SBOM are valid but bind a different artifact digest.
7. Production rebuild differs from the staging artifact.
8. A developer or CI identity tries to sign and publish without independent promotion authority.
9. Signing succeeds after the key or store account is marked compromised.
10. A staged mobile rollout is stopped after some users updated.
11. A web deployment is rolled back while browsers retain old/new cached assets.
12. A backend rolls forward while an old mobile client cannot parse a new safety field.
13. A database migration succeeds in one region and fails in another.
14. Rollback would discard valid data created after deployment.
15. A feature flag changes safety behavior without a binary release.
16. Normal configuration attempts to clear an emergency suspension.
17. A future OTA update changes code outside its authorized envelope.
18. A store/release owner leaves the company or loses account recovery access.
19. Restore brings back an old deployment key, configuration or revocation state.
20. Audit/provenance/registry evidence is unavailable during emergency correction.
21. A generated visual/resource differs from the approved input but retains the same filename.
22. The last known-good artifact is signed but contains the now-compromised dependency.
23. Repository administrator weakens branch/workflow policy and then releases a provenance-valid artifact.
24. Builder image, cache, compiler or base image is compromised while the attestation remains syntactically valid.
25. Registry/mirror serves inconsistent metadata while the filename/tag is unchanged.
26. Release graph combines a valid binary with stale configuration, a partial migration and an incompatible offline package.
27. Private/community metadata appears in SBOM/provenance or a public release evidence export.
28. Required independent promoter/key custodian is unavailable in a small team.

Every scenario must define authoritative allow/deny/hold and state transition, exact evidence generated, operator/user
explanation, impact on already deployed/installed/offline clients, recovery/reconciliation owner and path, and residual risk.
A valid signature, green build or stopped rollout is not an acceptance result by itself.

## 11. Measurements and evidence required before ADR

No numeric value is invented here. Later accountable owners must define:

- release consequence tiers and required independent roles;
- provenance/SBOM/attestation completeness and verification gates per artifact type;
- dependency/vulnerability response and exception-expiry objectives;
- build isolation, network and secret-access requirements;
- key/signing/store recovery, rotation and revocation objectives;
- staged rollout populations, observation windows, pause/abort/completion signals;
- compatibility/support windows for mobile, web, backend, database and content contracts;
- migration recovery/rollback/data-loss acceptance criteria;
- artifact/evidence/audit retention and restore objectives;
- release incident detection, containment, notification and recovery objectives.

## 12. Open decisions

1. Exact release consequence taxonomy and role/quorum matrix.
2. Which artifact types require reproducible independent rebuild comparison.
3. Accepted provenance/attestation and SBOM representations.
4. Dependency source, exception, license, vulnerability and end-of-life policies.
5. Build runner/network isolation and trusted-builder boundary.
6. Exact key hierarchy, custody, platform/store ownership and emergency recovery ceremony.
7. Environment/account/project separation and production-support access.
8. Mobile store rollout, old-client support and mandatory-update/hold rules.
9. Web/backend deployment units, canary model and cache/service-worker policy.
10. Database migration compatibility and destructive-change approval policy.
11. Feature-flag/configuration authority, expiry and maximum safety envelope.
12. Whether any future OTA channel is allowed and its strict mutable envelope.
13. Artifact/provenance/SBOM/audit retention, privacy and incident-disclosure policy.
14. Physical tools/providers for source, build, registry, signing, store, deployment and monitoring.

## 13. Manager working direction

Proceed provisionally with Option C:

- separate release authorities for binary, web, backend/data, content, configuration and emergency control;
- exact immutable reviewed inputs and dependency resolution;
- isolated controlled builds with artifact-bound provenance, SBOM and verification evidence;
- promote the same immutable artifact rather than rebuild production;
- scoped signing/deployment identities and separated key/account custody;
- consequence-proportionate approval and no single silent high-consequence path;
- configuration/migrations/transforms governed as releases;
- staged rollout with explicit partial/old-client semantics;
- rollback only to a still-trusted compatible artifact, otherwise hold/safe degradation;
- provider-neutral incident, revocation and restore reconciliation.

The user approved this reviewed working direction under `DEC-0027`. It is not an ADR and does not pass Gate 4 → 5.
Exact assurance tiers, governance details, OTA policy and implementation technology remain open.

## 14. Research basis

The following primary/official sources establish properties and limitations, not product selections:

- [SLSA v1.2 Build Track](https://slsa.dev/spec/v1.2/build-track-basics),
  [Build Provenance](https://slsa.dev/spec/v1.2/build-provenance) and
  [Verification Summary](https://slsa.dev/spec/v1.2/verification_summary): signed provenance, hosted builders,
  isolation and consumer verification; even high SLSA properties do not prove safe/correct source.
- [in-toto Attestation Framework](https://github.com/in-toto/attestation/blob/main/spec/README.md): subject digest,
  predicate and signature are distinct; policy must define accepted subjects/signers/predicates.
- [The Update Framework metadata roles](https://theupdateframework.io/docs/metadata/) and
  [TUF specification](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md): threshold roles,
  version/digest/expiry and rollback/freeze/mix-and-match resistance; denial of update remains possible.
- [NIST SP 800-218 SSDF](https://csrc.nist.gov/pubs/sp/800/218/final): protected source/configuration,
  release-integrity information, protected release archives/provenance, third-party component verification and
  vulnerability-response practice.
- [NIST SP 800-161 Rev. 1](https://csrc.nist.gov/pubs/sp/800/161/r1/upd1/final) and
  [NIST SP 800-204D](https://csrc.nist.gov/pubs/sp/800/204/d/final): supply-chain risk management and CI/CD
  provenance/attestation/SBOM/repository controls.
- [NTIA SBOM Minimum Elements](https://www.ntia.doc.gov/files/ntia/publications/sbom_minimum_elements_report.pdf) and
  [CISA SBOM Framing 2024](https://www.cisa.gov/sites/default/files/2024-10/SBOM%20Framing%20Software%20Component%20Transparency%202024.pdf):
  component/dependency inventory and minimum identity/relationship fields; an SBOM does not prove safety.
- [NIST Code Signing guidance](https://csrc.nist.gov/pubs/cswp/5/security-considerations-for-code-signing/final) and
  [NIST SP 800-57 Part 1](https://csrc.nist.gov/pubs/sp/800/57/pt1/r5/final): signing integrity/source authentication
  plus complete key generation/storage/use/compromise/revocation/recovery/destruction lifecycle.
- [Sigstore signing overview](https://docs.sigstore.dev/cosign/signing/overview/): short-lived identity certificates and
  transparency logging can make signing events inspectable; they do not prove artifact safety.
- [Reproducible Builds definition](https://reproducible-builds.org/docs/definition/) and
  [SLSA verified properties](https://slsa.dev/spec/v1.2/verified-properties): bit-for-bit reproduction can detect build
  differences but does not validate source intent.
- [CISA Safe Software Deployment](https://www.cisa.gov/sites/default/files/2024-10/safe-software-deployment-how-software-manufacturers-can-ensure-reliability-for-customers-508c.pdf):
  canary/controlled rollout, observation and breaker/stop practice; stopping rollout does not revert updated clients.
- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final): integrated preparation, detection, response,
  recovery and lessons learned.

Research limitations preserved:

- provenance can be forged at lower assurance and never proves benevolent/correct source;
- dependency completeness can remain best-effort even under a provenance standard, so Kavriva requires its own completeness policy;
- valid signatures, SBOMs, transparency entries and reproducible builds do not prove vulnerability-free or approved meaning;
- staged rollout success does not prove universal client delivery;
- backup existence does not prove safe migration rollback or preservation of revocation/audit truth.
