# PKCE and refresh-token rotation protect different moments

Revision: 01 | Domain: Identity/security | Researched: 2026-11-03

Owner: Research Analyst. Execution: [CARA-2](/CARA/issues/CARA-2).

Status: research proposal awaiting independent technical review and explicit human topic decision. Production and publishing are not approved.

## Relevance

Teams can adopt a secure login flow while leaving later token replay risks insufficiently addressed.

## Intended audience

Application developers and identity engineers with basic OAuth authorization-code flow knowledge.

## Original technical angle

Original teaching proposal: a two-stage threat timeline. A stolen authorization code and a stolen refresh token appear at different points; learners match each to the applicable control and explain the residual risk.

## Claim-to-evidence mapping

| Claim | Technical statement | Primary evidence |
|---|---|---|
| I1 | RFC 9700 requires PKCE for public clients and recommends it for confidential clients. | S1, section 2.1.1 |
| I2 | Refresh tokens for public clients must be sender-constrained or rotated. | S1, section 2.2.2 |
| I3 | Access-token privileges should be limited to the application's requirements. | S1, section 2.3 |

## Primary sources and freshness

- S1: [IETF RFC 9700: Best Current Practice for OAuth 2.0 Security](https://www.rfc-editor.org/rfc/rfc9700.html). Published January 2025; BCP 240; updates RFCs 6749, 6750, 6819. Retrieved 2026-11-03; normative source.
- S2: [RFC Editor status page for RFC 9700](https://www.rfc-editor.org/info/rfc9700/). Status page retrieved 2026-11-03; use as revalidation entry point. No assertion that all errata have been audited.

## Educational takeaway

Tie each control to a credential and attack stage; PKCE does not replace refresh-token replay defenses.

## Proposed scope if approved

One threat timeline, a credential-to-control exercise, and a terminology check. No exploit code or identity-provider configuration.

## Limits and review checks

Normative scope and MUST/SHOULD distinctions must be preserved. Provider support and application architecture need separate validation. Recheck RFC status and errata before producing approved content.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.
