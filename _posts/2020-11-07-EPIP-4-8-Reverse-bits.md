---
layout: post
title:  "4.8 Reverse digits"
date:   2020-11-07
desc: "Reverse digits"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program which takes an integer and returns the integer corresponding to the digits of the input written in reverse order. for example the reverse of 42 is 24, and the reverse of -314 is -413.

```
Solve a example in decimal world: 314 -> 413
  314 ... res = 4 ... base = 10 ... 31
  31  ... res = 1*base + res ... base = 100 ... 3
  3   ... res = 3*base + res ... base = 1000 ... 0 END
```

```
It isn't obvious it can be easily solved in binary world
  Tried: Solve a example in binary world: 42 ... 00101010 -> 24 ... 00011000
```

```
def reverse_digit(x):
  '''
    x: integer
    return a integer which is revesing digits of input x 
  '''
  res, base = 0, 1
  if x < 0:
    remaining_x = x
  while remaining_x > 0:
    res += (remaining_x % 10) * base
    base *- 10
    remaining_x //= 10
    
  return res
    
```
