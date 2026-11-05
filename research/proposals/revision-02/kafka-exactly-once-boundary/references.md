# References — Draw the boundary around Kafka exactly-once processing

Proposal revision: 02. Original research: 2026-11-03; source recheck: 2026-11-05. Owner: Research Analyst.

## S1 — Apache Kafka 4.1: Design

- Primary source: https://kafka.apache.org/41/design/design/
- Freshness/version: Versioned 4.1 documentation; rechecked 2026-11-05; site labels it older. Review target broker/client versions before production content.
- Evidence locations: D1: S1, Message Delivery Semantics and Using Transactions; D2: S1, Message Delivery Semantics

Evidence is paraphrased. Original angles and proposed exercises are analyst synthesis, not claims that the sources endorse them. Sources are documentation evidence; no runtime experiments were conducted.

D3–D4: S1, Message Delivery Semantics (isolation, external coordination and keyed repetition) and Using Transactions (ownership, atomic output/offset updates, configurations, abort recovery). Timeline repairs and counted-effect choices are analyst synthesis. No exact patch-version implementation or newest-release behavior is asserted.
