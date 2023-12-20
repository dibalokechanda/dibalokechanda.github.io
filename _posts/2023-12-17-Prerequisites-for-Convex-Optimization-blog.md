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

![convex_func](https://i.ibb.co/jhzGcny/chrome-Yh-Btw45cw4.png)

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

We also need to know how to formulate a convex optimization problem.



## Minimization or Maximization?


It does not matter if we need to minimize or maximize an objective function. For example suppose we need to minimize a objective function $f(\mathbf{x})$, which can be mathematically written as follows:

$$
\min f(\mathbf{x})

$$

This can be converted into a maximization problem as follows:


$$
\max -f(\mathbf{x})
$$


The other way is also true, a maximization can be converted into a minimization problem too. How an optimization problem should be posed depends on the context and the domain of the problem. 


## The formulation of a convex optimization problem


A standard convex optimization problem can be formed in the following way:

 $$
\begin{aligned}
\operatorname{minimize} & f_0(x) \\
\text { subject to: } & f_j(x) \leq 0 \quad \forall j \in 1,2, \ldots, J \\
& h_k(x)=0 \quad \forall k \in 1,2, \ldots, K
\end{aligned}
$$

Where all $f_j(x), j \in 0,1,2, \ldots J$ are convex and all $h_k(x), k \in 1,2, \ldots, K$ are affine.

Here,

- $f_0(x)$ is the objective function.
- $f_i(x)$ are the inequality constraints.
- $h_{k}(x)$ are the equality constraints.

Some other terminology to get familiar with:

- The feasible set is the set of points that satisfy the constraints
-  An inequality constraint can be in two states, active and inactive. For the values of $x$, $f_i(x)=0$, the inequality constraint is active. For the values of $x$, $f_i(x)<0$ the inequality constraint is inactive.


## Multivariate Calculus


### Gradient

For a function $f(\mathbf{x}): \mathbb{R}^n \rightarrow \mathbb{R}$, the gradient is defined as follows:


$$
\nabla f(\mathbf{x})=\frac{d f}{d \mathbf{x}}=\left(\begin{array}{c}
\frac{\partial f}{\partial x_1} \\
\frac{\partial f}{\partial x_2} \\
\vdots \\
\frac{\partial f}{\partial x_n}
\end{array}\right)
$$


Two key things about the gradient of a function:

- The gradient points to the direction of the steepest ascent. Additionally, $-\nabla f(\mathbf{x})$ is the direction of the steepest descent.

- The gradient vectors are always orthogonal to the contour lines. 

### Hessian 

For a function $f(\mathbf{x}): \mathbb{R}^n \rightarrow \mathbb{R}$, the hessian is defined as follows:

$$
\nabla^2 f(\mathbf{x})=\frac{\partial^2 f}{\partial x_i \partial x_j}=\left(\begin{array}{cccc}
\frac{\partial^2 f}{\partial x_1 \partial x_1} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2 \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n \partial x_n}
\end{array}\right)
$$


## Taylor Series Approximation 



## Supremum and Infimum

This is a "hard" concept to get your head around. Sometimes to avoid rigorous definitions, supremum is replaced with "max" and infimum is replaced with "min". This is fine as long as your optimization problem is "nice" and "well-behaved". Therefore, there is a good chance you can get away with just "min" and "max". But most of the resources you will come across, prefer "supremum" and "infimum" to enforce mathematical rigor. The definitions I will provide below are by no means a complete definition; because you can always argue about the "rigorousness" of the definition, but they should be enough to understand their usage in convex optimization.  


### Supremum 



## Subgradients