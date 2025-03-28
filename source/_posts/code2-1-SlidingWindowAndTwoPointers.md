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



#### 3439 重新安排会议得到最多空余时间 Ⅰ

由于会议之间是不重叠的，所以有`n`场会议就有`n + 1`个茶歇时间（包括茶歇时间为0的情况）。调整`k`次的话，就可以将`k + 1`段茶歇时间并在一起，得到最长的休息时间。

可以将这个情景抽象为这个问题：有`n + 1`个空余时间段，合并其中`k + 1`个连续的空余时间段，得到的最大长度是夺少？（滑动窗口问题！！）

###### c++

题解中给出了lambda表达式写法， 故复习一下。

```c++
// lambda表达式是一种对匿名函数的支持
// 具体形式为：
// [capture](para) -> return-type{body}

// 在这个例子中，使用 [&] 时，Lambda 表达式会以引用的方式捕获外部作用域中的所有变量。这意味着 Lambda 内部使用的变量与外部作用域中的变量是同一个对象，对这些变量的修改会反映到外部作用域中。
// 如果不使用[&]，而是具体写明调用哪些变量，那只是使用了类似声明局部变量的方式，在函数中的改变不影响外部变量的值。
auto get = [&](int i) -> int {
    if (i == 0) {
        return startTime[0];
    }
    if (i == n) {
        return eventTime - endTime[n - 1];
    }
    return startTime[i] - endTime[i - 1];
};
```

#### 2134 最少交换次数来组合所有的1 Ⅱ

这一题中，`1`的个数就是一个定长的滑动窗口，我们的任务是要得到当前环中`1`的数量最多的部分。

###### c++

`copy`函数的用法

```c++
vector<int> path(nums.size() * 2, 0);
copy(nums.begin(), nums.end(), path.begin());
```

#### 1297 子串的最大出现次数

注意看，这题有个陷阱（后面的超时就是这个原因）！

如果有一个子串出现了`n`次，那么这个子串的子串在字符串中出现的次数只多不少。

故，只要考虑要求的最小长度即可！

#### 2653 滑动字数组的美丽值

显然，这题需要用滑动窗口来实现。

在做这题的过程中，使用容器的过程遇到了亿点点小挫折，且听我细细道来。

###### c++

map的使用

题目的需求是要得到第x小的数值，应该怎么得到呢？

我第一想法是用迭代器迭代x次，但是，窗口中的数值可能是会重复的！

最后debug后得到这样的代码：

```c++
auto it = imap.begin(); 
for (int j = 0; j < x - 1; j++) {
    j += it->second - 1;
    if (j < x - 1) it++;
}
```

set的使用

在set中放入重复的数字是没有响应的！重复的数字有且只能存入一次。

#### 2269 找到一个数字的K美丽值

###### c++

1. 将`int`类型变量转为`string`

   ```c++
   to_string(num);
   ```

   将`string`类型变量转为`int`

   ```c++
   stoi();
   ```

   

2. 换一个方向思考

   题目是从最高位开始取`k`数判断是否美丽，不妨从最低`k`位开始取。

#### 1461 检查一个字符串是否包含所有长度为K的二进制子串

用unordered_set计算当前字符串的子串类型个数。

