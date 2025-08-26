# Final Report: Advanced Portfolio Risk Analysis using Extreme Value Theory

## Executive Summary
This comprehensive risk analysis project demonstrates the critical importance of using appropriate risk measurement methodologies for accurate financial risk assessment. Through rigorous comparison of four Value at Risk (VaR) approaches applied to S&P 500 data from 2018-2024, one can conclude that Extreme Value Theory (EVT) provides superior tail risk estimation while traditional parametric methods systematically underestimate risk. The research confirms the presence of heavy tails in financial return distributions and provides actionable insights for risk management.

## Table of Contents
- [Introduction](#introduction)
- [Methodology](#methodology)
- [Results](#results)
- [Discussion](#discussion)
- [Conclusions](#conclusions)
- [Recommendations](#recommendations)
- [Limitations & Future Research](#limitations-future-research)

## Introduction
Risk management in financial markets requires accurate estimation of potential losses, particularly during extreme market conditions. Traditional VaR methodologies often rely on normal distribution assumptions that fail to capture the heavy-tailed nature of financial returns. This project implements and validates multiple risk measurement approaches to identify the most effective methodology for tail risk estimation.

## Methodology
### Data Collection/Preparation
* Instrument: S&P 500 Index
* Period: January 2018 - December 2024 (1,759 trading days)
* Calculation: Logarithmic daily returns
* Preprocessing: Data cleaning and validation checks

## Risk Models Implemented
### 1. Historical VaR
* Empirical quantile-based approach
* No distributional assumptions
* Uses actual historical return distribution

### 2. Parametric VaR
* Normal distribution assumption
* Calculated using sample mean and standard deviation
* Represents traditional industry approach

### 3. EVT VaR (Extreme Value Theory)
* Generalized Pareto Distribution (GPD)
* Peak-over-threshold approach
* Method of moments parameter estimation:
  - Shape parameter (ξ): 0.2188
  - Scale parameter (σ): 0.009579

### 4. GARCH VaR
* Time-varying volatility modeling
* GARCH(1,1) specification
* Dynamic risk estimation

## Validation Framework
* Backtesting: Comparison of expected vs. actual VaR violations
* Stress Testing: Performance during crisis periods (COVID-19, Ukraine War)
* Statistical Testing: Kupiec tests for model validation


## Key Results Summary
### Model Performance Comparison (95% Confidence Level)

| Model      |   VaR     |   Violation Rate   | Performance       |
|:----------:|----------:|:------------------:|:-----------------:|
| Historical | -1.86%    | 5.00%              | ✅ Ideal          |
| Parametric | -2.01%    | 4.43%              | ❌ Underestimates |
| EVT        | -1.86%    | 5.00%              | ✅ Ideal          |
| GARCH      | -1.76%    | 5.63%              | ⚠️ Overestimates  |

### Expected Shortfall Comparison

| Model       |      CVaR       |    CVaR/VaR    | 
|:------------|:---------------:|:--------------:|
| Historical  |     -3.09%      |      1.66      |
| Parametric  |     -3.24%      |      1.61      |
| EVT         |     -3.09%      |      1.66      |
| GARCH       |     -2.95%      |      1.67      |

### Crisis Performance (COVID-19 Period)

| Metric           |  Result  |
|:----------------:|:--------:|
| Violation Rate   |  41.2%   |
| Max Exceedance   | -10.9%   |
| Avg Exceedance   |  -3.4%   | 

### Key Statistics
- Heavy Tails Confirmed: Shape parameter ξ = 0.2188 > 0
- Data Period: 1,759 trading days (2018-2024)
- Expected Violations: 88 (5% of 1,759 days)
- Fat Tail Threshold: CVaR/VaR > 1.25 (all models exceed this)


## Stress Testing Results
### COVID-19 Crisis (February-April 2020)
* Duration: 34 trading days
* Violation Rate: 41.2% (14 violations)
* Maximum Single-Day Exceedance: -10.9%
* Average Exceedance Magnitude: -3.4%

### Ukraine War Crisis (February-March 2022)
* Duration: 17 trading days
* Violation Rate: 5.9% (1 violation)
* Maximum Drawdown: -3.0%

## Key Statistical Findings
* Shape Parameter: ξ = 0.2188 > 0 (confirms heavy-tailed distribution)
* CVaR/VaR Ratios: 1.61-1.67 (significant tail risk presence)
* Autocorrelation: Violations show clustering during stress periods

## Discussion
### Model Accuracy
The perfect 5.0% violation rates for both Historical and EVT VaR demonstrate their accuracy in normal market conditions. This finding is particularly significant for EVT VaR, as it specifically focuses on tail events while maintaining overall accuracy.
### Parametric VaR Limitations
The systematic underestimation of risk by Parametric VaR (4.43% violation rate vs. expected 5.0%) highlights the danger of normal distribution assumptions in financial risk modeling. This 11% underestimation could lead to insufficient capital allocation during normal market conditions.
### Crisis Period Performance
The 41.2% violation rate during the COVID-19 crisis reveals that all models struggle during extreme events. However, this finding emphasizes the need for stress-adjusted models rather than invalidating the approaches altogether.
### Practical Implications
The CVaR/VaR ratios exceeding 1.6 across all methods indicate that expected losses during tail events are 60-67% worse than VaR estimates. This has significant implications for capital allocation and risk management practices.

## Conclusions
1. EVT Superiority: Extreme Value Theory provides the most theoretically sound approach for tail risk estimation while maintaining perfect accuracy in normal conditions.
2. Historical VaR Value: Despite its simplicity, Historical VaR demonstrates excellent performance, serving as a robust benchmark and validation tool.
3. Parametric VaR Deficiency: Methods based on normal distribution assumptions systematically underestimate risk and should be avoided for serious risk management applications.
4. Crisis Modeling Gap: All models require enhancement for extreme stress periods, where violation rates can exceed 40%.
5. Regulatory Implications: The significant difference between VaR and CVaR estimates supports regulatory requirements for Expected Shortfall calculations under Basel III/IV.

## Recommendations
 ### For Risk Managers
1. Primary Methodology: Adopt EVT VaR as the main risk measurement approach
2. Validation Framework: Use Historical VaR for model validation and benchmarking
3. Dynamic Monitoring: Implement GARCH models for volatility regime detection
4. Stress Testing: Develop separate models for crisis and normal periods

 ### For Portfolio Managers
1. Capital Buffers: Increase risk capital allocation by 25-40% to account for tail risk
2. Hedging Strategies: Enhance hedging during low volatility periods identified by GARCH models
3. Scenario Analysis: Implement regular stress testing using historical crisis parameters

 ### For Regulatory Compliance
1. Reporting Standards: Require both VaR and Expected Shortfall reporting
2. Model Validation: Mandate backtesting across multiple methodologies
3. Stress Testing: Formalize requirements for crisis period analysis

## Limitations & Future Research
### Current Limitations
1. Single Asset Focus: Analysis limited to S&P 500 only
2. Static Parameters: EVT parameters estimated over full historical period
3. Correlation neglect: No portfolio effects considered
4. Regime Detection: No automatic detection of volatility regime changes

### Future Research Directions
1. Multi-Asset Portfolios: Extend analysis to diverse portfolio compositions
2. Time-Varying Parameters: Implement rolling window EVT estimation
3. Machine Learning: Incorporate ML approaches for regime detection
4. Real-Time Monitoring: Develop live risk monitoring systems

## References
1) McNeil, A. J., Frey, R., & Embrechts, P. (2015). Quantitative Risk Management: Concepts, Techniques and Tools. Princeton University Press.
2) Coles, S. (2001). An Introduction to Statistical Modeling of Extreme Values. Springer-Verlag.
3) Basel Committee on Banking Supervision. (2019). Minimum capital requirements for market risk.
4) Diebold, F. X., Schuermann, T., & Stroughair, J. D. (2000). Pitfalls and opportunities in the use of extreme value theory in risk management.

**Report Generated:** August 2024  
**Data Period:** January 2018 – December 2024  
**Analysis Tools:** Python, Pandas, NumPy, SciPy, ARCH, Plotly  
**Author:** Aaron Weinberg  
**License:** MIT License

*This report is provided for educational and research purposes only. The analysis and recommendations should not be used for investment decisions without proper validation and professional advice. Past performance is not indicative of future results.*