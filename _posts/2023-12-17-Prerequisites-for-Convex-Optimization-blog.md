---
title: Prerequisites for Convex Optimization
date: 2023-12-17 12:00:00 -500
categories: [fundamentals]
tags: [optimization_theory, convexity]
math: true
toc: true
---


Convex Optimization is a huge topic with thousands of research works published in this domain. Before the Deep learning revolution started, they were one of the coolest approaches to solving optimization problems. I will attempt to cover some prerequisite concepts that need to be learned before delving into convex optimization theory.

Most of this post is from [Convex Optimization – Boyd and Vandenberghe](https://web.stanford.edu/~boyd/cvxbook/). Interested readers can refer to it for more details.





## Convex Sets

![convex_sets](https://i.ibb.co/tC3GG3v/chrome-t-W3nv-Re2-A2.png)

A set $C$ is convex if the line segment between any two points in $C$ lies in $C$, i.e. if for any $x_1, x_2 \in C$ and any $\theta$ with $0\leq\theta\leq 1$, we have

$$
\theta x_1+(1-\theta) x_2 \in C
$$

$$
\forall \theta \in[0,1], \forall x_1, x_2 \in C
$$



Here, $\theta x_1+(1-\theta) x_2 $ represents all possible points in the line segment between $x_1$ and $x_2$ by letting $\theta$ vary.

The above picture shows a visualization of a convex set and a non-convex set in 2D and 3D. But this is a really general concept that can be easily extended to any number of dimensions. 


## Key Facts about Convex Sets

I will simply state some key facts about convex sets without going into rigorous proofs.


- The empty set $\emptyset$ is a convex set.

-  $\mathbb{R}^{d}$ is a convex set.

-  Affine transformation (scaling and translation) of a convex set produces a convex set.

- The intersection of convex sets are also convex sets.

- Hyperplanes are convex sets.

- The set $\alpha C$ is convex for any convex set $C$ and scalar $\alpha$.


## Convex Functions

![](https://i.ibb.co/jhzGcny/chrome-Yh-Btw45cw4.png)

A function $f$ is a convex function if the following definition holds:

$$
f(\lambda x+(1-\lambda) y) \leq \lambda f(x)+(1-\lambda) f(y)
$$

$$
\forall~\lambda \in [0,1]
$$



Look into [Jensen's inequality](https://dibalokechanda.github.io/posts/Jensen's-Inequality-blog/) to get a better sense of this definition. A much simpler interpretation of this is :

The chord formed by connecting two points on the functions is above the function.

Another definition can be given with epigraph.

$$
\operatorname{epi}(f)=\left\{(x, t) \mid x \in \mathbb{R}^n, t \in \mathbb{R}, \text { and } t \geq f(x)\right\}
$$

In simpler terms, the epigraph of a function includes all the points that lie above or on the graph of the function. If $f$ is a convex function, its epigraph will be a convex set. 


![epigraph_def](https://i.ibb.co/Yjsd0Hs/chrome-Va-Ry-T3-Fp-AI.png)

Now these two definitions are actually not that useful in practice, because most of the time we deal with high-dimensional functions that we can not visualize. The way to go about it is to recognize some common convex functions (I know it sounds bad). 



- $f(\mathbf{x})=\mathbf{x}^T \mathbf{A}\mathbf{x}$ is a convex function if $\mathbf{A}\succeq0$.

- $f(x)=\frac{1}{2} x^T A x+b^T x+c$ is a convex function if  $\mathbf{A}\succeq0$.

- $\frac{1}{2}\|X w-y\|^2=\frac{1}{2} w^T X^T X w-y^T X w+\frac{1}{2} y^T y$ is convex.


Checking if the hessian (if it exists) is positive semidefinite is one of the easiest ways to check for convexity.


## Key Facts about Convex Functions


 - Any local minimum is a global minimum.

 - If hessian exists, the hessian is positive semidefinite.

 - Level sets of convex functions are convex functions.

 - The linear combination of a convex function is convex. This means $a \cdot f(x)+b \cdot g(x)$ is convex for convex $f$ and $g$ and $a,b>0$.

 - $\max (f(x), g(x))$ is convex for convex $f$ and $g$.



