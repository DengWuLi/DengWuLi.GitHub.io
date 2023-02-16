---
title: '判断 C++ 中 const 修饰问题的技巧'
index_img: /img/C++.jpg
banner_img: /img/C++.jpg
date: 2023-02-14
tags:
  - C++
category:
  - 其他
mermaid: true
---

# 判断 C++ 中 const 修饰问题的技巧

最近我在阅读 `<C++ Primer>` 时被书中 `2.4 const 限定符` 这一节内容搞得很头疼, 于是寻觅互联网, 在知乎上发现一个不错的技巧, 特此记录下来.

## 规则
**const默认是修饰它左边的符号的，如果左边没有，那么就修饰它右边的符号**

## 例一
```cpp
const int* p;
```
`const` 左边没有, 看右边的一个, 是`int`, 自然就是p指针指向的值不能改变.
*注意, 此处因为个人代码风格的问题, 表示指针的 `*` 是紧靠`int`*
## 例二
```cpp
int const* p;
```
此时 `const` 左边有`int`, 效果和例一, 还是修饰的`int`.

## 例三
```cpp
int* const p; 
```
修饰的是`*`, 即指针不能改变.

## 例四
```cpp
const int *const p;
```
第一个 `const` 左边没有, 所以修饰的是右边的 `int`, 第二个 `const` 左边有, 所以修饰的是 `*`, 因此指针和指针指向的值都不能改变.

## 例五
```cpp
const int const *p;
```
这里两个 `const` 修饰的都是 `int`了, 所以重复修饰了, 有的编译器可以通过但会有警告, 有的可能直接编译错误.

## 例六
```cpp
int const* const p;
```
留做练习题, 自己分析吧, 欢迎大家在评论区留下自己的见解.
总而言之, 看到 `const` 就看它左边是什么, 如果左边没有, 才看右边的, 就永远不会出错! ! !

## 写在最后
既然, 本人习惯将 `*` 与 `int` 绑定在一起由例一可以看出, 这样会造成一定的误解.
那么不妨修改我自己的代码风格为将 `const` 置于 `int` 之后.
于是便有:

```cpp
int const p1;   // 值不可修改
int* const p2;   // 指针不能修改, 即指针不能转向.
int const* const p3;   // 指针和指针指向的值均不能修改.
```

<pre class="note note-info">
<strong>2023-02-14</strong> 
<strong>IP属地: 曹县</strong>
</pre>