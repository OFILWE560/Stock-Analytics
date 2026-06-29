# Regression Analysis - Stock Open vs Close Price

> Repository: `OFILWE560/Regression-Analysis` *(rename this if your actual repo name differs)*

## Description

This project is **Task 1 of Level 2 (Intermediate)** in the Codveda Technologies data analytics internship. It performs a simple linear regression to predict one variable based on another, using a real-world stock prices dataset.

## Objectives

- Split the dataset into training and testing sets
- Fit a linear regression model using scikit-learn
- Interpret the coefficients and evaluate the model using metrics such as R-squared and mean squared error

## Dataset

A daily OHLCV (open, high, low, close, volume) dataset covering **505 stock symbols from 2014–2017** (497,472 rows). Before modeling, the data was cleaned:

- Parsed `date` into a proper datetime column
- Dropped rows with missing `open`/`high`/`low` values (19 rows)
- Checked for and removed duplicate rows (none found)
- Checked for and removed any non-positive prices (none found)

The cleaned dataset is saved as `cleaned_stock_prices.csv`.

## Approach

The model predicts **closing price** from **opening price** (`close = f(open)`). These two variables correlate at ~0.9999 same-day, making them a clean, interpretable pair for a first regression task and the strength of that relationship is itself a useful finding: stocks rarely move far from their open within a single trading day.

The data was split 80/20 into training and testing sets (`random_state=42` for reproducibility), and a `LinearRegression` model from scikit-learn was fit on the training set.

## Results

| Metric | Value |
|---|---|
| Slope (coefficient) | ≈ 1.00 |
| Intercept | ≈ 0.03 |
| R-squared | ≈ 0.9997 |
| MSE | ≈ 2.73 |
| RMSE | ≈ 1.65 |

A slope near 1 with an intercept near 0 means closing price tracks opening price almost exactly — a $1 move in the open price predicts roughly a $1 move in the close price, with very little drift. An R² above 0.999 confirms open price alone explains almost all the variation in close price.

![Open vs Close regression line](regression_open_vs_close.png)

## Repository Structure

```
Regression-Analysis/
├── 2__Stock_Prices_Data_Set.csv      # raw dataset
├── cleaned_stock_prices.csv          # cleaned dataset (output of the notebook)
├── regression_analysis.ipynb         # notebook: cleaning, modeling, evaluation
├── regression_open_vs_close.png       # regression line visualization
└── README.md
```

## Tools

Python · pandas · scikit-learn · matplotlib

## How to Run

1. Clone the repo and install dependencies:
   ```bash
   pip install pandas scikit-learn matplotlib
   ```
2. Open `regression_analysis.ipynb` in Jupyter Notebook or JupyterLab.
3. Run all cells in order. The cleaned dataset and regression plot will be generated automatically.

## Author

**Ofilwe Gabaitse**
[LinkedIn](https://www.linkedin.com/in/ofilwe-gabaitse/) · [GitHub](https://github.com/OFILWE560) · [Email](mailto:ofilwegabaitse@gmail.com)
