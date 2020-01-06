title: deep_ctr
author: nullfan
date: 2019-10-22 14:56:56
tags:
---
## 传统方法
### FTRL  
https://blog.csdn.net/china1000/article/details/51176654 
https://liam.page/2019/08/31/a-not-so-simple-introduction-to-FTRL/
![upload successful](/images/pasted-49.png)df

### FM
𝑦(𝑥):=𝑏𝑖𝑎𝑠+Σ𝑖(𝑤𝑖∗𝑥𝑖)+Σ𝑖Σ𝑗<𝑣𝑖,𝑣𝑗>∗𝑥𝑖∗𝑥𝑗 
 
好处：  
* 可以刻画交互信息  
* 可以处理非常稀疏和大规模的数据


### FFM
𝑦(𝑥):=𝑏𝑖𝑎𝑠+Σ𝑖(𝑤𝑖∗𝑥𝑖)+Σ𝑖Σ𝑗<𝑉𝑖[𝑛],𝑉𝑗[𝑚]>∗𝑥(𝑚)𝑖∗𝑥(𝑛)𝑗  
把所有的向量都映射到不同的领域，每个领域有各自特有的向量  
好处: 
* 在计算交互特征的时候可以损失更少的信息
### GBDT + LR
考虑在fm中，将所有的特征都做交叉组合，但实际上，并不是所有的交叉组合的特征都有效的，需要对这些交叉组合的特征做一定的筛选  
gbdt的叶子节点可以看作是一系列规则的组合，通过把叶子节点对应的索引做特征的方式，可以有效学习到筛选的组合特征

## Deep系列

* 参考文献
* https://deepctr.readthedocs.io/en/latest/

###### wide & deep   

###### deepfm   

###### dcn   

* https://blog.csdn.net/Dby_freedom/article/details/86502623

##### xddepfm  
https://github.com/shenweichen/Bytedance_ICME2019_challenge_baseline
https://github.com/Leavingseason/xDeepFM/tree/master/exdeepfm

##### DIN
#### TDM
###### tdm中文论文： http://d0evi1.com/tdm/