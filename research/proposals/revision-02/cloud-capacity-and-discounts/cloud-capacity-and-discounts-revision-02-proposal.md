# Can your recovery plan obtain compute when it needs it?

Revision: 02 | Domain: Cloud infrastructure | Researched: 2026-11-03 | Revised/source-checked: 2026-11-05

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
| C3 | Unused Capacity Reservations have equivalent On-Demand baseline charges; eligible discounts can change effective billing. | S2, Pricing |

## Primary sources and freshness

- S1: [Amazon EC2: On-Demand Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html). Living latest guide; rechecked 2026-11-05; no fixed publication date asserted. Scope is EC2, not every cloud reservation product.
- S2: [Amazon EC2: Capacity Reservation pricing and billing](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-pricing-billing.html). Living latest guide; rechecked 2026-11-05. Qualitative billing behavior only; no rates quoted.

## Educational takeaway

Review capacity assurance and discount eligibility separately, then verify attributes, quotas, and recovery assumptions.

## Proposed scope if approved

A fictional recovery matrix and a mismatch scenario; no resource creation and no live pricing calculation.

## Limits and review checks

AWS living documentation, not a contractual capacity guarantee or current price quote. Reservations do not by themselves establish application resilience. Verify region, platform, quotas, and commercial terms before any real decision.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.

## Revision 02: recovery worksheet design

Proposed fictional requirement: launch four matching instances in recovery AZ B at time T after AZ A becomes unavailable. Labels A/B and the count are invented teaching inputs. For each row, learners must supply separate evidence for billing and usable capacity.

| Proposed scenario | Recovery evidence learners must check | Billing question |
|---|---|---|
| Reservation exists only in AZ A | Does its AZ match recovery AZ B? This row fails the location test. | Does paying for A establish availability in B? |
| Matching reservation in B is scheduled for after T, delayed, expired or cancelled | Check actual state, start time and validity window at T. A request or future intention is not evidence of usable capacity now. | When does provisioning/billing begin, and what commitment terms apply? |
| Active B reservation lists four total but only two available | Compare available count with four required; inspect competing matching workloads. An open reservation can be consumed by other matching instances. | Separate used and unused portions. |
| B reservation has sufficient available count | Verify instance type, platform/AMI, tenancy and AZ; check launch targeting/preferences and the relevant account/Region quotas. | Determine applicable discount qualification separately. |
| Plan says “request during recovery” | Require evidence of an existing usable allocation; a future request can fail. | An intended purchase does not resolve launch uncertainty. |

This is a proposed paper exercise. A successful capacity worksheet still leaves networking, data recovery and application readiness to separate analysis.

### Evidence additions and qualifications

| Claim | Technical statement | Primary evidence |
|---|---|---|
| C4 | Launch requires matching attributes, active reservation and sufficient available capacity; launch preferences affect reservation use. | S3, introduction and launch options |
| C5 | active means available; scheduled, delayed, failed and expired describe different delivery outcomes. State reads are eventually consistent. | S4, introduction and Capacity Reservation states |
| C6 | Start date/time controls intended availability; end date/time defines release. | S5, Start date and time; End date and time |
| C7 | Reservations consume applicable On-Demand quota; eligibility must be checked for the actual account and Region. | S1, Quotas and Differences table |

C3 billing footnote: equivalent On-Demand pricing is the baseline, not every effective bill. Eligible Savings Plans and Regional Reserved Instance discounts can apply when attributes match; instance usage receives preference over unused reservations. Zonal Reserved Instance discounts do not apply to Capacity Reservations (S2, Pricing; Billing discounts). Do not infer discount eligibility from the existence of a commitment.

The worksheet should record evidence time as well as values. S4 warns state can lag after creation; do not teach every pending read as proof of unavailable capacity. The exercise's scheduled-after-T and expired cases avoid that ambiguity.

### Educational takeaway and review acceptance

Ask “where, when, for which workload, and how many available?” before discussing discounts. Holding recovery capacity creates utilization cost; a discount does not resolve a location mismatch. Re-review should check the location/state row, available count, quota/targeting prompts and qualified billing claim. No independent clearance is claimed.

- S3: [Launch instances into an existing Capacity Reservation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-launch.html). Living latest EC2 guide; checked 2026-11-05.

- S4: [View the state of a Capacity Reservation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-view.html). Living latest EC2 guide; checked 2026-11-05.

- S5: [Concepts for Amazon EC2 Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/cr-concepts.html). Living latest EC2 guide; checked 2026-11-05.
