---
layout: post
title:  "5.0 Even Odd integer"
date:   2020-11-13
desc: "Even Odd integer to oppsite end in the array"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program to reorder entries in the array with integers so that the even entries appear first.

```
cur, right = 0, len(arr)
while cur < right:
  if arr[cur] % 2 != 0:
    while cur < right:
      if arr[right] % 2 == 0:
        temp = arr[cur] 
        arr[cur] = arr[right]
        arr[right] = temp
        right -= 1
        break;
      right -= 1
  cur += 1
 
1, 2, 3, 4 --> 4, 2, 3, 1 --> Pass
```
