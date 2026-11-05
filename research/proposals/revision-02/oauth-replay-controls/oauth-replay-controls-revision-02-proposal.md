# PKCE and refresh-token rotation protect different moments

Revision: 02 | Domain: Identity/security | Researched: 2026-11-03 | Revised/source-checked: 2026-11-05

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

- S1: [IETF RFC 9700: Best Current Practice for OAuth 2.0 Security](https://www.rfc-editor.org/rfc/rfc9700.html). Published January 2025; BCP 240; updates RFCs 6749, 6750, 6819. Rechecked 2026-11-05; normative source.
- S2: [RFC Editor status page for RFC 9700](https://www.rfc-editor.org/info/rfc9700/). Status page rechecked 2026-11-05; use as revalidation entry point. No assertion that all errata have been audited.

## Educational takeaway

Tie each control to a credential and attack stage; PKCE does not replace refresh-token replay defenses.

## Proposed scope if approved

One threat timeline, a credential-to-control exercise, and a terminology check. No exploit code or identity-provider configuration.

## Limits and review checks

Normative scope and MUST/SHOULD distinctions must be preserved. Provider support and application architecture need separate validation. Recheck RFC status and errata before producing approved content.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.

## Revision 02: credential and attack-stage worksheet

The proposed authorization-code case assumes theft of the code alone, a secret verifier, correctly enforced transaction-bound PKCE with S256, and uncompromised client/server endpoints. It does not claim protection after verifier or client compromise.

| Credential/control | Prevention or detection being discussed | Residual exposure / recovery question |
|---|---|---|
| Authorization code + PKCE | Prevent redemption of the code-only theft in the stated model. | What changes if the attacker also obtains the verifier or controls the client? |
| Refresh token + rotation | Expose reuse when both parties use the related token chain. | First stolen-token redemption can succeed before reuse detection; which tokens and effects remain? |
| Refresh token + sender constraint | Bind use to a client instance cryptographically. | What if the binding key or client is also compromised? Validate provider behavior separately. |
| Already-issued access token | Restrict privileges and assess its own replay controls. | Do not assume refresh-token revocation reverses completed actions or automatically invalidates every access token. |

### First-use counterexample to propose

Learners receive this fictional public-client sequence: attacker steals unused refresh token R0; attacker redeems R0 first and obtains access token A1 and rotated R1; legitimate client later submits R0. Ask learners to identify first successful misuse, later reuse detection, active-refresh-token revocation, and legitimate recovery via a fresh authorization grant. If the legitimate client never reuses R0, this sequence supplies no reuse event for detection. This is analyst inference from the rotation mechanism, not a provider test.

The server cannot identify which party is the attacker from the invalid token alone. Ask separately how A1 expires or is revoked/checked and how previously completed effects are handled. Those outcomes are architecture/provider assumptions, not guarantees of rotation.

### Evidence additions and normative scope

| Claim | Technical statement | Primary evidence |
|---|---|---|
| I4 | Clients SHOULD choose a challenge method that hides the verifier in the request; RFC 9700 identifies S256 for this purpose. | S1, §2.1.1 |
| I5 | Rotation detects shared-chain reuse, cannot identify the attacker, and revokes the active refresh token at the cost of a fresh legitimate grant. | S1, §4.14.2 |
| I6 | Authorization servers MUST risk-assess whether to issue refresh tokens. | S1, §4.14.2 |

Preserve I1–I3: public-client PKCE MUST; confidential-client PKCE RECOMMENDED; public-client refresh tokens MUST use sender constraint or rotation; minimum access-token privileges SHOULD. The confidential-client binding requirement remains separate. Not issuing refresh tokens is a risk-based design option, not a universal prescription.

### Educational takeaway and review acceptance

Label each control's credential, stage, prevention/detection role, residual exposure and recovery cost. Re-review should challenge the first-use sequence, code-only assumptions and every MUST/SHOULD/client-scope statement. Provider support, complete login security and residual access-token lifetime remain unvalidated. No independent clearance is claimed.
