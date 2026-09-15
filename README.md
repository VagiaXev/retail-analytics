# Retail Revenue Optimization & Customer Lifetime Value (CLV) Analysis

## Table of Contents
- [Overview](#overview)
- [Repository Contents](#repository-contents)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Business Recommendations](#business-recommendations)
- [Documentation](#documentation)
- [How to Use](#how-to-use)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Overview
A proactive, end-to-end analytical pipeline built entirely in Excel, transforming 12,500+ rows of raw, uncleaned transactional retail data into strategic business recommendations. The project simulates an end-to-end performance review for a multi-category retail store — covering data cleaning, KPI reporting, Customer Lifetime Value (CLV) modeling, descriptive/diagnostic statistics, and an interactive BI dashboard.

**Key result:** a correlation analysis (r = 0.80) shows that Purchase Frequency accounts for 64% of the variance in Customer Lifetime Value, meaning repeat-purchase frequency scales long-term customer value far more than isolated large orders.

Full methodology, findings, and business recommendations are documented in detail on Confluence (see [Documentation](#documentation)).

## Repository Contents
- `retail_store_sales.xlsx` — the main analysis workbook, containing:
  - `Cleaned_data` — the validated, imputation-corrected master dataset
  - `KPI & CLV Overview` — high-level aggregate KPIs and the customer-level CLV table
  - `Data Insights` — descriptive and diagnostic statistics
  - `Chart Data Preparation` — supporting/hidden reference tables for the dashboard
  - `Interactive Dashboard` — the interactive BI interface (slicers, timeline, pivot charts)
- `docs/Retail Revenue Optimization & Customer Lifetime Value (CLV) Analysis-090926.pdf` — PDF export of the full Confluence documentation (methodology, findings, dashboard walkthrough)

## Dataset
- **Source:** [Retail Store Sales: Dirty for Data Cleaning](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning) by Ahmed Mohamed, via Kaggle
- **License:** [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — free to use, share, and adapt, provided appropriate credit is given
- **Description:** 12,500+ transactional retail records, deliberately engineered with missing values, inconsistent formatting, and categorical errors to simulate a raw, uncurated corporate database

> **Note on redistribution and adaptation:** CC BY-SA 4.0 is a *share-alike* license. Two things follow from that:
> 1. **Attribution is required** wherever the dataset (or the cleaned/derived version of it, e.g. the `Cleaned_data` tab) is used or shared — see Acknowledgments below.
> 2. **Share-alike applies to adaptations of the data itself.** If this repository includes the cleaned dataset (not just your original written analysis, charts, or commentary), that cleaned data is an adaptation of the original and should itself be shared under CC BY-SA 4.0, with credit to the original author. This is distinct from your own analysis, dashboard design, and written commentary, which you're free to license separately (see License section below). If you're unsure whether your specific use crosses into "adaptation" for CC BY-SA purposes, it's worth a quick look at the CC BY-SA 4.0 legal text or a legal opinion — I'm not a lawyer.

## Methodology
- **Data cleaning & standardization:** converted numeric columns from text (localized delimiters), audited `Transaction ID` for duplicate integrity
- **Missing value imputation:**
  - Reconstructed missing `Price Per Unit` / `Total Spent` using the relationship *Total Spent = Quantity × Price Per Unit*
  - Deduced missing `Item` values from `Price Per Unit` and category patterns
  - Imputed missing `Quantity` using the category **median** (chosen over the mode to avoid inflating revenue)
  - Labeled missing `Discount Applied` values as "Unknown" rather than guessing
- **Validity checks:** cross-verified that existing `Total Spent` values matched `Quantity × Price Per Unit`
- **Feature engineering:** derived `Day of the Week` and `Month` from transaction timestamps
- **KPIs:** Total Revenue, Total Units Sold, Total Transactions, Average Order Value, Average Items per Basket, Average Price per Item
- **CLV modeling:** aggregated by customer to calculate revenue contribution, transaction velocity, AOV, purchase frequency, and final Customer Lifetime Value
- **Statistics:** descriptive stats (mean, median, distribution shape) and diagnostic correlation analysis (Pearson r) between Purchase Frequency and CLV
- **Dashboard:** built with Excel Slicers, a Timeline control, dynamic Pivot Charts, and hidden reference tables

## Key Findings
- Purchase Frequency correlates strongly with CLV (r = 0.80, r² = 0.64) — frequency is the primary driver of long-term customer value
- Average Order Value: €130.08; average basket size: ~5.55–6 items
- Electric Household Essentials and Furniture lead in unit volume (1,591 units each), closely followed by Food (1,588 units)
- Butchers is the top revenue-generating category (€216,480.50)
- Cash transactions have the highest average basket value (€131.50), ahead of Credit Cards (€129.54) and Digital Wallets (€129.12)

## Business Recommendations
- Introduce a free-shipping threshold around €150 to lift the current €130.08 AOV
- Optimize cash-handling checkout workflows, given cash accounts for ~31.6% of transaction volume
- Focus retention/loyalty programs on increasing purchase frequency specifically, since it is the strongest lever on CLV

## Documentation
Detailed methodology, assumptions, and extended commentary are documented on Confluence: [Retail Revenue Optimization & Customer Lifetime Value (CLV) Analysis](https://vagiaxevgeni.atlassian.net/wiki/spaces/~7120209be58429b74d42e6971aac54e6f51aa4/pages/8126465/Retail+Revenue+Optimization+Customer+Lifetime+Value+CLV+Analysis). Note: this link requires access to the Atlassian workspace, so the PDF export below is the version viewable by anyone.

A PDF export of the full documentation is included in this repo at `docs/Retail Revenue Optimization & Customer Lifetime Value (CLV) Analysis-090926.pdf`, so the write-up is readable even without Confluence access.

**Authorship note:** The statistical analysis — data cleaning, KPI design, CLV modeling, and all findings — was performed entirely by the author in Excel. The Confluence documentation was written and finalized with the help of AI tools as an editorial aid (structuring and polishing), based on context, notes, and analytical content provided by the author.

## How to Use
1. Clone or download this repository
2. Open `retail_store_sales.xlsx` in Excel (some features, like Slicers and Timelines, require Excel — compatibility with Google Sheets/LibreOffice may be limited)
3. Start with the `Interactive Dashboard` tab to explore KPIs by region, category, and payment method; see `Data Insights` for the underlying statistics

## License
This repository contains two distinct licenses:

- **Your original work** — the analysis, KPI/CLV modeling, dashboard design, and written commentary — is licensed under the [MIT License](LICENSE.txt) — see the LICENSE file for details.
- **The dataset** (including any cleaned/derived version of it included in this repo) remains under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), per the original Kaggle license. It must be attributed and, if shared or adapted, kept under the same license.

## Acknowledgments
Dataset: "[Retail Store Sales: Dirty for Data Cleaning](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)" by Ahmed Mohamed, via Kaggle, licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
