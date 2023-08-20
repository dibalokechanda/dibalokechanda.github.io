---
title: Notations-1
date: 2023-08-20 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---
To keep consistency for the readers and for my own sanity, this article will be used as a reference for notations for the following articles:

- [Self Information](https://dibalokechanda.github.io/posts/self-information-blog/)
- [Entropy](https://dibalokechanda.github.io/posts/entropy-blog/)
- [Mutual Information](https://dibalokechanda.github.io/posts/mutual-information-blog/)

The common notations are related to random variables, probability density function (PDF) and probability mass function (PMF).

| Notation                                    | Symbol        |
|---------------------------------------------|---------------|
| Random Variable                             | $X$           |
| Sample Value of a Random Variable           | $x$           |
| Set of Possible Sample Values of $X$        | $\mathcal{X}$ |
| Probability Distribution (Both PDF and PMF) | $p(x)$        |
| Probability Mass Function (PMF)             | $P_{X}(x)$    |
| Probability Density Function (PDF)          | $p_{X}(x)$    |


The notation $p(x)$  is used as a general placeholder for probability distributions. If a statement is true for both discrete random variables and continuous random variables to keep it general, I will use $p(x)$ and I hope readers will be to distinguish based on the context. For example, if I use a summation symbol $\sum$ with $p(x)$, readers can assume that statement or equation can be generalized to an integration symbol $\int$ for continuous random variables.  

# Other Notations

- $\log$ : Assume natural logarithm or  $\log$ base-$e$