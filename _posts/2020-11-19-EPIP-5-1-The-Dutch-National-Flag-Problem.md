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
ie: [4, 1, 3, 8, 2, 4]
pivot = A[i]
pt1, pt2, left, right = 0, len(A)-1, 0,len(A)-1
while left <= right:
  if A[left] == pivot:
    left += 1
  elif A[left] < pivot:
    if A[pt1] == pivot:
      A[pt1], A[left] = A[left], A[pt1]
    pt1 += 1
    left += 1
  else:
    while left <= right:
      if A[right] <= pivot:
        A[right], A[left] = A[left], A[right]
        right -= 1
      else:
        if A[pt2] == pivot:
          A[pt2], A[right] = A[right], A[pt2]
        pt2 -= 1
        right -= 1
        

    
    
        
```
