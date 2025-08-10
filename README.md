# 📈 Global Index Portfolio Analysis

## Overview
This project performs a comprehensive **portfolio analysis** of **20 countries’ market indices** over the past **20 years**, using Python for data processing, statistical calculations, and strategy formation.

The analysis covers:
- Calculation of annualized performance and risk metrics
- Risk-adjusted return evaluation using the Sharpe Ratio
- Variance and volatility assessment
- Momentum signal generation for portfolio construction

---

## Objectives
- Evaluate long-term risk and return characteristics of global equity indices
- Compare performance across multiple markets
- Apply a momentum-based approach to identify outperforming indices
- Construct a portfolio allocation strategy based on quantitative signals

---

## Key Metrics Calculated
- **Annualized Standard Deviation** – Measures index volatility
- **Annualized Mean Returns** – Average yearly return
- **Sharpe Ratio** – Risk-adjusted performance metric
- **Variance** – Degree of return dispersion
- **Momentum Signals** – Ranking indices based on recent performance

---

## Methodology
1. **Data Acquisition**  
   - 20 years of historical price data for 20 country indices  
2. **Data Preparation**  
   - Cleaning and structuring data for analysis  
3. **Metric Computation**  
   - Annualized returns, volatility, variance, Sharpe ratios  
4. **Momentum Analysis**  
   - Calculate rolling returns to rank indices  
5. **Portfolio Formation**  
   - Select top-performing indices based on momentum rankings  

---

## Tools & Libraries
- **Language:** Python
- **Libraries:**
  - `pandas` – Data manipulation
  - `numpy` – Numerical analysis
  - `matplotlib` – Visualization

---

## Insights
- Global diversification benefits and risk profiles vary significantly by market
- Momentum-based selection highlights persistent trends in certain regions
- Risk-adjusted returns provide a more accurate comparison across markets

---

## Future Enhancements
- Backtesting of momentum strategies over multiple rebalancing periods
- Inclusion of additional asset classes for diversification analysis
- Automation of portfolio rebalancing and performance tracking

---

# Quantitative Portfolio and Risk Management Toolkit 🛠️📈

This Markdown guide provides an in-depth overview of the Python file you shared, summarizing its core quantitative finance functionality, with a special focus on Fama-French model integration, Value at Risk (VaR), Conditional Value at Risk (CVaR), and portfolio risk management techniques. No tables are used; instead, content is structured as sections and lists for readability. ⚡

---

## 1. Data Loading Functions 🔄

- **Fama-French Portfolios:** Functions load equity return series sorted by market capitalization (small vs large cap) and the multi-factor Fama-French factor returns.
- **Hedge Fund Indices:** Returns for hedge fund strategies can be loaded for benchmarking.
- **Industry Portfolios:** Provides flexible parsing for Ken French's industry portfolios, supporting returns, firm counts, and sizes for various groupings.

---

## 2. Portfolio Returns & Analytics 💡

- **Portfolio Return Calculation:** Compute expected portfolio return as a weighted sum of individual asset returns.
- **Portfolio Volatility:** Calculate portfolio volatility given weights and the covariance matrix—critical for understanding overall risk exposure.

---

## 3. Risk Metrics and Statistics 📊

- **Skewness and Kurtosis:** Custom methods for measuring non-normality in return distributions.
- **Compounded Growth:** Calculate compounded return over a period—useful for long-term investment analysis.

---

## 4. Annualization Helpers 📅

- **Annualize Returns:** Converts period returns (e.g., monthly) to annualized returns.
- **Annualize Volatility:** Converts standard deviation to an annual figure using the square-root-of-time rule.

---

## 5. Sharpe Ratio, Tracking Error, & Drawdowns 🏆

- **Sharpe Ratio:** Annualized Sharpe ratio measures return per unit risk, taking the risk-free rate into account.
- **Tracking Error:** Measures portfolio deviation relative to a benchmark.
- **Drawdown Analysis:** Tracks rolling portfolio losses from peak, providing context for worst observed losses.

---

## 6. Value at Risk (VaR) & Conditional VaR (CVaR) 🛡️

### a. **Historic VaR**  
- Calculates the loss threshold such that a given percentage (e.g., 5%) of returns fall below that threshold (quantile approach).

### b. **Conditional VaR (CVaR)**  
- Measures the average loss in the worst "x%" of outcomes (tail risk).

### c. **Parametric (Gaussian) VaR**  
- Assumes returns are normally distributed, calculating VaR from the distribution’s mean and standard deviation.  
- **Cornish-Fisher Modified VaR**: Adjusts the quantile for skewness and kurtosis to handle non-normal return distributions.

#### **Used in the File:**  
- `var_historic()`: Historic VaR  
- `cvar_historic()`: Conditional VaR  
- `var_gaussian()`: Parametric VaR (with or without Cornish-Fisher adjustment for skew/kurtosis)

---

## 7. Fama-French Model & Factor Analysis 📚

- **Fama-French Factor Returns Loader:** Supplies MKT, SMB, HML factor data.
- **Regression/Factor Exposure:**  
   - `regress()`: Linear regression for decomposing returns into factor exposures (betas), including optional alpha capture.
   - `ff_analysis()`: Computes Fama-French factor loadings for a return series or DataFrame.
- **Style Analysis:** Optimizes factor weights to best track a target return series, minimizing tracking error.

---

## 8. Normality Tests 📏

- **Jarque-Bera Test:** Assesses if return series are normally distributed at a specified significance level.

---

## 9. Portfolio Construction 🏗️

- **Efficient Frontier:** Plots and computes efficient frontiers for two-asset and multi-asset scenarios using mean-variance optimization.
- **Sharpe Ratio Maximization (MSR):** Finds weights that maximize Sharpe Ratio.
- **Global Minimum Variance (GMV):** Finds weights achieving portfolio’s minimum possible volatility.
- **Custom Constraints:** Optimization includes bounds (e.g., no negative weights) and ensures weights sum to one.

---

## 10. Advanced Strategies & Backtesting 🚦

- **CPPI (Constant Proportion Portfolio Insurance):** Implements dynamic risk budgeting using cushion (distance from floor).
- **Backtesting Framework:** Sliding estimation window lets you backtest arbitrary weighting schemes (equal weight, cap-weight, etc.).

---

## 11. Simulation Utilities 🔄

- **Geometric Brownian Motion (GBM):** Simulates potential investment paths under stochastic processes—helpful for scenario and stress testing.

---

## 12. Additional Portfolio Tools 🧰

- **Semi-Deviation:** Focuses on downside volatility (returns below zero).
- **Portfolio Weighting Schemes:** Supports naive (equal-weight) and market-cap-based weighting, with options for excluding micro-cap stocks or capping individual exposures.

---

## 13. Comprehensive Summary Statistics 📈

- **`summary_stats()`:**  
   Returns an aggregated view of annualized return, risk, skew, kurtosis, VaR (including Cornish-Fisher VaR), CVaR, Sharpe Ratio, and max drawdown for any return series or DataFrame.

---

## Example: Fama-French VaR & CVaR Application 🧑🔬

1. **Load Fama-French Factor Returns:**  
   Use `get_fff_returns()` to load factors.
2. **Compute Portfolio or Asset Returns:**  
   Create return stream from assets or factors.
3. **VaR/CVaR Calculation:**  
   - Call `var_historic()` or `var_gaussian()` (with or without Cornish-Fisher adjustments).
   - Call `cvar_historic()` for conditional tail loss.
4. **Factor Attribution:**  
   Use `ff_analysis()` to understand sensitivities.

---
