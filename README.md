# Exp-4-Compute-the-AutoCorrelation-Function-(ACF)
## AIM:
### Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the type of model to fit to the data.
## ALGORITHM:
### STEP 1: Import the necessary packages
### STEP 2: Find the mean, variance and then implement normalization for the data.
### STEP 3: Implement the correlation using necessary logic and obtain the results
### STEP 4: Store the results in an array
### STEP 5: Represent the result in graphical representation as given below.
## PROGRAM:

import matplotlib.pyplot as plt
import numpy as np
data = [3, 16, 156, 47, 246, 176, 233, 140, 130,
        101, 166, 201, 200, 116, 118, 247,
        209, 52, 153, 232, 128, 27, 192, 168, 208,
        187, 228, 86, 30, 151, 18, 254,
        76, 112, 67, 244, 179, 150, 89, 49, 83, 147, 90,
        33, 6, 158, 80, 35, 186, 127]
lags = range(35)
# Pre-allocate autocorrelation table
acorr = len(lags) * [0]
# Mean
mean = sum(data) / len(data)
# Variance
var = sum([(x - mean)**2 for x in data]) / len(data)
# Normalized data
ndata = [x - mean for x in data]
# Go through lag components one-by-one
for l in lags:
    c = 1 # Self correlation

    if (l > 0):
        tmp = [ndata[l:][i] * ndata[:-l][i]
            for i in range(len(data) - l)]

        c = sum(tmp) / len(data) / var
        #print(c)
        acorr[l] = c
print(acorr)
plt.grid(True)
plt.plot(acorr)
plt.title("Autocorrelation plot")
plt.xlabel("Lags")
plt.show()

## OUTPUT:
![image](https://github.com/gpavithra673/Exp-4-Compute-the-AutoCorrelation-Function-ACF-/assets/93427264/0f66c181-7c72-4140-acd7-a8cbc95109d8)

## RESULT: 
### Thus we have successfully implemented the auto correlation function using above mentioned program.
