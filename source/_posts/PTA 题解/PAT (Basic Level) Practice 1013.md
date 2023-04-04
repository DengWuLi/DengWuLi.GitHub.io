---
title: 'PTA: PAT (Basic Level) Practice 1013'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-28
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 数素数

## 题目描述: 
令 $P_{i}$ 表示第 $i$ 个素数. 现任给两个正整数 $M \leq N \leq 10^{4}$, 请输出 $P_{M}$ 到 $P_{N}$ 的所有素数.

## 输入格式: 
输入在一行中给出 $M$ 和 $N$, 其间以空格分隔.

## 输出格式:
输出从 $P_{M}$ 到 $P_{N} 的所有素数, 每 10 个数字占 1 行, 其间以空格分隔, 但行末不得有多余空格.

## 输入样例:
```txt
5 27
```

## 输出样例:
```txt
11 13 17 19 23 29 31 37 41 43
47 53 59 61 67 71 73 79 83 89
97 101 103
```

## C++
```cpp
/* PTA 1013 数素数
 * 2022/07/26
 * */

#include <cmath>
#include <iostream>

using namespace std;

int Judge(int n) {
    int b = 0;
    if (n == 1)
        return 0;
    else if (n == 2)
        return 1;
    else {
        for (int i = 2; i <= static_cast<int>(sqrt(n)) + 1; i++) {
            if (n % i == 0) {
                b = 0;
                break;
            }   // 如果n是合数则返回0.
            else
                b = 1;
        }
        return b;
    }
}

int main() {
    int m, n;
    cin >> m >> n;
    int count_1 = 0, count_2 = 0;   // count_1用于统计质数的个数，count_2用于按格式输出
    for (int i = 1; count_1 < n; i++) {
        if (Judge(i) == 1) {
            count_1++;
            if (count_1 >= m) {
                cout << i;
                count_2++;
                if ((count_2 != 10) && (count_1 != n))
                    cout << " ";
                else if (count_2 == 10) {
                    cout << endl;
                    count_2 = 0;
                }
            }
        }
    }
}
```

## Java
```java
/// PAT (Basic Level) Practice
/// 1013 数素数 20/20
/// 2023-02-28
/// 在毛概课上写题

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main {
    public static void main(String[] argc) {
        var input = new Scanner(System.in);
        var m = input.nextInt();
        var n = input.nextInt();
        List<Integer> prime = new ArrayList<>();
        var count = 0;

        for (int i = 2; count < n; i++)
            if (isPrime(i)) {
                count++;
                if (count >= m)
                    prime.add(i);
            }

        count = 0;
        for (Integer integer : prime) {
            count += 1;
            if (count % 10 != 1)
                System.out.print(" ");
            System.out.print(integer);
            if (count % 10 == 0)
                System.out.println();
        }
    }

    public static boolean isPrime(int n) {
        if (n == 1)
            return false;
        else if (n == 2)
            return true;

        for (int i = 2; i * i <= n; i++)
            if (n % i == 0)
                return false;

        return true;
    }
}
```

## 简要解析:
这道题又是有关质数的问题. 相信大家对于判断质数的方法已经了如指掌. 所以说这道题根本没有什么难度, 最后的格式输出也不是什么问题.

<pre class="note note-info">
<strong>2023-02-28</strong> 
<strong>IP属地: 北京</strong>
</pre>