---
layout: post
title: 矩阵分块乘法的一些推论
categories: 
 -Math
permalink: /posts/Important-Results-from-Matrix-Block-Multiplication
---

# 矩阵分块乘法的一些推论

### 简述

矩阵可以分块相乘似乎是矩阵乘法中相当本质的特点,基于它我们可以对矩阵乘法建立起一系列有用的推论


### 一些设定

设 $A$ 是 $m * n$ 的矩阵, $B$ 是 $n * p$ 的矩阵
设 $M$ 是任意矩阵.  
用 $M_{ij}$ 表示 $M$ 在第 $i$ 行, 第 $j$ 列处的元素    
用 $M.row[i]$ 表示 $M$ 的第 $i$ 行元素构成的向量  
用 $M.col[i]$ 表示 $M$ 的第 $i$ 列元素构成的向量

### 矩阵乘法定义

定义矩阵乘积 $AB$ 为 $m*p$ 的矩阵, 其中

$$
(AB)_{ij}=A.row[i] \cdot B.col[j]
$$

### 矩阵与列向量相乘 $Ax$

我们可以将 $A$ 按列进行划分, 每一列单独构成一个子矩阵, 这样 $A$ 可以理解为由 $n$ 个子矩阵构成的 $1*n$ 的分块矩阵  

  
$$
A=[A.col[1],A.col[2],...,A.col[n]]
$$

另一方面, 列向量 $x$ 可以理解为 $n * 1$ 的矩阵  


$$
x=[x_1,x_2,...,x_n]^T
$$

从分块相乘出发, 可得  


$$
Ax=\sum_{i=1}^n(x_iA.col[i])
$$

这表明, 矩阵与列向量 $x$ 相乘 ,将得到以 $x$ 各分量为系数,自身列向量为基底的线性组合.

### 以矩阵列变换的角度理解矩阵乘法

考虑 $AB$. 将 $B$ 视为 $1*p$ 的矩阵, 它的每个元素是长度为 $n$ 的列向量.  
根据分块乘法  


$$
\begin{align}
AB&=A\cdot[B.col[1], B.col[2], ..., B.col[p]]\\
&=[A\cdot B.col[1], A \cdot B.col[2], ..., A \cdot B.col[p]]
\end{align}
$$
  

于是有  


$$
AB.col[i]= A \cdot B.col[i]
$$
  

即, $AB$ 的第 $i$ 列由 $A$ 左乘 $B$的第 $i$ 列得到.  
结合矩阵左乘列向量得到自身列向量关于该向量系数的线性组合, 乘积 $AB$ 我们可以理解为以 $B$ 的诸列向量对 $A$ 进行列变换所得的向量所构成的矩阵. 或者,换句话说, $B$ 的列向量
表达了对 $A$ 的各列向量所进行的变换操作.

列变换的一些例子  

* $AI=A$.  
  $I$ 的第 $i$ 列被 $A$ 左乘以后构成了 $AI$ 的第 $i$ 列. 根据 $I$ 的定义, 它恰好选取了 $A$ 的第 $i$ 列进行了保留.
* 如果把 $I$ 的第 $i$ 列,乘以常数 $c$, 得到新的矩阵 $I_ic$ , 则 $AI_ic$ 的结果相当于对 $A$ 的第 $i$ 列乘以常数 $c$  
* 如果把 $I$ 的第 $j$ 列加到第 $i$ 列上, 得到新矩阵被 $A$ 左乘, 则结果相当于对 $A$ 进行同样的操作.

**Remark: 矩阵相乘相当于使用右乘矩阵的诸列对左乘矩阵进行列变换**

### 以矩阵行变换的角度理解矩阵乘法  

考虑 $AB$ . 将 $A$ 视为 $m * 1$ 的矩阵, 它的每个元素是长度为 $n$ 的向量.

根据分块乘法  


$$
\begin{align}
AB&=[A.row[1],A.row[2],...A.row[m]]^T \cdot B\\
&=[A.row[1] \cdot B, A.row[2] \cdot B,..., A.row[m] \cdot B]^T
\end{align}
$$

  

考察矩阵右乘向量 $xB$ , 其中 $x$ 是长度为 $n$ 的任意向量 .  

将 $B$ 的每行视为一个元素. 则 $B$ 变为长度为 $n$ 的列向量.   


$$
B=[B.row[1],B.row[2],...,B.row[n]]^T
$$
  

从而  


$$
xB=\sum_{i=1}^nx_iB.row[i]
$$
  

由此可见, 矩阵右乘向量 $x$ ,得到以 $x$ 为系数, 矩阵自身行向量的线性组合. $AB$ 的第 $i$ 行, 由 $A$ 的第 $i$ 行乘以 $B$ 得到, 因此矩阵 $A$ 左乘 $B$, 相当于用自身的行对矩阵 $B$ 进行行变换.

**Remark:矩阵相乘相当于使用左乘矩阵的诸行对右乘矩阵进行行变换**

### $(AB)^T=B^TA^T$ 的证明

显然两者阶数相等.只需证明 $(AB)^T_{ij}=(B^TA^T)_{ij}$   


$$
\begin{align}
(AB)^T_{ij}&=(AB)_{ji}\\
&=A.row[j] \cdot B.col[i]\\
&=A^T.col[j] \cdot B^T.row[i]\\
&=(B^TA^T)_{ij}
\end{align}
$$



证毕

### 矩阵乘法结合律的证明

设 $C$ 是可以右乘 $B$ 的任意矩阵. 其阶数设为 $p*q$, 则有 $(AB)C=A(BC)$ 

#### Proof 

引理1

定义常数 $k$ 与矩阵 $M$ 相乘的结果 $kM$ 为将 $M$ 的元素均乘以 $k$ 后所得矩阵. 并定义 $Mk=kM$

则  

* 当 $M$ 为向量时, 此乘法即向量的数乘.
* $(AB) \cdot k = A \cdot (kB)$

引理2

矩阵乘法(无论左乘右乘)满足分配律, 即  


$$
A(B+C)=AB+AC
$$

$$
(B+C)A=BA+CA
$$



回到原命题.   

显然两边具有相等的阶数. 我们可以证明两边对应列相等.

左边的第 $k$ 列  


$$
\begin{align}
left.col[k]&=(AB) \cdot C.col[k]\\
&=\sum_{i=1}^n((AB).col[i] \cdot C.col[k][i])\\
&=\sum_{i=1}^n((A \cdot B.col[i]) \cdot C.col[k][i])\\
&=\sum_{i=1}^n(A \cdot (B.col[i] \cdot C.col[k][i])) (由引理1)\\
&=A \cdot \sum_{i=1}^n(B.col[i] * C.col[k][i])(由引理2)\\
&=A \cdot (B \cdot C.col[k])\\
&=A \cdot (BC).col[k]\\
&=right.col[k]
\end{align}
$$
  

证毕.

















