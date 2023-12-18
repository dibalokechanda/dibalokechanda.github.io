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

![contour_plot](https://i.ibb.co/HPyTjLg/chrome-C3m6-Hf1-Jb8.png)

Think of it as the contour lines being projected to the x-y plane. See the below plot as a reference. I removed the original graph and kept only the contour lines. The Contour lines in the 3D surface are colored in green and the projected version in the x-y plane is colored in red.

![projecting_contour_lines](https://i.ibb.co/9cCNy3J/ezgif-com-video-to-gif-converted.gif)

I hope after seeing these visualizing contour plots are more intuitive now.

## Gradient vectors are orthogonal to contour lines

One special thing about contour lines is the gradient vectors of the function $f(x,y)$ i.e. $\nabla f(x,y)$ are always orthogonal to contour lines. This can be easily understood with the hill-climbing analogy. Imagine the surface in our discussion as some terrain we are trying to traverse. 

What happens when we walk along the contour lines?

- Do we climb up?
- Do we climb down?
- Do we stay on the same level? 

The answer is we stay on the same level by definition of contour lines. That means walking along the contour lines has a contribution of "0" if we want to climb the hills as fast as possible.

Now consider these three facts side by side :

- Walking along the contour lines contributes "0" to climbing the hill 
- That means moving in the orthogonal direction contributes "maximum" to climbing the hill. Meaning that you want to climb in that direction which does not have any component in the direction of the contour lines. Because that "component" along the contour line is getting wasted as it contributes "0" to the hill-climbing. Walking orthogonal to contour lines means there is no component whatsoever along the contour lines.

- Gradient vectors show the direction of the steepest ascent.

Voila ! This means gradient vectors are always orthogonal to the contour lines.


## Adding a Constraint Curve


Now if we do not want to find the maximum of the function at any given point, rather in a region we define, the optimization problem turns into a constrained optimization. To start, let us introduce a single constraint curve $g(x,y)$. To keep it simple, we will consider a unit circle center at the origin,

$$
x^2+y^2=1
$$

From the contour plot perspective, it looks like the following:

![Constraint_Contour](https://i.ibb.co/9gwsxK8/chrome-z-Ul5v-WEe5-Z.png)

If we look back a the 3D surface we will get something like the following:

![constraint_3d](https://i.ibb.co/Wfnpwgs/ezgif-com-video-to-gif-converted-1.gif)


If we visualize the portion of the curve under the constraint, we get something like the following:




