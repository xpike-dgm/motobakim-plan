# DEBATE-004 — Review A: Governance, Privacy, Operations and User Trust

Date: 2026-09-17
Reviewer: Independent Luna Max adversarial reviewer
Mode: Read-only, no code
Verdict: `PASS_WITH_CHANGES — NOT ADR-READY`

## Sound direction

- hybrid understandable roles plus server-authoritative scoped/contextual policy;
- deny-by-default and commit-time reauthorization;
- per-change separation of duties and immutable historical attribution;
- narrow negative emergency authority;
- quarantine-first ingestion and separate export authority;
- AI/OCR as attributable proposal only;
- private/community/official boundaries.

## Findings and corrections

### Small-team separation needs a safe fallback

If independent competence is unavailable, operators may otherwise share accounts or abuse administration/emergency paths.

Incorporated: high-consequence work remains `HELD` with owner/reason/escalation; only pre-authorized temporary/external
reviewers with scoped competence and independence may fill the gap. Emergency authority stays negative-only.

### Delegation could bypass separation

Incorporated: self/nested/transitive delegation is denied by default; delegation cannot copy competence, bridge
classification or combine incompatible capabilities. Every use retains the grant/delegation chain and expiry; commit
rechecks policy, authority generations and security epoch.

### Unknown/mixed classification could leak through derivatives

Incorporated: unknown/mixed classification uses the most restrictive handling and propagates to preview, extraction,
audit references and exports. Private/community material entering official review requires an explicit reviewed
classification/disclosure decision; moderation never creates verification.

### `EVIDENCE_ELIGIBLE` sounded like verification

Incorporated: the state is renamed `SAFE_FOR_HUMAN_REVIEW`; scanning/rendering remain cybersecurity/processing results,
separate from technical correctness, applicability, sufficiency, verification and approval.

### Quarantine ownership and appeal were incomplete

Incorporated: every item has owner/queue, reason, permitted viewers, next action, escalation and retention state. Originals
and sanitized derivatives remain distinct; inconclusive results block; false-positive challenge is a new attributable review.

### Privileged bootstrap/recovery could create a complete authority chain

Incorporated: dual-controlled or separately governed time-limited recovery, security-epoch invalidation, independent
notification and post-event review. Recovery cannot approve/publish content; unavailable safe recovery holds positive action.

### Export revocation could imply impossible retraction

Incorporated: export is a disclosure event with field/scope preview, recipient/purpose and generation manifest. Revoking a
link stops future access but cannot retract downloaded, printed, copied, forwarded or captured data.

### Audit needed investigator-readable continuity

Incorporated: object-centered current-state-to-authority-to-artifact-to-result chain, protected references for sensitive
detail and audited audit retrieval/redaction/retention/export.

## Remaining open policy

Low-risk role combinations, competence issuer/recertification, numeric session/delegation periods, exact recovery quorum,
retention/legal/export rules, file/source limits, encrypted documents, quarantine-original access, URL source classes,
audit custody and AI/provider boundaries remain deliberate later decisions.

## Conclusion

The corrected direction is suitable for a user working-direction decision, not an ADR or Gate 4 → 5 basis.
