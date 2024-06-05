# `NuggetKriging::predict`


## Description

Predict from a `NuggetKriging` Model Object


## Usage

* Python
    ```python
    # k = NuggetKriging(...)
    k.predict(x, return_stdev = True, return_cov = False, return_deriv = False)
    ```
* R
    ```r
    # k = NuggetKriging(...)
    k$predict(x, return_stdev = TRUE, return_cov = FALSE, return_deriv = FALSE)
    ```
* Matlab/Octave
    ```octave
    % k = NuggetKriging(...)
    k.predict(x, return_stdev = true, return_cov = false, return_deriv = false)
    ```

## Arguments

Argument      |Description
------------- |----------------
`x`     |     Input points where the prediction must be computed.
`return_stdev`     |     `Logical` . If `TRUE` the standard deviation is returned.
`return_cov`     |     `Logical` . If `TRUE` the covariance matrix of the predictions is returned.
`return_deriv`     |     `Logical` . If `TRUE` the derivatives of mean and sd of the predictions are returned.

## Details

Given $n^\star$ "new" input points $\mathbf{x}^\star_{j}$, the method
compute the expectation, the standard deviation and (optionally) the covariance
of the "new" observations $y(\mathbf{x}^\star_j)$ of the
stochastic process, conditional on the $n$ values $y(\mathbf{x}_i)$ at
the input points $\mathbf{x}_i$ as used when fitting the model. The
$n^\star$ input vectors (with length $d$) are given as the rows of a
$\mathbf{X}^\star$ corresponding to `x`.

The computation of these quantities is often called *Universal
Kriging* see [here](SecPredAndSim) for more details.


## Value

A list containing the element `mean` and possibly `return_stdev` and
`return_cov`. 

- The expectation in ` mean` is the estimate of the vector
   $\textsf{E}[\mathbf{y}^\star \, \vert \,\mathbf{y}]$ with length
   $n^\star$ where $\mathbf{y}^\star$ and $\mathbf{y}$ are the random
   vectors corresponding to the observation and the "new" input
   points. Similarly the conditional standard deviation in `return_stdev` is
   a vector with length $n^\star$ and the conditional covariance in
   `return_cov` is a $n^\star \times n^\star$ matrix. 
   
- The (optional) derivatives are two $n^\star \times d$ matrices
   `pred_mean_deriv` and ` pred_sdtdev_deriv` with their row $j$
   containing the vector of derivatives w.r.t. to the new input point
   $\mathbf{x}^\star$ evaluated at $\mathbf{x}^\star =
   \mathbf{x}^\star_j$. So the row $j$ of `pred_mean_deriv` contains
   the derivative $\partial_{\mathbf{x}^\star}
   \mathbb{E}[y(\mathbf{x}^\star) \, \vert \,\mathbf{y}]$.  evaluated
   at $\mathbf{x}^\star = \mathbf{x}^\star_j$.

Note that for a `NuggetKriging` object if it happens that the new
input $\mathbf{x}^\star$ is exactly equal to one of the inputs
$\mathbf{x}_i$ then the corresponding prediction will be equal to the
corresponding observed output $y_i$. So the prediction is
discontinuous at the observations.


## Examples

```r
f <- function(x) 1 - 1 / 2 * (sin(12 * x) / (1 + x) + 2 * cos(7 * x) * x^5 + 0.7)
plot(f)
set.seed(123)
X <- as.matrix(runif(10))
y <- f(X) + 0.1 * rnorm(nrow(X))
points(X, y, col = "blue", pch = 16)

k <- NuggetKriging(y, X, "matern3_2")

x <- sort(c(X,seq(from = 0, to = 1, length.out = 101))) # include design points to see interpolation
p <- k$predict(x)

lines(x, p$mean, col = "blue")
polygon(c(x, rev(x)), c(p$mean - 2 * p$stdev, rev(p$mean + 2 * p$stdev)), border = NA, col = rgb(0, 0, 1, 0.2))
```

### Results
```{literalinclude} ../functions/examples/predict.NuggetKriging.md.Rout
:language: bash
```
![](../functions/examples/predict.NuggetKriging.md.png)


## Reference

* Code: <https://github.com/libKriging/libKriging/blob/master/src/lib/NuggetKriging.cpp#L1326>
