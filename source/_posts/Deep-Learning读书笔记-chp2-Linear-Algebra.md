title: Deep Learning读书笔记 chp2-Linear Algebra
author: nullfan
tags:
  - deep learning
  - linear algebra
categories:
  - 读书笔记
date: 2020-01-20 11:20:00
---
Deep Learning第二章，线性代数，这里我摘抄一些重要的公式，顺便练习下latex  
```
矩阵乘法的分配律和结合律
```
* $A(B+C) = AB + AC$
* $A(BC) = (AB)C$  

```
Norms
```
$L^p $ Norm如下：
$||x||_p = (\sum_i{|x_i|}^p)^{1 \over p}$  

Norm有如下性质：
* $f(x) = 0 \Rightarrow x = 0$  
* $f(x + y) \leq f(x) + f(y) $(the triangle inequality)
* $\forall \alpha \in \mathbb{R}, f({\alpha}x) = |\alpha|f(x)$

```
正交矩阵(orthogonal matrix)
```
单位矩阵(unit vector)：$||x||_2 = 1$  
正交矩阵：$A^TA = AA^T = I$，这意味着 $A^{-1} = A^T$

```
正定矩阵(positive definite)
```
所有的特征值都为整数的矩阵是正定矩阵(positive define)，所有特征值都为非负数的矩阵是半正定矩阵(positive semidefine)  
所有的半正定矩阵存在如下性质：${\forall} x, x^TAx \geq 0$  
正定矩阵还有额外性质：$x^TAx = 0 \Rightarrow x = 0$

```
特征分解（eigendecomposition）
```
$A$的特征向量表示：
$Av = {\lambda}v$，其中$v$为非0向量，表示$A$的特征向量，$\lambda$为对应特征值  
由于$v$的每个元素放大$k$倍，还是$A$的特征向量，所以通常情况是考虑$v$为单位向量的情况  
假设$A$有$n$个线性无关特征向量，表示为 $V = [v^{(1)}, ... , v^{(n)}]$，对应的特征值表示为 $\lambda = [{\lambda}^{(1)}, ... , {\lambda}^{(n)}]$，则矩阵$A$的特征分解表示为$$A = V{diag(\lambda)}V^{-1}$$，并不是所有的矩阵都有对应的特征分解。  

实数对称矩阵有一个很好的性质，每个实数对称矩阵都可以被分解为如下：$$A = Q{\Lambda}Q^T$$，其中$Q$是由矩阵$A$的特征向量组成的正交矩阵，$\Lambda$是由$A$的特征值组成的对角矩阵  

```
奇异值分解(sigular value decomposition)
```
有些矩阵不存在特征分解，但任何矩阵都存在奇异值分解，$A = UDV^T$  
假设$A$是$m \times n$的矩阵，则$U$是$m \times m$的正交矩阵，$D$是对角矩阵，$V$也是正交矩阵  
更进一步，可以理解为$U$是$AA^T$的特征向量，$V$是$A^TA$的特征向量，非零的奇异值是$A^TA$的平方根  
```
摩尔-彭若斯广义逆(The Moore-Penrose Pseudoinverse) 
```
对于$Ax = y$,我们希望可以找到一个矩阵$B$，左乘以后希望可以得到$x = By$  
对于不同特性的$A$，可能不存在这样的矩阵$B$或者是存在多个这样的矩阵$B$  
摩尔-彭若斯广义逆定义如下：$A^+ = \lim_{\alpha \searrow 0}(A^TA + {\alpha}I)^{-1}A^T$
实际应用中通常采用另一种方式计算广义逆 $A^+ = VD^+U^T$，其中$U$、$V$、$D$是$A$的奇异值分解对应的矩阵，$D^+$是通过$D$的非零元素取倒数得到的矩阵转置得到  
当$A$的列数多余行数时，广义逆是无数可能解法中的一种，其中 $x = A^+y$是所有解法中$x$的二范数$(||x||_2)$最小的解  
当$A$的行数多余列数时，左乘的矩阵的解有可能不存在。在这种情况下，使用广义逆得到的$x$，会使得$Ax$和$y$在欧氏距离上最小$(||Ax-y||_2)$
```
矩阵的迹(The Trace Operator)
```
$Tr(A) = \sum_i{A_{i,i}}$

矩阵的迹有如下性质:
* $||A||_F = \sqrt{AA_T}$
* $Tr(A) = Tr(A^T)$  
* $Tr(ABC) = Tr(CBA) = Tr(BCA)$  
* $Tr(AB) = Tr(BA)$  
* $a = Tr(a)$  

```
行列式(the Determinant)
```
$det(A)$为矩阵的所有特征值的乘积  
行列式的绝对值表示与该矩阵相乘时，被乘矩阵在空间延展或者浓缩的程度。如果矩阵的行列式为0，乘完后失去所有体积； 如果矩阵行列式绝对值为1，乘完后保持体积不变。

```
主成分分析(prinipal components analysis)
```
主成分分析需要做的事情是这样的，假设我们有一个$n$维的数据，即$x \in {\mathbb{R}}^n$，我们希望可以找到一个映射关系f，将$x$映射到$l$维中，即$f(x) = c$，$c \in {\mathbb{R}}^l，$其中$l \lt n$。同时，在映射的过程中保持信息损失的信息尽可能的少，即我们可以找到另一个映射关系$g$，将$c$映射为$n$维的空间，映射回来的结果要和原始结果尽量接近，即$x \approx g(f(x))$。主成分分析就是希望可以找到$f$和$g$  
为了简化问题，我们假设$g(c)$的对应的解码方式如下$g(c) = Dc$，其中$D \in {\mathbb{R}}^{n \times l}$  
为了是问题简便，主成分分析时加了两个约束条件  
* 矩阵D的每列互相正交  
* 矩阵D的每列都是单位向量 

主成分分析的主要思想是$x \approx g(f(x))$，如果采用二范式，

则为$c^* = \underset{c}{\arg \min} ||x -g(c)||_2$，

等价于$c^* = \underset{c}{\arg \min} ||x -g(c)||_2^2 $   

$||x -g(c)||_2^2 = {(x-g(c))}^T(x-g(c))$ $=$ $x^Tx - x^Tg(c) - {g(c)}^Tx + {g(c)}^Tg(c)$ =  $x^Tx - 2x^Tg(c) + {g(c)}^Tg(c)$   
去除和$c$无关的部分，$c^* =\underset{c}{\arg \min} - 2x^Tg(c) + {g(c)}^Tg(c)$  

将$g(c) = Dc$代入，$c^* =\underset{c}{\arg \min} - 2x^TDc + {Dc}^TDc$ 



$=\underset{c}{\arg \min} - 2x^TDc + c^TI_lc$  
$=\underset{c}{\arg \min} - 2x^TDc + c^Tc$  
上式对$c$求导，即 $-2D^Tx + 2c = 0 \Rightarrow c = D^Tx$   
上述推导表明，对于给定的$x,D$，$c$取$D^Tx$是目标的最优解  
又知道$c = f(x)$，则有$f(x) = c = D^Tc$, $r(x) = g(f(x)) = g(c) = Dc = DD^Tc$  
考虑所有的样本，则最终表达式为$D^* = \underset{D} \arg \min \sum_{i,j} {(x_j^{(i)} - r(x^{(i)})_j)}^2,, s.t. D^TD = I_l$  
考虑$l=1$的情况，上面的式子化简为   

$d^* = \underset{d} \arg \min \underset{i} \sum ||x^(i) - dd^Tx^{(i)}||_2^2, s.t. ||d||_2 = 1$    

考虑所有样本，$d^* = \underset{d} \arg \min \underset{i} \sum ||X - dd^TX||_2^2, s.t. ||d||_2 = 1$  

$\underset{d} \arg \min ||X - Xdd^T||_F^2 s.t. d^d = 1$ 

不考虑约束条件 

$\underset{d} \arg \min ||X - Xdd^T||_F^2$  

$=\underset{d} \arg \min Tr((X - Xdd^T)^T(X-Xdd^T))$  
$=\underset{d} \arg \min Tr(X^TX - X^TXdd^T - dd^TX^TX + dd^TX^TXdd^T)$
$=\underset{d} \arg \min Tr(- X^TXdd^T - dd^TX^TX + dd^TX^TXdd^T)$(去除不包含d的项)  
$=\underset{d} \arg \min -Tr( X^TXdd^T) - Tr(dd^TX^TX) + Tr(dd^TX^TXdd^T)$
$=\underset{d} \arg \min -2Tr( X^TXdd^T)  + Tr(dd^TX^TXdd^T)$
$=\underset{d} \arg \min -2Tr( X^TXdd^T)  + Tr(X^TXdd^Tdd^T)$ 
$=\underset{d} \arg \min -2Tr( X^TXdd^T)  + Tr(X^TXdd^T)$ （$d^Td = 1$）  
$=\underset{d} \arg \min -Tr( X^TXdd^T)  $ （$d^Td = 1$） 
$=\underset{d} \arg \max Tr( X^TXdd^T)  $ （$d^Td = 1$）  
$=\underset{d} \arg \max Tr( d^TX^TXd)  $ （$d^Td = 1$）  




```
参考资料
```
latex数学公式在线编辑器：所见即所得  https://zohooo.github.io/jaxedit/  
latex输入语法：https://zhuanlan.zhihu.com/p/50667788  
latex箭头汇总:https://blog.csdn.net/liyuanbhu/article/details/51473886  
pac讲解视频：https://www.youtube.com/watch?v=FgakZw6K1QQ  
latex特殊符号：https://blog.csdn.net/caiandyong/article/details/53351737