---
title: 'PTA: PAT (Basic Level) Practice 1001'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-01-15
tags:
  - C++
  - Java
category:
  - PTA题解
mermaid: true
---

# 害死人不偿命的(3n+1)猜想
## 题目描述:
卡拉兹(Callatz)猜想：

对任何一个正整数 $n$, 如果它是偶数, 那么把它砍掉一半; 如果它是奇数, 那么把 $3n+1$ 砍掉一半.这样一直反复砍下去, 最后一定在某一步得到 $n=1$, 卡拉兹在 1950 年的世界数学家大会上公布了这个猜想, 传说当时耶鲁大学师生齐动员, 拼命想证明这个貌似很傻很天真的命题, 结果闹得学生们无心学业, 一心只证 $3n+1$, 以至于有人说这是一个阴谋, 卡拉兹是在蓄意延缓美国数学界教学与科研的进展……

我们今天的题目不是证明卡拉兹猜想, 而是对给定的任一不超过 1000 的正整数 $n$, 简单地数一下, 需要多少步 (砍几下) 才能得到 $n=1$?

## 输入格式: 
每个测试输入包含 1 个测试用例，即给出正整数 $n$ 的值.
## 输出格式:
输出从 $n$ 计算到 $1$ 需要的步数.
## 输入样例:
```txt
3
```
## 输出样例:
```txt
5
```

## C++
```cpp
/// PTA 1001 害死人不偿命的(3n+1)猜想
/// 2022/07/17

#include <iostream>

using namespace std;

int main() {
    int N, i = 0;
    cin >> N;
    for (; N != 1; i++) {
        if (N % 2 == 0)
            N = N / 2;
        else
            N = (3 * N + 1) / 2;
    }
    cout << i;
    return 0;
}
```
## Java
```java
/// PTA 1001 害死人不偿命的(3n+1)猜想
/// 2023/01/05

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner myscan = new Scanner(System.in);
        int n = myscan.nextInt();
        int count = 0;
        while (n != 1) {
            if (n % 2 == 0)
                n /= 2;
            else
                n = (3 * n + 1) / 2;
            count++;
        }
        System.out.println(count);
    }
}
```

## 简要解析:
本题作为 PAT (Basic Level) Practice 的开篇之题, 难度并不是很大, 只要读懂题意按照要求输出即可, 没有什么花花绕绕.

首先读入一个整数 $n$, 接着对这个整数进行如下操作:

1. $n$ 是偶数, 即:`if(n%2 == 0)`或者简写为:`if(!N%2)`要注意, 这种简单写法只使用与C++, Java中并不适用, 因为Java中没有定义int类型与boolean类型的转换关系. 砍掉 $n$ 的一半, 即: `n /= 2`;
2. 如果为奇数, 即在上面的if语句下添加一个else即可, 把 $3n+1$ 砍掉一半, 即:`n = (3 * n + 1) / 2`;
3. 重复这种操作, 直到 $n=1$, 这也启示我们直接在上述的逻辑判断外再加一层循环即可. 同时初始化一个用于记录循环进行次数的变量即可.
4. 最后注意输入和输出格式即可.

<pre class="note note-info">
<strong>2023-01-15</strong> 
<strong>IP属地: 曹县</strong>
</pre>