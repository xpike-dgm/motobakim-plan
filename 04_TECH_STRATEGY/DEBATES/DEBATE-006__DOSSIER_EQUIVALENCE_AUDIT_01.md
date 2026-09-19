# DEBATE-006 — DOSSIER EQUIVALENCE AUDIT 01

Status: `REVIEW COMPLETE / CORRECTIONS INCORPORATED / RECHECK PASSED FOR FIRST FOUR DOSSIERS`
Date: 2026-09-18
Scope: Flutter, React Native + Expo development builds, KMP-native
Reviewer: independent Luna Max read-only audit

## Result

No critical finding, invented framework score, unapproved price or shared-system work misattributed as a framework
benefit was found. All three drafts contained S1–S15 and recorded `0 PASS / 15 HELD / 0 REJECT`.

## Blocking Major Findings and Disposition

1. KMP-native omitted the frozen monthly workload arithmetic and incorrectly treated frequency as unresolved.
   - Corrected: restored two compact transfers/MAU/month, 10% optional 100 MB media use, 0.5 photos/MAU/month at 3 MB,
     plus the 1,000/10,000/50,000 MAU arithmetic.
2. Flutter and KMP-native did not explicitly enumerate all four frozen device cohorts.
   - Corrected: constrained Android, main Android, oldest supported-end iPhone and current standard iPhone are now
     explicit; later device evidence means all four.
3. Flutter compressed the controlled TCO columns and lost separate cost dimensions.
   - Corrected: the table now uses product-wide, candidate-caused, optional, scale-triggered, exit/contingency,
     free/capped path and amount/confidence columns.

## Minor Findings and Disposition

- React Native/Expo OTA row normalized from `REJECT (excluded path)` to `EXCLUDED / N-A`; S1–S15 result is unchanged.
- React Native/Expo FileSystem and SecureStore citations pinned from dynamic `latest` URLs to SDK 57 URLs.
- Flutter field-label normalization remains a deterministic-format cleanup before final judge synthesis; it does not
  change content or result.
- Line count is not evidence quality. Final comparison must use controlled fields, not dossier length.

## Recheck Result

- Flutter — `PASS` after major corrections.
- React Native/Expo — `PASS` after citation/OTA normalization.
- KMP-native — `PASS` after workload/device corrections.
- KMP-Compose — recheck initially found one blocking four-cohort omission; it was corrected in identity, global
  device-evidence rule and fixed-input repetition. No remaining blocking drift was reported for workload, TCO schema,
  S1–S15, accessibility, pricing or KMP-native separation.
- Full-native — final audit found one blocking ambiguity in later `both devices/platforms` language. A global rule now
  binds every such reference to all four cohorts. Monthly photo wording and accessibility-column mapping were normalized.

## Proceed Boundary

All five corrected drafts may proceed to independent five-way critique and judge synthesis. Every dossier remains
documentary, unselected and `HELD`; equivalence readiness is not a framework recommendation or ADR.

No technology ranking or recommendation is made.
