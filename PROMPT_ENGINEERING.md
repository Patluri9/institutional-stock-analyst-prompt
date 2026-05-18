# Prompt Engineering — How This Was Built

This document explains the design decisions behind the institutional stock analysis prompt so you can understand, modify, or extend it.

---

## Core Design Principles

### 1. Search Before Analyze
The #1 failure mode of LLM stock analysis is using stale training data. The prompt forces live data retrieval as **Step 1** before any analysis begins. This is non-negotiable — an analyst using 6-month-old earnings data is worse than useless.

### 2. Structured Sections = Auditable Output
Each section is distinct and labeled. This lets you:
- Skip sections you don't care about
- Compare outputs across tickers in the same format
- Spot when a section has low-confidence data

### 3. Signal Over Comfort
Disclaimers and hedging language were deliberately removed. Real institutional research doesn't say "this is not financial advice" every paragraph — it says "here's the risk, here's the setup, here's the invalidation." The prompt mimics that tone.

### 4. Auto-Discovery Over User Input
Earlier versions of this prompt asked the user to provide competitors. This was a bad UX — most users don't know the competitive landscape. The prompt now instructs the model to auto-identify peers, which produces better and more surprising competitive analysis.

### 5. Conviction Score as a Forcing Function
The 1–10 conviction score forces the model to synthesize everything into a single directional view. It also creates accountability — high-conviction calls should be tracked differently than low-conviction ones.

---

## Section-by-Section Design Rationale

### Live Data Retrieval
- Forces web search before analysis
- Checklist format ensures nothing is missed
- Explicitly includes insider transactions and institutional ownership — often overlooked

### Business Thesis
- Kept intentionally short — if you can't explain the business model in 1–2 sentences, the model should flag that as a risk
- "AI exposure — real or narrative?" is deliberate: many stocks claimed AI exposure in 2023–2024 with no revenue impact

### Peer Discovery
- The model is instructed to consider hyperscalers and open-source threats — two categories retail analysts miss
- Comparison is normalized across the same metrics for every peer
- The final verdict ("is this the best play in the group?") is often the most useful output

### Fundamental Research
- SBC as % of revenue is flagged explicitly — this dilution metric is under-discussed in retail research
- "What is management NOT discussing?" is one of the highest-signal questions in the prompt — good models pick up on conspicuous omissions in earnings calls

### Technical Analysis
- Uses the 21 EMA (institutional short-term trend), 34 EMA (Fibonacci-based), 50 SMA (institutional medium-term), 200 SMA (secular trend)
- RSI + MACD provides momentum confirmation, not just trend
- "Overextended vs. healthy pullback" framing helps avoid chasing

### Options Flow
- IV Rank tells you if options are cheap or expensive before recommending a strategy
- Gamma exposure is included because dealer hedging can trap price at key strikes — this is a mechanical, non-fundamental factor most retail investors miss

### Trading Plan
- The table format is intentional — forces specificity. "I'm bullish" is not a plan. "$247 entry, $231 stop, $275 T1, $310 T2, 2.5:1 R/R" is a plan.
- Position sizing guidance is included because risk management is part of the trade

---

## Prompt Variants You Can Build

### Earnings Play Variant
Add after Step 1:
> "This is an earnings setup. Analyze the stock specifically for a pre/post earnings trade. What is the expected move? What is the options strategy? What are the historical beat/miss patterns?"

### Sector Rotation Variant
Replace the ticker section with:
> "Identify the best risk-adjusted stock to buy in [SECTOR] right now for a 30–90 day swing trade. Screen across fundamentals, technicals, and flow. Present the top 3 candidates with a final recommendation."

### Short Thesis Variant
Add to instructions:
> "Build a short thesis. Identify the catalyst for decline, the timeline, the borrow availability, and the risk of a short squeeze. What is the short invalidation?"

### Portfolio Review Variant
> "Review this portfolio: [list of tickers and position sizes]. Identify the top 3 risks, overlapping exposures, and which positions to reduce or eliminate."

---

## Token Efficiency Notes

The prompt is designed to be token-efficient despite covering 10 sections:
- Bullets force compression
- "Max 2–3 lines per section" instruction cuts filler
- "Flag [LOW CONFIDENCE] rather than explaining uncertainty" saves tokens
- Final output is a summary, not a repeat of all prior sections

On Claude Sonnet 4.6 with web search, full analysis typically runs 2,000–4,000 tokens in output.

---

## Known Limitations

- **Options flow accuracy**: LLMs retrieve summarized flow data, not raw tape. Dark pool and gamma exposure data should be verified on Unusual Whales or Market Chameleon.
- **Small cap coverage**: Thin press coverage means lower quality analysis on sub-$500M market cap stocks.
- **Non-US markets**: The prompt was built for US-listed equities. For international stocks, add "Convert all figures to USD equivalents and note FX assumptions."
- **Pre-revenue companies**: Sections on earnings quality and margins will be sparse. The prompt handles this gracefully but flag it.
