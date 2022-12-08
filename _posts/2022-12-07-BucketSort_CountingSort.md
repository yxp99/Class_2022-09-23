---
layout: post 
title: Bucket Sort & Counting Sort
date: 2022-12-07
author: Shadow Song
tags: [Sorting]
toc: true
comments: true
---

## Overview

- easy: Bubble, Insertion, Selection. 
- core: Merge, Quick, Heap. 
- rare: Bucket, Counting, Radix. 

## Concept

- stable
- [comparison srot](https://en.wikipedia.org/wiki/Comparison_sort#:~:text=A%20comparison%20sort%20is%20a,in%20the%20final%20sorted%20list.)

## Practice

- [912 Sort an Array](https://leetcode.com/problems/sort-an-array/) 这道题可以用来练习所有的sorting

## Bucket Sort

### Algorithm

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/scene01801.jpg)

```
define function bucketSort(arr[]) as
    step 1: create as many empty buckets (lists or arrays) as the length of the input array
    step 2: store the array elements into the buckets based on their values (described in step 3)
    step 3: for i from 0 to length of arr do
                (a) bucket_index = int((n * arr[i]) / 10) //here n is the length of the input array
                (b) store the element arr[i] at bucket[bucket_index]
    step 4: for i from 0 to length of bucket do:
                (a) sort the elements stored inside bucket[i], either by applying recursion or by 
                    some other sorting method
    step 5: push the values stored in each bucket starting from lowest index to highest index to a 
            new array/list
step 6: return the sorted array/list
```

### Why inner sort is O(1)

Because we assume there are lots of bucket and each bucket only have a few elements. A few means the size of the bucket is really small compare to the length of the array. 

### When to use

- Bucket sort assumes that the input is drawn from a uniform distribution.
- The computational complexity estimates involve the number of buckets.

### Time complexity & space complexity

- Time complexity: `O(n + k)`
- Space Complexity: `O(n + k)`
- worst case: `O(n²)`
- Best Case: `O(n + k)`
- Average Case: `O(n + n²/k + k)`, `O(n)` when `k = Θ(n)`

where

- n is the number of elements
- k is the number of buckets

### 347 Top K Frequent Elements

## Counting Sort


### 两种实现方式

- 第一种, 目前找到[最好的图示理解](https://www.evernote.com/shard/s573/sh/2d2e97f4-cdf3-4e4a-acdf-b1e38d110709/76bef9329ebc7082c1060712a08845b2), 一看就懂
- 第二种, [Video](https://youtu.be/7zuGmKfUt7s)

### Time and space complexity

- Time Complexity: `O(n+k)` where n is the number of elements in the input array and k is the range of input. 
- Space Complexity: `O(n+k)`

### 912 Basic Sorting

- 普遍常规快速版版

这一版traverse 原 array 需要花时间理解, 优势是快. 

```java
class Solution {
    public int[] sortArray(int[] nums) {
        //-50000 <= nums[i] <= 50000
        // you can even use a smaller array if you know min and max values
        int[] count = new int[100_001]; 
        for (int num: nums) {
            count[num + 50_000]++;
        }
        
        for(int i = 1; i < 100_001; i ++){
            count[i] += count[i - 1];
        }
        
        int[] output = new int[nums.length];

        for(int i = nums.length - 1; i >= 0; i --){
            output[count[nums[i] + 50_000] - 1] = nums[i];
            -- count[nums[i] + 50_000];
        }

        return output;
    }
}
```

- 简洁版

这一版来自leetcode, 更易懂, traverse count array但慢. 

```java
class Solution {
    public int[] sortArray(int[] nums) {
        //-50000 <= nums[i] <= 50000
        // you can even use a smaller array if you know min and max values
        int[] count = new int[100_001]; 
        for (int c: nums) {
            count[c + 50_000]++;
        }
        // use new array
        int[] res = new int[nums.length];
        int i = 0;
        for (int j = 0; j < count.length; j++) {
            while (count[j] > 0) {
                res[i++] = j - 50_000;
                count[j]--;
            }
        }
        return res;
    }
}
```

### Problems

不重要

- [1094 Car Pooling](https://leetcode.com/problems/car-pooling/)
- [274 H-Index](https://leetcode.com/problems/h-index/)
- [164 Maximum Gap](https://leetcode.com/problems/maximum-gap/)


