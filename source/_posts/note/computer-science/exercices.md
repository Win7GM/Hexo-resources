---
title: 编程练习题
time: 2020-10-07 11:36:40
tags: [note,unfinished]
categories: [笔记,计算机科学]
math: true
---

1. 指定一个区间`[x,y]`，在一个存有`n`个整数的顺序表中删除处于该区间之中的数。要求时间复杂度小于`O(n^2)`。
    + 可以使用[划分](https://blog.msforever.xyz/note/computer-science/data-structure/data-structures-1/#%E4%BE%8B2)的算法来进行删除。
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
    + 也可以直接使用[删除](https://blog.msforever.xyz/note/computer-science/data-structure/data-structures-1/#%E4%BE%8B1)的算法。