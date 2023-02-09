---
title: 'PTA: PAT (Basic Level) Practice 1002'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-01-16
tags:
  - C++
  - Java
category:
  - PTA题解
mermaid: true
---
# 写出这个数

## 题目描述: 

读入一个正整数 $n$, 计算其各位数字之和, 用汉语拼音写出和的每一位数字.

## 输入格式:

每个测试输入包含 1 个测试用例，即给出自然数 $n$ 的值。这里保证 $n$ 小于 $10^{100}$.

## 输出格式:

在一行内输出 $n$ 的各位数字之和的每一位, 拼音数字间有 1 空格, 但一行中最后一个拼音数字后没有空格.

## 输入样例:
> 1234567890987654321123456789

## 输出样例:
> yi san wu

## C++
第一版:

```cpp
/*  PTA 1002 写出这个数
 *  2022/07/17
 * */
#include<stdio.h>
#include<math.h>
int main()
{
	char a[100];
	int sum = 0, c = 0, ss = 0;//c用于记录数字
	int gg = 0, z = 0;
	int mm = 0;
	gets(a);//输入到字符数组，算出总和
	for (int x = 0; a[x] != '\0'; x++)
	{
		sum = a[x] - 48 + sum;
	}
	ss = sum;
	//判断多少位
	while (sum != 0)
	{
		sum /= 10;
		c++;
	}
	// 开始输出
	for (int i = c; i > 0; i--)
	{
		z = ss / pow(10, i - 1);
		z = z % 10;
		if (i == 1)
		{
			switch (z)
			{
				case 0:printf("ling");
					break;
				case 1: printf("yi");
					break;
				case 2: printf("er");
					break;
				case 3: printf("san");
					break;
				case 4: printf("si");
					break;
				case 5: printf("wu");
					break;
				case 6: printf("liu");
					break;
				case 7: printf("qi");
					break;
				case 8: printf("ba");
					break;
				case 9: printf("jiu");
					break;
			
			}
		}
		else
		{
			switch (z)
			{
				case 0:printf("ling ");
					break;
				case 1: printf("yi ");
					break;
				case 2: printf("er ");
					break;
				case 3: printf("san ");
					break;
				case 4: printf("si ");
					break;
				case 5: printf("wu ");
					break;
				case 6: printf("liu ");
					break;
				case 7: printf("qi ");
					break;
				case 8: printf("ba ");
					break;
				case 9: printf("jiu ");
					break;
			}
		}
	
	}
	getchar();
	return 0;
}
```
第二版:
````cpp
/// PTA 1002 写出这个数
/// 初次写于 2022-07-17, 修改于 2023-01-16
/// 感觉之前对这个题写的代码写的代码太"娘希匹"了.

#include <iostream>

using namespace std;

int main() {
    int sum = 0;
    char ch;
    while ((ch = getchar()) && ch != '\n')
        sum += static_cast<int>(ch - '0');
    string arr[] = {"ling", "yi", "er", "san", "si", "wu", "liu", "qi", "ba", "jiu"};
    string str = to_string(sum);

    for (int i = 0; i < str.length(); i++) {
        cout << arr[static_cast<int>(str[i] - '0')];
        if (i < str.length() - 1)
            cout << " ";
    }
}
````
## Java
```Java
/// PTA 1002 写出这个数
/// 2023/01/05

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        int sum = 0;
        Scanner scanner = new Scanner(System.in);
        String str = scanner.nextLine();

        for (int i = 0; i < str.length(); i++)
            sum += str.charAt(i) - '0';

        str = String.valueOf(sum);
        for (int i = 0; i < str.length(); i++) {
            switch (str.charAt(i)) {
                case '0':
                    System.out.print("ling");
                    break;
                case '1':
                    System.out.print("yi");
                    break;
                case '2':
                    System.out.print("er");
                    break;
                case '3':
                    System.out.print("san");
                    break;
                case '4':
                    System.out.print("si");
                    break;
                case '5':
                    System.out.print("wu");
                    break;
                case '6':
                    System.out.print("liu");
                    break;
                case '7':
                    System.out.print("qi");
                    break;
                case '8':
                    System.out.print("ba");
                    break;
                case '9':
                    System.out.print("jiu");
                    break;
                default:
                    continue;
            }
            if (i < str.length() - 1)
                System.out.print(" ");
        }

    }
}
```
## 简要解析: 
* 首先读入这个正整数 $n$ 值得注意的是题目中给出的 $n$ 范围是 $[1,10^{100})$, 而C++中即便使用unsigned long int, 表示的最大整数为 $2^{64}-1$, 也就是 `18,446,744,073,709,551,615` (这个数是用计算器算出来的, 应该是正确的), 也不能满足题意, 所以我们应该考虑其他的输入方式
* 结合题目可知, 题目只要求我们计算出这个数各位上数的和, 于是我们可以用输入单个字符的方式读入这个数, 同时在读入的过程中接着把正整数各位上的和算出来, 于是有以下代码:
```cpp
while ((ch = getchar()) && ch != '\n')
        sum += static_cast<int>(ch - '0'); // 其实这里不必使用显式类型转换
```
* 其实也可以首先把 $n$ 以字符串的形式读进来, 之后调用库函数, 将字符串中各位和算出来, 于是有Java版的算法:
```java
Scanner scanner = new Scanner(System.in);
String str = scanner.nextLine();

for (int i = 0; i < str.length(); i++)
    sum += str.charAt(i) - '0';

str = String.valueOf(sum);
```
* 算出和之后, 将和每一位求出来后, 进行输出即可, 取和的每一位可以使用循环, 不断的对和进行对10模和除10操作(详见第一版C++代码), 也可以使用库函数, 将和转化为字符串(C++中的`to_stringJava`终的`String.valueOf()`) , 从知乎上找了一个[参考资料](https://zhuanlan.zhihu.com/p/441819455)
* 最后的问题便是输出, 可以使用switch语句对每个字符进行判断并输出. 因为输出内容与上文提到的'和'有着一 一对应的关系, 同时明显是存在偏序关系的, 于是可以先将要求输出的内容存到一个数组中, 之后找到字符和需要输出的内容的数组下标的对应关系即可.
于是有:
```cpp
switch (str.charAt(i)) {
    case '0':
        System.out.print("ling");
        break;
    case '1':
        System.out.print("yi");
        break;
    case '2':
        System.out.print("er");
        break;
    case '3':
        System.out.print("san");
        break;
    case '4':
        System.out.print("si");
        break;
    case '5':
        System.out.print("wu");
        break;
    case '6':
        System.out.print("liu");
        break;
    case '7':
        System.out.print("qi");
        break;
    case '8':
        System.out.print("ba");
        break;
    case '9':
        System.out.print("jiu");
        break;
    default:
        continue;
    }

```
```java
string arr[] = {"ling", "yi", "er", "san", "si", "wu", "liu", "qi", "ba", "jiu"};
for (int i = 0; i < str.length(); i++) {
        cout << arr[static_cast<int>(str[i] - '0')];
        if (i < str.length() - 1)
            cout << " ";
    }
```
* 最后需要注意的问题是: **行末没有空格!**
* 总的来说, 这道题不算太难, 许多繁琐的操作都有库函数的帮忙, 就是最后输出需要将规定的输出写入程序中, 比较烦人.
## 回想:
现在看第一版C++代码, 感觉当时真是太辣鸡了, 这么简单的题竟然用了86行代码, 有时回来看看自己之前写过的题目还是有必要的.

<pre class="note note-info">
<strong>2023-01-18</strong> 
<strong>IP属地: 曹县</strong>
</pre>