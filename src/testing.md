# Testing

Run these checks in `invoicepay-app`:

```sh
npm ci
npm run lint
npm run typecheck
npm test -- --maxWorkers=1
npm run build
```

Tests cover raw integer limits, address kinds, future deadlines, opaque reference
validation, configured-network refusal, error-table wording, invoice balance and
deadline semantics, wrong-network and abandoned-session write guards, pending
action lifecycle, lookup invalidation and labelled controls. Test code lives next
to its modules under `src/`. Mocks exercise failure paths without submitting to
the network. Axe tests disable color contrast because the DOM test environment
cannot assess rendered colors.

The CI workflow `.github/workflows/web.yml` runs these same commands on Node 24.
A configured workflow is not evidence of a successful remote CI run.

For the contract, run `cargo fmt --check`, `cargo clippy --locked --all-targets
-- -D warnings`, `cargo test --locked`, `node --test scripts/check-errors.test.mjs`
and `node scripts/check-errors.mjs` in `invoicepay-contracts`. The receipt-index
TTL regression belongs to the contract suite.

For this book:

```sh
node --test scripts/check-links.test.mjs
node scripts/check-links.mjs
mdbook build
```

The link checker verifies relative Markdown targets and anchors offline.
External links are not fetched. Local logs and actual check results belong in
the workspace submission evidence; this page states reproducible checks without
inventing counts or claiming a manual wallet test.
