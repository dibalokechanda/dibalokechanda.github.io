---
title: Lagrange Multipliers
date: 2023-12-16 12:00:00 -500
categories: [fundamentals]
tags: [multivariate_calculus,optimization_theory]
math: true
toc: true
---

Lagrange multipliers is a general concept in optimization theory that is applicable to any high dimensional surface. The drawback with such generalization is we can not visualize more than 3 dimensions. But it is possible to have some intuitions in the low-dimensional space and those intuitions do carry over to higher dimensions.


To fully appreciate Lagrange multipliers, some pre-requisite concepts must be understood. 

## Contour Lines 

Consider the following function which is given by the equation



$$
f(x,y)=\frac{7xy}{e^{x^2+y^2}}
$$

A 3D visualization of the function is shown below:


![3d_plot](https://i.ibb.co/tcDSnYr/ezgif-com-optimize.gif)

We can draw contour lines in the 3D surface of the plot which is shown below:

![contour_lines](https://i.ibb.co/sJ2CBHD/chrome-TSTm-FGEW6h.png)

A better way to see these contour lines is a contour plot generated from the top-down perspective as shown below:

![](https://i.ibb.co/HPyTjLg/chrome-C3m6-Hf1-Jb8.png)

Think of it as the contour lines are being projected to the x-y plane.

## Gradients being orthogonal to contour lines