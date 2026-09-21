# Creator View — akitaonrails/ai-memory

## The Idea

The repository is solving a narrower and more concrete problem than “give an AI a memory.” Its real thesis is that coding-agent memory should be **shared infrastructure owned by the developer**, not a feature trapped inside Claude Code, Codex, Cursor, or another harness. The durable object is a Git-backed Markdown wiki; lifecycle hooks capture what actually happened, session boundaries compile that stream into readable project knowledge, and a SQLite index makes that knowledge searchable. The database is acceleration state, not the authority. That one decision shapes backup, portability, hand editing, recovery, and vendor independence. Evidence: README.md, docs/ARCHITECTURE.md, docs/design-decisions.md. [F-001]

The second half of the idea is continuity. Switching agents is treated as a state-transfer problem, not merely a retrieval problem. The repository persists handoffs with ownership, project/cwd scope, claim/accept semantics and expiry rules, so “continue this work in another harness” becomes a protocol transition rather than a convention in a prompt. Evidence: docs/design-decisions.md §9 and docs/ARCHITECTURE.md. [F-002]

## Strongest and Newest Ideas

**1. File-first truth with rebuildable indexes.** Many memory systems choose either opaque database records or vector-first storage. ai-memory deliberately keeps the durable knowledge as ordinary Markdown under Git and makes FTS, entity links, graphs and embeddings derived. This is distinctive because it simultaneously optimizes for human inspection and machine retrieval. The design acknowledges the cost: there is no cross-resource filesystem/SQLite transaction, so all mutation paths are forced through wiki APIs and crash windows are repaired by reindexing. [F-001, F-008]

**2. Claim-once handoff semantics.** The repo does not rely on “write a summary at the end.” A handoff is typed persisted state that can be opened, accepted once, cancelled or expired, and resolved by project/cwd/owner rules. That makes agent-vendor switching an operational primitive. It is one of the most reusable ideas for a second brain that must serve multiple coding agents. [F-002]

**3. Retrieval as a federation of weak signals.** Search combines FTS, lexical entities, graph neighbours and optional vectors with reciprocal-rank fusion, then applies only a bounded authority adjustment for durable rules/decisions/procedures and related metadata. This avoids both vector-only failure modes and a brittle hard-priority hierarchy. Historical `as_of` queries deliberately use a different stream set because present-tense vectors and graph neighbours would contaminate time-specific recall. [F-003, F-011]

**4. Learning happens outside the hot path.** Auto-improvement is a scheduler-driven review of completed sessions, not part of event capture. Proposals are validated, staged, optionally held for approval, optionally checked by project executable gates, and failures now move through retry and parked states instead of silently disappearing. The recent #833 fix is revealing: the project treats the learning scheduler as durable infrastructure with explicit state-machine failure semantics. [F-004]

**5. Privacy boundaries are architectural, not a post-processing promise.** Capture is bounded, sanitization is explicit, assistant text requires double opt-in, stored historical content is marked untrusted when fed back to models, and non-loopback networking fails closed unless deliberately overridden. This is stronger than simply saying “we redact secrets.” [F-005]

## Hidden Depth

The temporal model is deeper than the README suggests. `memory_query(as_of=...)` searches the version whose validity window contained the requested instant, using temporal entity links plus version-filtered FTS. The documentation is explicit that this returns historical content but not an exact replay of historical ranking, because FTS corpus statistics evolve. That is a careful and uncommon distinction. [F-011]

The repository also has a managed-workstream layer beyond ordinary memory hooks. It can normalize portable visible transcript events from different harnesses into an append-only ledger, track native-session cursors and delivery state, and let a newly joined harness consume portable history without blindly adopting unrelated private session history. [F-012]

Another non-obvious strength is engineering verification. The workspace forbids unsafe Rust, uses workspace-wide nextest/CI gates, has dedicated secret scanning, and carries integration suites for auth, handoffs, multi-session behavior, retrieval, migration, hook behavior, packaging and stress cases. The repository is only a few months old but already behaves operationally like infrastructure software. [F-006]

## Weaknesses and Blind Spots

The largest architectural tradeoff is also the source-of-truth decision: filesystem + Git and SQLite cannot commit atomically together. The project compensates with centralized mutation APIs, best-effort rollback and reindex recovery, but this remains a real consistency boundary rather than something transactions can fully erase. [F-008]

Security is intentionally scoped to a single trust domain. Multiple attributed users are supported, but there is no true tenant isolation, no private per-user memory ACL, and no encryption at rest in v1. That is reasonable for workstation/homelab/team-trust use, but it matters if someone reads “multi-user” as “multi-tenant.” [F-007]

Maintainability is the clearest engineering pressure point. The crate layout is modular, yet several core implementation files are very large: MCP server/admin and store reader/ops are each hundreds of kilobytes, while CLI and hook files are also large. That does not make the code bad, but it increases review surface, ownership coupling, and the chance that future features keep accumulating in central files. [F-009]

Auto-improvement is powerful enough to deserve operational caution. By default validated scheduled proposals may be approved through normal wiki mutation paths unless `require_approval=true`; eval gates and trust boundaries exist, but an operator who enables provider-backed learning is granting the system permission to turn model judgments into durable project memory. [F-010]

Finally, the zero-LLM story is accurate for capture/search/handoff, but the most ambitious features—LLM consolidation, semantic embeddings depending on provider choice, reranking, and auto-improvement—create additional privacy, cost and availability dependencies. The repo documents this honestly; users still need to understand which mode they are actually running. [F-005, F-010]

## Questions Worth Following

1. Does retrieval quality remain stable as a wiki grows from thousands to hundreds of thousands of pages? Evidence needed: larger-corpus evals with latency, recall and ranking drift.
2. Will the very large central Rust modules be split before they become ownership bottlenecks? Evidence needed: module-size/churn trend over several releases.
3. How often does auto-improvement produce proposals that humans reject or later revert? Evidence needed: telemetry from proposal acceptance/rejection and downstream corrections.
4. How well do claim-once handoffs behave across unreliable or partially supported harness lifecycle events? Evidence needed: cross-harness fault-injection and recovery tests.
5. Does the Markdown-primary reconciliation model encounter real-world drift under external editors and network filesystems? Evidence needed: long-running watcher/reindex stress tests outside local filesystems.
