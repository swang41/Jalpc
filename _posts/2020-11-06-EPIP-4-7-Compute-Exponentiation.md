---
layout: post
title:  "4.7 Compute x to power of y while x is double and y is integer"
date:   2020-11-07
desc: "Write a program that a double x and an integer y and return x to power of y"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program that takes a double x and an integer y and returns x to power of y. You can ignore overflow and underflow.

```
def power(x,y):
  if y < 0:
    x = 1.0/x
    y = -y
  result, base = 1, x
  while y:
    if y & 1:
      result *= base
    base = base * base
  return result
```

<iframe height="400px" width="100%" src="https://repl.it/@swang88/47computeexponent?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>
