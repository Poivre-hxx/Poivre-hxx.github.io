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

**提出的有关情绪设计的游戏设框架**

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
