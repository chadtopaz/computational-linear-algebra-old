Pset - Fundamentals of Linear Systems
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

- Am I in any way passing off as my own work any work that belongs to
  someone else?

Whether intentional or unintentional, any potential violations of
academic integrity will be referred to the Honor Committee.

------------------------------------------------------------------------

Load necessary packages:

``` r
library("Matrix")
library("igraph")
library("pracma")
```

### Problem 1

A real $n \times n$ matrix $\mathbf{Q}$ is *orthonormal* if

$$
\mathbf{Q}^{T} \mathbf{Q}=\mathbf{Q} \mathbf{Q}^T=\mathbf{I};~i.e., \mathbf{Q}^{-1}=\mathbf{Q}^T.
$$

Note: sometimes you will see these matrices just called *orthogonal
matrices*.

Show that $||\mathbf{Q}||_2=||\mathbf{Q}^{-1}||_2=1$, and therefore the
2-norm condition number of any orthonormal matrix $\mathbf{Q}$ is
$\kappa_2(\mathbf{Q})=||\mathbf{Q}||_2 ||\mathbf{Q}^{-1}||_2=1$.

### Problem 1 Solution

Your solution goes here.

### Problem 2

Consider the $n \times n$ square matrix

$$
A=\begin{pmatrix}
1 & -1 & -1 & -1 & \ldots & -1 \\
0 & 1 & -1 & -1 & \ldots & -1 \\
0 & 0 & 1 & -1 & \ldots & -1 \\
\vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\
0 & 0 & 0 & 0 & 0 & 1 
\end{pmatrix}.
$$

a\. Write a function that takes a value of $n$ as input and outputs the
matrix A above. Challenge yourself to be efficient in your coding when
you create the matrix. Looking at patterns and Googling how to create
them helps. I managed to create the matrix with no loops, in two lines
of code. Hint: the commands `upper.tri` and `diag` will be helpful.

b\. Use your function and the R command `kappa` to calculate the
approximate condition number $\kappa(\mathbf{A})$ for $n=1,\ldots,30$.
Plot $\log_{10}[\kappa(\mathbf{A})]$ as a function of $n$ and use the
commands `lm` and `abline` to plot a best fit line. How would you
describe the conditioning of the matrix as $n$ increases?

c\. Now choose $n=30$. Generate the matrix $\mathbf{A}$ and let
$\mathbf{b_1}$ be an $n \times 1$ vector of random numbers chosen
uniformly from 0 to 1. Solve $\mathbf{A}\mathbf{x}_1 = \mathbf{b}_1$
using any appropriate method that you want (including R’s built-in
capabilities). Now let
$\mathbf{b}_2 = \mathbf{b}_1 + (0,\ldots,0,0.001)^T$, that is, you leave
the first 29 elements the same as in $\mathbf{b}_1$ but add 0.001 to the
last element. Solve $\mathbf{A} \mathbf{x}_2 = \mathbf{b}_2$. Use the
command `Norm` to find the (approximate) 2-norm of
$\mathbf{x_1}-\mathbf{x_2}$ and discuss vis-a-vis your result from part
b. Also, to help build your intuition, find the magnitude of the
difference between the first coordinate of $\mathbf{x}_1$ and that of
$\mathbf{x}_2$.

### Problem 2 Solution

a\. Your solution goes here.

b\. Your solution goes here.

c\. Your solution goes here.

### Problem 3

Note: This problem is taken from Linear Algebra and its Applications, by
Lay et al.

<img src="https://github.com/chadtopaz/computationallineaaralgebra/raw/main/psets/heat.png" width="400">

An important concern in the study of heat transfer is to determine the
steady-state temperature distribution of a thin plate when the
temperature around the boundary is known. Assume the plate shown in the
figure above represents a cross section of a metal beam, with negligible
heat flow in the direction perpendicular to the plate. Let the variables
$x_1, x_2, \ldots, x_8$ denote the temperatures at nodes 1 through 8 in
the picture. In steady state, the temperature at a node is approximately
equal to the average of the four nearest nodes (to the left, above,
right, below).

a\. The solution to the approximate steady-state heat flow problem for
this plate can be written as a system of linear equations
$\mathbf{A} \mathbf{x}=\mathbf{b}$, where $x=(x_1, x_2, \ldots, x_8)^T$
is the vector of temperatures at nodes 1 through 8. Find the
$8 \times 8$ matrix $A$ and the vector $b$.

b\. Solve the system any way you want (using R) to find the unknown
temperatures.

### Problem 3 Solution

a\. Your solution goes here.

b\. Your solution goes here.

### Problem 4

This is a problem about network science. Networks are objects made up of
**vertices** (visualized as dots) that are connected by **edges**
(visualized as straight or curved lines, doesn’t matter which). A
network is said to be **undirected** if the edges have no direction to
them (no arrows), and **directed** if the directionality of the edges
matters (arrows present). As a matter of vocabulary, sometimes people
interchangeably use the word “graph” for network and “vertex” for node.

The following command loads a matrix $\mathbf{A}$ describing the western
power network of the United States. This is an undirected network. Each
element is zero or one. A one in row $i$ and column $j$ means that
component $i$ of the network is connected by an edge to component $j$.
This type of matrix is called a network’s **adjacency matrix**.

``` r
A <- readMM(gzcon(url("https://math.nist.gov/pub/MatrixMarket2/Harwell-Boeing/bcspwr/bcspwr10.mtx.gz"))) + 0
```

Above, the `readMM` and `gzcon` commands read the data. We add zero
(which seems strange!) for the following reason. R initially interprets
the matrix, which only contains ones and zeroes, as representing `TRUE`
and `FALSE` logical values, which is not what we want. However, once you
perform arithmetic on logical values, they get turned into their
numerical values.

It’s worth realizing that the adjacency matrix and a picture of the
network are just two ways of representing the same thing; if you know
one, you know the other. Let’s visualize the network using a package
called `igraph`. It may take a little bit of time to run the commands
below because the network is large. Note how we set the color and size
of the nodes. Here, `V` means “vertices”. In other words, we are
accessing the vertices `V` of the network `g`, creating properties
called `color` and `size` that will be used for plotting, and assigning
all nodes the color grey and the size 2.

``` r
g <- graph_from_adjacency_matrix(A, mode="undirected")
V(g)$color <- "grey"
V(g)$size <- 2
myLayout <- layout_nicely(g)
plot(simplify(g), layout=myLayout, vertex.color=V(g)$color, vertex.size=V(g)$size, vertex.label="")
```

<img src="Pset-Fundamentals-of-Linear-Systems_files/figure-gfm/unnamed-chunk-3-1.png" width="70%" />

a\. In the analysis of networks, one is often concerned with finding the
most important (most central, in some sense) component. One measure of
importance is called Katz centrality. The Katz centrality of the nodes,
$\mathbf{x}$, satisfies

$$
\mathbf{x} = \bigl((\mathbf{I} - \alpha \mathbf{A}^T)^{-1} - \mathbf{I} \bigr) \mathbf{1}
$$

where $\mathbf{I}$ is the identity matrix, $\mathbf{1}$ is a vector of
ones, and $\alpha$ is a parameter that we get to choose. You can just
take this definition as a given. The mathematical ideas behind the
definition of Katz centrality are perhaps best suited for a course
focusing specifically on network science but if you are interested, go
investigate the topic on your own or ask me to point you to some
sources.

Write the system in the form $\mathbf{M}\mathbf{x}=\mathbf{b}$. Then
take $\alpha = 0.05$ and solve for $\mathbf{x}$ using R’s `solve`
command. Your solution vector $\mathbf{x}$ will come out as a sparse
matrix type but just go ahead and convert it to a “regular” vector by
using `x <- as.numeric(x)`. Print out the largest element of
$\mathbf{x}$ using the `max` command so that I can verify your answer.
Make a histogram of all the Katz centralities.

b\. Re-plot the network using your same network layout as before, color
the most important node red and plot it with size 5. This way, the most
important node (at least, according to the Katz measure) will stand out
on your plot. Remember, you can set colors of nodes by assigning values
to the `colors` field of the vertices `V` of the network `g`. That is to
say, if I wanted to set the 10th node to be green, I could write
`V(g)$color[10] <- "green"`. Similarly, we can set sizes with commands
like `V(g)$size[10] <- 17`. Finally, we of course don’t want the 10th
node; we want whichever node turns out to have the largest Katz
centrality. Here, you can use the command `which.max` to find its index.
For example, if I wanted to know the index of the largest value of the
vector $(1,3,5,7,6,4,2)$, I could do

``` r
v <- c(1, 3, 5, 7, 6, 4, 2)
which.max(v)
```

    ## [1] 4

### Problem 4 Solution

a\. Your solution goes here.

b\. Your solution goes here.
