---
layout: post
title: Backtrack
date: 2022-11-06
author: Shadow Song
tags: [上课记录, Backtrack]
toc: true
---


## 刷题顺序

## 简单

- 77 Combinations
- 78 Subsets
- 46 Permutations

### 核心

Backtrack的核心是三道题. 这三道题覆盖了很多其他题目.

- 40 Combination Sum II
- 47 Permutations II  
- 90 Subsets II  


### 好题

好题是难度跟核心类似但普遍性稍差的题目. 

- 131 Palindrome Partition 这道本质不难. 就是复合题.  i+1组合复杂条件判断组合双指针. 
- 698 Partition to K Equal Sum Subsets. 跟上面的131一样, 也是i+1条件判断跳跃. 只不过这道更难更复杂. 目前在条件判断跳跃之中, 这道是最难的.   可以理解为更加复杂的40题. 40题如果刷熟了的话可以刷这道. 

## 题号

* 78 Subsets (combination)
* 90 Subsets II(必刷)
* 46 Permutations
* 47 Permutations II (必刷)
* 77 Combinations
* 39 Combination Sum (简单)
* 40 Combination Sum II (必刷)
* 216 Combination Sum III
* 377 Combination Sum IV (没做)
* 131 Palindrome Partition
* 132 Palindrome Partitioning II (DP)
* 1278 Palindrome Partitioning III (DP)
* 1745 Palindrome Partitioning IV (DP)
* 267 Palindrome Permutation II (和47题重复)
* 17 Letter Combinations of a Phone Number
* 698 Partition to K Equal Sum Subsets


偏题/难题: 

- 60  Permutation Sequence
- 1048 Longest String Chain

应用题: 

- 1152 亚麻高频 建议看
- 526 Beautiful Arrangement
- 126 Word Ladder II  (难, 但是道好题, 有时间值得一看)

## Complexity Analysis

这一系列题目complexity通常都是一样的.  下面这个来自40题的截图. 


![](https://lh3.googleusercontent.com/pw/ACtC-3c4oY-srWO5rgHXDog4EJgOwDgkPWm7KQZwc5BChp3HETIKyX42dHECkEOMOE16ogL2C0CC1qCIMk2sUAY9FvKvl8A5VJPIfzJjlUsVUdUcyuyXFFkP_XeX9ZTwZlsMZalm-Gh-0pYV4Q-acsbS-p0J=w635-h436-no?authuser=0)

![](https://lh3.googleusercontent.com/pw/ACtC-3cXpes0x0OomgMlI0v6fqanlpM5ywD-NaCTHarbHgOzkN72UOChrdXluAVLKPRsj9ABzzLArSGqjJBNVsJHTHPYidbJGmGLRwc_kAhOb0T9R3SW4nlql5zsCgeYyid8e2NSyYBsJGPZz4-3O7KG8FD0=w617-h576-no?authuser=0)

## 总结

这一块是重点, 需要熟练掌握. 纯粹的backtrack由于算力过大其实不常考, 但碰见难题解不掉的时候可以暴力解救命. 常见的类型是把backtrack融合在题目之中,也就是应用题, 所以一般都不是太难. 

建议第一轮可以把题号上的非难题都刷一遍, 之后只刷三道核心, 三道核心刷熟刷透即可, 这一块没必要大量做题, 也没有必要刷太难的题目. 
