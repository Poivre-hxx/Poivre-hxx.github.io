---
title: ai python for beginners笔记
tags: 
  - Notes
  - python
  - llm
categories: 
  - [tutorials]
date: 2024-08-12 20:00:00
---

Often ask chatbots for help.

<!--more -->

吴恩达教授的这门课程的特点是传授了将llm融入与学习与工作中的方式，屡次强调了遇到bug和问题时推荐的做法是直接咨询gpt，把使用ai变成一种习惯。

## Basics of AI Python Coding

第一部分主要讲解了python的基本数据类型，以及f string的使用方法。最重要的是，如何与chat交流实现需求或者是修改代码

```python
# 几种数据类型
# 1 String
str = "string"

# 2 Multiline string
mulStr = """multiline
		string"""

# 3 f-strings
fStr = f"12 + 34 = {12 + 34: .0f}"
```



## Automating Tasks with Python

- #### Completing a task list with AI

  讲述了 list 数据类型，可以存放各种数据类型的数据（在同一个 list 中，数据类型可以是不同的），以及 append(), remove() 函数。

  tips：使用 remove() 函数进行删除操作时，只会删除重复数据（如果有的话）的顺序第一个。

- #### Repeating tasks with for loops

  讲述了 for 循环

  ```python
  for task in list_of_tasks:
  	print_llm_response(task)
  ```

  在这一段 for 循环中，每一次遍历时 task 变量存储的值就是 list_of_tasks 中对应 index 中的数据。

  需要注意 cursor 的问题（4个空格）

- #### Prioritizing tasks with dictionaries and AI

  讲述了 dictionaries 数据类型

  ```python
  ice_cream_flavors = {
      "Mint Chocolate Chip": "Refreshing mint ice cream studded with decadent chocolate chips.",
      "Cookie Dough": "Vanilla ice cream loaded with chunks of chocolate chip cookie dough.",
      "Salted Caramel": "Sweet and salty with a smooth caramel swirl and a hint of sea salt."
  }  
  
  # 输出 dictionaries keys
  print(ice_cream_flavors.keys())
  # 输出 dictionaries values
  print(ice_cream_flavors.values())
  
  # 取出某一键值对的值
  cookie_dough_description = ice_cream_flavors["Cookie Dough"]
  
  # 增/改
  ice_cream_flavors["Rocky Road"] = "chocolate ice cream mixed with other ngredients."
  ```

  ①采用键值对的方式存储数据

  ②最外层使用**花括号**而不是方括号；但是，在取出某一个键值对的值时，使用的是**方括号**

- #### Customizing recipes with lists, dictionaries and AI

- #### Comparing data in Python

  讲述了布尔型变量 & 比较运算符 & 逻辑运算符

  - 比较运算符：==、=、<、>、<=、>=

  - 逻辑运算符：and、or

- #### Helping AI make decisions

  将布尔值变量与循环语句相结合，编写条件语句。
