# ADR-004 — Identity, Authorization, Session, Recovery and Privileged Activation

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy answered who may see or do each internal action and how untrusted material enters safely
(DEBATE-004, user-approved under `DEC-0026`), and which physical identity composition carries those properties
(DEBATE-010, user-approved under `DEC-0037`): consumer Supabase Auth with local-first account-light as the working
direction, while privileged Internal Operations has no provider winner and stays held behind a full activation
evidence gate. This ADR locks the governance model, the identity contract and the activation gate. It selects no
identity provider plan, factor product, session product, SMTP/SMS service, scanner product or SIEM, and authorizes no
account, purchase, code or production activation.

## Decision Drivers

- Authentication proves a session claim; it never proves competence and never alone authorizes action.
- Small-team reality: unavailable independent competence must yield visible `HELD`, never weakened self-approval.
- Privileged paths (approval, publication, emergency, access administration, audit/export, quarantine release) are the
  highest-value attack targets and need phishing-resistant, transaction-bound, fully revocable controls.
- Untrusted files/URLs and AI/OCR output must be usable as evidence sources without ever becoming authority.
- Solo-owner operation: recovery that depends on owner debugging, plus a second human/organization dependency for
  last-admin recovery, must be explicit rather than assumed.

## Options Considered

### Authorization model

- **Option A — Shared administrator access (rejected):** everyone trusted can do most things. No least privilege, no
  separation of duties, unmanageable compromise radius.
- **Option B — Static role-based access only (useful baseline, insufficient alone):** understandable and auditable,
  but ignores motorcycle/domain scope, risk, workflow state, assignment, private-content boundaries and independence,
  causing role explosion or over-broad access.
- **Option C — Attribute/policy rules only (not recommended as the human governance model alone):** expressive but
  hard to explain, test and administer; hidden interactions risk accidental access.
- **Option D — Hybrid capability model (chosen):** understandable base roles grant candidate capabilities;
  server-side policy narrows them per request by resource/domain scope, workflow state, consequence tier, assignment,
  independence, session assurance and temporary conditions. Cost: policy versioning, simulation, change review and
  denied-access diagnostics are mandatory.

### Identity composition

- **Consumer: Supabase Auth as the working direction (locked as direction, not as purchase):** fits the approved
  Supabase-centered backend and Flutter path with the fewest initial control planes. Account-light first value starts
  from a Kavriva local installation/device principal; no server anonymous account is created merely to simulate it.
  Migration to a profile is a distinct, previewed, conflict-holding product operation — provider linking never
  silently merges history or ownership.
- **Privileged Internal Operations: no provider winner (locked as a held gate, not a selection):** single-Supabase
  composition stays held on phishing-resistant transaction-bound evidence and common-failure-domain proof; a separate
  internal-only IdP stays held on two-issuer/recovery/cost evidence. Forcing a winner now would violate the
  no-premature-selection principle confirmed by the Gate 4 -> 5 audit.

## Decision

Kavriva adopts the hybrid capability model (Option D) with the following locked rules:

1. **Server-authoritative decision tuple:** every sensitive read, export or mutation is decided server-side on current
   actor, session assurance and security epoch, action, exact resource/tenant/scope, classification, grant/delegation
   chain, competence/independence, policy version, resource version/generation and operation identity — returning
   allow/deny/hold with a stable operator-explainable reason. Browser state, hidden buttons, cached roles, provider
   claims and client-supplied IDs are never authority. Deny is the default; commit-time re-authorization is
   mandatory, and material context changes hold pending work for re-evaluation instead of retro-authorizing it.
2. **Separation of duties:** for high-consequence official content, propose/edit, domain review, safety approval and
   publication are pairwise incompatible per change packet. Emergency suspension stays negative-only. Small-team gaps
   produce attributed `HELD`, fillable only by pre-authorized temporary/external reviewers with documented competence,
   scope, independence and expiry.
3. **Authentication and sessions:** privileged operators require phishing-resistant authentication; high-consequence
   actions require fresh transaction-bound step-up; recovery/help-desk reset must not be weaker than normal privileged
   authentication; sessions carry explicit inactivity/absolute bounds, rotation and server-side revocation; stale or
   offline Internal Operations pages are read-only and non-authoritative. TOTP, SMS and magic links are not
   phishing-resistant substitutes.
4. **Security-epoch revocation:** compromise/recovery increments the epoch and revokes sessions, grants/policy/
   competence generations, pending/in-flight operations, retries, private object handles, browser caches and local
   package/key state end to end. Downloaded copies cannot be remotely retracted — represented honestly, with
   short-lived scoped handles and server mediation for private objects.
5. **Recovery separated from negative authority:** privileged account recovery revokes and re-authenticates but can
   never approve, publish or grant roles; emergency negative authority can only suspend/recall/quarantine/deny.
   Help-desk/last-admin recovery uses dual control or a separately governed time-limited break-glass path.
6. **Protected audit before effect:** high-consequence positive effects require durably recorded protected evidence
   (actor, authority, operation identity, object/version, policy/grant version, ordered server time/sequence,
   transition, result linkage) through normal or sufficiently independent fallback custody; otherwise the action stays
   `AUDIT_HELD`. Audit storage is append-only or equivalently tamper-evident, separately protected and recoverable;
   publishers and admins cannot erase evidence of their own actions. Provider logs never substitute product audit.
7. **Quarantine-first ingestion:** files and URL-fetched material travel
   `RECEIVED_UNTRUSTED → QUARANTINED → IDENTIFIED → VALIDATED → SCANNED → RENDERED_UNTRUSTED_PREVIEW →
   HUMAN_CLASSIFIED → SAFE_FOR_HUMAN_REVIEW`, with explicit reject/scan-unknown/parse-failed/malicious/expired
   branches. Scan, preview and review-readiness are processing states only — never technical correctness, sufficiency
   or approval. Previews render isolated without credentials or privileged APIs; originals never serve from the
   operations origin. URL retrieval uses credential-free, redirect-validated, DNS-rebinding-defended fetching with
   frozen reviewed artifacts.
8. **Export as disclosure:** export is a separately authorized capability with scope/purpose/classification preview,
   data minimization, generation identity and residual-copy warning; revoking a link stops future access only — the
   event is recorded as non-retractable disclosure.
9. **AI/OCR as proposal only:** extraction/classification output stays linked to input and transformation provenance,
   never becomes source truth or approval, and hostile document instructions have no policy/tool/workflow authority.
10. **Privileged activation gate (all must pass before high-consequence privileged production opens):** stable
    principal + provider adapter + current authorization tuple; passkey/step-up/factor-loss/stolen-token/logout-all
    fixtures; revoke/stale-tab/direct-API/cross-tenant/in-flight negative tests; recovery-vs-negative tabletop;
    audit/fallback/floor plus restore reconciliation; end-to-end object/package/queue revoke; last-admin and
    provider/outage runbooks; Android-first device fixtures (iOS parity separate); normalized safe-minimum bill of
    materials with owner cost stop; clean-room exit with factor re-enrollment; independent security and owner/TCO
    reviews. Any unknown critical line holds; any mandatory negative/recovery/audit/no-owner-debug violation rejects
    the capability until mitigated. Until the solo-owner project fields a real independent second human/organization
    for recovery custody, privileged production stays `HELD`.

## Rationale

Static roles alone cannot express scope, consequence and independence; pure policy rules alone cannot be governed by a
small team — the hybrid keeps human clarity with server-enforced precision. Consumer identity takes the simplest
fitting direction while privileged production, where a wrong choice is hardest to reverse, is locked behind evidence
instead of a premature winner. Ingestion and export rules close the two largest side doors (malicious content in,
private data out) without blocking legitimate evidence work.

## Consequences

### Positive

- Every sensitive action is explainable (who, under which grant/policy/epoch, with what evidence) and replayable for
  investigators through an object-centered chain.
- Compromise response is a defined epoch transition, not improvisation.
- Ingestion, preview, export and AI assistance stay useful without ever becoming trust roots.
- Privileged production cannot open on marketing labels (`GA`, `passkey`, `aal2`) alone.

### Negative / Trade-offs

- Policy versioning, simulation, denied-access diagnostics and periodic recertification are permanent operating work.
- Strict step-up, short sessions and held-on-unknown behavior add operator friction by design.
- The held privileged gate delays high-consequence internal production until evidence (and a second recovery
  human/organization) exists — a real schedule cost accepted deliberately.
- Two-issuer deployment, if ever chosen, doubles recovery/support/cost surfaces.

## Prohibited / Constrained Alternatives

- Shared administrator access; self-approval or self-publication of high-consequence work.
- Cached claims, `user_metadata`, browser state, provider roles or RLS as sole authority.
- TOTP/SMS/magic-link as phishing-resistant privileged factors.
- Provider identity linking that silently merges product history, ownership or entitlements.
- Scan/parser/sandbox result presented as safety, correctness or approval proof.
- Export or audit-search treated as ordinary read access; silent overwrite of attribution by revocation or migration.
- AI identities holding provider-owner, billing-root, `service_role`, unrestricted SQL/SSH, recovery, approval or
  publication authority.
- Any IdP account, plan, SMTP/SMS service, second recovery actor, purchase, code or production activation — none
  authorized by this ADR.

## Revisit Triggers

- Evidence shows the hybrid model cannot be administered within bounded AI workflows (policy complexity escapes
  simulation/review), or a held privileged candidate passes the full activation gate — resolved by superseding ADR.
- Numeric session/step-up/delegation/retention policy, exact role matrix, permitted file/source classes,
  encrypted-document handling, URL connector classes, legal/privacy/retention destinations and provider/cost BOM
  remain HELD for later design/procurement evidence, not blockers of this ADR.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0026`, `DEC-0037` (binding working directions)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__REVIEW_A_GOVERNANCE_PRIVACY_OPERATIONS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__REVIEW_B_IDENTITY_APPSEC_INGESTION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__IDENTITY_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__IDENTITY_PROVIDER_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__IDENTITY_FAILURE_THREAT_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__REVIEW_A_SECURITY_RECOVERY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__REVIEW_B_OWNER_TCO_OPERABILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__JUDGE_SYNTHESIS.md`
- Downstream: ADR-005 (audit custody detail), ADR-006 (API commit-time authorization), ADR-010 (web
  session/security), ADR-014 (AI identity scoping)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
