---
title: Self Information
date: 2023-07-29 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

# Quantifying information

The idea of quantifying information was first introduced by Claude E. Shanon [[1]](https://dl.acm.org/doi/pdf/10.1145/584091.584093) in his historical paper "A Mathematical Theory of Communication". The basic idea was quite simple and formed with first principle thinking. Shanon came up with the following formula to quantify information:

$$
\boxed{I(x)=-\log p(x)}
$$

> Information is a non-negative quantity _i.e._ $I(x)\geq0$
{: .prompt-tip }

where $x$ is the event, $p(x)$ is the probability of the event occurring and $I(x)$ is the information (self-information) quantity of that event. This might seem random but the reason the formula looks like this is because it fulfills three key intuitions about how information should be quantified.

- If an event has a less likely chance of happening, it should contain less information.

- In contrast, if an event has a more likely chance of happening it should contain more information.

- Independent events should contain additive information.

The following is a plot of $- \log p(x)$ where $p(x)$ is bounded between 0 and 1.

<iframe src="https://www.desmos.com/calculator/tf0y2jw8ra?embed" width="700" height="700" style="border: 1px solid #ccc" frameborder=0></iframe>

_(Click  and drag across the plot to see how the value changes)_

The x-axis of the plot represents $p(x)$. This means the self-information $I(x)$ and $p(x)$ are exponentially related.

One important detail to point out is the base of the logarithm. Normally in machine learning natural log is used, but in digital communication theory, a base-2 log is used. But changing the base only scales the relation by a constant factor, everything else remains the same. The unit for information with base-$e$ is **nats**. For base-2 logarithm, the unit is **bits**.

Now to make things concrete consider the two extremes. Suppose, you know an event will occur with 100% certainty which means the probability of that event $x$ occurring is $p(x)=1$. This results in a self-information of $I(x)=0$. On the other extreme, if an event has zero chance of occurring _i.e._ $p(x)=0$, the self-information is $\infty$. This also makes sense, because if an event had no chance of occurring at all, but still happens it theoretically should have an infinite amount of information.

Another thing is the additivity property in case of independent event can be represented as follows (for two events) :

$$
\begin{align*}
 I(x_{1})+I(x_{2}) &=-\log(p(x_{1})p(x_{2}))\\
 &= -\log p(x_{1}) -\log p(x_{2})
\end{align*}
$$

For $n$ number of events, this can be generalized as follows:

$$
 \sum_{i=1}^{n}I(x_{i})=-\log(\prod_{i=1}^{n}p(x_{i}))
$$

# References

[1] Shannon, C.E., 1948. A mathematical theory of communication. *The Bell system technical journal*, 27(3), pp.379-423.