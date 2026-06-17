# IDX UMA Early Warning System

IDX UMA Early Warning System is a machine learning based dashboard that detects unusual stock price and trading volume movements in Indonesian stocks. This project is inspired by the concept of Unusual Market Activity (UMA) monitoring in the Indonesian capital market.

The system uses historical stock price data, feature engineering, and an unsupervised learning model to identify trading days that look different from normal market behavior.

## Live Demo

Streamlit App: `Coming Soon`

## Project Overview

Unusual Market Activity can appear when a stock experiences unusual movement in price, volume, or volatility. This project aims to build a simple early warning prototype that can help detect unusual stock activity based on historical stock data.

This project does not predict stock manipulation and does not provide investment recommendations. The main purpose of this project is to demonstrate how anomaly detection can be used to identify unusual price and volume patterns in the stock market.

## Main Objective

The main objective of this project is to answer the following question:

> Can we detect unusual stock price and volume movements using historical market data and unsupervised machine learning?

## Key Features

* Collect historical Indonesian stock data using Yahoo Finance
* Process OHLCV data: Open, High, Low, Close, and Volume
* Create anomaly detection features from price and volume movements
* Detect unusual activity using Isolation Forest
* Show anomaly points on an interactive candlestick chart
* Display volume movement and anomaly markers
* Provide simple explanations for why a data point is considered unusual
* Build an interactive dashboard using Streamlit and Plotly

## Tech Stack

* Python
* Pandas
* NumPy
* Scikit-Learn
* Isolation Forest
* Plotly
* Streamlit
* yfinance

## Dataset

The stock data is collected using the `yfinance` library. Indonesian stock tickers are downloaded using the `.JK` suffix.

Example tickers used in this project:

* BBRI.JK
* TLKM.JK
* BMRI.JK
* BBCA.JK
* ANTM.JK
* GOTO.JK
* ADRO.JK
* MDKA.JK
* BRIS.JK
* UNVR.JK

The dataset contains the following main columns:

* Date
* Open
* High
* Low
* Close
* Volume
* Ticker

## Feature Engineering

Several features are created to detect unusual stock movement:

| Feature                | Description                                              |
| ---------------------- | -------------------------------------------------------- |
| Daily Return           | Daily percentage change in closing price                 |
| Volume Change          | Daily percentage change in trading volume                |
| Volume MA 20           | 20-day moving average of volume                          |
| Volume Spike Ratio     | Current volume compared to 20-day average volume         |
| Price Range Percentage | Daily high-low range compared to closing price           |
| Close MA 20            | 20-day moving average of closing price                   |
| Price Gap MA 20        | Distance between closing price and 20-day moving average |
| Rolling Volatility 20  | 20-day rolling volatility of daily return                |
| Return Z-score 20      | How extreme the return is compared to the last 20 days   |
| Volume Z-score 20      | How extreme the volume is compared to the last 20 days   |

## Machine Learning Model

This project uses **Isolation Forest**, an unsupervised machine learning algorithm that is commonly used for anomaly detection.

The model detects data points that are different from the normal pattern based on multiple features, such as daily return, volume spike, price range, volatility, and z-score.

In this project:

* Normal data is labeled as `False`
* Anomaly data is labeled as `True`
* The anomaly score is used to rank how unusual a data point is

## Dashboard Features

The Streamlit dashboard includes:

1. Stock ticker filter
2. Date range filter
3. KPI cards
4. Candlestick chart with anomaly markers
5. Volume chart with anomaly markers
6. Table of detected anomalies
7. Top 10 anomalies across all stocks
8. Explanation of how the system works

## Project Structure

```text
idx-uma-early-warning-system/
│
├── data/
│   ├── idx_stock_price.csv
│   ├── idx_stock_features.csv
│   ├── idx_stock_anomaly_result.csv
│   └── top_anomalies.csv
│
├── src/
│   ├── collect_data.py
│   ├── feature_engineering.py
│   └── anomaly_model.py
│
├── dashboard.py
├── requirements.txt
└── README.md
```

## How to Run This Project

### 1. Clone this repository

```bash
git clone https://github.com/your-username/idx-uma-early-warning-system.git
cd idx-uma-early-warning-system
```

### 2. Create virtual environment

```bash
py -3.12 -m venv venv
```

### 3. Activate virtual environment

For Windows:

```bash
venv\Scripts\activate
```

### 4. Install required libraries

```bash
pip install -r requirements.txt
```

### 5. Collect stock data

```bash
py -3.12 src/collect_data.py
```

This will create:

```text
data/idx_stock_price.csv
```

### 6. Run feature engineering

```bash
py -3.12 src/feature_engineering.py
```

This will create:

```text
data/idx_stock_features.csv
```

### 7. Run anomaly detection model

```bash
py -3.12 src/anomaly_model.py
```

This will create:

```text
data/idx_stock_anomaly_result.csv
data/top_anomalies.csv
```

### 8. Run Streamlit dashboard

```bash
py -3.12 -m streamlit run dashboard.py
```

After running the command, the dashboard will open in the browser.

## Example Output

The system can identify anomaly points and generate a simple reason, such as:

```text
Volume 4.2x higher than the 20-day average volume
Daily return moved 7.50%
Return z-score reached 2.85
```

This explanation helps users understand which factors caused a stock movement to be considered unusual.

## Disclaimer

This project is only an educational and portfolio project. It is not an official IDX system, not an investment recommendation, and not a tool to prove market manipulation.

The anomaly detection result only shows unusual price and volume patterns based on historical data. Further analysis is needed before making any financial or regulatory conclusion.

## Future Improvements

Some improvements that can be added in the future:

* Add official UMA announcement data from IDX for validation
* Compare anomaly detection results with official UMA announcement dates
* Add more Indonesian stocks
* Add sector-based filtering
* Add anomaly ranking for all stocks
* Add model evaluation using historical UMA events
* Add automatic daily data update

## Author

**Ariq Marwan Permana**

This project was created as an AI Engineer portfolio project to demonstrate skills in data collection, feature engineering, anomaly detection, machine learning, and dashboard development using Python and Streamlit.
