---
title: Prerequisites for Convex Optimization 2 
date: 2023-12-20 12:00:00 -500
categories: [fundamentals]
tags: [optimization_theory, convexity]
math: true
toc: true
---

This post is a continuation of my previous post [Prerequisites for Convex Optimization 1](https://dibalokechanda.github.io/posts/Prerequisites-for-Convex-Optimization-blog/). Here, I am going to cover more pre-requisite topics for understanding convex optimization. 


## Convex Combination

Let's start with the convex combination of two points. This is pretty easy to understand because we used this concept to define a convex set and convex function.


Consider the following, which represents the convex combination of two points:

$$
\theta \in[0,1] \quad \theta \mathbf{x}+(1-\theta) \mathbf{y}
$$


A visualization is given below:

![convex_combination](https://i.ibb.co/ZfdcjxK/chrome-he-U3-Oaxx-Xw.png)


This gets tricky when we are dealing with more than two points. First, let's take a look at the formal definition,

A convex combination of points $x_1,x_2,x_3,\cdots$ in a vector space is a linear combination of these points with non-negative coefficients that sum to $1$. Mathematically, 


$$
\theta_1 x_1+\theta_2 x_2+\ldots+\theta_k x_k
$$


$$
\theta_i \geq 0
$$


$$
\sum_{i=1}^k \theta_i=1
$$


![convex_comb](https://i.ibb.co/2PXZnhM/chrome-z-QW4e-Lv-CIK.png)


In my head, I visualize it as I am tuning knobs for $\theta_1,\theta_2,\theta_3, \cdots$ given a set of points $x_1,x_2,x_3\cdots$ and kind of filling in the area.


 In a convex set, any convex combination of points in the set remains within the set.


![comb_1](https://i.ibb.co/yRxy6wk/chrome-m4-N96-Mo-UYs.png)


## Affine Combination 


$$
\theta \mathbf{x}+(1-\theta) \mathbf{y}, \quad \theta \in \mathbb{R} 
$$

One important thing to notice here is the contrast with the convex combination. For the convex combination, we had restrictions for $\theta$. But for affine combination, there is no such restriction. This means $\theta$ does not have to be between $0$ and $1$, it just has to be in $\mathbb{R}$.


![affine_set](https://i.ibb.co/88gktvF/chrome-Jw5f-C5-QZjm.png)

## Affine Set
Contains the line through any two distinct points in the set. Think of it this way, you are given a set in $\mathbb{R}^n$, you pick two points from that set and draw a line that goes through those two points. Now all possible points on that line should be contained in that set. If that's the case, then the set is affine.


 One important thing to remember is every convex set is also affine, but not every affine set is convex. Convexity is a stronger condition than affineness.


## Affine Hull  and Convex Hull

The definition of an affine hull:

$$
\operatorname{aff}(S)=\left\{\sum_{i=1}^k \theta_i x_i \mid x_i \in S, \sum_{i=1}^k \theta_i=1, \theta_i \in \mathbb{R}\right\}
$$



The definition of a convex hull:


$$
\operatorname{conv}(S)=\left\{\sum_{i=1}^k \theta_i x_i \mid x_i \in S, \sum_{i=1}^k \theta_i=1, \theta_i \geq 0\right\}
$$


These seem useless because they are kind of redefining the convex set and affine set. Well, convex hull and affine hull are themselves respectively convex and affine sets by definition. These become useful when you are given a set of points without structure and you want to form a convex set and affine set. The way you form those convex sets and affine sets is by creating the convex hull and affine hull from those set of given points.


## Hyperplanes 



## Half Spaces 




## Supporting Hyperplane Theorem




## Separating Hyperplane Theorem