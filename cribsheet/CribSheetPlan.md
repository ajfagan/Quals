# A sketch of things I plan to include in my crib sheet:

- [ ] Change of Variables
- [ ] Characterizing functions by moments
- [ ] Discrete Distributions
- [ ] Continuous Distributions
- [ ] Convergence
  - [ ] In Distribution
  - [ ] In Probability
  - [ ] Almost Surely
- [ ] Delta Method
  - [ ] 1st order
  - [ ] 2nd order
  - [ ] multivariate
- [ ] Showing sufficiency
  - [ ] By definition
  - [ ] Factorization Thm
  - [ ] Exponential families
- [ ] Showing completeness
  - [ ] By definition
  - [ ] Exponential families
- [ ] Showing minimal sufficiency
  - [ ] By definition
  - [ ] In Exponential families
- [ ] Information
  - [ ] Definition
  - [ ] In exponential families
- [ ] Cramer-Rao Inequality
- [ ] Neyman-Pearson lemma
  - [ ] With sufficient statistics (follows by factorization thm)
- [ ] Monotone Likelihood Ratio (MLR)
- [ ] Karlin-Rubin
- [ ] Tests
  - [ ] Score test
  - [ ] Wald test
- [ ] Gauss-Markov
- [ ] Estimable functions
- [ ] Important fact of normals
- [ ] Distribution Thm
- [ ] Cochran's Theorem
- [ ] Outlier Detection
  - [ ] Leverage
    - [ ] Definition
    - [ ] Guideline
  - [ ] Studentized Residuals
    - [ ] Definition
    - [ ] Guideline
  - [ ] DFFITS
    - [ ] Definition
    - [ ] Guideline
  - [ ] Cooks
    - [ ] Definition
    - [ ] Guideline
  - [ ] VIF
    - [ ] Definition
    - [ ] Guideline
- [ ] Weighed least squares
  - [ ] Normal equations
  - [ ] Fit
- [ ] Box-Cox
- [ ] Pairwise Comparison
  - [ ] Bonferonni
  - [ ] Tukey HSD
  - [ ] Scheffe
- [ ] Model Selection
  - [ ] Mallow's $C_p$
  - [ ] AIC
  - [ ] BIC
- [ ] Penalized Regression
  - [ ] Lasso
  - [ ] Ridge
- [ ] Matrix calculus
- [ ] Shortest length CI using pivots
- [ ] Projection matrices (Paulynomial)
- [ ] Trace (Paulynomial)
- [ ] Inequalities
- [ ] Derivative/variance from exponential family form (Alex)
- [ ] Order statistic pdf
- [ ] $R^2 \to F$ statistic in one-way Anova (Ryan)
- [ ] GLM's


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
        - pmf: $`\frac{\begin{pmatrix}K\\ k\end{pmatrix}\begin{pmatrix}N-n \\ n-k\end{pmatrix}}{\begin{pmatrix}N\\ n\end{pmatrix}}`$
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

**Minimal Sufficiency in exponential families**

$T(X)$ is a minimal sufficient statistic for $\eta(\theta)$ iff for all $\eta_1, \eta_2$ in the natural parameter space and $x_1,x_2$ in the support of $X$, $(\eta_1 - \eta_2)(T(x_1) - T(x_2)) = 0 \implies \eta_1 = \eta_2$ or $x_1 = x_2.$

**Completeness (6.2.21)**

Let $f(t|\theta)$ be a family of pdfs for a statistic $T(X)$. The family of probability distributions is called _complete_ if $\mathbb E_\theta g(T) = 0$ implies that $P_\theta(g(T) = 0) = 1$ for all $\theta$. Equivalently, $T(X)$ is called a _complete statistic_.

**Completeness in Exponential families**

If the natural parameter space $\eta(\theta)$ has nonempty interior, then the statistic $T(X)$ is a complete statistic.

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

A family of pdf's $\{g(t|\theta): \theta\in\Theta\}$ for a univariate random variable $T$ with real-valued parameter $\theta$ has a _monotone likelihood ratio_ (MLR) if for every $\theta_2 > \theta_1, g(t| \theta_2) / g(t| \theta_1)$ is a monotone function of $t$ on the support $\{t : g(t|\theta_1) > 0 \hspace{1em} {\rm or} \hspace{1em} g(t|\theta_2) > 0\}$, where $c/0$ is defined as $\infty$ if $0< c$.

**Karlin-Rubin (8.3.17)**

Consider testing $H_0: \theta\leq\theta_0$ versus $H_1: \theta > \theta_0$. Suppose that $T$ is a sufficient statistic for $\theta$ and the family of pdfs $\{g(t|\theta) | \theta\in\Theta\}$ of $T$ has an MLR. Then for any $t_0$, the test that rejects $H_0$ iff $T>t_0$ is a UMP level $\alpha$ test, where $\alpha = P_{\theta_0}(T > t_0)$.

**Wald Test (10.3.2)**

A _Wald test_ is a test based on a statistic of the form

$$
Z_n = \frac{W_n - \theta_0}{S_n}
$$
where $\theta_0$ is the hypothesized null, $W_n$ is an estimator of $\theta$, and $S_n$ is a standard error for $W_n$. If $W_n$ is the MLE of $\theta$, then $S_n = 1 / \sqrt{I_v(W_n)}$ is a reasonable error. 

**Score Test (10.3.2)**

Define 

$$
Z_S = s(\theta_0)/\sqrt{I_n(\theta_0)}
$$

where $s(\theta) = \frac{\partial}{\partial\theta}\log f(X|\theta)$ is the score statistic. 

It can be shown that $\mathbb E_\theta s(\theta) = 0$ and $\mathbb V_\theta s(\theta) = I_n(\theta)$,

so $Z_s$ has mean 0 and variance 1, and, hence, converges to $N(0,1)$. 

## Linear Regression

**Gauss-Markov**

When columns of $X$ are linearly independent, the unique BLUE among the class of linear unbiased estimators of $c'\beta$ is $c'\hat\beta$ where 

$$
\hat\beta = (X'X)^{-1}X'Y
$$

If $X$ does not have full column space, then

$$
\hat\theta = \argmin_{\theta\in{\rm Col}(X)}||c'Y - c'\theta||^2
$$

is the BLUE.

**Estimable function**

The parametric function $\lambda'\beta$ is _estimable_ if it has a linear unbiased estimator $t'Y$ for $\beta$

Equivalently, it's estimable iff $\lambda \in {\rm Col}(X)$.

**Important fact of Normals**

$\newcommand{\indep}{\perp \!\!\! \perp}$

If $M \sim N_n(\mu\Sigma)$, then, for Matrices $A, B$, $AM\indep BM \iff A\Sigma B' = 0$.

**Distribution Theorem (Lecture 9 - STAT 849)**

If $Y = X\beta + \varepsilon$, $X$ is a full rank matrix, ${\rm rank}(X) = p$ and $\varepsilon \sim N_n(0, \sigma^2I_n)$, then
1. $\hat\beta \sim N_p(\beta, \sigma^2(X'X)^{-1})$
2. $(\hat\beta - \beta)'X'X(\hat\beta - \beta) / \sigma^2 \sim \chi_p^2$
3. $\hat\beta$ is independent of ${\rm RSS} = ||Y - X\hat\beta||^2$
4. $\frac{\rm RSS}{\sigma^2}\sim \chi_{n-p}^2$.

**Cochran's Theorem**

If $M\sim N_n(0, I_n)$ and let $A$ be a symmetric matrix of rank $r$. Then $M'AM\sim\chi_r^2$ if $A$ is idempotent. 

## Testing for outliers and influential points*

**Leverage**

If $H$ is the projection matrix in a linear model, then the _leverage_ is the value  $h_{ii}$. Large values of $h_{ii}$ will pull the fit towards $y_{i\cdot}$ and indicates outlying $X$ values.

**Studentized residuals**

Let 

$$
t_i = \frac{\hat\varepsilon_i}{\hat\sigma_{(i)}\sqrt{1 - h_{ii}}}
$$

where $\hat\sigma_{(i)}$ is the method of moments estimator of $\sigma$ when the $i^{th}$ data point is deleted. Then $|t_i| > 3$ is a good indicator for datapoint $i$ being an outlier. 

Idea: tests if datapoint $i$ is within the prediction interval when the model is fit without it. 

Detects outlying $y$ values, but doesn't necessarily indcate influence. 

**Cook's distance**

$$
D_i = \frac{\left(\hat y - \hat y_{(i)}\right)'\left(\hat y - \hat y_{(i)}\right)}{p\hat\sigma^2}
$$

Values of $D_i > 1$ indicate that datapoint $i$ is influential. 

**Variance Inflation Factor (VIF)**

$$
{\rm VIF}(\hat\beta_j) = \frac{\mathbb V(\hat\beta_j)_{\rm full}}{\mathbb V(\hat\beta_j)_{Y\sim X_j}} = \frac{1}{1 - R_{X_j|X_{-j}}^2}
$$

Values of $\rm VIF$ greater than 5 or 10 $\left(R_{X_j|X_{-j}}^2 > 0.8, 0.9\right)$ are frequently used as cutoffs. 

## Weighted least squares

If $Y = X\beta + \varepsilon$, where $\mathbb V \varepsilon = \sigma^2\Sigma$ where $\sigma^2$ is unknown, but $\Sigma = SS'$ is known, OLS found by solving the regression

$$
S^{-1}Y = S^{-1}X\beta + S^{-1}\varepsilon
$$

where $S^{-1}\hat\varepsilon$ should be approximately iid. 

**Box-Cox transformation**

For strictly positive responses (can add a constant to ensure), find the value of $\lambda$ that minimizes

$$
L(\lambda) = -\frac{n}{2}\log({\rm RSS}_\lambda / n) + (\lambda - 1)\sum\log y_i,
$$

where

$$
g_\lambda(y) = \begin{cases}
\frac{y^\lambda - 1}{\lambda}, & \lambda \neq 0 \\
\log y, & \lambda = 0
\end{cases}
$$

and ${\rm RSS}_\lambda$ is the residual sum of squares when $g_\lambda(y)$ is the response. 

## Pairwise Comparison

**Tukey-Kramer**

The Tukey-Kramer interval is defined as

$$
c'\bar \beta\hat - h \pm \frac{1}{\sqrt{2}} q_{k,n-k, \alpha}\times\sqrt{\hat{\mathbb V} c'\hat\beta}
$$

and it guarantees a level $\alpha$-test for all contrasts.

## Model Selection

**Mallow's $C_p$**

Let $\mathcal{F}$ be the full model, and $\mathcal{M}$ a proposed reduced model. Then Mallow's $C_p$ is defined as

$$
C_p(\mathcal{M}) = \frac{{\rm SSE}(\mathcal{M})}{\hat\sigma^2} - n + 2\times p_\mathcal{M}
$$

where $p_\mathcal{M}$ is the number of parameters in the model $\mathcal{M}$, and $\hat\sigma^2 = {\rm SSE}(\mathcal{F}) / df_\mathcal{F}$

Models should be favored if they have small $C_p$ close to $p$.

**AIC: Akaike Information Criterion**

$$
AIC(\mathcal{M}) = -2\log L_\mathcal{M}(\hat\theta) + 2p_\mathcal{M}.
$$


**AIC: Akaike Information Criterion**

$$
BIC(\mathcal{M}) = -2\log L_\mathcal{M}(\hat\theta) + \log (n)p_\mathcal{M}.
$$

## Penalized Regression

**Ridge Regression**

$$
\min_\beta ||Y-X\beta||^2 + \lambda ||\beta||^2
$$

$$
\hat\beta_\lambda = (X'X - \lambda I_p)^{-1}X'Y
$$

**Lasso Regression**

$$
\min_\beta ||Y - X\beta||^2 - \lambda ||\beta||_1
$$

## Misc.

**Convexity**

A function $f$ is _convex_ if, $\forall\lambda\in[0,1]$, $f(\lambda x + (1 - \lambda)y) \leq \lambda f(x) + (1 - \lambda)f(y)$ for all $x,y$ in $f$'s domain. 

**Matrix calculus**

$$
\mathbb V (AX + b) = A\mathbb V X A'
$$

$$
\frac{\partial}{\partial x} x'A = A
$$

$$
\frac{\partial}{\partial x} x'Ax = 2Ax
$$

Matrix Cookbook Chpt 6



**Minimal size CI**

Let $f(x)$ be a unimodal pdf. If the interval satisfies
1. $\int_a^bf(x)dx = 1 - \alpha$
2. $f(a) = f(b) > 0$
3. The interval $[a,b]$ contains the mode
<!-----break----->
Then $[a,b]$ is the shortest among all $1 - \alpha$ CI's.