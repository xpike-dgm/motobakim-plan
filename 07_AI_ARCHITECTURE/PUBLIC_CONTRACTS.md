# PUBLIC CONTRACTS

Status: PROPOSED (Group 2, reviewed PASS 2026-09-21; detection implementation owned by Group 4)

Only declared surfaces cross module boundaries. Internal implementations (storage layout, caches, helpers,
in-flight state) are never public API, even when reachable. Every cross-boundary call cites a contract ID +
version; unlisted communication is a violation.

Gate detectability (pointer): orphans, broken links, forbidden dependencies, cycles, ownerless public contracts,
untested critical behavior, stale context packs. Classification/authority boundaries propagate across every edge.
Detection implementation is Group-4-owned (see `ARCHITECTURE_TESTS.md`, PROPOSED) — defined there, not here.
