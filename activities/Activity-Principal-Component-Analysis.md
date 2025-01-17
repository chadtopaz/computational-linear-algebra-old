Activity - Principal Component Analysis
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
library(Matrix)
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.1     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.2     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.1     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ tidyr::expand() masks Matrix::expand()
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ✖ tidyr::pack()   masks Matrix::pack()
    ## ✖ tidyr::unpack() masks Matrix::unpack()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

### Problem 1

By completing this problem, you’ll hone your PCA skills in R. We’re
going to study nutritional information of food. Let’s load some data
from the USDA National Nutrient Database.

``` r
food <- read.csv("https://query.data.world/s/ixxtapv4y3rbkb6xo5c32ipljmdkor")
```

a\. Perform a principal component analysis based on the macronutrient
info, that is, protein, fat, carb, sugar, and fiber. What percent of
variation in the data do the first two principal components capture?

b\. For ease of bookkeeping, create a new data frame that has columns
`FoodGroup` and `ShortDescrip` from the original data set, and `PC1` and
`PC2` from your principal component analysis. Plot the data in
two-dimensional principal component space.

c\. That’s a lot of data! Just for funsies, subset your data to include
only the “Beef Products”,“Fruits and Fruit Juices”, and “Fats and Oils”
food groups. Plot these in two-dimensional principal component space,
colored by food group. If your data frame was called `myfood` you would
use the command

``` r
ggplot(myfood, aes(x = PC1, y = PC2, color = FoodGroup)) +
  geom_point()
```

Interpret what you see.

### Problem 1 Solution

a\. Your solution goes here.

b\. Your solution goes here.

c\. Your solution goes here.
