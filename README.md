# ◎ Polymarket Lens

**A prediction market aggregator & visualizer — live data from Polymarket with calibration analysis, spread tracking, and "what the market got wrong" insights.**

🔗 **Live demo:** [https://astuka.github.io/polymarket-lens/](https://astuka.github.io/polymarket-lens/)

## What It Does

Polymarket Lens pulls live data from [Polymarket's](https://polymarket.com) public APIs (no API key, no backend, no tracking) and visualizes it through four lenses:

### 1. 📊 Live Markets
Real-time prices from Polymarket's most liquid active markets. Searchable, filterable by category (Politics, Crypto, Sports, Economics). Each card shows Yes/No probabilities, 24h price change, volume, and spread.

### 2. 🎯 Calibration
Fetches resolved markets and pulls their price history to answer: **did the market's probability actually predict the outcome?** A perfectly calibrated market would have all points on the diagonal line. We compute:
- **Brier Score** — the mean squared error between predicted probabilities and actual outcomes (lower is better; 0.25 = random guessing)
- **Directional Accuracy** — how often the market's >50% call was correct
- **Average Surprise** — mean gap between predicted probability and actual outcome

### 3. 📰 What the Market Got Wrong
The markets where the crowd was most surprised — the biggest gaps between expected and actual outcomes. Sorted by "surprise" = |predicted probability − resolution|. These are the stories of the market being wrong, with links to each market.

### 4. 📏 Spread Analysis
Bid-ask spreads for active markets. Wide spreads signal uncertainty or low liquidity; tight spreads indicate high-confidence pricing. Shows both the widest (most uncertain) and tightest (most confident) markets.

## Architecture

```
index.html     ← everything (HTML + CSS + JS in one file)
```

- **No backend.** All API calls happen client-side from the browser.
- **No dependencies.** No npm, no build step, no frameworks. Just vanilla HTML/CSS/JS.
- **No API keys.** Polymarket's Gamma API is fully public with permissive CORS (`access-control-allow-origin: *`).
- **No tracking.** No analytics, no cookies, no third-party scripts.

### Data Sources

| API | Base URL | Used For |
|-----|----------|----------|
| Gamma API | `gamma-api.polymarket.com` | Market discovery, events, metadata |
| CLOB API | `clob.polymarket.com` | Price history, orderbook spreads |

All endpoints are public REST (GET), return JSON, and require no authentication.

## Run Locally

```bash
git clone https://github.com/astuka/polymarket-lens.git
cd polymarket-lens
# Just open index.html in your browser, or serve it:
python3 -m http.server 8000
# Visit http://localhost:8000
```

That's it. No build step, no dependencies to install.

## Deployment

The site is deployed via [GitHub Pages](https://pages.github.com/) from the `main` branch. Any push to `main` automatically updates the live site.

## Tech Stack

- Vanilla HTML/CSS/JavaScript (zero dependencies)
- Canvas API for the calibration chart
- Polymarket public APIs for all data
- GitHub Pages for hosting

## License

MIT — see [LICENSE](LICENSE).

## Links

- 📦 [Source on GitHub](https://github.com/astuka/polymarket-lens)
- ✍️ [Author's Substack](https://jacobrobinson.substack.com)
- 💬 [Discord](https://discord.gg/7H5g9mYQ)
- 🔗 [Data Source: Polymarket](https://polymarket.com)

---

*This is an independent project and is not affiliated with Polymarket.*
