---
title: 'PTA: PAT (Basic Level) Practice 1008'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-16
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 数组元素循环右移问题

## 题目描述:
一个数组 $A$ 中存在有 $N(N>0)$ 个整数, 在不允许使用另外数组的前提下，将每个整数循环向右移$M(M \geq 0)$ 个位置，即将 $A$ 中的数据由 $(A_{0}A_{1}···A_{N-1})$ 变换为 $(A_{N-M}···A_{N-1}A_{0}A_{1}A_{N-M-1})$ (最后 $M$ 个数循环移至最前面的 $M$ 个位置) 如果需要考虑程序移动数据的次数尽量少, 要如何设计移动的方法?

## 输入格式: 
每个输入包含一个测试用例, 第1行输入 $N(1 \geq N \leq 100)$ 和 $M(M \geq 0)$; 第2行输入 $N$ 个整数, 之间用空格分隔.

## 输出格式: 
在一行中输出循环右移 $M$ 位以后的整数序列, 之间用空格分隔, 序列结尾不能有多余空格.

## 输入样例:
```txt
6 2
1 2 3 4 5 6
```

## 输出样例:
```txt
5 6 1 2 3 4
```

## C++
```cpp
/* PTA 1008 数组元素循环右移问题
 * 2022/07/23
 * */

#include <iostream>
using namespace std;

void Move(int* p, int n) {
    int temp = p[n - 1];
    for (int i = n - 1; i > 0; i--)
        p[i] = p[i - 1];   // 从后向前赋值, 有些类似于矩阵. 从后一行加到前一行
    p[0] = temp;
}

int main() {
    int n, m;
    cin >> n >> m;
    int* p = new int[n];
    for (int i = 0; i < n; i++)
        cin >> p[i];
    for (int i = 0; i < m; i++)
        Move(p, n);
    for (int i = 0; i < n - 1; i++)
        cout << p[i] << " ";
    cout << p[n - 1];
    delete[] p;
}
```

## Java
```java
/// PAT (Basic Level) Practice
/// 1008 数组元素循环右移问题
/// 2023-02-14
/// Java 始终不能像 C++ 那般灵活的使用结构体数组......
/// 或许我还没有感受到 Java 语言的伟大之处.

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        int n, m;
        n = input.nextInt();
        m = input.nextInt();

        Number[] arr = new Number[n];

        for (int i = 0; i < n; i++)
            arr[i] = new Number();

        for (int i = 0; i < n; i++)
            arr[i].first = input.nextInt();

        for (int i = 0; i < n; i++)
            arr[(i + m) % n].second = arr[i].first;

        for (int i = 0; i < n; i++) {
            System.out.print(arr[i].second);
            if (i != n - 1)
                System.out.print(' ');
        }

    }

    static class Number {
        public Integer first;
        public Integer second;

        public Number() {
            this.first = 0;
            this.second = 0;
        }
    }

}
```

## 简要解析: 
这个题目有两个要求:

1. 不许使用额外的数组;
2. 程序移动数据的次数尽量少;

但从这两点来说, C++程序, 明显是不合格的, 因为其通过调用函数实现每次只向右移动一个位置, 总共循环 $M$ 次, 移动次数显然增多了不少.
然而, Java程序, 使用了一种巧妙的思路, 首先它先自定义了一个新的数据类型 `Number`, 其中包含两种数据, 数组的初始数据 `first` 和移动后的数据 `second` (这种命名方式类似于 C++ 中的 `pair`, 两个的作用也是类似的), 这样通过一次循环就可直接判断出 元素移动后的位置, 而不必一次次机械地移动.

## 写在最后:
网上的资料有些更为简单的写法 (是否能够AC, 本人并不能保证), 下面粘在这里, 供大家参考.
**`CSDN` --- 柳诺**
```cpp
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    vector<int> a(n);
    for (int i = 0; i < n; i++)
        cin >> a[i];
    m %= n;
    // 这一部分是这段代码的核心, 需要好好研究.
    if (m != 0) {
        reverse(begin(a), begin(a) + n);
        reverse(begin(a), begin(a) + m);
        reverse(begin(a) + m, begin(a) + n);
    }
    for (int i = 0; i < n - 1; i++)
        cout << a[i] << " ";
    cout << a[n - 1];
    return 0;
}
```

**`CSDN` --- 柳诺评论区**
```cpp
// 这段代码最为简洁, 而且很容易明白
#include <iostream>

using namespace std;

int main() {
    int n, m, i;
    cin >> n >> m;
    int a[n];
    for (i = 0; i < n; i++)
        cin >> a[i];
    for (i = 0; i < n; i++) {
        int j = i - m % n;
        if (j < 0)
            cout << a[j + n];
        else
            cout << a[j];
        if (i < n - 1) cout << " ";
    }
}

```

<pre class="note note-info">
<strong>2023-02-16</strong> 
<strong>IP属地: 曹县</strong>
</pre>