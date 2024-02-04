---
title: A Reference Guide to Statistics
date: 2023-08-30 12:00:00 -500
categories: [statistics]
tags: [statistics,inferential_statistics]
math: true
toc: true
---

This article acts as a repository of the concepts I learned about any topics in Statistics. I plan to use this as a reference for ideas/concepts/formulas in Statistics. Essentially this is a look-up reference guide; if I forget any specific topic, I can revise that topic again. A significant portion of these concepts is based on the videos from the following YouTube channels.

- [Simple Learning Pro](https://www.youtube.com/@Simplelearningpro/videos)
- [jbstatistics](https://www.youtube.com/@jbstatistics/videos)
- [zedstatistics](https://www.youtube.com/@zedstatistics/videos)

In addition, several blog posts and texts are also used as references. 


## Inferential Statistics 


>### Sampling 
<hr>

*References:* [Sampling Distributions (7.2)](https://www.youtube.com/watch?v=7S7j75d3GM4)

 - A <b>sample</b> is a small portion of the population that we examine and draw conclusions from.

 - The <b>process</b> of drawing a sample from the population is known as sampling. 


#### Sample Distribution

When we draw a particular sample from a distribution, that specific sample creates a distribution. This is known as the "sample distribution".

#### Sampling Distribution

The sampling distribution of a <b>statistic</b> is the probability distribution of that <b>statistic</b>. This means if we draw samples from the <b>population</b> a bunch of times, the distribution associated with a particular <b>statistic</b> is referred to as the <b>sampling</b> distribution. 

> The sample statistic is known as the point estimate of the population parameter.
{: .prompt-tip }


#### Sampling Distribution of the Sample Mean

*References:* [Sampling Distributions (7.2)](https://www.youtube.com/watch?v=7S7j75d3GM4), [The Sampling Distribution of the Sample Mean](https://www.youtube.com/watch?v=q50GpTdFYyI) 

For example, let's use "mean" as the statistic. In that case, given a population (say all people in Wisconsin) and a random variable (say weight) we have a "true" population distribution of people's weights. Now we draw a sample from that distribution to calculate the mean weight for that sample and plot it into a histogram. We do this process again and again. The resulting histogram generated from this is the mean sampling distribution. Think of the sample mean $\bar{X}$ as a random variable. Depending on which sample we choose it changes, therefore that is variable and randomness comes from the sampling process and the size of the sample. One fact is that this sampling distribution approaches a normal distribution due to the central limit theorem (under certain conditions). Three key facts about the sample mean given the sample size equals $n$:

- The expected value of the sample mean $\bar{X}$ equals the population mean meaning $\mathbb{E}(\bar{X})=\mu_{\bar{X}}=\mu$.

- The variance value of the sample mean $Var(\bar{X})=\frac{\sigma^{2}}{n}$.

- The standard error of the sample mean equals the population standard deviation divided by the square root of the sample size; $se(\bar{X})=\sigma_{\bar{X}}=\frac{\sigma}{\sqrt{n}}$. 

Other two key facts:

- If the original population distribution is normally distributed, then the sampling distribution will also be a normal distribution with sample mean equals $\mu$ and standard error equals $\frac{\sigma}{\sqrt{n}}$ *i.e.* $\bar{X} \sim \mathcal{N}(\mu,\frac{\sigma^{2}}{n})$

- If the original population distribution is not normally distributed, the sampling distribution might approach the normal distribution due to the central limit theorem but the sample size needs to be large enough for the normal approximation to be reasonable. In practice, the sample size needs to be $n\geq30$.

We can standardize the sampling distribution of the sample mean as follows:-

$$

Z= \frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}}

$$

This will result in a standard normal distribution.


#### Sampling Distribution of the Sample Proportion

*References:* [The Sampling Distribution of the Sample Proportion](https://youtu.be/fuGwbG9_W1c)

Here the statistic we are interested in is the <b>proportion</b>.


> The sampling distribution of the sample proportion is closely related with the binomial distribution.
{: .prompt-tip }

Three key facts about the sample proportion given the sample size equals $n$:

- The expected value of the sample proportion $\bar{p}$ (this is sometimes denoted as $\hat{p}$) is equal to the population proportion; that is $\mathbb{E}(\bar{p})=\frac{X}{n}=p$.

- The variance value of the sample proportion $Var(\bar{p})=\frac{p(1-p)}{n}$.

- The standard error of the sample proportion $\bar{p}$ equals $se(\bar{p})=\sqrt{\frac{p(1-p)}{p}}$
 
One other key fact:

 - For any population proportion $p$, the sampling distribution of $\bar{p}$ is approximately normal if the sample size $n$ is sufficiently large enough, As a general guideline $np \geq 5$ and $n(1-p)\geq 5$. However, this guideline is different in different references.

#### Sampling Distribution of the Sample Variance
*References:* [The Sampling Distribution of the Sample Variance
](https://youtu.be/V4Rm4UQHij0), [The Sample Variance and its Chi Squared Distribution
](https://youtu.be/EgA1fqww4B8)

Let's start by defining the sample variance. Mathematically, the sample variance denoted as $s^2$ can be defined as follows:

$$
s^2=\frac{\sum\left(X_i-\bar{X}\right)^2}{n-1}
$$

with sample variance we are trying to get the point estimate of the population parameter which is variance $\sigma^2$.

If we compute this sample variance numerious times and take the expectation of that, in the long learn we are going to get the population variance $\sigma^2$. 


$$
E\left(s^2\right)=\sigma^2
$$


What factors dicate the sampling distribution of the sample variance:

- Which distribution we are sampling from
- The sample size $n$


> Sampling Distribution of the Sample Variance for a normal distribution

Suppose the distribution we are sampling from is normally distributed with a population variance of $\sigma^2$. And we sample $n$ independent samples from the distribution. In that case, the sampling distribution of  <b>modified sample variance </b> (modified by scaling with $\frac{(n-1)}{\sigma^2}$) is given by a chi-square distribution which can be expressed as follows:

$$
\chi^2=\frac{(n-1) s^2}{\sigma^2}
$$


This is chi-square distribution with $n-1$ degrees of freedom. Again to reiterate this is not the exact distribution for the sample variance; rather a scaled version of the sample variance. Sometimes the expression is modified and written as follows to explicitly mention the degrees of freedom:


$$
\chi_{n-1}^2=\frac{(n-1) s^2}{\sigma^2}
$$

For low sample size the distribution is skewed. As the sample size increases the distribution becomes more and more symmetric.



> ### t-Distribution
<hr>

*References:* [Introduction to the t Distribution (non-technical)](https://www.youtube.com/watch?v=Uv6nGIgZMVw), [What is the t-distribution? An extensive guide!](https://www.youtube.com/watch?v=UetYS3PaHIo)

One issue when working with the sampling distribution of the sample mean is for many calculations we are required to know $\sigma$. But $\sigma$ is a population parameter which is most of the time not possible to know. This means we can not calculate the following quantity as $\sigma$ is unknown:

$$

Z= \frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}}

$$

The solution is to use $s$  which is the <b>sample standard deviation</b> instead of $\sigma$. But $s$ is not a constant in contrast to $\sigma$. As a result, the following quantity is no longer a standard normal distribution:

$$
T=\frac{\bar{X}-\mu}{s / \sqrt{n}}
$$

Here, $T$ is a random variable which follows the <b>t-distribution</b>. It is characterized by <b>degrees of freedom</b> where for the above equation the degree of freedom equals $n-1$.


#### Comparison with Normal Distribution
Both t-distribution and standard normal distribution are bell-shaped and symmetric about $0$, but t-distribution has broader tails. The reason is for standard normal distribution we work with population parameters that are constant. This implies less variability. But for t-distribution, we replace $\sigma$ with $s$
 which is a statistic, not a population parameter. This increases the variability of the distribution hence broader tails.


> The fewer the degrees of freedom the broader the tails.
{: .prompt-tip }

> ### Confidence Interval
<hr>

*References:* [Introduction to Confidence Intervals](https://www.youtube.com/watch?v=27iSnzss2wM), [What are confidence intervals? Actually.
](https://www.youtube.com/watch?v=EJe3jiZNwUU)

A confidence interval is a range of values that is constructed around a sample statistic, such as a mean or a proportion, to estimate the true population parameter with a certain level of confidence.


> Sometimes known as interval estimate in contrast to point estimate.
{: .prompt-tip }

For further clarification, another definition is given below:

A confidence interval, or interval estimate, provides a range of values that, with a certain level of confidence, contains the population parameter of interest.


Now one really important thing to keep in mind, the <b>interval estimate or the confidence interval is for the population parameter</b>. We are not trying to get an interval estimate for sample statistics.

The core idea is conveyed by the following equation:


$$
 \boxed{\text{Point Estimate} \ \pm \ \text{Margin of Error}}
$$

#### Confidence Interval for Population Mean $\mu$

*When the population standard deviation is known*

A (1-$\alpha$)$\times 100\%$ confidence interval for $\mu$

$$
\boxed{\bar{X} \pm z_{\alpha / 2} \times \frac{\sigma}{\sqrt{n}}}
$$

where,
 - $\bar{X}$ is the sample mean
 - $\sigma$ is the population standard deviation. In practice, this is rarely known.
 - $n$ sample size
 - $\frac{\sigma}{\sqrt{n}}$ is the standard error of the sampling distribution *i.e.* $se(\bar{X})=\sigma_{\bar{X}}$
 - $z_{\alpha /2}$ is the z-value determined based on the value of $\alpha$ 

 ![CI](https://i.ibb.co/qjPmWKz/chrome-j8-R9-WEb-V5-K.png)
 *Visualization for 95% confidence interval*

For $(1-\alpha)\times 100\%=95\%$ confidence interval the value of $\alpha=5\% =0.05$. Based on this $\frac{\alpha}{2}=0.025$. We can use software or the standard normal table to determine the $z_{\alpha/2}=z_{0.025}$.


*When the population standard deviation is not known*

$$
\boxed{\bar{X} \pm t_{\alpha / 2, d f} \frac{s}{\sqrt{n}}}
$$

where,
 - $\bar{X}$ is the sample mean
 - $s$ is the sample standard deviation. 
 - $n$ sample size

 - $t_{\alpha / 2, d f}$  is the critical value from t-distribution which is dependent on both $\alpha$ and $df$.
 
 - $df$ is the degrees of freedom of the t-distribution which is equal to $n-1$ 


 >### Hypothesis Testing

First let's try to understand what we mean by "Hypothesis". This kind of a general term to refer to a "claim" or a premise. We perform test to check the "Hypothesis" hence the name "hypothesis testing". Now, this might seem ambigious because of how general the definition is. That is an unfortunate consequence of trying to avoid attaching a concept to a specific example. Sometimes the concept seems way too abstract.

**Null hypothesis:** This is denoted as $H_0$. This is the accepted value (for now) for a parameter. Again, we are ambigious about what we mean by a "parameter". Again, the reason is we want it to be general. The parameter can be a mean or a proportion or predicted coefficients of the regression model.....


**Alternative hypothesis:** This is denoted as $H_a$. This the hypothesis that need to be tested.

There are two possible outcomes from hypothesis testing:

- We can reject the null hypothesis.
- Or we can fail to reject the null hypothesis. Note that, we did not prove the "null hypothesis" is actually true.

 A good another analogy for this is "you are innocent until proven guilty". Using that analogy we can say "Null hypothesis is true unless the evidence we get is substantial enough to accept the alternative hypothesis and reject the null hypothesis". Well, we need to define and quantify what we mean by "substantial evidence". 

 **Defining substantial evidence:** We use test statistic (the statistic for the parameter) to get the "evidence". Note that, this is  "statistic" because we will always be working with samples.  Also, this indicate what we mean by "substantial evidence". Because when we work with "statistic" and get a sampling distribution for a parameter, there is always randomness. So, by "substantial evidence" we mean we can say without any doubt the evidence against null hypothesis did not happen because of randomness.  Let's test a concrete example, assume we make a null hypothesis about the weight of people in Wisconsin. The null hypothesis is : The proportion of people that is overweight in Wisconsin is 0.3. And the alternative hypothesis is : The proportion of people that is overweight in Wisconsin is not 0.3. 

$$
H_0: \text{Proportion of overweight people in Wisconsin }=~0.3   
$$

$$
H_a: \text{Proportion of overweight people in Wisconsin is}\neq~0.3   
$$

Well, to get evidence to reject the null hypothesis, we collect a sample and measure the proportion of people that is overweight. Say, that comes out to be $0.32$. Does that mean we should reject the null hypothesis? Obivously not, because that small deviation can happen by random chance. We need some really extreme evidence to reject the null hypothesis.  This is where things become fuzzy and subjective. We need to quantify exactly what evidence would convince us to reject the null hypothesis.


**Quantifying substantial evidence:** 



<!-- >### Sampling Methods


>### Central Limit Theorem

>### Student t-Distribution







>### p-value


>### p-hacking 


## Bayesian Statistics


## Statistical Tests


## Fundamental Concepts 

>### Parameter vs. Statistic

>### Degrees of Freedom -->




# References

[1] Jaggia, S., Kelly, A., Lertwachara, K. and Chen, L., 2021. *Business analytics: Communicating with numbers.* McGraw-Hill Education.