# Architecture

The browser talks directly to Stellar RPC and the user's Stellar wallet. There
is no InvoicePay server and no secret key in the application.

`src/config.ts` validates public environment configuration through
`resolveNetworkConfig`. Only testnet is accepted. `src/lib/wallet.ts` lazy-loads
eight Stellar wallet modules and replaces their icons with local assets.

For writes, `runWrite` in `src/lib/flow.ts` checks the wallet network, prepares
the transaction, checks testnet again immediately before signing, asks the wallet
to sign, and submits. A session guard prevents abandoned actions from signing or
submitting after the workspace unmounts. A transaction already submitted cannot
be cancelled by disconnecting the wallet.

`src/lib/contract.ts` builds, simulates, assembles, submits and polls the actual
ABI. Read-only invoice and receipt calls use simulation; they do not submit a
transaction. The connected public account must exist on testnet to provide the
transaction source.

The contract's `src/invoices.rs` calls the token contract directly. It never
holds an escrow balance. `src/storage.rs` handles records and TTL behavior.
`src/types.rs` defines public errors, invoice/receipt types and events.

The app keeps IDs and token amounts as `bigint`, validates u64/i128 ranges,
and decodes records in `src/lib/invoice.ts`. It deliberately does not guess token
decimals or rebuild an archived record. Contract checks remain authoritative;
browser checks provide guidance, not authorization.

`src/lib/actions.ts` validates intended payment/refund/cancellation against the
displayed record. Submission is attempted once with a bounded timeout. Network
or confirmation uncertainty retains the transaction's exact derived hash and an
explorer link, with a warning to inspect it before retrying.
