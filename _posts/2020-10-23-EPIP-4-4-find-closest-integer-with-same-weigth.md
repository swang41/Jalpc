---
layout: post
title:  "4.4 Find closest integer with same weight"
date:   2020-10-23
desc: "Find closest integer with same weight, the weight is the number of bit with 1"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

```
'''
Write a program which takes as input a nonegative integer x and return
a number y which is not equal to x, but has the same weight as x and 
their difference, |y-x| is as small as possible.
'''

#brute force
'''
Searching for the first integer with same weight by moving 1 unit away 
from x at a time
'''
def closest_int_same_weight(x):
	def weight_int(x):
		LENGTH = 64
		res = 0
		for i in range(LENGTH):
			res += x & (1 << i)
		return res

	def has_same_wt(x, y):
		'''Assume the nonegative integer x is saved as 64bit'''
		return weight_int(x) == weight_int(y)

	i = 1
	while i < x:
		cand = x-i
		if has_same_wt(x, cand):
			return cand
		cand = x+i
		if has_same_wt(x, cand):
			return cand
		i += 1
	if i == x:
		return -1


#optimized version
'''
Assume flip index at k1 and k2, where k1 > k2, the goal is to find the
qualified pair k1, k2 where bit on k1 and k2 are different where k1 
k2 are closest enough
'''
def closet_int_same_weight(x):
	LENGTH = 64
	while i + 1 < LENGTH:
		if (x & (1 << (i + 1))) ^ (x & (1 << i)):
			return  (x ^ (1 << (i + 1))) ^ (1 << i))
```
