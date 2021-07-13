---
title: Python基础02
author: Jianghe
top: true
hide: false
mathjax: false
toc: true
date: 2021-07-05 13:56:20
img:
summary:
    - 控制
    - 循环
categories: Python
tags:
keywords:
---
## 控制流

* if-else

  ```python
  if 表达式:
      do this	
  else:
      do this
  ```

  表达式为真，程序执行缩进后的内容。为假，执行 else 后缩进的内容。

  > Python 中缩进也属于语法

## 循环

* while

  ```python
  while 表达式:
      内容1
      内容2
      cont
  ```

  表达式为真，循环。

* 退出循环

  * break 完全退出
  * continue 跳过本次循环
