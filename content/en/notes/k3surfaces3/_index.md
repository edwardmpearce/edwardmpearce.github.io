+++
title = "K3 Surfaces - more on Hodge structures and basic geometry of K3 surfaces"
summary = "Notes from K3 Surfaces Reading Seminar, 14/10/2019 at The University of Sheffield"

date = 2019-10-07T00:00:00
lastmod = 2019-10-07T00:00:00

markup = "mmark"
draft = false  # Is this a draft? true/false

+++

Lecture given by George Moulantzikos, notes taken by Edward Pearce, 14/10/2019, 3pm-4:30pm at The University of Sheffield, based on Daniel Huybrechts' book [Lectures on K3 surfaces](http://www.math.uni-bonn.de/people/huybrech/K3Global.pdf), Chapter 3.

## Linear Systems

Let $$D$$ be a divisor on a variety $$X$$. We denote by $$|D|$$ the set of effective divisors linearly equivalent to $$D$$.

There is a bijection between this set $$|D|$$ and the projectivization of the set of sections

$$|D| \leftrightarrow \mathbb{P}(\Gamma(X,\mathcal{O}_{X}(D)))$$

To a section $$s\in\Gamma(X,\mathcal{O}_{X}(D))$$ we can associate the divisor of zeros $$(s)_{0}$$, which is effective and linearly equivalent to $$D$$.

If $$s, s'\in\Gamma(X,\mathcal{O}_{X}(D))$$ are such that $$(s)_{0}=(s')_{0}$$, then $$s=\lambda s'$$.

We define the fixed part of a linear system $$P$$ to be the biggest divisor contained in every element of $$P$$.

Based points of a linear system $$P$$.

### Maps to projective space $$\mathbb{P}^{n}$$

There is a bijective correspondence between:

- The set of rational maps $$\phi:X \dashrightarrow \mathbb{P}^{n}$$ such that $$\phi(X)$$ is not contained in any hyperplane; and
- The set of linear systems on $$X$$ of dimension $$n$$ with no fixed part.

Given a map $$\phi$$, $$\phi^{\ast}(|H|)$$, where $$|H|$$ is a linear system of hyperplanes in $$\mathbb{P}^{n}$$, then we can obtain a linear system $$P$$ and denoting by $$\check{P}$$ the dual space, we have a map $$\phi:X\to\check{P}$$ which sends a point $$x$$ to the set of hyperplanes $$H$$ in $$P$$ that contain $$x$$.

### Examples

#### Projection from a base point $$p$$ in $$\mathbb{P}^{2}$$:

For $$|H|$$ a linear system of hyperplanes which is complete andof dimension 2, then $$\{H\ni p\}\subset|H|$$

$$\phi:\mathbb{P}^{2}\dashrightarrow\mathbb{P}^{1}$$ is defined for all $$q\neq p$$.

#### Canonical linear system of curves

1. If the genus $$g\ge1$$, then $$|K|$$ is base point free.
2. If the genus $$g\ge3$$, then there is a canonical map $$\phi_{K}:\mathbb{P}^{2}\to\mathbb{P}^{g-1}$$, which is an embedding if and only if $$C$$ is not hyperelliptic.

#### Non-hyperelliptic case

$$\phi_{K}$$ embeds $$C$$ as a degree $$g-1$$ projective curve in $$\mathbb{P}^{g-1}$$.

#### Hyperelliptic case

$$\phi_{K}$$ is a composition of a 2:1 map and a Veroneses map, so $$\phi_{K}(C)$$ is a rational curve of degree $$g-1$$.

#### Example

Dimension of quartics in $$\mathbb{P}^{2}$$ is $$\choose{4+2}{2}=14$$, $$g=3$$, $$\dim\mathrm{PGL}_{3}=9-1=8$$.

A non-hyperelliptic curve is a quartic in $$\mathbb{P}^{2}$$. 

$$K_{C}=(K_{\mathbb{P}^{2}}+C)\big|_{C}=-3H+4H\big|_{C}=H\big|_{C}$$

##  Riemann-Roch for surfaces - genus formula

Euler characteristic formula - Riemann-Roch formula

$$\chi(\mathcal{O}_{X}(D))=\chi(\mathcal{O}_{X}) + \frac{1}{2}D(D-K_{\ast})$$

As an exercise, verify that:

1. $$\chi(D)=\frac{1}{2}D^{2}$$ for abelian surfaces
2. $$\chi(D)=\frac{1}{2}D^{2} + 2$$ for K3 surfaces

### Curves with negative self-intersection

#### The case of (-1) curves

Let $$S$$ be a surface and let $$p\in S$$. We say that $$S'$$ is a blow up of $S$$ at $$p$$ if there is a map $$\epsilon:S'\to S$$
such that the restricton of $$\epsilon$$ at 

$$\epsilon^{-1}(S\setminus\{p\})$$ is an isomorphism onto $$S\setminus\{p\}$$, and $$\epsilon^{-1}(p)=E\cong\mathbb{P}^{1}$$, which is called the exceptional curve at the blow up.

#### Castelnuovo's contractibility theorem at the

...

#### The case of (-2) curves

Let $$C$$ be a curve in a K3 surface $$X$$. Then $$2g-2=C^{2}$$.

Exercise: Prove the genus formula using the adjunction formula

$$C$$ can be singular, reducible, non-reduced.

The arithmetic genus of a curve is generally defined as $$p_{a}(C)=1-\chi(C,\mathcal{O}_{C})$$.

Then in this case $$2p_{a}(C)-2=C^{2}$$.

Exercise: Prove the genus formula using the definition $$p_{a}(C)=1-\chi(C,\mathcal{O}_{C})$$ and the short exact sequence for Riemann-Roch surfaces given by 

$$0\to\mathcal{O}(-C)\to\mathcal{O}_{X}\to\mathcal{O}_{C}\to0$$

## Curves on K3 surfaces

#### Proposition

Let $$X$$ be a K3 surface and let $$C$$ be a smooth curve on $$X$$ of genus $$g$$. Then:

1. $$C^{2}=2g-2$$ and $$h^{0}(C)=g+1$$.
2. If $$g\ge1$$, then $$|C|$$ is base point free. It defines a morphism $$\phi_{C}:X\to\mathbb{P}^{g}$$ 
and the restriction of $$\phi_{C}$$ on $$C$$ is the canonical morphism $$\phi_{K}:C\to\mathbb{P}^{g-1}$$ given by $$|K_{C}|$$.
3. If $$g=2$$, then $$\phi:S\to\mathbb{P}^{2}$$ is a degree 2 morphism and the branch is a sextic in $$\mathbb{P}^{2}$$.
4. If $$g=3$$, then either
  - $$\phi$$ is a birational morphism and the generic curve of $$|C|$$ is non-hyperelliptic; or
  - $$\phi$$ is a 2:1 morphism to a rational surface, and the generic curve of $$|C|$$ is hyperelliptic.
5. If $$g\ge3$$ (respectively $$g\ge2$$), then the morphism defined by $$|2C|$$ (respectively $$|3C|$$) is birational.

### Examples

Suppose $$g=3$$, and $$\phi(S)\subset\mathbb{P}^{3}$$ is a quartic in $$\mathbb{P}^{3}$$. Then the dimension is 34, $$\dim\mathrm{PGL}_{4}=15$$, and the difference is 19.

# Part 2 by Evgeny Schinder

## Very ample, ample, big, and nef line bundles

Let $$S$$ be a surface and $$L=\mathcal{O}(D)$$ a line bundle on $$S$$.

Then very ample implies ample implies nef and big implies nef, where 'nef' stands for numerically effective.

- Very ample: $$\phi_{D}$$ is a closed embedding
- Ample: $$nD$$ is very ample for some $$n>>0$$
- Ample (equivalent condition): $$D\cdot C > 0$$ for all curves $$C\subset X$$, and $$D^{2}>0$$
- nef and big: $$D\cdot C \ge 0$$ for all curves $$C\subset X$$, and $$D^{2}>0$$
- nef: $$D\cdot C \ge 0$$ for all curves $$C\subset X$$.

### Examples

$$\mathbb{P}^{2}$$, then $$\mathrm{Pic}\mathbb{P}^{2}=\mathbb{Z}\cdot H$$, $$D=k\cdot H$$.

Then $$D$$ is very ample iff ample iff nef and big iff $$k>0$$.

Now consider the case $$S=\mathrm{Bl}_{p}\mathbb{P}^{2}$$, then $$\mathrm{Pic}S=\mathbb{Z}\cdot H \oplus \mathbb{Z}\cdot E$$ is generated by the line from $$\mathbb{P}^{2}$$ and the exceptional curve.

### Definition

The positive cone of a K3 surface $$X$$ is $$\mathcal{C}_{X}\subset\{D^{2}>0\}\subset\mathrm{Pic}X\otimes\mathbb{R}=\mathrm{NS}(X)\otimes\mathbb{R}$$, where we specifically restrict our attention to the component contatining ample classes.

### Proposition

Let $$L$$ on a K3 $$X$$, then

1. $$L$$ is ample if and only if $$L\in\mathcal{C}_{X}$$ and for all (-2) curves $$C$$ we have $$L\cdot C>0$$.
2. If $$L^{2}\ge0$$ and $$L\cdot C \ge 0$$ for all (-2) curves $$C$$, then $$L$$ is nef, unless there are no (-2) curves, in which case either $$L$$ or $$L^{\ast}$$ is nef.

## Kodaira vanishing theorem

Two big theorems, which both apply to the case $$\mathrm{char}(k)=0$$.

### Theorem (Kodaira vanishing)

Let $$X$$ be a smooth projective variety and $$L$$ an ample line bundle. Then 

$$\mathrm{H}^{i}(X, L\otimes\omega_{X})=0, \,\forall i>0$$

#### Example

Let $$X=\mathbb{P}^{2}$$, then $$\omega_{X}=\mathcal{O}(-3)$$, and so $$L=\mathcal{O}(j)$$ is ample if and only if $$j\ge1$$.

Thus $$L\otimes\omega_{X}=\mathcal{O}(j-3)$$ where $$j-3\ge-2$$.

Therefore:

- $$\mathrm{H}^{1}(X, \mathcal{O}(\ge-2))=0$$
- $$\mathrm{H}^{2}(X, \mathcal{O}(\ge-2))=0$$

Similar results hold for $$\mathbb{P}^{n}$$.

Note that for K3 surfaces, these results hold for any characteristic, and for $$L$$ big and nef.

## Bertini's theorem

Let $$X$$ be smooth, and $$P\subset|L|$$ be a linear system. Then a general member of $$P$$ is smooth outside the base locus of $$P$$.

### Corollary

For $$X\subset\mathbb{P}^{N}$$, the general hyperplane section is smooth.

### Theorem

Let $$L$$ be a line bundle on a K3 surface $$X$$ such that 

- $$L^{2}>0$$
- $$|L|\ni C$$ contains an irreducible curve

Then $$L$$ is base point free, and in particular the general member of $$|L|$$ is smooth.

## Irreducible curves on K3 surfaces

Let $$C$$ be an irreducible curve contained in a K3 surface $$X$$.

Flow chart: Consider three cases for $$C^{2}$$:

- Negative, then $$C^{2}=-2$$, and so $$C\cong\mathbb{P}^{1}$$
- Zero, then $$C$$ is an elliptic curve, i.e. a fiber of $$X\to\mathbb{P}^{1}$$
- Positive - Does there exist a (-2) curve $$E$$ such that $$E\cdot C-0$$?
  - Yes, then $$C$$ is big and nef, but not ample
  - No, then $$C$$ is ample

### Examples

#### An example of a line bundle which is nef, but not big and nef

We want $$L\cdot C \ge 0$$ and $$L^{2}=0$$.

So take $$L=\mathcal{O}(D)$$ where $$D$$ is an eliptic curve.

#### An example of a line bundle which is big and nef, but not ample

Let $$\bar{S}\subset\mathbb{P}^{3}$$ be a general quartic with an ordinary double point, and $$S\to\bar{S}$$ a resolution of singularities.

Then $$K_{S}=0$$, $$\mathrm{Pic}S=\mathbb{Z}\cdot H\oplus \mathbb{Z}\cdot E$$, where $$H^{2}=4$$, $$E^{2}=-2$$, and $$H\cdot E=0$$.

Then $$H$$ is big and nef, but not ample since $$H\cdot E=0$$. We say that "$$\phi_{H}$$ contracts $$E$$"

#### An example of a line bundle whichis ample, but not very ample

Consider the 2:1 map $$\phi_{H}:S\to\mathbb{P}^{2}$$ which is branched on a sextic curve. Then $$H$$ is not very ample, but $$H$$ is ample.
