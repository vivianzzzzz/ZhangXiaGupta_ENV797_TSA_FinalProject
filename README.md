# ZhangXiaGupta_ENV797_TSA_FinalProject

Team Members: Ayush Gupta, Haochong Xia, Xiyue Zhang


## Overview
For our final project we worked on Forecasting Bitcoin Returns. We aim to predict the daily returns of Bitcoin using time series analysis and using external regressors such as Crude Oil Prices and impact from the onset of COVID. We used the ARIMA, ETS, TBATS, and Neural Network models to forecast the daily returns of Bitcoin. The data used in this project is the daily Bitcoin price data from 2017-01-01 to 2024-04-08. The evaluation metric we have used is the Root Mean Squared Error (RMSE). The model with the lowest RMSE was considered the best model. The best model will be used to forecast the daily returns of Bitcoin for the next 30 days. 

## Data
The `Data` directory contains two datasets:
- bitcion.csv: Daily Bitcoin price data from 2017-01-01 to 2024-04-08.
- DCOILBRENTEU.csv: Daily Crude Oil price data from 2017-01-01 to 2024-04-08.

## Data Preprocessing
- DCOILBRENTEU.csv don't have price on weekend, so we insert more rows, and change non-numeric data into NA and then fill in with the data right before it, and use the last price on Friday to fill the price on Saturday and Sunday as well. 


## Models
1. Exponential Smoothing (ETS)
Model Type: ETS(A, A, A) allowing for error, trend, and seasonal components.
Seasonal Periods: 365.25 days to reflect annual seasonality.
Model Evaluation: Accuracy is assessed using holdout samples.

2. TBATS
Model Type: TBATS, chosen for its ability to handle multiple levels of seasonality.
Seasonal Periods: quarterly (91.25 days) and annual (365.25 days).
Components: Includes Box-Cox transformation, ARMA error modeling, trend, and seasonal components.

3. ARIMA
Model Type: Seasonal ARIMA with external regressors.
Parameters: Differencing parameters and seasonal orders are selected based on ACF and PACF plots.
Regressors: Fourier terms for seasonality, with daily price of crude oil and a dummy variable of covid as external regressors. We identifiy the covid period using the news from yalemedicine.org.

4. Neural Network (NN)
Model Type: NNETAR, a type of recurrent neural network suited for time series data.
Parameters: Configured with P=1 (lagged terms considered) and seasonal periods.
Regressors: Fourier terms for seasonality, with daily price of crude oil and a dummy variable of covid as external regressors. We identifiy the covid period using the news from yalemedicine.org.

## Results and Best Forecast Model

The best model from our testing dataset is:
- Arima model with Fourier terms and crude oil as external regressor
- It has an RMSE  of 2.511553 and a MAPE of 1.699530

We use this model to forecast the daily returns of Bitcoin for the next 30 days.

## Instructions for Reproduction

### Prerequisites
- Git installed on your local machine
- Python 3.x installed with pip

### Steps
1. **Clone Repository**: Clone this repository to your local machine using the following command:
   ```bash
   git clone https://github.com/vivianzzzzz/ZhangXiaGupta_ENV797_TSA_FinalProject/
   cd ZhangXiaGupta_ENV797_TSA_FinalProject
   ```
2. Execute the R Markdown file to run the scripts and notebooks for each model. This will generate the outputs, including model results, visualizations, and forecasts.


## References
1. https://fred.stlouisfed.org/series/DCOILBRENTEU
2. https://www.yalemedicine.org/news/covid-timeline
