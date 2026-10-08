# invoicepay — invoices on Stellar testnet

Status: **code-grounded mdBook implemented.** The contract and browser workspace
implement v0 creation, partial payment, cancellation, refund and receipt lookup.
Testnet only, no real money, **no real business pilot has happened**. A synthetic
demonstration deployment exists; a browser wallet payment still needs manual
verification. Do not use this project with real funds.

invoicepay is a Stellar/Soroban project in three repositories:

| Repo | Purpose | Status |
|---|---|---|
| `invoicepay-contracts` | Soroban contract (Rust) | implemented; synthetic testnet demonstration |
| `invoicepay-app` | web app (Vite + React + TypeScript) | v0 flows implemented; manual wallet demonstration pending |
| `invoicepay-docs` | mdBook documentation | book and offline link checks implemented |


## What is here now

An [mdBook table of contents](src/SUMMARY.md), code-grounded scope and architecture,
privacy, threat model, limitations, [app instructions](src/app-guide.md),
[testnet and explorer instructions](src/deployment.md), testing and future
pilot playbook. Repository governance:
[AGENTS.md](AGENTS.md) (the rulebook for agents and humans),
[CONTRIBUTING.md](CONTRIBUTING.md), [ROADMAP.md](ROADMAP.md) (what v0 will be,
from the project's playbook section), MIT [LICENSE](LICENSE), `.gitignore`,
`.gitattributes` (LF everywhere).

## Check the book

```sh
node --test scripts/check-links.test.mjs
node scripts/check-links.mjs
mdbook build
```

The dependency-free checker validates local Markdown paths, anchors and SUMMARY
entries. Its tests also ensure workflow targets resolve while hidden private
state stays excluded. External websites are not fetched.
Local verification on October 8, 2026: **14 checker tests passed**, and **29
relative links across 16 Markdown files** resolved.
CI installs mdBook and builds the book in [.github/workflows/docs.yml](.github/workflows/docs.yml).
Workflow configuration does not establish a passing remote run.

## What v0 will be

See [product scope](src/prd.md) and [ROADMAP.md](ROADMAP.md). The book documents
actual code entrypoints rather than features merely proposed in the playbook.

## Honest limitations

- No external security audit or assurance for real funds.
- Deployment alone does not prove a browser-to-wallet payment flow.
- mdBook is not installed locally; the offline checker tests are local evidence,
  while the configured book-build workflow awaits publication and remote results.
- [Verification still needed](src/todo.md) records manual and integration checks.
- No pilot has happened and none is claimed anywhere in these repositories.
