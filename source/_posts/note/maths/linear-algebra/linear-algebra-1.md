---
title: 行列式
time: 2020-09-30 09:36:40
tags: [note,unfinished]
categories: [笔记,数学,线性代数]
math: true
---

## 何为行列式
行列式，是我们通过一个方阵矩阵能够计算出的一个值。在几何上，它代表**对应矩阵所表示的线性变换对单位面积/体积的缩放的比例**。

我们可以将矩阵A的行列式表示为：
$$det(A),det A, |A|$$
注意其中最后一种表示方式和绝对值表示方式的相似。

行列式可以被用于求解线性方程组，并且在微积分等领域均有相应应用。

## 行列式的计算
:::warning
注意：非方阵的矩阵没有行列式。
:::

### 一阶行列式
我们规定，一阶行列式$\begin{vmatrix}a\end{vmatrix}=a$。
### 二阶行列式
二阶行列式记作如下形式：
$$\begin{vmatrix}
   a & b \\
   c & d
  \end{vmatrix}$$
其对应的矩阵为：
$$\begin{bmatrix}
   a & b \\
   c & d
  \end{bmatrix}$$
矩阵对应的线性变换是将列空间从
$$\begin{bmatrix}1&0\\0&1\end{bmatrix}$$
变换为$\hat{i}=(a,c),\hat{j}=(b,d)$。

所以，**行列式的值为该线性变换所导致的单位面积的变化：$ad-bc$**

#### 推导
:::warning
下述在某轴正方向上移动的距离，均指该向量除原点外的另一个端点的移动。首先，线性变换代表的仅仅是基的替换，它们的起始点仍为原点；其次，线性变换规定原点不能移动，换言之，如果原点移动了，那么该变换不是线性变换。
:::
在此，
$a$代表$\hat{i}$在$x$轴正方向上移动的距离；
$c$代表$\hat{i}$在$y$轴正方向上移动的距离。

类似地，
$b$代表$\hat{j}$在$x$轴正方向上移动的距离；
$d$代表$\hat{j}$在$y$轴正方向上移动的距离。

显然，在变换后，我们可以发现原本由基向量$\hat{i},\hat{j}$围成的面积为1的正方形被挤压或拉伸，而通过计算并化简之后，可以得出变换后得到的相应的平行四边形的面积为$\begin{vmatrix}a&b\\c&d\end{vmatrix}$，即$ad-bc$。

具体的内容见3b1b的[线性代数的本质系列视频](https://www.bilibili.com/video/BV1ys411472E?p=4)。

### 三阶行列式
三阶行列式如：
$$\begin{vmatrix}
   a & b & c \\
   d & e & f \\
   g & h & i
  \end{vmatrix}$$
类似地，其对应矩阵为：
$$\begin{bmatrix}
   a & b & c \\
   d & e & f \\
   g & h & i
  \end{bmatrix}$$
类似地，该矩阵也对应一个线性变换。只不过因为显然该矩阵对应的基向量是三维空间中的向量，所以该变换对应的是三维空间中的变换，同时行列式对应的是原体积为1的正方体的体积在变换后被放大或缩小成的平行六面体的体积。

由于描述上的麻烦，在此不作推导的解释，但推导原理和二阶行列式的推导原理类似。

总之，三阶行列式的值为
$$a\begin{vmatrix}
e&f\\
h&i
\end{vmatrix}
-b\begin{vmatrix}
d&f\\
g&i
\end{vmatrix}
+c\begin{vmatrix}d&e\\
g&h
\end{vmatrix}$$
此处使用了[*行列式的按行展开*](#行列式按行列展开)。

### n阶行列式
#### 推导：排列
为了推导方便，我们将行列式中的元素均替换为$a_{ij}$。其中，$i$代表该元素所在的行数，$j$代表该元素所在的列数。如下：
$$\begin{vmatrix}
   a_{11} & a_{12} & a_{13} \\
   a_{21} & a_{22} & a_{23} \\
   a_{31} & a_{32} & a_{33}
  \end{vmatrix}$$
经过展开并计算，我们可以得出结论：一个$n*n$的行列式的计算中，不合并同类项的情况下，会有$n!$个单项式。其中，每个单项式都是$n$个元素的乘积。每个单项式中的元素均来自不同行和不同列；换言之，每行/每列中只能有一个元素在同一项中。

如果固定列标为标准排序，即$1,2,...,n$，则各项行标的排列的逆序数决定该项的正负：**逆序数为偶，该项为正；逆序数为奇，该项为负。** 固定行标同理。

所以，n阶行列式
$$\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}$$
的值可以通过$\Sigma(-1)^ta_{1p_{1}}a_{1p_{2}}...a_{1p_{n}}$来计算，其中$t$是排列$p_1p_2...p_n$的逆序数。

#### 计算
从上述结论中，我们可以推得上（下）三角行列式的值为$a_{11}a_{22}...a_{nn}$，如下：
$$\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   0 & a_{22} & ... & a_{2n} \\
   ... & 0 & ...& ... \\
   0 & ... & 0 & a_{nn}
  \end{vmatrix}=a_{11}a_{22}...a_{nn}$$
此为上三角行列式。
$$\begin{vmatrix}
   a_{11} & 0 & ... & 0 \\
   a_{21} & a_{22} & 0 & ... \\
   ... & ... & ...& 0 \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}=a_{11}a_{22}...a_{nn}$$
下三角行列式同理。

另外，显然对角行列式的值也为$a_{11}a_{22}...a_{nn}$。
$$\begin{vmatrix}
   a_{11} & 0 & ... & 0 \\
   0 & a_{22} & ... & ... \\
   ... & ... & ...& 0 \\
   0 & ... & 0 & a_{nn}
  \end{vmatrix}=a_{11}a_{22}...a_{nn}$$
基本上，大多数行列式都可以通过对行（列）的操作将其变换为上述上（下）三角行列式。具体操作方式见下一节。
## 行列式的性质
### 性质1
行列式与其转置行列式相等。
$$\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}=\begin{vmatrix}
   a_{11} & a_{21} & ... & a_{n1} \\
   a_{12} & a_{22} & ... & a_{n2} \\
   ... & ... & ...& ... \\
   a_{1n} & a_{2n} & ... & a_{nn}
  \end{vmatrix}$$
左侧为原行列式$D$，右侧为转置后的行列式$D^T$。

由此性质可知，行列式中的行与列具有同等的地位，行列式的性质凡是对行成立的对列同样成立，反之亦然。
### 性质2
对换行列式的两行（列），行列式变号。
#### 推论
如果行列式有两行（列）完全相同，该行列式等于0。
### 性质3
行列式的某一行（列）中所有的元素都乘以同一数$k$，等于用数$k$乘以此行列式。
#### 推论
行列式中某一行（列）中所有元素的公因子可以提到行列式记号的外面。
### 性质4
行列式中如果有两行（列）的元素成比例，则此行列式等于0。
### 性质5
若行列式的某一行（列）的元素都是两数之和，例如第$i$行的元素都是两数之和：
$$D=\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{i1}+a_{i1}'&a_{i2}+a_{i2}'&...&a_{in}+a_{in}'\\
  ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}$$
则$D$等于下列两个行列式之和：
$$D=\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{i1}&a_{i2}&...&a_{in}\\
  ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}+\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{i1}'&a_{i2}'&...&a_{in}'\\
  ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}$$
  ### 性质6
  把行列式的某一行（列）的各元素乘同一数然后加到另一行（列）对应的元素上去，行列式不变。

## 行列式按行（列）展开
一般来说，低阶行列式的计算比高阶行列式的计算更简便。为了使用低阶行列式来表示高阶行列式的问题，我们引入余子式和代数余子式的概念。
### 余子式和代数余子式
在$n$阶行列式中，把$(i,j)$元$a_{ij}$所在的第$i$行和第$j$列划去后，留下来的$n-1$阶行列式叫做$(i,j)$元$a_{ij}$的**余子式**，记作$M_{ij}$；记
$$A_{ij}=(-1)^{i+j}M_{ij}$$
其中$A_{ij}$叫做$(i,j)$元$a_{ij}$的**代数余子式**。
例如一个四阶方阵的行列式是：
$$\begin{vmatrix}1&0&0&0\\0&1&0&0\\0&1&1&1\\0&0&0&1\end{vmatrix}$$
其中，元$a_{23}$的余子式$M_{23}$是：
$$\begin{vmatrix}1&0&0\\0&1&1\\0&0&1\end{vmatrix}$$
元$a_{23}$的代数余子式$A_{23}=(-1)^{2+3}M_{23}$。
:::warning
**注意，某元素代数余子式的值和该元素本身无关。**
:::

### 展开为含代数余子式的多项式
通过使用代数余子式，我们可以计算行列式的值。具体而言，对于$n$阶行列式，有：
$$D=\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{i1}&a_{i2}&...&a_{in}\\
  ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}=a_{i1}A_{i1}+a_{i2}A_{i2}+...+a_{in}A_{in}$$
  上例为行列式的对行展开。对列展开同理。
  
  容易看出，该行（列）中等于0的元素个数越多，使用该方法的计算越简单，如：
  $$D=\begin{vmatrix}
   a_{11} & ...&a_{1j} & ... & a_{1n} \\
   a_{21} & ...&a_{2j} & ... & a_{2n} \\
   ... & ... & ...& ...& ... \\
   0&...&a_{ij}&...&0\\
  ... & ... &...& ...& ... \\
   a_{n1} & ...&a_{nj} & ... & a_{nn}
  \end{vmatrix}=a_{ij}A_{ij}$$
另外，使用其他行（列）的相应元素乘以该行元素对应的代数余子式，得到的结果为0。即：
$$\begin{vmatrix}
   a_{11} & a_{12} & ... & a_{1n} \\
   a_{21} & a_{22} & ... & a_{2n} \\
   ... & ... & ...& ... \\
   a_{i1}&a_{i2}&...&a_{in}\\
   ...&...&...&...\\
    a_{j1}&a_{j2}&...&a_{jn}\\
  ... & ... & ...& ... \\
   a_{n1} & a_{n2} & ... & a_{nn}
  \end{vmatrix}(i\not=j)$$

  $$a_{j1}A_{i1}+a_{j2}A_{i2}+...+a_{jn}A_{in}=0$$
  使用上方[性质2推论](#推论)可以证明。

## 部分特殊行列式化简技巧
此处提到的特殊行列式指元素排布等性质符合一定特点的行列式。在实际计算中，可以通过适当变换将行列式化为下列行列式之一进行计算，例如升阶法等。
:::warning
由于$\KaTeX$的排版貌似只支持等号上下分别给一行公式，所以以下计算过程中略写格式均非标准格式。

本节引自[此处](https://zhuanlan.zhihu.com/p/34685081)。
对公式和说明做了一定修改。
:::
### 爪型
指形如
$$\begin{vmatrix}
   a_{1} & 1&1 & \dots & 1 \\
   1 & a_{2}& 0& \dots & 0 \\
   1 & 0 & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&0\\
   1 & 0& \dots& 0 & a_{n}
  \end{vmatrix}$$
的行列式，即除主对角线、第一列和第一行上元素均不为0之外，其余元素均等于0。

对于该形状的行列式，有固定的化简技巧：
$$\begin{vmatrix}
   a_{1} & 1&1 & \dots & 1 \\
   1 & a_{2}& 0& \dots & 0 \\
   1 & 0 & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&0\\
   1 & 0& \dots& 0 & a_{n}
  \end{vmatrix}=a_2a_3...a_n\begin{vmatrix}
   a_{1} & 1&1 & \dots & 1 \\
   \frac{1}{a_{2}} & 1& 0& \dots & 0 \\
   \frac{1}{a_{3}} & 0 & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&1&0\\
   \frac{1}{a_{n}} & 0& \dots& 0 & 1
  \end{vmatrix}$$
  $$\xlongequal[i=2,3,...,n]{r_1-r_i}a_2a_3...a_n\begin{vmatrix}
   a_{1}-\frac{1}{a_{2}}-\frac{1}{a_{3}}-\dots - \frac{1}{a_{n}}& 0&0 & \dots & 0 \\
   \frac{1}{a_{2}} & 1& 0& \dots & 0 \\
   \frac{1}{a_{3}} & 0 & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&1&0\\
   \frac{1}{a_{n}} & 0& \dots& 0 & 1
  \end{vmatrix}$$
  $$=a_2a_3...a_n(a_{1}-\frac{1}{a_{2}}-\frac{1}{a_{3}}-\dots - \frac{1}{a_{n}})$$

### 两三角型
指形如
$$\begin{vmatrix}
   a_{1} & c&c & \dots & c \\
   b & a_{2}& c& \dots & c \\
   b & b & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&c\\
   b & b& \dots& b & a_{n}
  \end{vmatrix}$$
的行列式。

当$b=c$时，可以化为上述爪形行列式：
$$\begin{vmatrix}
   a_{1} & b&b & \dots & b \\
   b & a_{2}& b& \dots & b \\
   b & b & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&b\\
   b & b& \dots& b & a_{n}
  \end{vmatrix}\xlongequal[i=2,3,...,n]{r_i-r_1}\begin{vmatrix}
   a_{1} & b&b & \dots & b \\
   b-a_1 & a_{2}-b& 0& \dots & 0 \\
   b-a_1 & 0 & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}-b&0\\
   b-a_1 & 0& \dots& 0 & a_{n}-b
  \end{vmatrix}$$
当$b\not = c$时，使用[拆行（列）法](#性质6)：
$$\begin{vmatrix}
   a_{1} & c&c & \dots & c \\
   b & a_{2}& c& \dots & c \\
   b & b & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&c\\
   b & b& \dots& b & a_{n}
  \end{vmatrix}=\begin{vmatrix}
   a_{1} & c&c & \dots & c+0 \\
   b & a_{2}& c& \dots & c+0 \\
   b & b & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&c+0\\
   b & b& \dots& b & a_{n}+b-b
  \end{vmatrix}$$
$$=\begin{vmatrix}
   a_{1} & c&c & \dots & c \\
   b & a_{2}& c& \dots & c \\
   b & b & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&c\\
   b & b& \dots& b & b
  \end{vmatrix}+\begin{vmatrix}
   a_{1} & c&c & \dots & 0 \\
   b & a_{2}& c& \dots & 0 \\
   b & b & \ddots&\ddots & \vdots \\
   \vdots &\vdots& \ddots&a_{n-1}&0\\
   b & b& \dots& b & a_{n}-b
  \end{vmatrix}\tag{1}$$
$$=\begin{vmatrix}
   a_{1}-c & 0&0 & \dots & c \\
   b-c & a_{2}-c& 0& \dots & c \\
   \vdots & \ddots & \ddots&\ddots & \vdots \\
   b-c &\dots&b-c &a_{n-1}-c&c\\
   0 & 0& \dots& 0 & b
  \end{vmatrix}+(a_n-b)D_{n-1}$$
化简得
$$D_n=b(a_1-c)(a_2-c)...(a_{n-1}-c)+(a_n-b)D_{n-1}\tag{2}$$
如果将$(1)$中两行列式第n列上的b用c替换，则可得
$$D_n=c(a_1-b)(a_2-b)...(a_{n-1}-b)+(a_n-c)D_{n-1}\tag{3}$$
由$(2)(3)$整理可得
$$D_n=\frac{1}{b-c}\bigg[b\prod_{i=1}^n(a_i-c)-c\prod_{i=1}^n(a_i-b) \bigg]$$

若每行（列）上有公因子，可以尝试将之提出后转化为两三角形行列式；若无法在保持行列式不变的基础上提出，采用升阶法：
$$\begin{vmatrix}1+x_1^2&x_1x_2&x_1x_3&\dots&x_1x_n\\x_2x_1&1+x_2^2&x_2x_3&\dots&x_2x_n\\x_3x_1&x_3x_2&1+x_3^2&\dots&x_3x_n\\\dots&\dots&\dots&\dots&\dots\\x_nx_1&x_nx_2&x_n+x_3&\dots&1+x_n^2\end{vmatrix}$$
加边升阶可得
$$\begin{vmatrix}1&x_1&x_2&x_3&\dots&x_n\\0&1+x_1^2&x_1x_2&x_1x_3&\dots&x_1x_n\\0&x_2x_1&1+x_2^2&x_2x_3&\dots&x_2x_n\\0&x_3x_1&x_3x_2&1+x_3^2&\dots&x_3x_n\\0&\dots&\dots&\dots&\dots&\dots\\0&x_nx_1&x_nx_2&x_n+x_3&\dots&1+x_n^2\end{vmatrix}$$
$$\xlongequal[i=2,3,...,n+1]{r_i-x_{i-1}r_1}\begin{vmatrix}1&x_1&x_2&x_3&\dots&x_n\\-x_1&1&0&0&\dots&0\\-x_2&0&1&0&\dots&0\\-x_3&0&0&1&\dots&0\\\dots&\dots&\dots&\dots&\dots&\dots\\-x_n&0&0&0&\dots&1\end{vmatrix}$$

### 两条线型
指形如
$$\begin{vmatrix}a_1&b_1&&\\&a_2&b_2&\\&&a_3&\ddots\\&&&\ddots&&\\&&&&a_{n-1}&b_{n-1}\\b_n&&&&&a_n\end{vmatrix}（空白处均为0）$$
按照第一列两个非0元素展开即可。

### 范德蒙德型
指有逐行（列）元素按幂递增（减），可以将其转化为范德蒙德行列式来计算，如：
$$\begin{vmatrix}a_1^n&a_1^{n-1}b_1&\dots&a_1b_1^{n-1}&b_1^n\\a_1^n&a_1^{n-1}b_1&\dots&a_1b_1^{n-1}&b_1^n\\\vdots&\vdots&&\vdots&\vdots\\a_1^n&a_1^{n-1}b_1&\dots&a_1b_1^{n-1}&b_1^n\\a_1^n&a_1^{n-1}b_1&\dots&a_1b_1^{n-1}&b_1^n\end{vmatrix}$$
$$=\prod_{i=1}^{n+1}a_{i}^n\begin{vmatrix}1&\frac{b_1}{a_1}&\dots&(\frac{b_1}{a_1})^{n-1}&(\frac{b_1}{a_1})^{n}\\1&\frac{b_2}{a_2}&\dots&(\frac{b_2}{a_2})^{n-1}&(\frac{b_2}{a_2})^{n}\\\vdots&\vdots&&\vdots&\vdots\\1&\frac{b_1}{a_1}&\dots&(\frac{b_1}{a_1})^{n-1}&(\frac{b_1}{a_1})^{n}\\1&\frac{b_1}{a_1}&\dots&(\frac{b_1}{a_1})^{n-1}&(\frac{b_1}{a_1})^{n}\end{vmatrix}$$
上述行列式即范德蒙德行列式，公式为：
$$D_n=\prod_{1\leq i<j\leq n+1}(a_ib_j-b_ia_j)$$

### Hessenberg型
指除了主（次）对角线及于其相邻的斜线，再加上第一行（列）或第n行（列）外，其余元素均为0。
一般可以将某一行（列）都化简到只有一个非0元素，便于降阶计算，如：
$$\begin{vmatrix}1&2&3&\dots&n-1&n\\1&-1\\&2&-2\\&&\ddots&\ddots\\&&&n-1&2-n\\&&&&n-1&1-n\end{vmatrix}$$
$$\xlongequal[i=2,3,...,n]{c_1+c_i}\begin{vmatrix}\frac{n(n+1)}{2}&2&3&\dots&n-1&n\\0&-1\\0&2&-2\\\vdots&\ddots&\ddots&\ddots\\0&&&n-2&2-n\\0&\dots&&0&n-1&1-n\end{vmatrix}$$
降阶后重复上述步骤可得通式$$D_n=(-1)^{n-1}\frac{(n+1)!}{2}$$
:::info
需要说明的是，上面举的例子比较容易看出如何实施累加消点法就可以实现将某一行(列)都化简到只有一个非0元素从而达到降阶的目的，但是还有很多Hessenberg型行列式并不这么容易就做到，还需要大家找找技巧稍微变换一下，只要始终记得你要用累加消点法来消元来降阶就可以了。
:::

### 三对角型
指形如
$$\begin{vmatrix}a&b&\\c&a&b\\
&c&\ddots&\ddots\\&&\ddots&\ddots&b\\&&&c&a\end{vmatrix}$$
的行列式。除上述三条斜线上元素外，其他元素均为0。展开最后一列，将所得$n-1$阶行列式再展开即可得到递推公式：
$$D_n=aD_{n-1}-bcD_{n-2}$$

### 各行（列）元素和相等型
例如
$$\begin{vmatrix}1+x_1&x_1&\dots&x_1\\x_2&1+x_2&\dots&x_2\\\vdots&\vdots&&\vdots\\x_n&x_n&\dots&1+x_n\end{vmatrix}$$
$$\xlongequal[i=2,3,...,n]{r_1+r_i}\begin{vmatrix}1+\sum_{i=1}^nx_i&1+\sum_{i=1}^nx_i&\dots&1+\sum_{i=1}^nx_i\\x_2&1+x_2&\dots&x_2\\\vdots&\vdots&&\vdots\\x_n&x_n&\dots&x_n\end{vmatrix}$$
$$=(1+\sum_{i=1}^nx_i)\begin{vmatrix}1&1&\dots&1\\x_2&1+x_2&\dots&x_2\\\vdots&\vdots&&\vdots\\x_n&x_n&\dots&x_n\end{vmatrix}$$
$$=1+\sum_{i=1}^nx_i$$

### 相邻两行对应元素相差k倍型
:::info
  1. 大部分元素为数字，且相邻两行对应元素相差为1，采用逐步作差的方法，即可出现大量$\pm 1$元素，进而出现大量0元素

  2. 若相邻两行相差K倍，采用逐步作k倍差得方法，即可出现大量0元素

:::
例如
$$\begin{vmatrix}0&1&2&\dots&n-2&n-1\\1&0&1&\dots&n-3&n-2\\2&1&0&\dots&n-4&n-3\\\vdots&\vdots&\vdots&&\vdots&\vdots\\n-2&n-3&n-4&\dots&0&1\\n-1&n-2&n-3&\dots&1&0\end{vmatrix}$$
$$\xlongequal[i=1,2,...,n-1]{r_i-r_{i+1}}\begin{vmatrix}-1&1&1&\dots&1&1\\-1&-1&1&\dots&1&1\\-1&-1&-1&\dots&1&1\\\vdots&\vdots&\vdots&&\vdots&\vdots\\-1&-1&-1&\dots&-1&1\\n-1&n-2&n-3&\dots&1&0\end{vmatrix}$$
$$\xlongequal[i=2,...,n]{c_i+c_{1}}\begin{vmatrix}-1&0&0&\dots&0&0\\-1&-2&0&\dots&0&0\\-1&-2&-2&\dots&0&0\\\vdots&\vdots&\vdots&&\vdots&\vdots\\-1&-2&-2&\dots&-2&0\\n-1&2n-3&2n-4&\dots&n&n-1\end{vmatrix}$$
得
$$D_n=(-1)^{n-1}(-2)^{n-2}(n-1)$$
又例如
$$\begin{vmatrix}1&a&a^2&\dots&a^{n-2}&a^{n-1}\\a^{n-1}&1&a&\dots&a^{n-3}&a^{n-2}\\a^{n-2}&a^{n-1}&1&\dots&a^{n-4}&a^{n-3}\\\vdots&\vdots&\vdots&&\vdots&\vdots\\a^2&a^{3}&a^{4}&\dots&1&a\\a&a^2&a^{3}&\dots&a^{n-1}&1\\\end{vmatrix}$$
$$\xlongequal[i=1,2,...,n-1]{r_i-(-a)r_{i+1}}\begin{vmatrix}1-a^n&0&0&\dots&0&0\\0&1-a^n&0&\dots&0&0\\0&0&1-a^n&\dots&0&0\\\vdots&\vdots&\vdots&&\vdots&\vdots\\0&0&0&\dots&1-a^n&0\\a&a^2&a^{3}&\dots&a^{n-1}&1\\\end{vmatrix}$$
得
$$D_n=(1-a^n)^{n-1}$$













  ## 参考资料
  1. [3Blue1Brown - 线性代数的本质](https://www.bilibili.com/video/BV1ys411472E)
  2. [高等教育出版社 - 《线性代数（第六版）》](http://item.kongfz.com/book/38368122.html/)
  3. [中国人民大学出版社 - 《经济应用数学基础（二）线性代数（第五版）》](http://product.dangdang.com/1579041005.html)
  4. [八大类型行列式及其解法 by 超超超超超喜欢@知乎](https://zhuanlan.zhihu.com/p/34685081)