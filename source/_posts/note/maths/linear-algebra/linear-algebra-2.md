---
title: 矩阵
time: 2020-10-13 18:36:40
tags: [note,unfinished]
categories: [笔记,数学,线性代数]
math: true
---
## 线性变换和矩阵
### 线性方程组
$$\begin{cases}a_{11}x_1&+&a_{12}x_2+...+a_{1n}x_n&=&b_1\\a_{21}x_1&+&a_{22}x_2+...+a_{2n}x_n&=&b_2\\&...&...\\a_{m1}x_1&+&a_{m2}x_2+...+a_{mn}x_n&=&b_m\end{cases}$$
形如上述方程组的方程组是线性方程组。当常数项$b_1,b_2,...b_m$全部等于0时，上述线性方程组为**n元非齐次线性方程组**。当常数项均为0时，该式为**n元齐次线性方程组**。

对于线性方程组，我们需要讨论：
1. 它是否有解？
2. 在有解时该解是否唯一？
3. 如果有多个解，如何求出它的所有解？

需要注意的是，对于线性方程组，上述三个问题的答案完全取决于其式中的$m*n$个系数和右端的常数项$b_1,b_2,...b_m$。或者说，完全取决于它们构成的矩形数表:

$$\begin{matrix}a_{11}&a_{12}&...&a_{1n}&b_{1}\\a_{21}&a_{22}&...&a_{2n}&b_{2}\\\vdots&\vdots&&\vdots\\a_{m1}&a_{m2}&...&a_{mn}&b_{m}\end{matrix}$$
另外，对于**齐次**线性方程组，相应问题的答案完全取决于：
$$\begin{matrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\\vdots&\vdots&&\vdots\\a_{m1}&a_{m2}&...&a_{mn}\end{matrix}$$

### 矩阵
$$\bold{A}=\begin{pmatrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\\vdots&\vdots&&\vdots\\a_{m1}&a_{m2}&...&a_{mn}\end{pmatrix}$$
+ 如上由$m*n$个数排成的$m$行$n$列的数表称为$m$行$n$列矩阵（$m*n$矩阵）。
+ 这$m*n$个数称为矩阵$\bold{A}$的元素（元），数$a_{ij}$位于$A$的第$i$行第$j$列，称为矩阵$\bold{A}$的$(i,j)$元。以数$a_{ij}$为$(i,j)$元的矩阵可简记为$(a_{ij})$或$(a_{ij})_{max}$，$m*n$矩阵$\bold{A}$也记作$\bold{A}_{m*n}$。
+ 元素是实数/复数的矩阵称为实矩阵/复矩阵。
+ 行数和列数都等于n的矩阵称为$n$阶矩阵或$n$阶方阵。$n$阶矩阵$\bold{A}$也记作$\bold{A}_{n}$。
+ 只有一行的矩阵称作行矩阵（行向量）。为了避免元素间的混淆，行矩阵在表示时可以**在元素间加逗号**。类似地，只有一列的矩阵称作列矩阵（列向量）。
+ 两个矩阵的行数、列数均相等时，就称他们是同型矩阵；如果两矩阵既是同型矩阵，对应位置上的元素又相等，则这两个矩阵相等。
+ 元素都是零的矩阵称为零矩阵，记作$\bold{O}$。
    :::warning
    不同型的零矩阵是不同的。
    :::
+ 除对角线外的元素均是0。这种矩阵叫做对角（矩）阵，也记作$\bold\Lambda=diag(\lambda_1,\lambda_2,...,\lambda_n)$
+ 除对角线外的元素均是0，且对角线上的元素均是1。这样的方阵叫做**单位矩阵**，记作$\bold{E}$。任何矩阵与单位矩阵相乘，等于其自身。

### 线性变换
如$n$个变量$x_1,x_2,...,x_n$与$m$个变量$y_1,y_2,...,y_m$之间的关系式：
$$\begin{cases}a_{11}x_1&+&a_{12}x_2+...+a_{1n}x_n&=&b_1\\a_{21}x_1&+&a_{22}x_2+...+a_{2n}x_n&=&b_2\\&...&...\\a_{m1}x_1&+&a_{m2}x_2+...+a_{mn}x_n&=&b_m\end{cases}$$
表示的是一个从变量$x_1,x_2,...,x_n$到$y_1,y_2,...,y_m$的线性变换。为了便于表示和理解，使用矩阵进行表示：
$$\underbrace{\begin{pmatrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\\vdots&\vdots&&\vdots\\a_{m1}&a_{m2}&...&a_{mn}\end{pmatrix}}_{\text{线性变换}}\underbrace{\begin{pmatrix}x_1\\x_2\\\vdots\\x_n\end{pmatrix}}_{\text{输入向量}}=\underbrace{\begin{pmatrix}y_1\\y_2\\\vdots\\y_m\end{pmatrix}}_{\text{输出向量}}$$
此处显然使用了矩阵相乘来计算$y_1,y_2,...,y_m$的值。但理解该式的意义并不需要会计算它。但为了方便理解，在这里提出：**矩阵相乘需要左侧矩阵的列数等于右侧矩阵的行数**。

为了便于理解，我们需要先回忆一下高中学习的向量知识：
+ 一个二维向量能够被表示为坐标，是因为它可以在向量空间中被表示为基向量$\hat{i}=\begin{pmatrix}1\\0\end{pmatrix},\hat{j}=\begin{pmatrix}0\\1\end{pmatrix}$的和（$n$维向量同理）。由此，我们为了方便，将向量的一端固定在原点，记录向量另一端的坐标，即可表示相应的向量。
:::info
向量空间就是向量构成的空间。要说样子的话一般表示得和一般的空间挺像的。理解起来其实也差不多，学校里学过的话，把你对画着向量的平面图的理解搬过来就行。
:::

而线性变换即是对基向量的操作。它通过变换基向量变换整个空间。

使用单位矩阵进行举例：
$$\begin{pmatrix}1&0\\0&1\end{pmatrix}$$
使用分块法将矩阵分为两列：
$$\bold{E}=\begin{pmatrix}1&0\\0&1\end{pmatrix}=\begin{pmatrix}\hat{i}&\hat{j}\end{pmatrix}$$
其中$\hat{i}=\begin{pmatrix}1\\0\end{pmatrix},\hat{j}=\begin{pmatrix}0\\1\end{pmatrix}$。
则有：
$$\bold{E}\begin{pmatrix}2\\3\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}\begin{pmatrix}2\\3\end{pmatrix}=\begin{pmatrix}\hat{i}&\hat{j}\end{pmatrix}\begin{pmatrix}2\\3\end{pmatrix}=\begin{pmatrix}2\hat{i}+3\hat{j}\end{pmatrix}=\begin{pmatrix}2\begin{pmatrix}1\\0\end{pmatrix}+3\begin{pmatrix}0\\1\end{pmatrix}\end{pmatrix}=\begin{pmatrix}2\\3\end{pmatrix}$$
为了推广到任意二阶矩阵，使用二阶方阵：
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}$$
该矩阵作为线性变换的几何意义是将基向量$\hat{i}=\begin{pmatrix}1\\0\end{pmatrix}$和$\hat{j}=\begin{pmatrix}0\\1\end{pmatrix}$拉伸或压缩（也可简单理解为“替换”）为$\hat{i}=\begin{pmatrix}a\\c\end{pmatrix},\hat{j}=\begin{pmatrix}b\\d\end{pmatrix}$。因为空间（此处为平面）基于基向量展开，所以空间会被拉伸或压缩。在向量被输入到线性变换时：
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}\begin{pmatrix}2\\3\end{pmatrix}=\begin{pmatrix}2a+3b\\2c+3d\end{pmatrix}$$
输出向量为经过该线性变换后输入向量在$\hat{i}=\begin{pmatrix}1\\0\end{pmatrix}$和$\hat{j}=\begin{pmatrix}0\\1\end{pmatrix}$的空间下的向量。


三阶矩阵同理：显然，其表示一个三维空间的线性变换。实际上其和二维空间大同小异，只是多了一个基向量$\hat{k}=\begin{pmatrix}0\\0\\1\end{pmatrix}$。

类似的，更高阶的线性变换也可以通过该过程理解（只不过无法给出直观的几何解释）。
#### 与行列式的联系
##### 行列式不等于0
线性变换拉伸或压缩空间。显然，单位面积的大小发生了改变。此时，行列式的值就等于单位面积大小变化的倍率。有兴趣的可以在纸上画一下自己写出二维的情况（三维太难画了，算了吧）。

值得注意的是，行列式的值可以是负值，但我们平常提到体积和面积等单位的时候不存在负值。为了区别负值的情况，我们引入**有向面积**和**有向体积**这种概念。当$\hat{i}$和$\hat{j}$围成的平行四边形在$\hat{j}$以原点为中心的顺时针方向时，行列式为正；反之则为负。

类似地，在三维空间中，我们规定：如果变换后的平行六面体不再符合右手定则，则行列式为负。
:::info
右手定则：食指指向$\hat{i}$，中指指向$\hat{j}$，拇指指向$\hat{k}$。
:::
##### 行列式等于0
行列式等于0，代表该矩阵表示的线性变换将体积/面积挤压到没有了。例如：三维空间被挤压为一个平面，一条直线，甚至一个点。

#### 非方阵表示的线性变换
虽然非方阵不存在行列式，但它们也可以表示线性变换。此时，它们表示不同维数之间的转换。
:::info
显然，此时的面积/体积变换倍率要么等于0，要么就不存在。
:::
例如：
$$\begin{pmatrix}1&5&2\end{pmatrix}$$
这个线性变换接收三维空间的向量，将其映射到一条数轴上：
$$\begin{pmatrix}1&5&2\end{pmatrix}\begin{pmatrix}1\\2\\3\end{pmatrix}=17$$ 
又例如：
$$\begin{pmatrix}1&0&0\\2&5&6\end{pmatrix}$$
这个线性变换同样接收三维空间向量，但将其映射到二维空间上：
$$\begin{pmatrix}1&0&0\\2&5&6\end{pmatrix}\begin{pmatrix}1\\2\\3\end{pmatrix}=\begin{pmatrix}1\\30\end{pmatrix}$$ 
又例如：
$$\begin{pmatrix}1&2\\2&3\\3&4\end{pmatrix}$$
这个线性变换接收二维空间向量，但将其映射到三维空间上：
$$\begin{pmatrix}1&2\\2&3\\3&4\end{pmatrix}\begin{pmatrix}1\\2\end{pmatrix}=\begin{pmatrix}5\\8\\11\end{pmatrix}$$

#### 复合线性变换
线性变换可以复合。复合的方式就是矩阵相乘。

由于**矩阵相乘不满足交换律**，我们需要将先发生的变换写在右侧，将先发生的变换作为输入向量输入后发生的线性变换里。

在前面说明时已经用过[**使用分块法将线性变换拆成基向量**](#线性变换)的方法。在此，我们就是将线性变换拆成其代表的基向量后，分别代入后一线性变换的变换，从而得到复合的线性变换。例如：
$$\begin{pmatrix}1&6\\2&6\\3&6\end{pmatrix}\begin{pmatrix}1&8&2\\2&8&1\end{pmatrix}$$
其中，第一个线性变换（右侧）接收三维向量，将其映射到二维空间；第二个线性变换（左侧）接收二维向量，将其映射到三维空间。所以，它们的复合应该是一个三维到三维的线性变换，即应该是一个3*3的矩阵，即：
$$\begin{pmatrix}1&6\\2&6\\3&6\end{pmatrix}\begin{pmatrix}1&8&2\\2&8&1\end{pmatrix}=\begin{pmatrix}13&56&8\\14&64&10\\15&72&12\end{pmatrix}$$

:::warning
显然，不能相乘的两矩阵所代表的两线性变换不能复合。
:::

## 矩阵的运算
### 加法
设有两个$m*n$矩阵$\bold{A}=(a_{ij})$和$\bold{B}=(b_{ij})$，那么这两个矩阵的和记为$\bold{A+B}$，规定为：
$$\bold{A+B}=\begin{pmatrix}a_{11}+b_{11}&a_{12}+b_{12}&...&a_{1n}+b_{1n}\\a_{21}+b_{21}&a_{22}+b_{22}&...&a_{2n}+b_{2n}\\\vdots&\vdots&&\vdots\\a_{m1}+b_{m1}&a_{m2}+b_{m2}&...&a_{mn}+b_{mn}\end{pmatrix}$$
即相应位置元素相加。显然，类型不同的矩阵不能相加。

矩阵加法满足交换律和结合律，即 $A+B=B+A,A+(B+C)=(A+B)+C$ 。

### 数乘
矩阵数乘，即矩阵和数相乘。我们将数$\lambda$和矩阵A的乘积记作$\lambda\bold{A}$或$\bold{A}\lambda$，规定为：
$$\lambda\bold{A}=\bold{A}\lambda=\begin{pmatrix}\lambda a_{11}&\lambda a_{12}&...&\lambda a_{1n}\\\lambda a_{21}&\lambda a_{22}&...&\lambda a_{2n}\\\vdots&\vdots&&\vdots\\\lambda a_{m1}&\lambda a_{m2}&...&\lambda a_{mn}\end{pmatrix}$$

### 矩阵与矩阵相乘
#### 定义
假设有两个线性变换：
$$\underbrace{\begin{pmatrix}a_{11}&a_{12}&...&a_{1n}\\a_{21}&a_{22}&...&a_{2n}\\\vdots&\vdots&&\vdots\\a_{m1}&a_{m2}&...&a_{mn}\end{pmatrix}}_{\text{线性变换}}\underbrace{\begin{pmatrix}b_{11}&b_{12}&...&b_{1p}\\b_{21}&b_{22}&...&b_{2p}\\\vdots&\vdots&&\vdots\\b_{n1}&b_{n2}&...&b_{np}\end{pmatrix}}_{\text{线性变换}}=\underbrace{\begin{pmatrix}c_{11}&c_{12}&...&c_{1p}\\c_{21}&c_{22}&...&c_{2p}\\\vdots&\vdots&&\vdots\\c_{m1}&c_{m2}&...&c_{mp}\end{pmatrix}}_{\text{线性变换}}$$
其中， $c_{ij}$是A的第i行和B的第j列的乘积。
例如：
$$\begin{pmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\\a_{31}&a_{32}\end{pmatrix}\begin{pmatrix}b_{11}&b_{12}&b_{13}\\b_{21}&b_{22}&b_{23}\end{pmatrix}=
\begin{pmatrix}
a_{11}b_{11}+a_{12}b_{21}&a_{11}b_{12}+a_{12}b_{22}&a_{11}b_{13}+a_{12}b_{23}\\
a_{21}b_{11}+a_{22}b_{21}&a_{21}b_{12}+a_{22}b_{22}&a_{21}b_{13}+a_{22}b_{23}\\
a_{31}b_{11}+a_{32}b_{21}&a_{31}b_{12}+a_{32}b_{22}&a_{31}b_{13}+a_{32}b_{23}
\end{pmatrix}$$
:::warning
只有当左矩阵的**列数**等于右矩阵的**行数**时，两个矩阵才能相乘。
:::

#### 性质
显然， $AB$ 有意义并不代表 $BA$ 有意义，且 $AB$ 一般情况下不等于 $BA$ ，即矩阵乘法**不满足交换律**。
对于两个方阵$A,B$，如果 $AB=BA$ ，称这两个方阵是可交换的。
另外，矩阵乘法也**不满足消去律**，即： $AB=O$ 不能推出 $A=O$ 或 $B=O$ 。

但矩阵乘法满足**结合律**和**分配律**。

:::info
特别地： $\lambda E$ 在乘法的效果上等价于 $\lambda$ （常数），所以可以和所有同阶方阵交换。
:::

#### 幂
矩阵的幂类似实数的幂。

要注意的是由于矩阵乘法一般来说不满足交换律，所以两个矩阵的乘积的幂不能随意像两个实数一样合并同类项。

### 转置
矩阵的转置满足
$$(A^T)^T=A\tag{i}$$
$$(A+B)^T=A^T+B^T\tag{ii}$$
$$(\lambda A)^T=\lambda A^T\tag{iii}$$
$$(AB)^T=B^TA^T\tag{iv}$$

如果有 $A^T=A$ ，则称A是对称矩阵。其特点是，元素以对角线为对称轴对应相等。

### 方阵的行列式
如另一篇文章行列式。需要注意的是，方阵是一个数表；而行列式是这些数按照一定的运算规则计算得到的一个数。有：
$$|\lambda A|=\lambda^n|A|\tag{i}$$
$$|AB|=|A||B|\tag{ii}$$
利用性质$(ii)$我们可以推知：
$$|AB|=|BA|$$
#### 伴随矩阵
利用行列式，我们定义矩阵A的伴随矩阵：
$$A^*=\begin{pmatrix}
A_{11}&A_{21}&\dots&A_{n1}\\
A_{12}&A_{22}&\dots&A_{n2}\\
\vdots&\vdots&&\vdots\\
A_{1n}&A_{2n}&\dots&A_{nn}\\
\end{pmatrix}$$
其中$A_{ij}$是A中对应元素的代数余子式。
:::warning
注意伴随矩阵的元素和其原本的位置。
如果直接将某元素的代数余子式的值填入该元素的位置，那么在最后需要进行**转置**，才能得到伴随矩阵。
:::
##### 伴随矩阵的性质
伴随矩阵有性质$AA^*=A^*A=|A|E$。
可以通过计算证明（只有代数余子式乘上其对应元素，然后求和才是A的行列式；乘上别的行/列得到的结果是0）。
详见展开为含代数余子式的多项式。

## 逆矩阵
从定义上来说，矩阵A的逆矩阵是和A相乘等于E的矩阵。显然，只有方阵有逆矩阵。另外，逆矩阵如果存在，显然唯一。

从前述的行列式运算法则来看，有：
$$|AA^{-1}|=|A^{-1}A|=|E|=1\tag{1}$$
显然，可逆矩阵A的行列式不为0。

### 通过伴随矩阵求逆
由于伴随矩阵有性质$AA^*=A^*A=|A|E$，只要$|A|$不等于0，就可以将原式变为
$$A^{-1}=\frac{1}{|A|}A^*\tag{2}$$
当矩阵行列式等于0时，矩阵称为奇异矩阵，否则称为非奇异矩阵。

由上述(1)(2)两式可以得得知某矩阵可逆的充要条件是其行列式不等于0，即其是非奇异矩阵。

### 逆矩阵满足的运算规律
1. 若A可逆，则它的逆矩阵也可逆，且
$$(A^{-1})^{-1}=A$$
2. 若A可逆，数$\lambda\neq 0$，则$\lambda A$可逆，且
$$(\lambda A)^{-1}=\frac{1}{\lambda}A^{-1}$$
3. 若A、B同阶且均可逆，则AB也可逆，且
$$(AB)^{-1}=B^{-1}A^{-1}$$
4. 若A可逆，则$A^T$也可逆，且
$$(A^T)^{-1}=(A^{-1})^T$$

当A可逆，可以定义 $A^0=E, A^{-k}=(A^{-1})^k$ ，其中k为正整数。
添加这些定义后，逆矩阵同样满足矩阵的幂的运算法则。

### 可逆矩阵应用
可逆矩阵和自身的幂是可交换的。所以可逆矩阵的多项式也是可交换的。于是同一个可逆矩阵的多项式可以像数一样分解因式，相乘等。
在相似变换中，通过相似变换将一个方阵变换为一个对角阵，以快速计算方阵的幂。
另外，对角阵的多项式还是对角阵。

## 克拉默法则
$$\begin{cases}a_{11}x_1&+&a_{12}x_2+...+a_{1n}x_n&=&b_1\\a_{21}x_1&+&a_{22}x_2+...+a_{2n}x_n&=&b_2\\&...&...\\a_{m1}x_1&+&a_{m2}x_2+...+a_{mn}x_n&=&b_m\end{cases}$$
上述含有n个未知数的n个线性方程的线性方程组，它的解可以用n阶行列式表示。
### 定义
如果线性方程组的系数矩阵A的行列式不等于0，那么方程组有唯一解：
$$x_k=\frac{|A_k|}{|A|}, k=1,2,\dots,n$$
其中$A_k$是将系数矩阵A中第k列的元素用b（右侧常数项）替换后得到的n阶矩阵，即
$$A=\begin{pmatrix}
a_{11}&\dots&a_{1,k-1}&b_1&a_{1,k+1}&\dots&a_{1n}\\
\vdots&&\vdots&\vdots&\vdots&&\vdots\\
a_{n1}&\dots&a_{n,k-1}&b_n&a_{n,k+1}&\dots&a_{nn}
\end{pmatrix}$$
### 证明
可以通过逆矩阵证明。将通过伴随矩阵求逆矩阵的公式代入，化简后展开即可。

该法则是行列式的应用，其证明是逆矩阵的应用。它解决的是方程个数和未知数个数相等并且系数行列式不等于0的线性方程组。

## 矩阵分块法
placeholder


