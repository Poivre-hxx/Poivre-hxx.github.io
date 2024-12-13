---
title: 21天学习c++_part1 笔记 
tags: 
  - Notes
  - c++
categories: 
  - [Tutorials, Book]
date: 2024-09-20 20:20:00
---

我要成为c++糕手！第一部分--基础知识

<!-- more -->

## chapter3 使用变量和常量

#### 1. 关于命名的约定：

- 帕斯卡命名法：每个单词的首字母都为大写
- 驼峰命名法：第一个单词的首字母采用小写
- 对于**变量名**，采用驼峰命名法；对于**函数名等其他元素**，采用帕斯卡命名法。

#### 2. 使用列表初始化避免缩窄转换错误

为避免在类型转换时出现缩窄转换错误，可以使用**列表初始化**的方法：将用于初始化的变量或值放在花括号内。

这样的作用是在编译时就会报错，而不是稀里糊涂地在程序运行时出现bug。

```c++
int largeNum = 400000;
short anotherNum{largeNum};
```



#### 3. 使用auto自动判断类型

借助关键字auto不显式地指定变量的类型。（使用auto时必须对变量进行初始化！！！）

#### 4. 常量的表现形式

- 字面常量

- const声明的常量

- constexpr声明的常量表达式

  可以对**同样声明为常量表达式的变量**赋值**（在编译期）**，而使用const时只能直接对常量赋值。

  而当赋值时使用变量的话，就会导致这个结果在程序运行时计算。

  - consteval是对consexpr的升级，如果传入的参数是变量，就会无法通过编译环节！

  ```c++
  constexpr double Div_expr(double a, double b)
  {
      return a / b;
  }
  constexpr double pi = Div_expr(22, 7);
  ```

- enum声明的枚举常量

  可以使用枚举指定变量的类型，这样声明的变量只能取指定的值。

  起始值默认为0，如果有初始化，将从初始化值开始计数。

  - 非域限定枚举 & 域限定枚举

    ```c++
    // 非域限定枚举
    // 编译器允许将这种类型的变量转换为整数
    enum CardinalDirections
    {
        North = 25, 
        South, 
        Ease,
        West
    };
    int num = North;
    
    // 域限定枚举
    enum class CardinalDirections 
    {
        North = 25, 
        South, 
        Ease,
        West
    }
    // 声明变量时，需要使用域解析符：：给变量指定初值
    CardinalDirections dir = CardinalDirections::South;
    // 只能将枚举类型的变量直接赋给其他相同类型的变量
    CardinalDirections dir2 = dir;
    ```

  

## chapter4 管理数组和字符串

#### 1. 声明和初始化静态数组

```c++
// 对于数值类型的数组，要将所有元素初始化为0
int myNumbers[5] = {};

// 如果只是要初始化部分元素
int myNumbers[5] = {1, 2};
```



## chapter5 使用运算符

#### 1. c++20 三向运算符（宇宙飞船运算符） <=>

对两个操作数进行比较，指出前者比后者大、比后者小还是与后者相当。

```c++
auto resultOfComparison = var1 <=> var2;
```



- 若 resultOfComparison < 0，说明 var1 < var2；
- 若 resultOfComparison > 0，说明 var1 > var2；
- 若 resultOfComparison = 0，说明 var1 = var2；

#### 2. 按位运算符 ~（每位取反）, &（对相应位执行AND）, |（对相应位执行OR）, ^（对相应位执行XOR，异或运算）

返回对操作数对应位执行指定运算的结果。

#### 3. sizeof()不是函数，而是一个***运算符***！!!

sizeof()可能对某些属性进行填充，使其与字边界对齐，也可能不这样做，取决于编译器。



## Chapter7 使用函数组织代码

#### 1. 带默认值的函数参数

在调用这种函数时， 提供的实参可以不包含已经默认的函数参数，也可以赋新的值。

```c++
// 函数定义
void Area(double radius, double pi = 3.14)
    
// 调用方法1
    Area(radius);
// 调用方法2
	double newPi = 3.1415;
	Area(radius, newPi);
```

 PS. 这些参数必须位于参数列表的末尾！

#### 2. 函数重载

名称和返回类型相同，但参数不同的函数。

```c++
double Area(double radius);
double Area(double radius, double height);
```

#### 3. 内联函数

处理较为**简单操作**的函数时，调用函数的开销往往会大于执行这个函数的开销，故可以考虑在调用的同时就执行这个函数。

在函数前加上`inline`的声明。

```c++
inline double GetPi()
{
    return 3.14;
}
```

PS. 内存珍贵，少用内联。

## chapter8 阐述指针和引用

在声明指针时，一般指向一个有效的内存地址，避免指向无效的内存单元

#### 几个符号的全称

- & 引用运算符
- \* 解除引用运算符（间接运算符）

#### 8.2 内存动态分配

使用new分配新的内存块

相应地，使用delete及时释放（**delete只能释放用于 new 返回的指针！！**）

```c++
Type* pointer = new Type;				delete pointer;
Type* pointer = new Type[numElements];  delete[] pointer;
```

##### 内存泄漏

不再需要分配的内存后，如果不及时释放，这些内存仍将预留并分配给应用程序。这将减少可供其他应用程序使用的系统内存量，甚至降低应用程序的执行速度！

##### 关键字const用于指针

```c++
// 1. 指针包含地址为常量，可以修改数据
type* const pointer = &value;

// 2. 指针指向的数据为常量，但是可以修改指针包含的地址
const type* pointer = &value;

//3. 指针包含的地址以及它指向的数据都是常量，不能修改
const type* const pointer = &value;
```

##### 检查new发出的分配请求是否满足的方法

- 使用 try catch 处理 bad_alloc 异常
- 使用 new(throw)，在内存分配失败时返回 NULL

#### 8.4 指针编程最佳实践

##### 引用

**引用是变量的别名。**

也就是说，只是给当前变量起了另一个名字，存储的地址以及数据是相同的！

所以在函数调用时使用引用，可以避免将实参复制给形参，从而极大提升性能。