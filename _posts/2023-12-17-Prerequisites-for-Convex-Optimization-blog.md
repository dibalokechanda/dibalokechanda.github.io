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

![convex_sets](https://i.ibb.co/d2rbV19/chrome-M4ke-MXX5-Sd.png)

A set $C$ is convex if the line segment between any two points in $C$ lies in $C$, i.e. if for any $x_1, x_2 \in C$ and any $\theta$ with $0\leq\theta\leq 1$, we have

$$
\theta x_1+(1-\theta) x_2 \in C
$$


The above picture shows a visualization of a convex set and a non-convex set in 2D. But this is a really general concept that can be easily extended to any number of dimensions.  For example, a visualization of convex and non-convex set in 3D is shown below:


![convex_sets_3d](https://i.ibb.co/zsfCd7c/chrome-fet1u-Ae-Cp2.png)