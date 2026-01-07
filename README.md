# customer-churn-revenue-risk-analysis.
 customer churn &amp; revenue risk using Python, SQL, and actionable business insights.
 ## Analysis Summary

This project aims to analyze customer churn in a telecommunications company to identify high-risk segments, quantify revenue loss, and provide actionable retention recommendations. The analysis uses the Telco Customer Churn Dataset, which includes demographic, subscription, billing, and churn information.

**Key Steps Performed:**
- **Data Loading and Initial Inspection**: The `WA_Fn-UseC_-Telco-Customer-Churn.csv` dataset was loaded into a pandas DataFrame.
- **Data Cleaning**: The `TotalCharges` column was converted to a numeric type, and rows with missing values were dropped.
- **Key Business Metrics**: Calculated churn rate (26.58%) and revenue at risk from churned customers ($139,130.85).
- **Churn Analysis by Contract Type**: Revealed that month-to-month contracts have a significantly higher churn rate (42.71%) compared to one-year (11.28%) and two-year (2.85%) contracts.
- **SQL-Based Analysis**: Demonstrated how to perform similar analyses using SQL by creating an SQLite database from the DataFrame.

**Main Insights:**
- Month-to-month contracts are a major vulnerability for customer churn.
- Longer-term contracts are highly effective in retaining customers.
- Churned customers represent a substantial financial loss.

**Recommendations:**
- Encourage migration from month-to-month to annual contracts.
- Implement targeted retention campaigns for high-risk, high-revenue customer segments.
- Enhance customer loyalty through service bundling.
- Proactively engage with customers before contract renewals.
