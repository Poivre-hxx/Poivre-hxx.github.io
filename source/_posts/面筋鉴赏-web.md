---
title: 面筋鉴赏-web
tags: 
  - Notes
  - LLM
  - Algorithm
  - Agent
categories: 
  - [Notes]
date: 2026-07-06 20:20:00

---

面筋学习（web）！！🤣🤣

<!-- more -->

## 前端 Typescript 最常用20道面试题总结

https://www.xiaohongshu.com/explore/68cbbbab000000001101fc34?xsec_token=ABCC96NVeHmWBnvTL43FlJ2YxZiVq5s-gPmLwZ8yN5jlY=&xsec_source=pc_search&source=web_search_result_notes

1. Typescript 和 Javascript 的区别是什么？

   ts 是 js 的超集，在 js 的基础上增加了静态类型系统。js 是动态类型语言，很多错误需要在运行时才能够发现，而 ts 可以在编译阶段检查变量、函数参数、返回值和对象结构的类型，从而减少运行时的错误。

   ts 提供了 interface 和 type 来描述对象结构，支持可选属性、联合类型、交叉类型的写法。也支持泛型，可以在保持类型安全的同时提高代码的复用性。

   ts 提供装饰器语法。

2. 什么是联合类型 / 泛型，如何使用

   使用 `|`表示联合类型，表示一个变量可以是多种类型之一，常用于变量、函数参数、状态值中

   泛型的作用是让代码在支持多种类型的同时，仍然保留具体的类型信息

   ```ts
   function getFirst<T>(arr: T[]): T {
       return arr[0];
   }
   // <T>是声明类型变量
   ```

   联合类型和泛型的区别是，联合类型是提前规定一个固定的类型范围，而泛型只是一个类型占位符，具体类型在调用时确定。泛型更强调类型之间的关系，比如参数是什么类型，返回值就是什么类型

3. 什么是类型断言，如何使用

   使用 <Type> 或 as Type，告诉编译器某个值的具体类型，不会改变变量运行时的真实类型，只会影响 ts 的类型检查

4. 接口和类型别名的区别，这两个概念和类的区别？

   interface 偏向定义对象结构，支持继承和声明合并；type 更加灵活，可以表示联合类型、交叉类型、函数类型等

   class 是具体的实现，interface / type 是类型描述。编译后，class 是仍然存在的，但是 interface / type 是会消失的

5. 如何定义可选的属性

   使用 ？标记可选属性

6. 元祖的作用是什么，如何定义？

   元祖是 ts 中一种特殊的数组类型，用来表示长度固定、每个位置类型固定的数据结构，适合表示坐标、固定格式的返回值。

   ```ts
   let user: [name: string, age: number] = ["Tim", 18];
   ```

7. 枚举有什么作用？如何定义

   枚举是 ts 中用来定义一组命名常量的语法，适合表示一组固定取值

8. 类型推断是什么

   如果没有显式标注类型，ts 会根据赋值自动推断类型

9. 如何定义函数类型

   ```ts
   // 使用类型表达式 type Fn = (a: number, b: number) => number;
   type Sum = (a: number, b: number) => number;
   const add: Sum = (x, y) = > x + y;
   ```

10. 类型守卫是？如何实现

    用于缩小变量类型范围的一种机制，常用于联合类型。可以通过 typeof、instanceof、in、参数 is 类型 的形式定义，相比类型断言更安全，因为是在运行时的判断

11. 如何定义只读属性

    readonly

    
