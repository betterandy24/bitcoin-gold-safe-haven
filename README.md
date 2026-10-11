# Is Bitcoin a Safe Haven? Evidence from the 2026 Strait of Hormuz Crisis

When a war or crisis hits, investors often move their money into "safe havens": assets that are expected to hold their value when the stock market falls. Gold is the classic example, and some people argue that Bitcoin is "digital gold". This project uses the 2026 Strait of Hormuz crisis, when fighting around one of the world's most important oil routes sent oil prices sharply higher, to test whether either of them actually behaved this way.

**Full analysis:** [analysis.ipynb](analysis.ipynb) (Python)

![How closely gold and Bitcoin followed the stock market in seven market shocks since 2019](beta_by_episode.png)

*Each dot shows how closely an asset followed the US stock market during a market shock (0 = no connection, 1 = moved one-for-one with stocks). Lines show the range of uncertainty. Gold usually sits near or below zero; in 2026 it jumped to about 1.*

## Key findings

**Bitcoin behaved like a risky investment, not a safe haven.** On the days the crisis escalated, Bitcoin usually moved in the same direction as US stocks, and its moves were no bigger than its normal day-to-day swings. Looking back to 2019, Bitcoin tends to fall even more than the stock market on the very worst days for stocks.

**Gold, surprisingly, stopped moving independently of the stock market.** Before the crisis, gold's daily ups and downs had almost nothing to do with stocks. During the crisis, gold started rising and falling together with them. Over the seven months of the conflict, gold lost about 20% of its value while US stocks gained about 13%. On the only two days during the war when US stocks fell sharply, gold fell too, by even more than stocks, although two days are too few to draw firm conclusions.

**2026 was unusual for gold, but not for Bitcoin.** In five of the six earlier market shocks since 2019, including a similar Israel–Iran conflict in June 2025, gold did not follow the stock market. 2026 is the only case where gold tracked stocks this closely, and this holds even when every shock is compared over just its first 40 trading days. Bitcoin, by contrast, behaved in 2026 much as it always has.

**Bitcoin and gold moved more closely together during the crisis.** This happened at the same time as gold began tracking the stock market, while Bitcoin's link to stocks stayed at its usual level. Their shared link to stocks explains part, but not all, of this closer co-movement, and the data cannot show what caused it.

## What this means

Whether an asset behaves as a "safe haven" is not a fixed fact. It can change from one crisis to the next. Gold has protected investors in most recent market shocks but did not behave that way in 2026, so investors should not assume it always will. I could not pin down why 2026 was different. One possibility is that gold had surged to a record high just before the crisis, so many investors were selling to lock in profits once the conflict began.

## How I did it

1. **Looked at the days the crisis changed.** I picked six key moments in 2026 (the start of the war, a ceasefire, a naval blockade, a peace memorandum, the ceasefire's collapse and attacks on oil tankers) and measured how Bitcoin, gold, oil and US stocks moved in the two days after each one, compared with their normal behaviour before the war.
2. **Compared calm times with the war.** I measured how closely Bitcoin and gold followed stocks, oil, the US dollar and interest rates before and during the war.
3. **Compared 2026 with earlier shocks.** I repeated the comparison for seven market shocks since 2019, including the COVID crash, Russia's invasion of Ukraine, the 2023 collapse of Silicon Valley Bank and the 2025 US tariff announcements.
4. **Applied a standard test from academic research** (Baur and Lucey, 2010), which checks how an asset behaves on the worst days for the stock market.

## How confident am I?

The 2026 crisis offers only a handful of clear events, the most extreme market days are rare, other news happened at the same time, and the historical comparison relies on windows of different lengths. The gold finding is the strongest: it holds up across several different checks. The Bitcoin findings agree with earlier research but rest on noisier data.

## Technical details

- **Event study (6 events, 2-day windows, baseline Jun 2025 – Jan 2026):** Bitcoin's abnormal returns were never significant (all |t| < 2). Oil moved +10.2% (t = 4.05) at the start of the war and −10.0% (t = −3.99) after the ceasefire.
- **Gold's beta to the S&P 500:** about 0 in the calm period, rising by 0.78 during the war (interaction regression, p = 0.008, Newey-West standard errors). Its 2026 beta of 1.02 (95% CI 0.71 to 1.33) compares with 0.08 over 2019–2025, −0.59 after the June 2025 Israel–Iran strikes and −0.55 during the 2023 SVB collapse.
- **Equal-length windows:** using only the first 40 trading days of each shock, gold's 2026 beta is 0.93 (95% CI 0.52 to 1.33), still the highest of the seven shocks.
- **2026 stress days:** only two war-period days had S&P 500 declines beyond the 2019–2025 5% threshold (−1.78%). Gold fell on both (average −3.8%, compared with −2.2% for stocks), whereas on such days in 2019–2025 gold's average return was −0.1%.
- **Bitcoin's beta:** 1.14 in 2026, compared with 1.05 over 2019–2025. Against the Jun 2025 – Jan 2026 baseline (1.87), Bitcoin's beta fell during the war, but that baseline was unusually high.
- **Correlations:** Bitcoin–gold rose from 0.10 to 0.43 (Fisher z-test, p = 0.001); Bitcoin–S&P 500 did not change significantly (p = 0.153). Removing each asset's co-movement with the S&P 500 lowers the war-period Bitcoin–gold correlation from 0.43 to 0.29 (calm period: 0.10 in both cases). Correlations are treated as supporting evidence because they rise mechanically with volatility (Forbes and Rigobon, 2002).
- **Factor regressions:** with the S&P 500, oil, the dollar (UUP) and TIPS (TIP) as explanatory variables, the stock market is Bitcoin's main driver and the dollar is gold's main driver in calm times.
- **Baur and Lucey (2010) test, 2019–2025:** gold's total beta is not significantly different from zero on normal days or on days in the worst 2.5–5% and 1–2.5% of stock-market returns, but is significantly positive on the worst 1% of days (0.14, p = 0.003). Bitcoin's total beta rises from 0.84 on normal days to 1.58 on the worst 1% of days. Both results hold when the COVID crash is excluded.

## Data

- **Massive API** (formerly Polygon.io): daily prices for Bitcoin (X:BTCUSD), the S&P 500 (SPY), gold (GLD and spot XAU/USD), Brent oil (BNO), the US dollar (UUP) and TIPS (TIP).
- **Yahoo Finance** (via `yfinance`): Bitcoin prices before October 2024, used for the 2019–2026 historical comparison. Over the 495 days covered by both sources, their daily returns have a correlation of 0.9995.
- **Event dates** were compiled from news timelines of the 2026 conflict (see the notebook) and should be checked against primary news reports.
- Raw price data are not included in this repository because of the data provider's license terms.

## Limitations

- Only six events in 2026, some overlapping with other news; event dates, historical windows and shock classifications are my own choices, and the historical windows differ in length.
- ETFs are used as proxies for the underlying assets.
- Bitcoin's daily close (midnight UTC) is four hours after the US stock market close.
- The most extreme stock-market days are few, so individual days can strongly influence the results.
- The results describe how assets moved together; they do not by themselves establish cause and effect.

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

## Author

Xiang Zheng, University of Toronto (Economics major; Statistics and Mathematics minors)
