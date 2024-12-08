---
title: 21天学习c++_part2笔记 
tags: 
  - Notes
  - c++
categories: 
  - [Tutorials, Book]
date: 2024-12-05 20:20:00
---

我要成为c++糕手！第二部分--c++面向对象编程基础

<!-- more -->

## Chapter9 类和对象

#### 9.1 类和对象

涉及的运算符：句点运算符（.），指针运算符（->），作用域解析运算符（::）

###### 构造函数

与类同名且不返回任何值，在创建对象时被调用，用于初始化类成员变量。

**默认构造函数**：在**不提供参数**的情况下调用的构造函数。如果在没有提供默认构造函数，编译器将会自动创建一个，并且自动创建成员属性（会赋一些随机的垃圾值）。

**重载构造函数**：

构造函数也是**可以重载**的。如果声明中只给出了**重载构造函数**而没有给出默认构造函数的话，创建对象时编译器不会自动创建默认构造函数，而是必须调用这个重载构造函数，也就是必须给出参数值，否则会报错滴。

btw，如果构造函数中给的参数都给出了默认值，那么这个函数仍然是**默认构造函数**，实例化对象时可以不给出参数。

**包含初始化列表的构造函数:**

直接将参数值赋给声明对象中对应的变量

```c++
human(string humansName = "adam", int humansAge = 25) : name(humansName), age(humansAge)
```

**转换构造函数？**（没看懂9.3）

###### 析构函数

在对象销毁时自动被调用：①对象不在作用域时（如进程结束）；②对象通过delete被删除时。

btw，如果没有声明析构函数，编译器将创建一个伪（dummy）析构函数并调用。