---
title: Deep Dive Into Pytorch - Dataset and DataLoaders
date: 2024-06-05 12:00:00 -500
categories: [pytorch]
tags: [pytorch]
math: true
toc: true
---

When I started learning Pytorch, one of the most confusing things to me was the `torch.utils.data.Dataset` and `torch.utils.data.DataLoader`. There were certain rules to define these things and I always wondered what was going on behind the scenes or what would I need to do if I ever had to define a custom variation of them. Later when I learned about `collate_fn`, `Sampler`, `pin_memory` I realized what I was missing. In this article, I want to dig deeper and understand from a fundamental level how these things work. Well, obviously there needs to be some level of abstraction, so when I say fundamental level, take it with a grain of salt.




# What is a Dataset ?

This might be surprising, but depending on your problem definition, it can be literally anything. For example, if you are doing a supervised object classification problem, a single data point in your dataset will contain an image and a label. Same thing if you are working with a tabular dataset and a label. One single data point is just one row in the table. But if you are doing something a little more complicated like working with a graph neural network, instead of an image it will contain a graph and the corresponding label. But to represent a graph you need two pieces of information. One is the feature matrix and the second is the adjacency matrix or edge list. This means now a single data point contains three "entities". The feature matrix, graph connectivity information and label. 

So, it is futile to concretely say what a dataset is. Hence, we need to show it in an abstract format. 

![Viz_dataset](https://i.ibb.co/X7Z4k93/POWERPNT-H7s-OJHWbyk.png)

In the above diagram, I use white blocks to represent a single data point. Mathematically the entire dataset is represented by $\mathcal{D}$ and a single data point is represented by $\mathcal{D}^{(k)}$ where $k$ is the index.

You will notice I used curly braces to contain all the data points. This is to imply it is a set of data points. This implicitly means the order doesn't matter which might not be true for certain cases like working time series or sequence data. But for simplicity, we will ignore those cases and assume the order does not matter.

## Getting an appreciation for the abstraction
Let's see some special cases to appreciate the need for abstraction.

![image_classification](https://i.ibb.co/HNhBby2/POWERPNT-2-Gvl-B9in-Xk.png)

As an example consider the above case which is a supervised object classification problem. One single data point $D^{(k)}$ contains two "entities". The first one is the image (denoted by $x_k$) and the second one is the label (denoted by $y_k$). However, both of them need to go through several transformations to get a tensor representation. These transformations can include normalization, changing the data type, cropping, scaling, etc. For image domain problems, `torchvision` provides several built-in approaches for transformation. In my experience, these are not enough and often you need to write custom transformations.

Let's look at another special case where in addition to object classification, an additional task is object detection. For that, in addition to the classification label you need to provide the ground truth label for the bounding box of the object.

![bound_box](https://i.ibb.co/J5M9VYf/POWERPNT-ui2mcth-Mm-H.png)

In this case, the dataset consists of three entities. The original image $x_k$, the classification label $y_k$, the bounding box label $b_k$ for object detection. 

Another such example is from a graph neural network. In the following example, $x_k$ consists of two parts $f_k$ which is the feature matrix and $e_k$ which is the edge matrix.


![graph_neural_network](https://i.ibb.co/vkCmJL4/POWERPNT-xy-Mb7xrwxz.png)


Based on these examples, it is easy to see the need for abstraction. There are just way too many ways a dataset can be formed. But as long as you follow certain criteria when defining your dataset, it does not matter what your dataset looks like.


# `torch.utils.data.Dataset`

This is an abstract class provided in Pytorch for map-style dataset. This can be used by subclassing it to create a custom dataset wrapper class.

The most basic version is shown below:


```python
from torch.utils.data import Dataset

class CustomDataset(Dataset):
    def __init__(self, data, labels):
        self.data = data
        self.labels = labels

    def __len__(self):
        return len(self.data)

    def __getitem__(self, index):
        x = self.data[index]
        y = self.labels[index]
        return x, y
```

There are three dunder methods you can define. 

- `__init__`: This should take in all the data 'entities' in some form in addition to other optional things you might require. Or you can take in the file path to the dataset as an argument and perform loading and all the other stuff inside the `__init__` method. One common thing is passing in additional information like a `transforms.compose()` object.

- `__len__`: This method should return the length of the dataset. You can just use the `len` function if all your data point is contained in a sequence. The most usual approach I have seen is all the data points are in a list. Or, it is a tabular dataset and just returning `data.shape[0]` does the job. Note that, there are many cases where you might indirectly get the length of your dataset. For example, when you are reading images from a folder you can apply the `len` function on top of `os.listdir` to get the dataset length. You do not need to read all the images and store them in a list. So, it is possible to come up with innovative ways to return the total length of your dataset. But why do we need to define this? The most obvious reason is for the `DataLoader` class to work. When DataLoader performs batching it needs to know the length of the dataset. In addition,  for shuffling or splitting the dataset you need to know the length.

- `__getitem__`: This needs to define the logic for how to access a single data point from the dataset and return the data 'entities'. Again this can customized. I have seen applying transformations before returning the data 'entities'.

How do you apply the transformations? If you are not doing something exotic, Pytorch provides some handy built-in transformations through `torchvision.transforms` for image data. 

## Applying transformations

Look up the official [documentation](https://pytorch.org/vision/main/transforms.html) image transformation for this. There is a plethora of image transformations you can use. Pytorch provides `transforms.Compose()` to chain together multiple transformations. 

A basic version from the Pytorch documentation :

```python
transforms.Compose([
    transforms.CenterCrop(10),
    transforms.PILToTensor(),
    transforms.ConvertImageDtype(torch.float),
])
```

In addition, you can make up your own custom transformation if you need it.




# `torch.utils.data.DataLoader`