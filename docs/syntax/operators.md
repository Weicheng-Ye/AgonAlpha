# Fast Expression Operators

## Arithmetic

### `abs`

Definition: `abs(x)`

Scope: `REGULAR` | Level: `ALL`

Returns the absolute value of a number, removing any negative sign.

Documentation: `/operators/abs`

### `add`

Definition: `add(x, y, filter = false), x + y`

Scope: `REGULAR` | Level: `ALL`

Adds two or more inputs element wise. Set filter=true to treat NaNs as 0 before summing.

Documentation: `/operators/add`

### `densify`

Definition: `densify(x)`

Scope: `REGULAR` | Level: `ALL`

Converts a grouping field of many buckets into lesser number of only available buckets so as to make working with grouping fields computationally efficient

Documentation: `/operators/densify`

### `divide`

Definition: `divide(x, y), x / y`

Scope: `REGULAR` | Level: `ALL`

x / y

### `inverse`

Definition: `inverse(x)`

Scope: `REGULAR` | Level: `ALL`

1 / x

### `log`

Definition: `log(x)`

Scope: `REGULAR` | Level: `ALL`

Calculates the natural logarithm of the input value. Commonly used to transform data that has positive values.

Documentation: `/operators/log`

### `max`

Definition: `max(x, y, ..)`

Scope: `REGULAR` | Level: `ALL`

Maximum value of all inputs. At least 2 inputs are required

Documentation: `/operators/max`

### `min`

Definition: `min(x, y ..)`

Scope: `REGULAR` | Level: `ALL`

Minimum value of all inputs. At least 2 inputs are required

Documentation: `/operators/min`

### `multiply`

Definition: `multiply(x ,y, ... , filter=false), x * y`

Scope: `REGULAR` | Level: `ALL`

Multiplies two or more inputs element wise. Set filter=true to treat NaNs as 0 before multiplication

Documentation: `/operators/multiply`

### `power`

Definition: `power(x, y)`

Scope: `REGULAR` | Level: `ALL`

x ^ y

Documentation: `/operators/power`

### `reverse`

Definition: `reverse(x)`

Scope: `REGULAR` | Level: `ALL`

- x

### `sign`

Definition: `sign(x)`

Scope: `REGULAR` | Level: `ALL`

Returns the sign of a number: +1 for positive, -1 for negative, and 0 for zero. If the input is NaN, returns NaN.

Input: Value of 7 instruments at day t: (2, -3, 5, 6, 3, NaN, -10)
Output: (1, -1, 1, 1, 1, NaN, -1)

Documentation: `/operators/sign`

### `signed_power`

Definition: `signed_power(x, y)`

Scope: `REGULAR` | Level: `ALL`

x raised to the power of y such that final result preserves sign of x

Documentation: `/operators/signed_power`

### `sqrt`

Definition: `sqrt(x)`

Scope: `REGULAR` | Level: `ALL`

Returns the non negative square root of x. Equivalent to power(x, 0.5); for signed roots use signed_power(x, 0.5).

Documentation: `/operators/sqrt`

### `subtract`

Definition: `subtract(x, y, filter=false), x - y`

Scope: `REGULAR` | Level: `ALL`

Subtracts inputs left to right: x ? y ? … Supports two or more inputs. Set filter=true to treat NaNs as 0 before subtraction.

Documentation: `/operators/subtract`

## Cross Sectional

### `normalize`

Definition: `normalize(x, useStd = false, limit = 0.0)`

Scope: `REGULAR` | Level: `ALL`

Centers a daily cross section by subtracting the market mean; optionally divide by the cross sectional standard deviation and clamp the result to [?limit, +limit]. NaNs are ignored in mean/std.

Documentation: `/operators/normalize`

### `quantile`

Definition: `quantile(x, driver = gaussian, sigma = 1.0)`

Scope: `REGULAR` | Level: `ALL`

Ranks and shifts a vector of Alpha values, then applies a chosen statistical distribution (gaussian, cauchy, or uniform) to reduce outliers. The sigma parameter controls the scale of the output.

Documentation: `/operators/quantile`

### `rank`

Definition: `rank(x, rate=2)`

Scope: `REGULAR` | Level: `ALL`

Ranks the values of the input x among all instruments, returning numbers evenly spaced between 0.0 and 1.0. Useful for normalizing data and reducing the impact of outliers.

Documentation: `/operators/rank`

### `scale`

Definition: `scale(x, scale=1, longscale=1, shortscale=1)`

Scope: `REGULAR` | Level: `ALL`

Scales the input so that the sum of absolute values across all instruments equals a specified book size. Allows separate scaling for long and short positions using optional parameters.

Documentation: `/operators/scale`

### `winsorize`

Definition: `winsorize(x, std=4)`

Scope: `REGULAR` | Level: `ALL`

Winsorize limits values in a data to within a specified number of standard deviations from the mean, reducing the impact of extreme outliers.

Documentation: `/operators/winsorize`

### `zscore`

Definition: `zscore(x)`

Scope: `REGULAR` | Level: `ALL`

Z-score is a numerical measurement that describes a value's relationship to the mean of a group of values. Z-score is measured in terms of standard deviations from the mean

Documentation: `/operators/zscore`

## Group

### `group_backfill`

Definition: `group_backfill(x, group, d, std = 4.0)`

Scope: `REGULAR` | Level: `ALL`

Fills missing (NaN) values for instruments within the same group by calculating a winsorized mean of all non-NaN values over the past d days. The winsorized mean is computed by trimming extreme values based on a specified standard deviation multiplier (std, default 4.0).

Documentation: `/operators/group_backfill`

### `group_mean`

Definition: `group_mean(x, weight, group)`

Scope: `REGULAR` | Level: `ALL`

Calculates the harmonic mean of a data field within each specified group.

Documentation: `/operators/group_mean`

### `group_neutralize`

Definition: `group_neutralize(x, group)`

Scope: `REGULAR` | Level: `ALL`

Neutralizes Alpha values within each specified group by subtracting the group mean from each value. Groups can be industry, sector, country, or any custom grouping.

Documentation: `/operators/group_neutralize`

### `group_rank`

Definition: `group_rank(x, group)`

Scope: `REGULAR` | Level: `ALL`

Ranks each element within its group based on the input field, assigning a value between 0.0 and 1.0. This helps compare items within the same group, such as stocks in the same industry.

Documentation: `/operators/group_rank`

### `group_scale`

Definition: `group_scale(x, group)`

Scope: `REGULAR` | Level: `ALL`

Normalizes values within each group to a range between 0 and 1, making data comparable across different groups.

Documentation: `/operators/group_scale`

### `group_zscore`

Definition: `group_zscore(x, group)`

Scope: `REGULAR` | Level: `ALL`

Calculates the Z-score of each value within its group, showing how far each value is from the group mean in terms of standard deviations. Useful for comparing values relative to their group.

Documentation: `/operators/group_zscore`

## Logical

### `and`

Definition: `and(input1, input2)`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if both inputs are 1 ('true'). Otherwise, returns 0 ('false').

### `equal`

Definition: `input1 == input2`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if input1 and input2 are the same. Otherwise, returns 0 ('false').

### `greater`

Definition: `input1 > input2`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if input1 is a larger than input2. Otherwise, returns 0 ('false').

### `greater_equal`

Definition: `input1 >= input2`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if input1 is a larger or the same as input2. Otherwise, returns 0 ('false').

### `if_else`

Definition: `if_else(input1, input2, input 3)`

Scope: `REGULAR` | Level: `ALL`

The if_else operator returns one of two values based on a condition. If the condition is true, it returns the first value; if false, it returns the second value.

Documentation: `/operators/if_else`

### `is_nan`

Definition: `is_nan(input)`

Scope: `REGULAR` | Level: `ALL`

If (input == NaN) return 1 else return 0

Documentation: `/operators/is_nan`

### `less`

Definition: `input1 < input2`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if input1 is a smaller than input2. Otherwise, returns 0 ('false').

### `less_equal`

Definition: `input1 <= input2`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if input1 is a smaller or the same as input2. Otherwise, returns 0 ('false').

### `not`

Definition: `not(x)`

Scope: `REGULAR` | Level: `ALL`

Returns the logical negation of x. Returns 0 when x is 1 (‘true’) and 1 when x is 0 (‘false’).

### `not_equal`

Definition: `input1!= input2`

Scope: `REGULAR` | Level: `ALL`

Returns 1 ('true') if input1 and input2 are different numbers. Otherwise, returns 0 ('false').

### `or`

Definition: `or(input1, input2)`

Scope: `REGULAR` | Level: `ALL`

Returns 1 if either input is true (either input1 or input2 has a value of 1), otherwise it returns 0.

## Time Series

### `days_from_last_change`

Definition: `days_from_last_change(x)`

Scope: `REGULAR` | Level: `ALL`

Calculates the number of days since the last change in the value of a given variable.

Documentation: `/operators/days_from_last_change`

### `hump`

Definition: `hump(x, hump = 0.01)`

Scope: `REGULAR` | Level: `ALL`

Limits amount and magnitude of changes in input (thus reducing turnover)

Documentation: `/operators/hump`

### `kth_element`

Definition: `kth_element(x, d, k, ignore=“NaN”)`

Scope: `REGULAR` | Level: `ALL`

Returns the K-th value from a time series by looking back over a specified number of (‘d’) days, with the option to ignore certain values. Commonly used for backfilling missing data.

Documentation: `/operators/kth_element`

### `last_diff_value`

Definition: `last_diff_value(x, d)`

Scope: `REGULAR` | Level: `ALL`

Returns the most recent value of x from the past d days that is different from the current value of x.

Documentation: `/operators/last_diff_value`

### `ts_arg_max`

Definition: `ts_arg_max(x, d)`

Scope: `REGULAR` | Level: `ALL`

Returns the number of days since the maximum value occurred in the last d days of a time series. If today's value is the maximum, returns 0; if it was yesterday, returns 1, and so on.

Documentation: `/operators/ts_arg_max`

### `ts_arg_min`

Definition: `ts_arg_min(x, d)`

Scope: `REGULAR` | Level: `ALL`

Returns the number of days since the minimum value occurred in a time series over the past d days. If today's value is the minimum, returns 0; if it was yesterday, returns 1, and so on.

Documentation: `/operators/ts_arg_min`

### `ts_av_diff`

Definition: `ts_av_diff(x, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the difference between a value and its mean over a specified period, ignoring NaN values in the mean calculation. In short, it returns x – ts_mean(x, d) with NaNs ignored.

Documentation: `/operators/ts_av_diff`

### `ts_backfill`

Definition: `ts_backfill(x,lookback = d, k=1)`

Scope: `REGULAR` | Level: `ALL`

Replaces missing (NaN) values in a time series with the most recent valid value from a specified lookback window, improving data coverage and reducing risk from missing data.

Documentation: `/operators/ts_backfill`

### `ts_corr`

Definition: `ts_corr(x, y, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the Pearson correlation between two variables, x and y, over the past d days, showing how closely they move together.

Documentation: `/operators/ts_corr`

### `ts_count_nans`

Definition: `ts_count_nans(x ,d)`

Scope: `REGULAR` | Level: `ALL`

Counts the number of missing (NaN) values in a data series over a specified number of days.

Documentation: `/operators/ts_count_nans`

### `ts_covariance`

Definition: `ts_covariance(y, x, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the covariance between two time-series variables, y and x, over the past d days. Useful for measuring how two variables move together within a specified historical window.

Documentation: `/operators/ts_covariance`

### `ts_decay_linear`

Definition: `ts_decay_linear(x, d, dense = false)`

Scope: `REGULAR` | Level: `ALL`

Applies a linear decay to time-series data over a set number of days, smoothing the data by averaging recent values and reducing the impact of older or missing data.

Documentation: `/operators/ts_decay_linear`

### `ts_delay`

Definition: `ts_delay(x, d)`

Scope: `REGULAR` | Level: `ALL`

Returns the value of a variable x from d days ago. Use this operator to access historical data points by specifying the desired time lag in days.

Documentation: `/operators/ts_delay`

### `ts_delta`

Definition: `ts_delta(x, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the difference between a value and its delayed version over a specified period. Useful for measuring changes or momentum in time-series data.

Documentation: `/operators/ts_delta`

### `ts_mean`

Definition: `ts_mean(x, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the simple average (mean) value of a variable x over the past d days.

Documentation: `/operators/ts_mean`

### `ts_product`

Definition: `ts_product(x, d)`

Scope: `REGULAR` | Level: `ALL`

Returns the product of the values of x over the past d days. Useful for calculating geometric means and compounding returns or growth rates.

Documentation: `/operators/ts_product`

### `ts_quantile`

Definition: `ts_quantile(x,d, driver="gaussian" )`

Scope: `REGULAR` | Level: `ALL`

Calculates the ts_rank of the input and transforms it using the inverse cumulative distribution function (quantile function) of a specified probability distribution (default: Gaussian/normal). This helps to normalize or reshape the distribution of your data over a rolling window.

Documentation: `/operators/ts_quantile`

### `ts_rank`

Definition: `ts_rank(x, d, constant = 0)`

Scope: `REGULAR` | Level: `ALL`

Ranks the value of a variable for each instrument over a specified number of past days, returning the rank of the current value (optionally adjusted by a constant). Useful for normalizing time-series data and highlighting relative performance over time.

Documentation: `/operators/ts_rank`

### `ts_regression`

Definition: `ts_regression(y, x, d, lag = 0, rettype = 0)`

Scope: `REGULAR` | Level: `ALL`

Returns various parameters related to regression function

Documentation: `/operators/ts_regression`

### `ts_scale`

Definition: `ts_scale(x, d, constant = 0)`

Scope: `REGULAR` | Level: `ALL`

Scales a time series to a 0–1 range based on its minimum and maximum values over a specified period, with an optional constant shift.

Documentation: `/operators/ts_scale`

### `ts_std_dev`

Definition: `ts_std_dev(x, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the standard deviation of a data series x over the past d days, measuring how much the values deviate from their mean during that period.

Documentation: `/operators/ts_std_dev`

### `ts_step`

Definition: `ts_step(1)`

Scope: `REGULAR` | Level: `ALL`

Returns a counter of days, incrementing by one each day.

Documentation: `/operators/ts_step`

### `ts_sum`

Definition: `ts_sum(x, d)`

Scope: `REGULAR` | Level: `ALL`

Sum values of x for the past d days.

### `ts_zscore`

Definition: `ts_zscore(x, d)`

Scope: `REGULAR` | Level: `ALL`

Calculates the Z-score of a time series, showing how far today's value is from the recent average, measured in standard deviations. Useful for standardizing and comparing values over time.

Documentation: `/operators/ts_zscore`

## Transformational

### `bucket`

Definition: `bucket(rank(x), range=“0, 1, 0.1”, skipBoth=False, NaNGroup=False)
or
bucket(rank(x), buckets = “2,5,6,7,10”, skipBoth=False, NaNGroup=False)`

Scope: `REGULAR` | Level: `ALL`

The bucket operator creates custom groups by dividing data into buckets (ranges) based on ranked values of any data field. These buckets can then be used with group operators like group_neutralize, group_rank, group_zscore etc.

Documentation: `/operators/bucket`

### `trade_when`

Definition: `trade_when(x, y, z)`

Scope: `REGULAR` | Level: `ALL`

The trade_when operator changes Alpha values only when a specific condition is met, keeps previous values otherwise, and can close positions by assigning NaN under an exit condition. It is useful for reducing turnover and controlling when trades are executed.

Documentation: `/operators/trade_when`

## Vector

### `vec_avg`

Definition: `vec_avg(x)`

Scope: `REGULAR` | Level: `ALL`

Calculates the mean (average) of all elements in a vector field for each instrument and date, converting vector data to a single matrix value.

Documentation: `/operators/vec_avg`

### `vec_sum`

Definition: `vec_sum(x)`

Scope: `REGULAR` | Level: `ALL`

Calculates the sum of all values in a vector field.

Documentation: `/operators/vec_sum`
