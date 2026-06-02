# Telecom Customer Churn Analysis — Power BI Dashboard

## Overview
An interactive business intelligence dashboard built in Power BI, 
using a real-world IBM Telco dataset (7,000+ customers) to analyse 
customer churn in the telecommunications industry.

The dashboard visualises relationships between contract type, internet 
service, monthly charges, customer tenure, and churn rate — providing 
actionable insights for customer retention strategy.

Dataset source: [IBM Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

## Dashboard Preview
<img width="1534" height="862" alt="Telecom Customer Churn Dashboard" 
src="https://github.com/user-attachments/assets/7fbedfc5-3c7d-4461-8979-4543f87a8d04" />

## Key Findings
- Month-to-month contracts show ~42% churn rate vs ~11% for annual contracts
- Fiber optic customers churn at a significantly higher rate than DSL users
- New customers (low tenure) are most at risk of churning regardless of price

## Process

### 1. Data Cleaning — Power Query
The raw dataset required cleaning before analysis:
- Removed empty rows in the `TotalCharges` column
- Corrected column type from Text to Decimal Number to enable 
  numerical analysis

### 2. DAX Measure
A custom churn rate measure was written in DAX:

```dax
Churn Rate = 
DIVIDE(
    COUNTROWS(FILTER(
        'WA_Fn-UseC_-Telco-Customer-Churn', 
        'WA_Fn-UseC_-Telco-Customer-Churn'[Churn] = "Yes"
    )),
    COUNTROWS('WA_Fn-UseC_-Telco-Customer-Churn')
) * 100
```

### 3. Dashboard Components

| Component | Description |
| --- | --- |
| KPI Card | Overall churn rate across all customers |
| Column Chart | Churn rate by contract type |
| Column Chart | Churn rate by internet service type |
| Scatter Plot | Monthly charges vs tenure, segmented by churn |
| Slicers | Interactive filters by contract type and internet service |

## Tools Used
- Power BI Desktop
- Power Query
- DAX
