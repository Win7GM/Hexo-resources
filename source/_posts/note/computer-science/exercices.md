---
title: 编程练习题
time: 2020-10-07 11:36:40
tags: [note,unfinished]
categories: [笔记,计算机科学]
math: true
---

1. 指定一个区间`[x,y]`，在一个存有`n`个整数的顺序表中删除处于该区间之中的数。要求时间复杂度小于`O(n^2)`。
    ;;;id1 划分
     可以使用[划分](https://blog.msforever.xyz/note/computer-science/data-structure/data-structures-1/#%E4%BE%8B2)的算法来进行判断并删除。
    代码如：
    ```cpp
    void fun(SqList *L, int x, int y)
    {
        int i = 0, j = L->length - 1;
        while (i < j)
        {
            // while (i < j)
            // {
            //     if (L->data[i] >= x && L->data[i] <= y)
            //     {
            //         break;
            //     }
            //     else
            //     {
            //         i++;
            //     }
            // } //和下面的while等价
            while (i < j && (L->data[i] < x || L->data[i] > y))
            {
                i++; //i从左向右扫描，遇到在[x,y]区间的数停下
            }

            // while (i < j)
            // {
            //     if (L->data[j] < x || L->data[j] > y)
            //     {
            //         break;
            //     }
            //     else
            //     {
            //         j--;
            //     }
            // } //和下面的while等价

            while (i < j && L->data[j] >= x && L->data[j] <= y)
            {
                j--; //j从右向左扫描，遇到不在[x,y]区间的数停下
            }

            swap(*&(L->data[i]), *&(L->data[j]));
        }
        L->length = i;//i扫描过的数均为不在[x,y]区间的数
    }
    ```
    ;;;
    
    ;;;id1 删除
    也可以直接使用[删除](https://blog.msforever.xyz/note/computer-science/data-structure/data-structures-1/#%E4%BE%8B1)的算法。
    ;;;

2. 给定一个正整数，求和是该正整数的正整数序列。例如：6=1+2+3。
    ;;;id2 暴力遍历
    ```cpp
    void fun(int n)
    {
        int a = 0;
        int *s = &a; //用于取出循环计算结果
        int flag = 0;
        for (int i = n / 2; i > 0; i--) //从n/2开始i向下遍历
        {
            for (int c = i, sum = 0; sum < n; ++c) //从i开始c向n遍历，一旦sum大于n则跳出循环
            {
                sum = sum + c;
                *s = sum;
            }
            if (*s == n)
            {
                for (int j = i, sum = 0; sum != *s; j++) //输出正整数序列
                {
                    cout << j << "+";
                    sum = sum + j;
                }
                cout <<char(8) <<"=" << *s << endl;//ASCII中8是backspace，用于删除循环输出的多余的加号，*s输出计算结果，即n
                *s = 0;
                flag += 1;
            }
        }
        if (flag == 0)
        {
         cout << "找不到" << endl;
        }
    }
    ```
    ;;;
    ;;;id2 等差数列求和公式
    由题目可知只要有输出，输出一定是等差数列，且和为$n$。所以，考虑等差数列求和公式
    $$S_n=na_1+\dfrac{n(n-1)}{2}d$$
    由题，$S_n$为用户输入，$d=1$；$a_1,n\in \N^+$。所以，可以将原式转化为含$S_n,n$的不等式，即
    $$\dfrac{S_n}{n}-\dfrac{n-1}{2}=a_1\geq 1\space\space\space (1)$$
    配方可得$n$有上界，即
    $$n\leq \sqrt{2S_n+\dfrac{1}{4}}-\dfrac{1}{2}$$
    由此得到$n$的遍历范围。将$n$向下取整后在式（1）中按此范围遍历，验证求得的$a_1$是否是整数。若是，则直接按$a_1$和当前的$n$进行输出后继续循环；若否，则直接继续循环。
    如此，算法复杂度为$\sqrt{n}$。
    代码如下：
    ```cpp
    void fun(int m)
    {
        int n = 0,start = 0,end = 0,flag = 0;
        double temp = 0.0;
        for (n = sqrt(2.0 * double(m) + 0.25) - 0.5; n > 1; --n) 
        {
            temp = double(m) / n - double(n - 1) * 0.5f;
            if (temp == int(temp))
            {
                for (flag = 1,start = int(temp),end = start + n; start < end; start++)
                {
                    cout << start << '+';
                }
                cout << char(8) << endl;
            }
        }
        if (flag == 0)
        {
            cout << "None." << endl;
        }
    }
    ```