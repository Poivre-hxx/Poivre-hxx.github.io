---
title: ai python for beginners笔记
tags: 
  - Notes
  - Python
  - LLM
categories: 
  - [Tutorials, Lec.]
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



## Working with your own data and documents in python

- #### Using files in Python

  ```python
  # 如何读取文件
  f = open("email.txt", "r")
  email = f.read()
  f.close()
  ```

  

- #### Loading and using your own data

  这一章节讲述了①如何查看当前文件夹文件列表；②如何上传文件。

- #### Reading journals from food critics

  这一章节讲述了如何通过for循环批量地让llm进行反馈操作。

- #### Extracting restaurant information from journal entries

  这一章节讲述了①如何使用llm从一个文件中摘出特定信息；②如何写文件。

  ```python
  # 如何写文件
  f = open("highlighted_text.html", "w")
  f.write(html_response)
  f.close()
  ```

  

- #### Vacation planning using CSV files

  这一章节讲述了如何处理csv格式的文件。

  数据使用 list 保存，数据中的每一个字段使用 dictionary 保存。

- #### Turing code blocks into reusable functions

  这一章节讲述了函数。

  ```python
  # python中函数的格式
  def func(para):
      # ...
      # return
  # 如果需要返回数据，加return即可
  ```

  

## Extending Python with Packages and APIs

- #### Using funcitons from a local file

  这一章节讲述了如何使用头文件中的函数。

  ```python
  # 引入头文件的某一函数
  from file import function
  function(15)
  
  # 引入头文件中的所有函数
  # 使用file.func()的形式使用该文件中的函数
  import file
  file.func()
  
  # 引入头文件的所有函数
  # 不要轻易使用这种方式，大咩
  from file import *
  func()
  ```

  

- #### Built-in packages

  这一章节讲述了如何使用python内置的包，包括 math & statistics & random 三个包。

- #### Using third-party packages

  这一章节讲述了①导入头文件时 as 的用法；②如何使用第三方的包，包括 pandas & matplotlib

  ```python
  # 使用as，你将得到一个创建可用于避免键入头文件全称的快捷方式
  import pandas as pd
  # 调用时，直接使用pd即可
  pd.read_csv()
  ```

  

- #### Installing packages

  这一章节讲述了使用 !pip install xxx 的指令下载包体。

- #### APIs to get data from the web

  这一章节讲述了使用API获得实时讯息。

- #### APIs to use AI models

