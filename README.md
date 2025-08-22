# Portfolio Optimization (Modern Portfolio Theory)

This project applies **Modern Portfolio Theory (MPT)** to optimize a portfolio of U.S. equities using historical stock data.

## 📊 Project Overview
- **Universe**: AAPL, MSFT, NVDA, AMZN, JPM, TSLA
- **Data Source**: Yahoo Finance (via `yfinance`)
- **Methods**:
  - Calculate daily log returns
  - Estimate expected returns and covariance matrix
  - Optimize portfolio weights using PyPortfolioOpt
  - Visualize efficient frontier and max Sharpe ratio portfolio
- **Tools**: Python, yfinance, pandas, numpy, matplotlib, PyPortfolioOpt

## 🚀 How to Run
1. Clone the repo
   ```bash
   git clone https://github.com/yourusername/finance-portfolio-optimization.git
   cd finance-portfolio-optimization  
