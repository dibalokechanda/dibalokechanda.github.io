---
title: R Code Snippets
date: 2024-01-26 12:00:00 -500
categories: [R]
tags: [code_snippets]
math: true
toc: true
---

This article contains code snippets for "R" programming language. I am fairly new to "R" and documenting the code snippets helps me to understand it better. Just a word of caution, the snippets are not organized neatly. This is just for my personal reference to keep track of what concepts I learned in R.

## Clear variables from work space

```R
rm(list=ls())
```

## Clear Plots

```R
dev.off(dev.list()["RStudioGD"]
```

## Basics 

### Installing libraries
```R
install.packages("ggplot2")
```

### Loading in libraries 
As an example, the `ggplot2` library can be loaded as follows:

```R
library(ggplot2)
```

### Printing

```R
# Example of using sprintf() inside print()
x <- 10
print(sprintf("The value of x is %d", x))
```

```R
# Example of using paste() inside print()
name <- "John"
age <- 30
print(paste("Name:", name, ", Age:", age))

```

### Conditionals 

```R
# Example of an else if statement
x <- 10
if (x > 20) {
  print("x is greater than 20")
} else if (x > 10) {
  print("x is greater than 10 but less than or equal to 20")
} else {
  print("x is less than or equal to 10")
}
```

### While loops

```R
# Example of a while loop
i <- 1
while (i <= 5) {
  print(i)
  i <- i + 1
}
```

### For loops
```R
# Example of a for loop
for (i in 1:5) {
  print(i)
}
```

```R
# Looping over elements of a vector
element_vector <- c("a", "b", "c", "d", "e")
for (element in element_vector) {
  print(element)
}
```


### Creating a sequence of numbers given a range 

```R
# To create a sequence from 1 to 10 in steps of 1
sequence <- seq(1, 10, by=1)
print(sequence)
```

Another way to create a sequence is with ``:`` 

```R
# Create a sequence from 1 to 100
i <- 1:100
```

### Creating vectors 

```R
# Creating empty vectors 
empty_vec <- c()

# Creating an empty vector of a specific length and type
empty_vector <- vector("numeric", length = 5)

# Creating a numeric vector
numeric_vector <- c(1, 2, 3, 4, 5)

# Creating a character vector
character_vector <- c("a", "b", "c", "d", "e")

# Creating a logical vector
logical_vector <- c(TRUE, FALSE, TRUE, FALSE, TRUE)
```


### Creating matrices

#### Creating an empty matrix filled with zeros (or any specific values)

```R
mat <- matrix(0,nrow = num_rows, ncol = num_cols)
```

#### Creating matrices by stacking matrices (vertically and horizontally)

```R
col1 <- c(1, 4, 7)
col2 <- c(2, 5, 8)
col3 <- c(3, 6, 9)

mat_cbind <- cbind(col1, col2, col3)
mat_rbind <- rbind(col1, col2, col3)
```

## Generating samples from a probability distribution

### Generating samples from a uniform distribution
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
In ggplot the first argument is the data frame and the second argument inside `aes()` specifies the columns of the data frame that is to be used as the x-axis and y-axis. If the type of plot only involves a single column (for example histogram) we only need to pass in one column as the x-axis. 
```
ggplot(data,aes(x=price))
```

**Specify the type of plot**: Then we add in the geometry to specify the type of plot. We can specify additional parameters as arguments which will control the look of the plot

```R
# Plot a histogram where bindwidth=50 and specify the edge and fill colors
ggplot(data,aes(x=price))+
  geom_histogram(binwidth = 50,col='#9683F5',fill='#D2CDE9')
```

As an example, here we are plotting a histogram with `geom_histogram`. There are way too many parameters to go through. The best approach is to look up the documentation when you need to implement a specific thing.
[https://ggplot2.tidyverse.org/reference/geom_histogram.html](https://ggplot2.tidyverse.org/reference/geom_histogram.html)

### Clean themes

This is kinda subjective and varies from person to person. But I normally use the following code snippets as a theme. This code snippet needs to be varied for different types of plots.

```R
theme_bw()+
  theme(panel.border = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.major.y = element_line(linetype = "dashed",color = "black"),
        panel.grid.minor =element_blank(),
        panel.background = element_blank(),
        axis.line = element_line(color = "white"),
```


### 2D density contour plot with heatmap overlay

```R
m<-ggplot(data, aes(x = HEIGHT, y = WEIGHT)) +
  geom_point()+
  stat_bin2d(bins=80)+
  scale_fill_gradient(low="lightblue", high="red")+

m+geom_density_2d()

```

### Save an image with ggplot

```R
# Saves the last plot as "plot.png" 5x5 image
ggsave("plot.png",width=5,height=5)
```



## Personalized snippets 

### Split continuous numerical variables in different classes

```R
breaks <- c(10, 20, 40, 60, 90,Inf)
labels <- c("10-20", "21-40", "41-60", "61-80","81+")

# Create a new column with age groups
data$age_group <- cut(data$AGE, breaks = breaks, labels = labels, right = FALSE) 
```
In the above example code, there is a continuous age group variable. A new column is created by assigning different edge groups.