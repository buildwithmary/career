# Independent technical re-review — cloud-capacity-and-discounts

Review revision: 02 | Reviewed: 2026-11-05 | Technical Reviewer

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-5) | [Execution task](/CARA/issues/CARA-3)

Input: [proposal revision 02](https://github.com/buildwithmary/career/blob/1db3dd7e3e89544cf1cce89a01277a4128d44e5f/research/proposals/revision-02/cloud-capacity-and-discounts/cloud-capacity-and-discounts-revision-02-proposal.md) and [references](https://github.com/buildwithmary/career/blob/1db3dd7e3e89544cf1cce89a01277a4128d44e5f/research/proposals/revision-02/cloud-capacity-and-discounts/references.md). Manifest revision ecc434cc-6240-4ce7-b38f-71c2e6e344b2; compared with original findings revision b7c487f4-fd7f-4543-9ff5-e8077f7d6b7d and all ten finding-to-change matrix rows.

Verdict: CLEAR for explicit human topic selection with caveats. No remaining material revision-01 finding.

Matrix reconciliation: all three cloud rows close. The fictional AZ-B/time-T/four-instance worksheet covers location, state/start, available count, competing open workloads, matching, targeting and quota. The qualified billing footnote closes the effective-price omission.

C1–C2/C7 match [EC2 reservations and quotas](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html); C4 matches [launch prerequisites](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-launch.html); C5 matches [states and eventual consistency](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-view.html). C6 matches [timing concepts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/cr-concepts.html). C3 and discount qualifications match [billing guidance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-pricing-billing.html).

Reviewer judgment: capacity evidence and billing evidence are now usefully separated. Preserve the pending-read caveat. “Platform/AMI” should mean platform compatibility, not an exact AMI-ID reservation attribute. Before a timed production example, explain documented end-time release granularity rather than treating expiry as instantaneous. Neither point blocks this qualitative proposal. A matching reservation is still only one recovery dependency; networking, data and application readiness remain outside the worksheet. Living sources need revalidation before production.

Primary sources checked 2026-11-05. Exercises remain proposals; no runtime validation. Originality means teaching synthesis, not literature novelty. Paul presents exact versions for human approve/revise/park decisions. No production approval, publishing, resources or additional spend.
