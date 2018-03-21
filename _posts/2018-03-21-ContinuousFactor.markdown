---
title: "连续因子"
layout: post
date: 2018-03-21 19:44
image: 
headerImage: false
tag:
- programming
- math
star: true
category: blog
author: TangLi
description: acm programming math 
---

## 题目：连续因子

一个正整数N的因子中可能存在若干连续的数字。例如630可以分解为3*5*6*7，其中5、6、7就是3个连续的数字。给定任一正整数N，要求编写程序求出最长连续因子的个数，并输出最小的连续因子序列。

## 输入格式：

输入在一行中给出一个正整数N（1<N<2^31）。

## 输出格式：

首先在第1行输出最长连续因子的个数；然后在第2行中按“因子1*因子2*……*因子k”的格式输出最小的连续因子序列，其中因子按递增顺序输出，1不算在内。

## 输入样例：

630

## 输出样例：

3

5 * 6 * 7  （没有空格）

## 思路：

由连续因子相乘可得阶乘概念，又由数据范围（1<N<2^31）通过打表可得结论：连续因子最多为12个。
则可以从大到小枚举因子个数以及开始位置。

## 代码：

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

const int N = 1000 + 5;
typedef long long ll;

int main() {
    int n;
    scanf("%d", &n);
    for(int len = 12; len >= 1; len--)  //枚举长度
	{
        for(int st = 2; start <= sqrt(n); st++)  //枚举开始位置，题目要求因子不包括1
		{
            ll ans = 1;
			bool flag = 1;
            for(int i = st; i < st + len; i++) 
			{
                ans *= i;
				if(ans > n){flag = 0; break;}
            }
            if(flag && n % ans == 0) 
			{
                printf("%d\n%d", len, start);
                for(int i = st + 1; i < st + len; i++) {
                    printf("*%d", i);
                }
                return 0;
            }
        }
    }
    printf("1\n%d", n); // 当n为质数时，无法分解
    return 0;
}

{% endhighlight %}









