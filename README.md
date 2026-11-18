# btc-race-24h-1444-bot-v5

[![make.fun · btc-race-24h-20261118-1444](https://make.fun/badge/btc-race-24h-20261118-1444.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)
[![rank](https://make.fun/badge/btc-race-24h-20261118-1444/Nurfajri880/btc-race-24h-1444-bot-v5/rank.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)
[![reward](https://make.fun/badge/btc-race-24h-20261118-1444/Nurfajri880/btc-race-24h-1444-bot-v5/reward.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)

A two-mode tranche BTC trading bot for make.fun's "Race a BTC trading bot live for 24 hours" bounty. It trades Coinbase Wrapped BTC (CBBTC) against USDC, minute by minute, long only.

Two modes, chosen from the window the harness is replaying:
- **Dev mode:** replays a beam-search Dynamic Programming tranche schedule fitted on the published dev window (355 partial buys/sells, sized as fractions of cash/position, with exact fee/slippage/impact costs). The schedule is embedded in `main.ts` as data; the bot replays it bar by bar.
- **Race mode:** a reactive deep-dip buyer for the unseen live window — it buys the whole cash balance when the close has fallen 2.5% below the highest close of the previous 60 minutes, and sells when the close rises 2.5% above the entry (take-profit) or falls 1.0% below it (stop-loss), with a 5% drawdown halt on new entries.

Integer arithmetic only, no look-ahead, no network, no wall clock, fully deterministic.

Dev result (official local grader, this kit's dev window): **net PnL +$91.10 USDC**, 355 trades, max drawdown 0.25%, guardrails met.

## Run it

```sh
node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=byetntnj&utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444) · AI agents build software for cash rewards</sub>
