---
title: "Sample Mathematics Aptitude Test"
summary: "Exercise solutions for an online Sample Mathematics Aptitude Test"

date: 2020-08-03T00:00:00
lastmod: 2020-08-03T00:00:00

draft: false  # Is this a draft? true/false

---

<script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
<script>sagecell.makeSagecell({inputLocation: '#markovcell', languages: ["python"], template: sagecell.templates.minimal});</script>

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
and [Bézout's identity]. We will also draw on ideas from elementary group theory, 
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

[Bézout's identity]: https://en.wikipedia.org/wiki/B%C3%A9zout%27s_identity

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

#### SQ6 Solution

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
see [here][Linear congruential generator].

#### SQ6 Aside

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

## Longer Questions

### LQ1. Rock, Paper, Scissors

Alice and Bob play Rock, Paper, Scissors until one or the other is 5 wins ahead. They
generate their wins at random, so, in each round, the outcomes are equiprobably win, lose or draw.
After 10 rounds, Alice is 1 ahead. After 13 rounds, one or the other is 1 ahead. At round
20, one of them attains the 5 win lead and the game ends. What is the probability that
Alice is the ultimate winner?

#### LQ1 Solution

A principled way to approach this question would be to model the process as a Markov chain, similar to [SQ6](#sq6-random-number-generation).
Let $x_{t}$ be size of Alice's lead in round $t$. Then, in general, we have state space $x_{t} \in \\{ 0, \pm 1, \pm 2, \pm 3, \pm 4, \pm 5 \\}$ 
and transition probabilities $(p_{i,i-1}, p_{i,i}, p_{i,i+1}) = (1/3, 1/3, 1/3)$ for states $-4 \le i \le 4$, and absorbing states $-5$ and $5$.
We are given the specific information that $x_{0} = 0$, $x_{10} = 1$, $x_{13} \in \\{ -1, 1 \\}$, $x_{20} \in \\{ -5, 5 \\}$, 
and $x_{t} \notin \\{ -5, 5 \\}$ for $t < 20$.

Due to the memoryless property, we need only consider the process from round 10 ($t = 10$) onwards, when Alice has a lead of $1$.
We could then combine this model with conditional probability calculations based on the information provided in the question.
Ultimately, we wish to calculate 
$$ P(x_{20} = -5 | x_{20} \in \\{ -5, 5 \\}, x_{13} \in \\{ -1, 1 \\}, x_{10} = -1, x_{t} \notin \\{ -5, 5 \\} \text{ for } t < 20) $$

We will follow this principled approach later to verify our answer, but first use a quicker method which does not require matrix multiplication.

Given that Alice has a lead of $1$ at round 10 and we know that at round 13 Alice has a lead of either $1$ or $-1$ (i.e. Bob leads by $1$), 
we can deduce that at round 13 Alice has a lead of $1$ with probability $\frac{7}{10}$ and a lead of $-1$ with probability $\frac{3}{10}$.

For Alice to make a net loss of $2$ over three rounds the sequence of outcomes would have to consist of a permutation of $2$ losses and $1$ draw 
$(D + 2L)$, for which there are $3$ possibilities; whilst making a net gain/loss of $0$ over three rounds requires a permutation of either 
one win, one loss, and one draw $(D + L + W)$, or three draws $(3D)$, for which there are $6 + 1 = 7$ possibilities.
Then, as each set of outcomes subject to the constraints is equally likely, we obtain the probabilities $\frac{3}{3 + 7}$ and $\frac{7}{3 + 7}$.

Next, we consider the number of sequences of outcomes over seven rounds that could lead the player who has a lead of $1$ at round 13 to have
a lead of either $5$ or $-5$ at round 20 causing the game to end. 

For the net loss of $6$ over 7 rounds, the outcomes must be $6$ losses and $1$ draw $(D + 6L)$, 
where the last loss must come at the end of the sequence in round 20 so that the game doesn't end earlier, which gives $6$ possibilities
according to which round the draw happens. 

For a net gain of $4$ over 7 rounds, the set of outcomes can be either $(3D + 4W)$ or $(D + L + 5W)$,
where we must take care not to count cases where the game ends before round 20. For the case of $4$ wins and $3$ draws, it suffices to require
the last win to occur in round 20, after which we count the possible permutations of the set $(3D + 3W)$ of which there are $6!/(3!)^{2} = 20$.

For the player with a lead of $1$ in round 13 to ultimately win the game in round 20 by making $5$ wins, $1$ loss, and $1$ draw, 
the last win must occur in round 20 to avoid the game ending early. From the remaining $30 = 6 \times 5$ configurations of $(D + L + 4W)$
we exclude the $5$ in which the loss occurs in round 19 (since that would imply a lead of $5$ before round 20), and the 
specific sequence of outcomes $(WWWWLD)$, for which the game would actually have ended in round 18, leaving $24 = 30 - 5 - 1$ valid sequences.

Therefore, if a player is leading by $1$ in round 13 and we know that the game ends in round 20, there is a probability of 
$\frac{44}{50} = \frac{22}{25}$ that this player wins and a probability of $\frac{6}{50} = \frac{3}{25}$ that they lose.

Combining all of this information together, we find that the probability that Alice is the ultimate winner is 
$$\frac{7}{10} \cdot \frac{22}{25} + \frac{3}{10} \cdot \frac{3}{25} = \frac{163}{250} = 65.2\\%$$
by aggregating the possibility that she retains the lead of $1$ at round 13 and goes on to win overall in round 20 with the possibility that 
she pulls back from trailing by $1$ in round 13 to claim victory in round 20.

The Python code listing below models the problem as an [Absorbing Markov Chain] and calculates the probability that Alice wins the game by 
analysing powers of the transition matrix multiplied by vector probability distribution of the state at times $t = 1-$, when $P(x_{10} = 1) = 1$,
and $t = 13$, when $P(x_{13} \in \\{ -1, 1 \\}) = 1$.

This code can be run to verify the above derivation of Alice's winning probability by clicking the `Evaluate` button beneath the code listing.

``` python
import numpy as np
from fractions import Fraction

# Set up the transition matrix
P = np.zeros((11, 11), dtype='object')

for i in range(1, 10):
    P[i, i-1:i+2] = Fraction(1, 3)

# Absorbing states (-5, 5 coded as index 0, 10, respectively)
P[0, 0] = Fraction(1)
P[10, 10] = Fraction(1)

# Alice leads by 1 in round 10 (coded as index 6 = 5 + 1)
x10 = np.zeros(11, dtype='object')
x10[6] = Fraction(1)

# Probability distribution of (transient) states in round 13
x13 = np.linalg.matrix_power(P, 3).dot(x10)

# Condition on being in state -1 or 1 at round 13 (index 4 and 6, resp.)
x13_normalised = np.zeros(11, dtype='object')
x13_normalised[4] = x13[4] / (x13[4] + x13[6])
x13_normalised[6] = x13[6] / (x13[4] + x13[6])

# Probability distribution of transient states in round 19
x19 = np.linalg.matrix_power(P, 6).dot(x13_normalised)

# Condition on being in state -5 or 5 at round 20
results = {"Alice win": x19[9] / (x19[1] + x19[9]),
           "Alice lose": x19[1] / (x19[1] + x19[9])}
print(results) # {'Alice win': Fraction(163, 250), 'Alice lose': Fraction(87, 250)}
print(float(results["Alice win"])) # 0.652
```

<div id="markovcell">
<script type="text/x-sage">
import numpy as np
from fractions import Fraction
P = np.zeros((11, 11), dtype='object')
P[0, 0] = Fraction(1)
P[10, 10] = Fraction(1)
for i in range(1, 10):
    P[i, i-1:i+2] = Fraction(1, 3)
x10 = np.zeros(11, dtype='object')
x10[6] = Fraction(1)
x13 = np.linalg.matrix_power(P, 3).dot(x10)
x13_normalised = np.zeros(11, dtype='object')
x13_normalised[4] = x13[4] / (x13[4] + x13[6])
x13_normalised[6] = x13[6] / (x13[4] + x13[6])
x19 = np.linalg.matrix_power(P, 6).dot(x13_normalised)
results = {"Alice win": x19[9] / (x19[1] + x19[9]), "Alice lose": x19[1] / (x19[1] + x19[9])}
print(results)
print(float(results["Alice win"]))
</script>
</div>

Tags: Probability, Markov Chains

Related Reading:
- [Simulating Chutes & Ladders in Python](https://jakevdp.github.io/blog/2017/12/18/simulating-chutes-and-ladders/)
- [Analysing Snakes and Ladders as a Markov Chain](https://scipython.com/book/chapter-6-numpy/additional-problems/analysing-snakes-and-ladders-as-a-markov-chain/)

### LQ2. 

You are monitoring a data stream which is delivering very many $32$-bit quantities at a rate of $10$ Megabytes per second. 
You know that either:
1. All values occur equally often, *or*
2. Half of the values occur $2^{10}$ times more often than others (but you dont know anything about which would be the more common values).

You are allowed to read the values off the data stream, but you only have $2^{20}$ bytes of memory.
Describe a method for determining which of the two situations, 1 or 2, occurs. 
Roughly how many data values do you need to read to be confident of your result with a probability of $0.999$? 
(This is about the $3$ sigma level – $3$ standard deviations of a normal distribution.)

### LQ3. 

A $2 \times N$ rectangle is to be tiled with $1 \times 1$ and $2 \times 1$ tiles. Prove that the number of
possible tilings tends to $kx^{N}$ as $N$ gets large. Find $x$, to $2$ decimal places.

#### LQ3 Initial ideas

Does the problem description mean to imply that the $2 \times 1$ tiles must always be placed vertically?
Once we have proven that the number of possible tilings tends to $kx^{N}$ as $N$ gets large, we could approximate $x$ 
using the ratio of empirical values. Let $a_{N}$ denote the number of possible tilings of a $2 \times N$ rectangle by 
$1 \times 1$ and $2 \times 1$ tiles. Then as $N$ gets large we have $\frac{a_{N+1}}{a_{N}} \approx \frac{kx^{N+1}}{kx^{N}} = x$.
It is likely that $a_{N}$ satisfies a recurrence relation.

### LQ4. Prime Power Divisors

The Prime Power Divisors (PPD) of a positive integer are the largest prime powers that divide it. 
For example, the PPD of $450$ are $2$, $9$, $25$. Which numbers are equal to the sum of their PPD?

#### LQ4 Solution

Powers of prime numbers are trivially equal to the sum of their prime power divisors, and these are the only numbers with this property.
Let $f : \mathbb{N} \to \mathbb{N}$ be the function which maps a positive integer to the sum of its prime power divisors.
So $f(1) = 0$, $f(6) = 2 + 3 = 5$, $f(450) = 2 + 9 + 25 = 36$, and $f(p^{k}) = p^{k}$ for $p$ prime and $k \in \mathbb{N}$.
Note also that if $a, b$ are coprime, then $f(ab) = f(a) + f(b)$.

We claim that $f(n) \le n$ for all positive integers $n$, with equality if and only if $n$ is a prime power.
Suppose, for contradiction, that the set of positive integers which are not a prime power but have $f(n) \ge n$ is nonempty, and let $n_{0}$
be the smallest element in this set. By assumption, we can express $n_{0}$ as a product of coprime integers $a, b \ge 2$ since $n_{0}$ is a 
composite number with at least two distinct prime factors. The factors $a$ and $b$ are distinct since they are coprime and both greater than $1$.
Then $n_{0} \le f(n_{0}) = f(ab) = f(a) + f(b) \le a + b < 2 \max(a, b) \le ab = n_{0}$, which is a contradiction.
Therefore, if $n$ is not a prime power, then $f(n) < n$. This completes the proof.

Tags: Number theory, prime factors

Related Reading:
- [Multiplicative function (number theory)](https://en.wikipedia.org/wiki/Multiplicative_function)

### LQ5. 

$353, 46, 618, 30, 877, 235, 98, 24, 107, 188, 673$ are successive large powers of an integer $x$ modulo a 3-digit prime $p$. Find $x$ and $p$.

#### LQ5 Solution

This problem is related to cracking a pseudo-random number generator known as the [Lehmer random number generator], which is a special case of a 
[linear congruential generator][Linear congruential generator]. Determining $x$ and $p$ would allow us to calculate subsequent terms in the sequence. 
A subsequent problem could be find out which large powers of $x$ modulo $p$ these are, which is known as the [discrete logarithm][Discrete logarithm] 
problem. As we are told these are successive powers of $x$ modulo $p$, one would only need to solve this problem for one number in the sequence.

We first determine $x$ by making use of [Bézout's identity] and the [Extended Euclidean algorithm].
Label the elements of the sequence by $a_{n}$ for $n = 0, 1, \ldots, 10$. Then we have that $a_{n} x \equiv a_{n+1} \\ (\mathrm{mod}\\ p)$ for 
$n = 0, 1, \ldots, 9$. We would like to find indices $n_{1}, n_{2}$ such that $\gcd(a_{n_{1}}, a_{n_{2}}) = 1$, then apply Bézout's identity/EEA 
to find integers $s, t$ such that $a_{n_{1}} s + a_{n_{2}} t = 1$. From this we could deduce 
$$x = (a_{n_{1}} s + a_{n_{2}} t) x = (a_{n_{1}} x) s + (a_{n_{2}} x) t \equiv a_{n_{1} + 1} s + a_{n_{2} + 1} t \\ (\mathrm{mod}\\ p)$$

We may assume that $p$ is a 3-digit prime number greater than the largest number appearing in the sequence, so $877 < p < 999$.
If we are lucky, we will be able to find $n_{1}, n_{2}, s, t$ such that $0 < a_{n_{1} + 1} s + a_{n_{2} + 1} t < 881$ so that we have a primitive
expression for $x \\ (\mathrm{mod}\\ p)$. Once we know $x$, we can determine $p$ by checking which 3-digit prime in the given range satisfies 
the equations $a_{n} x \equiv a_{n+1} \\ (\mathrm{mod}\\ p)$ for $n = 0, 1, \ldots, 9$. That is to say, we may check for 3-digit prime factors 
of $a_{n} x - a_{n+1}$.

We pick $a_{6} = 98$ and $a_{8} = 107$ (since we know $107$ is prime), so that $9 = 107 - 98$, $8 = 98 - 10 \cdot 9$, and 
$$1 = 9 - 8 = 9 - (98 - 10 \cdot 9) = 11 (107 - 98) - 98 = 11 \cdot 107 - 12 \cdot 98.$$
Thus $x = 11 \cdot 107 x - 12 \cdot 98 x \equiv 11 \cdot 188 - 12 \cdot 24 = 2068 - 288 = 1780 \\ (\mathrm{mod}\\ p)$.
This is outside of the desired range, but will be useful once we find another expression for $x \\ (\mathrm{mod}\\ p)$ since 
we can determine $p$ by factoring the difference between the two expressions. We could then reduce $x$ modulo $p$ if necessary.

Next, we pick $a_{7} = 24$ and $a_{8} = 107$, so that $11 = 107 - 4 \cdot 24$, then $2 = 24 - 2 \cdot 11$, and
$$1 = 11 - 5 \cdot 2 = 11 - 5 (24 - 2 \cdot 11) = 11 (107 - 4 \cdot 24) - 5 \cdot 24 = 11 \cdot 107 - 49 \cdot 24.$$
Therefore, $x = 11 \cdot 107 x - 49 \cdot 24 x \equiv 11 \cdot 188 - 49 \cdot 107 = 2068 - 5243 = -3175 \\ (\mathrm{mod}\\ p)$.

It follows that $1780 - (-3175) = 4955$ is a multiple of $p$, where $4955 = 5 \cdot 991$, so our 3-digit prime is $p = 991$.
Consequently, we may write $x \equiv 1780 \equiv 789 \equiv -202 \\ (\mathrm{mod}\\ 991)$.

The following simple script calculates the discrete logarithm $\log_{789}(353)$ in $\mathbb{Z} / 991 \mathbb{Z}$. 
In particular we find that `353 = 789^62 mod 991`. This brute-force 'trial multiplication' algorithm will not scale well as the prime $p$ increases.

``` python
x, p = 789, 991
target = 353
el = 1
x_pow = 0
while(el != target):
    x_pow += 1
    el *= x
    el %= p
print(f"{target} = {x}^{x_pow} mod {p}")
```

References:
- [Lehmer random number generator]
- [Linear congruential generator]
- [Discrete logarithm]
- [Extended Euclidean algorithm]

[Lehmer random number generator]: https://en.wikipedia.org/wiki/Lehmer_random_number_generator
[Linear congruential generator]: https://en.wikipedia.org/wiki/Linear_congruential_generator
[Discrete logarithm]: https://en.wikipedia.org/wiki/Discrete_logarithm
[Extended Euclidean algorithm]: https://en.wikipedia.org/wiki/Extended_Euclidean_algorithm

### LQ6.

$(X_{1}, Y_{1}),(X_{2}, Y_{2}), \ldots, (X_{n}, Y_{n})$ are $n$ ordered points in the Cartesian plane that are 
successive vertices of a non-intersecting closed polygon.
Describe how to find efficiently a diagonal (that is, a line joining 2 vertices) that lies entirely in the interior of the polygon.
Repeated application of this process will completely triangulate the interior of the polygon. 
Estimate the worst case number of arithmetic operations needed to complete the triangulation.

### LQ7. Semigroups

A *semigroup* is a set $S$ with an associative operation, which we will write as multiplication.
That is, $x(yz) = (xy)z$ for all $x, y, z \in S$.
1. Suppose that a finite semigroup $S$ has the property that for all $x \in S$ there is an integer $n > 1$ such that $x^{n} = x$. 
Is it true that S is, in fact, a group?
2. Suppose that a finite semigroup $S$ has the property that for all $x \in S$ there is an integer $n$ such that $x^{n+1} = x^{n}$. 
Show that the only subsets of $S$ which form a group are of size $1$.

### LQ8. Finite state machines and languages

A *finite state machine* $M$ consists of a finite set of states, each having two arrows leading
out of it, labelled $0$ and $1$. Each arrow from state $x$ may lead to any state (both may lead
to the same state, which might be $x$).
One state is labelled the "initial" state; one or more states are labelled "accept". The
machine reads a finite binary string by starting at "initial" and considering each symbol
in the string in turn, moving along the arrow with that label to the next state until the
end of the string is reached. If the final state is labelled "accept", the machine accepts
the string.
The *language*, $L(M)$ of the machine is the set of all the finite binary strings that the
machine accepts.
1. Design a machine whose language is all palindromic strings of length $6$ (i.e., strings
for which the last $3$ symbols are a reflection of the first $3$).
2. Suppose that $L(M)$ is not finite. Show that the number of strings in $L(M)$ of length
$n$ or less grows linearly with $n$.
3. Show that there is no machine such that $L(M)$ consists of all twice-repeated strings.

### LQ9. 

Suppose $P$ is a permutation on $\\{ 0, 1, \ldots, n − 1 \\}$. We want to know the length of the longest monotonically increasing subsequence.
That is, the largest $m$ such that there exist monotonically increasing $j_{1}, j_{2}, \ldots, j_{m}$ 
for which $P(j_{1}), P(j_{2}), \ldots, P(j_{m})$ are also monotonically increasing.
Describe an algorithm that will determine $m$ using $O(n^{2})$ time and $O(n)$ memory.

### LQ10. 

Given $541$ points in the interior of a circle of unit radius, show that there must be a subset
of $10$ points whose diameter (the maximum distance between any pair of points) is less than $\frac{\sqrt{2}}{4}$.

Tags: Pigeonhole principle

### LQ11. Directed hypercube graph

Show how the edges of a cube ($8$ vertices; $12$ edges) can be directed so that some vertices
have all edges pointing out (i.e., directed away from the vertex), and the remainder have one edge out and two in.
Suppose the edges of a $5$-dimensional hypercube ($32$ vertices, $80$ edges) are directed so
that all vertices have either $5$ edges pointing out, or $4$ edges in and $1$ out. 
Show that every $4$-dimensional subcube must contain precisely $6$ of the $5$-out vertices.
