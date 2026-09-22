# VALIDATION STRATEGY

Status: PROPOSED (Group 4, reviewed PASS 2026-09-21; harness construction HELD for Phase 8)

Check classes: lint, typecheck, unit, integration, e2e, build, architecture check, design regression,
accessibility check, security scan. Consequence-tier mapping below is PROPOSED, anchored to existing lanes
(E1 render vs E3/E5/E6 privileged/server) and the Phase-6 E1/E2 validation assignment: render-only tasks use
lint + design regression; state/branch tasks add unit/integration; privileged/release/data-migration tasks use
the full set incl. security scan + independent review. No numeric gates, no tool/vendor choice; all checks are
SPECIFIED-not-executed until Development/CI.

Ownership: implementer runs, reviewer (different chat) verifies, gate enforces — reviewer = different chat,
narrow remediation, loop-until-PASS, agreement≠approval (DEC-0052/0056).
