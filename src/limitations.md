# Limitations

- Testnet only. Network resets can remove contract addresses and history.
- No real business pilot, customer, partner or mainnet deployment.
- Synthetic deployment does not prove a browser-to-wallet payment flow.
- No decimals lookup, token whitelist, trustline creation, balance check, fiat
  conversion or assurance that a configured token is legitimate.
- No receipt pagination or payer discovery by account. Know the numeric invoice
  ID; a receipt has a bounded distinct-payer list.
- No archived-record restoration flow or public TTL-extension entrypoint.
- No backend, notifications, PDFs, platform fees or invoice document storage.
- No legal enforcement, escrow, dispute resolution or proof of service delivery.
- No external audit or assurance for real funds.
- The app dependency audit on October 8, 2026 reports 19 advisories (13 low,
  six moderate). They remain unresolved; no high or critical advisories were
  reported. The main JavaScript chunk is above Vite's 500 kB warning threshold.
- Automated DOM accessibility checks do not establish screen-reader, color
  contrast, device or assistive-technology support.

The relevant source is contract `src/lib.rs`, `src/invoices.rs`, `src/storage.rs`
and app `src/pages/Workspace.tsx`, `src/lib/contract.ts`, `src/lib/forms.ts`.
Anything absent from these entrypoints or explicitly listed as pending must not
be described as a completed feature.
