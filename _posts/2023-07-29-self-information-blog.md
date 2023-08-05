---
title: Self Information
date: 2023-07-29 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
---

# Quantifying information

The idea of quantifying information was first introduced by Claude E. Shanon [1] in his historical paper "A Mathematical Theory of Communication". The basic idea was quite simple and formed with first principle thinking. Shanon came with the following formula to quantify information:-

$$
I(x)=-\log p(x)
$$

> $I(x)\geq0$
{: .prompt-info }

where $x$ is the event, $p(x)$ is the probability of the event occurring and $I(x)$ is the information (self-information) quantity of that event. This might seem random but the reason the formula looks like this because it fulfills three key intutions about how information should be quantified.

- If an event has less likely chance of happening, it should contain less information.

- In contrast, if an event has more likely chance of happening it should contain more information.

- Independent events should contain additive information.

The following is a plot of $- \log p(x)$ where $p(x)$ is bounded between 0 and 1.

<iframe src="https://www.desmos.com/calculator/u6v7rqes2e?embed" width="700" height="500" style="border: 1px solid #ccc" frameborder=0></iframe> 

_(Click  and drag across the plot to see how the value changes)_

The x-axis of the plot represents $p(x)$. This means the self-information $I(x)$ and $p(x)$ are exponentially related.

One important detail to point out is that the base of the logarithm. Normally in machine learning natural log is used, but in digital communication theory base-2 log  is used. But changing the base only scales the relation by a constant factor, everything else remains same. The unit for information is **nat**. For base-2 logarithm, the unit is **bit**.

Now to make things concrete consider the two extremes. Suppose, you know a event will occur with 100% certainty which means the probability of that event $x$ occurring is $p(x)=1$. This results in a self-information of $I(x)=0$. On the other extreme, if a event a zero chance of ocurring _i.e._ $p(x)=0$, the self information is $\infty$. This also makes sense, because of a event had no chance of occuring at all, but still happens it theoritcally should have infinite amount of information.

# References

[1] Shannon, C.E., 1948. A mathematical theory of communication. *The Bell system technical journal*, 27(3), pp.379-423.