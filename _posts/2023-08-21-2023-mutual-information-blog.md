---
title: Mutual Information
date: 2023-08-21 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

Mutual information is one of the most important concepts in machine learning. It is closely related to concepts like Kullback–Leibler (KL) divergence, cross-entropy etc. This is such a fundamental concept that many novel work in the machine learning domain is based on this.

# The Venn Diagram

If you are familiar with mutual information, you must have come across the following Venn diagram.

![Venn diagram](https://i.ibb.co/cX3n5HJ/chrome-1n-Xw-UGxw-IH.png)


This diagram is used as a reference to explain mutual information. From the diagram, we can see mutual information $I(X; Y)$ is the overlapping region between $H(X)$ and $H(Y)$.  This corresponds with the name <b>mutual information</b> as $H(X)$ is the expected self-information quantity in the random variable $X$ and $H(Y)$ is the expected self-information quantity in the random variable $Y$. Hence, the common section will be the "mutual information" which is shared by both random variables. Just by using common sense, without any prior knowledge, we can write down the following equations with the help of the Venn diagram:

$$
\begin{align*}
I(X;Y)&= H(X)-H(X|Y)\\
      &= H(Y)-H(Y|X) \\
      &= H(X)+H(Y)-H(X,Y)
\end{align*}
$$