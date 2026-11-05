# Can your recovery plan obtain compute when it needs it?

Revision: 01 | Domain: Cloud infrastructure | Researched: 2026-11-03

Owner: Research Analyst. Execution: [CARA-2](/CARA/issues/CARA-2).

Status: research proposal awaiting independent technical review and explicit human topic decision. Production and publishing are not approved.

## Relevance

Cost commitments and launch-capacity planning answer different operational questions.

## Intended audience

Cloud engineers, SREs, and technical leads reviewing EC2 recovery assumptions.

## Original technical angle

Original teaching proposal: a paper exercise with fictional recovery requirements. Place each requirement in a two-column matrix: billing treatment and capacity availability. Add matching-attribute checks before considering a capacity reservation. This is educational analysis, not a purchase recommendation.

## Claim-to-evidence mapping

| Claim | Technical statement | Primary evidence |
|---|---|---|
| C1 | EC2 Capacity Reservations reserve capacity in a specific Availability Zone and require matching instance attributes. | S1, introduction |
| C2 | Savings Plans provide billing discounts without reserving capacity; Capacity Reservations provide no inherent billing discount. | S1, Differences table |
| C3 | Unused Capacity Reservations incur equivalent On-Demand charges. | S2, Pricing |

## Primary sources and freshness

- S1: [Amazon EC2: On-Demand Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html). Living latest guide; retrieved 2026-11-03; no fixed publication date asserted. Scope is EC2, not every cloud reservation product.
- S2: [Amazon EC2: Capacity Reservation pricing and billing](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-pricing-billing.html). Living latest guide; retrieved 2026-11-03. Qualitative billing behavior only; no rates quoted.

## Educational takeaway

Review capacity assurance and discount eligibility separately, then verify attributes, quotas, and recovery assumptions.

## Proposed scope if approved

A fictional recovery matrix and a mismatch scenario; no resource creation and no live pricing calculation.

## Limits and review checks

AWS living documentation, not a contractual capacity guarantee or current price quote. Reservations do not by themselves establish application resilience. Verify region, platform, quotas, and commercial terms before any real decision.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.
