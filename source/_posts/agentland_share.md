---
title: Agentland Festival 2025
tags: 
  - Notes
  - AI Agent
  - LLM
categories: 
  - [Tutorials]
date: 2024-12-24 20:20:00

---



<!-- more -->

## 提示词工程

#### 关注信息、样本、任务三个条件

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/54d6a0e4248442eab85c545d76400bd.jpg" alt="54d6a0e4248442eab85c545d76400bd" style="width:40%;" />

但是，一次性提供过多的信息和样本会导致LLM**失去注意力**

#### 一些与需求关联的情境

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/909acbb0cea23552edeef2d654d0726.jpg" alt="909acbb0cea23552edeef2d654d0726" style="width:40%;" />

#### 游戏中的AI Agent需要突出的点：有鲜明的个性！

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20241224212356798.png" alt="image-20241224212356798" style="width:40%;" />

人物设定八股图

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/f2deeb4cfb981894ca3e80b12170b6d.jpg" alt="f2deeb4cfb981894ca3e80b12170b6d" style="width:40%;" />

#### 选择适合需求的LLM

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/0f99af72cd5aff9cf64960163abc109.jpg" alt="0f99af72cd5aff9cf64960163abc109" style="width:40%;" />

## Unity+LLM

#### 游戏进程&agent之间的相互作用

需要注意两个部分的互相影响，减少游戏的割裂感。

#### 函数调用功能

考虑使用函数调用严格固定LLM的输出格式

#### 不止文字交互

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/4b31f21eeaa86bfe9e688746e4cefe4.jpg" alt="4b31f21eeaa86bfe9e688746e4cefe4" style="width:40%;" />

#### 程序算法 & LLM的选择

 <img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/7745d8d6042a3d51e3c23e31df13ac1.jpg" alt="7745d8d6042a3d51e3c23e31df13ac1" style="width:50%;" />

如何提升LLM的准确度呢？

- 选用更聪明的模型
- 拆解问题：将大问题转化为小问题
- 行为树.降低单个决策的复杂度
- 使用更好的提示词工程

## AI原生游戏

#### AI原生游戏的可能方向

- Master Agent 用于AI NPC

- Multi-Agent

- UGA（user general agent）用户创建专有的agent

- 从MDA的角度出发

  <img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/fd1b59242d3e9bee72f41b25b984407.jpg" alt="fd1b59242d3e9bee72f41b25b984407" style="width:40%;" />

  尝试将AI与M、D结合

#### BDI Prompt

写角色prompt的一种方法（结合角色在不同阶段的特征）

Belief-Desire-Intention

#### PromptGraph

原子化prompt（在单个prompt中完成单件事情的准确性更高）



#### AI游戏目前的问题

1. AI 生成内容堆量的边界
2. 玩家决策的自由度
