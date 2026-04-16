
Never throw information away, no matter how poor it is.

Residual: the difference between the measurement and prediction. (measurements and the filter's output)

The g-h filter algorithm, refers to two scaling factor. The Kalman filter is a form of the g-h filter.

Key points:
- Multiple data points are more accurate than one data point, so throw nothing away no matter how inaccurate it is.
- Always choose a number part way between two data points to create a more accurate estimate.
- Predict the next measurement and rate of change based on the current estimate and how much we think it will change.
- The new estimate is then chosen as part way between the prediction and next measurement scaled by how accurate each is.

The state of the system is the current configuration or values of that system that is of interest to us. We are interested only in the weight reading. If I put a 100 kg weight on the scale, the state is 100kg. We define the state based on what is relevant to us.

