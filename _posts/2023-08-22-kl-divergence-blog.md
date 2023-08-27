---
title: Kullback–Leibler Divergence
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

which is called the log-likelihood ratio. Now, this is measuring "distance" for only sample $x_{1}$. We need to take into account all the samples $x_{1},x_{2},\cdots$ not just a single sample $x_{1}$. First, we can generalize the likelihood ratio by replacing index $1$ with $i$ and we get the following:


$$
\log \left( \frac{p_{\theta}(x_i)}{q_{\phi}(x_i)} \right)
$$

We can take the weighted average of this "distance measure" for all samples of the random variable $X$. You can think of it like we are averaging all individual log-likelihood ratio values for the random variable $X$. Following this logic, we can write :

$$
\sum_{i=1} p_\theta\left(x_i\right) \log \left[\frac{p_\theta\left(x_i\right)}{q_\phi\left(x_i\right)}\right]
$$

This is the definition of KL divergence. For continuous random variable we can replace $\sum$ with $\int$ to get the following:

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

An example of KL divergence is shown in the diagram below. It is kind of self-explanatory if you know KL divergence is a measure of "distance" between distributions. When two distributions are not similar you should expect a larger value; whereas if the distributions are quite similar you should expect a lower value.

![kl_div](https://i.ibb.co/Fm5rGy5/chrome-zd-NX24h06x.png)

Even though the visualization is shown of one-dimensional distribution it is easily generalizable for higher dimensional distribution.

## Why it is called "Divergence"?

One thing you might have noticed in the previous section I always used " " when using the word "distance". It was intentional because KL divergence is not a true "distance" measure in the sense it is not symmetric. KL divergence between $p_{\theta}$ and $q_{\theta}$ will not be the same as the KL divergence between $q_{\theta}$ and $p_{\theta}$. In addition, it does not satisfy the triangle inequality. The unsymmetric nature can be mathematically expressed as below:

$$
D_{KL}(p||q) \neq D_{KL}(q||p)
$$

Also as it does not follow triangle inequality and hence we can write down the expression below: 

$$
D_{\mathrm{KL}}(p \| q) \nleq D_{\mathrm{KL}}(p \| r)+D_{\mathrm{KL}}(r \| q)
$$

## Forward KL Divergence vs Reverse KL Divergence

There are a couple of consequences due to the asymmetry property of KL divergence. To understand that, first, we need to understand the difference between "Forward KL Divergence" and " Reverse KL divergence". For this, we need to consider a practical setting like variational inference, where we have a target distribution (or true distribution) $p$ and we are trying to approximate a candidate distribution $q$. In this context, the forward KL divergence is given by :

$$
D_{K L}(p \| q)=\mathbb{E}_{x \sim p}\left[\log \frac{p(x)}{q(x)}\right]
$$

And the reverse KL divergence is given  by:

$$
D_{K L}(q \| p)=\mathbb{E}_{x \sim q}\left[\log \frac{q(x)}{p(x)}\right]
$$

Let's try to visualize what is happening by considering the distribution below as the true distribution $p$.

![target_distribution](https://i.ibb.co/CvjcgZn/image-removebg-preview.png)

From the figure, we can see that $p$ is a bi-modal distribution. If we use forward KL divergence as a metric and use variational inference to approximate the parameterized distribution $q$ we will get something like below.  

![forward_kl](https://i.ibb.co/vPv3RKr/image-removebg-preview-1.png)

This shows that the forward KL exhibits mean-seeking behavior. In contrast, if reverse KL divergence is used as a metric it exhibits a mode-seeking behavior as shown in the following diagram. 

![reverse_kl](https://i.ibb.co/pR8YtW3/image-removebg-preview-2.png)

Most people after learning this fact wonder which one is better or which one should be used; the forward KL divergence or the reverse KL divergence? The short answer is it depends. The first thing you need to come to terms with is, for higher dimensional distributions you can't visualize what the hell is happening. Hence, there is no visual intuition to rely on and to decide which one you would want. In higher dimensions, the distribution might have $n$-number of modes and depending on the problem you are trying to solve, you might prefer the forward or the reverse KL divergence.
# Connection to Information Theory

KL Divergence is also known as <b>Relative Entropy</b> and has a close connection to [Mutual Information](https://dibalokechanda.github.io/posts/2023-mutual-information-blog/). Let's start with the equation which connects mutual information to KL divergence:

$$
\boxed{I(X; Y)=D_{K L}\left(p(x,y) \| p(x)  p(y)\right)}
$$

where $p(x) \otimes p(y)$ is the product between the marginal distribution between $p(x)$ and $p(y)$. The derivation of this specific equation is shown below:

$$
\begin{aligned}
I(X ; Y) & =H(Y)-H(Y \mid X) \\
& =-\sum_{y \in \mathcal{Y}} p(y) \log p(y)+\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x) p(y \mid x) \log p(y \mid x) \\
& =\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log p(y \mid x)-\sum_{y \in \mathcal{Y}}\left(\sum_{x \in \mathcal{X}} p(x, y)\right) \log p(y) \\
& =\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log p(y \mid x)-\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log p(y) \\
& =\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log \frac{p(y \mid x)}{p(y)} \\
& =\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log \frac{p(y \mid x) p(x)}{p(y) p(x)} \\
& =\sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log \frac{p(x, y)}{p(y) p(x)} \\
& =D_{K L}(p(x,y) \| p(x) p(y))
\end{aligned}
$$

# Connection to Cross-Entropy



# References

[1] Ghosh, D. (2018). *KL Divergence for Machine Learning*. [online] The RL Probabilist. Available at: [https://dibyaghosh.com/blog/probability/kldivergence.html](https://dibyaghosh.com/blog/probability/kldivergence.html).