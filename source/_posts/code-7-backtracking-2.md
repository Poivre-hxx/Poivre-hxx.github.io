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

## 非递减子序列（491）

这一题的测试样例十分逆天，出现了答案错误但是输入输出因为写不下而完全相同的情况。。。。导致我还得去编译器里自己查是什么bug😭。

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20241106234733174.png" alt="image-20241106234733174" style="width:50%;" />

他是要输出按序的子序列（重复数字也包含），所以与之前的题目不同的是不需要进行预先的排序。按照去重的思路，需要对同一层中出现的重复数字进行去重操作，有三种方法。

但是！因为不需要对序列进行预排序的问题，直接比较当前数字与前一位是行不通的（与他相同的数字可能在前前前面）。

剩下的两种使用布尔型的used向量和使用unordered_set的方法都是可行的。

PS 定义布尔型的向量并初始化为false的办法：

```c++
vector<bool> used(nums.size(), false);
```

