---
title: "Sample Mathematics Aptitude Test"
summary: "Exercise solutions for an online Sample Mathematics Aptitude Test"

date: 2020-08-03T00:00:00
lastmod: 2020-08-03T00:00:00

draft: false  # Is this a draft? true/false

---

This page will contain selected solutions to exercises from the Sample Mathematics Aptitude Test 
found online [here](https://gchq-careers.co.uk/media/30806/Sample_Maths_Aptitude_Test.pdf).

{{< toc >}}

## Short Questions

### SQ1. Digital clock displays

Consider a 12 hour digital clock (one that takes values from 00:00 to 11:59). Look at it at a random point during a 12 hour period.
- What is the probability that you see at least one digit taking the value '1'?
- What is the probability that you see exactly one digit taking the value '1'?

#### SQ1 Solution

All 720 possible clock displays can be expressed in the form $hh$:$m_{1}m_{2}$,
where $hh$ denotes the hour display, ranging from $00$ to $11$,
and $m_{1}m_{2}$ represents the minute display, with the $m_{1}$ digit ranging from $0$ to $5$ and $m_{2}$ ranging from $0$ to $9$.

Sampling a clock display at random can be split into independently sampling values of $hh$, $m_{1}$, and $m_{2}$ uniformly from their possible values.

To calculate the probability of at least one '1' digit on the clock display, 
we take the complement of the probability of seeing no '1' digits on the clock display.
$$
P(\text{at least one digit is '1'}) = 1 - P(\text{no digits are '1'})
$$
Then, by independence, we have 
$$
P(\text{no digits are '1'}) = P(hh \not\in \\{ 01, 10, 11 \\})P(m_{1} \neq 1)P(m_{2} \neq 1) = 
\frac{9}{12} \times \frac{5}{6} \times \frac{9}{10} = \frac{9}{16}
$$
Therefore, $$P(\text{at least one digit is '1'}) = 1 - \frac{9}{16} = \frac{7}{16}$$
Next, to calculate the probability of exactly one '1' digit on the clock display we split this into the mutually exclusive cases
depending on where the single '1' digit appears, either in the value of $hh$, $m_{1}$, or $m_{2}$. This yields
$$
\\begin{split}
P(\text{exactly one digit is '1'}) 
 & = P(hh \in \\{ 01, 10 \\})P(m_{1} \neq 1)P(m_{2} \neq 1) \\\\
 & + P(hh \not\in \\{ 01, 10, 11 \\})P(m_{1} = 1)P(m_{2} \neq 1) \\\\
 & + P(hh \not\in \\{ 01, 10, 11 \\})P(m_{1} \neq 1)P(m_{2} = 1) \\\\
 & = \frac{2}{12} \cdot \frac{5}{6} \cdot \frac{9}{10} + 
     \frac{9}{12} \cdot \frac{1}{6} \cdot \frac{9}{10} + 
     \frac{9}{12} \cdot \frac{5}{6} \cdot \frac{1}{10} \\\\
 & = \frac{3}{10}
\\end{split}
$$

Therefore, when randomly sampling from the display of a 12 hour digital clock taking values from 00:00 to 11:59,
one would expect to see at least one digit taking the value '1' on the display $43.75\\%$ of the time,
and one would expect to see exactly one digit taking the value '1' on the display $30\\%$ of the time.

Tags: Probability

Related reading:
- [Benford's law](https://en.wikipedia.org/wiki/Benford%27s_law)

### SQ2. Prime factors and greatest common divisors

Let $a, b$ be positive integers and let $p$ be a prime factor of $a^{b} − 1$.
Show that either $\gcd(p, a − 1)$ or $\gcd(b, p − 1)$ must be greater that $1$.

#### SQ2 Solution

First, recall two important facts that we will use in the proof: [Fermat's Little Theorem](https://en.wikipedia.org/wiki/Fermat%27s_little_theorem) 
and [Bézout's identity](https://en.wikipedia.org/wiki/B%C3%A9zout%27s_identity). We will also draw on ideas from elementary group theory, 
in particular the notion of the [order](https://en.wikipedia.org/wiki/Order_(group_theory)) of a group element, 
and properties of $\mathbb{Z}/p\mathbb{Z}$.

By the assumption that $p$ divides $a^{b} − 1$ it follows that $p$ does not divide $a$.
Otherwise, $p$ would divide both $a^{b}$ and $a^{b} − 1$ and hence also their difference $a^{b} - (a^{b} − 1) = 1$, 
but $1$ does not have any prime divisors, so $p$ cannot divide $a$.

Note that since $p$ is prime, $\gcd(p, a − 1)$ is greater than $1$ if and only if $\gcd(p, a − 1) = p$, or equivalently,
if and only if $p$ divides $a - 1$.

**Case 1.** Suppose $\gcd(p, a − 1) = 1$, so $p$ does not divide $a - 1$. We will show that we must have $\gcd(b, p − 1) > 1$.
By our main assumption, $a^{b} \equiv 1 \\ (\mathrm{mod}\\ p)$. As $p$ does not divide $a$, we may apply Fermat's Little Theorem to deduce that
$a^{p - 1} \equiv 1 \\ (\mathrm{mod}\\ p)$. It follows that the (multiplicative) order of $a$ in $\left( \mathbb{Z}/ p \mathbb{Z} \right)^{\times}$
is a common factor of $b$ and $p - 1$, so $\mathrm{order}(a) \le \gcd(b, p − 1)$.
As we assume $p$ does not divide $a - 1$, we have $a \not\equiv 1 \\ (\mathrm{mod}\\ p)$, 
and in particular $\mathrm{order}(a) > 1$. Hence, $$\gcd(b, p − 1) \ge \mathrm{order}(a) > 1$$ as required.

**Case 2.** Now, suppose $\gcd(b, p − 1) = 1$. We will show that $p$ divides $a - 1$ and hence $\gcd(p, a − 1) = p > 1$.
By Bézout's identity, there exist integers $x, y$ such that $bx + (p - 1)y = \gcd(b, p − 1) = 1$.
Then $$a = a^{1} = a^{bx + (p - 1)y} = (a^{b})^{x}(a^{p - 1})^{y} \equiv 1^{x}1^{y} = 1 \\ (\mathrm{mod}\\ p)$$
once again using that $a^{b} \equiv 1 \\ (\mathrm{mod}\\ p)$, and $a^{p - 1} \equiv 1 \\ (\mathrm{mod}\\ p)$ by Fermat's Little Theorem.
<br>Hence $a - 1$ is divisible by $p$ as required.

Tags: Modular arithmetic, Number theory, Group theory

### SQ3. Estimating coin bias

Alice and Bob are given a set of five biased coins. 
They both estimate the probability that each coin will show a head when flipped, and each coin is then flipped once. 
These are the estimates and values observed:

| Coin | Alice's estimates | Bob's estimates | Observed |
|------|-------------------|-----------------|----------|
| 1    | 0.4               | 0.2             | Heads    |
| 2    | 0.7               | 0.8             | Heads    |
| 3    | 0.2               | 0.3             | Tails    |
| 4    | 0.9               | 0.6             | Tails    |
| 5    | 0.4               | 0.3             | Heads    |

Whom would you say is better at estimating the bias of the coins, and why?

#### SQ3 Solution

By coding "Heads" as 1 and "Tails" as 0, we can calculate the (absolute) error and the squared error for each estimate 
and sum these errors over the five coins. The results are shown in the table below.

| Coin | Alice's estimates | Bob's estimates | Observed | Is "Heads"? | $\mathrm{Err}(A)$ | $\mathrm{Err}(B)$ | $\mathrm{Err}(A)^{2}$ | $\mathrm{Err}(B)^{2}$ |
|------|-------------------|-----------------|----------|-------------|-------------------|-------------------|-----------------------|-----------------------|
| 1    | 0.4               | 0.2             | Heads    | 1           | 0.6               | 0.8               | 0.36                  | 0.64                  |
| 2    | 0.7               | 0.8             | Heads    | 1           | 0.3               | 0.2               | 0.09                  | 0.04                  |
| 3    | 0.2               | 0.3             | Tails    | 0           | 0.2               | 0.3               | 0.04                  | 0.09                  |
| 4    | 0.9               | 0.6             | Tails    | 0           | 0.9               | 0.6               | 0.81                  | 0.36                  |
| 5    | 0.4               | 0.3             | Heads    | 1           | 0.6               | 0.7               | 0.36                  | 0.49                  |
|      |                   |                 |          | **Total**   | 2.6               | 2.6               | 1.66                  | 1.62                  |

We can see from the table of results that, in terms of absolute error both Alice and Bob are equally bad at predicting the outcome of the coin flip,
where their coin bias estimate is used as a proxy for the most likely outcome of a single flip. However, when comparing the sum of squared errors,
which will more heavily penalize overconfidence in an incorrect outcome, we find that Bob is marginally better than Alice 
at predicting the outcome of the coin flips (and hence estimating the bias of the coins?).

#### SQ3 Discussion

It should be noted that both Alice and Bob performed slightly worse than a totally naive prior estimate of a $0.5$ probability of landing on heads 
for each coin, which might cast doubts on their predictive skills if the experiment was more powerful.
One might also like to examine the level of statistical correlation between the predictions and the outcomes, in case one's predictions are
systematically wrong which could be helpful in this binary case/for excluding an unlikely outcome.

It could be said that a single flip each of five independent biased coins is not particularly strong evidence for determining forecasting skills.
To test one's ability to predict the bias of a coin (from, say, physical examination beforehand) it would make sense to perform multiple flips
of each biased coin so that an observed estimate $\text{Heads} / \text{Flips}$ of the bias could be compared to the predictor's estimate.
Testing more predictions by flipping a larger set of coins would also increase the information gained from the experiment.

A more rigorous analysis from the viewpoint of information theory or Bayesian statistics might yield more insight into this scenario.
This scenario can also be related to examining the predictive power of a binary classifier in machine learning.

This mean squared error for forecasts is actually more commonly known as the [Brier score], 
whose definition extends to mutually exclusive multi-category forecasts. 
This [article][Superforecasting, HBR], written by Paul J. H. Schoemaker and Philip E. Tetlock for the Harvard Business Review, 
explains the benefits of better organisational decision making for businesses and suggests general methods to achieve them,
introducing the Brier score as a way to measure forecasting skills, whilst emphasising the importance of carefully tracking the analysis process 
used to make predictions so that they can be improved where possible through trial and error. Techniques for reducing cognitive biases, and
producing forecasts in teams was also shown to produce better results. 
For more information on [The Good Judgement Project], the study on which the above article is based, 
see also the 2015 book by Philip E. Tetlock and Dan Gardner, [Superforecasting: The Art and Science of Prediction][Superforecasting book].

Shortcomings of the Brier score when it comes to differential penalization for false-positive and false-negative misclassifications
(as opposed to an overall measure of forecasting accuracy), which may be relevant in clinical scenarios where making a correct or incorrect
prediction come with different levels of utility, are addressed in the following [article][Brier score and clinical utility]. 
The authors of this article recommend an alternative method for comparing clinical diagnostic tests or prediction models called *net benefit*.
Limitations in comparing forecasting performance on very rare events are also discussed on the [Wikipedia page for Brier score][Brier score].
Related reading on the **sensitivity/recall** (true positive rate) and **specificity** (true negative rate) and other metrics for judging
binary classification prediction models can be found [here][Sensitivity and specificity] and 
[here](https://towardsdatascience.com/evaluating-categorical-models-ii-sensitivity-and-specificity-e181e573cff8).

Tags: Forecasting, Statistics, Information theory, Machine Learning

References:
- [Brier score]
- [Sensitivity and specificity]

Related Reading:
- [Superforecasting: How to Upgrade Your Company's Judgment][Superforecasting, HBR]
- [The Good Judgement Project]
- [The Brier score does not evaluate the clinical utility of diagnostic tests or prediction models][Brier score and clinical utility]
- [Evaluating Forecasting Methods](https://repository.upenn.edu/cgi/viewcontent.cgi?article=1182&context=marketing_papers)
- [The probabilistic elicitation of subjective data](https://www.gov.uk/government/publications/the-probabilistic-elicitation-of-subjective-data)
- [Analytical Quality Assurance book](https://www.gov.uk/government/publications/the-aqua-book-guidance-on-producing-quality-analysis-for-government)

[Brier score]: https://en.wikipedia.org/wiki/Brier_score
[Superforecasting, HBR]: https://hbr.org/2016/05/superforecasting-how-to-upgrade-your-companys-judgment
[The Good Judgement Project]: https://en.wikipedia.org/wiki/The_Good_Judgment_Project
[Superforecasting book]: https://en.wikipedia.org/wiki/Superforecasting:_The_Art_and_Science_of_Prediction
[Brier score and clinical utility]: https://diagnprognres.biomedcentral.com/articles/10.1186/s41512-017-0020-3
[Sensitivity and specificity]: https://en.wikipedia.org/wiki/Sensitivity_and_specificity

### SQ4. A devilish question

Find an example of a function $f$ from $[0, 1]$ to $[0, 1]$ with the following properties:
1. $f$ is continuous;
2. $f(0) = 0$;
3. $f(1) = 1$;
4. $f(x)$ is locally constant almost everywhere.

#### SQ4 Solution

Whether you can answer this question without the aid of the internet may depend on how well/how recently you remember your second year 
undergraduate calculus/analysis course. An example of such a function is the [Cantor function](https://en.wikipedia.org/wiki/Cantor_function)
which "is a notorious counterexample in analysis, because it challenges naive intuitions about continuity, derivative, and measure."

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/4/49/CantorEscalier.svg" title="Devil's staircase" lightbox="false" width=300px >}}

The [definition of the Cantor function by iterative construction](https://en.wikipedia.org/wiki/Cantor_function#Iterative_construction)
makes clear that the function has the desired properties, in particular it is continuous as the uniform limit of a sequence of continuous functions.
More interesting information about the related [Cantor set](https://en.wikipedia.org/wiki/Cantor_set) is also available online.

Tags: Analysis, Measure theory, point-set topology

### SQ5. A piece of cake

You have a large rectangular cake, and someone cuts out a smaller rectangular piece from
the middle of the cake at a random size, angle and position in the cake (see the picture
below). Without knowing the dimensions of either rectangle, using one straight (vertical)
cut, how can you cut the cake into two pieces of equal area?

<canvas id="cakeProblem">Your browser does not support the HTML5 canvas tag.</canvas>

#### SQ5 Solution

For a while I was confused about the 'vertical' restriction on the straight cut when looking at this picture, but seeing it as the cross section when
viewed from above I realised that 'vertical' refers to the hidden $z$-axis of the cake rather than the $y$-axis of the cross section in the image.
This is to avoid slicing the cake horizontally into top and bottom pieces of equal area, which would be inappropriate for a cake with icing.

Any straight line through the midpoint of a rectangle will cut it into two pieces of equal area regardless of the angle of the line.
Therefore it suffices to cut along the (unique) line passing through both the midpoint of the original cake rectangle and the 
midpoint of the rectangular shaped hole left by the removed piece of cake.

The solution to this question is satisfying to think about, and probably worth trying for yourself at home so you can have your cake and eat it too.

<canvas id="cakeSolution">Your browser does not support the HTML5 canvas tag.</canvas>

<script>
function makeCake(canvasId) {
  var canvas = document.getElementById(canvasId);
  // Canvas size on page
  canvas.width = "1000";
  canvas.height = "210";
  
  // Drawing setup
  var ctx = canvas.getContext("2d");
  ctx.translate(250, 5);
  ctx.fillStyle = "#c3c3c3";
  ctx.strokeStyle = "#000000";
  
  // Draw rectangle with border
  ctx.fillRect(0,0,450,200);
  ctx.strokeRect(0,0,450,200);
  
  // Cut out rectangular piece
  ctx.rotate(Math.PI / 3);
  ctx.clearRect(100, -50, 100, 50);
  ctx.strokeRect(100, -50, 100, 50);
  
  // Reset axes
  ctx.rotate(- Math.PI / 3);
  ctx.translate(-250, -5);
}

function sliceCake(canvasId) {
  // Drawing setup
  var canvas = document.getElementById(canvasId);
  var ctx = canvas.getContext("2d");
  ctx.translate(250, 5);
  ctx.strokeStyle = "#000000";
  ctx.fillStyle = "#000000";
  
  // Draw line
  ctx.moveTo(0, 130.51);
  ctx.lineTo(450, 69.49);
  //ctx.moveTo(225, 100);
  //ctx.lineTo(25 * (3 + Math.sqrt(3) / 2), 12.5 * (6 * Math.sqrt(3) - 1));
  //ctx.rotate(Math.PI / 3);
  //ctx.lineTo(150, -25);
  ctx.stroke();
}

makeCake("cakeProblem");
makeCake("cakeSolution");
sliceCake("cakeSolution");
</script>

Tags: Geometry

### SQ6. Random number generation

A random number generator produces independent random variates $x_{0}, x_{1}, x_{2}, \ldots$ drawn
uniformly from $[0, 1]$, stopping at the first $x_{T}$ that is strictly less than $x_{0}$. Prove that
the expected value of $T$ is infinite. Suggest, with a brief explanation, a plausible value
of $P(T = \infty)$ for a real-world (pseudo-)random number generator implemented on a computer.

#### SQ5 Solution

We first consider the expected stopping time conditional on the value of $x_{0}$, 
i.e. the expected value of $T$ given that $x_{0} = p$ for some $p \in [0, 1]$.
Once we have a formula for $\mathbb{E}[T | x_{0} = p]$, we may integrate to find $$\mathbb{E}[T] = \int_{0}^{1} \mathbb{E}[T | x_{0} = p] dp$$
as $x_{0}$ is uniformly distributed on $[0, 1]$.

We may calculate $\mathbb{E}[T | x_{0} = p]$ in two different ways: The first is to consider the probability of stopping at a given time $T$,
which occurs when $x_{T} < x_{0}$ and $x_{i} \ge x_{0}$ for $i = 1, \ldots, T - 1$, and using this in the definition of expectation:
$$
\mathbb{E}[T | x_{0} = p] = \sum_{t = 1}^{\infty} t P(T = t | x_{0} = p) = 
\sum_{t = 1}^{\infty} t P(x_{T} < p) \prod_{i = 1}^{t - 1} P(x_{i} \ge p) = 
\sum_{t = 1}^{\infty} t p (1 - p)^{t - 1}
$$
The right hand side is a special case of an [Arithmetico–geometric sequence], for which [Swain][Swain, 1994] has a wonderful picture proof 
(originally published in Mathematics Magazine in 1994, and reproduced on the Wolfram Mathworld website 
[here](https://mathworld.wolfram.com/GabrielsStaircase.html)) demonstrating the formula 
$$\sum_{k=1}^{\infty} k r^{k} = r + 2r^{2} + 3r^{3} + \ldots = \frac{r}{(1 - r)^{2}} \text{ for } 0 \le r < 1.$$
![](https://mathworld.wolfram.com/images/eps-gif/GabrielsStaircase_1000.gif)
The picture proof proceeds by computing the same area in two different ways, applying the trick for deriving the formula of a geometric series: 
If $S_{n} = \sum_{k=1}^{n-1} r^{k-1} = 1 + r + r^{2} + \ldots + r^{n - 1}$, then $(1 - r) S_{n} = 1 - r^{n}$, so $S_{n} = \frac{1 - r^{n}}{1 - r}$
and $\sum_{k=1}^{\infty} r^{k-1} = \lim_{n \to \infty} S_{n} = \frac{1}{1 - r}$ for $0 \le r < 1$. This summation trick is applied twice,
first in calculating the area of each horizontal row, and then in summing up over all rows after taking out a common factor.

We apply the formula to our summation to find that $$\mathbb{E}[T | x_{0} = p] = \sum_{t = 1}^{\infty} t p (1 - p)^{t - 1} = \frac{1}{p}.$$

Alternatively, we may analyse the problem from the perspective of the[hitting time][Markov Chain hitting times] of an [Absorbing Markov Chain].
The $x_{1}, x_{2}, \ldots$ are independent uniform random variates, so the process of successively sampling $x_{i}$, stopping when $x_{i} < x_{0}$, 
is memoryless. 

We may equivalently formulate the problem as flipping a biased coin with fixed probability $p$ of landing on heads, and calculating
the expected number of coin tosses before observing the coin landing on heads; coin flips are not affected by previous (or future) coin flips.

Let $T_{i}$ denote the number of remaining draws before stopping after already drawing $x_{0}, \ldots, x_{i}$. 
By the memorylessness property, if the first coin flip lands on tails (i.e. if $x_{1} \ge x_{0}$), then expected remaining number of flips afterwards
has not changed compared to before making the flip, so $\mathbb{E}[T_{1} | x_{1} \ge x_{0}, x_{0} = p] = \mathbb{E}[T_{0} | x_{0} = p]$.

Following this line of reasoning when considering all possible outcomes of drawing $x_{1}$, we deduce that:
$$
\mathbb{E}[T_{0} | x_{0} = p] = 
1 + \mathbb{E}[T_{1} | x_{1} < x_{0}, x_{0} = p] P(x_{1} < p) + \mathbb{E}[T_{1} | x_{1} \ge x_{0}, x_{0} = p] P(x_{1} \ge p)
$$
$$
 = 1 + 0 \cdot p + \mathbb{E}[T_{1} | x_{1} \ge x_{0}, x_{0} = p] (1 - p) = 1 + (1 - p) \mathbb{E}[T_{0} | x_{0} = p]
$$
Rearranging this equation once again yields the result: $\mathbb{E}[T_{0} | x_{0} = p] = \frac{1}{p}$.

Now that we know the expected stopping time conditional on the value of $x_{0}$, we can integrate over all the possible values of $x_{0}$, uniformly 
weighted, to find that $$\mathbb{E}[T] = \int_{0}^{1} \mathbb{E}[T | x_{0} = p] dp = \int_{0}^{1} \frac{1}{p} dp$$
which diverges to infinity, and so we have shown that the expected value of $T$ is infinite, as required.

When dealing with a real-world (pseudo-)random number generator implemented on a computer, the number of possible values for the $x_{i}$ is finite,
and a good implementation will give a roughly uniform distribution among a (large) discrete set of values in the interval $[0, 1]$.
Therefore, a plausible value for $P(T = \infty)$ is $P(x_{0} = 0)$, in which case we can be certain the process will not stop.
The actual value of $P(x_{0} = 0)$ may depend on the kind of (pseudo-)random number generator used and possibly on incidences of numerical underflow,
but can be reasonably approximated by the reciprocal of the number of distinct (pseudo-)random values that can be generated.
For a simple example of a pseudo-random number generator based on modular arithmetic and an affine linear transform, 
see [here](https://en.wikipedia.org/wiki/Linear_congruential_generator).

#### Aside

More pictorial proofs regarding ['staircase series'][staircase series] can be found in another Mathematics Magazine article published in 2018, whilst 
an excellent collection of other proofs without words can be found at the Art of Problem Solving [online wiki][AOPS: Proofs without words], including
a proof of the formula for infinite geometric series using similar triangles. 
Wolfram Alpha also has references to more pictorial proofs [here][Wolfram Alpha: Proof without words].

![Geometric series and similar triangles](https://latex.artofproblemsolving.com/3/5/c/35ca1caaa3ff0d0eb67f64f8c0c48da6df657b15.png)

Finding succinct expressions for certain power series expressions also occurs in the study of 
[generating functions](https://en.wikipedia.org/wiki/Generating_function), with applications in number theory, combinatorics, and beyond.

Tags: Probability, Markov Chains, Random number generators

References:
- [Arithmetico–geometric sequence]
- [Absorbing Markov Chain]
- [Markov Chain hitting times]

Related Reading:

- [Swain, S. G. (1994). Proof without words: Gabriel’s staircase. Math. Mag. 67(3):209.][Swain, 1994]
- [Edgar. T. (2018). Staircase Series. Math. Mag. 91 (2018) 92–95.][staircase series]
- [Art of Problem Solving: Proofs without words][AOPS: Proofs without words]
- [Probability and Markets: Trading Interview Preparation](https://www.janestreet.com/static/pdfs/trading-interview.pdf)
- [Expected number of tosses to get 3 consecutive heads](https://math.stackexchange.com/questions/1839496/expected-number-of-tosses-to-get-3-consecutive-heads/1839505)
- [Expected number of coin tosses to get five consecutive heads](https://math.stackexchange.com/questions/364038/expected-number-of-coin-tosses-to-get-five-consecutive-heads?rq=1)

[Arithmetico–geometric sequence]: https://en.wikipedia.org/wiki/Arithmetico%E2%80%93geometric_sequence
[Swain, 1994]: https://www.maa.org/sites/default/files/Swain61227118.pdf
[staircase series]: https://community.plu.edu/~edgartj/staircase.pdf
[AOPS: Proofs without words]: https://artofproblemsolving.com/wiki/index.php/Proofs_without_words
[Wolfram Alpha: Proof without words]: https://mathworld.wolfram.com/ProofwithoutWords.html
[Markov Chain hitting times]: https://en.wikipedia.org/wiki/Markov_chain#Hitting_times
[Absorbing Markov Chain]: https://en.wikipedia.org/wiki/Absorbing_Markov_chain

### SQ7. Four digit square numbers

Prove that there does not exist a four-digit square number $n$ such that $n \equiv 1 \\ (\mathrm{mod}\\ 101)$.

#### SQ7 Solution

Noting that $31^{2} = 961, 32^{2} = 1024, 99^{2} = 9801, 100^{2} = 10000$, we find that the set of four digit square numbers is precisely 
$\\{ n = x^{2} : x = 32, \ldots, 99 \\}$. Suppose, for contradiction, that we have a four digit square number $n = x^{2}$ 
such that $n \equiv 1 \\ (\mathrm{mod}\\ 101)$. This means that there is an integer $k$ such that $n - 1 = x^{2} - 1 = 101k$.
By factorising the difference of two squares we find that $(x + 1)(x - 1)$ is divisible by $101$. As $101$ is prime, it follows that either
$(x + 1)$ or $(x - 1)$ is divisible by $101$, however this is impossible for $x \in \\{ 32, \ldots, 99 \\}$. Therefore, there can be no
four-digit square number which is congruent to $1$ modulo $101$, as required. 

Tags: Modular arithmetic, Number theory

### SQ8. Scaled Fourier transform

The Fourier transform of a function $f(t)$ is defined as:
$$F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-2 \pi i \omega t} dt.$$
Express the Fourier transform of $f(\alpha t)$ in terms of $F$, $\alpha$ and $\omega$.

#### SQ8 Solution

The Fourier transform of $f(\alpha t)$ is $\int_{-\infty}^{\infty} f(\alpha t) e^{-2 \pi i \omega t} dt$. 
When $\alpha \neq 0$, we can use the substitution $s = \alpha t$, so that $t = \frac{s}{\alpha}$ and $dt = \frac{1}{\alpha} ds$.
In the case when $\alpha > 0$, the limits of integration are preserved and we get
$$\int_{-\infty}^{\infty} f(\alpha t) e^{-2 \pi i \omega t} dt = 
\frac{1}{\alpha} \int_{-\infty}^{\infty} f(s) e^{-2 \pi i (\frac{\omega}{\alpha}) s} ds = 
\frac{1}{\alpha} F(\frac{\omega}{\alpha})$$
In the case that $\alpha < 0$, the limits of integration are reversed and we get
$$\int_{-\infty}^{\infty} f(\alpha t) e^{-2 \pi i \omega t} dt = 
 -\frac{1}{\alpha} \int_{-\infty}^{\infty} f(s) e^{-2 \pi i (\frac{\omega}{\alpha}) s} ds = 
-\frac{1}{\alpha} F(\frac{\omega}{\alpha})$$
Combining these two, we find that for $\alpha \neq 0$ the Fourier transform of $f(\alpha t)$ is given by 
$\frac{1}{\lvert \alpha \rvert} F(\frac{\omega}{\alpha})$.

When $\alpha = 0$, $f(\alpha t) = f(0)$ is constant with respect to $t$ and we have 
$$\int_{-\infty}^{\infty} f(\alpha t) e^{-2 \pi i \omega t} dt = f(0) \int_{-\infty}^{\infty} e^{-2 \pi i \omega t} dt = f(0) \delta(\omega)$$
a multiple of the [Dirac delta function](https://mathworld.wolfram.com/DeltaFunction.html).
This requires more sophisticed analysis than simple techniques for evaluating [improper integrals](https://en.wikipedia.org/wiki/Improper_integral).
See [here](https://en.wikipedia.org/wiki/Fourier_transform) for more properties of the Fourier transform.

Tags: Fourier transform, Calculus, Improper integration

### SQ9. Intersection of multisets

A multiset is a collection of objects, some of which may be repeated. So, for example,
$\\{ 1, 3, 5, 3, 2, 7, 2 \\}$ is a multiset. The multiplicity of an element in a multiset is the number
of times that element occurs in the multiset. Intersections of multisets can be produced
as follows: given multisets $A$ and $B$, the multiplicity of an element in $A \cap B$ is
the minimum of its multiplicities in each of $A$ and $B$.
Given multisets $A$ and $B$, with unordered elements, outline an algorithm for generating
the intersection $A \cap B$.

#### SQ9 Solution

Initially modelling a multiset with unordered elements as an unsorted list or array, we outline three different algorithms 
for computing the intersection of two unordered multisets and discuss their time complexity.
Further optimizations for the methods described (as well as alternative solutions) exist.
Define the size of a multiset to be the total number of elements it contains or equivalently the sum of the multiplicities of its distinct elements,
and let the size of multisets $A$ and $B$ be $a$ and $b$, respectively.
The space complexity of the result $A \cap B$ is simply the size $|A \cap B|$ of the intersection, which is bounded above by $\min(a, b)$.

**Method 1. Linear search** 
1. Create a list data structure to hold the result of the intersection of $A$ and $B$.
2. For each element in $A$ (sequentially), check whether it occurs in $B$ (sequential/linear search);
   - If so, add this element once to the list of common elements and remove it once from $B$ (e.g. remove the first occurence in $B$);
   - If not, move on to the next element in $A$;
3. Once the loop is completed, the resulting list will contain all of the common elements with the appropriate multiplicities.

The time complexity of this algorithm is $O(ab)$ since we loop over the $a$ elements of $A$, and for each loop we sequentially/linearly search
through the list $B$, which has runtime $O(b)$. The worst case behaviour is typically achieved when the two multisets are disjoint/do not intersect.

``` python
def intersection_sequential(A: list, B: list) -> list:
    result = []
    for x in A:
        if (len(B) == 0): break; # Stop if `B` is empty
        if (x in B): # Sequential/linear search for `x` in unsorted list `B`
            result.append(x) # Add the common element `x` to `result` once
            B.remove(x) # Remove the first occurence of `x` from `B` (once)
    return result
```

**Method 2. Sort and binary search** 
1. Create a list data structure to hold the result of the intersection of $A$ and $B$.
2. Sort the list $B$ (assumes a (total) ordering on the elements of the multisets, such as for numbers or strings).
3. For each element in $A$ (sequentially), check whether it occurs in $B$ using a binary search;
   - If so, add this element once to the list of common elements and remove it once from $B$ (e.g. remove the first occurence in $B$);
   - If not, move on to the next element in $A$;
4. Once the loop is completed, the resulting list will contain all of the common elements with the appropriate multiplicities.

The runtime for sorting $B$ is $O(b \log b)$, then we loop over the $a$ elements of $A$, for which each binary search through the sorted list $B$
has runtime $O(\log b)$. Therefore the overall runtime is $O((a + b) \log b)$. 
This method is asymptotically faster than method 1, but makes the (possibly incorrect) assumption that all elements in the multisets can be compared
using the operators `<` and `>` rather than only `==`. If this is the case, further optimizations may be achieved by choosing which multiset out of 
$A$ and $B$ to sort (or both, with further modifications to the algorithm) contingent on comparing the size of $A$ and $B$.

``` python
def intersection_with_sort(A: list, B: list) -> list:
    result = []
    B.sort() # Sort `B` in place
    for x in A:
        if (len(B) == 0): break; # Stop if `B` is empty
        if (x < B[0] or x > B[-1]): continue; # Skip if x < min(B) or x > max(B) to save time
        if (x in B): # Binary search for `x` in sorted list `B`
            result.append(x) # Add the common element `x` to `result` once
            B.remove(x) # Remove the first occurence of `x` from `B` (once)
    return result
```

**Method 3. Hash table**

For this method, we remodel a multiset using a [hash table], 
where the keys are the distinct elements and the values are their respective multiplicities.
This requires the elements of a multiset to be hashable.

1. Create empty hash table/dictionary data structures `A_dict`, `B_dict`, and `result` to hold the data for $A$, $B$, and $A \cap B$, respectively.
2. Calculate the multiplicities of the elements in $A$ by counting. For each element $x$ in $A$, check whether it is already a key in `A_dict`;
   - If so, increment the value at `A_dict[x]` by one;
   - Otherwise, add the key-value pair `(x, 1)` to `A_dict`;
3. Repeat this process for $B$ to populate `B_dict` with element counts/multiplicities.
4. For each distinct element in $A$, check whether it occurs in $B$ using the hash table lookup;
   - If so, add a new entry to the results table with the common element as the key and 
     the minimum of its multiplicities in each of $A$ and $B$ as the value;
   - If not, move on to the next (distinct) element in $A$;
5. Once the loop is completed, the resulting table will contain all of the common elements as keys 
   with their multiplicities in $A \cap B$ as the corresponding values.

In a well-implemented [hash table] the average runtime for each lookup is constant time $O(1)$, 
i.e. independent of the number of elements stored in the table. Such designs also allow arbitrary insertions and deletions of key-value pairs, 
at (amortized) constant average cost per operation.
Therefore, the runtime for storing $A$ and $B$ as hash tables is $O(a + b)$, and looping over (distinct) elements in $A$ and looking them up 
in the hash table of $B$ has runtime $a \cdot O(1) = O(a)$, which leads to an overall runtime of $O(a + b)$.
This is as good as we can hope for in terms of asymptotic runtime complexity since any algorithm for computing $A \cap B$ would necessarily have to
access all of the elements of both $A$ and $B$, which is an $O(a + b)$ operation.

In the [`collections`](https://docs.python.org/3/library/collections.html) module of the Python Standard Library there are container datatypes 
[`defaultdict`][defaultdict] and [`Counter`][Counter] which are subclasses of `dict`, Python's built-in hash table implementation, 
with a few specialised methods which make coding up the algorithm described above simpler and faster
than using the [`dict.setdefault()`](https://docs.python.org/3/library/stdtypes.html#dict.setdefault) method.

``` python
from collections import defaultdict

def counts_dict(mylist: list) -> defaultdict:
    d = defaultdict(int) # Sets default count of each key to int() = 0
    for key in mylist:
        d[key] += 1
    return d

def intersection_with_hash_table(A: list, B: list) -> dict:
    result = dict()
    A = counts_dict(A)
    B = counts_dict(B)
    for key in set(A.keys()).intersection(B.keys()):
        result[key] = min(A[key], B[key])
    return result
```

The winning implementation in terms of combination of efficiency and simplicity is as follows:

``` python
from collections import Counter

def intersection_pythonic(A: list, B: list) -> Counter:
    return Counter(A) & Counter(B)
```

Tags: Multiset, multiplicity, Set theory, algorithms, hash table, sorting, data structures

References:
- [Hash table, Wikipedia][hash table]
- Python's `defaultdict` container datatype [documentation][defaultdict]
- Python's `Counter` container datatype [documentation][Counter]

[hash table]: https://en.wikipedia.org/wiki/Hash_table
[defaultdict]: https://docs.python.org/3/library/collections.html#collections.defaultdict
[Counter]: https://docs.python.org/3/library/collections.html#collections.Counter

### SQ10. Number patterns and properties

Sort the following $16$ numbers into $4$ sets of $4$ and give an explanation for each grouping:
$\\{ 1, 2, 3, 4, 4, 5, 5, 8, 9, 11, 13, 17, 25, 32, 49, 128 \\}$.

#### SQ10 Solution

This question allows for multiple interpretations, especially for those familiar with the 
[On-Line Encyclopedia of Integer Sequences (OEIS)](https://en.wikipedia.org/wiki/On-Line_Encyclopedia_of_Integer_Sequences),
but a possible grouping might be as follows:
- $\\{ 4, 9, 25, 49 \\}$ - squares of primes
- $\\{ 4, 8, 32, 128 \\}$ - multiples of 4
- $\\{ 1, 2, 3, 5 \\}$ - first four values of the [partition function](https://en.wikipedia.org/wiki/Partition_function_(number_theory))
- $\\{ 5, 11, 13, 17 \\}$ - primes with residue $\pm 1$ modulo $6$

Tags: Number theory, patterns

### SQ11. Logarithms and continued fractions

Given
$$
\log_{2}(11) = 3 + \cfrac{1}{2 + \cfrac{1}{5 + \cfrac{1}{1 + \cfrac{1}{1 + \cfrac{1}{1 + \cfrac{1}{25 + \cfrac{1}{1 + \cdots}}}}}}}
$$
which is larger, $2^{128}$ or $11^{37}$?

#### SQ11 Solution

As $\log_{2}$ is an increasing function it suffices to compare the numbers $\log_{2}(2^{128}) = 128$ and $\log_{2}(11^{37}) = 37 \log_{2}(11)$.

For $x > 0$, it follows that 
$$\cfrac{1}{1 + x} < \cfrac{1}{1 + 0} = 1$$
$$\cfrac{1}{25 + \cfrac{1}{1 + x}} > \cfrac{1}{25 + \cfrac{1}{1 + 0}} = \frac{1}{26}$$
$$\cfrac{1}{1 + \cfrac{1}{25 + \cfrac{1}{1 + x}}} < \cfrac{1}{1 + \cfrac{1}{25 + \cfrac{1}{1 + 0}}} = \frac{26}{27}$$
$$\vdots$$
$$
\cfrac{1}{2 + \cfrac{1}{5 + \cfrac{1}{1 + \cfrac{1}{1 + \cfrac{1}{1 + \cfrac{1}{25 + \cfrac{1}{1 + x}}}}}}} < 
\cfrac{1}{2 + \cfrac{1}{5 + \cfrac{1}{1 + \cfrac{1}{1 + \cfrac{1}{1 + \cfrac{1}{25 + \cfrac{1}{1 + 0}}}}}}} = \frac{453}{986}
$$
Therefore, $37 \log_{2}(11) < 111 + 37 \cdot \frac{453}{986}$. At this point we suspect that $111 + 37 \cdot \frac{453}{986} < 128$
which is equivalent to $37 \cdot \frac{453}{986} < 17$, which we can verify by calculating 
$$37 \cdot 453 = 16761 < 16762 = 17 \cdot 986.$$
Therefore, we have shown that $\log_{2}(11^{37}) < 111 + 37 \cdot \frac{453}{986} = 128 - \frac{1}{986} < 128$ and hence $11^{37} < 2^{128}$.

A similar line of reasoning with $x < 1$ allows us to bound $\frac{889}{1935} < \log_{2}(11) - 3 < \frac{453}{986}$.

Tags: Continued fractions, logarithms

References:
- [Continued fraction, Wikipedia](https://en.wikipedia.org/wiki/Continued_fraction)

### SQ12. Maximum power-of-2 factor of factorial numbers

Write $n! = 2^{a}b$ where $b, n \in \mathbb{N}$ and $a \in \mathbb{N} \cup \\{ 0 \\}$. Prove that $a < n$.

#### SQ12 Solution

For fixed $n \in \mathbb{N}$ there may be multiple ways to express $n! = 2^{a}b$ with $b \in \mathbb{N}$ and $a \in \mathbb{N} \cup \\{ 0 \\}$,
and we are interested in when $a$ is as large as possible, so that we are extracting the largest possible power of $2$ from $n!$ as a factor.

Let $a_{n} := \max \\{ a \in \mathbb{N} \cup \\{ 0 \\} : \exists b \in \mathbb{N} \text{ such that } n! = 2^{a}b \\}$. 
It suffices to show that $a_{n} < n$ for all $n \in \mathbb{N}$.

The result holds for $n = 1$, in which case $1! = 1$ and $a_{1} = 0$, and for $n = 2$, in which case $2! = 2$ and $a_{2} = 1$.
Notice that if $n$ is even, then $a_{n+1} = a_{n}$ since $(n + 1)! = (n + 1) \cdot n!$ where $n + 1$ is not divisible by $2$.

We define the [$2$-adic valuation][P-adic order] of a positive integer $m \in \mathbb{N}$ to be 
$$\nu_{2}(m) = \max \\{ v \in \mathbb{N} \cup \\{ 0 \\} : 2^{v} \text{ divides } m \\}.$$
Notice that by the [unique prime factorisation][Fundamental theorem of arithmetic] of positive integers it follows that 
$\nu_{2}(m_{1} \cdot m_{2}) = \nu_{2}(m_{1}) + \nu_{2}(m_{2})$ and 
therefore by our definition above $$a_{n} = \nu_{2}(n!) = \sum_{i = 1}^{n} \nu_{2}(i).$$

We observed that odd numbers have $2$-adic [valuation][Valuation] equal to zero, that is $\nu_{2}(2k + 1) = 0$ for all $k \ge 0$, 
whilst even numbers have $2$-adic valuation greater than $1$, that is $\nu_{2}(2k) \ge 1$ for all $k \in \mathbb{N}$.
Moreover, [singly even positive integers][Singly and doubly even] (of the form $4k + 2$) have $2$-adic valuation exactly $1$, 
$\nu_{2}(4k + 2) = 1$ for all $k \ge 0$, whilst [doubly even positive integers][Singly and doubly even] (of the form $4k$)
have $2$-adic valuation at least $2$, i.e. $\nu_{2}(4k) \ge 2$ for all $k \in \mathbb{N}$.

This generalises to the fact $\nu_{2}^{-1}(m) = \left( 2^{m + 1} \mathbb{Z} + 2^{m} \right) \cap \mathbb{N}$ for all $m \ge 0$.

Therefore, one way to express $a_{n} = \nu_{2}(n!)$ is
$$a_{n} = \nu_{2}(n!) = \sum_{i = 1}^{n} \nu_{2}(i) = \sum_{k = 1}^{\lfloor \log_{2}{n} \rfloor} \Bigl \lfloor \frac{n}{2^k} \Bigr \rfloor < 
\sum_{k = 1}^{\infty} \frac{n}{2^k} = n.$$
The idea is to count one towards $a_{n}$ for each even number less than (or equal to) $n$, then count an additional one for each multiple of 4 
less than (or equal to) $n$, and then count an extra one for each multiple of 8 less than (or equal to) $n$, and so on for all powers of $2$.
Each time we add $1$ to the count represents another factor of $2$ in the factorial $n!$, and we can represent these counts using floor functions.

Tags: Number theory, p-adic valuation

References:
- [Singly and doubly even integers][Singly and doubly even]
- [$p$-adic order][P-adic order]
- [Valuation]
- [Fundamental theorem of arithmetic]
- [Integer factorization]

[Singly and doubly even]: https://en.wikipedia.org/wiki/Singly_and_doubly_even
[P-adic order]: https://en.wikipedia.org/wiki/P-adic_order
[Valuation]: https://en.wikipedia.org/wiki/Valuation_(algebra)
[Fundamental theorem of arithmetic]: https://en.wikipedia.org/wiki/Fundamental_theorem_of_arithmetic
[Integer factorization]: https://en.wikipedia.org/wiki/Integer_factorization