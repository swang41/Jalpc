---
layout: post
title:  "5.2 Increment Arbitrary Precision Integer"
date:   2020-12-07
desc: ""
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program which takes as input an array of digits encoding a decimal integer D and updates the array to represent the interger D+1. For example, if the input is <1,2,9> then you should update the array to <1,3,0>.


```
ie: <1, 2, 9>  --> <1, 3, 0>
idea: add 1 to the last number in the array, check the arrary from left to right if the number greater than 9, mimus by 10 and carry 1 out to the right, if the position is the first minus by 10 and insert 1 in the begining of the array.
def incre_int_arr(A):
  A[-1] += 1
  for i in reversed(range(1, len(A))):
    if A[i] > 9:
      A[i-1] += 1
      A[i] -= 10
  if A[0] > 9:
    A[0] -= 10
    A.insert(0, 1)
```
