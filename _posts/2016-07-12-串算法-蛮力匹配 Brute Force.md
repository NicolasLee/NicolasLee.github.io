---
title: 串算法 - 蛮力匹配 Brute Force
layout: post
categories: Algorithm
tags: 蛮力匹配 暴力 串算法
excerpt: 目前有两个版本
---

第一个版本 Brute Force

```c++
// Brute Force - 1

#include <iostream>
using namespace std;

int match(char* p, char* t)
{
	size_t n = strlen(t), i = 0;
	size_t m = strlen(p), j = 0;
	while(j < m && i < n)
	{
		if (t[i] == p[j])	// 匹配
		{	
			i++; j++;		// 转到下一对字符
		}
		else
		{
			i -= j - 1; j = 0; // 主串回退、模式串复位
		}
	}
	return i - j;	// 返回匹配的起始位置
}

int main()
{
	char* t = "abcdefghijklmnopqrstuvwxyz0123456789";
	char* p = "xyz";

	int index = match(p, t);
	cout << index << endl;
	return 0;
}
```

第二个版本 Brute Force

```c++
#include <iostream>
using namespace std;
 
int match(char* p, char* t)
{
	size_t n = strlen(t), i = 0;
	size_t m = strlen(p), j = 0;
	for (i = 0; i < n - m+1; i++)
	{
		for (j = 0; j < m; j++)
		{
			if (t[i+j] != p[j])
				break;
		}
		if (j >= m)
			break;
	}
	return i;
}
 
int main()
{
	char* t = "abcdefghijklmnopqrstuvwxyz0123456789";
	char* p = "xyz";
 
	int index = match(p, t);
	cout << index << endl;
	return 0;
}
```

