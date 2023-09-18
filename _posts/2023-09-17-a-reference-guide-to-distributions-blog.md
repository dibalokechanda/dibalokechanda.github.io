---
title: A Reference Guide to Distributions
date: 2023-09-17 12:00:00 -500
categories: [fundamentals]
tags: [distributions,probability_theory]
math: true
toc: true
---


## Continuous Probability Distributions

### Gaussian Distribution

<u>Probability Density Function:</u>

$$
\boxed{f(x \mid \mu, \sigma)= \frac{1}{\sqrt{2\pi \sigma^{2}}} \exp({-\frac{(x-\mu)^{2}}{2\sigma^{2}}})}
$$


<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\boxed{\mu}

$$


<u>Variance:</u>

$$
\boxed{\sigma^{2}}

$$


### Beta Distribution

<hr>






<u>Probability Density Function:</u>


$$
\boxed{f(x \mid \alpha, \beta)=\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha) \Gamma(\beta)} x^{\alpha-1}(1-x)^{\beta-1}}
$$


$$
\text { where, } \alpha, \beta>0, x \in[a, b]
$$
<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\boxed{\frac{\alpha}{\alpha+\beta}}

$$

<u>Variance:</u>

$$
\boxed{\frac{\alpha \beta}{(\alpha+\beta)^2(\alpha+\beta+1)}}
$$

<u>Properties:</u>

 - Known as "The Probability Distribution of Probabilities".
 - Bounded between $0$ to $1$. As it signifies the distribution of probability values it does not makes sense for it to have value not within the range  $0$ to $1$.
 - Suitable distribution model for the random behavior of percentages and proportions.

<u>Visualizations:</u>

- How the parameter change of $\alpha$ and $\beta$ change the shape of the distribution (Visualization taken from Wikipedia).

<center>

 ![beta_distribution](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/PDF_of_the_Beta_distribution.gif/330px-PDF_of_the_Beta_distribution.gif)
 
 </center>