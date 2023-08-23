---
title: Kullback–Leibler divergence
date: 2023-08-21 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

There are two ways to introduce KL divergence, one is with the notion of "distance between distributions"  and another is with information theory. I will first introduce it with the first approach and then connect it back to the information-theoretic approach.

## "Distance" between two distributions

Let consider a discrete random variable $X$ where the samples of the random variable are $X=\{x_{1},x_{2},x_{3},\cdots,x_{n}\}$. Suppose there are two distribution $p_{\theta}$ and $q_{\phi}$. The subscript denotes the parameters of the distribution. One key thing to notice here, we are not claiming that the distribution is the same class of distributions. 


For one specific sample of the distribution we can compute $p_{\theta}(x_{1})$ and $q_{\phi}(x_1)$. How do we measure the distance between these two evaluations? Just taking the difference seems like a good idea. But one important thing to keep in mind is, that we are dealing with a probability value, which is why it is better to take the $\log$ of these quantities first and then take the difference.
