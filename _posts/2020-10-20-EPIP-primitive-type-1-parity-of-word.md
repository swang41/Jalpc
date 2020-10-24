---
layout: post
title:  "4.1 Compute parity of a word"
date:   2020-10-20
desc: "Primitive type"
keywords: "Coding"
categories: [PYTHON, CODINGS]
tags: [python]
icon: icon-html
---

```
'''
Background: The parity of a binary words is 1 if the number of 1s in the word is odd; otherwise, it is 0.
'''

#Brute-Force
def parity(x):
	result = 0
	while x:
		result ^= x&1
		x >> 1
	return result

#Lowest digit
def parity(x):
	result = 0
	while x:
		result ^= 1
		x &= (x-1)

#Lookup table(assume )
def parity(x):
	MASK_SIZE = 16
	BIT_MASK = 0XFFFF
	return (PRECOMPUTED_PARITY[x >> (3 * MASK_SIZE)] ^
		PRECOMPUTED_PARITY[(x >> (2 * MASK_SIZE)) & BIT_MASK] ^
		PRECOMPUTED_PARITY[(x >> MASK_SIZE) & BIT_MASK] ^ 
		PRECOMPUTED_PARITY[x & BIT_MASK])

#Use property of XOR, being associative and communitive, the parity of <b63,b62,...,b3,b2,b1,b0> equals
#the parity of the XOR of <b63,b62,...,b32> and <b31,b30,...,b0>
def parity(x):
	x ^= x >> 32
	x ^= x >> 16
	x ^= x >> 8
	x ^= x >> 4
	x ^= x >> 2
	x ^= x >> 1
	return (x & 1)

'''
Variant problem set: Use bitwise operator to do the following in 0(1) time
1. Right propagate the rightmost set bit in x,e.g., turns (01010000) to (01011111)
ans: 
x += x&~(x-1)-1

2. Compute x mod a power of two, e.g., return 13 for 77 mod 64
ans:
Same to find the most significant bit in O(1) time
def mod2(x):
	#Assume 32 bits length of integer
	n = x
	n |= n >> 1
	n |= n >> 2
	n |= n >> 4
	n |= n >> 8
	n |= n >> 16
	n += 1
	n = n >> 1
	return x-n

3. Test if x is a power of 2, i.e., evalutes to true for x =1, 2, 4, 8, ..., false for all other values
ans:
Get the least significant bit
x -= x & ~(x-1)

'''
```
