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

#### 1343 大小为K且平均值大于等于阈值的子数组数目

###### ts

数组的`reduce()`方法需要有返回值！！

#### 2090 半径为k的子数组平均值

###### c++

考虑到测试用例，需要用long长整型声明变量。

###### ts

```ts
// 1 声明数组
let res = Array(nums.length).fill(-1);

// 2 取证（默认除法是带有小数的）
let res = Math.floor(cur / k);
```

#### 2379 得到K个黑块的最少涂色次数

ts

数组的`reduce()`方法中不能使用`continue`。

`continue`语句只用用在`for`、`while`、`do-while`这类循环语句中，而`reduce`是一个高阶方法，不能用`continue`。

#### 2841 几乎唯一子数组的最大和

###### c++

由于需要统计是否出现重复数字，故使用`map`类方法。

再次复习一下`map`和`unordered_map`的常用方法：

```c++
// map用于存储键值对
// map容器中的元素是按照键的顺序**自动排序**的，非常适合需要快速查找和有序数据的场景
// 1. 声明 map 容器
map<key_type, value_type> map;
// 2. 插入元素
map[key] = value;
// 3. 访问元素
value = map[key];
// 4. 遍历map
for (map<key_type, value_type>::iterator it = map.begin(); it != map.end(); it++) {
    cout << it->first << "=>" << it->second << endl;
}
// 5. 检查键是否存在
if (map.find(key) != map.end()) {
   // 键
}
// 6. 删除元素
map.erase(key);
// 7. 清空map
map.clear();
// 8. 获取map的大小
size_t size = map.size();


// unordered_map用于存储键值对
// unordered_map容器不保证元素的排序，但是提供更快的查找速度
// 1. 声明 unordered_map 容器
unordered_map<key_type, value_type> map;
// 2. 插入元素
map.insert({3, "three"});
// 3. 访问元素
string value = map[1];
// 4. 删除元素
map.erase(1);
// 5. 查找元素
auto it = map.find(1);
if (it != map.end()) {
    ...
}
```



#### 1423 可获得的最大点数

###### 解题思路

1. 正向思维 ⭐⭐⭐⭐

   题目要求是要按顺序从正面或者反面拿牌使得取得的点数最大。由于牌面的点数是固定的，也就是说此时剩下的`n - k`张牌的点数和是最小的。

   此时，只要求点数和最小的连续`n - k`张牌即可。

2. 逆向思维

   先计算按正序取牌的总点数，然后依次按倒序取牌，算得最小值。

#### 1652 拆炸弹

解题思路

当`k < 0`或`k > 0` 时，窗口都是随着`i`的增大而向右移动的，两者的不同在于初始窗口的位置不同，所以可以把这两个情况放在一个循环中考虑。
