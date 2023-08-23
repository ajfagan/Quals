$`\usepackage{amsmath}`$
# Statistical Inference - All sources from Casella-Berger

TODO

- [ ] Add sources for easier stuff

## Sample

## Population 

## Statistics

## Sampling distribution

## Sufficiency (6.2)

### Important Definitions: 

Sufficiency (6.2.1)
- A statistic $T(X)$ is a sufficient statistic for $\theta$ if the conditional distribution of the sample $X$ given $T(X)$ does not depend on $\theta$

#### Important Results:

Showing sufficiency

Theorem (6.2.2)
- If $p(x|\theta)$ is the joint pdf of $X$ and $q(t|\theta)$ is the pdf of $T(X)$, then $T(X)$ is a sufficient statistic for $\theta$ if, for every $x$ in the sample space, the ratio $p(x|\theta) / q(T(x)|\theta)$ is a constant as a function of $\theta$

Factorization Theorem (6.2.6)
- Let $f(x|\theta)$ denote the joint pdf of a sample $X$. A statistic $T(X)$ is a sufficient statistic for $\theta$ iff there exists functions $g(t|\theta)$ and $h(x)$ such that, for all sample points $x$ and all parameters $\theta$,
$$
f(x|\theta) = g(T(x)|\theta)h(x).
$$

## Minimial Sufficiency (6.2.2)

Minimal sufficiency (6.2.11)
- A sufficient statistic $T(X)$ is called a minimal sufficient statistic if, for any other sufficient statistic $T'(X)$, $T(X)$ is a function of $T'(X)$. 

Showing minimal sufficiency (6.2.13)
- Let $f(x|\theta)$ be the pdf of a sample $X$. Suppose there exists a function $T(X)$ such that, for every two sample points $x$ and $y$, the ratio $f(x|\theta) / f(x|\theta)$ is a constant as a function of $\theta$ iff $T(x) = T(y)$. Then $T(X)$ is a minimal sufficient statistic. 

# Completeness (6.2.4)

