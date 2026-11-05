# Independent technical review — oauth-replay-controls

Review revision: 01 | Reviewed: 2026-11-05 | Reviewer: Technical Reviewer

Verdict: Revision requested before presenting as a technically cleared proposal.

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-6) | [Execution task](https://paperclip.ing/CARA/issues/CARA-3)

Reviewed input: [proposal revision 01](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/oauth-replay-controls/oauth-replay-controls-revision-01-proposal.md) and [references](https://github.com/buildwithmary/career/blob/89fd715671af670df3ebfe83154aaf33e1d316db/research/proposals/revision-01/oauth-replay-controls/references.md). The immutable handoff bundle was read locally; delivery provenance is recorded in the research handoff manifest.

I1, I2 and I3 match [RFC 9700 §§2.1.1, 2.2.2 and 2.3](https://www.rfc-editor.org/rfc/rfc9700.html): public-client PKCE is mandatory, confidential-client PKCE recommended; public-client refresh tokens require sender constraint or rotation; minimum access privileges are recommended. January 2025 and BCP 240 metadata match the [RFC status page](https://www.rfc-editor.org/info/rfc9700/). No exhaustive errata audit is claimed.

Material qualification for the exercise: §4.14.2 describes rotation as exposing reuse when both parties use the token chain; it cannot identify the attacker, and revocation costs the legitimate client a fresh grant. Avoid teaching rotation as prevention of the first stolen-token use. §2.1.1 also recommends a non-exposing challenge method, currently S256.

Reviewer counterexample: an attacker redeems a stolen refresh token before its legitimate owner. Ask what is detected later, what remains usable, and what recovery costs. A compromised verifier/client is outside the simple stolen-code illustration's protection assumptions.

The threat timeline suits the audience, but a credential-by-credential table should separate prevention, detection and residual exposure. Choosing not to issue refresh tokens is also a design option requiring risk assessment (§4.14.2).

Acceptance for revision: add that counterexample, preserve MUST versus SHOULD and public/confidential scope, and state code-only theft assumptions. Provider behavior and architecture remain unvalidated; this is not a login-security completeness checklist.

This verdict assesses proposal suitability only. Paul owns response to findings and presentation for explicit human topic selection. Production and manual publication require their own gates. No experiments, resources, spending or production content were created.
