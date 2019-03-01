---
title: 排序算法-希尔排序 Shell Sort
layout: post
categories: Algorithm
tags: C C++ 算法 Algorithm
excerpt: 希尔排序快速但不稳定，且根据增量的不同有多种不同的写法。
---
希尔排序快速但不稳定，且根据增量的不同有多种不同的写法。

```
// Selection sort
// 选择排序
#include <iostream>
#include <cmath>
using namespace std;

void swap(int* a, int* b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}

void print(int a[], int size)
{
	for (int i = 0; i < size; i++)
	{
		cout << a[i] << " ";
	}
	cout << endl;
}

void shell_sort(int a[], int size)
{
	int i, j, temp, gap = size/2;   // 设置希尔排序的增量
	while(gap >= 1)
	{
		for(i=gap; i<size; i++)    
		{    
			temp = a[i];
			j = i-gap;
			while(j>=0 && a[j]>temp)    
			{    
				a[j+gap] = a[j];    
				j = j-gap;    
			}    
			a[j+gap] = temp;
			print(a, size);	// 打印每趟排序后的结果
		}
		gap = gap/2;// 缩小增量
		
	}    
	cout << "Sorting procedure ended!" << endl;
}

int main(int argc, char* argv[])
{
//#define DEBUG

#ifdef DEBUG
	int A[] = { 8,7,6,5,4,3,2,1 };  
	int size = sizeof(A)/sizeof(int);
#else // 假设个数未知
	int size = 0;
	cout << "Enter array size: ";
	cin >> size;

	cout << "Enter array elements: ";
	int* A = new int[size];
	int i = 0;
	while ((cin >> A[i]) &&
			(i < size) )
	{
		i++;
	}
	
#endif

	shell_sort(A, size);

	print(A, size);

#ifndef DEBUG
	delete[] A;
#endif
	
	return 0;
}
```



