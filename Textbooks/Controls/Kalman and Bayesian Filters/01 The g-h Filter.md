
Never throw information away, no matter how poor it is.

Residual: the difference between the measurement and prediction. (measurements and the filter's output)

The g-h filter algorithm, refers to two scaling factor. The Kalman filter is a form of the g-h filter.

Key points:
- Multiple data points are more accurate than one data point, so throw nothing away no matter how inaccurate it is.
- Always choose a number part way between two data points to create a more accurate estimate.
- Predict the next measurement and rate of change based on the current estimate and how much we think it will change.
- The new estimate is then chosen as part way between the prediction and next measurement scaled by how accurate each is.

The state of the system is the current configuration or values of that system that is of interest to us. We are interested only in the weight reading. If I put a 100 kg weight on the scale, the state is 100kg. We define the state based on what is relevant to us.

The measurement is a measured value of the system. Measurements can be inaccurate, so it may not have the same value as the state.

The state estimate is our filter's estimate of the state. For example, for the 100 kg weight our estimate might be 99.327 kg due to sensor errors. This is commonly abbreviated to estimate, and I have done that in this chapter.

The state is the actual value of the system, which is usually hidden to us. If you step on a scale you have a measurement, measurements are observable. You can never directly observe your weight, you can only measure it.

Any estimation problem consists of forming an estimate of a hidden state via observable measurements.

The predict step is known as the system propagation or evolution.

The update step is known as the measurement update, one iteration is known as an epoch.