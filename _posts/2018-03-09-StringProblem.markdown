---
title: "古风排版--字符串处理"
layout: post
date: 2018-03-09 21:07
image: /assets/images/markdown.jpg
headerImage: false
tag:
- solution
- algorithm
star: true
category: blog
author: TangLi
description: 
---

## problem:

中国的古人写文字，是从右向左竖向排版的。本题就请你编写程序，把一段文字按古风排版。

输入格式：

输入在第一行给出一个正整数N（<100），是每一列的字符数。第二行给出一个长度不超过1000的非空字符串，以回车结束。

输出格式：

按古风格式排版给定的字符串，每列N个字符（除了最后一列可能不足N个）。

输入样例1：

5

2/5 4/15 1/30 -2/60 8/3

输出样例1：

4

This is a test case


输出样例1：

asa T
st ih
e tsi
 ce s


## code:

{% highlight C++ %}

#include <iostream>
#include <cstdio>
#include <algorithm>
#include <cmath>
#include <map>
#include <string>
#include <vector>
#include <stack>
#include <cstring>

using namespace std;

const int N = 10000;
typedef long long ll;

char mp[N][N];
int main()
{
    int n;
    cin >> n;
    string s;
    getchar();
    getline(cin,s);
    int cnt = s.length();
    int col = cnt/n + (cnt%n==0?0:1);

    int all = 0;
    for(int i = col-1; i >= 0; i--)
    {
        for(int j = 0; j < n; j++)
        {
            if(all >= cnt) mp[j][i] = ' ';   //注意这里是大于等于号，因为字符串s到s[cnt-1]为止
            else mp[j][i] = s[all];
            all++;
        }
    }
    for(int i = 0; i < n; i++)
    {
        for(int j = 0; j < col; j++)
            printf("%c",mp[i][j]);
        printf("\n");
    }

    return 0;
}


{% endhighlight %}


## 注意字符串下标问题

