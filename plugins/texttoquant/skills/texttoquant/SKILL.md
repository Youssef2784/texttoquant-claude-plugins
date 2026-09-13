---
name: texttoquant
description: Backtest a trading strategy described in plain English on real market data with the TextToQuant MCP server — parse, run, read the graded result honestly, stress-test it, and share the interactive report. Use whenever the user wants to backtest, evaluate, compare, or stress-test a trading idea, author a custom indicator, or scan the crypto market.
---

# TextToQuant

Every tool below is served by the `texttoquant` MCP server (remote, OAuth). The first call opens a browser sign-in to the user's own TextToQuant account; runs spend that account's credits.

## Core flow
1. `describe_capabilities` before authoring — the strategy vocabulary (assets, timeframes, indicators, exits, sizing).
2. `parse_strategy` structures the idea. Read it back with `explain_parse` and confirm with the user before spending a credit.
3. `run_backtest` runs it (bills one credit). `show_backtest` renders the run as a chart image — show it first, then interpret.
4. Always offer the full page: `share_backtest` returns a private, revocable link; present it as `[Open the full interactive report](url)`.

## Be honest
Every result carries a grade and honesty flags (zero fees, missing stops, thin sample). State them plainly. Fewer than 30 trades proves nothing — say so. Report in this order: trade count, flags, grade, numbers. Never present a single backtest as evidence of a tradable edge.

## Costs and recovery
`run_backtest`, `edit_backtest`, `filter_by_context`, `start_analysis`, `run_portfolio` bill credits. Call `get_usage` before batch work and confirm any billed call the user did not explicitly ask for. Pass an `idempotencyKey` when you might retry. A long run keeps going if a call times out — recover it with `list_backtests`, never resubmit.

## Robustness
After a promising run, suggest a sensitivity sweep or walk-forward (`start_analysis` → poll `get_analysis` → `show_analysis`). Edge at one parameter value is curve fit; `get_overfit_verdict` gives the deflated-Sharpe call.

## Edge by regime
Price-action blocks (Trend Up, Trend Down, Quiet Range, Volatile Chop) → `get_regime_edge`. Indicator buckets (RSI, Williams %R, a custom indicator) → `show_context`. Both accept `basis`; pass it, do not guess.

## Custom indicators
Author in JavaScript or Python (`validate_*` → `preview_*` → `save_*`), Pine Script (`validate_indicator` → `preview_indicator` → `save_pine_indicator`), or upload CSV. Names from `list_indicators` go in `parse_strategy.customIndicatorHints` and `run_backtest.savedIndicatorMapping`, with explicit start and end dates.

## Portfolios and market
`parse_portfolio` → `run_portfolio` → `get_portfolio` → `show_portfolio` for shared-capital multi-asset books. `scan_market`, `market_regime`, `market_sectors`, `token_stats` for the crypto screener.

Research and education only: nothing is traded and nothing is bought through these tools.
