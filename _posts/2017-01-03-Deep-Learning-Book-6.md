---
layout: post
title: Deep Learning Book read along - 6
---

Second part of the chapter on [Machine Learning basics](http://www.deeplearningbook.org/contents/ml.html).

#### Hyperparameters and Validation Sets

A quick word on hyperparameters: we can be more specific in naming those which control model complexity as capacity hyperparameters. Barring some of the more recent DL papers, we generally do not apply ML on optimising the hyperparameters themselves, as they tend to result in overfitting. Instead, validation sets are used for model selection, which are split from the training data. A train/validation/test split as advocated by Andrew Ng is 6:2:2 . Furthermore, when working with small datasets, cross validation methods (such as k-fold CV) can give better reassurance about a model’s performance by reporting an estimated test error averaged across multiple trials on mutually exclusive subsets.

#### Consistency

Consistency is a desired quality for our estimators:

*"Consistency ensures that the bias induced by the estimator is assured to diminish as the number of data examples grows. In other words, even with biased estimators, the strong form of the condition of consistency means that as the training data size grows, the model’s parameters would almost surely converge to the true value. However, the reverse is not true—asymptotic unbiasedness does not imply consistency.”*

#### Maximum Likelihood Estimation

We can use the Maximum Likelihood Principle to derive functions that are good estimators. A good estimator is one which has a model probability distribution that is similar with the empirical distribution of the training data, which serves as the proxy for the true data generating distribution.

The degree of dissimilarity between two probability distributions (denoted p and q) is measured by the [Kullback-Leibler divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence), also known as discrimination information, information divergence, information gain, or relative entropy, which formally is the relative entropy of p with respect to q. Recall in the earlier blogpost on information theory about how entropy measures 'surprise', if you need a reminder of the intuition. By training the model to minimise KL divergence we optimise for a model to become a better predictor. Minimising cross-entropy means exactly the same thing in this context.

In a ML context, cross entropy is frequently used to define the loss function. The true probability distribution p
is the ground truth of the training set, and the distribution q is the predicted value of the current model.

An aside on the topic of Bayesian statistics: the KL distribution can be used to measure the information gain going from a prior distribution to a posterior distribution.

A note on terminology. In engineering circles, the principle of minimising KL Divergence can be called the Principle of Minimum Cross-Entropy or Minxent. Also, the logistic loss in a logistic regression is sometimes called cross-entropy loss.

Minimising the KL divergence to arrive at an optimal estimator is useful because it has a known minimum value of zero, which is subtly different from MLE, which can yield a negative value for log likelihood.

Maximum likelihood is a preferred estimator in ML because of its two desirable properties:

- Consistency. It can be shown mathematically that the estimator derived through MLE approaches the best estimator for a given dataset as the number of training examples increases, provided that the model has sufficient capacity to reflect the true data generating distribution.
- Statistical efficiency. For a given number of samples, a more efficient estimator may obtain a lower generalisation error than a less efficient one. Stated otherwise, an efficient estimator is able to generalise well using a smaller training dataset than an inefficient one.

#### Bayesian statistics

The previous discussion on MLE leads up nicely to Bayesian statistics, which is a central part to understanding DL and many other ML algorithms. It is however a humongous field to tackle, and though the book gives a nicely condensed summary of its main points, I would suggest devoting more time to its study before proceeding further. The book [Bayesian Methods for Hackers](https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers) is an excellent, hands-on approach to learning the topic with an emphasis on implementation in Python.

In contrast with the usual frequentist approach that is taught in schools, Bayesian statistics differs in a key aspect where it uses a prior probability distribution, which represents our knowledge of the world. Through observing incoming new information, we constantly update our worldview to form a posterior distribution, which also reflects how certain we are of its predictions. Another key difference is that, instead of making all predictions based on one purported ‘best’ estimator, we take the predictions from all possible estimators, and set some confidence interval within which a most likely prediction lies, the certainty of which grows as the number of training samples increases. These differences tend to make Bayesian methods generalise better when the training data size is small, at the cost of requiring more computational resources.
