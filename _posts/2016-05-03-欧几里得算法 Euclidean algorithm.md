---

title: 欧几里得算法 Euclidean algorithm
layout: post
categories: Algorithm
tags: C C++ 算法 Algorithm 欧几里得
excerpt: 记录看过的书，并且整理书籍里提到的书籍和论文

---

突然发现我连int main里标准的参数都不会写。尴尬啊，哈哈哈哈...

```
// Euclidean algorithm
// 欧几里得算法
#include <iostream>
using namespace std;

int gcd(int p, int q)
{
	if (q == 0) return p;
	int r = p % q;
	return gcd(q, r);
}

int main(int argc, char* argv[])
{
	int a, b;
	cout << "Enter two number for gcd calculation: ";
	cin >> a >> b;

	cout << gcd(a, b) << endl;

	return 0;
}
```
