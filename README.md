# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 11-05-2026
### Name: Ramitha chowdary S

## AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

## PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load the dataset, Convert 'Month' column to datetime format, Set it as index
data = pd.read_csv('AirPassengers.csv', parse_dates=['Month'], index_col='Month')

# FIRST FIVE ROWS
display(data.head())

# PLOTTING THE DATA
data.plot()
plt.title('Monthly Passengers')
plt.xlabel('Year')
plt.ylabel('No of Passengers')
plt.show()

# Step 2: Perform seasonal decomposition
decomposition = seasonal_decompose(data['#Passengers'], model='additive', period=12)

# SEASONAL PLOT REPRESENTATION
decomposition.seasonal.plot()
plt.title('Seasonal Plot')
plt.xlabel('Year')
plt.ylabel('Seasonal')
plt.show()

# TREND PLOT REPRESENTATION
decomposition.trend.plot()
plt.title('Trend Plot')
plt.xlabel('Year')
plt.ylabel('Trend')
plt.show()

# OVERALL REPRESENTATION
plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(data['#Passengers'], label='Monthly Passengers')
plt.legend(loc='upper left')
plt.title('Monthly Passengers')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Linear Trend Plot')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```
## OUTPUT:
#### FIRST FIVE ROWS:
<img width="221" height="194" alt="image" src="https://github.com/user-attachments/assets/46ba6f61-8862-4dea-bbf8-a02641c2c11f" />


#### PLOTTING THE DATA:
<img width="565" height="446" alt="image" src="https://github.com/user-attachments/assets/cd7a737e-e32c-475a-be44-7faaa3cb0b6f" />

#### SEASONAL PLOT REPRESENTATION :
<img width="566" height="450" alt="image" src="https://github.com/user-attachments/assets/662d65fb-0946-4c4c-8075-31d1a3a8f729" />

#### TREND PLOT REPRESENTATION :
<img width="563" height="450" alt="image" src="https://github.com/user-attachments/assets/52cdf605-9c0a-4c59-9d66-c4fc4649124f" />

#### OVERALL REPRESENTATION:

<img width="747" height="228" alt="image" src="https://github.com/user-attachments/assets/7f080e4a-92ac-433a-8bc9-aa086acdf8a9" />
<img width="984" height="287" alt="image" src="https://github.com/user-attachments/assets/188554cf-02e6-412a-956d-b2360c2d1214" />
<img width="749" height="219" alt="image" src="https://github.com/user-attachments/assets/24d8dadc-1665-458e-9ff6-10d00ccb79ee" />
<img width="745" height="222" alt="image" src="https://github.com/user-attachments/assets/51e94f27-ebbe-42e4-954d-1235007fa9db" />


## RESULT:
Thus we have created the python code for the time series analysis and decomposition.
