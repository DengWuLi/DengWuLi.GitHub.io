---
title: 'JLU数据结构课设 - 手撕STL Sort'
index_img: /img/JLU.jpeg
banner_img: /img/PTA-编程随想.png
date: 2023-04-23
tags:
  - C++
category:
  - 其他
  - PAT题解
mermaid: true
---

# 手撕STL Sort

## 题目描述: 
C++ STL是 *Standard Template Library* 的简称, 即标准模板库. 简单来说, STL 将常用的数据结构与算法进行了封装, 用户需要时可以直接调用, 不用重新开发. 排序算法 sort() 是 STL 包含的一个重要算法.

STL 中的 sort() 函数基于快速排序算法实现, 众所众知, 快速排序是目前已知平均情况下最快的排序算法, 被 IEEE 评选为 20 世纪十大算法之一, 但其最坏情况下时间复杂度会退化为 $ O(n^2) $. STL 中的 sort() 对传统快速排序做了巧妙的改进, 使其最坏情况下时间复杂度也能维持在 $ O(nlogn) $, 它是如何实现的呢？

快速排序算法最坏情况下时间复杂度退化为 $ O(n^2) $ 的主要原因是, 每次划分 (Partition) 操作时, 都分在子数组的最边上, 导致递归深度恶化为 $ O(n) $层. 而 STL 的 sort() 在 Partition 操作有恶化倾向时, 能够自我侦测, 转而改为堆排序, 使效率维持在堆排序的 $ O(nlogn) $. 其具体方法是: 侦测快速排序的递归深度, 当递归深度达到 $ \lfloor 2 \log_2n \rfloor = O(logn) $ 层时, 强行停止递归, 转而对当前处理的子数组进行堆排序.

此外, 传统的快速排序在数据量很小时, 为极小的子数组产生许多的递归调用, 得不偿失. 为此, STL 的 sort() 进行了优化, 在小数据量的情况下改用插入排序. 具体做法是: 当递归处理的子数组长度 (子数组包含的元素个数) 小于等于某个阈值 `threshold` 时, 停止处理并退出本层递归, 使当前子数组停留在 "接近排序但尚未完成" 的状态, 最后待所有递归都退出后, 再对整个序列进行一次插入排序 (注意不是对当前处理的子数组进行插入排序, 而是在快速排序的所有递归完全退出后, 对整个数组统一进行一次插入排序). 实验表明, 此种策略有着良好的效率, 因为插入排序在面对 "接近有序" 的序列时拥有良好的性能.

在本题中, 请你按照上述思路, 自己实现 STL 的 sort() 函数.

**备注: Partition 操作选取第 1 个元素作为基准元素. Partition 操作的不同实现可能导致不同的输出结果, 为保证输出结果唯一, 该操作的实现请以教材为准**

## 函数接口定义:
```cpp
void sort(int *R, int n);
```

功能为对整数 `R[1]`...`R[n]` 递增排序.

## 裁判测试程序样例:
```cpp
#include<iostream>
#include<stdlib.h>
#include<math.h>
using namespace std;
int threshold;

/* 请在这里补充你的代码，即你所实现的sort函数 */

int main()
{
    int n,i;
    int a[50010];
    scanf("%d %d", &n, &threshold);
    for (i = 1; i <= n; i++)
        scanf("%d", &a[i]);
    
    sort(a,n);
    
    printf("Final:");
    for (i = 1; i <= n; i++)
        printf("%d ",a[i]);
    printf("\n");
    return 0;
}
```
**备注: 提交代码时, 只需提交 `sort` 函数以及你自定义的其他函数, 不用提交 `#include` 或者 `main` 函数等内容.**

## 输入格式:
输入第一行为 2 个正整数 `n` 和 `threshold`, n 为待排序的元素个数, 不超过50000, threshold 为改用插入排序的阈值, 不超过 20, 含义如上所述. 第二行为 n 个空格间隔的整数. 本题中读入数据的操作无需你来实现, 而由框架程序完成.

## 输出格式:
输出第一行为以 `depth_limit:` 开头的整数, 表示转为堆排序的递归深度, 即 $ \lfloor 2log_2n \rfloor $ 从第二行开始, 输出对某子数组转为堆排序后, 该子数组初始建堆的结果, 每个元素后一个空格, 每个堆占一行, 以`Heap:`开头. 注意, 可能不止一个堆. 接下来下一行, 输出 n 个整数, 每个整数后一个空格, 为快速排序所有递归退出后, 插入排序执行前的数组元素, 以`Intermediate:`开头. 最后一行为 n 整数, 每个整数后一个空格, 表示排序后的数组, 以 `Final:` 开头 (最后一行由框架程序完成, 无需你来输出)

## 输入输出样例:

### 输入样例 1:
```txt
10 2
10 9 8 7 6 5 4 3 2 1
```

### 输出样例 1:
```txt
depth_limit:6
Heap:7 6 5 4 
Intermediate:1 2 3 4 5 6 7 8 9 10 
Final:1 2 3 4 5 6 7 8 9 10 
```

### 输入样例 2:
```txt
60 2
66 61 92 22 50 80 39 2 25 60 49 17 37 19 24 57 40 82 11 52 45 0 33 78 32 25 19 42 92 50 39 87 74 87 56 79 63 63 80 83 50 3 87 2 91 77 87 10 59 23 25 6 49 85 9 95 60 16 28 1 
```

### 输出样例 2:
```txt
depth_limit:11
Heap:24 19 23 19 17 22 
Intermediate:1 0 2 2 3 6 10 9 11 16 17 19 19 22 23 24 25 25 25 28 32 33 37 39 39 42 40 45 49 49 50 50 50 52 56 57 59 60 60 61 63 63 66 77 74 78 79 80 80 82 83 85 87 87 87 87 91 92 92 95 
Final:0 1 2 2 3 6 9 10 11 16 17 19 19 22 23 24 25 25 25 28 32 33 37 39 39 40 42 45 49 49 50 50 50 52 56 57 59 60 60 61 63 63 66 74 77 78 79 80 80 82 83 85 87 87 87 87 91 92 92 95 
```

## C++
```cpp
// 2023/04/23
// 手撕STL Soer
// 应 Mar-Bro 要求写的

// 维护堆的性质
void heapify(int arr[], const int& len, int pos) {
    int largest = pos,
        left = 2 * pos + 1,
        right = 2 * pos + 2;

    // 找出父节点, 左孩子, 右孩子中最大节点的下标
    if (left < len && arr[largest] < arr[left])
        largest = left;
    if (right < len && arr[largest] < arr[right])
        largest = right;

    if (largest != pos) {
        swap(arr[largest], arr[pos]);
        heapify(arr, len, largest);
    }
}

void heapSort(int* first, const int* last) {
    auto len = last - first;
    // 建堆

    for (int i = len / 2 - 1; i >= 0; i--)
        heapify(first, len, i);

    printf("Heap:");
    for (auto i = first; i < last; i++)
        printf("%d ", *i);
    printf("\n");
    // 排序
    for (int i = len - 1; i > 0; i--) {
        swap(first[i], first[0]);
        heapify(first, i, 0);
    }
}

// 用于 introSort 的分割函数, 返回, pivot 所在的指针
int* partition(int* first, int* last) {
    int pivot = *first;   // 默认是以第一个作为枢轴量
    auto p = first;
    // 这一段循环基本必须照着这个格式写, 不然不能 AC
    // 因为分组的实现方式有很多, 但是要想 AC 许多细节的地方需要注意
    // 这种实现方式选择的是, 一开始 first 并不参与排序, 直到返回时, 才将 first 对应的值进行交换
    while (true) {
        while (*(++first) <= pivot) // 少一个等号都不行!
            ;
        while (*(--last) > pivot)
            ;
        if (first >= last) {
            swap(*p, *last);   // 这里是选择 last 与枢轴量进行交换
            return last;
        }
        swap(*first, *last);
    }
}

void introSort(int* first, int* last, int& depthLimit) {
    --depthLimit;
    if ((last - first) > threshold) {
        if (depthLimit <= 0) {
            heapSort(first, last);
            ++depthLimit;
            return;
        }

        auto cut = partition(first, last);
        introSort(first, cut, depthLimit);      // 对 [first, cut) 进行排序
        introSort(cut + 1, last, depthLimit);   // 对 [cut + 1, last) 进行排序
    }
    ++depthLimit;
}

// 插入排序
void insertSort(int* first, const int* last) {
    if (first == last)
        return;
    int *i, *j;
    int val;
    for (i = first + 1; i != last; ++i) {
        val = *i;
        for (j = i - 1; j >= first && val < *j; --j)
            *(j + 1) = *j;
        *(j + 1) = val;
    }
}

// 请在这里补充你的代码, 即你所实现的 sort 函数
void sort(int* R, int n) {
    int *first = R + 1, *last = R + n + 1;

    auto depthLimit = static_cast<int>(2 * (log(n) / log(2)));
    printf("depth_limit:%d\n", depthLimit);
    // 此处自加一下, 是因为, 在第一调用 introSort 时会默认递归了一次, 其实不然
    introSort(first, last, ++depthLimit);

    printf("Intermediate:");
    for (auto p = first; p < last; ++p)
        printf("%d ", *p);
    printf("\n");

    insertSort(first, last);
}
```

## 写在最后
本答案也是应 **Mao-Bro** 写的答案题解.
我一开始也写了个代码 (按照我之前看 `STL源码剖析` 时写的 sort, 进行了一定的简化), 但是输入输出样例都对不上, 于是搁置在一边了.
后来 *Mao-Bro* 成功的 AC 了此题, 特来向 ~~它~~ 求教后, 结合 ~~它~~ 的代码修改后, 才能 AC.
下面就来说一下我的心得体会:

我感觉, 一般学校学数据也会让学生实现一个 `sort`, 估计也就是课下实现一下就可以了, 并不会放到 OJ上, 因为此函数有多种实现方式 (实现时有很多细节问题, 不同的选择, 导致排序中间状态的输出也不同), 不方便 OJ 判题.
但是, 作为 ~~酒吧舞~~ 高校, *Mar-Bro* 的老师还是选择放到 OJ 上进行评测, 因此给这个 `sort` 增加了许多限制条件, 一些写在了题目描述中, 一些则需要自己的研究. 这就导致了你看自己的思路确实没问题, 但是就是不能和样例对上的烦人的结果.
然而, 我们的 *Mao-Bro* 顶住课业压力, 终于研究出来了!
许多实现的具体细节, 我已经写在代码注释中了, 大家可以研究一下.

对了, 这篇 blog 写于 2023 年劳动节补班的周日, *Mao-Bro* 正在补课 :rofl:. 作为 **北京放假大学** 的我们, 从来没有补班这种事情!

:laughing: :laughing: :laughing: 
<pre class="note note-info">
<strong>2023-04-23</strong> 
<strong>IP属地: 北京</strong>
</pre>