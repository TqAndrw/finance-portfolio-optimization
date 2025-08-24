# Robust Mean–Variance Portfolio with Turnover Control

## Abstract
We construct a long-only, regularized mean–variance portfolio with turnover control and evaluate it out-of-sample using monthly rebalancing and transaction costs. The strategy outperforms an equal-weight baseline on risk-adjusted metrics over 2014–present.

## Data
- Universe: {AAPL, MSFT, NVDA, AMZN, JPM, TSLA, XOM, PG}
- Frequency: Monthly (last business day)
- Source: Yahoo Finance (adjusted close)
- Sample: 2014-01 to present

## Methodology
We estimate expected returns \\( \mu \\) as trailing-window means (annualized) and covariance \\( \Sigma \\) via Ledoit–Wolf shrinkage. At each rebalance date, we solve:

\\[
\max_{w} \ \mu^\top w \;-\; \lambda \, w^\top \Sigma w \;-\; \gamma \|w\|_2^2 \;-\; \tau \|w - w_{t-1}\|_1
\\]
subject to \\( \sum_i w_i = 1, \ 0 \le w_i \le w_{\max} \\).

- \\( \lambda \\): risk aversion  
- \\( \gamma \\): L2 regularization  
- \\( \tau \\): turnover penalty  
- Costs: \\(c\\) bps applied to one-way turnover

## Backtest Design
- Lookback window: 36 months
- Rebalance: Monthly
- Costs: 10 bps per one-way trade
- Benchmarks: Equal-weight on same universe (and SPY, optional)
- Metrics: CAGR, Volatility, Sharpe, Max Drawdown, Calmar, Hit Rate, Turnover

## Results
- **Summary metrics** (OOS): see `data/performance_summary.csv`
- **Cumulative growth**: ![](../figs/cum_growth_oos.png)
- **Drawdown**: ![](../figs/drawdown_optimized.png)
- **Turnover distribution**: ![](../figs/turnover_hist.png)

## Robustness & Limitations
- Hyperparameters (\\( \lambda, \gamma, \tau \\)) can be selected via walk-forward validation.
- Universe selection and survivorship bias are considerations.
- Alternative estimators: EWMA cov, Black–Litterman, CVaR optimization.
- Cardinality constraints can be approximated via L1 penalty or post-thresholding.

## Next Steps
- Add hyperparameter sweep with time-series cross-validation
- Sector/position caps; dynamic volatility targeting
- Compare to risk parity and minimum-variance portfolios
