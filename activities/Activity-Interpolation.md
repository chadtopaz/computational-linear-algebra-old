Activity - Interpolation
================

------------------------------------------------------------------------

When you begin work during class, work with your assigned partner.
Please have only one electronic device open and work on it jointly. When
writing up this assignment, please remember that showing all of your
work and giving your reasoning are critical parts of achieving mastery.
If the course staff cannot tell how you solved a problem or finds leaps
in explanation or logic, the problem is not mastered. Finally, as a
matter of academic integrity, please make sure that you are positioned
to honestly answer yes to these questions:

- Have I disclosed everyone with whom I collaborated on this work? (Even
  if it is only my assigned partner.)

- Have I made a substantive intellectual contribution to the solution of
  every problem?

- Am I making sure not to pass off as my own work any work that belongs
  to someone else?

Whether intentional or unintentional, any potential violations of
academic integrity will be referred to the Honor Committee.

------------------------------------------------------------------------

Load necessary packages:

``` r
library(pracma)
```

### Problem 1

Consider the points (-2,0), (-1,14), (2,-4), (3,10).

a\. Find the interpolating polynomial in R, using the Vandermonde
method. Also, evaluate your polynomial at the point x = 1.5 by using the
built-in `horner` command.

b\. Find the interpolating polynomial by hand, using the Lagrange
method. Simplify your answer to show that it is the same polynomial you
obtained in part a. You can use WolframAlpha or a similar tool to help
you simplify it.

c\. Perform interpolation using the Lagrange method with the command
`lagrangeInterp`. Plot the interpolating polynomial using 30 equally
spaced points from x = -2 to x = 3. Make the polynomial appear as a
curve and add the original four sampled values as points.

### Problem 1 solution

a\. Your solution goes here.

b\. Your solution goes here.

c\. Your solution goes here.

### Problem 2

a\. Construct the interpolating polynomial $P(x)$ for the function
$f(x) \equiv 1/(1+x^2)$ on $[-2,2]$ using 100 equally spaced points.
Make a plot of the original function in blue (using 1000 equally spaced
points on the interval) and the interpolating polynomial in red on the
same axes, setting the vertical range of the plot to be $[0,1]$. State
the (approximate) infinity norm of the error, that is,
$||f(x)-P(x)||_\infty$.

b\. Repeat part (a) but using 100 Chebyshev nodes. Here, it’s preferable
to use the interpolation command `barylag` and you will need to slightly
modify your grid of $x$ points for plotting so that they don’t extend
past the range of the Chebyshev nodes. Try
`x <- seq(from = min(xdata), to = max(xdata), length = 1000)` where
`xdata` is your vector of x values for the Chebyshev nodes.

### Problem 2 Solution

a\. Your solution goes here.

b\. Your solution goes here.
