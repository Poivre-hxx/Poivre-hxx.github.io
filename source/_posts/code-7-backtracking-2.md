---
title: 代码随想录一刷笔记_回溯算法（下）
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode, 代码随想录]
date: 2024-11-06 20:20:00

---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 全排列（46）

排列与组合的不同点在于，可以交换输出序列中的具体顺序。

所以，横向搜索的for循环不能再用startIndex来控制了，而是每一次的for循环都是要遍历整个数组或者字符串。

为了避免重复，需要引入前面的避免重复的方法：`unordered_set`方法 或 `vector<bool> used`向量。

## 全排列Ⅱ（47）

这道题是在数组中加入了重复的数字，所以需要进行去重的工作。与前面组合的去重方法相同，有两种方法：

- 使用`unordered_set`方法
- 使用`vector<bool> used`向量
