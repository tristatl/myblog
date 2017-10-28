---
title: "python 学习笔记(2)"
layout: post
date: 2017-10-28 22:50
image: /assets/images/python.jpg
headerImage: false
tag:
- python
- notes
star: true
category: blog
author: TangLi
description: python learning notes
---

## python 

## 12.函数

### 12.1函数参数：

1.1.位置参数：普通函数定义方法

1.2.默认参数：定义时给定默认值
```python
def enroll(name,gender,age = 6,city = 'beijing'):
	pass
```
调用方式：

1.按顺序提供默认参数 

ps:默认参数要指向不变对象，否则多次调用会改变默认参数的值
```python
enroll('Bob','M',7)
```
2.不按顺序提供部分默认参数时，需要把参数名写上
```python
enroll('Adam','M',city = 'Tianjin')
```
1.3.可变参数：传入的参数个数可变参数前面加了一个*号 ( *args )
```python
def calc(*numbers):
	pass
```
调用方式：

1.list类型调用
```python	
nums = [1,2,3]
calc(*nums)

# *nums把nums这个list的所有元素作为可变参数传进去
```
2.直接调用
```python
calc(1,2,3)
```
1.4.关键字参数 

函数的调用者可以传入任意不受限制的关键字参数

```python
**kw
def person(name,age,**kw):
	pass
```
调用方式：

1.dict类型调用
```python
extra = {'city':'Beijing','job':'Engineer'}
person('jack',22,**extra)
```
2.直接调用
```python
extra = {'city':'Beijing','job':'Engineer'}
person('jack',22,city=extra['city'],job=extra['job'])
```

*可变参数在函数调用时自动组装为一个tuple	
*关键字参数在函数内部自动组装为一个dict

1.5.命名关键字参数

**限制关键字参数的名字**

1.命名关键字参数需要一个特殊分隔符*，*后面的参数被视为命名关键字数

2.如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符*了

```python
def person(name,age,*,city,job):
	pass
def person(name,age,*args,city,job):
	pass
```

1.6.参数组合

可以用必选参数、默认参数、可变参数、关键字参数和命名关键字参数，这5种参数都可以组合使用

参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。
```python
def f1(a,b,c=0,*args,**kw):
	pass
def f2(a,b,c=0,*,d,**kw):
	pass
```

## 13.递归函数

## 14.切片操作符

取一个list或者tuple的部分元素
```python
L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']
#取前三个元素
L[0:3]
#或者0可省略
L[:3] 
>>>['Michael', 'Sarah', 'Tracy']
#倒数切片
L[-2:-1]
>>>['Bob']
#倒数第一个元素的索引是-1
```

可以对字符串操作
```python
'ABCDEFG'[:3]
>>>'ABC'
```

## 14.迭代

1.迭代list或者tuple

2.迭代dict类型
```python
for key in d:
	pass
for value in d.values():
	pass
for k,v in d.items():
	pass
```

3.迭代字符串
```python
for ch in 'ABC':
	pass
```

4.判断是否是可迭代对象
```python
from collections import Iterable
isinstance('abc',Iterable) #str是否可迭代
isinstance([1,2,3], Iterable) #list是否可迭代
```

5.实现带下标的索引

```python
#Python内置的enumerate函数可以把一个list变成索引-元素对

>>>for i, value in enumerate(['A', 'B', 'C']):
...     print(i, value)
...
0 A
1 B
2 C
```		

	


