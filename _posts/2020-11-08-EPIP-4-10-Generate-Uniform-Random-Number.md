---
layout: post
title:  "4.10 Generate Uniform Random Number"
date:   2020-11-08
desc: "Implement a random number generator that generates a random integer i between a and b."
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Generate a random integer i between a and b, inclusive, given a random number generator that produces zero or one with equal probability.

```
Given: rand() --> 0 or 1 with equal probability
Goal: urand(a,b) --> i between a and b, inclusive with equal probaility

rand() --> can be 0 or 1. if it represent a bit, a sequence of rand() output can represent a integer
exmaples:
rand() -> 0000(0) or 0001(1)
rand()x2 -> 0000(0), 0001(1), 0010(2), 0011(3)
rand()x3 -> 0000(0), 0001(1), 0010(2), 0011(3), 0100(4), 0101(5), 0110(6), 0111(7)
rand()x4 -> ..., 1111(15)
...
```

```
#idea: rand() x l ... l = math.floor(log2(b-a+1)), each represent a bit, if the number of these l bit greater than b-a, the repeat the same process till it between [0, b-a].

def urand(a, b):
  res, l = 0, math.ceil(math.log(2, b-a+1))
  do:
    for i in range(l):
      if rand():
        res += 1 << i
  while res > b - a
  return (res + a)
```
