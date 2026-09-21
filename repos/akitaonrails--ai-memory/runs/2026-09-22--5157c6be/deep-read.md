# Deep Read Selection

Target: akitaonrails/ai-memory @ 5157c6be10b5830d7adc7e29b0a4358c3ecbe6a2
Inventory entries: 817

## High-signal artifacts inspected

1. README.md — product thesis, modes, integration matrix, retrieval overview.
2. docs/ARCHITECTURE.md — canonical data flow, invariants, lifecycle, retrieval, retention.
3. docs/design-decisions.md — source-of-truth choice, storage, capture, temporal tiers, handoff rationale.
4. docs/prior-art-implementation-findings.md — explicit lessons borrowed from peer memory systems.
5. docs/auto-improvement-loop.md — learning-review policy and proposal workflow.
6. docs/experience.md — cross-session experience layer.
7. docs/temporal.md — historical validity-window retrieval semantics.
8. docs/vector-backend-policy.md — vector storage/provider mismatch design.
9. DATA_HANDLING.md — outbound-data and retention posture.
10. SECURITY.md — threat model and trust boundary.
11. Cargo.toml — workspace topology, dependencies, lint policy.
12. .cargo/config.toml (search excerpt) — nextest workspace gate.
13. crates/ai-memory-core/src/sanitize.rs (search excerpt) — sanitizer/allowlist behavior.
14. crates/ai-memory-consolidate/src/auto_improve_schedule.rs (search excerpt) — scheduler/approval semantics.
15. crates/ai-memory-store/src/auto_improve.rs (search excerpt) — proposal apply choke point.
16. crates/ai-memory-store/src/reader.rs (search excerpts) — retrieval and scheduler visibility behavior.
17. docs/design-hindsight-borrowings.md (search excerpts) — bounded authority/RRF evolution.
18. recent commit 5157c6be — scheduler claim failure retry/parking repair.
19. repository tree — test/CI/security/integration breadth and module-size signals.
20. CONTRIBUTING.md / AGENTS.md search excerpts — engineering gates and test strategy.

## Deferred after Standard cap

Remaining docs, most source modules, full test bodies, generated hooks, release scripts, web UI, companion importer details, benchmark methodology replication, issue/PR corpus, and historical churn/contributor analysis are deferred to Deep mode.
