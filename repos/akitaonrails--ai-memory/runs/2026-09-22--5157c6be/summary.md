# ai-memory — Standard Repository Analysis

Analyzed commit: `5157c6be10b5830d7adc7e29b0a4358c3ecbe6a2`  
Depth: **standard**  
Skill: **personal-brain-repo-analysis v7.1**

## Central idea

ai-memory turns coding-agent memory into developer-owned infrastructure: lifecycle events are captured automatically, durable knowledge is compiled into a Git-backed Markdown wiki, SQLite supplies derived retrieval indexes, and explicit claim-once handoffs let work continue across agent vendors and machines.

## Top discoveries

1. **Markdown/Git is authoritative; indexes are disposable acceleration state.** This is the core portability and recoverability pattern. [F-001]
2. **Cross-agent handoff is a protocol, not a convention.** Persisted ownership/scope/acceptance semantics make vendor switching reliable. [F-002]
3. **Hybrid retrieval is deliberately multi-stream and bounded.** FTS + entities + graph + optional vectors are RRF-fused, then only lightly authority-adjusted. [F-003]
4. **Self-improvement is an asynchronous state machine.** Proposal staging, approval/eval gates, retry and parking are separate from hook latency. [F-004]
5. **Historical recall has validity semantics.** `as_of` searches the version that was live then, not just current text with timestamps. [F-011]

## Weaknesses

The main structural risks are the unavoidable filesystem/SQLite consistency boundary [F-008], intentionally single-trust-domain security model [F-007], large central implementation files [F-009], and governance risk when model-reviewed proposals are auto-applied [F-010].

## Engineering health

| Band | Score | Evidence-based read |
|---|---:|---|
| Security | 80 | Strong threat model, sanitization, network hardening and secret scanning; no tenant isolation or at-rest encryption. |
| Reliability | 87 | Single-writer design, idempotency/recovery paths, retry/parking semantics, substantial integration tests. |
| Maintainability | 68 | Clean crate boundaries and strict lints, but several central files are extremely large. |
| Documentation | 95 | Architecture, security, data handling, design rationale, comparisons and operational guides are unusually comprehensive. |
| Process | 91 | Workspace gates, CI, secret scans, contribution guidance and release discipline are visible in-tree. |
| Velocity | 96 | Very active September 2026 development with rapid issue/PR fixes. |

**Quality score: 86 / 100 — Excellent.**  
**Critical floor: Maintainability (68 / Healthy)** because central-file size is the clearest scaling pressure.

## Evidence limits

This run inspected the full tracked tree plus selected high-signal docs/code-search evidence under the Standard cap. It did **not** execute the repository's Rust test suite, Semgrep, gitleaks, cargo-audit/deny, or a local clone-based complexity scan. Standard mode also skips 12-month history analysis.

The deterministic artifacts and schemas are prepared. The workflow's final independent fresh-context semantic reviewer is not available in this chat runtime, so the persisted state remains **in-progress** rather than falsely marked complete.
