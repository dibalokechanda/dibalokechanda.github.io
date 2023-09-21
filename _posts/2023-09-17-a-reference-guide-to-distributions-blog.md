---
title: A Reference Guide to Distributions
date: 2023-09-17 12:00:00 -500
categories: [fundamentals]
tags: [distributions,probability_theory]
math: true
toc: true
---

## ⦿ Discrete Probability Distributions

### ⯈ Bernoulli Distribution

<u>Probability Density Function:</u>

$$
\begin{align*}
\operatorname{P}(X=x \mid p) &=p^{x}(1-p)^{1-x} \\
&= \begin{cases}p & x=1 \\ 1-p & x=0\end{cases}
\end{align*}
$$

$$
\text { where, }  p \in[0, 1]
$$

Here,

- $p$ is the probability of success and $(1-p)$ is the probability of failure
- $x=1$ defines the success event and $x=0$ defines the failure event


![bernouli](https://i.ibb.co/D8SqsR2/chrome-Rnw-GIVNZj-R.png)

<u>Cumulative Density Function:</u>


$$
\begin{cases}0 & \text { if } x<0 \\ 1-p & \text { if } 0 \leq x<1 \\ 1 & \text { if } x \geq 1\end{cases}
$$


<u>Expected Value:</u>

$$

\boxed{E(X)=p}

$$


<u>Variance:</u>

$$
\boxed{Var(x)=p(1-p)}
$$

<u>Properties and Key Facts:</u>

- The number of trials is equal to $1$.
- Model events when there are only two possible outcomes : success and failure. 
- Binomial distribution, Negative Bionomial Distribution and Geometric Distribution are built upon the idea of bernoulli trials.

### ⯈ Bionomial Distribution

<u>Probability Density Function:</u>

$$
\boxed{P(X=x|p)= \binom{n}{x} p^x (1-p)^{n-x}= \frac{n!}{x!(n-x)!}p^x (1-p)^{n-x}}
$$

where,

- $n$ is the number of trials
- $p$ is the probability of success and $(1-p)$ is the probability of failure for an individual trial
- $x$ is the number of success out of $n$ trials 

<u>Expected Value:</u>

$$
\boxed{E(x)=np}
$$

<u>Variance:</u>

$$
\boxed{Var(x)=np(1-p)}
$$


<u>Properties and Key Facts:</u>

 - Involves $n$ independent bernoulli trials


## ⦿ Continuous Probability Distributions

### ⯈ Gaussian Distribution
<hr>

<u>Probability Density Function:</u>

$$
\boxed{f(x \mid \mu, \sigma)= \frac{1}{\sqrt{2\pi \sigma^{2}}} \exp({-\frac{(x-\mu)^{2}}{2\sigma^{2}}})}
$$


<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\boxed{E(x)=\mu}

$$


<u>Variance:</u>

$$
\boxed{Var(x)=\sigma^{2}}

$$

<u> Multivariate case (PDF):</u>

$$
f(x \mid \mu, \Sigma)=\frac{1}{(2 \pi)^{D / 2}|\Sigma|^{1 / 2}} \exp \left\{-\frac{1}{2}(\mathbf{x}-\mu)^{\top} \Sigma^{-1}(\mathbf{x}-\mu)\right\}
$$

Here,

- $D$ is the number of dimensions
- $\mu$ is the mean vector
- $\Sigma$ is the covariance matrix


### ⯈ Beta Distribution

<hr>



<u>Probability Density Function: </u>


$$
\boxed{f(x \mid \alpha, \beta)=\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha) \Gamma(\beta)} x^{\alpha-1}(1-x)^{\beta-1}}
$$

$$
\text { where, } \alpha, \beta>0, x \in[a, b]
$$

Here, $\Gamma(x)$ is the gamma function defined as $\Gamma(x-1)!$

<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\boxed{E(x)=\frac{\alpha}{\alpha+\beta}}

$$

<u>Variance:</u>

$$
\boxed{Var(x)=\frac{\alpha \beta}{(\alpha+\beta)^2(\alpha+\beta+1)}}
$$

<u>Properties and Key Facts:</u>

 - Known as "The Probability Distribution of Probabilities".
 - Bounded between $0$ to $1$. As it signifies the distribution of probability values it does not makes sense for it to have value not within the range  $0$ to $1$.
 - Suitable distribution model for the random behavior of percentages and proportions.
 - Has close connection to bernoulli distribution. Just as binomial distribution is a generalization bernoulli distribution, dirichlet distribution is a generationalization of beta distribution.
 - Member of the exponential family

###  ⯈ Gamma Distribution
<hr>



<u>Probability Density Function:</u>


$$
\boxed{f(x \mid \alpha, \beta)=\frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha-1} \mathrm{e}^{-\beta x}}
$$

There  is  another version of this distribution with only one parameter $\alpha$.

<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\boxed{E(x)=\alpha / \beta}

$$

<u>Variance:</u>

$$

\boxed{Var(x)=\alpha / \beta^{2}}

$$

###  ⯈ Inverse Gamma Distribution
<hr>

<u>Probability Density Function:</u>

$$
\boxed{f(x \mid \alpha, \beta)=\frac{\beta^\alpha}{\Gamma(\alpha)} x^{-\alpha-1} \mathrm{e}^{-\beta / x}}
$$

$$
\text { where, } \alpha, \beta>0,0<x<\infty
$$

<u>Cumulative Density Function:</u>

<b>No Closed Form Analytical Equation</b>

<u>Expected Value:</u>

$$

\boxed{E(x)=\frac{\beta}{\alpha-1}}

$$


<u>Variance:</u>

$$
\boxed{Var(x)=\frac{\beta^2}{(\alpha-1)^2(\alpha-2)}}
$$