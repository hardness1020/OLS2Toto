<h1 align="center">OLS2Toto</h1>

<div align="center">


</div>

---

<!-- <p align="center"> Few lines describing your project.
    <br> 
</p> -->

## 📝 Table of Contents

- [📝 Table of Contents](#-table-of-contents)
- [🧐 About ](#-about-)
- [📊 Results ](#-results-)
  - [Forecast Visualization](#forecast-visualization)
  - [Residuals Visualization](#residuals-visualization)
- [🏁 Prerequisites ](#-prerequisites-)
  - [Environment Setup](#environment-setup)
  - [Dataset](#dataset)
  - [Toto Time Series Forecasting Model](#toto-time-series-forecasting-model)
- [🎈 Usage ](#-usage-)
- [✍️ Authors ](#️-authors-)
- [📓 References ](#-references-)

<br>

## 🧐 About <a name = "about"></a>

This study investigates whether applying OLS-based diagnostic checks and subsequent feature engineering can improve the performance of a state-of-the-art (SOTA) time series forecasting model, [Toto](https://arxiv.org/abs/2407.07874), in predicting hourly bike rental demand. Full report can be found [here](https://www.overleaf.com/read/ftncmqsqbysm#3457b3).


<br>

## 📊 Results <a name = "results"></a>
We compared the performance of the Toto forecasting model on both:
* Method A (original dataset), and
* Method B: a transformed dataset where OLS-based feature engineering was applied to address linear regression assumptions (e.g., heteroscedasticity, multicollinearity).

| Dataset                    | MAE  | RMSE |
| -------------------------- | ---- | ---- |
| Method A: Original Data    | 39.8 | 63.0 |
| Method B: Transformed Data | 40.5 | 60.9 |

The results indicate that the OLS-based feature engineering did not significantly improve the performance of the Toto model. The MAE and RMSE values for the transformed dataset were slightly higher than those for the original dataset, suggesting that the SOTA model's architecture may already be robust enough to handle the complexities of the data without additional feature engineering.

### Forecast Visualization
Below are the visual comparisons of Toto forecasts using the original data and transformed data. Both figures show that the Toto model captures trends and uncertainty intervals similarly in both cases.

![Forecast by Original Data](https://raw.githubusercontent.com/hardness1020/OLS2Toto/main/figures/results/Forecast_by_Original_Data.png)

![Forecast by Transformed Data](https://raw.githubusercontent.com/hardness1020/OLS2Toto/main/figures/results/Forecast_by_Transformed_Data.png)

### Residuals Visualization
We further examined the residuals to understand model fit. Both residual series exhibit similar patterns with comparable magnitudes and occasional spikes, reinforcing that the transformation did not yield significant gains.

![Comparison of Residuals](https://raw.githubusercontent.com/hardness1020/OLS2Toto/main/figures/results/Comparison_of_Residuals.png)

<br>

## 🏁 Prerequisites <a name = "prerequisites"></a>
### Environment Setup
GPU is required to run the Toto model. It is avaliable on Google Colab, or you can set up a local environment with GPU support.
```
pip install -r requirements.txt
```

### Dataset
We analyze the [bike-sharing dataset](https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset) from the UCI Machine Learning Repository. Our analysis is based on `hour.csv`. Run the following command to download the dataset:

```
wget https://archive.ics.uci.edu/static/public/275/bike+sharing+dataset.zip
unzip bike+sharing+dataset.zip
rm bike+sharing+dataset.zip
```


### Toto Time Series Forecasting Model
The Toto model is a state-of-the-art time series forecasting model. Clone the Toto repository to access the model implementation:
```
git clone https://github.com/DataDog/toto.git
```


<br>

## 🎈 Usage <a name="usage"></a>
The OLS-based feature engineering is implemented in the `diagnotics.ipynb` notebook. The notebook performs the following steps:
1. Load the bike-sharing dataset: `hour.csv`.
2. Export the input for Method A (original data): ` hour_base.csv`.
3. Perform OLS diagnostics to check for linear regression assumptions.
4. Apply feature engineering based on the diagnostics results.
5. Export the input for Method B (transformed data): ` hour_transformed.csv`.

Both datasets are then used to train the Toto model, `forecast.ipynb`. The notebook also includes code to visualize the forecasts and residuals.


<br>

## ✍️ Authors <a name = "authors"></a>

- [@hardness1020](https://github.com/hardness1020) - Time Series Forecasting
- [@ripple-space](https://github.com/ripple-space) - OLS-based Feature Engineering


<br>

## 📓 References <a name = "references"></a>
- [Bike Sharing Dataset](https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset)
- [Toto: A State-of-the-Art Time Series Forecasting Model](https://arxiv.org/abs/2407.07874)
