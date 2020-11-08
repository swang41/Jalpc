---
layout: post
title:  "4.6 Integer Division implemented with bit operation"
date:   2020-10-23
desc: "Impletmenting integer division with bit operation only"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Given two positive integers, compmute their quotient, using only the addition, subtration and shifting operators.

*Example:*
10/3
brute force: subtract 10 or its remainder by 3 till the remainder less than 3, but there are not bitwise subtraction availble.
burte force(work around): keep adding 3 till the sum is about to exceed 10, bitwise addition is available.

```
*Revisit:bitwise addition*
10 + 3 ... 00001010 + 00000011
sum <- 0
carryin <- 0
k <- 1
remain_a, remain_b <- a, b
while remainings of both integers after right 1 aren't 0:
  ak <- a & k
  bk <- b & k
  remain_a <- remain_a >> 1
  remain_b <- remain_b >> 1
  sum <- sum | (ak ^ bk ^ carryin)
  carryout <- (ak & bk) | (ak & carryout) | (bk & carryout)
  carryin <- carryout << 1
  k <- k << 1
sum <- sum | carryin
```

```
*Revisit:bitwise multiplication*
10 * 3 = 30 ... 00001010 * 00000011 = 00011110
draft: 00001010 + (00001010 << 1) = 00011110
running_sum = 0
multiplier = a
temp_b = b
while temp_b:
  if temp_b & 1:
    running_sum = bitwise_add(running_sum, multiplier)
   multiplier = multiplier << 1
   temp_b = temp_b >> 1
```

```
#My first approach for bitwise division
Problem: x/y ... both x and y are integer
quote = 0
while x >= y:
  power = 1
  subtract = y
  while subtract < x:
    power += 1
    subtract = substract << 1
  power -= 1
  quote += subtract
return quote
```

```
#Better solution for bitwise division, assume 32-bit integer

quote, power, y_power = 0, 32, y << 32
while x >= y:
  while y_power > x:
    y_power = y_power >> 1
    power -= 1
  quote += 1 << power
return quote
```

  


