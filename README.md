# Portfolio Optimization with Modern Portfolio Theory

An **interview-ready, production-grade portfolio optimization** application using Python and **Modern Portfolio Theory (MPT)**. This project fetches real-time market data, applies quantitative finance principles to maximize the **Sharpe Ratio** under realistic constraints, and includes advanced features like automated rebalancing and rolling backtests.

**Author:** Costas Antony Pinto | **Role:** AI/ML Engineer, Finance Enthusiast | **GitHub:** [MrCoss](https://github.com/MrCoss)

-----

## Table of Contents

  - [1. Project Rationale & Business Value](https://www.google.com/search?q=%231-project-rationale--business-value)
  - [2. Core Features & Functionality](https://www.google.com/search?q=%232-core-features--functionality)
  - [3. The Quantitative Finance Pipeline](https://www.google.com/search?q=%233-the-quantitative-finance-pipeline)
  - [4. Project Structure & Code Philosophy](https://www.google.com/search?q=%234-project-structure--code-philosophy)
  - [5. Technical Stack](https://www.google.com/search?q=%235-technical-stack)
  - [6. Local Setup & Execution Guide](https://www.google.com/search?q=%236-local-setup--execution-guide)
  - [7. For Interviewers & Professionals](https://www.google.com/search?q=%237-for-interviewers--professionals)
  - [8. Author & License](https://www.google.com/search?q=%238-author--license)

-----

## 1\. Project Rationale & Business Value

Investing in financial markets involves a fundamental trade-off between risk and return. Modern Portfolio Theory (MPT), pioneered by Harry Markowitz, provides a mathematical framework for assembling a portfolio of assets such that the expected return is maximized for a given level of risk.

The objective of this project is to implement MPT in a practical, automated tool. It moves beyond simple theory to address real-world challenges by incorporating:

  - **Realistic Constraints:** Applying bounds on asset allocation and total portfolio volatility.
  - **Dynamic Rebalancing:** Ensuring the portfolio adapts to changing market conditions.
  - **Robust Validation:** Using backtesting to verify the strategy's historical performance.

This tool empowers investors to construct diversified, data-driven portfolios that are optimized for risk-adjusted returns, replacing guesswork with a quantitative strategy.

-----

## 2\. Core Features & Functionality

  - **Real-Time Data Ingestion:** Fetches up-to-date historical stock prices for a defined list of tickers using the `yfinance` library.
  - **Constraint-Based Optimization:** Maximizes the **Sharpe Ratio** subject to realistic constraints:
      - No short-selling (weights \>= 0).
      - Asset allocation bounds (e.g., 5% to 30% per stock).
      - A cap on total portfolio volatility (e.g., max 45%).
  - **Efficient Frontier Simulation:** Runs a Monte Carlo simulation of 10,000 random portfolios to visualize the risk-return trade-off and plot the Efficient Frontier.
  - **Rolling Backtesting:** Implements a rolling window backtest to evaluate the strategy's performance over historical periods, demonstrating its real-world generalizability.
  - **Automated Monthly Rebalancing:** Uses `APScheduler` to schedule the entire optimization pipeline to run automatically (e.g., on the first day of each month), making it suitable for deployment.
  - **Comprehensive Reporting:** Generates clear visualizations of optimal asset allocation and exports the final weights and performance metrics to an Excel file.

-----

## 3\. The Quantitative Finance Pipeline

The project is structured as a sequence of modular tasks, from data collection to automated execution.

### Task 1 & 2: Data Ingestion & Preparation

  - Historical adjusted closing prices for 10 large-cap tech stocks are downloaded via `yfinance`.
  - The data is cleaned, and daily log returns are calculated.

### Task 3: Covariance & Return Calculation

  - The annualized covariance matrix is computed from daily returns, which is essential for modeling portfolio volatility.
  - Expected annual returns for each asset are also calculated.

### Task 4: The Optimization Engine

  - **Objective Function:** To maximize the Sharpe Ratio (`(Portfolio Return - Risk-Free Rate) / Portfolio Volatility`).
  - **Solver:** The optimization problem is solved using the **SLSQP (Sequential Least Squares Programming)** method from `scipy.optimize`, which is well-suited for constrained non-linear optimization.
  - **Output:** The engine returns the optimal weights for each asset that satisfy all constraints.

### Task 5 & 6: Visualization & The Efficient Frontier

  - The optimal portfolio weights are displayed in a bar chart.
  - A scatter plot of 10,000 simulated portfolios visualizes the **Efficient Frontier**. The point with the highest Sharpe Ratio is marked with a star (⭐), representing the optimal portfolio.

### Task 8: Rolling Backtest

  - This crucial validation step simulates the strategy's historical performance.
  - The process works as follows:
    1.  Train the optimizer on a "lookback" window (e.g., 1 year of data).
    2.  Use the generated optimal weights to calculate the portfolio's return over the next quarter (the "test" period).
    3.  "Roll" the window forward by one quarter and repeat the process.
  - This demonstrates how the strategy would have performed across different market regimes.

### Task 9: Automated Rebalancing

  - The `APScheduler` library is configured to run the entire optimization function (`rebalance_portfolio`) on a recurring schedule (e.g., `cron` job for the 1st of every month).
  - This makes the system autonomous and ready for a live-trading or a paper-trading environment.

-----

## 4\. Project Structure & Code Philosophy

```
.
├── main.ipynb          # Jupyter Notebook containing the entire modularized pipeline.
├── main.py             # (Optional) A script version of the notebook for terminal execution.
├── requirements.txt    # A list of all Python dependencies for reproducibility.
├── .gitignore          # Excludes sensitive files, virtual environments, and outputs.
└── README.md           # This detailed project documentation.
```

The code is designed to be **modular, exception-handled, and reproducible**, reflecting professional software engineering practices.

-----

## 5\. Technical Stack

  - **Core Language:** Python
  - **Data Analysis & Manipulation:** Pandas, NumPy
  - **Quantitative Finance & Optimization:** SciPy
  - **Financial Data Source:** yFinance
  - **Data Visualization:** Matplotlib, Seaborn
  - **Task Scheduling:** APScheduler
  - **Reporting:** OpenPyXL

-----

## 6\. Local Setup & Execution Guide

To run this project on your local machine, please follow these steps.

### Step 1: Clone the Repository

```bash
git clone https://github.com/MrCoss/portfolio-optimizer.git
cd portfolio-optimizer
```

### Step 2: Create and Activate a Virtual Environment (Recommended)

```bash
# Create the environment
python -m venv venv

# Activate on Windows
.\venv\Scripts\activate

# Activate on macOS/Linux
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Run the Optimizer

Execute the main script or run the cells in the Jupyter Notebook to perform a one-time portfolio optimization.

```bash
python main.py
```

*(Assuming you have a `main.py` script)*

-----

## 7\. For Interviewers & Professionals

This project demonstrates proficiency in several key areas relevant to quantitative finance and data science roles:

  - **Applied Quantitative Finance:** Practical implementation of Modern Portfolio Theory with a focus on the Sharpe Ratio.
  - **Constrained Optimization:** Ability to define and solve complex optimization problems with realistic bounds and constraints.
  - **Time-Series Validation:** Understanding of robust validation techniques like rolling backtests, which are superior to a simple train-test split for time-series data.
  - **Automation & System Design:** Experience with scheduling tools like APScheduler, demonstrating the ability to build automated, deployable systems.
  - **Production-Ready Code:** A focus on modularity, exception handling, and reproducibility.

-----

## 8\. Author & License

  - **Author:** Costas Antony Pinto
  - **License:** This project is free for academic, research, and personal use. Commercial use with attribution is permitted.
