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

