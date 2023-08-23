# Study guide for quals 2023 - Option B

TODO:
- [ ] Complete discrete distributions 
- [ ] Complete continuous Distributions
- [ ] Multivariate and linear and quadratic forms
- [ ] Finish Syllabus

# Syllabus

## Probability Theory - All sources from Casella-Berger

### Probability and conditional probability (1.2 - 1.3)

### Correlation and independence (1.3)

### Random Variable (1.4)

### Distributions (1.5 - 1.6)

### Transformations (2.1)

Important Results:

- Theorem 2.15 (Change of Variables): 
    - Let $X$ have pdf $f_X(x)$ and let $Y = g(X)$, where $g$ is <i>monotone</i>. Let $\mathcal{X}$ and $\mathcal{Y}$ be defined by
    $$
    \mathcal{X} = \{x:f_X(x) > 0\}
    $$
    $$
    \mathcal{Y} = \{y : \exists x\in\mathcal{X}, y = g(x)\}.
    $$
    Suppose that $f_X(x)$ is continuous on $\mathcal{X}$ and that $g^{-1}(y)$ has a continuous derivative on $\mathcal{Y}$. Then the pdf of $Y$ is
    $$
    f_Y(y) = \begin{cases}
    f_X(g^{-1}(y))\left|\frac{d}{dy}g^{-1}(y)\right|, &y\in\mathcal{Y}\\
    0, &otherwise.
    \end{cases}
    $$
- Theorem 2.18 (Generalized Change of Variables)
    - Let $X$ have pdf $f_X(x)$ and let $Y = g(X)$. Define the sample space $\mathcal{X}$ as in Theorem 2.15. Suppose $\exists A_0,\ldots, A_k$ a partition of $\mathcal{X}$ such that $P(x\in A_0) = 0$ and $f_X(x)$ is continuous on each $A_i$. Further, suppose $\exists g_1(x), \ldots,g_k(x)$ , defined on $A_1, \ldots, A_k$ respectively, satisfying 
        1. $g(x) = g_i(x), \forall x\in A_i$
        2. $g_i(x)$ is monotone on $A_i$
        3. The set $\mathcal{Y} = \{y: \exists x\in A_i, g_i(x) = y\}$ is the same for each $i$ in $1,\ldots,k$.
        4. $g_i^{-1}(y)$ has a continuous derivative on $\mathcal{Y}$ for each $i$ in $1,\ldots,k$
    - Then
    $$
    f_Y(y) = \begin{cases}
        \sum_{i=1}^kf_X(g_i^{-1}(x))\left|\frac{d}{dy}g_i^{-1}(y)\right|,& y\in\mathcal{Y}\\
        0, &otherwise.
    \end{cases}
    $$

### Expectations (2.2)

### Moment generating functions (2.3)

Important definitions:

- Moment generating function (2.3.6)
    - $M_X(t) = \mathbb{E}\exp\{Xt\}$

Important Results:

- Characterizing function by moments (Thm 2.3.11)
    - Let $F_X(x)$ and $F_Y(y)$ be two cdf's all of whose moments exists.
        1. If $X$ and $Y$ have bounded support, then $F_X(u) = F_Y(u)$ for all $u$ $\iff$ $\mathbb EX^r  =\mathbb EY^r$ for all integers $r = 0, 1, \ldots$
        2. If the moment generating functions exist and $M_X(t) = M_Y(t)$ for all $t$ in some neighborhood of 0, then $F_X(u) = F_Y(u)$ for all $u$.

### Useful distributions

#### Discrete distributions (3.2)
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
        - pmf: $f_X(x) = \begin{pmatrix}n \\ x\end{pmatrix} p^x(1-p)^{n-x}, x = 0, \ldots, n$
        - cmf: $F_X(x) = \begin{cases}
            \sum_{i=0}^{\lfloor{x}\rfloor}f_X(i),& 0\leq x < n\\
            1, &x >n
            \end{cases}$
    - Moments:
        - Mean: $np$
        - Variance: $np(1-p)$
    - mgf: $((1 - p) + pe^t)^n$
- Hypergeometric distribution: Probability of $k$ successes in $n$ draws from a population of size $N$ containing $K$ successes
    - parameters: $k, n, N, K$
    - Mass functions
        - pmf: 
        $$
        \frac{\begin{pmatrix}K\\k\end{pmatrix}\begin{pmatrix}N-n \\ n-k\end{pmatrix}}{\begin{pmatrix}N\\ n\end{pmatrix}}
        $$
    - Moments:
        - Mean = $n\frac{K}{N}$
        - Variance = $n\frac{K}{N}\frac{N-K}{N}\frac{N-n}{N-1}$
- Poisson: Probability of a certain number of events occuring in a time interval, given the average number is $\lambda$
    - Parameters: $\lambda$
    - Mass functions: 
        - pmf: $f_X(x) = \frac{\lambda^xe^{-\lambda}}{x!}$
        - cmf: $F_X(x) = e^{-\lambda}\sum_{i=0}^{\lfloor x \rfloor}\frac{\lambda^i}{i!}$
    - Moments:
        - Mean: $\lambda$
        - Variance: $\lambda$
    - mgf: $\exp\{\lambda(e^t - 1)\}$

#### Continuous Distributions (3.3)

### Exponential and location-scale families (3.4)

Important Definitions:
- A family of pdfs or pmfs is called an exponential family if it can be expressed as
$$
f(x|\theta) = h(x)c(\theta)\exp\left(\eta(\theta)'T(x)\right)
$$
or, equivalently
$$
\log f(x|\theta) = \log h(x) - \log c(\theta) + \eta(\theta)'T(x)
$$
- A curved exponential family is one whose dimension $d$ is smaller than the number of parameters $k$. If $d=k$, then the family is a full exponential family. 

Important Results:
- If $X$ is a random variable with pdf in an exponential family, then 
$$
\mathbb E\frac{\partial}{\partial \theta}\eta(\theta)'T(x) = - \frac{\partial}{\partial \theta}\log c(\theta)
$$
$$
\mathbb V\frac{\partial}{\partial \theta}\eta(\theta)'T(x) = - \frac{\partial^2}{\partial \theta^2}\log c(\theta) - \mathbb{E}\left(\frac{\partial^2}{\partial\theta^2}\eta(\theta)\right)'T(x)
$$

### Location and Scale Families (3.5)

### Multivariate normal and linear and quadratic forms
