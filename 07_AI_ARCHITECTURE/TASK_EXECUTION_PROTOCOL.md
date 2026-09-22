# TASK EXECUTION PROTOCOL

Status: PROPOSED (Group 3, reviewed PASS 2026-09-21)

## Lifecycle states

READY → CLAIMED → IN_PROGRESS → REVIEW → DONE, with BLOCKED and CANCELLED branches, plus the
CHANGES_REQUESTED loop: CHANGES_REQUESTED → narrow remediation → different-chat re-review → REVIEW.
(Scaffold VALIDATING is a review-phase activity label, not a separate state.)
CANCELLED entry (owner cancels scope or scope superseded) and exit (records archived, dependents re-planned);
CHANGES_REQUESTED→REVIEW transitions defined above. No silent state skips.

Required context per pack standard; reviewer must be a different chat (DEC-0052/0041, five-guard parallel
safeguards: same frozen brief, separately-identified outputs, no overwrite, disagreement preserved,
agreement≠approval). High-impact work never self-PASSes.
