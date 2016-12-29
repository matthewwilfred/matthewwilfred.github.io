---
layout: post
title: Deep Learning Book read along - 4
---

#### [Numerical computation](http://www.deeplearningbook.org/contents/numerical.html)

<p style="text-align: center">ML algorithms usually arrive at their estimates of the solution iteratively, and can be computationally intensive. There are also problems associated with representing (potentially) infinitely many real numbers on a digital computer with (relatively) limited memory and a finite number of bit patterns, namely rounding errors, which can be categorised as:
- Underflow: where numbers near zero are rounded to zero
- Overflow: where large numbers are approximated as infinity or negative infinity

The softmax function, used for multi-category classification problems, is vulnerable to either of these rounding errors. Some tricks to avoid this are:

- adding or subtracting a scalar from the input vector
- other implementations that calculate a similar function that yield numerically stable results

Fortunately for your everyday ML/DL practitioner, these implementation problems are handled by low-level libraries that can automatically detect and stabilise numerically unstable expressions.

#### Poor conditioning:
This refers to functions being sensitive to small changes in its inputs. A more formal definition can be found in these nicely written articles on [Wikipedia](https://en.wikipedia.org/wiki/Condition_number) and [Wolfram's Mathworld](http://mathworld.wolfram.com/ConditionNumber.html). As a result of this sensitivity, small deviations due to rounding errors can be compounded and results in very inaccurate solutions. Gradient descent performance may also be poor if the cost function is (locally) poorly conditioned. The condition number is a quantity called the [Condition Number](http://math.stackexchange.com/questions/675474/what-is-the-practical-impact-of-a-matrixs-condition-number) describing this characteristic:

*“The condition number of a function with respect to an argument measures how much the output value of the function can change for a small change in the input argument. This is used to measure how sensitive a function is to changes or errors in the input, and how much error in the output results from an error in the input. A problem with a low condition number is said to be well-conditioned, while a problem with a high condition number is said to be ill-conditioned.”*

*“...it estimates worst-case loss of precision. A system is said to be singular if the condition number is infinite, and ill-conditioned if it is too large.”
Whether or not a condition number is “too large” is very problem dependent."*

For Python and Numpy users, numpy.linalg.cond( ) is a nice method that returns the condition number of a matrix based on a specified norm.

#### Gradient-based Optimisation:
The following terms can be used interchangeably to denote the same thing:

- cost function
- loss function
- error function
- objective function
- criterion

Optimisation involves minimising (or maximising, depending on how the function is defined) the function f(x) iteratively via an algorithm by changing x. x* is the notation used to denote the value xmin (or xmax) that has been minimised (or maximised), formally expressed as x* = arg min f(x). In practice ML algorithms cannot guarantee that the minima found is the global minima, so we compromise and settle for a reasonably low value of the function. Saddle points around flat regions of the space can be problematic.

Gradient descent is one of the algorithms for optimisation where analytical solutions do not exist, where f(x) is decreased iteratively by changing x in the direction (denoted by unit vector u) of steepest descent with the scalar epsilon (or learning rate) to control the step size.

#### Jacobian and Hessian matrices:
- Jacobian matrix: the matrix of all partial derivatives of a function
- Hessian matrix: the matrix of all second partial derivatives of a function; second derivatives measure the curvature. The multivariate second derivative test can distinguish between local minima and maxima

For cost functions that have continuous second partial derivatives, which is usually the case for DL purposes, the resulting Hessian matrix is real and symmetric and therefore can be decomposed into real eigenvalues and eigenvectors.

We can use information from the Hessian matrix to guide the search for a minima. Algorithms that use this are called second-order optimisation algorithms, of which Newton’s method is commonly used. This is contrasted with first-order optimisation algorithms such as gradient descent that use only the gradient. The problem with second-order algorithms though is they are attracted by saddle points. Second order methods often converge much more quickly, but it can be very computationally expensive to calculate and store the Hessian matrix. Generally, first order methods are preferred in practice, because they need nothing more than the value of the error function, and its gradient. Furthermore, instead of directly computing the curvature, the sequence of gradients (or first order derivatives) can be used to approximate the second order terms.

The choice of optimisation algorithms is not an exact science, because there are no performance guarantees for the wide range of functions they are applicable to. Sometimes we can constrain the functions we wish to optimise to be Lipschitz continuous which is a function whose rate of change is bounded by a Lipschitz constant. (Note: There may be a relation between the Lipschitz constant and condition number but this is not stated in the book.)

#### Convex optimisation algorithms
*“Convex optimization algorithms are able to provide many more guarantees by making stronger restrictions. Convex optimization algorithms are applicable only to convex functions—functions for which the Hessian is positive semidefinite everywhere. Such functions are well-behaved because they lack saddle points and all of their local minima are necessarily global minima. However, most problems in deep learning are difficult to express in terms of convex optimization. Convex optimization is used only as a subroutine of some deep learning algorithms. Ideas from the analysis of convex optimization algorithms can be useful for proving the convergence of deep learning algorithms. However, in general, the importance of convex optimization is greatly diminished in the context of deep learning.”*
</p>