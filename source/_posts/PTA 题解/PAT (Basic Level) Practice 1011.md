---
title: 'PTA: PAT (Basic Level) Practice 1011'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-25
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 1011 A+B 和 C

## 题目描述: 
给定区间 $[−2^{31}, 2^{31}]$ 内的 3 个整数 $A, B 和 C$, 请判断 $A + B$ 是否大于 $C$.


## 输入格式: 
输入第 1 行给出正整数 $T (T \leq 10)$, 是测试用例的个数. 随后给出 $T$ 组测试用例, 每组占一行, 顺序给出 $A, B 和 C$. 整数间以空格分隔.
## 输出格式:
对每组测试用例, 在一行中输出 `Case #X: true` 如果 $A + B > C$, 否则输出 `Case #X: false`, 其中` X` 是测试用例的编号(从 1 开始).

## 输入样例:
```txt
4
1 2 3
2 3 4
2147483647 0 2147483646
0 -2147483648 -2147483647
```

## 输出样例:
```txt
Case #1: false
Case #2: true
Case #3: true
Case #4: false
```

## C++
```cpp
/* PTA 1011 A+B 和 C
 * 2022/07/25
 * */

#include <iostream>
using namespace std;

int main() {
    int t;
    cin >> t;
    const int T = t;
    long long A[T], B[T], C[T];
    for (int i = 0; i < T; i++)
        cin >> A[i] >> B[i] >> C[i];
    for (int i = 0; i < T; i++) 
        if ((A[i] + B[i]) > C[i])
            cout << "Case #" << i + 1 << ": true" << endl;
        else
            cout << "Case #" << i + 1 << ": false" << endl;
    
    return 0;
}
```

## Java
```java
/// 1011 A + B 和 C
/// 2023/01/06

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int t = input.nextInt();
        long a, b, c;
        for (int i = 0; i < t; i++) {
            a = input.nextInt();
            b = input.nextInt();
            c = input.nextInt();
            if (a + b > c)
                System.out.printf("Case #%d: true\n", i + 1);
            else
                System.out.printf("Case #%d: false\n", i + 1);
        }
    }
}
```
## 简要解析:
这道题真没什么难度, 在此不做过多讲解了.


<pre class="note note-info">
<strong>2023-02-25</strong> 
<strong>IP属地: 北京</strong>
</pre>