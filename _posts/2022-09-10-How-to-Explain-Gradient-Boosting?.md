# How to Explain Gradient Boosting?


## Adaboost
The trees in Adaboost/Normal boosting are built sequentially and each tree boosts the attributes that lead to the misclassifications/errors in the previous tree.

### How?
1. Each data point is assigned a weight in the beginning, usually same weight to say that all data points are equally important to the model(all the weights add upto 1). <br>
2. After assigning the weight, a small tree is created, these small trees are called stumps.<br>
3. After the first weak learner/model, one finds which data points were misclassified and the
weights of the misclassified data points are increased/changed to tell the next model that these data points are more important than the other ones.(Also, because the sum of weights need to be 1, and we have increased weight of a few data points, to make the things consistent, we need to decrease the weights of the other data points - Noramlise).<br>
4. A second weak learner will try to improve the misclassifications of the previous model and in turn it will have its own misclassifications, we go to step 3 again and adjust the weights for the third weak learner.
5. This goes on until a stopping criteria such as time limit, number of iterations, number of trees etc has reached.

Essentially, these sequential trees help in decreasing the error of the previous misclassifications and the learnings are carried forward as we move though the iterations. <br>
The results of the final model encompass the learnings of all the weak learners.


## Gradient Boosting
Gradient boost has a little difference.<br>
In GBM, learning happens by optimising the loss function(just like how a regression model tries to optimise the sum of squared errors). Too much jargon!

### How?
> #### _Maybe an example might help in this case:_

Distance in miles, time in hours

| Distance  |Time|Speed|
|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |
| 6 m  |2 h   | 3 m/h  |
| 3 m  | 0.5 h  |  6 m/h |

<br>
Let's say we don't know how to calculate speed given the time and distance of a vehicle, so we have to take help of the gradient boosting algo(yeah! because calculators aren't available, can any scenario be more hypothetical than this!!)<br>
As a first step, let's estimate the speed randomly.
<br>

| Distance  |Time|Speed| Estimated Speed|
|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h|
| 6 m  |2 h   | 3 m/h  | 4 m/h|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|

From the estimate, we'll calculate the first set of residual(actual-predicted):

| Distance  |Time|Speed| Estimated Speed| First Residual|
|:---:|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h| 1|
| 6 m  |2 h   | 3 m/h  | 4 m/h|-1|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|2|

Now, as the next step, the GBM will use the first residual as the target i.e. it will use Distance and time columns to predict the first residual. This will be the first residual model. Predicted residual is the column which is the prediction of this residual column.

| Distance  |Time|Speed| Estimated Speed| First Residual|Predicted Residual 1|
|:---:|:---:|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h| 1| 1.5|
| 6 m  |2 h   | 3 m/h  | 4 m/h|-1|-1.2|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|2|2.4|

After this first model, the new estimated speed will be:<br>
``Estimated speed + learning rate  * predicted residual 1`` <br>
If learning rate is 0.1, then new estimate for the first row will be: ``4 + 0.1 * 1.5 = 4.15`` which is a little closer to 5 than 4 is.<br>


| Distance  |Time|Speed| Estimated Speed| First Residual|Predicted Residual 1|New Estimate|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h| 1| 1.5| 4.15|
| 6 m  |2 h   | 3 m/h  | 4 m/h|-1|-1.2| 3.88|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|2|2.4|4.24|

Use the ``New Estimate`` values to calculate second residuals(Speed - New estimate).


| Distance  |Time|Speed| Estimated Speed| First Residual|Predicted Residual 1|New Estimate| Second Residual|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h| 1| 1.5| 4.15|0.75|
| 6 m  |2 h   | 3 m/h  | 4 m/h|-1|-1.2| 3.88|-0.88|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|2|2.4|4.24|1.76|

As you see, that the second residuals are smaller than the first residual.

Now, for the second residual model, use the second residual as the target and predict a value.


| Distance  |Time|Speed| Estimated Speed| First Residual|Predicted Residual 1|New Estimate| Second Residual|Predicted Residual 2|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h| 1| 1.5| 4.15|0.75| 0.8|
| 6 m  |2 h   | 3 m/h  | 4 m/h|-1|-1.2| 3.88|-0.88| -0.6|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|2|2.4|4.24|1.76| 2|

Again, use the ``New Estimate + learning rate  * predicted residual 2`` to update the estimated Speed, let's call it new estiamte 2.
<br>

| Distance  |Time|Speed| Estimated Speed| First Residual|Predicted Residual 1|New Estimate| Second Residual|Predicted Residual 2| New Estimate 2|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 5 m |1 h   | 5 m/h  |  4 m/h| 1| 1.5| 4.15|0.75| 0.8|4.23|
| 6 m  |2 h   | 3 m/h  | 4 m/h|-1|-1.2| 3.88|-0.88| -0.6|3.82|
| 3 m  | 0.5 h  |  6 m/h |  4 m/h|2|2.4|4.24|1.76| 2|4.44|

Again, find the ``Third Residual`` by subtracting, New estimate 2 from speed and use the third residual as the target that your third residual model will predict.

This will keep going on until a stopping criteria is reached such as number of iterations, depth of a tree, time limit etc

Essentially, in this algorithm, we are boosting the gradient(though the learning param and new residuals calculated at each step) and it is helping in decreasing the overall error.

Also, as we can see that it is an additive model.

``Estmated Speed + learning rate * predicted residual 1 + learning rate * predicted residual 2 + ...``

That's how Gradient Boosting works!!
Quite simple :P
