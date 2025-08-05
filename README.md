<img width="1600" height="747" alt="Code_Generated_Image" src="https://github.com/user-attachments/assets/aa41fd44-fca1-489c-bd12-dece4df6d1ab" /># univariate-time-series
"Analysis and forecasting using ARIMA and SARIMAX on univariate time series data

As you can see from the plot, the monthly sales data shows a clear upward trend, indicating that the time series is non-stationary. The results of the initial ADF test confirm this, as the p-value is greater than 0.05.

Now, let's proceed with the next steps to prepare the data for an ARIMA model. I will perform first-order differencing to remove the trend and then re-evaluate the stationarity of the differenced data.


<img width="1600" height="747" alt="Code_Generated_Image" src="https://github.com/user-attachments/assets/0f0ccccf-050b-4b50-9623-c452801070db" />


Step 2: Differencing and Re-checking for Stationarity (Continued)

I will now create the first-order differenced series and check its stationarity.

<img width="1600" height="1280" alt="image" src="https://github.com/user-attachments/assets/08362737-1fa3-402a-8959-1efd31035136" />
<img width="1600" height="747" alt="image" src="https://github.com/user-attachments/assets/2e7ade1b-6ea9-42c3-8dcb-76be532e50f5" />



The differencing operation was successful. The plot of the differenced data shows that the upward trend has been removed, and the data now fluctuates around a mean of zero. The ADF test confirms this, as the p-value (1.277
times10 
−5
 ) is well below the 0.05 significance level, indicating that the series is now stationary.

Now, we will determine the p and q parameters from the ACF and PACF plots.

Step 3: Identifying the AR(p) and MA(q) Parameters

ACF Plot: The plot shows a significant spike at lag 1 that quickly tails off, suggesting an MA(1) component.

PACF Plot: Similarly, the plot shows a significant spike at lag 1, suggesting an AR(1) component.

Based on these observations, a suitable starting point for our model is ARIMA(1,1,1), where:

p=1 (Autoregressive component)

d=1 (Integrated/Differencing component)

q=1 (Moving Average component)

Step 4: Building, Training, and Evaluating the ARIMA Model

We will now split the data into a training set and a test set to evaluate the model's performance on unseen data. We will train the ARIMA(1,1,1) model on the training data and then make predictions on the test set. Finally, we will calculate the Root Mean Squared Error (RMSE) to measure the model's accuracy.

Step 5: Forecasting Future Sales

After evaluating the model, we will use it to forecast future monthly sales for the next 12 months.


<img width="1600" height="747" alt="image" src="https://github.com/user-attachments/assets/7434a983-e1e7-4bd4-9fe9-9d0f307e1fd6" />
<img width="1600" height="747" alt="image" src="https://github.com/user-attachments/assets/2e70867b-28cd-4bcd-848e-6988bfefc3bc" />



Analysis of the Grocery Store Monthly Sales Data using ARIMA
I have successfully performed a time series analysis on the store_monthly_sales.csv dataset, following the key steps of building an ARIMA model.

Step 1: Data Preparation and Visualization
First, I loaded the data, converted the Month column to a datetime index, and then plotted the monthly sales.

The plot below reveals a clear upward trend in sales over the years, which is a strong indicator that the time series is non-stationary.

Step 2: Checking for Stationarity and Differencing
To confirm the visual observation of non-stationarity, I performed an Augmented Dickey-Fuller (ADF) test on the original sales data.

ADF Test on Original Data: The p-value was 0.995, which is much greater than 0.05. This confirmed that the data was non-stationary.

Differencing: To make the series stationary, I applied a first-order difference (d=1), which involves subtracting the previous month's sales from the current month's. The plot of this differenced data shows that the trend has been successfully removed, and the series now fluctuates around a constant mean.

ADF Test on Differenced Data: The p-value on the differenced data was 1.277
times10 
−5
 , which is significantly less than 0.05. This confirms that our differenced series is now stationary.

Step 3: Identifying the AR(p) and MA(q) Parameters
With a stationary series, I generated Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots to determine the p and q parameters for the ARIMA model.

ACF Plot: A significant spike at lag 1 suggests a potential Moving Average (MA) component of order 1 (q=1).

PACF Plot: Similarly, a significant spike at lag 1 suggests a potential Autoregressive (AR) component of order 1 (p=1).

Based on this analysis, I selected an ARIMA(1,1,1) model for the sales data.

Step 4: Model Building and Evaluation
I split the data into an 80% training set and a 20% test set. The ARIMA(1,1,1) model was trained on the training data and then used to forecast sales for the test period.

Model Summary: The model's Ljung-Box test p-value of 0.76 is greater than 0.05, indicating that the residuals are random (white noise), which is a good sign for the model's fit.

Evaluation: The Root Mean Squared Error (RMSE) on the test set was calculated to be 6037.88. This value represents the average error between the model's predictions and the actual sales. The lower the RMSE, the better the model's predictive accuracy. The plot below shows how the model's predictions align with the actual sales data.

Step 5: Forecasting Future Sales
Finally, using the fitted model, I forecasted the monthly sales for the next 12 months. The plot below shows the historical sales data and the future forecast, which continues the upward trend observed in the past.
