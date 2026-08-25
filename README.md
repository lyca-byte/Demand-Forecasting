# Retail Demand Forecasting

Time-series sales forecasting project using the **Online Retail II** dataset from the UCI Machine Learning Repository.

The project explores historical retail sales patterns, establishes multiple forecasting baselines, builds statistical forecasting models, and compares their performance using time-based evaluation.

---

## Project Overview

Accurate demand forecasting can help retailers make better decisions regarding inventory planning, staffing, and purchasing.

In this project, historical transaction data is transformed into a weekly sales time series. Several forecasting approaches are then developed and compared, including naive baselines, ARIMA, SARIMA, and Prophet.

### Business Problem

> A retailer wants to forecast future sales so it can improve inventory planning, staffing, and purchasing decisions.

### Project Objectives

This project aims to:
- Explore historical retail sales patterns.
- Aggregate sales at daily, weekly, and monthly levels.
- Identify trends, seasonality, outliers, sudden changes, and missing periods.
- Establish simple baseline forecasting methods.
- Build ARIMA, SARIMA, and Prophet forecasting models.
- Use time-based train-test splitting.
- Evaluate forecasting performance using MAE, RMSE, and MAPE.
- Identify the best-performing forecasting approach.
- Generate future sales forecasts.
- Translate forecasting results into potential business recommendations.

---

## Key Results

Six forecasting approaches were evaluated using the same time-based test period.

| Rank | Model | MAE | RMSE | MAPE |
|---:|---|---:|---:|---:|
| 1 | **Prophet** | **39,757.38** | **47,583.78** | **16.75%** |
| 2 | Seasonal Naive (52 weeks) | 53,282.01 | 71,923.75 | 22.01% |
| 3 | SARIMA(1, 1, 1) × (1, 1, 1, 52) | 56,587.19 | 72,176.82 | 23.67% |
| 4 | ARIMA(1, 1, 1) | 84,393.09 | 107,162.58 | 30.04% |
| 5 | 4-week Moving Average | 101,562.49 | 124,378.28 | 36.94% |
| 6 | Previous-period Naive | 115,448.44 | 135,953.52 | 43.28% |

### Best Performing Model

**Prophet** achieved the best overall performance across all three evaluation metrics:

- **MAE:** 39,757.38
- **RMSE:** 47,583.78
- **MAPE:** 16.75%

Compared with the previous-period naive baseline, Prophet reduced:

- MAE by approximately **65.6%**
- RMSE by approximately **65.0%**
- MAPE by approximately **61.3%**

This indicates that the Prophet model was substantially better at capturing the underlying sales patterns in the evaluated test period.

---

## Dataset

This project uses the **Online Retail II** dataset provided by the **UCI Machine Learning Repository**.

The dataset contains transactional records from a UK-based online retailer covering transactions between **2009 and 2011**.

### Dataset Information

| Attribute | Description |
|---|---|
| Dataset | Online Retail II |
| Source | UCI Machine Learning Repository |
| Period | 2009–2011 |
| Data Type | Transactional retail data |
| Domain | Retail / E-Commerce |
| DOI | `10.24432/C5CG6D` |

The dataset contains information such as:

- Invoice number
- Stock code
- Product description
- Quantity
- Invoice date
- Unit price
- Customer ID
- Country

### Dataset Source

[UCI Machine Learning Repository — Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii)

**DOI:** `10.24432/C5CG6D`

> The raw dataset is not included in this repository. Please download it directly from the official UCI repository.

---

## Business Problem

Retail businesses need accurate demand estimates to support operational decision-making.

Poor demand estimation can lead to:

- Overstocking
- Stockouts
- Inefficient purchasing
- Poor staff allocation
- Increased inventory holding costs

This project therefore focuses on forecasting future retail sales from historical transaction data.

The forecasting results can potentially support:

- Inventory planning
- Purchasing decisions
- Staffing decisions
- Demand planning
- Identification of high-demand and low-demand periods

---

## Forecasting Workflow

The overall workflow is:

```text
Online Retail II Dataset
          │
          ▼
   Data Preprocessing
          │
          ▼
    Data Cleaning
          │
          ▼
   Sales Aggregation
   ┌──────┼──────┐
   ▼      ▼      ▼
 Daily   Weekly  Monthly
   │      │      │
   └──────┼──────┘
          ▼
 Time-Series Exploration
          │
          ▼
 Pattern & Anomaly Analysis
          │
          ▼
    Baseline Forecasting
          │
  ┌───────────────┐
  ▼               ▼
ARIMA             SARIMA
  │               │
  └───────┬───────┘
          ▼
       Prophet
          │
          ▼
 Time-Based Evaluation
          │
          ▼
  MAE / RMSE / MAPE
          │ 
          ▼
   Model Comparison
          │
          ▼
Business Interpretation
          │
          ▼
   Future Forecast