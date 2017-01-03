---
layout: post
title: Deep Learning Book read along - 7
---

Third part of the chapter on [Machine Learning basics](http://www.deeplearningbook.org/contents/ml.html).

### Supervised learning algorithms

This section is intentionally kept short as I presume that you, the reader, already have a good foundation in ML before embarking on this discovery of DL. The algorithms below are good to know as background knowledge, and certainly are very valuable in real life situations for any ML practitioner, but they are not too relevant to the story of DL that is being told here.

#### Probabilistic supervised learning

Support Vector Machines: the kernel trick allows its optimisation to be more computationally efficient, however the cost is still high when the dataset is large. DL was in part designed to overcome this limitation.
k Nearest Neighbours
Decision trees

#### Unsupervised learning algorithms

Below are several ways unsupervised ML can be used to find some representation of a given dataset:

- lower dimensional representations
- sparse representations; typically requires an increase in dimensionality in exchange for transforming the data into a representation of mostly zeroes
- independent representations; seeks to disentangle the sources of variation into components that are statistically independent

These three types of representation are not mutually exclusive.

#### Principal Components Analysis

PCA is a technique where data is compressed into a representation with lower dimensionality via a learned orthogonal, linear transformation that disentangles the unknown factors of variation. This is useful only if the data is a multivariate normal distribution, and that the variance contains key information relevant to the problem. The intuition is of rotating the ‘mind’s eye’ or ‘camera’ in the input space to maximise the variance along the the axes of the newly transformed space.

#### Stochastic Gradient Descent

SGD is an extension of the gradient descent algorithm. Its use is borne out of the fact that training on large data sets are very computationally expensive. So instead of training on all samples, we use mini batches that are drawn uniformly from the training set.

#### Building a ML algorithm

Stated simply, almost all DL algorithms are combinations of the following:

- a dataset
- a cost function: frequently containing a negative log-likelihood term, and a regularisation term. Some can be solved analytically, for others an iterative numerical approach is needed, e.g. SGD. Special case optimisers are used for ML models such as decision trees and k-means because their cost functions have flat regions.
- an optimisation procedure
- a model

### Challenges to ML that motivated DL’s development

#### The Curse of Dimensionality
In short, way more features than data points. Unless many more training samples can be found to train with, many traditional ML algorithms perform poorly in this situation.

#### Local Constancy and Smoothness Regularisation
We pick up from the earlier sections on Bayesian methods, priors, and the No Free Lunch theorem. In order for a ML algorithm to work well, it needs prior assumptions built into the model that make it fit a better estimator for the task at hand. These assumptions may be implicitly or explicitly stated, some might not even be readily formulated in mathematical form. One of the most commonly used implicit priors is the smoothness prior, or local constancy prior. Concretely, it assumes that the value of a cost function does not change much for a small change in x (a small learning step in gradient descent). The mental picture is that of a smooth landscape with no sudden bumps or valleys.

However, there is a problem when we our problem space consists of more distinct regions than there are data points. ML algorithms that assume the smoothness prior would not be able to make accurate predictions for those regions that do not have a data point in the training data set. The authors provide an excellent mental picture of a chessboard. For a training data set that gives board position x,y and what colour it is (black/white), models that rely only on the local constancy prior would fail to predict the colour of points in certain regions if they were not given that data point to train on in the first place.

A further complication ties in with higher dimensionality. As the number of dimensions increase, even smooth functions may not be easily described without a very large training set, because the gradients would slope differently in each dimension.

With the above two cases in mind, the authors reassure us that as long as additional assumptions are made about the underlying data generating distribution, our models should be able to fit the data accurately enough. This is where DL comes in; because we make the additional assumption that our data is generating by the composition of features at multiple levels in a hierarchy, exponential gains in the number of regions distinguishable by the model can be had from an increase in the number of training samples. Recall in the first blogpost the [paper regarding “the exceptional simplicity of physics-based functions”](https://arxiv.org/abs/1608.08225), then we can see how the use of deep, distributed representations distinctive to DL networks can tackle problems of high dimensionality in the real world that most other ML algorithms cannot.

#### Manifold Learning

Here are [several](https://www.quora.com/What-is-manifold-learning-in-laymans-term) [good](http://colah.github.io/posts/2014-03-NN-Manifolds-Topology/) [links](https://prateekvjoshi.com/2014/06/21/what-is-manifold-learning/) for reference. I will attempt to explain this intuitively and without going too deep into the mathematics. A key insight is that manifold learning algorithms reduce the dimensionality of data much as Principal Components Analysis does, but instead of projecting onto orthogonal sets of axes we use manifolds, which you can picture as a sheet of cloth that can be twisted into any shape, and even intersect itself.

Why is this significant? Because if we think the manifold hypothesis is valid, then similar data should lie clustered closely along some low-dimensional space. Hence, instead of having a traverse the entire space of possible solutions, we should be able to find very high probability regions on some manifold for the same type of data, e.g. images of human faces. It makes intuitive sense: within the space of all possible images, the set containing human faces must occupy an exceedingly small volume of an infinite space. If we were able to learn the manifold that all human face images lie on, then we can make face detection and generation much easier by having our model focus on just that region of high probability. There is evidence supporting this hypothesis, at least for such areas of AI research interest as Computer Vision, Speech Recognition and Natural Language Processing, and it is no coincidence that DL has been ‘unreasonably effective’ in solving these problems compared to traditional ML algorithms.  Recall from the first of this series of blogposts that a key strength of DL is its ability to learn representations - manifold learning is proof positive of that.

This ends the reading of Chapter 5 on Machine Learning Basics, and the end of Part I of the Deep Learning book. Stay tuned for more as we head into Part II: “Deep Networks: Modern Practices”.
