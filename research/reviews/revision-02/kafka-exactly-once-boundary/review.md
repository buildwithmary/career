# Independent technical re-review — kafka-exactly-once-boundary

Review revision: 02 | Reviewed: 2026-11-05 | Technical Reviewer

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-4) | [Execution task](/CARA/issues/CARA-3)

Input: [proposal revision 02](https://github.com/buildwithmary/career/blob/1db3dd7e3e89544cf1cce89a01277a4128d44e5f/research/proposals/revision-02/kafka-exactly-once-boundary/kafka-exactly-once-boundary-revision-02-proposal.md) and [references](https://github.com/buildwithmary/career/blob/1db3dd7e3e89544cf1cce89a01277a4128d44e5f/research/proposals/revision-02/kafka-exactly-once-boundary/references.md). Manifest revision ecc434cc-6240-4ce7-b38f-71c2e6e344b2; compared with original findings revision b7c487f4-fd7f-4543-9ff5-e8077f7d6b7d and all ten finding-to-change matrix rows.

Verdict: CLEAR for explicit human topic selection with caveats. No remaining material revision-01 finding.

Matrix reconciliation: all three Kafka rows close. The bounded timeline now defines the counted effect, writes output and offsets transactionally, distinguishes commit/abort visibility, resets position/state before replay, and offers atomic commitment OR safe repetition for external effects. Version and destination assumptions are explicit.

D1–D4 agree with [Kafka 4.1 Design, Message Delivery Semantics and Using Transactions](https://kafka.apache.org/41/design/design/). The isolation counterexample is valid; retry deduplication remains distinct from business deduplication.

Reviewer judgment: the revised exercise suits intermediate engineers and now makes the observer part of the guarantee. Retain coordination/recovery costs and stable operation-ID scope/retention as discussion questions. Before runnable production, pin broker/client patch versions and test rebalances, fencing and ambiguous commit outcomes; this review establishes no implementation correctness. These are future validation conditions, not new proposal blockers.

Primary sources checked 2026-11-05. Exercises remain proposals; no runtime validation. Originality means teaching synthesis, not literature novelty. Paul presents exact versions for human approve/revise/park decisions. No production approval, publishing, resources or additional spend.
