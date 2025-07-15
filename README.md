# Portfolio Optimization using Modern Portfolio Theory (MPT)

> Author: **Costas Antony Pinto**  
> Role: AI/ML Engineer | MCA | Finance Enthusiast  
> GitHub: [MrCoss](https://github.com/MrCoss)  

---

## 📘 Overview

This project implements a **robust, interview-ready, production-grade portfolio optimizer** using Modern Portfolio Theory (MPT). It’s designed to simulate and optimize investment portfolios by maximizing the **Sharpe Ratio** under realistic financial constraints and volatility limits.

You’ll learn how to:
- Pull real-time financial data using `yfinance`
- Apply quantitative finance principles (return, risk, Sharpe)
- Run **realistic optimizations** with diversification and risk bounds
- Visualize allocation and simulate the **Efficient Frontier**
- Automate monthly **rebalancing** and perform **rolling backtests**

---

## 📌 Technologies Used
- **Programming Language:** Python 3.x
- **Libraries:** NumPy, Pandas, SciPy, yFinance, Matplotlib, Seaborn, APScheduler, OpenPyXL
- **Concepts:** Modern Portfolio Theory, Sharpe Ratio, Constraints, Backtesting, Automation

---

## 📊 Stocks Used (FAANG + Tech)

10 liquid large-cap stocks:
```python
['AAPL', 'MSFT', 'GOOGL', 'AMZN', 'META', 'NVDA', 'TSLA', 'NFLX', 'ADBE', 'INTC']
```

---

## 🧠 Features (Tasks)

### ✅ Task 1: Setup and Configuration
- Imports, plot settings, seed config
- Tickers, start-end dates, risk-free rate, sector map

### ✅ Task 2: Data Download (yFinance)
- Download **Adj Close** prices for tickers
- Checks nulls, shape, structure
- Fully exception-handled

### ✅ Task 3: Return & Covariance Calculation
- Computes daily and annual returns
- Generates covariance matrix for volatility modeling

### ✅ Task 4: Portfolio Optimization (Sharpe Max)
- Constraints: No shorting, 5–30% bounds
- Caps volatility to 0.45
- Optimizes using SLSQP method
- Outputs return, risk, Sharpe

### ✅ Task 5: Visualize Portfolio Allocation
- Bar plot showing capital weights per asset

### ✅ Task 6: Simulate Efficient Frontier
- 10,000 random portfolios
- Return vs volatility plot
- Optimal point (Sharpe max) marked with ⭐

### ✅ Task 7: Export to Excel
- Sheets: `Weights`, `Metrics`
- Exported using `openpyxl`

### ✅ Task 8: Rolling Backtest (NEW)
- Uses a moving window (1 year)
- Simulates performance in next quarter
- Shows real-world generalizability

### ✅ Task 9: Monthly Rebalancing (NEW)
- Uses `apscheduler` to schedule monthly re-optimization
- Ideal for deployment or cron jobs

---

## 🧾 Requirements

### 1. Setup Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### requirements.txt
```txt
pandas
numpy
matplotlib
seaborn
scipy
yfinance
openpyxl
apscheduler
```

---

## 🧠 Sample Optimized Portfolio (Weights)

| Stock | Weight |
|-------|--------|
| AAPL  | 0.05   |
| MSFT  | 0.05   |
| GOOGL | 0.05   |
| AMZN  | 0.05   |
| META  | 0.05   |
| NVDA  | 0.30   |
| TSLA  | 0.30   |
| NFLX  | 0.05   |
| ADBE  | 0.05   |
| INTC  | 0.05   |

### ➕ Metrics:
- **Expected Annual Return:** 39.13%
- **Portfolio Volatility:** 44.83%
- **Sharpe Ratio:** 0.772

---

## 🧪 For Interviewers and Professionals

### ✅ Highlights
- Exception-handled, modularized architecture
- Constraint-based optimization (bounds, volatility caps)
- Includes automated rebalancing
- Covers backtesting for time-based evaluation
- Clean plotting for reporting and analysis

### 📁 Professional Practices
- `.gitignore` to exclude `/outputs`, `.xlsx`, cache, and venv
- `requirements.txt` for reproducibility
- `main.py` or Jupyter-based execution
- Logs and printouts with symbols for clarity

---

## ✅ Run the Script

### Execute Portfolio Optimizer:
```bash
python main.py
```

### Schedule Monthly Rebalancing:
```python
from apscheduler.schedulers.blocking import BlockingScheduler
scheduler = BlockingScheduler()
scheduler.add_job(rebalance_portfolio, 'cron', day=1)
scheduler.start()
```

---

## 🏁 Folder Structure

```
├── main.ipynb
├── README.md
├── requirements.txt
└── .gitignore

```

---

## 📜 License

Free for academic, research, and personal projects. Commercial use with attribution.

---

## 💬 Connect
For collaborations, reach out via GitHub or LinkedIn.
