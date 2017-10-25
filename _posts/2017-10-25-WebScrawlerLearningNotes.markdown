---
title: "Web Scrawler Learning Notes"
layout: post
date: 2017-10-25 22:18
image: 
headerImage: false
tag:
- python
- Web Scrawler
star: true
category: blog
author: TangLi
description: python learning Web Scrawler
---

## Web Scrawler （python 版）

### 一、爬虫架构

需要的基本结构：

调度器

URL管理器（待访问的网址和已访问的网址）

网页下载器（urllib2）

网页解析器（BeautifuSoup）

### 二、URL管理器的实现
python内存可以使用以下方法实现

* 待爬取URL集合：使用 set()容器

* 已爬取URL集合：使用 set()容器

<font color = 'red' face = 'Times'> ps: 小数据可以直接使用set() </font>


* 使用关系数据库MySQL
 urls(url,1s_crawled)

* 使用缓存数据库redis

### 三、网页下载器：将互联网上URL下载到本地工具
* 使用urllib2  python官方包 

* 使用request  第三方工具

1.最简单的一种

``` python
import urllib2
#直接请求
#打开待访问的url
urllib2.urlopen("http://")
#获取状态码
#状态码为200时成功
print(response.getcode())  
#读取下载好的内容
cont = response.read()
```
2.添加header,伪装成浏览器
``` pyhton
import urllib2
#创建Request对象
request = urllib2.Request(url)
#向服务器提交数据
request.add_data('a','1')
#添加http的header,伪装成浏览器
request.add_header('User-Agent','Mozilla/5.0')
#发送网页下载请求获取结果
response = urllib2.urlopen(request)
```
3.模拟用户登录访问，添加cookie的处理

处理方法：HTTPCookieProcessor

``` pyhton
#代理访问
ProxyHandler
#网页使用HTTPS加密协议
HTTPSHandler
#相互之间自动跳转的网页
HTTPRedirectHandler

opener = urllib2.build_opner(handler)
urllib2.install_opener(opener)
urllib2.urlopen(url)

#eg:

import urllib2,cookielib

#创建cookie容器，存储cookie数据
cj = cookielib.CookieJar()
#创建一个opener
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
#给urllib2安装opener
urllib.install_opener(opener)
#使用带cookie的urllib2访问网页
response = urllib2.urlopen("http://")
```

### 四、网页解析器

1.使用正则表达式

2.使用python自带的html.parse模块

3.使用第三方插件BeautifulSoup

4.使用第三方插件lxml

解析过程：

html网页其实都是DOM树模型

通过 结构化解析-DOM树（文件对象模型）

1.创建BeautifulSoup对象
``` python
from bs4 import BeautifuSoup
soup = BeautifulSoup(
html_doc,               #HTML文档字符串
'html,parser',          #HTML解析器
from_encoding = 'utf8'  #HTML文档的编码
)
```

2.搜索节点 

find_all: 找到所有符合要求的节点

fine： 只找第一个符合要求的节点

搜索节点方法：

* 按节点名称
* 按节点属性
* 按节点文字

``` python
find_all(name,attrs,string)

#查找所有标签为a的节点
soup.find_all('a')  
#查找所有标签为a,链接符合/view/123.htm形式的节点
soup.fina_all('a',href = '/view/123.htm')
#可以用正则表达式匹配
soup.fina_all('a',href = re.compile(r'/view/\d+\.htm'))
#查找所有标签为div,class为abc,文字为python的节点
soup.fina_all('a',class_ = 'abc', string = 'Python')
```

3.访问节点（名称，属性，文字）
``` python 
#得到节点：<a href = '1.html'>Python</a>

#获取查找到的节点的标签名称
node.name

#获取查找到的a节点的href属性
node['href']

#获取查找到的a节点的链接文字
node.get_text()
```

### 五、一般步骤：

#### 1.确定目标

哪个网站哪些网页哪些数据

#### 2.分析目标

url格式：  限定抓取的页面的范围

数据格式： 页面的标题和简介（要抓取的数据）

网页编码： 进行正确的解析

#### 3.编写代码

#### 4.执行爬虫


### 六、升级新的抓取策略

进阶爬虫

需要登录，验证码，Ajax，服务器防爬虫，多线程，分布式

