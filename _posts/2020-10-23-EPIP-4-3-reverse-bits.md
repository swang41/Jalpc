---
layout: post
title:  "4.3 Reverse bits"
date:   2020-10-23
desc: "Reverse bits of a integer by swap the front to the end, second front to the second end and etc"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

```
'''
Write a program that takes a 64bit unsigned integer and returns the 64bit usigned integer consisting of the bits
of the input in reverse order.
'''

#brute force with swap bit function
def reverse_bits(x):
	LENGTH = 64
	for i in range(LENGTH//2):
		x = swap_bit(x, LENGTH-i, i)
	return x


#Use a lookup table, 2^16 = 60k combination
def reverse_bits(x):
	MASK_SIZE = 16
	BIT_MASK = 0XFFFF
	return (PRECOMPUTED_REVERSE[x & BIT_MASK] << (3 * MASK_SIZE) |
		PRECOMPUTED_REVERSE[(x >> MASK_SIZE) & BIT_MASK] << (2 * MASK_SIZE) |
		PRECOMPUTED_REVERSE[(x >> (2 * MASK_SIZE)) & BIT_MASK] << MASK_SIZE |
		PRECOMPUTED_REVERSE[(x >> (3 * MASK_SIZE)) & BIT_MASK])
```
