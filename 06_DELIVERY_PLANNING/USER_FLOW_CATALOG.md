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
| FL4.1.1 | F4.1.1 | System | Package assembly requested | Verified core + nested safety media; manifest bound | — (API surface; generation owned by E3/E6 pipeline, E4 consumes) | PROPOSED |
| FL4.1.2 | F4.1.2 | User | Optional media requested | Size shown; explicit fetch; cancelable; evictable | — (client logic, surfaced via E1 — E1 screen HELD per Step 3) | PROPOSED |
| FL4.2.1 | F4.2.1 | System | Package update available | Verified promote or complete-package fallback; never partial | — (API surface; generation owned by E3/E6 pipeline, E4 consumes) | PROPOSED |
| FL4.3.1 | F4.3.1 | System | Task requires required-core content | Auto-start any network; no dialog; Saver may delay; completion≠authority | — (client logic, surfaced via E1 — E1 screen HELD per Step 3) | PROPOSED |
| FL4.4.1 | F4.4.1 | System | Storage pressure signal | Ordered eviction; protected truth intact; transfer held if needed | — (client logic, surfaced via E1 — E1 screen HELD per Step 3) | PROPOSED |
| FL4.5.1 | F4.5.1 | User/system | Offline work created | Persisted locally; submitted/looked-up via E3 API; E3 acceptance authoritative | History screens (E1 renders per C1.6) | PROPOSED |
| FL4.6.1 | F4.6.1 | System | Stale/unknown critical dependency | Fail closed inherited; safe-stop available; internal-ops online-only | — (client logic, surfaced via E1 — E1 screen HELD per Step 3) | PROPOSED |
| FL4.7.1 | F4.7.1 | Security task | Gate evaluated, mechanism HELD | Proven or held; plaintext blocked at gate | — (API surface; gate check, mechanism HELD) | PROPOSED |
| FL4.8.1 | F4.8.1 | Measurement task | HELD policy evaluated | No numbers selected; acceptance criterion noted | Owner-view (HELD) | PROPOSED |
| FL9.1.1 | F9.1.1 | User | Free-text symptom/task described | Clarify; bounded proposal; verification by E3, render by E1 | AI Usta screens (E1 renders per C1.10) | PROPOSED |
| FL9.2.1 | F9.2.1 | System | HELD policy evaluated (no numeric) | No model selected/logged | — (API surface) | PROPOSED |
| FL9.3.1 | F9.3.1 | Platform task | Provider/model changed | Adapter + revalidation; product logic untouched | — (API surface) | PROPOSED |
| FL9.4.1 | F9.4.1 | System | Tool call attempted | Authority check; bounded retry + cost visibility; safe continuation | — (API surface) | PROPOSED |
| FL9.5.1 | F9.5.1 | User/system | Ranking/summary requested | Only eligible ranked; verification by E3, render by E1 | AI Usta screens (E1 renders per C1.10) | PROPOSED |
| FL9.6.1 | F9.6.1 | System | Unsupported/risky request | HOLD with reason; verification by E3, render by E1; no invention | AI Usta screens (E1 renders per C1.10) | PROPOSED |
| FL9.7.1 | F9.7.1 | Reviewer (different chat) | High-impact AI work submitted | Independent review assigned; no self-PASS | — (planned review view, mechanism HELD Phase 7-8 per E10) | PROPOSED |
| FL1.0.1 | F1.0.1 | User | Tab switched mid-repair | Preservation objective; bottom-bar HELD, no behavior locked | SCR-005 + tabs | PROPOSED |
| FL1.0.2 | F1.0.1 | User | Garage opened/switched | Selected context displayed/switched; lifecycle entry; no dashboard hub | SCR-005/SCR-008 | PROPOSED |
| FL1.1.1 | F1.1.1 | New user | First launch | Value before account; bike added | SCR-001/002 screens | PROPOSED |
| FL1.1.2 | F1.1.2 | User | Ambiguous motorcycle | Variant clarified; fit or missing-distinction shown | SCR-003/004 screens | PROPOSED |
| FL1.2.1 | F1.2.1 | User | Task sought | Fit/readiness evaluated, never bypassed; SCR-013 teaching-only labeled | SCR-009..013 screens | PROPOSED |
| FL1.3.1 | F1.3.1 | User | Guide step executed | Truthful outcome incl. partial/unresolved/safe-stop; no continue-anyway | SCR-014..018 screens | PROPOSED |
| FL1.3.2 | F1.3.1 | User | Interrupted work resumed | Revalidated vs current state; saved progress is not proof | SCR-016 screens | PROPOSED |
| FL1.3.3 | F1.3.1 | User | Guide changed mid-repair | Remap required; no guessed continuation | SCR-017 screens | PROPOSED |
| FL1.4.1 | F1.4.1 | User | Symptom described | E9-routed check; supported or unresolved outcome | SCR-019..021 screens | PROPOSED |
| FL1.5.1 | F1.5.1 | User | Reminder due | Verified source shown; snooze≠completed; SCR-024 catch-up path | SCR-022..024 screens | PROPOSED |
| FL1.6.1 | F1.6.1 | User | History/export requested | Provenance shown; E5 authorizes, E3 serves, E1 renders; gates server-side | SCR-025..030 screens | PROPOSED |
| FL1.6.2 | F1.6.1 | User | Standalone record/dispute opened | SCR-027 preserved; SCR-028 reviewed, no-silent-winner | SCR-027/028 screens | PROPOSED |
| FL1.6.3 | F1.6.1 | User | Correction with impact issued | SCR-029 reach-back by severity; survives inactive/entitlement | SCR-029 screens | PROPOSED |
| FL1.7.1 | F1.7.1 | User | Lifecycle/entitlement event | Inactive/transfer/delete honored; gates server-side | SCR-008/031-033/037 screens | PROPOSED |
| FL1.8.1 | F1.8.1 | User | Migration/collaboration action | Scope preview; no silent loss; revocable attribution | SCR-006/007/034 screens | PROPOSED |
| FL1.9.1 | F1.9.1 | User | Community contribution/status check | Opt-in flows; status/repair paths; decisions in E2, acceptance≠verification | SCR-035/036/038 screens | PROPOSED |
| FL1.10.1 | F1.10.1 | User | AI Usta opened | A1 split only; routes SCR-009/019; no third path/composer; propose=E9 verify=E3 | AI Usta root screen | PROPOSED |
| FL2.1.1 | F2.1.1 | Operator | Workspace opened | Dense workspace + nav; a11y baseline active | — (planned shell view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.2.1 | F2.2.1 | Reviewer | Packet assigned | Evidence reviewed; independence checked; decision recorded | — (planned queue view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.2.2 | F2.2.1 | Reviewer | Conflict/gap detected | WS-05 conflict review with owner/reason/escalation | — (planned queue view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.3.1 | F2.3.1 | Operator | Release/recall action taken | Surface invokes; E6 authorizes/executes; display reconciled | — (planned ops view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.3.2 | F2.3.1 | Operator | Recall/suspension issued | WS-11 impact/reach-back case with scope, correction, re-entry | — (planned ops view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.4.1 | F2.4.1 | Operator | File/URL submitted | Quarantine + isolated preview; graph/withdrawal-impact + scope separation | — (planned quarantine view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.5.1 | F2.5.1 | Operator | Metrics checked | Record-derived metrics + drill-down; WS-01/WS-09; E3 owns, E8 derives, E2 shows | — (planned metrics view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.6.1 | F2.6.1 | Access admin | Grant/delegation/recertification action | Scoped change with approval; no self-grant path | — (planned access view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.7.1 | F2.7.1 | Moderator | Content flagged | Reasoned decision + audit; SCR-036 renders status; notify channel HELD | — (planned moderation view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.8.1 | F2.8.1 | Author | Draft created/edited | Bounded draft saved; never live without approval path | — (planned editor view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.9.1 | F2.9.1 | Operator | Scope rule changed | Variant fencing + matrix/duplicate/comparison; approved | — (planned scope view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.10.1 | F2.10.1 | Operator | Lineage queried | Version/derivation chain + rollback-candidate/correction links | — (planned lineage view, mechanism HELD Phase 7-8) | PROPOSED |
| FL2.11.1 | F2.11.1 | Investigator | Audit question | RQ-046 fields + RQ-047 separation; trail from E5 custody; access audited | — (planned audit view, mechanism HELD Phase 7-8) | PROPOSED |
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
