# Independent technical review — outbox-obligation

Review revision: 01 | Reviewed: 2026-11-05 | Reviewer: Technical Reviewer

Verdict: Suitable for human topic selection with caveats.

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-7) | [Execution task](https://paperclip.ing/CARA/issues/CARA-3)

Reviewed input: [proposal revision 01](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/outbox-obligation/outbox-obligation-revision-01-proposal.md) and [references](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/outbox-obligation/references.md). The immutable handoff bundle was read locally; delivery provenance is recorded in the research handoff manifest.

A1–A3 are supported by [AWS Transactional outbox pattern, Intent, Motivation, Issues and considerations, and relational outbox](https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/transactional-outbox.html): dual writes can diverge; business and outbox rows share a local transaction; duplicate handling remains necessary. This is living architectural guidance, not a verified implementation.

The durable-obligation metaphor and rollback/retry worksheet suit backend architects. It is distinct from the Kafka proposal when kept focused on originating database changes.

Reviewer disagreement: “when it can be discharged” needs an explicit endpoint. Broker acceptance and completion of the downstream business effect are different milestones. My proposed failure case is broker acceptance followed by relay crash before recording success: replay must remain safe. A second case is a relay that never recovers; durable intent alone does not supply eventual progress.

Add a stable event identifier, a discussion of atomic deduplication with the consumer's local effect, and an explicit ordering scope as design questions. These are reviewer suggestions; their correctness depends on the chosen implementation. Do not infer global ordering or exactly-once business effects from outbox storage, timestamps or broker features.

Tradeoff: polling/CDC, concurrency and retention introduce operational work. Include backlog age, retry exhaustion and ownership as proposed operational questions. No implementation validation has occurred. These caveats can accompany human topic selection without requiring a factual rewrite.

This verdict assesses proposal suitability only. Paul owns response to findings and presentation for explicit human topic selection. Production and manual publication require their own gates. No experiments, resources, spending or production content were created.
