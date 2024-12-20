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

## 解数独（37）

这一题与本章节题目的有两个不同点。

一是只需找到一个合适的解即可，二是需要对二维的数组进行遍历，所以需要两重for循环。

#### 按照回溯的三步骤来梳理一下这个题目：

1. 传入参数以及返回值

   因为要遍历整个棋盘，所以传入参数只需是棋盘向量`board`

   另一点是只需要找到一个符合数独的解即可，所以需要一个返回值。这里选用了布尔型变量作为返回值，在遍历完找到符合要求的解后返回真。

2. 函数结束的判定条件

   由于只要找到一个符合要求的值，所以只要在找的符合要求的解时返回真即可。

3. 函数的主体遍历部分以及函数调用

   由于遍历的是二维的棋盘，所以需要两重for循环。

   **这一题麻烦的是**需求要满足三个条件，分别是横向、 纵向，所处九宫格内不重复，我直接绕进去了，没想好该怎么遍历这个棋盘。

   实际上只要按一般情况先遍历横向、再遍历纵向上的每一个格子即可，然后判定在这个格子上分别填上”1-9“是否能够满足需求就行啦😂。

   判定当前数字可以填入后，递归调用回溯函数判定下一个格子上能否填上剩下的数字，不行就返回。

#### PS. 二维向量的用法

```c++
vector<vector<char>> board;
// 该向量的行数为
int rowSize = board.size();
// 该向量的列数为
int colSize = board[0].size();
```
