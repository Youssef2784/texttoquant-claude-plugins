# TextToQuant — Claude Code plugin

Backtest trading strategies written in plain English on real market data, from inside Claude Code. Graded results with honesty flags, parameter sweeps and walk-forward tests, regime analysis, custom indicators (JavaScript, Python, Pine Script, CSV), multi-asset portfolios, Pine Script export and shareable interactive reports.

## Install

```
/plugin marketplace add Youssef2784/texttoquant-claude-plugins
/plugin install texttoquant@texttoquant
```

The first tool call opens a browser window to sign in to your TextToQuant account (free tier at https://www.texttoquant.com) and approve the connection. Then:

> Backtest buying BTCUSDT on the 1d chart when RSI(14) crosses above 30, take profit 8%, stop loss 4%, from 2022 to 2025

## What the plugin adds

- the `texttoquant` MCP server (remote, OAuth) — 77 tools: parse / run / show a backtest, robustness analyses, edge by regime, overfit verdict, custom indicators, portfolios, market scan, Pine export, share links
- a `texttoquant` skill that teaches Claude how to read a result honestly (trade count, flags, grade, then numbers), when to stress-test, and what bills credits

Runs use the credits of your own TextToQuant account. Research and education only: nothing is traded and nothing is purchased through the plugin.

## Links

- Website: https://www.texttoquant.com · Docs: https://www.texttoquant.com/docs/api/mcp
- Privacy: https://www.texttoquant.com/privacy · Terms: https://www.texttoquant.com/terms · Support: https://www.texttoquant.com/security
