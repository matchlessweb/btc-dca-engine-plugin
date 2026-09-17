# BTC DCA Engine — Claude plugin

Ask what a dollar-cost-averaging plan would have been worth, and get an answer computed from real
price history, with a link that reopens the run.

> *"What would $50 a week into Bitcoin since January 2018 be worth today?"*
> → $22,750 invested across 455 purchases, worth $107,091 at the close of 16 September 2026, plus a
> link that opens the same run in the web app.

This repository is the plugin wrapper only. It contains no simulation code: the engine runs at
[btcdcaengine.com](https://btcdcaengine.com), and the plugin points Claude at its MCP endpoint.

## What you get

Four read-only tools:

| Tool | What it does |
|---|---|
| `run_dca` | Simulates one plan: asset, amount, schedule, start date. Returns what was invested, what it is worth, the returns, the units held, and optional per-purchase rows. |
| `compare_plans` | Runs several plans over the same data and ranks them by final value. |
| `list_assets` | Every asset available, with the first and last date its price series covers. |
| `data_status` | The data vintage and the refresh schedule. |

Plus a skill that teaches Claude how to compose a sound run and report it honestly, and a `/dca`
command for one-line requests.

## Install

```
/plugin install btc-dca-engine
```

Or point Claude Code at this repository directly:

```
claude plugin marketplace add matchlessweb/btc-dca-engine-plugin
```

No account, key or sign-in is needed. See [SETUP.md](SETUP.md) for allowances and for connecting a
paid account.

## What it will not do

- It does not trade, hold funds, take payments, or connect to an exchange or a wallet.
- It does not forecast. Every figure is arithmetic over prices that have already happened.
- It is not advice. The results carry that note, and so should any summary of them.

## Where the numbers come from

Daily closes for crypto, equity indices and commodities; inflation and rate series from the
St. Louis Fed (FRED); the Fear & Greed index from alternative.me. Each result names its sources, and
the [sources page](https://btcdcaengine.com/sources) lists them with their update times. Crypto data
runs to the last completed UTC day, so "today's value" means the last close, never a moving intraday
price.

## Privacy

The endpoint is anonymous by default. Calls are counted, never identified: the daily allowance is
tracked against a salted hash of the calling address, and the usage statistics record the tool, the
outcome and the timing — never the plan, the figures or the caller.
[Privacy policy](https://btcdcaengine.com/legal/privacy) ·
[Terms](https://btcdcaengine.com/legal/terms)

## Support

[support@btcdcaengine.com](mailto:support@btcdcaengine.com) ·
[Connection guide](https://btcdcaengine.com/docs?article=agent_access) ·
[Tool reference](https://btcdcaengine.com/docs?article=mcp_tools) ·
[Limits and troubleshooting](https://btcdcaengine.com/docs?article=mcp_troubleshooting)

Built by [Matchless Web, LLC](https://matchlessweb.com). MIT licensed — see [LICENSE](LICENSE).
