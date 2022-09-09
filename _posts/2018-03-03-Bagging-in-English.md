# What is Bagging?

This is a simple explanatory note to myself on how boosting works without use of much Mathematics.
<br>
There are times when the model make a _not so decent_ prediction and have errors in the results. To mend this, Leo Brieman came up with
the idea of **Bagging**.
<br>

> #### _Basic idea_
![](https://blog.paperspace.com/content/images/2019/11/image-66.png)

Let's say, we have a model that's not very good and has many errors in the predictions. It's not a systematically biased error, it's not
always predicting too high or too low, the models generally predict the average, a few high values, a few low values. <br>
One can build a different model, with different parameters and that model will have its own errors; and one can keep building many such different models.
All these models are unbiased i.e. don't really predict one value in favour of the other or classify in one category over the others.

> #### _What will happen if we average their predictions?_<br>
Assuming that the models are not correlated with each other, then we will have the errors on either side of the correct prediction,
some are bit high and some are bit low.<br>
There will a distribution of errors.<br>
**The average of those errors will be 0**, this is an important insight. We are taking all the distributions and stacking them on top of each other,
the average of the errors will be 0.<br>
If we add all the predictions together and average them out, they will be centered around the mean value, which in this case will be the correct value.
<br>
In nutshell, this process helps in reaching us close to the real value and close the gap between the real and the predicted.<br>

> #### _The models need to be unbiased and uncorrelated, and we can average the results, because the average of the error will be 0._
<br>
Bagging is a short form for bootstrap aggregation.
