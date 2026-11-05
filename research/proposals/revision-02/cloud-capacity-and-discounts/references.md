# References — Can your recovery plan obtain compute when it needs it?

Proposal revision: 02. Original research: 2026-11-03; source recheck: 2026-11-05. Owner: Research Analyst.

## S1 — Amazon EC2: On-Demand Capacity Reservations

- Primary source: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html
- Freshness/version: Living latest guide; rechecked 2026-11-05; no fixed publication date asserted. Scope is EC2, not every cloud reservation product.
- Evidence locations: C1: S1, introduction; C2: S1, Differences table

## S2 — Amazon EC2: Capacity Reservation pricing and billing

- Primary source: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-pricing-billing.html
- Freshness/version: Living latest guide; rechecked 2026-11-05. Qualitative billing behavior only; no rates quoted.
- Evidence locations: C3: S2, Pricing

Evidence is paraphrased. Original angles and proposed exercises are analyst synthesis, not claims that the sources endorse them. Sources are documentation evidence; no runtime experiments were conducted.

## S3 — Launch instances into an existing Capacity Reservation

- Primary source: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-launch.html
- Living latest EC2 documentation; checked 2026-11-05; no fixed publication date asserted.
- Evidence location: C4: opening eligibility list and Console launch preferences; matching attributes, active state, sufficient available count and targeting.

## S4 — View the state of a Capacity Reservation

- Primary source: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-view.html
- Living latest EC2 documentation; checked 2026-11-05; no fixed publication date asserted.
- Evidence location: C5: introduction (eventual consistency) and Capacity Reservation states; example describes AvailableInstanceCount.

## S5 — Concepts for Amazon EC2 Capacity Reservations

- Primary source: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/cr-concepts.html
- Living latest EC2 documentation; checked 2026-11-05; no fixed publication date asserted.
- Evidence location: C6: Start date and time; End date and time.

C7: S1, Quotas and Differences table. C3 qualification: S2, Pricing, Billing and Billing discounts (matching eligibility and instance-use priority; no zonal RI discount). Fictional AZ/count/time cases and worksheet are analyst synthesis. No price, purchase recommendation or application-resilience guarantee.
