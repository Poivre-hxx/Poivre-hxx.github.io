---
title: 论文阅读-26-06w2
tags: 
  - Notes
  - LLM
categories: 
  - [Notes]
date: 2026-06-14 20:20:00

---

每周论文阅读笔记~

<!-- more -->

## STORY2GAME: Generating (Almost) Everything in an Interactive Game

让 LLM 先自由生成故事，然后自动生成能够支撑这个故事运行的游戏世界、动作系统和游戏代码，输出一个真正可玩的文字冒险游戏

**Generate a story**

如何生成一个连续的、有因果关系的故事。

1️⃣ LLM 根据故事标题、主要事件、故事目标和世界设定，生成具体事件（粒子化的动作），例如“找到钥匙”、“打败守卫”

2️⃣ 给每个具体事件添加 **preconditions** 和 **effects**，明确这些事件能在什么条件下执行。**preconditions** 分为这几类：基础条件（位置，拥有的物品）；**preceding events** 动作之间的因果关系；**effects** 包含移动位置、设置属性、创建新物体、删除已有物体

**Dynamic player action generation**

当玩家输入了故事主线中没有预先生成的动作时，动态生成该动作需要的物品、属性、前置事件和执行效果，并在必要时更新已有的动作，在收到世界状态和因果逻辑约束下让玩家自由探索

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260613103910279.png" alt="image-20260613103910279" style="width:80%;" />

**Evaluation**

由两部分组成：初始化生成的游戏能不能跑通 & 玩家临时输入的新动作能不能被动态生成并且合理执行

1️⃣ Game World Initialization Evaluation

系统根据故事生成的初始游戏世界和动作代码是否正确。将不同长度的故事按照动作数量分组（e.g. 5-7 actions，8-10 actions），每一组中有8个故事，检查这些故事的每个 action 能否成功编译

2️⃣ Dynamic Action Generation Evaluation

当玩家输入故事主线之外的新动作时，系统能不能动态生成合理的动作逻辑。选取5个故事，从中挑取15个 character / item 生成3个新的动词，评估 **Compilation Success** & **Semantic Success**



## Baba Is AI: Break the Rules to Beat the Benchmark

现有多模态大模型看起来很强，但一旦任务要求它们**理解、修改并组合规则**，能力会明显崩掉。只做了一个测试的benchmark。



## From World-Gen to Quest-Line: A Dependency-Driven Prompt Pipeline for Coherent RPG Generation

提出一个面向 RPG 内容生成的分阶段 LLM pipeline，把世界、角色、任务和扩展剧情串起来。它的目标是解决 LLM 一次性生成复杂游戏叙事时容易不连贯的问题。

**pipeline**

按图中的步骤生成资产

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260616162538743.png" alt="image-20260616162538743" style="width: 60%;" />
