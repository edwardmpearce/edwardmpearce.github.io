+++
title = "Gauss-Legendre algorithm"
summary = "Implementing an algorithm to compute the digits of Pi using the arithmetic-geometric mean"

date = 2019-10-08T00:00:00
lastmod = 2019-10-08T00:00:00

markup = "mmark"
draft = false  # Is this a draft? true/false

+++

The [Gauss-Legendre algorithm] is an algorithm to compute the digits of $$\pi$$. 
Successive iterations of the algorithm produce better [approximations of the circle constant][Approximations of Pi], $$\pi$$. 
The algorithm is based on an understanding of the [arithmetic-geometric mean] and is notable for being rapidly convergent, quadratically so, 
with only 25 iterations producing 45 million correct digits of $$\pi$$.

The code cell below allows the user to choose the number of iterations of the Gauss-Legendre algorithm to calculate and plots the number of significant figures to which
the calculated approximation agrees with the value of $$\pi$$ built in to Python's `numpy` module.

<!-- Embed SageMath cells in your webpages -->
<script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
<script>sagecell.makeSagecell({"inputLocation": ".sage"});</script>

<div class="sage">
  <script type="text/x-sage">
import numpy as np
import matplotlib.pyplot as plt

# Set your value for the number of iterations here!
num_iter = 6

def gauss_legendre_algorithm(num_iter):
    r"""Implement the Gauss-Legendre algorithm for the specified number of iterations"""
    a, b, t, = [1.0], [1.0/np.sqrt(2)], [1.0/4.0]
    approx = list()
    for i in range(num_iter):
        a.append((a[i] + b[i]) / 2.0)
        b.append(np.sqrt(a[i] * b[i]))
        t.append(t[i] - (2**i) * np.square(a[i] - a[i+1]))
        approx.append(np.square(a[i+1] + b[i+1]) / (4 * t[i+1]))
    return np.array(approx)

approx = gauss_legendre_algorithm(num_iter)

fig = plt.figure()
ax = fig.gca()
ax.plot(range(1, num_iter + 1), -np.log10(np.abs(approx - np.pi)), 'o')
ax.set(xlabel='Number of iterations', ylabel='Accuracy (significant figures)')
plt.show()

print([value == approx[2] for value in approx])
print(approx[-1])
  </script>
</div>

Notice that at the precision level of 64-bit floating point numbers the algorithm stabilises after only 3 iterations, which means we max out the accuracy we can possibly get using this data type very quickly.

If we want to use this method to calculate $$\pi$$ to a greater number of decimal places we could use the Python's in-built `decimal` library, which you can read more about [here][decimal docs].

## Approximating $\pi$ by fractions and polygons

![Dinosaur Comics - Pi Approximation Day](https://www.qwantz.com/comics/comic2-987.png "Dinosaur Comics - Pi Approximation Day")

Following on from discussion in the [comic][Pi Approximation Day] above, we highlight some interesting sources discussing [approximations of Pi] throughout history. 
Another approximation to $$\pi$$ by a fraction is $$\frac{355}{113}$$, which is the best rational approximation of $$\pi$$ with a denominator of four digits or fewer, being accurate to 6 decimal places.

This approximation was known to Chinese mathematicians in the 5th Century as [密率][Milü], improving on an accuracy of two decimal places achieved by the Ancient Greeks before the beginning of the Common Era (BCE) with $$\frac{22}{7}\approx3.14285714286$$,
and was found by Chinese mathematician and astronomer, [Zǔ Chōngzhī (祖沖之)][Zu Chongzhi], who used an [algorithm][Liu Hui's Pi algorithm] of the 3rd Century mathematician [Liu Hui] 
which approximates the area of a (unit) circle from below by inscribed regular polygons and also provides upper bounds by enclosing polygons.

Interestingly, this remained the most accurate approximation to $$\pi$$ found in historical manuscripts for several centuries to follow, being independently rediscovered by Dutch mathematician [Adriaan Anthonisz] only in 1585.

Moreover, this is even more impressive when considering that the necessary calculation of the area of a 24,576-sided regular polygon was made purportedly using only arrangements of wooden sticks known as [counting rods]. 

The [Chinese abacus], also known as the [suanpan (算盤)][suanpan], is likely to have been extant in some early form during the 5th Century, though (my) knowledge of the extent of its usage and its capabilities at the time is limited.

[Gauss-Legendre algorithm]: https://en.wikipedia.org/wiki/Gauss-Legendre_algorithm
[arithmetic-geometric mean]: https://en.wikipedia.org/wiki/Arithmetric-geometric_mean
[Approximations of Pi]: https://en.wikipedia.org/wiki/Approximations_of_%CF%80
[decimal docs]: https://docs.python.org/3/library/decimal.html
[Pi Approximation Day]: https://www.qwantz.com/index.php?comic=955
[Milü]: https://en.wikipedia.org/wiki/Mil%C3%BC
[Zu Chongzhi]: https://en.wikipedia.org/wiki/Zu_Chongzhi
[Liu Hui's Pi algorithm]: https://en.wikipedia.org/wiki/Liu_Hui%27s_%CF%80_algorithm#Later_developments
[Liu Hui]: https://en.wikipedia.org/wiki/Liu_Hui
[Adriaan Anthonisz]: https://en.wikipedia.org/wiki/Adriaan_Anthonisz
[counting rods]: https://en.wikipedia.org/wiki/Counting_rods
[Chinese abacus]: https://en.wikipedia.org/wiki/Abacus#Chinese
[Suanpan]: https://en.wikipedia.org/wiki/Suanpan
