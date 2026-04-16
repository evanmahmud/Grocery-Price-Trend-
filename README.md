

# 🌾 Grocery Price Forecasting: Time Series Modeling in Bangladesh

> **An advanced Time Series Machine Learning pipeline designed to forecast essential commodity prices, empowering policymakers to stabilize markets and prevent syndicate manipulation in Bangladesh.**

## 📌 Project Overview
As a developing, agriculturally reliant nation, Bangladesh frequently faces unforeseen spikes in the prices of daily dietary staples. These fluctuations put immense strain on low-income demographics and disrupt market equilibrium. 

This project tackles this socio-economic challenge by deploying a robust machine learning pipeline to forecast the wholesale and retail prices of three primary commodities: **Rice, Wheat Flour, and Lentils**. By benchmarking 12 state-of-the-art time series algorithms across six major divisions, this research provides a predictive framework that can help government bodies and Trading Corporation of Bangladesh (TCB) authorities anticipate market trends and disrupt artificial price hikes.

---

## 📊 The Dataset
The dataset is sourced from the **Humanitarian Data Exchange (HDX)**, which aggregates monthly market monitoring data published by the **United Nations World Food Programme (WFP)**.

### Dataset Specifications
| Feature | Details |
| :--- | :--- |
| **Total Samples** | 7,732 Monthly Entries |
| **Timeframe** | November 2005 – December 2021 |
| **Target Variable** | Monthly Commodity Price (in BDT) |
| **Geographic Scope** | 6 Divisions: Dhaka, Chattogram, Rajshahi, Khulna, Barishal, Sylhet |
| **Commodities** | Rice, Wheat Flour, Lentils (Massor), Palm Oil |
| **Categories** | Cereals and Tubers, Pulses and Nuts, Oil and Fats |

---

## ⚙️ Machine Learning Pipeline

This repository leverages the `Darts` library for high-performance time series forecasting and `Plotly Express` for interactive visual evaluation. 

### 1. Data Engineering & Preprocessing
* **Temporal Scaling:** Utilized the `Scaler` transformer within the `Darts` ecosystem to normalize the vast differences in historical pricing data.
* **Transform Cycle:** Data was fitted and transformed to an optimal mathematical range for neural network training, and subsequently passed through an `inverse_transform` function to evaluate predictions in their original real-world currency scale.
* **Validation Split:** A strict chronological split of **70% Training / 30% Validation** was maintained to ensure the models evaluated true future, unseen data.

### 2. Time Series Architecture Benchmarking
To identify the most accurate forecasting mechanism, the study benchmarked **12 distinct algorithmic approaches**:
1. Recurrent Neural Network (RNN)
2. Temporal Convolutional Network (TCN)
3. Neural Basis Expansion Analysis (NBEATS)
4. Fast Fourier Transform (FFT)
5. Facebook Prophet (FBP)
6. Auto-ARIMA & Standard ARIMA
7. Trend, Seasonal, and Exogenous Bayesian Time Series ((T)BATS)
8. Theta Method
9. Naïve Drift, Naïve Seasonal, & Naïve Ensemble

*Hyperparameter Tuning Note:* Epoch thresholds were specifically optimized per architecture to minimize loss (e.g., NBEATS: 40 epochs; TCN: 400 epochs; RNN: 500 epochs).

---

## 🏆 Key Findings & Experimental Results

Model accuracy was rigorously evaluated using **Mean Absolute Error (MAE)**. The empirical results demonstrated that the **RNN** and **Naïve Ensemble** models possessed the strongest generalization capabilities for volatile market data.

### 🍚 Rice Forecasting
* **Top Performers:** RNN and Naïve Ensemble.
* **Regional Nuances:** The RNN model excelled in the Chattogram, Rajshahi, Khulna, and Barishal divisions (MAE ranging from 1.98 to 2.79). Meanwhile, the Naïve Ensemble delivered the lowest error margins for Dhaka and Sylhet.

### 🌾 Wheat Flour Forecasting
* **Top Performers:** Highly varied by region.
* **Regional Nuances:** RNN dominated in Chattogram and Rajshahi (scoring an impressive 0.59 MAE in Rajshahi). The Naïve Ensemble captured the best trends in Khulna and Barishal. Deep learning models NBEATS and TCN specifically outperformed all traditional models in Sylhet (0.38 MAE) and Dhaka (0.79 MAE), respectively.

### 🍲 Lentils (Massor) Forecasting
* **Top Performers:** Naïve Ensemble.
* **Regional Nuances:** The Naïve Ensemble model proved exceptionally stable for lentil pricing, outperforming complex neural networks across almost all divisions, achieving MAE scores as low as 4.54 in Chattogram and 4.83 in Dhaka.

---

## 💻 Getting Started

### Prerequisites
Ensure your Python environment is set up with the required libraries for deep learning and time series processing:
```bash
pip install darts plotly pandas numpy scikit-learn
```

### Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Grocery-Price-Forecasting.git
   ```
2. Launch your Jupyter environment:
   ```bash
   cd Grocery-Price-Forecasting
   jupyter notebook
   ```
3. Run the primary notebook to observe the `Darts` forecasting pipeline and Plotly evaluation charts.

---

## 🎓 Academic Citation

This repository is based on the published research paper. If you utilize this methodology, code, or findings in your own research or policy-making applications, please cite the following:

```bibtex
@inproceedings{hoque2023analyzing,
  title={Analyzing price forecasting of grocery products in bangladesh: A comparison of time series modeling approaches},
  author={Hoque, Md Mahmudul and Ahmed, Ikbal and Banik, Nayan and Hoque, Mohammed Moshiul},
  booktitle={International Conference on Intelligent Computing \& Optimization},
  pages={334--341},
  year={2023},
  organization={Springer},
  doi={10.1007/978-3-031-50158-6_33}
}
```

---
*Developed by Md Mahmudul Hoque, Ikbal Ahmed, Nayan Banik, and Mohammed Moshiul Hoque.*
