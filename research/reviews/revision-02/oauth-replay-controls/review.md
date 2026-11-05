# Independent technical re-review — oauth-replay-controls

Review revision: 02 | Reviewed: 2026-11-05 | Technical Reviewer

[Jira topic](https://blueinit.atlassian.net/browse/CAREER-6) | [Execution task](/CARA/issues/CARA-3)

Input: [proposal revision 02](https://github.com/buildwithmary/career/blob/1db3dd7e3e89544cf1cce89a01277a4128d44e5f/research/proposals/revision-02/oauth-replay-controls/oauth-replay-controls-revision-02-proposal.md) and [references](https://github.com/buildwithmary/career/blob/1db3dd7e3e89544cf1cce89a01277a4128d44e5f/research/proposals/revision-02/oauth-replay-controls/references.md). Manifest revision ecc434cc-6240-4ce7-b38f-71c2e6e344b2; compared with original findings revision b7c487f4-fd7f-4543-9ff5-e8077f7d6b7d and all ten finding-to-change matrix rows.

Verdict: CLEAR for explicit human topic selection with caveats. No remaining material revision-01 finding.

Matrix reconciliation: all four OAuth rows close. The code-only theft model, credential worksheet, attacker-first R0/R1/A1 sequence, delayed reuse detection, fresh-grant recovery, residual access-token questions and issuance alternative address every original acceptance condition.

I1–I6 preserve the applicable client scope and normative strength in [RFC 9700 §§2.1.1, 2.2.2, 2.3 and 4.14.2](https://www.rfc-editor.org/rfc/rfc9700.html). The first-use example is a valid inference from rotation, not a measured provider result. [RFC metadata](https://www.rfc-editor.org/info/rfc9700/) confirms January 2025 / BCP 240.

Reviewer judgment: prevention, detection and recovery are now separated clearly. Keep the distinction between a refresh-token chain response and already-issued access-token exposure; no automatic invalidation guarantee follows. Do not turn a fresh authorization grant into an unconditional password-entry requirement. Provider concurrency/grace policies and binding-key compromise deserve validation if production expands the case. No exhaustive errata audit or complete login-security assessment is claimed.

Primary sources checked 2026-11-05. Exercises remain proposals; no runtime validation. Originality means teaching synthesis, not literature novelty. Paul presents exact versions for human approve/revise/park decisions. No production approval, publishing, resources or additional spend.
