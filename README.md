# End-to-End Stock Market Analytics Dashboard

A fully automated analytics pipeline that transforms raw market data into interactive financial insights. Built in Python using yfinance, Pandas, and Plotly.

![Python](https://img.shields.io/badge/Python-3.8+-blue) ![Pandas](https://img.shields.io/badge/Pandas-2.0+-green) ![Plotly](https://img.shields.io/badge/Plotly-5.0+-purple)

**[Portfolio](https://derrickscottux-collab.github.io/) · [LinkedIn](https://www.linkedin.com/in/derrick-scott-980109236/)**

---

## Overview

This project started as an IBM Data Analytics guided notebook covering basic stock visualization for Tesla and GameStop. It evolved into a complete analytics pipeline with modular architecture, a validation system, five financial metrics, nine interactive visualizations, benchmark comparison, automated insight generation, and a full export system.

The key design principle: **nothing is hardcoded**. Change the tickers or date range in the config and every chart, metric, and insight regenerates automatically from scratch.

---

## Pipeline Architecture

```
Configuration → Data Extraction → Validation & Structuring → Quantitative Analysis
     → Visualization → Insight Generation → Export & Reporting
```

Each stage has a clear input and output. Nothing downstream runs without the stage before it completing cleanly.

---

## Features

- **Centralized config layer** — tickers, date range, colors, moving average windows, and risk-free rate all live in one dictionary
- **Dual data extraction** — yfinance API for OHLCV price data, BeautifulSoup web scraping for quarterly revenue
- **Caching system** — downloaded data is stored locally so repeated runs don't re-fetch
- **Validation & structuring** — checks for missing values, date gaps, and invalid records before any analysis runs
- **5 financial metrics** — Total Return, Annualized Volatility, Sharpe Ratio, Max Drawdown, CAGR
- **9 interactive visualizations** — all exported as standalone HTML (no Python required to view)
- **Automated insight generation** — plain-language findings written by code, not manually typed
- **Full export system** — CSVs, insights text file, and HTML dashboards

---

## Visualizations

| File | Chart |
|------|-------|
| `01_normalized_performance.html` | Normalized price performance (base = 100) vs S&P 500 |
| `02_revenue_vs_price_TSLA.html` | Tesla quarterly revenue vs stock price |
| `02_revenue_vs_price_GME.html` | GameStop quarterly revenue vs stock price |
| `03_price_volume_ma_TSLA.html` | Tesla price, 50/200-day MAs, volume, golden/death crosses |
| `03_price_volume_ma_GME.html` | GameStop price, 50/200-day MAs, volume, golden/death crosses |
| `04_correlation_heatmap.html` | Pearson correlation matrix of daily returns |
| `05_returns_distribution.html` | Daily return distributions with KDE curves |
| `06_monthly_heatmap.html` | Monthly return heatmap by stock and year |
| `07_alpha_vs_benchmark.html` | Rolling 1-year alpha vs S&P 500 benchmark |

---

## Stocks Analyzed

| Ticker | Company | Period |
|--------|---------|--------|
| TSLA | Tesla | Jan 2019 – present |
| GME | GameStop | Jan 2019 – present |
| AAPL | Apple | Jan 2019 – present |
| MSFT | Microsoft | Jan 2019 – present |
| ^GSPC | S&P 500 (benchmark) | Jan 2019 – present |

---

## Key Findings

- **Tesla** delivered the highest total return at +1,878%, roughly 10x the S&P 500 over the same period
- **GameStop** peaked at 2,749x its starting value during the January 2021 short squeeze — a +1,625% monthly return — then gave most of it back
- **Apple** had the best risk-adjusted performance with a Sharpe Ratio of 1.01, outperforming Tesla on a return-per-unit-of-risk basis
- **GameStop's** correlation with every other stock in the group was essentially noise (0.12–0.17), driven by retail sentiment rather than market-wide factors
- **2022** is the clearest macro signal in the data — January through June was broadly red across all four stocks as the Fed began its most aggressive rate hiking cycle in decades

---

## Project Structure

```
stock-analytics-pipeline/
│
├── Stock_Analysis_Dashboard_Portfolio.ipynb   # Main notebook
│
├── figures/                                   # Interactive HTML charts
│   ├── 01_normalized_performance.html
│   ├── 02_revenue_vs_price_TSLA.html
│   ├── 02_revenue_vs_price_GME.html
│   ├── 03_price_volume_ma_TSLA.html
│   ├── 03_price_volume_ma_GME.html
│   ├── 04_correlation_heatmap.html
│   ├── 05_returns_distribution.html
│   ├── 06_monthly_heatmap.html
│   └── 07_alpha_vs_benchmark.html
│
├── exports/                                   # Data exports
│   ├── metrics_summary.csv
│   ├── all_close_prices.csv
│   ├── insights.txt
│   ├── TSLA_revenue_data.csv
│   └── GME_revenue_data.csv
│
├── data/                                      # Cached price data (git-ignored)
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Getting Started

### Install dependencies

```bash
pip install -r requirements.txt
```

### Run

1. Clone the repo
   ```bash
   git clone https://github.com/derrickscottux-collab/stock-analytics-pipeline.git
   ```
2. Open `Stock_Analysis_Dashboard_Portfolio.ipynb` in Jupyter or VS Code
3. Optionally edit the `CONFIG` dictionary at the top to change tickers or date range
4. Run all cells — **Kernel → Restart & Run All**

All charts, metrics, exports, and insights will regenerate automatically.

### Changing the Tickers

Edit the `CONFIG` block at the top of the notebook:

```python
CONFIG = {
    "tickers": ["AAPL", "GOOGL", "AMZN", "META"],
    "ticker_names": {
        "AAPL": "Apple",
        "GOOGL": "Google",
        "AMZN": "Amazon",
        "META": "Meta"
    },
    "start_date": "2020-01-01",
    ...
}
```

Everything downstream updates automatically.

---

## Dependencies

```
yfinance
pandas
numpy
plotly
matplotlib
seaborn
scipy
requests
beautifulsoup4
nbformat
```

---

## Data Sources

- **Price & volume data**: [yfinance](https://github.com/ranaroussi/yfinance) (Yahoo Finance API)
- **Revenue data**: IBM Skills Network static course archive (web scraped via BeautifulSoup) — covers Tesla through Q3 2022, GameStop through Q1 2020

---

## Origin

Expanded from the IBM Data Analytics Professional Certificate capstone notebook. The original covered basic revenue and price visualization for two stocks. This version adds modular architecture, a validation system, four additional stocks, a full financial metrics engine, benchmark comparison, nine visualizations, automated insight generation, and a complete export pipeline.

---

## Author

**Derrick Scott**
[Portfolio](https://derrickscottux-collab.github.io/) · [LinkedIn](https://www.linkedin.com/in/derrick-scott-980109236/) · [GitHub](https://github.com/derrickscottux-collab)

---

## License

This repository does not currently have a formal license. If you would like to use or adapt this project, please reach out via [LinkedIn](https://www.linkedin.com/in/derrick-scott-980109236/).
