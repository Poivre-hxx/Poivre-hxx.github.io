---
title: 二分查找
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode]
date: 2025-06-20 20:20:00

---

`灵茶山艾府`的题单。

<!-- more -->

## 一、二分查找

#### 34 在排序数组中查找元素的第一个和最后一个位置

方法一：双指针

方法二：二分查找

找到符合target的数值，分别向左和向右找到边界。

这里给出了一种用开区间的二分查找方法（第一次见）：

```c++
// 通过这个函数可以找到第一个目标值（如果存在）
// 可以找到第一个比当前值大的数（如果不存在）
int lower_bound(vector<int>& nums, int target) {
    int left = -1, right = nums.size();
    while (left + 1 < right) {
        int mid = left + (right - left) / 2;
        (nums[mid] >= target ? right : left) = mid;
    }
    return right;
}
```

#### 35 搜索插入位置

直接套用二分查找即可。

#### 704 二分查找

直接套用二分查找即可。

`35`与`704`的细微区别，35只需要返回`target`在数组中的位置或者应该插入的位置，所以不需要考虑下标越界的问题。

#### 744 寻找比目标字母大的最小字母

直接套用二分查找即可。

#### 2529 正整数和负整数的最大计数

分别查找`0`，`1`在数组中的位置即可。

#### 2389 和有限的最长子序列

```c++
// 二分查找的库函数使用方法
ranges::upper_bound(nums, q);
```

#### 1170 比较字符串最小字母出现频次

这一题是在查找的背景外套了一层查找字符串中最小字母的皮。
