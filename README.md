This is a quantitative research project designed to build, optimize, and most importantly validate a pairs trading strategy.

The primary focus of this project was not simply to build a profitable backtest, but to systematically prove that the strategy possesses a robust statistical edge and is not a result of overfitting to historical data.

# Final Validation Results (Out-of-Sample)
The most important conclusion from this project is the performance comparison between the "Training" (In-Sample) data and the "Test" (Out-of-Sample) data.

The results show that the strategy is robust. The model discovered in the past data proved to hold up exceptionally well on new, unseen data.

- In-Sample (Train) Sharpe Ratio: 2.19

- Out-of-Sample (Test) Sharpe Ratio: 2.08

- In-Sample (Train) Max Drawdown: -14.29%

- Out-of-Sample (Test) Max Drawdown: -8.06%

The Sharpe Ratio (our risk-adjusted return metric) barely decreased, and the risk profile (Max Drawdown) was actually better (lower) in the live test. This is the strongest possible validation of a model.

# Methodology: A 6-Step Research Process
This project followed a strict, professional quantitative workflow.

1. Data Preparation & Splitting
    - Stock Pair: BBCA.JK vs BMRI.JK
    
    - Data Source: Daily close prices from yfinance.
    
    - In-Sample (IS) / Training Data: 2020-01-02 to 2023-12-29
    
      - This data was used to discover the model and for optimization.
    
    - Out-of-Sample (OOS) / Test Data: 2024-01-02 to 2025-11-06
    
      - This data was held out and used only for the final, one-time test.

2. Analysis & Modeling (In-Sample)
    - An OLS regression was run on In-Sample data to find the Hedge Ratio (Beta).
    
    - Discovered Hedge Ratio (Beta): 0.7960
    
    - Cointegration P-Value: 0.1404

3. Parameter Optimization (In-Sample Grid Search)
    - Instead of guessing, a systematic Grid Search was performed ONLY on In-Sample data to find the best-performing parameters.
    
    - Parameters Tested: rolling_window, entry_threshold, exit_threshold.
    
    - Champion Parameters Found:
    
    - Window: 30 (days)
    
    - Entry: 1.5 (Z-Score)
    
    - Exit: 1.0 (Z-Score)

4. Validation (Out-of-Sample)
    - The "champion" model from Step 3 (with parameters 30, 1.5, 1.0) was then applied one time to the unseen OOS data.
    
    - This was the honest "final exam" to see if the strategy was overfit.
    
    - Result: The strategy passed the test with a Sharpe Ratio of 2.08 and MDD of -8.06%.

5. Performance Analysis
    - The strategy's performance was also benchmarked against a simple "Buy and Hold" strategy for both BBCA and BMRI.
    
    - The analysis showed the pairs strategy delivered far smoother, less volatile returns (a superior risk-adjusted return), as proven by its high Sharpe Ratio.

6. Further Analysis & Findings
    - This validation process was also tested on a US tech stock pair. The result was a failure (OOS Sharpe -0.51), which proves the strength of this validation process in correctly identifying an overfit strategy and preventing real-world losses.

# Key Findings & Analysis
This research process yielded several critical findings:

1. OOS Validation > P-Value: The most interesting finding was the "paradox" between the P-Value and the results. Although the initial cointegration test was weak (P-Value 0.14), the OOS validation (Sharpe 2.08) proved the strategy was highly robust. This shows that a rigorous OOS test is a far more important arbiter of a model's quality than relying on a single statistical test.

2. The Importance of Parameters: The Grid Search proved that the exit=1.0 parameter was crucial. A test on exit=0.0 (meaning "never take profit") resulted in a catastrophic Sharpe of -1.77. This proves the strategy's success is dependent on a disciplined, rule-based profit-taking mechanism.

# Research Context vs. Real-World Application
This project is a showcase of an end-to-end quantitative research process. Its goal is to demonstrate, step-by-step, how a researcher can find and validate a true statistical edge.

It is important to differentiate this research from a live production system. Any real-world implementation would require navigating additional practical hurdles, such as:

  - Transaction Costs & Slippage
  
  - Market Frictions & Liquidity
  
  - Specific local market regulations (e.g., retail short-selling restrictions)

The success of this portfolio project lies in its validation methodology, which is the core skill of a Quantitative Researcher.
