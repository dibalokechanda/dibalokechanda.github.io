---
title: Entropy 
date: 2023-08-07 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

# Self-Information to Entropy

In a previous post about self-information, I explained how to mathematically formalize the concept of information associated with a specific event. One key thing about self-information is it quantifies the "information quantity" of a single event. But often we deal with distribution rather than just a single event.

To give an example, if we roll a die, with self-information we can quantify how much information is contained in the event that a "5" came up. The probability of that event is $p(x)=\frac{1}{6}$ for a fair die.  We can easily apply the formula $I(x)=-log(x)$  and quantify the self-information. But how do we quantify the "information quantity" in the entire probability distribution associated with a die roll? That is where the concept of **Entropy** comes into play.

I am gonna assume readers are familiar with the concept of "Expectation" in the context of probability theory. If not, I highly encourage you to go through some basic materials for it. A good place to start would be this [video](https://www.youtube.com/watch?v=_yJsO5955ZE).


# Averaging Self-Information

Entropy quantifies the information associated with an entire probability distribution by taking the weighted average of self-information of each event. Mathematically that is represented by the following equation:

$$
H(p)=\mathbb{E}_{X \sim p}[I(x)]=-\mathbb{E}_{X \sim p}[\log p(x)]
$$

The equation follows the definition I mentioned above. We are essentially taking the expectation of self-information over a probability distribution. As per the expectation formula, we can rewrite the equation as follows for discrete distributions *i.e.* for PMFs:

$$
H(p)= - \sum_{x \in \mathcal{X}} p(x) \log p(x)
$$

For continuous cases, the summation turns into integration which is given by the following equation:-

$$
H(p)=-\int_{x \in \mathcal{X}} p(x) \log p(x) d x
$$

Another important thing to note here, these equations can be generalized for high-dimensional distributions.


# What is captured by Entropy

In a nutshell, entropy captures how much uncertainty is associated with a distribution. Now this in turn captures two things: the range of the distribution and the "flatness" of the distribution.

#### Range of distribution

Let's describe it with an example. Suppose you are making a 100$ bet. There are two ways to go. One is to make a bet on the distribution for a fair coin toss. You can choose either head or tail. Another is to make a bet on the distribution for a fair die roll. You can choose one out of six possible outcomes. Just from common sense which one would you choose and why?

The answer is pretty obvious. You are going to choose the coin toss. The reason is the distribution range is lower compared to the range of the distribution for a die roll.

![Probability Mass Function for a coin toss vs a die roll](..\assets\img\entropy_pmf.png)
