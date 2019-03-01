---
title: 排序算法-插入排序 Insertion Sort Θ(n-n)
layout: post
categories: Algorithm
tags: 插入 排序 算法
excerpt: 还在读书的孩子要好好珍惜读书的日子啊。
---

还在读书的孩子要好好珍惜读书的日子啊。

多羡慕你们完全不用为生活操心，每天只需要一心扑在学习或者自己喜欢的事情上。

### 版本一

```
#include<iostream>
using namespace std;

void swap(int* a, int* b)
{
	//*a = *a + *b;
	//*b = *a - *a;
	//*a = *a - *b;

	int temp = *a;
	*a = *b;
	*b = temp;
}

void InsertSort(int A[], int size)
{
	for (int j = 1; j < size; j++)
	{
		for (int i = j - 1; i >= 0; i--)
		{
			if (A[i] > A[i + 1])
				swap(A[i], A[i + 1]);
		}
	}
}

int main()
{
//	int A[] = { 5,2,4,6,1,3 };	// 假设个数未知
	int A[6] = { 0 };

	int x = 0;
	while (cin>>A[x])
	{
		x++;
	}

	int size = sizeof(A) / sizeof(int);

	InsertSort(A, size);
	
	for (int i = 0; i < size; i++)
	{
		cout << A[i] << " ";
	}

    return 0;
}
```
### 版本二

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

void insertion_sort(Item a[], int size)
{
	for (int i = 0; i < size; i++)
		compexch(a[0], a[i]);
	for (int i = 1; i < size; i++)
	{
		int j = i; Item v = a[i];
		while(less(v, a[j-1]))
		{
			a[j] = a[j-1]; 
			j--;
		}
		a[j] = v;
	}
}

int main(int argc, char* argv[])
{
	int A[] = { 8,7,6,5,4,3,2,1 };  
	int size = sizeof(A)/sizeof(int);

	insertion_sort(A, size);
	print(A, size);
	return 0;
}
```

