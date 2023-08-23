# Linear and Generalized Linear Models

## Linear Regression

For a matrix of independent variables (design matrix) $X_{n\times (p +1)}$ and a vector of dependent variables $Y_{n\times 1}$, find the parameter vector $\beta_{(p+1)\times1}$ such that:
$$
\mathbb EY = X\beta
$$

## Least squares fit

$$
\hat\beta = (X'X)^{-1}X'Y
$$

## Gauss-Markov

Least squares fit is BLUE. 