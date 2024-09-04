## DEVELOPED BY : AJAY ASWIN M
## REGISTER NUMBER : 212222240005
## Date:
# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on Petrol Price in top cities
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```python
import pandas as pd
import numpy as np

file_path = '/content/petrol.csv'
df = pd.read_csv(file_path)

print(df.head())

df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

df['Log_Value'] = np.log(df['Chennai'])

df['Differenced_Value'] = df['Chennai'].diff()

seasonal_period = 12
df['Seasonally_Adjusted_Value'] = df['Chennai'].diff(seasonal_period)

import matplotlib.pyplot as plt

# Plot the original data
plt.figure(figsize=(14, 10))

plt.subplot(4, 1, 1)
plt.plot(df['Value'], label='Original')
plt.title('Original Time Series')
plt.legend(loc='best')

# Plot the log-transformed data
plt.subplot(4, 1, 2)
plt.plot(df['Log_Value'], label='Log Transformed', color='orange')
plt.title('Log Transformed Time Series')
plt.legend(loc='best')

# Plot the regular differenced data
plt.subplot(4, 1, 3)
plt.plot(df['Differenced_Value'], label='Differenced', color='green')
plt.title('Regular Differenced Time Series')
plt.legend(loc='best')

# Plot the seasonally adjusted data
plt.subplot(4, 1, 4)
plt.plot(df['Seasonally_Adjusted_Value'], label='Seasonally Adjusted', color='red')
plt.title('Seasonally Adjusted Time Series')
plt.legend(loc='best')

plt.tight_layout()
plt.show()
```

### OUTPUT:
![petrol2](https://github.com/user-attachments/assets/912ca0af-2bc6-4940-9f75-9bed2016cbcc)




### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on Petrol Prices in Top cities
data.
