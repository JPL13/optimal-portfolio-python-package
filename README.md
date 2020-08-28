# ptf_optimize

## Overview

This package implements portfolio optimization methods based on Modern Portfolio Theory which was first introduced in Harry Markowitz's 1952 paper.

The key insight of this paper is that by combining assets with different expected returns and volatilities, one can find a optimal weights which minimises the risk for a targeted return or maximizes the return for a targeted risk. The set of all such optimal portfolios is referred to as the efficient frontier in the absence of a risk-free asset. The shape of this efficient frontier is a parabola. 

When a risk-free asset is present, the line passes vertical intercept at the risk-free rate and tangent to the efficient frontier is the new efficient frontier, which is called the capital allocation line (CAL). The tangency point with the parabola represents the optimal portfolio constructed with 100% risky assets. We will mark this portfolio as a "Star" in the plot at the bottom of this file.  


## Dependent packages

The dependent packages are : `pandas`, `numpy`, `matplotlib`, `pandas_datareader`, and `datetime`

## Install this package

This project is available on PyPI, meaning that you can just:

```python
pip install ptf_optimize
```

## Functions:
- constructor: construct a 'portfolio' object with a list of stock tickers. Users can specify the start date and the end date for the period of the stock price data. The defaut is is to use last five years of data on the stock price. 

- equal_allocation: This results in a portfolio with equal weights. This may be useful if you're trying to get a sense of how equal allocation portfolio performs compared to other portfolios.

- opt_portfolio: this results in a tangency point on the efficient frontier when risk free asset is present, this portfolio corresponds to the tangent of the efficient frontier that has a y-intercept equal to the risk-free rate. 

- min_risk: This results in a portfolio that has minimum volitility. 

- min_risk_given_return: This results in a portfolio that has minimum volatility for a targeted return rate. 

- get_portfolio_stats: This function prints out the allocation of the portfolio as well as the resulting expected return, volatility, variance, and sharpe ratio of the portfolio.

- plot_efficient_frontier: This function plots the efficient frontier as well as the minimum risk portfolio, the optimal portfolio when risk free rate is 0.005 and the optimal portfolio when the target return is 30%. 


## Example usage

Here is an example on real life stock data, demonstrating how to find the various optimal portfolio weights (with short sellings allowed) in certain conditions.

```python
from ptf_optimize import portfolio

tickers = ["AAPL", "CSCO", "MSFT", "SNE", "ADBE", "MU", "CWT", "SJW", "NRG", "KEP", "NEE", "SO", "BRK-B", "V", "JPM", "C", "MA", "LFC", "JNJ", "CVS", "ISRG", "NVO", "ABT", "CI", "AMZN", "TM", "HD", "NKE", "TSLA", "LOW"]

obj= portfolio(tickers, '2012-1-1', '2017-1-1') ## initialize a portfolio object with the stock tickers
```

First, we can get the minimum risk portfolio by using:

```python
weights=obj.min_risk()
```
This outputs the following weights:

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

We can get the optimal portfolio with risk free rate of 0.004 by using:

```python
weights=obj.opt_portfolio(Rf=0.004)
```
This outputs the following weights:

```
 AAPL  : 0.0397
 CSCO  : -0.0825
 MSFT  : 0.0523
 SNE   : -0.0604
 ADBE  : 0.1024
 MU    : 0.0502
 CWT   : 0.0199
 SJW   : 0.1031
 NRG   : -0.1289
 KEP   : 0.0725
 NEE   : 0.6312
 SO    : -0.4500
 BRK-B : -0.0968
 V     : 0.1714
 JPM   : 0.3396
 C     : -0.2325
 MA    : -0.0997
 LFC   : -0.1507
 JNJ   : 0.2092
 CVS   : 0.0323
 ISRG  : -0.0800
 NVO   : 0.0498
 ABT   : -0.1918
 CI    : 0.1906
 AMZN  : 0.0944
 TM    : 0.0183
 HD    : 0.3160
 NKE   : -0.0095
 TSLA  : 0.0898
 LOW   : 0.0002
Expected annual return : 42.61%
Annual volatility/standard deviation/risk : 17.91%
Annual variance : 3.21%
Sharpe ratio : 2.35
```

We can get optimal weights for a targeted return by using:

```
weights =obj.min_risk_given_return(expected_return=0.3)
```

This outputs the following weights:

```
 AAPL  : 0.0437
 CSCO  : -0.0251
 MSFT  : 0.0251
 SNE   : -0.0478
 ADBE  : 0.0487
 MU    : 0.0250
 CWT   : 0.0089
 SJW   : 0.0614
 NRG   : -0.0728
 KEP   : 0.0584
 NEE   : 0.3424
 SO    : -0.1057
 BRK-B : 0.0063
 V     : 0.1074
 JPM   : 0.2114
 C     : -0.1686
 MA    : -0.0743
 LFC   : -0.0961
 JNJ   : 0.2222
 CVS   : 0.0501
 ISRG  : -0.0284
 NVO   : 0.0481
 ABT   : -0.1137
 CI    : 0.1358
 AMZN  : 0.0522
 TM    : 0.0273
 HD    : 0.1936
 NKE   : 0.0141
 TSLA  : 0.0490
 LOW   : 0.0014
Expected annual return : 30.00%
Annual volatility/standard deviation/risk : 13.08%
Annual variance : 1.71%
Sharpe ratio : 2.26

```
Finally, we can plot the Efficient Frontier by using:

```python
obj.plot_efficient_frontier()
```
<center>
<img src="https://github.com/JPL13/optimal-portfolio-python-package/blob/master/Efficient%20Frontier.jpg" style="width:60%;"/>
</center>
