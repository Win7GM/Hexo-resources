---
title: 0.数据结构前置
time: 2020-10-11 22:36:40
tags: [note,unfinished]
categories: [笔记,计算机科学,数据结构]
---
## 前置知识
### 指针、引用和取地址
指针在数据结构中非常常用。它可以简化某些编程任务的执行，另外还有一些任务，如动态内存分配，没有指针是无法执行的。

#### 指针
指针是一个变量，占4个字节。它存放的是一个内存地址。一般来讲，是另一个变量的内存地址。
:::info
实际上，指针存放的是另外一个变量在内存中的存储位置的首地址。
因为变量类型不同所占的内存大小不同，指针实际上必须记录它所指向的内存处存放的变量的类型，以在使用指针时避免破坏数据。
另外，你可以使用指向指针的指针。用法和指向普通变量的指针类似。
:::

像其他变量一样，在使用指针之前必须进行声明：
```cpp
type *var-name;
```
在这里，`type`是指针指向的地址存放的变量的类型，它必须是一个有效的C++数据类型；`var-name`是指针变量的名称。`*`在此处用于声明这是一个指针变量。

为了通过指针操作其指向的内存，需要使用`*`运算符，例如：
```cpp
int a;
int* ptr = &a;
*ptr = 10; //修改a的值
```
这个过程被称为解引用。

##### NULL
如果你暂时不想给一个指针赋值，你可以给它赋上NULL。在头文件中，有`#define NULL 0`。所以，被赋值为`NULL`的指针实际上不指向任何地址；另外，在判断中NULL会被判断成`false`。

因此，如果所有未使用的指针都被赋予空值，同时避免使用空指针，就可以防止误用一个未初始化的指针。很多时候，未初始化的变量存有一些垃圾值，导致程序难以调试。

##### 作为参数
使用中，只需简单将函数参数声明为指针即可。例如：
```cpp
void getSeconds(unsigned long* par)
{
    *par = time(NULL);
    return;
}
```
在运行时，上例函数会创造一个值和类型等于输入的参数指针的指针作为局部变量使用。

##### 作为返回值
可以在声明函数的时候声明函数的返回值为指针类型。例如：
```cpp
int* fun()
{
    static int a = 0;
    return &a;
}
```
该函数在函数内声明了一个静态局部变量`a`，返回值为指向a的地址的指针。
:::warning
如果该局部变量不是`static`（静态）变量，则不能返回它：非静态的局部变量会在函数执行完毕后被释放。
静态局部变量的生存期和全局变量相同，是整个源程序。在声明静态局部变量时，如果没有为之赋值，系统会自动赋值它为`0`。另外，它只能在声明它的函数内被调用。
:::

#### 取地址
为了给一个指针变量赋值，我们需要取得另外一个变量的地址。
通过在变量前附加`&`运算符，我们可以获取该变量当前的内存地址，当它被放在赋值表达式的右边时，它可以被赋值给表达式左边的变量。如：
```cpp
int *ptr;
int var;
ptr = &var; //在指针ptr之中存储变量var的地址
```
由此，我们可以对指针变量进行赋值。像其他变量一样，我们也可以在声明指针变量的同时初始化它：
```cpp
int var;
int *ptr = &var;
```
:::warning
未初始化的指针变量指向随机地址，在使用前一定要初始化，否则可能导致异常。

另外，指针指向不属于程序的内存的时候有：在指向`malloc()`申请的内存后`free()`掉了申请的内存、指针未初始化、指向数组时超限访问等。我们要避免类似的使用指针的错误。
:::

#### 引用
引用实际上是一种别名。

引用和指针类似。它们之间有三个主要的不同：
+ 不存在空引用。引用在初始化时就必须指向一块合法的内存，即必须指向一个已经存在的变量。
+ 一旦引用被初始化未一个对象，就不能被指向另一个对象。指针可以在任何时候被指向另一个对象。
+ 引用必须在创建时被初始化。指针可以在任何时候被初始化。

在实际编程中，我们依然要在使用引用前声明（并初始化）它：
```cpp
int& r = i;
double& s = d;
```
此处的`&`标识`r`，`s`是引用。

##### 作为参数
例如：
```cpp
void swap(int& x, int& y)
{
   int temp;
   temp = x; /* 保存地址 x 的值 */
   x = y;    /* 把 y 赋值给 x */
   y = temp; /* 把 x 赋值给 y  */
  
   return;
}
```
如此，函数操作的变量`x`和`y`实际上就是传入的参数本身。即没有在函数中创造一个临时变量，而直接操作外层函数中的变量本身。

##### 作为返回值
函数可以返回一个引用。这样，函数就可以放在赋值语句的左边。例如：
```cpp
#include <iostream>
using namespace std;
 
double vals[] = {10.1, 12.6, 33.1, 24.1, 50.0};
 
double& setValues( int i )
{
  return vals[i];   // 返回第 i 个元素的引用
}
 
// 要调用上面定义函数的主函数
int main ()
{
 
   cout << "改变前的值" << endl;
   for ( int i = 0; i < 5; i++ )
   {
       cout << "vals[" << i << "] = ";
       cout << vals[i] << endl;
   }
 
   setValues(1) = 20.23; // 改变第 2 个元素
   setValues(3) = 70.8;  // 改变第 4 个元素
 
   cout << "改变后的值" << endl;
   for ( int i = 0; i < 5; i++ )
   {
       cout << "vals[" << i << "] = ";
       cout << vals[i] << endl;
   }
   return 0;
}
```
返回的引用需要是对外部变量的引用。返回对非静态局部变量的引用会导致错误：非静态局部变量在函数执行结束后会被释放。

### 结构体
| |C|C++|
|:-:|:-:|:-:|
|成员函数|不能（可以使用函数指针）|可以|
|静态成员|不能|可以|
|属性|默认public，不能修改|public/private/protected|
#### 声明
```cpp
struct Angel
{
    int age;
    char[] name;
} //在此处填写变量名可以声明结构体成员
```
上述是标准的结构体声明。该结构体名称为Angel，在C++中声明变量如下：
```cpp
Angel Aiwass;
```
但在C中，使用如上结构体声明在声明结构体变量时，要在结构体名前加上struct，如下：
```c
struct Angel Aiwass;
```
若想去掉struct，需要使用typedef：
```c
typedef struct [struct-name]
{
    int age;
    char[] name;
}Angel;
```
此处括号内struct-name选填。但如果结构体内部成员有它自身，则必填。例如：
```c
typedef struct LNode //结构体名
{
    ElemType data;
    LNode* next;
}LinkNode; //别名
```
#### 使用
在访问结构体变量时，使用`.`运算符对其成员进行操作；通过指针访问结构体时，使用`->`运算符对其成员进行操作，例如：
```cpp
LinkNode a;
func(a.data);

LinkNode* L;
func(L->data);
```
如上例，通过`->`可以直接操作成员，不需要对指针进行解引用。
在输出时，不能整个结构体一起输出，只能一个成员一个成员进行输出。












## 参考资料
1. [菜鸟教程](runoob.com)