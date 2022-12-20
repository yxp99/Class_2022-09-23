---
layout: post
title: Topological Sort
date: 2022-12-09
author: Shadow Song
tags: [Graph, Algorithm]
toc: true
comments: true
---

## When to use

- Use to find cycles in directed graph. 
- cannot apply to undirected graph. 

## Algorithm

1. 便利每一个节点，根据输入来.  
	a. 并记录每一个节点的入度map<节点，入度的值>.  
	b. 每一个节点指向的节点map<节点，［指向的节点］>.  
2. 把入度为0的节点放入queue中. 
3. BFS.   
	a. 从queue中pop元素，counter＋＋.  
	b. 查看当前节点指向的节点，并把指向的节点的入度的值减1，并把指向的节点的入度为0的元素放入queue中.  
	c. 重复i直到queue为空.  
	
## Problems 

- 核心: 207, 210. 
- 其他: 444
- 难:  269