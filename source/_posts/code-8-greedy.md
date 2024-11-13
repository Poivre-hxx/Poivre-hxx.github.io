---
title: 代码随想录一刷笔记_贪心算法
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode, 代码随想录]
date: 2024-11-11 20:20:00

---

60+在408的算法考察难度和深度上还是收手了👍）

<!-- more -->

## 贪心算法理论基础

**贪心的本质是选择每一阶段的局部最优，从而达到全局最优**。

第一个难点是如何判断该使用贪心算法了，需要 手推/特殊值/举反例 的方法。

#### 贪心算法的解题步骤：

找到局部最优是什么，然后推导出全局最优。

## 分发饼干

这一题的优化技巧在于，饼干分配掉之后是不会再使用了，所以可以使用一个指针指向最大尺寸的饼干，分配掉之后向前递减即可。省去了一重for循环 & 判定当前饼干是否分配的空间。

## 摆动序列

这一题先是使用了回溯的方法解决，虽然进行了一定的剪枝操作，但还是被一个很长的测试样例卡住了。事实证明，回溯是一种暴力算法，效率不是很高。

#### 贪心算法

例如 [33,53,12,64,50,41,45,21,97,35,47,92,39,0] 这一个测试样例，可以画出这样的图

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/2305adb002cca4053ce43f861db53f4.jpg" alt="2305adb002cca4053ce43f861db53f4" style="width:50%;" />

可以得到的最长的摆动序列就是荧光笔标注的地方。记录每一个波峰和波谷，去除其他的元素，想起来挺有道理的，但是数学证明略（其实是不会）。。。。

用一个变量记录下一个应该收录的元素应该是在波峰还是波谷，然后记录最长的长度即可。

PS. 这个是我一开始的解法版本，错误只出在一个逆天（特别长）的测试用例上， 找这个问题找了许久。

```c++
if (nums.size() == 1) return 1;
int flag = 0;
int lastNum = nums[0];
for (int i = 1; i < nums.size(); i++) {
    if (nums[i] == lastNum) continue;
    else if (nums[i] > lastNum && flag < 0) continue;
    else if (nums[i] < lastNum && flag > 0) continue;
    else {
        result.push_back(nums[i]);
        if (nums[i] > lastNum) flag = -1;
        else flag = 1;
        lastNum = nums[i];
    }
}
```

想法是这样的，由于我要找的是有几个上升序列和下降序列，所以我只要记录这条趋势里的一个数字即可，然后就造成了一种类似抖动幅度变小的结果。

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/381a9a7ddffc8db38fdaa6d20998f1e.jpg" alt="381a9a7ddffc8db38fdaa6d20998f1e" style="width:50%;" />

后来改成了和前一个数字进行比较

```c++
for (int i = 1; i < nums.size(); i++) {
    if (nums[i] > nums[i - 1] && flag != 1) {  // 如果当前元素比前一个大且趋势不是上升
        length++;
        flag = 1;  // 更新趋势为上升
    } else if (nums[i] < nums[i - 1] && flag != -1) {  // 如果当前元素比前一个小且趋势不是下降
        length++;
        flag = -1;  // 更新趋势为下降
    }
    // 如果nums[i] == nums[i-1]，什么都不做
}
```

虽然说仍然记录的不是波峰和波谷的那几个数据，但是是记录了有几条上升/下降趋势。

PS.. 题解的版本是根据当前数值和前一个&后一个的差值判断是不是在波峰/波谷上。

PS... 遇到问题还是得数形结合，干瞪眼了好久没想到好的办法。。。。
