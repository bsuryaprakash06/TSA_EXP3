# Autocorrelation Function (ACF) Computation and Lag Analysis

A foundational statistical implementation of sample autocovariance and autocorrelation function (ACF) algorithms from first mathematical principles without high-level wrapper libraries.

---

## Objective

Compute the sample Autocorrelation Function (ACF) across the first 35 lags ($k = 0, 1, \dots, 34$) to quantify temporal dependence, memory decay, and cyclic periodicity within empirical observations, providing the theoretical diagnostic required for autoregressive order selection.

---

## Dataset Utilized

- **Dataset Name**: Daily Minimum Temperatures in Melbourne
- **Filename**: `daily-min-temperatures.csv`
- **Domain**: Climatology / Surface Temperature
- **Location**: Melbourne, Australia
- **Sample Size**: 3,650 daily observations spanning 1981 to 1990
- **Target Feature**: `Temp` (Daily minimum temperature in Celsius, °C)

---

## Mathematical Formulation

For an empirical time series $y_1, y_2, \dots, y_N$ with sample mean $\bar{y} = \frac{1}{N}\sum_{t=1}^N y_t$ and sample variance $\hat{\gamma}(0) = \frac{1}{N}\sum_{t=1}^N (y_t - \bar{y})^2$:

### 1. Sample Autocovariance
For lag $k \ge 0$:
$$\hat{\gamma}(k) = \frac{1}{N} \sum_{t=1}^{N-k} (y_t - \bar{y})(y_{t+k} - \bar{y})$$

### 2. Sample Autocorrelation Function (ACF)
The dimensionless correlation coefficient normalized to $[-1, 1]$:
$$\hat{\rho}(k) = \frac{\hat{\gamma}(k)}{\hat{\gamma}(0)} = \frac{\sum_{t=1}^{N-k} (y_t - \bar{y})(y_{t+k} - \bar{y})}{\sum_{t=1}^N (y_t - \bar{y})^2}$$

At lag $k = 0$, $\hat{\rho}(0) = 1.0$ by definition. Subsequent lags display slow harmonic decay characteristic of annual sinusoidal periodicity.

---

## Results & Visualizations

The computed autocorrelation values across 35 lags demonstrate substantial short-term memory ($\hat{\rho}(1) > 0.75$), confirming persistent thermal inertia and short-term meteorological predictability.

<p align="center">
  <img src="https://github.com/user-attachments/assets/f105e751-a5fb-4f44-be76-5d099721a865" alt="Autocorrelation Function Plot Across 35 Lags" width="85%" />
</p>

---

## License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
