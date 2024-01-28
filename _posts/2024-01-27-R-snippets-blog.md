---
title: R Code Snippets
date: 2024-01-26 12:00:00 -500
categories: [R]
tags: [code_snippets]
math: true
toc: true
---

This article contains codes snippets for "R" programming language. I am fairly new to "R" and documenting the code snippets helps me to understand it better. Just a word of caution, the snippets are not organized neatly. This just for my personal reference to keep track of what concepts I learned in R. 




## Clear variables from workspace

```R
rm(list=ls())
```

## Basics 

## Installing libraries
```R
install.packages("ggplot2")
```

## Loading in libraries 
As an example the `ggplot2` library can be loaded as follows:

```R
library(ggplot2)
```


### Creating a sequence of numbers given a range 

```R
# To create a sequence from 1 to 10 in steps of 1
sequence <- seq(1, 10, by=1)
print(sequence)
```


## Generating samples from a probability distribution

### Generating samples from an uniform distribution
_Reference_: [https://www.rdocumentation.org/packages/stats/versions/3.6.2/topics/Uniform](https://www.rdocumentation.org/packages/stats/versions/3.6.2/topics/Uniform)


```R
# Sample 20 values from a uniform distribution which ranges from -1 to 1
x <- runif(20, min = -1, max = 1)
```

### Generating samples from a normal distribution 

_Reference_: [https://www.rdocumentation.org/packages/stats/versions/3.6.2/topics/Normal](https://www.rdocumentation.org/packages/stats/versions/3.6.2/topics/Normal)

```R
# Sample 100 sample from normal distribution with a specified mean and standard deviation
x <- rnorm(n=100,mean=68.5,sd=5.7)
```

## Operations on dataframe

### Getting a summary for the dataframe

```R
summary(data)
```

## ggplot commands


### Basic ggplot  plot

**Specifiy the data**:
In ggplot the first argument is the dataframe and the second argument inside `aes()` specify the columns of the dataframe that is to be used as the x-axis and y-axis. If the type of plot only involves a single column (for example histogram) we only need to pass in one column as x-axis. 
```
ggplot(data,aes(x=price))
```

**Specify the type of plot**: Then we add in the geometry to specify the type of plot. We can specify additional parameter as argument which will control the look of the plot

```R
# Plot a histogram where bindwidth=50 and specify the edge and fill colors
ggplot(data,aes(x=price))+
  geom_histogram(binwidth = 50,col='#9683F5',fill='#D2CDE9')
```

As an example, here we are plotting a histogram with `geom_histogram`. There are way too many parameters to go through. The best approach is to look up the documentation when you need to implement a specific thing.
[https://ggplot2.tidyverse.org/reference/geom_histogram.html](https://ggplot2.tidyverse.org/reference/geom_histogram.html)

### Clean themes

This is kinda subjective and varies from person to person. But I normally use the followning code snippets as a theme.

```R
theme_bw()+
  theme(panel.border = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.major.y = element_line(linetype = "dashed",color = "black"),
        panel.grid.minor =element_blank(),
        panel.background = element_blank(),
        axis.line = element_line(color = "white"),
```


### Save an image with ggplot

```R
# Saves the last plot as "plot.png" 5x5 image
ggsave("plot.png",width=5,height=5)
```