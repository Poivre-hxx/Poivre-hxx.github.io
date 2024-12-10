---
title: 代码随想录一刷笔记_动态规划（下）
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode, 代码随想录]
date: 2024-12-09 20:20:00

---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 198 打家劫舍

因为之前做了一周的背包问题，所以现在看到题目的第一反应就是，这是背包😖😖....

实际上这一题并不满足背包的条件，背包需要满足容量是固定的，但是这一题是让我求最大的容量，根据题设，这是一个小于40000的正整数....

## 213 打家劫舍Ⅱ

我的想法，本题和上一题的区别在于数组由线性的变成了环状的，所以我加了一个布尔类型的数组用于判断当前的最大值里有没有包含首位数字，然后最后进行一个判断。但是在`[2,1,2,6,1,8,10,10]`这个样例里面没有通过。

```c++
// 处理代码段
if (nums.size() >= 3) {
    int delta1 = dp[nums.size() - 2] + nums[nums.size() - 1];
    int delta2 = dp[nums.size() - 3] + nums[nums.size() - 1];
    if (jud[nums.size() - 2]) delta1 -= min(nums[0], nums[nums.size() - 1]);
    if (jud[nums.size() - 3]) delta2 -= min(nums[0], nums[nums.size() - 1]);
    dp[nums.size()] = max(delta1, delta2);
}
```

#### 题解

看了题解，我是想把这一部分在一个循环里实现，搞复杂了，实际上只要遍历两次dp数组（分别包含首元素和尾元素），然后取最大值即可。。。。

数组环的三种情况：

1. 情况一：考虑不包含首尾元素
2. 情况二：考虑包含首元素，不包含尾元素
3. 情况三：考虑包含尾元素，不包含首元素

这里的情况一是包含在二和三里的，所以只需要遍历两遍取极大值即可。

PS：网友抚平了我提交10多次没有ac的痛苦，笑死了。

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20241210145220476.png" alt="image-20241210145220476" style="width:80%;" />
