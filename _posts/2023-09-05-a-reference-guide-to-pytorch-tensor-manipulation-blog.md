---
title: A Reference Guide to Tensor Manipulation in Pytorch
date: 2023-09-04 12:00:00 -500
categories: [pytorch]
tags: [pytorch,pytorch_basics]
math: true
toc: true
---

Every now and then I will come across a tensor manipulation method in Pytorch and think "I wish I had known about this earlier". Then after one or two days completely forget about that method. This article is a reference for such useful Pytorch tensor manipulation methods.


## `torch.Tensor.new_ones()`

> Creates a new tensor but with all elements initialized to the value 1. By default, the returned Tensor has the same `torch.dtype` and `torch.device` as the original tensor.

```python
tensor = torch.tensor((), dtype=torch.int32)
tensor.new_ones((2, 3))
```