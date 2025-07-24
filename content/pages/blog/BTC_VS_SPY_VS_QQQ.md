---
type: PostLayout
title: Comparing Bitcoin to the S&P and the NASDAQ
date: '2025-07-24'
excerpt: >-
  I compared Bitcoin’s performance to the S&P 500 and Nasdaq using real market
  data from the past several years. The goal was to see how these popular
  indexes stack up against crypto in today’s markets—looking at growth, risk,
  and how each one handles market shocks.
featuredImage:
  type: ImageBlock
  url: /images/Bitcoin.webp
  altText: Post thumbnail image
  caption: Caption of the image
  elementId: ''
media:
  type: ImageBlock
  url: /images/Bitcoin.webp
  altText: Post image
  caption: Caption of the image
  elementId: ''
addTitleSuffix: true
colors: colors-a
backgroundImage:
  type: BackgroundImage
  url: /images/bg2.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 100
author: content/data/team/doris-soto.json
---
When I first started investing, the go-to answer from everyone was the S\&P 500. It wasn’t even a question—if you weren’t trading every day, you were just supposed to keep putting money in and wait. That’s what everyone said works.

But over the last few years, things changed. Tech keeps taking over, the economy feels a lot more unpredictable, and Bitcoin exploded in a way nobody really saw coming. Suddenly, the old advice doesn’t seem as solid. The S\&P’s had some rough patches, and Bitcoin, for all its craziness, has made a lot of people rethink what’s possible.

So I wanted to actually run the numbers and see for myself: If you’re not a trader, is the S\&P 500 still the smart move, or is it time to look at Bitcoin? And since the Nasdaq is full of tech names and the “next big thing,” I threw that in too.

This whole project is about cutting through the usual talk and actually seeing how Bitcoin, the S\&P, and the Nasdaq stack up—risk, returns, everything—since after the 2008 crash. I wanted real answers, not just opinions.

## What I Did

1.  Pulled end-of-quarter prices for BTC, SPY, and QQQ (Yahoo Finance). Stocks from 2009, Bitcoin from 2020.

2.  Turned prices into quarterly returns for each.

3.  Tracked how $100 would’ve grown in each, plus volatility, biggest drawdown, Sharpe and Sortino. Wanted to see returns and what you’d have to put up with.

4.  Ran t-tests, ANOVA, Mann-Whitney, and checked correlations—basically, tested if any of these are really different or just look that way.

5.  Forecasted future returns (ARIMA) and future risk (GARCH) for each asset.

6.  Ran 2,000 Monte Carlo simulations for all three—just to see what 10 years could actually look like.

7.  Checked rolling beta and rolling correlation (how Bitcoin’s relationship with stocks shifts), and ran OLS regressions to see if stuff like rates or inflation actually explains anything.

8.  Looked at worst-case scenarios with VaR and CVaR.

9.  Did an event study on the FTX collapse—just zoomed in to see how each asset reacted.

## What I learned

### Growth, Risk, and the Experience 

Compound Annual Growth Rate (CAGR): 

*   QQQ (Nasdaq): 18.3% per year 

*   SPY (S\&P 500): 13.6% per year 

*   BTC-USD (Bitcoin): 65.8% per year (since 2020)

CAGR tells you the average annual return, including compounding. Bitcoin’s growth rate is way beyond either index, reflecting how explosive it has been.

Maximum Drawdown (worst loss from peak to trough): 

*   QQQ: -32.6%

*   SPY: -23.9%

*   BTC-USD: -71.9%

Drawdown captures the pain of big crashes. Bitcoin’s drawdowns have been over double the worst drops in QQQ or SPY.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfarCCJZr-weYKOHeVL7dfmQ8g1bwHZvzNtXROHGSTeil5f7ehLwiKLrgay3iV2etSdPrWv1oRCluf-CLpdTF5mlAF0mIuw0SjGwrLM5x0xHSCB_XS_dykouJuY2D_YU3haL5rE?key=PJsXnYpGWPzp0jbCzYmaZw)

Sharpe Ratio (reward per unit of total risk):

*   QQQ: 0.52

*   SPY: 0.48

*   BTC-USD: 0.46

Sortino Ratio (reward per unit of downside risk):

*   QQQ: 0.52

*   SPY: 0.36

*   BTC-USD: 0.88

Despite all its swings, Bitcoin’s return for the risk taken is similar to the indexes, and by the Sortino Ratio (focusing on negative volatility), it actually comes out ahead.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdVycwSgQzrgacEF5NWdyt17zqhoMCqFZmPm2U-M5jjJGPCRU4iwjoEmcgh9jwlJKKnKfjM68R2-KNtDoTR-kWmvxcu-F_WUUvWsPWXW_aqwb7txy8kg7-gLO8DKd-7IhneTimQ?key=PJsXnYpGWPzp0jbCzYmaZw)

If you invested $100 in Bitcoin and just held on, you’d have the biggest gains—but you would have had to sit through extreme ups and downs. QQQ beat SPY on both growth and risk-adjusted returns, showing the tech tilt has paid off for investors.

### Are These Differences Real? 

Investing isn’t just about eye-popping averages—you want to know if the results are reliable, or if you just got lucky. That’s where statistical tests come in.

T-test: Tests if Bitcoin’s average return is really different from the indexes, or if it’s just a statistical fluke. A p-value below 0.05 means you can be pretty sure it’s a real difference (by conventional research standards). Here, BTC vs QQQ is 0.12, BTC vs SPY is 0.10. These are “suggestive” (the difference is probably real) but not conclusive at the strictest standard, partly due to Bitcoin’s short history and huge swings.

ANOVA: Looks at all three assets together to see if at least one has an average return that stands out. With a p-value of 0.085, it’s just shy of being “statistically significant,” but it does suggest something unusual is going on—especially with Bitcoin’s numbers.

Mann-Whitney U Test: Rather than only comparing averages, this test looks at the entire spread of returns. It asks: Do these assets give you the same kind of ride, or are they fundamentally different in how gains and losses show up?

Bitcoin’s returns aren’t just higher on average—they’re much more extreme. You get far more quarters with massive wins and massive losses, compared to stocks. This means that holding Bitcoin isn’t just about chasing a higher return, but also accepting much bigger swings, for better or worse.

### Do These Assets Move Together?

Correlation measures whether assets move in sync or not. A value of 1 means they move together perfectly; 0 means they move totally independently. ​​Beta measures how much an asset moves compared to a benchmark—here, it’s “rolling,” meaning it’s recalculated over a moving window so you can see how relationships shift over time.

*   QQQ and SPY: 0.92 (very high—almost always move in the same direction)

*   BTC-USD and QQQ: 0.47

*   BTC-USD and SPY: 0.52

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc_GUjd-uK4FBr_2cYYRqNIhbOgL-2y94VAQTFa_vajXUM7HRgNm8YNEeP4HomnOJ3_Tht42gklkQdB40jhbhHYNI5ngxYPmRWXHmty3ccUmneaFbwgyaYtKl8fDZ7p-wZpv4og6A?key=PJsXnYpGWPzp0jbCzYmaZw)This graph tracks how closely Bitcoin’s returns move with the SPYand the Nasdaq (QQQ), quarter by quarter. The lines show the rolling correlation and the rolling beta (how sensitive Bitcoin is to moves in each index). The correlation lines vary, but move around 0.5. This means Bitcoin sometimes moves with the stock market. When beta is above 1, Bitcoin usually moves more than the S\&P or Nasdaq. So, if beta is 1.5, and the S\&P 500 rises 2%, you’d expect Bitcoin to rise about 3% (or fall 3% if the S\&P drops 2%), on average.

Bitcoin only loosely tracks the stock indexes. Sometimes it rises when stocks fall, and vice versa. That means adding Bitcoin to a traditional portfolio can offer real diversification, sometimes softening the blow during stock selloffs—but it can also make things bumpier overall.

### How Bad Can It Get?

Volatility tells you how much an asset’s value jumps around each quarter. Value at Risk (VaR) and Conditional VaR (CVaR) are ways to size up the worst-case scenarios.

Quarterly Volatility (Std Dev):

*   BTC-USD: 54%

*   QQQ: 9%

*   SPY: 7%

5% Value at Risk (VaR):

*   BTC-USD: -39.2% (5% chance of losing at least this much in a quarter)

*   QQQ: -10.0%

*   SPY: -13.2%

CVaR (Average of Worst 5% Quarters):

*   BTC-USD: -48.5%

*   QQQ: -15.1%

*   SPY: -15.7%

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc-whDjkc0sCfhJUZ8X3VgJoHIQsAORBcOdwus985AOarJrepv0OU--cHEvNas4czE0lbfO-rUNsfWc1_fxe6JcGxKzWPZrRKL4oWkm-hRng6Oj2HWS3yMaaak5NEs3uquHyNVY5Q?key=PJsXnYpGWPzp0jbCzYmaZw)

This graph shows the volatility over time for each of the assets. Both the S\&P and NASDAQ have low and fairly stable volatility. Bitcoin on the other starts off much higher, but is on a path towards stabilization.

### What Drives These Returns?

I ran OLS regressions to see if common factors like the market, interest rates, or inflation can explain how these assets move.

*   SPY: R² = 1.00 (market explains almost everything)

*   QQQ: R² = 0.82 (market and tech explain most of the moves)

*   BTC-USD: R² = 0.32 (not linked to broad economic factors)

R²: A high R² (like SPY) means the asset’s returns are predictable from big-picture trends. A low R² (like BTC) means a lot is happening that standard models can’t explain.

### What Might Happen Next?

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdBTGzl-T_jYdNHJk0A6_dyjajGz4NkQsjWs1g7BJR1cZfcJs-5M5Vgn2gzq2bE3yIwdVRM267gS4BFAbczT7bdsDYStEP8hdc4j4hTIUVz9qMpaO4u_oNyigMJS335r_SpBjG9pQ?key=PJsXnYpGWPzp0jbCzYmaZw)ARIMA models future returns based on past trends and cycles. For SPY and QQQ, the forecast lines are smooth and steady—they’re expected to keep producing similar returns to the past. For Bitcoin, the ARIMA forecast shows high expected returns despite its volatility.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfjQDzouQfNT2ZaWCHt6ZS73hAobwn3f3fCxCi5YtKnpP0lW3HBoTGjA_FSOhluncmW17dgGQQN_FC4Hv8-Jhi3fOkKUrUJRLQTJ--MmANu3GxTI0EfXGblZ3GAFJvIWFp1R_xK?key=PJsXnYpGWPzp0jbCzYmaZw)GARCH models forecast how risky (volatile) each asset will be. Stocks are projected to stay low-risk, with volatility barely moving. Bitcoin’s volatility, despite being much higher than the others, is on a downtrend.

### Monte Carlo Simulation: Many Possible Futures

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdJypQPbkhKvx2SSPnh5bgZYpBgxw_h_loV31y3pXvA054WwqO6nzmADmVIejWNLp39ohyY-ZsLS-ovBIPFv0m3wDJ2QWRc29Ijs5HNbnZs39wy2lnTH5Tp-vIss891KYZxT1E4xw?key=PJsXnYpGWPzp0jbCzYmaZw)

A Monte Carlo simulation doesn’t just give you an average—it shows you the range of what could actually happen if you invested today and held for 10 years, using the real ups and downs from the past.

*   SPY: Most scenarios are steady and positive—you rarely lose big.

*   QQQ: Slightly more spread; higher gains are possible, with some extra risk.

*   BTC-USD: The widest range by far—high concentration of simulations show profit, some even 10x or 100x, while others have you crashing to zero or close to it. 

This isn’t about predicting a single future, but showing the real odds: With Bitcoin, the chance for outlier success is huge, but so is the risk of disappointment. Stocks offer much more predictability, but not the same shot at outsized gains.

### Stress Test: FTX Collapse and Real-World Shocks

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcdkQ1RCsNG0e0b8xWxmea1dM21bbST2WrFhjjQN1Neu4UVcyBxXh4EN5pLg3sZV8bcJPp925Jgm9JljCOgfN2AXXONCwqiISVhxrpcxlv2vTetgB75yEbMPA0Zy5lHFoIQ2BT-gg?key=PJsXnYpGWPzp0jbCzYmaZw)The FTX collapse in late 2022 was a huge moment for crypto. When I zoomed in, Bitcoin, SPY, and QQQ all dropped—but none of the drops were extreme for their own histories. For Bitcoin, even a collapse like FTX is “just another bad quarter.” The t-stat was -0.31 and the p-value was 0.77.

A p-value below 0.05 is the benchmark for calling a result “significant”—it would suggest the drop was unusual compared to the past. A p-value of 0.77 is much higher, which means the drop during the FTX event was well within the normal range of Bitcoin’s typical volatility. For both stocks and Bitcoin, the event wasn’t an outlier when measured against their own wild histories.

## Limitations

*   We don’t have much Bitcoin data—just since 2020. That means a few big quarters can swing the whole comparison.

*   The stock indexes start in 2009, so the periods don’t really line up. We’re not seeing how these assets behave through the same cycles.

*   By using quarterly returns, we’re smoothing over the rough stuff that actually happens month to month, especially with crypto.

*   This is just looking at each asset alone. No mixing, no rebalancing, no “real world” portfolio building.

*   None of the numbers reflect trading fees, slippage, or taxes. Especially for Bitcoin, those can eat into returns.

*   By setting the risk-free rate to zero, we slightly inflate the Sharpe and Sortino ratios. Using the real US Treasury rate would lower them a bit, especially if rates are high. This doesn’t usually change the overall ranking, but it does mean the ratios aren’t exactly what you’d see in a professional fund analysis.

*   All the forecasts (ARIMA, GARCH, Monte Carlo) are just projections based on what’s happened lately. If markets change in a big way, these models won’t catch it.

*   Indexes like QQQ and SPY drop underperformers, so long-term results are boosted by survivorship bias.

*   The math doesn’t show what it feels like to live through big drops or wild swings. It assumes nobody sells during the tough times—which isn’t how most people actually behave.

## Takeaways

1.  The S\&P 500 isn’t the gold standard it’s made out to be. The data shows that the Nasdaq (QQQ) has left the S\&P behind, both in growth and risk-adjusted returns. Tech-driven stocks have been where the real gains happened.

2.  Crypto’s story is still unfolding. Despite its reputation for wild swings, the overall trend in Bitcoin’s volatility is downward—and the growth, so far, is unmatched. If that trend holds, ignoring crypto could mean missing out. Whether you add it to your portfolio or not comes down to your own risk appetite, but being “crypto-free” may be riskier than people think.

3.  It’s not too late to join the crypto train. Crypto isn’t just about price speculation. It’s a way to access decentralized finance, hedge against traditional financial system risks, and participate in new digital economies. Crypto’s blockchain technology can also lower transaction costs, improve transparency, and allow for faster global payments.

4.  Personally, I’m moving away from buy-and-hold S\&P 500 investing and focusing more on the Nasdaq for long-term growth. I will keep investing in crypto, but I’ll be watching closely—potentially using active strategies to take advantage of its still-immature market dynamics.

Want to see what I did behind the scenes? Check out my Github

<https://github.com/Zetty0827/Projects/blob/main/Crypto_VS_NASDAQ.ipynb>
