# Error Metrics

## Root Mean Squared Error (RMSE)

RMSE is the most popular evaluation metric used in regression problems. It follows an assumption that errors are unbiased and follow a normal distribution. Here are the key points to consider on RMSE:

<ol>


<li>The power of ‘square root’ empowers this metric to show large number deviations.</li>
<li>The ‘squared’ nature of this metric helps to deliver more robust results, which prevent canceling the positive and negative error values. In other words, this metric aptly displays the plausible magnitude of the error term.</li>
<li>It avoids the use of absolute error values, which is highly undesirable in mathematical calculations.</li>
<li>When we have more samples, reconstructing the error distribution using RMSE is considered to be more reliable.</li>
<li>RMSE is highly affected by outlier values. Hence, make sure you’ve removed outliers from your data set prior to using this metric.</li>
<li>As compared to mean absolute error, RMSE gives higher weightage and punishes large errors.</li>


</ol>

## R Squared

R is the correlation between the dep and indep vars.
R squared is just the square of R value.

It explains how much variation can the predictors explain about the dependent variable. It is dependent on the data and increases as you add more data.<br>
Also, it increases when you add more predictors even though the predictors don't have any relationship to the dependent variable for example the price of the house and the gender of the person buying it shouldn't be related but adding it to the model will improve the R squared value.
<br>
That's why the concept of Adjusted R squared comes into pciture which penalises such predictors. The formula contains n and p which are number of data points and number of predictors and thus effects of high R squared can be mitigated.
<br>
R squared isn't a notion for accuracy but how much variation in y can be explained by predictors.
<br>
R sq also tells how much less variation is around the fitted line compared to that of the mean line. A high value means there is less variation of the data around that line and it is a better line compared to the mean line.
<br>


## Precision and Recall

Accuracy can be defined as correct identified items/ total items.
<br>
Apple and Orange classifier. If 7 correctly identified out of 10 then 70% accuracy but accuracy suffers from problem of imbalanced classes. 
If 990 oranges and 10 apples, then almost everything will be classified as an orange and we will still call the model to be 99% accurate.
<br>

Precision for apple,  Out of all that were classified as apple, total apples in the classifcation bucket/ total items classified as apples
3/5 = 60%
<br>
Recall for apple, correctly classified apples/ total apples in the system.
3/4 = 75%
<br>

Precision can be seen as a measure of quality, and recall as a measure of quantity. Higher precision means that an algorithm returns more relevant results than irrelevant ones, and high recall means that an algorithm returns most of the relevant results (whether or not irrelevant ones are also returned).Precision can be seen as a measure of quality, and recall as a measure of quantity. Higher precision means that an algorithm returns more relevant results than irrelevant ones, and high recall means that an algorithm returns most of the relevant results (whether or not irrelevant ones are also returned).

<br>

Both precision and recall should be balanced. Not one at the cost of the other.
<br>

F1 score is Harmonic mean between precision and recall. It is a system that incorporates both precision and recall.

## ROC AUC
Receiver Operating Characteristics and Area under the curve

<br>
ROC curve is a curve between TPR and FPR
<br>
PR curve is between precision and recall

<br>
Area under the curve can be calculated by measuring either of the 2 curves PR or ROC. It will be a number, the higher the better.

<br>

## Mean Absolute Error(MAE)

Mean Absolute Error is the average of the difference between the Original Values and the Predicted Values. It gives us the measure of how far the predictions were from the actual output. However, they don’t gives us any idea of the direction of the error i.e. whether we are under predicting the data or over predicting the data. We take the absolute value of the errors to mitigate the negative signs from cancelling the positive values.

<br>
convergence takes a long time because gradient descent can't be used easily. Not a parabola but straight line. Uses sub gradient concept.

## Mean Squared Error(MSE)

Mean Squared Error(MSE) is quite similar to Mean Absolute Error, the only difference being that MSE takes the average of the square of the difference between the original values and the predicted values. The advantage of MSE being that it is easier to compute the gradient, whereas Mean Absolute Error requires complicated linear programming tools to compute the gradient. As, we take square of the error, the effect of larger errors become more pronounced then smaller error, hence the model can now focus more on the larger errors.

It has one local and global minima and thus it won't be stuck in only local minima like many other curves.

It is not robust to outliers though as it will try to take the outliers into account and thus too much error.
Second issue is MSE is changes the unit as the unit gets squared e.g. if measuring error in salary, MSE will measure it in dollar squared.

## RMSE

It is sq root of MSE. The units are retained.
RMSE removes the bias towards only higher value error terms in the MSE.


# Errors in forecasting


![image](https://github.com/Prashantmdgl9/ml_experiments/assets/8743929/edd60ec4-f38d-46e6-91f6-20dfbb2dbd1d)

## MAPE

Scale dependent metrics such as MAR, RMSE, MSE are not suitable for comparing different time series.
<br>

Scale-dependent means the error metrics are expressed in the units (i.e. Dollars, Inches, etc.) of the underlying data.
<br>

The main advantage of scale dependent metrics is that they are usually easy to calculate and interpret. However, they can not be used to compare different series, because of their scale dependency
<br>

Percentage Error Metrics solve this problem. They are scale independent and used to compare forecast performance between different time series. However, their weak spots are zero values in a time series. Then they become infinite or undefined which makes them not interpretable.
<br>

MAPE’s advantages are it’s scale-independency and easy interpretability. As said at the beginning, percentage error metrics can be used to compare the outcome of multiple time series models with different scales.
<br>

However, MAPE also comes with some disadvantages. First, it generates infinite or undefined values for zero or close-to-zero actual values

Second, it also puts a heavier penalty on negative than on positive errors which leads to an asymmetry (Hyndman 2014).
<br>

And last but not least, MAPE can not be used when using percentages make no sense. This is for example the case when measuring temperatures. The units Fahrenheit or Celsius scales have relatively arbitrary zero points, and it makes no sense to talk about percentages.

<br>















  


