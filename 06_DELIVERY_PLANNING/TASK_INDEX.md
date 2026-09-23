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
| T-E3-019 | FL3.4.1/F3.4.1 | Queue/worker contract | T-E3-001, T-E3-003, T-E3-004 | ADR-006 Decision 5 | Lease/retry/DLQ/backpressure specified; lease-expiry→OUTCOME_UNKNOWN/PARTIAL/RECONCILING | PROPOSED |
| T-E3-020 | FL3.4.1/F3.4.1 | Job-family list skeleton | T-E3-019 | ADR-006 Decision 5 | All families listed | PROPOSED |
| T-E3-020b | FL3.4.1/F3.4.1 | Per-family gate-conditions matrix | T-E3-020 | ADR-006 Decision 5 | Gate conditions per family | PROPOSED |
| T-E3-021 | FL3.4.1/F3.4.1 | Poison/backpressure/cancel/drain handling | T-E3-019 | ADR-006 Decision 5 | Poison→DLQ/OBJECT_QUARANTINE + PARTIAL/RECONCILING; re-drive budget owner named; drain on deploy | PROPOSED |
| T-E3-022 | FL3.4.1/F3.4.1 | Owner-visible backlog + resolver | T-E3-019 | ADR-006 Decision 5 | Backlog readable; technical recovery owner named (never owner-debug); link T-E6-015 | PROPOSED |
| T-E3-023 | FL3.5.1/F3.5.1 | Floors store + pre-commit re-read | T-E3-001 | ADR-006 Decision 6 | Newer/equal floor wins; ties hold | PROPOSED |
| T-E3-024a | FL3.5.2/F3.5.2 | Epoch edge list | T-E3-023 | ADR-006 Decision 7 | All revocation edges listed | PROPOSED |
| T-E3-024b | FL3.5.2/F3.5.2 | Per-edge revocation contract | T-E3-024a | ADR-006 Decision 7 | Revocation per edge + E4/E5/E6 call-outs | PROPOSED |
| T-E3-025 | FL3.5.2/F3.5.2 | Non-retraction handling | T-E3-024b | ADR-006 Decision 7 | Downloaded copies marked non-retractable | PROPOSED |
| T-E3-026 | FL3.6.1/F3.6.1 | 4-plane quarantine import procedure (document) | T-E3-009, T-E3-013, T-E3-016, T-E3-023 | ADR-002 Decisions 2+3 | Procedure + checklist document; independent custody | PROPOSED |
| T-E3-027 | FL3.6.1/F3.6.1 | Manifest reconciliation checklist | T-E3-026 | ADR-002 Decisions 2+3 | Checklist closable with evidence | PROPOSED |
| T-E3-028 | FL3.6.2/F3.6.2 | Stable-ID + logical-export format spec | T-E3-026 | ADR-002 Decision 4 | Spec only; no execution, no account | PROPOSED |
| T-E3-029 | FL3.6.2/F3.6.2 | PARTIAL/QUARANTINE state handling | T-E3-028 | ADR-002 Decision 4 | Gaps explicit, never smoothed | PROPOSED |
| T-E3-030 | FL3.7.1/F3.7.1 | Cost BOM skeleton with classification | — | ADR-006 Decision 11 | Slots classified; thresholds HELD; drain-vs-hold edge to queue/rollout tasks | PROPOSED |
| T-E3-031 | FL3.7.1/F3.7.1 | Hold-not-weaken + owner-readable HELD spec | T-E3-030 | ADR-006 Decision 11 | No numerics; no live metering; drain-vs-hold edge to queue/rollout tasks | PROPOSED |
| T-E3-032 | FL3.8.1/F3.8.1 | Env identity/secret separation | T-E3-013 | ADR-007 env control | Separated identities/secrets per env | PROPOSED |
| T-E3-033 | FL3.8.1/F3.8.1 | Promotion-gate reference stub | T-E3-032 | ADR-007 env control | HELD unless E6 checks pass; no logic | PROPOSED |
| T-E3-034 | FL3.1.1/F3.1.1 | Durable-state category list | — | ADR-006 Decision 1 | Categories listed, no implementation | PROPOSED |
| T-E3-035 | FL3.1.2/F3.1.2 | Core-vs-effect + outbox-intent contract | T-E3-003 | ADR-006 Decision 3 | Deterministic intent specified | PROPOSED |
| T-E3-036 | FL3.3.1/F3.3.1 | Transition-gate package (HELD) | T-E3-013 | ADR-006 Decision 10 | Evidence-gated; no migration | PROPOSED |
| T-E10-001 | FL10.1.1/F10.1.1 | Graph node registration rule | — | ADR-015 Decision 3; C10.1 | Stable identity + metadata on every record | PROPOSED |
| T-E10-002 | FL10.1.1/F10.1.1 | Identity/metadata convention (§3 relations only) | T-E10-001 | ADR-015 Decision 3; addendum §3 | 8-relation verbatim list | PROPOSED |
| T-E10-003a | FL10.1.1/F10.1.1 | Structural detectors (4) | T-E10-002 | ADR-015 Decision 3 | Orphan/broken/cycle/forbidden specified | PROPOSED |
| T-E10-003b | FL10.1.1/F10.1.1 | Governance detectors (3) | T-E10-003a | ADR-015 Decision 3 | Ownerless/untested/stale specified | PROPOSED |
| T-E10-004 | FL10.2.1/F10.2.1 | Capsule declaration template | T-E10-001 | ADR-015 Decisions 1+2; C10.2 | Purpose/surface/interior/deps/tests/change fields | PROPOSED |
| T-E10-005 | FL10.2.1/F10.2.1 | Dependency direction rules | T-E10-004 | ADR-015 Decision 4; C10.2 | Toward-stability; no silent imports | PROPOSED |
| T-E10-006 | FL10.2.1/F10.2.1 | Repo topology + governed addresses | T-E10-004 | ADR-015 Decision 2; C10.2 | Linkage, addresses, no-orphan rule, manifest coverage | PROPOSED |
| T-E10-007 | FL10.3.1/F10.3.1 | Pack schema fields (14 enumerated) | T-E10-004 | ADR-015 Decision 5; addendum §4 | All field names listed; detail HELD Phase 7 | PROPOSED |
| T-E10-008 | FL10.3.2/F10.3.1 | Registry states + transitions | T-E10-007 | ADR-015 Decision 5; addendum §4 | READY→…→DONE/BLOCKED + out-of-scope→BLOCKED | PROPOSED |
| T-E10-009 | FL10.4.1/F10.4.1 | Closure matrix template (enumeration only) | T-E10-007 | ADR-015 Decision 6; addendum §5 | 10 layers + bidirectional trace shape | PROPOSED |
| T-E10-010 | FL10.4.1/F10.4.1 | Traceability audit + gap/all-DONE tests | T-E10-009 | ADR-015 Decision 6 | Orphan/gap labels; removal-gap + all-DONE tests | PROPOSED |
| T-E10-011a | FL10.5.1/F10.5.1 | Core checklists (document-level) | T-E10-009 | ADR-015 Decision 7; addendum §6 | Order/doc/failure checklists, no code | PROPOSED |
| T-E10-011b | FL10.5.1/F10.5.1 | Cross-cutting checklists (document-level) | T-E10-011a | ADR-015 Decision 7; addendum §6 | Collision/compat/walkthrough checklists, no code | PROPOSED |
| T-E10-012 | FL10.5.1/F10.5.1 | Excess-work scan rule | T-E10-011a | ADR-015 Decision 7 | Excess-work detection specified | PROPOSED |
| T-E10-013 | FL10.6.1/F10.6.1 | Design gate checklist + controlled-change entry | T-E10-002 | ADR-015 Decision 8; addendum §7 | Full §7 set; new patterns via controlled change | PROPOSED |
| T-E10-014 | FL10.6.1/F10.6.1 | Regression evidence rule | T-E10-013 | ADR-015 Decision 8 | Full/cross-screen/state/a11y evidence required | PROPOSED |
| T-E10-015 | FL10.7.1/F10.7.1 | Review protocol + externals-notice template | T-E10-007 | ADR-015 Decision 9; addendum §0 | Role separation; nontechnical externals notice | PROPOSED |
| T-E10-016 | FL10.7.1/F10.7.1 | DEC-0041 parallel-output guards | T-E10-015 | ADR-015 Decision 9; DEC-0041 | Separate outputs, no overwrite, no consensus-PASS | PROPOSED |
| T-E5-001 | FL5.1.1/F5.1.1 | Account-light start procedure | — | ADR-004 identity; C5.1 | Local-first default; no forced server account | PROPOSED |
| T-E5-002 | FL5.1.1/F5.1.1 | Profile migration with preview + conflict hold | T-E5-001 | ADR-004 migration; C5.1 | Preview shown; conflicts held; source preserved | PROPOSED |
| T-E5-003 | FL5.2.1/F5.2.1 | Tuple decision point | — | ADR-004 R1; C5.2 | Current-context allow/deny/hold + reason | PROPOSED |
| T-E5-004 | FL5.2.1/F5.2.1 | Reason-coded responses | T-E5-003 | ADR-004 R1; C5.2 | Stable reason categories | PROPOSED |
| T-E5-005 | FL5.2.2/F5.2.2 | Incompatible-pair blocking | T-E5-003 | ADR-004 SoD; C5.2 | Self-approval blocked per change | PROPOSED |
| T-E5-006 | FL5.2.2/F5.2.2 | Small-team HELD + escalation | T-E5-005 | ADR-004 SoD; C5.2 | Visible HELD with owner/escalation | PROPOSED |
| T-E5-007a | FL5.3.1/F5.3.1 | Auth method (phishing-resistant login) | — | ADR-004 R3; C5.3 | Specify method, no numerics, no implementation | PROPOSED |
| T-E5-007b | FL5.3.1/F5.3.1 | Step-up + recovery-strength rules | T-E5-007a | ADR-004 R3; C5.3 | Fresh transaction-bound step-up; recovery not weaker | PROPOSED |
| T-E5-008 | FL5.3.1/F5.3.1 | Session bounds/rotation/revocation | T-E5-007a | ADR-004 R3; C5.3 | Bounds specified; server revoke; no numerics | PROPOSED |
| T-E5-009 | FL5.3.2/F5.3.2 | Identity-plane epoch sweep | T-E5-008, T-E5-013, T-E5-014 | ADR-004 R4; C5.3 + F3.5.2/T-E3-024b | Sessions/grants/pending revoked; runtime via E3; quarantine/unknown binding on audit outage | PROPOSED |
| T-E5-010 | FL5.3.2/F5.3.2 | Honest non-retraction marking | T-E5-009 | ADR-004 R4; C5.3 | Downloaded copies marked non-retractable | PROPOSED |
| T-E5-011 | FL5.4.1/F5.4.1 | Recovery-only procedure | T-E5-008 | ADR-004 R5; C5.4 | Revoke + re-auth; never approve/publish/grant | PROPOSED |
| T-E5-012 | FL5.4.1/F5.4.1 | Dual-control/last-admin path | T-E5-011 | ADR-004 R5; C5.4 | Dual control or governed break-glass | PROPOSED |
| T-E5-013 | FL5.5.1/F5.5.1 | Custody store + fallback buffer | — | ADR-005 R3/R5; C5.5 | Append-only + independent fallback; bounded-buffer size/overflow→HELD; dual-down reconciliation owner named (with T-E3-027/T-E5-015) | PROPOSED |
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
| T-E6-007a | FL6.3.1/F6.3.1 | Plane/credentials/paths | T-E3-023, T-E5-013, T-E5-014, T-E3-005 | ADR-003 R5; C6.3 | Negative-only; independence; drilled paths; audit-precondition bound | PROPOSED |
| T-E6-007b | FL6.3.1/F6.3.1 | Membership/bounds/confirmation | T-E6-007a | ADR-003 R5; C6.3 | Two-person/single-actor; time-bound; retros | PROPOSED |
| T-E6-008 | FL6.3.1/F6.3.1 | Drills + retrospectives | T-E6-007a | ADR-003 R5; C6.3 | Drill records; mandatory retros | PROPOSED |
| T-E6-009 | FL6.4.1/F6.4.1 | Provenance/SBOM/signing chain | — | ADR-007 R2/R4; C6.4 | Artifact-bound chain; independent verifier; no numerics | PROPOSED |
| T-E6-010 | FL6.4.1/F6.4.1 | Custody + verification independence | T-E6-009 | ADR-007 R2/R4; C6.4 | Scoped dual-controlled custody | PROPOSED |
| T-E6-011 | FL6.5.1/F6.5.1 | Config-as-release typing | — | ADR-007 R7; C6.5 | Typed/versioned/reviewed config; no numerics | PROPOSED |
| T-E6-012 | FL6.5.1/F6.5.1 | Migration state machines | T-E6-011, T-E3-023, T-E3-026, T-E3-027, T-E6-014, T-E6-015 | ADR-007 R7; C6.5 | Explicit states; per-region PARTIAL rule; forward-only recovery owner; no binary rollback of valid data | PROPOSED |
| T-E6-013 | FL6.6.1/F6.6.1 | Rollout states + stop | T-E3-023, T-E6-015, T-E6-016 | ADR-007 R8; C6.6 | Staged states; stop never downgrades; stop resolver named; offline residual disclosure via T-E1-013 | PROPOSED |
| T-E6-014 | FL6.6.1/F6.6.1 | Rollback-as-event + quarantine | T-E6-013, T-E3-023, T-E6-015, T-E6-016 | ADR-007 R8; C6.6 | New-event rollback; restore quarantine; generations monotonic | PROPOSED |
| T-E6-015 | FL6.7.1/F6.7.1 | Incident taxonomy + graph | — | ADR-007 R9; C6.7 | Taxonomy + protected-copy graph | PROPOSED |
| T-E6-016 | FL6.7.1/F6.7.1 | Protected copy + closure rule | T-E6-015 | ADR-007 R9; C6.7 | Outside-plane copy; reconcile-to-close | PROPOSED |
| T-E6-017 | FL6.8.1/F6.8.1 | OTA denial gate | — | ADR-007 R10; C6.8 | Default deny + future envelope listed | PROPOSED |
| T-E4-001 | FL4.1.1/F4.1.1 | Core composition check | — | ADR-009 R1; C4.1 | Verified core + nested safety; selected scope only; no full-library; essentials irremovable | PROPOSED |
| T-E4-002 | FL4.1.1/F4.1.1 | Safety-media nesting check | T-E4-001 | ADR-009 R1; C4.1 | Never additive/on-demand-for-size | PROPOSED |
| T-E4-003 | FL4.1.2/F4.1.2 | Nonessential on-demand rules | — | ADR-009 R1; C4.1 | Separate/explicit/cancelable/evictable/re-fetchable | PROPOSED |
| T-E4-004 | FL4.1.2/F4.1.2 | Size-shown rule | T-E4-003 | DEC-0023; C4.1 | Size shown before download | PROPOSED |
| T-E4-005 | FL4.2.1/F4.2.1 | Stage-verify-promote contract | — | ADR-009 R2; C4.2 | Verified; atomic; peak-space by eviction, never by deleting truth | PROPOSED |
| T-E4-006 | FL4.2.1/F4.2.1 | Fallback rule | T-E4-005 | ADR-009 R2; C4.2 | Missing/stale delta → complete package | PROPOSED |
| T-E4-007 | FL4.3.1/F4.3.1 | CON-005 auto-transfer (required only) | — | ADR-009 R3; CON-005; C4.3 | ONLY required core; no dialog; priority; completion≠authority | PROPOSED |
| T-E4-008 | FL4.3.1/F4.3.1 | Retry-HELD + saver rule | T-E4-007 | ADR-009 R3; C4.3 | Where-supported retry; values HELD; saver delays, never gates | PROPOSED |
| T-E4-009a | FL4.4.1/F4.4.1 | Eviction order | — | ADR-009 R4; C4.4 | Ordered eviction specified | PROPOSED |
| T-E4-009b | FL4.4.1/F4.4.1 | Never-evict list (6-class) | T-E4-009a | ADR-009 R4; C4.4 | 6 classes protected | PROPOSED |
| T-E4-010 | FL4.4.1/F4.4.1 | Hold-transfer rule | T-E4-009b | ADR-009 R4; C4.4 | Transfer held if staging cannot complete | PROPOSED |
| T-E4-011a | FL4.5.1/F4.5.1 | Ledger states | — | ADR-009 R5; C4.5 | Explicit states enumerated | PROPOSED |
| T-E4-011b | FL4.5.1/F4.5.1 | API reconcile via E3 | T-E4-011a | ADR-009 R5; C4.5; F3.1.2 | Submit/lookup via E3; E3 acceptance authoritative | PROPOSED |
| T-E4-012 | FL4.5.1/F4.5.1 | Anti-resurrection + restore quarantine | T-E4-011b | ADR-009 R5; C4.5 | Cannot resurrect; restore enters quarantine first | PROPOSED |
| T-E4-013 | FL4.6.1/F4.6.1 | Fail-closed gate + online-authoritative | — | ADR-009 R6; C4.6 | Fails closed inherited; internal-ops online-only; cached enforcement | PROPOSED |
| T-E4-014 | FL4.6.1/F4.6.1 | Recovery-closure check | T-E4-013 | ADR-009 R6; C4.6 | Complete compact closure for offline start | PROPOSED |
| T-E4-015 | FL4.7.1/F4.7.1 | No-plaintext gate | — | ADR-009 R7; C4.7 | Mechanism HELD; plaintext blocked at gate | PROPOSED |
| T-E4-016 | FL4.8.1/F4.8.1 | Candidate-points HELD registry | — | ADR-009 R8; C4.8 | Verbatim TEST POINTS; selection deferred to evidence | PROPOSED |
| T-E4-017 | FL4.9.1/F4.9.1 | Classification table | T-E4-001, T-E4-003 | Q-0046/BR-131..133; C4.1 + guard | Criteria + Q156/Q157 examples recorded; rule only, mechanism in F4.1.1/F4.1.2 | PROPOSED |
| T-E2-016 | FL2.12.1/F2.12.1 | Failed-state render | T-E2-004, T-E2-005 | RQ-060..062; C2.3 + guard | Failed states shown recoverable + resolver named (E6 via T-E6-014/015 chain; T-E2-004/005 invoke-only); unsaved/partial distinguished; four-part explanation | PROPOSED |
| T-E9-001 | FL9.1.1/F9.1.1 | 5-option proposal rule | — | ADR-014 R1; C9.1 | Exactly 5 bounded options | PROPOSED |
| T-E9-002 | FL9.1.1/F9.1.1 | 6-dimension verify checklist | T-E9-001 | ADR-014 R1; C9.1 + verify-E3/render-E1 seam | All six dimensions checked | PROPOSED |
| T-E9-003 | FL9.2.1/F9.2.1 | Economy skeleton | — | ADR-014 R2; C9.2 | Cheapest-adequate first; nothing selected/logged/budgeted | PROPOSED |
| T-E9-004 | FL9.3.1/F9.3.1 | Adapter boundary rule | — | ADR-014 R3; C9.3 | Specifics behind adapters; change re-evaluates | PROPOSED |
| T-E9-005 | FL9.3.1/F9.3.1 | Re-evaluation trigger | T-E9-004 | ADR-014 R3; C9.3 | Version/behavior change triggers review | PROPOSED |
| T-E9-006 | FL9.4.1/F9.4.1 | Tool sandbox + cost visibility | — | ADR-014 R4; C9.4 | Authority outside output; bounded retry + cost seen | PROPOSED |
| T-E9-007 | FL9.4.1/F9.4.1 | Non-AI continuation rule | T-E9-006 | ADR-014 R4; C9.4 | Safe deterministic path preserved | PROPOSED |
| T-E9-008 | FL9.5.1/F9.5.1 | Allowed-10 reference | — | ADR-014 R5; C9.5 + verify-E3/render-E1 seam | Items 1–10 verbatim cited | PROPOSED |
| T-E9-009 | FL9.6.1/F9.6.1 | Never-15 reference | — | ADR-014 R6; C9.6 + verify-E3/render-E1 seam | Items 1–15 verbatim cited; HOLD on ambiguity | PROPOSED |
| T-E9-010 | FL9.6.1/F9.6.1 | HOLD-on-ambiguity rule | T-E9-009 | ADR-014 R6; C9.6 | No invented certainty or fallback answer | PROPOSED |
| T-E9-011 | FL9.7.1/F9.7.1 | Role separation + externals notice | — | ADR-014 R7; C9.7; F10.7.1/C10.7; DEC-0028/0029 | Separation; nontechnical externals notice | PROPOSED |
| T-E1-001 | FL1.0.1/F1.0.1 | Shell + tabs only (excl. SCR-005 context) | — | ADR-008 D2+D8; C1.0 | Five tabs; bottom-bar HELD; no dashboard/KPI/card-stack | PROPOSED |
| T-E1-002 | FL1.0.2/F1.0.1 | Garage context only (SCR-005/008) | T-E1-001 | SCR-005/008; C1.0 + guard | Display/switch; lifecycle entry; no hub | PROPOSED |
| T-E1-003 | FL1.1.1/F1.1.1 | First-value + add-bike render | T-E1-001 | SCR-001/002; C1.1 + guard | Value before account; creation form | PROPOSED |
| T-E1-004 | FL1.1.2/F1.1.2 | Variant resolution render | T-E1-003 | SCR-003/004; C1.1 + guard | Distinction + fit/missing states | PROPOSED |
| T-E1-005a | FL1.2.1/F1.2.1 | Discovery render (009/010) | T-E1-004 | SCR-009/010; C1.2 + guard | Task find/select shown; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-005b | FL1.2.1/F1.2.1 | Fit render (011/012) | T-E1-005a | SCR-011/012; C1.2 + guard | Fit evaluation shown; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-005c | FL1.2.1/F1.2.1 | Preparation render (013 teaching-only) | T-E1-005b | SCR-013; C1.2 + guard | Labeled teaching-only, never active instruction; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-006 | FL1.3.1/F1.3.1 | Active execution render (014/015/018 only) | T-E1-005b | SCR-014/015/018; C1.3 + guard | Truthful outcomes; safe closure not payable; no ignore-and-continue; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-007 | FL1.3.2/F1.3.1 | Resume/revalidation render | T-E1-006 | SCR-016; C1.3 + guard | Revalidation; saved≠proof; bottom-bar HELD; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-008 | FL1.3.3/F1.3.1 | Remap render | T-E1-006 | SCR-017; C1.3 + guard | Remap required; no guessed continuation; bottom-bar HELD; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-009 | FL1.4.1/F1.4.1 | Diagnosis render via E9 | T-E1-001 | SCR-019..021; ADR-014 R1/R5/R6; C1.4 + guard | Check shown; E9 proposes/E1 renders/E3 verifies; renders SCR-019..021 only; offline OUTCOME_UNKNOWN→E3 reconcile via T-E4-011b/T-E3-004; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-010 | FL1.5.1/F1.5.1 | Maintenance/reminder render | T-E1-001 | SCR-022..024; C1.5 + guard | Verified source; snooze≠completion; catch-up path; novice-comprehensible copy (CON-004; verified at F10.6.1 gate) | PROPOSED |
| T-E1-011 | FL1.6.1/F1.6.1 | History render (025/026/030 only) | T-E1-001 | SCR-025/026/030; ADR-001/004/005; C1.6 + guard | Provenance; serve T-E3-010; authorize T-E5-013/019 | PROPOSED |
| T-E1-012 | FL1.6.2/F1.6.1 | Record/dispute render | T-E1-011 | SCR-027/028; C1.6 + guard | Standalone preserved; no-silent-winner | PROPOSED |
| T-E1-013 | FL1.6.3/F1.6.1 | Reach-back render | T-E1-011 | SCR-029; C1.6 + guard | Severity reach-back; survives inactive | PROPOSED |
| T-E1-014a | FL1.7.1/F1.7.1 | Lifecycle render (031/032/033) | T-E1-001 | SCR-031/032/033; C1.7 + guard | States shown; excl. SCR-008; DEC-0053 shape shown (1-free/3-subscribed/1-guide-selected) | PROPOSED |
| T-E1-014b | FL1.7.1/F1.7.1 | Entitlement gate render (037) | T-E1-014a | SCR-037; C5.x/T-E5-003; C1.7 + guard | Gates shown incl. DEC-0053 shape; enforcement server-side (E3/E5) | PROPOSED |
| T-E1-015 | FL1.8.1/F1.8.1 | Profile/collab/migration render | T-E1-001 | SCR-006/007/034; C1.8 + guard | Preview; no silent loss; revocable | PROPOSED |
| T-E1-016 | FL1.9.1/F1.9.1 | Community surface render | T-E1-001 | SCR-035/036/038; C1.9 + guard | Opt-in flows; decisions in E2 | PROPOSED |
| T-E1-017 | FL1.10.1/F1.10.1 | AI entry render (A1 verbatim) | T-E1-001 | AI_USTA DEC-0018; C1.10 + guard | 1+1+2; clutter/NL bounds; E9/E3 seam; renders A1 root only | PROPOSED |
| T-E1-018 | FL1.2.2/F1.2.2 | Range display | T-E1-005a | BR-063/064; C1.2 + guard | Experience-dependent range + date shown | PROPOSED |
| T-E1-019a | FL1.2.2/F1.2.2 | Split/exclusions render | T-E1-018 | BR-063/064; C1.2 + guard | Cost split + exclusions shown | PROPOSED |
| T-E1-019b | FL1.2.2/F1.2.2 | Assumptions/no-fabrication rule | T-E1-019a | BR-063/064; C1.2 + guard | Assumptions shown; unknown never invented | PROPOSED |
| T-E1-020 | FL1.9.2/F1.9.2 | Sponsored marking | T-E1-001 | BR-070/071/073; C1.9 + guard | Sponsored explicitly marked; hidden ads + alternatives visible | PROPOSED |
| T-E1-021 | FL1.9.2/F1.9.2 | Ranking firewall | T-E1-020 | BR-070/071/073; C1.9 + guard | Listing never substitutes guide; sales-target blocked; fit-first; no analytics input | PROPOSED |
| T-E1-022a | FL1.3.4/F1.3.2 | Condensed render | T-E1-006 | BR-074; C1.3 + guard | Short/fast shown | PROPOSED |
| T-E1-022b | FL1.3.4/F1.3.2 | Uncertainty banner | T-E1-022a | BR-074; C1.3 + guard | Safety uncertainty persistent; E4 fail-closed seam | PROPOSED |
| T-E1-023 | FL1.3.5/F1.3.3 | Criteria content per category | — | OPEN criterion + author role; C1.3 + guard | Content authored by domain expert + second review; E2 draft→E6 approve; validation HELD | PROPOSED |
| T-E1-024 | FL1.3.5/F1.3.3 | Enforcement render | T-E1-023 | OPEN criterion; C1.3 + guard + E3/E6 refs | Checked per E3 verification, rendered by E1 | PROPOSED |
| T-E1-025 | FL1.7.2/F1.7.1 | Replacement right render + server ref | T-E1-014a | Q222/Q227; C1.7 + guard | Pre-step correction + MAY-open; server decision cited; window HELD | PROPOSED |
| T-E2-001 | FL2.1.1/F2.1.1 | Workspace shell render | — | ADR-010 D2-D5; C2.1 + guard | Dense workspace; a11y baseline; responsive deferred | PROPOSED |
| T-E2-002 | FL2.2.1/F2.2.1 | Review queue render | T-E2-001 | WS-06; C2.2 + guard | Packets; independence; review≠publication | PROPOSED |
| T-E2-003 | FL2.2.2/F2.2.1 | Conflict review render | T-E2-002 | WS-05; C2.2 + guard | Conflict/gap with owner/reason/escalation | PROPOSED |
| T-E2-004 | FL2.3.1/F2.3.1 | Publication ops surface render | T-E2-001 | WS-07; C2.3 + guard + ADR-003/007 | Invokes only; E6 authorizes/executes | PROPOSED |
| T-E2-005 | FL2.3.2/F2.3.1 | Recall impact render | T-E2-004 | WS-11; C2.3 + guard + ADR-003/007 | Impact/reach-back; invoke only | PROPOSED |
| T-E2-006 | FL2.4.1/F2.4.1 | Source/quarantine view render | T-E2-001 | WS-03; C2.4 + guard | States + isolated preview + classification | PROPOSED |
| T-E2-007a | FL2.5.1/F2.5.1 | Coverage/research render (WS-01) | T-E2-001 | WS-01; C2.5 + guard + ADR-012 | Record-derived research queue | PROPOSED |
| T-E2-007b | FL2.5.1/F2.5.1 | Quality signals render (WS-09) | T-E2-007a | WS-09; C2.5 + guard + ADR-012 | Coverage-vs-completeness; drill-down; no opaque score | PROPOSED |
| T-E2-008 | FL2.6.1/F2.6.1 | Access admin view render | T-E2-001 | WS-12; C2.6 + guard | Scoped changes; no self-grant path | PROPOSED |
| T-E2-009 | FL2.7.1/F2.7.1 | Moderation decision render | T-E2-001 | SCR-036; WS-06/WS-10; IDCO-RQ-045..047; C2.7 + guard | Reasoned decision + audit; custody in E5 | PROPOSED |
| T-E2-010 | FL2.8.1/F2.8.1 | Authoring draft render | T-E2-001 | RQ-017..024; C2.8 + guard | Bounded draft; never live | PROPOSED |
| T-E2-011 | FL2.9.1/F2.9.1 | Variant admin render | T-E2-001 | WS-02; C2.9 + guard | Fencing + matrix/duplicate/comparison | PROPOSED |
| T-E2-012 | FL2.10.1/F2.10.1 | Lineage view render | T-E2-001 | WS-08; C2.10 + guard | Chain + rollback-candidate links | PROPOSED |
| T-E2-013 | FL2.11.1/F2.11.1 | Audit trail view render | T-E2-001 | WS-10; RQ-046/047; C2.11 + guard | Full fields + separation; custody in E5 | PROPOSED |
| T-E2-014 | FL2.7.1/F2.7.1 | Notify/status surfacing | T-E2-009 | SCR-036; C2.7 + guard | Contributor status/repair/appeal surfaced; channel HELD | PROPOSED |
| T-E2-015 | FL2.7.1/F2.7.1 | Withdrawal re-review owner | T-E2-009 | Q-0049/0050; C2.7 + guard | Trigger owner named for dependent-claim re-review | PROPOSED |
| T-E7-001 | FL7.1.1/F7.1.1 | Android lane checklist (8 nouns) | — | ADR-013 R1; C7.1 + E6-policy note | Recorded; HELD unless E6 decides; defines no policy | PROPOSED |
| T-E7-002 | FL7.1.1/F7.1.1 | Provenance-binding check | T-E7-001 | ADR-013 R1; C7.1 + E6-policy note | Binding as E6-policy application | PROPOSED |
| T-E7-003a | FL7.2.1/F7.2.1 | iOS proofs 1-2 (Mac, Apple custody) | — | ADR-013 R2; C7.2 + E6-policy note | Pass/HELD separately; no commitment | PROPOSED |
| T-E7-003b | FL7.2.1/F7.2.1 | iOS proofs 3-4 (provenance, recovery) | — | ADR-013 R2; C7.2 + E6-policy note | Pass/HELD separately; no commitment | PROPOSED |
| T-E7-003c | FL7.2.1/F7.2.1 | iOS proof 5 (clean-room rebuild) | — | ADR-013 R2; C7.2 + E6-policy note | Pass/HELD separately; no commitment | PROPOSED |
| T-E7-004 | FL7.3.1/F7.3.1 | Separation check | — | ADR-013 R3; C7.3 + E6-policy note | Distinctness verified; no takeover | PROPOSED |
| T-E7-005 | FL7.3.1/F7.3.1 | Key-loss path reference | T-E7-004 | ADR-013 R3; C7.3 + E6-policy note | Refers to E6 playbook; no handling here | PROPOSED |
| T-E7-006 | FL7.4.1/F7.4.1 | Classification maintenance | — | ADR-013 R4; C7.4 + E6-policy note | Bands current; triggers explicit | PROPOSED |
| T-E7-007 | FL7.5.1/F7.5.1 | Spend range evaluation (read-only) | — | ADR-013 R5; C7.5 + E6-policy note | TRY context only; holds by reference; no commitment; BILLING_HELD declarant is E3/E6 hold tasks (owner: payment only) | PROPOSED |
| T-E8-001 | FL8.1.1/F8.1.1 | 8-noun authority reference check | — | ADR-011 R1; C8.1 + E3/E6-ownership note | Reference present; E8 defines nothing | PROPOSED |
| T-E8-002 | FL8.1.1/F8.1.1 | 6-vector bypass check | T-E8-001 | ADR-011 R3; C8.1 + E3/E6-ownership note | All six vectors blocked | PROPOSED |
| T-E8-003 | FL8.1.1/F8.1.1 | Rebuildability check | T-E8-001 | ADR-011 R4; C8.1 + E3/E6-ownership note | Projections rebuildable-non-authoritative | PROPOSED |
| T-E8-004 | FL8.2.1/F8.2.1 | Boundedness evaluation | — | ADR-011 R2; C8.2 + workspace E2 note | 4 bounds checked; gate-only | PROPOSED |
| T-E8-005a | FL8.2.1/F8.2.1 | Removability evaluation (R5) | T-E8-004 | ADR-011 R5; C8.2 | 5 proofs; no first-release CMS | PROPOSED |
| T-E8-005b | FL8.2.1/F8.2.1 | Reconsideration trigger (R6) | T-E8-005a | ADR-011 R6; C8.2 | Measured-burden trigger specified | PROPOSED |
| T-E8-006 | FL8.3.1/F8.3.1 | Plane split check | — | ADR-012 R1; C8.3 + E3-owns seam | Metrics from records; E2 renders only | PROPOSED |
| T-E8-007 | FL8.4.1/F8.4.1 | Exclusion-list check | — | ADR-012 R2/R3; C8.4 + E2-render note | Verbatim nouns; per-class purpose/retention | PROPOSED |
| T-E8-008 | FL8.4.1/F8.4.1 | Purpose/retention check | T-E8-007 | ADR-012 R3; C8.4 + E2-render note | Named purpose + bounded retention per class | PROPOSED |
| T-E8-009 | FL8.5.1/F8.5.1 | Band classification | — | ADR-012 R4; C8.5 + E2-render note | Exact-qualifier bands incl. 9th outage item | PROPOSED |
| T-E8-010 | FL8.5.1/F8.5.1 | Outage-independence check | T-E8-009 | ADR-012 R2/R4; C8.5 + E2-render note | Dedicated failure never disables safe core | PROPOSED |
| T-E8-011 | FL8.6.1/F8.6.1 | 5-gate check | — | ADR-012 R5; C8.6 + E2-render note | Privacy/operability/TCO/offline/exit evaluated | PROPOSED |
| T-E8-012 | FL8.6.1/F8.6.1 | Exit-honesty check | T-E8-011 | ADR-012 R6; C8.6 + E2-render note | Export≠proof; 4 HELD proofs listed | PROPOSED |
