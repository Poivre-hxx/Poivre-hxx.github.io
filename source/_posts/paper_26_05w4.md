---
title: 论文阅读-26-05w4
tags: 
  - Notes
  - LLM
categories: 
  - [Notes]
date: 2026-05-30 20:20:00

---

每周论文阅读笔记~

<!-- more -->

## Emotion Design for Video Games: A Framework for Affective Interactivity

把情绪理解为一个跨时间、依赖上下文、由互动持续构成的动态构成，建立一个“游戏-玩家情绪交互”的统一理论框架，提出一种通过“情绪反馈闭环”实现情绪自适应游戏的方法论

**有关情绪（*Emotion*）**

Emotion 并不等于所有的 Affective States（情感状态），Emotion 的特点在于持续时间较短、强度较高，并且往往由某个具体事件触发。
$$
Affect = Emotion + moood + attitude + ....
$$

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260522171225359.png" alt="image-20260522171225359" width="70%;" />

现代心理学对于“Emotion 到底是什么”并没有统一的答案。不同理论对于情绪的本质、结构与来源有着明显不同的理解。有关情绪是 连续的/离散的，是 人类天生固有的/大脑结合环境与经验动态构建出来的（很哲学了)

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260522171140627.png" alt="image-20260522171140627" width="60%" />

有关情绪的研究，有一定的共识：情绪由多个部分组成（生理、行为、主观感受），情绪与个体对事件的主观评估密切相关，并且会受到环境、context 和个体差异的影响。

情绪是一个随时间持续变化与演化的动态过程。

**Emotion 在生产中的实际应用**

同一个产品，在不同人的 appraisal 下，会产生不同的理解与情感体验（1000个读者有1000个哈姆雷特）

Norman基于认知处理过程，提出了设计的三个层级

​	本能层（visceral level）：对应直觉性的即时反应

​	行为层（behavior level）：对应使用过程中的行为与操作

​	反思层（reflective level）：对应有意识的主观体验与思考

整个游戏设计过程应该围绕***“目标体验的激发”***展开（Schell）；玩家会发挥主观能动性寻找符合某种主观体验的内容（比如喜欢 fps，就会玩 fps 类型的游戏）

**作品与用户之间的情绪交互循环**

the player	

​	1️⃣情绪由多个组成部分构成（例如生理反应、行为表现以及主观感受）

​	2️⃣ 主观评价（appraisal）是情绪体验中的核心部分

​	3️⃣ 主观评价（appraisal）的过程以及情绪体验本身会受到 context 的影响

​	4️⃣ 主观评价（appraisal）的过程以及情绪体验会受到个体差异的影响

​	5️⃣ 情绪会随着时间不断演化

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260527191610666.png" alt="image-20260527191610666" width="80%" />

the game

​	游戏系统通过“情绪检测 —— 情绪诱发 —— 动态适应”这三个模块，与玩家形成 loop

如何通过 emotional i/o 连接用户和游戏

​	1️⃣ 游戏如何制造情绪

什么样的 gameplay / narrative / challenge 会诱发目标的情绪

​	2️⃣ 游戏如何理解情绪

什么样的用户输入能够反应玩家当前的状态

**提出的有关情绪设计的游戏设计框架**

情绪设计*不能简单依赖固定的情绪分类或者经验判断*，而应该通过用户研究，明确*什么样的游戏内容会诱发什么样的情绪体验*，什么样的用户输入能够反应玩家当前的情绪

Emotional Output

关注游戏如何通过 narrative、challenge、music、pacing 等游戏元素来诱发目标情绪。

情绪体验不是由游戏内容本身直接决定的，而是玩家在特定的 context 下经过 appraisal 后形成的结果，因此需要结合具体玩家群体进行测试验证

Emotional Input

关注游戏如何理解玩家当前的情绪状态，作为进一步动态调整游戏的依据

------

**MDA**

从三个方向，**Mechanics**（机制）、**Dynamics**（动态）、**Aesthetics**（美学）来解释游戏的构成以及如何影响玩家的体验。一个优秀的游戏需要达成三者的动态平衡

在设计游戏时，应该先想明白想要给玩家的体验，总结对应的玩法流程，最后落实到游戏的主题机制





## Large Language Models in Game Development: Implications for  Gameplay, Playability, and Player Experience

当游戏中真正把 LLM 作为游戏系统的一部分时，会对 gameplay、playability 和 px 产生什么影响

gameplay 关注游戏中“玩家能够进行哪些活动”；playability 关注这些活动“能够以多高质量被执行”；px 关注玩家在交互过程中产生的感知与反应

**Impact on Gameplay**

LLM 在稳定的规则框架上，叠加了概率生成的内容，引入了变化性，但是底层的 gameplay 逻辑仍然稳定

**Impact on Playability**

LLM 的不稳定容易让 playability 崩溃，如何约束 LLM 的生成自由度？

1️⃣ difficulty calibration。对游戏的 pacing， progression cruve 带了影响

2️⃣ correctness。AI 生成的内容可能本来就是错的

​	比如说产出一道没有正确答案的选择题。会影响游戏的 fairness，trust，legitimacy

3️⃣ statistical bias。AI 生成的内容是有规律的，player可以抓住规律，利用漏洞，不按照策划的想法进行游戏

**Impact on PX**





## ⚠️ Gemini: Bidirectional Generation and Analysis of Games via ASP

提出了一个能够同时完成“游戏分析”和“游戏生成”的系统：能够通过静态分析游戏规则来推导游戏的玩法体验（play aesthetics）及其可能表达的含义（interpretations），也能够根据指定的目标含义生成相应的游戏。提出的 DSL 相较于 VGDL 能够表达更多样的游戏机制和游戏形式

**Cygnus**

设计了新的游戏描述语言 **Cygnus**，相较于 VGDL，主要增强了：
1️⃣ 支持 鼠标/触摸 输入

2️⃣ 支持更灵活的移动机制

3️⃣ 支持通用规则构建（条件 -> 结果）

​	VGDL 的核心思想是

```
Sprite（实体定义）
Interaction（实体交互）
Termination（胜负条件）
```

​	所以主要是 碰撞 => 预定义动作

​	而这个系统中目标达成的是 任意条件 => 任意结果

4️⃣ 不再局限于实体碰撞触发规则

​	触发**条件**包含这些：

 	1. 实体交互（也就是碰撞）
 	2. 资源数值比较（Scalar Comparison）
 	3. 用户输入（User Input）
 	4. 时间触发（Timer Elapsed）

​	支持这些**结果**：

1. 创建实体
2. 删除实体
3. 修改资源（数值）
4. 移动实体

**ASP 表示规则，底层的逻辑推理与求解框架**

将游戏规则转化为可被逻辑推理和约束求解的逻辑事实与规则

**Analysis Path**

从已有的游戏出发，反向推断这个游戏可能表达的设计意图。分析游戏中的规则、实体关系和交互机制，并利用预先定义的游戏规则，将底层机制映射到高维的概念（如合作、冲突、分享），判断游戏传达的内容

**Generation Path**

输入 => ASP 求解符合的游戏机制 => 组合生成 => 分析检查

------

**bottom-up & top-down**

bottom-up（自底向上），先生成机制，再观察会产生什么玩法

top-down（自顶向下），先确定目标，再生成机制





## ⚠️ ANGELINA - Coevolution in Automated Game Design

一个自动化游戏设计系统。它从在线资源中自己寻找相关素材和设计元素，自动生成相关的游戏

由四个模块组成：

1️⃣ Level Designer：负责方式实体方块和上锁的门，塑造玩家在关卡中的推进路径

2️⃣ Layout Designer：负责放置并设计玩家将要面对的敌人，同时确定关卡的起点和终点位置

3️⃣ Powerup Designer：负责定义玩家在游戏过程中可以获得的奖励道具及功能

4️⃣ Creative Direction Module：负责在关卡中安排一组媒体资源





## ⚠️ Puck: A Slow and Personal Automated Game Designer

自动化游戏设计（Automated Game Design，AGD）系统，能够自主生成和测试游戏，还会保留历史经验，形成设计偏好

**Related Work - Automated Game Design**

这篇文章中对于 AGD 的理解概念更宽泛，定义为 AI 参与游戏设计过程的各种方式，大致可以分为两类：

1️⃣ 自主式的 AGD，AI 自己设计游戏

例如 METAGAME、Ludi、Game-o-Matic、ANGELINA、Puck

2️⃣ 辅助式 / 混合 主动式设计工具

例如 Sentient Sketchbook、Tanagra、Germinate、Mechanic Maker

**作者对于 AI 应用的理解**

Puck 反对以效率和产量为核心的创作观，主张将 AI 视为一种具有个体性、成长历史和社区关系的长期创作者，提出了三点的特性：

1️⃣ Human-Scale

将生成的效率向人类的制作周期看齐，花费更多的时间打磨（玩游戏、反馈、学习、社区讨论）

2️⃣ Open

公开透明，告诉用户如何做决定、为何这样设计、数据构造

3️⃣ Individual

Puck 具有自己的成长轨迹，保留历史形成自己的设计风格

**Benchmark**

- m1: generate new ideas

  生成一个新游戏后会使用中等强度的 OLMCT agent 试玩，初步筛查 可玩性 （游戏是否能推进、玩家能否影响状态、胜利条件是否可能触发等）

- m2: test promision games

  使用 Random Valid Agent、Weak OLMCTS 和 Strong OLMCTS 等不同水平的 agent 多轮试玩，系统评估游戏的平衡性、技巧性、状态多样性和进展情况

为什么能够使用这些 Benchmark 作为评估标准？ Puck 的游戏空间被限制在固定大小的棋盘游戏中（游戏类型固定，游戏空间固定），状态是可枚举、可模拟、agent 水平可区分的，可以通过不同的 agent 测试游戏是否值得继续探究





## ⚠️ Game-O-Matic: Generating Videogames that Represent Ideas

让非专业用户通过“概念图（名词节点 + 动词关系）“输入想表达的主题，自动生成简单街机游戏。

系统将用户输入表示为由**名词节点（实体）**和**动词边（关系）**组成的概念图，例如“Man needs Food”“Food attacks Hunger”。在生成过程中，名词被映射为游戏实体，而动词则映射为预定义的游戏机制模板（Micro-Rhetoric）。每个动词对应多个可能的机制实现，例如“needs”可以被表示为“离开目标对象时持续缩小”，“harms”可以被表示为“产生攻击物并使目标受损”。这些机制模板构成了游戏表达意义的基本单元。

在完成关系到机制的映射后，系统会得到一个由实体和机制组成的半成品游戏。由于这些机制本身较为抽象，尚未包含胜负条件、玩家角色和场景结构，因此系统进一步引入 **Recipe（配方）系统**。Recipe 根据当前游戏状态选择合适的胜利条件、失败条件以及关卡结构模板，并补全玩家控制对象和实体布局，从而将离散的机制组合组织为一个完整可玩的街机游戏。





## ⚠️ Mechanic Maker: Accessible Game Development via Symbolic Learning Program Synthesis

一种基于符号学习与程序合成（Program Synthesis）的游戏机制编辑工具。输入几个游戏状态变化的示例，系统学习并生成对应的规则，创建游戏机制

**不依赖编程方式创建游戏机制的方法**

1️⃣ 可视化编程（Visual Programming）

用户通过图形化元素的方式构建游戏机制，例如 **Scratch**、**UE Blueprints**

这类工具降低了开发门槛，但是没有消除技术障碍，用户仍然需要具备一定的编程思维知识

2️⃣ 带有用户可配置参数的预制组件（Pre-autohored Components）

用户可以通过组合预制组件的方式构建新的游戏，但是显然能够输出的结果会受到预制件的约束。🌰：**Kodu Game Lab**、**Dreams**。

**backend - SLPS**

使用 SLPS（Symbolic Learning Program Synthesis）作为后端。系统把用户提供的了连续游戏帧转化为一组结构化事实（🌰：对象位置、速度、图像、按键输入、对象之间的关系）。系统比较当前规则预测出下一帧与用户实际给出的下一帧之间的差异，不断添加、修改、删除规则，最终学习出一套能够解释这些状态变化的规则系统

**人机协同**

用户每新增或修改一帧，系统都会持续更新已学到的规则，并用半透明的预测结果提示用户“系统认为下一步会发生什么”

用户也可以随时修改示例

**Evaluation**

以 User Study 为主，通过“制定任务的复刻相似性 + 主观问卷评分”的方式验证
