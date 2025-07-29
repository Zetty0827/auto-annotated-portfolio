---
type: PostLayout
title: Is a Recession Coming?
date: '2025-07-29'
excerpt: >-
  Reworking the Fed's recession probability model to gain new insights into the
  state of the US economy.
featuredImage:
  type: ImageBlock
  url: /images/Declining Graph 2.jpg
  altText: Post thumbnail image
  caption: Caption of the image
  elementId: ''
media:
  type: ImageBlock
  url: /images/Declining Graph.webp
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
Since Donald Trump returned to office in January 2025, the U.S. economy hasn’t had a chance to catch its breath. Right out the gate, his administration slapped tariffs back on imports from China, Mexico, Canada, and others—driving up costs for both manufacturers and regular people. Then came the “Big Beautiful Budget Bill,” extending previous Trump-era tax cuts and sending another wave of money toward infrastructure and defense. Along with that, stricter immigration rules and new limits on Medicaid and food stamps marked a sharp shift in federal priorities.

To pay the bill, Treasury Secretary Scott Bessent ramped up government borrowing, leaning especially hard on short-term bonds. The plan? Bet that rates will come down soon, so refinancing gets cheaper. But Fed Chair Jerome Powell isn’t budging. Trump is publicly calling for deep rate cuts to juice the economy, while Powell keeps pushing back, worried about stubborn inflation and the fallout from all this new spending and trade policy.

Looking at the data, wage growth has cooled off, so most workers aren’t seeing much growth in their paychecks. The prime-age employment rate—basically, how many 25- to 54-year-olds are working—has flattened out, which points to a job market that’s losing steam. Credit spreads—the gap between what companies and the government pay to borrow—have actually narrowed a bit, so markets aren’t panicking yet. But the yield curve is still inverted: when short-term rates are higher than long-term, it’s a sign that investors are bracing for rough times. Debt service ratios—share of household income goes toward paying off debt—are creeping up again after a drop during the pandemic. That means more families are shelling out for debt(loans, credit cards, etc...) which could become a problem if rates don’t fall or unemployment rises. On top of that, Google searches for “recession” have been bouncing around, telling you that people aren’t exactly feeling secure.

Meanwhile, the national debt just blew past $36 trillion. Some say heavy borrowing and spending are the price of investing in America, while others warn we’re gambling with the country’s future if interest rates spike or the economy takes another hit. So, are these signals pointing to a real recession on the horizon, or is this just what “normal” looks like in today’s economy? I’ll break down each indicator—jobs, wages, credit spreads, the yield curve, debt, and sentiment—and try to make sense of what’s actually happening. 

## Establishing a Baseline

Before building my own model, I started by recreating the Fed’s basic recession probability model as a benchmark. The Fed’s version is built around the yield curve—the difference between the 10-year and 3-month Treasury rates. When the curve goes negative, it’s often taken as a recession warning.

In my version, I used monthly data (for a closer look at changes as they happen) and ran the numbers using Python with up-to-date FRED data. My setup and logic matched the Fed’s as closely as possible, but because I used newer tools and higher-frequency data, the results aren’t identical—though they’re pretty close. The point was to test how well the classic signal holds up and to give myself a solid baseline before bringing in any extra variables.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXes7wI4kvGM4_6n3hiRCNmqhvPafqNmdniHpbKIOPn0RE1lgBwjd55GRDQVLgTi9OOApCQXro3RbWxnVkP1DpqlKXl-3YjNdyewUlLvmXmJD70uutxKmJLIo4hW0VNTzhd6096kcg?key=qhr3jCzOLCz5xmaAemL5Ng)

## Building a Broader Model: Beyond the Yield Curve

After reworking the classic Fed yield curve model, I wanted to go deeper and build something that captured more of what’s actually happening in the economy right now. The Fed’s original approach is simple, but in today’s world, recession risk is shaped by more than just bond market signals. I set out to design a model that blended the traditional—like the yield curve—with a handful of indicators that reflect the changing nature of work, debt, and public mood.

I started by creating a wide range of factors. Some were obvious, like prime-age employment (it gives a direct look at job market health) and wage growth (paychecks still drive the bulk of household spending). Others, like debt service ratios, are about how much financial stress households are feeling as borrowing costs rise. What really sets this model apart, though, is the inclusion of Google search data for “recession.” It’s a way to quantify public anxiety in real time—something you can’t get from economic statistics alone.

The process wasn’t just about piling on variables. I ran each factor through rigorous testing: dropping, splitting, and combining them to see which actually contributed useful, independent signals. Real wage growth was split out into wage growth and inflation separately, to get a clearer sense of what’s driving any change. Factors that didn’t add much predictive power or overlapped too much with others were cut.

A major limitation popped up here: adding Google Trends meant I could only use data from 2004 onward, since that’s when reliable search data starts. On one hand, this makes the model highly relevant to our digital, always-connected era, picking up on panics and sentiment swings that are more common now. On the other hand, it cuts off a big chunk of history, including some of the most important past recessions. There’s an argument that pre-2004 downturns—before smartphones, social media, and viral economic news—just aren’t as useful for understanding today’s risks. But losing that historical range also means the model hasn’t been “stress-tested” on the full variety of U.S. economic crises.

In the end, the model balances old and new: yield curve for the traditional signal, credit spreads for market stress, prime-age employment and wage growth for the real economy, debt service ratios for financial pressure, and Google Trends for public sentiment. The result is a tool that aims to be sharper and more responsive to the reality of 2020s America—even if it means giving up some of the lessons from the more distant past.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeQj4iJ0_0siUY1yVuCsmQ3X93SNXmC1qrRdA3OipCmg7feE1KblTypcU839oRX8hyoFkjtqOzUjFPyDX8q5HWx20Jp-sA03BO6XcpHQ44ndq1wTiKmRNWkXhB4opWCCC_MYZVU?key=qhr3jCzOLCz5xmaAemL5Ng)

## Testing Delayed Effects

The non-lagged model was a solid starting point, but real life isn’t that simple—sometimes economic signals take a while to actually hit the economy. Things like the yield curve and credit spreads can flash warning signs long before we see the real fallout in jobs or spending. To figure out if timing made a difference, I went back and tested what happens if you shift the yield curve and credit spreads back a few months. For the yield curve, I looked at what happens if you lag it by 6 or 12 months. For credit spreads, I tried 3 and 6 months. These aren’t random choices; they’re pretty standard in the research.

For each test, I built a new model, swapped in the lagged variable, and checked the numbers—looking at things like Pseudo R² and AIC to see if the fit improved. What stood out is that lagging the yield curve by 12 months and credit spreads by 6 months gave the best results. Basically, the warning signs from financial markets do matter, but you’ve got to be patient—those signals often take a while to show up in the broader economy.

You can see how each model performed in the graph below. The lagged models picked up on rising recession risk earlier and gave clearer signals than the versions without lags. Not every lag helped, though, and the best fit came from a 12-month lag for the yield curve and 6 months for credit spreads.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdGYY_TiXxRUZ6WkZxa-N4hfityVrBdoFeMKYTVXtteysDmQXM_I2hjkgLLwHyd0QplCuFXa-BlKGAB-in-s3mC0p1Y8A6XUyQHoWsPxyMYPpoxwCPSH6AI892PpziZCh6jBQ7wqw?key=qhr3jCzOLCz5xmaAemL5Ng)

## Looking Inside the Model

To really get a sense of what’s driving the numbers in my model, I put every key factor on one chart: wage growth, prime-age employment, debt service, yield curve, credit spread, and Google Trends for “recession.” I didn’t do this to compare the absolute values—each one has its own scale—but to watch how they actually move over time.

What I’m interested in is the story these lines tell. You can see which factors are steady most of the time and which ones swing up or down when something big happens. You start to notice if certain indicators get volatile when the economy’s shaky or if they move early before a recession or recovery. Sometimes, one factor starts to drift before the rest; other times, everything shifts at once.

The point isn’t just to spot reactions to bad news, but to see what these trends look like during good periods too. It gives a full picture: how each piece behaves when things are calm, and how the patterns change during stress. By seeing it all at once, it’s a lot easier to pick up on signals you’d miss if you only looked at one number at a time.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdB3CK5MDTs8etozkPYWLQ2-0U3f3EWvosevCV-JdKVBfoFvI32xlmJ2szAs4FRHgi8ymTSYK10uTavi86-vkooowNB1_aUUwHcFmf2jRvMzuISgDt_1vWRkPGOk-fgGJ4PuG8iyA?key=qhr3jCzOLCz5xmaAemL5Ng)

Prime-age employment has a pattern: it rose in the early 2000s, plateaued ahead of the 2008 recession, dropped sharply during the crisis, then recovered and climbed steadily. It took a sudden hit during COVID but bounced back quickly. Now it’s flattening out again, which has often signaled that the labor market is losing momentum and trouble could be brewing.

Wage growth has always bounced around, but lately, it’s been trending lower from the higher post-COVID peaks. The story isn’t one of major volatility, just a steady loss of momentum. If this keeps up, it means workers are getting less of a boost, and that can ripple through the whole economy.

The debt service ratio—the share of income going to debt payments—was high before the 2008 crash, then steadily declined for years. It fell hard during COVID thanks to stimulus and refinancing, but now it’s creeping up again. Paired with slower wage growth, it’s clear that household finances are feeling more strain.

The yield curve inverted before the 2008 recession, then returned to normal, only to take a major dive in 2022. It’s stayed deep in negative territory since then—a classic sign of economic stress that still hasn’t resolved.

Credit spreads loosely mirror the yield curve. They saw a dramatic spike in late 2008 and 2009 (reflecting real financial stress), then again during COVID. Since then, they’ve been on a slow, subtle decline, approaching the path of the yield curve. This means markets aren’t panicking, but the lack of recovery isn’t especially comforting.

Google Trends for “recession” show a clear pattern: spikes before and during downturns—like in 2008 and again with COVID—followed by quieter periods. After a huge spike in 2022–2023, search interest has bounced around. But right now, even beyond the data, the near-constant news about tariffs, Fed policy, and new economic policies is fueling uncertainty. Americans are hearing more questions and concerns about where the economy is headed, especially as debate heats up over the impact of recent policy changes.

## What’s Next?

At the end of the day, no matter how much you model or analyze, you can’t say for sure a recession is coming—if someone says otherwise, they’re probably selling you something. Even top economists and the Fed can’t fully predict these things. But if you look past the headlines—at the numbers, the mood at the Fed, and what people are actually saying—you see a country stuck in a cycle of instability and reaction.

Trump’s team keeps tossing out big numbers and talking up trade deals with Japan and the EU, but when you check for real details, it never quite adds up. The debt keeps growing, but regular people aren’t seeing any payoff. For most, nothing’s getting easier.

And it’s not just numbers—it’s real life. There’s a clear disconnect between those making decisions and everyone else. No matter how many speeches you hear about “growth” and “opportunity,” it just keeps getting tougher to get ahead. Wages aren’t keeping up, debt’s a bigger burden, and the cost of living is squeezing everyone. People aren’t buying the spin—they’re just trying to get by.

So where does that leave us? I can’t guarantee a recession is coming—but if we keep this up, it sure feels like that’s where we’re headed. You can’t keep reaching for quick fixes and dodging the hard choices forever. At some point, we need to put people first, face reality, and come up with a real plan. America doesn’t need another sales pitch. It needs something real.



Want to see the numbers and my work behind the scenes? Check out my Github:

[https://github.com/Zetty0827/Projects/blob/main/RecessionModelling.ipynb ](https://github.com/Zetty0827/Projects/blob/main/RecessionModelling.ipynb)

Want to see the Fed's model? Click the link below:

[https://www.newyorkfed.org/research/capital\_markets/ycfaq#/ ](https://www.newyorkfed.org/research/capital_markets/ycfaq#/)


