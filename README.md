# Volatility Arbitrage Project

## Authors
- **Jiaqi(Scarlett) He**
- **Brian Eide**
- **Anuraag Aravindan**
- **Ranjith Rajeshram**

## Introduction to Volatility Arbitrage

Volatility arbitrage seeks to exploit mispriced volatility in options markets. Option prices imply the expected level of volatility between now and expiration. An option’s replicating portfolio is given by the option’s delta. If volatility is mispriced, there is an arbitrage opportunity between the replicating portfolio (dynamic delta hedge) and the option.

- **Implied volatility is rich**: Sell the option, delta hedge (buy the replicating portfolio)
- **Implied volatility is cheap**: Buy the option, delta hedge (sell the replicating portfolio)

We will buy or sell a delta-hedged at-the-money (ATM) straddle if we see a discrepancy between our predicted realized and the market-implied volatility in SPX options. ATM straddles best isolate gamma and vega risk, which are what we intend to trade. We will delta hedge with the SPY ETF because it tracks this index.

## Goals

- Learn about option and volatility theory
- Learn about volatility forecasting techniques
- Gain hands-on experience with wrangling options data
- Gain experience with the process of backtesting

## Models Tested

- LSTM (Singular and Bivariate)
- XGBoost
- ARCH
- GARCH
- Volatility cones

## Backtest Data Preprocessing

- Downloaded a year’s worth of SPX options price and other historical data, including SPX index, SPY price, SOFR, and S&P 500 dividend yield
- Parsed data and formatted the dataframe
- Calculated straddle price at each strike and expiration
- Calculated Black-Scholes inputs and Greeks, including time to expiration, implied volatility, and straddle delta

## Backtest Profit and Loss Calculation

- Initial cash flows: pay/receive straddle premium, open delta hedge position
- Intermediate cash flows: delta hedge adjustments
- Calculate cumulative sum of cash flows
- Calculate daily mark-to-market P&L

## Results

Short straddles performed well, while long straddles performed poorly; this is likely due to delta hedging intervals not capturing enough volatility.

## Reflections

### What We Learned

- Learned about option theory and volatility trading in a short amount of time
- Learned about backtesting an option trading strategy and P&L calculation

### Challenges

- Building a systematic, quantitative model to predict volatility is challenging
  - Volatility is a measure of uncertainty, which is often idiosyncratic and fundamentally driven
  - Options markets are generally efficiently priced; edge is found in niche areas of expertise
  - Likely need to incorporate more features beyond relying on the time series’ memory
- Acquiring accurate pricing data was difficult; we could only use approximations for implied volatility and delta

## Repository Contents

- `AAPL.csv`: Contains historical data for Apple Inc.
- `AppleHistoricalData.csv`: Historical data specific to Apple.
- `LSTM.ipynb`: Jupyter notebook for LSTM model testing.
- `SPX_Options.parquet`: SPX options data in Parquet format.
- `SPX_Options.parquet2`: Additional SPX options data in Parquet format.
- `Volatility Arbitrage Presentation.pdf`: Presentation on the volatility arbitrage project.
- `backtest.ipynb`: Jupyter notebook for backtesting the trading strategy.
- `rollingVol.ipynb`: Jupyter notebook for rolling volatility forecast.
