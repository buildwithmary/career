# Draw the boundary around Kafka exactly-once processing

Revision: 02 | Domain: Distributed systems | Researched: 2026-11-03 | Revised/source-checked: 2026-11-05

Owner: Research Analyst. Execution: [CARA-2](/CARA/issues/CARA-2).

Status: research proposal awaiting independent technical review and explicit human topic decision. Production and publishing are not approved.

## Relevance

An exactly-once label can hide a gap when a consumer performs an external business action.

## Intended audience

Intermediate backend and data engineers who understand consumer offsets and database transactions.

## Original technical angle

Original teaching proposal: use two parallel failure timelines for a Kafka-to-Kafka transform and a Kafka-to-database writer. Mark the crash point between output and offset commit, then ask what must be committed atomically or made safe to repeat.

## Claim-to-evidence mapping

| Claim | Technical statement | Primary evidence |
|---|---|---|
| D1 | Kafka transactions can combine output-topic writes and consumed offsets. | S1, Message Delivery Semantics and Using Transactions |
| D2 | Exactly-once behavior for external destinations requires cooperation from those destinations. | S1, Message Delivery Semantics |

## Primary sources and freshness

- S1: [Apache Kafka 4.1: Design](https://kafka.apache.org/41/design/design/). Versioned 4.1 documentation; rechecked 2026-11-05; site labels it older. Review target broker/client versions before production content.

## Educational takeaway

State the input, output, failure model, and transaction boundary before making an exactly-once claim.

## Proposed scope if approved

Two failure timelines and a transaction-boundary annotation exercise. No benchmark or runnable demo produced.

## Limits and review checks

Pinned to Kafka 4.1 documentation, explicitly an older version; not a claim about the newest release. Database, email, and payment effects do not inherit Kafka guarantees automatically.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.

## Revision 02: bounded timeline design

The proposed exercise counts committed output records for one input record in Kafka; its external branch counts one database business mutation. It assumes a single Kafka cluster, retained input for replay, crash/restart failures, and correct partition ownership and recovery. It does not count emails or payments as Kafka output.

| Proposed timeline | Commit/abort and visibility annotations | Replay and destination assumptions |
|---|---|---|
| Kafka → Kafka | Consume input; transactionally write output and consumed offsets together. Commit exposes transactional output to downstream read_committed consumers. Abort leaves the stored offset unchanged and hides that output from those consumers. | After abort, explicitly restore consumer position/application state before reprocessing. A restart recovers from committed offsets. No separately committed offsets or external side effects belong inside this guarantee. |
| Isolation counterexample | A read_uncommitted observer can see aborted or still-open transactional records. | Ask learners whether counting those observations as completed business effects supports their claimed boundary. |
| Kafka → database, separate commits | Apply a database mutation, then crash before committing the Kafka offset. | Replay can repeat the mutation. Reversing the order risks omission after a crash. Assume no automatic transaction spans Kafka and this database. |
| External repair alternatives | Ask what must be committed atomically OR made safe to repeat. | Candidate designs: coordinate output and recovery position; store both in a destination transaction; or atomically couple a stable operation ID/deduplication check with the database mutation. Destination atomicity, key scope, retention and recovery remain design obligations. |

These are proposed reasoning cases, not observed results. Producer retry deduplication is a different unit from deduplicating a replayed business operation. The learner must name that unit.

### Evidence additions

| Claim | Technical statement | Primary evidence |
|---|---|---|
| D3 | read_committed excludes aborted transactional records; read_uncommitted can expose them and open transactions. | S1, Message Delivery Semantics; Using Transactions |
| D4 | Correct transactional processing includes partition ownership, atomic output/offset updates, and explicit state/position reset after abort. | S1, Using Transactions |

Configuration assumptions for a future implementation: transactional producer identity, disabled consumer auto-commit, and read_committed where transactional visibility matters, including downstream observation. This remains a Kafka 4.1 conceptual proposal; pin exact broker/client patch versions, group/rebalance handling and error recovery before any approved runnable example. No implementation is supplied.

### Educational takeaway and review acceptance

Draw the counted effect, transaction boundary and observer together. Evaluate atomic commitment and safe repetition as alternatives with different recovery costs. Re-review should challenge both timelines at each crash point and the isolation counterexample; no independent clearance is claimed.
