# 📊 Institutional Stock Analysis Prompt

> **The prompt that replaces "do your own research."**

Most stock influencers give you a thesis, then hide behind "DYOR." This repo gives you the actual research framework — the same one institutional analysts use — so you can evaluate any stock yourself in minutes.

---

## ⚡ Quick Start

1. Open [Claude](https://claude.ai), [ChatGPT](https://chatgpt.com), or any LLM with **web search enabled**
2. Copy the prompt from [`prompts/STOCK_ANALYSIS_PROMPT.md`](prompts/STOCK_ANALYSIS_PROMPT.md)
3. Replace `[TICKER]` with your stock symbol (e.g., `NVDA`, `AAPL`, `TSLA`)
4. Paste and run

That's it. No code. No API. No setup.

---

## 🗂️ Repo Structure

```
stock-analyst-prompt/
├── prompts/
│   ├── STOCK_ANALYSIS_PROMPT.md   ← Full institutional-grade prompt (use this)
│   └── QUICK_ANALYSIS_PROMPT.md   ← Lite version for fast scans
├── examples/
│   └── EXAMPLE_OUTPUT.md          ← Sample output so you know what to expect
├── docs/
│   ├── HOW_IT_WORKS.md            ← What each section analyzes and why
│   ├── BACKTEST_METHODOLOGY.md    ← How to validate prompt quality yourself
│   └── PROMPT_ENGINEERING.md     ← How the prompt was built
├── web/
│   └── index.html                 ← Simple browser UI (open and use locally)
└── README.md
```

---

## 🧠 What the Prompt Covers

| Section | What It Does |
|---|---|
| **Live Data Retrieval** | Searches for current price, earnings, news, analyst actions before analyzing |
| **Business Thesis** | Revenue model, AI exposure, TAM, valuation verdict |
| **Peer Discovery** | Auto-finds competitors, compares margins, growth, moat durability |
| **Fundamental Research** | Earnings quality, SBC, debt, red flags, regulatory risk |
| **Competitive Positioning** | Moat strength, commoditization risk, hyperscaler threat |
| **Macro Risk Layer** | Rate sensitivity, FX, China, semiconductor cycle, AI capex risk |
| **Technical Analysis** | EMAs, RSI, MACD, support/resistance, entry zones |
| **Options & Flow** | Unusual activity, IV rank, gamma exposure, dark pool |
| **Sentiment** | Retail + institutional positioning, crowding risk |
| **Trading Plan** | Entry, stop, targets, R/R ratio, position sizing guidance |
| **Final Summary** | Bull/bear case, conviction score, thesis invalidation |

---

## 📌 Why This Exists

Every week, thousands of people watch stock recommendation videos that end with *"do your own research."*

The problem: most retail investors don't have a research framework. They don't know what to look at, in what order, or what actually matters. So they either:
- Trust the influencer blindly
- Get overwhelmed and don't research at all
- Research the wrong things (price alone, Reddit sentiment)

This prompt gives anyone access to the same analytical structure that institutional desks use — for free, in any LLM.

---

## 🛠️ How to Use It (Step by Step)

### Option 1 — Claude (Recommended)
Claude with web search has the best results because it retrieves live data.
1. Go to [claude.ai](https://claude.ai)
2. Enable web search (toggle in the chat bar)
3. Paste the full prompt with your ticker
4. Let it run — expect a 3–5 minute response

### Option 2 — ChatGPT
1. Go to [chatgpt.com](https://chatgpt.com) (GPT-4o with search)
2. Paste the prompt — it will auto-search for live data

### Option 3 — API / Automation
See [`docs/PROMPT_ENGINEERING.md`](docs/PROMPT_ENGINEERING.md) for how to integrate this into your own tools, scripts, or dashboards.

### Option 4 — Local Web UI
Open `web/index.html` in your browser for a simple interface that lets you enter a ticker and copies the pre-filled prompt to clipboard.

---

## ⚠️ Important Notes

- **Enable web search** in your LLM — without it, the model uses training data which may be months old
- Works best with: Claude (Sonnet/Opus), GPT-4o, Gemini 1.5 Pro
- The AI is a research assistant, not a financial advisor — use its output as input to your own judgment
- Accuracy improves with models that have real-time search; older models or those without search will give less accurate live data

---

## 🔄 How to Validate / Backtest

See [`docs/BACKTEST_METHODOLOGY.md`](docs/BACKTEST_METHODOLOGY.md) for a simple method to test the prompt's historical accuracy on past setups.

The short version:
1. Pick a stock, pick a historical date (e.g., 3 months ago)
2. Run the prompt using only data available on that date
3. Compare the predicted direction, entry, and targets to what actually happened
4. Track a paper portfolio of 10–20 setups

---

## 🤝 Contributing

Pull requests welcome. Ideas:
- Sector-specific prompt variants (biotech, financials, commodities)
- Non-US market versions (LSE, TSX, ASX, NSE)
- Earnings season variant (pre/post earnings setups)
- Backtesting results from the community

Open an issue to discuss before submitting a large PR.

---

## 📣 Share This

If this helped you, share it on LinkedIn or X. The goal is to make institutional-quality research accessible to everyone — not just those with Bloomberg terminals.

---

## 📄 License

MIT — free to use, modify, and share. Attribution appreciated but not required.

---

*Built by someone tired of "do your own research" without a framework to do it.*
