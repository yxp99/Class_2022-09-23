---
layout: post 
title: Space Complexity
date: 2022-09-23
author: Shadow Song
tags: [上课记录]
toc: true
comments: true
---

## Space Complexity

Data | SC
---|---
Fixed size any data structure: `int[] arr = new int[1000]` | O(1)
Fixed size HashMap for English chars: `Map<Character, Integer>` | O(26) = O(1)
`Map<Integer, Integer>`| O(n)
`Map<Integer, List<Integer>>` | O(n^2)   O(nm)
`Map<Integer, List<List<Integer>>` | O(n^3)
`int[][]` | O(n^2)
`int[]` | O(n)