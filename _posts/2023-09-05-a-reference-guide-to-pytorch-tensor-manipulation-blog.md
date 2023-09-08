---
title: A Reference Guide to Pytorch Tips and Tricks
date: 2023-09-04 12:00:00 -500
categories: [pytorch]
tags: [pytorch,pytorch_basics]
math: true
toc: true
---

Every now and then I will come across a tensor manipulation method in Pytorch or some piece of code in Pytorch and think "I wish I had known about this earlier". Then after one or two days completely forget about that thing. This article is a reference for such useful Pytorch code snipptets.

## Code organization 

### Separate Trainer class to train model 

I usually write the training portion of the code in `main.py` file. But a much better approach is to have a separate trainer class to train the model. You can have additional functions like  `store_values` to store different metrices  and outputs (for example embeddings) from the model. You can also provide an additional variable like `train_log=['True',20]` which will decide if you should log the training metrics and how frequent the training logs should be. For some model training it does not make sense to log metrices after every epoch. Finally, you can return the trained model in the `train` function.


```python
class Trainer():
    def __init__(self,model,data,optimizer,num_epochs,train_log=['True',20]): 
        self.model=model 
        self.data=data
        self.optimizer=optimizer
        self.num_epochs=num_epochs
        self.train_log=train_log
        
        self.losses = []
        self.accuracies = []
        self.outputs = []


    def accuracy(self,pred_y, y):
        return ((pred_y == y).sum() / len(y)).item()
    
    def store_values(self,loss,acc,out):
        self.losses.append(loss)
        self.accuracies.append(acc)
        self.outputs.append(out)
        

    def train(self):
        if self.train_log[0]:
            
            print('Training Info:')
            print('-------------')
            
        for epoch in range(self.num_epochs):
            self.model.train()
            self.optimizer.zero_grad()
            out = self.model(self.data.x,self.data.edge_index)
            loss = F.nll_loss(out[self.data.train_mask], self.data.y[self.data.train_mask])
            acc = self.accuracy(out[self.data.train_mask].argmax(dim=1), self.data.y[self.data.train_mask])
                
            self.store_values(loss,acc,out)
                       
            if self.train_log[0]:
                if epoch % self.train_log[1] == 0:
                    print(f'Epoch: {epoch}   | Training Loss: {loss} | Training Accuracy : {acc} ')
            
            loss.backward()
            self.optimizer.step()
            
        return self.model

```


## Tensor Manipulation Methods
### `torch.Tensor.new_ones()`

> Creates a new tensor but with all elements initialized to the value 1. By default, the returned Tensor has the same `torch.dtype` and `torch.device` as the original tensor.

```python
tensor = torch.tensor((), dtype=torch.int32)
tensor.new_ones((2, 3))
```

### `torch.unbind()`

> Removes a tensor dimension. Returns a tuple of all slices along a given dimension, already without it.

```python

torch.unbind(torch.tensor([ [1, 2, 3],
                            [4, 5, 6],
                            [7, 8, 9]]))
```

```
(tensor([1, 2, 3]), tensor([4, 5, 6]), tensor([7, 8, 9]))
```

### `torch.Tensor.tolist()`

> Returns the tensor as a (nested) list.

```python
a = torch.randn(2, 2)
a.tolist()
```

```
[[0.012766935862600803, 0.5415473580360413],
 [-0.08909505605697632, 0.7729271650314331]]
```