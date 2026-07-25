# Swedish personal-finance reference data, 2026

Machine-readable reference data for Swedish personal finance, extracted from the data layer behind [MacLaine Finance](https://maclaine.se/en/finance) and published so you don't have to scrape Skatteverket yourself.

**Licence: [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/).** Public domain, no attribution required. A link back is appreciated, never demanded.

**This is reference data, not tax advice.** It is maintained because I need it accurate for my own calculators, but verify anything load-bearing against [Skatteverket](https://www.skatteverket.se/privat/skatter/beloppochprocent) before you rely on it.

## Files

| File | Contents |
|---|---|
| `municipal-tax-rates-2026.json` / `.csv` | All 290 Swedish municipalities with their combined municipal + regional income tax rate. Range: 28.93% to 35.65%. |
| `burial-fee-2026.json` | Begravningsavgift: the national rate plus the two municipalities that set their own. |
| `trossamfund-rates-2026.json` | The 20 registered religious communities whose membership fee Skatteverket collects, with Swedish and English names. |
| `national-constants-2026.json` | Headline national figures: prisbasbelopp, inkomstbasbelopp, employer fees, state tax threshold, ISK, capital gains, ROT/RUT, mortgage rules, property fee, deposit guarantee, policy rate. |

Every file carries a `_meta` block with the tax year, source, retrieval date, licence and disclaimer, so a single file read in isolation is still correctly attributed and correctly dated.

## The one thing worth knowing about the municipal rates

The `rate` field is **kommunalskatt + regionskatt only**. Two further fees sit on the same taxable income and are not in it:

- **Begravningsavgift** (burial fee): mandatory for everyone registered in Sweden regardless of belief, ~0.292% nationally. See `burial-fee-2026.json`.
- **Trossamfundsavgift**: voluntary, members only, 0.50% to 1.00%. See `trossamfund-rates-2026.json`.

Neither affects jobbskatteavdrag, which is calculated on the municipal rate alone. Getting this wrong is the single most common error I see in third-party Swedish tax calculators, which is most of why these are three files instead of one.

## What is not here

Bracket structures and the rules governing how these figures interact (grundavdrag and jobbskatteavdrag tables, pension contribution floors and ceilings, the age-dependent rules) are not published here. Those are the calculators' logic rather than reference data, and they live at [maclaine.se/en/finance](https://maclaine.se/en/finance), free to use, no account, no tracking. If you want a worked net-salary figure, [the salary tool](https://maclaine.se/en/finance/salary) will give you one and show its working.

## Updates

Regenerated each January when the new tax year's figures are published. `styrranta` (the Riksbank policy rate) is the one point-in-time value here; check the Riksbank for the current rate rather than trusting this file.

Spotted an error? [Open an issue](../../issues). I would much rather hear about it than ship it.
