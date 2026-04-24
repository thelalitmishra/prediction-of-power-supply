Objective:
The objective of this project is to forecast the next hour electricity demand (demand_mw)
on the national grid using historical data.

The project uses three main datasets:
* Demand Data – Historical electricity demand and generation
* Weather Data – Weather-related features (temperature, etc.)
* Economic Data – Year-wise economic indicators

Methodology
1. Data Preprocessing
* Converted all column names to lowercase
* Converted datetime columns into proper format
* Sorted data based on time
* Removed duplicate entries
* Filled missing values using forward fill

2. Data Merging
* Merged demand and weather data using datetime
* Extracted year from datetime
* Merged economic data using year

3. Outlier Handling
* Used Z-score method to detect extreme values
* Replaced outliers with NaN and applied forward fill

4. Feature Engineering
Created useful features to help the model learn patterns:
* Time-based features:
    * Hour of day
    * Day of week
* Lag features:
    * Previous hour demand (lag_1)
    * Previous day same hour (lag_24)
* Rolling feature:
    * 24-hour moving average
* Target variable:
    * Next hour demand using shift(-1)
 
5. Train-Test Split
* Used 80% data for training
* Used 20% data for testing
* Maintained time order (no shuffling)

6. Model Used
* Random Forest Regressor
Reason:
* Simple and reliable
* Works well on tabular data
* No complex tuning required

7. Evaluation Metric
Used:
* MAPE (Mean Absolute Percentage Error)
MAPE tells how much error the model makes in percentage terms.

Results
* Test Samples: ~18,000
* MAPE: 3.65%

The model has an average error of only 3.65%, which indicates high accuracy in predicting electricity demand.
