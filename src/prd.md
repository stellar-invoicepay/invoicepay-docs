# Product scope

The intended user is a freelancer and a client who want to inspect payment
history without publishing the invoice document. This is an intended audience,
not a claim of existing users.

| Task | Implemented behavior | Code |
| --- | --- | --- |
| Create | One SEP-41 token, positive raw amount, future deadline, optional allowed payer, 32-byte document hash | `Contract::create_invoice` |
| Pay | Partial payments up to the remaining balance; payer authorization | `invoices::pay` |
| Cancel | Freelancer authorization, only before any payment ever occurred | `invoices::cancel` |
| Refund | Freelancer's token balance, bounded by a payer's net payment | `invoices::refund` |
| Inspect | Invoice fields and bounded payer receipt | `get_invoice`, `receipt` |

The app presents the same scope in `src/pages/Workspace.tsx`, with input checks
in `src/lib/forms.ts`, `amount.ts`, `reference.ts` and `validation.ts`.

No platform fee, fiat conversion, invoice PDF, notifications, backend, account
index, pagination, live USDC integration, property tests or public TTL-extension
entrypoint is implemented. The token address is configurable; describing the
project as USDC-only would be inaccurate.
