---
title: 代码随想录一刷笔记_动态规划（上）
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode, 代码随想录]
date: 2024-11-28 20:20:00

---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 动态规划理论基础

#### DP的特点

每一个状态是由上一个状态推导出来的（区别于贪心，贪心是局部选择最优）

#### DP的解题步骤

1. **确定dp数组（dp table）以及下标的含义**（很关键⭐⭐⭐⭐⭐）
2. 确定递推公式（需要推导一下）
3. dp数组如何初始化
4. 确定遍历顺序
5. 举例推导dp数组

## 509 斐波那契数

#### 递归

先是使用了一下递归

时间和空间复杂度还都挺高的

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20241128151833407.png" alt="image-20241128151833407" style="width:50%;" />

#### dp

按照dp的解题步骤顺一下这道题

1. 确定dp数组（dp table）以及下标的含义

   dp[i]表示第i个数值

2. 确定递推公式

   dp[i] = dp[i - 1] + dp[i - 2];

3. dp数组如何初始化

   dp[0] = 0, dp[1] = 1;

4. 确定遍历顺序

   从前往后遍历

5. 举例推导dp数组

   举个栗子：0, 1, 1, 2, 3, ...

## 70 爬楼梯

#### 回溯

试了下回溯，这简单题也要插几个超时例子是吧(╯▔皿▔)╯

#### dp

按照dp的解题步骤顺一下这道题

1. **确定dp数组（dp table）以及下标的含义**（确定这个很重要！）

   dp[i]表示到达第i层楼梯有几种方法

2. 确定递推公式（需要演算一下）

   dp[i] = dp[i - 1] + d[i - 2]；

3. dp数组如何初始化

   dp[0] = 1（照顾一下i = 2的情况），dp[1] = 1, dp[2] = 2;

4. 确定遍历顺序

   从前往后遍历

5. 举例推导dp数组

   举个栗子：1, 1, 2, 3, 4, ...

## 746 使用最小花费爬楼梯

#### 回溯

太棒了，又超时了┗|｀O′|┛

#### dp

按照dp的解题步骤顺一下这道题

1. **确定dp数组（dp table）以及下标的含义**（确定这个很重要！）

   dp[i]想从这个台阶出发的低消（最低消费）

2. 确定递推公式（需要演算一下）

   dp[i] = cost[i] + min(dp[i - 1], dp[i - 2])；

3. dp数组如何初始化

   dp[0] = cost[0], dp[1] = cost[1]

4. 确定遍历顺序

   从前往后遍历

5. 举例推导dp数组

   举个栗子：cost为[10, 15, 20]

   则对应的dp数组为[10, 15, 30]

## 62 不同路径

#### dp

按照dp的解题步骤顺一下这道题

1. **确定dp数组（dp table）以及下标的含义**

   dp[i]\[j]到达这个格子的方法有几种

2. 确定递推公式（需要演算一下）

   dp[i]\[j] = dp[i - 1]\[j] + dp[i]\[j - 1]；

3. dp数组如何初始化

   dp[0]\[0] = 0;

4. 确定遍历顺序

   从左到右，从上到下遍历

5. 举例推导dp数组

   举个栗子：dp[0]\[1] = 1; dp[1]\[0] = 1;


#### tips: 如何声明二维的向量

```c++
vector<vector<int>> path(m, vector<int>(n, 0));
```

## 63 不同路径Ⅱ

与`62 不同路径`相比，只要判断先进行对当前位置是否为障碍物的判断就行了，如果是障碍物就continue。

题解的方法有一点冗余力哈哈。