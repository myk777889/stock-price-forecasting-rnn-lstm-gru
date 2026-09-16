# Stock Price Forecasting Using RNN, LSTM and GRU

## Project Overview

This project focuses on forecasting the next trading day's closing price of **Reliance Industries** using historical stock-price data from **2015 to 2025**.

Three recurrent neural network architectures are implemented and compared:

* Vanilla RNN
* LSTM
* GRU

An **ARIMA** model is also used as a classical time-series baseline.

The project analyzes forecasting performance, gradient behavior, and the effect of different architectural configurations.

## Problem Statement

Stock prices are sequential time-series data where previous observations can provide information about future values.

The objective of this project is to use historical Reliance Industries closing prices to predict the **next trading day's closing price** and compare different recurrent neural network architectures.

## Objectives

* Implement a Vanilla RNN for sequential forecasting.
* Implement an LSTM with forget, input, and output gates.
* Implement a GRU with update and reset gates.
* Compare RNN, LSTM, GRU, and ARIMA.
* Evaluate models using RMSE, MAE, and R².
* Analyze gradient behavior during training.
* Study the effect of sequence length, hidden-state size, and network depth.

## Dataset

The project uses daily historical stock-price data for Reliance Industries.

**Dataset:** `RELIANCE_2015_2025_Daily.csv`

* Period: 2015–2025
* Records: 2,870
* Features: Date, Open, High, Low, Close, Volume
* Target: Closing Price

## Methodology

### Data Preprocessing

The data was cleaned and checked for missing values, duplicate records, and chronological ordering.

The dataset was divided chronologically into:

* 80% Training
* 10% Validation
* 10% Testing

MinMax scaling was applied using the training data.

### Sequence Windowing

A **60-day sliding window** was used.

```text
Previous 60 Trading Days
          ↓
     RNN / LSTM / GRU
          ↓
Next Trading Day Close
```

The previous 60 closing prices are used to predict the next trading day's closing price.

## Models

### Vanilla RNN

The Vanilla RNN processes the sequence one timestep at a time and maintains a hidden state that carries information from previous observations.

### LSTM

LSTM uses a memory cell and three main gates:

* Forget Gate
* Input Gate
* Output Gate

These gates control the information that is removed, stored, and passed forward.

### GRU

GRU uses two main gates:

* Update Gate
* Reset Gate

It provides a simpler gated recurrent architecture compared with LSTM.

### ARIMA

ARIMA is used as a classical time-series forecasting baseline for comparison with the neural-network models.

## Experimental Setup

| Parameter        | Value   |
| ---------------- | ------- |
| Sequence Length  | 60      |
| Hidden Size      | 50      |
| Recurrent Layers | 1       |
| Batch Size       | 32      |
| Epochs           | 30      |
| Learning Rate    | 0.001   |
| Optimizer        | Adam    |
| Loss Function    | MSE     |
| Framework        | PyTorch |

## Final Results

| Model       |    RMSE |     MAE |    R² | Training Time |
| ----------- | ------: | ------: | ----: | ------------: |
| Vanilla RNN |  676.05 |  593.50 |  0.70 |       20.99 s |
| GRU         |  907.85 |  831.17 |  0.45 |       53.54 s |
| LSTM        | 1999.96 | 1834.56 | -1.65 |       29.43 s |
| ARIMA       | 3788.03 | 3583.59 | -8.52 |        0.29 s |

In the final experimental configuration, the **Vanilla RNN achieved the lowest RMSE and MAE and the highest R²** among the evaluated models.

This result is specific to the selected dataset, preprocessing, architecture, and training configuration.

## Gradient Analysis

Gradient norms were monitored during training to study gradient behavior and training stability.

The analysis compares the global gradient norm across training batches for:

* Vanilla RNN
* LSTM
* GRU

## Controlled Experiments

The project also investigates the effect of different architectural configurations.

### Sequence Length

* 30
* 60
* 90

### Hidden State Size

* 32
* 50
* 100

### Network Depth

* 1 recurrent layer
* 2 recurrent layers

These experiments help analyze how sequence length, model capacity, and network depth affect training behavior and performance.

## Technologies Used

* Python
* PyTorch
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* Google Colab
* Jupyter Notebook

## Project Structure

```text
stock-price-forecasting-rnn-lstm-gru/
│
├── README.md
├── Stock_Price_Forecasting_RNN_LSTM_GRU.ipynb
├── RELIANCE_2015_2025_Daily.csv
│
└── models/
```

## How to Run

1. Open the Jupyter Notebook in Google Colab or Jupyter Notebook.
2. Make sure `RELIANCE_2015_2025_Daily.csv` is available.
3. Install the required Python libraries if necessary.
4. Run the notebook cells sequentially.
5. The notebook performs data preprocessing, sequence creation, model training, evaluation, gradient analysis, and controlled experiments.

## Key Findings

* Recurrent neural networks can be applied to sequential stock-price forecasting.
* Vanilla RNN achieved the best performance in the final experimental configuration.
* GRU achieved the second-best forecasting performance.
* LSTM did not outperform the simpler architectures in this experiment.
* Gradient diagnostics provide insight into training behavior.
* Sequence length, hidden-state size, and network depth can affect model performance and training cost.

## Future Scope

* Multivariate forecasting using Open, High, Low, Close, and Volume.
* Hyperparameter optimization.
* Longer forecasting horizons.
* Attention-based and Transformer models.
* Real-time stock-price forecasting.
* Interactive forecasting dashboards.

## Conclusion

This project presents an experimental comparison of **Vanilla RNN, LSTM, and GRU** models for Reliance Industries stock-price forecasting.

The models were evaluated using forecasting metrics, gradient analysis, and controlled architectural experiments. The results demonstrate how model architecture and experimental configuration can influence forecasting performance on sequential financial data.

## Author

**Yeshwanth Kumar**
**Kanishk Sai Raj**
**Lokeshwar**
**Durga Prasad**

B.Tech — Computer Science and Engineering
Specialization: Artificial Intelligence and Machine Learning
