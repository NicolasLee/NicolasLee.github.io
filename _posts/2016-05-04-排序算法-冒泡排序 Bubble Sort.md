---
title: 排序算法-冒泡排序 Bubble Sort
layout: post
categories: Algorithm
tags: 冒泡 排序 算法
excerpt: 这应该是大多数初学者最早学会的排序算法吧。
---

这应该是大多数初学者最早学会的排序算法吧。

### 版本一

```
#include <iostream>
using namespace std;

typedef int Item;
#define key(A) (A)
#define less(A, B) (key(A) < key(B))
#define exch(A, B) {Item t = A; A = B; B = t;}
#define compexch(A, B) if(less(B, A)) exch(A, B)

void print(int a[], int size)
{
	for (int i = 0; i < size; i++)
		cout << a[i] << " ";
	
	cout << endl;
}

void bubble_sort(Item a[], int size)
{
	for (int i = 0; i < size-1; i++)
		for (int j = size-1; j > i; j--)
			{compexch(a[j-1], a[j]); print(a, size);}
}

int main(int argc, char* argv[])
{
	int A[] = { 8,7,6,5,4,3,2,1 };  
	int size = sizeof(A)/sizeof(int);

	bubble_sort(A, size);
	print(A, size);
	return 0;
}
```
版本二

```
#include <iostream>
using namespace std;

void print(int a[], int size)
{
	for (int i = 0; i < size; i++)
		cout << a[i] << " ";

	cout << endl;
}

void bubble_sort1A(int A[], int n)
{
	bool sorted = false;
	while (!sorted)
	{
		sorted = true;
		for (int i = 1; i < n; i++)
		{
			if (A[i-1] > A[i])
			{
				swap(A[i - 1], A[i]);//void std::swap<int>(int&, int&)
				sorted = false;//清除排序标志
			}
		}
		n--;//末尾元素必要已经就位，可减少待排序列长度
	}
}

int main()
{
	
	int A[10] = { 6, 5, 1, 7, 8, 9, 4, 3, 0, 2 };
	bubble_sort1A(A, 10);
	print(A, 10);

	return 0;
}
```

