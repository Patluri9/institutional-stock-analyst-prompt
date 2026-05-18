# Backtest Methodology

How to validate the quality of this prompt's output before trusting it with real capital.

---

## Why Backtest a Prompt?

LLMs can produce confident-sounding analysis that is directionally wrong. Backtesting forces accountability: you track whether the thesis, entry, and direction were correct — not just whether the output sounded good.

---

## Simple Backtesting Method (No Code Required)

### Step 1 — Choose Your Test Cases
Pick 10–15 stocks across:
- At least 3 sectors
- Mix of market caps (mega, mid, small)
- Include at least 2–3 that turned out to be losers

### Step 2 — Set a Historical Date
For each stock, pick a date **at least 3 months in the past**. This is your "analysis date."

### Step 3 — Run the Prompt with Frozen Data
Tell the LLM explicitly:

> "Analyze [TICKER] as of [DATE]. Only use information available on or before that date. Do not use any information after [DATE]."

This simulates what the prompt would have produced at that point in time.

### Step 4 — Record the Output
Log:
- Directional bias (Bullish / Neutral / Bearish)
- Entry zone
- Target 1, Target 2
- Stop-loss level
- Conviction score
- 3-month outlook

### Step 5 — Compare to Actual Outcomes
Look at what actually happened in the 3 months after the analysis date:
- Did price hit the entry zone?
- Did price hit T1? T2?
- Did price hit the stop?
- Was the directional bias correct?

### Step 6 — Score Each Setup

| Outcome | Score |
|---|---|
| Hit T2+ without stopping out | +2 |
| Hit T1 without stopping out | +1 |
| Directionally correct, no clean entry | +0.5 |
| Flat / inconclusive | 0 |
| Stopped out but small loss | -0.5 |
| Full stop-out, directionally wrong | -1 |
| Catastrophic miss (wrong direction + big move) | -2 |

### Step 7 — Calculate Win Rate and Expected Value

Track:
- Win rate: % of setups that reached T1 or better
- Average R/R on winners vs. losers
- Expected Value = (Win% × Avg Win R) − (Loss% × Avg Loss R)

A positive EV over 15+ setups suggests the framework is useful.

---

## What Good Looks Like

Based on institutional swing trade frameworks:
- Win rate: 45–60% is acceptable if R/R is 2:1 or better
- Expected Value > 0.3R per trade is solid
- Conviction score correlation: track whether high-conviction (8–10) setups outperform low-conviction (4–6)

---

## What to Watch For (Failure Modes)

- **Recency bias**: The LLM may weight recent momentum too heavily
- **Narrative capture**: If a stock has a dominant narrative (e.g., "AI winner"), the model may be bullish regardless of valuation
- **Missing low-quality data**: Small-cap or international stocks may have thinner data coverage
- **Options data gaps**: Dark pool and unusual flow data is often estimated, not retrieved precisely

---

## Community Backtesting

If you run a backtest using this prompt, consider submitting your results as a PR to the `examples/` folder. Include:
- Ticker
- Analysis date
- Key outputs from the prompt
- Actual outcome at 30/60/90 days
- Score

Aggregated community data will make this framework stronger over time.

---

## Automated Backtesting (Advanced)

For those with coding ability:

1. Use the prompt via the Anthropic or OpenAI API
2. Pass in historical earnings, price, and news data (frozen to your analysis date)
3. Log the structured output (entry, stop, targets, conviction)
4. Compare against historical price data from Yahoo Finance or Polygon.io
5. Calculate P/L, win rate, and EV across your full dataset

Example libraries:
- `yfinance` — historical price data (Python)
- `backtrader` or `vectorbt` — trade simulation
- `pandas` — result aggregation

A notebook template is planned for a future version of this repo.
