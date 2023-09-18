---
title: A Reference Guide to Distributions
date: 2023-08-26 12:00:00 -500
categories: [fundamentals]
tags: [distributions,probability_theory]
math: true
toc: true
---

Most of us who have been doing research in the machine learning domain already familiar with basic probability distributions. This article will serve as a reference for those distributions mentioning their key aspects. 

## Continuous Probability Distributions

### Gaussian Distribution

<u>Probability Density Function:</u>

$$
f(x \mid \mu, \sigma)= \frac{1}{\sqrt{2\pi \sigma^{2}}} \exp({-\frac{(x-\mu)^{2}}{2\sigma^{2}}})
$$


<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\mu

$$



### Beta Distribution

<hr>

$$\text{`` The Probability Distribution of Probabilities "}$$




<u>Probability Density Function:</u>


$$
f(x \mid \alpha, \beta)=\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha) \Gamma(\beta)} x^{\alpha-1}(1-x)^{\beta-1}
$$

<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\frac{\alpha}{\alpha+\beta}

$$