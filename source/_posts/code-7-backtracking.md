---
title: 代码随想录一刷笔记_回溯算法
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode, 代码随想录]
date: 2024-10-23 20:20:00

---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 回溯算法理论基础

回溯的本质是穷举，找出符合要求的答案。所以回溯算法的效率不会很高。

##### 回溯法解决的问题

- 组合问题（不强调元素顺序）个数里面按一定规则找出k个数的集合
- 切割问题：一个字符串按一定规则有几种切割方式
- 子集问题：一个N个数的集合里有多少符合条件的子集
- 排列问题（强调元素顺序）：N个数按一定规则全排列，有几种排列方式
- 棋盘问题：N皇后，解数独等

##### 回溯三部曲

1. 回溯函数返回值以及参数
2. 回溯函数终止条件
3. 回溯函数的单层遍历逻辑

## 组合（77）

整个过程感觉可以认为是在构造二叉树的过程，每一层往结果里push一个新的数，直到满足数量要求后向上返回。

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20241025234100819.png" alt="image-20241025234100819" style="width:80%;" />

##### PS. 剪枝

当`剩余的数组size` <`数量要求`的时候，可以进行剪枝操作。 

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20241025234620246.png" alt="image-20241025234620246" style="width:80%;" />
