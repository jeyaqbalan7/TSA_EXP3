# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
### name : Jeyabalan T
### Register Number : 212222240040
### Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load the Gold Price DataSet 
Gold_price = pd.read_csv("/content/rainfall.csv")

# Print the columns of the DataFrame to check their exact names
print(Gold_price.columns)

# Extract the 'Price' column (sales data) - Note the Capital P
price_data = Gold_price['rainfall'].values

# Calculate mean and variance
mean_price = np.mean(price_data)
var_price = np.var(price_data)

```
```
# Normalize the data (subtract mean and divide by standard deviation)
normalized_price = (price_data - mean_price) / np.sqrt(var_price)

# Compute the ACF for the first 35 lags
lags = range(35)
acf_values = [np.corrcoef(normalized_price[:-lag], normalized_price[lag:])[0, 1] if lag != 0 else 1 for lag in lags]

# Plot the ACF results
plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values, use_line_collection=True)
plt.title('Autocorrelation Function (ACF) for Gold price')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()

```

### OUTPUT:

![image](https://github.com/user-attachments/assets/e37eac7e-4e05-44c9-b048-d1317d48a0be)


### RESULT:
Thus we have successfully implemented the auto correlation function in python.
