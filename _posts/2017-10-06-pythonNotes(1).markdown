---
title: "python 学习笔记(1)"
layout: post
date: 2017-10-06 19:38
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

解释型语言，代码执行时一行一行的翻译成机器语言

**缺点**：
1.速度慢
2.代码不能加密

**对比**：
c 运行前直接编译成机器码 .obj文件链接之后得到.exe程序

**敲代码**：

* 可以运行控制台输入python进入python环境，直接敲代码，但是不能保存

* 可以在文本编辑器敲，保存成.py文件，进入文件所在目录运行python xx.py 


### 1.输入:
 
python2.7 : raw_input()

python3.6 : input()

eg: name = input()

<font color = 'red' face = 'Times'> ps: input()的类型是str </font>

### 2.输出:

python2.7 : print 或者 print()

python3.6 : print()

可用加号连接  eg: print ('Hello ' + 'World!')

<font color = 'red' face = 'Times'> python3.x 中 用逗号连接   eg:  print('Hello ', 'World!') </font>

### 3.大小写敏感

### 4.注释


* 单行
* 多行
* 中文注释

```python

#这是单行注释

'''
多行注释
'''

#中文注释
coding = utf-8
coding = gbk

```

### 5.使用4个空格缩进

### 6.数据类型


<strong>*a.整数*</strong> 

可以处理任意大小的整数

<strong>*b.浮点数*</strong>

<strong>*c.字符串*</strong>

用单引号或双引号括起来

若文本中有单引号，可以用转义字符

<font color = 'red' face = 'Times'>Python还允许用r''表示''内部的字符串默认不转义</font>

eg:

```pyhton

print('\\\t\\')

#输出：\       \

 print(r'\\\t\\')
 
#输出：\\\t\\

```

<font color = 'red' face = 'Times'>Python允许用'''...'''的格式表示多行内容</font>

eg：

```pyhton

print '''

line1

line2

line3

'''

```

<font color = 'red' face = 'Times'>
在交互式命令行内输入，在输入多行内容时，提示符由>>>变为...，提示你可以接着上一行输入</font>

eg:


```pyhton

>>> print('''line1

... line2

... line3''')

```


<strong>*d.布尔值*</strong>

True   False

可以进行逻辑运算 and or not 运算

<strong>*e.空值*</strong>

None 

<strong>*f.其他：列表，字典，自定义数据类型*</strong>


### 7.变量
 
* 可以是任意数据类型

* 变量名命名： 英文，数字，下划线

* 可以把任意数据类型赋值给变量

* 同一个变量可以反复赋值，且可以是不同类型的

eg:

```python

a = 123  #a是整数

print(a)

a = 'ABC' #a变为字符串

print(a)

```

**变量在内存中的表示：**

eg：

```python
a = 'abc'

print a

b = a

print b

a = 'ABC'

print a

print b

'''
输出：
abc
abc
ABC
abc
'''

```

1.在内存中创建了一个'abc'的字符串。

2.在内存中创建了一个名为a的变量，并把它指向'abc'。

3.变量b指向变量a所指向的数据。

4.内存中创建字符串'ABC'，把a指向'ABC'，但b没有更改。


### 8.常量

用全部大写的变量名表示

PI = 3.14159265359


### 9.除法

传统除法，整数地板除法，浮点数精确除法

* 精确除法： 
from __future__ import division
总是返回真实的商

* 地板除法：操作符 //

* 内建函数： divmod(a,b) 返回 (a//b,a%b)

### 10.取余 

%

### 11.字符串和编码

(1) python3.x 可以直接输出中文
```python
print('中国')
```

(2) 
ord()取字符的整数

chr()取把对应编码转为对应的字符

(3)bytes字节类型表示b''
```python
x = b'ABC'
```
bytes的每个字符占一个字节

encode()编码为指定的bytes

decode()将bytes变为str

(4)

len()计算包含多少个字符

若bytes类型，len()计算的是字节数

(5)

<font color = 'red' face = 'Times'>格式化 类似 C语言，用%实现</font>

%d 整数

%f 浮点数

%s 字符串

%x 十六进制整数

超过两个变量要写括号

```pyhton
PI = 3.1415926
s1 = 72
s2 = 85
r = "Ivy"
print('%s' % r)
print('%.2f' % PI)
print('Hello, %d %d' % (s1,s2))
```

<font color = 'red' face = 'Times'>不确定的类型可以用%s</font>


<p><font color = 'red' face = 'Times'>要输出%用转义字符%%</font></p>













