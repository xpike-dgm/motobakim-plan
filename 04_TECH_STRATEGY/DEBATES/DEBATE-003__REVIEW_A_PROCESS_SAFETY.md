# DEBATE-003 — Review A: Process Safety, Content Operations and User Trust

Date: 2026-09-17
Reviewer: Independent Luna Max adversarial reviewer
Mode: Read-only, no code
Verdict: `PASS_WITH_CHANGES — NOT ADR-READY`

## Scope

The reviewer tested the B+C direction against the approved Internal Data & Content Operations requirements/lifecycle,
DEBATE-002, active-work safety, human escalation and browser-operation honesty.

## Sound direction

- immutable exact approval snapshots and closed dependency manifests;
- preflight plus commit-time revalidation;
- explicit failed, partial and outcome-unknown states;
- emergency negative authority that cannot author replacement truth;
- rollback as a new event, restore quarantine and preserved history;
- browser cache/optimistic UI never treated as authority;
- explicit limit for genuinely offline consumers;
- no-code and vendor-neutral boundary.

## Findings and required corrections

### Critical — Publication can race emergency suspension

The draft stated that suspension overrides positive authority but did not fence the two authorities at commit/read time.
A publication could preflight, then a suspension could commit, then the older publication could become current.

Correction incorporated:

- publication commit binds the exact current suspension/revocation generation;
- clients evaluate a consistent release + suspension tuple;
- mismatch/unknown holds affected critical use;
- an explicit publish-versus-suspension race scenario was added.

### Critical — Emergency-path unknown outcome lacked a complete product rule

An unavailable or timed-out emergency operation cannot be assumed to have failed or succeeded.

Correction incorporated:

- durable emergency operation identity and authoritative status lookup;
- no blind retry or success claim;
- high-consequence positive eligibility holds while negative authority is unknown;
- out-of-band reach-back and owned escalation remain required policy work.

### Major — Scope overlap and dependency closure were underspecified

Claim, guide, variant and release scopes can overlap. A broad stop must not be silently canceled by a narrower release,
while an unrelated variant should not be blocked without cause.

Correction incorporated: emergency scope is dependency-aware; the most restrictive applicable negative authority wins;
narrower re-entry requires an explicit reviewed event. The canonical scope lattice remains an open ADR prerequisite.

### Major — Infrastructure failure was at risk of looking like a recall

`Publisher unavailable`, `known current`, `suspension unknown` and `known suspended` are different truths.

Correction incorporated: separate operator/consumer states with distinct reason, owner, next action and effects. An
outage is not labeled as a recall.

### Major — Audit fallback required minimum evidence

Emergency action during an audit-sink outage is acceptable only if protected attributable evidence still exists.

Correction incorporated: independently recoverable tamper-detectable emergency evidence buffer, minimum required event
fields and quarantine/reconciliation. The exceptional case where both audit paths fail remains a user/policy decision.

### Major — Unknown operations need ownership and aging

Correction incorporated as a required pre-ADR measurement/control: one resolver, guarded transitions, escalation owner,
age threshold and impact summary for every unknown/partial normal or emergency operation.

### Major — Suspension and recall were combined

Correction incorporated: `SUSPENDED` is the immediate negative authority; `RECALL_OPEN` is the impact/reach-back,
correction and re-entry case.

## Preserved user boundary

Internal Operations remains browser-based. Independence refers to backend/authority/failure domains and does not silently
introduce a desktop wrapper or a second operator client. Any alternate client/channel would require a new user decision.

## Reviewer conclusion

The corrected B+C direction is suitable for a user working-direction decision. It is not an implementation approval or
Gate 4 → 5 basis until scope rules, role/quorum policy, numeric objectives, failure-domain independence and acceptance
evidence are completed.
