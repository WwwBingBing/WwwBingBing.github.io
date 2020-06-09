---
layout: post
title: "leetcode: 爬楼梯"
categories: JavaScript
tags: 算法 数据结构 leetcode
author: superw
---

- content
{:toc}

## 爬楼梯

题目如下：

> 假设你正在爬楼梯。需要 n 阶你才能到达楼顶。每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。


#### 示例

    输入： 2
    输出： 2
    解释： 有两种方法可以爬到楼顶。
    1.  1 阶 + 1 阶
    2.  2 阶

    输入： 3
    输出： 3
    解释： 有三种方法可以爬到楼顶。
    1.  1 阶 + 1 阶 + 1 阶
    2.  1 阶 + 2 阶
    3.  2 阶 + 1 阶

#### 思路分析

这道题目是一道非常高频的面试题目，也是一道非常经典的斐波那契数列类型的题目。

解决本道题目我们会用到动态规划的算法思想-可以分成多个子问题，爬第 n 阶楼梯的方法数量，等于 2 部分之和：

- 爬上n−1阶楼梯的方法数量，因为再爬 1 阶就能到第 n 阶
- 爬上n−2阶楼梯的方法数量，因为再爬 2 阶就能到第 n 阶













可以得到公式：

> climbs[n] = climbs[n-1] + climbs[n-2]

同时需要做如下初始化：

> climbs[0] = 1; climbs[1] = 1

```javascript
var climbStairs = function(n) {
    let climbs = [];
    climbs[0] = 1;
    climbs[1] = 1;
    for(let i = 2; i<= n; i++) {
        climbs[i] = climbs[i-1] + climbs[i-2]
    }
    return climbs[n]
};

```
