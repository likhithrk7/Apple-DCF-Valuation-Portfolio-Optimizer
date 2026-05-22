# Apple Inc. (AAPL) — DCF Valuation & Portfolio Analysis

> **Finance portfolio project** demonstrating financial modeling, valuation, and quantitative analysis skills using real-world data.

---

## 📊 Project Overview

This project contains two independent finance tools built for a **$100,000 mock portfolio**:

1. **DCF Valuation Model** — Full 5-year Discounted Cash Flow model for Apple Inc. (AAPL) built in Excel, with sensitivity analysis and an investment memo
2. **Portfolio Optimizer** — Python-based stock portfolio tracker and Sharpe Ratio optimizer for AAPL, TSLA, MSFT, AMZN, GOOGL

Both projects reflect skills tested in entry-level financial analyst, investment banking, and portfolio management interviews.

---

## 🗂️ Repository Structure

```
apple-dcf-valuation/
│
├── outputs/
│   └── Apple_DCF_Valuation_Model.xlsx   # Full DCF model (4 tabs)
│
├── portfolio_tracker.py                 # Python portfolio optimizer
├── requirements.txt                     # Python dependencies
├── .gitignore
└── README.md
```

---

## 1️⃣ DCF Valuation Model (Excel)

**File:** `outputs/Apple_DCF_Valuation_Model.xlsx`

### What It Does
- Projects Apple's Free Cash Flow over 5 years (FY2025–FY2029) based on FY2024 10-K actuals
- Calculates WACC using CAPM (Risk-Free Rate + Beta × Equity Risk Premium)
- Derives Terminal Value using the Gordon Growth Model
- Outputs an implied share price vs. current market price (upside/downside %)
- Runs a 5×5 sensitivity table across WACC (8–12%) and terminal growth rate (1.5–3.5%)

### Model Tabs
| Tab | Description |
|-----|-------------|
| **Assumptions** | All input drivers in one place — change any blue cell to run scenarios |
| **DCF Model** | 5-year FCF projection → Enterprise Value → Implied Share Price |
| **Sensitivity** | 25-scenario sensitivity table (WACC vs. terminal growth) |
| **Investment Memo** | Written BUY/SELL recommendation with thesis and key risks |

### Key Assumptions (Base Case)
| Driver | Value | Source |
|--------|-------|--------|
| Base Revenue (FY2024) | $391,035mm | Apple 10-K FY2024 |
| Revenue Growth (Yr 1–5) | 8% → 10% → 8% | Analyst consensus |
| EBIT Margin | 29.5% | Apple 10-K FY2024 |
| Tax Rate | 24.1% | Apple 10-K FY2024 |
| WACC | ~10.0% | CAPM + capital structure |
| Terminal Growth Rate | 2.5% | Long-run nominal GDP |
| Diluted Shares | 15,204mm | Apple 10-K FY2024 |

### Color Coding (Industry Standard)
- 🔵 **Blue text** = Hardcoded inputs (user changes these)
- ⚫ **Black text** = Formulas / calculated cells
- 🟢 **Green text** = Cross-sheet links
- 🟡 **Yellow background** = Key output cells

---

## 2️⃣ Portfolio Tracker & Optimizer (Python)

**File:** `portfolio_tracker.py`

### What It Does
- Tracks a **$100,000 equal-weight portfolio** across 5 stocks
- Calculates annualized return, volatility, and Sharpe Ratio per stock
- Runs **Sharpe Ratio optimization** via `scipy.optimize` to find the ideal weight allocation
- Simulates **5,000 random portfolios** (Monte Carlo) to map the efficient frontier
- Outputs rebalancing recommendations (buy/sell by %)
- Generates a 4-panel dashboard chart

### Key Results (Sample Output)
```
EQUAL-WEIGHT PORTFOLIO (Baseline):
  Expected Annual Return : 45.86%
  Annual Volatility      : 17.30%
  Sharpe Ratio           : 2.36

OPTIMIZED PORTFOLIO (Max Sharpe):
  Expected Annual Return : 49.42%
  Annual Volatility      : 14.84%
  Sharpe Ratio           : 2.99

Sharpe Improvement: +26.7%
```

### Charts Generated
- Normalized price performance (base = 100)
- Equal-weight vs. optimized weight comparison
- Monte Carlo efficient frontier (5,000 portfolios, colored by Sharpe)
- Annualized return & Sharpe ratio per stock

### How to Run

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/apple-dcf-valuation.git
cd apple-dcf-valuation

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the portfolio optimizer
python portfolio_tracker.py
```

> **Note:** The script uses simulated price data by default. To use live data, replace the data section with:
> ```python
> import yfinance as yf
> raw = yf.download(["AAPL","TSLA","MSFT","AMZN","GOOGL"], period="2y", auto_adjust=True)
> prices = raw["Close"].dropna()
> ```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.10+ | Portfolio analysis & optimization |
| pandas / numpy | Data manipulation & math |
| scipy | Sharpe Ratio optimization (SLSQP) |
| matplotlib | Dashboard charts |
| yfinance | Live stock price data (optional) |
| Excel / openpyxl | DCF model construction |

---

## 📚 Finance Concepts Demonstrated

- **Discounted Cash Flow (DCF)** — core valuation methodology
- **Free Cash Flow** — NOPAT + D&A − Capex − ΔNWC
- **WACC** — weighted average cost of capital via CAPM
- **Gordon Growth Model** — terminal value calculation
- **Sharpe Ratio** — risk-adjusted return = (Return − Rf) / Volatility
- **Modern Portfolio Theory** — efficient frontier & diversification
- **Monte Carlo Simulation** — probabilistic portfolio analysis
- **Sensitivity Analysis** — scenario testing across key assumptions

---

## 📖 Data Sources

- Apple Inc. FY2024 Annual Report (10-K) — [SEC EDGAR](https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=AAPL&type=10-K)
- Damodaran Equity Risk Premium (Jan 2025) — [NYU Stern](https://pages.stern.nyu.edu/~adamodar/)
- US Treasury yield (risk-free rate) — [US Treasury](https://home.treasury.gov/resource-center/data-chart-center/interest-rates)

---

## ⚠️ Disclaimer

This project is for **educational and portfolio purposes only**. It does not constitute investment advice. All projections are based on publicly available information and analyst estimates.

---

## 👤 Author

**[Your Name]**  
Finance Student | Aspiring Financial Analyst  
[LinkedIn](https://linkedin.com/in/yourprofile) · [Email](mailto:your@email.com)
