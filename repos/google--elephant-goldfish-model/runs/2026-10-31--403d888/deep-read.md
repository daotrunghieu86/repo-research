# Evidence selection

Selected 15 commit-pinned internal artifacts:

- README.md
- docs/designs/architecture.md
- docs/harnesses.md
- TESTING.md
- skills/egm-review/SKILL.md
- skills/egm-review-loop/SKILL.md
- agents/comprehension.md
- agents/implementation_readiness.md
- docs/codex.md
- skills/egm-bootstrap/SKILL.md
- skills/egm-drift-report/SKILL.md
- resources/document_standards/implementation-readiness-standard.md
- .github/workflows/tests.yml
- tests/integration/test_codex.py
- docs/privacy.md

Selection prioritizes fresh-context semantics, review ordering, readiness, failure accounting, native trace verification and host limits. Inventory uses the complete commit-pinned GitHub tree API (227 blobs), substituting for a local clone under the connector-only workflow. No target instructions executed. See coverage-audit.jsonl for all selected and deferred tracked paths. External essay and linked issue/PR details are deferred; TESTING.md reports were read but not independently reproduced. No native EGM tests or application tests were run.

## Traceable observations

| Selected evidence | Finding | Limit |
|---|---|---|
| README and architecture | F-001, F-013, F-014: design-first lifecycle and support boundary | Internal adoption is self-reported |
| Review and review-loop | F-002, F-006: ordered stages and failure accounting | Prompt-level contracts need live enforcement |
| Comprehension and readiness | F-004, F-005: paraphrase and explicit implementation choices | Document quality is not behavioral correctness |
| Codex guide and integration fixture | F-003, F-009, F-010: fresh turns and native evidence | No independent fixture rerun here |
| Bootstrap and drift | F-007, F-008: component contracts and comparison | No guarantee of complete or current knowledge |
| Offline CI and privacy | F-011, F-012: packaging checks and host data boundary | No independent security audit |
