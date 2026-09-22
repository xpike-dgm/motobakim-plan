# MIGRATION POLICY

Status: PROPOSED (Group 5, review loop closed PASS 2026-09-21)

Migrations reference (never redefine) ADR-007 migration rules and ADR-003 publication/fencing rules:
staged-rollout fields + stop-never-downgrades; signing-alone-insufficient; same controlled path, otherwise
suspend + corrected release; still-trusted + compatible + applicable + non-revoked + non-recalled artifacts;
no binary restore; fenced precedence violations are fatal errors; quarantine with 4 reconciliations and no
positive serve; never erases the intervening record or cancels reach-back.

States, compatibility checks and forward-recovery ownership live with the executing epics (E6 T-E6-011/012,
E3 T-E3-023/026/027); this policy constrains, never operates. Destructive/irreversible changes invoke Group-4
tier re-invocation (higher assurance) plus owner approval per Protocol/DEC-0030. No numeric windows, no
tool/vendor/CI selection, no account/key/purchase/code/deployment.
