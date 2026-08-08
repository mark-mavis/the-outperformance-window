# The Outperformance Window

## How the Odds of Beating the Market Change Across 5–20 Trading Days

**Research proposal and pre-analysis plan**  
**Status:** Study design  
**Author:** Mark Mavis
**Date:** August 2026

---

## Abstract

This project investigates whether the probability that an individual U.S. stock outperforms the broader market changes as the return-measurement window increases from 5 to 20 trading days. For each stock and horizon, the study compares the stock's total return with the return of a broad-market benchmark over the same dates. The principal outcome is a binary indicator equal to one when the stock beats the market and zero otherwise. Estimated win probabilities, formal odds, excess returns, and uncertainty intervals will be reported for every horizon from 5 through 20 trading days. The primary analysis will use a diversified, rule-based sample of stocks; Apple Inc. (AAPL) will be presented as a detailed case study. The design addresses overlapping observations, cross-sectional dependence, multiple comparisons, and survivorship bias. The study is descriptive and historical: it measures how frequently outperformance occurred, not whether future outperformance can be guaranteed.

## 1. Introduction

Statements such as “AAPL outperformed the market during the previous 20 trading days” are common in financial analysis. Such statements are incomplete, however, unless they identify the market benchmark, the method used to calculate returns, and the time horizon. They also say little about whether the result is unusual or persistent.

This study extends the question beyond a single stock and a single horizon. It measures outperformance across a diversified sample of stocks and across every horizon from 5 to 20 trading days. This approach allows the project to examine whether the apparent odds of beating the market rise, fall, or remain stable as the measurement period becomes longer.

The project does not treat historical outperformance as proof of forecasting ability. Instead, it provides a transparent description of relative performance and establishes a framework that could later support tests of momentum, persistence, or predictive strategies.

## 2. Research Question

> **Across a diversified sample of U.S. stocks, how does the historical probability of beating the overall market change as the measurement window increases from 5 to 20 trading days?**

### Secondary questions

1. How much do outperformance probabilities differ across individual stocks and economic sectors?
2. Is AAPL's outperformance profile materially different from that of the broader sample?
3. Are the conclusions sensitive to the benchmark, sample period, or treatment of overlapping return windows?
4. Does the economic magnitude of excess returns change with the measurement horizon, even when the win probability does not?

## 3. Hypotheses

The primary horizon-comparison hypotheses are:

$$
H_0: p_5=p_6=\cdots=p_{20}
$$

$$
H_A: \text{At least one horizon has a different probability of outperformance.}
$$

Here, $p_h$ is the probability that a sampled stock outperforms the benchmark over a window of $h$ trading days.

A secondary test at each horizon considers:

$$
H_{0,h}: p_h=0.50
$$

This 50% reference point is useful for interpretation, but it is not automatically the theoretically correct probability for a capitalization-weighted index. The index's weighting, the distribution of individual-stock returns, and the selected stock universe may cause the expected proportion to differ from one-half.

## 4. Data

### 4.1 Stock universe

The primary sample will contain approximately 30 U.S. stocks selected by a rule established before examining the results. The sample will be stratified across economic sectors so that the findings are not driven by the technology sector or by a few unusually large companies. AAPL will be included as the principal case study.

The final sampling rule, stock list, and study dates must be recorded before the main analysis begins. If reliable historical index-membership data are available, the preferred robustness sample will use historical constituents rather than only companies that survive to the end of the study.

### 4.2 Market benchmark

The primary market proxy will be **SPY**, the exchange-traded fund that tracks the S&P 500 Index. A robustness analysis may use another broad-market proxy, such as a total-U.S.-market fund.

### 4.3 Prices and returns

The study will use adjusted closing prices from one consistent data provider. Adjusted prices account for stock splits and distributions and therefore provide a practical total-return measure when calculated consistently for both the stock and benchmark.

The dataset should contain, at minimum:

- trading date;
- ticker symbol;
- adjusted closing price;
- benchmark adjusted closing price;
- sector classification; and
- index membership or sample-eligibility information, when available.

Missing observations, trading suspensions, ticker changes, mergers, and delistings will be documented rather than silently discarded.

## 5. Methods

### 5.1 Horizon returns

For stock $i$, date $t$, and horizon $h$, the trailing adjusted-price return is:

$$
R_{i,t,h}=\frac{P^{adj}_{i,t}}{P^{adj}_{i,t-h}}-1,
\qquad h\in\{5,6,\ldots,20\}.
$$

The benchmark return over the identical dates is:

$$
R_{m,t,h}=\frac{P^{adj}_{m,t}}{P^{adj}_{m,t-h}}-1.
$$

The stock's excess return is:

$$
ER_{i,t,h}=R_{i,t,h}-R_{m,t,h}.
$$

### 5.2 Outperformance indicator

The stock is classified as beating the market when its excess return is positive:

$$
Y_{i,t,h}=\mathbb{1}(ER_{i,t,h}>0).
$$

Ties will be coded separately and reported. A robustness analysis will require outperformance to exceed a small practical threshold, such as estimated transaction costs, rather than merely exceed zero.

### 5.3 Probability and odds

For each horizon, the estimated outperformance probability is the proportion of eligible observations for which $Y_{i,t,h}=1$:

$$
\hat p_h=\frac{1}{N_h}\sum_{i,t}Y_{i,t,h}.
$$

Formal odds will be calculated as:

$$
\widehat{Odds}_h=\frac{\hat p_h}{1-\hat p_h}.
$$

For example, a 60% estimated probability corresponds to odds of $0.60/0.40=1.5$, or **1.5 to 1**. The report will present probabilities and odds separately to prevent the terms from being used interchangeably.

### 5.4 Aggregation

The primary estimate will give each stock equal weight: first calculate the win probability for each stock at each horizon, then average those probabilities across stocks. A pooled observation-level estimate will be reported as a secondary result. This prevents companies with longer or more complete price histories from automatically dominating the main estimate.

Results will also be summarized by stock and sector. Alongside the binary win rate, the analysis will report mean and median excess returns so that statistical frequency is not confused with economic magnitude.

### 5.5 Statistical inference

Rolling return windows overlap. Consequently, observations on adjacent dates share many of the same daily returns and cannot be treated as independent. Stocks are also exposed to common market events, producing dependence across companies.

Confidence intervals will therefore be estimated with a block-resampling or dependence-robust method that preserves short-run time dependence and common-date effects. As a sensitivity check, the study will repeat the analysis with non-overlapping windows. When many stock-level or horizon-level tests are reported, adjusted p-values or simultaneous confidence intervals will be used to limit false discoveries.

## 6. Analysis Plan

The analysis will proceed in the following order:

1. Freeze the sampling rule, ticker list, benchmark, and date range.
2. Download and validate adjusted-price data from one provider.
3. Check missing dates, corporate actions, ticker changes, and sample eligibility.
4. Calculate stock, benchmark, and excess returns for horizons 5 through 20.
5. Estimate equal-weighted outperformance probabilities and formal odds.
6. Construct uncertainty intervals that account for dependent observations.
7. Compare results across horizons, stocks, and sectors.
8. Present AAPL as a case study within the broader results.
9. Run the prespecified robustness checks.
10. Interpret the findings without treating historical frequencies as forecasts.

## 7. Planned Tables and Figures

### Main figures

- **Outperformance curve:** estimated probability of beating the market at each horizon from 5 to 20 days, with confidence intervals.
- **AAPL comparison:** AAPL's probability curve plotted against the equal-weighted sample curve.
- **Stock–horizon heat map:** win probability for every stock and horizon.
- **Excess-return distribution:** distribution of relative returns at selected horizons.

### Main tables

- sample composition and sector coverage;
- probability, odds, mean excess return, and median excess return by horizon;
- stock-level and sector-level summaries; and
- robustness results under alternative specifications.

## 8. Robustness Checks

The following checks will be specified before results are interpreted:

- replace SPY with a broader total-market benchmark;
- compare equal-weighted and pooled estimates;
- use non-overlapping return windows;
- divide the sample into earlier and later periods;
- examine calm and high-volatility market periods separately;
- require excess returns to exceed a practical threshold;
- compare mean, median, and binary outperformance measures; and
- repeat the analysis using a historical-constituent universe if those data are available.

Exploratory analyses conducted after seeing the primary results will be labeled clearly as exploratory.

## 9. Limitations

This design has several important limitations:

- Historical win rates do not establish future predictability.
- Results may depend on the selected stocks, benchmark, and date range.
- A sample based only on currently successful companies can introduce survivorship bias.
- Overlapping windows can make naive confidence intervals too narrow.
- A positive excess return may be too small to be economically meaningful after costs.
- Adjusted-price conventions can differ across data providers.
- Testing many stocks and horizons increases the risk of chance findings.
- Market-cap-weighted benchmarks complicate a simple interpretation of 50% as neutral.

These limitations will be addressed where possible and stated explicitly where they cannot be eliminated.

## 10. Reproducibility

The completed project should preserve:

- the final research protocol and sampling rule;
- raw-data source information and retrieval dates;
- a data dictionary;
- cleaning and analysis code;
- software and package versions;
- a record of exclusions and missing observations; and
- generated tables and figures.

Random seeds will be fixed for resampling procedures. Raw data will not be altered manually; corrections will be implemented through documented code.

## 11. Interpretation Standard

The study will distinguish among three claims:

1. **Descriptive:** sampled stocks historically beat the benchmark at a given frequency.
2. **Statistical:** estimated differences are unlikely to be explained by sampling variation under the stated model.
3. **Economic:** excess returns are large enough to remain meaningful after plausible costs and implementation constraints.

Evidence for one claim will not automatically be presented as evidence for the others. In particular, a horizon with a win probability above 50% is not by itself a profitable trading strategy or a forecast of future performance.

## 12. Expected Contribution

The project will produce a horizon-by-horizon view of relative stock performance rather than relying on a single arbitrary window. Its contribution is a transparent comparison of outperformance frequency, formal odds, and return magnitude across stocks while retaining AAPL as an accessible example. The resulting framework can later be extended to investigate whether recent outperformance predicts subsequent returns, but that predictive question is outside the primary scope of this study.

---

## Disclaimer

This project is for research and educational purposes only. It does not provide investment advice, and its results should not be interpreted as a recommendation to buy or sell any security.
