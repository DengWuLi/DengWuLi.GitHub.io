---
title: 'PTA: PAT (Basic Level) Practice 1004'
index_img: /img/PTA.png
banner_img: /img/PTA-编程随想.png
date: 2023-01-20
tags:
  - C++
  - Java
category:
  - PTA题解
mermaid: true
---

# 成绩排名
## 题目描述: 
读入 $n(n>0)$ 名学生的姓名, 学号, 成绩, 分别输出成绩最高和成绩最低学生的姓名和学号.

## 输入格式:
每个测试输入包含 1 个测试用例, 格式为:

> 第 1 行：正整数 n
> 第 2 行：第 1 个学生的姓名 学号 成绩
> 第 3 行：第 2 个学生的姓名 学号 成绩
> ... ... ...
> 第 n+1 行：第 n 个学生的姓名 学号 成绩

其中`姓名`和`学号`均为不超过 10 个字符的字符串, 成绩为 0 到 100 之间的一个整数, 这里保证在一组测试用例中没有两个学生的成绩是相同的.

## 输出格式: 
对每个测试用例输出 2 行, 第 1 行是成绩最高学生的姓名和学号, 第 2 行是成绩最低学生的姓名和学号, 字符串间有 1 空格.

## 输入样例: 
```txt
3
Joe Math990112 89
Mike CS991301 100
Mary EE990830 95
```

## 输出样例: 
```txt
Mike CS991301
Joe Math990112
```

## C++
```cpp
/* PTA 1004 成绩排名
 * 2022/07/18
 * 2023-01-20: 没想到当时竟然写出这么低效的代码
 * */

#include <iostream>

using namespace std;

struct student {
    char name[11];
    char number[11];
    int score;
};

int main() {
    int N;
    cin >> N;
    const int n = N;
    student stu[n];
    for (int i = 0; i < N; i++) 
        cin >> stu[i].name >> stu[i].number >> stu[i].score;

    student temp;
    for (int i = 1; i < N; i++) {
        for (int j = 0; j <= N - 1 - i; j++) {
            if (stu[j].score > stu[j + 1].score) {
                temp = stu[j];
                stu[j] = stu[j + 1];
                stu[j + 1] = temp;
            }
        }
    }
    cout << stu[n - 1].name << " " << stu[n - 1].number << endl;
    cout << stu[0].name << " " << stu[0].number;
}
```

## Java
```java
/// PTA 1004 成绩排名
/// 2023/01/05

import java.util.Scanner;

class Student {
    String name, ID;
    int score;
}

public class Main {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        Student maxStudent = new Student(), minStudent = new Student();
        maxStudent.score = -1;
        minStudent.score = Integer.MAX_VALUE;
        String tempName, tempID;
        int tempScore;
        for (int i = 0; i < n; i++) {
            tempName = scanner.next();
            tempID = scanner.next();
            tempScore = scanner.nextInt();
            if (tempScore > maxStudent.score) {
                maxStudent.name = tempName;
                maxStudent.ID = tempID;
                maxStudent.score = tempScore;
            }
            if (tempScore < minStudent.score) {
                minStudent.name = tempName;
                minStudent.ID = tempID;
                minStudent.score = tempScore;
            }
        }
        System.out.printf("%s %s\n", maxStudent.name, maxStudent.ID);
        System.out.printf("%s %s\n", minStudent.name, minStudent.ID);
    }
}
```

## 简要解析:
这道题应该是非常简单的来, 解题的思路也不少. 下面先来说一下Java语言的解题思路, 因为其算法的时间复杂度更低,只有 $O(n)$.
首先在主函数外定义了一个"结构体", 用来存储有关学生的各种信息(包括成绩和ID), 之后在主函数中定义`maxStudent`和`minStudent`, 用来记录成绩最好的学生和成绩最差的学生. 注意: **在正式进行比较之前, 要给它们赋予对应的初始值.**
```java
Student maxStudent = new Student(), minStudent = new Student();
maxStudent.score = -1;
minStudent.score = Integer.MAX_VALUE;
```
> 关于初始值的问题: 根据题目给的条件
> 成绩为 0 到 100 之间的一个整数 所以也可以如此赋值:
> maxStudent.score = -1; minStudent.score = 101;
> 之后, 遍历所有数据, 使用if语句进行比较即可, 这一点通过查看源代码是很清晰易懂的, 在此不做过多赘述.

下面, 再来说一下C++语言版本的做法, 首先还是定义了一个结构体用来存储有关学生的各种信息.
```cpp
struct student {
    char name[11];
    char number[11];
    int score;
};
```
申请一个结构体数组 `student stu[n]`, 存储输入的数据.
最后, 对这个数组进行排序(此处使用的是冒泡排序的排序方法), 最后按要求输出即可.

> 其实这两版代码都写麻烦了, 根本不需要什么"结构体".
> 只要定义 `maxName` 和 `maxScore`, `minName` 和 `minScore`(这些变量的含义应该很容易理解, 见名知意即可), 遍历整个数据, 进行比较, 最后直接输出即可.

<pre class="note note-info">
<strong>2023-01-20</strong> 
<strong>IP属地: 曹县</strong>
</pre>