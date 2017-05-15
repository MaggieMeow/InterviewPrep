# Time Series Machine Learning

## Concepts
**Concept Drift**:
The statistical properties of the target variable, which the model tries to predict, change over time. Predictions become less accurate over time.

**time dimension**: 
An explicit order dependence between observations: a time dimension.

**sliding window**:
The use of prior time steps to predict the next time step.  In statistics and time series analysis, this is called a lag or lag method.

## Components of Time Series
1. **Level**. The baseline value for the series if it were a straight line.
2. **Trend**. The optional and often linear increasing or decreasing behavior of the series over time.
3. **Seasonality**. The optional repeating patterns or cycles of behavior over time.
4. **Noise**. The optional variability in the observations that cannot be explained by the model.

## ARIMA

An initial differencing step (corresponding to the "integrated" part of the model) can be applied one or more times to eliminate the non-stationarity.

**non-stationarity** (or stationarity):
A stationary process is a stochastic process whose joint probability distribution does not change when shifted in time. Consequently, parameters such as mean and variance, if they are present, also do not change over time.

