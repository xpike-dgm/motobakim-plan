# TASK INDEX

Status: PROPOSED (E3 recorded 2026-09-21 after independent review PASS + micro PASS; Status PROPOSED = planned, never executed in Phase 6; full context-pack enrichment in Phase 7)

| Task ID | Flow/Feature | Objective | Depends On | Context Pack | Acceptance | Status |
|---|---|---|---|---|---|---|
| T-E3-001 | FL3.1.1/F3.1.1 | Enforce commit-time tuple decision point | — | ADR-006 Decision 2; C3.1 | Deny-by-default; cached claims rejected; reason-coded | PROPOSED |
| T-E3-002 | FL3.1.1/F3.1.1 | Reason-coded deny/hold responses | T-E3-001 | ADR-006 Decision 2 | Stable reason category on every denial | PROPOSED |
| T-E3-003 | FL3.1.2/F3.1.2 | Operation identity + idempotency store | T-E3-001 | ADR-006 Decision 4 | Same-retry-returns-result; different-payload CONFLICT | PROPOSED |
| T-E3-004 | FL3.1.2/F3.1.2 | Status lookup + unknown reconciliation | T-E3-003 | ADR-006 Decision 4 | OUTCOME_UNKNOWN until canonical lookup resolves | PROPOSED |
| T-E3-005 | FL3.1.3/F3.1.3 | State dictionary skeleton | T-E3-001 | ADR-006 Decision 8 | Verbatim tokens incl. CONFLICT/REJECTED | PROPOSED |
| T-E3-005b | FL3.1.3/F3.1.3 | Per-state-block addenda | T-E3-005 | ADR-006 Decision 8 | Allowed/blocked/retry/resolver per state block | PROPOSED |
| T-E3-006a | FL3.1.4/F3.1.4 | DB/RPC direct-path inventory | — | ADR-006 Decision 9 | Tables/views/functions/RPC inventoried | PROPOSED |
| T-E3-006b | FL3.1.4/F3.1.4 | Storage/URLs/Studio inventory | — | ADR-006 Decision 9 | Storage/URLs/Studio surfaces inventoried | PROPOSED |
| T-E3-006c | FL3.1.4/F3.1.4 | Browser contract rules | — | ADR-006 Decision 9 | Storage/origin/CSRF/step-up/lookup limits specified | PROPOSED |
| T-E3-007 | FL3.1.4/F3.1.4 | Bypass negative-test suite | T-E3-006a, T-E3-006b, T-E3-006c | ADR-006 Decision 9 | Cross-tenant/console bypass tests fail closed | PROPOSED |
| T-E3-008 | FL3.1.4/F3.1.4 | AI task-scope rules | T-E3-006a | ADR-002 Decision 6 | Narrow scope; no owner/billing creds | PROPOSED |
| T-E3-009 | FL3.2.1/F3.2.1 | Domain authority registry + versioning | — | ADR-001 Decision 1 | One authority per domain, stable identity | PROPOSED |
| T-E3-010 | FL3.2.2/F3.2.2 | History/provenance separation + convenience-copy rule | T-E3-009 | ADR-001 Decisions 2+6 | Copies never authority | PROPOSED |
| T-E3-011 | FL3.2.3/F3.2.3 | Object boundary + classification propagation | T-E3-009 | ADR-001 Decision 4 | Lineage/digest/classification on derivatives | PROPOSED |
| T-E3-012 | FL3.2.3/F3.2.3 | Quarantine activation gate | T-E3-011 | ADR-001 Decision 4 | Activation only after validation | PROPOSED |
| T-E3-013 | FL3.3.1/F3.3.1 | Reversibility preconditions checklist | — | ADR-002 Decisions 1+2 | No selection; preconditions listed | PROPOSED |
| T-E3-014 | FL3.3.1/F3.3.1 | API-boundary enforcement needs | T-E3-013 | ADR-002 Decisions 1+2 | Needs specified, no provisioning | PROPOSED |
| T-E3-015 | FL3.3.1/F3.3.1 | Platform BOM inputs template | T-E3-013 | ADR-002 cost paragraph | Classification slots, no numbers | PROPOSED |
| T-E3-016 | FL3.3.2/F3.3.2 | RLS/storage defense policies | — | ADR-002 Option A + Decision 1 | Defense-only; never sole authority | PROPOSED |
| T-E3-017 | FL3.3.2/F3.3.2 | Secret custody + rotation rules | T-E3-016 | ADR-002 Option A + Decision 1 | Server-only secrets; rotation procedure | PROPOSED |
| T-E3-018 | FL3.3.2/F3.3.2 | Changelog/compat-hold procedure | T-E3-016 | ADR-002 Decision 7 | Dated changelog; hold on change | PROPOSED |
| T-E3-019 | FL3.4.1/F3.4.1 | Queue/worker contract | T-E3-001 | ADR-006 Decision 5 | Lease/retry/DLQ/backpressure specified | PROPOSED |
| T-E3-020 | FL3.4.1/F3.4.1 | Job-family list skeleton | T-E3-019 | ADR-006 Decision 5 | All families listed | PROPOSED |
| T-E3-020b | FL3.4.1/F3.4.1 | Per-family gate-conditions matrix | T-E3-020 | ADR-006 Decision 5 | Gate conditions per family | PROPOSED |
| T-E3-021 | FL3.4.1/F3.4.1 | Poison/backpressure/cancel/drain handling | T-E3-019 | ADR-006 Decision 5 | Poison quarantined; drain on deploy | PROPOSED |
| T-E3-022 | FL3.4.1/F3.4.1 | Owner-visible backlog + resolver | T-E3-019 | ADR-006 Decision 5 | Backlog readable; resolver assigned | PROPOSED |
| T-E3-023 | FL3.5.1/F3.5.1 | Floors store + pre-commit re-read | T-E3-001 | ADR-006 Decision 6 | Newer/equal floor wins; ties hold | PROPOSED |
| T-E3-024a | FL3.5.2/F3.5.2 | Epoch edge list | T-E3-023 | ADR-006 Decision 7 | All revocation edges listed | PROPOSED |
| T-E3-024b | FL3.5.2/F3.5.2 | Per-edge revocation contract | T-E3-024a | ADR-006 Decision 7 | Revocation per edge + E4/E5/E6 call-outs | PROPOSED |
| T-E3-025 | FL3.5.2/F3.5.2 | Non-retraction handling | T-E3-024b | ADR-006 Decision 7 | Downloaded copies marked non-retractable | PROPOSED |
| T-E3-026 | FL3.6.1/F3.6.1 | 4-plane quarantine import procedure (document) | T-E3-009, T-E3-013, T-E3-016, T-E3-023 | ADR-002 Decisions 2+3 | Procedure + checklist document; independent custody | PROPOSED |
| T-E3-027 | FL3.6.1/F3.6.1 | Manifest reconciliation checklist | T-E3-026 | ADR-002 Decisions 2+3 | Checklist closable with evidence | PROPOSED |
| T-E3-028 | FL3.6.2/F3.6.2 | Stable-ID + logical-export format spec | T-E3-026 | ADR-002 Decision 4 | Spec only; no execution, no account | PROPOSED |
| T-E3-029 | FL3.6.2/F3.6.2 | PARTIAL/QUARANTINE state handling | T-E3-028 | ADR-002 Decision 4 | Gaps explicit, never smoothed | PROPOSED |
| T-E3-030 | FL3.7.1/F3.7.1 | Cost BOM skeleton with classification | — | ADR-006 Decision 11 | Slots classified; thresholds HELD | PROPOSED |
| T-E3-031 | FL3.7.1/F3.7.1 | Hold-not-weaken + owner-readable HELD spec | T-E3-030 | ADR-006 Decision 11 | No numerics; no live metering | PROPOSED |
| T-E3-032 | FL3.8.1/F3.8.1 | Env identity/secret separation | T-E3-013 | ADR-007 env control | Separated identities/secrets per env | PROPOSED |
| T-E3-033 | FL3.8.1/F3.8.1 | Promotion-gate reference stub | T-E3-032 | ADR-007 env control | HELD unless E6 checks pass; no logic | PROPOSED |
| T-E3-034 | FL3.1.1/F3.1.1 | Durable-state category list | — | ADR-006 Decision 1 | Categories listed, no implementation | PROPOSED |
| T-E3-035 | FL3.1.2/F3.1.2 | Core-vs-effect + outbox-intent contract | T-E3-003 | ADR-006 Decision 3 | Deterministic intent specified | PROPOSED |
| T-E3-036 | FL3.3.1/F3.3.1 | Transition-gate package (HELD) | T-E3-013 | ADR-006 Decision 10 | Evidence-gated; no migration | PROPOSED |
| T-E10-001 | FL10.1.1/F10.1.1 | Graph node registration rule | — | ADR-015 Rule 3; C10.1 | Stable identity + metadata on every record | PROPOSED |
| T-E10-002 | FL10.1.1/F10.1.1 | Identity/metadata convention (§3 relations only) | T-E10-001 | ADR-015 Rule 3; addendum §3 | 8-relation verbatim list | PROPOSED |
| T-E10-003a | FL10.1.1/F10.1.1 | Structural detectors (4) | T-E10-002 | ADR-015 Rule 3 | Orphan/broken/cycle/forbidden specified | PROPOSED |
| T-E10-003b | FL10.1.1/F10.1.1 | Governance detectors (3) | T-E10-003a | ADR-015 Rule 3 | Ownerless/untested/stale specified | PROPOSED |
| T-E10-004 | FL10.2.1/F10.2.1 | Capsule declaration template | T-E10-001 | ADR-015 Rules 1+2; C10.2 | Purpose/surface/interior/deps/tests/change fields | PROPOSED |
| T-E10-005 | FL10.2.1/F10.2.1 | Dependency direction rules | T-E10-004 | ADR-015 Rule 4; C10.2 | Toward-stability; no silent imports | PROPOSED |
| T-E10-006 | FL10.2.1/F10.2.1 | Repo topology + governed addresses | T-E10-004 | ADR-015 Rule 2; C10.2 | Linkage, addresses, no-orphan rule, manifest coverage | PROPOSED |
| T-E10-007 | FL10.3.1/F10.3.1 | Pack schema fields (14 enumerated) | T-E10-004 | ADR-015 Rule 5; addendum §4 | All field names listed; detail HELD Phase 7 | PROPOSED |
| T-E10-008 | FL10.3.2/F10.3.1 | Registry states + transitions | T-E10-007 | ADR-015 Rule 5; addendum §4 | READY→…→DONE/BLOCKED + out-of-scope→BLOCKED | PROPOSED |
| T-E10-009 | FL10.4.1/F10.4.1 | Closure matrix template (enumeration only) | T-E10-007 | ADR-015 Rule 6; addendum §5 | 10 layers + bidirectional trace shape | PROPOSED |
| T-E10-010 | FL10.4.1/F10.4.1 | Traceability audit + gap/all-DONE tests | T-E10-009 | ADR-015 Rule 6 | Orphan/gap labels; removal-gap + all-DONE tests | PROPOSED |
| T-E10-011a | FL10.5.1/F10.5.1 | Core checklists (document-level) | T-E10-009 | ADR-015 Rule 7; addendum §6 | Order/doc/failure checklists, no code | PROPOSED |
| T-E10-011b | FL10.5.1/F10.5.1 | Cross-cutting checklists (document-level) | T-E10-011a | ADR-015 Rule 7; addendum §6 | Collision/compat/walkthrough checklists, no code | PROPOSED |
| T-E10-012 | FL10.5.1/F10.5.1 | Excess-work scan rule | T-E10-011a | ADR-015 Rule 7 | Excess-work detection specified | PROPOSED |
| T-E10-013 | FL10.6.1/F10.6.1 | Design gate checklist + controlled-change entry | T-E10-002 | ADR-015 Rule 8; addendum §7 | Full §7 set; new patterns via controlled change | PROPOSED |
| T-E10-014 | FL10.6.1/F10.6.1 | Regression evidence rule | T-E10-013 | ADR-015 Rule 8 | Full/cross-screen/state/a11y evidence required | PROPOSED |
| T-E10-015 | FL10.7.1/F10.7.1 | Review protocol + externals-notice template | T-E10-007 | ADR-015 Rule 9; addendum §0 | Role separation; nontechnical externals notice | PROPOSED |
| T-E10-016 | FL10.7.1/F10.7.1 | DEC-0041 parallel-output guards | T-E10-015 | ADR-015 Rule 9; DEC-0041 | Separate outputs, no overwrite, no consensus-PASS | PROPOSED |
| T-E5-001 | FL5.1.1/F5.1.1 | Account-light start procedure | — | ADR-004 identity; C5.1 | Local-first default; no forced server account | PROPOSED |
| T-E5-002 | FL5.1.1/F5.1.1 | Profile migration with preview + conflict hold | T-E5-001 | ADR-004 migration; C5.1 | Preview shown; conflicts held; source preserved | PROPOSED |
| T-E5-003 | FL5.2.1/F5.2.1 | Tuple decision point | — | ADR-004 R1; C5.2 | Current-context allow/deny/hold + reason | PROPOSED |
| T-E5-004 | FL5.2.1/F5.2.1 | Reason-coded responses | T-E5-003 | ADR-004 R1; C5.2 | Stable reason categories | PROPOSED |
| T-E5-005 | FL5.2.2/F5.2.2 | Incompatible-pair blocking | T-E5-003 | ADR-004 SoD; C5.2 | Self-approval blocked per change | PROPOSED |
| T-E5-006 | FL5.2.2/F5.2.2 | Small-team HELD + escalation | T-E5-005 | ADR-004 SoD; C5.2 | Visible HELD with owner/escalation | PROPOSED |
| T-E5-007a | FL5.3.1/F5.3.1 | Auth method (phishing-resistant login) | — | ADR-004 R3; C5.3 | Specify method, no numerics, no implementation | PROPOSED |
| T-E5-007b | FL5.3.1/F5.3.1 | Step-up + recovery-strength rules | T-E5-007a | ADR-004 R3; C5.3 | Fresh transaction-bound step-up; recovery not weaker | PROPOSED |
| T-E5-008 | FL5.3.1/F5.3.1 | Session bounds/rotation/revocation | T-E5-007a | ADR-004 R3; C5.3 | Bounds specified; server revoke; no numerics | PROPOSED |
| T-E5-009 | FL5.3.2/F5.3.2 | Identity-plane epoch sweep | T-E5-008 | ADR-004 R4; C5.3 + F3.5.2/T-E3-024b | Sessions/grants/pending revoked; runtime via E3 | PROPOSED |
| T-E5-010 | FL5.3.2/F5.3.2 | Honest non-retraction marking | T-E5-009 | ADR-004 R4; C5.3 | Downloaded copies marked non-retractable | PROPOSED |
| T-E5-011 | FL5.4.1/F5.4.1 | Recovery-only procedure | T-E5-008 | ADR-004 R5; C5.4 | Revoke + re-auth; never approve/publish/grant | PROPOSED |
| T-E5-012 | FL5.4.1/F5.4.1 | Dual-control/last-admin path | T-E5-011 | ADR-004 R5; C5.4 | Dual control or governed break-glass | PROPOSED |
| T-E5-013 | FL5.5.1/F5.5.1 | Custody store + fallback buffer | — | ADR-005 R3/R5; C5.5 | Append-only + independent fallback | PROPOSED |
| T-E5-014 | FL5.5.1/F5.5.1 | Before-effect linkage + integrity + R6 | T-E5-013 | ADR-005 R3/R5 + ADR-004 R6 | Receipt pre-effect; alerting; restore continuity | PROPOSED |
| T-E5-015 | FL5.5.2/F5.5.2 | Investigation chain queries | T-E5-013 | ADR-005 R7; C5.5 | Object-centered chain; access audited | PROPOSED |
| T-E5-016a | FL5.5.3/F5.5.3 | Event coverage R1 + minimum meaning R2 | T-E5-013 | ADR-005 R1/R2; C5.5 | Enumeration only | PROPOSED |
| T-E5-016b | FL5.5.3/F5.5.3 | Retention/legal/admin R6/R8 | T-E5-016a | ADR-005 R6/R8; C5.5 | Explicit policy; changes audited | PROPOSED |
| T-E5-017 | FL5.6.1/F5.6.1 | Quarantine pipeline states | — | ADR-004 R7; C5.6 | Full state chain with branches | PROPOSED |
| T-E5-018 | FL5.6.1/F5.6.1 | Isolated preview rules | T-E5-017 | ADR-004 R7; C5.6 | No creds/APIs/network in preview | PROPOSED |
| T-E5-019 | FL5.6.2/F5.6.2 | Export disclosure record | — | ADR-004 R8; C5.6 | Minimization + non-retractable record + warnings | PROPOSED |
| T-E5-020 | FL5.6.3/F5.6.3 | AI proposal-only tagging | T-E5-017 | ADR-004 R9; C5.6 | Provenance-linked; never approval; hostile inert | PROPOSED |
| T-E5-021 | FL5.7.1/F5.7.1 | Activation gate checklist (skeleton only) | — | ADR-004 R10; C5.7; F5.7.1 | 11 items evaluable; HELD default; evidence HELD Phase 7 | PROPOSED |
| T-E6-001 | FL6.1.1/F6.1.1 | Authority registry (8 authorities) | — | ADR-007 R1; C6.1 | Distinct registered authorities | PROPOSED |
| T-E6-002 | FL6.1.1/F6.1.1 | Non-collapse + HOLD rules + R8 | T-E6-001 | ADR-007 R1/R6 + ADR-003 R8 | Alias/service collapse blocked; per-change independence | PROPOSED |
| T-E6-003 | FL6.2.1/F6.2.1 | Snapshot binding | T-E6-001 | ADR-003 R1; C6.2 | Exact immutable snapshot bound | PROPOSED |
| T-E6-004 | FL6.2.1/F6.2.1 | Guarded transition + fence (E3 floors consumed) | T-E6-003 | ADR-003 R2/R4 + T-E3-023 | Single transition; fenced precedence; backward fatal | PROPOSED |
| T-E6-005 | FL6.2.1/F6.2.1 | State enumeration | T-E6-004 | ADR-003 R3; C6.2 | Full state model + branches | PROPOSED |
| T-E6-006 | FL6.2.2/F6.2.2 | Consumer contract checks | T-E6-004 | ADR-003 R9; C6.2 | Client-side evaluability; stale rejected | PROPOSED |
| T-E6-007a | FL6.3.1/F6.3.1 | Plane/credentials/paths | — | ADR-003 R5; C6.3 | Negative-only; independence; drilled paths | PROPOSED |
| T-E6-007b | FL6.3.1/F6.3.1 | Membership/bounds/confirmation | T-E6-007a | ADR-003 R5; C6.3 | Two-person/single-actor; time-bound; retros | PROPOSED |
| T-E6-008 | FL6.3.1/F6.3.1 | Drills + retrospectives | T-E6-007a | ADR-003 R5; C6.3 | Drill records; mandatory retros | PROPOSED |
| T-E6-009 | FL6.4.1/F6.4.1 | Provenance/SBOM/signing chain | — | ADR-007 R2/R4; C6.4 | Artifact-bound chain; independent verifier; no numerics | PROPOSED |
| T-E6-010 | FL6.4.1/F6.4.1 | Custody + verification independence | T-E6-009 | ADR-007 R2/R4; C6.4 | Scoped dual-controlled custody | PROPOSED |
| T-E6-011 | FL6.5.1/F6.5.1 | Config-as-release typing | — | ADR-007 R7; C6.5 | Typed/versioned/reviewed config; no numerics | PROPOSED |
| T-E6-012 | FL6.5.1/F6.5.1 | Migration state machines | T-E6-011 | ADR-007 R7; C6.5 | Explicit states; forward recovery | PROPOSED |
| T-E6-013 | FL6.6.1/F6.6.1 | Rollout states + stop | — | ADR-007 R8; C6.6 | Staged states; stop never downgrades | PROPOSED |
| T-E6-014 | FL6.6.1/F6.6.1 | Rollback-as-event + quarantine | T-E6-013 | ADR-007 R8; C6.6 | New-event rollback; restore quarantine | PROPOSED |
| T-E6-015 | FL6.7.1/F6.7.1 | Incident taxonomy + graph | — | ADR-007 R9; C6.7 | Taxonomy + protected-copy graph | PROPOSED |
| T-E6-016 | FL6.7.1/F6.7.1 | Protected copy + closure rule | T-E6-015 | ADR-007 R9; C6.7 | Outside-plane copy; reconcile-to-close | PROPOSED |
| T-E6-017 | FL6.8.1/F6.8.1 | OTA denial gate | — | ADR-007 R10; C6.8 | Default deny + future envelope listed | PROPOSED |
|---|---|---|---|---|---|---|
