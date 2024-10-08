---
title: 代码随想录一刷笔记_数组
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode, 代码随想录]
date: 2024-08-06 20:20:00
---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 二分查找

1. 二分查找应用于顺序排列的数组，主要分为两种情形：数组区间为左闭右闭和左闭右开。

   - 初始的赋值：right的赋值

     ```c++
     ①左闭右闭：right = nums.size() - 1
     ②左闭右开：right = nums.size()
     ```

     

   - 判断条件：left __ right （相等时是否合法？）

     ```c++
     ①左闭右闭：left <= right
     ②左闭右开：left < right
     ```

     

   - 新区间设置：新区间是否要包含mid？

     ```c++
     ①左闭右闭：left = mid + 1; / right = mid - 1;
     ②左闭右开：left = mid + 1; / right = mid;
     ```

     

2. 为了防止溢出，可以避免 (left + right) 这种相加的情况出现：

   ```c++
   ① mid = left + (right - left) / 2
   ② mid = left + ((right - left) >> 1)
   ```

   

3. 查找的元素可以分为四种情况：

   - 目标值在数组所有元素之前
   - 目标值等于数组中某一元素
   - 目标值处于插入数组中的位置
   - 目标值在数组所有元素之后

PS:在数据量不大的情况下，暴力解法可能也是一种好的选择。

## 移除元素（快慢指针）

有两种常用的方法

- ###### 暴力解法

使用两层for循环的方法，一层用于遍历数组元素，一层用于循环更新数组。

时间复杂度为O(n^2)。

- ###### 双指针法

使用一组快慢指针，在一层for循环中，快指针用于寻找新数组的元素，慢指针指向新数组下标的位置。

时间复杂度为O(n)。 

###### 有序数组的平方（变式）

定义一个新数组，用空间换时间。

使用一组左右指针，分别指向左右两端，比较两端元素平方后的数值大小并放入新数组中。

时间复杂度为O(n)，空间复杂度为O(n)。

## 长度最小的子数组(滑动窗口)

所谓滑动窗口，**就是不断的调节子序列的起始位置和终止位置，从而得出我们要想的结果**。

在这个问题中，可以使用一个for循环完成遍历，其中指针指向滑动窗口的终止位置。

- 窗口就是 满足其和 ≥ s 的长度最小的 连续 子数组。
- 窗口的起始位置如何移动：如果当前窗口的值大于等于s了，窗口就要向前移动了（也就是该缩小了）。
- 窗口的结束位置如何移动：窗口的结束位置就是遍历数组的指针，也就是for循环里的索引。

时间复杂度为O(n)。

## 螺旋矩阵

这一题的关键在于找到输出的规律。

将矩阵按照顺时针方向拆解时，需要坚持**循环不变量**原则。

模拟顺时针画矩阵的过程:

- 填充上行从左到右
- 填充右列从上到下
- 填充下行从右到左
- 填充左列从下到上

由外向内一圈一圈这么画下去。

时间复杂度为O(n^2)。

## 区间和（前缀和）

**前缀和 在涉及计算区间和的问题时非常有用**！

面对这类问题时，暴力方法是直接对输入的区间元素进行求和操作。但是，当查询次数m过多时，时间复杂度为 O(n * m) ，不免会超时。

前缀和的思想是重复利用计算过的子数组之和，从而降低区间查询需要累加计算的次数。

新定义一个数组或是对原数组进行操作，使得a[i]代表区间0 - i区间内的元素和，当要计算下标i - j的前缀和时，只需计算a[j] - a[i - 1]即可。
