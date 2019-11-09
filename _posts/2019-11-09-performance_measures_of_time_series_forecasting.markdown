---
layout: post
title:      "Performance Measures of Time Series Forecasting"
date:       2019-11-09 14:45:55 -0500
permalink:  performance_measures_of_time_series_forecasting
---


Time series forecasting is a way to predict future behavior of the data we currently have. Time series models provides different ways of handling the prediction based  on the patterns of the data. However, there is only one way of knowing how accurate these predictions would be. It is comparing the predicted data with the real data. 

![](https://dr5dymrsxhdzh.cloudfront.net/blog/images/a9c500b24/2019/10/investment-theme-stockmarket-and-finance-business-analysis-with-picture-id1127753940.jpg)

Using some part of the data for training the model and saving another part, usually much smaller one, is general practice in time series forecasting. Although, there are many different ways of choosing the train-test pieces, at the end of the prediction, it is always the predicted data and test data to be compared as the accuracy measure. It is imperative to not to use the testing data in the training to get correct result.
There are a few measures to obtain from comparison of predicted and expected (real) data. Those are;

-	Residual Forecasted Error 
-	Mean Forecast Error (or Forecast Bias)
-	Mean Absolute Error (MAE)
-	Mean Squared Error (MSE)
-	Root Mean Squared Error (RMSE)

### **Residual Forecast Error (RFE)**
Residual Forecast Error is the difference between the forecasted data and the actaul data for the same time stamp in the dataset. For each data point in the test set, it is sum of the real value minus the predicted value. It could be positive or negative for different points. This might be tricky because a very large positive mistake can be cancelled out by another large negative mistake. When add them up the number we get is the Residual Forecast Error. Since the unit is the same with the values in the dataset, we may draw conclusion easily. If the number is close or equal to “0”, that indicates the model’s predictions are very accurate. 

### Mean Forecast Error (or Forecast Bias)
Residual Forecast Error is the sum of Forecast Errors. The average of the forecast errors is the Mean Forecast Error (MFE). So for the n size of the test data, the formula is RFE / n. It can be a positive or a negative value. If it is positive, it means, the model tends to over forecast and it is called positive error. If it is negative, that means the model tends to under forecasts and it is called negative error. This number is also called as Forecast Bias. A close number to zero suggests that model is unbiased. 

### Mean Absolute Error (MAE)
For Mean Absolute Error, all errors (negative or positive) count as positive. This gives a real picture of total errors since they do not cancell each other out.  The average of absolute value of errors gives as Mean Absolute Error.

### Mean Squared Error (MSE)
The Mean Squared Error is the average squared forecas errors. The reaoson to square the errors is to enphesize the large error values.  So it punished the models that have large wrong predictions.  The performense show worse with this measure. 

### Root Mean Squared Error (RMSE)
Last but not least, the Root Mean Squared Error is calculated by taking the square root of Mean Squared Error.  This operation brings the unit back to same with the normal and we can get better intuition of the accuracy of the model. Zero is the best and as it gets bigger the accuracy gets lover.  


Let us see all of these measeure calculations in a real example. 

![](https://raw.githubusercontent.com/fcamuz/dsc-sarima-models-lab-online-ds-sp-000/master/pic1.png  ) 
![](https://raw.githubusercontent.com/fcamuz/dsc-sarima-models-lab-online-ds-sp-000/master/pic2.png  ) 
![](https://raw.githubusercontent.com/fcamuz/dsc-sarima-models-lab-online-ds-sp-000/master/pic3.png  ) 
![](https://raw.githubusercontent.com/fcamuz/dsc-sarima-models-lab-online-ds-sp-000/master/pic4.png  ) 
