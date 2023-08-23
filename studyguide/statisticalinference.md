# Statistical Inference - All sources from Casella-Berger

TODO

- [ ] Add sources for easier stuff
- [ ] Estimation Equation
- [ ] Weighted Least Squares
- [ ] Bayes Estimators
- [ ] Likelihood ratio tests

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

**Minimal Sufficiency in exponential families**

$T(X)$ is a minimal sufficient statistic for $\eta(\theta)$ iff for all $\eta_1, \eta_2$ in the natural parameter space and $x_1,x_2$ in the support of $X$, $(\eta_1 - \eta_2)(T(x_1) - T(x_2)) = 0 \implies \eta_1 = \eta_2$ or $x_1 = x_2.$

## Ancillary Statistics (6.2.3)

**Ancillary Statistics (6.2.16)**

A statistic $S(X)$ whose distribution does not depend on the parameter $\theta$ is called an _ancillary statistic_.

## Completeness (6.2.4)

**Completeness (6.2.21)**

Let $f(t|\theta)$ be a family of pdfs for a statistic $T(X)$. The family of probability distributions is called _complete_ if $\mathbb E_\theta g(T) = 0$ implies that $P_\theta(g(T) = 0) = 1$ for all $\theta$. Equivalently, $T(X)$ is called a _complete statistic_.

**Completeness in Exponential families**

If the natural parameter space $\eta(\theta)$ has nonempty interior, then the statistic $T(X)$ is a complete statistic.

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

The _bias_ of a point estimater $W$ of a parameter $\theta$ is $`\text{Bias}_\theta W = \mathbb E_\theta - \theta`$. An estimator with bias 0 for all values of $\theta$ is called _unbiased_. 

**MSE-Bias relationship**

$$
MSE_{\theta}(W) = \mathbb V\theta + (Bias_{\theta}(W))^2
$$

## Weighted Least Squares

## Bayes Estimators

## UMVUE (7.3.2)

**UMVUE (7.3.7)**

An estimator $`W^*`$ is a uniformly minimum variance unbiased estimator (UMVUE) of $\tau(\theta)$ if it satisfies $`\mathbb EW^* = \tau(\theta)`$ for all $\theta$ (it's unbiased) and, for any other estimator $W$ with $\mathbb E_\theta W = \tau(\theta)$, we have $`\mathbb V_\theta W^*\leq\mathbb V_\theta W`$ for all $\theta$. 

## Information inequality (7.3.2)

**Cramer-Rao Inequality (iid case) (7.3.10)**

Let $X_1,\ldots, X_n$ be an iid sample with pdf $f(x|\theta)$, and let $W(X) = W(X_1, \ldots X_n)$ be any estimator satisfying

$$
\frac{d}{d\theta}\mathbb E_\theta W(X) = \int_\mathcal{X}\frac{\partial}{\partial\theta}[W(x)f(x|\theta)]dx
$$

and

$$
\mathbb V_\theta W(X) < \infty.
$$

Then

$$
\begin{aligned}
\mathbb V_\theta W(X) \geq& \frac{\left(\frac{d}{d\theta}\mathbb E_\theta W(X)\right)^2}{n\mathbb E_\theta \left(\left(\frac{\partial}{\partial\theta}\log f(X|\theta)\right)^2\right)}\\
=& \frac{\left(\frac{d}{d\theta}\mathbb E_\theta W(X)\right)^2}{nI(\theta)}
\end{aligned}
$$

**Information for an exponential family (7.3.11)**

If $f(x|\theta)$ satisfies regularity conditions, which are always satisfied in an exponential family:

$$
I(\theta) = \mathbb E_\theta \left(\left(\frac{\partial}{\partial\theta}\log f(X|\theta)\right)^2\right) = -\mathbb E_\theta \left(\frac{\partial^2}{\partial\theta^2}\log f(X|\theta)\right)
$$

**Rao-Blackwell (7.3.17)**

Let $W$ be any unbiased estimator of $\tau(\theta)$, and let $T$ be a sufficient statistic for $\theta$. Define $\phi(T) = \mathbb E[W|T].$ Then $\phi(T)$ is the UMVUE of $\tau(\theta)$.

**Connecting completeness-sufficiency with UMVUE**

If $T$ is a complete, sufficient statistic for a parameter $\theta$, then $\phi(T)$ is the UMVUE of $\mathbb E \phi(T)$.

## Likelihood ratio tests (8.2.1)

## Evaluation of tests and Neyman-Pearson Lemma, UMP tests, unbiased tests (8.3)

**Power function (8.3.1)**

The power function of a hypothesis test with rejection region $R$ is the function of $\theta$ defined by $\beta(\theta) = P_\theta (X\in R)$.

**Size and level (8.3.5-8.3.6)**

For $0\leq\alpha\leq 1$, a test with power function $\beta(\theta)$ is a _size_ $\alpha$ test if $\sup_{\theta\in\Theta_0}\beta(\theta) = \alpha$.

For $0\leq\alpha\leq 1$, a test with power function $\beta(\theta)$ is a _level_ $\alpha$ test if $\sup_{\theta\in\Theta_0}\beta(\theta) \leq \alpha$.

**Unbiased tests (8.3.9)**

A test with power function $beta(\theta)$ is unbiased if $\beta(\theta') \geq \beta(\theta'')$ for every $\theta'\in\Theta_0^c$ and $\theta''\in\Theta_0.$

**UMP tests (8.3.11)**

Let $\mathcal{C}$ be a class of tests for testing $H_0:\theta\in\Theta_0$ versus $H_1:\theta\in\Theta_0^c$. A test in class $\mathcal{C}$ with power function $\beta(\theta)$, is a _uniformly most powerful_ (UMP) class $\mathcal{C}$ test if $\beta(\theta) \geq \beta'(\theta)$ for every $\theta\in\Theta_0^c$ and $\beta'(\theta)$ that is a power function of a test in class $\mathcal{C}$.

**Neyman-Pearson Lemma (8.3.12)**

Consider testing $H_0:\theta = \theta_0$ vs. $H_1:\theta = \theta|1$, where the pdf corresponding to $\theta_i$ is $f(x|\theta_i)$, using a test with rejection region $R$ that satisfies

$$
x\in R \hspace{1em} {\rm if} \hspace{1em} f(x|\theta_1) > kf(x|\theta_0)
$$

and

$$
x\in R^c \hspace{1em} {\rm if} \hspace{1em} f(x|\theta_1) < kf(x|\theta_0),
$$

for some $k\geq0$ and

$$
\alpha = P_{\theta_0}(X\in R).
$$

Then 
1. (Sufficiency) Any test that satisfies the above is a UMP level $\alpha$ test. 
2. (Necessity) If there exists such a test with $k>0$, then every UMP level $\alpha$ test is a size $\alpha$ test and every UMP level $\alpha$ test satisfies the first condition except, perhaps, on a null set, $A$, under both $\theta_i$, i.e.

$$
P_{\theta_0}(X\in A) = P_{\theta_1}(X\in A) = 0.
$$

**Corollary for sufficient statistics**

Consider the hypothesis in Neyman-Pearos. Suppose $T(X)$ is a sufficient statistic for $\theta$ and $g(t|\theta_i)$ is the pdf of $T$ corresponding to $\theta_i$. Then any test based on $T$ with reject region $S$ is a UMP level $\alpha$ test if it satisfies

$$
t\in S \hspace{1em} {\rm if} \hspace{1em} g(t|\theta_1) > kg(t|\theta_0)
$$

and

$$
t\in S^c \hspace{1em} {\rm if} \hspace{1em} g(t|\theta_1) < kg(t|\theta_0),
$$

for some $k\geq0$, where

$$
\alpha = P_{\theta_0}(X\in S).
$$

**Monotone Likelihood Ratio**

A family of pdf's $\{g(t|\theta): \theta\in\Theta\}$ for a univariate random variable $T$ with real-valued parameter $\theta$ has a _monotone likelihood ratio_ (MLR) if for every $\theta_2 > \theta_1, g(t, \theta_2) / g(t, \theta_1) is a monotone function of $t$ on the support $\{t : g(t|\theta_1) > 0 \hspace{1em} {\rm or} \hspace{1em} g(t|\theta_2) > 0\}$, where $c/0$ is defined as $\infty$ if $0< c$.

**Karlin-Rubin (8.3.17)**

Consider testing $H_0: \theta\leq\theta_0$ versus $H_1: \theta > \theta_0$. Suppose that $T$ is a sufficient statistic for $\theta$ and the family of pdfs $\{g(t|\theta) | \theta\in\Theta\}$ of $T$ has an MLR. Then for any $t_0$, the test that rejects $H_0$ iff $T>t_0$ is a UMP level $\alpha$ test, where $\alpha = P_{\theta_0}(T > t_0)$.

**p-values (8.3.26)**

A _p-value_ $p(X)$ is a test statistic satisfying $0\leq p(x) \leq 1$ for every sample point $x$. Small values of $p(X)$ give evidence that $H_1$ is true. A $p$-value is _valid_ if, for every $\theta\in\Theta_0$ and every $0\leq\alpha\leq1$,

$$
P_\theta(p(X) \leq \alpha) \leq \alpha.
$$

**Calculating $p$-values from statistics**

Let $W(X)$ be a test statistic such that large values of $W$ give evidence that $H_1$ is true. for each sample point $x$, define 

$$
p(x) = \sup_{\theta\in\Theta_0}P_\theta(W(X) \geq W(x)).
$$

Then $p(X)$ is a valid $p$-value.

## Duality between tests and confidence sets (9.1)

**Interval estimation (9.1.1)**

An _interval estimate_ of a real-valued parameter $\theta$ is any pair of functions $L(X)$ and $U(X)$ of a sample that satisfy $L(x) \leq U(x)$ for all $x\in\mathcal{X}$. If $X = x$ is observed, the inference $L(x) \leq \theta \leq U(x)$ is made. The random interval $\left[L(X), U(X)\right]$ is called an _interval estimator_.

**Coverage probability (9.1.4)**

For an interval estimator $\left[L(X), U(X)\right]$ of a parameter $\theta$, the _coverage probability_ is the probability that the random interval $\left[L(X),U(X)\right]$ covers the true parameter $\theta$. Denoted

$$
P_\theta(\theta\in \left[L(X), U(X)\right]).
$$

**Coverage coefficient (9.1.5)**

For an interval estimator $\left[L(X),U(X)\right]$ of a parameter $\theta$, the _confidence coefficient_ of the interval estimator is the infimum of the coverage probabilities,

$$
\inf_\theta P_\theta(\theta \in \left[L(X), U(X)\right]).
$$

**Confidence sets**

A $1 - \alpha$ _confidence set_ is a random set generated from a sample $X$, $C(X)$ satisfying 

$$
\inf_\theta P_\theta(\theta \in C(X)) = 1 - \alpha.
$$

**Inverting a test statistic**

For every $\theta_0\in\Theta$, let $A(\theta_0)$ be the acceptance region of a level $\alpha$ test of $H_0:\theta = \theta_0$. For each $x\in\mathcal{X}$, define a set $C(x)$ in the parameter space by

$$
C(x) = \{\theta_0 : x\in A(\theta_0)\}.
$$

Then the random set $C(X)$ is a $1-\alpha$ confidence set. Conversely, let $C(X)$ be a $1 - \alpha$ confidence set. For any $\theta_0\in\Theta$, define

$$
A(\theta_0) = \{x : \theta_0\in C(x)\}.
$$

Then $A(\theta_0)$ is the acceptance region of a level $\alpha$ test of $H_0: \theta = \theta_0$.

## Pivots (9.2.2)

**Pivots (9.2.6)**

A random variable $Q(X, \theta)$ is a _pivotal quantity_ (or _pivot_) if the distribution of $Q(X,\theta)$ is independent of all parameters. That is, if $X\sim F(x|\theta)$, then $Q(X,\theta)$ has the same distribution for all values of $\theta.$

**In location-scale families (9.2.7)**

|Form of pdf                                    | Type of pdf     | Pivot                         |
|-----------------------------------------------|-----------------|-------------------------------|
|$f(x-\mu)$                                     | Location        | $\bar X - \mu $               |
| $\sigma^{-1}f(\frac{x}{\sigma})$              | Scale           | $\frac{\bar X}{\sigma}$       |
| $\sigma^{-1}f(\frac{x - \mu}{\sigma})$        | Location-scale  | $\frac{\bar X - \mu}{\sigma}$ |

**Constructing confidence sets from pivots**

A pivot, $Q$, leads to a confidence set of the form

$$
C(x) = \{\theta_0: a\leq Q(x, \theta_0) \leq b\},
$$

and if $Q$ is a monotone function of $\theta$ for every $x$ (as in location-scale families), then $C(x)$ is an interval.

**Pivoting a continuous cdf (9.2.12)**

Let $T$ be a statistic with continuous cdf $F_T(t | \theta)$. Let $\alpha_1 + \alpha_2 = \alpha$ with $0\leq\alpha\leq1$ be fixed values. Suppose that for each $t\in\mathcal{T}$, the functions $\theta_L(t)$ and $\theta_U(t)$ can be defined as follows.
1. If $F_T(t|\theta)$ is a decreasing function of $\theta$ for each $t$, define $\theta_L(t)$ and $\theta_U(t)$ by

$$
F_T(t|\theta_U(t)) = \alpha_1, \hspace{1em} F_T(t|\theta_L(t)) = 1 - \alpha_2.
$$

2. If $F_T(t|\theta)$ is an increasing function of $\theta$ for each $t$, define $\theta_L(t)$ and $\theta_U(t)$ by

$$
F_T(t|\theta_U(t)) = 1 - \alpha_2, \hspace{1em} F_T(t|\theta_L(t)) = \alpha_1.
$$

Then the random interval $\left[\theta_L(T), \theta_U(T)\right]$ is a $1 - \alpha$ confidence interval for $\theta$. 

**Pivoting a discrete cdf (9.2.12)**

Let $T$ be a discrete statistic with continuous cdf $F_T(t | \theta) = P(T\geq t | \theta)$. Let $\alpha_1 + \alpha_2 = \alpha$ with $0<\alpha<1$ be fixed values. Suppose that for each $t\in\mathcal{T}$, the functions $\theta_L(t)$ and $\theta_U(t)$ can be defined as follows.
1. If $F_T(t|\theta)$ is a decreasing function of $\theta$ for each $t$, define $\theta_L(t)$ and $\theta_U(t)$ by

$$
P(T\leq t|\theta_U(t)) = \alpha_1, \hspace{1em} P(T\geq t|\theta_L(t)) = \alpha_2.
$$

2. If $F_T(t|\theta)$ is an increasing function of $\theta$ for each $t$, define $\theta_L(t)$ and $\theta_U(t)$ by

$$
P(T\geq t|\theta_U(t)) = \alpha_1, \hspace{1em} P(T\leq t|\theta_L(t)) = \alpha_2.
$$
Then the random interval $\left[\theta_L(T), \theta_U(T)\right]$ is a $1 - \alpha$ confidence interval for $\theta$. 