---
title: Python基础04
author: Jianghe
top: true
hide: false
mathjax: false
toc: true
date: 2021-07-10 17:05:51
img:
summary:
    - 列表
    - 字典
    - 元组
    - 集合
categories: Python
tags:
keywords:
---
## 数据结构

### 1. 列表

中括号之间的一列逗号分割的值，列表的元素不必是同一类型。

* 使用列表的 append(*) 方法可以添加元素到列表末尾

    ```python
    >>> a = [1, 2, 3, 4]
    >>> a.append(6)
    >>> a
    [1, 2, 3, 4, 6]
    ```

* 使用 insert() 方法，插入元素到列表中

    ```python
    >>> a.insert(0,1) # 在列表索引 0 位置添加元素 1
    >>> a
    [1, 1, 2, 3, 4, 6]
    >>> a.insert(1,'x') # 在列表索引 1 位置添加元素 x
    >>> a
    [1, 'x', 1, 2, 3, 4, 6]
    ```

* 使用方法 count(x) 会返回列表中元素 x 的数量

    ```python
    >>> a.count(1)
    2
    ```

* 使用 remove()方法可以移除列表中任意指定值

    ```python
    >>> a
    [1, 'x', 1, 2, 3, 4, 6]
    >>> a.remove(1)
    >>> a  # 可以发现 remove() 只移除了找到的第一个 1
    ['x', 1, 2, 3, 4, 6]
    ```

* 使用 reverse() 反转整个列表

    ```python
    >>> a
    ['x', 2, 3, 4, 6]
    >>> a.reverse()
    >>> a
    [6, 4, 3, 2, 'x']
    ```

* 使用 extend() 将一个列表所有元素添加到另一个列表的末尾

    ```python
    >>> b = [1, 2, 4]
    >>> a = a + b  # 列表拼接
    >>> a
    [6, 4, 3, 2, 'x', 1, 2, 4]
    >>> a.extend(b) # 使用列表方法 extend()
    >>> a
    [6, 4, 3, 2, 'x', 1, 2, 4, 1, 2, 4]
    ```

* 使用 sort() 方法，给列表排序（前提是列表的元素是可比较的）

    ```python
    >>> a
    [6, 4, 3, 2, 'x', 1, 2, 4, 1, 2, 4]
    >>> a.sort() 
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: '<' not supported between instances of 'str' and 'int'
    >>> a = [23, 1, 6, 2, 69, 0]
    >>> a.sort()
    >>> a
    [0, 1, 2, 6, 23, 69]
    ```

* 使用 del 关键字 删除指定位置的列表元素

    ```python
    >>> a
    [0, 1, 2, 6, 23, 69]
    >>> del a[-1]
    >>> a
    [0, 1, 2, 6, 23]
    >>> a[0:1] = [] # 也可以删除位置 0 的元素
    >>> a
    [1, 2, 6, 23]
    >>> a[0] = [] # 这样不能删除
    >>> a
    [[], 2, 6, 23]
    ```

####  将列表用作栈和队列

* 栈是我们通常所说的一种 *LIFO* （Last In First Out 后进先出）数据结构。它的意思是最后进入的数据第一个出来。一个最简单的例子往一端封闭的管道放入一些弹珠然后取出来，如果你想把弹珠取出来，你必须从你最后放入弹珠的位置挨个拿出来。用代码实现此原理：

    ```python
    >>> a = [1, 2, 3, 4, 5, 6]
    >>> a
    [1, 2, 3, 4, 5, 6]
    >>> a.pop() # 列表方法 pop()，弹出列表最后一个元素 ，传入参数 i ，会将第 i 个元素弹出
    6
    >>> a.pop()
    5
    >>> a.pop()
    4
    >>> a.pop()
    3
    >>> a
    [1, 2]
    ```

* *队列* 是一种在末尾追加数据以及在开始弹出数据的数据结构。与栈不同，它是 *FIFO* （First In First Out 先进先出）的数据结构：

    ```python
    >>> a = [1, 2, 3, 4, 5]
    >>> a.append(1)
    >>> a
    [1, 2, 3, 4, 5, 1]
    >>> a.pop(0)	# 使用a.pop(0)弹出列表中的第一个元素
    1
    >>> a.pop(0)
    2
    >>> a
    [3, 4, 5, 1]
    ```


#### 列表推导式

列表推导式为从序列中创建列表提供了一个简单的方法。如果没有列表推导式，一般都是这样创建列表的：通过将一些操作应用于序列的每个成员并通过返回的元素创建列表，或者通过满足特定条件的元素创建子序列。

假设我们创建一个 squares 列表，可以像下面这样创建。

```python
>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

注意这个 for 循环中的被创建（或被重写）的名为  `x` 的变量在循环完毕后依然存在。使用如下方法，我们可以计算 squares 的值而不会产生任何的副作用：。

```python
squares = list(map(lambda x: x**2, range(10)))
```

等价于下面的列表推导式。

```python
squares = [x**2 for x in range(10)]
```

上面这个方法更加简明且易读。

列表推导式由包含一个表达式的中括号组成，表达式后面跟随一个  for 子句，之后可以有零或多个  for 或  if 子句。结果是一个列表，由表达式依据其后面的 for 和  if 子句上下文计算而来的结果构成。

例如，如下的列表推导式结合两个列表的元素，如果元素之间不相等的话：

```python
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

等同于：

```python
>>> combs = []
>>> for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
...
>>> combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

值得注意的是在上面两个方法中的 for 和 if 语句的顺序。

列表推导式也可以嵌套。

```python
>>> a=[1,2,3]
>>> z = [x + 1 for x in [x ** 2 for x in a]]
>>> z
[2, 5, 10]
```

### 3. 元组

元组是由数个 逗号分割的值组成,元组是不可变类型，这意味着你不能在元组内删除或添加或编辑任何值。

```python
>>> a = 'Fedora', 'ShiYanLou', 'Kubuntu', 'Pardus'
>>> a
('Fedora', 'ShiYanLou', 'Kubuntu', 'Pardus')
>>> a[1]
'ShiYanLou'
>>> for x in a:
...     print(x, end=' ')
...
Fedora ShiYanLou Kubuntu Pardus
```

将元组拆封并赋值给多个变量：

```python
>>> a = 1, 'x', 3
>>> a
(1, 'x', 3)
>>> b, c, d = a # 利用元组给多个变量赋值
>>> b
1
>>> c
'x'
>>> d
3
```

要创建只含有一个元素的元组，在值后面跟一个逗号:

```python
>>> a = (123)
>>> a
123
>>> type(a)
<class 'int'>
>>> a = (123, )
>>> b = 321,
>>> a
(123,)
>>> b
(321,)
>>> type(a)
<class 'tuple'>
>>> type(b)
<class 'tuple'>
```

>通过内建函数 `type()` 你可以知道任意变量的数据类型。使用 `len()` 函数可以查询任意序列类型数据的长度。

### 4. 集合

集合是一个无序不重复元素的集。基本功能包括关系测试和消除重复元素。集合对象还支持 union（联合），intersection（交），difference（差）和 symmetric difference（对称差集）等数学运算。

大括号或 set() 函数可以用来创建集合。注意：想要创建空集合，你必须使用 set() 而不是 {}。后者用于创建空字典，我们在下一节中介绍的一种数据结构。

集合的常见操作：

```python
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # 你可以看到重复的元素被去除
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket
True
>>> 'crabgrass' in basket
False

>>> # 演示对两个单词中的字母进行集合操作
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # a 去重后的字母
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # a 有而 b 没有的字母
{'r', 'd', 'b'}
>>> a | b                              # 存在于 a 或 b 的字母
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # a 和 b 都有的字母
{'a', 'c'}
>>> a ^ b                              # 存在于 a 或 b 但不同时存在的字母
{'r', 'd', 'b', 'm', 'z', 'l'}
```

从集合中添加或弹出元素：

```python
>>> a = {'a','e','h','g'}
>>> a.pop()  # pop 方法随机删除一个元素并打印
'h'
>>> a.add('c')
>>> a
{'c', 'e', 'g', 'a'}
```



### 5. 字典

字典是无序的键值对（`key:value`）集合，同一个字典内的键必须是互不相同的。一对大括号 `{}` 创建一个空字典。初始化字典时，在大括号内放置一组逗号分隔的键：值对，这也是字典输出的方式。我们使用键来检索存储在字典中的数据。

```python
>>> data = {'kushal':'Fedora', 'kart_':'Debian', 'Jace':'Mac'}
>>> data
{'kushal': 'Fedora', 'Jace': 'Mac', 'kart_': 'Debian'}
>>> data['kart_']
'Debian'
```

创建新的键值对很简单：

```python
>>> data['parthan'] = 'Ubuntu'
>>> data
{'kushal': 'Fedora', 'Jace': 'Mac', 'kart_': 'Debian', 'parthan': 'Ubuntu'}
```

使用 `del` 关键字删除任意指定的键值对：

```python
>>> del data['kushal']
>>> data
{'Jace': 'Mac', 'kart_': 'Debian', 'parthan': 'Ubuntu'
```

使用 `in` 关键字查询指定的键是否存在于字典中。

```python
>>> 'ShiYanLou' in data
False
```

必须知道的是，字典中的键必须是不可变类型，比如你不能使用列表作为键。

`dict()` 可以从包含键值对的元组中创建字典。

```python
>>> dict((('Indian','Delhi'),('Bangladesh','Dhaka')))
{'Indian': 'Delhi', 'Bangladesh': 'Dhaka'}
```

如果你想要遍历一个字典，使用字典的 `items()` 方法。

```python
>>> data
{'Kushal': 'Fedora', 'Jace': 'Mac', 'kart_': 'Debian', 'parthan': 'Ubuntu'}
>>> for x, y in data.items():
...     print("{} uses {}".format(x, y))
...
Kushal uses Fedora
Jace uses Mac
kart_ uses Debian
parthan uses Ubuntu
```

许多时候我们需要往字典中的元素添加数据，我们首先要判断这个元素是否存在，不存在则创建一个默认值。如果在循环里执行这个操作，每次迭代都需要判断一次，降低程序性能。

我们可以使用 `dict.setdefault(key, default)` 更有效率的完成这个事情。

```python
>>> data = {}
>>> data.setdefault('names', []).append('Ruby')
>>> data
{'names': ['Ruby']}
>>> data.setdefault('names', []).append('Python')
>>> data
{'names': ['Ruby', 'Python']}
>>> data.setdefault('names', []).append('C')
>>> data
{'names': ['Ruby', 'Python', 'C']}
```

试图索引一个不存在的键将会抛出一个 *keyError* 错误。我们可以使用 `dict.get(key, default)` 来索引键，如果键不存在，那么返回指定的 default 值。

```python
>>> data['foo']
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
KeyError: 'foo'
>>> data.get('foo', 0)
0
```

如果你想要在遍历列表（或任何序列类型）的同时获得元素索引值，你可以使用 `enumerate()`。

```python
>>> for i, j in enumerate(['a', 'b', 'c']):
...     print(i, j)
...
0 a
1 b
2 c
```

你也许需要同时遍历两个序列类型，你可以使用 `zip()` 函数。

```python
>>> a = ['Pradeepto', 'Kushal']
>>> b = ['OpenSUSE', 'Fedora']
>>> for x, y in zip(a, b):
...     print("{} uses {}".format(x, y))
...
Pradeepto uses OpenSUSE
Kushal uses Fedora
```
