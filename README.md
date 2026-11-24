# Stock Portfolio Analysis

Exploratory and statistical analysis of a real stock portfolio in Python, covering price behaviour, return distributions and risk-adjusted performance.

**Author:** Floris Schulmaijer
**Data snapshot:** July 6, 2026 (one year of daily closing prices)

---

## About This Project

This project combines a personal interest in investing with the statistics, probability theory and Python skills from my Business Analytics degree at VU Amsterdam. Rather than using a generic dataset, the analysis is built on real holdings, so every metric and chart reflects an actual investment decision.

---

## Key Results

Annualised volatility and Sharpe ratio per stock (risk-free rate: 4% per year):

| Stock | Annualised volatility | Sharpe ratio |
|---|---|---|
| GOOGL | 29.9% | 2.47 |
| AMD | 68.5% | 2.37 |
| AEHR | 121.8% | 1.90 |
| PLAB | 83.8% | 0.87 |
| NVDA | 35.3% | 0.68 |
| SOUN | 80.4% | -0.29 |

- **AEHR** had by far the highest return (over 700%), but also the highest volatility, so its risk-adjusted performance ranks below GOOGL and AMD.
- **GOOGL** was the least volatile stock and delivered the best return per unit of risk.
- **SOUN** is the only stock with a negative Sharpe ratio: it underperformed the risk-free rate.

---

## Repository Structure

```
stock-analyzer/
├── data/
│   ├── portfolio_data.csv      # Frozen price snapshot (main portfolio)
│   └── spcx_data.csv           # Frozen price snapshot (SpaceX, since IPO)
├── portfolio.ipynb             # Analysis notebook
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Getting Started

```bash
git clone https://github.com/florisschulmaijer/stock-analyzer.git
cd stock-analyzer
pip install -r requirements.txt
```

Then open `portfolio.ipynb` in VS Code or Jupyter and run all cells.

No API keys or live downloads are needed: the notebook loads the frozen CSV snapshots in `data/`, so results are identical for every user every time (see [Data & Reproducibility](#data--reproducibility)).

---

## Notebook Structure

**1. Data Import**

**2. Exploratory Analysis**
- 2.1 Raw stock prices (and 2.1.1 SpaceX since IPO)
- 2.2 Relative growth
- 2.3 Daily returns
- 2.4 Moving averages (20-day / 50-day, Golden Cross / Death Cross)
- 2.5 Return distribution (histogram + KDE)

**3. Risk & Performance Metrics**
- 3.1 Volatility (annualised standard deviation of daily returns)
- 3.2 Sharpe ratio (risk-adjusted return)

---

## Data & Reproducibility

Price data was downloaded once via [`yfinance`](https://pypi.org/project/yfinance/) and saved as CSV snapshots in `data/`. The notebook always loads these frozen files instead of re-downloading live prices, so:

- results and written interpretations stay consistent no matter when the notebook is run;
- anyone cloning the repo gets identical output without an internet connection;
- the (commented-out) download code stays in the notebook as documentation of how the snapshot was created and how to refresh it.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `yfinance` | Historical stock price data (snapshot creation) |
| `pandas` | Data manipulation and statistics |
| `matplotlib` | Visualisations |
| `scipy` | Kernel density estimates |
| Jupyter Notebook | Analysis environment |

---

## Course Connections

| Course | Concepts applied here |
|---|---|
| Statistics | Descriptive statistics, sample standard deviation |
| Statistical Data Analysis | Kernel density estimation, distribution shape, fat tails |
| Stochastic Modelling | Daily returns as a stochastic process |
| Probability Theory | Return distributions, normal distribution as benchmark |

---

## Roadmap

Completed:
- [x] Data import with frozen, reproducible snapshots
- [x] Exploratory analysis: prices, relative growth, daily returns, moving averages, return distributions
- [x] Volatility and Sharpe ratio

Planned:
- [ ] Maximum drawdown
- [ ] Skewness and kurtosis
- [ ] Correlation matrix
- [ ] Beta versus the market (S&P 500)
- [ ] Bootstrap analysis: resampling-based confidence interval for the mean return
- [ ] Portfolio overview: real dollar-weighted holdings with covariance-based portfolio risk
- [ ] Predictive modelling: scikit-learn Ridge regression pipeline predicting next-day returns from lagged features
- [ ] Watchlist notebook: the same analysis for stocks not yet owned
- [ ] Interactive Streamlit dashboard
- [ ] News sentiment analysis (VADER + NewsAPI)

---

## Disclaimer

This project is for educational purposes only and is not investment advice.
