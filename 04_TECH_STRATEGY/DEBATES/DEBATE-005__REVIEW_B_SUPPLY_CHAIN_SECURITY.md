# DEBATE-005 — Review B: Supply-Chain, Build, Signing and Deployment Security

Date: 2026-09-17
Reviewer: Independent Luna Max adversarial reviewer
Mode: Read-only, no code
Verdict: `PASS_WITH_CHANGES AS DIRECTION — REJECT AS ADR/GATE BASIS`

## Sound direction

The review accepted exact digest binding, no production rebuild, separate software/content/config/emergency authority,
release-governed configuration/migrations, still-trusted rollback, honest staged-rollout limits and explicit non-approval
of any OTA channel.

## Critical findings and incorporated corrections

### Valid provenance can come from a malicious builder/policy

Incorporated: a trust-root/independence matrix covers repository rules, workflow/actions, builder control plane, runner
image/cache, toolchain/base image, registry, verifier, signer, promoter and target. The independent verifier checks digest,
builder/signer, policy and attestation chain; unknown bootstrap/input state holds release. Independent rebuild or a named
hardened-builder equivalent is tier-required, not vague best effort.

### Key rotation cannot revoke installed/offline trust

Incorporated: authenticity, approval/provenance and current eligibility are separate. Compromise produces an impact set
and monotonic revocation/suspension state plus online containment, store action, account recovery, client reconciliation
and explicit offline residual risk. Future OTA remains unapproved without threshold/root/expiry/rollback/freeze controls.

### Runtime config/migration/mixed rollout can alter meaning outside the artifact

Incorporated: closed cross-domain release graph is verified at promotion/runtime; configuration is bounded/non-scriptable;
migration has explicit partial/recovery states; emergency negative authority precedes normal configuration and restore.

## Major findings and incorporated corrections

- Dependency closure uses `KNOWN_COMPLETE`, `BEST_EFFORT` and `UNKNOWN`; high-consequence unknown holds. Closure explicitly
  considers runtime/build/toolchain/base-image/generated/dynamic/cache dependencies.
- Reviewed commit, workflow digest, review-policy version and merge identity bind to the candidate; administrative policy
  weakening is a tested high-consequence path.
- Artifact/evidence archives are independently protected from CI/registry compromise; digest verifies every handoff.
- Signer/verifier/promoter human and service-account independence is mandatory by consequence tier.
- Rollout has prepared/canary/paused/stopped/partial/completed/superseded/recalled/failed/unknown states with cohort/evidence ownership.
- Browser private/mutation/status responses are network-authoritative; stale/mixed assets become read-only.
- Incident response creates an external protected impact graph across artifacts, deployments, cohorts, offline packages and config.
- Every dependency has owner/source/support/security contact/license/EOL/replacement/containment policy appropriate to consequence.
- Acceptance scenarios now require expected authority result, evidence, deployed-client impact, recovery and residual risk.

## Evidence note

SLSA, in-toto, TUF, NIST SSDF/SP 800-161/SP 800-204D, NTIA/CISA SBOM guidance, NIST signing/key guidance and CISA safe
deployment guidance establish useful properties and limits. They do not select a CI, registry, signer, store or cloud and
do not prove code safety merely because provenance, SBOM, signature or transparency evidence exists.

## Conclusion

The corrected proposal is a strong Phase-4 governance direction. Observable acceptance properties, accountable owners,
numeric thresholds and implementation evidence remain necessary before ADR/Gate 4 → 5.
