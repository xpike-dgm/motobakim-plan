# ACCEPTANCE MATRIX

Status: PROPOSED (Step 5 three-lane traceability merged 2026-09-21 + gap-closure rows; orphans: none; all gaps closed except explicit HELD-by-design)

Schema: Requirement / Rule | Covered By Feature | Covered By Flow | Covered By Task | Validation Method.
Validation vocabulary: review (independent AI review), test (specified-but-unrun test), gate (HELD-acceptance
evaluation), simulation (no-code sim set). No test is EXECUTED phase-wide by design (no code in Phase 6);
`test` in this column means a specified test awaiting execution. Behavior proof is HELD-gate until then.

## E1 — Consumer app (render only; enforcement cross-lane)

Validation for rows in this section: see § Validation assignment (review/simulation/gate lists below); per-row
NONE = governed-by-assignment, not unassigned. (Reconciled 2026-09-21 per re-audit.)

## E1 — Consumer app (render only; enforcement cross-lane)

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| BR-105/Q-0041/SCR-001+002: first value before account, add bike | F1.1.1 | FL1.1.1 | T-E1-003 | NONE |
| BR-106/107/Q-0038/0045/SCR-005-shell: TR units, contrast/captions, no profile prerequisite | F1.0.1 | FL1.0.1, FL1.0.2 | T-E1-001, T-E1-002 | NONE |
| BR-001/002/003/050/051/Q-0002/SCR-003+004: variant distinction, unresolved fit blocks | F1.1.2 | FL1.1.2 | T-E1-004 | NONE |
| BR-009/010/036/081/082/083/Q-0006/0018/0030/SCR-009..012: fit/readiness gate + recheck | F1.2.1 | FL1.2.1 | T-E1-005a, T-E1-005b | NONE |
| SCR-013/BR-084: teaching-only labeled, never active instruction | F1.2.1 | FL1.2.1 | T-E1-005c | NONE |
| BR-011/012/013/019/SCR-014+015: single objective, safety first, no ignore-and-continue | F1.3.1 | FL1.3.1 | T-E1-006 | NONE |
| BR-149/Q-0054/0059/SCR-016: resume needs revalidation, saved≠proof | F1.3.1 | FL1.3.2 | T-E1-007 | NONE |
| BR-148/021/Q-0053/0058/SCR-017: guide change forces stop + remap | F1.3.1 | FL1.3.3 | T-E1-008 | NONE |
| BR-022/SCR-018: truthful partial/safe-closure, not paywalled | F1.3.1 | FL1.3.1 | T-E1-006 | NONE |
| BR-015/016/017/040/041/042/Q-0011/0017/SCR-019..021: evidence-narrowed diagnosis, unresolved allowed | F1.4.1 | FL1.4.1 | T-E1-009 | NONE |
| BR-024/025/026/Q-0008/SCR-022+023: verified intervals only, postpone≠completion | F1.5.1 | FL1.5.1 | T-E1-010 | NONE |
| BR-055/056/095/096/097/Q-0034/SCR-024: alerts visible, catch-up summary | F1.5.1 | FL1.5.1 | T-E1-010 | NONE |
| BR-057/059/093/094/114-116/144-146/Q-0009/0033/0042/SCR-025+026: history meaning + provenance trail | F1.6.1 | FL1.6.1 | T-E1-011 | NONE |
| BR-150/Q-0055/SCR-027+028: standalone preserved, no silent winner | F1.6.1 | FL1.6.2 | T-E1-012 | NONE |
| BR-140/Q-0061/SCR-029: reach-back by severity, survives inactive | F1.6.1 | FL1.6.3 | T-E1-013 | NONE |
| BR-078/113/Q-0028/SCR-030: export with provenance, never premium | F1.6.1 | FL1.6.1 | T-E1-011 | NONE |
| BR-103/111/117/118/136/137/Q-0039/0043/0065/SCR-008+031..033: archive≠delete, gaps visible | F1.7.1 | FL1.7.1 | T-E1-014a | NONE |
| Q-0065/0067/0068/SCR-037/BR-048: entitlement gates render, enforcement server-side | F1.7.1 | FL1.7.1 | T-E1-014b | NONE |
| BR-101/141/142/143/147/Q-0037/0052/0063/SCR-006+007+034: no-coercion, no silent loss, revoke keeps history | F1.8.1 | FL1.8.1 | T-E1-015 | NONE |
| BR-065..067/069/089..092/Q-0021/0032/SCR-035+036+038: opt-in community, status/appeal paths | F1.9.1 | FL1.9.1 | T-E1-016 | NONE |
| DEC-0018/A1: 1 context + 1 prompt + 2 paths only | F1.10.1 | FL1.10.1 | T-E1-017 | NONE |
| SCR-005 narrowing: Garaj = context only, no dashboard hub | F1.0.1 | FL1.0.1, FL1.0.2 | T-E1-001, T-E1-002 | NONE |
| BR-124/125/104/Q-0040/0044: stale-critical blocks app, teaching/history stay | F1.3.1, F1.5.1 | FL1.3.1, FL1.5.1 | T-E1-006, T-E1-010 | NONE |
| BR-134/135/045/Q-0047: per-bike isolation | F1.0.1, F1.7.1 | FL1.0.2, FL1.7.1 | T-E1-002, T-E1-014a | NONE |
| BR-126/127/Q-0045: active-repair a11y never drops safety | F1.0.1, F1.3.1 | FL1.0.1, FL1.3.1 | T-E1-001, T-E1-006 | NONE |

## E2 — Internal panel (browser view; truth cross-lane)

Validation for rows in this section: see § Validation assignment (review/simulation/gate lists below); per-row
NONE = governed-by-assignment, not unassigned. (Reconciled 2026-09-21 per re-audit.)

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| IDCO-RQ-063/064: dense workspace, a11y, no entitlement hiding | F2.1.1 | FL2.1.1 | T-E2-001 | NONE |
| IDCO-RQ-025..031: review queues, partial approval, independence | F2.2.1 | FL2.2.1, FL2.2.2 | T-E2-002, T-E2-003 | NONE |
| IDCO-RQ-032..037: approval snapshot + fenced publish, failed shown failed | F2.3.1 | FL2.3.1 | T-E2-004 | NONE |
| IDCO-RQ-040..044: recall/suspension scope/reason/re-entry, history preserved | F2.3.1 | FL2.3.2 | T-E2-005 | NONE |
| IDCO-RQ-009..016: source/evidence separate, withdrawal re-evals | F2.4.1 | FL2.4.1 | T-E2-006 | NONE |
| IDCO-RQ-001..008: research queue, duplicate/uncertainty, gap ownership | F2.5.1 | FL2.5.1 | T-E2-007a | NONE |
| IDCO-RQ-052..058: coverage-vs-completeness, drill-down, no opaque score | F2.5.1 | FL2.5.1 | T-E2-007b | NONE |
| IDCO-RQ-048..051: least-privilege roles, separated powers, revoke preserves history | F2.6.1 | FL2.6.1 | T-E2-008 | NONE |
| IDCO-RQ-045..047: moderation reason + full audit fields | F2.7.1 | FL2.7.1 | T-E2-009 | NONE |
| IDCO-RQ-017..024: bounded draft, never-live, unknown allowed | F2.8.1 | FL2.8.1 | T-E2-010 | NONE |
| IDCO-RQ-002: variant fencing, matrix/duplicate/comparison | F2.9.1 | FL2.9.1 | T-E2-011 | NONE |
| IDCO-RQ-038/039: lineage, rollback as new event | F2.10.1 | FL2.10.1 | T-E2-012 | NONE |
| IDCO-RQ-045..047: audit-trail view fields | F2.11.1 | FL2.11.1 | T-E2-013 | NONE |

## E3 + E5 + E6 — Platform rules (ADR-numbered rows)

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| ADR-001 R1: one authority per domain | F3.2.1 | FL3.2.1 | T-E3-009 | review |
| ADR-001 R2: history never overwritten | F3.2.2 | FL3.2.2 | T-E3-010 | review |
| ADR-001 R3: fenced publishing control | F6.2.1 | FL6.2.1 | T-E6-003, T-E6-004, T-E6-005 | gate |
| ADR-001 R4: quarantine-first object boundary | F3.2.3, F5.6.1 | FL3.2.3, FL5.6.1 | T-E3-011, T-E3-012, T-E5-017, T-E5-018 | test |
| ADR-001 R5: integrity-bound phone package | NONE (E4 materializes) | NONE | NONE | HELD-acceptance |
| ADR-001 R6: convenience copies never authority | F3.2.2 | FL3.2.2 | T-E3-010 | review |
| ADR-002 R1: API mediation, no client authority | F3.1.1, F3.3.1 | FL3.1.1, FL3.3.1 | T-E3-001, T-E3-013, T-E3-014, T-E3-016 | test |
| ADR-002 R2: private quarantine before activation | F3.2.3 | FL3.2.3 | T-E3-011, T-E3-012 | test |
| ADR-002 R3: separate DB/object/audit/floor custody | F3.6.1 | FL3.6.1 | T-E3-026, T-E3-027 | gate |
| ADR-002 R4: stable IDs + clean-room export | F3.6.2 | FL3.6.2 | T-E3-028, T-E3-029 | review |
| ADR-002 R5: outage as held/unknown/unavailable | F3.1.3 | FL3.1.3 | T-E3-005, T-E3-005b | gate |
| ADR-002 R6: task-scoped AI, no secrets | F3.1.4 | FL3.1.4 | T-E3-008 | review |
| ADR-002 R7: dated changelog + compat hold | F3.3.2, F3.1.4 | FL3.1.4 | T-E3-018 | review |
| ADR-003 R1: approval binds exact snapshot | F6.2.1 | FL6.2.1 | T-E6-003 | review |
| ADR-003 R2: single guarded publish transition | F6.2.1 | FL6.2.1 | T-E6-004 | test |
| ADR-003 R3: explicit state model + branches | F6.2.1, F3.1.3 | FL6.2.1, FL3.1.3 | T-E6-005, T-E3-005, T-E3-005b | review |
| ADR-003 R4: fenced precedence, no backward gen | F3.5.1, F6.2.1 | FL3.5.1, FL6.2.1 | T-E3-023, T-E6-004 | test |
| ADR-003 R5: independent negative-only emergency plane | F6.3.1 | FL6.3.1 | T-E6-007a, T-E6-007b, T-E6-008 | simulation |
| ADR-003 R6: rollback as new event only | F6.6.1 | FL6.6.1 | T-E6-014 | gate |
| ADR-003 R7: restore quarantine, no positive serve | F3.6.1, F6.6.1 | FL3.6.1, FL6.6.1 | T-E3-026, T-E3-027, T-E6-014 | gate |
| ADR-003 R8: SoD author/reviewer/approver/publisher | F5.2.2, F6.1.1 | FL5.2.2, FL6.1.1 | T-E5-005, T-E5-006, T-E6-002 | gate |
| ADR-003 R9: evaluable consumer contract | F6.2.2 | FL6.2.2 | T-E6-006 | test |
| ADR-004 R1: server tuple allow/deny/hold | F5.2.1, F3.1.1 | FL5.2.1, FL3.1.1 | T-E5-003, T-E5-004, T-E3-001, T-E3-002 | test |
| ADR-004 R2: pairwise SoD per packet | F5.2.2 | FL5.2.2 | T-E5-005, T-E5-006 | gate |
| ADR-004 R3: phishing-resistant + step-up + bounded session | F5.3.1 | FL5.3.1 | T-E5-007a, T-E5-007b, T-E5-008 | test |
| ADR-004 R4: epoch revokes end-to-end | F5.3.2, F3.5.2 | FL5.3.2, FL3.5.2 | T-E5-009, T-E5-010, T-E3-024a, T-E3-024b, T-E3-025 | test |
| ADR-004 R5: recovery never approves/publishes/grants | F5.4.1 | FL5.4.1 | T-E5-011, T-E5-012 | gate |
| ADR-004 R6: protected audit before effect else AUDIT_HELD | F5.5.1 | FL5.5.1 | T-E5-013, T-E5-014 | gate |
| ADR-004 R7: quarantine ingestion chain | F5.6.1, F3.2.3 | FL5.6.1, FL3.2.3 | T-E5-017, T-E5-018, T-E3-011, T-E3-012 | test |
| ADR-004 R8: export as non-retractable disclosure | F5.6.2 | FL5.6.2 | T-E5-019 | review |
| ADR-004 R9: AI/OCR proposal-only | F5.6.3 | FL5.6.3 | T-E5-020 | review |
| ADR-004 R10: 11-item activation gate, second-human HELD | F5.7.1 | FL5.7.1 | T-E5-021 | HELD-acceptance |
| ADR-005 R1: full event coverage list | F5.5.1 | FL5.5.1, FL5.5.3 | T-E5-016a | review |
| ADR-005 R2: minimum event meaning | F5.5.1 | FL5.5.3 | T-E5-016a | review |
| ADR-005 R3: receipt bound before effect | F5.5.1 | FL5.5.1 | T-E5-014 | test |
| ADR-005 R4: fallback buffer, else HELD/quarantined | F5.5.1 | FL5.5.1 | T-E5-013, T-E5-014 | gate |
| ADR-005 R5: append-only + gap/fork/replay + alerts | F5.5.1 | FL5.5.1 | T-E5-014 | test |
| ADR-005 R6: explicit retention/legal-hold/redaction | F5.5.3 | FL5.5.3 | T-E5-016b | HELD-acceptance |
| ADR-005 R7: object-centered investigation chain | F5.5.2 | FL5.5.2, FL3.2.2 | T-E5-015 | review |
| ADR-005 R8: audit admin separated from publisher | F5.5.1, F5.5.3 | FL5.5.3 | T-E5-016b | review |
| ADR-006 R1: ephemeral runtime, listed durable state | F3.1.1 | FL3.1.1 | T-E3-034 | review |
| ADR-006 R2: full commit-time auth tuple | F3.1.1 | FL3.1.1 | T-E3-001, T-E3-002 | test |
| ADR-006 R3: DB core binds intent, effects separate | F3.1.2 | FL3.1.2 | T-E3-035 | review |
| ADR-006 R4: idempotency CONFLICT/HELD/DENIED | F3.1.2 | FL3.1.2 | T-E3-003, T-E3-004 | test |
| ADR-006 R5: durable long-job gate, no sync jobs | F3.4.1 | FL3.4.1 | T-E3-019, T-E3-020, T-E3-020b, T-E3-021, T-E3-022 | test |
| ADR-006 R6: monotonic negatives, ties hold | F3.5.1 | FL3.5.1 | T-E3-023 | test |
| ADR-006 R7: end-to-end epoch to all edges | F3.5.2 | FL3.5.2 | T-E3-024a, T-E3-024b, T-E3-025 | test |
| ADR-006 R8: shared state dictionary verbatim | F3.1.3 | FL3.1.3 | T-E3-005, T-E3-005b | review |
| ADR-006 R9: direct-path inventory + negative tests | F3.1.4 | FL3.1.4 | T-E3-006a, T-E3-006b, T-E3-006c, T-E3-007 | test |
| ADR-006 R10: equal-evidence A/B transition only | F3.3.1 | FL3.3.1 | T-E3-036 | HELD-acceptance |
| ADR-006 R11: owner/support/AI bounds + classified BOM | F3.7.1 | FL3.7.1 | T-E3-030, T-E3-031 | HELD-acceptance |
| ADR-007 R1: 8 distinct release authorities | F6.1.1, F3.8.1 | FL6.1.1, FL3.8.1 | T-E6-001, T-E6-002, T-E3-032, T-E3-033 | review |
| ADR-007 R2: immutable artifact + digest-bound provenance | F6.4.1 | FL6.4.1 | T-E6-009 | review |
| ADR-007 R3: promote exact artifact, no rebuild | F6.4.1, F3.8.1 | FL6.4.1, FL3.8.1 | T-E6-009, T-E3-033 | gate |
| ADR-007 R4: independent verifier + trust-root | F6.4.1 | FL6.4.1 | T-E6-009, T-E6-010 | review |
| ADR-007 R5: scoped dual-controlled key custody | F6.4.1 | FL6.4.1 | T-E6-010 | gate |
| ADR-007 R6: no role collapse, missing staff holds | F6.1.1 | FL6.1.1 | T-E6-002 | gate |
| ADR-007 R7: config/flag/migration as release | F6.5.1 | FL6.5.1 | T-E6-011, T-E6-012 | review |
| ADR-007 R8: staged rollout, rollback new event | F6.6.1 | FL6.6.1 | T-E6-013, T-E6-014 | gate |
| ADR-007 R9: incident impact graph + protected copy | F6.7.1 | FL6.7.1 | T-E6-015, T-E6-016 | review |
| ADR-007 R10: OTA denied by default | F6.8.1 | FL6.8.1 | T-E6-017 | gate |

## E4 + E9 + E7 + E8 + Cross-cutting

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| ADR-009 R1: verified compact core, safety media nested never additive | F4.1.1 | FL4.1.1 | T-E4-001, T-E4-002 | review |
| ADR-009 R1b: nonessential media separate/explicit/cancelable/evictable, size shown | F4.1.1, F4.1.2 | FL4.1.1, FL4.1.2 | T-E4-003, T-E4-004 | review |
| ADR-009 R2: stage-verify-promote atomic; delta falls back | F4.2.1 | FL4.2.1 | T-E4-005, T-E4-006 | review |
| ADR-009 R3 + CON-005: required-core auto-transfer, no dialog, priority, completion≠authority | F4.3.1 | FL4.3.1 | T-E4-007, T-E4-008 | review |
| ADR-009 R4: ordered eviction + 6-class never-evict + hold-transfer | F4.4.1 | FL4.4.1 | T-E4-009a, T-E4-009b, T-E4-010 | review |
| ADR-009 R5: durable ledger, E3 submit/lookup, anti-resurrection + quarantine | F4.5.1 | FL4.5.1 | T-E4-011a, T-E4-011b, T-E4-012 | review |
| ADR-009 R6: fail-closed inherited, recovery closure, Internal-Ops online-only | F4.6.1 | FL4.6.1 | T-E4-013, T-E4-014 | review |
| ADR-009 R7: encryption HELD, plaintext prohibited at gate | F4.7.1 | FL4.7.1 | T-E4-015 | gate |
| ADR-009 R8 + TSQ-009-HELD: points stay HELD TEST POINTS | F4.8.1 | FL4.8.1 | T-E4-016 | gate |
| CON-005: confirmation-free required transfer | F4.3.1 | FL4.3.1 | T-E4-007, T-E4-008 | review |
| Q-0029/0039/0040/0044: offline baseline, selective transfer, stale re-check | F4.6.1, F4.1.2 | FL4.6.1, FL4.1.2 | T-E4-013, T-E4-003 | review |
| TSQ-003-narrow: exact taxonomy/windows | F4.6.1 | FL4.6.1 | T-E4-013, T-E4-014 | gate |
| TSQ-012-narrow: exact encryption/key/versions/device proof | F4.7.1, F4.8.1 | FL4.7.1, FL4.8.1 | T-E4-015, T-E4-016 | gate |
| ADR-014 R1: 5-option proposal + 6-dimension verify (E9 proposes, E3 verifies, E1 renders) | F9.1.1 | FL9.1.1 | T-E9-001, T-E9-002 | review |
| ADR-014 R2 + TSQ-018-narrow: economy skeleton; provider/model HELD | F9.2.1 | FL9.2.1 | T-E9-003 | gate |
| ADR-014 R3: adapters; change triggers re-evaluation | F9.3.1 | FL9.3.1 | T-E9-004, T-E9-005 | review |
| ADR-014 R4: least-privilege tools + cost visibility + non-AI continuation | F9.4.1 | FL9.4.1 | T-E9-006, T-E9-007 | review |
| ADR-014 R5: allowed-10 verbatim | F9.5.1 | FL9.5.1 | T-E9-008 | review |
| ADR-014 R6: never-15 verbatim + HOLD-on-ambiguity | F9.6.1 | FL9.6.1 | T-E9-009, T-E9-010 | review |
| ADR-014 R7: project AI discipline + externals notice (ref F10.7.1) | F9.7.1 | FL9.7.1 | T-E9-011 | review |
| CON-001: fit-specific info, generic never bike-specific | F9.1.1 | FL9.1.1 | T-E9-002 | review |
| CON-002: no fabricated values | F9.6.1 | FL9.6.1 | T-E9-009, T-E9-010 | review |
| CON-003: risk/safety warnings never hidden | F4.1.1, F9.6.1 | FL4.1.1, FL9.6.1 | T-E4-001, T-E9-009 | review |
| ADR-013 R1: Android continuity checklist, execution-only | F7.1.1 | FL7.1.1 | T-E7-001, T-E7-002 | review |
| ADR-013 R2 + TSQ-008-narrow: iOS 5-proof gate, no commitment | F7.2.1 | FL7.2.1 | T-E7-003a, T-E7-003b, T-E7-003c | gate |
| ADR-013 R3: separation of powers; provider never owns | F7.3.1 | FL7.3.1 | T-E7-004, T-E7-005 | review |
| ADR-013 R4: classification lists kept current | F7.4.1 | FL7.4.1 | T-E7-006 | review |
| ADR-013 R5: spend read-only vs TRY context, fees separate | F7.5.1 | FL7.5.1 | T-E7-007 | gate |
| ADR-008 R3: Android-first rebuild on owner hardware | F7.1.1 | FL7.1.1 | T-E7-001 | gate |
| ADR-008 R5: no-owner-debug build recovery | F7.2.1, F7.3.1 | FL7.2.1, FL7.3.1 | T-E7-003b, T-E7-004 | gate |
| ADR-011 R1: Kavriva owns 8-noun authority (reference-only) | F8.1.1 | FL8.1.1 | T-E8-001 | review |
| ADR-011 R3: 6-vector bypass blocked | F8.1.1 | FL8.1.1 | T-E8-002 | review |
| ADR-011 R4: projections rebuildable non-authoritative | F8.1.1 | FL8.1.1 | T-E8-003 | review |
| ADR-011 R2: CMS authoring-only, boundedness gate | F8.2.1 | FL8.2.1 | T-E8-004 | review |
| ADR-011 R5 + TSQ-016-narrow: removability proofs; no first-release CMS | F8.2.1 | FL8.2.1 | T-E8-005a | gate |
| ADR-011 R6: reconsideration only on measured burden | F8.2.1 | FL8.2.1 | T-E8-005b | gate |
| ADR-012 R1: plane split, metrics from records | F8.3.1 | FL8.3.1 | T-E8-006 | review |
| ADR-012 R2+R3: exclusion verbatim + purpose/retention; outage independence | F8.4.1 | FL8.4.1 | T-E8-007, T-E8-008 | review |
| ADR-012 R4: capability bands + outage-independence pass | F8.5.1 | FL8.5.1 | T-E8-009, T-E8-010 | review |
| ADR-012 R5 + TSQ-017-narrow: 5-gate fallback without weakening | F8.6.1 | FL8.6.1 | T-E8-011 | gate |
| ADR-012 R6: exit honesty, export≠proof, portability HELD | F8.6.1 | FL8.6.1 | T-E8-012 | gate |
| ADR-015 R1: capsule rule, minimum change surface | F10.2.1 | FL10.2.1 | T-E10-004 | review |
| ADR-015 R2: repo topology, governed addresses, no orphans | F10.2.1 | FL10.2.1 | T-E10-006 | review |
| ADR-015 R3: graph identity/metadata + 7 detectors | F10.1.1 | FL10.1.1 | T-E10-001, T-E10-002, T-E10-003a, T-E10-003b | review |
| ADR-015 R4: toward-stability direction, no silent imports | F10.2.1 | FL10.2.1 | T-E10-005 | review |
| ADR-015 R5: 14-field pack minimum + registry states | F10.3.1 | FL10.3.1, FL10.3.2 | T-E10-007, T-E10-008 | review |
| ADR-015 R6: 10 closure layers + audits | F10.4.1 | FL10.4.1 | T-E10-009, T-E10-010 | review |
| ADR-015 R7: simulation scenarios + excess-work scan | F10.5.1 | FL10.5.1 | T-E10-011a, T-E10-011b, T-E10-012 | simulation |
| ADR-015 R8: design gate + regression evidence | F10.6.1 | FL10.6.1 | T-E10-013, T-E10-014 | review |
| ADR-015 R9: role separation + parallel-output guards | F10.7.1 | FL10.7.1 | T-E10-015, T-E10-016 | review |
| ADR-015 R9b + ADR-010 R3: owner never repairs technical systems | F10.7.1 | FL10.7.1 | T-E10-015 | review |
| Q-0038/Q-0045 + ADR-010 R3/R4: Turkish/units/a11y baseline | F10.6.1 | FL10.6.1 | T-E10-013, T-E10-014 | review |

## HELD-acceptance rows (deliberately no plan side yet)

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| CON-004: beginner-comprehensible guide copy, verified at F10.6.1 design gate | F1.2.1/F1.3.1/F1.4.1/F1.5.1 | FL1.2.1/FL1.3.1/FL1.4.1/FL1.5.1 | T-E1-005a/b/c, T-E1-006/007/008/009/010 | review |
| Q-0046/BR-131..133: necessity-to-understand/prove test + inviolability (Q156 core, Q157 expanded) | F4.9.1 | FL4.9.1 | T-E4-017 | review |
| IDCO-RQ-060/061/062: failed states inspectable + recoverable + resolver; unsaved/partial distinguished; four-part explanation | F2.12.1 | FL2.12.1 | T-E2-016 | review |
| ADR-008 R6: real-device proof (simulators never substitute) | NONE (HELD by design; authority: ADR-008 R6 + DEC-0054 no-device-proof rule) | NONE | NONE | HELD |
| ENTITLEMENT SET Q-0020/0026/0046/0047/0065–0069 + DEC-0053: 1 bike free, paid slots, subscription → 3, full guide for 1 selected bike (moves, never stacks); prices/packages/switch-rules HELD | F1.7.1 | FL1.7.1 | T-E1-014a, T-E1-014b (+ server checks E3/E5) | gate |
| TSQ-001-narrow: Flutter/Dart channels, plugin allowlist, device/OS matrix | NONE (HELD by design; authority: DEC-0054 + ADR-008 revisit triggers) | NONE | NONE | HELD |

## Gap-closure additions (2026-09-21, all review PASS)

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| BR-063/064: duration-as-range + cost-split with exclusions/date/assumptions, no fabrication | F1.2.2 | FL1.2.2 | T-E1-018, T-E1-019a, T-E1-019b | review |
| BR-070/071/073: sponsored marked, listing never substitutes guide, no sales-target manipulation, fit-first | F1.9.2 | FL1.9.2 | T-E1-020, T-E1-021 | review |
| BR-074: user-invoked roadside mode, condensed steps, uncertainty persistent | F1.3.2 | FL1.3.4 | T-E1-022a, T-E1-022b | review |
| OPEN safe-closure criteria: per-category content (expert + second review), E3-verified, E1-rendered | F1.3.3 | FL1.3.5 | T-E1-023, T-E1-024 | gate |
| Q-0066/Q222/Q227: pre-step correction + MAY-open renewal per server decision, window HELD | F1.7.1 | FL1.7.2 | T-E1-025 | gate |

## Gap-closure additions 2 (2026-09-23, OUT-1 B-04 — pending independent review)

Six tasks had no matrix row (orphan-trace gap against the Step-5 "none" claim corrected below):

| Requirement / Rule | Feature | Flow | Task | Validation |
|---|---|---|---|---|
| SCR-036/C2.7: contributor status surfacing + repair paths | F2.7.1 | FL2.7.1 | T-E2-014 | simulation |
| Q-0049/0050: withdrawal re-review owner trigger | F2.7.1 | FL2.7.1 | T-E2-015 | simulation |
| ADR-002 cost paragraph: platform BOM inputs template | F3.3.1 | FL3.3.1 | T-E3-015 | review |
| ADR-002 Option A + Decision 1: secret custody + rotation rules | F3.3.2 | FL3.3.2 | T-E3-017 | gate |
| ADR-004 identity: account-light start procedure | F5.1.1 | FL5.1.1 | T-E5-001 | review |
| ADR-004 migration: profile migration preview + conflict hold | F5.1.1 | FL5.1.1 | T-E5-002 | review |

## Step 5 Findings (merged three lanes, 2026-09-21)

- ORPHAN TASKS: none in any lane (Step-5 claim) — CORRECTED 2026-09-23: OUT-1 B-04 proved 6 untraced tasks
  (T-E2-014, T-E2-015, T-E3-015, T-E3-017, T-E5-001, T-E5-002); mapped in "Gap-closure additions 2" above, pending
  independent review. Step-5 history preserved; this line records the correction, not an erasure.
- COVERAGE GAPS (content, not just validation): ALL CLOSED 2026-09-21 — estimates/commerce/roadside/closure/Q-0066 via E1 gap rows; media rule via F4.9.1 row above; RQ-060..062 via F2.12.1 row above; CON-004 via guide-task wording + F10.6.1 gate. Remaining: ADR-008 R6 device proof + TSQ-001-narrow (HELD by design, implementation evidence). Validation column is `NONE` phase-wide for E1/E2 (no review PASS recorded there) and `test` is absent phase-wide by design.
- CONFLICTS: none irreconcilable. Four managed tensions recorded with precedence (data-efficiency vs safety-closure: safety wins; cheapest-model vs safety: HOLD wins; Android-first vs iOS parity: conditional containment; CON-005 vs cost controls: never a user gate). The open entitlement tension is RESOLVED under `DEC-0053` (1 bike free, paid slots, subscription raises to 3, full guide for 1 selected bike; prices/packages HELD).
- CROSS-LANE NEEDS: resolved by construction — every cross-lane pointer in the matrix names an existing row in another lane (server auth, truth/history, package materialization, AI propose/verify/render split, E2 consume-only, E6 decide-only). No dangling cross-lane reference found.
- NEXT: Step 6 no-code simulation (dependency order, collision, failure/rollback, removal-gap, all-DONE re-evaluation), then Gate 6 -> 7 readiness audit.

## Validation assignment — E1/E2 rows (2026-09-21, no `test` anywhere: Phase 6 has no code)

- REVIEW features (15): F1.0.1, F1.1.1, F1.1.2, F1.2.1, F1.2.2, F1.5.1, F1.8.1, F1.9.1, F1.9.2, F1.10.1, F2.1.1, F2.4.1, F2.8.1, F2.9.1, F2.10.1.
- SIMULATION features (10): F1.3.1, F1.3.2, F1.4.1, F1.6.1, F2.2.1, F2.3.1, F2.5.1, F2.7.1, F2.11.1, F2.12.1.
- GATE features (3): F1.7.1, F1.3.3, F2.6.1. (28 = E1 16 + E2 12.)
- REVIEW flows (16): FL1.0.1, FL1.0.2, FL1.1.1, FL1.1.2, FL1.2.1, FL1.2.2, FL1.5.1, FL1.8.1, FL1.9.1, FL1.9.2, FL1.10.1, FL2.1.1, FL2.4.1, FL2.8.1, FL2.9.1, FL2.10.1.
- SIMULATION flows (16): FL1.3.1, FL1.3.2, FL1.3.3, FL1.3.4, FL1.4.1, FL1.6.1, FL1.6.2, FL1.6.3, FL2.2.1, FL2.2.2, FL2.3.1, FL2.3.2, FL2.5.1, FL2.7.1, FL2.11.1, FL2.12.1.
- GATE flows (4): FL1.7.1, FL1.7.2, FL1.3.5, FL2.6.1. (36 = E1 22 + E2 14.)
- REVIEW tasks (23): T-E1-001,002,003,004,005a,005b,005c,010,015,016,017,018,019a,019b,020,021,022a,022b; T-E2-001,002,006,010,011.
- SIMULATION tasks (17): T-E1-006,007,008,009,011,012,013; T-E2-003,004,005,007a,007b,009,012,014,015,016.
- GATE tasks (7): T-E1-014a,014b,023,024,025; T-E2-008,013. (47 = E1 30 + E2 17.)
