What's Driving India's Sugar Price Spike?

A data analysis project investigating whether ethanol diversion, domestic production, or global markets are behind India's 2026 sugar price surge — using real government and institutional data (2021-2026) and multiple linear regression.

The Question

In 2026, Indian sugar prices hit record highs, and public narratives pointed to several possible causes: ethanol diversion under the government's blending program, a domestic production shortfall, crop disease, festive demand, hoarding, and global market pressure. The Indian government itself stated in August 2026 that the price rise "cannot be attributed to ethanol alone." This project tests that claim directly using available data, rather than assuming any single cause.

Key Findings
Sugar production showed the clearest relationship with price (R² = 0.35) — lower production consistently aligns with higher prices.
Global sugar prices showed almost no relationship with domestic price (R² = 0.00) — Indian prices kept rising even as global prices fell from 2023 onward. This points to a domestic story, not an imported one.
Ethanol diversion showed an inconsistent relationship with no clear trend (R² = 0.11), and its effect flipped direction across different model specifications — meaning the data cannot confirm the common narrative that ethanol diversion is driving India's sugar prices.
A regression trained on 2021-2025 predicted 2026's price would be ₹4,147.28/quintal; the actual price was ₹4,648.60/quintal — a 10.8% gap likely explained by factors this data can't measure directly: disease damage, festive demand, and hoarding/speculation.
Dashboard

Show Image

Show Image

Methodology (brief)

Multiple linear regression (2021-2025) testing sugar price against three factors: ethanol diversion %, sugar production, and global sugar price (converted to ₹/quintal using yearly average USD-INR exchange rates). 2026 was held out as a case study rather than included in the regression: the model's prediction for 2026, based on 2026's actual factor values, was compared against the real observed price.

Important limitation: with only 6 years of data, none of the regression coefficients are statistically significant at conventional thresholds (p > 0.05 for all variables), and the model shows signs of multicollinearity. Findings should be read as directional patterns in the available data, not proven causal effects.

Full data source log, including which figures are official government data versus secondhand reporting, is documented in data_sources_final.md.

Data Sources
Sugar price: Agmarknet (Govt. of India), Uttar Pradesh, 2021-2026
Ethanol diversion %: ISMA statements (via Tribune India, Deccan Herald), cross-validated against the Government of India's PIB Press Release (21 Aug 2026, Release ID 293781)
Sugar production: ISMA seasonal estimates
Global sugar price: World Bank Pink Sheet (Jan 2021-Jul 2026) + ICE Sugar No. 11 futures (Aug 2026 gap-fill), converted to ₹/quintal using IRS yearly average USD-INR exchange rates
Files in This Repo
run_regression.ipynb — the regression analysis, run in Python (pandas, statsmodels)
dashboard_page1.jpg — main dashboard: scatter plots, trend chart, predicted vs. actual
dashboard_page2.jpg — methodology & data sources page
data_sources_final.md — full data source log with reliability notes
Tools Used

Power BI (data cleaning, merging, dashboard), Python (regression analysis via pandas and statsmodels), and data sourced directly from Agmarknet, PPAC, IMD, USDA FAS GAIN, World Bank, ISMA, and PIB.
