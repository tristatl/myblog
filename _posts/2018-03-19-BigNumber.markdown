---
title: "C++ 大数模拟"
layout: post
date: 2018-03-19 23:39
image: 
headerImage: false
tag:
- C++
- notes
star: true
category: blog
author: TangLi
description: C++
---

## 大数模拟

### 1.大数加法

{% highlight C++ %}

string sum(string s1,string s2)
{
	if(s1.length()<s2.length())
	{
		string temp=s1;
		s1=s2;
		s2=temp;
	}
	int i,j;
	for(i=s1.length()-1,j=s2.length()-1;i>=0;i--,j--)
	{
		s1[i]=char(s1[i]+(j>=0?s2[j]-'0':0));   //注意细节
		if(s1[i]-'0'>=10)
		{
			s1[i]=char((s1[i]-'0')%10+'0');
			if(i) s1[i-1]++;
			else s1='1'+s1;
		}
	}
	return s1;
}

{% endhighlight %}


### 2.大数乘以整数(int)

{% highlight C++ %}

string Multiply(string s,int x)  //大数乘以整形数
{
    reverse(s.begin(),s.end());
    int cmp=0;
    for(int i=0;i<s.size();i++)
    {
        cmp=(s[i]-'0')*x+cmp;
        s[i]=(cmp%10+'0');
        cmp/=10;
    }
    while(cmp)
    {
        s+=(cmp%10+'0');
        cmp/=10;
    }
    reverse(s.begin(),s.end());
    return s;
}

{% endhighlight %}

### 3.大数除以整数(int)

{% highlight C++ %}

string Except(string s,int x)  //大数除以整形数
{
    int cmp=0,ok=0;
    string ans="";
    for(int i=0;i<s.size();i++)
    {
        cmp=(cmp*10+s[i]-'0');
        if(cmp>=x)
        {
            ok=1;
            ans+=(cmp/x+'0');
            cmp%=x;
        }
        else{
            if(ok==1)
                ans+='0';  //注意这里啊。才找出错误
        }
    }
    return ans;
}

{% endhighlight %}


### 4.大数乘法

{% highlight C++ %}

string sum(string s1,string s2)  //大数加法
{
	if(s1.length()<s2.length())
	{
		string temp=s1;
		s1=s2;
		s2=temp;
	}
	int i,j;
	for(i=s1.length()-1,j=s2.length()-1;i>=0;i--,j--)
	{
		s1[i]=char(s1[i]+(j>=0?s2[j]-'0':0));   //注意细节
		if(s1[i]-'0'>=10)
		{
			s1[i]=char((s1[i]-'0')%10+'0');
			if(i) s1[i-1]++;
			else s1='1'+s1;
		}
	}
	return s1;
}

string Mult(string s,int x)  //大数乘以整形数
{
    reverse(s.begin(),s.end());
    int cmp=0;
    for(int i=0;i<s.size();i++)
    {
        cmp=(s[i]-'0')*x+cmp;
        s[i]=(cmp%10+'0');
        cmp/=10;
    }
    while(cmp)
    {
        s+=(cmp%10+'0');
        cmp/=10;
    }
    reverse(s.begin(),s.end());
    return s;
}
string Multfa(string x,string y)  //大数乘法
{
    string ans;
    for(int i=y.size()-1,j=0;i>=0;i--,j++)
    {
        string tmp=Mult(x,y[i]-'0');
        for(int k=0;k<j;k++)
            tmp+='0';
        ans=sum(ans,tmp);
    }
    return ans;
}

{% endhighlight %}



