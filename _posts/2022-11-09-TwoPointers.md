---
layout: post 
title: Two Pointers & Sliding Window
date: 2022-11-09
author: Shadow Song
tags: [上课记录,SlidingWindow, TwoPointers]
toc: true
comments: true
---

## 相向指针

### Two Sum II - Input array is sorted LC_167
### 3Sums LC15
### Container With Most Water LC_011

## 同向指针

### LC438_Find All Anagrams in a String

## Sliding Window

239 **monostatic queue**, 992, 76

## 快慢针

- 用法比较单一, Linkedlist, 提取index

### LC876_Middle of the Linked List


### LC19_Remove Nth Node From End of List

一道在LinkedList上的快慢指针. 一开始看很简单, 其实不然. 思路很简单, 但具体edge case很特殊, 不好处理. 需要考虑的是只有一个元素和remove head的情况, 所以加装这个dummy head. 

**19题, 1721题, 1474 这三道题同宗同源**. 其中最难的是19题, 需要考虑的稍微多一些.  如果要刷的话, 就刷19题吧. 

**code**


## 总结

### 什么时候用

- 基本上是Array/String, 可以说SlidingWindow一定是array/String.  然后twoPointer不一定. 
- 不能存在区间内的求和关系. 
- 一段区间之内, 产生连续关系的时候, 使用SlidingWindow

### Sliding Window

- **等于 Two Pointer + 一段中间数据的存储**.  存储方式通常有 HashSet, HashMap 或者 Deque. 
- 如果不需要存储的情况是纯two pointer, Deque 和 两个index two pointer都可以做. 首选two pointers.

### 边界条件

- 针是不是碰到了边界.  j<n
- 相向i < j 
- 同向情况: 可以需要考虑的一个因素, 每一次, j必往右走一步, i走不走, 情况判断. 这样可以尽量保证, j在i右边.   

### 技巧

- HashMap常用, 记录 freq, 记录 index
- Deque 记录 滑动窗口内的元素

## 作业

- **3**, 11, 167, 15, **438**, 581, 26, 42(难), 763
- 876, 19, **239**, 992. 239