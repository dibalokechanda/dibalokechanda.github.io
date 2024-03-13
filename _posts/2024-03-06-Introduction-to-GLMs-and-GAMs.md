---
title: Introduction to GLMs
date: 2024-03-6 12:00:00 -500
categories: [statistics]
tags: [inferential_statistics]
math: true
toc: true
---

In this article, I am going to give a beginner-friendly introduction to generalized linear models (GLMs). As a prerequisite you should have a pretty clear idea about about OLS and the assumptions of OLS. Also, you need to be somewhat familiar to expoential family.

# Generalized Linear Models (GLM) 

This starts with the idea about the ordinary least squares (OLS) and the assumptions we make when we fit an OLS. One of the assumptions is the response variable follows a Gaussian distribution with constant variance. When we are introduced to OLS we come across a figure like the following:

![ols](https://i.ibb.co/5xsFKVV/chrome-j5j-Tu-I7-Ar-N.png)

In this figure, the Gaussian distribution of the response variable is superimposed on the regression line. I think anyone can immediately see the problem if this model is to be applied in a real-world scenario. The response variable is not always going to follow the Gaussian distribution. When it does not follow a Gaussian distribution the OLS is going to fail. Also for OLS to work it need to abide by the homoscedasticity requirement which is often not the case in real-life data. 

How do we adjust for this? Is there a way we can specify the distribution of the response variable before hand and the model will adapt accordingly ?  Generalized linear models does exactly that. A well-known example of GLM is logistic regression where we assume the response variable follows a bernouli distribution.

There are three components related to a generalized linear model.

- <b> Systemic Component: </b> This the component which contains the predictor variables $x_1,x_2,x_3,\cdots,x_n$. This means the systemic component is $\beta_+\beta_1x_1+\beta_2x_2+\cdots+\beta_nx_n$.

- <b> Random Component:</b> This the probability distribution of the response variable. For OLS this is a Gaussian distribution, for binary logistic regression this is a bionomial distribution. As these are related to a distributions, they act as random component in the model. 

- <b> Link Function:</b> It is typically denoted by $\eta$ or $g(\cdot)$. Link function connects the random component and the systemic component. The general formula for link functions is given by the following:

$$
\eta=g(E(Y_i))
$$

This signifies the link function connects the expected value of the response variable to the linear combination of predictor variables. 

- For OLS the link function is just an identity mapping meaning $\eta=g(E(Y_i))=E(Y_i)$. This make sense, because for Gaussian distribution the expected value of the response variable is in the center of the distribution.

- For binary logistic regression, the link function is the logit function. 


One important detail everyone forgets to mention is, the GLM only works if the distribution of the response variable is from exponential family. Exponential family are defined generally in the following form: 

$$
f(y|\theta, \phi) = \exp\left\{\frac{t(y)\theta - b(\theta)}{a(\phi)} + c(y, \phi)\right\}
$$

This can help us give a concise definition of the GLMs.

IN GLMs, the response variable $y_i$ follows a distribution from the exponential family with a expected value of $\mu_i$. This expected value  $\mu_i$ can be modeled as a function of the linear combination of response variables. But this is not necessarily a direct functional mapping rather a mapping after applying the link function.




