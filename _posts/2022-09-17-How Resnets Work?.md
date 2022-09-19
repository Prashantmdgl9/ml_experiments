# How Resnets work?

One can think that if one would keep on increasing the depth of a neural network, one can keep on achieving higher accuracy but that's not the case as we have seen in the paper by Kaiming He et al. 

Link to the paper - https://arxiv.org/pdf/1512.03385.pdf

As we see in the first image itself, the training error for the deep network with 56 layers is worse than the training error with 20 layers. 

[![SCR-20220919-ubn.png](https://i.postimg.cc/nzYd4nGM/SCR-20220919-ubn.png)](https://postimg.cc/r0sCcXbL)

The reason behind this stalling of the training of the neural network as we go deeper is the problem of the vanishng gradient.
During the backpropagation, the model has to adjust the weights and those adjustments are calculated accordin to the chain rule of derivatives. For many of the weights, these values come out as less than 1.<br>

Also, these values are multiplied by a earning rate whose value is 0.1 > learning_rate > 0.0001, essentially a much smaller number. When we multiply more and more numbers that are less than 1, we get more small numbers and thus the weights of the earlier layers don't get adjusted at all during the backpropagation.<br>

For earlier layers, the chain rule will contain many more terms than the later layers and thus the earlier layers' weight adjustement will consist of more multiplications which will result in a tiny number and according to:<br>

`` new_weight = old_weight - learning_rate * result of chain rule``

### How Resnets help?

Resents are short for residual network and they contain a special block called the skip connection block after each convolution. <br>


This skip connected block helps in avoiding the issue of vanishing gradient and the model is able to train not only faster but also with much greater accuracy.

We can see the loss surface of the two networks, one with the skip connection and the other without.

Goldstein, Xu, Li et all did some really great work for this paper of theirs in which they visualise the loss landscape of the neural networks.

Link to the paper - https://arxiv.org/pdf/1712.09913.pdf


[![SCR-20220919-uty.png](https://i.postimg.cc/QdJqCjhM/SCR-20220919-uty.png)](https://postimg.cc/213WXRqp)

In a normal convolution network, the layers are stacked on top of one another, while in Resnet, apart from the stacking, there is a skip connection that goes from the input to the output.

[![SCR-20220919-ucq.png](https://i.postimg.cc/8CvXCRFR/SCR-20220919-ucq.png)](https://postimg.cc/KKZDqgDj)


We have added the original input to the output of the convolution block via the skip connection, this will help during the backpropagation calculus and the partial derivative won't reach a very small value and thus avoiding the issue of the vanishing gradient.


[![SCR-20220919-vzq.png](https://i.postimg.cc/xCMnHj7F/SCR-20220919-vzq.png)](https://postimg.cc/jwxpYTRz)

X is the input, f(X) is the output of the small network block and we have added the skip connection, so, at the adder, the value is f(X) + X.

If we can make f(X) = 0, then the output will at the adder will be Y = X, which is what we want = No error from the system and input gets recognised as the output(if not 0 then make f(X) as small as possible)


**Note** The first layer of the Resnet arch has stride 2 convolution. The vernacular 1x1 conv, 64 means filter size of 1x1  and 64 such filters; 3x3, 128 means 3x3 sized filter and 128 such filters.


