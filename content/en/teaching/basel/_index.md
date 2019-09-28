+++
title = "Basel problem"
summary = "A classical problem in mathematical analysis examined through the lens of computer programming"

date = 2019-09-28T00:00:00
lastmod = 2019-09-28T00:00:00

markup = "mmark"
draft = false  # Is this a draft? true/false

+++

The convergence of the infinite sum of inverse squares $$\sum_{n=1}^{\infty}\frac{1}{n^2}$$ is typically taught to undergraduate mathematicians in their first year mathematical analysis courses, 
often by bounding above by the geometric series $$\sum_{n=0}^{\infty}\frac{1}{2^n}=2$$, and is compared with the divergence of the harmonic series $$\sum_{n=1}^{\infty}\frac{1}{n}$$. 

The limit $$\sum_{n=1}^{\infty}\frac{1}{n^2}=\frac{\pi^2}{6}$$ is given as a well-known fact (along with the infinite sum of reciprocal fourth powers $$\sum_{n=1}^{\infty}\frac{1}{n^4}=\frac{\pi^4}{90}$$), 
though the problem of finding and proving this limit dates back to 1650 and was famously solved by Leonhard Euler in 1734, earning itself the name the [Basel problem][Wikipedia]. 

![Picture](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Basel_-_M%C3%BCnsterpfalz1.jpg/800px-Basel_-_M%C3%BCnsterpfalz1.jpg "Basel, Switzerland")

In doing some background research on a programming exercise whilst preparing to lead a computer lab session, I stumbled across the Wikipedia page for the [Basel problem][Wikipedia], 
which gives a brief history of the problem along with a number of different methods of proof. More alternative proofs have been gathered by [Robin Chapman] as well as by the users of [MathStackExchange][StackExchange2].

The programming exercise in question involves writing a script/function to compute the partial sums 

$$\sum_{i=1}^{n}\frac{1}{i^4} = \frac{1}{1^4} + \frac{1}{2^4} + \ldots + \frac{1}{n^4}$$

for any given choice of $n$ and observe its properties as $n$ increases.

The code cell below allows the user to choose values $N$ and $s$ and plots the values of the partial sums $$S_{n}:=\sum_{i=1}^{n}\frac{1}{i^s}$$ for $$n=1,\ldots,N$$ and compares them with the limits $$\zeta(s) := \sum_{n=1}^{\infty}\frac{1}{n^s}$$ using the Riemann zeta function from the [SciPy][SciPy zeta] package.

<!-- Embed SageMath cells in your webpages -->
<script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
<script>sagecell.makeSagecell({"inputLocation": ".sage"});</script>

<div class="sage">
  <script type="text/x-sage">
import numpy as np
import matplotlib.pyplot as plt
from scipy.special import zeta#, bernoulli
# Set your value for n and s here!
n, s = 1000, 2
def plot_inverse_power_partial_sums(n, s):
    fig = plt.figure()
    ax = fig.gca()
    # Create an array of integers and compute the corresponding summands and partial sums
    x = np.arange(1., n+1)
    summands = np.reciprocal(np.power(x, s))
    partial_sums = np.cumsum(summands)
	# Plot the partial sums and the reference line
    ax.hlines(zeta(s), x[0], x[-1], linestyles='dashed')
    ax.plot(x, partial_sums)
    plt.show()
plot_inverse_power_partial_sums(n, s)
  </script>
</div>

A further discussion on [MathStackExchange][StackExchange4] considers proofs of the limit $$\sum_{n=1}^{\infty}\frac{1}{n^4}=\frac{\pi^4}{90}$$. 

An interesting generalization discussed on the [Wikipedia] page for the Basel problem and in the other references is the relation between values of the Riemann zeta function and the [Bernoulli numbers][Bernoulli numbers algorithms] for positive even integers.

Therefore, it was very interesting for me to dig deeper into the history and details of this classical problem which relates mathematical analysis and number theory, 
with proofs applying techniques of varying levels of sophistication that one might encounter whilst studying for a degree in mathematics.

[Wikipedia]: https://en.wikipedia.org/wiki/Basel_problem
[Robin Chapman]: http://empslocal.ex.ac.uk/people/staff/rjchapma/etc/zeta2.pdf
[StackExchange2]: https://math.stackexchange.com/questions/8337/different-methods-to-compute-sum-limits-k-1-infty-frac1k2-basel-pro
[StackExchange4]: https://math.stackexchange.com/questions/28329/nice-proofs-of-zeta4-frac-pi490
[SciPy zeta]: https://docs.scipy.org/doc/scipy/reference/generated/scipy.special.zeta.html
[Bernoulli numbers algorithms]: https://rosettacode.org/wiki/Bernoulli_numbers
