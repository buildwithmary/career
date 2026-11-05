# Revision 02 finding-to-change matrix

Research Analyst | 2026-11-05 | [Execution task](/CARA/issues/CARA-2)

Scope: CAREER-4, CAREER-5 and CAREER-6 only. Revision 01 stays immutable at commit 89fd715671af670df3ebfe83154aaf33e1d316db. CAREER-3 and CAREER-7 remain revision 01. Five topics total; this is proposal revision, not production.

Input: [independent findings](/CARA/issues/CARA-3#document-findings), exact revision b7c487f4-fd7f-4543-9ff5-e8077f7d6b7d; review commit 70fb5e70e46a28a81e39154c4773f3fd4cc1648e.

| Finding | Revision 02 location/change | Evidence / remaining review obligation |
|---|---|---|
| CAREER-4: transactional writes/offsets and commit/abort visibility missing | Bounded timeline design: Kafka → Kafka row, isolation counterexample; D3–D4 | Kafka 4.1 Design, delivery semantics/transactions; re-review boundaries |
| CAREER-4: atomic-storage question too narrow | Original angle and external repair alternatives ask atomic commitment OR safe repetition | S1 external coordination/key discussion; destination atomicity and dedup remain design assumptions |
| CAREER-4: replay, destination and version assumptions | Timeline replay column and configuration assumptions | Abort resets position/state; exact patch versions required before implementation |
| CAREER-5: recovery AZ/state/start absent | Recovery worksheet AZ A/B and scheduled-after-T/delayed/expired rows | S1, S4, S5; pending reads qualified for eventual consistency |
| CAREER-5: matching/count/quota/targeting gaps | Four required/two available row; sufficient-capacity row | S1 Quotas; S3 launch rules; competing open-reservation workload |
| CAREER-5: unqualified effective billing | C3 and billing footnote | S2 pricing/discount eligibility; fictional qualitative exercise |
| CAREER-6: first-use theft and detection/prevention | Credential worksheet and first-use R0/R1/A1 counterexample | RFC 9700 §§2.1.1, 4.14.2; provider behavior untested |
| CAREER-6: residual exposure and legitimate recovery | Reuse detection versus first success; fresh grant; A1 lifetime/revocation questions | §4.14.2; no automatic access-token invalidation assertion |
| CAREER-6: normative/client scope and code-only theft | Code-only model, I4–I6 and explicit I1–I3 scope recap | §§2.1.1, 2.2.2, 2.3, 4.14.2; preserve MUST/SHOULD |
| CAREER-6: issuance alternative | Risk-assessed no-refresh-token option | §4.14.2; no universal prescription |

All source pages were read/rechecked on 2026-11-05. Files contain claim-to-evidence mappings and reference/version caveats. Exercises are proposed scope only; no runtime tests, demos, exploit code or cloud resources. No independent clearance is claimed. Paul resumes CARA-4 to commission bounded re-review on the existing CARA-3 task. Human topic decisions, production approval and manual publishing gates remain. Existing subscription only; $0 additional spend.
