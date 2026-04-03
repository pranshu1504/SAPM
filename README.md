# Portfolio Construction & Asset Pricing

**Course:** Security Analysis & Portfolio Management (SAPM)  
**Benchmark:** Nifty 50 (`^NSEI`)

---

## Overview

Full Markowitz mean-variance optimization pipeline on a 5-stock Indian equity portfolio, with CAPM analysis and an international diversification extension. All data is fetched live via `yfinance`.

---

## Stocks Analysed

| Ticker | Company |
|---|---|
| `BIOCON.NS` | Biocon |
| `PIDILITIND.NS` | Pidilite Industries |
| `SIEMENS.NS` | Siemens India |
| `ETERNAL.NS` | Eternal |
| `NATIONALUM.NS` | National Aluminium Co. |
| `SPOT` | Spotify *(international asset)* |

> Risk-free rate: **6.8% p.a.** (RBI T-bill average)

---

## What the notebook does

### 1. Data Fetching & Descriptive Stats
Pulls adjusted close prices, computes daily returns, and outputs mean return, variance, and std dev for each stock and the Nifty 50 index. Saves `cov.csv` and `corr.csv`.

### 2. CAPM & Beta Estimation
OLS regression of each stock's returns against Nifty 50. Computes beta, annualised historical return, and CAPM required return (`Rf + β × Market Premium`). Saves `betas_capm.csv` and individual beta scatter plots.

### 3. Markowitz Efficient Frontier — Domestic
Optimises for:
- **Tangency portfolio** — maximum Sharpe ratio (SLSQP)
- **Minimum variance portfolio**
- **Efficient frontier** — 50 target-return points

Plots interactive EF with CML and Nifty 50 overlay via Plotly.

### 4. International Diversification
Repeats the same optimisation after adding Spotify (`SPOT`) as an international asset. Compares tangency portfolio return and volatility against the domestic-only version.

---

## Setup

```bash
pip install numpy pandas yfinance scipy plotly matplotlib statsmodels
```

Run the single notebook cell — outputs are printed inline and saved as CSV/PNG files.

---

## Key Outputs

| File | Contents |
|---|---|
| `cov.csv` / `corr.csv` | Covariance & correlation matrices |
| `betas_capm.csv` | Beta, historical return, CAPM required return per stock |
| `beta_<STOCK>.png` | Beta regression scatter plots |
| Interactive Plotly charts | Efficient frontier (domestic + international) |
