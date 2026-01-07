# LSTM-stock-prediction
TSLA Stock Price Prediction using LSTM 📈
This project uses a Long Short-Term Memory (LSTM) neural network to predict the closing price of Tesla (TSLA) stock. It utilizes historical data from Yahoo Finance and implements advanced feature engineering to improve model accuracy.

Project Overview

Goal: Predict future stock closing prices based on the past 60 days of market data.

Model: Sequential LSTM with Dropout layers to prevent overfitting.

Data Source: Yahoo Finance (yfinance).

Time Period: Jan 1, 2020 – July 16, 2025.

Feature Engineering

Unlike simple price-based models, this project incorporates technical indicators and market context:

Market Correlation: S&P 500 (^GSPC) and Volatility Index (^VIX).

Momentum: Relative Strength Index (RSI), MACD.

Volatility: Average True Range (ATR), 21-day Rolling Volatility.

Volume: On-Balance Volume (OBV).

Trend: Price vs. 50-day SMA.

Lag Features: Lagged returns for TSLA and S&P 500.

Model Architecture

The model is built using TensorFlow/Keras:

LSTM Layer 1: 100 units (return sequences=True).

Dropout: 0.2 (to reduce overfitting).

LSTM Layer 2: 100 units.

Dropout: 0.2.

Dense Layer: Output unit (Prediction).

Optimizer: Adam (Learning rate: 0.0005).

Loss Function: Mean Squared Error (MSE).

 Results
 
The model was evaluated on unseen test data.

MAPE (Mean Absolute Percentage Error): ~5.21%

RMSE (Root Mean Squared Error): ~$21.62

MAE (Mean Absolute Error): ~$16.40
