# DEBATE-001 — REVIEW A: ARCHITECTURE, MOBILE & SCALE

Status: `COMPLETE — PASS_WITH_CHANGES`
Date: 2026-09-17
Reviewer: independent adversarial AI, architecture/mobile/scale role
Repository edits by reviewer: none

Later user constraint: `DEC-0021` prohibits executing the prototype/spike ideas named in this historical review.
They survive only as no-code scenario and evidence requirements.

## Verdict

The strategy may continue in Phase 4, but it does not yet justify a mobile-framework selection or a physical
publication topology. The main web-first/separate-authority direction is reasonable after the changes below.

## Critical Finding

### A-C1 — Unsafe resume could pass the original experiment

The original `resume at exact progress offline` condition restored progress without explicitly requiring the
approved physical/safety-state revalidation. Recall was tested only after reconnection. That could pass while
violating `STATE_MATRIX`, `SCR-016`, `BR-104` and `BR-125`.

Required disposition:

- restore saved context, not automatic permission to continue;
- keep critical confirmations open until revalidated;
- test offline expiry without receiving a server event;
- preserve teaching/history/safe-recovery while closing unsafe application;
- use synthetic expiry values only to test mechanics, not to invent product thresholds.

Disposition: `ACCEPTED / INCORPORATED`.

## Major Findings

| ID | Finding | Disposition |
|---|---|---|
| `A-M1` | Numerical scores asserted unknown staffing/performance/implementation quality and assigned service-level security/publication qualities to client packaging. | Numerical rankings removed; evidence-limited qualitative tables used. |
| `A-M2` | KMP-native and shared Compose were one option; React Native/Expo envelope was undefined; fully native baseline absent. | Options split; RN envelope must be explicit; native pair added as reference baseline. |
| `A-M3` | “Required projection/read model” prematurely chose a physical data topology. | Reduced to logical trust boundary; transaction/version and projection alternatives move to separate debate. |
| `A-M4` | Publication tests omitted edit/withdrawal/recall races, old clients and active-work material changes. | Race, compatibility and material-change scenarios added. |
| `A-M5` | Spike list lacked common fixture, workload, device profiles, budget, measurements and stop criteria. | Comparable experiment contract added; Phase 4 authorizes specifications, not code. |

## Minor Findings

- Optional desktop shell is a web extension policy, not a separately scored option — incorporated.
- Strict separation of duties should test high-consequence changes without deciding low-risk staffing — incorporated.
- Central web release does not eliminate stale tabs/session/client cache — old-tab rejection test added.
- `no code` in Phase 4 conflicted with “build spikes” — corrected to experiment specification and later authorization.

## Sound Elements

- Framework selection remains provisional.
- Web-first Internal Operations is a reasonable reversible hypothesis.
- Desktop packaging depends on demonstrated local capability.
- Server-side permission/publication enforcement is mandatory.
- Editorial data, user history and application eligibility remain distinct.
- Framework/local database is not treated as a sync/recall solution.
- Real-device accessibility/lifecycle/interruption validation is retained.

## Required Falsification Scenarios

1. Restore context without unsafe continuation.
2. Expire application eligibility while fully offline.
3. Recall/version race with delayed messages.
4. Material guide change during active work.
5. Unsupported/older client safety semantics.
6. Conflicting migration while local use continues, including cancel/retry.
7. Comparable real-device/accessibility experiment with identical fixtures.

## Final Reviewer Position

`PASS_WITH_CHANGES`. Corrections must remain visible as obligations; they are not evidence that a framework or
publication architecture has passed.
