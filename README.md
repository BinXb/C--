### 函数
>库函数
自定义函数

参考手册（网站）
www.cplusplus.com

https://en.cppreference.com/w/  
中文版https://zh.cppreference.com/w/

还可以下载个离线文档工具zeal在里面下载C++，这里也是官网内容    https://zealdocs.org/

c的库函数有很多，但学习方法都差不多，下面举几个例子帮助理解
#### strcpy - string copy
>strcpy(需要拷贝的目标,被拷贝内容的来源); - char* strcpy( char* dest, const char* src );
```
#include <stdio.h>
#include <string.h>

int main()
{
	char arr1[] = "Hello";//source
	char arr2[20] = {0};//destination
	strcpy(arr2, arr1);
	printf("%s\n", arr2);
	//strcpy - string copy - 字符串拷贝
	//strlen - string length -字符串长度
	return 0;
}
```
注意：当来源比目标长度长时会溢出，因此我们要保持目标数组的长度比来源要长，防止出现bug
#### memset - memory（内存） set（设置）
>	memset( void *dest, int ch, size_t count );//memset(目标地址 , 值 , 更改长度)
```
#include <stdio.h>
#include <string.h>

int main()
{
	char arr[] = "Hello world";
	memset(arr, '*', 5);//memset(目标,值,更改长度)  -  替换arr数组中前五个字符为*
	printf("%s\n", arr);
	return 0;
}
```
### 函数的组成
```
ret_type fun_name(paral, * )
{
	statement://函数体
}
ret_type 返回类型
fun_name 函数名
paral 函数参数
```

举个例子，写一个函数找出两个数的较大值
```
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>
#include <string.h>
//定义函数
int get_max(int x,int y)
{
	if (x > y)
	{
		return x;
	}
	else
		return y;
}
int main()
{
	int a = 10;
	int b = 20;
	int max = get_max(a, b);//调用函数
	printf("%d\n", max);
	int max1 = get_max(100, 200);//调用函数直接传值
	printf("%d\n", max1);
	return 0;
}
```
对两个数进行交换
```
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>
#include <string.h>

//错误的方法
int Swap1(int x, int y)
{
	int z = 0;
	z = x;
	x = y;
	y = z;
	return x, y;
}
//正确的方法
void Swap2(int* pa,int* pb)//
{
	int tmp = 0;
	tmp = *pa;//解引用a，直接利用a的地址进行更改
	*pa = *pb;
	*pb = tmp;
}

//将两个数利用函数的形式进行交换
int main()
{
	int a = 10;
	int b = 20;
	printf("a=%d b=%d\n", a, b);
	Swap2(&a,&b);//传a，b的地址到函数Swap2的值中
	printf("a=%d b=%d\n", a, b);
	return 0;
}
```


####  实际参数（实参）：
>真实传给函数的参数，叫实参。实参可以是：常量，变量，表达式，函数等。无论实参是何种类型的量，在进行调用时，他们都必须由确定的值，以便把这些值传送给形参。


#### 形式参数（形参）：
>形式参数是指函数名后括号中的变量，因为形式参数只有在函数被调用的过程中才实例化(分配内存单元)，所以叫形式参数。形式参数当函数调用完成之后就睡自动销毁了，因此形式参数只在函数中有效。

上面Swap1和Swap2函数中的参数x,y,px,py都是形式参数。在main函数中传给Swap1的num1，num2和传给Swap2函数的&num1,&num2是实际参数。

**形参实例化之后，其实相当于实参的一份临时拷贝**

### 函数的嵌套调用和链式访问
#### 嵌套调用
#### 链式访问
>链式访问

```
int main() {
	int len = 0;
	//1，正常访问
	len = strlen("abc");
	printf("%d\n", len);
	//2,l链式访问
	printf("%d\n", strlen("abc"));
	return 0;
}
```

### 函数声明和调用
*一般在公司里写函数都会将函数的定义和声明写在另一个文件中，那样就可以多人合作提高效率*
在未来写工程时就分开写：
分别创建一个头文件和源文件用来声明函数
在主函数中调用

<img width="1280" alt="函数的声明和调用" src="https://user-images.githubusercontent.com/114718718/196066784-89f0e282-2f4a-44b4-9d19-3c494470a9ad.png">
#### 函数声明：
>1.告诉编译器有一个函数叫什么，参数是什么，返回类型是什么，但具体是不是存在，无关紧要
2.函数的声明一般出现在函数的使用之前，要满足先声明后使用
3.函数的声明一般放在头文件中

#### 函数定义：
>函数定义指的是函数的具体实现，交代函数的功能实现


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






