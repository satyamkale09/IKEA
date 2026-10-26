# 📊 IKEA Gifting: Customer Analytics & RFM Segmentation

An end-to-end data analytics project transforming 1M+ retail transactions into actionable business insights using **SQL Server, Python, and Power BI**.

> **Disclaimer:** IKEA Gifting is a fictional brand created for this educational portfolio project. It is not affiliated with the real IKEA corporation. All findings are based on the public Online Retail II dataset.

## 🎯 Project Overview

This project simulates a real-world analytics engagement for a fictional UK-based gifting and home décor e-commerce business. The objective is to identify valuable customers, analyze churn risk, and understand revenue trends through customer segmentation and an interactive Power BI dashboard.

## 🛠️ Tech Stack

- **SQL Server / SSMS:** Data cleaning, deduplication, and exploration
- **Python & Pandas:** RFM analysis and customer segmentation
- **Jupyter Notebook:** Data analysis
- **Power BI & DAX:** Interactive dashboards and business KPIs

## 📂 Data Source

**Dataset:** [Online Retail II — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii)

- **Records:** 1,067,371 raw transactions
- **Period:** December 2009 – December 2011
- **License:** CC BY 4.0

## ✨ Key Features

- Data cleaning and validation using SQL Server.
- RFM scoring based on Recency, Frequency, and Monetary value.
- Six customer segments: Champions, Loyal, At Risk, New, Needs Attention, and Lost.
- Churn flagging using a 90-day inactivity threshold.
- Three-page Power BI dashboard with KPIs, segment analysis, trends, and interactive filters.

## 📈 Key Findings

- 🏆 **Revenue Concentration:** Champions represent approximately 22% of customers and contribute close to 68% of revenue.
- ⚠️ **Churn Rate:** 50.86%, based on the project's 90-day inactivity definition.
- 💰 **Customer Value:** Significant differences in average customer value across segments.
- 📅 **Seasonality:** Revenue peaks are observed during Q4.

*These findings relate to the analyzed dataset and do not represent IKEA's actual business performance.*

## 🔄 Project Workflow

1. **Business Requirements:** Defined business questions and KPIs.
2. **SQL Server:** Cleaned, deduplicated, and validated transaction data.
3. **Python:** Calculated RFM scores, assigned segments, and flagged potential churn.
4. **Power BI:** Built an interactive dashboard for business performance and customer analysis.

## 💻 Code Highlights

### SQL Server — Handling Mixed Date Formats

```sql
SELECT
    Invoice,
    StockCode,
    Description,
    Quantity,
    COALESCE(
        TRY_CONVERT(datetime2, InvoiceDate, 120),
        TRY_CONVERT(datetime2, InvoiceDate, 105)
    ) AS InvoiceDate,
    TRY_CONVERT(decimal(10, 2), Price) AS Price,
    Customer_ID,
    Country
INTO dbo.RetailCombined
FROM dbo.[Year 2009-2010];
```

### Python — RFM Scoring

```python
import pandas as pd

rfm["R_Score"] = pd.qcut(
    rfm["Recency"],
    5,
    labels=[5, 4, 3, 2, 1]
).astype(int)

rfm["F_Score"] = pd.qcut(
    rfm["Frequency"].rank(method="first"),
    5,
    labels=[1, 2, 3, 4, 5]
).astype(int)

rfm["M_Score"] = pd.qcut(
    rfm["Monetary"],
    5,
    labels=[1, 2, 3, 4, 5]
).astype(int)
```

## 📊 Dashboard Preview

Add screenshots of your Power BI report below.

![Business Overview Dashboard](images/business-overview.png)

![RFM Analysis Dashboard](images/rfm-analysis.png)

*Replace these paths with your actual screenshot filenames.*

## 💡 Key Learnings

- Data cleaning and validation using SQL.
- Customer analytics and segmentation using Python.
- Dashboard development and DAX measures in Power BI.
- Converting analytical findings into business recommendations.

## 🤝 Connect With Me

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/satyamkale09)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/satyamkale)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:satyamkale22@gmail.com)

---

*Educational portfolio project. IKEA Gifting is fictional and is not affiliated with the real IKEA corporation. Dataset: Online Retail II, UCI Machine Learning Repository, CC BY 4.0.*
