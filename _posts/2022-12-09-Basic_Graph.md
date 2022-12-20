---
layout: post
title: Basic Graph
date: 2022-12-09
author: Shadow Song
tags: [Graph]
toc: true
comments: true
---

## Concept

- vertex, edge. 
- weight, direction. 
- cycle, bridge. 

## Construction

```java
// Build a hashmap graph
Map<Integer, List<Integer>> graph = new HashMap<>();
for(int i=0; i<n; i++){
    graph.put(i, new ArrayList<>());
}
    
for(int[] edge: edges){
    int first = edge[0];  // 0
    int second = edge[1]; // 1
    List<Integer> l1 = graph.get(first);  // l1 is all the edges of 0.
    List<Integer> l2 = graph.get(second); // l2 is all the edges of 1.
    l1.add(second); // add 1 to 0's edge list
    l2.add(first); // add 0 to 1's edge list
}
```

## 奇特的input 类型 举例

![](https://lh3.googleusercontent.com/pw/AM-JKLXXjHARmQzq91ysHWFq45ytoaiI0x99OQyn6pAoIHP515_hT1XlGZF3VWzNk0yHuM0VCMnsPz4K8pb9ZhEDoTcfVJwbtn5DrVp78kQ-k1YLGGSoa4K5jqkyDH9pAGsBrElCZjE2fxCHiEx7h70Hp-Wy=w500-h730-no?authuser=0)

## dfs Traverse

- Leetcode 323

## Time Complexity and Space Complexity

- TC: O(V+E)
- Space Complexity: O(V+E)