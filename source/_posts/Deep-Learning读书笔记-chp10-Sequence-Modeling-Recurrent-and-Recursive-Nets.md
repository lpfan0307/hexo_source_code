title: ' Deep Learning读书笔记 chp10-Sequence Modeling: Recurrent and Recursive Nets'
author: nullfan
date: 2020-02-27 22:36:28
tags:
---
# RNN常见的几种结构  
## 输入输出都是序列
![upload successful](/images/pasted-70.png)  
$a^{(t)} = b + Wh^{(t-1)} + Ux^{(t)}$  
$h^{(t)} = \tanh(a^{(t)})$  
$o^{(t)} = c + Vh^t$  
${\widehat y}^{(t)} = softmatx(o^{(t)})$  


![upload successful](/images/pasted-71.png)  
这个网络图将每一层的输出层传递给后面一层，这通常会丢失到一些信息； 相比传递隐藏层，这样的网络的每层传递的信息更少。但这样的网络在训练和并行上具有一定的便利性。  

## 输入是序列，输出是一个单个  

![upload successful](/images/pasted-72.png)  

## Tearch Forcing  

![upload successful](/images/pasted-73.png)  

## fully connected graphical model  

![upload successful](/images/pasted-74.png)  

## 输入是固定长度向量，输出是一个序列  

![upload successful](/images/pasted-75.png)  

## 双向RNN  

![upload successful](/images/pasted-76.png)  
## Encoder-Decoder Sequence-to-Sequence Architectures 

![upload successful](/images/pasted-77.png)  

# The Long Short-Term Memory and Other Gated RNNs
## LSTM

![upload successful](/images/pasted-78.png) 
### forget gate:
$$f_i^{(t)} = \sigma (b_i^f + \sum_j{(U_{i,j}^f x_j^{(t)})} + \sum_j{W_{(i,j)}^f h_j^{(t-1)})}$$
其中$x^{(t)}$是当前输入向量，$h^{(t)}$是当前隐藏层向量，$b^f$、$U_f$、$W^f$分别对应forget的bias、输入权重和循环权重 
### the LSTM cell internal state  
$$s_i^{(t)} = f_i^{(i)}s_i^{(t-1)} + g_i^{(t)} \sigma (b_i+ \sum_j U_{(i,j)}x_j^{(t)} + \sum_j W_{(i,j)}h_j^{(t-1)})$$  
其中$b$、$U$、$W$分别代表LSTM cell的bias、输入权重和循环权重  
### the external input gate  
$$g_i^{(t)} = \sigma (b_i^g + \sum_j U_{(i,j)}^g x_j^{(t)} + \sum_j W_{(i,j)}^g h_j^{(t-1)})$$  
### output gate  
$$h_i^{(t)} = \tanh (s_i^{(t)}) q_i^{(t)}$$
$$q_i^{(t)} = \sigma (b_i^o + \sum_j U_{(i,j)}^o x_j^{(t)}+ \sum_j W_{(i,j)}^o h_j^{(t-1)})$$  
output $h_i^{(t)}$由output gate $q_i^{(t)}$控制  

## GRN  
$$h_i^{(t)} = u_i^{(t-1)} h_i^{(t-1)} + (1 - u_i^{(t-1)}) \sigma (b_i + \sum_j U_{(i,j)} x_j^{(t-1)}) + \sum_j W_{(i,j)} r_j^{(t-1)} h_j^{(t-1)})$$  
$$u_i^{(t)} = \sigma (b_i^u + \sum_j U_i^u x_j^{(t)} + \sum_j W_{(i,j)}^u h_j^{(t)})$$  
$$r_i^{(t)} = \sigma (b_i^r + \sum_j U_i^r x_j^{(t)} + \sum_j W_{(i,j)}^r h_j^{(t)})$$