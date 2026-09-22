# AI CODING PROTOCOL

Status: PROPOSED (Group 3, reviewed PASS 2026-09-21; enforced via review, not harness)

## Read-before-touch sequence

Pack reads → scope verify → dependency re-check → touch allowed files only.

## Stop conditions

Out-of-scope need, ambiguous requirement, failing gate, missing credential/approval — stop and move the task
to BLOCKED / change-request. Never silently expand scope.

## Per-task shared-blind-spot statement

Visible even when the same model fills multiple roles: what this task might miss and how the reviewer must
check it.

## Impersonation prohibition (verbatim)

AI never impersonates legal identity, store ownership, or qualified attestation.

## Change report and completion evidence

Files changed, tests run, evidence links, graph updates. Externals surface early in nontechnical language
with the exact required user/outside action (linked to T-E10-015).
