# NovaSuite Business Analystics

> End-to-end analytics project using Python (pandas, numpy) across six structured notebooks — from raw data to executive recommendations.

\---

## Overview

NovaSuite is a mid-market B2B SaaS platform serving 500 customers across 8 industries and 8 countries. The company was experiencing slowing revenue growth entering 2024, with Net Revenue Retention (NRR) running at \~98% against a 110% target.

This project builds a full analytical pipeline — data cleaning, EDA, revenue analysis, churn analysis, and pricing strategy — to identify root causes and deliver a data-driven retention and pricing roadmap.

**Date range covered:** January 2021 – June 2024  
**Total records analyzed:** 9,408 customer-month observations

\---

## The Business Problem

|Challenge|Signal in the Data|
|-|-|
|High churn in EdTech|9 of 36 total churns; 15.0% churn rate vs 7.2% baseline|
|Small companies over-provisioned|Small + Pro churns at 11.0% vs 5.2% on Basic|
|Weak expansion revenue|Only 5.5% of total revenue; target is 15%|
|Discount leakage|$154,061 discounted away annually (15.5% of base revenue)|
|Usage decay before churn|Sessions drop \~50% in the 2–3 months before a customer leaves|
|No mid-tier plan option|172% price jump from Basic ($29) to Pro ($79) with nothing in between|

\---

## Dataset

|File|Rows|Description|
|-|-|-|
|`customers.csv`|500|Company profile, industry, size, plan, country, signup date|
|`plans.csv`|4|Subscription tiers: Basic / Pro / Business / Enterprise|
|`revenue.csv`|9,408|Monthly billing: base revenue, discounts, expansion revenue|
|`usage.csv`|9,408|Monthly product activity: sessions, logins, feature scores|
|`churn.csv`|36|Cancelled customers with dates and stated exit reasons|

\---

## Project Structure

```
novasuite/
│
├── NovaSuite_01_Data_Loading_Understanding.ipynb              # Data loading \\\& schema inspection
├── NovaSuite_02_Data_Cleaning_and_Preparation.ipynb      # Null checks, type fixes, referential integrity
├── NovaSuite_03_Exploratory_Data_Analysis.ipynb                # Customer composition, distributions, correlations
├── NovaSuite_04_Revenue_and_Growth_Analysis.ipynb   # MRR trends, ARPA, discount leakage, expansion
├── NovaSuite_05_Churn_Risk_Analysis.ipynb     # Segment churn rates, usage decay, feature adoption
├── NovaSuite_06_Pricing_and_Retention_Strategy.ipynb  # Pricing simulation, at-risk customers, utilization
│
├── NovaSuite_Business_Recommendations_and_Executive_Summary.md        # Executive summary \\\& business recommendations
│
├── customers.csv
├── plans.csv
├── revenue.csv
├── usage.csv
└── churn.csv
```

\---

## Key Findings

### Revenue

* Enterprise + Business plans contribute **63.5% of total revenue** despite fewer customers
* Enterprise LTV is **$5,385** vs **$502** for Basic — a 10× gap
* Expansion revenue sits at **5.5%** of total; target is 15%
* $154k discounted away annually, concentrated in the highest-churn segments

### Churn

* **EdTech churns at 15.0%** — more than double the 7.2% baseline
* **58.3% of exits are budget/price-driven** (Budget Cut + Too Expensive)
* Churned customers had **53% fewer sessions** and **53% fewer logins** than retained customers
* This usage decay is detectable **2–3 months before churn** — an actionable early warning signal

### Usage \& Features

* **Integrations users churn at 3.7%**; Dashboard users at 4.1% — the stickiest features
* **Data Export users churn at 19.2%** — using the platform as a one-time tool, not a workflow hub
* Basic plan seat utilization: only **24%** (avg 1.2 of 5 seats used)

\---

## Recommendations

|#|Recommendation|Priority|Revenue Impact|
|-|-|-|-|
|1|Deploy usage-decline churn alerts (≥40% session drop over 60 days)|**P1 — Immediate**|Medium|
|2|Introduce a usage-based Starter tier ($20 + $8/active user)|**P1 — Immediate**|Medium|
|3|Launch structured QBRs for all 56 Enterprise accounts|**P1 — Immediate**|High|
|4|Phase out broad EdTech discounts; investigate product-market fit|**P2 — 90 Days**|High|
|5|Cap discounts at 10% / 12% / 15% by plan tier|**P2 — 90 Days**|Medium|
|6|Feature adoption campaign for accounts below 3.5 usage score|**P2 — 90 Days**|Low|
|7|Evaluate price increase after feature adoption improves|**P3 — 6–12 Months**|High|



\---

## Tools \& Methods

* **Python** — pandas, numpy only (no scikit-learn, no visualization libraries)
* **Analysis approach** — all findings derived from groupby aggregations, cross-tabulations, and descriptive statistics
* All revenue impacts are **directional estimates** based on observed data patterns, not validated forecasts

\---

## Project Limitations

This project uses a synthetic dataset designed to reflect realistic SaaS dynamics. Key limitations to note:

* No A/B testing or causal validation was performed
* Pricing recommendations lack competitor benchmarks and willingness-to-pay data
* Revenue impact figures are illustrative scenarios, not financial projections
* Usage-churn correlation is observational — a causal model would require survival analysis

These limitations are documented in full in Section 10 of the final notebook.

\---

*Data range: January 2021 – June 2024 | 500 customers | 8 industries | 8 countries*

