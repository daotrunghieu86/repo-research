# Independent Review Gate

Status: **NOT RUN**

The v7.1 workflow requires a fresh-context model that did not produce the analysis. This ChatGPT runtime exposes no separate Claude/Codex reviewer session, so marking the run complete would violate the skill contract.

## Resume action

Run a fresh Claude CLI session if available; otherwise use a separate subscription-backed Codex session. Give it read-only access to:

- this run directory
- akitaonrails/ai-memory at commit 5157c6be10b5830d7adc7e29b0a4358c3ecbe6a2
- the v7.1 skill contracts

Ask it to verify every major claim, find missing discoveries/weaknesses, check scores and evidence links, and return PASS or actionable findings. Save that output here, repair resolvable findings, rerun validation, then change state.json to `complete`.
