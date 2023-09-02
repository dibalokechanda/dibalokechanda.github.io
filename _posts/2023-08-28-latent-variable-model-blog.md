---
title: Latent Variable Model (LVM)
date: 2023-08-28 12:00:00 -500
categories: [fundamentals]
tags: [variational_inference, latent_variables, probablistic_models]
math: true
toc: true
---


Latent variable models defines a distribution over observations $x$ by using a latent variable $z$.
Now there are $5$ separate distributions associated with a LVM.

- $p(x,z)$ : Joint distribution of observation $x$ and latent variable $z$
- $p(z)$ : Prior distribution of latent variable $x$
- $p(x)$ : Marginal distribution of the observations $x$
- $p(x \mid z)$ : likelihood distribution  $x$ given $z$
- $p(z\mid x)$ : posterior  distribution $z$ given $x$

A visualization is shown below:



![LVM](https://i.ibb.co/mFb7gTb/chrome-x-V1u-P8-BZz-Y.png)

We can get the joint distribution $p(x,y)$ if we know prior of the latent variable $p(z)$ and the conditional distribution $p(x \mid z)$.

$$
p(x,z) = p(x \mid z ) p(z) 
$$

To get the posterior distributio we need to do the following. Note that this requires knowing the marginal distribution $p(x)$ by integrating over all possibilities of $z$ and the joint distribution $p(x,z)$.

$$
p(z \mid x)=\frac{p(x,z)}{p(x)}=\frac{p(x, z)}{\int p(x, z) d z} = \frac{p(x\mid z) p(z)}{\int p(x, z) d z}
$$



From this explanation you might think that the goal of latent variable models is to learn the posterior distribution $p(z \mid x)$. That's correct, but there is a sub-goal which is learning the marginal distribution $p(x)= \int p(x, z) d z = \int  p(x\mid z) \ p(z)$.

Why is that it's just an integration right ? Nope, in practice this calculating this term intractable. In high dimensional space, computing this term becomes really really hard.