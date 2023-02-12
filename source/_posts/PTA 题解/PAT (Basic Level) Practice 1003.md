---
title: 'PTA: PAT (Basic Level) Practice 1003'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-01-18
tags:
  - C++
  - Java
category:
  - PTA题解
mermaid: true
---

# 我要通过！

## 题目描述:

"**答案正确**" 是自动判题系统给出的最令人欢喜的回复. 本题属于 PAT 的 "**答案正确**" 大派送---只要读入的字符串满足下列条件,
系统就输出 "**答案正确**", 否则输出 "**答案错误**". 得到 "**答案正确**"的条件是:

1. 字符串中必须仅有`P`, `A`, `T`, 这三种字符, 不可以包含其它字符;
2. 任意形如 `xPATx` 的字符串都可以获得"**答案正确**", 其中 `x` 或者是空字符串, 或者是仅由字母 `A` 组成的字符串;
3. 如果 `aPbTc` 是正确的, 那么 `aPbATca` 也是正确的. 其中`a`, `b`, `c`均或者是空字符串, 或者是仅由字母 `A` 组成的字符串.

现在就请你为 PAT 写一个自动裁判程序，判定哪些字符串是可以获得"**答案正确**"的.

## 输入格式:

每个测试输入包含 1 个测试用例, 第 1 行给出一个正整数 $n \leq 10$, 是需要检测的字符串个数. 接下来每个字符串占一行,
字符串长度不超过 100，且不包含空格.

## 输出格式:

每个字符串的检测结果占一行, 如果该字符串可以获得"**答案正确**", 则输出 YES, 否则输出 NO.

## 输入样例:

```text
10
PAT
PAAT
AAPATAA
AAPAATAAAA
xPATx
PT
Whatever
APAAATAA
APT
APATTAA
```

## 输出样例:

```text
YES
YES
YES
YES
NO
NO
NO
NO
NO
NO
```

## C++

```cpp
/// PTA 1003 我要通过!
/// 首次写于: 2022-07-17, 修改与 2023-01-17
/// m没想到竟然都在去年7月和今年1月碰到这个题, 真可以说是缘分的呢.
/// 之前太注意通过了, 代码没怎么写注释, 今天回来不上, ☺

#include <iostream>

using namespace std;

bool judge(string s) {
    // 这两个变量分别用来记录字符串中P, T出现的次数
    int PNum = 0, TNum = 0;

    /**
     * 用来统计A出现的次数, 根据题意可以将A出现的位置划分为三中情况:
     * <ol>
     * <li>出现在P的左边, 用<strong>ANum[0]</strong>表示</li>
     * <li>出现在P和T的中间, 用<strong>ANum[1]</strong>表示</li>
     * <li>出现在T的右边, 用<strong>ANum[3]</strong>表示</li>
     * </ol>
     * 统计到最后只要判断一下:
     * <p>ANum[0]*ANum[1]?=ANum[3]</p>即可
     * */

    int ANum[3] = {0};
    int a[5] = {0};
    for (char i : s) {
        // 当一个字符串中出现了非`P`, `A`, `T`这三种字符时, 直接返回false
        if (i != 'P' && i != 'A' && i != 'T')
            return false;
        // 当检测到字符=='P'时, PNum++, 
        // 同时进行判断, 若字符串中P出现的次数>1 || 在P出现之前, T已经出现, 直接返回false
        if (i == 'P') {
            PNum++;
            if (PNum > 1 || TNum != 0)
                return false;
        }
        // 当检测到字符=='T'时, TNum++, 
        // 同时进行判断, 若字符串中T出现的次数>1 || 在T出现后, P仍未出现, 直接返回false.
        else if (i == 'T') {
            TNum++;
            if (TNum > 1 || PNum == 0)
                return false;
        }
        else {
            if (PNum == 0 && TNum == 0)
                ANum[0]++;
            else if (PNum != 0 && TNum == 0)
                ANum[1]++;
            else
                ANum[2]++;
        }
    }
    // "PAAAAA" 这样的输入也是不能通过的
    if (PNum == 0 || TNum == 0 || ANum[1] == 0)
        return false;

    if(ANum[0]*ANum[1]!=ANum[2])
        return false;
    else
        return true;
}

int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) {
        string s;
        cin >> s;
        if (judge(s))
            cout << "YES" << endl;
        else
            cout << "NO" << endl;
    }
    return 0;
}
```

## Java

```java
/// PAT (Basic Level) Practice (中文)
/// 1003 我要通过!
/// 2023-01-17

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        String str;
        for (int i = 0; i < n; i++) {
            str = in.next();
            if (judge(str))
                System.out.println("YES");
            else
                System.out.println("NO");

        }
    }

    public static boolean judge(String str) {
        int PNum = 0, TNum = 0;

        int[] ANum = {0, 0, 0};

        for (int i = 0; i < str.length(); i++) {

            if (str.charAt(i) != 'P' && str.charAt(i) != 'A' && str.charAt(i) != 'T')
                return false;

            if (str.charAt(i) == 'P') {
                PNum++;
                if (PNum > 1 || TNum != 0)
                    return false;
            } else if (str.charAt(i) == 'T') {
                TNum++;
                if (TNum > 1 || PNum == 0)
                    return false;
            } else {
                if (PNum == 0 && TNum == 0)
                    ANum[0]++;
                else if (PNum != 0 && TNum == 0)
                    ANum[1]++;
                else
                    ANum[2]++;
            }
        }

        if (PNum == 0 || TNum == 0 || ANum[1] == 0 || (ANum[0] * ANum[1] != ANum[2]))
            return false;
        else
            return true;
    }
}
```

## 简要解析:

相比起前两道题, 这道题就稍显麻烦了, 我记得我第一次做这道题目时, 搞不懂题目描述的规则在说什么, 于是前去百度, 最终才明白题目的含义.
综合题目给的几个条件, 我们可以得出以下判断字符串是否**正确**的规则:

1. 字符串仅含`P`, `A`, `T`三个字符，且不存在其它字符(这是题目原话);
2. 字符串中 `P` 和 `T` 均只能出现一次, 且 `P` 一定要出现在 `T` 的前面;
3. `P` 和 `T` 中间一定要有一个 `A`. 也就是说 `PT` 也是不正确的输入, 这一点可以从输入样例里看出;
4. **P左侧A的数量 $\times$ 中间A的数量 $=$ 右侧A的数量**

前三个条件并没有什么难以理解的地方, 主要是第四个条件需要费点时间. 下面, 我们就来重点说一下第四个条件的由来.

> 2. 任意形如 `xPATx` 的字符串都可以获得"**答案正确**", 其中 `x` 或者是空字符串, 或者是仅由字母`A`组成的字符串;
>3. 如果 `aPbTc` 是正确的, 那么 `aPbATca` 也是正确的. 其中`a`, `b`, `c`均或者是空字符串, 或者是仅由字母 `A` 组成的字符串.

由条件2可知, `PAT`, `APATA`, `AAPATAA` 等均是**答案正确**的字符串;
条件3实质上就是在条件2的基础上进行拓展, 为方便描述, 下面举几个例子(第一个可由条件2推得一定正确):

> a = null, b = A, c = null
>
>> PAT $\rightarrow$ PAAT $\rightarrow$ PAAAT $\rightarrow$ PAAAAT $\rightarrow$ ...
>
> a = A, b = A, c = A
>
>> APATA $\rightarrow$ APAATAA $\rightarrow$ APAAATAAA $\rightarrow$ APAAAATAAAA $\rightarrow$ ...
>
> a = AA, b = A, c = AA
>> AAPATAA $\rightarrow$ AAPAATAAAA $\rightarrow$ ...

通过以上的三个例子, 我们可以得出结论: **P左侧A的数量 $\times$ 中间A的数量 $=$ 右侧A的数量**  

依照这些规则, 就可以编写程序了, C++代码中写了比较详尽的注释, 特别是在如何实现这4条规则上, 在这里就不做过多赘述了.

<pre class="note note-info">
<strong>2023-01-18</strong> 
<strong>IP属地: 曹县</strong>
</pre>