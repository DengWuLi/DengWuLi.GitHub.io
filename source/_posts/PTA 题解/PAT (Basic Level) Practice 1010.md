---
title: 'PTA: PAT (Basic Level) Practice 1010'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-18
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 一元多项式求导

## 题目描述: 
设计函数求一元多项式的导数. (注: $x^{n}$ $(n)$ 为整数的一阶导数为 $nx^{n-1}$. )



## 输入格式: 
以指数递降方式输入多项式非零项系数和指数 (绝对值均为不超过 1000 的整数). 数字间以空格分隔.

## 输出格式:
以与输入相同的格式输出导数多项式非零项的系数和指数. 数字间以空格分隔, 但结尾不能有多余空格. 注意 "零多项式" 的指数和系数都是 0, 但是表示为 `0 0`.

## 输入样例:
```txt
3 4 -5 2 6 1 -2 0
```

## 输出样例:
```txt
12 3 -10 1 6 0
```

## C++
```cpp
/* PTA 1010 一元多项式求导
 * 2022/07/24
 * */

#include <iostream>

using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    if (b == 0) {
        cout << "0 0";
        return 0;
    }
    else
        cout << a * b << " " << b - 1;
    
    while (cin >> a >> b)
        if (b != 0)
            cout << " " << a * b << " " << b - 1;
    return 0;
}
```

## Java
```java
/// 1010 一元多项式求导
/// 2023/01/06

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int a, b;
        a = input.nextInt();
        b = input.nextInt();
        if (b == 0) {
            System.out.print("0 0");
            return;
        } else
            System.out.printf("%d %d", a * b, b - 1);
        while (input.hasNextInt()) {
            a = input.nextInt();
            b = input.nextInt();
            if (b != 0)
                System.out.printf(" %d %d", a * b, b - 1);
        }

    }
}
```
## 简要解析:
这道题没什么难度, 在此不做过多讲解了, 值得注意的是输出格式, 所以, 要对第一个输入进行特殊处理.


## 写在最后:
在学习数据结构的时候, 曾在课本上遇到过类似的问题, 当时课本上给出的代码是使用链表实现的, 同时课本上也实现了诸如多项式的加减乘等算法.

<pre class="note note-info">
<strong>2023-02-18</strong> 
<strong>IP属地: 曹县</strong>
</pre>