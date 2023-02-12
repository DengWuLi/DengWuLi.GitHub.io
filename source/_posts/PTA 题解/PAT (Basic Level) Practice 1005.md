---
title: 'PTA: PAT (Basic Level) Practice 1005'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-01-24
tags:
  - C++
  - Java
category:
  - PTA题解
mermaid: true
---

# 继续(3n+1)猜想

## 题目描述: 
卡拉兹(Callatz)猜想已经在1001中给出了描述. 在这个题目里. 情况稍微有些复杂.

当我们验证卡拉兹猜想的时候, 为了避免重复计算, 可以记录下递推过程中遇到的每一个数. 例如对 $n=3$ 进行验证的时候，我们需要计算3, 5, 8, 4, 2, 1, 则当我们对 $n=5,8,4,2$ 进行验证的时候, 就可以直接判定卡拉兹猜想的真伪, 而不需要重复计算. 因为这 4 个数已经在验证 3 的时候遇到过了, 我们称 5, 8, 4, 2 是被 3 "覆盖" 的数. 我们称一个数列中的某个数 $n$ 为 "关键数", 如果 $n$ 不能被数列中的其他数字所覆盖.

现在给定一系列待验证的数字, 我们只需要验证其中的几个关键数, 就可以不必再重复验证余下的数字. 你的任务就是找出这些关键数字, 并按从大到小的顺序输出它们.

## 输入格式:
每个测试输入包含 1 个测试用例, 第 1 行给出一个正整数 $K(K<100)$, 第 2 行给出 $K$ 个互不相同的待验证的正整数 $n(1 < n \leq 100)$ 的值, 数字间用空格隔开.

## 输出格式: 
每个测试用例的输出占一行, 按从大到小的顺序输出关键数字. 数字间用 1 个空格隔开, 但一行中最后一个数字后没有空格.

## 输入样例: 
```txt
6
3 5 6 7 8 11
```

## 输出样例: 
```txt
7 6
```

## C++
```cpp
#include <algorithm>
#include <iostream>

using namespace std;

int main() {
    int n;
    cin >> n;
    int p[n];
    for (int i = 0; i < n; i++)
        cin >> p[i];
    for (int i = 0; i < n; i++) {
        if (p[i] == 0)
            continue;
        else {
            for (int j = p[i]; j != 1;) {
                if (j % 2 == 0)
                    j /= 2;
                else
                    j = (3 * j + 1) / 2;
                for (int k = 0; k < n; k++)
                    if (p[k] == j)
                        p[k] = 0;
            }
        }
    }
    sort(p, p + n, greater<>());
    int m = 0;
    for (; m < n; m++)
        if (p[m] == 0)
            break;

    for (int i = 0; i < m; i++) {
        cout << p[i];
        if (i != m - 1)
            cout << " ";
    }
}
```

## Java
```java
/// PTA 1005 继续(3n+1)猜想
/// 2023/01/06

import java.util.Arrays;
import java.util.Collections;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        /* 要想使用Java中sort函数实现降序排列, 竟然要使用其对应的类, 比C++麻烦不少 */
        Integer[] p = new Integer[n];
        for (int i = 0; i < n; i++)
            p[i] = input.nextInt();
        for (int i = 0; i < n; i++) {
            if (p[i] != 0) {
                for (int j = p[i]; j != 1; ) {
                    if (j % 2 == 0)
                        j /= 2;
                    else
                        j = (3 * j + 1) / 2;
                    for (int k = 0; k < n; k++)
                        if (p[k] == j)
                            p[k] = 0;
                }
            }
        }
        Arrays.sort(p, Collections.reverseOrder());
        int m = 0;
        for (; m < n; m++)
            if (p[m] == 0)
                break;
        for (int i = 0; i < m; i++) {
            System.out.print(p[i]);
            if (i != m - 1)
                System.out.print(" ");
        }

    }
}
```

## 简要解析: 
这道题总体来说并不难, 下面说一下我的主要思路(两种语言思路一致, 这里我以C++为例子):

首先, 读入n和相应的n个数. 接着, 对每个数进行 **卡拉兹(Callatz)** 猜想所描述的操作进行处理, 并将处理中出现的中间数且在输入的数中的那部分数赋值为零, 表示此数被**覆盖**了.

对这n个数据进行降序排序, 最后对那些不为0的数据输出即可.

<pre class="note note-info">
<strong>2023-01-24</strong> 
<strong>IP属地: 曹县</strong>
</pre>