# Privacy

The contract stores public wallet and token addresses, raw amounts, deadlines,
optional payer restrictions, a 32-byte document hash, cancellation status and
payer payment/refund totals. `src/types.rs` defines these fields. Events reveal
invoice creation and payment, cancellation and refund activity.

Names, email addresses, phone numbers, legal IDs, client identifiers, invoice
numbers and invoice documents must stay off-chain. The app accepts only a
64-character hexadecimal opaque reference (`src/lib/reference.ts`). This format
check cannot establish that its content is safe or private.

A hash does not anonymize a predictable document. Public observers can guess
documents or correlate wallet addresses, timing and amounts. Use synthetic data
for demonstrations; keep any real invoice data outside this project until a
partner and suitable privacy process exist.

The app has no analytics, trackers or InvoicePay backend. Wallet icons are
served locally. RPC providers and selected wallet providers can observe network
requests. The wallet kit can remember a public address; no application code asks
for or stores a private key. There is no on-chain deletion or confidentiality.
