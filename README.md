# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date:12/05/2026 

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
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Load Salary Prediction Dataset
data = pd.read_csv('/content/salary_prediction_data.csv')

# Select Salary Column
salary_data = data['Salary']

# Convert into NumPy Array
data_values = np.array(salary_data)

# Length of Data
N = len(data_values)

# Define Lags
lags = range(35)

# Empty List for Autocorrelation Values
autocorr_values = []

# Calculate Mean and Variance
mean_data = np.mean(data_values)
variance_data = np.var(data_values)

# Normalize Data
normalized_data = (data_values - mean_data) / np.sqrt(variance_data)

# -----------------------------------
# Calculate Autocorrelation
# -----------------------------------
for lag in lags:

    if lag == 0:
        autocorr_values.append(1)

    else:
        auto_cov = np.sum(
            (data_values[:-lag] - mean_data) *
            (data_values[lag:] - mean_data)
        ) / N

        # Normalize by Variance
        autocorr_values.append(auto_cov / variance_data)

# -----------------------------------
# Display the Graph
# -----------------------------------
plt.figure(figsize=(10, 6))

plt.stem(lags, autocorr_values)

plt.title('Autocorrelation of Salary Data')

plt.xlabel('Lag')

plt.ylabel('Autocorrelation')

plt.grid(True)

plt.show()
```


### OUTPUT:

<img width="795" height="513" alt="image" src="https://github.com/user-attachments/assets/55a7ce3e-b14e-4744-b826-a18669d1f3c2" />



### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
