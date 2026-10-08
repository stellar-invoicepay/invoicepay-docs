# Use the app

Use synthetic invoice documents and testnet tokens only.

1. Install Node 24 and run `npm ci` in `invoicepay-app`.
2. Copy `.env.example` to a local `.env`. Set the public contract ID from the
   [deployment record](deployment.md), keeping network `testnet`.
3. Run `npm run dev`. Connect a funded testnet wallet. The app never asks for a
   seed phrase or secret key.
4. Choose **Create an invoice**. Enter a testnet SEP-41 token contract, positive
   whole amount in the token's smallest units, future local deadline and an
   opaque 64-character hexadecimal hash. Optionally restrict payment to one
   public account. Never enter a client name, invoice number or contact detail.
5. Review the wallet's transaction details. After confirmation, keep the numeric
   invoice ID and transaction hash. Follow the explorer link.
6. Choose **Find an invoice**, enter the numeric ID and submit. The read requires
   a connected, funded source account, but does not submit a transaction.
7. Pay up to the displayed remaining balance. The freelancer can refund a payer
   from their own token balance or cancel an invoice that has never received a
   payment. Cancellation is permanent.
8. Look up the invoice again after every action to refresh its receipt. Editing
   the ID immediately clears the previous record.

Raw units matter: for a token with seven decimals, `10000000` units equals one
token. The app does **not** fetch decimals, check balances or establish trustlines.
Check these separately. An expired invoice may still show status `Open`; the
app explains separately that its payment deadline has passed.

A wallet request, simulation or pending transaction is not a confirmed payment.
If submission confirmation times out, inspect the transaction hash before retrying.
See [limitations](limitations.md).
