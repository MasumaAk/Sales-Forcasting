# Sales Forecasting & Pricing Optimization

Forecasting future sales and surfacing pricing optimization opportunities using time-series modeling and anomaly detection on retail order data.

## Overview

Retailers need to know not just what happened, but what's likely to happen next — and where pricing or discounting is quietly eating into profit. This project builds a sales forecasting pipeline and layers on pricing diagnostics (margin, discount impact, revenue opportunity) to turn raw order data into decisions a business can act on.

## Dataset

- **Source:** Sample Superstore dataset (order-level retail transactions)
- **Fields used:** Order Date, Ship Date, Sales, Profit, Discount, Quantity, Category

## Approach

1. **Data cleaning** — parsed order/ship dates to datetime, handled missing values
2. **Feature engineering**
   - Time features: year, month, quarter
   - Pricing features: profit margin, discount impact
   - Customer behavior: order value
3. **Business analysis** — category-level sales/profit/margin summaries, monthly sales aggregation
4. **Sales forecasting** — built a **Prophet** time-series model on monthly sales, generating a 6-month forward forecast with trend and seasonality components
5. **Model evaluation** — assessed forecast accuracy using **MAE** and **RMSE** against actuals
6. **Anomaly detection** — applied **Isolation Forest** to monthly sales to flag unusual spikes or drops
7. **Pricing optimization insights**
   - Identified low-margin categories (profit margin < 10%)
   - Quantified revenue lost to high discounting by category
   - Calculated a revenue opportunity score (`Sales × (1 − Discount)`) to rank products by untapped potential
8. **Export for BI tools** — saved forecast results, anomaly flags, category analysis, and cleaned data to CSV for use in Tableau/Power BI dashboards

## Results

- Produced a 6-month sales forecast with trend/seasonality decomposition, evaluated against held-out actuals using MAE and RMSE
- Flagged anomalous months in the sales trend using Isolation Forest, useful for catching demand shocks or data issues early
- Surfaced specific product categories with thin profit margins and high discount-driven revenue loss
- Built a Revenue Opportunity Score to prioritize which products/categories deserve pricing attention

## Tools

Python · pandas · NumPy · Prophet · scikit-learn (Isolation Forest, MAE/RMSE) · matplotlib

## Repo Structure

```
sales-forecasting-pricing/
├── sales_forecasting_pricing_optimization.ipynb   # Full analysis notebook
├── README.md
└── .gitignore
```

## How to Run

1. Place the Superstore CSV in the project root (update the file path in the notebook if needed)
2. Install dependencies: `pip install pandas numpy matplotlib prophet scikit-learn jupyter`
3. Open and run `sales_forecasting_pricing_optimization.ipynb`

---
*Author: Masuma Akter*
