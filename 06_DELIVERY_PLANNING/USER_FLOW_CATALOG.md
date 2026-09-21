# USER FLOW CATALOG

Status: PROPOSED (E3 recorded 2026-09-21 after independent review PASS; rest pending)

| Flow ID | Feature | Actor | Trigger | Expected Outcome | Screens | Status |
|---|---|---|---|---|---|---|
| FL3.1.1 | F3.1.1 | Operator/system | Sensitive mutation request | ALLOW/DENY/HELD with reason before commit | — (API surface) | PROPOSED |
| FL3.1.2 | F3.1.2 | Operator | Lost response after submit | OUTCOME_UNKNOWN; same-ID lookup resolves, no blind retry | — (API surface) | PROPOSED |
| FL3.1.3 | F3.1.3 | Operator | State lookup/policy question | Allowed/blocked effects + retry/resolver per dictionary | — (API surface) | PROPOSED |
| FL3.1.4 | F3.1.4 | Security task | Audit sweep | Inventoried surfaces + negative-test results | — (API surface) | PROPOSED |
| FL3.2.1 | F3.2.1 | Operator | Create/version domain record | Versioned authority with stable identity; conflicts held | — (API surface) | PROPOSED |
| FL3.2.2 | F3.2.2 | Investigator | Audit question on an object | Full object-centered chain from protected evidence | — (API surface; investigator UI in E2) | PROPOSED |
| FL3.2.3 | F3.2.3 | Operator | Upload media batch | Quarantined; activated with lineage/digest/classification check | — (API surface) | PROPOSED |
| FL3.3.1 | F3.3.1 | Bounded AI task (no owner/billing/service_role) | Readiness check requested | Gap list + HELD provisioning; no account created | — (provider console, AI-operated) | PROPOSED |
| FL3.3.2 | F3.3.2 | Security task | Scheduled rotation window | Keys rotated/revoked/re-issued + audit event | — (API surface) | PROPOSED |
| FL3.4.1 | F3.4.1 | Operator/system | Long job submitted | ACCEPTED/QUEUED vs effect separated; checkpoint/heartbeat/cancel/drain/backlog/resolver visible | — (API surface) | PROPOSED |
| FL3.5.1 | F3.5.1 | System (commit path) | Any positive-effect commit | Current floors re-read; newer/equal floor wins; ties hold | — (API surface) | PROPOSED |
| FL3.5.2 | F3.5.2 | Security task | Suspected compromise | Epoch incremented; full edge list revoked end-to-end | — (API surface) | PROPOSED |
| FL3.6.1 | F3.6.1 | Recovery task | Scheduled drill | Restore executed; quarantine entered; checklist + evidence closed | — (API surface) | PROPOSED |
| FL3.6.2 | F3.6.2 | Recovery task | Exit rehearsal | Floors/truth preserved; gaps explicit PARTIAL/QUARANTINE | — (API surface) | PROPOSED |
| FL3.7.1 | F3.7.1 | System | HELD threshold policy evaluated (no numeric) | Owner-readable HELD; capability held not weakened | Owner-view | PROPOSED |
| FL3.8.1 | F3.8.1 | Release task | Promote staging artifact to production | Promotion HELD unless E6 artifact checks pass (reference) | — (API surface) | PROPOSED |
| FL10.1.1 | F10.1.1 | System/task author | New record created | Node with stable identity + metadata; gates detect orphans/broken links | — (planning graph, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.2.1 | F10.2.1 | Architect task | Module boundary declared | Capsule + contracts recorded; forbidden edge rejected | — (planning graph, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.3.1 | F10.3.1 | Planning selection rule (manual carrying default) | AI signals ready | Next READY selected; minimum pack handed over, nothing outside authorized | — (planned task-registry view, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.3.2 | F10.3.1 | AI worker | Task state change | Transitions with evidence links; out-of-scope forces BLOCKED/change-request | — (planned task-registry view, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.4.1 | F10.4.1 | Audit task | Closure audit requested | All 10 named layers evaluated; orphans/gaps stay visible | — (planned audit view, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.5.1 | F10.5.1 | Planning task | Simulation requested | Scenarios over documents incl. excess-work scan; no false PASS | — (planned audit view, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.6.1 | F10.6.1 | Design task | Screen submitted | Token/catalog/rules + Turkish/contracts/reference/shell compliance | — (planned design-review view, mechanism HELD Phase 7-8) | PROPOSED |
| FL10.7.1 | F10.7.1 | Reviewer (different chat) | Work submitted | Independent + adversarial review; verdict recorded; no self-PASS | — (planned review view, mechanism HELD Phase 7-8) | PROPOSED |
| FL5.1.1 | F5.1.1 | User | Profile creation/migration requested | Scope preview; conflicts held not merged; source preserved until accepted | Account screens (E1 renders) | PROPOSED |
| FL5.2.1 | F5.2.1 | Operator/system | Sensitive action requested | Tuple evaluated; allow/deny/hold + reason | — (API surface) | PROPOSED |
| FL5.2.2 | F5.2.2 | Operator | Self-approval attempt on own change | Blocked incompatible pair; visible HELD + escalation | — (API surface) | PROPOSED |
| FL5.3.1 | F5.3.1 | Operator | Privileged login / high-consequence action | Phishing-resistant auth + fresh step-up; session bounded | Login/step-up screens (E1 renders per C1.1/C1.3; E2 privileged view planned HELD) | PROPOSED |
| FL5.3.2 | F5.3.2 | Security task | Suspected compromise | Identity-plane sweep; E3 F3.5.2 called for runtime edges | — (API surface) | PROPOSED |
| FL5.4.1 | F5.4.1 | Recovery actor | Recovery requested | Sessions revoked, fresh auth; no approval/publish/grant | Recovery screens (E1 renders; E2 privileged view planned HELD) | PROPOSED |
| FL5.5.1 | F5.5.1 | System (commit path) | High-consequence effect commits | Protected event first; else AUDIT_HELD; Acil istisna karantinalı/bilinmiyor; NO_EFFECT/ABORTED vs OUTCOME_UNKNOWN kapanışları | — (API surface) | PROPOSED |
| FL5.5.2 | F5.5.2 | Investigator | Audit question | Chain reconstructed (E5 custody read); access itself audited | Audit view (E2 renders per C2.11) | PROPOSED |
| FL5.5.3 | F5.5.3 | Audit task | Retention/redaction/policy-admin change | Change itself audited with before/after meaning; custody re-verified | — (API surface) | PROPOSED |
| FL5.6.1 | F5.6.1 | Operator | File/URL submitted | Quarantine states (E5 policy); enforcement in E3 F3.2.3; isolated preview | Quarantine view (E2 renders per C2.4) | PROPOSED |
| FL5.6.2 | F5.6.2 | Operator | Export requested | Preview + minimization; disclosure non-retractable | Export dialog (E1 renders per C1.6; E2 bulk view planned HELD) | PROPOSED |
| FL5.6.3 | F5.6.3 | System | Extraction produced | Proposal linked; never auto-approved; hostile inert | — (API surface) | PROPOSED |
| FL5.7.1 | F5.7.1 | Audit task | Activation evaluation requested | HELD with gap list; no open verdict from this feature | — (API surface) | PROPOSED |
| FL6.1.1 | F6.1.1 | Release task | New authority registered | Distinctness + non-collapse verified; missing staffing → HELD | — (API surface) | PROPOSED |
| FL6.2.1 | F6.2.1 | Operator | Publish candidate submitted | Preflight + guarded transition; states enumerated (HELD/FAILED/OUTCOME_UNKNOWN/PARTIAL_PROPAGATION/SUSPENDED/RECALL_OPEN…); idempotent result | Release view (E2 renders per C2.3) | PROPOSED |
| FL6.2.2 | F6.2.2 | Consumer client/system | Release evaluation | Current/superseded/suspended/recall resolved; stale rejected | — (client logic) | PROPOSED |
| FL6.3.1 | F6.3.1 | Emergency operator | Safety incident | Narrow negative hold; audit recorded; retrospective scheduled | Emergency view (E2 renders per C2.3) | PROPOSED |
| FL6.4.1 | F6.4.1 | Verification task | Artifact submitted | Digest-equal promotion check; rebuild/tag rejected; trust-root verified | — (API surface) | PROPOSED |
| FL6.5.1 | F6.5.1 | Operator | Config/flag/migration change | Release-treated with review; incompatible client held; suspension never cleared by config | Config view (E2 renders per C2.3) | PROPOSED |
| FL6.6.1 | F6.6.1 | Release task | Rollout/rollback/restore event | Staged states; stop never downgrades; quarantine on restore; monotonic generations | Rollout view (E2 renders per C2.3) | PROPOSED |
| FL6.7.1 | F6.7.1 | Incident task | Incident declared | Taxonomy + impact graph with protected copy; closure only on reconcile | Incident view (E2 renders per C2.3) | PROPOSED |
| FL6.8.1 | F6.8.1 | Release task | OTA proposal submitted | Denied by default + reason; future envelope listed (no native-replace/widen/merge) | — (API surface) | PROPOSED |
|---|---|---|---|---|---|---|
