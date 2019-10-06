# PY

<center><b><font size = "4">Table of contents</font></b></center>
[TOC]

## 数据类型

### 字符串

py中字符串可用单引号也可双引号，因此字符串中可以包含"或'，如

```python
# LEGAL
'I told my friend, "Python is my favorite language!"'
"The language 'Python' is named after Monty Python, not the snake."
"One of Python's strengths is its diverse and supportive community."
# ILLEGAL
'One of Python's strengths is its diverse community.'  # 肉眼可见的不对劲
```

py2与py3中print函数区别

```python
>>> python2.7
>>> print "Hello Python 2.7 world!" # 本质上我也不知道是什么，感觉是个macro
Hello Python 2.7 world!

# PY3
>>> print("Hello Python interpreter!")  # 本质上是函数
Hello Python interpreter!
```

一些字符串操作

```python
# 大小写转换
strName.title()  # 首字母大写
strName.upper()  # 全大写
strName.lower()  # 全小写

# 字符串合并
first_name = "Ada"
last_name = "lovelace"
full_name = "I am " + first_name + " " + last_name.title()  # "I am Ada Lovelace"

# 删除头尾空格(并没有实际删除)
>>> favorite_language = ' python '
>>> favorite_language.rstrip()
' python'
>>> favorite_language.lstrip()
'python '
>>> favorite_language.strip()
'python'
>>> favorite_language  # 字符串内容还是这样
' python '
```

### 整数与浮点数

```python
# **表示power运算

# PY3中 3/2=1.5；PY2中 3/2=1

# 浮点运算结果包含的小数位数可能是不确定的
## 但是我在Terminal里测发现不会这样？可能是有优化了
>>> 0.2 + 0.1
0.30000000000000004
>>> 3 * 0.1
0.30000000000000004

# str()将数转为字符串
## 小数也🉑
>>> age = 23
>>> message = "Happy " + str(age) + "rd Birthday!"
>>> print(message)
Happy 23rd Birthday!
## 但是这里小数会有这个现象(1.000-->1.0)，应该是存储的问题，计算机无法区分.00和.0
>>> age = 23.00
>>> message = "Happy " + str(age) + "rd Birthday!"
>>> print(message)
Happy 23.0rd Birthday!


```

## 列表

### 创建、访问、修改、添加、删除

```python
>>> bicycles = ['trek', 'cannondale', 'redline', 'specialized']
>>> print(bicycles)
['trek', 'cannondale', 'redline', 'specialized']

>>> bicycles = ['trek', 'cannondale', 'redline', 'specialized']
>>> print(bicycles[0])
trek

# -n表示倒数第n个元素
>>> bicycles = ['trek', 'cannondale', 'redline', 'specialized']
>>> print(bicycles[-3].title())
Cannondale
## 但是不能溢出，比如[-5]就会报错

# 修改元素
array[0] = val

# 添加元素
## 末尾 append (没返回值(print(list.append('c'))会输出"None"))
>>> motorcycles = ['honda', 'yamaha', 'suzuki']
>>> print(motorcycles.append('ducati'))
>>> print(motorcycles)
None
['honda', 'yamaha', 'suzuki', 'ducati']

## 中间插入 insert (没返回值(print(list.insert(x, 'c'))会输出"None"))
>>> motorcycles = ['honda', 'yamaha', 'suzuki']
>>> print(motorcycles.insert(0, 'ducati'))
>>> print(motorcycles)
None
['ducati', 'honda', 'yamaha', 'suzuki']

# 删除元素
## 用del
>>> motorcycles = ['honda', 'yamaha', 'suzuki']
>>> del motorcycles[0]
>>> print(motorcycles)
['yamaha', 'suzuki']

## 用pop(永久弹出/有返回值)
### 没加参数弹最后一个
>>> motorcycles = ['honda', 'yamaha', 'suzuki']
>>> print(motorcycles.pop())  #返回值是个元素
>>> print(motorcycles)
suzuki
['honda', 'yamaha']
### 加了参数弹该位置的元素
>>> motorcycles = ['honda', 'yamaha', 'suzuki']
>>> print(motorcycles.pop(1))  #返回值是个元素
>>> print(motorcycles)
yamaha
['honda', 'suzuki']

## 用remove(无返回值(print(list.remove())会报错))
>>> motorcycles = ['honda', 'yamaha', 'suzuki']
>>> motorcycles.remove('yamaha')  #参数也可以是变量
>>> print(motorcycles)
['honda', 'suzuki']
### 若有多个重复的只会删掉第一个
>>> motorcycles = ['1', '2', '1']
>>> motorcycles.remove('1')
>>> print(motorcycles)
['2', '1']
### 没有的会报错
>>> motorcycles = ['1', '2', '3']
>>> motorcycles.remove('4')
File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list

```

### 组织

```python
# 永久排序
>>> listName.sort()
>>> print(listName)

# 临时排序
>>> print(sorted(listName))

# 永久反转
>>> listName.reverse()

# 获取长度
>>> cars = ['bmw', 'audi', 'toyota', 'subaru']
>>> len(cars)
4


```

### 索引错误



## 列表操作

### 循环

```python
>>> magicians = ['alice', 'david', 'carolina']
>>> for magician in magicians:
>>>     print(magician)

# 此处，显然magician不是仅在for中作用的临时变量
>>> magicians = ['alice', 'david', 'carolina']
>>> for magician in magicians:
>>> 	print(magician.title() + ", that was a great trick!")
>>> print("I can't wait to see your next trick, " + magician.title() + ".\n")
Alice, that was a great trick!
David, that was a great trick!
Carolina, that was a great trick!
I can't wait to see your next trick, Carolina.

>>> for value in range(1,3)
>>> 	print(value)

# 用list(range())生成列表
# list(tup) ## tup为要转换为列表的元组
# range(start, stop[, step])

>>> numbers = list(range(1,6))
>>> print(numbers)
[1, 2, 3, 4, 5]

>>> even_numbers = list(range(2,11,2))
>>> print(even_numbers)
[2, 4, 6, 8, 10]

## 复杂操作
>>> squares = []
>>> for value in range(1,11):
>>> 	square = value**2
>>> 	squares.append(square)
>>> print(squares)
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]


```

