
### 函数和递归
>程序调用自身的编程技巧成为递归(recursion).递归作为一种算法在程序设计语言中广泛应用。一个过程或函数在其定义或说明中直接或间接调用自身的一种方法，它它通常把一个大型复杂的问题层层转化位一个与原问题相似的规模较小的问题来求解，递归策略只需少量的程序就可描述出解题过程所需要的多次重复计算，大大的减少了程序的代码量。

**递归的主要思考方式在于:把大事化小**
#### 递归的两个必要条件***
>存在限制条件，当满足这个条件的时候，递归便不再继续。
每次递归调用之后越来越接近这个限制条件。


#### Stack overflow递归常见的一个错误(栈溢出)
```
//main函数调用自己
int main() {
	main();
	return 0;
}
```
<img width="474" alt="栈溢出" src="https://user-images.githubusercontent.com/114718718/196067878-f9aaba1f-ecdd-4f07-9349-935a6671aba1.png">
```
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

void print(int n) {
	if (n > 9) {
		print(n/10);
	}
	printf("%d ", n % 10);
}
int main() {
	unsigned int num = 0;
	scanf("%d", &num);
	//递归
	print(num);
	return 0;
}
```
<img width="744" alt="递归_练习1" src="https://user-images.githubusercontent.com/114718718/196067906-d52d1f21-fcfc-4c29-8a28-6ab9b1f022d7.png">

```
//练习： 模拟strlen的作用

//int my_strlen(char* str) {
//	int count = 0;
//	while (*str != '\0') {
//		count++;
//		str++;
//	}
//	return count;
//}
//递归的方法
int my_strlen(char* str) {
	if (*str != '\0') {
		return 1 + my_strlen(str + 1);
	}
	else {
		return 0;
	}
}
//my_strlen(str + 1) -- hello
//1 + my_strlen(str + 1) -- ello
//1 + 1 my_strlen(str + 1) -- llo
//1+1+1 + my_strlen(str + 1) -- lo
//1+1+1+1 + my_strlen(str + 1) -- o
//1+1+1+1+1 + my_strlen(str + 1) -- '\0'
//5
int main() {
	char arr[] = "hello";
	int len = my_strlen(arr);
	printf("%d\n", len);
	return 0;
}

```

#### 递归与迭代
>求n的阶乘

```
////循环的方式
//int Fac1(int n) {
//	int i = 0;
//	int ret = 1;
//	for (i = 1; i <= n; i++) {
//		ret *= i;
//	}
//	return ret; 
//}
////递归的方法
//int Fac2(int n) {
//	if (n <= 1)
//		return 1;
//	else
//		return n*Fac2(n - 1);
//}
//
////求n的阶乘
//int main() {
//	int n = 0;
//	int ret = 0;
//	scanf("%d", &n);
//	ret = Fac2(n);//循环的方式
//	printf("%d\n", ret);
//	return 0;
//}
```
>求斐波那契额数
```
//斐波那契额数列
//1 1 2 3 5 8 13 21 34 55 ...
// 递归的方法 - 非常慢效率不高 不推荐使用
//int Fib(int n) {
//	if (n <= 2) {
//		return 1;
//	}
//	else {
//		return Fib(n - 1) + Fib(n - 2);
//	}
//}
//循环的方法
int Fib(int n) {
	int a = 1;
	int b = 1;
	int c = 1;
		while (n > 2) {
			c = a + b;
			a = b;
			b = c;
			n--;
		}
		return c;
}
int main() {
	int n = 0;
	int ret = 0;
	scanf("%d", &n);
	//TDD - 测试驱动开发   (先写出主函数，然后再写如何实现)
	ret = Fib(n);
	printf("%d\n", ret);
	return 0;
}

```
#### 什么时候用递归什么时候用循环
>要懂得变通
```

```
### 《剑指offer》
>针对面试的一本书，对面试的介绍和一些面试题的讲解，我最近在看，觉得很不错



