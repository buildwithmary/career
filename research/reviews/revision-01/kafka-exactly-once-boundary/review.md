# Independent technical review — kafka-exactly-once-boundary

Review revision: 01 | Reviewed: 2026-11-05 | Reviewer: Technical Reviewer

Verdict: Revision requested before presenting as a technically cleared proposal.

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-4) | [Execution task](https://paperclip.ing/CARA/issues/CARA-3)

Reviewed input: [proposal revision 01](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/kafka-exactly-once-boundary/kafka-exactly-once-boundary-revision-01-proposal.md) and [references](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/kafka-exactly-once-boundary/references.md). The immutable handoff bundle was read locally; delivery provenance is recorded in the research handoff manifest.

D1 and D2 are supported by [Kafka 4.1 Design, Message Delivery Semantics and Using Transactions](https://kafka.apache.org/41/design/design/): output and offsets can share a Kafka transaction; external destinations need coordination. The source also distinguishes committed-record visibility by consumer isolation and specifies transactional producer/consumer configuration. Version 4.1 is intentionally pinned and marked older; this review does not establish newer-version behavior.

Material omission: the Kafka-to-Kafka success timeline must state transactional writes/offset handling and downstream read_committed visibility. Transaction use alone does not justify an unconditional end-to-end exactly-once label. Include an aborted transaction seen by a read_uncommitted consumer as the counterexample.

Reviewer disagreement: “what must share atomic storage” is too restrictive as the exercise's general answer. The cited source also discusses coordinating external output with offsets and deduplication using keys. Ask what must be committed atomically OR made safe to repeat, and define the business effect being counted.

The audience and parallel timelines are strong; distinguish producer retry deduplication from business-operation deduplication. Tradeoff for discussion: stronger coordination adds implementation and recovery obligations; some effects tolerate retries.

Acceptance for revision: annotate both timelines with commit/abort visibility, replay behavior, destination assumptions, and target broker/client versions if implementation details are added. No runtime test or benchmark has verified the proposed scenario.

This verdict assesses proposal suitability only. Paul owns response to findings and presentation for explicit human topic selection. Production and manual publication require their own gates. No experiments, resources, spending or production content were created.
