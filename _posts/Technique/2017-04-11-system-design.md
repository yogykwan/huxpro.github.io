---
layout:     post
title:      "系统设计原理"
subtitle:   ""
date:       2017-04-11
author:     "Jennica"
header-img: "img/post-bg-internet.jpg"
catalog: true
tags:
    - 技术
    - 系统设计
---


# 习题

- [system-design](https://github.com/yogykwan/system-design) - mock exercises for system design.

# 基础

## 4S分析法

1. Scenario：功能、需求、QPS、存储容量
2. Service：逻辑块聚类、函数设计、访问接口设计
3. Storage：选择SQL或NoSQL、OOD细化Schema
4. Scale：可能遇到的问题、优化系统

## SQL和NoSQL选择标准

1. SQL：支持transaction；query丰富；Sequential id；与Web框架兼容好
2. NoSQL：支持高QPS；不需要自己写Scale，如sharding和replica

## 如何sharding

1. 水平sharding：将表的不同列拆开
2. 垂直sharding：按行拆分至多台数据库，利用一致性hash决定放在哪台
3. 一致性hash：为每台机器在int64的环上随机分配1000虚拟节点，写入hash值顺时针遇到的第一个虚拟结点代表的机器

## 如何replica

1. SQL：自带master和slave进行有延迟的replica，可再手动在sharding时写入连续的3台虚拟结点机器
2. NoSQL：自动sharding时写入连续的3台虚拟结点机器，无需手动再replica

## 提高访问效率

1. Web服务器与数据服务器：利用缓存提高读，拆分数据库sharding提高写
2. 用户与服务器：不同地区用不同Web服务器，中心化服务器集群（共享数据库）+分布式缓存
3. 中心化服务器集群与跨地域Web服务器：按地域热点sharding到本地数据
