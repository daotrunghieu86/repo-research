# The Idea

EGM turns design into a reviewable input to coding. A context-rich Elephant explores requirements and drafts a specification. Fresh Goldfish agents read that specification and selected source material, without inheriting the author's conversation. A human resolves tradeoffs and approves implementation. It is a plugin of agent skills, personas and document standards, rather than a new trained model or a standalone factory service. [F-001, F-003, F-012]

# Strongest and Newest Ideas

1. **Test the handoff, not the author's memory.** Reviewers must receive their task, persona, standards and relevant files explicitly. Codex instructions specify fresh native dispatch and warn that filesystem and host context are still shared. This creates a useful check that the artifact carries enough information for another session. [F-003]
2. **Paraphrase before critique.** The comprehension reviewer restates both the proposal and the existing system. This can expose disconnected explanations even when every term has a definition. [F-004]
3. **Review simplicity twice.** The five-stage sequence places a second zoom-out after critique, so proposed mitigations themselves can be checked for excess complexity before implementation readiness. [F-002]
4. **Inspect native evidence.** Codex integration tests inspect actual dispatch arguments, child completion and file-read traces rather than trusting parent-written receipts. This is a transferable verification practice for agent harnesses. [F-009, F-010]
5. **Keep documentation navigable and check it against code.** Bootstrap constructs component contracts and parent blueprints, while drift reporting compares checked-in intent to current source. These are possible inputs to repository intelligence, though not a complete business feature map. [F-007, F-008]

# Hidden Depth

The review loop distinguishes a reviewer that found nothing from one that did not run. It retries failures once, and a missing reviewer prevents a clean round. Findings that are contested or accepted as risks can be settled; applied fixes are reopened when they fail. Consequently convergence means no new unsettled blocking or major findings, not that the design is objectively correct. [F-006]

The native Codex fixture uses six brainstorm reviewers plus nine review-stage reviewers. It deliberately preapproves interactive gates and generates design artifacts without application code. Its passing result is evidence about orchestration and isolation under the tested setup, not production software reliability or approval usability. [F-009, F-010]

# Weaknesses and Blind Spots

- **Design review ends before behavioral verification.** Implementation readiness specifies code and tests to write; it does not execute the application or prove acceptance and regression behavior. Keep deterministic checks and independent code review. [F-001, F-005, F-010]
- **Full review can be costly.** The fixture uses at least 15 reviewers, and the standalone review loop permits five rounds. Cost savings, latency improvements and defect reductions for our tasks remain unmeasured. [F-006, F-010]
- **Host isolation is a contract that needs evidence.** Fresh turns alone do not exclude filesystem, memory or project instruction leakage. ChatGPT Work's recorded native trace verification is incomplete; the current setup guide also notes a desktop-local package boundary. [F-003, F-009]
- **Specifications can be wrong or stale.** Bootstrap and drift are model-driven workflows. Their output still needs source checking, and no mismatch report is a guarantee of equivalence. [F-007, F-008]
- **Durable factory operations remain a separate responsibility.** Skills orchestrate review prompts and artifacts; the inspected runtime provides no hosted queue or database. This assessment found no standalone factory dashboard or durable scheduler in the tracked runtime layout. [F-002, F-012, F-014]
- **Support and usage claims have limits.** Apache licensing enables reuse, but this is explicitly not an officially supported Google product. Repository-reported internal usage has not been verified here. [F-013]

# Questions Worth Following

Can an engine design pass comprehension and readiness review with only its checked-in specification and linked sources? Can a targeted review find useful omissions at a lower total cost than the full flow? Can our executor record reviewer launch, reads, completion and design SHA without trusting model narratives? Does design-first review reduce rework across equivalent CRUD, ADA and responsive tasks? These require live trials and fair baseline measurements; static inspection cannot answer them.
