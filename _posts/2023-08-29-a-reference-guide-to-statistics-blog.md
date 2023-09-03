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

*References:* [Sampling Distributions (7.2)](https://www.youtube.com/watch?v=7S7j75d3GM4)

 - A <b>Sample</b> is a small portion of the population that we examine and draw conclusions from.

 - The <b>process</b> of drawing a sample from the population is known as sampling. 


#### Sample Distribution

When we draw a particular sample from a distribution, that specific sample creates a distribution. This is known as the "sample distribution".

#### Sampling Distribution

The sampling distribution of a <b>statistic</b> is the probability distribution of that <b>statistic</b>. This means if we draw samples from the <b>population</b> a bunch of times, the distribution associated with a particular <b>statistic</b> is referred to as the <b>sampling</b> distribution. 

#### Sampling Distribution of the Sample Mean

*References:* [Sampling Distributions (7.2)](https://www.youtube.com/watch?v=7S7j75d3GM4), [The Sampling Distribution of the Sample Mean](https://www.youtube.com/watch?v=q50GpTdFYyI) 

For example, let's use "mean" as the statistic. In that case, given a population (say all people in Wisconsin) and a random variable (say weight) we have a "true" population distribution of people's weights. Now we draw a sample from that distribution to calculate the mean weight for that sample and plot it into a histogram. We do this process again and again. The resulting histogram generated from this is the mean sampling distribution. Think of the sample mean $\bar{X}$ as a random variable. Depending on which sample we choose it changes, therefore that is variable and randomness comes from the sampling process and the size of the sample. One fact is that this sampling distribution approaches a normal distribution due to the central limit theorem (under certain conditions). Three key facts about the sample mean given the sample size equals $n$:

- The expected value of the sample mean $\bar{X}$ equals the population mean meaning $\mathbb{E}(\bar{X})=\mu_{\bar{X}}=\mu$.

- The variance value of the sample mean $Var(\bar{X})=\frac{\sigma^{2}}{n}$.

- The standard error of the sample mean equals the population standard deviation divided by the square root of the sample size; $se(\bar{X})=\sigma_{\bar{X}}=\frac{\sigma}{\sqrt{n}}$. 

Other two key facts:

- If the original population distribution is normally distributed, then the sampling distribution will also be a normal distribution with sample mean equals $\mu$ and standard error equals $\frac{\sigma}{\sqrt{n}}$ *i.e.* $\bar{X} \sim \mathcal{N}(\mu,\frac{\sigma^{2}}{n})$

- If the original population distribution is not normally distributed, the sampling distribution might approach the normal distribution due to the central limit theorem. The condition is the sample size $n\geq30$.

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

- The expected value of the sample proportion $\bar{P}$ (this is sometimes denoted as $\hat{P}$) is equal to the population proportion; that is $\mathbb{E}(\bar{P})=\frac{X}{n}=P$.

- The variance value of the sample proportion $Var(\bar{P})=\frac{P(1-P)}{n}$.

- The standard error of the sample proportion $\bar{P}$ equals $se(\bar{P})=\sqrt{\frac{P(1-P)}{P}}$
 
<!-- >### Sampling Methods


>### Confidence Interval 


>### Central Limit Theorem

>### Student t-Distribution




>### Hypothesis Testing


>### p-value


>### p-hacking 


## Bayesian Statistics


## Statistical Tests


## Fundamental Concepts 

>### Parameter vs. Statistic

>### Degrees of Freedom -->




# References

[1] Jaggia, S., Kelly, A., Lertwachara, K. and Chen, L., 2021. *Business analytics: Communicating with numbers.* McGraw-Hill Education.