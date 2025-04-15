# Developed By : Abhishek kannan M
# Register Number : 212224040007
# Date: 14/5/25
# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES


### AIM:

To implement ARMA model in python.

### ALGORITHM:

1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000 data points using the ArmaProcess class. Plot the generated time series and set the title and x-axis limits.
4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000 data points using the ArmaProcess class. Plot the generated time series and set the title and x-axis limits.
6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using plot_acf and plot_pacf.

### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
import warnings
warnings.filterwarnings('ignore')
```
Load the AirPassengers dataset
```py
data = pd.read_csv('irPassengers.csv')
```
Use the '#Passengers' column
```py
passenger_counts = data['#Passengers'].dropna()
plt.rcParams['figure.figsize'] = [10, 7.5]
```

Simulate ARMA(1,1) Process
```py
ar1 = np.array([1, 0.33])
ma1 = np.array([1, 0.9])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=len(passenger_counts))
plt.plot(ARMA_1)
plt.title('Simulated ARMA(1,1) Process')
plt.xlim([0, len(passenger_counts)])
plt.show()
```
Plot ACF and PACF for ARMA(1,1)
```py
plot_acf(ARMA_1)
plt.show()
plot_pacf(ARMA_1)
plt.show()
```
Simulate ARMA(2,2) Process
```py
ar2 = np.array([1, 0.33, 0.5])
ma2 = np.array([1, 0.9, 0.3])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=len(passenger_counts) * 10)
plt.plot(ARMA_2)
plt.title('Simulated ARMA(2,2) Process')
plt.xlim([0, 200])
plt.show()
```
Plot ACF and PACF for ARMA(2,2)
```py
plot_acf(ARMA_2)
plt.show()
plot_pacf(ARMA_2)
plt.show()

```

### OUTPUT:

SIMULATED ARMA(1,1) PROCESS:

![image](https://github.com/user-attachments/assets/571079aa-0f1f-4abc-b8f2-171c72e62a8b)


Partial Autocorrelation

![image](https://github.com/user-attachments/assets/e518a20b-5cca-489b-9f20-f4b83273041e)


Autocorrelation

![image](https://github.com/user-attachments/assets/0d07adb3-a184-4b40-bcb7-509aeffa75d5)


SIMULATED ARMA(2,2) PROCESS:

![image](https://github.com/user-attachments/assets/71848c7e-936f-4bb4-9e4c-9528da1bab32)


Partial Autocorrelation

![image](https://github.com/user-attachments/assets/7c8c36a9-8276-4461-a18c-046e0442853b)


Autocorrelation

![image](https://github.com/user-attachments/assets/fe154455-3af8-41c8-8066-b649ea9d34d0)


### RESULT:
Thus, a python program is created to fir ARMA Model successfully.
