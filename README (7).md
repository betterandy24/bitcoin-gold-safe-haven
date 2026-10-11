# Is Bitcoin a Safe Haven? Evidence from the 2026 Strait of Hormuz Crisis

When a war or crisis hits, investors often move their money into "safe havens": assets that are expected to hold their value when the stock market falls. Gold is the classic example, and some people argue that Bitcoin is "digital gold". This project uses the 2026 Strait of Hormuz crisis, when fighting around one of the world's most important oil routes sent oil prices sharply higher, to test whether either of them actually behaved this way.

**Full analysis:** [analysis.ipynb](analysis.ipynb) (Python)

![How closely gold and Bitcoin followed the stock market in seven market shocks since 2019](beta_by_episode.png)

*Each dot shows how closely an asset followed the US stock market during a market shock (0 means no connection; 1 means it moved as much as stocks, in the same direction). Lines show the range of uncertainty. Gold usually sits near or below zero; in 2026 it jumped to about 1.*

## In short

Bitcoin behaved like a risky investment rather than a safe haven, as it has since 2019. Gold, unusually, rose and fell with the stock market during the 2026 conflict, but there were too few sharp market falls to tell whether it still protects investors in a crash. These are patterns in prices; on their own they cannot show that the war caused them.

## Key findings

**Gold followed the stock market far more than usual.** Before the conflict, gold's daily moves had almost nothing to do with stocks; during it, the two often rose and fell together. This shows up against three of the four "before" periods I compared with, and when every shock is compared over the same length of time, and no other market shock since 2019 comes close, including a similar Israel–Iran conflict in June 2025. Part of the change had already started a few months before the war.

**On the two sharp market falls during the conflict, gold fell too,** and by more than stocks. On similar days in 2019–2025 it was roughly flat on average.

**For Bitcoin, the main evidence is its long-run behaviour.** Since 2019 it has tended to move about as much as US stocks, and even more than stocks on their very worst days. In 2026 it behaved in its usual way, whether its price is taken at the US market close or later in the evening. Its reactions on individual conflict days were mixed: it rose noticeably after the war began, but not by more than it often moves over a few ordinary trading days.

**Bitcoin and gold moved more closely together during the conflict.** Their shared link to stocks explains part of this, but not all.

## What this means

Whether an asset behaves as a safe haven is not a fixed fact; it can change from one crisis to the next, so investors should not assume gold will always move against stocks. I could not establish why 2026 was different. One possibility, which I did not test, is that some investors sold gold to lock in profits after its sharp rise in 2025.

## How I did it

1. **Worst days for stocks, 2019–2025 (main evidence for Bitcoin).** A standard test from academic research (Baur and Lucey, 2010) checks how closely an asset follows stocks on normal days and on the very worst days for the stock market.
2. **Before vs. during the conflict (main evidence for gold).** I compared how closely Bitcoin and gold followed stocks, oil, the US dollar and interest rates before and during the conflict, using four different "before" periods.
3. **2026 vs. earlier shocks.** I repeated the comparison for six earlier market shocks since 2019, including the COVID crash, Russia's invasion of Ukraine and the 2025 US tariff announcements, over each shock's full length and over its first 40 trading days.
4. **Key conflict days (supporting evidence).** For six key moments in 2026, I looked at how Bitcoin and gold moved over the next one to three trading days, after taking out the part explained by the stock market, and compared those moves with their normal range.

## How confident am I?

- The 2026 conflict produced only six clear events to study.
- Some results depend on which "before" period is used, so I report several.
- Event dates come from news timelines, and I did not check for other economic news released on the same days.
- I use funds that track stocks, gold and oil as stand-ins for the assets themselves.

## Technical details

This section is for readers who want the exact numbers. **Beta** measures how much an asset moves when the S&P 500 moves by 1% (0 = no relation, 1 = one-for-one); CI is a 95% confidence interval. Model definitions are in the Technical notes at the end of the notebook.

| Measure | Sample | Result |
|---|---|---|
| Gold's beta to the S&P 500, before period (Jun 2025 – Jan 2026) | 167 days | 0.08 |
| Gold's beta to the S&P 500, conflict period (Mar 2 – Oct 9, 2026), S&P 500 only | 155 days | 1.02 (95% CI 0.71 to 1.33) |
| Change in gold's beta, conflict vs. before period, S&P 500 only | 167 + 155 days | +0.94 (95% CI 0.47 to 1.41) |
| Same change, also controlling for oil, the dollar and TIPS | 167 + 155 days | +0.78 (p = 0.008) |
| Same change against the last 60 / 120 / 180 pre-war trading days | 60 / 120 / 180 + 155 days | +0.60 / +0.65 / +0.86 (p = 0.27 / 0.03 / 0.001) |
| Gold's beta, first 40 trading days of the 2026 shock | 40 days | 0.93 (95% CI 0.52 to 1.33) |
| Gold's beta, all days 2019–2025 | 1,759 days | 0.08 (95% CI 0.03 to 0.14) |
| 2026 days with the S&P 500 down more than 1.78% (2019–2025 worst-5% threshold) | 2 days | Gold fell on both (average −3.8%, S&P 500 −2.2%) |
| Gold on the worst 5% of S&P 500 days, 2019–2025 | about 88 days | Average −0.1% |
| Bitcoin's beta to the S&P 500, all days 2019–2025 | 1,759 days | 1.05 (95% CI 0.75 to 1.36) |
| Bitcoin's total beta, Baur–Lucey test, 2019–2025 | normal days vs. worst 1% | 0.84 vs. 1.58 |
| Bitcoin's beta, conflict period (midnight UTC / 4 p.m. ET price) | 155 days | 1.14 (95% CI 0.76 to 1.52) / 1.38 |
| Bitcoin–gold correlation, before vs. conflict | 167 / 155 days | 0.10 vs. 0.43 (p = 0.001); partial correlation controlling for the S&P 500: 0.10 vs. 0.29 |

The 1.02 and +0.78 are different statistics: the first is gold's beta within the conflict period from a model with the S&P 500 only; the second is the increase relative to the before period in a model that also includes oil, the dollar and TIPS.

- **Event study, constant-mean model (2-day windows, CAR(0,+1)):** Bitcoin's abnormal returns were never significant (all |t| < 2). Oil moved +10.2% (t = 4.05) at the start of the war and −10.0% (t = −3.99) after the ceasefire.
- **Event study, market model (1-, 2- and 3-day windows, empirical p-values):** with the before-period beta, Bitcoin's abnormal return was +4.6% (p = 0.04) on the first day of the war and −5.5% (p = 0.01) on the first day of the ceasefire; with the 2019–2025 beta and distribution, all Bitcoin p-values are 0.11 or higher. Gold has one or two windows below 0.05 out of 18, consistent with chance.
- **Baur and Lucey (2010) test, 2019–2025:** gold's total beta is not significantly different from zero on normal days or on days in the worst 2.5–5% and 1–2.5% of stock-market returns, and slightly positive on the worst 1% of days (0.14, p = 0.003). Both assets' results hold when the COVID crash is excluded.
- **Correlations** are supporting evidence only, because they rise mechanically with volatility (Forbes and Rigobon, 2002).

## Data

- **Massive API** (formerly Polygon.io): daily prices for Bitcoin (X:BTCUSD), the S&P 500 (SPY), gold (GLD and spot XAU/USD), Brent oil (BNO), the US dollar (UUP) and TIPS (TIP), plus hourly Bitcoin prices for the US-close check.
- **Yahoo Finance** (via `yfinance`): Bitcoin prices before October 2024, used for the 2019–2026 historical comparison. Over the 495 days covered by both sources, their daily returns have a correlation of 0.9995.
- **Event dates** come from news timelines of the 2026 conflict; the notebook lists each date, the first US trading day used and the source.
- Raw price data are not included in this repository because of the data provider's license terms.

## How to run

1. Install the packages:
   ```
   pip install massive pandas numpy matplotlib statsmodels scipy yfinance jupyter
   ```
2. Open `analysis.ipynb` in Jupyter and run all cells. You will be asked for your own Massive API key; it is not stored in the notebook.

## References

- Baur, D. G., & Lucey, B. M. (2010). Is gold a hedge or a safe haven? An analysis of stocks, bonds and gold. *Financial Review*, 45(2), 217–229.
- Baur, D. G., & Smales, L. A. (2020). Hedging geopolitical risk with precious metals. *Journal of Banking & Finance*, 117, 105823.
- Bouri, E., Molnár, P., Azzi, G., Roubaud, D., & Hagfors, L. I. (2017). On the hedge and safe haven properties of Bitcoin: Is it really more than a diversifier? *Finance Research Letters*, 20, 192–198.
- Conlon, T., & McGee, R. (2020). Safe haven or risky hazard? Bitcoin during the Covid-19 bear market. *Finance Research Letters*, 35, 101607.
- Forbes, K. J., & Rigobon, R. (2002). No contagion, only interdependence: Measuring stock market comovements. *Journal of Finance*, 57(5), 2223–2261.
- Klein, T., Pham Thu, H., & Walther, T. (2018). Bitcoin is not the New Gold – A comparison of volatility, correlation, and portfolio performance. *International Review of Financial Analysis*, 59, 105–116.
- MacKinlay, A. C. (1997). Event studies in economics and finance. *Journal of Economic Literature*, 35(1), 13–39.
- Newey, W. K., & West, K. D. (1987). A simple, positive semi-definite, heteroskedasticity and autocorrelation consistent covariance matrix. *Econometrica*, 55(3), 703–708.

## Author

Xiang Zheng, University of Toronto (Economics major; Statistics and Mathematics minors)
