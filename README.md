# Portfolio Risk Analysis Tool (V1)

## Project Overview

This project is a **quantitative finance risk analysis tool** developed in Python using a Jupyter Notebook.

The goal is to analyse the **risk profile of a multi-asset portfolio** composed of equities and indices by applying several classical techniques used in quantitative risk management.

The project includes:

* Historical market data retrieval
* Log return computation
* Volatility analysis
* Correlation analysis
* Portfolio volatility estimation
* Monte Carlo simulation of portfolio returns
* Value at Risk (VaR)
* Expected Shortfall (ES)
* VaR backtesting
* Stress testing
* Risk contribution decomposition

This first version focuses on **building the core risk analysis engine** and visualising the results.

A second version of the project will extend this work into an **interactive portfolio risk application**.


# Assets Analysed

The portfolio analysed in this project contains a mix of **European equities, Chinese exposure, and major market indices**.

Example assets:

* LVMH (MC.PA)
* Dassault Systèmes (DSY.PA)
* Sanofi (SAN.PA)
* BYD (BY6.F)
* Asia ETF (PAASI.PA)
* S&P 500 (^GSPC)
* Euro Stoxx 50 (^STOXX50E)

Historical data is retrieved using the **yfinance API**.


# Methodology

## 1. Market Data Collection

Historical price data is downloaded using `yfinance`.

Adjusted close prices are used in order to account for dividends and splits.


## 2. Log Return Computation

Daily log returns are computed using:

[
r_t = \ln \left(\frac{P_t}{P_{t-1}}\right)
]

Log returns are commonly used in quantitative finance because they:

* simplify compounding
* are more suitable for statistical modelling
* are additive over time


## 3. Volatility Analysis

The project computes:

* **Daily volatility**
* **Annualized volatility**

Annualized volatility is obtained using:

[
\sigma_{annual} = \sigma_{daily} \times \sqrt{252}
]

This provides a measure of the **risk of each asset**.


## 4. Correlation Analysis

A **correlation matrix** of asset returns is computed and visualised using a heatmap.

This analysis highlights:

* diversification benefits
* highly correlated assets
* potential concentration risk


## 5. Portfolio Volatility

Portfolio volatility is calculated using the covariance matrix of asset returns:

[
\sigma_p = \sqrt{w^T \Sigma w}
]

Where:

* (w) = portfolio weights
* (\Sigma) = covariance matrix of returns

This provides the **overall risk of the portfolio**.


## 6. Monte Carlo Simulation

A **multivariate normal simulation** is used to simulate thousands of possible daily portfolio returns.

The simulation is based on:

* mean vector of historical returns
* covariance matrix of returns

This allows estimation of the **distribution of potential portfolio losses**.


## 7. Value at Risk (VaR)

The **Value at Risk (VaR)** estimates the maximum loss that should not be exceeded with a given probability over a specific time horizon.

Example:

95% VaR means:

> There is a 95% probability that the loss will not exceed this value over one day.

VaR is estimated from the simulated loss distribution.


## 8. Expected Shortfall (ES)

Expected Shortfall measures the **average loss in the worst cases beyond the VaR threshold**.

It is a **coherent risk measure** and is widely used in modern risk management frameworks.


## 9. VaR Backtesting

The model is evaluated by comparing:

* predicted VaR
* actual historical losses

Days where losses exceed the VaR are called **exceptions**.

This helps assess the reliability of the risk model.


## 10. Stress Testing

The project simulates **extreme market scenarios** by applying shocks to asset returns.

Example shocks:

* European equities −12%
* S&P500 −8%
* BYD −25%

This allows evaluation of **portfolio resilience under crisis conditions**.


## 11. Risk Contribution Analysis

The contribution of each asset to total portfolio risk is computed.

This identifies:

* assets driving portfolio volatility
* potential risk concentrations
* diversification inefficiencies

Risk contribution is based on the covariance matrix and portfolio weights.


# Visualisations

The notebook includes several visual tools:

* asset return time series
* return distributions
* volatility bar charts
* correlation heatmap
* loss distribution
* VaR / ES visualization
* risk contribution charts

These visualizations provide an intuitive understanding of portfolio risk.


# Technologies Used

Python libraries used in the project:

* pandas
* numpy
* matplotlib
* seaborn
* yfinance
* jupyter


# Future Improvements (Version 2)

The next version of the project will transform this notebook into a **fully interactive portfolio risk analysis tool**.

Planned features include:

* user portfolio input (tickers + number of shares)
* automatic portfolio weight calculation
* automated risk diagnostics
* portfolio optimisation (Markowitz framework)
* target risk selection
* interactive dashboards
* web interface using **Streamlit**


# Educational Purpose

This project was developed as a **personal quantitative finance project** to explore portfolio risk analysis techniques commonly used in:

* asset management
* portfolio management
* risk management
* quantitative finance


# Author

Personal quantitative finance project.
