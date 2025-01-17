Activity - R Bootcamp
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

# Problem 1

Generate the following matrices with as little code as possible.

a\.

$$
\begin{pmatrix}
1 & 1 & 1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 5 & 5 & 5 & 1 \\
1 & 1 & 1 & 5 & 5 & 5 & 1 \\
1 & 1 & 1 & 1 & 1 & 1 & 1 
\end{pmatrix}
$$

b\.

$$
\begin{pmatrix}
1 & 2 & 3 & \cdots & 10 \\
2 & 4 & 6 & \cdots & 20 \\
3 & 6 & 9 & \cdots & 30 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
8 & 16 & 24 & \cdots & 80
\end{pmatrix}
$$

c\.

$$
\begin{pmatrix}
1 & 1 & 1 & 1 & 1 \\
4 & 4 & 4 & 4 & 4 \\
9 & 9 & 9 & 9 & 9 \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
121 & 121 & 121 & 121 & 121
\end{pmatrix}
$$

# Problem 1 Solution

a\. Your solution goes here.

b\. Your solution goes here.

c\. Your solution goes here.

# Problem 2

Here is an example of how to create a function in R:

``` r
P <- function(x){
  y <- 2*x^5 - 3*x^4 + x^3 - 10*x^2 + 1
  return(y)
}
```

I can evaluate the function at a specific value of $x$:

``` r
P(2)
```

    ## [1] -15

or at multiple values of $x$:

``` r
xx <- 3:7
P(xx)
```

    ## [1]   181  1185  4251 11521 26265

Write a function to evaluate the same polynomial,
$P(x)=2x^5-3x^4+x^3-10x^2+1$, but this time, let the inputs to the
function be a vector containing the coefficients of $P$ and then a
vector of values of $x$ at which you want to evaluate the polynomial. It
should look like

``` r
P <- function(a,x) {
  
  # Your code goes here
  
}
```

where I have used $a$ to represent the vector of coefficients in order
of highest degree to lowest degree (making sure to account for terms
that have coefficients of zero). The point of doing this is that now
don’t need to change our function each time we want to evaluate a
different polynomial. We can just pass in a different set of
coefficients. **Before you start coding**, make a plan (in words) for
how to do the calculation. Report your plan, write the code, use it to
evaluate the polynomial at $x = 3, 4, 5, 6, 7$, and verify that the
answers match what we computed above

Hints:

- Actually create a plan first. The real intellectual challenge of the
  problem is figuring out how to do the calculation in a nice, tight,
  efficient way. Turning the idea into code is only the second most
  important part.
- Avoid using a for-loop at all costs.
- The command `outer` with `FUN = "^"` will be helpful.
- My function to evaluate $P(x)$ was under 10 lines of brief code (not
  including comments).

# Problem 2 Solution

Your solution goes here.

# Key Commands

- `matrix` to create a matrix
- `:` (colon operator) to create a vector of integers
- `function` to define a function
- `length` to get length of a vector
- `rep` to copy a number/vector multiple times
- `t` to take transpose of a matrix or vector
- `%o%` to take outer product of two vectors
- `outer` to take outer product of two vectors (more flexible command)
- `rowSums` to get the sum of each row of a matrix
