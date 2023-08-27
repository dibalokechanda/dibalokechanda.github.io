---
title: Notations-1
date: 2023-08-19 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---
To keep consistency for the readers and my sanity, this article will be used as a reference to introduce notations for the following articles:

- [Self Information](https://dibalokechanda.github.io/posts/self-information-blog/)
- [Entropy](https://dibalokechanda.github.io/posts/entropy-blog/)
- [Joint, Conditional and Marginal Entropy](https://dibalokechanda.github.io/posts/joint-conditional-marginal-entropy-blog/)
- [Mutual Information](https://dibalokechanda.github.io/posts/2023-mutual-information-blog/)
- [Kullback–Leibler Divergence](https://dibalokechanda.github.io/posts/kl-divergence-blog/)

The common notations are related to random variables, probability density function (PDF) and probability mass function (PMF).

| Notation                                    | Symbol                  |
|---------------------------------------------|-------------------------|
| Random Variable                             | $X$                     |
| Sample Value of a Random Variable           | $x$                     |
| Set of Possible Sample Values of $X$        | $\mathcal{X}$           |
| Probability Distribution (Both PDF and PMF) | $p(x)$                  |
| Probability Mass Function (PMF)             | $P_{X}(x)$              |
| Probability Density Function (PDF)          | $p_{X}(x)$              |
| Expectation over Distribution $p$           | $\mathbb{E}_{x \sim p}$ |


The notation $p(x)$  is used as a general placeholder for probability distributions. If a statement is true for both discrete random variables and continuous random variables to keep it general, I will use $p(x)$ and I hope readers will be able to distinguish based on the context. For example, if I use a summation symbol $\sum$ with $p(x)$, readers can assume that statement or equation can be generalized to an integration symbol $\int$ for continuous random variables.  

# Other Notations

- $\log$ : Assume natural logarithm or  $\log$ base-$e$. Most resources you will come across for these topics, tend to use base- $2$ logarithm, but in the machine learning domain, it is common practice to use a base- $e$ logarithm.

- $I(X; Y)$: You can find more information about using a semicolon [here](https://math.stackexchange.com/questions/3820274/what-does-the-semicolon-mean-in-ixy-mutual-information). I might have as well used $I(X, Y)$ instead.

- $D_{KL}(p||q)$: Even though it depends on the context of what I am talking about, in general, consider $p$ as the true/target distribution which we are trying to approximate and $q$ as the parameterized distribution. Most of these are only applicable when talking about variational inference.

- In general, usually, I won't express distribution as parameterized. For example instead of using $p_{\theta}$ which is distribution $p$ parameterized by $\theta$, I will use $p$ only. I expect readers to understand from context if a distribution can be parameterized or not. For example in the context of a supervised classification problem, if $D_{KL}(p||q)$ is used, it usually means $p$ is the true data distribution (where parameterization does not make sense) and $q$ is the parameterized model generated distribution.