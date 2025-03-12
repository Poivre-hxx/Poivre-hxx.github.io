---
title: 滑动窗口与双指针
tags: 
  - Notes
  - LeetCode
  - Data structure
  - Algorithm
  - C++
categories: 
  - [LeetCode]
date: 2025-03-12 20:20:00

---

`灵茶山艾府`的题单。

<!-- more -->

## 一、定长滑动窗口

这类问题的框架可以分为三步

```c++
for (int i = 0; i < s.length(); i++) {
    // 1. 进入窗口
    	// 窗口大小不足时的判定
    		// 一方面是防止下标越界
    		// 另一方面是当窗口大小不足k个时不进行计数！ 
    	if (i < k - 1) continue;
    	
    // 2. 更新答案
    // 3. 离开窗口
}
```



#### 1456 定长子串中元音的最大数目

###### ts

```typescript
// 1. s.split('')
// 将字符串拆解为一个字符数组
let s = "hello";
let chars = s.split('');

// 2. reduce
// 遍历数组中每一个元素，并对每个元素执行回调函数
// 回调的参数包括
// accumulator（累加器）、currentValue（当前值）、currentIndex（当前索引，可选）、array（原数组，可选）
chars.reduce((_, char, index) => {});
```

#### 643 子数组最大平均数Ⅰ

###### c++

输出结果有精度要求，所以返回值应该带上类型转换`(double)`

