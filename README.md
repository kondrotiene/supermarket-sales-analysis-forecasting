# Supermarket Sales Analysis & Forecasting

> **Portfolio project** | Python · Data Analysis · Machine Learning · Time Series

A complete end-to-end data analysis project covering exploratory data analysis (EDA), statistical hypothesis testing, linear regression modelling, and time series forecasting on a real-world supermarket sales dataset.

## Project Overview

This project analyses **1,000 supermarket transactions** across three branches (Cairo, Alex, Giza) to uncover what drives sales and forecast future revenue.

**Key questions answered:**
- Which factors have the strongest impact on sales?
- Do branches, product lines, or payment methods differ significantly?
- Can we reliably forecast daily sales one week ahead?


## Repository Structure

```
supermarket-sales/
│
├── data/
│   └── SuperMarketAnalysis.csv       # Raw dataset (from Kaggle)
│
├── Project_Supermarket_Sales_Eng.ipynb  # Main analysis notebook
│
├── requirements.txt                  # Python dependencies
├── README.md                         # This file
└── .gitignore                        # Files to exclude from Git
```

## Analysis Pipeline

### 1. Data Understanding & Preparation
- Shape, dtypes, missing values check
- Datetime conversion, duplicate removal
- Custom function for unique value exploration

### 2. Exploratory Data Analysis (EDA)
- Distribution analysis: `Sales`, `Gross Income`, `Unit Price`, `Quantity`, `Rating`
- Group comparisons: Branch, Product Line, Gender, Payment method
- Correlation heatmap identifying key predictors

### 3. Statistical Testing
| Test | Question | Result |
|------|----------|--------|
| Chi-square | Health&Beauty vs Fashion: equal demand? | No significant difference (p > 0.05) |
| ANOVA | Are Sales equal across all Branches? | No significant difference (p > 0.05) |
| t-test + Cohen's d | Unit price: Health&Beauty vs Fashion? | Included with effect size |

### 4. Linear Regression (OLS)
- **Full model**: 7 features (including dummies) → R² = 0.887
- **Simplified model**: Unit Price + Quantity only → R² = 0.904
- Residuals analysis, Q-Q plot, Actual vs Predicted visualisation

### 5. Time Series Forecasting
- Daily sales aggregation and visualisation
- ADF stationarity test (Augmented Dickey-Fuller)
- Seasonal decomposition (trend + seasonality + residuals)
- Day-of-week sales pattern analysis
- Models compared:
  - 7-day Rolling Average (baseline)
  - Holt-Winters Exponential Smoothing
  - SARIMA(1,1,1)(1,1,1)[7]
- Backtest with MAE, RMSE, MAPE on held-out last 7 days

## Key Results

| Metric | Value |
|--------|-------|
| Best model R² (test) | 0.904 |
| MAE (regression) | 58.54 $ |
| RMSE (regression) | 78.92 $ |
| Time series MAPE | ~35% (typical for daily retail data) |
| Top sales driver | Quantity (each +1 unit adds ~58$) |
| Strongest weekly peak | Identified via day-of-week analysis |

## Business Insights

- **Quantity is the primary revenue driver** — bundle promotions (Buy 3, get discount) have the highest projected ROI.
- **All three branches perform equally** — no branch-specific strategy needed; focus on product mix instead.
- **Health & Beauty underperforms in volume** but has one of the highest average basket sizes — a marketing opportunity.
- **Strong weekly seasonality** detected — staffing and promotions should align with peak day(s).


## Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas` | Data manipulation |
| `numpy` | Numerical operations |
| `matplotlib` / `seaborn` | Visualisation |
| `scipy` | Statistical tests |
| `statsmodels` | OLS regression, SARIMA, decomposition |
| `scikit-learn` | Train/test split, metrics |



## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/supermarket-sales.git
cd supermarket-sales
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Dataset: [Supermarket Sales – Kaggle](https://www.kaggle.com/datasets/faresashraf1001/supermarket-sales)  
Place the CSV file in the `data/` folder as `SuperMarketAnalysis.csv`.

### 4. Run the notebook
```bash
jupyter notebook Project_Supermarket_Sales_Eng.ipynb
```

## Dataset

**Source:** [Kaggle – Supermarket Sales](https://www.kaggle.com/datasets/faresashraf1001/supermarket-sales)  
**Size:** 1,000 rows × 17 columns  
**Period:** January – March 2019  
**Features:** Branch, City, Customer type, Gender, Product line, Unit price, Quantity, Sales, Gross income, Rating, Payment, Date, Time

> The raw CSV is **not included** in this repository due to Kaggle's terms of service. Please download it directly from the link above.

## Contact

Feel free to connect or leave feedback:

- **GitHub:** [github.com/YOUR_USERNAME](https://github.com/kondrotiene)
- **LinkedIn:** [[linkedin.com/in/YOUR_PROFILE](https://linkedin.com/in/YOUR_PROFILE)](https://www.linkedin.com/in/ingrida-kondrotiene/)


*This project was completed as a data analytics capstone. All analysis, interpretations, and visualisations are original work.*
