# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the Vegetable Price Dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```py

import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the data
file_path = '/content/vegetable.csv'
data = pd.read_csv(file_path)
print(df.head())

# Convert 'Date' to datetime format
data['Date'] = pd.to_datetime(data['Date'])

# Select data for a specific commodity, e.g., 'Tomato Big(Nepali)'
commodity_data = data[data['Commodity'] == 'Tomato Big(Nepali)']

# Set 'Date' as the index
commodity_data.set_index('Date', inplace=True)

# Resample to monthly data by averaging
monthly_data = commodity_data['Average'].resample('M').mean()

# Perform seasonal decomposition (multiplicative model)
decomposition = seasonal_decompose(monthly_data.dropna(), model='multiplicative', period=12)

# Plot the decomposition
fig, (ax1, ax2, ax3, ax4) = plt.subplots(4, 1, figsize=(10, 8))

# Original Price
ax1.set_title('Original Vegetable Price')
monthly_data.plot(ax=ax1, color='blue')

# Trend
ax2.set_title('Trend')
decomposition.trend.plot(ax=ax2, color='green')

# Seasonal
ax3.set_title('Seasonal')
decomposition.seasonal.plot(ax=ax3, color='orange')

# Residual
ax4.set_title('Residual')
decomposition.resid.plot(ax=ax4, color='red')

plt.tight_layout()
plt.show()

```


### OUTPUT:
## FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/d2d46057-1bdd-47fe-98fe-05cb8a904c38)



## PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/41ec4999-7792-4f25-845b-ee0925bf7ba1)




### RESULT:
Thus the python code for the time series analysis and decomposition is executed sucessfully.
