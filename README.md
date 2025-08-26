# Advanced Portfolio Risk Analysis using Extreme Value Theory (EVT)
![Python](https://img.shields.io/badge/python-3.7%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Pandas](https://img.shields.io/badge/pandas-1.3%2B-150458)
![NumPy](https://img.shields.io/badge/NumPy-1.21%2B-013243)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4%2B-blueviolet)
![SciPy](https://img.shields.io/badge/SciPy-1.7%2B-8CAAE6)
![Plotly](https://img.shields.io/badge/Plotly-5.0%2B-3F4F75)
![ARCH](https://img.shields.io/badge/ARCH-5.0%2B-green)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Contributions](https://img.shields.io/badge/contributions-welcome-orange)

## Project Overview
This project implements a comprehensive risk assessment framework for S&P 500, demonstrating the limitations of traditional Value at Risk (VaR) models and providing more robust alternatives using Extreme Value Theory (EVT). Through rigorous backtesting and stress testing, we are able to validate various risk models and provide practical guidance for financial risk management.

## Problem Statement
Traditional risk models based on normal distribution assumptions systematically underestimate tail risk in financial markets. This project addresses this critical limitation by:
* Implementing and comparing multiple risk assessment methodologies
* Demonstrating the presence of "Heavy tails" in S&P 500 return distributions
* Providing more accurate risk estimates through Extreme Value Theory
* Validating models through rigorous backtesting and stress testing

## Model Performance Comparison (95% Confidence Level)

### VaR Estimates Comparison
| Model          | VaR Estimate |
|:---------------|:------------:|
| Historical VaR |   -1.86%     |
| Parametric VaR |   -2.01%     |
| EVT VaR        |   -1.86%     |
| GARCH VaR      |   -1.76%     |

### Model Performance
| Model             | Violation Rate   |      Performance        |
|:-----------------:|------------------|:-----------------------:| 
| Historical VaR    | 5.00%            |      ✅ Ideal           |   
| Parametric VaR    | 4.43%            | ❌ Underestimates risk  |
| EVT VaR           | 5.00%            |      ✅ Ideal           |
| GARCH VaR         | 5.63%            | ⚠️ Overestimates risk   |

## Key Findings Summary

- Historical VaR: -1.86% VaR, 5.00% violation rate (ideal performance)
- Parametric VaR: -2.01% VaR, 4.43% violation rate (underestimates risk)
- EVT VaR: -1.86% VaR, 5.00% violation rate (ideal performance) 
- GARCH VaR: -1.76% VaR, 5.63% violation rate (overestimates risk)

## Expected Shortfall (CVaR) Comparison
* Historical CVaR: -3.09%
* Parametric CVaR: -3.24%
* EVT CVaR: -3.09%
* GARCH CVaR: -2.95%

## Fat Tails Identification
Shape parameter (ξ) = 0.2188 > 0 confirms heavy-tailed distribution
CVaR/VaR ratios range from 1.61-1.67 across all methods
Significant discrepancy between normal distribution assumptions and empirical data
## Crisis Period Analysis (COVID-19, 2020)
All models showed 41.2% violation rates during extreme stress
* Maximum single-day exceedance: 10.9%
* Average exceedance magnitude: 3.4%

## Methodology
1. Data Analysis
Dataset: S&P 500 daily returns (2018-2024)
Preprocessing: Logarithmic return calculation, data cleaning
Descriptive Statistics: Volatility, quantiles, distribution analysis
2. Risk Models Implementation
Historical VaR: Empirical quantile-based approach
Parametric VaR: Normal distribution assumption
EVT VaR: Generalized Pareto Distribution (GPD) with method of moments
GARCH VaR: Time-varying volatility modeling
3. Model Validation
Backtesting: Kupiec tests, violation rate analysis
Stress Testing: COVID-19 crisis, Ukraine war period
Comparative Analysis: Accuracy, conservatism, and practicality assessment

## Project Structure

quant-risk-portfolio/
├── data/                         # Data files
│   └── notebooks/
│       └── data/
│           └── processed_returns.csv
├── src/                          # Source code
│   └── data/
│       └── 01_data_analysis.py
├── reports/                      # Analysis reports
│   ├── final_report.en.md/final_report.rus.md
│   ├── 02_backtesting_stress.md
│   └── figures/                  # Visualization files
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt

## Key Insights
1. Model Accuracy
EVT and Historical VaR show perfect accuracy with exactly 5% violation rates
Parametric VaR systematically underestimates risk (4.43% violation rate)
GARCH VaR overestimates risk (5.63% violation rate) but useful for volatility monitoring
2. Tail Risk Characteristics
Heavy tails confirmed with shape parameter ξ = 0.2188
CVaR significantly worse than VaR (60-67% higher losses)
Extreme events occur more frequentlythan normal distribution predicts
3. Crisis Performance
All models struggle during extreme events(41.2% violation rate during COVID-19)
Maximum exceedance of 10.9% in single day
Models need stress-adjusted parametersfor crisis periods

## Practical Recommendations
### For Risk Managers:
Primary method: Use EVT VaR for accurate tail risk estimation
Validation: Complement with Historical VaR for model verification
Monitoring: Implement GARCH models for volatility tracking
Avoid: Parametric VaR based on normal distribution assumptions
### For Portfolio Managers:
Capital allocation: Increase capital buffers by 25-40% for tail risk
Hedging: Strengthen hedging strategies during low volatility periods
Stress testing: Implement crisis scenarios with 40%+ violation rates
### For Regulatory Compliance:
Reporting: Include CVaR alongside VaR in risk reports
Validation: Require backtesting with multiple methodologies
Stress testing: Mandate crisis period analysis for model approval

## Future Enhancements
Multi-asset analysis: Extend to portfolios with multiple assets
Time-varying parameters: Implement rolling window EVT estimation
Machine learning: Incorporate ML approaches for risk prediction
Real-time monitoring: Develop live risk dashboard

## Conclusion
This research demonstrates that Extreme Value Theory provides superior tail risk estimation compared to traditional parametric methods. The implementation offers a robust framework for financial risk management that accurately captures the heavy-tailed nature of financial markets, particularly during crisis periods. The findings emphasize the importance of using appropriate risk measurement methodologies that account for extreme events rather than relying on normal distribution assumptions.


## Keywords  
**Value at Risk**, **Expected Shortfall**, **Extreme Value Theory**, **Risk Management**, **Backtesting**, **Stress Testing**, **Financial Risk**, **S&P 500**, **Quantitative Finance**.

## References
1) McNeil, A. J., Frey, R., & Embrechts, P. (2015). Quantitative Risk Management: Concepts, Techniques and Tools. Princeton University Press.
2) Coles, S. (2001). An Introduction to Statistical Modeling of Extreme Values. Springer-Verlag.
3) Basel Committee on Banking Supervision. (2019). Minimum capital requirements for market risk.
4) Diebold, F. X., Schuermann, T., & Stroughair, J. D. (2000). Pitfalls and opportunities in the use of extreme value theory in risk management.

*This report is provided for educational and research purposes only. The analysis and recommendations should not be used for investment decisions without proper validation and professional advice. Past performance is not indicative of future results.*


