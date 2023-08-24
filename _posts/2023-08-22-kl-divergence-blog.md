---
title: Kullback–Leibler divergence
date: 2023-08-21 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

There are two ways to introduce KL divergence, one is with the notion of "distance between distributions"  and another is with information theory. The latter one is more in line with what is really captured by KL divergence; but requires a lot of fundamental prerequisite concepts like entropy, mutual information, etc. Hence, I will introduce it with the first approach and then connect it back to the information-theoretic approach.

## "Distance" between two distributions

Let consider a discrete random variable $X$ where the samples of the random variable are $X=\{x_{1},x_{2},x_{3},\cdots\}$. Suppose there are two distribution $p_{\theta}$ and $q_{\phi}$. The subscript denotes the parameters of the distribution. One key thing to notice here, we are not claiming that the distribution is the same class of distributions because $\theta$ and $\phi$ are different. One can be a binomial distribution parameterized by $\theta$ and another can be poisson distribution parameterized by $\phi$. 


For one specific sample of the distribution, we can compute the likelihood $p_{\theta}(x_{1})$ and $q_{\phi}(x_1)$. How do we measure the distance between these two evaluations? Think of them as two values in a number line. We can just take the difference between them to get a measure of "distance". If the two distributions $p_{\theta}$ and $q_{\phi}$ are quite similar then the difference between $p_{\theta}(x_{1})$ and $q_{\phi}(x_1)$ should be low and vice versa.

But one important thing to keep in mind is, that we are dealing with a probability value, which is why it is better to take the $\log$ of these quantities first and then take the difference. This gives us $\log p_{\theta}(x_{1}) - \log q_{\phi}(x_{1})$ . But using the property of $\log$ we can get the following:-

$$
\log \left( \frac{p_{\theta}(x_1)}{q_{\phi}(x_1)} \right)
$$

which is called the likelihood ratio. Now, this is measuring "distance" for only sample $x_{1}$. We need to take into account all the samples $x_{1},x_{2},\cdots$ not just a single sample $x_{1}$. First, we can generalize the likelihood ratio by replacing index $1$ with $i$ and we get the following:s


$$
\log \left( \frac{p_{\theta}(x_i)}{q_{\phi}(x_i)} \right)
$$

We can take the weighted average of this "distance measure" for all samples of the random variable $X$. You can think of it like we are averaging all individual log-likelihood ratio values for the random variable $X$. Following this logic we can write the following:-

$$
\sum_{i=1} p_\theta\left(x_i\right) \log \left[\frac{p_\theta\left(x_i\right)}{q_\phi\left(x_i\right)}\right]
$$

This is the definition of KL divergence. For continuous random variable we can replace $\sum$ with $\int$ get the following:

$$

\int_{i=1} p_\theta\left(x_i\right) \log \left[\frac{p_\theta\left(x_i\right)}{q_\phi\left(x_i\right)}\right]

$$

For ease of writing it is conventional to drop $\theta$ and $\phi$ and just use $p$
and $q$ to refer to two separate distributions. Also, we don't need to explicitly show the summation of over indices. This gives the following equation for discrete random variable:

$$
 \boxed{D_{KL}(p||q)= \sum_{x\in \mathcal{X}}p(x) \log \frac{p(x)}{q(x)}}
$$

For continuous random variables the summation can be replaced by an integral sign and we get the following:

$$
 \boxed{D_{KL}(p||q)= \int_{x\in \mathcal{X}}p(x) \log \frac{p(x)}{q(x)}}
$$

## Why it is called "Divergence"?

One thing you might have noticed in the previous section I always used " " when using the word "distance". It was intentional because KL divergence is not a true "distance" measure in the sense it is not symmetric.