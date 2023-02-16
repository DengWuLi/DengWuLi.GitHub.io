---
title: 'PTA: PAT (Basic Level) Practice 1007'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-14
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 素数对猜想

## 题目描述:
让我们定义 $d_{n}$ 为: $d_{n} = p_{n+1} - p_{n}$, 其中 $p_{i}$ 是第 $i$ 个素数. 显然有 $d_{1} = 1$, 且对于 $ n > 1$ 有 $d_{n}$ 是个偶数. "素数对猜想" 认为 "存在无穷多对相邻且差为2的素数".
现给定任意正整数 `N`$(<10^5)$, 请计算不超过`N`的满足猜想的素数对的个数.

## 输入格式: 
输入在一行给出正整数`N`.

## 输出格式: 
在一行中输出不超过`N`的满足猜想的素数对的个数.

## 输入样例:
```txt
20
```

## 输出样例: 
```txt
4
```

## C++
```cpp
/* PTA 1007 素数对猜想
 * 2022/07/22
 * */

#include <cmath>
#include <iostream>

using namespace std;

int judge(int n) {
    int b = 0;
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

int main() {
    int a;
    cin >> a;
    int* p = new int[a + 1];
    p[0] = 0;
    p[1] = 0;
    p[2] = 1;
    for (int i = 3; i < a + 1; i++)
        p[i] = judge(i);
    int count = 0;
    for (int i = 2; i <= a - 2; i++)
        if (p[i] == 1 && p[i + 2] == 1)
            count++;
    cout << count;
    delete[] p;
}

```

## Java
```java
/// PAT (Basic Level) Practice
/// 1007 素数对猜想 20/20
/// 2023-02-14

import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        ArrayList<Integer> prime = new ArrayList<>();
        for (int i = 2; i <= n; i++)
            if (isPrime(i))
                prime.add(i);
        int num = 0;
        for (int i = 0; i < prime.size() - 1; i++)
            if (prime.get(i) - prime.get(i + 1) == -2)
                num++;
        System.out.println(num);
    }

    public static boolean isPrime(int number) {
        if (number == 1)
            return false;
        else if (number == 2)
            return true;

        for (int i = 2; i <= Math.sqrt(number); i++)
            if (number % i == 0)
                return false;
        return true;
    }
}
```

## 简要解析: 
这道题主要考察了 **"素数"** 这个概念和如何判断一个数是否为素数. 判断素数的算法多种多样, 我以后应该会专门写一篇blogs来总结一下常用的各种计算素数的算法. 
结合本题的数据范围, 我们这里选择一种最为简便的方式进行判断:
> 对于数字 $n$, 如果 $n$ 能被 $[2,\sqrt n)$ 范围内任意一个整数整除, 说明 $n$ 不是素数. 否则说明 $n$ 是素数. 

在本题中, 我首先计算出 $n$ 内 所有的素数, 并在数组 `p` 中进行标记, 之后开始遍历, 判断 `i` 和 `i+2` 是否均为素数, 并使用 `count` 进行计数. 最后输出 `count` 即可.

## 写在最后: 
为什么 $\sqrt n$ 而不是 $n$, 这一点很容易看出. 因为, 一个整数的因数是成对的. 例如, 12可以分解为: 
> $1 \times 12 \quad 2 \times 6 \quad 3 \times 4 \quad 4 \times 3 \quad 6 \times 2 \quad 12 \times 1$

可以发现后半部分是前半部分的翻转.
如果6是12的因数, 就一定会有另外一个对应的因数2. 因为因数6大于根号12, 所以另一个因数2., 就一定小于根号12.
换句话说, 每一个大于根号n的因数, 都有一个对应的小于根号n的因数, 等于根号n的因数, 对应的另一个因数也是根号n, 比如 $5 \times 5 = 25$.
因此, 只需要判断到 (包括) 根号n为止即可.

<pre class="note note-info">
<strong>2023-02-14</strong> 
<strong>IP属地: 曹县</strong>
</pre>