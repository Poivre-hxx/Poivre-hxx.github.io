---
title: 论文阅读-26-07w1
tags: 
  - Notes
  - LLM
categories: 
  - [Notes]
date: 2026-07-04 20:20:00

---

每周论文阅读笔记~

<!-- more -->

## SDD（Spec-Driven Development）

规范驱动开发，核心理念是**先定义规则，再进行实现（先写技术方案再开发）**

几个单词的拆解理解：

- Spec。解决“要做什么、不要做什么”的问题。它会写清楚用户场景、功能边界、异常情况和验收标准。这样 AI 在实现时就不需要自己猜需求，也不容易把无关逻辑一起改掉。
- Design。解决“应该怎么做”的问题。这里会说明我们的技术方案、模块影响范围、数据流、接口依赖和兼容性要求等。
- Tasks。解决“先做哪一块、做到什么程度”的问题。它会把需求拆成可执行、可验证的小任务。AI 每次只处理一个明确范围，改动就更容易收敛，更方便人做 review 和回滚。

**工具选型** - OpenSpec

有以下几个核心文件

| 文件        | 作用                                                     |
| ----------- | -------------------------------------------------------- |
| spec.md     | 定义需求、边界、行为、约束、验收标准，作为AI的长期上下文 |
| design.md   | 记录具体的技术方案与实现设计                             |
| proposal.md | 描述背景、目标、影响面与推进理由                         |
| tasks.md    | 任务拆解与执行进度参考                                   |

**工作流程**

![image-20260630150220858](https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260630150220858.png)

**整体架构**

![image-20260630150305671](https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260630150305671.png)



## Art or Artifice? Large Language Models and the False Promise of Creativity

提出一个专家驱动的创意写作评价框架 TTCW，证明当前 LLM 写出的短篇小说虽然表面流畅，但在原创性、复杂性和文学创造力上明显弱于专业作家；并且 LLM 也不能可靠地评价创意写作

**RQs**

1️⃣ 当专家评价者对同一批故事进行测试时，他们之间是否存在一致意见？

2️⃣ 人类写作的故事是否比 LLM 生成的故事更可能通过单个 TTCW 测试？如果是，哪些测试体现出的差距最大？

3️⃣ 不同 LLM 是否在不同的 Torrance 创造力维度上表现更好？

**TTCW 的四个设计原则**

1️⃣ 借用 TTCT 的四个创造力维度评估

2️⃣ 作品导向，不关注作品的创作过程，LLM 和既有文本的创作过程很难观察

3️⃣ 二元评价的方式 + 开放式理由解释辅助

4️⃣每个问题彼此独立，通过的测试越多，作品的创造力越高

------

**Torrance Test of Creative Thinking (TTCT)**

一个创造力测试框架，通过一系列开放式的任务，观察人类在面对不寻常问题时，能否产生多样、新颖、丰富的想法。

测评的核心是 **divergent thinking**（发散思维）

有四个核心的维度：

<img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260701113104215.png" alt="image-20260701113104215" style="width:50%;" />

**Consensual Assessment Technique（CAT）**

一个作品是否有创造力，最有效的判断方式，是让该领域的专家独立评价，然后看专家之间是否达成共识



## Luminate: Structured Generation and Exploration of Design Space with Large Language Models for Human-AI Co-Creation

让LLM先生成“设计维度”，再在这些维度构成的空间中生成内容

**divergent-convergent thinking**

divergent：发散思维，也称横向思维，是指针对某个问题或任务生成多个独特想法或解决方案的过程

convergent：收敛思维，也称纵向思维，是指针对各个想法和可能性进行整合、综合与评估，最终形成一个单一的创造性结果的过程

**design space**

设计空间表示为一个概念性的“可能性空间”，广义上可以理解为由各种想法、设计、概念或解决方案构成的集合。设计空间通常被表示为笛卡尔空间，其中可能的变化分布在设计的不同维度之中，而不同变化则对应这些维度上的不同取值
