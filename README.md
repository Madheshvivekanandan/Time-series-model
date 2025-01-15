# Time Series Forecasting with ARIMA

This project demonstrates time series forecasting using the ARIMA (AutoRegressive Integrated Moving Average) model. It includes data preprocessing, stationarity testing, model training, evaluation, and prediction.

## Features
- Time series analysis and preprocessing
- Stationarity testing using the Augmented Dickey-Fuller (ADF) test
- ARIMA model training and parameter selection
- Model evaluation using residual analysis
- Future value predictions

## Requirements
The following Python libraries are required:
- `numpy`
- `pandas`
- `matplotlib`
- `statsmodels`

Install the dependencies using:
```bash
pip install numpy pandas matplotlib statsmodels
```

## Dataset
The project uses a dataset with two columns:
- `Datetime`: A timestamp representing the time of observation.
- `Value`: The observed value at the corresponding timestamp.

Example:
```
Datetime,Value
2012-12-31 01:00:00,2945.0
2012-12-31 02:00:00,2868.0
2012-12-31 03:00:00,2812.0
```

## Steps to Run the Project

1. **Load the Dataset**:
   - Ensure the dataset is in CSV format.
   - Use the `pandas` library to read the dataset and parse the `Datetime` column.

2. **Preprocessing**:
   - Set `Datetime` as the index.
   - Check for missing values and handle them appropriately.

3. **Stationarity Check**:
   - Apply the Augmented Dickey-Fuller test to determine if the time series is stationary.
   - If non-stationary, apply differencing or other transformations.

4. **Train the ARIMA Model**:
   - Choose ARIMA parameters `(p, d, q)` based on ACF and PACF plots or trial-and-error.
   - Fit the ARIMA model to the training data.

5. **Evaluate the Model**:
   - Analyze residuals to ensure they resemble white noise.
   - Use metrics like AIC, BIC, and MSE for evaluation.

6. **Forecast Future Values**:
   - Generate forecasts and compare them with actual values (if available).

## Example Code
```python
from statsmodels.tsa.arima.model import ARIMA
import pandas as pd

# Load the dataset
data = pd.read_csv("data.csv", parse_dates=["Datetime"], index_col="Datetime")

# Train ARIMA model
model = ARIMA(data['Value'], order=(2, 1, 2))
results = model.fit()

# Print model summary
print(results.summary())

# Forecast future values
forecast = results.forecast(steps=10)
print(forecast)
```

## Results
- Visualizations of the original and differenced time series.
- Model summary with AIC and BIC values.
- Forecasted values for the next steps.

## Directory Structure
```
project/
├── data.csv            # Input dataset
├── main.py             # Main Python script
├── README.md           # Project documentation
└── requirements.txt    # List of dependencies
```

## Acknowledgements
This project uses the ARIMA model from the `statsmodels` library and is designed for educational purposes.
