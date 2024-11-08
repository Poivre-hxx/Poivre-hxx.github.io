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

## N皇后（51）

这一题的话就是按照N皇后的定义按棋盘的层序遍历，找到所有可能的解，虽然标的是困难题，但是思路还是挺清晰的，可以做出来（没重新安排行程这么逆天）。

PS. 处理这一题时，我是使用一个函数将每一层的字符串填充入`vector<string> path`向量中，当`path`中包含了n个字符串后将结果放入`vector<vector<string>> result`结果中。

但是，题解给出了向量的另一个使用方式！🧐他定义了一个二维的向量组，初始化为n行n列均填充为“.”。

```c++
std::vector<std::string> chessboard(n, std::string(n, '.'));
```

整个过程都是对其进行操作，遍历完棋盘的每一层后只需将`chessboard`放入`result`即可(^^ゞ。

**std库函数真有用。**
