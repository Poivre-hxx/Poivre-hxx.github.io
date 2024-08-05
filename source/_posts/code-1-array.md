---
title: 代码随想录一刷笔记_数组
tags: 
  - Notes
  - leet code
  - data structure
categories: 
  - [代码随想录]
date: 2024-08-06 20:00:00
---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

#### 二分查找

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
