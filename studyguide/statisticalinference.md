# Statistical Inference - All sources from Casella-Berger

TODO

- [ ] Add sources for easier stuff
- [ ] Estimation Equation
- [ ] Weighted Least Squares
- [ ] Bayes Estimators

## Sample

## Population 

## Statistics

## Sampling distribution

## Sufficiency (6.2)

### Important Definitions: 

**Sufficiency (6.2.1)**

A statistic $T(X)$ is a sufficient statistic for $\theta$ if the conditional distribution of the sample $X$ given $T(X)$ does not depend on $\theta$

#### Important Results:

The following two results provide a method of determining sufficiency.

**Theorem (6.2.2)**

If $p(x|\theta)$ is the joint pdf of $X$ and $q(t|\theta)$ is the pdf of $T(X)$, then $T(X)$ is a sufficient statistic for $\theta$ if, for every $x$ in the sample space, the ratio $p(x|\theta) / q(T(x)|\theta)$ is a constant as a function of $\theta$

**Factorization Theorem (6.2.6)**

Let $f(x|\theta)$ denote the joint pdf of a sample $X$. A statistic $T(X)$ is a sufficient statistic for $\theta$ iff there exists functions $g(t|\theta)$ and $h(x)$ such that, for all sample points $x$ and all parameters $\theta$,
$$
f(x|\theta) = g(T(x)|\theta)h(x).
$$

## Minimial Sufficiency (6.2.2)

**Minimal sufficiency (6.2.11)**

A sufficient statistic $T(X)$ is called a minimal sufficient statistic if, for any other sufficient statistic $T'(X)$, $T(X)$ is a function of $T'(X)$. 

**Showing minimal sufficiency (6.2.13)**

Let $f(x|\theta)$ be the pdf of a sample $X$. Suppose there exists a function $T(X)$ such that, for every two sample points $x$ and $y$, the ratio $f(x|\theta) / f(x|\theta)$ is a constant as a function of $\theta$ iff $T(x) = T(y)$. Then $T(X)$ is a minimal sufficient statistic. 

## Ancillary Statistics (6.2.3)

**Ancillary Statistics (6.2.16)**

A statistic $S(X)$ whose distribution does not depend on the parameter $\theta$ is called an _ancillary statistic_.

## Completeness (6.2.4)

**Completeness (6.2.21)**

Let $f(t|\theta)$ be a family of pdfs for a statistic $T(X)$. The family of probability distributions is called _complete_ if $\mathbb E_\theta g(T) = 0$ implies that $P_\theta(g(T) = 0) = 1$ for all $\theta$. Equivalently, $T(X)$ is called a _complete statistic_.

**Basu's Theorem (6.2.24)**

If $T(X)$ is a complete, minimal sufficient statistic, then $T(X)$ is independent of every ancillary statistic. 

## Maximum Likelihood (7.2.2)

**Maximum Likelihood Estimator (7.2.4)**

For each sample point $x$, let $\hat\theta(x)$ be a parameter value at which $L(\theta | x)$ attains its maximum as a function of $\theta$. A _maximum likelihood estimator_ (MLE) of the parameter based on a sample $X$ is $\hat\theta(X)$.

**Invariance property of MLEs (7.2.10)**

If $\hat\theta$ is the MLE of $\theta$, then for any function $\tau(\theta)$, the MLE of $\tau(\theta)$ is $\tau(\hat\theta)$.

## Method of Moments (7.2.1)

**Method of Moments**
Let $X_1, \ldots, X_n$ be a sample from a population with pdf $f(x| \theta_1,\ldots, \theta_k)$. The method of moments estimator of $\tilde\theta$ is the solution to the system of equations
$$
\frac{1}{n}{\sum}_{i=1}^nX_i^t = \mu_t'(\tilde\theta)
$$
for $t = 1,\ldots,k$ and $\mu_t'(\theta) = \mathbb EX^t$.

## Estimation equation

## Least Squares (7.3.1)

**Mean Squared Error (7.3.1)**

The _Mean squared error_ (MSE) of an estimator $W$ of a parameter $\theta$ is the function of $\theta$ defined by $\mathbb E_\theta (W-\theta)^2$.

**Bias (7.3.2)**

The _bias_ of a point estimater $W$ of a parameter $\theta$ is ${\rm Bias}_\theta W = \mathbb E_\theta - \theta$. An estimator with bias 0 for all values of $\theta$ is called _unbiased_. 

**MSE-Bias relationship**

$$
{\rm MSE}_\theta(W) = \mathbb V\theta + ({\rm Bias}_\theta(W))^2
$$

## Weighted Least Squares

## Bayes Estimators

## UMVUE (7.3.2)

**UMVUE (7.3.7)**

An estimator $W^*$ is a uniformly minimum variance unbiased estimator (UMVUE) of $\tau(\theta)$ if it satisfies $\mathbb EW^* = \tau(\theta)$ for all $\theta$ (it's unbiased) and, for any other estimator $W$ with $\mathbb E_\theta W = \tau(\theta)$, we have $\mathbb V_\theta W^*\leq\mathbb V_\theta W$ for all $\theta$. 

## Information inequality (7.3.2)