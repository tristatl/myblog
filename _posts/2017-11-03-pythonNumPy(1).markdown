---
title: "numpy 学习笔记"
layout: post
date: 2017-10-28 22:50
image: /assets/images/python.jpg
headerImage: false
tag:
- python
- numpy
- notes
star: true
category: blog
author: TangLi
description: python numpy learning notes
---

##  Numpy

Numpy 是一个开源的Python科学计算基础库。
* 一个强大的N维数组对象ndarray
* 广播功能函数
* 整合C/C++/Fortran代码的工具
* 线性代数，傅里叶变换，随机数生成等功能
* 是SciPy,Pandas等数据处理或科学计算库的基础

### 1.Numpy的引用

```python
import numpy as np  #引入模块的别名
```

### 2.N维数组对象： ndarray

np.array()生成一个ndarray数组

轴(axis)：保存数据的维度。 在轴上，该维度的数据保存其中

秩(rank)：轴的数量

```python
.ndim  
#秩，维度/轴的数量
.shape 
#ndarray对象的尺度
.size 
#ndarray对象元素的个数，
.dtype 
#ndarray对象的元素类型
.itemsize 
#ndarray对象中每个元素的大小，以字节为单位
```
### 3.创建ndarray数组

1.从python中的列表，元组等类型创建ndarray数组
```python
x = np.array(list/tuple)
x = np.array(list/tuple, dtype = np.float32) #指定元素类型

a = np.array([0,1,2]) #list
a = np.array((0,1,2)) #tuple
```
### 2.使用NumPy中函数创建
```python
np.arrange(n) 
#元素从0~n-1
np.ones(shape) 
#根据shape生成一个全1的数组
np.zeros(shape) 
#根据shape生成一个全0的数组
np.full(shape,val) 
#根据shape生成一个全val的数组
np.eye(n) 
#n*n矩阵，对角线为1
```

### 3.关于轴的理解
*NumPy中维度叫做轴，轴的数目叫做秩
*关于.shape()函数

1.创建一个四维数组,各维度大小(4,3,2,3)

![image](/assets/images/numpy/6.png)

2.数组

![image](/assets/images/numpy/5.png)

3.测试

<font color = 'red' face = 'Times'>通过不同的axis，numpy会沿着不同的方向进行操作：</font>如果不设置，那么对所有的元素操作；如果axis=0，则沿着纵轴进行操作；axis=1，则沿着横轴进行操作。但这只是简单的二位数组，如果是多维的呢？可以总结为一句话：设axis=i，则numpy沿着第i个下标变化的放下进行操作。所以axis=0时，沿着第0个下标变化的方向进行操作。

<font color = 'red' face = 'Times'>
最外面的括号axis = 0,

向里面，依次为 axis = 1, 2, 3, ...
</font> 

*在哪个轴上求和，即该轴的数据相加，最后该轴上的维度大小为1，其他轴大小不变

*在哪个轴/维度上操作，即是使该维度最后结果中不见

3.1.在轴为0上进行求和
![image](/assets/images/numpy/4.png)

3.2.在轴为1上进行求和

第二维度数据合并，其他维度大小不变
![image](/assets/images/numpy/3.png)

3.3.在轴为2上进行求和

第三维度数据合并，其他维度大小不变
![image](/assets/images/numpy/2.png)

3.4.在轴为3上进行求和

第四维度数据合并，其他维度大小不变
![image](/assets/images/numpy/1.png)

3.5.其他和轴有关的函数 min,max...
![image](/assets/images/numpy/7.png)
