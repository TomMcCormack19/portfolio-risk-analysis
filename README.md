# Portfolio Risk Analysis & Optimisation

## Overview

This project analyses the risk and return characteristics of a diversified portfolio of five assets using Python.

The project applies quantitative finance techniques to historical market data, including return analysis, correlation and covariance analysis, Value at Risk (VaR), Expected Shortfall, maximum drawdown and portfolio optimisation.

The final stage compares an equal-weight portfolio with minimum-variance and maximum-Sharpe portfolios and constructs an efficient frontier.

## Assets

The portfolio contains:

* Apple (AAPL)
* SPDR Gold Shares (GLD)
* JPMorgan Chase (JPM)
* Microsoft (MSFT)
* Exxon Mobil (XOM)

Historical daily price data was obtained using `yfinance` for the period from January 2021 to January 2026.

## Project Structure

```text
Portfolio-Risk-Analysis/
│
├── Data/
├── Notebooks/
│   ├── 01_data_analysis.ipynb
│   ├── 02_correlation.ipynb
│   ├── 03_risk_metrics.ipynb
│   └── 04_portfolio_optimisation.ipynb
│
├── Results/
│   ├── correlation_heatmap.png
│   ├── daily_portfolio_returns_distribution.png
│   ├── portfolio_drawdown_over_time.png
│   ├── efficient_frontier.png
│   └── portfolio_comparison.png
│
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```

## Methodology

### 1. Data Analysis

Historical adjusted closing prices were downloaded using `yfinance`.

Daily percentage returns were calculated using:

$$
R_t = \frac{P_t-P_{t-1}}{P_{t-1}}
$$

The individual assets were then analysed using summary statistics and return visualisations.

### 2. Correlation & Covariance

The correlation and covariance matrices were calculated to examine the relationships between assets.

Correlation was particularly useful for assessing diversification. Assets with lower correlations can potentially reduce overall portfolio risk when combined.

### 3. Portfolio Risk

The portfolio was initially constructed using equal weights of 20% for each asset.

Several risk measures were calculated:

* Annualised volatility
* Historical Value at Risk (95%)
* Parametric Value at Risk (95%)
* Expected Shortfall (95%)
* Maximum Drawdown

These measures capture different aspects of portfolio risk, including typical volatility and potential losses during adverse market conditions.

### 4. Portfolio Optimisation

Three portfolios were compared.

#### Equal-Weight Portfolio

Each asset was assigned a weight of 20%.

#### Minimum-Variance Portfolio

Portfolio weights were chosen to minimise portfolio variance subject to:

* Weights summing to 1
* No short selling
* Individual asset weights between 0% and 100%

#### Maximum-Sharpe Portfolio

Portfolio weights were chosen to maximise the Sharpe ratio, using a 0% risk-free rate.

The optimisation was performed using the Sequential Least Squares Programming (SLSQP) algorithm from `scipy.optimize`.

### Efficient Frontier

Random portfolios were generated and plotted against their expected returns and annualised volatility.

An efficient frontier was then constructed by minimising portfolio variance for a range of target returns.

This illustrates the trade-off between expected return and risk.

## Key Results

The three portfolio strategies produced the following results:

| Portfolio        | Expected Return | Volatility | Sharpe Ratio |
| ---------------- | --------------: | ---------: | -----------: |
| Equal Weight     |          21.98% |     15.35% |         1.43 |
| Minimum Variance |          19.73% |     12.38% |         1.59 |
| Maximum Sharpe   |          21.20% |     12.84% |         1.65 |

The maximum-Sharpe portfolio achieved the highest Sharpe ratio of approximately 1.65.

Compared with the equal-weight portfolio, it produced a similar historical expected return while reducing annualised volatility from approximately 15.35% to 12.84%.

The minimum-variance portfolio achieved the lowest volatility at approximately 12.38%, but also had the lowest historical expected return of the three strategies.

## Portfolio Allocations

### Minimum-Variance Portfolio

| Asset | Weight |
| ----- | -----: |
| AAPL  |  2.82% |
| MSFT  | 58.29% |
| JPM   | 15.43% |
| XOM   | 13.74% |
| GLD   |  9.73% |

### Maximum-Sharpe Portfolio

| Asset | Weight |
| ----- | -----: |
| AAPL  |  0.00% |
| MSFT  | 46.77% |
| JPM   | 19.12% |
| XOM   | 14.32% |
| GLD   | 19.80% |

The optimisation produced significantly different allocations from the equal-weight portfolio, demonstrating how expected returns, volatility and correlations influence portfolio construction.

## Visualisations

### Correlation Heatmap

The correlation matrix shows the relationships between the five assets and highlights potential diversification benefits.

![Correlation Matrix](Results/Correlation%20Matrix.png)

### Daily Portfolio Returns Distribution

The distribution of daily portfolio returns provides an overview of the portfolio's return behaviour and tail risk.

![Daily Portfolio Returns Distribution](Results/Daily%20Portfolio%20Returns%20Distribution.png)

### Portfolio Drawdown Over Time

The drawdown chart shows the historical decline in portfolio value from previous peaks and identifies periods of larger losses.

![Portfolio Drawdown](Results/Portfolio%20Drawdown.png)

### Efficient Frontier

The efficient frontier illustrates the relationship between expected return and portfolio risk and identifies portfolios that offer the highest expected return for a given level of volatility.

![Efficient Frontier](Results/Efficient%20Frontier.png)

### Portfolio Comparison

The portfolio comparison chart compares the expected return and volatility of the equal-weight, minimum-variance and maximum-Sharpe portfolios.

![Portfolio Comparison](Results/Portfolio%20Return%20vs%20Volatility.png)

## Key Takeaways

The analysis demonstrates that portfolio construction should consider risk-adjusted returns rather than simply maximising expected returns.

The maximum-Sharpe portfolio achieved a historical expected return close to the equal-weight portfolio while taking substantially less risk.

The minimum-variance portfolio reduced risk further, although this came with a lower expected return.

Overall, the project demonstrates how quantitative methods can be applied to portfolio construction and risk management.

## Limitations

The results are based on historical market data and should not be interpreted as predictions of future performance.

The optimisation assumes that historical returns, volatility and correlations provide reasonable estimates of future behaviour. In practice, these quantities can change significantly over time.

The model also does not account for:

* Transaction costs
* Taxes
* Liquidity constraints
* Short selling
* Changing market regimes
* Estimation error
* Portfolio rebalancing costs

The Sharpe ratio calculations assume a 0% risk-free rate.

## Future Improvements

Potential extensions to the project include:

* Backtesting the optimised portfolios
* Adding transaction costs
* Introducing a non-zero risk-free rate
* Implementing rolling volatility and correlation estimates
* Adding factor models
* Comparing historical and Monte Carlo VaR
* Testing the portfolios across different market regimes
* Introducing portfolio rebalancing

## Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* SciPy
* yfinance
* Jupyter Notebook

## Author

Built as a quantitative finance portfolio project to develop practical skills in Python, portfolio risk analysis and quantitative portfolio optimisation.
