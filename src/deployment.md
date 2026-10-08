# Testnet deployment and explorer

The owner authorized demonstration deployments using synthetic data on October
8, 2026. This authorization is separate from the real pilot-partner gate.

| Public identifier | Value |
| --- | --- |
| Contract | `CCJ652VR7Y7H5KE5FUDT4FSTTN3FJECY44RJYHBW4J2BPSXVETJLTJKU` |
| Creation transaction | `ab1b0d5718a824d718996c6d9497ac56d93770897769ff19435af37b3618eb2e` |
| Wasm SHA-256 | `df77525063bda9e74fd183547895be59a3c7efd50b039cc8241d4313b316f709` |

The deployment task verified `SUCCESS` through Stellar RPC and matched the
on-chain executable's Wasm hash to the local build. No invoice payment or
refund outcome is claimed. The contract does not have a separate initialization
entrypoint; see its six methods in `src/lib.rs`.

## Inspect on Stellar Expert

1. Open [the testnet contract](https://stellar.expert/explorer/testnet/contract/CCJ652VR7Y7H5KE5FUDT4FSTTN3FJECY44RJYHBW4J2BPSXVETJLTJKU).
2. Confirm the network is **testnet**. Compare the entire contract address,
   including the last characters, with the table above.
3. Open [the creation transaction](https://stellar.expert/explorer/testnet/tx/ab1b0d5718a824d718996c6d9497ac56d93770897769ff19435af37b3618eb2e).
4. Inspect status, ledger and operation details. A successful contract-creation
   transaction establishes deployment, not invoice creation or payment.
5. The contract screen's activity may be empty until someone invokes it. This
   does not mean the creation transaction failed. Indexing can lag.
6. For an app action, open the full hash linked after confirmation. Compare
   status, contract, invocation name and events with the action you intended.
   Partial payments and refunds need separate transaction hashes.
7. Keep your public contract ID and transaction hash when reporting problems.
   Do not send a secret key, seed phrase, client detail or real invoice document.

## Configure the app

Set `VITE_STELLAR_NETWORK=testnet`, a testnet RPC URL,
`VITE_EXPLORER_BASE_URL=https://stellar.expert/explorer/testnet` and the public
address above as `VITE_CONTRACT_ID` in the app's local `.env`. Restart Vite after
changing config. The code has no built-in contract address.

Testnet resets can remove this deployment. Check availability immediately before
a demonstration. The browser-to-wallet flow still needs a manual test; see
[verification still needed](todo.md).
