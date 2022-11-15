Load necessary packages:

    library(expm)
    library(pracma)
    library(igraph)

### Problem 1

In this problem, you’ll analyze a Markov chain model that has states
where you can get stuck, known as absorbing states.

You are headed to Las Vegas. Your plan is to bring $100 of gambling money, gamble\$ 1 at a time, and stop gambling when you hit &lt;pre&gt;$0 or when you
hit $
</pre>

1.  Let’s assume at first that the probability of winning each game is
    50% (a naive assumption).

a\. Let’s model your earnings with a Markov chain. What are the states?
You don’t need to include it in your response, but draw a state diagram
and label the edges with probabilities. Then form the transition matrix $\mathbf{P}$. To help me check your answer, run these commands on $\mathbf{P}$
:

    colSums(P)
    image(P)

b\. Compute the probability that you have &lt;pre&gt;$105 after placing
10 different $
</pre>

1 bets.

c\. Use `eigen` to find the eigenvalues and eigenvectors of $\mathbf{P}$
. What do you notice? Can you explain why the eigenvectors associated
with the eigenvalue 1 are steady-state distributions?

d\. Once you reach &lt;pre&gt;$0 or $
</pre>
200, you cannot reach any other state. We say that those two states are
**absorbing** states. We are interested in the absorption probabilities;
i.e., what is the probability that you reach &lt;pre&gt;$0 before $
</pre>
200, and vice versa? To answer this, we can first reorder the state
labels so that the absorption states
&lt;pre&gt;0*a**n**d*$ &lt; /*p**r**e* &gt; 200*a**r**e**t**h**e**f**i**r**s**t**t**w**o**l**i**s**t**e**d*, *a**n**d**t**h**e**n**e**v**e**r**y**t**h**i**n**g**e**l**s**e*.*T**h**a**t**i**s*, *w**e**c**a**n**r**e**a**r**r**a**n**g**e**t**h**e**t**r**a**n**s**i**t**i**o**n**m**a**t**r**i**x* &lt; *p**r**e*&gt;$
</pre>

into the following form:
 $$\mathbf{P}=\begin{bmatrix}\mathbf{I} &\mathbf{S}\\\mathbf{0}  &\mathbf{R}\end{bmatrix},$$
</pre>

where

-   <pre>$\mathbf{I}$
    is a 2x2 identity matrix

-   <pre>$\mathbf{0}$
    is a
 $2\times (N-2)$
    matrix of zeros

-   <pre>$\mathbf{S}$
    is a
 $(N-2)\times 2$
    matrix giving the transition probabilities from the non-absorbing
    states (called the **transient** states) to the absorbing states,
    and

-   <pre>$\mathbf{R}$
    is the matrix of transition probabilities from the transient states
    to other transient states.

To find the absorption probabilities, once you have $\mathbf{S}$, $\mathbf{R}$, and $\mathbf{I}$, compute the **fundamental matrix** $\mathbf{F} =\mathbf{S}(\mathbf{I}_{n-2} -\mathbf{R})^{-1}$. The probability of absorbing into state $i$ (say &lt;pre&gt;$0 in this case) starting from transient state
 &lt; /*p**r**e* &gt; *j* &lt; *p**r**e*&gt; (say $
</pre>
100 in this case) is $(\mathbf{F})_{ij}$. If you start with &lt;pre&gt;$100, what is the probability of reaching
$
</pre>
200 before going broke? How does it change if you start with
&lt;pre&gt;$120 and only aim to make $
</pre>

80 profit?

e\. Does your probability of reaching &lt;pre&gt;$200 before going broke
change if you bet $
</pre>

10 at a time or $100 at a time?

f\. The actual odds of winning a game in Vegas are not equal to 50%!
Let’s say you are betting on red at the roulette wheel. Assuming it is a
wheel with a double zero, your chances of winning each game are $18/38\approx 47.4$ %. Now does your probability of reaching &lt;pre&gt;$200 before going
broke change if you bet $
</pre>

10 at a time or $100 at a time? What is the best strategy?

### Problem 1 Solution

a\. Your solution goes here.

b\. Your solution goes here.

c\. Your solution goes here.

d\. Your solution goes here.

e\. Your solution goes here.

f\. Your solution goes here.

### Problem 2

Russian historians often attribute the dominance and rise to power of
Moscow to its strategic position on medieval trade routes (see below).
Others argue that sociological and political factors aided Moscow’s rise
to power, and thus Moscow did not rise to power strictly because of its
strategic location on the trade routes. You are to use eigenvectors to
analyze this question.

![](route.png)

Here is the list of cities and their index numbers for an adjacency
matrix I will give you.

<table>
<thead>
<tr class="header">
<th style="text-align: center;">Index</th>
<th style="text-align: left;">City</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">1</td>
<td style="text-align: left;">Novogrod</td>
</tr>
<tr class="even">
<td style="text-align: center;">2</td>
<td style="text-align: left;">Vitebsk</td>
</tr>
<tr class="odd">
<td style="text-align: center;">3</td>
<td style="text-align: left;">Smolensk</td>
</tr>
<tr class="even">
<td style="text-align: center;">4</td>
<td style="text-align: left;">Kiev</td>
</tr>
<tr class="odd">
<td style="text-align: center;">5</td>
<td style="text-align: left;">Chernikov</td>
</tr>
<tr class="even">
<td style="text-align: center;">6</td>
<td style="text-align: left;">Novogrod Severskiy</td>
</tr>
<tr class="odd">
<td style="text-align: center;">7</td>
<td style="text-align: left;">Kursk</td>
</tr>
<tr class="even">
<td style="text-align: center;">8</td>
<td style="text-align: left;">Bryansk</td>
</tr>
<tr class="odd">
<td style="text-align: center;">9</td>
<td style="text-align: left;">Karachev</td>
</tr>
<tr class="even">
<td style="text-align: center;">10</td>
<td style="text-align: left;">Kozelsk</td>
</tr>
<tr class="odd">
<td style="text-align: center;">11</td>
<td style="text-align: left;">Dorogobusch</td>
</tr>
<tr class="even">
<td style="text-align: center;">12</td>
<td style="text-align: left;">Vyazma</td>
</tr>
<tr class="odd">
<td style="text-align: center;">13</td>
<td style="text-align: left;">“A”</td>
</tr>
<tr class="even">
<td style="text-align: center;">14</td>
<td style="text-align: left;">Tver</td>
</tr>
<tr class="odd">
<td style="text-align: center;">15</td>
<td style="text-align: left;">Vishny Totochek</td>
</tr>
<tr class="even">
<td style="text-align: center;">16</td>
<td style="text-align: left;">Ksyatyn</td>
</tr>
<tr class="odd">
<td style="text-align: center;">17</td>
<td style="text-align: left;">Uglich</td>
</tr>
<tr class="even">
<td style="text-align: center;">18</td>
<td style="text-align: left;">Yaroslavl’</td>
</tr>
<tr class="odd">
<td style="text-align: center;">19</td>
<td style="text-align: left;">Rostov</td>
</tr>
<tr class="even">
<td style="text-align: center;">20</td>
<td style="text-align: left;">“B”</td>
</tr>
<tr class="odd">
<td style="text-align: center;">21</td>
<td style="text-align: left;">“C”</td>
</tr>
<tr class="even">
<td style="text-align: center;">22</td>
<td style="text-align: left;">Suzdal</td>
</tr>
<tr class="odd">
<td style="text-align: center;">23</td>
<td style="text-align: left;">Vladimir</td>
</tr>
<tr class="even">
<td style="text-align: center;">24</td>
<td style="text-align: left;">Nizhny Novogrod</td>
</tr>
<tr class="odd">
<td style="text-align: center;">25</td>
<td style="text-align: left;">Bolgar</td>
</tr>
<tr class="even">
<td style="text-align: center;">26</td>
<td style="text-align: left;">Isad’-Ryazan</td>
</tr>
<tr class="odd">
<td style="text-align: center;">27</td>
<td style="text-align: left;">Pronsk</td>
</tr>
<tr class="even">
<td style="text-align: center;">28</td>
<td style="text-align: left;">Dubok</td>
</tr>
<tr class="odd">
<td style="text-align: center;">29</td>
<td style="text-align: left;">Elets</td>
</tr>
<tr class="even">
<td style="text-align: center;">30</td>
<td style="text-align: left;">Mtsenk</td>
</tr>
<tr class="odd">
<td style="text-align: center;">31</td>
<td style="text-align: left;">Tula</td>
</tr>
<tr class="even">
<td style="text-align: center;">32</td>
<td style="text-align: left;">Dedoslavl’</td>
</tr>
<tr class="odd">
<td style="text-align: center;">33</td>
<td style="text-align: left;">Perselavl’</td>
</tr>
<tr class="even">
<td style="text-align: center;">34</td>
<td style="text-align: left;">Kolomna</td>
</tr>
<tr class="odd">
<td style="text-align: center;">35</td>
<td style="text-align: left;">Moscow</td>
</tr>
<tr class="even">
<td style="text-align: center;">36</td>
<td style="text-align: left;">Mozhaysk</td>
</tr>
<tr class="odd">
<td style="text-align: center;">37</td>
<td style="text-align: left;">Dmitrov</td>
</tr>
<tr class="even">
<td style="text-align: center;">38</td>
<td style="text-align: left;">Volok Lamskiy</td>
</tr>
<tr class="odd">
<td style="text-align: center;">39</td>
<td style="text-align: left;">Murom</td>
</tr>
</tbody>
</table>

The following code block loads the adjacency matrix into the matrix $\mathbf{A}$ and plots the graph. The adjaceny matrix has an entry $A_{i,j}=1$ if the cities indexed $i$ and $j$ are connected in the network, and $0$
otherwise. I’m suppressing the appearance of the codeblock in the
markdown output because it includes a lot of lines of ones and zeros.
![](Pset-Eigenvalues-II_deleteme_files/figure-markdown_strict/unnamed-chunk-30-1.png)

Let $\mathbf{B}=\mathbf{A}+\mathbf{I}$ be the **augmented adjacency matrix** and let $\mathbf{x}=(1,1,\ldots,1)^{\top}$. Think about computing $\mathbf{B}\mathbf{x}$, $\mathbf{B}^2\mathbf{x}$, $\mathbf{B}^3\mathbf{x}$. The entries are nonnegative integers, and they can be interpreted as
counting something. The ij-th entry of the matrix $\mathbf{B}^k$ represents the number of paths of length $k$ or less from vertex $i$ to vertex $j$. As $k$ grows, the normalized version of $\mathbf{B}^k x$ converges to the dominant eigenvector of the augmented adjacency matrix,
and is therefore a good measure of accessibility, because it represents
the total number of paths of length $k$
or less from each vertex to all of the other vertices. This idea is
developed at length in the article [“Linear Algebra in Geography:
Eigenvectors of
Networks,”](http://www.jstor.org/stable/2689388?seq=1#page_scan_tab_contents)
by Philip D. Straffin, Jr. in Mathematics Magazine, November 1980.

The matrix $\mathbf{B}$ turns out to be primitive, so the Perron-Frobenius theorem applies and
there is a dominant eigenvector. **Gould’s index of accessibility** is
just the dominant eigenvector of $\mathbf{B}$, normalized so that the entries sum to one. That is to say, if $\mathbf{v}$
is the dominant eigenvector, then Gould’s index is

    v/sum(v)

Compute Gould’s index for this problem and answer the historians’
question.

### Problem 2 Solution

Your solution goes here.