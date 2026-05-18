# Publishing to GitHub — Step by Step

## One-Time Setup (5 minutes)

### 1. Install Git
- **Mac**: `brew install git` or it's pre-installed
- **Windows**: Download from https://git-scm.com
- **Linux**: `sudo apt install git`

### 2. Create a GitHub Account
Go to https://github.com and create a free account if you don't have one.

### 3. Create the Repo on GitHub
1. Click the **+** button → "New repository"
2. Name it: `institutional-stock-analyst-prompt`
3. Description: `Institutional-grade stock analysis prompt for Claude/ChatGPT. The research framework behind "do your own research."`
4. Set to **Public**
5. Check "Add a README" — NO (you already have one)
6. Click "Create repository"

---

## Push Your Files

Open your terminal and run:

```bash
# Navigate to the repo folder
cd /path/to/stock-analyst-prompt

# Initialize git
git init

# Add all files
git add .

# First commit
git commit -m "Initial release: institutional stock analysis prompt v2.0"

# Connect to GitHub (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/institutional-stock-analyst-prompt.git

# Push
git branch -M main
git push -u origin main
```

---

## Enable GitHub Pages (Free Website)

This turns your `web/index.html` into a live website anyone can use without downloading anything.

1. Go to your repo on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under "Source" → select **main** branch
4. Under "folder" → select **/web**
5. Click **Save**

Your site will be live at:
`https://YOUR_USERNAME.github.io/institutional-stock-analyst-prompt`

It takes ~2 minutes to go live. Share this URL on LinkedIn.

---

## Recommended Repo Settings

### Topics (makes it discoverable)
In your repo, click the gear icon next to "About" and add topics:
```
stocks, investing, trading, llm-prompts, prompt-engineering, 
stock-analysis, technical-analysis, ai, chatgpt, claude
```

### Description
```
Institutional-grade stock analysis prompt. 10-section deep research covering fundamentals, technicals, options flow, sentiment & trading plan. Replaces "do your own research" with an actual framework. Works with Claude, ChatGPT, Gemini.
```

### Pin the repo
On your GitHub profile, pin this repo so it shows up when people visit your profile.

---

## LinkedIn Post Template

Here's a post optimized for LinkedIn engagement:

---

**Every stock influencer ends with "do your own research."**

But nobody tells you *how.*

So I built an open-source prompt that does what institutional analysts do — for free, in Claude or ChatGPT.

You type a ticker. The AI does 10 sections of deep research:

✅ Live price, earnings, analyst actions
✅ Business thesis & valuation verdict
✅ Auto peer discovery & competitive comparison
✅ Fundamental red flags (SBC, dilution, debt)
✅ Macro risk layer
✅ Technical analysis (EMAs, RSI, MACD, entries)
✅ Options flow & dark pool signals
✅ Sentiment & crowding risk
✅ Full trading plan with R/R ratio
✅ Bull/bear case, conviction score, thesis invalidation

The whole framework is free on GitHub.

🔗 [Your GitHub URL]
🔗 [Your GitHub Pages URL] ← just enter a ticker and copy

No code. No setup. Just paste and analyze.

---

*Built because retail investors deserve the same research framework that institutional desks use.*

#investing #stocks #trading #AI #openai #promptengineering #stockmarket #technicalanalysis #fintech

---

**Pro tips for LinkedIn reach:**
- Post Tuesday–Thursday, 8–10am your timezone
- Add a screenshot of an example output as an image (images get 3x the reach of text-only posts)
- Engage with every comment in the first 60 minutes — this boosts algorithmic reach
- Tag 2–3 finance/investing creators who might share it

---

## Staying Current

Once published, keep the prompt fresh:
- When a new model drops (Claude Opus 5, GPT-5), test and update the "tested with" section
- Add community backtest results to the `examples/` folder
- Accept PRs for sector-specific variants (biotech, commodities, etc.)

Version your updates:
```bash
git add .
git commit -m "v2.1: add earnings variant prompt"
git push
```
