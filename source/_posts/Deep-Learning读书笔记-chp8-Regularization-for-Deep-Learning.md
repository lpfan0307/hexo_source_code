title: ' Deep Learning读书笔记 chp8-Regularization for Deep Learning'
author: nullfan
date: 2020-02-24 00:13:20
tags:
---
# mini-batch 
$n$个样本的均值的标准差为$\sigma / \sqrt{n }$，分母的$\sqrt n$表明样本的均值的标准差的下降程度小于线性。考虑到100个样本和10000个样本，后者计算程度是前者的100倍，但准确程度却仅是10倍。从总体计算复杂度来说，使用mini-batch是收敛更快的方式。  

# Nesterov Momentum
在计算梯度时，将$\theta$加上累计的梯度方向，在凸函数全局梯度下，可以将下降速度从$O(1/k)$变为$O(1/k^2)$  
![upload successful](/images/pasted-69.png)

# Batch Nomalization