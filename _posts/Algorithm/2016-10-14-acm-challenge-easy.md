---
layout:     post
title:      "《挑战程序设计竞赛》初级篇笔记"
subtitle:   ""
date:       2016-10-14
author:     "Jennica"
header-img: "img/post-bg-acm.jpg"
catalog: true
tags:
    - 算法
    - 读书
---

> 王者归来。

# 1.1 算法笔记
本篇为[《挑战程序设计竞赛（第2版）》](http://www.ituring.com.cn/book/1044)初级篇的读书笔记，旨在：

- 梳理算法逻辑
- 探索优化思路
- 深入代码细节
- 撰写[解题报告](https://github.com/yogykwan/acm-challenge-workbook)

# 1.2 程序设计竞赛
- Google Code Jam（[GCJ](https://code.google.com/codejam)）
- Peking University Online Judge（[POJ](http://poj.org/)）
- CodeForces（[CF](http://codeforces.com/)）
- LeetCode（[LC](https://leetcode.com/)）
- Aizu Online Judge（[AOJ](http://judge.u-aizu.ac.jp/onlinejudge/index.jsp?lang=en)）

***updated at 2016.10.14***

---

# 2.1 穷竭搜索

## 2.1.1 核心思想
1. 深度优先搜索（DFS）：从某个状态开始，不断转移，直至无法转移，回退到前一步，再继续转移到其他状态，直到找到最终解。通常采用递归函数或者栈（Stack）来实现。

2. 宽度优先搜索（BFS）：从初始状态开始，总是先搜索至距离初始状态近的状态。每个状态都只经过一次，因此复杂度为O(状态数*转移方式数)。通常采用循环或队列（Queue）实现。

## 2.1.2 优化细节
1. 特殊状态枚举：可行解空间多数可采用DFS，但当其比较特殊时，可简短地实现。
如：全排列使用STL中的next_permutation，组合或子集使用位运算。

2. 剪枝：明确知道从当前状态无论如何转移都不会存在解的情况下，不再继续搜索而是直接跳过。

3. 栈内存与堆内存：
main函数中的局部变量存储在栈内存中，统一分配后不再扩大，影响栈深度，与机器设置有关。通常，C++中执行上万次递归是可行的。
new或malloc的分配的是堆内存，全局变量存储在堆内存中，使用全局变量代替局部变量可减少栈溢出的风险。

4. 加深深度优先搜索（IDDFS）：初始的DFS递归深度限制为1，在找到解之前不断增加递归深度。

***updated at 2016.10.15***

---

# 2.2 贪心

## 2.2.1 核心思想

1. 贪心算法：遵循某种规律，不断贪心选取当前最优策略。
2. 贪心证明：
    * 与其它选择方案相比，该算法并不会得到更差的解（归纳法）
    * 不存在其他的解决方案（反证法）


# 2.3 动态规划

## 2.2.1 核心思想

1. 动态规划（DP）：通过定义某种最优状态，进行状态间转移达到最终解。
2. 记忆化搜索：将重复状态通过标记降低复杂度。
3. 多种形式的DP：搜索的记忆化或利用递推关系的DP，或从状态转移考虑的DP。状态定义和循环顺序都会影响复杂度。

## 2.1.2 优化细节

1. 使用memset初始化
2. 重复循环数组
3. dp仅bool是一种浪费
4. 根据规模改变DP对象


# 2.1.3 经典模型

1. 背包问题（01背包，完全背包）
2. 最长子序列（LCS，LIS）
3. 划分数（第二类Stirling数，Bell数）
4. 组合数问题


***updated at 2016.10.16***

---



***转载请注明出处***
