---
title: Latent Variables
date: 2023-08-26 12:00:00 -500
categories: [fundamentals]
tags: [variational_inference, latent_variables, probablistic_models]
math: true
toc: true
---

![latent](/assets/img/Latent_Variables/lv1.png)
 *Image taken from [MIT Introduction to Deep Learning 6.S191: Lecture 4](https://youtu.be/3G5hWM6jqPk?t=479)*


## What are Latent Variables ?

In simplest term, the variables to which we have no access to or in other words "unobserved" variables. This implies, we don't have access to the probability distribution of that variable. This in turn mean, we don't have access to mean, mode, variance and other stuffs for that variable.

Well, how do we work with it then ? From a deep learning perspective, we use the available observed variables/data to train a model and get an approximation to the latent variables (at least for some of the models). The usual notation for expressing a latent variable is $z$ and its distribution as $p(z)$. There are many models that involves latent variables. Just to name a few the following three model are different ways to generate approximation to the latent variables.


- <b> Autoencoder </b> : latent variables are the hidden representations of the input data.
- <b>Variational Autoencoder (VAE) </b> : latent variables are the parameters of the latent distribution.
- <b> Generative Adversarial Network (GAN)</b> : latent variables are the parameters of the generator network. 

## Latent Distribution 

In some cases, the latent variables are assumed to be probabilistic rather than deterministic. In those cases, the latent variable is associated with a probability distribution. For example in variational autoencoder we assume the data generation distribution is a latent distribution. The mean and the variance of that distribution are the variables that we want to learn during training.

## Latent Space

This is normally associated with a space (most of the time a vector space) where the latent variables live. In most literature, it is a comparetively lower dimensional space compared to the dimension of the original data.

## Latent Representation

This is yet another terminology to refer to latent variables. For example, we say we want to learn the "latent representation of this Image X". This means we want to project the original image to a low-dimensional latent space. That projected version of the image is referred to as the latent representation.