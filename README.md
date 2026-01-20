
# LSTM Stock Price Prediction 📈

TSLA Stock Price Prediction using LSTM neural network. This project uses a Long Short-Term Memory (LSTM) deep learning model to predict the closing price of Tesla (TSLA) stock based on historical market data and technical indicators.

## 📌 Overview

Unlike simple price-based prediction models, this project implements advanced feature engineering by incorporating multiple technical indicators and market correlation data to improve prediction accuracy. The model learns temporal patterns from 60-day historical windows to forecast future closing prices.

**Goal:** Predict future stock closing prices based on the past 60 days of market data.

**Model:** Sequential LSTM with Dropout layers to prevent overfitting.

**Data Source:** Yahoo Finance API (yfinance).

**Time Period:** January 1, 2020 – July 16, 2025.

## 🔍 Feature Engineering

The model doesn't rely solely on historical prices. It incorporates multiple technical indicators and market con  features:

### Market Correlation
- **S&P 500 (^GSPC):** Benchmark index correlation
- **VIX (^VIX):** Volatility Index for market fear gauge

### Momentum Indicators
- **RSI (Relative Strength Index):** Identifies overbought/oversold conditions
- **MACD (Moving Average Convergence Divergence):** Trend momentum indicator

### Volatility Measures
- **ATR (Average True Range):** Price volatility metric
- **21-Day Rolling Volatility:** Standard deviation of returns

### Volume Analysis
- **OBV (On-Balance Volume):** Cumulative volume indicator

### Trend Analysis
- **Price vs. 50-Day SMA:** Trend confirmation
- **Lagged Returns:** Historical momentum for TSLA and S&P 500

## 🏗️ Model Architecture

Built using TensorFlow/Keras with the following structure:

Input Layer (60 timesteps, n features)
↓
LSTM Layer 1 (100 units, return_sequences=True)
↓
Dropout (0.2)
↓
LSTM Layer 2 (100 units)
↓
Dropout (0.2)
↓
Dense Layer (1 unit - Output)


**Training Configuration:**
- **Optimizer:** Adam (Learning rate: 0.0005)
- **Loss Function:** Mean Squared Error (MSE)
- **Batch Size:** 32
- **Epochs:** 100 (with early stopping)
- **Callbacks:** EarlyStopping, ModelCheckpoint

## 📊 Data Preprocessing

1. **Data Collection:** Historical stock data retrieved via `yfinance` API
2. **Feature Calculation:** Technical indicators computed using pandas
3. **Normalization:** MinMaxScaler applied to scale features to [0, 1] range
4. **Sequence Creation:** 60-day sliding windows for temporal pattern learning
5. **Train/Validation Split:** 70% training, 15% validation, 15% test

## 📈 Results & Performance

The model was evaluated on unseen test data (last 15% of the dataset):

| Metric | Value | Interpretation |
|--------|-------|----------------|
| **MAPE** | ~5.21% | Predictions are typically within 5.21% of actual price |
| **RMSE** | ~$21.62 | Root mean squared error in dollars |
| **MAE** | ~$16.40 | Median absolute prediction error |

### Interpretation
- The model successfully captures general price trends and momentum
- Low MAPE (<10%) indicates reasonable prediction accuracy for educational purposes
- The model may struggle with sudden market shifts, news-driven volatility, or black swan events
- Performance is strongest during stable market conditions

## 🛠️ Technologies Used

- **Python 3.x**
- **TensorFlow/Keras** - Deep learning framework for LSTM implementation
- **yfinance** - Yahoo Finance API for stock data retrieval
- **pandas & NumPy** - Data manipulation and numerical operations
- **scikit-learn** - Preprocessing (MinMaxScaler) and evaluation metrics
- **matplotlib** - Visualization of predictions and training curves

## 🚀 Getting Started

### Prerequisites

Install required packages:

``` 
pip install tensorflow yfinance pandas numpy scikit-learn matplotlib
Running the Notebook
Clone the repository:

 
git clone https://github.com/abdulmajeedalageli/LSTM-stock-prediction.git
cd LSTM-stock-prediction
Open the notebook in Jupyter or Google Colab:

 
jupyter notebook LSTM_TSLA.ipynb
Run all cells sequentially:

Data will be automatically downloaded from Yahoo Finance

Model will train and save checkpoints

Predictions vs actual prices will be visualized

Expected Output
Training/validation loss curves

Price prediction vs actual comparison plot

Performance metrics (MAPE, RMSE, MAE)

Saved model file: best_lstm_model_procedural.h5

📂 Project Structure

LSTM-stock-prediction/
│
├── LSTM_TSLA.ipynb          # Main notebook with full pipeline
├── README.md                # Project documentation
├── .gitignore              # Git ignore file
└── best_lstm_model_procedural.h5  # Saved model (generated after training)
⚠️ Important Disclaimers
This is an educational project for learning purposes only:

❌ NOT for actual trading: Stock prediction models should never be used for real investment decisions

❌ Past performance ≠ Future results: Historical patterns may not repeat

❌ Black swan events: The model cannot predict unprecedented market crashes or news events

❌ Regulatory risk: Stock markets are influenced by policies, regulations, and geopolitical factors not captured in technical data

For educational exploration only. Consult a licensed financial advisor for investment decisions.



📝 Key Learnings
LSTM networks are effective for capturing temporal dependencies in time series data

Feature engineering significantly improves model performance over raw price data

Dropout regularization is critical for preventing overfitting in financial data

Proper train/validation/test splits are essential for realistic performance evaluation

Stock prediction is inherently challenging due to market randomness and external factors

📄 License
This project is open source and available for educational purposes.



Note: This is a learning project demonstrating LSTM capabilities for time series forecasting. The techniques shown can be applied to other sequential prediction problems like weather forecasting, energy consumption prediction, or sensor data analysis.
