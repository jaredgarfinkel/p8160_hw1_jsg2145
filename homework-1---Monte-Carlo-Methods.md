Homework 1 - Monte Carlo Methods
================
Jared Garfinkel - jsg2145

# Problem 1

The standard Laplace distribution has density
\[f(x) = 0.5e^{-|x|}, x \in
(-\infty, \infty)\]. Please provide an algorithm that uses the inverse
transformation method to generate a random sample from this
distribution. Use the \(U(0,1)\) random number generator in 

# Answer: your answer starts here…

X = \(F^{-1}(U)\)

\= \(F(x)\)

\(f(x) = 0.5e^{-|x|},~x \in(-\infty, \infty)\)

``` r
set.seed(123)
U <- runif(1000)
X <- (U < 0.5) * log(2*U) + (U >= 0.5) * -log(2-2*U)

plot(X)
```

<img src="homework-1---Monte-Carlo-Methods_files/figure-gfm/unnamed-chunk-1-1.png" width="90%" />

``` r
hist(X, prob = T)
```

<img src="homework-1---Monte-Carlo-Methods_files/figure-gfm/unnamed-chunk-1-2.png" width="90%" />

\#Problem 2

Use the inverse transformation method to derive an algorithm for
generating a Pareto random number with \(U\sim U(0,1)\), where the
Pareto random number has a probability density function
\[f(x; \alpha, \gamma)=\frac{\gamma\alpha^{\gamma}}{x^{\gamma+1}} I\{x\ge \alpha\}\]
with two parameters \(\alpha >0\) and \(\gamma>0\). Use visualization
tools to validate your algorithm (i.e., illustrate whether the random
numbers generated from your function truely follows the target
distribution.)

\[F(x) = 1 - \left(\frac{\alpha}{x}\right)^{\gamma},~x \ge \alpha,~\alpha > 0,~\gamma > 0\]

\[x = \frac{\alpha}{(1-u)^{1/\gamma}}\]

# Answer: your answer starts here…

``` r
set.seed(1001)
U <- runif(1000)
xdens = function(gamma = 5, alpha = 2, x = U) {
  alpha/((1-U)^(1/gamma))
}

x <- xdens(5, 2, U)

hist(x, prob = T)
```

<img src="homework-1---Monte-Carlo-Methods_files/figure-gfm/unnamed-chunk-2-1.png" width="90%" />

\#Problem 3

Construct an algorithm for using the acceptance/rejection method to
generate 100 pseudorandom variable from the pdf
\[f(x) = \frac{2}{\pi \beta^2} \sqrt{\beta^2-x^2}, \,\, -\beta \le x \le \beta.\]
The simplest choice for \(g(x)\) is the \(U(-\beta, \beta)\)
distribution but other choices are possible as well. Use visualization
tools to validate your algorithm (i.e., illustrate whether the random
numbers generated from your function truely follows the target
distribution.)

# Answer: your answer starts here…

``` r
set.seed(1001)

accrej <- function(fdens, gdens, beta, M = (4/pi), x){
  x = runif(2222, min = -beta, max = beta)
  return(x[runif(length(x)) <= fdens(x, beta) / (M * gdens(x, beta))])
}

xdens = function(x, beta){
  return((2/(pi*beta^2))*sqrt(beta^2 - x^2) * (abs(x) <= beta))
}

unifdens = function(x, beta){
  return((1/(2*beta))*(abs(x) <= beta))
}


y = accrej(xdens, unifdens, 3, 4/pi)

hist(y, prob = T)
```

<img src="homework-1---Monte-Carlo-Methods_files/figure-gfm/unnamed-chunk-3-1.png" width="90%" />

\#Problem 4

Develop two Monte Carlo methods for the estimation of
\(\theta=\int_0^1 e^{x^2} dx\) and implement in 

# Answer: your answer starts here…

``` r
simdat <- function(n, x) {
  rexp(n, rate = x^2)
}
```

``` r
compare <- function(n, x, N=500) {
  SSEmean <- SSEmedian <- 0                    
# Initialize
  for(i in 1:N){
    dat <- integrate(simdat, 0, 1)
    SSEmean <- SSEmean + mean(dat)^2
    SSEmedian <- SSEmedian + median(dat)^2
  }
  
  return(list(n=n, x=x, MSEmean = SSEmean / N,
              MSEmedian = SSEmedian / N))
}
```

``` r
pvec <- seq(1, 30, by=1)

res <- NULL

for(i in 1:length(pvec)){
  res <- rbind(res, as.numeric(compare(30, pvec[i])))
}

res <- data.frame(res)
names(res) <- c("n", "x", "MSEmean", "MSEmedian")

plot(res$x, res$MSEmean, type="l", xlab="x", ylab="MSE",
     ylim=c(0,max(res$MSEmean)))
lines(res$x, res$MSEmedian,lty=2)
```

\#Problem 5 Show that in estimating \(\theta=E\sqrt{1-U^2}\) it is
better to use \(U^2\) rather than \(U\) as the control variate, where
\(U\sim U(0,1)\). To do this, use simulation to approximate the
necessary covariances. In addition, implement your algorithms in 

# Answer: your answer starts here…

``` r
#Your R codes/functions 
```

\#Problem 6 Obtain a Monte Carlo estimate of
\[\int_1^\infty \frac{x^2}{\sqrt{2\pi}} e^{-\frac{x^2}{2}} dx\] by
importance sampling and evaluate its variance. Write a 

# Answer: your answer starts here…

``` r
#Your R codes/functions 
```
