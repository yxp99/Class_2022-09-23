---
layout: post 
title: Matrix Traversal
date: 2022-11-02
author: Shadow Song
tags: [上课记录, Matrix]
toc: true
---

## DFS

- 200

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:

        if not grid:
            return 0

        ROW, COL = len(grid), len(grid[0])

        def dfs(row, col):
            if checkBoundary(row, col):
                grid[row][col] = '0'

                dfs(row + 1, col)
                dfs(row - 1, col)
                dfs(row, col + 1)
                dfs(row, col - 1)
        
        def checkBoundary(row, col):
            return row>=0 and col>=0 and row<ROW and col<COL and grid[row][col] == '1'

        output = 0
        for row in range(ROW):
            for col in range(COL):
                if grid[row][col] == '1':
                    dfs(row, col)
                    output += 1
        return output
```

## BFS

- 994

## 难题

- 827, 用 695的图来讲. 


## 技巧

- DFS 模板
- 染色, 去色


## Problems

- Leetcode练习: 1730, 岛系题目, 490

## Time complexity and Space complexity

both O(m x n)
