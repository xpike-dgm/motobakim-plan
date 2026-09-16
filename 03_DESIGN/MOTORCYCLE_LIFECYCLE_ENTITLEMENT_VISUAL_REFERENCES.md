# KAVRIVA MOTORCYCLE LIFECYCLE / ENTITLEMENT VISUAL REFERENCES

Status: APPROVED WORKING VISUAL REFERENCE SET
Approved: 2026-09-17
Reference: `REF-LIFECYCLE-001`
Evidence: `KAVRIVA_MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUALS_01_HANDOFF.md`
Review: `KAVRIVA_MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUALS_REVIEW.md`

## Approval Boundary

J01–J05 are approved as working Phase-3 visual references for FAM-07 Motorcycle Lifecycle / Entitlement.

Approval covers hierarchy and product semantics for active/inactive switching, lifecycle actions, transfer scope, delete scope and preserved-access entitlement states. It does NOT finalize pricing/tier/quota, billing, legal retention, exact transfer permissions, backend/data architecture, routing/modality, production tokens or Gate 3 -> 4.

## Approved Working Set

- **J01 — SCR-008 Motorcycle Switch / Active-Inactive Management**: one active motorcycle; inactive context remains accessible; routine reminders may pause while history/evidence/corrections/export and critical safety reach-back remain available.
- **J02 — SCR-031 Motorcycle Lifecycle**: inactive/archive, transfer and delete remain distinct; destructive action is separated from history-preserving actions.
- **J03 — SCR-032 Transfer Scope & Coverage**: partial coverage is explicit; included history/evidence/provenance/corrections and gaps/exclusions are reviewable; transfer does not verify records.
- **J04 — SCR-033 Delete Scope & Warning**: affected user-owned scope is explained; independent/shared data boundaries remain protected; history-preserving inactive alternative is available; destructive confirmation is explicit.
- **J05 — SCR-037 New-Activity Entitlement Gate / Preserved Access**: accepted v3 is authority; relevant new activity may be blocked while existing history/evidence/provenance/correction/export/critical recovery stay open.

## Required Constraints

1. Inactive motorcycle != deleted motorcycle.
2. Inactive motorcycle != history, evidence, correction or export lock.
3. Routine reminders may pause for inactive motorcycles; critical historical safety/correction reach-back remains accessible.
4. Reactivation restores the same historical/evidence context and may require current mileage/use and physical-state revalidation.
5. Archive/inactive != transfer != delete.
6. Transfer partial coverage must not look complete.
7. Transfer or ownership change does not automatically validate records.
8. Delete must not silently erase independent data/evidence/provenance held by other actors.
9. J04 irreversibility wording is working UX; exact retention/backup/legal semantics remain later implementation/legal work.
10. Entitlement may gate relevant new routine activity but must not retroactively lock existing truth/safety/history/export/correction/dispute or required safe closure/recovery.
11. J05 v3 supersedes earlier J05 candidates within this family.
12. Exact price/tier/quota/subscription/billing is not decided.
13. Focused-flow bottom navigation and exact screen/sheet/modal mappings remain PROPOSED ONLY.
14. Exact copy/components/icons/tokens/dark mode/accessibility remain non-final.

## Visual QA Notes

The set preserves V10/L05A working visual DNA: near-white canvas, graphite/navy hierarchy, restrained blue, amber for consequential caution and restrained red only for final destructive deletion.

J05 was refined from a text-heavy first version. Accepted v3 reduces top-copy repetition and redistributes vertical rhythm without removing protected-access semantics.

## Image Provenance

The manager conversation received 887x1774 J01–J05 PNG uploads. Visual QA matched the accepted handoff set. Upload-container SHA-256 values can differ from delegated-session hashes due to binary transfer/re-encoding; therefore the delegated handoff and review file together preserve provenance rather than declaring a new production binary master.

## Next Mobile Family

FAM-08 — Profile / Collaboration (`SCR-006`, `SCR-007`, `SCR-034`).

After FAM-08: FAM-09 Community critical visuals, then remaining FAM-01 First Use / Motorcycle Context visual coverage before Gate 3 readiness.
