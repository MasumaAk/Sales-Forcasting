# Sales Forecasting and Pricing Analysis

Forecasting monthly sales and analyzing pricing patterns using the Sample Superstore dataset.

## What I did

I wanted to see if I could build a short-term sales forecast and also figure out which product categories were losing money through over-discounting.

For the forecasting I used Prophet since it handles seasonality well without needing a lot of configuration. For anomaly detection I used Isolation Forest to flag any months where sales looked unusually high or low.

## Dataset

Sample Superstore dataset — about 9,994 rows of retail order data covering 2014 to 2017. Fields used: Order Date, Sales, Profit, Discount, Quantity, Category, Sub-Category.

The CSV is not included in the repo. Place `Sample - Superstore.csv` in the project folder before running.

## Approach

1. Loaded and cleaned the data — converted date columns, removed duplicates
2. Created new features — profit margin, discount impact, revenue opportunity score
3. Did a category-level summary to see how Furniture, Office Supplies and Technology compare
4. Rolled daily orders up to monthly totals for Prophet
5. Built a Prophet forecast with 6 months forward
6. Evaluated using MAE and RMSE
7. Used Isolation Forest to flag unusual months
8. Looked at which sub-categories have the most pricing opportunity
9. Exported results to CSV for use in Tableau or Power BI

## Results

**Forecast accuracy (in-sample):**
- MAE: $6,179.83
- RMSE: $7,551.10
- Mean monthly sales: $47,858

**Category summary:**

| Category | Total Sales | Profit Margin | Avg Discount |
|---|---|---|---|
| Furniture | $741,999 | 3.9% | 17.4% |
| Office Supplies | $719,047 | 13.8% | 15.7% |
| Technology | $836,154 | 15.6% | 13.2% |

Furniture has the worst margins despite having the highest discount rate — over $123,000 lost to discounting.

**Anomalies flagged:** 5 months — mainly the big end-of-year spikes in late 2016 and 2017, and some very low months in early 2014.

**Top sub-categories by revenue opportunity:** Phones ($281,914), Chairs ($278,634), Storage ($210,646)

## Tools

Python, pandas, numpy, Prophet, scikit-learn, matplotlib

## How to run

1. Put `Sample - Superstore.csv` in the project folder
2. Install: `pip install pandas numpy matplotlib prophet scikit-learn jupyter`
3. Run the notebook top to bottom

## Files

```
Sales-Forcasting/
├── sales_forecasting_pricing_optimization.ipynb
├── README.md
└── .gitignore
```

---
Author: Masuma Akter
