---
title: Prerequisites for Convex Optimization 2 
date: 2023-12-20 12:00:00 -500
categories: [fundamentals]
tags: [optimization_theory, convexity]
math: true
toc: true
---

This post is a continuation of my previous post [Prerequisites for Convex Optimization](https://dibalokechanda.github.io/posts/Prerequisites-for-Convex-Optimization-blog/). Here, I am going to cover more pre-requisite topics for understanding convex optimization. 


## Convex Combination

Let's start with the convex combination of two points. This is pretty easy to understand because we used this concept to define a convex set and convex function.


Consider the following, which represents the convex combination of two points:

$$
\theta \in[0,1] \quad \theta \mathbf{x}+(1-\theta) \mathbf{y}
$$


A visualization is given below:

![convex_combination](https://i.ibb.co/ZfdcjxK/chrome-he-U3-Oaxx-Xw.png)


This gets tricky when we are dealing with more than two points. First, let's take a look at the formal definition,

A convex combination of points $x_1,x_2,x_3,\cdots$ in a vector space is a linear combination of these points with non-negative coefficients that sum to $1$.


$$
\theta_1 x_1+\theta_2 x_2+\ldots+\theta_k x_k
$$


$$
\theta_i \geq 0
$$


$$
\sum_{i=1}^k \theta_i=1
$$


## Affine Combination 


$$
\theta \mathbf{x}+(1-\theta) \mathbf{y}, \quad \theta \in \mathbb{R} 
$$


## Affine Set
Contains the line through any two distinct points in the set


 One important thing to remember is every convex set is also affine, but not every affine set is convex. Convexity is a stronger condition than affineness.


## Hyperplanes 



## Half Spaces 




## Supporting Hyperplane Theorem




## Separating Hyperplane Theorem