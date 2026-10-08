# InvoicePay

InvoicePay records an opaque invoice reference and its payment history on Stellar
testnet. The invoice document remains off-chain. Tokens move directly from payer
to freelancer, and refunds move back from the freelancer's own balance.

The contract implements creation, partial payment, cancellation, refund, invoice
lookup and a bounded receipt. The React app implements these same operations.
The book describes code, not a business pilot. **No pilot has happened. Testnet
only; do not use real money.**

Sources: [contract entrypoints](https://github.com/stellar-invoicepay/invoicepay-contracts/blob/main/src/lib.rs),
[invoice logic](https://github.com/stellar-invoicepay/invoicepay-contracts/blob/main/src/invoices.rs),
[app workspace](https://github.com/stellar-invoicepay/invoicepay-app/blob/main/src/pages/Workspace.tsx).

Read [limitations](limitations.md) before attempting a demonstration. Local files
may precede GitHub publication; use the checked-out source as the source of truth.
