+++
title = "Introduction to K3 Surfaces"
summary = "Notes from K3 Surfaces Reading Seminar, Autumn Semester 2019-2020 at The University of Sheffield"

date = 2019-09-30T00:00:00
lastmod = 2019-09-30T00:00:00

markup = "mmark"
draft = false  # Is this a draft? true/false

+++

Lecture given by Evgeny Shinder, notes taken by Edward Pearce, 30/09/2019, 3pm-4:30pm at The University of Sheffield, based on Daniel Huybrechts' book [Lectures on K3 surfaces](http://www.math.uni-bonn.de/people/huybrech/K3Global.pdf).

## Calabi-Yau varieties and canonical classes

### Definition (CY variety)

A (generalized) Calabi-Yau variety is a variety $$X$$ with a non-vanishing global holomorphic top-form $$\sigma\in\Omega_{X}^{n}(X)$$, where $$\Omega_{X}^{1}=T^{\ast}$$ is the cotangent bundle and $$\Omega_{X}^{j}=\bigwedge^{j}\Omega_{X}^{1}$$, and $$n=\dim X$$

More generally, for any $$X$$, let $$\sigma$$ be a meromorphic top-form on $$X$$, and let 

$$\mathrm{div}(\sigma) = \sum_{D\subset X}\mathrm{ord}_{D}(\sigma)\cdot[D]\in\mathrm{Div}(X)$$

Where the sum is over irreducible divisors $$D$$ in $$X$$. Then $$\mathrm{div}(\sigma)$$ is called a canonical divisor.

### Exercise

If $$\sigma'$$ is another form, then $$\mathrm{div}(\sigma') - \mathrm{div}(\sigma)$$ is a principal divisor, i.e. a divisor of a meromorphic function. Hence $$\mathrm{div}(\sigma)$$ is well-defined in $$\mathrm{Pic}(X)=\mathrm{Div}(X)/\{\text{principal divisors}\}$$. We write $$K_{X}=\mathrm{div}(\sigma)$$.

The sheaf (or bundle) $$\omega_{X}=\Omega_{X}^{n}$$ is called the canonical line bundle.

In this language $$X$$ is Calabi-Yau if and only if $$K_{X}=0\in\mathrm{Pic}(X)$$ if and only if $$\omega_{X}\cong\mathcal{O}_{X}$$.

### Example: Curves

Let $$X$$ be a curve and $$g=g(X)$$ be its geometric genus. Then $$\Omega_{X}^{1}=\omega_{X}$$, $$\Gamma(X, \Omega_{X}^{1})=\mathbb{C}^{3}$$, and $$\deg K_{X}=2g-2$$.

- Fano ($$g=0$$), then $$X=\mathbb{P}^{1}$$, $$\sigma=\frac{dz}{z}$$. Exercise: $$\mathrm{div}(\sigma)=-[0]-[\infty]$$ and so $$\deg K_{X}=2$$.
- Calabi-Yau ($$g=1$$), then $$X$$ is an elliptic curve, $$\omega_{X}=\mathcal{O}_{X}$$, i.e. there exists a unique non-vanishing holomorphic 1-form (up to scaling)
- General type ($$g\ge2$$), then "general-type"

## Calabi-Yau Surfaces

There are two types of CY surfaces: abelian surfaces and K3 surfaces.
- For an abelian surface $$A$$, $$\pi_{1}(A)=\mathbb{Z}^{4}$$, $$H^{1}(A, \mathbb{Z})=\mathbb{Z}^{4}$$, $$H^{1}(A, \mathcal{O}_{A})=\mathbb{C}^{4}$$
- For a K3 surface $$S$$, $$\pi_{1}(S)=0$$, $$H^{1}(S, \mathbb{Z})=0$$, $$H^{1}(S, \mathcal{O}_{S})=0$$

### Definition (K3 Surface)

A K3 surface is a CY surface with $$H^{1}(S, \mathbb{Z})=0$$ (in this setting we can replace the last condition by $$\pi_{1}(S)=0$$ simply connected, or $$H^{1}(S, \mathbb{Z})=0$$.

### Examples of K3 surfaces

- $$A=E\times E'$$ an abelian surface formed as the product of two elliptic curves
- $$S\subset\mathbb{P}^{3}$$ a quartic surface. e.g. The Fermat quartic defined by $$X^{4}+Y^{4}+Z^{4}+W^{4}=0$$.

### Cohomology and Hodge structure

- Hodge decomposition: $$H^{n}(X, \mathbb{C})=\bigoplus_{p+q=m,\, p,q\ge0} H^{p, q}(X)$$
where $$H^{p, q}(X)\cong H^{q}(X, \Omega_{X}^{p})$$, $$\overline{H^{p, q}}(X)=H^{q, p}(X)\subset H^{n}(X, \mathbb{C})$$
- Hodge numbers $$h^{p, q}(X, \mathbb{C})=\dim H^{p, q}(X)$$
- Hodge diamond: Serre duality and Poincare duality imply vertical and horizontal symmetry, respectively. 

Horizontal rows in the bottom half describe the decomposition $$H^{m}(X, \mathbb{C})=\bigoplus_{p=0}^{m} H^{p, m-p}(X)$$ where $$m$$ runs from $$0$$ to $$n$$.

$$[[h^{n,n}],\ldots, [h^{0,n}, h^{1,n-1}, \ldots, h^{n-1,1}, h^{n,0}], \ldots, [h^{0,1}, h^{1,0}], [h^{0,0}]]$$

### Examples of Hodge diamonds

For $$X$$ a curve of genus $$g$$, the Hodge diamond is $$[[1], [g, g], [1]]$$

For $$X$$ a connected surface, the Hodge diamond is $$[[1], [q, q], [p, h, p], [q, q], [1]]$$ where $$q=h^{1,0}$$ is the number of 1-forms on $$X$$ and $$p=h^{2,0}$$ is the number of 2-forms on $$X$$ and $$h=h^{1,1}$$.

For $$A=E\times E'$$, $$[[1],[2,2],[1,4,1],[2,2],[1]]$$.

For $$S$$ a K3 surface, $$[[1],[0,0],[1,20,1],[0,0],[1]]$$.

For $$X=\mathbb{P}^{2}$$, $$[[1],[0,0],[0,1,0],[0,0],[1]]$$.

For $$X=\mathbb{P}^{1}\times\mathbb{P}^{1}$$, $$[[1],[0,0],[0,2,0],[0,0],[1]]$$.

To show that $$h^{1,1}=20$$ for a K3 surface, we need to apply Noether's formula.

### Noether's formula

- Holomorphic Euler characteristic: $$\chi(X, \mathcal{O}_{X})=h^{0,0}-h^{0,1}+h^{0,2}=\sum(-1)^{i}h^{i}(X, \mathcal{O}_{X})$$
- Topological Euler characteristic: $$\chi_{\text{top}}(X(\mathbb{C}))=\sum(-1)^{i}\dim H^{i}(X; \mathbb{Q})=c_{2}(X)$$
- Self-intersection number of the canonical divisor $$K_{X}$$: $$K_{X}^{2}=K_{X}\cdot K_{X}\in\mathbb{Z}$$
- Noether's formula for surfaces: $$12\cdot\chi(X, \mathcal{O}_{X})=K_{X}^{2}+\chi_{\text{top}}(X)$$

For example, for $$X=\mathbb{P}^{2}$$, $$\chi(X, \mathcal{O}_{X})=1$$, $$K_{X}=-3H$$ where $$H$$ is the class of a line, $$K_{X}^{2}=9$$, and $$\chi_{\text{top}}(X)=3$$.

Exercise: Show that $$h^{1,1}=20$$ for a K3 surface.

## Construction of K3 surfaces

### Computing canonical classes

- Fact 1: $$K_{\mathbb{P}^{N}}=-(n-1)H$$ where $$H$$ is a hyperplane divisor, and for $$\mathbb{P}^{1}$$ is $$\frac{dz}{z}$$.
- Fact 2: **Adjunction formula** For $$X\subset Y$$ a smooth divisor, then 
$$K_{X}=(K_{Y}+X)\big|_X\,\text{or}\,\omega_{X}=\omega_{Y}(X)\big|_X$$ where $$\omega_{Y}(X)=\omega_{Y}\bigotimes\mathcal{O}(X)$$

Exercise: Verify the adjunction formula for $$\mathbb{P}^{n-1}\subset\mathbb{P}^{n}$$.

#### Example 

For $$X\subset\mathbb{P}^{2}$$ a degree $$d$$ curve, $$\omega_{X}=\mathcal{O}(-3-d)$$.

Exercise: Deduce the genus-degree formula $$g=\frac{(d-1)(d-2)}{2}$$

#### Example

For $$S\subset\mathbb{P}^{3}$$ a degree $$d$$ surface, $$\omega_{S}=\mathcal{O}(-4-d)$$. Hence $$S$$ is Calabi-Yau if and only if $$d=4$$, $$\mathcal{O}(1)=\mathcal{O}(H)$$, and $$H^{1}(S, \mathcal{O}_{S})=0$$ by cohomology long exact sequence.

Exercise: Classify all K3 surfaces which are complete intersections of hypersurfaces. That is, $$S=H_{1}\cap\ldots\cap H_{r}\subset\mathbb{P}^{r+2}$$, where $$H_{i}$$ is a hypersurface of degree $$d_{i}$$. Hint: Induction on adjunction to get equations for $$d_{1},\ldots,d_{r}$$.

### Polarizations

Given $$S\subset\mathbb{P}^{N}$$, let $$H\in\mathrm{Pic}(S)$$ be the hyperplane section divisor. Such an $$H$$ is called a polarization of $$S$$.

#### Example

Let $$S\subset\mathbb{P}^{3}$$ be a quartic surface, and $$H\subset S$$ a quartic curve obtained as $$H=S\cap\mathbb{P}^{2}\subset\mathbb{P}^{3}$$, then $$H^{2}=4$$.

More generally, a polarization is the class of an ample divisor.

#### Example

Let $$S\to\mathbb{P}^{2}$$ be a 2-to-1 cover ramified in a degree 6 curve (sextic), then Riemann-Hurwitz formula and the vanishing of $$H^{1}(S, \mathcal{O}_{S})$$ implies that $$S$$ is a K3 surface, since $$K_{S}=\mathcal{O}(-3)\bigotimes\mathcal{O}(\frac{6}{2})=\mathcal{O}(S)$$.

## K3 in other categories

- Analytic K3 surfaces
- K3 surfaces over arbitrary fields
- Noncommutative K3 surfaces

### Definition (Analytic K3 surface)

A complex-analytic K3 surface is a compact analytic surface such that $$\omega_{S}\cong\mathcal{O}_{S}$$ and $$H^{1}(S, \mathcal{O}_{S})=0$$.

Remark: There exist many more analytic K3 surfaces than algebraic K3 surfaces.

#### Example

A complex torus $$A=\mathbb{C}^{2}/\Lambda$$, $$\Lambda\cong\mathbb{Z}^{4}$$.
Note: most of these are not algebraic.

Let $$S'A/\pm$$, i.e. quotient out 2-torsion points, that is, points (equivalence classes) for which $$\bar{z}=-\bar{z}$$, or equivalently $$2\bar{z}=0$$. This has 16 ordinary double points. Let $$S\to S'$$ be the blow up of these ordinary double points, then $$S$$ has $$\omega_{S}=0$$ and $$H^{1}(S, \mathcal{O}_{S})=0$$, so $$S$$ is a K3 surface.

Hence $$S$$ is algebraic if and only if $$A$$ is algebraic, where _algebraic_ means it can be embedded in $$\mathbb{P}^{N}$$ for some $$N$$. This $$S$$ is called a Kunicov K3 surface.

### Definition (K3 surface over an arbitrary field)

The same definition over an arbitrary field $$k$$ gives K3 surfaces over $$k$$. Usually we will work with complex algebraic projective K3 surfaces.

Let $$\rho=\mathrm{rank}\,\mathrm{Pic}(S)$$ noting that $$\mathrm{Pic}(S)$$ is a torsion-free finitely generated abelian group.

- For algebraic K3 surfaces over $$\mathbb{C}$$, $$1\le\rho\le20$$, where the lower bound is given by polarizations and the upper bound is given by $$h^{1,1}$$.
- For analytic K3 surfaces over $$\mathbb{C}$$, $$0\le\rho\le20$$.
- For algebraic K3 surfaces over characteristic $$p$$, $$1\le\rho\le22$$.

### Definition (Noncommutative K3 surfaces)

Starting from $$S$$, consider the bounded derived category $$\mathcal{D}^{b}(S)$$ of $$S$$ and the maps to: 

1. An abelian category $$\mathcal{A}$$ which is a K3 category with $$\mathcal{S}_{\mathcal{A}}=[2]$$ where $$\mathcal{S}_{\mathcal{A}}$$ is the Serre functor (autoequivalence) on $$\mathcal{A}$$ and $$[2]$$ is obtained by applying the triangulated structure autoequivalence $$[1]$$ on $$\mathcal{A}$$ twice.
2. The bounded derived category $$\mathcal{D}^{b}(S, \beta)$$ where $$\beta\in\mathrm{Br}(S)$$ is an element of the (braid? Brauer?) group(?) of $$S$$.
