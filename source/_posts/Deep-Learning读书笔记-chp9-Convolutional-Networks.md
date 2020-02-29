title: ' Deep Learning读书笔记 chp9-Convolutional Networks'
author: nullfan
date: 2020-02-24 10:34:30
tags:
---
# the  motivation  
* sparse interactions  
例如对于一张图片，有成百甚至上千个像素，但是对于发现一些边缘的基础特征通常只需要很少的像素，即卷积核不需要太大。另外，对于一个输入维度为$n$，输出维度为$m$的场景，通过卷积可以限制与输出连接维度为$k$。在实际应用场景中，通常$k$取比$m$小很多的值就可以达到不错的效果
* parameter sharing  
对于一张图片，使用卷积的方式我们通常不需要对每个局部区域学习不同的参数，而可以对这些局部学习一组共同的参数，这也可以减少需要存储的参数。
* equivariant representations  
对于图片的平移或者时序信息，使用卷积可以获得相同的输出。  

# pooling  
pooling操作是将网络的局部信息使用某些统计量来代替的方式。使用一些pooling操作后，对于输入的一些微小变动，几乎都可以保持不变的结果。在我们关注某些特生是否出现，在不在乎出现在什么的时候，pooling操作具有很好的作用。pool操作加入了一个很强的先验偏置：使用了pool层的必须对微小的变化保持不变。