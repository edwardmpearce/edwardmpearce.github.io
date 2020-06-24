+++
title = "Partitions and Hilbert schemes"
summary = "Notes from Algebraic Geometry Seminar, Autumn Semester 2019-2020 at The University of Sheffield"

date = 2019-10-01T00:00:00
lastmod = 2019-10-01T00:00:00

markup = "mmark"
draft = false  # Is this a draft? true/false

+++

Lecture given by Paul Johnson, notes taken by Edward Pearce, 01/10/2019, 12pm-1pm at The University of Sheffield.

## Relation to Representation theory

| Topology of $$\mathrm{Hilb}(S)$$ | Representation of some algebra | Quiver varieties | Partitions |
|:-------------:|:---------------:|:-----------:|:-----------:|
| Cohomology $$H^{\ast}$$ | Heisenberg algebra | | |
| Homology $$H_{\ast}$$ | Virasoro algebra | | |
| K-theory $$K$$ | Hall algebra | | |
| Derived Category $$\mathcal{D}$$ | | | |

## Partitions

For a partition $$\lambda=(5,3,3,2,1,1)$$, the size of $$\lambda$$, denoted $$|\lambda|$$, is the sum of its parts, here 15, and the length of $$\lambda$$, denoted $$\ell(\lambda)$$, is the number of parts, here 6.

Let $$\mathcal{P}$$ denote the set of all partitions, and $$\mathcal{P}(n)$$ denote the set of partitions of (size) $$n$$.

### First theorem of partitions: Euler product formula

$$\sum_{\lambda\in\mathcal{P}}q^{|\lambda|}t^{\ell(\lambda)}=\prod_{m\ge1}\frac{1}{1-tq^{m}}=:\frac{1}{(t;q)_{\infty}}$$

where we call $$(t;q)_{\infty}$$ the Pochammer symbol.

We define the arm and leg of a cell/box in a partition, and the hook length of a cell as $$h(\square)=1+a(\square)+l(\square)$$.

From the representation theory of symmetric groups, we get the hook length formula 

$$\dim\lambda=\frac{|\lambda|!}{\prod_{\square\in\lambda}h(\square)}$$

### Cores and quotients

Define the $$r$$-hook dimension of a partition $$\lambda$$ to be

$$h_{r}(\lambda):=|\{\square\in\lambda:a(\square)>0, h(\square)\equiv0\bmod r\}|$$

We call a partition $$\lambda$$ an $r$-core if $$r$$ does not divide $$h(\square)$$, i.e. $$r\nmid h(\square)$$, for any $$\square\in\lambda$$. Consequently, for $$\lambda$$ an $$r$$-core, $$h_{r}(\lambda)=0$$.

The generating function involving $$h_{r}(\lambda)$$ can be expressed using the following product formula

$$\sum_{\lambda\in\mathcal{P}}q^{|\lambda|}t^{h_{r}(\lambda)}=\prod_{m\ge1}\frac{(1-q^{rm})^{r}}{1-q^{m}}\cdot\frac{1}{(1-q^{rm}t^{m-1})(1-q^{rm}t^{m})^{r-1}}$$

where the factor $$\frac{(1-q^{rm})^{r}}{1-q^{m}}$$ corresponds to the generating function for $$r$$-cores.

### Generalized cores

Let $$0 < k < r$$ be coprime integers, and define the $$k/r$$-hook dimension of a partition $$\lambda$$ to be

$$h_{k/r}(\lambda):=|\{\square\in\lambda:a(\square)>0, ka(\square)-l(\square)-1\equiv0\bmod r)\}|$$

This is a generalization of the previous hook dimension since $$h_{(r-1)/r}=h_{r}$$. 

Define the $$k/r$$-hook dimension generating function to be

$$G_{k/r}=\sum_{\lambda\in\mathcal{P}}q^{|\lambda|}t^{h_{k/r}(\lambda)}$$

Gusein-Zade, Luengo, and Melle-Hernandez conjectured a product formula for the following case:

$$G_{1/3}=\frac{1}{(q;q^{3}t)_{\infty}}\cdot\frac{1}{(q^{2}t;q^{3}t)_{\infty}}\cdot\frac{1}{(q^{3};q^{3}t)_{\infty}}=\big(\frac{1}{1-q}\frac{1}{1-q^{2}t}\frac{1}{1-q^{3}}\big)\big(\frac{1}{1-q^{4}t}\frac{1}{1-q^{5}t^{2}}\frac{1}{1-q^{6}t}\big)\ldots$$

This summer Johnson and Rennemo proved a general product formula for $$G_{k/r}$$.

## Hilbert schemes

Definition: $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})=\{I\vartriangleleft R:\dim_{\mathbb{C}}R/I=n\}$$ where $$R=\mathbb{C}[x, y]$$.

If $$I$$ is a reduced ideal, then we can interpret $$R/I$$ as functions vanishing on $$n$$ points in $$\mathbb{C}^{2}$$. Therefore we may identify the reduced Hilbert scheme of $$n$$ points on the complex plane with the smooth locus of $$\mathbb{C}^{2n}/S_{n}$$. That is, 

$$\mathrm{Hilb}_{n}^{\text{red}}(\mathbb{C}^{2})\cong\big(\mathbb{C}^{2n}\setminus\{p_{i}=p_{j}\}\big)/S_{n}=\big(\mathbb{C}^{2n}/S_{n}\big)_{\text{smooth}}$$

If points collide, then $$\mathbb{C}^{2n}/S_{n}$$ becomes singular, and $$\mathrm{Hilb}$$ fixes this by taking a resolution of singularities.

### Example $$\mathrm{Hilb}_{2}(\mathbb{C}^{2})$$

Consider the family of ideals 

$$I_{t}=(x,y)\cap(x-at,y-bt)=(x^{2}-axt,xy-bxt,xy-ayt,y^{2}-byt)$$

which represent two points in $$\mathbb{C}^{2}$$ which get closer and closer as $t$ tends to $0$.

If we naively take the limit $$t=0$$, we would obtain $$I_{0}=(x^{2},xy,y^{2})$$, but then $$\dim_{\mathbb{C}}R/I_{0}=3\ne2$$, so $$I_{0}\notin\mathrm{Hilb}_{2}(\mathbb{C}^{2})$$. 

However, since $$ayt-bxt=(ay-bx)t\in I_{t}$$ for all $t$ it follows that $$ay-bx\in I_{t}$$ for all $t$, and indeed for $$I_{0}'=(x^{2},xy,y^{2}, ay-bx)$$ we have $$\dim_{\mathbb{C}}R/I_{0}'=2$$ and so $$I_{0}'\in\mathrm{Hilb}_{2}(\mathbb{C}^{2})$$. 

Therefore, in the case of points colliding, the Hilbert scheme retains extra information (the tangent direction of collision) which resolves the singularities along the diagonal of $$\mathbb{C}^{2n}/S_{n}$$.

### Facts about $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$

#### Hilbert-Chow morphism 

$$\pi:\mathrm{Hilb}_{n}(\mathbb{C}^{2})\to\mathbb{C}^{2n}/S_{n}$$ is a crepent resolution of singularities, which means that $$\pi^{\ast}(K_{\mathbb{C}^{2n}/S_{n}})=K_{\mathrm{Hilb}_{n}(\mathbb{C}^{2})}$$. In other words, the pullback along $$\pi$$ of the canonical bundle of $$\mathbb{C}^{2n}/S_{n}$$ is equal to the canonical bundle of $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$.

#### Cohomology of $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$

The Euler characteristic of $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$ is equal to the number of partitions of size $$n$$. That is 

$$\chi(\mathrm{Hilb}_{n}(\mathbb{C}^{2}))=p(n)$$

An algebraic torus $$T=(\mathbb{C}^{\times})^{2}$$ acts on the complex plane $$\mathbb{C}^{2}$$ and hence on $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$.

The fixed points of this action are the monomial ideals in $$\mathbb{C}[x,y]$$, which are of the form $$I=(x^{a_{i}}y^{b_{i}})$$ for a finite set of non-negative integer pairs $$(a_{i},b_{i})$$, and these in turn are in bijection with the set of partitions of size $$n$$.

Using Białynicki-Birula decomposition (algebraic Morse theory), we can compute 

$$\sum_{k}h_{k}(\mathrm{Hilb}_{n}(\mathbb{C}^{2}))\cdot t^{k}=\sum_{\text{fixed points partitions}}t^{f(\lambda)}$$

where $$f(\lambda)$$ encodes data about the tangent space $$T_{\lambda}\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$ to $$\mathrm{Hilb}_{n}(\mathbb{C}^{2})$$ at $$\lambda$$ as a $T$-representation.

Ellingrud-Stromme proved that

$$\sum_{k,n}h_{k}(\mathrm{Hilb}_{n}(\mathbb{C}^{2}))t^{k}q^{n}=\prod_{m\ge1}\frac{1}{1-q^{m}t^{2m-2}}$$

Gottsche proved that for $S$ any smooth quasiprojective surface, we have 

$$\sum_{k,n}h_{k}(\mathrm{Hilb}_{n}(S))t^{k}q^{n}=\prod_{\text{2 basis of }H_{0}(S)}\frac{1}{(qt^{\deg2};q^{m}t^{\alpha})_{\infty}}$$

whilst noting that $$S$$ has only even cohomology.

The formula from the main theorem resembles Gottsche's formula with $r$ cohomology classes - some are in $$h_{0}$$ and some are in $$h_{2}$$.

$$G_{k/r}$$ is a formula for

$$\sum_{n,k}h_{k}(\mathrm{Hilb}_{n}(\big[\mathbb{C}^{2}/\mathbb{Z}_{r}\big]))q^{n}t^{k}$$

where $$\mathbb{Z}_{r}$$ acts on $$\mathbb{C}^{2}$$ linearly via $$\left(\begin{array}{cc}e^{\frac{2\pi i}{r}} & 0\\0 & e^{\frac{2\pi i}{r}}\end{array}\right)$$.
