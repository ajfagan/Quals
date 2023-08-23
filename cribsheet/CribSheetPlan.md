# A sketch of things I plan to include in my crib sheet:

**Theorem 2.15 (Change of Variables):**

Let $X$ have pdf $f_X(x)$ and let $Y = g(X)$, where $g$ is <i>monotone</i>. Let $\mathcal{X}$ and $\mathcal{Y}$ be defined by
$$\mathcal{X} = \{x:f_X(x) > 0\}$$
$$\mathcal{Y} = \{y : \exists x\in\mathcal{X}, y = g(x)\}.$$

Suppose that $f_X(x)$ is continuous on $\mathcal{X}$ and that $g^{-1}(y)$ has a continuous derivative on $\mathcal{Y}$. Then the pdf of $Y$ is

$$ 
f_Y(y) = \begin{cases} 
    f_X(g^{-1}(y))\left|\frac{d}{dy}g^{-1}(y) \right|, &y\in\mathcal{Y}\\
    0, & otherwise. \end{cases} 
$$


**Characterizing function by moments (Thm 2.3.11)**

Let $F_X(x)$ and $F_Y(y)$ be two cdf's all of whose moments exists.
    1. If $X$ and $Y$ have bounded support, then $F_X(u) = F_Y(u)$ for all $u$ $\iff$ $\mathbb EX^r  =\mathbb EY^r$ for all integers $r = 0, 1, \ldots$
    2. If the moment generating functions exist and $M_X(t) = M_Y(t)$ for all $t$ in some neighborhood of 0, then $F_X(u) = F_Y(u)$ for all $u$.

### Discrete distributions (3.2)
- Bernoulli: The 0/1 distribution with $p$ being the probability of $1$ 
    - parameters: $p$
    - Mass functions
        - pmf: $f_X(x|p)$ = $pI(x = 1) + (1 - p)I(x = 0)$
        - cmf: $F_X(x|p) = (1-p)I(0\leq x < 1) + pI(x > 1)$
    - Moments:
        - Mean: $p$
        - Variance: $p(1-p)$
    - mgf: $(1 - p) + pe^t$
- Binomial: The sum of $n$ iid Bernoulli processes with mean $p$
    - parameters: $n,p$
    - Mass functions
        - pmf: $`f_X(x) = \begin{pmatrix}n \\ x\end{pmatrix} p^x(1-p)^{n-x}, x = 0, \ldots, n`$
        - cmf: $`
        F_X(x) = \begin{cases}
            {\sum}_{i=0}^{\lfloor{x}\rfloor}f_X(i),& 0\leq x < n\\
            1, &x >n
            \end{cases}
        `$
    - Moments:
        - Mean: $np$
        - Variance: $np(1-p)$
    - mgf: $((1 - p) + pe^t)^n$
- Hypergeometric distribution: Probability of $k$ successes in $n$ draws from a population of size $N$ containing $K$ successes
    - parameters: $k, n, N, K$
    - Mass functions
        - pmf: $`\frac{\begin{pmatrix}K-k\end{pmatrix}\begin{pmatrix}N-n \\ n-k\end{pmatrix}}{\begin{pmatrix}N\\ n\end{pmatrix}}`$
    - Moments:
        - Mean = $n\frac{K}{N}$
        - Variance = $n\frac{K}{N}\frac{N-K}{N}\frac{N-n}{N-1}$
- Poisson: Probability of a certain number of events occuring in a time interval, given the average number is $\lambda$
    - Parameters: $\lambda$
    - Mass functions: 
        - pmf: $f_X(x) = \frac{\lambda^xe^{-\lambda}}{x!}$
        - cmf: $F_X(x) = e^{-\lambda}{\sum}_{i=0}^{\lfloor x \rfloor}\frac{\lambda^i}{i!}$
    - Moments:
        - Mean: $\lambda$
        - Variance: $\lambda$
    - mgf: $\exp\{\lambda(e^t - 1)\}$

### Continuous Distributions (3.3)

**Finding mean and variance in exponential families**

$$
\mathbb E\frac{\partial}{\partial \theta}\eta(\theta)'T(x) = - \frac{\partial}{\partial \theta}\log c(\theta)
$$

$$
\mathbb V\frac{\partial}{\partial \theta}\eta(\theta)'T(x) = - \frac{\partial^2}{\partial \theta^2}\log c(\theta) - \mathbb{E}\left(\frac{\partial^2}{\partial\theta^2}\eta(\theta)\right)'T(x)
$$

**Convergence in probability:  (5.5.1)**

A sequence of random variables $X_1, X_2, \ldots$ converges in probability to a random variable $X$, denoted $X_n \rightarrow_p X$, if, for every $\varepsilon >0$, 

$$
\lim_{n\rightarrow\infty}P(|X_n - X| < \varepsilon) = 1
$$

**Convergence almost surely: (5.5.5)**

A sequence of random variable $X_1, X_2,\ldots$ converges almost surely to $X$, denoted $X_n \rightarrow_{a.s.} X$, if for every $\varepsilon > 0$,

$$
P\left(\lim_{n\rightarrow\infty}|X_n - X| < \varepsilon\right) = 1.
$$

**Convergence in distribution: (5.5.10)**

A sequence of random variables $X_1,X_2,\ldots$ converges in distribution to $X$, denoted $X_n \rightarrow_d X$, if, for all continuity points of $F_X(x)$,

$$
\lim_{n\rightarrow\infty}F_{X_n}(x) = F_X(x)
$$

## Delta's Method (5.5)
Delta's Method (5.5.24)
- Let $Y_n$ such that $\sqrt{n}(Y_n - \theta) \rightarrow_d N(0, \sigma^2)$. Then for a function $g$ and a value $\theta$, suppose that $g'(\theta)$ exists and is not 0. Then

$$
\sqrt{n}[g(Y_n) - g(\theta)] \rightarrow_d N(0, \sigma^2[g'(\theta)]^2)
$$

Second-order Delta's Method (5.5.26)
- Let $Y_n$ such that $\sqrt{n}(Y_n - \theta) \rightarrow_d N(0, \sigma^2)$. Then for a function $g$ and a value $\theta$, suppose that $g'(\theta) = 0$ and $g''(\theta)$ exists and is not 0. Then

$$
n[g(Y_n) - g(\theta)] \rightarrow_d \sigma^2\frac{g''(\theta)}{2}\chi_1^2
$$

Multivariate Delta's Method (5.5.28)
- Let $X_1, \ldots, X_n$ be a random sample with $\mathbb E X_{ij} = \mu_i$ and ${\rm Cov}(X_{ik}, X_{jk}) = \sigma_{ij}$. For a given function $g$ with continuous first partial dervatives and a specific $\mu = (\mu_1, \ldots, \mu_p)$ for which $\tau^2 = \sum\sum\sigma_{ij}\frac{\partial g(\mu)}{\partial \mu_i}\frac{\partial g(\mu)}{\partial \mu_j} > 0$,

$$
\sqrt{n}[g(\bar X_1, \ldots \bar X_s) - g(\mu_1, \ldots, \mu_p)] \rightarrow_d N(0, \tau^2).
$$

**Showing minimal sufficiency (6.2.13)**

Let $f(x|\theta)$ be the pdf of a sample $X$. Suppose there exists a function $T(X)$ such that, for every two sample points $x$ and $y$, the ratio $f(x|\theta) / f(x|\theta)$ is a constant as a function of $\theta$ iff $T(x) = T(y)$. Then $T(X)$ is a minimal sufficient statistic. 

**Completeness (6.2.21)**

Let $f(t|\theta)$ be a family of pdfs for a statistic $T(X)$. The family of probability distributions is called _complete_ if $\mathbb E_\theta g(T) = 0$ implies that $P_\theta(g(T) = 0) = 1$ for all $\theta$. Equivalently, $T(X)$ is called a _complete statistic_.