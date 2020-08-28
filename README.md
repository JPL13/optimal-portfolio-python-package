# optimal-portfolio-python-package

## Overview

This package implements portfolio optimisation methods using classical mean-variance optimisation techniques which was first introduced in Harry Markowitz's 1952 paper.

## Dependent packages

pandas, numpy, matplotlib.pyplot, pandas_datareader, datetime

## Install this package

This project is available on PyPI, meaning that you can just:

'''
pip install PyPortfolioOpt
'''

## Functions:
- constructor: construct a 'portfolio' object with a list of stock tickers. 

- equal_allocation: stocks in this portfolio has equal weights. This may be useful if you're trying to get a sense of how equal allocation portfolio performs compared to other portfolios.

- opt_portfolio: this results in a tangency portfolio because on a graph of expected returns vs volatility, this portfolio corresponds to the tangent of the efficient frontier that has a y-intercept equal to the risk-free rate. 

- min_risk: This results in a portfolio that has minimum volitility. 

- min_risk_given_return: 

- get_portfolio_stats: This function prints out the allocation of the portfolio as well as the resulting expected return, volatility, variance, and sharpe ratio of the portfolio.

- plot_efficient_frontier:


## Example usage

```python
tickers = ["AAPL", "CSCO", "MSFT", "SNE", "ADBE", "MU", "CWT", "SJW", "NRG", "KEP", "NEE", "SO", "BRK-B", "V", "JPM", "C", "MA", "LFC", "JNJ", "CVS", "ISRG", "NVO", "ABT", "CI", "AMZN", "TM", "HD", "NKE", "TSLA", "LOW"]
obj= portfolio(tickers, '2012-1-1', '2017-1-1')
```

```python
weights=obj.min_risk()
```

```text
AAPL  : 0.0488
 CSCO  : 0.0485
 MSFT  : -0.0098
 SNE   : -0.0317
 ADBE  : -0.0201
 MU    : -0.0073
 CWT   : -0.0052
 SJW   : 0.0079
 NRG   : -0.0008
 KEP   : 0.0403
 NEE   : -0.0281
 SO    : 0.3359
 BRK-B : 0.1387
 V     : 0.0253
 JPM   : 0.0470
 C     : -0.0866
 MA    : -0.0417
 LFC   : -0.0261
 JNJ   : 0.2389
 CVS   : 0.0729
 ISRG  : 0.0378
 NVO   : 0.0460
 ABT   : -0.0134
 CI    : 0.0654
 AMZN  : -0.0019
 TM    : 0.0388
 HD    : 0.0366
 NKE   : 0.0444
 TSLA  : -0.0032
 LOW   : 0.0029
Expected annual return : 13.83%
Annual volatility/standard deviation/risk : 10.10%
Annual variance : 1.02%
Sharpe ratio : 1.32
```

```python
obj.plot_efficient_frontier()
```
<center>
<img src="https://github.com/robertmartin8/PyPortfolioOpt/blob/master/media/efficient_frontier_white.png" style="width:60%;"/>
</center>
