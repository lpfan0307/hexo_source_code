title: ' Deep Learning读书笔记 chp11 & chp12'
author: nullfan
date: 2020-02-28 23:43:17
tags:
---
# practical design process  
## determine your goals  
```
performance metric 和 cost function
```
通常情况下，performance metric和cost function是不相同的，通常使用准确率、错误率等来衡量一个系统，而使用log loss等来作为cost function  
## establish a working end-to-end pipeline as soon as possible 
通常使用SGD（with momentum，with a deaying learning rate）来作为baseline  

## instrument the system well to determine bottlenecks in performance  
    
## repeatly make incremental changes  
### 是否需要获取更多数据  
虽然可以采用不同的算法来提升系统，但获取更多的数据经常是一个更好的做法，可以通过画出training set size和generation error的方式来看出是否需要更多的训练数据  
### 参数调整  
学习率几乎是最终要的参数，如果只能够调整一个参数，那么就调整学习率  
其他参数的调整需要通过观察训练误差和泛化误差来做出结论  
如果训练集误差比泛化误差大，则模型是under fitting，需要增加模型的复杂度；如果训练集误差比泛化误差小，通常可以在正则项做一些文章。  
### grid search VS random search  

![upload successful](/images/pasted-79.png)  
一个模型通常只对几个特定的参数敏感，例如图中该模型只对横坐标的值敏感，使用grid search会重复多次相同横坐标的值而浪费计算资源。使用random search可以取得更好的效果，random search的一个例子如下：
log_learning_rate ~ $u(-1, -5)$  
learning_rate = $10^{log_learning_rate}$  
### debugging strategies  
* visualize the model in action，例如可以观察模型中隐藏节点的激活比例等等    
* visual the worst mistakes，这个是个很好的想法，通常看模型最不确定的正样本可以获取不少的insight，不论是模型的学习效果还是特征的补充  
### 不同年份都区分开的语言模型  
![upload successful](/images/pasted-81.png)  
## High-Dimensional Outputs  
在自然语言处理中，通常会遇到输出维度很多的情况。为了减轻计算的复杂度，通常有下面的做法  
* use of a short list，将输出限制在最常见的word(10000~20000)中  
* hierachical softmax，这个存在的一个问题是如果数中的类不是很准确，得到的结果可能会很差  
