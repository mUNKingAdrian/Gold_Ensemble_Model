# Gold Direction Prediction Using Ensemble Machine Learning

**Author:** Adrian King

------------------------------------------------------------------------

## Overview

This project builds a machine learning pipeline to predict the
**next-day direction of gold prices** (up or down). Using historical
price data, I engineered technical indicators and applied multiple
machine learning models, ultimately combining them through ensemble
techniques to improve predictive performance.

------------------------------------------------------------------------

## Objective

The goal is to determine whether machine learning models---particularly
ensemble methods---can extract predictive signals from technical
indicators and outperform simple baseline strategies.

------------------------------------------------------------------------

## Data

-   Dataset: `finalgolddata.csv`\
-   Frequency: Daily gold price data\
-   Core features: Open, High, Low, Close (and Volume if available)

------------------------------------------------------------------------

## Feature Engineering

All features were derived from raw price data:

### Returns & Lag Features

-   Daily returns\
-   Log returns\
-   Lagged returns (t-1, t-2, t-3)

### Trend Indicators

-   Simple Moving Averages (10, 50, 200)\
-   Exponential Moving Averages\
-   Price-to-moving-average ratios

### Momentum Indicators

-   RSI (14-day)\
-   MACD (line, signal, histogram)

### Volatility Indicators

-   Bollinger Bands\
-   Rolling standard deviation\
-   Average True Range (ATR)

### Data Cleaning

-   Replaced infinite values (`inf`, `-inf`) with NaN\
-   Dropped rows with missing values after feature creation

------------------------------------------------------------------------

## Target Variable

Binary classification:

-   **1** → Next day closing price is higher\
-   **0** → Next day closing price is lower or unchanged

------------------------------------------------------------------------

## Models

### Baseline

-   Logistic Regression (with regularization tuning)

### Tree-Based Models

-   Random Forest\
-   Gradient Boosting\
-   AdaBoost (Decision Tree base estimator)\
-   Bagging Classifier

### Ensemble Methods

-   Voting Classifier (soft voting)\
-   Stacking Classifier

------------------------------------------------------------------------

## Training Process

-   Time-aware train/test split\
-   Cross-validation using `TimeSeriesSplit`\
-   Hyperparameter tuning with `GridSearchCV`\
-   Primary evaluation metric: ROC-AUC

------------------------------------------------------------------------

## Evaluation Metrics

-   Accuracy\
-   Precision\
-   Recall\
-   F1 Score\
-   ROC-AUC\
-   Confusion Matrix

------------------------------------------------------------------------

## Results & Insights

-   Ensemble methods (especially boosting and stacking) produced the
    strongest performance\
-   Tree-based models captured nonlinear relationships better than
    linear models\
-   Logistic Regression served as a useful baseline for
    interpretability\
-   Feature engineering significantly improved model performance

------------------------------------------------------------------------

## Baseline Comparison

Models were compared against: - Always predicting "up"\
- Predicting previous day's direction

All ensemble models outperformed these baselines, indicating the
presence of learnable signal.

------------------------------------------------------------------------

## Limitations

-   Only technical indicators were used\
-   No macroeconomic or sentiment data included\
-   No trading strategy or backtesting performed\
-   Potential overfitting despite time-aware validation

------------------------------------------------------------------------

## Next Steps

-   Add macroeconomic variables (interest rates, dollar index)\
-   Incorporate sentiment analysis (NLP)\
-   Implement walk-forward validation\
-   Backtest model predictions in a trading strategy\
-   Explore deep learning approaches (LSTM)

------------------------------------------------------------------------

## Tools

-   Python (pandas, numpy)\
-   scikit-learn\
-   Quarto

------------------------------------------------------------------------

## Author

Adrian King\
Machine Learning \| Finance \| Quantitative Modeling\
University of Illinois Chicago
