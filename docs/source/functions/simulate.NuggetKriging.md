# `NuggetKriging::simulate`


## Description

Simulation from a `NuggetKriging` model object.


## Usage

* Python
    ```python
    # k = NuggetKriging(...)
    k.simulate(nsim = 1, seed = 123, x)
    ```
* R
    ```r
    # k = NuggetKriging(...)
    k$simulate(nsim = 1, seed = 123, x)
    ```
* Matlab/Octave
    ```octave
    % k = NuggetKriging(...)
    k.simulate(nsim = 1, seed = 123, x)
    ```


## Arguments

Argument      |Description
------------- |----------------
`nsim`     |     Number of simulations to perform.
`seed`     |     Random seed used.
`x`     |     Points in model input space where to simulate.
`with_nugget`     |     Set to FALSE if wish to remove the nugget in the simulation.
`will_update`     |     Set to TRUE if wish to use `update_simulate(...)` later.


## Details

This method draws paths of the stochastic process at new input
 points conditional on the values at the input points used in the
 fit.


## Value

A matrix with `nrow(x)` rows and `nsim` 
 columns containing the simulated paths at the inputs points
 given in `x` .


## Examples

```r
f <- function(x) 1 - 1 / 2 * (sin(12 * x) / (1 + x) + 2 * cos(7 * x) * x^5 + 0.7)
plot(f)
set.seed(123)
X <- as.matrix(runif(10))
y <- f(X) + 0.1  *rnorm(nrow(X))
points(X, y, col = "blue")

k <- NuggetKriging(y, X, kernel = "matern3_2")

x <- seq(from = 0, to = 1, length.out = 101)
s <- k$simulate(nsim = 3, x = x)

lines(x, s[ , 1], col = "blue")
lines(x, s[ , 2], col = "blue")
lines(x, s[ , 3], col = "blue")
```

### Results
```{literalinclude} ../functions/examples/simulate.NuggetKriging.md.Rout
:language: bash
```
![](../functions/examples/simulate.NuggetKriging.md.png)


## Reference

* Code: <https://github.com/libKriging/libKriging/blob/master/src/lib/NuggetKriging.cpp#L1501>


