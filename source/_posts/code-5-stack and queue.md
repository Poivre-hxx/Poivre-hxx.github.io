---
title: 代码随想录一刷笔记_栈与队列
tags: 
  - Notes
  - leetCode
  - data structure
  - algorithm
  - C++
categories: 
  - [代码随想录]
date: 2024-09-18 20:20:00

---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 栈与队列理论基础

##### 四个基本问题

- c++中stack是容器莫

  **“栈是以底层容器完成其所有的工作，对外提供统一的接口，底层容器是可插拔的（也就是说我们可以控制使用哪种容器来实现栈的功能）。”**

  故，stl中stack往往不被归类为容器，而被归类为**container adapter**（容器适配器）

- 我们使用的stack是属于哪个版本的stl

  三个最为普遍的stl版本：

  - HP STL。c++的第一个STL版本，且开源。
  - P.J.Plauger STL。被visual c++编译器采用，不开源。
  - SGI STL。被Linux的c++编译器GCC采用，开源。（显然用的是这个👌）

- 我们使用的stl中stack是如何实现的

  <img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20240918190632930.png" alt="image-20240918190632930" style="width:67%;" />

  栈的底层实现可以是vector，deque，list等数据结构。

  在SGI STL中，stack默认是以deque为基础实现的（封住了一端）。

- stack提供迭代器来遍历stack空间莫

  栈只提供了push和pop等接口访问元素，不提供走访功能，也不提供迭代器。

## 用栈实现队列（232）

这一题使用两个栈模拟队列q的q.pop()，q.push()，q.getTop操作。

栈的基本操作：

```c++
// 声明栈
stack<int> s;

// 栈的基本操作
s.push();
s.pop();
s.top();
s.empty();
s.size();
```



## 用队列实现栈（225）

这一题使用两个队列模拟栈s的s.pop()，s.push()，s.getTop操作。

- 这一题的优化：可以指使用一条队列就能模拟栈的功能。

  将队列中弹出的元素添加回该条队列，最后的那一个元素也就是对应的栈的栈顶元素。

队列的常用操作：

```c++
// 声明队列
queue<int> q;

// 队列的基本操作
q.empty();
q.size();
q.front();	q.back();
q.push();	q.pop();
```



## 有效的括号（20）

经典的括号匹配问题）

tips:关于左右括号匹配判断的写法

```c++
if ((top == '(' && ch != ')') || (top == '{' && ch != '}') || (top == '[' && ch != ']'))
{ .... }
```



## 删除字符串中的所有相邻重复项（1047）

这一题有两种办法：

- 判断字符串是否有相邻重复项并去重，重复该操作直到不存在重复项。

- 使用栈。

  栈用来存放遍历过的元素，当遍历当前的元素的时候，去栈里查看是否遍历过相同数值的相邻元素。

  更进一步，直接把输出的result作为一个栈进行遍历，可以在一次循环后直接输出。时间复杂度达到了O(n)。
