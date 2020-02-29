title: Deep Learning读书笔记 chp3-Probability and Information Theory
author: nullfan
date: 2020-02-03 21:47:33
tags:
---
# 概率存在的三个主要因素
* 系统内在的随机性；如量子力学或者扑克牌  
* 观察不完备
* 建模不完备  

很多时候，使用一个简单的不确定性的例子，通常比使用一个确定性的但复杂很多的例子更有意义，例如：“大多数鸟会飞” VS "鸟会飞，除了那些还没有学会飞行的幼鸟、受伤的或者虚弱的丧失了飞行能力的鸟、还有一些特殊种类的鸟比如鹤鸵等等"  
概率可以看错是逻辑在不确定性上的扩展  


# 概率分布  

随机变量：$\mathrm{x}$(一般用罗马字体)  
随机变量对应的概率分布：$\mathrm{x} ~ P(\mathrm{x})$  


# 概率密度函数（probability density function(PDF)）
  
概率密度函数有如下性质:  
* $p$的值域是$\mathrm{x}$所有可能的状态  
* $\forall x \in \mathrm{x}, p(x) \ge 0$，注意这里没有$p(x) \le 1$的约束  
* $\int{p(x)d(x)} = 1$  

# 边缘概率（marginal probability）

对于离散值：  
$\forall x \in \mathrm{x}, P(\mathrm{x} = x) = \underset{y} \sum P(\mathrm{x}=x,\mathrm{y}=y)$  
对于连续值：  
$p(x) = \int{p(x,y)dy}$  

# 条件概率（conditional probability）
  
$P(\mathrm{y} = y |\mathrm{x} = x) = \frac{P(\mathrm{x} = x, \mathrm{y} = y)}{P(\mathrm{x} = x)}$ 
# 条件概率的链式规则(the chain rule of conditional probabilities)

$P(\mathrm{x}^{(1)},\mathrm{x}^{(2)},...,\mathrm{x}^{(n)}) = P(\mathrm{x}^{(1)}) \prod_{i=2}^nP(\mathrm x^{(i)} | \mathrm{x}^{(1)},...,\mathrm x^{(i-1)})$  
$P(\mathrm {a,b,c}) = P(\mathrm {a|b,c})P(\mathrm {b,c})$  
$P(\mathrm {b,c}) = P(\mathrm {b|c})P(\mathrm c)$  
$P(\mathrm {a,b,c}) = P(\mathrm {a|b,c})P(\mathrm {b|c})P(\mathrm c)$
# 条件独立(conditional independence)  
$x$和$y$条件独立，则有:$\forall x \in \mathrm x, y \in \mathrm y, p(\mathrm x = x, \mathrm y = y) = p(\mathrm x = x)p(\mathrm y = y)$  
# 期望(expection)、方差(variance)、协方差(covariance) 
```
期望
```
对于离散值，$\mathbb E_{\mathrm x \sim P[f(x)]} = \underset{x} \sum P(x)f(x)$  
对于连续值，$\mathbb E_{\mathrm x \sim p[f(x)]} = \inf p(x)f(x)dx$  
```
方差
```
$Var(f(x)) = \mathbb E[(f(x) - \mathbb E[f(x)])^2]$  
```
协方差
```
$Cov(f(x), g(y)) = \mathbb E[(f(x)- \mathbb E[f(x)])(g(y)- \mathbb E[g(y)])] $  
# 信息论  
信息论背后直观的想法如下：不经常发生的事情往往比经常发生的事情更加具有信息量，比如“太阳今天升起了”没有什么信息量，而“今天发生日食了”就更加具有信息量  
我们希望找到一个符合上述直觉的衡量信息的方式  
* 更可能发生的事情具有更少的信息量，极端情况下，确定发生的事情没有信息量  
* 不常发生的事情具有更多的信息量  
* 独立的事情具有额外的信息量  
为了满足上面三个性质，我们定义**自信息(self-information)**  
$$I(x) = -\log P(x)$$

# KL散度（Kullback-Leibler (KL) divergence）  
如果存在对于$\mathrm x$的$P(x)$和$Q(x)$两个不同的概率分布，那么我么可以KL散度来衡量这两个分布的差别  
$$D_{KL}(P||Q) = E_{\mathrm x \sim P} [\log \frac{P(x)}{Q(x)}]$$  
# 图概率模型  
```
有向图
```
![upload successful](/images/pasted-61.png)  
$p(a,b,c,d,e) = p(a)p(b|a)p(c|a,b)p(d|b)p(e|c)$  
