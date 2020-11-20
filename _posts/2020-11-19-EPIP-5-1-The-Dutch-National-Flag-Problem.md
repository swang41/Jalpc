---
layout: post
title:  "5.1 The Dutch Flag Problem"
date:   2020-11-19
desc: ""
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program that takes an array A and an index i into A, and rearranges the elements such that all element less than A[i](the "pivot") appear first, followed by elements equal to the pivot, followed by elements greater than the pivot.

```
idea: simplify the problem into reorder element less than pivot at the begining and element greater than pivot at the end.
pivot = A[i]
pt1, pt2, num_eq_pivot = 0, 0, 0
while pt2 < len(A):
  if A[pt2] < pivot and pt2 < pt1:
    while pt1 < len(A) and A[pt1] < pivot:
      pt1 += 1
    A[pt2], A[pt1] = A[pt1], A[pt2]
  elif A[pt2] == pivot:
    num_pivot += 1
  else:
    
  
    
```
