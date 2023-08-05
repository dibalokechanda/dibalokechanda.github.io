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

where $x$ is the event, $p(x)$ is the probability of the event occurring and $I(x)$ is the information (self-information) quantity of that event. This might seem random but the reason the formula looks like this because it fulfills three key intutions about information should be quantified.

# References

[1] Shannon, C.E., 1948. A mathematical theory of communication. *The Bell system technical journal*, 27(3), pp.379-423.