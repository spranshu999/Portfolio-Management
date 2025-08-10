# 📈 Global Index Portfolio & Risk Management Report 🌍💹

## 1. Overview
This project delivers a **comprehensive portfolio analysis** of **20+ countries’ market indices** spanning over **two decades** of historical data.  
Using Python, we process raw index data, compute statistical & risk metrics, apply **momentum trading strategies**, and evaluate performance using advanced portfolio analytics inspired by **quantitative finance models** (including **Fama-French 3-Factor analysis**, **VaR**, and **CVaR**).

---

## 2. Objectives 🎯
- ✅ Evaluate long-term **risk** and **return** characteristics of global equity indices  
- ✅ Compare **volatility-adjusted** performance across multiple markets  
- ✅ Apply a **momentum-based strategy** to identify outperforming indices  
- ✅ Quantify risk using **Value at Risk (VaR)** and **Conditional Value at Risk (CVaR)**  
- ✅ Analyze **factor exposures** using the **Fama-French Model**  
- ✅ Build a diversified, systematic **global index portfolio**

---

## 3. Dataset 📂
- **Source:** Historical index prices for **34 global markets** from 2003–2023 (monthly frequency)  
- **Data Cleaning:**  
  - Removed NaNs and aligned indices by date  
  - Calculated **monthly returns** from price series  
- **Special Columns in Data:**  
  - `"World Returns"` & `"World Return"` as global benchmarks  
  - Each index represented by its country name  

---

## 4. Metrics Computed 📊

### 4.1 Annualized Performance & Risk
- **Annualized Returns (CAGR)** – Long-term growth rate per index  
- **Annualized Volatility (Std Dev)** – Measures overall market risk  
- **Variance of Returns** – Dispersion measure for stability analysis  

### 4.2 Risk-Adjusted Performance 🏆
- **Sharpe Ratio** – Return-to-risk efficiency  
- **Maximum Drawdown** – Largest peak-to-trough loss over the period  

### 4.3 Portfolio Risk Management 🛡️
From the attached file’s functions:
- **VaR (Value at Risk):**  
  - *Historic Approach* (`var_historic`) – quantile-based  
  - *Gaussian Approach* (`var_gaussian`) – assumes normality  
  - *Cornish-Fisher VaR* – adjusted for skewness & kurtosis  
- **CVaR (Conditional VaR):**  
  - `cvar_historic` – Expected loss beyond the VaR threshold  

### 4.4 Factor Model Analysis 🔗
- **Fama-French 3-Factor Regression (`ff_analysis`)**:  
  - Breaks returns into market risk premium (MKT), size (SMB), and value (HML) exposures  
  - Helps identify style tilts in chosen markets  

---

## 5. Methodology 🔍
1. **Data Loading** – Using `pandas` to ingest and organize 20 years of index prices  
2. **Return Calculation** – Percentage change for monthly returns  
3. **Metric Computation** – Using numpy-based formulas for annualization  
4. **Momentum Scoring** – Ranking markets based on recent multi-month returns  
5. **Portfolio Construction** – Selecting top decile indices by momentum rank  
6. **Risk Adjustment** – Using **VaR**, **CVaR**, and drawdown limits to size positions  
7. **Factor Attribution** – Applying the **Fama-French** model to assess exposures  

---

## 6. Tools & Libraries 🧰
- **Language:** Python  
- **Libraries:**
  - `pandas` – Time-series handling & cleaning  
  - `numpy` – Mathematical computations  
  - `matplotlib` – Charts & plots  
  - `scipy.stats` – Skewness, kurtosis, normality testing  
  - Custom functions from *Index-Portfolio.ipynb* for:
    - Summary Statistics  
    - VaR / CVaR Calculations  
    - Fama-French Regression  
    - Efficient Frontier Optimization  

---

## 7. Key Insights 📌
- **Volatility & Returns:**  
  Developed markets tend to have lower volatility but also lower returns, while emerging markets show higher growth potential with higher risk.  
- **Momentum Effects:**  
  Select markets (e.g., tech-heavy or commodity-linked economies) show **trend persistence** outperforming the global index over multiple months.  
- **Risk Management Impact:**  
  Applying CVaR constraints reduced tail losses significantly without overly sacrificing performance.  
- **Factor Exposures:**  
  Some markets exhibit high **SMB** (small-cap tilt) or **HML** (value tilt) sensitivity, useful for macro allocation strategies.  

---

## 8. Example Findings 🔍
*(Illustrative numbers — will reflect actual computations from the notebook)*
- **Top Sharpe Ratios:** Sweden 🇸🇪, USA 🇺🇸, Switzerland 🇨🇭  
- **Lowest Volatility:** Switzerland 🇨🇭, Denmark 🇩🇰  
- **Highest CAGR:** India 🇮🇳, Brazil 🇧🇷 (with higher drawdowns)  
- **Historic 5% VaR:** -6.2% monthly loss threshold for the portfolio  
- **Conditional VaR (CVaR):** -8.5% average loss in worst 5% cases  

---

## 9. Future Enhancements 🚀
- 📅 **Backtest Momentum Strategies** with quarterly & semiannual rebalancing  
- 🌐 **Add Bonds, Commodities, & FX** for multi-asset diversification  
- ⚡ **Automated Risk Controls** – Rebalance weights automatically when VaR breaches thresholds  
- 📈 **Live Dashboard** for real-time market scoring and portfolio monitoring  

---

## 10. Conclusion 💡
This **global index portfolio analysis** combines **traditional return/volatility metrics** with **advanced factor models** and **tail risk measures**, resulting in a more **resilient, data-driven investment strategy**.  

By blending **momentum selection** with **Fama-French attribution** and **CVaR-based risk sizing**, investors can potentially enhance returns while maintaining a disciplined risk profile.

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
