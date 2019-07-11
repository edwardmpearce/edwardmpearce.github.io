+++
title = "Miscellaneous"
summary = "Miscellaneous educational resources"

date = 2019-07-11T00:00:00
# lastmod = 2019-07-11T00:00:00

draft = false  # Is this a draft? true/false

+++

![Picture](https://upload.wikimedia.org/wikipedia/commons/e/e6/Minkowski3.png)

Below is an interactive tool to draw the $l_{p}$-norm unit circle in $\mathbb{R}^2$ for a given value of $p$, inspired by the above [picture](https://commons.wikimedia.org/wiki/File:Minkowski3.png) from Wikipedia. All you need to do is set the value of $p$ you want in the box and then click the button to evaluate.

<!-- Embed SageMath cells in your webpages -->
<script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
<script>sagecell.makeSagecell({"inputLocation": ".sage"});</script>

<div class="sage">
  <script type="text/x-sage">
import numpy as np
import matplotlib.pyplot as plt
# Set your value for p here!
p = 2
def unit_ball(p):
    fig = plt.figure()
    ax = fig.gca()
    ax.set(xlim=(-1.1, 1.1), ylim=(-1.1, 1.1))
    ax.set_aspect('equal')    
    # Create coordinates for points evenly spaced around the unit circle
    t = np.linspace(0., 2*np.pi, num=10000)
    x, y = np.cos(t), np.sin(t)
    # l_p normalize each point by dividing its coordinates by its l_p norm
    if not p == 2:
        norms = np.linalg.norm(np.array([x, y]), p, axis=0)
        x, y = np.divide(x, norms), np.divide(y, norms)
    # Return the plot - the projection of the l2 ball onto the l_p ball
    ax.plot(x,y)
    plt.show()
unit_ball(p)
  </script>
</div>