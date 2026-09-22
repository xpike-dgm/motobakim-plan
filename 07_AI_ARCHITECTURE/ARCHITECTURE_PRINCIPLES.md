# ARCHITECTURE PRINCIPLES

Status: PROPOSED (Group 1, reviewed PASS 2026-09-21; architecture tests in Group 4 will enforce these)

1. Contract-governed capsules: every part owns purpose, public contract surface, internal scope, allowed/forbidden
   dependencies, tests, change/rollback rules and requirement/design/task/test links.
2. Minimum change surface with explicit ownership and narrow contracts beats file-count fragmentation.
   Over-fragmentation into dependency spaghetti is failure; small files are not the goal.
3. Product truth flows one way: product truth → contracts → capsules → tasks. Nothing flows upward silently.
4. No orphan artifacts: everything resolves to at least one purpose/ownership/module/task link (small files via
   manifests, path indexes and task evidence — never per-file bureaucracy without assurance).
5. Planning truth and implementation truth stay linked through stable identities; history is never rewritten,
   only superseded with preserved text.
6. No fixed AI is load-bearing: registry → pack → work → evidence → review → registry update runs on written
   instructions alone (DEC-0028/0029/0051/0052/0056).
