---
layout: post 
title: LinkedList
date: 2022-10-19
author: Shadow Song
tags: [上课记录, LinkedList]
toc: true
comments: true
---

## Python

- [Google Python style](https://google.github.io/styleguide/pyguide.html#316-naming)
- [Naming for Python stackOverFlow](https://stackoverflow.com/questions/159720/what-is-the-naming-convention-in-python-for-variable-and-function)

## 分类

LinkedList 分为三种问题: 

- dummyhead
- 138题
- LRU 和 LFU


## DummyHead Template

```python
dummy_head = ListNode(-1)
dummy_head.next = head
prev_node = dummy_head
    
# while loop to operate

return dummy_head.next
```

## LC24

## LC148

找中点 + Merge Sort + 合并两个List.  一道题考三道题. 建议可以用来刷Merge Sort. 

## LC138

## Double LinkedList

```python
class DLinkedNode(): 
    def __init__(self):
        self.key = 0
        self.value = 0
        self.prev = None
        self.next = None
        
    def _add_node(self, node):
        """
        Always add the new node right after head.
        """
        node.prev = self.head
        node.next = self.head.next

        self.head.next.prev = node
        self.head.next = node

    def _remove_node(self, node):
        """
        Remove an existing node from the linked list.
        """
        prev = node.prev
        new = node.next

        prev.next = new
        new.prev = prev

    def _move_to_head(self, node):
        """
        Move certain node in between to the head.
        """
        self._remove_node(node)
        self._add_node(node)

    def _pop_tail(self):
        """
        Pop the current tail.
        """
        res = self.tail.prev
        self._remove_node(res)
        return res
```

## LC146_LRU

应用: 
- stream
- keyword: first/last, most/least frequent. 
- Need to optimize: add, remove, insert, all O(1). 

Millions of customers visit the Amazon websites. For a marketing campaign it is required to be able to:

1. Keep record of the number of times a given customer has visited the site
2. Most importantly, Marketing wants to know the first ONE TIME VISITOR (the first customer to visit the site only once). 
3. For customers = B, D, E, A, D, ,C, B, ... Result = E .


Solution:

maintain double-linked list to hold valid customers (new customers added to tail)

keep hashmap <customer, node pointer> to hold valid customer pointers

maintain a set of invalid customers

for each customer:

if he's in invalid customers, skip
if hes not in invalid, but in hashmap, remove him from hashmap, add to invalid, and unlink the node by using the pointer stored in the map
if hes not invalid, and not in hashmap, he's a new customer. add him to the tail of the linked list.
the result is the head of the linkedlist.

O(1) for all operations
total runtime O(n), after processing each customer with O(1)

## 总结

- 遍历链表的时候，新创建一个头节点，以方便返回. 链表一般要开一个新节点以便回归头节点
- 倒着遍历或者从某位数第n个元素的时候, 用快慢指针
- **双向链表（LRU）**
- Null和走到末尾. 注意查next是否为空.   edge case. 
- 遍历的过程中用pre来记录前一个遍历的节点
- **链表 vs Array**：增加：链表插入的时候不用后移元素，删：链表删除不用后移元素，查找时间复杂度O(n)

## 作业

- 206, 876, 92, 148, **138, 146**