---
title: "Is Gold Still a Safe Haven? Bitcoin and Gold in the 2026 Strait of Hormuz Crisis"
author: "Xiang Zheng, University of Toronto, October 2026"
geometry: margin=0.65in
fontsize: 10pt
header-includes:
  - \usepackage{titling}
  - \setlength{\droptitle}{-5em}
  - \usepackage[labelformat=empty]{caption}
---

**The question.** When a crisis hits, investors look for assets that hold their value while
stocks fall. Gold is the classic choice, and some argue that Bitcoin is "digital gold". The
2026 Strait of Hormuz conflict sent oil prices sharply higher. Did gold and Bitcoin protect
investors, or did they fall with the stock market?

**What I did.** Using daily prices from 2019 to October 2026, I measured how closely each
asset moved with the US stock market (the S&P 500): 0 means no connection, and 1 means it
moved one-for-one with stocks. I compared the conflict period (March–October 2026) with the
months before it and with six earlier market shocks since 2019, while allowing for oil, the
US dollar and interest rates. For Bitcoin, I also used a standard test from academic
research of how an asset behaves on the stock market's very worst days.

![How closely gold and Bitcoin followed the S&P 500 in each shock (dots), with the range of uncertainty (lines).](figures/beta_by_episode.png){width=86%}

**What I found.**

- **Gold moved with stocks far more than usual.** Its link to stocks rose from 0.08 over
  2019–2025 to about 1.0 during the conflict, higher than in any of the six earlier shocks,
  including a similar Israel–Iran conflict in June 2025. The result does not depend on a few
  big market days, and it holds with a direct measure of inflation-adjusted interest rates.
- **When stocks fell sharply, gold fell too.** On the two sharpest stock-market falls during
  the conflict, gold dropped 3.7% on average, more than stocks (2.2%).
- **Bitcoin behaved like a risky asset, not a hedge.** Since 2019 it has moved close to
  one-for-one with stocks on normal days (0.84) and by more on their worst days (1.58 on the
  worst 1% of days). In 2026 its link to stocks was again about 1.1 to 1.4.

**How sure can we be?** Gold's link to stocks began rising about four months before the war,
and the size of the change depends on which "before" period it is compared with: it is
clearly larger than chance in two of four comparisons. The conflict produced only two sharp
market falls, too few to judge gold as crash protection. These are patterns in prices; on
their own they do not show that the war caused them.

**What this means for decision-makers.** For *portfolio managers*: whether an asset protects
a portfolio is not fixed. Gold went from almost no link with stocks to moving one-for-one
within months, so allocations that rely on it should be checked against its recent
behaviour, not only its long-run average. For *risk managers*: stress tests that keep
correlations at historical levels can miss the case where diversifiers fall with stocks, as
gold did here. For *crypto allocations*: Bitcoin should be sized as a risky asset; in a
sell-off it adds to losses rather than offsetting them.

*Full analysis and Python code: https://github.com/betterandy24/bitcoin-gold-safe-haven*
