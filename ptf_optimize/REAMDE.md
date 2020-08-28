## Overview

This package implements portfolio optimisation methods using classical mean-variance optimisation techniques which was first introduced in Harry Markowitz's 1952 paper.

## Functions:
- equal_allocation: stocks in this portfolio has equal weights. This may be useful if you're trying to get a sense of how equal allocation portfolio performs compared to other portfolios.

- opt_portfolio: this results in a tangency portfolio because on a graph of expected returns vs volatility, this portfolio corresponds to the tangent of the efficient frontier that has a y-intercept equal to the risk-free rate. 

- min_risk: This results in a portfolio that has minimum volitility. 

- get_portfolio_stats: This function prints out the allocation of the portfolio as well as the resulting expected return, volatility, variance, and sharpe ratio of the portfolio.
