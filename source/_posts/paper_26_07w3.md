---
title: 论文阅读-26-07w3
tags: 
  - Notes
  - LLM
categories: 
  - [Notes]
date: 2026-07-11 20:20:00


---

每周论文阅读笔记~

<!-- more -->每周论文阅读笔记~

## When Scaffolding Breaks: Investigating Student Interaction with LLM-Based Writing Support in Real-Time K-12 EFL Classrooms

制作了一个LLM写作工具，发现统一分布式的AI框架有利有弊：虽然能够即时提升学生作文语法正确率、减轻教师答疑负担，但是低水平的学生会丧失写作动力、过度依赖ai并且知识留存率低，高水平学生能够借助ai创作；ai能够改变课堂生态，内向学生不再向老师提问、同伴互助减少，学生语法短板被ai修改掩盖，教师难以掌握真实情况

![The interface design of WriteAid](https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20260715203357283.png)

1. 模块 A：展示课程的写作主题、学习目标以及必须使用的语法和内容要求，帮助学生明确任务
2. 模块 B：作文编辑区，学生可以在其中直接撰写和修改英语作业
3. 模块 C：AI 对话交互面板，可以通过不同标签页选择示例作文、与ai协作造句、询问词汇或语法概念，检查语法错误，通过聊天方式获得相应的写作支持

## The Procedural Content Generation Benchmark: An Open-source Testbed for Generative Challenges in Games

提出了一个开源的“程序化内容生成基准”，目标是为游戏中的生成算法建立一套统一评测平台。该基准包含 12 类生成任务，覆盖迷宫、平台关卡、地下城、建筑、弹幕、文字游戏以及游戏规则等内容，并从质量、生成结果的多样性和对设计参数的可控性三个维度进行评价。作者还用随机生成、进化策略和遗传算法作为基线进行实验，结果表明不同任务的难度差异很大：大型关卡如《超级马里奥》和《淘金者》较难生成，而进化算法总体优于随机方法；同时，优化质量、可控性和多样性之间存在明显权衡。文章认为，这一基准可用于更规范地比较不同 PCG、强化学习、机器学习和大模型生成方法，但基准得分高只代表满足当前预设指标，并不等于生成内容真正适合所有玩家或已经解决了该类生成问题。

#### **related work**

⭕️ PCG in games

| 发展阶段 | 核心变化 | 代表应用/方法 | 主要意义 |
| --- | --- | --- | --- |
| Early PCG（2000前） | - | 1980 年《Rogue》的无限关卡；1984 年《Elite》的大型星系 | 主要用于突破硬件和存储限制，扩大游戏规模、提高重复可玩性 |
| Search-based PCG（2000s-2010s） | 将内容视为候选解，通过遗传算法、进化策略或随机优化，使内容满足评价函数 | 2009 年《Galactic Arms Race》通过进化方法生成武器；随后出现基于搜索的《Super Mario Bros.》关卡生成，以及面向设计师的混合主动式关卡建议系统 | PCG从“随机生成”转向“面向目标优化”，能够对可玩性、难度和功能性进行约束 |
| Experience-driven PCG（2010s） | 将搜索式生成与玩家模型结合，根据期望的玩家体验生成内容 | 通过玩家模型生成符合目标难度、趣味性或情绪轨迹的 Mario 关卡；例如依据 Raph Koster 的乐趣理论最大化体验差异 | 评价目标从“内容是否可用”扩展到“玩家会获得怎样的体验” |
| PCG through QD（2015-2020） | 不再只寻找一个最优解，而是同时搜索一组高质量且行为特征不同的解 | MAP-Elites 等 QD 方法逐渐被用于生成新型关卡、弹幕模式、2D/3D 飞船和 Minecraft 建筑 | 将“高质量”与“有意义的多样性”同时纳入生成目标，更接近创意辅助需求 |
| PCG via machine learning, PCGML（2016-2020） | 从已有游戏内容中学习数据分布，再快速生成新的关卡或资产 | 使用 GAN、视觉模型、Wave Function Collapse 等方法学习和生成游戏关卡 | 将主要计算成本转移到训练阶段，提高生成速度，但依赖足够的训练数据 |
| PCG via reinforcement learning, PCGRL（2020s） | 将生成过程建模为强化学习任务，智能体通过奖励逐步修改和构造内容 | PCGRL 框架通过奖励训练智能体生成关卡，并支持在线或迭代式生成 | 不依赖大量现成关卡数据，可直接围绕目标奖励学习生成策略 |
| PCG via generative AI methods（2022-） | 使用大语言模型和多模态生成模型处理游戏规则、任务、文本、代码和结构化关卡 | LLM 被用于生成游戏规则、任务、关卡描述、代码和可执行原型；也开始与传统搜索、验证和游戏引擎结合 | PCG的内容范围进一步扩展，但稳定性、可控性和自动验证成为新的难题 |

⭕️ Game AI Benchmarks

PCG基准与游戏智能体基准之间的一个关键区别在于：创意系统输出的评价标准往往定义不明确、难以测量，并且具有较强的主观性。

#### PCG Benchmark

[PCG Benchmark 结构](https://app.notion.comhttp://![](https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/20260717171453084.png))

PCG Benchmark 结构

从quality、diversity、controllability三个方面评价生成内容

Quality 用于衡量生成内容是否满足特定任务的功能性要求，例如关卡是否可玩、地图是否可解；Diversity 用于衡量生成结果之间的差异程度，避免生成器仅产生大量相似内容；Controllability 用于评价生成器是否能够根据设计者提供的控制参数生成符合预期的内容。该框架并**不固定具体评价标准**，而是针对不同生成任务定义对应的评估函数，使不同类型的游戏内容生成算法能够在统一接口下进行比较。

![6种生成方法在 Binary、Sokoban、Zelda 三个任务上的表现](https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/20260717173306364.png)

6种生成方法在 Binary、Sokoban、Zelda 三个任务上的表现

左图表示Feasible Solutions（可行解数量，反应能不能正确生成内容），GA > Constructive > ES > Random > Llama 3.2 > Deepseek-r1

右图表示Unique Solutions（独特解数量，反应生成是否有多样性），GA ≈ ES > Random > Constructive > Llama 3.2 > Deepseek-r1

## Agentic PCG: Procedural Content Generation via  Tool-using LLMs

提出了一种基于“工具调用型 LLM Agent”的程序化内容生成框架，LLM 不直接生成内容，而是调用 PCG 工具；把已有 PCG 方法变成 Agent Skill；加入自然语言设计意图

#### Methods

![](https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/20260717192845994.png)

将关卡生成建模为一个**类似强化学习的迭代优化过程**。Agent 每轮接收当前关卡、评价指标、可用工具以及历史反馈，然后输出结构化 JSON，包括修改理由（rationale）和具体工具调用（tool calls），或者输出 STOP 结束生成。系统执行这些操作后，通过 PCG Benchmark 对候选关卡进行评价，并根据评价结果决定是否接受修改，从而形成：Observe → Reason → Tool Call → Evaluate → Accept/Reject → Repeat的优化流程

Tool：1️⃣ 低层编辑工具，例如修改单个 tile、绘制线条、填充矩形区域等，使 Agent 可以进行精细调整；2️⃣ 高层算法工具，例如随机生成、DFS 迷宫生成、BSP 房间生成、Cellular Automata、WFC 等，使 Agent 可以直接调用已有生成算法完成大规模结构调整。

优化和反馈机制：通过 PCG Benchmark 计算综合分数，该分数由四部分组成：**可控制指标匹配度、关卡可解性、结构有效性以及修改惩罚**。其中，指标匹配用于满足设计目标（例如路径长度、敌人数量），可解性保证关卡能够运行，结构有效性保证实体数量和布局合法，而修改惩罚限制 Agent 对已有地图进行过大的破坏。最终系统采用类似爬山搜索（hill climbing）的接受策略：更优结果直接接受，较差结果以一定概率探索接受，被拒绝的结果作为负反馈提供给后续 Agent 推理。

#### Evaluation

模型能力大致排名：Claude > Gemini > GPT > Qwen

#### Prmopt

```jsx
You are an AI agent optimizing a binary maze level.Your goal is to achieve a longest shortest path of ~256 while maintaining exactly 1 connected region.

## Current Level (rows are y, columns are x, 0-indexed):
```
....................................############################
##.............#########...########.############################
##..................................############################
###............#################################################
###.......######################################################
########..######################################################
########..####.#################################################
.............#.#################################################
.#######.....#.#.###############################################
.########.####.#.###############################################
.########......#.###############################################
.#############.#....############################################
.#############.#.##.############################################
.###...........#..#.############################################
.################.#.############################################
........##...........................###########################
.######.............##############.#############################
.######.............##############.#############################
....................##############.#############################
#######.............##############.#############################
#######.............##############.#############################
```
Legend: '.' = empty (passable), '#' = wall (blocked)
## Current Level Metrics:
 - path: 92 (goal: ~256) 
 - num_connected_regions: 1 (goal: ~1) 
 - traversable: yes
 ## Score: -164.00 (path=92, regions=1, w_path=1.0, w_regions=10.0)
 
 ## Termination Status:
 Changes: 410/4096 (10.0% used, 3686 remaining)
 
 ## Available Tools:
 
 ## calculate_stats
 Description: Calculates statistics for the current level including path (the longest shortest path between any two empty tiles) and num_connected_regions (number of separate connected regions of empty tiles). Returns metrics, targets, and gaps to help guide optimization. 
 Parameters: 
 - level_string (string) (optional): Optional: ASCII level representation to evaluate. If not provided, evaluates the current level.
 
 ## place_tile 
 Description: Places a tile on the level. Supported tile types: empty, wall. Supports three modes:
 - 'single': place one tile at (y, x). 
 - 'line': place a straight horizontal or vertical segment. Specify the endpoint using ONE of: (a) direction ('up'/'down'/'left'/'right') + length, (b) end_y + end_x for an explicit endpoint, (c) end_x only (end_y defaults to y, drawing a horizontal line), or (d) end_y only (end_x defaults to x, drawing a vertical line). Example horizontal line: {mode:'line', y:5, x:0, end_x:10} Example vertical line: {mode:'line', y:0, x:3, end_y:8}
 - 'rect': fill a rectangle from (y, x) to (end_y, end_x). Requires end_y and end_x. 
 Parameters: 
 - mode (string) (required): Mode of operation: 'single' for one tile, 'line' for a segment, 'rect' for rectangle 
 - tile_type (string) (required): Type of tile to place: empty, wall 
 - y (integer) (required): Row coordinate (0-indexed). For line/rect, this is start_y. 
 - x (integer) (required): Column coordinate (0-indexed). For line/rect, this is start_x. 
 - end_y (integer) (optional): Ending row coordinate. Required for rect mode. For line mode: if only end_y is given (no end_x), draws a vertical line from y to end_y at column x. If both end_y and end_x are given, draws a line from (y,x) to (end_y,end_x). 
 - end_x (integer) (optional): Ending column coordinate. Required for rect mode. For line mode: if only end_x is given (no end_y), draws a horizontal line from x to end_x at row y. If both end_y and end_x are given, draws a line from (y,x) to (end_y,end_x). 
 - direction (string) (optional): Direction to extend from (y,x) --- alternative to end_y/end_x for line mode. Must be paired with 'length'. - length (integer) (optional): Number of tiles to place in 'direction' (for line mode with direction). Must be paired with 'direction'. 
 - filled (boolean) (optional): For rect mode: if true, fill entire rectangle; if false, only draw border'
 
 ## generate_bsp
 Description: Ignores the current level and generates a new room-and-corridor layout using Binary Space Partitioning. Recursively splits the space into rectangles, carves a room inside each partition, and connects adjacent rooms with corridors. Works regardless of the current level state. Output has open rectangular rooms linked by narrow passages --- typically 1 connected region with moderate path lengths. Increase splits for more, smaller rooms (longer paths); decrease for fewer, larger rooms (shorter paths). Calling this again discards all previous progress.
 Parameters: 
 - splits (integer) (optional): Number of recursive splits (default 3) 
 - min_width (integer) (optional): Minimum partition width (default 5) 
 - min_height (integer) (optional): Minimum partition height (default 5)
 
 ## generate_ca 
 Description: REFINEMENT tool: evolves the CURRENT level in-place using cellular automata rules --does NOT discard previous work. Each iteration, every tile checks its 8 neighbors (Moore neighborhood): if wall-neighbor count <= solid_count the tile becomes wall; if empty-neighbor count >= empty_count the tile becomes empty. Effect: smooths noisy layouts into organic cave-like shapes by removing isolated tiles and filling small holes. IMPORTANT: has no effect on a blank (all-empty or all-wall) level --- needs a mix of wall and empty tiles to work. Best used after generate_random or generate_digger to smooth rough output. Fewer iterations = subtle smoothing; more iterations = stronger smoothing toward large blobs. 
 Parameters: 
 - iterations (integer) (optional): Number of CA iterations (default 10) 
 - solid_count (integer) (optional): Neighbor threshold for becoming/staying wall (default 2) 
 - empty_count (integer) (optional): Neighbor threshold for becoming empty (default 6)
 
 ## generate_connect
 Description: REFINEMENT tool: post-processes the CURRENT level in-place to fix connectivity --does NOT discard previous work. Finds all connected empty regions, removes regions smaller than smallest_region_size (fills them with wall), then connects remaining regions with straight corridors. Effect: reduces num_connected_regions toward 1 and increases path length by linking previously isolated areas. IMPORTANT: has no effect on a blank (all-empty) level since it is already one region. Best used as a final pass after any generator (especially generate_random, generate_ca, or generate_digger) to ensure the level is fully connected. Can also be called after manual place_tile edits that may have split the level.
 Parameters: 
 - smallest_region_size (integer) (optional): Minimum region size to keep; smaller regions become wall (default 5)
 
 ## generate_digger 
 Description: Ignores the current level and generates a new cave layout using a random-walk digger. Starts from an all-solid grid at a random position and carves empty tiles by walking in random directions, occasionally carving rooms. Stops when the fraction of empty tiles reaches stop_size. Works regardless of the current level state. Output is a single naturally-connected cave with organic, irregular shape --- guaranteed 1 connected region. Higher stop_size = more open space (shorter paths); lower stop_size = tighter tunnels (longer paths). Follow up with generate_ca to smooth rough edges. Calling this again discards all previous progress.
 
 Parameters: 
 - change_prob (number) (optional): Probability of changing walk direction (default 0.15) 
 - room_prob (number) (optional): Probability of carving a room instead of a single tile (default 0.01) 
 - room_size (integer) (optional): Half-size of carved rooms (actual size is 2*room_size+1, default 3) 
 - stop_size (number) (optional): Stop when empty tile fraction reaches this value (0.0-1.0, default 0.3)
 
 ## Instructions: 
 1. Analyze the current level and its metrics 
 2. Plan edits to improve the score (move metrics toward goals described above) 
 3. Execute tool calls to modify the level 
 4. You may call calculate_stats to evaluate changes before committing
 
 ## Response Format: 
 Respond with a JSON object of one of these types:
 
 ### STEP - To execute tools: 
 ```json 
 {  "type": "STEP", "rationale": "explanation of your reasoning", "plan": "high-level plan for improvement", "tool_calls": [ {"tool_name": "place_wall_segment", "parameters": {...}}, {"tool_name": "calculate_stats", "parameters": {}} ], "acceptance_hint": "hint about whether to accept changes" } 
```

 ### PROPOSE_SKILL - To propose a new tool:
 ```
 json {  "type": "PROPOSE_SKILL", "rationale": "why this tool would help", "skill_spec": { "name": "tool_name", "description": "what it does", "parameters": {}, "implementation_hint": "how to implement" } } 
 ```

 ### STOP - To terminate optimization: 
 ```
 Json {  "type": "STOP", "rationale": "why stopping now", "final_notes": "observations about the result" } 
 ```

 Respond with ONLY the JSON object, no additional text. 
```

```jsx
You are an AI agent optimizing a Super Mario Bros level. Your goals are: 
1. Create a completable level (Mario can reach the end) 
2. Have proper tube/pipe structures (tubes must span 2 tiles properly) 
3. Achieve ~3 enemies killed, ~5 jumps performed, ~3 coins collected during gameplay simulation 
4. Minimize horizontal noise for smoother gameplay 
5. Add coins and question blocks for rewards

## How Evaluation Works 
A Mario AI agent (A* solver) plays your level from left to right. The metrics below reflect the **gameplay outcome**, not the tile layout:
- **enemies_killed**: Number of enemies the player stomped or hit with shells during play. Enemies that fall off cliffs on their own do NOT count. Simply placing enemy tiles does not guarantee kills --- enemies must be on the player's path where they cannot be avoided. 
- **coins_collected**: Number of coins the player picked up during play. Coins must be on or near the traversal path. 
- **jumps**: Number of voluntary jumps the player performed from the ground. Bouncing off enemies (stomp bounces) does NOT count. More gaps and elevated platforms force more jumps.
- **complete**: Whether the player reached the end flag (1.0 = yes).

To increase enemies_killed, place enemies on narrow ground platforms that the player must cross (not on optional platforms). To increase coins_collected, place coins along the main path or on mandatory platforms. To increase jumps, create gaps in the ground and elevated platforms that force the player to jump from the ground --- enemy stomps do not count as jumps.

## Current Level (rows are y, columns are x, 0-indexed):
```
................................
................................
................................
................................
................................
...................GGGG.G.......
...................BBBB.BB......
................................
.................C..............
..........GCGCGG...........GC...
..........BBB.BB..........BBB.?.
.........................X......
...C.TT..C...............X....C.
.CGCGTT..................X.GGGG.
XXX.XXX.X.................XXXX.X
```
Legend: '.' = empty, 'X' = solid floor, 'L' = ladder, 'B' = brick, '?' = question block, 'T' = tube, 'C' = coin, 'G' = goomba, 'K' = koopa, 'Y' = spiny

## Simulation Trajectory Map (last evaluation)
```
................................
................................
....................***.........
...................**..*........
..................**....*.......
..................*.....*.......
.............*...!.GGGG.G**....*
.............**.**.BBBB.BB*...**
........**..*.*.*.........*..*..
.......**.*.*.*.*C.........*.*..
...**..*..GCGCGG...........GC...
..*..*.*..BBB.BB..........BBB.?.
.**..**..................X......
**.C.TT..C...............X....C.
.!GCGTT..................X.GGGG.
XXX.XXX.X.................XXXX.X
```
Legend: '*' = Mario's path (empty tiles only), '!' = enemy killed here Note: Enemies move during simulation. '!' marks where Mario was when the kill happened, not the enemy's spawn position. Enemies that were avoided or not reached are still shown at their original tile positions (G/K/Y).

## Current Level Metrics: 
- complete: 100.0% (goal: 100%) 
- enemies_killed: 2 (goal: ~3) 
- coins_collected: 3 (goal: ~3) 
- jumps: 4 (goal: ~5) [stomp bounces: 2, not counted] - tube_issues: 0 (goal: 0) 
- empty_ratio: 88.5% 
- noise: 0.363 (goal: minimize) 
- simulation: ran 
- playable: yes

## Simulation Results 
The Mario AI agent played through the level. Here is what happened: 
- Completion: 100% (reached the flag) 
- Enemies killed: 2 (goomba stomped at tile [1, 14], goomba stomped at tile [17, 6]) 
- Coins collected: 3 
- Jumps performed: 4 (stomp bounces: 2, not counted as jumps) 
- Mario traversed from column 0 to column 31

Enemy behavior during simulation: 
- Goomba (G): Walks horizontally, reverses on walls. Speed ~1.75 px/frame.
- Koopa (K): Green koopa walks horizontally, falls off cliffs. Becomes a kickable shell when stomped. 
- Spiny (Y): Walks horizontally like goomba but CANNOT be stomped (hurts Mario). Must be avoided or killed with shell/fireball.

## Score: 70.00 (complete=100%, tubes=0, enemies_killed=2, coins_collected=3, jumps=4)  

## Termination Status: 
Changes: 89/1536 (5.8% used, 1447 remaining)

## Available Tools:  

## place_tile 
Description: Places a tile on the level. Supported tile types: empty, solid, ladder, brick, question, tube, coin, goomba, koopa, spiny. Supports three modes:
- 'single': place one tile at (y, x). 
- 'line': place a straight horizontal or vertical segment. Specify the endpoint using ONE of: (a) direction ('up'/'down'/'left'/'right') + length, (b) end_y + end_x for an explicit endpoint, (c) end_x only (end_y defaults to y, drawing a horizontal line), or (d) end_y only (end_x defaults to x, drawing a vertical line). Example horizontal line: {mode:'line', y:5, x:0, end_x:10} Example vertical line: {mode:'line', y:0, x:3, end_y:8}
- 'rect': fill a rectangle from (y, x) to (end_y, end_x). Requires end_y and end_x. Parameters:
Parameters:
- mode (string) (required): Mode of operation: 'single' for one tile, 'line' for a segment, 'rect' for rectangle 
- tile_type (string) (required): Type of tile to place: empty, solid, ladder, brick, question, tube, coin, goomba, koopa, spiny 
- y (integer) (required): Row coordinate (0-indexed). For line/rect, this is start_y. 
- x (integer) (required): Column coordinate (0-indexed). For line/rect, this is start_x. 
- end_y (integer) (optional): Ending row coordinate. Required for rect mode. For line mode: if only end_y is given (no end_x), draws a vertical line from y to end_y at column x. If both end_y and end_x are given, draws a line from (y,x) to (end_y,end_x). 
- end_x (integer) (optional): Ending column coordinate. Required for rect mode. For line mode: if only end_x is given (no end_y), draws a horizontal line from x to end_x at row y. If both end_y and end_x are given, draws a line from (y,x) to (end_y,end_x). 
- direction (string) (optional): Direction to extend from (y,x) --- alternative to end_y/end_x for line mode. Must be paired with 'length'. 
- length (integer) (optional): Number of tiles to place in 'direction' (for line mode with direction). Must be paired with 'direction'. 
- filled (boolean) (optional): For rect mode: if true, fill entire rectangle; if false, only draw border

## Instructions:
1. Ensure the level is completable (Mario can traverse from start to end) 
2. Place solid ground (X) for Mario to walk on 
3. Add platforms using bricks (B) and question blocks (?) 
4. Place enemies (G, K, Y) on solid ground along the player's path --- enemies the player can avoid will not count 
5. Place coins (C) along the main traversal path --- coins the player never reaches will not count 
6. Avoid creating impossible jumps or dead ends

## Response Format: 
Respond with a JSON object of one of these types:

### STEP - To execute tools: 
```
json {  "type": "STEP", "rationale": "explanation of your reasoning", "plan": "high-level plan for improvement", "tool_calls": [ {"tool_name": "place_tile", "parameters": {"mode": "single", "tile_type": "solid", "y": 15, "x": 1}} ], "acceptance_hint": "hint about whether to accept changes" } 
```

### PROPOSE_SKILL - To propose a new tool: 
```
json {  "type": "PROPOSE_SKILL", "rationale": "why this tool would help", "skill_spec": { "name": "tool_name", "description": "what it does", "parameters": {}, "implementation_hint": "how to implement" } }

```

### STOP - To terminate optimization: 
```
json {  "type": "STOP", "rationale": "why stopping now", "final_notes": "observations about the result" }
```

Respond with ONLY the JSON object, no additional text.  

## Extra Instruction: 
Make level with two elevated platforms, requires travelling to upper platform to solve
```

```jsx
[Previous step result: REJECTED - rejected (score: 70.00 -> 50.00)] 
Metrics change from your last edit: 
enemies_killed: 2 → 3 (target: ~3) 
coins_collected: 3 → 1 (target: ~3) 
jumps: 4 → 3 (target: ~5) 
complete: 100.0% → 100.0% (target: ~1.0) 
tube_issues: 0 → 0 
noise: 0.363 → 0.178 
Tool results: 16 calls, 16 succeeded, 102 tiles changed
```