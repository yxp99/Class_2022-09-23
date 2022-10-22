---
layout: post 
title: Prefix Sum
date: 2022-10-21
author: Shadow Song
tags: [上课记录]
toc: true
comments: true
---

## 分类

- Array
- Matrix

## 栗子

- Leetcode 560

```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        count = 0
        sums = 0
        dic = {0 : 1}
        
        
        for num in nums :
            
            sums += num
            if sums - k in dic :
                count += dic.get(sums - k)

            dic.update({sums : dic.get(sums, 0) + 1})

        return count
    
```

## 特点

- 解法固定, 套用模板
- 关键词: **continuous subarray**, consecutive elements,  consecutive sequence, Subarray Sum
- Array中的元素可以为负数, 无影响. 见560题条件. 

## 技巧

- 记录什么?  和对应的公式
- 起点
- Matrix 公式


## Problems

- 典型: 523, 560,

- Matrix: 304

- 练习题: 128, 1248, 974, 325,  Matrix: 1314

- 剑指: 66(题不好, 非常规prefix sum). 
