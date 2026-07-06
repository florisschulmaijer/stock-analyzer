# Stock Portfolio Analysis

Personal exploratory and statistical analysis of a real stock portfolio. Covering price behavior, risk metrics, and portfolio-level performance using Python.

**Author:** Floris Schulmaijer

**Data snapshot:** July 6, 2026

---

## About This Project

This project applies statistics, probability theory, and Python skills currently being developed in the second year of a Business Analytics degree (VU Amsterdam) to a real personal stock portfolio. It combines an interest in investing with a growing focus on quantitative finance, statistical modeling, and machine learning.

Rather than using a generic dataset, the analysis is built on real holdings, so every metric and chart reflects an actual investment decision.

---

## Repository Structure

```
stock-analyzer/
├── data/
│   ├── portfolio_data.csv      # Frozen price snapshot (main portfolio)
│   └── spcx_data.csv           # Frozen price snapshot (SpaceX, since IPO)
├── portfolio.ipynb             # Main analysis notebook
├── watchlist.ipynb             # Analysis of stocks not yet owned
├── dashboard.py                      # Interactive Streamlit dashboard
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/florisschulmaijer/stock-analyzer.git
cd stock-analyzer
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Open the notebook
Open `portfolio.ipynb` in VS Code or Jupyter and run all cells.

No API keys or live downloads are required — the notebook loads directly from the frozen CSV snapshots in `data/`, so results are identical for every user, every time (see [Data & Reproducibility](#data--reproducibility)).

---

## What's Inside — Notebook Structure

**1. Data Import**
Historical daily closing prices loaded from a frozen snapshot.

**2. Exploratory Analysis**
- 2.1 Raw Stock Prices
- 2.1.1 SpaceX — Since IPO
- 2.2 Relative Growth
- 2.3 Daily Returns
- 2.4 Moving Averages (20-day / 50-day, Golden Cross / Death Cross)
- 2.5 Return Distribution (histogram + KDE)

**3. Risk & Performance Metrics**
- 3.1 Volatility (annualized standard deviation)
- 3.2 Sharpe Ratio (risk-adjusted return)
- ⬜ 3.3 Maximum Drawdown
- ⬜ 3.4 Skewness & Kurtosis
- ⬜ 3.5 Correlation Matrix
- ⬜ 3.6 Beta vs Market (S&P 500)

**4. Bootstrap Analysis** ⬜
Resampling based confidence interval for mean return.

**5. Portfolio Overview** ⬜
Combines real dollar-weighted holdings with covariance-based portfolio risk.

**6. Predictive Modelling** ⬜ *(optional, advanced)*
A simple sklearn Ridge regression pipeline predicting next day return from lagged features. An educational exercise, explicitly not a reliable trading signal.

---

## Data & Reproducibility

Stock data is downloaded once via [`yfinance`](https://pypi.org/project/yfinance/) and saved as a CSV snapshot in `data/`. The notebook always loads from that frozen file instead of re-downloading live prices, so:

- Results and written interpretations stay consistent no matter when the notebook is run
- Anyone cloning the repo gets identical output, immediately, without needing an internet connection
- The (commented-out) download code remains in the notebook purely as documentation of how the snapshot was created and how to refresh it

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `yfinance` | Historical stock price data |
| `pandas` | Data manipulation |
| `matplotlib` | Static visualizations |
| Jupyter Notebook | Main analysis environment |
| Streamlit | Interactive dashboard |
| VADER + NewsAPI | News sentiment analysis |

---

## Roadmap

**Dashboard (`dashboard.py`) — planned, separate from the notebook:**
- Free ticker input (any stock, not just current holdings)
- Monte Carlo simulation / Efficient Frontier
- Rolling Sharpe Ratio & Rolling Volatility
- Value at Risk (VaR) with adjustable confidence slider
- News sentiment (Yahoo Finance headlines + VADER)

Unlike the notebook, the dashboard always fetches live data. Reproducibility only applies to the static analysis above.

---

## Course Connections

| Course | Concepts applied here |
|---|---|
| Statistics | Descriptive statistics, confidence intervals (basis for Section 4 bootstrap) |
| Stochastic Modelling | Daily returns treated as an independent stochastic process — the assumption behind annualizing risk with √252 |
| Statistical Data Analysis | KDE, bootstrap resampling, skewness/kurtosis, correlation matrix |
| Probability Theory | Binomial distributions, covariance/regression (beta) |
| Project Big Data | sklearn Pipeline, Ridge regression, cross-validation |
| Data Engineering | Streamlit dashboard build skills |

---

## Disclaimer

This project is for educational purposes only. Nothing here constitutes financial advice. All analysis reflects a personal learning exercise, not a recommendation to buy or sell any security.
