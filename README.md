# The Outperformance Window
## Does Recent Outperformance Predict Apple's Next Move?

**Research Project**  
**Status:** Pre-analysis  
**Author:** Mark Mavis  
**Date:** August 2026

---

## The Question

> **When Apple has outperformed the S&P 500 over the past 20 trading days, is it more likely to outperform the S&P 500 over the next 5 trading days?**

In other words: **Does momentum matter?** If Apple has been beating the market recently, does that suggest it will keep beating the market in the near term?

---

## Why This Matters

Investors often act on recent performance. "Apple's been crushing the market, so it should stay strong"—is that intuition right?

This study tests a specific form of that intuition: the relationship between Apple's *recent* outperformance (20 days) and its *immediate near-term* outperformance (5 days). 

If there's a real link, it could inform decision-making. If there's none, it's a reminder that past performance, even strong past performance, tells us little about what comes next.

---

## The Hypothesis

**Null Hypothesis:**  
When Apple outperformed over the past 20 trading days, the probability it outperforms over the next 5 days is 50% (no better than a coin flip).

**Alternative Hypothesis:**  
The probability differs from 50%—either higher (momentum) or lower (mean reversion).

$$H_0: P(\text{Next 5 days up} \mid \text{Past 20 days up}) = 0.50$$

$$H_A: P(\text{Next 5 days up} \mid \text{Past 20 days up}) \neq 0.50$$

---

## How We'll Test It

### The Setup
- **Stock:** Apple Inc. (AAPL)
- **Benchmark:** S&P 500 (SPY)
- **Time span:** Historical daily data (dates to be locked before analysis)

### The Process

**Step 1: Identify all 20-day windows**

For each trading date $t$, calculate Apple's return over the past 20 trading days and the S&P 500's return over the same period:

$$R_{AAPL, t, 20} = \frac{P_{AAPL, t}}{P_{AAPL, t-20}} - 1$$

$$R_{SPY, t, 20} = \frac{P_{SPY, t}}{P_{SPY, t-20}} - 1$$

Mark date $t$ as a "recent outperformance" event if:
$$R_{AAPL, t, 20} > R_{SPY, t, 20}$$

**Step 2: Look ahead 5 days**

For each date $t$ where Apple recently outperformed, check whether it outperforms *again* over the next 5 trading days:

$$R_{AAPL, t+5, 5} = \frac{P_{AAPL, t+5}}{P_{AAPL, t}} - 1$$

$$R_{SPY, t+5, 5} = \frac{P_{SPY, t+5}}{P_{SPY, t}} - 1$$

Mark a success (1) if $R_{AAPL, t+5, 5} > R_{SPY, t+5, 5}$; otherwise mark a zero (0).

**Step 3: Calculate the win rate**

$$\hat{p} = \frac{\text{# of 5-day windows where Apple outperformed after recent outperformance}}{\text{Total # of 20-day outperformance events}}$$

### The Test

Compare $\hat{p}$ to 50%:
- If $\hat{p}$ is significantly *above* 50%, there's evidence of momentum
- If $\hat{p}$ is significantly *below* 50%, there's evidence of mean reversion
- If $\hat{p}$ is close to 50%, there's no predictive value

We'll use a 95% confidence interval to determine whether any difference is real or just noise.

---

## What We'll Measure

1. **Outperformance probability:** What fraction of the time does Apple beat the market in the next 5 days *given* it just beat the market in the past 20?
2. **Excess return:** Average size of the next 5-day return difference
3. **Confidence interval:** The range where we expect the true probability to fall
4. **Comparison:** How does this compare to the baseline (50% or the unconditional probability)?

---

## Robustness Checks

Before finalizing, we'll test whether our result is sensitive to:
- **Different time periods:** Does the pattern hold in recent years vs. earlier years?
- **Different benchmarks:** What if we use a broader market fund instead of SPY?
- **Different lookback/lookahead windows:** Does the pattern hold with 10/5, 20/10, or 30/5 day combinations?
- **Volatility regimes:** Does momentum work better in calm markets or turbulent ones?

---

## Key Limitations

- **Past performance ≠ future:** Historical patterns may not persist
- **Survivorship:** We're only looking at Apple, a successful survivor
- **Transaction costs:** Even if a pattern exists, costs and fees could erase any edge
- **Correlation vs. causation:** Finding a pattern doesn't explain *why* it exists
- **Multiple testing:** If we test many windows, we risk finding patterns by chance

---

## What We Won't Claim

- This is **not a trading strategy** or investment recommendation
- We're not claiming **predictive power** for future markets
- We're not claiming the pattern is **economically profitable** after costs
- We're not claiming this pattern is **causal** or based on fundamental factors

We're simply answering: *Did this pattern exist in the historical data?*

---

## The Deliverable

**Main result:**  
A single number: the outperformance probability after recent outperformance, with a 95% confidence interval.

**Supporting analysis:**
- A 2×2 table showing outcomes (outperformed/underperformed recently × outperformed/underperformed next)
- Comparison to baseline rates
- Results from robustness checks
- Interpretation of whether any observed difference is likely real or noise

---

## Timeline

1. **Lock the time period** (which years of data to use)
2. **Download daily price data** (AAPL and SPY)
3. **Identify all 20-day outperformance events**
4. **Track the next 5-day outcomes** for each event
5. **Calculate the win rate and confidence interval**
6. **Run robustness checks**
7. **Report findings**

---

## Disclaimer

This project is for research and educational purposes only. It does not provide investment advice. Finding a historical pattern does not predict future market behavior or guarantee profits. Do not make investment decisions based on this analysis. Past performance is not indicative of future results.
