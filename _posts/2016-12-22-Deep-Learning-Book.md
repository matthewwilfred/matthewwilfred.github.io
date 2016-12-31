---
layout: post
title: Deep Learning Book read along - 1
---

#### [Available for free at deeplearningbook.org](http://www.deeplearningbook.org/)

I've decided to read through this recently released book on Deep Learning by Ian Goodfellow, Yoshua Bengio and Aaron Courville. As a means of tracking my own progress, I'll be using this blog to note down what I've read and put out links to related articles, so I'd view it as a personal, but shared sketchpad. If you like what you're reading, think about buying a copy to support the authors! It seems well on its way to becoming a classic.

Without further ado, the read-along starting with [Chapter One](http://www.deeplearningbook.org/contents/intro.html):

#### What is Deep Learning?

As a domain of machine learning, DL differs from the previous knowledge-based approaches to AI, which hard code human knowledge into algorithms. Instead, patterns are extracted from raw data and learned by the algorithm itself. This is true of all ML algorithms.

DL is a subset of machine learning where computers, through learning from experience, understands the world as a hierarchy of concepts, that if shown diagrammatically would be a deep graph with many layers reaching all the way down to the simplest concepts. This is a powerful approach, because the physical world itself is similarly organised, with complex phenomena emerging from the interaction of relatively simple interactions, which was referred to as “the exceptional simplicity of physics-based functions” in [this paper](https://arxiv.org/abs/1608.08225).

The ability of ML algorithms to learn features depends heavily on how it is represented. In Figure 1.1, the book uses the example of Cartesian and Polar coordinate representations to demonstrate how the same dataset may be trivially separable in one representation while seemingly impossible in another. [colah’s excellent blogpost](https://colah.github.io/posts/2015-01-Visualizing-Representations/) provides beautiful visualisations to help develop your intuition.

_Representation learning_ is an approach where an algorithm is used to discover the ‘optimal' representation, as well as the mapping from representation to output. Instead of having to rely on humans for feature engineering, the algorithm can achieve this faster on its own. The autoencoder is cited as the quintessential example.

The _autoencoder_ combines:

- an encoder, which converts input data to a representation; and
- a decoder, which converts the new representation back into its original format.

An autoencoder can be trained such that the new representation it generates has certain desired properties while preserving as much information as possible from the original input.

DL is an extension of this concept: it is able to learn complex representations built upon other simpler representations as ’nested simple mappings', which we noted earlier on mirrors the hierarchical fashion that the physical world works. However, it is not the only thing that makes DL so effective - the deep neural network
can also be viewed as having learnt a multi-step computer programme, and so the deeper it is, the more ‘instructions’ in the programme it can hold. The network can learn both complex representations (or features), and also what to do with it.

Two concepts are key to DL:

- Distributed representation of features by different neurons
- Back-propagation for training models

#### How deep is deep?

Two approaches are described:

- Computational graph depth, or the longest path length through the network. The choice of element set is crucial here: a logistic regression can be regarded as one element, or broken up into separate addition, multiplication and logistic sigmoid steps. The key is to be consistent.
- Probabilistic modeling graph depth, where the graph of computations needed to compute the representations may be deeper than the graph of concepts. An intuitive way of thinking about it is a double-take: when new information surprises you, you’re likely to go back to basics and reassess what you thought you knew - effectively, traversing the computation graph another time.

Both measures have their supporters, but in any case there isn’t some magic threshold where a NN is considered deep.

#### A Brief History of Deep Learning
(It really is brief, I promise.)

Before DL was DL, a wave in academia that began with the humble perceptron (1950s) went through periods of relative popularity and decline. It was variously called cybernetics, parallel distributed processing and connectionism, before it became known as artificial neural networks (ANN) and DL. While it drew and continually draws inspiration from neuroscience, including the belief that a single algorithm is responsible for all the brain functions as well as several neural network architectures, DL is its own discipline that the book describes in general terms as "a principle of learning multiple levels of composition”.

Without going into all the details of the intermediate incarnations:

_“The central idea in connectionism is that a large number of simple computational units can achieve intelligent behavior when networked together. This insight applies equally to neurons in biological nervous systems and to hidden units in computational models.”_

So if it’s been around for so long, why is it only now being picked up by so many?

- Big data. According to the book:

_“As of 2016, a rough rule of thumb is that a supervised deep learning algorithm will generally achieve acceptable performance with around 5,000 labeled examples per category, and will match or exceed human performance when trained with a dataset containing at least 10 million labeled examples."_

- More and faster computers (especially ones with GPUs) to make bigger model sizes work:

_"Since the introduction of hidden units, artificial neural networks have doubled in size roughly every 2.4 years. This growth is driven by faster computers with larger memory and by the availability of larger datasets.” "Unless new technologies allow faster scaling, artificial neural networks will not have the same number of neurons as the human brain until at least the 2050s."_


That's it for today. More to come!
