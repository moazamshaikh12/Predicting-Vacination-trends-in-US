# COVID-19 Vaccination Trend Prediction Pipeline

## 📋 Project Overview
A lightweight, production-ready machine learning pipeline for predicting 7-day average COVID-19 vaccination trends in the United States. This project demonstrates advanced time series forecasting with focus on reproducibility, explainability, and performance.

## 🎯 Business Problem
Predict future vaccination trends to support:
- Healthcare resource planning and allocation
- Vaccine supply chain optimization
- Public health policy decisions
- Early detection of vaccination rate changes

## 📊 Model Performance
- **R² Score**: 0.877 (Excellent)
- **MAE**: 25,273 vaccinations per day
- **RMSE**: 36,298 vaccinations
- **Directional Accuracy**: 62.5%
- **Error Rate**: 15.8% of total vaccinations

## 🏗️ Pipeline Architecture

### Data Processing
- **Source**: Our World in Data COVID-19 Vaccination Dataset
- **Cleaning**: Advanced missing value imputation using forward/backward fill
- **Feature Engineering**: 39+ temporal features including lags, rolling statistics, and seasonal patterns
- **Stationarity**: Achieved through differencing (ADF p-value: 0.000008)

### Feature Engineering
| Feature Category | Examples | Purpose |
|------------------|----------|---------|
| Temporal | day_of_week, month, is_weekend | Capture seasonality |
| Lag Features | lag_7, lag_30 | Historical patterns |
| Trend Indicators | 7-day MA, 30-day MA | Short/long-term trends |
| Volatility | rolling_std_7 | Measure variability |
| Coverage Metrics | fully_vaccinated_ratio | Population saturation |

### Model Selection
Tested 7 algorithms with specialized time series configurations:

| Model | R² Score | Key Insight |
|-------|----------|-------------|
| Lasso Regression | 0.877 | **Selected - Best performance** |
| Ridge Regression | 0.828 | Good alternative |
| Ensemble | 0.838 | Combines multiple models |
| Linear Regression | 0.795 | Baseline performance |
| Tree-based models | Negative R² | Unsuitable for this time series |

## 🔍 Model Explainability

### Key Drivers of Vaccination Trends
1. **Recent Momentum (EMA_7)**: Strongest positive predictor
2. **Short-term Trends (MA_7)**: Complex relationship with EMA
3. **Long-term Trends (MA_30)**: Negative correlation (saturation effect)
4. **Coverage Ratio**: Higher vaccination rates predict slowdown
5. **Weekly Trends**: Positive momentum continues

### Business Insights
- **Momentum Matters**: Recent vaccination rates strongly influence future trends
- **Saturation Effect**: High vaccination coverage naturally reduces daily rates
- **Trend Persistence**: Rising trends tend to continue in short term
- **Seasonal Patterns**: Weekly and monthly patterns impact vaccination rates

## 🚀 Quick Start

### Installation
```bash
pip install pandas numpy scikit-learn matplotlib seaborn xgboost lightgbm shap joblib
