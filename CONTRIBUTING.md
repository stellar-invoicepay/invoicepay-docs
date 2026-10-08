# Contributing

Thanks for helping with `invoicepay`. **Read [AGENTS.md](AGENTS.md) first** — it is
the rulebook for this repository, for people and for AI agents alike. This page
is a shorter orientation.

## Before you change anything

- **Testnet only.** Never write anything that suggests mainnet use.
- **Only a synthetic testnet demonstration is deployed; no pilot has happened.**
  Describe public identifiers from [the deployment record](src/deployment.md)
  accurately. Never invent users, partners or transaction outcomes.
- **No personal data, ever** — not in examples, not in tests, not in issue
  drafts. Use obvious placeholders.
- **Never commit `.env`**, a secret key or a seed phrase.

## Commits

- One logical change per commit; subject `type: imperative summary`, 72
  characters or fewer.
- Stage by explicit file name and read the staged diff before committing.
- No "Generated with" or co-author trailers of any kind.

## Checks to run before you push

Run `node --test scripts/check-links.test.mjs`, `node scripts/check-links.mjs`
and `mdbook build` when mdBook is available. CI installs mdBook and builds the
book. Record which checks actually ran and distinguish local and remote evidence.
