---
layout:     post
title:      "《挑战程序设计竞赛》初级篇"
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

# 1.1 程序设计竞赛
1. Google Code Jam（[GCJ][1]）
2. Peking University Online Judge（[POJ][3]）
3. CodeForces（[CF][2]）
4. LeetCode（[LC][4]）

*updated at 2016.10.14*

# 2.1 穷竭搜索（updated at 20161015）
## 2.1.1 核心思想
1. 深度优先搜索（DFS）：从某个状态开始，不断转移，直至无法转移，回退到前一步，再继续转移到其他状态，直到找到最终解。通常采用递归函数或者栈（Stack）来实现。
2. 宽度优先搜索（BFS）：从初始状态开始，总是先搜索至距离初始状态近的状态。每个状态都只经过一次，因此复杂度为O(状态数*转移方式数)。通常采用循环或队列（Queue）实现。
## 2.1.2 优化细节
1. 特殊状态枚举：可行解空间多数可采用DFS，但当其比较特殊时，可简短地实现。
A(n,n): STL中的next_permutation
C(n,m)或全部子集：位运算
2. 剪枝：明确知道从当前状态无论如何转移都不会存在解的情况下，不再继续搜索而是直接跳过。
3. 栈内存与堆内存：
main函数中的局部变量存储在栈内存中，统一分配后不再扩大，影响栈深度，与机器设置有关。通常，C++中执行上万次递归是可行的。
new或malloc的分配的是堆内存，全局变量存储在堆内存中，使用全局变量代替局部变量可减少栈溢出的风险。
4. 加深深度优先搜索（IDDFS）：初始的DFS递归深度限制为1，在找到解之前不断增加递归深度。

*updated at 2016.10.15*

---

***转载请注明出处***

[1]: https://code.google.com/codejam
[2]: http://codeforces.com/
[3]: http://poj.org/
[4]: https://leetcode.com/

