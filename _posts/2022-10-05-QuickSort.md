---
layout: post 
title: Quick Sort
date: 2022-10-02
author: Shadow Song
tags: [Sorting, 上课记录]
toc: true
comments: true
---

## Quick Sort

- 跟 merge sort 一样是divide and conquer
- 相较于merge sort直接二分, quick是选一个节点进行比较, 然后把节点放在对的位置, 保证节点前比其小, 后面比节点都大, 之后再进行二分. 
- 选节点pivot的方法可以自由发挥, 没有固定规定.
- 与merge sort的不同在于拼回去的过程之中无需再比较

### Algorithm

- Select a 'pivot' element from the array and partitioning the other elements into two sub-arrays, **one subarray with elements less** than the pivot element, **the other with elemnts greater** or equal to the pivot element. 
- The sub-arrays are then sorted **recursively** until only one element is left in each subarrays. 

这个图中里选用的是最后一个数作为节点. 

![Quick Sort Illustration](https://www.techiedelight.com/wp-content/uploads/Quicksort.png)

### Code

{::options parse_block_html="true" /}

<details><summary markdown="span">Let's see some code!</summary>

```java
public static void quickSort(int[] arr){
    qsort(arr, 0, arr.length-1);
}
private static void qsort(int[] arr, int left, int right){
    if(left<right){
        int pivot = partition(list, left, right);
        qSort(list, left, pivot-1);
        qSort(list, pivot+1, right);
    }
}

-3, 2, -6, -1   最后要换 -3 到正确位置.  store_index = 0

-1, 2, -6, -3 

-6, 2, -1, -3  store_index = 1

-6, -3, -1, 2

public static int partition(int[] arr, int left, int right) {
	 // -3, 2, -6, -1   最后要换 -3 到正确位置.  store_index = 0
	 
    int pivot = arr[left]; // 此处选取Left, 也就是第一个数为Pivot. 
    // 1. move pivot to end
    swap(arr, left, right);  // -1, 2, -6, -3 
    int store_index = left; // store_index = 0

    // 2. move all smaller elements to the left
    for (int i = left; i <= right; i++) {
      if (arr[i] < pivot) {
        swap(arr, store_index, i); 
        store_index++; // -6, 2, -1, -3  store_index = 1
      }
    }

    // 3. move pivot to its final place
    swap(arr, store_index, right); // -6, -3, -1, 2
    return store_index;
  }

  public static void swap(int[]arr, int a, int b) {
    int tmp = arr[a];
    arr[a] = arr[b];
    arr[b] = tmp;
  }
```

</details>

{::options parse_block_html="false" /}

### Unstable

1, 2, 3, 4, 2`.  Cannot make sure the array keeps the same order. 

### Space and Time Complexity

For an array, in which partitioning leads to unbalanced subarrays, to an extent where on the left side there are no elements, with all the elements greater than the pivot, hence on the right side.

And if keep on getting unbalanced subarrays, then **the running time is the worst case, which is `O(n^2)`**

Where as if partitioning leads to almost equal subarrays, then the running time is the best, with time complexity as `O(n*log n)`.

- Worst Case Time Complexity [ Big-O ]: `O(n^2)`
- Space Complexity: `O(1)`

### Compare Quick Sort and Merge Sort

- Merge: time complexity stable O(nlogn). require O(n) space. 
- Quick: time complexity not stable. averge O(nlogn), worst scenario O(n^2). O(1) space.

## Quick Select


**重点: FB 和 Amazon 最近两年非常喜欢考 LC347 LC973**

![](https://lh3.googleusercontent.com/pw/AM-JKLWNIJ1Gdr26zSrNm4J3_bG1sqNZukMc4vlIDv-_s-pcZ_fZSz35wHKS6FzwElatBCyHOKjWPUZTwgVRIxBIC5djdTmCMWKgHHfPxlogdRJ9aNDPTNpYh5JMTheshW9pbPbr-_-JNfdQPq0K8mtPXuRy=w1015-h783-no?authuser=0)


### 栗子

4,2,1,3 k = 1, 找里面前k个最小的数. 

2,1   |  3  | 4 

### Code

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        int[] output = new int[k];
        Map<Integer, Integer> hm = new HashMap<>();
        List<Count> countList = new ArrayList<>();
        
        for(int num: nums){
            hm.put(num, hm.getOrDefault(num, 0) + 1);
        }
        
        // 1->3, 2->2, 3->1.
        
        for(Map.Entry<Integer, Integer> entrySet: hm.entrySet()){
            countList.add(new Count(entrySet.getKey(), entrySet.getValue()));
        }
        
        // (1,3), (2,2), (3,1)
        
        this.quickSelect(countList, 0, countList.size() - 1, k);
        for(int i = 0; i < k; i ++){
            output[i] = countList.get(i).num;
        }
        return output;
    }
    
    private void quickSelect(List<Count> countList, int left, int right, int k){
        if (left < right){
            int pivot = sort(countList, left, right);
            if(pivot == k){
                return;
            }else if(pivot < k){
                quickSelect(countList, left + 1, right, k);
            }else{
                quickSelect(countList, left, right - 1, k);
            }
        }
    }

    private int sort(List<Count> countList, int left, int right){
        int index = left;
        int pivotFreq = countList.get(index).freq;
        Collections.swap(countList, index, right);
        
        for(int i = left; i <= right; i++){
            if(countList.get(i).freq > pivotFreq){
                Collections.swap(countList, index ++, i);
            }
        }
        
        Collections.swap(countList, index, right);
        return index;
    }
    
}


class Count{
    int num;
    int freq;
    public Count(int num, int freq){
        this.num = num;
        this.freq = freq;
    }
}
```

## 其他

- [LC912](https://leetcode.com/problems/sort-an-array/) 可以练习默写

## Big-O

- [Guide](https://developerinsider.co/big-o-notation-explained-with-examples/)