---
title: Python基础01
author: Jianghe
top: true
hide: false
mathjax: false
toc: true
date: 2021-07-04 12:06:03
img:
summary:
    - 代码风格
    - 运算符
categories: Python
tags:
keywords:
---
## 代码风格建议

1. 使用4个空格缩进
2. 不要混用空格和制表符
3. 函数之间空一行
4. 类之间空两行
5. 字典，列表，元组以及参数列表中，在`，`和`:`后面添加一个空格
6. 在赋值运算符和比较运算符周围要有空格 （参数列表中除外）:`a = f(1, 2) + g(3, 4)`



## 注释

```
# FIXME -- fix these code later
# TODO -- in future you have to do this
```



## 模块

模块是包含我们能复用的代码的文件，包含了不同的函数定义，变量。通常以`.py`为扩展名。Python 在默认安装时就带有大量的模块。

```python
import math	#导入 math 模块
```



## 变量和数据类型

* Python 中不需要为变量指定数据类型

  a = 1 它就是整型；a = 1.1 它就是浮点型；a = "1231" 它就是字符串

* 类型转换

  手动类型转换

  | 类型转换函数  |    转换路径    |
  | :-----------: | :------------: |
  | float(string) | 字符串->浮点值 |
  |  int(string)  | 字符串->整数值 |
  |   str(int)    | 整数值->字符串 |
  |  str(float)   | 浮点值->字符串 |

  

* 关键字和标识符

  ```
  False               def                 if                  raise
  None                del                 import              return
  True                elif                in                  try
  and                 else                is                  while
  as                  except              lambda              with
  assert              finally             nonlocal            yield
  break               for                 not
  class               from                or
  continue            global              pass
  ```

* 单行定义多个变量或赋值

  ```python
  >>> a, b = 45, 54
  >>> a
  45
  >>> b
  54
  >>> a, b = b, a  ## 利用此技巧交换两个变量的值
  >>> a
  54
  >>> b
  45
  ```

  * 利用了 **元组** 这个数据类型。我们是用逗号创建元组。在赋值语句的右边我们创建了一个元组，我们称这为元组封装（_tuple packing_），赋值语句的左边我们则做的是元组拆封 （_tuple unpacking_）。

    ```python
    >>> data = ("shiyanlou", "China", "Python")
    >>> name, country, language = data
    >>> name
    'shiyanlou'
    >>> country
    'China'
    >>> language
    'Python'
    ```


## 运算符

1. 算数运算符

   | Operator | Meaning |
   | :------: | :-----: |
   |    +     |   加    |
   |    -     |   减    |
   |    *     |   乘    |
   |    /     |   除    |
   |    %     |  取余   |
   |    //    |  取整   |
   |    **    |   幂    |

   

2. 比较运算符(关系运算符)

   | Operator | Meaning  |
   | :------: | :------: |
   |    <     |   小于   |
   |    <=    | 小于等于 |
   |    >     |   大于   |
   |    >=    | 大于等于 |
   |    ==    |   等于   |
   |    !=    |  不等于  |

   

3. 逻辑运算符

   | Operator | Meaning |
   | :------: | :-----: |
   |   and    |   与    |
   |    or    |   或    |
   |   not    |   非    |

   * and, or 也称作短路运算符：参数从左向右解析，一旦结果确定就停止。
   * 三者中 not 优先级最高，其次 and


