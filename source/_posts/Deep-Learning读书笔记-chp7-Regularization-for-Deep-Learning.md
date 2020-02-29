title: Deep Learning读书笔记 chp7-Regularization for Deep Learning
author: nullfan
date: 2020-02-23 23:20:12
tags:
---
# 正则化的几种方式  
## 惩罚项和约束项  
借助广义拉格朗日算法，惩罚项和约束项在一定程度上可以看做是等价的。  
## 数据增广（data augmentation）
数据增光对于一些特定的问题可以取得很好的效果，例如在物体识别中，将图片的每个像素沿着某个方向旋转，将新获得的图片加入训练集，通常可以获得很好的效果，即便是在使用的卷积这样对旋转不变的操作后。
## 噪声鲁棒性（noise robustnesss）
一般来说，噪声的引入比单纯的对参数的shrinking要重要，特别是这些噪声是加在隐层单元上时。
## multi-task learning
多任务学习模型的架构：
屏幕快照 2020-02-23 下午11.37.16
![upload successful](/images/pasted-66.png)  
多任务学习中，一个模型的参数会由两个部分组成（1）模型特有的参数（2）几个模型通用的参数。可以使用多任务学习的一个前提是不同的任务之间存在某些统计学上的关系。
## early stopping
## bagging and other ensemble methods  
将几组模型平均通常比单个模型取得更好的效果，这背后的原因是因为不同的模型通常不会犯相同的错误。  

![upload successful](/images/pasted-68.png)  

## dropout   
dropout和bagging的关联：（1）bagging的各个模型的参数是独立的，但dropout的各个模型的参数是从母shenjingwangluo继承的不同子集，（2）bagging的每个模型都可以被充分训练，而dropout的模型数太多以至于让每个模型充分训练是不太现实的，但各个模型之间的参数共享可以使得各个模型都取得一个不错的结果。（3）除此之外，bagging和dropout是一样的。  
dropout有的优点：
* 计算更加轻便  
* 对神经网络的结构没有要求，通用性很广  
dropout取得很好的结果，很大一部分是来自于给隐层节点的噪声。例如，如果需要识别一个人脸，一个隐藏节点通过鼻子学到该脸部的信息，当这个节点被随机丢弃时，就迫使神经网络去学习其他如嘴巴、耳朵等信息。而传统的噪声引入很难做到将一个鼻子或者嘴巴丢掉这样。