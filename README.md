# Casper Account Info — Manifest.network-Sarson Funds

Static hosting (via GitHub Pages) for the [Casper Account Info Standard](https://github.com/make-software/casper-account-info-standard)
files of the Sarson Funds Casper validator. cspr.live and other explorers read the validator's
display name and details from:

- `/.well-known/casper/account-info.casper.json` — Mainnet (`casper-val-1`)
- `/.well-known/casper/account-info.casper-test.json` — Testnet (`casper-test-1`)

Served at the custom domain **casper.sarsonfunds.com** (CNAME → `sarsonfund.github.io`,
DNS on Cloudflare). The domain is registered on-chain against the validator account via the
Account Info contract's `set_url` entry point — see the `account-info/` directory of the
internal `validator_casper` repo for the runbook.

Notes:

- `.nojekyll` is required — without it GitHub Pages (Jekyll) silently drops the `.well-known`
  dot-directory from the published site.
- Changing the validator name/details = edit the JSON here and push. No on-chain call needed;
  only changing the *domain* costs a `set_url` deploy (0.5 CSPR).
- The `CNAME` file is managed by GitHub Pages settings; don't remove it.
