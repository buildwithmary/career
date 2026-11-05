# Draw the boundary around Kafka exactly-once processing

Revision: 01 | Domain: Distributed systems | Researched: 2026-11-03

Owner: Research Analyst. Execution: [CARA-2](/CARA/issues/CARA-2).

Status: research proposal awaiting independent technical review and explicit human topic decision. Production and publishing are not approved.

## Relevance

An exactly-once label can hide a gap when a consumer performs an external business action.

## Intended audience

Intermediate backend and data engineers who understand consumer offsets and database transactions.

## Original technical angle

Original teaching proposal: use two parallel failure timelines for a Kafka-to-Kafka transform and a Kafka-to-database writer. Mark the crash point between output and offset commit, then ask what must share atomic storage.

## Claim-to-evidence mapping

| Claim | Technical statement | Primary evidence |
|---|---|---|
| D1 | Kafka transactions can combine output-topic writes and consumed offsets. | S1, Message Delivery Semantics and Using Transactions |
| D2 | Exactly-once behavior for external destinations requires cooperation from those destinations. | S1, Message Delivery Semantics |

## Primary sources and freshness

- S1: [Apache Kafka 4.1: Design](https://kafka.apache.org/41/design/design/). Versioned 4.1 documentation; retrieved 2026-11-03; site labels it older. Review target broker/client versions before production content.

## Educational takeaway

State the input, output, failure model, and transaction boundary before making an exactly-once claim.

## Proposed scope if approved

Two failure timelines and a transaction-boundary annotation exercise. No benchmark or runnable demo produced.

## Limits and review checks

Pinned to Kafka 4.1 documentation, explicitly an older version; not a claim about the newest release. Database, email, and payment effects do not inherit Kafka guarantees automatically.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.
