---
layout: post
title:  "4.2 Swap bits"
date:   2020-10-23
desc: "Swap ith bit with jth bit"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

```
'''
Problem: swap ith bit with jth bit
'''

#Brute force
def swap_bit(x, i, j):
	bit_i = x >> i & 1
	bit_j = x >> j & 1
	if bit_i != bit_j:
		if bit_i:
			x &= bit_i << j
			x ^= bit_j << i
		else:
			x ^= bit_i << j
			x &= bit_j << i
	return x

#Rewrite brute force
def swap_bit(x, i, j):
	if (x>>i) & 1 != (x>>j) & 1:
		bit_mask = (1 << i) | (1 << j)

```
