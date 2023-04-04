---
title: 'PTA: PAT (Basic Level) Practice 1012'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-28
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 数字分类

## 题目描述: 
给定一系列正整数, 请按要求对数字进行分类, 并输出以下 5 个数字: 
* $A_{1} = $ 能被 5 整除的数字中所有偶数的和;
* $A_{2} = $ 将被 5 除后余 1 的数字按给出顺序进行交错求和, 即计算 $n_{1} - n_{2} + n_{3} - n_{4} ...$ ;
* $A_{3} = $ 被 5 除后余 2 的数字的个数;
* $A_{4} = $ 被 5 除后余 3 的数字的平均数, 精确到小数点后 1 位;
* $A_{5} = $  被 5 除后余 4 的数字中最大数字.

## 输入格式: 
每个输入包含 1 个测试用例. 每个测试用例先给出一个不超过 1000 的正整数 $N$, 随后给出 $N$ 个不超过 1000 的待分类的正整数, 数字间以空格分隔.

## 输出格式:
对给定的 N 个正整数，按题目要求计算 $A_{1} \sim A_{5} $ 并在一行中顺序输出. 数字间以空格分隔, 但行末不得有多余空格.
若分类之后某一类不存在数字, 则在相应位置输出 `N`.

## 输入样例 1:
```txt
13 1 2 3 4 5 6 7 8 9 10 20 16 18
```

## 输出样例 1:
```txt
30 11 2 9.7 9
```
## 输入样例 2:
```txt
8 1 2 4 5 6 7 9 16
```

## 输出样例 2:
```txt
N 11 2 N 9
```


## C++
```cpp
/* PTA 1012 数字分类
 * 2022/07/29
 * */

#include <iostream>
#include <valarray>

using namespace std;

int main() {
    int N;
    cin >> N;

    int A[6] = {0};
    int j = 0, count = 0;
    bool flag = false;
    while (N--) {
        int temp;
        cin >> temp;
        int temp2 = temp % 5;
        switch (temp2) {
        case 0:
            if (temp % 2 == 0)
                A[1] += temp;
            break;
        case 1:   // 交错求和结果可能为零或根本没有数据, 要分这两种情况讨论, 这一点比较坑
            j++;
            flag = true;
            A[2] += int(pow(-1, j - 1)) * temp;
            break;
        case 2:
            A[3]++;
            break;
        case 3:
            A[4] += temp;
            count++;
            break;
        case 4:
            A[5] = max(A[5], temp);
            break;
        default:
            break;
        }
    }

    double ave;
    if (count != 0)
        ave = double(A[4]) / count;

    for (int i = 1; i <= 5; i++) {
        if (i == 2) {
            if (flag)   // 表示有这个数字
                cout << A[i];
            else
                cout << "N";
        }
        else if (i == 4) {
            if (A[i] == 0)
                cout << "N";
            else
                printf("%.1f", ave);
        }
        else {
            if (A[i] == 0)
                cout << "N";
            else
                cout << A[i];
        }
        if (i != 5)
            cout << " ";
    }
}
```

## Java
```java
/// PTA 1011 A+B 和 C
/// 2023/01/06

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        int[] a = new int[5];
        int j = 0, count = 0, temp;

        while (n-- > 0) {
            temp = input.nextInt();
            switch (temp % 5) {
                case 0 -> {
                    if (temp % 2 == 0)
                        a[0] += temp;
                }
                case 1 -> {
                    if (j % 2 == 0)
                        a[1] = a[1] + temp;
                    else
                        a[1] = a[1] - temp;
                    j+=1;
                }
                case 2 -> a[2]++;
                case 3 -> {
                    a[3] += temp;
                    count++;
                }
                case 4 -> a[4] = Math.max(a[4], temp);
            }
        }

        double ave = 0;
        if (count != 0)
            ave = a[3] * 1.0 / count;
        for (int i = 0; i < 5; i++) {
            switch (i) {
                case 1 -> {
                    if (j != 0)
                        System.out.print(a[i]);
                    else
                        System.out.print("N");
                }
                case 3 -> {
                    if (a[i] == 0)
                        System.out.print("N");
                    else
                        System.out.printf("%.1f", ave);
                }
                default -> {
                    if (a[i] == 0)
                        System.out.print("N");
                    else
                        System.out.print(a[i]);
                }
            }
            if (i != 4)
                System.out.print(" ");
        }
    }
}
```
## 简要解析:
这道题目读完就会发现, 难到是不难, 就是需要各种判断, 所以需要有清晰的思维.
详细解析可以看代码(我自认为我写的代码逻辑清晰, 可读性强).
当然, 尽管不算难, 但是依然有些小坑, 比如, 处理 $A_{2}$ 时要注意最后的和可能为**零**, 不能单靠最后的`和`来判断是否有输入.


<pre class="note note-info">
<strong>2023-02-28</strong> 
<strong>IP属地: 北京</strong>
</pre>