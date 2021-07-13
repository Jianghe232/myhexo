---
title: Python基础03
author: Jianghe
top: true
hide: false
mathjax: false
toc: true
date: 2021-07-10 17:05:25
img:
summary:
    - 列表
    - 循环
categories: Python
tags:
keywords: 
---
## 列表

列表是 python 的一种数据结构，可以写作中括号之间的一列逗号分割的值，列表的元素不必是同一类型。

```python
>>> a = [1, 232, 12, 'Fedora', 'Archlinux']
>>> a
[1, 232, 12, 'Fedora', 'Archlinux']
```

列表中的元素编号从零开始，可以通过编号（称为索引）访问每一个元素的值：

```python
>>> a[0]
1
>>> a[4]
Fedora
```

列表的索引也可以为负数，表示从列表末尾计数：

```python
>>> a[-1]
Archlinux
```

列表可以被切成不同部分（切片）：

```python
>>> a[0:-1]
[1, 232, 12, 'Fedora']
>>> a[2:-2]
12
```

切片的索引有非常有用的默认值；省略的第一个索引默认为零，省略的第二个索引默认为列表元素个数:

```python
>>> a[:-2]
[1, 232, 12]
>>> a[-2:]
['Fedora', 'Archlinux']
```

切片的索引满足左开右闭原则，左边的值能取到，右边的值不能。

Python 能够优雅地处理那些没有意义的切片索引：一个过大的索引值(即大于列表实际长度)将被列表实际长度所代替，当上边界比下边界大时(即切片左值大于右值)就返回空列表:

```python
>>> a[3: 333]
['Fedora', 'Archlinux']
>>> a[12:]
[]
```

切片操作还可设置步长：

```python
>>> a[1::2]    # 从切片索引 1 到列表末尾，间隔一个元素取值
[232, 'Fedora']

```

列表支持连接这样的操作：

```python
>>> a + [1, 2, 3, 4]
[1, 232, 12, 'Fedora', 'Archlinux']
```

列表允许修改元素：

```python
>>> b = [1, 2, 3 ,4]
>>> b[3] = 5  # 修改第 3 个元素(从零开始)
>>> b
[1 ,2 ,3 , 5]
>>> b[0:2] = ['c', 'd'] # 修改第 0, 1个元素
>>> b
['c', 'd', 3, 5]
>>> b[0:2] = []  # 移除第 0, 1 个元素
>>> b
[3, 5]
>>> b[:] = [] # 清空列表
>>> b
[]
```

检查某个值是否存在于列表:

```python
>>> h = ['hello', 'world']
>>> 'hello' in h
True
>>> 'Fedora' in h
False
```

检查列表是否为空：

```python
if list_name: # 列表不为空
    pass
else:
    pass # 列表不为空
```

列表是允许嵌套的:

```python
>>> a = ['a', 'b', 'c']
>>> d = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1,2,3]]
```



##  循环

### while 循环

```python
while 表达式:
    内容1
    内容2
    cont
```

表达式为真，循环。

### for 循环

python 中的 for 循环可以遍历任何序列（列表，字符串）

```python
>>> a = ['Hello', 'World', '!']
>>> for x in a:
...     print(x)
... 
Hello
World
!
```

我们也可以这样做：

```python
>>> a = [1, 2, 3, 4, 5, 6]
>>> for x in a[::2]:
...     print(x)
... 
1
3
5
```

循环后面还可以添加 else 语句, 它会在循环结束后执行，除非有 break 语句终止了循环

```python
>>> for i in range(0, 5):
...     print(i)
... else:
...     print("Bye bye")
...
0
1
2
3
4
Bye bye
```



 如果需要一个数值序列，内置函数 range() 会很方便，它生成一个等差数列 （并不是列表）

 ```python
 >>> for i in range(5):
 ...     print(i)
 ...
 0
 1
 2
 3
 4
 >>> a = range(1, 5)
 >>> a    # range()返回的不是列表，而是一种1可迭代对象
 range(1, 5)
 >>> list(range(1, 5))    # 通过 list() 转成列表
 [1, 2, 3, 4]
 >>> list(range(1, 15, 3))
 [1, 4, 7, 10, 13]
 >>> list(range(4, 15, 2))
 [4, 6, 8, 10, 12, 14]
 ```



### 退出循环

* break 完全退出循环
* continue 跳过其后的代码，回到循环开始

