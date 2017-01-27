---
layout: post
title: [DL Book Series - Post III] Information Theory
---

#### [Information theory](http://www.deeplearningbook.org/contents/prob.html)

We continue on page 73 of the book. Information theory is used to quantify the amount of information in a given signal. Its use in ML is mainly for characterising, or quantifying similarities between probability distributions. The basic intuition of information theory is that the learning of an improbable event’s occurrence is more informative than learning of a likely event occurring. The authors use this example:

- the sun rose this morning
- there was a solar eclipse this morning

to illustrate that some messages have higher information content. In other words, information content and likelihood of events should be inversely related. The formal definition of this is the “self information”, or I of an event x is: I(x) = - ln P(x), which is expressed in units of ‘nats’ as is the convention with ML. When base-10 log is used instead of ln which is more commonly encountered in other disciplines, the units are referred to as ‘bits' or ‘shannons’, named after the father of Information Theory, Claude E. Shannon, whose [seminal paper](http://worrydream.com/refs/Shannon%20-%20A%20Mathematical%20Theory%20of%20Communication.pdf) more or less created the field.

Self-information only describes the information content of a single event. For an entire probability distribution, we would use the expected value of information from all events drawn from the given distribution, which is called ‘Shannon entropy’, or ‘differential entropy’ when the events denoted by the variable ‘x’ are continuous.

We can also compare the information of two different probability distributions over the same random variable x, by using an equation called the Kullback-Leibler (KL) divergence: a KL divergence of zero means the two distributions are identical, and takes on positive values only when they are different.

A closely related measure is the cross-entropy. A couple of [links](http://neuralnetworksanddeeplearning.com/chap3.html#introducing_the_cross-entropy_cost_function) are recommended [here](http://peterroelants.github.io/posts/neural_network_implementation_intermezzo02/) for additional reading. When using cross-entropy as the cost (or loss) function, the larger the error, the faster the neuron will learn. c.f. MSE as a cost function.

Cross-entropy measures 'surprise'. Put in the context of a neural network, a node or 'neuron' is trying to solve for some function that maps an input x to an output y. The best it can do though, is an approximation based on the training data it has seen so far. Supposing that we train it for binary classification, if we denote the neuron's estimated probability that y is 1 as 'a', then '1−a' is the estimated probability that the correct value for y is 0. Cross-entropy then comes into the picture because it measures how "surprised" we are when we learn the true value for y. If the output matches what we expect then we have low cross-entropy, or low 'surprise', and vice versa.

#### Structured probabilistic models, or graphical models

Here I defer once more to the authors' expertise, and let their words speak for themselves:

*“Machine learning algorithms often involve probability distributions over a very large number of random variables. Often, these probability distributions involve direct interactions between relatively few variables. Using a single function to describe the entire joint probability distribution can be very inefficient (both computationally and statistically). Instead of using a single function to represent a probability distribution, we can split a probability distribution into many factors that we multiply together.”*

*“These factorizations can greatly reduce the number of parameters needed to describe the distribution. This means that we can greatly reduce the cost of representing a distribution if we are able to find a factorization into distributions over fewer variables. When we represent the factorization of a probability distribution with a graph, we call it a structured probabilistic model or graphical model. Any set of nodes the are all connected to each other in the graph G is called a clique, denoted as C. The probability distribution of a configuration of random variables in a clique is a product of all the factors associated with each node, then divided by a normalising constant Z for it to sum to 1."*

Let's keep this blogpost short and sweet. The next one on Numerical Computation is going to be hefty!
