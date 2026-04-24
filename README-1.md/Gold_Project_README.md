
# Gold Direction Prediction Using Ensemble Machine Learning

**Author:** Adrian King

---

## Overview

This project builds a machine learning pipeline to predict the **next-day direction of gold prices** (up or down). Using historical price data, I engineered technical indicators and applied multiple machine learning models, combining them through ensemble techniques to improve predictive performance. The project was later expanded to include **transformer-based sentiment analysis** and a **dense neural network** to test whether unstructured text data could improve forecasting results. :contentReference[oaicite:0]{index=0}

---

## Objective

The goal is to determine whether machine learning models, particularly ensemble methods, can extract predictive signals from technical indicators and outperform simple baseline strategies. A secondary objective was to test whether sentiment features derived from gold-related news text could enhance model performance.

---

## Data

- Dataset: `finalgolddata.csv`
- Frequency: Daily gold price data
- Core features: Open, High, Low, Close, Volume
- Additional dataset: `artificial_gold_news_text.csv`

---

## Feature Engineering

All features were derived from raw price data and transformer-generated sentiment data.

### Returns & Lag Features

- Daily returns
- Lagged returns (t-1, t-2, t-3, t-5)

### Trend Indicators

- Moving averages (5, 10, 20)
- Price-to-moving-average ratios

### Momentum Indicators

- 3-day, 5-day, 10-day momentum

### Volatility Indicators

- Rolling standard deviation
- High-low price range

### Volume Indicators

- Volume change
- Rolling volume averages

### Sentiment Features

Artificial gold-related headlines were processed using a transformer model:

- `avg_sentiment`
- `bullish_count`
- `bearish_count`
- `neutral_count`
- `headline_count`
- `avg_sentiment_confidence`
- 3-day and 7-day rolling sentiment averages

### Data Cleaning

- Replaced infinite values (`inf`, `-inf`) with NaN
- Imputed missing values with medians
- Scaled numeric features where appropriate

---

## Target Variable

Binary classification:

- **1** → Next day closing price is higher
- **0** → Next day closing price is lower or unchanged

---

## Models

### Baseline

- Logistic Regression

### Tree-Based Models

- Random Forest
- Gradient Boosting
- AdaBoost
- Bagging Classifier

### Ensemble Methods

- Soft Voting Classifier

### Deep Learning Extension

- Transformer Sentiment Model
- Dense Neural Network Classifier

---

## Training Process

- Time-aware train/test split
- Cross-validation using `TimeSeriesSplit`
- Hyperparameter tuning with `GridSearchCV`
- Neural network training with early stopping
- Primary evaluation metric: ROC-AUC

---

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC
- Confusion Matrix

---

## Results & Insights

- Ensemble tree-based models delivered the strongest overall performance
- Random Forest achieved the highest Accuracy and F1-score
- AdaBoost achieved the highest ROC-AUC
- Logistic Regression served as an interpretable baseline
- The dense neural network did not outperform the tree ensembles
- Transformer sentiment integration demonstrated how text data can be converted into predictive features
- Gold direction forecasting remains challenging, with only modest predictive signal detected

---

## Baseline Comparison

Models were compared against simple strategies such as:

- Always predicting “up”
- Predicting the previous day’s direction

The machine learning models modestly outperformed these baselines.

---

## Limitations

- Artificial sentiment data was used instead of live news feeds
- No macroeconomic variables included (rates, CPI, DXY, VIX)
- No live trading strategy or backtesting performed
- Neural network architecture was intentionally simple
- Financial markets are inherently noisy and difficult to predict

---

## Next Steps

- Use real-world financial news sentiment feeds
- Add macroeconomic indicators
- Explore LSTM / sequence models
- Implement walk-forward validation
- Backtest predictions in a trading strategy
- Tune neural network architecture further

---

## Tools

- Python
- pandas
- numpy
- scikit-learn
- TensorFlow / Keras
- Hugging Face Transformers
- matplotlib
- Quarto / Jupyter

---

## Author

Adrian King  
Machine Learning | Finance | Quantitative Modeling  
University of Illinois Chicago
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

