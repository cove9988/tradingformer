### Regression Accuracy Check in Python (MAE, MSE, RMSE, R-Squared)

   The predictive model's error rate can be evaluated by applying several accuracy metrics in machine learning and statistics. The basic concept of accuracy evaluation in regression analysis is that comparing the original target with the predicted one and applying metrics like MAE, MSE, RMSE, and R-Squared to explain the errors and predictive ability of the model.  

   In this article, we'll briefly learn how to calculate the regression model accuracy by using the above-mentioned metrics in Python. The post covers:  

1.  Regression accuracy metrics
2.  Preparing data
3.  Metrics calculation by formula 
4.  Metrics calculation by sklearn.metrics
Let's get started.  

**Regression accuracy metrics**  

   The MSE, MAE, RMSE, and R-Squared are mainly used metrics to evaluate the prediction error rates and model performance in regression analysis.  

* **MAE** (Mean absolute error) represents the difference between the original and predicted values extracted by averaged the absolute difference over the data set.
* **MSE** (Mean Squared Error) represents the difference between the original and predicted values extracted by squared the average difference over the data set.
* **RMSE** (Root Mean Squared Error) is the error rate by the square root of MSE.
* **R-squared** (Coefficient of determination) represents the coefficient of how well the values fit compared to the original values. The value from 0 to 1 interpreted as percentages. The higher the value is, the better the model is.
The above metrics can be expressed,  

[![](https://1.bp.blogspot.com/-IXZrfXmG5Hs/XZvl6zHgwLI/AAAAAAAAAhw/-XoWPQLbkG4f-R6kQ7M4HxSOfP15KEAEwCLcBGAsYHQ/s1600/formula-MAE-MSE-RMSE-RSquared.JPG)](https://1.bp.blogspot.com/-IXZrfXmG5Hs/XZvl6zHgwLI/AAAAAAAAAhw/-XoWPQLbkG4f-R6kQ7M4HxSOfP15KEAEwCLcBGAsYHQ/s1600/formula-MAE-MSE-RMSE-RSquared.JPG)  


**Preparing data**  

   Original target data _**y**_ and predicted label the **_yhat_** are the main sources to evaluate the model. We'll start by loading the required modules for this tutorial.  

<pre style="line-height: 125%; margin: 0;">
importnumpy as np 
import sklearn.metrics as metrics
import matplotlib.pyplot as plt
</pre>  

Next, we'll create sample **_y_** and **_yhat_** data to evaluate the model by the above metrics.  

<pre style="line-height: 125%; margin: 0;">
y = np.array([-3, -1, -2, 1, -1, 1, 2, 1, 3, 4, 3, 5])
yhat = np.array([-2, 1, -1, 0, -1, 1, 2, 2, 3, 3, 3, 5])
x = list(range(len(y)))
</pre>  

We can visualize them in a plot to check the difference visually.  

<pre style="line-height: 125%; margin: 0;">
plt.scatter(x, y, color="blue", label="original")
plt.plot(x, yhat, color="red", label="predicted")
plt.legend()
plt.show() 
</pre>

<pre style="line-height: 125%; margin: 0;">

</pre>

[![](https://1.bp.blogspot.com/-pDVGs38kj_I/XZvmEHOyboI/AAAAAAAAAh0/TGwrQp924SsoauaCpmeJpqdbMz2slBXJACLcBGAsYHQ/s400/accuracy_check_data.png)](https://1.bp.blogspot.com/-pDVGs38kj_I/XZvmEHOyboI/AAAAAAAAAh0/TGwrQp924SsoauaCpmeJpqdbMz2slBXJACLcBGAsYHQ/s1600/accuracy_check_data.png)  

**Metrics calculation by formula**   

By using the above formulas, we can easily calculate them in Python.  

<pre style="line-height: 125%; margin: 0;">
\# calculate manually
d = y - yhat
mse_f = np.mean(d\**2)
mae_f = np.mean(abs(d))
rmse_f = np.sqrt(mse_f)
r2_f = 1-(sum(d\**2)/sum((y-np.mean(y))\**2))

print("Results by manual calculation:")
print("MAE:",mae_f)
print("MSE:", mse_f)
print("RMSE:", rmse_f)
print("R-Squared:", r2_f)
</pre>

<pre style="line-height: 125%; margin: 0;">

</pre>

<pre style="line-height: 125%; margin: 0;">
Results by manual calculation:
MAE: 0.5833333333333334
MSE: 0.75
RMSE: 0.8660254037844386
R-Squared: 0.8655043586550436 
</pre>  

**Metrics calculation by sklearn.metrics**  

Sklearn provides the number of metrics to evaluate accuracy. The next method is to calculate metrics with sklearn functions.  

<pre style="line-height: 125%; margin: 0;">
mae = metrics.mean_absolute_error(y, yhat)
mse = metrics.mean_squared_error(y, yhat)
rmse = np.sqrt(mse) \# or mse**(0.5)  
r2 = metrics.r2_score(y,yhat)

print("Results of sklearn.metrics:")
print("MAE:",mae)
print("MSE:", mse)
print("RMSE:", rmse)
print("R-Squared:", r2)
</pre>

<pre style="line-height: 125%; margin: 0;">

</pre>

<pre style="line-height: 125%; margin: 0;">
Results of sklearn.metrics:
MAE: 0.5833333333333334
MSE: 0.75
RMSE: 0.8660254037844386
R-Squared: 0.8655043586550436 
</pre>  

   The results are the same in both methods. You can use any method according to your convenience in your regression analysis.   

   In this post, we've briefly learned how to calculate MSE, MAE, RMSE, and R-Squared accuracy metrics in Python. The full source code is listed below.  


**Source code listing**  

<pre style="line-height: 125%; margin: 0;">
importnumpy asnp 
import sklearn.metrics asmetrics
importmatplotlib.pyplotasplt

y = np.array([-3, -1, -2, 1, -1, 1, 2, 1, 3, 4, 3, 5])
yhat = np.array([-2, 1, -1, 0, -1, 1, 2, 2, 3, 3, 3, 5])
x = list(range(len(y)))

plt.scatter(x, y, color="blue", label="original")
plt.plot(x, yhat, color="red", label="predicted")
plt.legend()
plt.show()

\# calculate manually
d = y - yhat
mse_f = np.mean(d\**2)
mae_f = np.mean(abs(d))
rmse_f = np.sqrt(mse_f)
r2_f = 1-(sum(d\**2)/sum((y-np.mean(y))\**2))

print("Results by manual calculation:")
print("MAE:",mae_f)
print("MSE:", mse_f)
print("RMSE:", rmse_f)
print("R-Squared:", r2_f)

mae = metrics.mean_absolute_error(y, yhat)
mse = metrics.mean_squared_error(y, yhat)
rmse = np.sqrt(mse) \#mse**(0.5)  
r2 = metrics.r2_score(y,yhat)

print("Results of sklearn.metrics:")
print("MAE:",mae)
print("MSE:", mse)
print("RMSE:", rmse)
print("R-Squared:", r2)
</pre>