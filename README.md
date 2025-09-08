# 📈 Stock Price Prediction (TCS & Infosys)

This project explores **time series forecasting** of stock prices for two leading IT companies in India — **TCS** and **Infosys**.  
The objective is to build and compare traditional statistical models (**ARIMA, ARIMAX**) with a deep learning model (**LSTM**) to evaluate forecasting accuracy.

---

## 📌 Background and Objective

- Stock market forecasting is challenging due to volatility, seasonality, and external influences.  
- The aim of this project is to predict **closing prices** of TCS and Infosys stocks and compare model performance.  
- Models applied: **ARIMA, ARIMAX, LSTM**.  
- Evaluation based on: **MAE, MSE, RMSE**.

---

## 🗂 Project Structure

The project is organized into step-by-step Jupyter notebooks:

1. **`1_Data_Preprocessing.ipynb`**  
   - Dropped unnecessary columns (`Trades`).  
   - Handled missing values in `Deliverable Volume` and `% Deliverable` (using `ffill`/`bfill`).  
   - Converted `Date` to datetime, set as index, sorted by date.  
   - Visualized TCS vs Infosys closing prices.  

2. **`2_Stationarity_checks.ipynb`**  
   - Performed **ADF Test** for stationarity.  
   - Differencing applied where necessary (`d=1` for TCS, Infosys already stationary).  
   - Generated **ACF** and **PACF** plots to guide ARIMA/ARIMAX parameter selection.  

3. **`3_ARIMA_Model.ipynb`**  
   - Built univariate ARIMA models using `Close` price only.  
   - Trained on 80% data, tested on 20%.  

4. **`4_ARIMAX_Model.ipynb`**  
   - Extended ARIMA by including `Open` price as **exogenous variable**.  
   - Trained on 80% data, tested on 20%.  

5. **`5_LSTM_Model.ipynb`**  
   - Implemented LSTM (Long Short-Term Memory) neural network.  
   - Normalized stock prices, reshaped into 3D sequences.  
   - Captured sequential dependencies for improved forecasting.  

6. **`Final_Stock_Price_Prediction_Project.ipynb`**  
   - Combined pipeline with preprocessing → stationarity checks → ARIMA → ARIMAX → LSTM → evaluation.

---

## ⚙️ Models Implemented

- **ARIMA**: Autoregressive Integrated Moving Average, univariate on `Close`.  
- **ARIMAX**: ARIMA with `Open` as exogenous variable.  
- **LSTM**: Deep learning model for sequence prediction, capturing temporal dependencies.  

---

## 📊 Evaluation Metrics

All models were evaluated using:

- **MAE**: Mean Absolute Error  
- **MSE**: Mean Squared Error  
- **RMSE**: Root Mean Squared Error  

These metrics quantify prediction errors and help compare statistical vs deep learning approaches.

---

## 📈 Results

| Model   | MAE     | MSE       | RMSE    |
|---------|---------|-----------|---------|
| ARIMA   | 25.4    | 980.2     | 31.3    |
| ARIMAX  | 22.8    | 910.6     | 30.1    |
| LSTM    | 15.6    | 620.4     | 24.9    |

- **LSTM** outperformed ARIMA and ARIMAX in terms of forecasting accuracy.  
- **ARIMAX** showed improvement over ARIMA by including `Open` as an exogenous variable.  
- Visual comparisons of predicted vs actual prices confirmed that **LSTM captured trends more effectively**.  

> 📌 *Note: The metrics above are based on the test dataset split (20% of the data). Values may vary if retrained.*

---

## 🛠 Tech Stack

- **Programming Language:** Python  
- **Libraries:** pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn, tensorflow/keras  
- **Models:** ARIMA, ARIMAX, LSTM  
- **Tools:** Jupyter Notebook, Google Colab, GitHub  

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/RameshKelavath/StockPricePrediction.git
   cd StockPricePrediction
