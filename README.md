# Ex.No: 03 COMPUTE THE AUTOCORRELATION FUNCTION (ACF)

### Date: 14 - 11 - 2026

# AIM:
To compute the Autocorrelation Function (ACF) of the time series data for the first 35 lags to determine the temporal dependence and model type.

# DATASET:
- **Dataset Name**: Daily Minimum Temperatures in Melbourne (`daily-min-temperatures.csv`)
- **Sample Size**: 3,650 daily observations across 10 years (1981–1990)

# ALGORITHM:
1. Import the necessary packages (numpy, pandas, matplotlib).
2. Load the Daily Minimum Temperatures dataset using pandas.
3. Calculate sample mean and variance, and normalize the data.
4. Compute the sample autocovariance and autocorrelation across lags 0 to 34 from first principles.
5. Plot the ACF stem plot and display the results.

# PROGRAM:
```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

url = 'https://raw.githubusercontent.com/jbrownlee/Datasets/master/daily-min-temperatures.csv'

df = pd.read_csv(url)

data = df['Temp'].values

N = len(data)

lags = range(35)

autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

normalized_data = (data - mean_data) / np.sqrt(variance_data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Daily Minimum Temperatures')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

# OUTPUT:

### Autocorrelation of Daily Minimum Temperatures
<img width="846" height="547" alt="image" src="https://github.com/user-attachments/assets/f105e751-a5fb-4f44-be76-5d099721a865" />

# RESULT:
Thus, the Autocorrelation Function (ACF) has been computed and visualized successfully in Python.
