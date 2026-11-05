# References — PKCE and refresh-token rotation protect different moments

Proposal revision: 02. Original research: 2026-11-03; source recheck: 2026-11-05. Owner: Research Analyst.

## S1 — IETF RFC 9700: Best Current Practice for OAuth 2.0 Security

- Primary source: https://www.rfc-editor.org/rfc/rfc9700.html
- Freshness/version: Published January 2025; BCP 240; updates RFCs 6749, 6750, 6819. Rechecked 2026-11-05; normative source.
- Evidence locations: I1: S1, section 2.1.1; I2: S1, section 2.2.2; I3: S1, section 2.3

## S2 — RFC Editor status page for RFC 9700

- Primary source: https://www.rfc-editor.org/info/rfc9700/
- Freshness/version: Status page rechecked 2026-11-05; use as revalidation entry point. No assertion that all errata have been audited.
- Evidence locations: Freshness/status context only; no technical claim depends on this page.

Evidence is paraphrased. Original angles and proposed exercises are analyst synthesis, not claims that the sources endorse them. Sources are documentation evidence; no runtime experiments were conducted.

I4: S1 §2.1.1 (challenge method and verifier secrecy). I5–I6: S1 §4.14.2 (rotation sequence, replay detection, active-token revocation, fresh grant and issuance risk assessment). First-use timeline, access-token residual questions and recovery worksheet are analyst synthesis; no provider-specific revocation guarantee. S2 metadata rechecked 2026-11-05; no exhaustive errata audit claimed.
