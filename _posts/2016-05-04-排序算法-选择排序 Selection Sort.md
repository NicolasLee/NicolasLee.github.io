---
title: 排序算法-选择排序 Selection Sort
layout: post
categories: Algorithm
tags: 选择 排序 算法
excerpt: 代码三天不写手生，是真的哟。
---

代码三天不写手生，是真的哟。
所以要像做日常一样，每天写点最简单的东西。
###版本一
```
// Selection sort
// 选择排序
#include <iostream>
using namespace std;

void swap(int* a, int* b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}

void SelectionSort(int a[], int size)
{
	for (int i = 0; i < size; i++)
		for (int j = i+1; j < size; j++)
			if (a[j] < a[i])
				swap(a[j], a[i]);
}

void print(int a[], int size)
{
	for (int i = 0; i < size; i++)
		cout << a[i] << " ";
	
	cout << endl;
}

int main(int argc, char* argv[])
{
#if 0
	int A[] = { 5,2,4,6,1,3 };  
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

	SelectionSort(A, size);

	print(A, size);

	delete[] A;
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

void selection_sort(Item a[], int size)
{
	for (int i = 0; i < size; i++)
	{
		int min = i;
		for (int j = i+1; j < size; j++)
			if (less(a[j], a[min])) min = j;
		
		exch(a[i], a[min]);
	}
}

int main(int argc, char* argv[])
{
	int A[] = { 8,7,6,5,4,3,2,1 };  
	int size = sizeof(A)/sizeof(int);

	selection_sort(A, size);

	print(A, size);
	return 0;
}
```



