# An outbox makes the publishing obligation durable

Revision: 01 | Domain: Software architecture | Researched: 2026-11-03

Owner: Research Analyst. Execution: [CARA-2](/CARA/issues/CARA-2).

Status: research proposal awaiting independent technical review and explicit human topic decision. Production and publishing are not approved.

## Relevance

Separately saving a business change and publishing an event creates a failure window that is easy to overlook.

## Intended audience

Backend developers and software architects designing database-backed event workflows.

## Original technical angle

Original teaching proposal: treat the outbox record as a durable obligation. Follow a fictional order through transaction rollback, successful commit, and relay retry; ask where the obligation is stored and when it can be discharged.

## Claim-to-evidence mapping

| Claim | Technical statement | Primary evidence |
|---|---|---|
| A1 | Separate database and message writes can diverge when one succeeds and the other fails. | S1, Intent and Motivation |
| A2 | A relational outbox writes the business row and outbox row in one transaction. | S1, Using an outbox table with a relational database |
| A3 | Duplicate delivery remains a concern and consuming services should be idempotent. | S1, Issues and considerations |

## Primary sources and freshness

- S1: [AWS Prescriptive Guidance: Transactional outbox pattern](https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/transactional-outbox.html). Living latest guidance; retrieved 2026-11-03. No fixed revision or implementation-version compatibility asserted.

## Educational takeaway

Use a local transaction to preserve intent, then reason separately about relay retry, duplicate handling, and ordering.

## Proposed scope if approved

A failure matrix and durable-obligation worksheet. Proposed discussion only; no full tutorial or service implementation.

## Limits and review checks

This proposal does not claim end-to-end exactly-once effects or prescribe an AWS service. Ordering, relay concurrency, and retention need design-specific validation. Distinct from the Kafka proposal: this focuses on originating database changes.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.
