---
title: 矩阵
time: 2020-10-13 18:36:40
tags: [note,unfinished]
categories: [笔记,数学,线性代数]
math: true
---
## 线性变换和矩阵
### 线性方程组
$$\Bigg\{\begin{alignedat}{4}a_{11}&x_1+&a_{12}&x_2+...+a_{1n}x_n=&b_1\\a_{21}&x_1+&a_{22}&x_2+...+a_{2n}x_n=&b_2\\...&...\\a_{m1}&x_1+&a_{m2}&x_2+...+a_{mn}x_n=&b_m\end{alignedat}$$
形如上述方程组的方程组是线性方程组。当常数项$b_1,b_2,...b_m$全部等于0时，上述线性方程组为**n元非齐次线性方程组**。当常数项均为0时，该式为**n元齐次线性方程组**。

对于线性方程组，我们需要讨论：
1. 它是否有解？
2. 在有解时该解是否唯一？
3. 如果有多个解，如何求出它的所有解？

需要注意的是，对于线性方程组，上述三个问题的答案完全取决于其式中的$m*n$个系数和右端的常数项$b_1,b_2,...b_m$。或者说，完全取决于它们构成的矩形数表:

$$\begin{matrix}a_{11}&a_{12}&...&a_{1n}&b_{1}\\a_{21}&a_{22}&...&a_{2n}&b_{2}\\...&...&&...\\a_{m1}&a_{m2}&...&a_{mn}&b_{m}\end{matrix}$$
另外，对于**齐次**线性方程组，相应问题的答案完全取决于：
$$\begin{matrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\...&...&&...\\a_{m1}&a_{m2}&...&a_{mn}\end{matrix}$$

### 矩阵
$$\bold{A}=\begin{pmatrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\...&...&&...\\a_{m1}&a_{m2}&...&a_{mn}\end{pmatrix}$$
如上由$m*n$个数排成的$m$行$n$列的数表称为$m$行$n$列矩阵（$m*n$矩阵）。
其余定义不作赘述。

### 线性变换
如$n$个变量$x_1,x_2,...,x_n$与$m$个变量$y_1,y_2,...,y_m$之间的关系式：
$$\Bigg\{\begin{alignedat}{4}a_{11}&x_1+&a_{12}&x_2+...+a_{1n}x_n=&y_1\\a_{21}&x_1+&a_{22}&x_2+...+a_{2n}x_n=&y_2\\...&...\\a_{m1}&x_1+&a_{m2}&x_2+...+a_{mn}x_n=&y_m\end{alignedat}$$
表示的是一个从变量$x_1,x_2,...,x_n$到$y_1,y_2,...,y_m$的线性变换。为了便于理解，使用矩阵进行表示：
$$\underbrace{\begin{pmatrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\...&...&&...\\a_{m1}&a_{m2}&...&a_{mn}\end{pmatrix}}_{\text{线性变换}}\underbrace{\begin{pmatrix}x_1\\x_2\\...\\x_n\end{pmatrix}}_{\text{输入向量}}=\underbrace{\begin{pmatrix}y_1\\y_2\\...\\y_n\end{pmatrix}}_{\text{输出向量}}$$
此处显然使用了矩阵相乘来计算$y_1,y_2,...,y_m$的值。但理解该式的意义并不需要会计算它。为了便于说明，使用二阶方阵：
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}$$
该矩阵作为线性变换的几何意义是将基向量$\hat{i}=\begin{pmatrix}1\\0\end{pmatrix}$和$\hat{j}=\begin{pmatrix}0\\1\end{pmatrix}$拉伸或压缩为$\hat{i}=\begin{pmatrix}a\\c\end{pmatrix}$$\hat{j}=\begin{pmatrix}b\\d\end{pmatrix}$。因为空间（此处为平面）基于基向量展开，所以空间会被拉伸或压缩。在向量被输入到线性变换时：
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}\begin{pmatrix}2\\3\end{pmatrix}=\begin{pmatrix}2a+3b\\2c+3d\end{pmatrix}$$
即输入向量会被线性变换变换为其空间在线性变换后的值，即输出向量。

又如三阶矩阵，显然，其表示一个三维空间的线性变换。实际上其和二维空间大同小异，只是多了一个基向量$\hat{k}$。