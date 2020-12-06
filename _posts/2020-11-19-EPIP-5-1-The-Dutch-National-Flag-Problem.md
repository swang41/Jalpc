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
        break
      else:
        if A[pt2] == pivot:
          A[pt2], A[right] = A[right], A[pt2]
        pt2 -= 1
        right -= 1
```

The code above isn't neat. It need some clean up.

__Solutions from EPIP in the order of efficiency and conciseness.__

### O(n^2) solution:
Idea: First move all the number smaller than pivot to the begining and then moving all the number greater than pivot to the end.

```
def dutch_flag_partition(pivot_index, A):
  
  pivot = A[pivot_index]
  
  #move all the smaller number to the begining
  for i in range(len(A)):
    for j in range(i+1, len(A)):
      if A[j] < pivot:
        A[j], A[i] = A[i], A[j]
        break
   
   #move all the larger number to the end
   for i in reversed(range(len(A))):
    if A[i] < pivot:
      break;
    for j in reversed(range(i)):
      if A[j] > pivot:
        A[j], A[i] = A[i], A[j]
        break
```

### O(n) solution ... two loops:
Idea: Improve the O(n^2) by cutting down the redundant search for smaller number, visit each number once is good enough, just need to keep track of the saving position. Every time find the smaller number just switch the smaller number with the number at the saving position. then move forward for both search and saving position.

```
def dutch_flag_partition(pivot_index, A):
  
  pivot = A[pivot_index]
  
  #smaller
  smaller = 0 #init saving position
  for i in range(len(A)):
    if A[i] < pivot:
      A[i], A[smaller] = A[smaller], A[i]
      smaller += 1
   
  #larger
  larger = 0 #init saving position
  for i in reversed(range(len(A))):
    if A[i] > pivot:
      A[i], A[larger] = A[larger], A[i]
      larger += 1
```


### O(n) ... one while loop:


