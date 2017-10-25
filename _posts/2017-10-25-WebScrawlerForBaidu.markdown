---
title: "My first Web Scrawler"
layout: post
date: 2017-10-25 21:36
image: 
headerImage: false
tag:
- Web Scrawler
- practice
star: true
category: blog
author: TangLi
description: Baidu baike 名词和解释抓取
---

## 爬取百度百科相关词条及解释

### 第一次爬虫的实例分析：

#### 1.目标：百度百科Python词条相关网页

#### 2.入口页：http://baike.baidu.com/item/Python

<font color = 'red' face = 'Times'> ps:由于网站维护，可能该网址不可用，需要及时更新 </font>

#### 3.URL格式：

-词条页面URL：/item/125370.htm （其他网页地址）

<font color = 'red' face = 'Times'> ps:该网址不全，需要根据入口页网址补全为 /baike.baidu.com/item/125370.htm </font>

#### 4.数据格式：

-标题：

```html
<dd class = "lemmaWgt-lemmaTitle-title"><h1>***</h1></dd>
-简介：
<div class="lemma-summary">***</div>
```
#### 5.页面编码：UTF-8

### 分析：

#### 1.总共有5个.py文件

* 主文件： spider_main.py
* url管理器： url_manager.py
* 下载器： html_dowmloader.py
* 解析器： html_parser.py
* 爬虫结果保存： html_outputer.py

![Image](/assets/images/1a.png)

#### 2.主函数入口
![Image](/assets/images/1b.png)

#### 3.主要算法

1.将入口页添加入url管理器

<font color = 'red' face = 'Times'> 2.进入循环 </font>

3.从url管理器中取出一条url地址，计数+1

4.将新的url内容下载

5.解析下载下来的新的url的内容

6.若有新的url，则加入url管理器；若有有效数据，则进行收集

<font color = 'red' face = 'Times'> 7.若达到所需爬取的页面数量则退出循环，否则继续回到3</font>


![Image](/assets/images/1c.png)

![Image](/assets/images/1d.png)

#### 完整代码: <https://github.com/tristatl/pythonCode/tree/master/WebScrawler/first_try/baike_spider>






