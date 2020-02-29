title: Hexo基础配置学习
author: nullfan
tags:
  - markdown
  - hexo入门
categories:
  - Hexo
date: 2020-01-06 11:20:00
---
## 博客环境搭建  
hexo搭建博客的原理：生成博客的代码是可以同步到自己的github上，这样可以轻松实现博客在不同端的迁移和保存工作，比如我的博客的github代码库如下：https://github.com/lpfan0307/hexo_source_code ；  同时根据这个代码库，可以生成用户可见的博客，托管在github上，其他用户可以根据网址访问相应的博客，比如访问我博客的链接如下：https://lpfan0307.github.io/ 

这里是hexo的中文官网：https://hexo.io/zh-cn/docs/  
建立博客环境的方式如下：https://hexo.io/zh-cn/docs/setup  

## 主题选择 
选取的主题是Next，这个主题是使用较为广泛的，使用的时候可以较少踩坑，同时，因为这个博客系列主要是技术博客，可能会涉及到一些数学公式的编写，采用Next主题，可以很好的适配[mathjax](https://colobu.com/2014/08/17/MathJax-quick-reference/)，在浏览器中插入数学公式。 [mathjax](https://colobu.com/2014/08/17/MathJax-quick-reference/)插入数学公式可以参考如下链接：http://stevenshi.me/2017/06/26/hexo-insert-formula/

## Hexo Markdown
### Hexo的可视化编辑器：
https://github.com/jaredly/hexo-admin  
按照这个github配置后编辑的效果如下：

![upload successful](/images/pasted-57.png)  
可以将hexo中的mark down实时渲染，可以理解为一个支持很好的mark down的IDE，使用起来非常方便。  
### Hexo Markdown 
这里我记录一些我可能会经常用到的语法
这里主要参考文献如下：  
https://fengmumu1.github.io/2018/06/29/hexo-markdown-grammar/  
https://hyxxsfwy.github.io/2016/01/15/Hexo-Markdown-%E7%AE%80%E6%98%8E%E8%AF%AD%E6%B3%95%E6%89%8B%E5%86%8C/
####  标题
\# H1    
\##  H2  
\...     
\###### H6     
#### 分割线
***  

---  
\*** 或者 ---
#### 超链接  
\[链接文字](链接地址 "链接标题")  
#### 注释  
用 \ 表示注释，\ 后面的文字解析为纯文本格式。  
#### 引用  
使用 > 表示引用  
>  野火烧不尽，春风吹又生 

#### 列表与表格
** 无序列表 **   
使用 *，+，- 表示无序列表。

![upload successful](/images/pasted-58.png)  

+ 无序列表项 一
	- 子无序列表 一
	- 子无序列表 二
		* 子无序列表 三
+ 无序列表项 二
+ 无序列表项 三  

** 有序列表 **  

使用数字和点表示有序列表。

1. 有序列表项 一
	1. 子有序列表项 一
	2. 子有序列表项 二
2. 有序列表项 二
3. 有序列表项 三

#### 绘制表格
绘制表格格式如下，| 控制分列，- 控制分行，: 控制对齐方式。

| Item     | Value     | Qty   |
| :------- | --------: | :---: |
| Computer | 1600 USD  | 5     |
| Phone    | 12 USD    | 12    |
| Pipe     | 1 USD     | 234   |  
#### 代码块  
```
这里是代码块
```
## Hexo数学公式  
Hexo插入数学公式：http://stevenshi.me/2017/06/26/hexo-insert-formula/

$f(x)=ax+b$  
$f(x) = a_1x^n + a_2x^{n-1} + a_3x^{n-2}$  
$\left \lbrace \sum_{i=0}^n i^3 = \frac{(n^2+n)(n+6)}{9} \right \rbrace$  
$\frac xy$  
$ x+3 \over y+5 $  
$ \lim_{x \to 0} $