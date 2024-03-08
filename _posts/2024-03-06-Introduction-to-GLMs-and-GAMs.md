---
title: Introduction to GLMs and GAMs
date: 2024-03-6 12:00:00 -500
categories: [statistics]
tags: [inferential_statistics]
math: true
toc: true
---

In this article, I am going to give a beginner-friendly introduction to generalized linear models (GLMs) and generalized additive models (GAMs).

# Generalized Linear Models (GLM) 

This starts with the idea about the ordinary least squares (OLS) and the assumptions we make when we fit an OLS. One of the assumptions is the response variable follows a Gaussian distribution with constant variance. When we are introduced to OLS we come across a figure like the following:

![ols](https://i.ibb.co/5xsFKVV/chrome-j5j-Tu-I7-Ar-N.png)

I think anyone can immediately see the problem if this model is to be applied in a real-world scenario. The issue is we make the assumption about the response variable $y$. 