---
title: Entropy : The fundamentals
date: 2023-08-08 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

# Self-Information to Entropy

In a previous post about self-information, I explained how to mathematically formalize the concept of information associated with a specific event. One key thing about self-information is it quantifies the "information quantity" of a single event. But often we deal with distribution rather than just a single event.

To give an example, if we roll a die, with self-information we can quantify how much information is contained that a "5" came up. The probability of that event is $p(x)=\frac{1}{6}$ for a fair die.  We can easily apply the formula $I(x)=-log(x)$  and quantify the self-information. But how do we quantify the "information quantity" in the entire probability distribution associated with a die roll? That is where the concept of **Entropy** comes into play.

I am gonna assume readers are familiar with the concept of "Expectation" in the context of probability theory. If not, I highly encourage you to go through some basic materials for it. A good place to start would be this video.


# Averaging Self-Information

Entropy quantifies the information associated with an entire probability distribution.