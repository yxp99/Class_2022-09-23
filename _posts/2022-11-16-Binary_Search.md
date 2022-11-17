---
layout: post
title: Binary Search
date: 2022-11-16
author: Shadow Walker
tags: [上课记录, BinarySearch]
toc: true
comments: true
---

## BinarySearch

两种方式

### left<=right

```java
// 这个的优势是思路更清晰, 但是当无解的时候会存在 out of bound 的问题. 
private int binarySearch(int left, int right)
{
    while(left <= right)
    {
        int pivot = (left + right )/2;
        if(nums[pivot] == target){
            return pivot;
        }else if(nums[pivot]<target){
            left = pivot +1;
        }else{
            right = pivot -1;
        }
    }
    return -1;
}
```

### left<right


```java
while (left < right) {
	  // 这样取值的优势是防止 right or left = Integer.MAX_VALUE, 这样可以防止integer overflow. 
     int m = left + (right - left)/2  
     if(nums[m] < target) {   // 注意这里, 大部分题目给的都是符合条件的判断, 而并非给的是不符合条件, 所以其实写符合条件的判断, 更不容易出错. 
    	left = m + 1;
    } else {
	right = m;
   }
}
```

优势: 

- 结束的时候 left = right, 不存在讨论取 left 还是取 right 的问题
- 可以安心使用 nums[m + 1], 绝对不会超出边界. 

### lower bound & upper bound

upper bound 的表达方式有三种:

- int mid = left + (right - left) / 2 + 1
- int mid = right - (right - left) / 2
- int mid = left + (right - left + 1) / 2

栗子: [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

Binary的难点在于边界判断, 对于边界判断, 就刷1095题, 一道题基本涵盖了所以可能的binary search边界处理. 对于理解bianry search大有帮助. 

## Search in sorted array/matrix

### when to use

- sorted array/matrix. (must be for the first type)
- too simple to solve with O(n), for example : [LC 1060](https://leetcode.com/problems/missing-element-in-sorted-array/)

### Basic Simple Applications

- Leetcode: 34, 35, 278.  简单搜索题目, 如果对模板不熟, 可以拿来刷.  

### 74. Search a 2D Matrix

### 查 peak 类问题

- 162 Find Peak Element
- 852 Peak Index in a Mountain Array
- 1901 Find a Peak Element II
- 1095 Find in Mountain Array

### 数学 59/60

### 非常规

Binary search 有一些非常规题目比如 [540 Single Element in a Sorted Array ](https://leetcode.com/problems/single-element-in-a-sorted-array/). 

## 区间取值问题 | 切糕问题

### When to use

这类问题的特点是根据条件可以选取一个最大值和最小值, 然后在这两个点之间选取满足题目条件的值.  满足条件的值肯定是min/max. 

- 在array上的取值一般是有连续性的, 目前还没有看到例外, 1482题比较特殊, 虽然用了条件判断, 但也是连续的. 
- 无论求 min/max, 必须是用在每一步的判断, 不存在叠加关系, 不然如果是整体的min/max, 则需要用DP, 例如 [Leetcode 1000](https://leetcode.com/problems/minimum-cost-to-merge-stones/)
- for loop的比较过程也一定是O(n). 

### How to use

- 所有切糕问题都可以完全不讨论边界, 直接用Integer.MAX_VALUIE来做, 但注意一下1011, 不用边界很可能需要在check之中查一下是否OK. 另外OA可以直接用, 提升效率, 但面试的时候有的面试官不认可, 不认可的话他会告诉你, 告诉你之后你就主动改成边界讨论版就好, 不要跟他理论. 或者你觉得有的题边界讨论很简单, 那直接讨论一下也可以. **总之讨论边界版是常规做法, 不讨论边界是取巧.**
- 切糕问题分三个部分, 讨论边界, binary search 和 check, 其中 前两步都不应该产生过度思考, 可以通过刷题/背模板达到通透. 思考应该在check那一步, 要确保一下check那一步正确即可. 

## 题目

- 简单入门: 1011, 875, 1482
- 核心: 1095, 410, 1891
- 难: 1231
- 偏: 774, 540
