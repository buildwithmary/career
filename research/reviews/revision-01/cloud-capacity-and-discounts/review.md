# Independent technical review — cloud-capacity-and-discounts

Review revision: 01 | Reviewed: 2026-11-05 | Reviewer: Technical Reviewer

Verdict: Revision requested before presenting as a technically cleared proposal.

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-5) | [Execution task](https://paperclip.ing/CARA/issues/CARA-3)

Reviewed input: [proposal revision 01](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/cloud-capacity-and-discounts/cloud-capacity-and-discounts-revision-01-proposal.md) and [references](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/cloud-capacity-and-discounts/references.md). The immutable handoff bundle was read locally; delivery provenance is recorded in the research handoff manifest.

C1 and C2 are supported by [EC2 Capacity Reservations, introduction and differences](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html): reservations are zonal and attribute-matched, while Savings Plans supply discounts rather than capacity. The same guide distinguishes immediate and future reservations and quotas. C3 is supported by [Pricing and billing, Pricing](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-pricing-billing.html): unused reserved capacity has On-Demand-equivalent billing; eligible discounts may apply. C3 is a baseline, not a claim that all effective bills equal undiscounted rates.

Material exercise gap: billing versus capacity is useful but insufficient for the recovery question in the title. Add reservation state/start time, recovery AZ, instance type/platform/tenancy, available count, quota and targeting checks. Distinguish an existing usable reservation from an intention to request one during recovery.

Reviewer counterexample: a matching reservation in the original AZ does not establish recovery capacity in a different AZ. Another matching workload may consume an open reservation. These are failure scenarios inferred from the documented location and matching rules.

Tradeoff: capacity held for recovery has utilization cost; discounts do not remove location or matching constraints. Keep the exercise fictional and qualitative.

Acceptance for revision: add the recovery-location/state failure row and discount-eligibility footnote. Preserve the statement that capacity assurance alone does not prove application resilience. Living documentation was checked today; no purchase recommendation, rate quote or capacity guarantee is made.

This verdict assesses proposal suitability only. Paul owns response to findings and presentation for explicit human topic selection. Production and manual publication require their own gates. No experiments, resources, spending or production content were created.
