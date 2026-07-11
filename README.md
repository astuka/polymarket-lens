# ◎ Polymarket Lens

**Are prediction markets accurate? Where are the mispricing opportunities?**

🔗 **Live:** [https://astuka.github.io/polymarket-lens/](https://astuka.github.io/polymarket-lens/)

A single-page analytical dashboard that pulls live data from [Polymarket's](https://polymarket.com) public APIs and answers two questions:

1. **How well-calibrated are crowd-sourced prediction markets?** — Do events priced at 30% actually happen 30% of the time?
2. **Where do mispricing opportunities live?** — Which resolved markets were most wrong, and which active markets have the widest spreads?

## Design Philosophy

The UI follows the academic minimalist tradition of [LessWrong](https://lesswrong.com) and [gwern.net](https://gwern.net): serif typography, monochrome palette, dense prose, collapsible detail sections, and no gratuitous visuals. The content is the interface.

## Features

### §1 Calibration
Fetches all resolved markets (≥$5K volume), reconstructs pre-resolution probabilities using the `oneMonthPriceChange` field, and plots them on a calibration chart with Brier score, directional accuracy, and mean surprise. Collapsible per-bin breakdown shows exactly where the market over- and under-confident.

### §2 Where the Market Was Wrong
Table of the 25 resolved markets with the largest gap between predicted probability and actual outcome, plus a pattern analysis (high-confidence misses vs. low-confidence hits, base-rate neglect in the tails).

### §3 Active Mispricing Opportunities
Live bid-ask spreads for active markets — widest (disagreement = opportunity) and tightest (consensus = priced in).

### §4 Methodology
Full transparency on data sources, calibration method, Brier score formula, and limitations.

## Architecture

```
index.html     ← everything (HTML + CSS + JS in one file)
```

- **No backend.** All API calls happen client-side from the browser.
- **No dependencies.** No npm, no build step, no frameworks. Vanilla HTML/CSS/JS.
- **No API keys.** Polymarket's Gamma API is fully public with permissive CORS.
- **No tracking.** No analytics, no cookies, no third-party scripts.
- **Dark mode.** Respects `prefers-color-scheme`.

## Run Locally

```bash
git clone https://github.com/astuka/polymarket-lens.git
cd polymarket-lens
python3 -m http.server 8000
# Visit http://localhost:8000
```

## License

MIT — see [LICENSE](LICENSE).

## Links

- 📦 [Source on GitHub](https://github.com/astuka/polymarket-lens)
- ✍️ [Substack](https://astukari.substack.com)
- 💬 [Discord](https://discord.gg/xh6meZFhH7)
- 🔗 [Data Source: Polymarket](https://polymarket.com)

---

*Independent project, not affiliated with Polymarket.*
