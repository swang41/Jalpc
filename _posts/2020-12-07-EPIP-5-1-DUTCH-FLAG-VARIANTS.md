---
layout: post
title:  "5.1 The Dutch Flag Problem Variants"
date:   2020-12-07
desc: ""
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Variant#1: Assuming that keys take one of three values, reorder the array so that all objects with the same key appear together. The order of subarrays is not important. For example, both Figure 5.1(b) and 5.1(c) on Page 40 are valid answers for Figure 5.1(a) on Page 40. Use O(1) additional space and O(n) time.
idea: use the solution for dutch flag problem but checking the key's value instead of evaluting if the key iteself within the while loop.
```
#assume we know the the three values are 1, 2, 3
def dutch_flag_problem_v1(dict, A):
  smaller, i, larger = 0, 0, len(A)
  while i < larger:
    if dict[A[i]] == 1:
      A[i], A[smaller] = A[smaller], A[i]
      i += 1
      smaller += 1
    elif dict[A[i]] == 2:
      i += 1
    else:
      larger -= 1
      A[i], A[larger] = A[larger], A[i]
```


Variant#2: Given an array A of n objects with keys that takes one of four values, reorder the array so that all objects that have the same key appear together. Use O(1) additional space and O(n) time.
idea: Simplify the problem as variant#1 by arbitrarty pick two keys and treat them as one key. After the first reordering, reset the i to smaller and strat to reorder the subarray this treat the two keys differently. 
```
#assume we know the four values are 1, 2, 3, 4
def dutch_flag_problem_v2(dict, A):
  smaller, i, larger = 0, 0, len(A)
  while i < larger:
    if dict[A[i]] == 1:
      A[i], A[smaller] = A[smaller], A[i]
      i += 1
      smaller += 1
    elif dict[A[i]] == 2 or dict[A[i]] == 3:
      i += 1
    else:
      larger -= 1
      A[i], A[larger] = A[larger], A[i]
 for i in range(smaller, larger):
  if dict[A[i]] == 2:
      A[i], A[smaller] = A[smaller], A[i]
      smaller += 1
```


Variant#3: Given an array A of n objects with Boolean-valued kyes, reorder the array so that objects that have the key false appear first. Use O(1) additional space and O(n) time.
```
def dutch_flag_problem_v3(dict, A):
  smaller = 0
  for i in range(len(A)):
    if not dict[A[i]]:
      A[i], A[smaller] = A[smaller], A[i]
      smaller += 1
```


Variant#4: Given an array A of n objects with Boolean-valued keys, reorder the array so that objects that have the key false appear first. The relative ordering of objects with key true should not change. Use O(1) additional space and O(n) time.
```
ie: [2t 1f 2f 1t 3f 4t] --> [1f 2f 3f 1t 2t 4t]
def dutch_flag_problem_v3(dict, A):
  larger = len(A)-1
  for i in reversed(range(len(A))):
    if dict[A[i]]:
      A[i], A[larger] = A[larger], A[i]
      larger -= 1
```
