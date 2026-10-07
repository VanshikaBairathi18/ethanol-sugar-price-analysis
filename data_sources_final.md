# Data Source Log
### Ethanol Blending vs. Sugar Prices in India — Project Documentation

This log records every data source used in this project, which file it feeds into,
and how reliable/authoritative each source is.

---

## 1. Sugar Price (India, Uttar Pradesh)

- **Source:** Agmarknet (agmarknet.gov.in) — Directorate of Marketing & Inspection,
  Ministry of Agriculture & Farmers Welfare, Government of India
- **What it is:** Daily wholesale price and arrival reports, Commodity = Sugar,
  State = Uttar Pradesh, downloaded year-by-year (2021-2026), then aggregated to
  yearly averages (Modal Price)
- **Reliability:** Official primary government source, directly downloaded.
- **Known limitation:** Agmarknet's date-range filter does not allow dates before
  2021, which set this project's overall time window. Uttar Pradesh used as a
  representative state (largest sugar producer) rather than all-India.

## 2. Ethanol Diversion % (and Sugar Production)

- **Sources:** ISMA (Indian Sugar & Bio-Energy Manufacturers Association) statements,
  accessed via news reporting (Tribune India, Deccan Herald, Hindustan Times/
  PressReader), since ISMA does not publish a public downloadable dataset.
  Cross-validated against the Government of India's PIB Press Release
  (21 Aug 2026, Release ID 293781), which independently states diversion fell
  from ~12% (2022-23) to ~9% (2025-26) — closely matching the calculated figures
  from raw ISMA tonnage data (10.4% and 9.9% respectively).
- **Reliability:** Secondhand (news reporting ISMA's statements) but internally
  cross-validated against an official government release.
- **Known limitation:** Ethanol Supply Year (Nov-Oct) mapped to its starting
  calendar year as an approximation. Where multiple estimates existed for one
  season (initial vs. revised), the most recent/final estimate was used.
  2026 diversion and production figures use the ESY 2025-26 estimate as a proxy,
  since ESY 2026-27 had not started at the time of analysis.

## 3. Global Sugar Price

- **Sources:** World Bank "Pink Sheet" Commodity Markets Data, Monthly Prices
  (Jan 2021-Jul 2026, "Sugar, world" series), gap-filled for August 2026 using
  ICE Sugar No. 11 futures (via Investing.com historical data), since World Bank's
  monthly data lags by about a month.
- **Reliability:** World Bank data is official and directly downloaded. The ICE
  figure is a market data aggregator, lower-tier than World Bank but used only to
  fill a one-month gap, with the overlapping month (July 2026) cross-checked
  between both sources and found consistent.
- **Known limitation:** Converted from USD/kg to Rs/quintal using IRS yearly
  average USD-INR exchange rates; 2026's rate is a partial-year (Jan-Sep) average.
  Note: the Government of India's own PIB release cites a different global price
  figure ($474 to $552/tonne, Jun-Aug 2026) than World Bank/ICE benchmarks
  (~$310-400/tonne for the same period) — likely due to a different reference
  index (possibly ISO composite price vs. ICE futures). Both are legitimate
  benchmarks measuring slightly different things; this project uses World Bank/
  ICE for consistency across the full time series, while citing the PIB figure
  separately as the government's own stated reference point.

---

## Overall Data Quality Notes

1. **Time window:** 2021-2026, constrained primarily by Agmarknet's date-range
   limitation on sugar price data.
2. **Two sources disagree in places** (e.g., USDA vs. ISMA sugar stock estimates;
   PIB's global price figure vs. World Bank/ICE) — disclosed transparently above
   rather than silently reconciled.
3. **2026 is a partial/incomplete year across several variables** — sugar price
   data is relatively complete, but rainfall, exact diversion %, and production
   for 2026 rely on proxies or in-progress estimates, not final actuals.
4. **Sample size:** With only 6 years of data, the regression's statistical power
   is limited; results are reported as directional findings, not statistically
   significant causal estimates (see README and dashboard Methodology page for
   full caveat).
