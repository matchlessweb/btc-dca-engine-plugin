---
name: btc-dca-engine-setup
description: Setup for the BTC DCA Engine plugin. Read when the plugin is installed or activated, or when someone asks how to connect it, sign in, or use their paid account with it.
---

# Setting up BTC DCA Engine

**There is nothing to configure.** The plugin connects to `https://btcdcaengine.com/mcp` over HTTPS
and works immediately, with no account, no key and no sign-in. If the tools answer, setup is done.

Confirm it with: *"Which assets can the BTC DCA Engine simulate?"* — a list with each asset's coverage
dates means the connection is live.

## Allowances

- **No account:** 50 simulations per day per address, seven assets, two plans per comparison.
- **A free account's key:** 200 per day.
- **A paid account's key:** 1,000 per day, the full catalogue, five plans per comparison, and the
  lump-sum, inflation, Mayer Multiple, risk and buy-rule settings.

## Using a paid account

This plugin connects anonymously on purpose: an API key belongs to the person, not to a shared plugin
file, and an empty or wrong key is refused rather than quietly downgraded.

To connect with a key, create one under **Account → API keys** at
[btcdcaengine.com/app](https://btcdcaengine.com/app), then add the server yourself in addition to the
plugin:

```
claude mcp add --transport http --scope local btc-dca-pro https://btcdcaengine.com/mcp \
  --header "Authorization: Bearer <your key>"
```

Keep that in local scope so the key stays out of any repository. A key that is not live is rejected
outright, so if every call starts failing after adding one, check the key before anything else.

## If the tools do not answer

- A `405` from a browser is expected: `/mcp` speaks JSON-RPC over POST, not web pages.
- A `429` means the day's allowance is spent; it resets at 00:00 UTC.
- A refusal naming a paid feature is the server working correctly — the request needs an account.
