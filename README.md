# Analyzing Price Forecasting of Grocery Products in Bangladesh

## Overview
[cite_start]This repository contains the methodology, findings, and analysis from the research paper **"Analyzing Price Forecasting of Grocery Products in Bangladesh: A Comparison of Time Series Modeling Approaches"**[cite: 2]. [cite_start]The project aims to forecast the prices of essential grocery commodities—specifically rice, wheat flour, and lentils—across various divisions in Bangladesh[cite: 11, 16]. 

[cite_start]By accurately predicting commodity prices, this research assists policymakers and decision-makers in monitoring market equilibrium, regulating price manipulation by market syndicates, and supporting low-income individuals affected by unforeseen price hikes[cite: 14, 27, 42].

## Dataset Information
[cite_start]The dataset was collected from the Humanitarian Data Exchange (HDX) platform, which aggregates monthly market monitoring data from the World Food Programme (WFP)[cite: 72, 75]. 

* [cite_start]**Total Entries:** 7,732 [cite: 79]
* [cite_start]**Target Variable:** Monthly commodity prices (wholesale and retail) [cite: 17, 79]
* [cite_start]**Monitored Commodities:** Rice, Wheat Flour, Lentils, and Palm Oil [cite: 79, 103]
* [cite_start]**Geographic Coverage:** Six primary divisions in Bangladesh (Dhaka, Chattogram, Rajshahi, Khulna, Barishal, and Sylhet) [cite: 83, 103]
* [cite_start]**Timeframe:** Data spans from roughly November 2005 to December 2021 (varying slightly by division)[cite: 83].

## Methodology

### 1. Data Preprocessing
[cite_start]The data was prepared and scaled using the `Scaler` transformer within the `Darts` library[cite: 86]. 
* [cite_start]The time series was transformed to a specific range using the `fit` and `transform` techniques[cite: 88, 89]. 
* [cite_start]An `inverse_transform` technique was utilized to return the predicted series back to its original price scale for evaluation[cite: 91].
* [cite_start]The dataset was split into **70% for training** and **30% for validation**[cite: 106].

### 2. Time Series Modeling
[cite_start]The experiment compared the performance of **12 distinct time series forecasting algorithms**[cite: 40, 97]:
1. Temporal Convolutional Network (TCN)
2. Neural Basis Expansion Analysis for Interpretable Time Series Forecasting (NBEATS)
3. Trend, Seasonal, and Exogenous Bayesian Time Series ((T)BATS)
4. Auto-ARIMA
5. Theta
6. Naïve Drift
7. Naïve Seasonal
8. Facebook Prophet
9. ARIMA
10. Fast Fourier Transform (FFT)
11. Recurrent Neural Network (RNN)
12. Naïve Ensemble

*Hyperparameter Tuning Note:* Epochs were modified to minimize forecasting inaccuracies. [cite_start]For example, NBEATS utilized 40 epochs, TCN utilized 400 epochs, and RNN utilized 500 epochs for optimal performance[cite: 98, 99].

## Key Findings & Results
[cite_start]Model performance was evaluated using **Mean Absolute Error (MAE)**[cite: 107]. [cite_start]Overall, the **RNN and Naïve Ensemble models** proved to be the most accurate in generalizing price changes across most divisions[cite: 18, 360].

* [cite_start]**Rice:** The RNN model performed best for the Chattogram, Rajshahi, Khulna, and Barishal divisions[cite: 110]. [cite_start]The Naïve Ensemble model yielded the lowest inaccuracy for the Dhaka and Sylhet divisions[cite: 111].
* [cite_start]**Wheat Flour:** The RNN model outperformed others in Chattogram and Rajshahi[cite: 113]. [cite_start]The Naïve Ensemble was best for Khulna and Barishal[cite: 114]. [cite_start]NBEATS and TCN models performed best for Sylhet and Dhaka, respectively[cite: 115].
* [cite_start]**Lentils:** The Naïve Ensemble model performed exceptionally well across all six divisions[cite: 276]. 

## Technologies & Libraries
* [cite_start]**Modeling & Forecasting:** `Darts` [cite: 105]
* [cite_start]**Visualization:** `Plotly Express` [cite: 105]

## Future Work
[cite_start]Future iterations of this research aim to utilize deep learning techniques to forecast a wider variety of grocery items on a weekly basis, rather than monthly, to achieve even greater accuracy[cite: 361].

## Citation
If you use this research or methodology in your work, please cite the original paper:

```bibtex
@inproceedings{hoque2023analyzing,
  title={Analyzing price forecasting of grocery products in bangladesh: A comparison of time series modeling approaches},
  author={Hoque, Md Mahmudul and Ahmed, Ikbal and Banik, Nayan and Hoque, Mohammed Moshiul},
  booktitle={International Conference on Intelligent Computing \& Optimization},
  pages={334--341},
  year={2023},
  organization={Springer}
}
