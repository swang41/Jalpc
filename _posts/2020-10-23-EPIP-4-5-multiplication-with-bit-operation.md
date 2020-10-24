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

'''
Compute two postive integer number with bit operation only
no addition, less or larger operator
Note: Using brute force repeated addition will take O(2^n) time (Page 44)
'''
def bit_multiply(x,y):
	def bit_add(a,b):
		running_sum, k, carry_in, temp_a, temp_b = 0, 1, 0, a, b 
		
		while temp_a or temp_b:
			ak, bk = a & k, b & k
			running_sum |= ak ^ bk ^ carry_in
			carry_in = (ak|bk) & (ak|carry_in) & (bk|carry_in)
			k, temp_a, temp_b = k << 1, temp_a >> 1, temp_b >> 1

		return running_sum

	running_sum = 0
	while y:
		if y & 1:
			running_sum = bit_add(running_sum, x)
		x, y = x << 1, y >> 1
		

	return running_sum
