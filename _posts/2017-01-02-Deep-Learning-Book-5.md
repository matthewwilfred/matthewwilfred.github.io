---
layout: post
title: DL Book Series Part V: More Machine Learning
---

#### [ML Basics](http://www.deeplearningbook.org/contents/ml.html)

A fair amount in this chapter covers the fundamentals of ML which will not all be repeated here. For those who are unfamiliar with the subject, the [Coursera module on ML delivered by Andrew Ng](https://www.coursera.org/learn/machine-learning) is highly recommended, though I personally would not spend too much time on the Octave exercises unless you were already familiar with MATLAB. I would suggest going through the video lectures to gain a high level understanding first, then do the implementations if so inclined. [Introduction to Statistical Learning](http://www-bcf.usc.edu/~gareth/ISL/ISLR%20Sixth%20Printing.pdf) is another great resource for beginners, with worked examples in the preferred programming language of many statisticians, R.

Examples of ML tasks are:

- Classification (with/without missing inputs)
- Regression
- Transcription (eg.captioning/speech recognition)
- Machine translation
- Structured output (vector output, eg. word2vec)
- Anomaly detection
- Synthesis and sampling (of datapoints)
- Missing value Imputation
- Denoising (generating clean example from corrupted exampled resulting from an unknown corruption process)
- Density estimation, or probability mass function estimation: the ML algorithm learns the structure of the seen data and explicitly capture the structure of the probability distribution

Although ML can be broadly divided into supervised and unsupervised tasks, there are cases where they are blurred. There are cases where unsupervised ML problems can be formulated as a supervised one, and vice versa; furthermore other paradigms such as semi-supervised and reinforcement learning are under active research.

As is no doubt of great familiarity to all data scientists and ML practitioners, DataFrames are used all the time, which in the book we learn can also be called a design matrix. As is sometimes the case with heterogeneous data, it is not always the case that everything can be neatly fitted into an m x n row by column structure; in other words not all data points can be cast into equal length vectors. To give a brief glimpse into some material covered further ahead in the book, neural network architectures such as Convolutional networks or Recurrent networks deal with this problem.

Typically, a set of assumptions called i.i.d. assumptions are made about the training and test samples of a dataset, which is to say that they are:

- Independent; each data point is independent of each other
- Identically distributed; all data points are drawn from the same probability distribution

No word so far on the book on what happens if these assumptions do not hold true.

#### Capacity and model fitting

Some semantics relating to over/underfitting which bear noting are introduced in the book. The representational capacity of a model is the "family of functions the learning algorithm can choose from when varying the parameters in order to reduce a training objective.” However, imperfections of the optimisation algorithm mean that its effective capacity may be less than that. If the capacity is too high for the dataset in question, the model may be prone to overfitting, and vice versa.

Model capacity can be quantified with the Vapnik-Chervonenkis (VC) dimension, which measures the capacity of a binary classifier. However, these types of measures are of limited utility for DL models because the theory behind their optimisation is at this point in time not very well developed.

*"In statistical classification, Bayes error rate is the lowest possible error rate for any classifier of a random outcome (into, for example, one of two categories) and is analogous to the irreducible error."*

*"Any fixed parametric model with less than optimal capacity will asymptote to an error value that exceeds the Bayes error.  Note that it is possible for the model to have optimal capacity and yet still have a large gap between training and generalization error. In this situation, we may be able to reduce this gap by gathering more training examples.”*

kNN (regression or classification) is an example of a non-parametric ML model.

#### The No Free Lunch Theorem
The theorem states that:

*"When averaged over all possible data generating distributions, every classification algorithm has the same error rate when classifying previously unobserved points… No machine learning algorithm is universally any better than the other.”*

Luckily, the probability distributions that we deal with in real life is merely a subset of all possible kinds of data generating distributions, thus we can make meaningful assumptions about them and have our ML algorithms perform well on the specific tasks we design them for.

#### Regularisation
An appropriate degree of regularisation (with suitable hyperparameter tuning) allows us to use a model with sufficient effective capacity while minimising the chances of overfitting. Weight decay is a means of implementing that, by modifying the cost function to include a term that forces the weights to become smaller at each iteration, unless said weight significantly reduces the error; but it is not the only regulariser that can be applied to cost functions. The goal of all regularisation is to reduce generalisation error, but not training error, of a ML model.

Here too the No Free Lunch theorem applies: no regulariser is universally better than any other. It is up to the ML practitioner to choose which one to apply as befitting the problem at hand. Fortunately, a wide variety of regularisers are applicable and effective in DL.
