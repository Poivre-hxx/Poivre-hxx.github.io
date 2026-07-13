---
title: 面筋鉴赏-unity
tags: 
  - Notes
  - LLM
  - Algorithm
  - Agent
categories: 
  - [Notes]
date: 2026-07-06 20:20:00

---

面筋学习（unity）！！🤣🤣

<!-- more -->

## Unity 客户端八股

https://www.xiaohongshu.com/explore/68c43fb8000000001c00b7c9?xsec_token=AB8Wg83k3of_Th3DsGTpKnlAtt5Nc3EtufhlWY34jEG8k=&xsec_source=pc_search&source=web_explore_feed

**面向对象的三大特征**

- 封装：把对象的属性和行为封装在类中，并隐藏内部实现，只对外提供必要的方法访问，保护数据降低使用的复杂度

- 多态：同一个方法或接口在不同对象上有不同的实现效果。多态通过方法重写、抽象类和接口实现，提高程序的扩展性

  重载（编译时多态），同一个类中多个方法同名但是参数不同，编译器会在编译阶段根据参数决定调用哪个方法

- 继承：子类复用父类的属性和方法，并且可以在父类基础上扩展新的功能或重写原有方法，它主要用于代码复用和表达类之间的层次关系

  重写是在继承的基础上，子类对父类已有方法进行重新实现

**协程和线程的异同，线程和进程的异同，协程和异步的区别是**

Unity 中的协程运行于主线程中，协程通过 yield return 暂停和恢复执行，常用于延迟执行、等待几秒、等待动画，不会真正并行执行

线程是真正的执行单元，可以由操作系统调度。在多核 CPU 上，多个线程可以并行运行，适合处理耗时计算、文件读写、网络请求等任务。但在 Unity 中，大多是 Unity API 只能在主线程中调用，所以子线程不能直接操作 GameObject、Transform、UI 等对象

进程可以理解为一个正在运行的程序，它拥有独立的内存空间。线程则是进程内部的执行单位，一个进程可以包含多个子线程。进程之间资源隔离更强，但是创建和切换的成本更高；线程共享同一个进程的资源，成本更低

协程是一种“非阻塞、可暂停恢复的流程控制方式”，所以它能实现异步式的效果；但 Unity 协程本身通常仍然运行在主线程，不代表多线程，也不一定是真正意义上的异步任务。



## Unity 生命周期是怎么走的

https://www.xiaohongshu.com/explore/6954c647000000002200bb6b?xsec_token=ABWySvZvO4uSBQdtpP8wUfZDVSaXczA6hp3LioLS5bDOE=&xsec_source=pc_search&source=web_search_result_notes

Unity 中 MonoBehaviour 脚本的生命周期，可以理解为一个脚本从创建、启用、运行到销毁的过程。

首先会执行 Awake()。它通常用于脚本自身的初始化，比如获取组件、初始化变量等。Awake() 只要对象被加载出来就会执行，不一定要求对象已经启用。

接着会执行 OnEnable()。当 GameObject 或脚本组件被启用时，它就会被调用。如果这个对象之后被反复禁用和启用，OnEnable() 也会被反复调用。

然后是 Start()。Start() 会在第一次 Update() 之前执行，并且只执行一次。它通常用于依赖其他对象已经初始化完成之后的逻辑。

进入运行阶段后，Unity 会不断调用一些更新函数。Update() 每一帧都会执行，常用于处理输入、角色移动、普通逻辑等；FixedUpdate() 按固定时间间隔执行，常用于物理相关逻辑；LateUpdate() 会在 Update() 之后执行，常用于相机跟随、收尾处理等。

当对象或脚本被禁用时，会调用 OnDisable()。一般可以在这里取消事件监听、停止协程，避免对象禁用后还继续执行相关逻辑。

最后，当对象被销毁时，会调用 OnDestroy()。它通常用于最终的资源释放和清理，比如解绑全局事件、清除引用等。

简单来说，常见顺序可以记为：Awake → OnEnable → Start → Update / FixedUpdate / LateUpdate → OnDisable → OnDestroy。

​                                                     
