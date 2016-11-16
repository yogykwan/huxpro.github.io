---
layout:     post
title:      "《挑战程序设计竞赛》中级篇笔记"
subtitle:   ""
date:       2016-11-16
author:     "Jennica"
header-img: "img/post-bg-acm.jpg"
catalog: true
tags:
    - 算法
    - 读书
---

> 王者归来。

# 1.1 算法读书笔记说明

本篇为[《挑战程序设计竞赛（第2版）》](http://www.ituring.com.cn/book/1044)中级篇的读书笔记，旨在：

- 梳理算法逻辑
- 探索优化思路
- 深入代码细节

配套习题及详解同步发布在GitHub仓库[acm-challenge-workbook](https://github.com/yogykwan/acm-challenge-workbook)，持续更新。

# 1.2 程序设计训练题库

- Google Code Jam（[GCJ](https://code.google.com/codejam)）
- Peking University Online Judge（[POJ](http://poj.org/)）
- CodeForces（[CF](http://codeforces.com/)）
- LeetCode（[LC](https://leetcode.com/)）
- Aizu Online Judge（[AOJ](http://judge.u-aizu.ac.jp/onlinejudge/index.jsp?lang=en)）

# 2.1 初级算法

[《挑战程序设计竞赛》初级篇笔记](http://jennica.space/2016/10/14/acm-challenge-easy/)概要：

  1. 穷竭搜索
  2. 贪心
  3. 动态规划
  4. 数据结构
  5. 图论
  6. 数论


# 3.1 二分搜索

## 3.1.1 核心思想

  1. 二分搜索：对于某个有序区间，每次查找区间中点是否满足条件，并以此为依据，决定递归查询左半区间或右半区间。反复循环上述折半过程，直到条件或精度被满足。
  
## 3.1.2 优化细节

  1. STL：以函数lower_bound()和up_bound()的形式实现了二分搜索
  2. 结束判定：1次循环可将区间减半，循环100次可达到精度10^-30 。还可通过区间长度与EPS判断，但要避免EPS太小因浮点数精度问题造成的死循环。
  
## 3.1.3 经典模型

  1. 有序数组中查找某值
  2. 判断一个假定解是否可行
  3. 最大化最小值
  4. 最大化平均值
  
# 3.2 常用技巧

## 3.2.1 核心思想

1. 尺取法：又称两点法，通过在区间上标记并顺序移动头尾两点，将复杂度降为线性。
2. 反转（开关问题）：若为初末态确定，则可通过贪心求得最少步骤。高斯消元法也可求得一组可行解，且自由变元有限，所以也可以求得最优解。
3. 集合的整数表示：通过二进制将集合状态映射至整数。涉及到的位运算包括：与、或、非（取反）、异或、取负（取反+1）、逻辑左移右移、交、并。遍历所有子集或找到所有大小为k的子集，都可以通过位运算操作求得字典序升序的二进制码。
4. 折半枚举（双向搜索）：当全局枚举复杂度太大时，可将条目折半，分别枚举所有情况。复杂度降为原本平方根。
5. 坐标离散化：将数列排序并去重，将原数列离散化映射至有限可控的区间。


---

***转载请注明出处***