# Stock Price Prediction

Forecasting daily **Close** prices for **TCS** and **Infosys** using classical time-series models (ARIMA, ARIMAX) and a deep-learning model (LSTM).  
The project compares statistical vs deep learning methods for forecasting accuracy.

---

## Introduction

The goal of this project is to **build, compare, and evaluate** three forecasting approaches:

- **ARIMA** – univariate forecasting using only the Close price.  
- **ARIMAX** – ARIMA with an **exogenous** driver (**Open** price).  
- **LSTM** – a neural network that models non-linear temporal dependencies.

All models are evaluated with **MAE**, **MSE**, and **RMSE** on a held-out test split.

---

## Repository Structure

1_Data_Preprocessing.ipynb
2_Stationarity_checks.ipynb
3_ARIMA_Model.ipynb
4_ARIMAX_Model.ipynb
5_LSTM_Model.ipynb
Final_Stock_Price_Prediction_Project.ipynb     # end-to-end notebook
INFY.csv
TCS.csv
README.md
LICENSE


---

##  Data Preparation (`1_Data_Preprocessing.ipynb`)

- Dropped unused column **`Trades`**.
- Filled missing values in **`Deliverable Volume`** and **`% Deliverable`** using `ffill` / `bfill`.
- Parsed **`Date`** to `datetime`, set it as **index**, and sorted chronologically.
- Plotted TCS vs Infosys closing prices over time.

---

## Stationarity & Diagnostics (`2_Stationarity_checks.ipynb`)

- Performed **ADF (Augmented Dickey–Fuller)** tests.  
  - **TCS**: non-stationary → stationary after **first differencing** (`d=1`).  
  - **Infosys**: already stationary without differencing.
- Used **ACF/PACF** plots to guide choices of **(p, d, q)**.

---

## Models Implemented

### 1) ARIMA (`3_ARIMA_Model.ipynb`)
- Univariate model on **Close** only.  
- Train/test split: **80% / 20%**.  
- Forecasted Close price for the test set.

### 2) ARIMAX (`4_ARIMAX_Model.ipynb`)
- ARIMA with **Open** price as an **exogenous** variable.  
- Same split protocol; target is Close price.

### 3) LSTM (`5_LSTM_Model.ipynb`)
- Data normalized & reshaped into 3D sequences.  
- Sequence-to-one prediction of Close prices.

---

## Evaluation Metrics

- **MAE** – Mean Absolute Error  
- **MSE** – Mean Squared Error  
- **RMSE** – Root Mean Squared Error  

---

## Results

| Model  | Company |   MAE   |     MSE     |  RMSE  |
|--------|---------|---------|-------------|--------|
| ARIMA  | TCS     | 496.37  | 285756.22   | 534.56 |
| ARIMA  | Infosys | 396.71  | 231179.31   | 480.81 |
| ARIMAX | TCS     | 28.78   | 1465.50     | 38.28  |
| ARIMAX | Infosys | 9.91    | 191.06      | 13.82  |
| LSTM   | TCS     | 54.68   | 13201.82    | 114.90 |
| LSTM   | Infosys | 30.54   | 1780.10     | 42.19  |

**Insights:**
- **ARIMAX** significantly outperforms both ARIMA and LSTM, thanks to including **Open** as an exogenous variable.  
- **LSTM** performs better than ARIMA, capturing non-linear dependencies.  
- **ARIMA** (Close only) has the **highest errors**, showing its limitations on volatile stock data.  

---

## Conclusion

This project compared **ARIMA**, **ARIMAX**, and **LSTM** models for predicting stock prices of **TCS** and **Infosys**.  

- **ARIMAX performed the best**, as the inclusion of the **Open** price improved accuracy.  
- **LSTM** performed better than **ARIMA**, leveraging deep learning for non-linear patterns, but still fell short of ARIMAX.  
- **ARIMA** had the **highest errors**, making it less effective for volatile data.  

---

## How to Run

1. Clone the repo  
   ```bash
   git clone https://github.com/RameshKelavath/StockPricePrediction.git
   cd StockPricePrediction
