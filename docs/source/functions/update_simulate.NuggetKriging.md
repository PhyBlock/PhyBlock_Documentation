# `NuggetKriging::update_simulate`


## Description

Update previous simulation of a `NuggetKriging` model object.

This method draws paths of the stochastic process conditional on the values at the input points used in the
fit, plus the new input points and their values given as argument (knonw as 'update' points).

## Usage

* Python
    ```python
    # k = NuggetKriging(...)
    # k.simulate(nsim = 1, seed = 123, x, will_update = True)
    k.update_simulate(y_u, X_u)
    ```
* R
    ```r
    # k = NuggetKriging(...)
    # k$simulate(nsim = 1, seed = 123, x, will_update = TRUE)
    k$update_simulate(y_u, X_u)
    ```
* Matlab/Octave
    ```octave
    % k = NuggetKriging(...)
    % k.simulate(nsim = 1, seed = 123, x, will_update = true)
    k.update_simulate(y_u, X_u)
    ```

## Arguments

Argument      |Description
------------- |----------------
`y_u`     |     Numeric vector of new responses (output).
`X_u`     |     Numeric matrix of new input points.


## Details

This method draws $n_{\texttt{sim}}$ paths of the stochastic process
$y(\mathbf{x})$ at the $n^\star$ given new input points
$\mathbf{x}^\star_j$ conditional on the values $y(\mathbf{x}_i)$ at
the input points used in the fit, plus the new input points and their values given as argument (knonw as 'update' points).

## Value

A matrix with `nrow(x)` rows and `nsim` columns containing the updated
simulated paths at the inputs points given in `x`.


## Examples

```r
f <- function(x) 1 - 1 / 2 * (sin(12 * x) / (1 + x) + 2 * cos(7 * x) * x^5 + 0.7)
plot(f)
set.seed(123)
X <- as.matrix(runif(10))
y <- f(X) + 0.1 * rnorm(nrow(X))
points(X, y, col = "blue")

k <- NuggetKriging(y, X, "matern3_2")

x <- seq(from = 0, to = 1, length.out = 101)
s <- k$simulate(nsim = 3, x = x, will_update = TRUE)

lines(x, s[ , 1], col = "blue")
lines(x, s[ , 2], col = "blue")
lines(x, s[ , 3], col = "blue")

X_u <- as.matrix(runif(3))
y_u <- f(X_u) + 0.1 * rnorm(nrow(X_u))
points(X_u, y_u, col = "red")

su <- k$update_simulate(y_u, X_u)

lines(x, su[ , 1], col = "blue", lty=2)
lines(x, su[ , 2], col = "blue", lty=2)
lines(x, su[ , 3], col = "blue", lty=2)
```

### Results
```{literalinclude} ../functions/examples/update_simulate.NuggetKriging.md.Rout
:language: bash
```
![](../functions/examples/update_simulate.NuggetKriging.md.png)


## Reference

* Code: <https://github.com/libKriging/libKriging/blob/master/src/lib/NuggetKriging.cpp#L1357>


