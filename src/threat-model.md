# Threat model

This is a code review aid, not a security audit or assurance for real funds.

| STRIDE category | Risk and implemented boundary | Remaining limitation |
| --- | --- | --- |
| Spoofing | Contract entrypoints require payer or freelancer authorization; wallet signs | Compromised wallet/device or misleading wallet prompt remains possible |
| Tampering | On-chain amount, due-date, client restriction, overpayment and refund checks | Browser data may be stale; contract checks are authoritative |
| Repudiation | Public transaction hashes, events and receipt totals | Does not prove real-world delivery, identity or legal agreement |
| Information disclosure | Off-chain documents, only opaque hash accepted by app | Addresses, amounts and timing public; predictable hashes can be guessed |
| Denial of service | Distinct payer count is bounded; RPC reads have bounded retries and timeouts | Provider outages, archived records, reset or exhausted ledger resources remain possible |
| Elevation of privilege | Cancellation/refund authorization belongs to freelancer | No recovery, dispute resolution or role administration exists |

Sources: contract `src/invoices.rs`, `src/storage.rs`, `src/types.rs` and
`src/error_paths.rs`; app `src/lib/flow.ts`, `contract.ts`, `reference.ts` and
`src/hooks/useWallet.ts`.

Server authentication, database permissions and server-side injection are not
applicable to this no-backend version. Dependency and frontend risks still apply.
No penetration test, external audit or real-wallet browser validation is claimed.
