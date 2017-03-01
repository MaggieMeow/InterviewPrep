# Machine Learning

I summarised these notes from the Udacity Machine Learning Nanodegree course and various online articles. Enjoy!

## Deep Learning

**Logistic classifier**: wx+b=ywx+b=y, w is weight, x is input, b is bias.
Logistic regression: A regression model where the dependent variable (DV) is categorical. This article covers the case of a binary dependent variable

**Softmax**: S(yi)=eyi∑jeyjS(yi)=eyi∑jeyj turn scores into probabilities.
Softmax regression (or multinomial logistic regression) is a generalization of logistic regression to the case where we want to handle multiple classes. Multi-class classification (as opposed to only binary classification).

- If multiply the scores by 10, the probabilities get close to either 0 or 1.
- If divided by 10, the probabilities get close to uniform.

**Cross-entropy**: D(S,L)=−∑iLilog(Si)D(S,L)=−∑iLilog(Si), S is socre, L is lable.

Multinomial logistic classification:linear model wx+bwx+b -> logit score -> softmax S(y) -> Cross-entropy D(S,L) -> 1-hot labels.

**Loss** = average cross-entropy: 1N∑iD(S(wxi+b),Li)1N∑iD(S(wxi+b),Li).

Minimize traning loss using **gradient descent method**.

**Ordinary gradient descent** is a simple algorithm in which we repeatedly make small steps downward on an error surface defined by a loss function of some parameters.

Input is typically normalized, weights are typically initilized with random values from Gaussian distribution.

**Stochastic gradient descent (SGD**) works according to the same principles as ordinary gradient descent, but proceeds more quickly by estimating the gradient from just a few examples at a time instead of the entire training set.

Two methods to help SGD faster:

- **Momentum**: for SGD, each step we take a very small step in a random direction, but on aggregate, those steps take us toward the minimum of the loss. We can take advantage of the knowledge that we’ve accumulated from previous steps about where we should be headed. A cheap way to do that is to keep a running average of the gradients, and to use that running average instead of the direction of the current batch of the data. M <- 0.9M + ΔαΔα.
- **Learning rate decay**: when replacing gradient descent with SGD, we are going to take smaller, noiser steps towards our objective. It is hard to decide how smaller that step should be. However, it is beneficial to make that step smaller and smaller as you train.


### Convolutional Neural Network

#### Convolutional layer
The primary purpose of Convolution in case of a ConvNet is to extract features from the input image. Convolution preserves the spatial relationship between pixels by learning image features using small squares of input data.

Slide the kernel matrix over the image matrix by n pixels (also called ‘stride’) and for every position, we compute element wise multiplication (between the two matrices) and add the multiplication outputs to get the final integer which forms a single element of the output matrix.

The Convolution operation captures **the local dependancies** in the original image. CNN learns the values of these filters/kernels on its own during the training process (although we still need to specify parameters such as number of filters, filter size, architecture of the network etc. before the training process). The more number of filters we have, the more image features get extracted and the better our network becomes at recognizing patterns in unseen images.

The size of the Feature Map (Convolved Feature) is controlled by three parameters: depth, stride and padding.

#### ReLU
ReLU is an element wise operation (applied per pixel) and replaces all negative pixel values in the feature map by zero. Convolution is a linear operation – element wise matrix multiplication and addition, so we account for non-linearity by introducing a non-linear function like ReLU.


#### Fully connected
A traditional Multi-Layer Perceptron that uses a softmax activation function in the output layer.

“Fully connect” all the hidden units to all the input units.

Adding a fully-connected layer is also a (usually) cheap way of learning non-linear combinations of these features. Most of the features from convolutional and pooling layers may be good for the classification task, but combinations of those features might be even better.

For output layer:
The purpose of the Fully Connected layer is to use these features for classifying the input image into various classes based on the training dataset.

#### Locally connected
Restrict the connections between the hidden units and the input units, allowing each hidden unit to connect to only a small subset of the input units. Specifically, each hidden unit will connect to only a small contiguous region of pixels in the input.

#### Pooling
Spatial Pooling (also called subsampling or downsampling) **reduces the dimensionality of each feature map** but retains the most important information. Spatial Pooling can be of different types: Max, Average, Sum etc. The output from the convolutional and pooling layers represent high-level features of the input image.

Advantages:
- Makes the input representations (feature dimension) smaller and **more manageable**
- reduces the number of parameters and computations in the network, therefore, **controlling overfitting**
- makes the network **invariant to small transformations, distortions and translations** in the input image.
- helps us arrive at an almost **scale invariant representation of our image** (the exact term is “equivariant”). This is very powerful since we can detect objects in an image no matter where they are located .

####  Training using Backpropagation
Use backpropagation to calculate the gradients of the error with respect to all weights in the network and use gradient descent to update all filter values / weights and parameter values to minimize the output error.
The weights are adjusted in proportion to their contribution to the total error.


#### Regularisation

Regularization of an estimator works by trading increased bias for reduced variance. An effective regularizer is one that makes a proﬁtable trade, reducing variance significantly while not overly increasing the bias.

**Dropout** is a technique where randomly selected neurons are ignored during training. This means that their contribution to the activation of downstream neurons is temporally removed on the forward pass and any weight updates are not applied to the neuron on the backward pass.

As a neural network learns, neuron weights settle into their context within the network. Weights of neurons are tuned for specific features providing some specialization. Neighboring neurons become to rely on this specialization, which if taken too far can result in a fragile model too specialized to the training data. This reliant on context for a neuron during training is referred to complex co-adaptations.

#### Flatten
The Flatten layer is a utility layer that flattens an input of shape n * c * h * w to a simple vector output of shape n * (c*h*w), so as to consider each pixel as a separate input feature and facilitate the fully connected layer.

## Reinforcement learning

### Markov Decision Process


## Unsupervised learning

## Supervised Learning

## Model Evaluation and Validation

#### Accuracy
Accuracy = (no. of items in a class labelled correctly / all items in that class)

Shortcomings:
Not ideal for skewed cases 
May want to err on side of guessing innocent 
Asymmetries favouring different types of error.

#### F1 Score
F1 score can be interpreted as a weighted average of the precision and recall, where an F1 score reaches its best value at 1 and worst score at 0.

F2 measure, which weighs recall higher than precision (by placing more emphasis on false negatives), and the F0.5 measure, which weighs recall lower than precision (by attenuating the influence of false negatives).

Recall = TP/(TP + FN)
Precision = TP/(TP + FP)

#### Feature transformation
**Principal component analysis (PCA**) is a statistical procedure that uses an orthogonal transformation to convert a set of observations of possibly correlated variables into a set of values of linearly uncorrelated variables called principal components.

Feature transform e.g. PCA fit then PCA transform.
PCA fit on training features
PCA transform on training features
PCA transform on test features (usually after training SVC) -> Represent test data with principle components found in training data.

#### Cross-Validation for Parameter Tuning
**GridSearchCV**
Systematically works through multiple combinations of parameter tunes, cross-validating as it goes to determine which tune gives the best performance.

#### Error 
Two main causes of error: Bias and Variance

**Bias** due to a model being unable to represent the complexity of the underlying data.
Accuracy and Underfitting Bias occurs when a model has enough data but is not complex enough to capture the underlying relationships. As a result, the model consistently and systematically misrepresents the data, leading to low accuracy in prediction. This is known as underfitting.


**Variance** due to a model being overly sensitive to the limited data it has been trained on.
Precision and Overfitting When training a model, we typically use a limited number of samples from a larger population. If we repeatedly train a model with randomly selected subsets of data, we would expect its predictons to be different based on the specific examples given to it. Here variance is a measure of how much the predictions vary for any given test sample.

few features used (if you have access to lots more) -> high bias.
Carefully minimised SSE (sum of squares due to error), used lots of features, tuned parameters -> High variance

#### Ideal learning curve
The ultimate goal for a model is one that has good performance that generalizes well to unseen data. In this case, both the testing and training curves converge at similar values.
The smaller the gap between the training and testing sets, the better our model generalizes.

#### Curse of Dimensionality
As the number of features or dimensions grows, the amount of data we need to generalise accurately grows exponentially.


## Auxiliary

Noise Reduction

gaussian discrimination

edge kernel 
gaussian kernel
average kernel

cross correlation






