# How Decision Trees Work?

Decision Trees work on the principle of the binary split of the data; The splits are decided on the basis of asking questions in a manner that will give us pure leaf nodes.
Pure leaf nodes don't have/or have minimum impurity in them and what remains after the end of the iterations is a well split tree based on the questions asked.


> ## _How do we make the decision of the split?_


Goal is to get the pure leaf nodes.<br>
The model will choose the split that maximises the information gain, our goal is to reach the state of low entropy i.e. as little mixing of labels/data as possible in the leaf node. Entropy should be as low as possible for the leaf nodes.<br>
A binary split is a split that splits the rows into two groups.<br>

We want a score of how good a binary split is and we want it for every variable in the dataset. A decent scoring system can be - A good split is one in which all of the values of the dependent variables on one side are pretty much the same and the values on the other side are the same. So, how to measure how similar things are in a group - standard deviation. For the split, add the standard deviation of the two sides and that will be your score.
And the lower score is better.

We will find the score for all the variables, not only all the variables but also where to split i.e. there would be unique values for each of the variable, we'll try a split for each of the unique value of that variable and will calculate the score.<br>
We'll do this for all the variables and for all the unique values and eventually split the one with the lowest "score".

There is another score called gini, it should keep getting lower as we go to the leaf nodes from the root.
Gini calculates the probability that if you picked 2 rows from a group, then they're from the same category. If they are from the same group, the probability will be 1, and otherwise 0.



<img src="https://i.postimg.cc/hv15JmRr/SCR-20220910-vqp.png" alt="" style="height: 500px; width:600px;"/>
<br>
<br>
Once you have fond the way to split the root node, you have two children nodes. Treat those 2 children nodes as separate datasets and repeat the steps as above to find the best split fot each of them.<br>
Continue this process recursively, until you have reached some stopping criteria.<br>
<br>

*Note* : The splitting criteria is calculated differently for different variables.<br>
- For continuous variables - reduction in variance(similar to the "score" method above)<br>
- For categorical variables - information gain, entropy, gini impurity, chi-sq test.<br>


Random forests are just a lot of trees based on the concept of Bagging.
