# Cointegration-Based Pairs Trading Strategy

This repository contains a public project summary of my Certificate in Quantitative Finance (CQF) final project on cointegration-based pairs trading.

The original submission was completed as an exam/project deliverable, so the full report, code, datasets, selected instruments, and course-specific materials are not included here. This README summarizes the research objective, methodology, findings, and limitations at a high level for portfolio and discussion purposes.

## Disclaimer

This repository is for educational and portfolio purposes only.

The full CQF submission, code, datasets, selected instruments, and course-specific materials are not included. This README is a public-facing summary of the project methodology and findings. Nothing here should be interpreted as investment advice, a trading recommendation, or a production-ready investment strategy.


## Project Overview

This project investigated whether statistically identified cointegrated relationships could be used to construct a systematic mean-reversion trading strategy with positive out-of-sample performance.

The research focused on identifying stable long-run relationships between selected financial instruments, estimating equilibrium spreads, and testing whether deviations from those spreads could be translated into tradable signals.

The selected instruments and final trading relationships are intentionally not disclosed in this public summary. The purpose of this repository is to document the research process and framework design without publishing the full strategy specification.

The project used approximately three years of daily price data. The earliest year was used for training and parameter calibration, while the remaining two years were used for backtesting.

## Research Objective

The main objective was to test whether cointegration-based relationships could be translated into practical pairs trading strategies.

The project focused on:

- identifying cointegrated relationships between financial instruments
- estimating hedge ratios and equilibrium spreads
- constructing trading signals from standardized deviations
- testing multiple strategy designs
- assessing return, volatility, drawdown, rolling Sharpe, and market beta
- evaluating sensitivity to thresholds, stop-loss rules, leverage, and structural breaks

## Methodology

The project followed a structured quantitative research process:

1. **Data Preparation**
   - Imported daily price data
   - Cleaned and aligned time series
   - Applied log transformations
   - Conducted exploratory data analysis and correlation checks

2. **Integration Order Testing**
   - Applied ADF and KPSS tests
   - Evaluated whether price series were broadly consistent with I(1) behavior
   - Confirmed that first differences were generally stationary

3. **VAR and Lag Selection**
   - Built VAR estimation from first principles
   - Used AIC and BIC for lag selection
   - Selected VAR(1) based primarily on BIC

4. **Cointegration Testing**
   - Applied Engle-Granger pairwise cointegration tests
   - Applied Johansen testing for broader cointegration context
   - Selected three relationships for deeper analysis and strategy testing

5. **Mean Reversion Analysis**
   - Estimated equilibrium spreads
   - Applied Ornstein-Uhlenbeck-style mean-reversion diagnostics
   - Estimated half-life, mean-reversion speed, and equilibrium volatility

6. **Signal Construction**
   - Converted spreads into standardized Z-score signals
   - Swept threshold parameters to assess robustness
   - Chose trading thresholds based on stability rather than one-off optimization

7. **Backtesting**
   - Tested three strategy variants:
     - basic mean-reversion strategy
     - re-entry and stop-loss strategy
     - leveraged version of the stop-loss strategy
   - Evaluated performance across return, volatility, Sharpe, drawdown, rolling beta, and trade behavior

8. **Adaptive Estimation**
   - Discussed rolling re-estimation
   - Applied Kalman Filter concepts to explore time-varying hedge ratios and adaptive spread estimation

## Selected Relationships

The final trading relationships are anonymized in this public summary.

| Relationship | Description |
|---|---|
| Relationship 1 | Selected based on pairwise cointegration evidence, economic intuition, and tradable mean-reversion behavior |
| Relationship 2 | Selected based on strong long-run relationship characteristics and interpretable hedge-ratio behavior |
| Relationship 3 | Selected based on cointegration evidence, relative-value structure, and favorable backtest behavior |

The selected instruments are not disclosed because this repository is intended to summarize the research framework rather than publish the full strategy universe or trade specification.

## Strategy Design

The project tested three strategy designs.

### Strategy 1: Basic Mean-Reversion Strategy

The first strategy entered trades when the spread crossed upper or lower Z-score thresholds and exited when the spread reverted toward equilibrium.

This strategy produced mixed results, highlighting that cointegration alone is not enough to generate strong trading performance.

### Strategy 2: Re-Entry and Stop-Loss Strategy

The second strategy added immediate re-entry logic and tight stop-loss controls. This materially improved performance by reducing drawdowns, controlling downside, and increasing the consistency of realized trades.

The stop-loss framework led to stronger Sharpe ratios and lower drawdowns across the selected relationships.

### Strategy 3: Leveraged Strategy

The third strategy applied 2x leverage to Strategy 2.

This improved absolute returns while maintaining relatively low market beta and moderate drawdowns in the tested sample.

## Key Results

In the stop-loss strategy, the three selected relationships produced positive annualized returns during the test period:

| Relationship | Approx. Annualized Return | Approx. Annualized Sharpe |
|---|---:|---:|
| Relationship 1 | 5.9% | 2.3 |
| Relationship 2 | 3.2% | 1.8 |
| Relationship 3 | 10.5% | 2.8 |

In the 2x leveraged version, annualized returns increased approximately to:

| Relationship | Approx. Annualized Return |
|---|---:|
| Relationship 1 | 12.1% |
| Relationship 2 | 6.5% |
| Relationship 3 | 21.8% |

For the 2024 calendar year, an equally weighted 2x leveraged combination of the three selected relationships produced an estimated return of approximately **16.5% after transaction costs**.

## Interpretation

The project found that cointegration alone was not sufficient to generate robust trading performance. The basic strategy produced mixed results, while the stop-loss and re-entry framework materially improved outcomes.

The results suggest that implementation design can matter as much as statistical relationship selection. Signal construction, stop-loss rules, holding periods, transaction costs, parameter stability, and structural break risk all had major effects on realized performance.

The strongest result came from Relationship 3, while Relationship 2 demonstrated faster mean reversion but weaker profitability. Relationship 1 benefited meaningfully from the enhanced stop-loss framework.

## Risk and Robustness Considerations

The project should not be interpreted as a production-ready trading strategy.

Important limitations include:

- small number of selected relationships
- limited historical sample
- simplified transaction cost assumptions
- no financing, borrow, slippage, or liquidity modeling beyond basic transaction costs
- possible parameter sensitivity
- structural break risk
- possible overfitting in strategy design
- limited out-of-sample regime diversity
- simplified comparison against broad hedge fund indices
- undisclosed instrument universe in the public version

The benchmark comparison is also imperfect because three selected relationships are not directly comparable to a diversified institutional portfolio.

## Structural Break Discussion

The analysis included discussion of possible structural breaks affecting the selected relationships.

Potential structural break drivers included:

- changes in business models or regulation
- macroeconomic regime shifts
- monetary policy divergence
- commodity-linked shocks
- geopolitical events
- changes in liquidity or market microstructure
- breakdowns in historical relationships

This reinforced the importance of rolling recalibration, regime awareness, and adaptive estimation methods.

## Future Improvements

Possible extensions include:

- expanding the instrument universe
- testing more relationships
- applying stricter walk-forward validation
- introducing purged or embargoed cross-validation
- modeling slippage, financing, borrow costs, and execution constraints
- stress-testing across more market regimes
- comparing static versus rolling hedge ratios
- improving Kalman Filter calibration
- adding more robust structural break detection
- testing portfolio construction across multiple relationships
- applying capital allocation and volatility targeting frameworks

## Relevance to Quantitative Finance

This project reflects several core quantitative finance skills:

- time series analysis
- cointegration testing
- statistical arbitrage research
- spread construction
- mean-reversion modeling
- backtesting
- risk and drawdown analysis
- market-neutral strategy evaluation
- parameter stability assessment
- implementation-aware research design

The main takeaway was not simply that a strategy appeared profitable in a backtest, but that systematic trading research must be evaluated through robustness, regime sensitivity, and realistic implementation constraints.
