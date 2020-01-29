Homework 1 - Monte Carlo Methods
================
Jared Garfinkel - jsg2145

# Problem 1

The standard Laplace distribution has density
\[f(x) = 0.5e^{-|x|}, x \in
(-\infty, \infty)\]. Please provide an algorithm that uses the inverse
transformation method to generate a random sample from this
distribution. Use the \(U(0,1)\) random number generator in
\(\em{\bf{R}}\), write a \[\em{\bf{R}}\]-function to implement the
algorithm. Use visualization tools to validate your algorithm (i.e.,
illustrate whether the random numbers generated from your function
truely follows the standard Laplace distribution.)

# Answer: your answer starts here…

``` r
#Your R codes/functions 
```

\#Problem 2

Use the inverse transformation method to derive an algorithm for
generating a Pareto random number with \(U\sim U(0,1)\), where the
Pareto random number has a probability density function
\[f(x; \alpha, \gamma)=\frac{\gamma\alpha^{\gamma}}{x^{\gamma+1}} I\{x\ge \alpha\}\]
with two parameters \(\alpha >0\) and \(\gamma>0\). Use visualization
tools to validate your algorithm (i.e., illustrate whether the random
numbers generated from your function truely follows the target
distribution.)

# Answer: your answer starts here…

``` r
#Your R codes/functions 
```

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
#Your R codes/functions 
```

\#Problem 4

Develop two Monte Carlo methods for the estimation of
\(\theta=\int_0^1 e^{x^2} dx\) and implement in 

# Answer: your answer starts here…

``` r
#Your R codes/functions 
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
