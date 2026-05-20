# walmart-department-recommender
A machine learning model that predicts weekly sales per department and recommends optimal product placement for Walmart stores based on store type, seasonality, and economic conditions. This ML model uses Random Forest.

# Walmart Department Recommender

A machine learning model that predicts weekly sales per department and recommends the optimal department placement for a product given store conditions, seasonality, and economic factors.

## Overview

Given a store, time of year, and economic conditions, the model ranks all 81 Walmart departments by predicted weekly sales and returns the top 5. This helps identify which departments drive the most revenue under specific conditions — for example, which departments perform best during Christmas week vs. a regular January week.

## Dataset

The project uses the [Walmart Store Sales Forecasting dataset](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting):

| File | Description |
|------|-------------|
| `train.csv` | 421,570 rows of weekly sales by store and department |
| `features.csv` | Economic data per store/week (temperature, fuel price, CPI, unemployment, markdowns) |
| `stores.csv` | Store type (A/B/C) and size |

## Project Structure

```
walmart-department-recommender/
├── data/
│   ├── raw/               # Original dataset files
│   └── processed/         # Cleaned and merged data
├── notebooks/
│   ├── exploration.ipynb  # Data cleaning and preprocessing
│   └── model.ipynb        # Model training, evaluation, and recommendations
├── models/
│   └── random_forest.pkl  # Saved trained model
├── img/
│   ├── feature_importance.png
│   ├── jan_vs_xmas.png
│   └── holiday_vs_nonholiday.png
└── README.md
```

## Model

- **Algorithm:** Random Forest Regressor (100 trees)
- **Target:** Weekly Sales ($)
- **Evaluation:** Mean Absolute Error = $1,445
- **Train/Test Split:** 80/20

## Key Findings

- **Department**, **Size**, and **Store** were the most important features, meaning location matters more than economic conditions
- Holiday weeks shift, which departments perform best? — Department 7 (electronics) jumps into the top 5 during Christmas but doesn't appear in January
- Holiday weeks average $17,427 in sales vs. $15,984 for non-holiday weeks

## Sample Output

```
Rank   Department   Predicted Sales
-----------------------------------
1      Dept 92      $149,285.19
2      Dept 7       $145,847.53
3      Dept 95      $111,601.48
4      Dept 72      $109,729.51
5      Dept 90      $93,020.30
```

## How to Run

1. Install dependencies:
   ```
   pip install pandas scikit-learn matplotlib seaborn joblib
   ```
2. Run `notebooks/exploration.ipynb` to preprocess the data
3. Run `notebooks/model.ipynb` to load the model and generate recommendations

## Technologies

Python, pandas, scikit-learn, matplotlib, seaborn, joblib
