---
title: Mutual Information
date: 2023-08-16 12:00:00 -500
categories: [fundamentals]
tags: [entropy, information_theory]
math: true
toc: true
---

To understand the concept of mutual information first, we need to understand joint entropy and conditional entropy.

![image_3_blue_1_brown](https://i.ibb.co/vwVcyC8/chrome-b-WRWGz5-VBh.png)
 (*Image taken from [3Blue1Brown](https://www.youtube.com/@3blue1brown) video-[Solving Wordle using information theory](https://youtu.be/v68zYyaEmEA?t=708)*)



# Joint Entropy

Joint Entropy is nothing but the entropy of a joint distribution. The joint distribution can be constructed with multiple random variables. But to keep it simple, let's consider a joint distribution of two random variables $X$ and $Y$. In addition, let's keep the discussion limited to discrete random variables as that is easier to visualize and reason with. The joint entropy $H(X,Y)$ is given by the following equation:

$$
H(X, Y) = -\sum_{x \in X} \sum_{y \in Y} p(x, y) \log p(x, y)
$$

Sometimes the double summation is replaced by a single summation and written as follows:-

$$
H(X, Y) = -\sum_{x \in X, \ y \in Y} p(x, y) \log p(x, y)
$$

Now this equation essentially takes in a joint probability distribution $p(x,y)$ and spits out a single number that represents the expected information quantity in that joint distribution. Let's start with a simple example, a joint distribution of a fair coin toss and a fair die roll. The assumption that needs to be made here the coin toss and die roll are independent of each other. The visualization of the distribution is shown below:

![joint_pmf](https://i.ibb.co/C5ZV4Mf/chrome-a-MM4-Ni3hk-N.png)

We can easily tell as the distribution is completely flat, which means it has a high joint entropy. We can compute it as follows (with $\log-e$ base) :

$$
 H(X,Y)= - 12 \times \frac{1}{12} \times log(\frac{1}{12})=2.485
$$

Now suppose we change the flatness of the distribution