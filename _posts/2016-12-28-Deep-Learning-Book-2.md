---
layout: post
title: Machine Learning Basics
---

We now dive into Part I of the book: _Applied Math and Machine Learning Basics_.

*"Mathematics is the art of giving the same name to different things."*
Henri Poincare

For a summary of the mathematical notation used throughout this book, refer to [this page](http://www.deeplearningbook.org/contents/notation.html). It may be tough going for someone who is unfamiliar with the diverse areas of mathematics touched upon in this book, so wherever possible I have tried to link external resources for extra learning, such as this [cheat sheet on Hacker Moon](https://hackernoon.com/deep-learning-cheat-sheet-25421411e460#.hroesyk2j) that summarises a number of frequently encountered mathematical terms.

#### [Linear Algebra](http://www.deeplearningbook.org/contents/linear_algebra.html)
This section introduces the mathematical notation for scalars, vectors and matrices. For a refresher on linear algebra, I can recommend the excellent course by MIT Professor Gilbert Strang, the materials for which can be found on [Youtube](https://ocw.mit.edu/courses/mathematics/18-06-linear-algebra-spring-2010/) and [MIT OpenCourseWare](https://www.youtube.com/watch?v=ZK3O402wf1c). A shortened guide that explains the topic in the vein of Prof Strang can be found [here](https://betterexplained.com/articles/linear-algebra-guide/) as well. This blogpost doesn't pretend to provide complete coverage of all the concepts needed to proceed further further with the book, rather, it's intended to highlight concepts and terminology that may be less well known outside of Deep Learning. There's also a [cheatsheet](https://minireference.com/static/tutorials/linear_algebra_in_4_pages.pdf) for the time-strapped.

Let's look at the '*less conventional notation*' as applied in DL. In particular, the addition of a matrix A and a vector b is allowed, where C<sub>i,j</sub> = A<sub>i,j</sub> + b<sub>i,j</sub>; the vector b is added to each row of the matrix A. In the words of the authors, "This shorthand eliminates the need to define a matrix with b copied into each row before doing the addition. This implicit copying of b to many locations is called _broadcasting_."

The authors also note that generally for Machine Learning algorithms, there is a need to discriminate between elements that are exactly zero and elements that are small but nonzero; the L1 norm is used when the difference between zero and nonzero elements is very important, because the L1 norm increases by the same quantity as an element of a matrix X moves away from the origin.

#### [Probability theory](http://www.deeplearningbook.org/contents/prob.html)
For this part of my read-along, I've opted to directly report what the authors have to say on the subject as I struggled to reformulate what they teach in a clearer way. Direct quotes are, of course, attributed to the original authors Ian Goodfellow, Yoshua Bengio and Aaron Courville. The focus of selected passages (in italics) is once again on notation while being light on the fundamentals. I personally profited from Khan Academy videos quite a lot when I was revising for exams a few years ago, and is a good source of revision material for those who haven't touched this stuff for a while.

*"The probability mass function maps from a state of a discrete random variable to the probability of that random variable taking on that state. The probability that x = x is denoted as P(x), with a probability of 1 indicating that x = x is certain and a probability of 0 indicating that x = x is impossible. Sometimes to disambiguate which PMF to use, we write the name of the random variable explicitly: P<sub>x = x</sub>. Sometimes we define a variable first, then use ∼ notation to specify which distribution it follows later: x ∼ P(x).”*

*"A probability distribution over discrete variables may be described using a probability mass function (PMF). We typically denote probability mass functions with a capital P. Probability mass functions can act on many variables at the same time. Such a probability distribution over many variables is known as a joint probability distribution. P<sub>x = x, y =y</sub> denotes the probability that x = x and y = y simultaneously. We may also write P(x,y) for brevity.”*

*"When working with continuous random variables, we describe probability distributions using a probability density function (PDF) rather than a probability mass function.”*

*“We often denote that x follows the uniform distribution on [a,b] by writing x ∼ U(a,b). We can do this with a function u(x;a,b), where a and b are the endpoints of the interval, with b > a. The “;” notation means “parametrized by”; we consider x to be the argument of the function, while a and b are parameters that define the function.”*

A note on covariance:

*"It is possible for two variables to be dependent but have zero covariance. For example, suppose we first sample a real number x from a uniform distribution over the interval [−1, 1]. We next sample a random variable s. With probability 0.5, we choose the value of s to be 1. Otherwise, we choose the value of s to be −1. We can then generate a random variable y by assigning y = sx. Clearly, x and y are not independent, because x completely determines the magnitude of y. However, Cov(x, y) = 0.”*

#### Measure theory - continuous variables

*"A proper formal understanding of continuous random variables and probability density functions requires developing probability theory in terms of a branch of mathematics known as measure theory. Measure theory is beyond the scope of this textbook, but we can briefly sketch some of the issues that measure theory is employed to resolve.”*

*“However, it is useful to understand the intuition that a set of measure zero occupies no volume in the space we are measuring. For example, within R<sup>2</sup>, a line has measure zero, while a filled polygon has positive measure. Likewise, an individual point has measure zero. Any union of countably many sets that each have measure zero also has measure zero (so the set of all the rational numbers has measure zero, for instance)."*

#### A list of probability distributions

Some of these will be more familiar to you than others, depending on your background in statistics and/or ML. I have found Wikipedia articles to be sufficiently detailed to provide a good overview; going through them with an emphasis on the graphs to visually depict what each of the distributions below look like is a good approach to follow.

- Bernoulli: binary random variable
- Multinoulli: categorical distribution
- Gaussian: a.k.a. normal distribution, parametrised by mu and covariance, or beta
- Exponential and Laplace (back-to-back exponentials, peak with decay)
- Dirac delta function: infinitely narrow and high single peak (x = mu) and zero elsewhere
- Empirical distribution: can be modelled using Dirac delta function as components, with one Dirac component for each training example
- Mixture distribution: for building complex probability distributions. Gaussian mixtures use gaussian distributions as components

#### Common functions

- Logistic sigmoid [0,1]: used often to produce phi parameter for Bernoulli distributions
- Softplus [0, inf]: used for producing sigma or beta parameter of normal distributions. Comes from ‘softening’ max(0,x) ie. ReLU.
