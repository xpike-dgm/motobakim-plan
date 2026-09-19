# DEBATE-004 — Review B: Identity, Application Security, Audit and Ingestion

Date: 2026-09-17
Reviewer: Independent Luna Max adversarial reviewer
Mode: Read-only, no code
Verdict: `PASS_WITH_CHANGES AS DIRECTION — REJECT AS ADR/GATE BASIS`

## Sound direction

The reviewer accepted server-side per-request authorization, deny-by-default, per-object separation of duties,
non-destructive revocation, explicit quarantine/unknown states, layered ingestion, isolated-preview intent, URL provenance,
separate export authority and AI/OCR proposal-only boundaries.

## Critical findings and corrections

### Recovery did not guarantee active-session invalidation

Incorporated: privileged recovery increments a security epoch, revokes all relying-party sessions/refresh/recovery
artifacts and pending high-consequence transaction authorizations, requires fresh phishing-resistant authentication plus
transaction-bound step-up, independently notifies security/owner and fails closed when revocation truth is unavailable.

### Policy administration remained a self-grant/confused-deputy path

Incorporated: authorization policy is a protected versioned artifact with distinct author/approver/activator capabilities,
impact simulation, explicit effective time, no retroactive authority, pending-work recheck and controlled rollback. IdP,
group, database, storage, deployment, key, backup, policy-engine, service-account and nested-group paths enter accumulation tests.

### Audit guarantee was not testable during compromise/outage

Incorporated: minimum protected evidence precedes high-consequence effect; independent custody, ordered sequence,
integrity checkpoints, gap/fork/replay detection, restore reconciliation and bounded protected fallback are normative.
When neither normal nor fallback evidence is durable, normal high-consequence action is held; emergency behavior follows
the explicitly governed DEBATE-003 exception and remains unknown/quarantined until reconciliation.

## Major findings and corrections

- Originals are never served from the operations origin; preview has no ambient cookies, privileged APIs, arbitrary
  network, active content, attachment/native-viewer handoff, implicit download, print or unrestricted navigation.
- URL retrieval rejects credentials/userinfo, unapproved schemes/ports, parser disagreement, mapped/ambiguous addresses
  and downgrade; actual connection and every redirect are revalidated under deny-by-default egress.
- Competence is an issued, scoped, expiring/revocable controlled record; conflicts include delegations, aliases/groups,
  service identities and policy-defined organizational relationships.
- Commit binds policy/grant/security epoch, resource state, competence/independence and authority generations.
- Human and workload identities are separate; service accounts receive explicit minimal non-interactive capabilities.
- Browser private/mutation authority is online/server-side; downloads/screenshots remain an explicit residual disclosure risk.
- Export cannot retract copied data and is recorded as disclosure.
- AI/extraction records exact input/output and model/config provenance; hostile document instructions cannot invoke tools,
  network, policy or workflow authority.
- Acceptance scenarios now require expected allow/deny/hold, state, side effects, audit evidence and recovery path.

## Evidence note

NIST SP 800-63B-4, NIST SP 800-162, NIST SP 800-53, CISA phishing-resistant MFA guidance and OWASP authorization,
session, logging, file-handling, CSP/HTML5 and SSRF guidance support the required properties. They do not select an
identity provider, scanner, policy engine, log product or cloud.

## Conclusion

After correction, the document is a strong reviewed Phase-4 direction. Numeric controls, detailed governance and
architecture acceptance evidence remain mandatory before ADR/Gate 4 → 5.
