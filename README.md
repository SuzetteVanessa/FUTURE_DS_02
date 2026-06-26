# FUTURE_DS_02

Business Questions Answered:


What is the overall churn rate and how does it compare to retention?

Which customer segments churn the most?

How does tenure affect the likelihood of churn?

What contract types and payment methods correlate with higher churn?

How much monthly revenue is being lost to churn?

What actions can the business take to reduce churn?



Dashboard Structure:

The report is organized across four pages:

Executive Summary - High-level KPIs — churn rate, retention rate, avg tenure, avg monthly charges

Churn Deep Dive - Churn breakdown by contract type, internet service, payment method, demographics

Cohort & Lifetime AnalysisChurn and revenue patterns by tenure band and contract type

RecommendationsKey findings, high-risk segments, and strategic retention actions


Tools & Techniques:


Power BI Desktop — end-to-end analysis and dashboard

Power Query (M) — data cleaning and transformation

DAX — calculated columns and measures

Data Modeling — single-table model with a generated Date Table



Key DAX Measures:

daxTotal Customers = COUNTROWS('Telco Customer')

Churned Customers = 
CALCULATE(COUNTROWS('Telco Customer'), 'Telco Customer'[Churn] = "Yes")

Churn Rate = DIVIDE([Churned Customers], [Total Customers], 0)

Retention Rate = 1 - [Churn Rate]

Churned Revenue Lost = 
CALCULATE(SUM('Telco Customer'[MonthlyCharges]), 'Telco Customer'[Churn] = "Yes")


Data Cleaning Steps:


Loaded raw CSV into Power BI via Power Query

Replaced blank spaces in TotalCharges with 0 before converting to Decimal

Verified data types across all 21 columns

Removed duplicate customerID entries

Created Tenure Band calculated column in DAX using SWITCH logic



Key Findings:


Overall churn rate sits at approximately 26%

Month-to-month contract holders churn at the highest rate

Customers in the 0–12 month tenure band are most at risk

Fiber optic internet subscribers churn more than DSL users

Senior citizens and customers without partners or dependents show elevated churn

Electronic check payment method correlates with the highest churn rate



Dataset:

Telco Customer Churn Dataset — IBM Sample Dataset via Kaggle

7,043 customer records | 21 features | Binary churn label

View on Kaggle
