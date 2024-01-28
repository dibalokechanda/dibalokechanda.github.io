---
title: R Code Snippets
date: 2024-01-26 12:00:00 -500
categories: [R]
tags: [code_snippets]
math: true
toc: true
---

This article contains codes snippets for "R" programming language. I am fairly new to "R" and documenting the code snippets helps me to understand it better. Just a word of caution, the snippets are not organized neatly.




## Clear Variables

```R
rm(list=ls())
```


## Loading in Libraries 
As an example the ggplot2

## Generating Samples from a probability distribution

### Generating samples from an uniform distribution


```R
# Sample 20 values from a uniform distribution which ranges from -1 to 1
x <- runif(20, min = -1, max = 1)
```