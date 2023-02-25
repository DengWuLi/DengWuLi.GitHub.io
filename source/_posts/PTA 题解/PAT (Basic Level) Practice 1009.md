---
title: 'PTA: PAT (Basic Level) Practice 1009'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-02-17
tags:
  - C++
  - Java
category:
  - PTA题解
---

# 说反话

## 题目描述: 
给定一句英语, 要求你编写程序, 将句中所有单词的顺序颠倒输出.

## 输入格式: 
测试输入包含一个测试用例, 在一行内给出总长度不超过 80 的字符串. 字符串由若干单词和若干空格组成, 其中单词是由英文字母 (大小写有区分) 组成的字符串, 单词之间用 1 个空格分开, 输入保证句子末尾没有多余的空格.

## 输出格式:
每个测试用例的输出占一行, 输出倒序后的句子.

## 输入样例:
```txt
Hello World Here I Come
```

## 输出样例:
```txt
Come I Here World Hello
```

## C++
```cpp
/* PTA 1009 说反话
 * 2022/07/24
 * */

#include <iostream>

using namespace std;

int main() {
    char a[81];
    cin.getline(a, 81, '\n');
    char p[80][80] = {'\0'};
    int count = 0;
    int i = 0;
    int y = 0;
    while (a[i] != '\0') {
        for (; (a[i] != ' ') && (a[i] != '\0'); y++, i++)
            p[count][y] = a[i];
        p[count][y] = '\0';
        count++;
        if (a[i] != '\0')
            i++;
        y = 0;
    }
    for (int j = count - 1; j > 0; j--)
        cout << p[j] << " ";
    cout << p[0];
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
        String str = input.nextLine();
        String[] ans = str.split(" ");
        for (int i = ans.length - 1; i >= 0; i--) {
            System.out.print(ans[i]);
            if (i != 0)
                System.out.print(" ");
        }
    }
}
```

## 简要解析:
这道题用 Java 来做的话还是比较简单的, 用一个字符串存放输入的句子, 然后按空格拆分成字符串数组, 然后倒序输出就是结果了.
用 C++ 的化比较复杂了, 要自己手写一个 `split` 函数. (其实, 这个题的 C++ 程序应该更接近 C 语言风格)


## 写在最后:
又去 CSDN 上看了看柳诺的代码, 发现她使用了 **"栈"** 这种数据结果, 对这个题来说确实是降维打击啊!
附柳诺的代码:
```cpp
#include <iostream>
#include <stack>
using namespace std;
int main() {
    stack<string> v;
    string s;
    while(cin >> s) 
        v.push(s);
    cout << v.top();
    v.pop();

    while(!v.empty()) {
        cout << " " << v.top();
        v.pop();
    }
    return 0;
}
```

<pre class="note note-info">
<strong>2023-02-17</strong> 
<strong>IP属地: 曹县</strong>
</pre>