---
title: Jensen's Inequality
date: 2023-08-26 12:00:00 -500
categories: [fundamentals]
tags: [convexity, information_theory]
math: true
toc: true
---


## The Basic Idea

Jensen's inequality requires prerequisite knowledge about the definition of convex functions. I will assume the readers are somewhat familiar with convexitiy of functions.

Jensen's inequality is one of most fundamental concept which connects a lot of different ideas in information theory. Most of things we taken for granted in information theory or hand-wave with intuition are proved with Jensen's inequality.

The statement says that given a real-valued convex function $f(\cdot)$ and a random variable $X$ the following inequality relation holds true:

$$
f(\mathbb{E}[X]) \leq \mathbb{E}[f(X)]
$$

There are two components to this inequality relation. The first component is a convex function $f(\cdot)$ and another is a random variable $X$. Now as we are dealing with a random variable there has to be distribution associated with it. There is no restriction on what kind of distribution it could be. For the purpose of visualization, I chose normal distribution.

![jensen_inequality](https://i.ibb.co/fHL8P2x/chrome-K1h-MCRJ6-Pf.png)


<b>Right Hand Side</b> : $\mathbb{E}[f(X)]$


To get this quantity we need to sample from the distribution associated with $X$ and plug them into the convex function $f(\cdot)$  and we will get outputs $f(X)$. Then we apply expectation to get $\mathbb{E}[f(x)]$.

![JIE_1](https://i.ibb.co/8br4qWP/chrome-MKXKZa-Qz-Rp.png)


<b>Left Hand Side</b> : $f(\mathbb{E}[X])$

To get this quantity we first compute the expectation of the random variable to get $\mathbb{E}[X]$. Then we plug that into the convex function $f(\cdot)$ to get $f(\mathbb{E}[X])$.

![JIE_2](https://i.ibb.co/PxPYpyz/chrome-ki-OBst-NSCt.png)

One thing to note here, this holds for any number of sample points (more than one) and for any number of dimensions. 
## Application of Jensen's Inequality

Well there are numerous application, but to keep it concise I will provide two such application. One is in the proof of non-negativity of KL divergence. Another is it's usage in the wild, a research paper related to explainability in graph neural network.




# References

[1] [Duane Rich (2021). *Jensen’s Inequality*. YouTube. Available at: https://www.youtube.com/watch?v=u0_X2hX6DWE [Accessed 26 Aug. 2023]](https://www.youtube.com/watch?v=u0_X2hX6DWE).

[2] [MIT OpenCourseWare (2018). *S18.2 Jensen’s Inequality*. YouTube. Available at: https://www.youtube.com/watch?v=GDJFLfmyb20 [Accessed 27 Aug. 2023]](https://www.youtube.com/watch?v=GDJFLfmyb20).