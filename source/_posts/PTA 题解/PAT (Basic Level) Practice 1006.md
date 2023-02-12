---
title: 'PTA: PAT (Basic Level) Practice 1006'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-12
tags:
  - C++
  - Java
category:
  - PTA题解
mermaid: true
---

# 换个格式输出整数

## 题目描述: 
让我们用字母 `B`来表示 "百", 字母 `S` 表示 "十", 用 `12...n` 来表示不为零的个位数字 $`n`(n<10>)$, 换个格式来输出任一个不超过 3 位的正整数. 例如 `234` 应该被输出为 `BBSSS1234`，因为它有 2 个"百", 3 个"十", 以及个位的 4.

## 输入格式: 
每个测试输入包含 1 个测试用例，给出正整数 $n(n<1000)$.

## 输出格式: 
每个测试用例的输出占一行，用规定的格式输出 $n$.

## 输入样例 1:
```txt
234
```

## 输出样例 1:
```txt
BBSSS1234
```

## 输入样例 2: 
```txt
23
```

## 输出样例 2:
```txt
SS123
```

## C++
```cpp
/* PTA 1006 换个格式输出整数
 * 2022/07/21
 * */

#include <iostream>
#include <string.h>

using namespace std;

void fun1(int a) {
    for (int i = 0; i < a; i++)
        cout << 'B';
}

void fun2(int a) {
    for (int i = 0; i < a; i++)
        cout << 'S';
}

void fun3(int a) {
    for (int i = 1; i <= a; i++)
        cout << i;
}

int main() {
    char ch[3];
    cin >> ch;
    int a = strlen(ch);
    switch (a) {
    case 3:
        fun1(static_cast<int>(ch[0]) - 48);
        fun2(static_cast<int>(ch[1]) - 48);
        fun3(static_cast<int>(ch[2]) - 48);
        break;
    case 2:
        fun2(static_cast<int>(ch[0]) - 48);
        fun3(static_cast<int>(ch[1]) - 48);
        break;
    case 1:
        fun3(static_cast<int>(ch[0]) - 48);
        break;
    default:
        break;
    }
}
```

## Java
```java
/// PTA 1006 换个格式输出整数
/// 2023/01/06

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        int i;
        for (i = 0; i < n / 100; i++)
            System.out.print("B");
        for (i = 0; i < n % 100 / 10; i++)
            System.out.print("S");
        for (i = 1; i <= n % 10; i++)
            System.out.print(i);
    }
}
```

## 简要解析: 
这道题非常简单. 只需要简单地根据 `n` 的每一位的数字, 循环输出对应位的字母即可, 没有什么难度.
也可以像 `C++` 代码所写的那样, 先对数据进行位数判断, 之后根据不同位数进行处理, 当然这样就比较麻烦了.
总的来说, 还是 `Java` 代码的解题思路简单明了.

<pre class="note note-info">
<strong>2023-02-12</strong> 
<strong>IP属地: 曹县</strong>
</pre>