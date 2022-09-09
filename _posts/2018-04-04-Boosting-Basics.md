# Boosting

Boosting in another ensembling method of creating a strong learner from various weak learners.
<br>
> ### _Basic idea_

It is a sequential method in which the learners are created in a sequential manner and the errors/misclassifications from the previous model/learner
are given a higher weight to be included in sample that will be selected for training the next learner/model.<br>
This goes on till a condition is met such as batch size or the time reached.<br>

![](https://miro.medium.com/max/1088/1*m2UHkzWWJ0kfQyL5tBFNsQ.png)

- In the above diagram, Box 1 is the first learner, the task is to separate the positives and the negatives. The vertical line D1 is called the decision stump and is drawn to separate the data in two parts. The left side has correct classification but the right side has 3 positive points which are the errors/residuals.
- In the next learner, Box 2, the previously misclassified points are given higher weightage and keeping that in mind, a new decision stump is created.
- The Box 3 takes care of the errors in previous misclassifcations.
- In the last step, all 3 learners combine to give Box 4 which is the final classification of the data points.

> ### _Algorithm_

1. Create a small model(a weak learner e.g. a tree that's not large enough) and get the predictions.
2. Calculate the residuals, fancy name for error. Target - Prediction for each point in dataset.
3. Train another model but instead of using original target use the residual calculated in step 2 as the target for training the model.
5. Continue till you reach a stopping criteria.
<br>

> ### _Why Boosting works?_

Each new model will be attempting to fit the error of all of the previous models combined. As we are continuoously creating new residuals, by subtracting the predictions of each new model from the residuals from the previous model, the residuals will get smaller and smaller and thus prediction will get stronger.
<br>
To make predictions with an ensemble of boosted trees, we calculate the predictions from each tree, and then add them all together. Also, Boosting unlike Bagging can overfit a lot. Bagging doesn't overfit because trees aren't correlated while in Boosting, one model is dependent on all the previous ones.
