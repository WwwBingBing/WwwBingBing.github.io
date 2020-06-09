---
layout: post
title: "leetcode: 括号生成"
categories: JavaScript
tags: 算法 数据结构 leetcode
author: superw
---

- content
{:toc}

## 括号生成

题目如下：

> 数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。

注意：给定 n 是一个正整数。


#### 示例

    输入：n = 3
    输出：[
          "((()))",
          "(()())",
          "(())()",
          "()(())",
          "()()()"
        ]


#### 思路分析

这道题目通过 `递归` 去实现。

因为左右括号需要匹配、闭合。所以对应“(”和“)”的数量都是n，当满足这个条件时，一次递归就结束，将对应值放入结果数组中。
这里有一个潜在的限制条件：有效的括号组合。对应逻辑就是在往每个位置去放入“(”或“)”前：

- 需要判断“(”的数量是否小于 n
- “)”的数量是否小于“(”

![img](https://user-gold-cdn.xitu.io/2020/6/8/17291e03e2e57427?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)


















```javascript
var generateParenthesis = function(n) {
    let res = []
    const generate = (cur, left, right) => {
        if (left ===n && right === n) {
            res.push(cur)
            return
        }
        if (left < n) {
            generate(cur + '(', left + 1, right)
        }
        if (right < left) {
            generate(cur + ')', left, right + 1)
        }
    }
    generate('', 0, 0)
    return res
};

```
