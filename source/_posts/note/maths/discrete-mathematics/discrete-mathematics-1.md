---
title: 数理逻辑
time: 2020-10-05 23:36:40
tags: [note,unfinished]
categories: [笔记,数学,离散数学]
math: true
quiz: true
---

## 命题逻辑的基本概念
### 命题与联结词
数理逻辑是研究推理的数学分支，推理由一系列的陈述句组成。非真即假的陈述句称作**命题**。例如：因为$3>2$，所以$3\not=2$。

作为命题的陈述句，它所表达的判断结果称作命题的**真值**。真值只取**真**或**假**。任何命题的真值都是唯一的。即：**“真值”不唯一的陈述句不是命题**。

上例中，命题“因为$3>2$，所以$3\not=2$”由两个更简单的命题“$3>2$”和“$3\not=2$”组成。前述两个命题不能再被分解为更简单的命题。这种命题被称为**简单命题**或**原子命题**，是命题的最小单位。由简单命题通过联结词联结而成的命题，称为**复合命题**。

判断给定句子是否为命题，首先应该判断它是否为**陈述句**，其次判断它是否有**唯一的真值**。
:::warning
此处是否有唯一的真值，重要的是真值的存在性和唯一性。即要存在真值，且真值唯一。至于真值你知不知道是多少，一点都不重要。
:::
1. “我正在说假话”这句陈述句是命题吗？如果是，是什么命题？[]{.gap} {.quiz}
    - 真命题
    - 假命题
    - 不是命题 {.correct}
{.options}
    > 这种由真能推出假，由假能推出真，于是不能为真，也不能为假的陈述句称为**悖论**。**悖论不是命题。**


我们一般使用小写英文字母表示命题，用1表示真，用0表示假。

例如：
$p$：$3>2$
$q$：$3\not=2$
它们称作这些命题的符号化。其中，$p$和$q$的真值均为1。

由于自然语言中出现的联结词有的具有二义性，我们在数理逻辑中必须给出联结词的严格定义，并将它们符号化。
+ 设$p$为命题（以下不再赘述），复合命题“非$p$”（或“$p$的否定”）称作$p$的否定式，记作$\lnot p$。符号$\lnot$称作否定联结词。只有这个是一元联结词。

+ 复合命题“$p$并且$q$”（或“$p$与$q$”）称为$p$与$q$的合取式，记作$p\land q$。符号$\land$称作合取联结词。

+ 复合命题“$p$或$q$”称为$p$与$q$的析取式，记作$p\lor q$。$\lor$称作析取联结词。

:::warning
“或”表达的可能是相容或（即||）或者排斥或（即^），在实际使用时注意鉴别。
:::

+ 复合命题“如果$p$，则$q$”称为$p$与$q$的蕴涵式，记作$p\to q$，并称$p$是蕴涵式的前件，$q$是蕴涵式的后件，$\to$称作蕴涵联结词。

:::warning
在自然语言中，前件$p$和后件$q$间往往具有某种内在联系，而数理逻辑是研究抽象的推理，$p$和$q$可以无任何内在联系。
:::

+ 复合命题“$p$当且仅当$q$”称作$p$与$q$的等价式，记作$p\leftrightarrow q$，$\leftrightarrow$记作等价联结词。

真值表如下：
|$p$|$q$|$\lnot q$|$p\land q$|$p\lor q$|$p\to q$|$p\leftrightarrow q$|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|0|0|1|0|0|1|1|
|0|1|1|0|1|1|0|
|1|0|0|0|1|0|0|
|1|1|0|1|1|1|1|
使用多个联结词可以组成更复杂的复合命题，此外还可以使用圆括号$()$。联结词的优先顺序为$()$，$\lnot$，$\land$，$\lor$，$\to$，$\leftrightarrow$。

### 命题公式及其赋值
简单命题是命题逻辑种最基本的研究单位，其真值是确定的，又称作**命题常项**或**命题常元**。相对的，取值不定（0/1）的变元称作**命题变项**或**命题变元**。

将命题变项通过联结词联结起来的符号串称作**合式公式**。也称作**命题公式**或**命题形式**，简称为**公式**。

我们一般用大写字母来表示公式，这称作**元语言符号**。某个具体的公式称作**对象语言符号**。对象语言指用来描述研究对象的语言，元语言指用来描述对象语言的语言。

若公式A是单个命题变项，则称A是0层公式。

$A=\lnot B$，若B是n层公式，则A是n+1层公式。

用联结词联结不同公式得到的公式的层次为这些公式中最大的那个公式的层次（类比多项式的次数）。

给某公式中出现的全部命题变项指定真值，称为对该公式的一个**赋值**或**解释**。若指定值使该公式为真，则称该组值为该公式的**成真赋值**，否则为**成假赋值**。

将某命题公式在所有赋值下的取值情况列成表，称为它的**真值表**。

## 命题逻辑等值演算
### 等值式
设A，B是两个命题公式。若A，B构成的等价式$A\leftrightarrow B$为重言式，则称A与B是等值的，记作$A\iff B。注意该符号不是联结词，而是元语言符号。

常用的等值式模式如下：
|名称|公式|
|:-:|:-:|
|双重否定律|$$A\iff\lnot\lnot A$$|
|幂等律|$$\begin{aligned}A\iff A \lor A \\ A\iff A\land A\end{aligned}$$|
|交换律|$$\begin{aligned}A\lor B\iff B\lor A \\ A\land B\iff B\land A\end{aligned}$$|
|结合律|$$\begin{aligned}(A\lor B)\lor C\iff A\lor(B\lor C)\\ (A\land B)\land C\iff A\land(B\land C)\end{aligned}$$|
|分配律|$$\begin{aligned}A\lor(B\land C)\iff(A\lor B)\land(A\lor C)\\ A\land(B\lor C)\iff(A\land B)\lor(A\land C)\end{aligned}$$|
|德摩根律|$$\lnot(A\lor B)\iff\lnot A\land\lnot B$$|
|吸收律|$$\begin{aligned}A\lor(A\land B)\iff A\\ A\land(A\lor B)\iff A \end{aligned}$$|
|零律|$$\begin{aligned}A\lor 1\iff 1\\ A\land 0\iff 0\end{aligned}$$|
|同一律|$$\begin{aligned}A\lor 0\iff A\\ A\land 1\iff A\end{aligned}$$|
|排中律|$$A\lor\lnot A\iff 1$$|
|矛盾律|$$A\land\lnot A\iff 0$$|
|蕴涵等值式|$$A\to B\iff\lnot A\lor B$$|
|等价等值式|$$A\leftrightarrow B\iff(A\to B)\land(B\to A)$$|
|假言易位|$$A\to B\iff\lnot B\to\lnot A$$|
|等价否定等值式|$$A\leftrightarrow B\iff\lnot A\leftrightarrow\lnot B$$|
|归谬论|$$(A\to B)\land(A\to\lnot B)\iff\lnot A$$|

由已知等值式推出另外一些等值式的过程称为**等值演算**。它是布尔代数或逻辑代数的重要组成部分。

### 析取范式与合取范式
命题公式有两种规范表示方法，即**析取范式**与**合取范式**。这两种方法可以互相转化，能表达真值表所能提供的一切信息。

此处，我们将命题变项及其否定统称为**文字**。仅由有限个文字构成的析取式称为**简单析取式**。仅由有限个文字构成的合取式称为**简单合取式**。
:::warning
一个文字既是简单析取式，又是简单合取式。
:::
placeholder













## 参考资料
1. [高等教育出版社 - 离散数学（第二版）](http://www.hep.edu.cn/book/details?uuid=92edf222-14a4-1000-973c-3fafc67de19c)