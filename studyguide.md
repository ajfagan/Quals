# Study guide for quals 2023 - Option B

## Syllabus

### Probability Theory - All sources from Casella-Berger

#### Probability and conditional probability (1.2 - 1.3)

#### Correlation and independence (1.3)

#### Random Variable (1.4)

#### Distributions (1.5 - 1.6)

#### Transformations (2.1)

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

#### Expectations (2.2)

#### Moment generating functions (2.3)

Important definitions:

- Moment generating function (2.3.6)
    - $M_X(t) = \mathbb{E}\exp\{Xt\}$

Important Results:

- Characterizing function by moments (Thm 2.3.11)
    - Let $F_X(x)$ and $F_Y(y)$ be two cdf's all of whose moments exists.
        1. If $X$ and $Y$ have bounded support, then $F_X(u) = F_Y(u)$ for all $u$ $\iff$ $\mathbb EX^r  =\mathbb EY^r$ for all integers $r = 0, 1, \ldots$
        2. If the moment generating functions exist and $M_X(t) = M_Y(t)$ for all $t$ in some neighborhood of 0, then $F_X(u) = F_Y(u)$ for all $u$.

- Convergence of mgfs (Thm 2.3.12)